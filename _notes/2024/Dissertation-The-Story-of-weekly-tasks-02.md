---
date: 2024-11-11
title: "Dissertation: The Story of weekly tasks (2 Nov - 10 Nov)"
tags:
  - Creative-Coding
  - UAL
  - CCI
  - Dissertation
  - Physical-Computing
---
### Previously on...
[[Dissertation-The-Story-of-weekly-tasks-01]]

### 1. The visualisation
As I've mentioned before, now's the time to implement the precious `Micromoth for Arduino` library to the Physical computing part. Before that, I needed to confirm the detailed visualisation sketch and the technical sketch. I was able to do this with the eureka moment, but lot of struggle happened in the background.

The problem was, I still couldn't visualise the exact art installation in my head. The ideal image is from the animated computer music series, [Animusic](https://youtube.com/playlist?list=PL11rcBnKdlyPd--MRTJOMn__12IZ7S2So&si=d4g4a3h25SV3akei), which I first watched 13 years ago (2009!), and which has been the huge inspiration since then. In 'Resonant Chamber', it introduces plucking movements of robot fingers alongside the perfectly synchronised string music. 

![Resonant Chamber](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/resonant%20chamber.png?raw=true)

This served as the building block of my belief when I was 11 years old, the belief which computers can be the composers and partners of musicians. I think that's why I first imagined this similar image in my head and tried to buy the ukulele/guitar for the MSc project. Also, the electric guitar is my main musical instrument. Next, it both sounds and looks awesome in the art exhibition, with its iconic visuals with such a powerful amp⋯⋯.

![Long time no see, the soldering desk!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0799.JPG?raw=true)

On Wednesday and Thursday, I finally visited CCI multiple times to pick up the sensors and be given an advice. I haven't seen Matt from last year's PComp class, so I talked to him with my art installation idea. And the first reaction that came out from him was 'This is too complicated.' It felt like I smashed my head with a sack of tomatoes, standing in the middle of tomato juices without wiping it. Still? I spent four months to narrow my project down, but should it be considered as complicated?

Matt talked to me with patience, mentioning his previous project about locomotion. He also tried to create mind-bogglingly complicated interaction but ended up with vibration motors that participants could wear. It was so simple. Much simpler than the original plan, however, its interaction was filled with satisfaction to deliver the purpose of the art installation well. I was fascinated by his project, but in my mind, I was stubborn to change my plan. I still thought the ukulele is the best choice because I know it well compared to other musical instruments, and state vectors can be mapped onto four different ukulele string. I thought there's nothing more suitable than the ukulele.

So, on Wednesday, I did soldering for mini solenoids for string-plucking locomotion, listened to the advice from Matt and Louis (he did such a complicated robot hand piano project for his PhD) and bought the ukulele from Flying Tigers and went back to work. And there were two sessions afterwards, about the graduation show and the dissertation. Those two are the reason why I drained out in that night.

