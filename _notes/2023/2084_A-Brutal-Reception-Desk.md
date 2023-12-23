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

![The Idea comes from the unstoppable thoughts!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/Imagination.JPG?raw=true)

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

I bought a load cell and a HX711 amplifier on Amazon. Also a teacher's bell. A load cell is complicated than I thought and Cyrene told me she gave up implying it to her project. My anxiety level has been risen.

![The Teacher's Bell that I Bought from Amazon](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/bell.png?raw=true)

This bell looks as suspicious as Miss Minutes. My intention is succeeded!

![The Image of Miss Minutes](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/miss-minutes.png?raw=true)

Also, I tested out using Python as the backend of an Arduino project. I made a very simple Python script on Visual Studio Code and connect it with Arduino IDE. The method was not easy but I used serial communication from Arduino and send a character or a String object to Python. If the Python script receives any correct literal objects it would conduct lines that I intended to. I tested this workflow with a flex sensor we'd made in the last class. Its softness makes me calm and concentrating so it helped me a lot for this process.

The result was successful. I flexed the flex sensor and used `analogRead()` to receive analog data from the sensor and tried to print those out on Python (Mac Terminal). It was a simple test but it confirmed me that I can use the Python script as a serial monitor and if I modified codes really well it might do the job.

![Test Number One](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/Test-Circuit.JPG?raw=true)

Right after the first test, I put a yellow LED on the circuit and make the program do two jobs at the same time. Make the Arduino do its job and send data to Python simultaneously. It also succeeded. Now I can finally move on to the next step.

## 3. (Week 8)

Finally, I started to code the actual backend of the reception desk. I made a huge amount of PDF for week 8 and 9. This is the link of the PDF: https://drive.google.com/file/d/1Q1lyQgTyWEcsF5AMcc0mAXmQQAA3VXjW/view?usp=sharing

-  ==A tilt switch → A toggle switch==: At the first time, I tried to use a tilt switch to turn the machine on and off. This step indicates if the new user comes up to the reception desk and ready to insert their information to the desk or not. But I discovered significant glitches on my code. It was weird because sometimes my code was working and sometimes didn't. I booked the tutorial with Agnes and discovered a tilt switch is a switch from a marble toy that I used to play when I was a child, not a proper switch to indicate 0s and 1s. I broke down the limit switch (Poor thing!) and finally realised the mechanism of it. I started to use a toggle switch which looks exactly like this.

![A toggle switch from the opening credit from Loki](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/toggle.JPG?raw=true)

-  ==A slit with two servos and a load cell → Two limit switches==: When my idea sticked to a design looks like a teachers desk I needed a slit to make audiences submit their information as paper. However after I decreased the size of the reception desk due to the financial problem and lack of time, I don't need it anymore. It makes computers machines. What is the natural form of interaction when humans need to submit something to someone? <br> There's a term: "Pass me the paper." I can do that with limit switches. When people give something to someone they put the object onto the palm. I decided to use limit switches instead of a load cell because I don't need to weigh anything on this project. Go sleep, my load cell. Maybe next time.

-  ==A piezo → Several servos==: If the user takes too long to submit their submission, the reception desk would beep loudly. However, this is too simple for an organism, so I changed it to the servos. If the computer angry at you it will slam the bell. Like a teacher back in the school years. Also at the end of the interaction it will show similar movements like a human. I don't know the final form of it yet, but we'll see how it ends. The current thought of my project is the final step of the project is too vague and meaningless, so I need to fix it.

- ==Two webcams → Only one webcam==: I kept thinking myself that using two webcams is nonsense because information of audiences is already created by a computer. Why you need to submit your paper into a digital way using another webcam on the computer? It is total nonsense. That's why I changed the way of submitting paper to the reception desk. Computer already knows information, so there should be another way to make the user think that their information is submitted to the reception desk. Never stop thinking.

- ==A physical printer → Morse codes and a thermal printer==: To create information as a physical form I stumbled upon an idea of a *ticket*. If the reception desk creates a ticket and make the user submit onto a palm of itself, it would be very meaningful interaction. After the user submit their information the desk will print out *the ticket*. I need to build a backend of translating morse codes into a `String` and send it to the Arduino for printing.

Also, **this week was Extremely hell** because of building a morse code transmitter from scratch using Arduino IDE and Python. Everyone (including Agnes) acknowledged that my project is extremely complicated and very difficult to build, but I managed to do that. So proud of you!

I tried to use a limit switch to insert a morse code into the reception desk. But I realised I wanted to make a new interaction for the inserting process. I started to think what's the best input for creating short and long signals. And arrived at the point. It was ==a potentiometer==. Measuring time between the highest and the lowest resistance using `millis()` it would be the best indicator for dividing electrical signals into long signals and shorter ones. That's the basic concept of morse codes. If the time is short it would be translated into a short signal of morse codes and if it takes slightly long than it would be translated into a long signal. For Python, I used an indicator and send indicators to Python script to store them into `.` or `_`, just like morse codes.

The first step was a potentiometer and the next is about grouping each signals to create actual `String` characters from electrical signals. For this I implied ==two pushbuttons==. One of them acts like *a separator* (to divide each words) and the other acts like *a space bar* (to insert a blank letter between specific words).

![My method of Morse Codes](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/Morse-Codes.png?raw=true)

If the user turns a potentiometer up and down, it will make each dots and dashes. If the user presses one pushbutton it will insert a blank letter (`''`) for dividing each characters. If the user presses another pushbutton it will insert a divider (`'/'`) for a blank letter. Using `String` method provided by Python package such as `.join()`, I succeeded to create a String `Astryd Park` with a group of electrical signals and dividers like this: `.- ... - .-. -.-- -.. / .--. .- .-. -.-`. 

After this I built a workflow with a webcam and OpenCV. **This was an actual hell of mind-boggling processes**. (Everyone concerned my mental health.)

First, access onto video object automatically after the input process ended properly. At the first time, I considered it connected to with `sys.argv[]` but it wasn't. OpenCV University gave me a hint. It was something about a command line application. I'm not using it right now because I deleted all input process except those are coming from the Arduino, so I can stick to `default camera value: `. Done for finding a proper index of the Logitech webcam. It was on index `0`.

Secondly, `cv2.VideoCapture` should work really well. There was an official bug of it which didn't shut down the window properly so that it makes Python script stop in the middle. So I should bring several lines of `cv2.waitKey(1)`. If the user press the ESC key using an external input device such as a physical long wooden stick it would make the `videoCapture` object release the capture object which is the Logitech webcam.

During the second process it will save all frame into the form of `.mp4v`. After the user kills this step it will move onto bringing the specific frame from the video object onto the Python script. It means that the reception desk won't consider the best state of the user. It only considers its best timing for capturing facial data of the user. What a brutal reception desk!

The third process is converting that image into a bitmap image and transform it into a hexadecimal array. OpenCV helped me a lot with its methods (functions). It should be done well because a thermal printer only accepts that kind of data to print image. This was the hardest part of my project. Agnes suggested me to using Raspberry Pi to make process easier but I cannot use it because I didn't know how to send analog data to it. Maybe next time.

I tried to send the huge hexadecimal array which is a size of 300 x 300 to Arduino but it failed. The transmitting speed was extremely slow because of the limited size of RAM on the Arduino. So there was another method of transmitting data to Arduino IDE. I can write a C++ header file using Python. A thermal printer requires specific form of a header file to print a bitmap. That's the last method. If this fails, I should change the direction of my project.

![Example C++ header file](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/header.png?raw=true)

Everyone told me I would fail, but I did it. *Almost* did it because I realised C++ couldn't imply the live update of its header file because, obviously, C++ complies everything prior to execution. So it means that a thermal printer now can print something out but it is the result of a past user. That's a incomplete workflow. I decided to print this hexadecimal array straightly on a thermal printer because people need to obey the computer's way. The user can see their face but cannot understand because data is processed already. That's what the modern algorithm acts like. The veiled backend processing conceals everything and people of colours, women and others become victims.

I cannot spend all paper roll for printing such a huge hexadecimal array so selected some pixel data from the array.

The final step of this huge backend is sending all processed data into the Arduino and process it along the rules. I printed `String` data and hexadecimal data. That was the easiest part for a thermal printer. But this printer is so tricky to use, so I finally understood why Adafruit stopped making it.

After finishing initial circuit design I soldered a lot. Now I should design the housing and confirm the result of whole interactions as quickly as possible.

![first soldering](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/first-soldering.JPG?raw=true)

## 4. (Week 9)

This week was all about debugging my circuit and building a proper housing for my project. I finally escaped from the huge teacher's desk-like housing and explore Brutalism with plywoods, transparent acrylic plates and clay. For plywoods I built outer rim of the housing. For acrylic plates it would contain information of interaction. I especially select transparent acrylics because Nothing Phone (1) gave me an idea. I think if the computer reveals everything about itself transparently people still couldn't understand what it's up to. That's Brutalism. Also plywoods really help me to create cold-looking housing.

![the sketch of the housing](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/sketch-of-housing.JPG?raw=true)

I tried to build the housing with cardboards at first but it looks very messy so I left it as an initial try.

![initial housing](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/first-housing.JPG?raw=true)

The user interface should be combined as a form of cold, physical buttons and switches, not containing friendlier input devices. Also it should looks like a small Brutalism building. I added clay for its organism-like touch. When clay from Art Shop hardens it gives you creepy feelings. I covered a Logitech webcam with clay and transformed it into an eye. For servos and a limit switch, I created hands and legs. After I finished the sketch of the housing and figured it out well suddenly the proper ending of this project was arrived. After a thermal printer prints the *ticket*, the user has to be given an autograph of the reception desk. After that the user can become a proper citizen of year 2084. Signing on the paper makes a computer alive and I'm finally satisfied with the whole workflow.

Also I tried more proper soldering with a toggle switch and limit switches. Lexin thought me how to use three-pinned switches properly so I figured out why some glitches kept happening on my circuit. For my object, I needed to choose only two pins from switches and use them like a pushbutton's. I cancelled all soldering that I did before and start again. I was extremely painful because I already burnt several spots on my fingers. But it leads a better result, though. Sometimes cancel everything and start from the beginning would be extremely helpful.

![Soldering...again.](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/soldering.JPG?raw=true)

I trapped inside the building while using a laser cutter late at night. What a wonderful experience. And yes, I designed everything with a glue gun, clay and huge effort.

![An eye](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/eye.JPG?raw=true)

![Hands](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/hand.JPG?raw=true)

After all of this, I should record a teaser trailer for this project and showcasing whole interactions. Cinematic Mode on my iPhone helped me a lot.

<iframe width="560" height="315" src="https://www.youtube.com/embed/o1TTCmOTaoM?si=00m1vcfyPEDo_0xk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

![The title image of the brutal reception desk](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/final.JPG?raw=true)

## Is This the End?

Definitely not. We didn't conduct any show. It is extremely sad but Jessica conducted a small *Demo day* for students who want to voluntarily showcase their work. I signed up for it, too. And really looking forward to it.

If there were an exhibition by CCI I really wanted to design the whole process of this reception desk. Make a reception desk really huge, make a queue at the front of the desk and make a huge showcase video, not only presenting my work awkwardly toward the camera. If there were a chance, I would definitely sign up for the external exhibition, etc. Hopefully someone can lead me to do that.

Also, because of several reasons in my life (e.g. financial crisis, etc.) effected me a lot and that's why I *slightly* failed to do a proper time management. If I start something at the very first it wouldn't be harder than this. I swear I'll perform better in the next time. I realised why time management and building a workflow at the very beginning of the huge project is extremely important.

This is the nice start. In this term I can finally discover the possibilities of creative computing. I really want to be a pioneer of the broadening of creative computing. With every effort and more hard work, yes, I can do that.

![Added after the demo day - Thank you, Adina! For this wonderful photograph!](https://github.com/artreadcode/artreadcode.github.io/blob/main/assets/images/2023/UAL/Pcomp/demo-day.jpg?raw=true)

c.f. This photo is added after the demo day.





