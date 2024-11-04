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

The good examples in my mind is created by John Cage, Libby Heaney, Mark Carney and Professor Eduardo Miranda. Professor Miranda is both the leader and the pioneer of creative applications in Quantum computing field. He wrote the book 'Quantum Computing Music' and announced a LP called 'Qubism', which shows his deep understanding of creativity in 21st Century, because I think creativity in this era is not only using the traditional medium to make something impactful, but also the attitude with no hesitation when there's new technique coming toward you. It's a good reflection for me to write the MSc dissertation because I can throw an iterative question to myself: **'Are you merely a receiver-the fan-of new tech, or are you seeking the problems, the possibilities, the outcomes and the meanings of it?'**

Along with the structure of my paper, I built `Micromoth for Arduino`. I couldn't believe I built this library less than a week. The last of debugging was so painful but I did it. Here's the steps that I went through:

1. Making header files for the library

`Micromoth` stems from `MicroQiskit`, which is the essential version of `IBM Qiskit` for the simplest Quantum computing applications. I remember it was this May, but IBM released `Qiskit v1.0` and it leads to lack of support to `MicroQiskit`, which is now deprecated. So, the company that I'm working at, Moth, forked the official repository and started to adapt it for `Qiskit v1.0` which is now called `Micromoth`. There's the fundamental file called `micromoth.py` for Python. It's comparatively easier to make Qiskit simpler for Python because it originally used Python. However, for other programming languages, especially for microcontrollers, it's disastrous.

Why it's like that? Because `Arduino C++` don't have key features of Python and the modern C++. It don't support dynamic arrays, effective resource distribution for maths, plus the hardware restriction. On Arduino website, the one that I borrowed from CCI, `Arduino Mega 2560`'s spec sheet is like this:
``` ino
|Clock speed|   |   |
|Main Processor|ATmega2560 16 MHz|
|USB-Serial Processor|ATmega16U2 16 MHz|

|Memory|   |   |
|ATmega2560|8KB SRAM, 256KB FLASH, 4KB EEPROM|
```

It's so tiny for cloud-based Quantum computing like Qiskit. If you want to use Qiskit for your Physical computing project, you need to always bring your laptop with your microcontrollers if you want to use Qiskit on Arduino for Serial communication. Quantum computing's power comes from the calculation of complex numbers in matrices, and Python is the best option. However, for the simplest simulation, e.g. Bell states, and for the creative applications, minimalistic version of `Micromoth` is necessary. Because it's a side hustle and an open-source project, I decided to build up `Micromoth for Arduino` from scratch. Before my project, there's no such thing called `Microqiskit for Arduino`, too.

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

If you use `operator+`, `operator-`, `operator*`, you can override the conventional `+`, `-` and `*` operators and define your own calculation. Here's the typical complex number addition and special operations for $C^n$ number space.

Now, we can move onto `MicroMothArduino.h`, the main powerhouse.

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

