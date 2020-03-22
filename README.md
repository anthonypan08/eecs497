# Learning Objectives
After completing our tutorial sequence, students should be able to:
1. Design and build functioning circuits that incorporate an Arduino, as well as components like switches, lights, and sensors
2. Write "Arduino Sketches" (programs) for their circuits that collect data and log it for later retrieval
3. Troubleshoot issues with their circuit wiring, if any should occur
4. Debug their Arduino Sketches, if they malfunction or don't work as expected
# What to Cover
Heavily integrate the Autodesk Circuit Designer.
Include a link to [this video](https://www.youtube.com/watch?v=nL34zDTPkcs), as a quick introduction for more impatient students.

## For 1) Circuits,
* Explain the very, VERY basics of electrical wiring. For now, talk only about direct current.
* "Flows" from a point of "high potential" (voltage) to a point of "low potential"
* On an Arduino, this would look like:
  * Battery/Power source to the Arduino
  * Connect 5V, ground to the components of a circuit (an LED)
  * Should light up. (Have this be part of a tutorial?)
* Explain different terms:
  * Voltage
  * Current
  * "Electric potential" is comparable to "potential energy", such as the gravitational potential energy of river water at the top of a hill.
  * Some of this potential is lost when the energy is used by something to do something.
    * Lighting a light bulb (load) uses energy.
    * This causes a voltage drop "across" the load.
    * Different kinds of loads exist:
      * Light bulbs/LEDs (energy used to make light)
      * Electric motors (energy converted into rotational motion)
      * Resistors (energy converted into waste heat)
* Add an explanation of resistance.

* What if we wanted to power multiple loads? Do we need additional 5V pins and additional ground pins?
   * No, we don't. Can connect several things into this circuit, like this: (diagram)
   * This will "split" current between the different loads. It's possible to calculate voltage drops and current flow in different parts of this circuit; those are the sorts of problems that you would solve in an electricity/magnetism physics class.
   * We don't care about those details too much. However,
   * Think (again) of the river water analogy. You could split the river into three and power three different water wheels, but each water wheel would receive proportionally less power.
   * The maximum amount of current ("river water") produced by the 5V pin on an Arduino is...
   * Takeaway: you can power sensors and stuff with the Arduino 5V pin, but not, like, multiple electric motors.

* Talk about things to watch out for when working with electric circuits
  * "Shorting" a power source, like the Arduino's 5V and GND pins or the two terminals of a battery, is Bad.
  * Can destroy expensive electronics.
  * Avoid this by making sure that no "uninterrupted" path exists between 5V and GND
* At some point, talk about "pull-up" and "pull-down" resistors (for preventing "free-floating" button readings).
* Explain how the Arduino can monitor/control electrical current.
  * Arduino has I/O pins. They can act as a voltage source ("outputs" current), or "receive" a voltage.
  * Demo: analogWrite, different levels of brightness on an LED
  * Demo: analogRead, measure the voltage drop across a variable resistor
  * (Note that it's generally safe to run 5V power directly into one of these pins, since the Arduino's internal circuitry acts as a load between the pin and ground) 
  * If you were to connect two Arduinos together, you could use (something like) this process to have the two communicate.

* Explain breadboards
  * Rather than needing to splice wires together directly, can use a breadboard.
  * Explain how they're laid out, how they're connected.
  * Draw out some diagrams in Adobe Illustrator or something

## For 2) Arduino Sketches and 4) Debugging
### Programming in C++

* Computer code analogy: a very literal-minded and methodical cook following a multi-step recipe.
  * Example recipe would somehow incorporate, "And repeat steps 4-6 until...", which we could later use to introduce loops.
("If the egg white turns purple...(?)" to introduce if-statements.)
  * Cook has "no common sense": if a typo/misprint/coffee stain covers up the "until...", cook will repeat 4-6 forever.
  * If Step 7 says "take the container from the previous step and add bleach" back when Step 6 said "pull the container out of the oven; it will now be dirty," but then a Step 6.5 gets added that says "retrieve a bottle of ammonia" without Step 7 being rewritten, Bad Things will happen.
  * Implications:
    * Good for delegating tasks to be done by other people.
    * Requires that you understand the task very thoroughly.
    * Minor mistakes can cause big problems in unexpected ways (the recipe was supposed to make a cake but somehow the whole house filled with chloramine gas!?).

* Kind of like what an Arduino is.
  * Is a "wrapper" around a programmable microcontroller, normally used in electronics, e.g. to control a vending machine.
  * The microcontroller is like the methodical chef without common sense, and the code that it is running is the recipe.
  * Arduino enables programming that can easily affect and be affected by the real world.
  * Would be useful for simple, repetitive tasks that need to be done at scale, e.g. taking regular measurements of moisture levels at different locations.

* Tutorial: button that toggles an LED on or off.
  * Busy loop that checks if the button has been pressed; if yes, toggle the light's state.
  * Analogy: recipe that calls for a cook to find and stand next to a light switch, making sure that he could hear the doorbell (setup());   * wait until he hears a doorbell, then after which he'll flip a light switch. Repeat this until he dies (loop()).
  * Write out some pseudocode for this, and actual code. Walk through an example of the cook executing each step of the program.
  * Explain the "translation process" from the pseudocode to the regular code.
  * Demonstrate with an example circuit + Sketch on the Autodesk Circuit simulator.
  * Explain variables as being like whiteboards on which some value is written. bool is a tiny whiteboard only big enough to store "yes" or "no" (technically, "true" or "false"). int is a larger whiteboard that can store a number. char is a whiteboard that can fit a single letter. And so on.
bool var; var = true; means to take the whiteboard named "var", erase its contents, and write a "true".
  * Explain chained assignment, bool b1, b2, b3; b1 = b2 = b3 = true; as reading a value, writing it onto a whiteboard, and repeating for the next bool in sequence.
* Explain if statements.
* Explain the setup() and loop() functions.

* Explain debouncing.
  * Notice that, without debouncing, the light doesn't just toggle on or off.
  * Demonstate print-statement debugging with Serial.write; note that when we press the button, we see multiple "light switched!" print statements even when we only click the button once.
  * One solution (debouncing): remember the last time the button was pushed, and don't switch the LED if the button is on, but had been already been pressed <100 ms ago.

* Segue into a long tutorial talking about C/C++ syntax and semantics.
  * The difference between global and local variables.
  * Legal C++ identifiers (can't start with a number, can't be a reserved word, etc.).
  * The concept of a "variable scope" (what it is, how it's literally defined with curly braces).
  * Can't redeclare a local variable with the same name in the same scope (compilation errors).
  * Can "hide" a name from the outer scope by declaring another one with the same name.
  * Run through a few examples step-by-step, with diagrams.
  * Explain function calls.
  * Talked before about reading values into variables.
  * Can "do work" and read the result of doing that work. That's what digitalRead() does.
  * Going back to the "writing a recipe" metaphor, since we're (generally) writing very complicated (or at least, very detailed) recipes, it might be helpful to create "mini-recipes" that we could "re-use" throughout the recipe: like, "crack an egg into a container".
  * Show an example of a function that returns the smaller of two numbers.
  * Talk about how the function signature basically declares variables.
  * Can read from them and write into them.
    * What happens if we write into them?
    * Whiteboard metaphor: we erase and overwrite the "function's parameter whiteboard", but not the whiteboard from which it was copied.     * Passed in the value of the caller's variable, "pass-by-value".
    * What if we wanted to change the original whiteboard? Then would pass a pointer or a reference. Show what this would look like.
    * This is a very important topic that we will talk about later.
  * Explain return values.
  
* Mention that this would get annoying with a lot of buttons; setting several global variables, etc.
  * Wouldn't it be nice to group these related variables together?
  * Introduce structs; show how to declare a struct to store "was last pressed at this time" (ButtonPress?).
  * Rewrite code to use the struct rather than global variables.
  * Am repeating code to populate the struct.
  * Write a function: takes in a parameter by reference, the struct, and sets its values.
  * Note: function overloading, talk about how we could also write functions with the same name that take different parameters
  * We're still repeating the if check, though. Write a function: takes in a parameter (the ButtonPress struct) and a debounce interval,   * and does the debounce check.
  * Code looks simpler!
  * Make it even more simple: demonstrate how to write member functions (for the struct).
  * Can be invoked on any struct instance, and it'll be passed as an "implicit" parameter called this.
* Elaboration: note that, if we were to hold the button down, it would toggle on-and-off after each debounce interval. How might we fix this so the button is a "true" toggle-switch?
  * Example: robust ButtonPress struct, with constructor. Sets up a pin in its constructor.
  * Call an "update" function in every loop, which reads the state of the pin, determines if it's being held down for a long time, automatically debounces...
  * If hasChanged, then switch.
  * Include a "reference library" of classes that manage this kind of thing.
