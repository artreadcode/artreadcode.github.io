---
date: 2024-11-04
title: "Dissertation: The Story of weekly tasks (25 Oct - 1 Nov)"
tags:
  - Creative-Coding
  - UAL
  - CCI
  - Dissertation
  - Physical-Computing
---
### Previously on...
[[Dissertation-The-Story-of-mid_September-and-mid_October]]

This week, I finally started to make the actual progress. After all those hard work-idealisation, consideration of feedback, dumb sketches, searching through the Internet, etc.-I am finally able to draw the roadmap in my head. The downside of the perfectionist is they took a seriously long time before kick-off. The good thing is, right after you have a clear roadmap on your mind, the progress will be extremely fast.

Before coding, I created a brief outline of the paper. The opinion is I'm not sure whether I should include the subtitle 'Inspiration' on the dissertation. All those scientific/engineering papers must be objective, however, the 'Inspiration' section looks subjective. Also, if I write down the results from critical reading, the examples will be already included in the paper, right? But I saw lot of students from previous academic years used it. I'll ask a question of this at the Jessica's QnA session on 6th November.

The good examples in my mind is created by John Cage, Libby Heaney, Mark Carney and Professor Eduardo Miranda. Professor Miranda is both the leader and the pioneer of creative applications in Quantum computing field. He wrote the book 'Quantum Computer Music' and announced a LP called 'Qubism', which shows his deep understanding of creativity in 21st Century, because I think creativity in this era is not only using the traditional medium to make something impactful, but also the attitude with no hesitation when there's new technique coming toward you. It's a good reflection for me to write the MSc dissertation because I can throw an iterative question to myself: **'Are you merely a receiver-the fan-of new tech, or are you seeking the problems, the possibilities, the outcomes and the meanings of it?'**

Along with the structure of my paper, I built `Micromoth for Arduino`. I couldn't believe I built this library less than a week. The last of debugging was so painful but I did it. Here's the steps that I went through:

1. Making header files for math

`Micromoth` stems from `MicroQiskit`, which is the essential version of `IBM Qiskit` for the simplest Quantum computing applications. I remember it was this May, but IBM released `Qiskit v1.0` and it leads to lack of support to `MicroQiskit`, which is now deprecated. So, the company that I'm working at, Moth, forked the official repository and started to adapt it for `Qiskit v1.0` which is now called `Micromoth`. There's the fundamental file called `micromoth.py` for Python. It's comparatively easier to make Qiskit simpler for Python because it originally used Python. However, for other programming languages, especially for microcontrollers, it's disastrous.

Why it's like that? Because `Arduino C++` don't have key features of Python and the modern C++. It don't support dynamic arrays, effective resource distribution for maths, plus the hardware restriction. On Arduino website, the one that I borrowed from CCI, `Arduino Mega 2560`'s spec sheet is like this:
``` 
|Clock speed|   |   |
|Main Processor|ATmega2560 16 MHz|
|USB-Serial Processor|ATmega16U2 16 MHz|

|Memory|   |   |
|ATmega2560|8KB SRAM, 256KB FLASH, 4KB EEPROM|
```

It's so tiny for cloud-based Quantum computing like Qiskit. If you want to use Qiskit for your Physical computing project, you need to always bring your laptop with your microcontrollers if you want to use Qiskit on Arduino for Serial communication. Quantum computing's power comes from the calculation of complex numbers in matrices, and Python is the best option. However, for the simplest simulation, e.g. Bell states, and for the creative applications, minimalistic version of `Micromoth` is necessary. Because it's a side hustle and an open-source project, I decided to build up `Micromoth for Arduino` from scratch. ==Before my project, there's no such thing called `Microqiskit for Arduino`, too.==

What should I do to create header files? First of all, because it's mathematically intense, I need to make a math library for this. There's `complex.h` on Arduino but it's too heavy and contains unnecessary functions for `Micromoth`. So, I decided to make my own `complex` library. Including the true-ish random number generator that I made last time, also the `1/sqrt(2)` (`r2`) constant, I included everything on the file called `MicroMothArduinoMath.h`.

``` cpp
struct ComplexNumber {
	float real;
	float imag;
	// A constructor
	ComplexNumber(float r = 0.0, float i = 0.0) : real(r), imag(i) { }

	// Addition of two Complex numbers
	ComplexNumber operator+(const ComplexNumber& other) const {
		return ComplexNumber(real + other.real, imag + other.imag);
	}

	// ...

	float magnitude() const {
		return sqrt(real * real + imag * imag);
	}

	// Conjugate of the Complex number
	ComplexNumber conjugate() const {
		return ComplexNumber(real, -imag);
	}
};
```

