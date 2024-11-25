---
date: 2024-11-25
title: "Dissertation: The Story of weekly tasks (Final)"
tags:
  - Creative-Coding
  - UAL
  - CCI
  - Dissertation
  - Physical-Computing
---
### Previously on...
[[Dissertation-The-Story-of-weekly-tasks-03]]

The journey is now coming to an end. I started to write a dissertation and also gathered all needed components for assemble. 

Honestly, there was no time to visit Dark Lab or find any place to hang the installation and record a video. Bear in mind the pictures in the log is still contains early stage of the manufacturing.

![Fabrication sketch](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_1025.JPG?raw=true)

The important change of the character design of Wie is now the fact that it only has one leg, not two. It was inevitable because the ball of yarn was smaller than I think. Now, it looks more non-human than before. The accelerometer nested upon the leg, and grey yarn covered the entire components.

![Hello, Wie!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_1019.JPG?raw=true)

![The accerlometer](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_1017.JPG?raw=true)

Also, the circuit design was finalised. I drew a formal version of hand drawing, and glued servos and the breakout board onto the acrylic disk. It means that I also finalised the Arduino code for mapping hand gestures in the format of quantum circuit, which was difficult than I thought.

![The finalised design of the Arduino curcuit](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0982.JPG?raw=true)

My original plan was using Block sphere to calculate the 3D coordinate of data values from the quantum circuit and make components waving around the space. However, that was the plan for more complicated version of the instalment, the previous system design using the ukulele. In this it's not useful, even it looks more interesting in Physics.

I added a member function to `MicroMothArduino.h` to support resetting. This is the functionality that other `MicroMoth` is not supporting. This added for the freedom of creativity in Physical computing. So that after the communication of Wie, the circuit can be restored into blank state to build up a new thought.

Managing 9g servos was more difficult than I thought because I needed to test out every single numbers to define which `int` would be suitable for `SERVOMIN` and `SERVOMAX`. This is crucial because if you put a pulse length which is too much, the servo can be down and the whole system would stop running. The fair values were 70 and 470, respectively. Other values such as `pwm.setPWMFreq()` or `SERVO_FREQ` were acceptable from the example library code of Adafruit.

I used single tap detection for the accelerometer to detect hand-stroking. It was easy to detect but the sensor was extremely sensitive. To give some time to interact with Wie, I set up the counter and it will decide Wie will act or not. Here, I didn't forget to avoid `delay()`. Instead, the timestamps from the start of performance and the ending point are tracked by `millis()`.

After mapping the hardware acceleration values as determinators of quantum gate selection, for the translation of the measured state vectors, I used the probability to determine which servo will rotate in how many angles. Because I have successfully implemented rotation gates, and the meaning of state vectors can be described as probability, this could be justified in the context of Physics.

When you put a square of two onto the real number part and the imaginary number part of the state vector, that's the probability. In reality, there is error mitigation to make sure the sum of all state vectors is 1, but in creative application, the tiny hardware noise could be negotiable.

``` cpp
for (int i = 0; i < states; i++) {
	float sr = qc.statevectors[i].real;
	float si = qc.statevectors[i].imag;
	probs[i] = sr * sr + si * si; // |amplitude|^2

	Serial.print("State |"); Serial.print(i, BIN); Serial.print(">: ");
	Serial.print("Probability: "); Serial.println(probs[i], 4);
}
```

The problem was, because the 9g servos looked same but were actually different, the hardware parameter for deciding the baseline of 0s or 1s contained trial and error. But they worked and now the only process left is yarning every components and hang it on the ceiling.

Because I need to go to business trip this Friday, the photos and videos will be recorded early next week. This week, I'll put down every greed in my mind and focus on writing a document (a dissertation). I did it while working and studying as a full-time postgraduate student. This is extremely challenging, but I believe I did such a remarkable job.

This dissertation was the first attempt to make Quantum computing as a partner of Physical computing. I demonstrate that it's possible, so it'll be impactful for future research and also for people around the world who really want to understand the mechanism of black box.

Again, science and technology could 'evolve' if there're creativity, communication and exploration. Sitting at the desk and solving thousands of questions won't be helpful at all. Quantum Physics is still mysterious even for physicists. I wish I could continue my journey of art + science + technology to discover the true nature behind our universe.

*End of Document*

*Astryd Park*