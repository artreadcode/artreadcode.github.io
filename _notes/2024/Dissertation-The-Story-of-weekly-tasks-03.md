---
date: 2024-11-18
title: "Dissertation: The Story of weekly tasks (11 Nov - 17 Nov)"
tags:
  - Creative-Coding
  - UAL
  - CCI
  - Dissertation
  - Physical-Computing
---
### Previously on...
[[Dissertation-The-Story-of-weekly-tasks-02]]

This week was full of important company events, also finally received the fixed laptop, plus the most precious day in mankind-my birthday! 🎂 So, this week's log is more a diary of Thursday, 14th November.
I didn't want to spend my birthday with nervous feelings and that's why I didn't go to work and stayed at CCI from 9 to 5. As I've mentioned in the previous week's log, this week is fully dedicated on digital fabrication. Also, such a good timing, that the acrylic sheets, wind chimes and fishing lines have just arrived. So, I went to CCI, and focused on reminding my memories of 3D printers and laser cutters.

First, I needed to design an acrylic disk for hanging wind chimes, an Arduino and servos. Because it needs to be printed on a laser cutter, I used Adobe Illustrator. The biggest acrylic sheet that I could get was 600mm x 450mm so the maximum diameter of the disk will be 450mm. Originally, I wanted to make it bigger. However, after the session of PG Graduation Show, this size is more plausible.
I added the tiny holes (5mm of diameter) for fishing lines, some decorations which look exactly like Google Quantum AI's quantum computer. The disk is amber, and it leaded to the beautiful result. (I added the small Moth logo because it looks cute.)

![Acrylic sheet](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/ai.JPG?raw=true)

Before that, I put Wie's chicken legs into the 3D printer. It was trickier than I thought because my USB was in exFAT format, not FAT32 format that the printer wants. I needed to erase it once more and feed the sliced 3D model into the machine. Thankfully, it worked smoothly. I still remember the nightmare about spaghetti-styled threads that ruined the print last year⋯⋯.

The thing is, setting up the laser cutter took longer than I expected. I didn't use the laser cutter after last year's Creative Making class so that does make sense⋯⋯. However, I did it and print out the first result.

![It's printing!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/laser-printer.JPG?raw=true)

However, the tiny holes didn't been cut properly because it was so tiny. So, I increased the diameter a little bit and divided the layers so that the laser cutter can only cut the holes again, not the whole disk. After that, it worked.

While waiting for the 3D printer, I also did soldering. Today's soldering was dedicated to an accelerometer. GND is for GND, Vin is for 5V, SCL and SDA are there for respectively. I soldered pins carefully onto the tiny PCB mockup to implant on Wie's forehead.

![soldering!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/accelerometer-soldering.JPG?raw=true)

And, on Saturday morning, I went to CCI and soldered the INT pin as well. I saw the changed X, Y and Z coordinate values through the Serial Monitor and originally thought the accelerometer itself should be moved along with the stroking interaction. But I checked the example codes from the official Adafruit library and realised there's a code called `touth`. There was an option for hardware interruption. It doesn't make any sense if something is touching (single tap) the accelerometer, it won't move quite much to be detected. It means that something on the board is sensing the movement, and that's called as hardware interruption. And it's only available when the INT pin is connected to Arduino⋯⋯.
I didn't do it on Thursday because I didn't know. Goodness me.

![Wasted £3.50 because of only one pin...](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/morning-soldering.JPG?raw=true)

Anyway, back to the Thursday, the result from the 3D printer was marvellous.

![Wie's chicken legs](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/wie-legs.JPG?raw=true)

And the result from the laser cutter looks good, too. There will two more to make a quantum computer on the ceiling.

![Acrylic disk](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2024/printed-disk.JPG?raw=true)

On my birthday (Friday), I had a lengthy discuss with Polo about the Methodology section. I thought I finished the Methodology section within four paragraphs, but they suggested more. There was the point that I needed to review, because my writing only contained the overview of the methodology, not the detail⋯⋯. I think mine has a mixed structure between the Background, the Methodology, the Evaluation, etc. Based on our discussion, I decided to separate the visual design and the technical development (`Micromoth for Arduino`) from each other. Also, I think the detail of the Methodology could be directly imposed underneath each field so I left the Methodology section as it looks. Hope this is ok for the future⋯⋯.

This long journey is going to the end. I already submitted the proposal for the degree show on Monday and I'm moving onto the building, the dissertation, the final step of coding at the same time. Also, I'm preparing for the conference/event in Cyprus in the upcoming week. There's so much things to do.

c.f. I just realised that I didn't add the tiny hole for fishing lines in the middle of the disk. I need to visit CCI again⋯⋯.


