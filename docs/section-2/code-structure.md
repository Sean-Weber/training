Let's look at how our robot code project is structured.

!!! note
    We'll be assuming that our robot code package is `org.team199.robot` and our code lives in `src/main/java/org/team199` but honestly the package naming scheme varies by year and by team, and it doesn't matter as long as you keep it consistent for a project.

A robot project structure generally looks something like this:
```
src/main/java/org/team199/
  └── robot2020/
  |   |   Main.java
  |   |   Robot.java
  |   |   RobotContainer.java
  |   |   Constants.java
  |   |
  |   └── subsystems/
  |   |   |   Drivetrain.java
  |   |   |   Intake.java
  |   |   |   Climber.java
  |   |   |   Lift.java
  |   |
  |   └── commands/
  |       |   Drive.java
  |       |   Climb.java
  |       |   RunIntake.java
  |       |   RunEject.java
  |       |   MoveLift.java
  |       |   Autonomous.java
  |
  └── lib/
      |   MotorControllerFactory.java
      |   FancyMathStuff.java
```
It's a lot, so let's break it down. This is an intro to our robot structure, so we won't go into specifics on how to actually write the code until the next section.

## Main.java
This file is autogenerated, and there is rarely any reason to touch this file at all. It contains the classic `main` method, which is run at startup and starts up the rest of the robot code. 

## Robot.java
This file is the control center of the robot. It has the methods that are called to run the robot.

## RobotContainer.java
This is where we create and store the objects for the subsystems, then set up all of the default commands and joystick commands that the robot uses to operate.

## Constants.java
This file contains all of the numbers that don't change and are relevant to the whole robot. This includes all ports and joystick buttons, which correlate to motor controllers, solenoids, and commands in the code.

## Subsystems
Subsystems are anoter name for robot mechanisms, such as a drivetrain, an elevator, an intake, or a climber. The subystem classes contain the Objects for the motor controllers and solenoids and have methods for controlling the subsystem, which are used by commands.

## Commands
Commands are what run the robot. For example, there may be a `RunIntake` command that runs two motors to turn the wheels that intake a game piece. 

## Lib
The `lib` folder is where we would store the complex calculations, wrappers, or other things that do not directly interact with the robot, but are rather called on by commands or subsystems to assist in their execution. Stuff in this folder would be valuable code that we would actually want to keep and develop on from one year to another, such as drivetrain characterization, motion profiling, or swerve drive code.

## MotorControllerFactory.java
This is the most-used file in the lib folder. It stores methods for creating the objects for the motor controllers and solenoids that are used in the subsystems.