If you use `operator+`, `operator-`, `operator*`, you can override the conventional `+`, `-` and `*` operators and define your own calculation. Here's the typical complex number addition and special operations for C^n number space.

Now, we can move onto `MicroMothArduino.h`, the main powerhouse.

2. Making header files for `class QuantumCircuit`

In Python (Qiskit, `Micromoth.py`), you can build arrays with different data types, e.g. in the file, there's a method adding the X gate onto `QuantumCircuit`.
``` py
def x(self,q):
    '''Applies an x gate to the given qubit.'''
    self.data.append(('x',q))
```

There're already so many issues. First of all, using `char` for every single gate operators might consume too much unnecessary resources. And the `data` array, which is initialised as `data = []`, you cannot expand it throughout the execution in `Arduino C++`. Finally, for the `q` parameter, which is the number (`int`) of the qubit is affected by the X gate, cannot added onto the `data` array with the gate, because their data types are different. This is just the simplest(?) issues on this program, so I must work hard to make this happen.

Thus, the thing that I tried is building a `QuantumCircuit` class, of course, but inside of it, I created the `Op` (Operator) struct, which could not only be the gate operator, but also the tiny container which has all parameters that the gate should have.

``` cpp
#include "MicroMothArduinoMath.h"

class QuantumCircuit {
	public:
		enum GateOp { INIT, X, RX, RZ, H, CX, CRX, SWAP, RY, Z, T Y, M };
		struct Op {
			GateOp gate;
			float angle;
			int control;
			int target;

			Op(GateOp g = INIT, float a = 0.0, int q1 = 0, int q2 = 0) : gate(g), angle(a), control(q1), target(q2)
		}
		int num_qubits;
		int num_clbits;

		Op* data;
		int size;
		int capacity;

		String name;
		ComplexNumber* statevectors;

		// ...

}
```

For Arduino to manage its states, I used `enum` to manage the constant variables easier. If the users want to create more gates, they can just simply add the gate's name on the enum list and add its function underneath. For now, I included the basic to intermediate level of Quantum gates for Micromoth. `INIT` is initialisation (setting the first qubit to the zero-ket state). Others are the typical Quantum gates and `M` is the measurement gate.

Inside of the operator, there's an indicator for which gate does this operator indicate. Also, there're multiple parameters which is sometimes mandatory and sometimes don't. For example, for the X gate, you only need a target qubit (the qubit where the X gate will be applied to). But for the CX (Control-X or Control-NOT) gate, you need both a control qubit (the qubit which will provide conditions) and a target qubit. Also, for the RX (Rotation-X) gate, you need an angle value (how much rotation should it take?) and a control qubit. Because there's no such thing like dynamic array on `Arduino C++` with lack of `std::vector`, there's no choice rather than bringing everything into one place.

Also, to support the expansion of the circuit, I needed to use some elementary method of making the array bigger.
```cpp
void initialise(const int* k, int s) {
	size = 0;
	data[size].gate = INIT;
	data[size].angle = 0.0;

	for (int i = 0; i < s; i++) {
		data[size].control = 0;
		data[size].target = k[i];
	}

	size++;
}

void resize() {
	capacity += 2;
	Op* temp = new Op[capacity];
	for (int i = 0; i < size; i++) {
		temp[i] = data[i];
	}
	delete[] data;
	data = temp;
}
```

Before this, in the constructor of the quantum circuit, I initially set the capacity to 10. There's a difference between `size` and `capacity` here, while `size` is for tracking the size of the array and `capacity` indicates the pre-allocated resource for our circuit. Also, the `QuantumCircuit` constructor is for allocating memory and the `initialise()` is for setting all qubits into the zero-ket (`|0>`) state.

Also, to make the structures as lightweight as possible, the methods for gates are actually very simple. You can simply add the name of the gates, the qubits and the angle. The all math part is happening in the `simulation` part.

For example, this is the difference between the X gate, the CX gate and the RX gate.
```cpp
// Pauli-X gate: Flips the statevector
void x (int q) {
	if (size >= capacity) resize();
	data[size++] = Op(X, 0.0, 0, q);
}

// ...

void cx(int s, int t) {
	// ...
	data[size++] = Op(CX, 0.0, s, t); // control qubit + target qubit
}

void rx(float theta, int q) {
	// ...
	data[size++] = Op(RX, theta, 0, q);
}

// ...
```
Whenever you add the gate to the circuit, the size (indicator) should be increased to tackle the system, of course. After this, the most important part of all library is here. Enabling the basic quantum simulations on Arduino.

