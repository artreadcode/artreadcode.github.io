---
title: "2084: A Brutal Reception Desk"
tags:
  - Physical-Computing
---
## In the Beginning...

At the first time when I read the book '1984' when I was a ten-year old young human, it gave me underlying sensation which force me to imagine what would year 2084 look like, when I would be many, many years old and couldn't resist the world order but obey it. Will it be nice or will it be worse than ever? While I has skeptical vision and am a harsh-to-everything-person, I didn't imagine the future will be brighter than the present. I didn't dare to.

Time passed and, after terrible years of pandemic also passed, the world has been changed rapidly. People are more and more addicted to social media and its notion, its own way of politeness and its interaction. Suddenly Internet 'memes' flushed from nowhere and covered up everywhere it went. Some CEOs from Silicon Valley rode the rocket ship and went back to the Earth. Some of them died at deep sea of their home planet. Meanwhile, books, along with natural conversations, also gradually died with individualism, mixture of newborn nationalism.
In developing countries such as South Korea, the conflict between old generation and younger generation is too harsh to bear with. Most of them are based on the different way of receiving rapidly-changing culture, especially abbreviation(based on slang) and technologies.

So, *Newspeak* is already settled down in South Korea society. Here and there. Fewer consonants and vowels, replacing other words with the original form of vocabularies that doesn't contain prefixes, make people more dumber and meaner. Watching every phenomenon as a avid reader of '1984' (read this book more than twenty times), I realised the year 2084 would be exactly same as the world from '1984'.

This is the beginning of this project '2084'.
What happened around the world? People obeyed the law of computers with loyalty, behaving and thinking alike. Terrible modern UI demonstrates this-even people couldn't complain because they had to wait until the bug fixed by tech giants. Computers became humans, meanwhile, won in Go games, draw realistic paints, distinguish dogs and cats, give brighter solutions while 'chatting' with a person, etc. This is what I wanted to implement in the year 2084, dystopian world where computers are look like and behave like organisms.

That's why I built this *2084: A Brutal Reception Desk*. Here's the journey of it.

## 0. (~The Presentation Day from  Week 5)

What computers will use when they observe the world? Might use OpenCV, though, if that open source project would still alive in 2084. Brought the notion of reception desks in the real world, my first plan was if an audience submit their document to 'a receptionist' through a slit, their information would be logged on the National database. That's why I included a webcam, two servos and transparent acrylics to receive information and design a housing.

![Initial Sketch](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/plan.png?raw=true)

The initial process was this: An audience comes up. They hold their *paper* includes their basic personal information. They put their palm on a load sensor. Small gate opens and reveals a tiny slit which is perfectly fit for A4-sized paper. They submit it. A slit concealed. A webcam indicates information and pick image data from it. A computer mixes image data pixel group by pixel group. It will show the result on the display and the piezo will madly beep. End of the registration process in 2084.

The housing result was a huge, teacher's desk-looking instalment because I needed to conceal my MacBook and A4-sized documents from audiences. I was satisfied at the fist, but, after the week 5 presentation, I suddenly realised the problem of my project. Painful debugging and redesigning processes beginneth.

## 1. (Week 6)

Consider everything, Astryd. How could you force audiences to include their sensitive information (some of them might consider their gender as sensitive information) on paper? Also, is there any way of preparing documents when they're in the exhibition site? How could they?

My brain was full of question marks. This idea was great if it were on the sci-fi film and work as a CGI. This is, however, a student project which will be displayed in the classroom. If they should use another laptop to create a word file, jot something down, print it out using CCI's printer and line up at the front of the reception desk, it would be disastrous. That's not a physical computing project. Also, it didn't perfectly suit my intention. What should I do? I spent whole week doodling, suffering, googling and with desperation.

## 2. (Week 7)

Another week of doodling, suffering and googling.

I seriously considered buying a old-school typewriter from the local second-hand store. But there was no luck. Also I didn't want to bring back old memories to people living in the future. It makes computers so *humanistic*. They should be cold-blooded organisms.

Also, to make computers like organisms there should be several movements. They should be flick their eyes, move their fingers or nod their heads. It means that the housing of this project should be changed, too. It's exactly the same as a teacher's desk from nowadays so the modify is necessary.

In this week, I made a 87% of decision for my project. Those were like these:

1. The audience should create their information on the site, not print those from anywhere else or write down on paper. They should obey to the computer. They should follow their rules. Using another machine to create *paper* or using a human way to leave record is not an ideal way.
2. The reception desk must have its own feelings. They can get angry and smash the bell like teachers from secondary schools. (Dearie me!) They can stare us with their eyes. They can look like humans. More consideration is needed for the housing.
3. The interaction between the reception desk and audiences should be natural. Any hassle should be avoided. They should start and finish the whole interaction *only* using this reception desk. Any outer material is not allowed.

I bought a load cell and a HX711 amplifier on Amazon. Also a teacher's bell. A load cell is complicated than I thought and Cyrene told me she gave up implying it to her project. My anxiety level has been arisen.

![The Teacher's Bell that I Bought from Amazon](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/bell.png?raw=true)

This bell looks as suspicious as Miss Minutes. My intention is succeeded.

![The Image of Miss Minutes](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/miss-minutes.png?raw=true)

Also, I tested out using Python as the backend of an Arduino project. I made a very simple Python script on Visual Studio Code and connect it with Arduino IDE. The method was not easy but I used serial communication from Arduino and send a character or a String object to Python. If the Python script receives any right literal objects it would conduct lines that I intended to. I tested this workflow with a flex sensor we'd made in the last class. Its softness makes me calm and concentrating so it helped me a lot for this process.

The result was successful. I flexed the flex sensor and used `analogRead()` to receive analog data from the sensor and tried to print those out on Python (Mac Terminal). It was a simple test but it confirmed me that I can use the Python script as a serial monitor and if I modified codes really well it might do the job.

![Test Number One](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/Test-Circuit.JPG?raw=true)

Right after the first test, I put a yellow LED on the circuit and make the program do two jobs at the same time. Make the Arduino do its job and send data to Python simultaneously. It also succeeded. Now I can finally move on to the next step.

## 3. (Week 8)

Finally, I started to code the actual backend of the reception desk. I made a huge amount of PDF for week 8 and 9. 

## 4. (Week 9)

The first idea of huge housing was recycling cardboards from Art Shop because 3D printers are still not available and there was no time for waiting for vacancy. To recreate Brutalism with cardboards I bought 



