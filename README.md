# Robot-Arm

### **The Plan:**

Our initial goal for the robot arm project is to build an arm that can accurately transcribe a short melody onto a sheet of paper. In service of consistency, these melodies will be composed of quarter notes from a specified frequency range, played in 4/4 time at a constant tempo. During the testing stages, these melodies will also be rendered by a computer to ensure absolute consistency, adequate volume, and the convenience of testing in the lab. 

If time allows, we hope to expand our bot’s capabilities in some of the following ways: 
- Transcribing melodies in different meters and tempos 
- Identifying pitches from a more diverse range of sources
- Accommodating simple variations in note length (half and eighth notes)
- A more accurate machine-learning based approach the pitch identification (using TinyML)

### **Pre-Project Considerations:**

Before we start modeling and coding, there are a few questions we have to address:

- Will the bot transcribe continuously or listen to the melody and then write?
  - We’ll set a length for the melody, hit start, and then transcribe in real time
- What interval between pitches will yield the greatest accuracy without sacrificing musical flow?
  - We’ll determine this through testing
- What other parameters do we need to consider for the audio?
  - Refer to auto-tuner documentation
- Will it be possible to accommodate artistic variation (such as vibrato) later in the process?
  - Since pitches are defined as a range of frequencies, it should be possible to accommodate reasonably narrow vibrato. What are other ways we can consider adapting to human musicians?
- What frequency range is ideal for our hardware? 
  - Refer to auto-tuner
- What margin of error is acceptable for a transcription to be considered correct?
  - This depends on the length of our melody, which will be determined through testing
 
We also have to think about how we plan to keep a project with such an expansive scope realistic and on-schedule. To this end, we’ve committed to the following measures:
- The creation of a detailed schedule (found below) with weekly priorities and checkpoints and a realistic and detailed path to completion
- Daily check-ins to share goals for the day, challenges, and necessary updates to any of our planning documents
- Weekly reflections on our progress, to be recorded for inclusion in our final documentation

### **Our Timeline:**

**2/26** - *We will spend this week planning and outlining our vision for the project in general terms*

Whole Team: Brainstorm and research, record initial questions

**3/4** - *This week, we will answer the questions outlined in our initial plan, create specific sketches, and start prototyping our bot* 

Whole Team: Create sketches, finalize design, start prototype, answer preliminary questions

**3/11** - *This week is dedicated to finalizing planning. We’ll transfer our outline materials to a repository, continue work on our prototype, and finalize our schedule*

Build: Outline bill of materials 

Code: Write pseudocode

Whole Team: Finalize schedule, transfer planning to a repository 

**3/18** - *We’re using this week to start the process in earnest. We’ll get our pitch identification up-and-running in Arduino and started in Circuitpython, finish our prototype, and begin the CAD*

Build: Finish prototype, begin CAD

Code: Start pitch-identification Arduino translation

**3/25** - *Overview*

Build: ABC

Code: ABC

**4/1** - *Overview*

Build: ABC

Code: ABC

**4/8** - *Overview*

Build: ABC

Code: ABC

**4/15** - *Overview*

Build: ABC

Code: ABC

**4/22** - *Overview*

Build: ABC

Code: ABC

### **Safety Concerns:**
Safety is our first priority, and throughout the process of building our robot arm we will take every precaution to ensure that our robot does not become sentient. Some potential concerns and countermeasures include:
- The robot develops consciousness and starts attacking because it hates the music we play
  - We will include a power button
  - We will play good music
- Gudrun programs the robot to start attacking when it hears Mozart
  - C’est la vie
  - There’s nothing we can do
- We accidentally short circuit our project
  - Create thorough wiring diagrams beforehand 

### **Initial Build Questions:**
Since our robot will essentially be drawing the same shape in different positions, our actual writing function can be pretty basic. Depending on how professional we want our final transcriptions to appear, a few of our options for representing a note include:
- A diagonal dash with a stem
- A circle/dot with a stem
- An oval with a stem, as a quarter note (or half note, if unfilled) would appear in printed sheet music
- Any of the above, without the stem (indicating that the transcription is only recording melody, without regard for rhythm)
I’m personally inclined toward the first or third option. The dash-and-stem motion for the arm would be more straightforward and it is less visually offensive than a circle, but the standard oval would be better-looking and more adaptable for other note lengths. A fine-tipped marker is my writing implement of choice.

From what I’ve seen, robots tend to have trouble with pressure. To avoid issues with this, I plan to include pieces dedicated to aligning the paper at the same depth and position relative to the arm each time. This should also make code easier, since the lines and spaces will be defined by a constant position and not by the robot’s visual analysis of a staff. The soft marker tip should also accommodate slight variations in height.

### **Initial Code Questions:**
Considering Gudrun already created (with absolute success) an auto-tuning project using a microphone and servo, we have a basis for both our code and build. In her code, she has a series of frequency ranges that correspond to different notes. Hence, I’m not worried about the implementation of our pitch reader.
The more intimidating code of our project will be the drawing. To adhere to KISS (keep it simple, stupid), we will forgo our initial vision recognition idea.
This prompts the following questions:
- How will we draw the notes such that they align correctly with their place on the music staff?
- How will we draw an oval? Should it be filled in?
  - We’ll use a coreXY pen plotter to achieve precise motion along both planes
- How will we draw the stem? Should this be a separate subsystem to the oval-drawer?
  - The same system will be responsible for the entire note. If we use a pen, the motion needed to draw the note will be a small-scale version of the motion that places the note relative to the staff. If we go with a stamp, we’ll only need the latter motion.  

### **Bill of Materials**

### **Pseudocode**