3. `measurement` and `simulation`

Measurement on Quantum computing is making all those superposition-ed qubits into the deterministic state, as known as 'making quantum states collapse into one point'. In the quantum-scale, 'beings' exist as a probabilistic states. Before you 'measure' it, you'll never know which state they are pointing at. Quantum computing is the high-functioning skill that allows you to control, expect, manage qubits with difficult Maths and Physics. Officially, if you measure it, it'll collapse into the classical bits and it'll lose the quantum-scale properties.

However, we're not dealing with actual Quantum hardwares. We need results of calculation, but we don't need to predict the molecule's interaction or photon's movement. It means that we can do lots of experiment, for example, in `Micromoth`, we can simulate the circuit whenever we want, and we can even 'interfere' between each gate and make fun applications with those numbers. That's the purpose of separating measurement and quantum simulation.

In Quantum computing context, when you measure the circuit, the result from each qubit will store into classical bits so that we can use it into typical classical computing. That's what I did for `measure()` and `measure_all()` method. In `measure()` you can choose which qubit do you want to measure and `measure_all()`, you can add measurement gates in the very last part of each wires (qubits).

And the `simulate()` part was the nightmare.

While doing simulation, we can see the glimpse of `measure_all()` without measurement. Depend on my intention, I can interfere the quantum process and store the results after each gate.
To make those happen, there should be crucial methods. Those are `superposition()`, `rotate()` and `phaseturn()`. In gate-operated Quantum computing, the H gate puts two qubits onto the 'equally-distributed' superposition, so it'll put two qubits' probability into a half and a half. Rotation is key to gates such as the RX gate. Phase is also important to deal with more complicated gates. It'll demonstrate how powerful Quantum computing will be, because in classical bits, they're only 0s and 1s. But for qubits, there will be unlimited combination of data in only two qubits.

With these three, the gate-based operations could be finally built. I used several `if-else` to distinguish each operation, other than `switch`. Because inside of one qubit, the state vector of each qubit will be increased exponentially. Because we're on the tiniest computing resource, I used bit left-shift operations to make it happen. (e.g. `1 << $number$`) So that, we can save memory exponentially.

I won't talk about the detailed, hidden, mathematical + physical operation behind each gate, however, it'll be good to mention the most frustrating bug during the development.
Because I combined all different gates into the one `strct` called `Op`, there're slots for two qubits on both one-qubit gates and two-qubit gates. So, I needed to track whenever I build each gate operations in `simulate()`, am I putting the right gate onto the right qubit. Or, the result of the simulation will be totally different. I thought I handled it quite well, but there were some error.

For example, when I build `g.gate == QuantumCircuit::X`, it's definitely connected to `void x()` in the member function. However, I only added one parameter, which will automatically be mapped into the `control` qubit, not the `target`. Which means that if I do `qc.x(1)` it'll send the X gate into q0, not q1!

That's what happened when I first try the Psi-minus Bell state. The state vectors were different from what it should be! I spent a day for debugging. But anyway, I fixed it on Friday morning, and I need to bring my laptop to Apple Covent Garden to fix the display. What a relief.

Here's the comparison between the `void x()` and `QuantumCircuit::X` in `simulate()`. As you can see, the control qubit and the angle, which will be not needed, are initialised into 0, the default value. `q` is the qubit that the X gate will be positioned onto.

```cpp
void x (int q) {
	if (size >= capacity) resize();
	data[size++] = Op(X, 0.0, 0, q);
}

// ...
// (indentation is needed in the real code)
if (g.gate == QuantumCircuit::X) {
	for (int i0 = 0; i0 < (1 << j); i0++) {
		for (int i1 = 0; i1 < (1 << (qc.num_qubits - j - 1)); i1++) {
			int b0 = i0 + (1 << (j + 1)) * i1;
			int b1 = b0 + (1 << j);
			ComplexNumber temp = statevectors[b0];
			statevectors[b0] = statevectors[b1];
			statevectors[b1] = temp;
		}
	}
}
```

Also, there're multiple methods of measurement/simulation out there. The thing that I'm using is the state vector measurement. There'll be also the probability measurement. But I didn't include this for my MSc thesis. Because for Physical computing, I need the actual calculation, not the probabilities. (Reminder of the purpose of `Micromoth for Arduino`.)

So, here's the wild journey of mine doing lot of hard coding in last week. Now I can move onto Physical computing. I'm honestly so excited to finish this earlier than I expected, because I started to work on my dissertation in such a late time. Next week, I aim for focusing on mapping state vectors onto 3D representation of those, so that I can use it onto spatial interaction with Arduino. Stay tuned. ✌