![I thought I totally stuck and won't make it to the graduation show...](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0801.JPG?raw=true)

I already submitted an EC claim to support my poor mental health and financial struggle and it was accepted. I didn't think I would use the final deadline for the submission, but having an EC feels safe. However, for the graduation show, I should submit at least a detailed sketch, a prototype or a working image so that my project can be received as a true project, not a concept, and finally get on the stage. I'm so behind from the others. What should I do? Why am I doing like this? I am so stupid, I thought. And stay bed all night without my eyes closed.

In the next morning, there was a miracle. Or **my iterative design thinking process lead me to a miracle.**

In this ungodly hour, my brain switched on, and such a fantastic idea came to my mind. It felt like I grabbed an idea from outside the window while it was walking pass through. (Yes, I borrowed this metaphor from Erich Kästner.) This is the memo that I wrote Thursday morning.

![eureka](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0815.PNG?raw=true)

And turned out 'pipes on the door' is called ***wind chimes*** in English.

Wind chimes are perfect. Its locomotion is much simpler than the ukulele but extremely persuasive. Wind chimes are non-binary. There's no pluck-the-string-or-do-not binary encoding. Its sound is produced naturally, not through digital amps. The motto of *'Wie?'* is ==bringing the world's tiniest interaction into the physical world== so wind chimes fits really well. Finally, the bonus point is, when you gather up wind chimes, it'll look like the actual Quantum computer.

![Google Quantum AI's Quantum computer](https://quantumai.google/static/site-assets/images/marketing/quantum-computing/hero-heading.jpg)

Of course, for the graduation show, my project won't look like this. (I hope so, anyway) But it'll be a good start for future exhibitions that I'll lead, using `Micromoth for Arduino`! I wanted to make the visuals as similar as possible, so I originally thought using 16 different 9g servos using `Adafruit PCA9685` (because it has 16 pin groups for 16 servos) and make a group of huge wind chimes from scratch. I searched aluminium tubes online, acrylic sheets and fishing lines. I thought this is the finalised design.

The fact that I realised is when the design is good, when the design is persuasive and when you like the idea you can build up the sketch, the visualisation and the system design really fast. Even within the few hours! That's what I did!

But on Friday, during the dissertation meeting with Polo, they recommended me to buy wind chimes from Amazon and just use it. They said it's good for melodies and for saving time and effort. I should've listened to their words. I thought minimising the effort will lead the terrible mark. But after I was talking to Kearie, the beloved Studio Quantum artist, she said that's a good idea. Thus, I was finally convinced.

When I looked up the Amazon website the price range was not so bad, so I ordered the strongest fishing lines, three wind chimes and three acrylic sheets. I needed to slightly modify the sketches but that's not a problem at all. This is the final sketch and system design.

![Astryd presents...Wie](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/wie-sketch.jpg?raw=true)

(Also, I realised the wind chimes had holes on their aluminium tubes so that they could be hung on the ceiling. I was so ignorant to neglect the fact that if I create the wind chimes from scratch with customised tubes, I should make multiple holes on the surface!)

For the Arduino circuit, it's quite simple. However, even if the system design looks simple, there would be hard work in the background. Because I've never used `Adafruit PCA9685` before, same for `Adafruit ADXL343 accelerometer`. In the upcoming week, this will be the final stage of my coding. Figuring out the mechanism of these two and map the quantum circuit onto the physical setup.

### 2. Debugging `Micromoth for Arduino`

I thought I created the perfect Arduino library for quantum simulation. However, on Sunday night, I tested out the complex three qubit system and my board almost fried itself.

![overflow!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0833.JPG?raw=true)

I didn't know Arduino prints `ovf` for memory overflow. This was such an interesting discovery. But I'd got things to do.

There was a bug in `phaseturn()`. I accidentally bring the wrong `.real` and `.imag` for the calculation and that's why the numbers were suddenly jumped. Secondly, I realised I didn't make `swap`, `rz`, `crx` gates because I didn't expect to use three qubit system. (I was a total idiot) I needed to debug lot of things. There was also an error in `rz` gate where I brought wrong index of `statevector`.

Long story. Around 1AM Monday, I was able to finalise `Micromoth for Arduino` and run this quantum circuit on Arduino Mega 2560.

![The result from my Micromoth](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0836.JPG?raw=true)

Anyone can check if this is correct or incorrect on IBM Circuit Composer.
![The answer!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/eight%20superposition.png?raw=true)
Such a beautiful eight superposition qubit state, on which classical computers will never simulate!

Also, I added a method for `Evaulation` section for my thesis. It'll track the remained memory and it the memory is less than 100 bytes it'll stop all executions. I needed to code low-level C++ but that wasn't a problem.

```cpp
int how_many_memory() {
    extern int __heap_start, *__brkval;
    int v;
    return (int) &v - (__brkval == 0 ? (int) &__heap_start : (int) __brkval);
}
```

After that simulation, there were 7085 bytes of memory left. Arduino Mega 2560 has a total of 8kb (8192 bytes) of SRAM (dynamic memory) so this simulation only used 107 bytes for local variables, array and other dynamic allocations! This is remarkable.

I ordered bunch of stuff from Amazon and borrowed everything from CCI. Now I can build up the installation and submit the proposal for the graduation show successfully! After coding the 89% of the Physical computing part, I'll write the Introduction of my thesis, too.

It's finally happening! I couldn't believe I developed the MSc project quite fast.
Stay tuned ✌🏻

