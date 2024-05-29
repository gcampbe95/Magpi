![](https://github.com/gcampbe95/Magpi/blob/main/Untitled%20design.png)

* [Overview](#The_Plan)
* [Pre-Project Considerations](#Pre-Project_Considerations)
* [Timeline](#Our_Timeline)
* [Safety](#Safety_Concerns)
* [Build Brainstorm](#Initial_Build_Questions)
* [Code Brainstorm](#Initial_Code_Questions)
* [Bill of Materials](#Bill_of_Materials)
* [Weekly Updates](#Weekly_Updates)
* [Final Build](#Final_Build)
* [Final Code](#Final_Code)
* [Reflections](#Reflections)



### **The_Plan:**

Our initial goal for the robot arm project is to build an arm that can accurately transcribe a short melody onto a sheet of paper. In service of consistency, these melodies will be composed of quarter notes from a specified frequency range, played in 4/4 time at a constant tempo. During the testing stages, these melodies will also be rendered by a computer to ensure absolute consistency, adequate volume, and the convenience of testing in the lab. 

If time allows, we hope to expand our bot’s capabilities in some of the following ways: 
- Transcribing melodies in different meters and tempos 
- Identifying pitches from a more diverse range of sources
- Accommodating simple variations in note length (half and eighth notes)
- A more accurate machine-learning-based approach the pitch identification (using TinyML)

### **Pre-Project_Considerations:**

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

### **Our_Timeline:**

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

**3/25** - *Goals for this week include making progress with our pitch reader in VS Code and continuing with our CAD modeling*

Build: Continue modeling in Onshape

Code: Continue working on VS Code pitch reader

**4/1** - *This week build will continue modeling and code will get the pitch reader functional*

Build: Continue modeling in Onshape

Code: Get VS Code pitch reader working

**4/8** - *We're using this week to begin finish the frame and continue code research*

Build: Finish frame, start modeling pen holder

Code: Research coding motion with corexy

**4/15** - *This week we're troubleshooting our CAD and fine-tuning the pitch reader*

Build: Update documentation, fix disappearing assembly

Code: Continue corexy research

**4/22** - *Goals this week include starting our motor code and getting our CAD model ready for fabrication*

Build: Double-check all measurements with real parts, start pen mount

Code: Start coding motors and begin work on circle motion

**4/29** - *We're using this week to continue corexy research and polish our CAD*

Build: Finish pen mount, add final touches

Code: Get motors operational, start polar code

**5/6** - *This week we hope to finish our CAD model and have larger corexy motions up and running*

Build: Finish CAD model and prepare for fabrication

Code: Continue work on circle motion

* 5/6 - Alexis takes AP Gov exam
* 5/7 - Alexis takes AP Stats exam
* 5/10 - Gudrun takes APUSH exam

**5/13** - *This will be a code-focussed week, and we'll be working to get corexy completely operational before Alexis graduates*

Build: NA

Code: Combine corexy motions with functions

* 5/13 - Gudrun takes Calc AB exam
* 5/14 - Gudrun takes Lang exam
* 5/16 - Gudrun takes Spanish Lang exam, Alexis takes AP Bio exam
* 5/17 - Gudrun take Physics II exam

**5/20** - *This week we're fabricating and testing*

Build: Fabricate!

Code: Test!

**5/27** - *We're using this week to troubleshoot any issues that arise in testing and finish documentation*

Build: Continue testing

Code: RIP Alexis


### **Safety_Concerns:**
Safety is our first priority, and throughout the process of building our robot arm we will take every precaution to ensure that our robot does not become sentient. Some potential concerns and countermeasures include:
- The robot develops consciousness and starts attacking because it hates the music we play
  - We will include a power button
  - We will play good music
- Gudrun programs the robot to start attacking when it hears Mozart
  - C’est la vie
  - There’s nothing we can do
- We accidentally short circuit our project
  - We will create thorough wiring diagrams beforehand, and double-check our circuit with those before connecting to power

### **Initial_Build_Questions:**
Since our robot will essentially be drawing the same shape in different positions, our actual writing function can be pretty basic. Depending on how professional we want our final transcriptions to appear, a few of our options for representing a note include:
- A diagonal dash with a stem
- A circle/dot with a stem
- An oval with a stem, as a quarter note (or half note, if unfilled) would appear in printed sheet music
- Any of the above, without the stem (indicating that the transcription is only recording melody, without regard for rhythm)
I’m personally inclined toward the first or third option. The dash-and-stem motion for the arm would be more straightforward and it is less visually offensive than a circle, but the standard oval would be better-looking and more adaptable for other note lengths. A fine-tipped marker is my writing implement of choice.

From what I’ve seen, robots tend to have trouble with pressure. To avoid issues with this, I plan to include pieces dedicated to aligning the paper at the same depth and position relative to the arm each time. This should also make code easier, since the lines and spaces will be defined by a constant position and not by the robot’s visual analysis of a staff. The soft marker tip should also accommodate slight variations in height.

### **Initial_Code_Questions:**
Considering Gudrun already created (with absolute success) an auto-tuning project using a microphone and servo, we have a basis for both our code and build. In her code, she has a series of frequency ranges that correspond to different notes. Hence, I’m not worried about the implementation of our pitch reader.
The more intimidating code of our project will be the drawing. To adhere to KISS (keep it simple, stupid), we will forgo our initial vision recognition idea.
This prompts the following questions:
- How will we draw the notes such that they align correctly with their place on the music staff?
- How will we draw an oval? Should it be filled in?
  - We’ll use a coreXY pen plotter to achieve precise motion along both planes
- How will we draw the stem? Should this be a separate subsystem to the oval-drawer?
  - The same system will be responsible for the entire note. If we use a pen, the motion needed to draw the note will be a small-scale version of the motion that places the note relative to the staff. If we go with a stamp, we’ll only need the latter motion.  

### **Bill_of_Materials**

2 x 8mm Steel Rod 350mm long (Amazon)

2 x 8mm Steel Rod 250mm long (Amazon)

2 x 8mm Steel Rod 100mm long (Amazon)

2 x 1/4" Wooden Dowels 

1 x 7mm Spring (Backroom)

10 x LM8UU Slider Bearings (Amazon)

GT2 Belt 1.2m (Backroom)

2 x GT2 Stepper Motor Pulley (Backroom)

3D Printed Parts


### **Weekly_Updates**

* 4/16 - Build : I'm finished with the framework and starting work on the pen holder, which is a little more complicated since it has to accomodate variations in angle and pen size, as well as incorporate a way to control the pen's Z motion. My assembly is mysteriously broken so hopefully I can fix it with versions sometime this week.
* 4/23 - Build: I made a new assembly that will hopefully be immune to the disappearing issue. I finished the mount for the pen holder and am starting the pen holder itself, which is a little complicated. I'm also using today to double-check all my models against their real-world counterparts (dummy steppers, rods, bolts, holes)

### **Final_Build**
Our build for this project was heavily inspired by **[this model](https://www.youtube.com/watch?v=IVgoBncPw4E)**. We ultimately settled on a pen plotter design (our CAD model can be found **[here](https://cvilleschools.onshape.com/documents/f9e96cad35b00365d59784e5/w/c50bc8ac21633ac130774c6d/e/e97623283331c061e6ee782c)** that uses a belt and two stepper motors to control motion in the x and y directions, and a servo to control z motion.

Isometric View
![](https://github.com/gcampbe95/Magpi/blob/main/Magpi%20Assembly%20(1).png)
Front View with Clear View of Pen Holder Mechanism
![](https://github.com/gcampbe95/Magpi/blob/main/Magpi%20Assembly%20(2).png)
Birdeye View
![](https://github.com/gcampbe95/Magpi/blob/main/Magpi%20Assembly%20(3).png)


### **Final_Code**
```python
import time
import board
from analogio import AnalogIn
import ulab.numpy as np
import digitalio
from adafruit_motor import stepper, servo
import math
import pwmio

DELAY = 0.01 # delay between each step 
STEPS = 100 # number of steps for half a rotation

# servo for moving pen up and down 
pwm = pwmio.PWMOut(board.D11, duty_cycle=2 ** 15, frequency=50)
penServo = servo.Servo(pwm)

# motor class, easy control of stepper motor
class Motor:
    def __init__(self, A1pin, A2pin, B1pin, B2pin):  
        self.coils = ( # the four metal coils in motor
            digitalio.DigitalInOut(getattr(board, f'D{A1pin}')),  
            digitalio.DigitalInOut(getattr(board, f'D{A2pin}')), 
            digitalio.DigitalInOut(getattr(board, f'D{B1pin}')),
            digitalio.DigitalInOut(getattr(board, f'D{B2pin}')), 
        )

        for coil in self.coils: # set direction of each coil
            coil.direction = digitalio.Direction.OUTPUT

        # stepper motor instance, allows for easy control of each coil
        self.motor = stepper.StepperMotor(self.coils[0], self.coils[1], self.coils[2], self.coils[3], microsteps=None)
    
    # step function
    def step(self, steps, direction=stepper.FORWARD):
        for _ in range(abs(steps)):
            self.motor.onestep(direction=direction, style=stepper.DOUBLE)
            time.sleep(DELAY)

# init the 2 stepper motors
motorA = Motor(7, 8, 10, 9)
motorB = Motor(5, 6, 3, 4)

# deprecated, didn't use, was to draw a circle using polar math
def draw_circle(radius, num_steps):
    angle_increment = (2 * math.pi) / num_steps
    for i in range(num_steps):
        angle = i * angle_increment
        x = radius * np.cos(angle)
        y = radius * np.sin(angle)

        motorA_steps = int(x + y)
        motorB_steps = int(x - y)

        motorA.step(abs(motorA_steps), stepper.FORWARD if motorA_steps > 0 else stepper.BACKWARD)
        motorB.step(abs(motorB_steps), stepper.FORWARD if motorB_steps > 0 else stepper.BACKWARD)


# list of notes detectable
NOTE_NAMES = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B']

# convert frequency into note name
# source: https://www.johndcook.com/blog/2016/02/10/musical-pitch-notation/
def freq_to_note(frequency):
    if frequency == 0:  # Avoid log of zero
        return "None"
    print(frequency)
    A4 = 440
    C0 = A4 * pow(2, -4.75) # calc half steps to C0
    h = round(12 * np.log2(frequency / C0)) #
    octave = h // 12
    n = h % 12
    return NOTE_NAMES[n] + str(octave)
    
buffer_size = 4096  # power of 2
buffer = np.zeros(buffer_size)  # init buffer

mic_pin = AnalogIn(board.A0)

# collect frequency
# adapted from: https://learn.adafruit.com/sound-reactive-neopixel-peace-pendant/circuitpython-code
def collect_note():
    for i in range(buffer_size): # collect samples
        sample = mic_pin.value
        buffer[i] = (sample / 65535.0) * 3.3 - 1.65  # range centered at 0
    
    # perform FFT
    r, c = np.fft.fft(buffer)
    magnitudes = np.sqrt(r * r + c * c)

    # find the dominant frequency
    dominant_freq_index = np.argmax(magnitudes[1:]) + 1  # ignore the DC component
    sample_rate = 10000 
    frequency_resolution = sample_rate / buffer_size
    dominant_frequency = dominant_freq_index * frequency_resolution

    # convert to note
    note = freq_to_note(dominant_frequency)
    return dominant_frequency, note

# dictionary of musical notes mapped to positions
note_steps = {
    'C4': 0,
    'D4': 3,
    'E4': 6,
    'F4': 9,
    'G4': 12,
    'A4': 15,
    'B4': 18,
    'C5': 21
}

# moves pen to specific note
def move_to_note(current_note, target_note):
    current_pos = note_steps[current_note]
    target_pos = note_steps[target_note]
    steps_to_move = target_pos - current_pos # # of steps to move to get to new note
    
    directionA = stepper.FORWARD if steps_to_move > 0 else stepper.BACKWARD
    directionB = stepper.BACKWARD if steps_to_move > 0 else stepper.FORWARD
    print(steps_to_move)
    
    # move the motors the correct number of steps, instead of asyncrohonous just small steps iterated
    for i in range(10):
        motorA.step(abs(steps_to_move), directionA)
        motorB.step(abs(steps_to_move), directionB)
    print(f"Moved from {current_note} to {target_note}")

# start on first line 
current_note = 'E4'

# main loop
while True:
    # collect note
    dominant_frequency, note = collect_note()
    print(f"Dominant frequency: {dominant_frequency:.2f} Hz, Note: {note}\n")
    note.replace('#', '') # ignore # since we dont plot that
    
    # dont plot notes out of range
    if note not in note_steps:
        print(f"Error: '{note}' is out of range.")
        continue
    
    penServo.angle = 40 # put pen up
    move_to_note(current_note, note) # move to note recognized
    time.sleep(1) 
    
    current_note = note
    penServo.angle = 0 # put pen down, stamps circle
    time.sleep(3)
```

### **Reflections and Design Process**

