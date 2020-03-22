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


