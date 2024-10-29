---
date: 2024-10-24
title: "Dissertation: The Story of mid-September + mid-October"
tags:
  - Creative-Coding
  - UAL
  - CCI
  - Dissertation
  - Physical-Computing
---
### Previously on...
[[Dissertation-The-Story-of-August-and-September(ish)]]

- Achievement one: **ual:Qiskit Fall Fest 2024** went incredibly well!
![Me doing lectures of Quantum computing](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0002.jpg?raw=true)
- Achievement two: I went a one-night holiday to my friend's house in Colchester!

In the past few weeks, I set my dissertation aside and focused on hosting the perfect event for the beginners of Quantum computing. While preparing for the event, there was two important meetings with Rebecca and Polo, also a chance to set the short-term goal for my dissertation.

Rebecca said I should **say clearly about the fact that this project is not affiliated from the company and all work is purely by myself**. I plan to include it in the introduction or in the technical motivation section of the paper. However, I'm so glad that I found the solution as a member of Moth, because there will be lot of opportunities of raising questions, because CCI can't help me with Quantum computing. I also bought the [*Bela board*](https://bela.io/products/bela-and-bela-mini/), just in case. But I've got important insight with help from Lieven, Tom and Rohit, too.

![It was expensive, though...](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0407.JPG?raw=true)

For example, while preparing for the event, I created a tiny amount of code which brings a `1/sqrt(2)` (this constant is important when you're performing rotation gates on a quantum circuit) and a random number generator to Arduino. By the way, I'm using Arduino Mega 2560 from CCI and I'm so glad that I can borrow stuffs from CCI. Everything was so expensive these days.
Back to the point, I found out after 7-8 decimal places of `1/sqrt(2)`, Arduino cannot print out the difference between the (slightly) different decimal numbers. Also, it had an issue between `float` and `double` because even in Arduino document some methods return `float` value and some returns `double`, on Arduino Mega both work similar. I was so stressed out because all things will be decimal numbers in the Quantum computing library. However, those (slight) incorrectness won't be important in creative applications. Because, like I've mentioned before, we're not focusing chemical simulation here. Also, it's calculating the value, anyway. So, I decided the value of `r2` well and put it on the top of the header file.

Secondly, there's no such random number generators on Arduino. The reader might probably ask: What are you talking about? There's a `random` Arduino basic method! However, when you look into the documentation, it generates `pseudo-random`. It means that it makes numbers based on the pre-described algorithm. If we generate thousands and thousands of numbers, we could predict the next one. However, for Quantum computing, I needed a true-random number generator.

I could use one analog pin to receive a true noise from the open circuit and modify it using `analogRead()`. But I seriously didn't want to waste any pins when I'm doing Physical computing projects. Instead of that, I used bit-shift left operations. Because of Arduino's tiny architecture, this is also not powerful enough like Python's `random()`. However, it's much better for the random number generator between `0.0` and `1.0`. I'm planning to include it to the library, but I tested it on the simplest `.ino` file.

I went to CCI multiple times to discuss Physical computing aspect of my project. I imagined some flocking movement triggered by a quantum circuit. There will be a robot hand. Not the realistic one but the very mechanical-style one with servos or something. Lexin recommended the tiny servos or actuators for the small rotational movements from the *fingers* which flocks the strings, and the solenoids for pressing the guitar chords. Luckily, Rohit got five different actuators so that I could borrow those. However, I forgot there're actually six different strings on the guitar. I should borrow one more. Also, for the *petting* interaction, I need an accelerometer. I need to borrow these two.

What's all this about? Here's the presentation slides that I used for the meeting with Polo, my new supervisor: [Over here!](https://docs.google.com/presentation/d/1uFbecsMUEKNryNf6cNDbDOSXy2KLXsEI3C2IBNdjEFE/edit#slide=id.g2768ca7ef44_0_65)

Before the meeting with Polo: I discussed length with Rebecca about what's the method/ology for my dissertation. (The slides are [here](https://docs.google.com/presentation/d/1tsqtTuwIT888ZIA-cXCVe4X6O9RzY10T3n86Wmt2Po4/edit#slide=id.g2768ca7ef44_0_65)) I thought it's a practise-based research but if I emphasise the technical motivation more, it wouldn't. So, I needed to shift my point of view and be honest. I'm making *Micromoth for Arduino* to make my project possible. So, after the motivation, there will be a iterative attempt to make it happen. That was the true definition of a practice-based research. Thank you so much, Rebecca!

After all of those discussion, I finally started to make a final version of the slides, where I'll add things gradually and use for my final presentation. Early bird catches the worm. Polo also said this is a good idea and we discussed more about the project design.

![The workflow sketch of Wie?](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/Screenshot%202024-10-28%20at%2022.28.58.png?raw=true)

While we're talking, I suddenly remembered a ukulele might be a better option rather than a guitar, because it only has four different strings and that might be beneficial for such a tiny computational resource like Arduino. Polo also said I shouldn't insist only the guitar, also the Physical movement to generate sound. But for my purpose, physical movements, spatial interactions are the crucial part so I should study hard for those.
Also, I'm planning to write the first draft of the paper, before the 'Development' part to save time. I slightly regret that I didn't do anything during August and mid-September but my mental health was so bad back in those days. Also, I believe because I thought about it consistently, now I've got a good outline of the thesis.

Also, after this time cohort, my project finally has a name. It's '*Wie?*'. '*Wie*' is also the name of my imaginary non-human being. Or is it truly a non-human being? Isn't it a futuristic 'human' like the ones from the book 'The Time Machine - H.G.Wells'? It's up to the audience's thought. But while bringing the tiniest spatial interaction to the surface, '*Wie?*' will throw a question to us in post-humanism-istic point of view. Because in quantum-scale realms, the division between the state A and the states B gets dimmer. It's not 0 or 1. That's crucial for this moment of our 21st century⋯⋯.

![The digitalised sketch of Wie](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/Screenshot%202024-10-28%20at%2022.28.08.png?raw=true)

Ok, the festival is ended, I moved to the great place to live, I recovered my mental state from depression, **now is the time to get back to study**!

Peace. ✌️

c.f. 1. I found £15 ukulele in the shop called *Flying Tiger* which is located in Tottenham Court Road. Its colour is good, also it's awesomely transparent. Maybe I should buy this!

![I found a perfect ukulele!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/IMG_0624.JPG?raw=true)

c.f. 2. 'Wie' means 'how'! I was so confused! What a mistake! Probably it was just a typo. Anyway, it suits the purpose of the project, so this embarrassment shall pass⋯⋯.

![An a3 poster for ual:QFF2024](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/A3.jpg?raw=true)

