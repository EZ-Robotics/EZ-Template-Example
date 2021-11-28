# EZ-Template-Example
EZ-Template is a simple plug-and-play PROS template that handles drive base functions for VEX robots.  

EZ-Template Version: 2.0.0-RC4  
Example Project Version: 1.0.0-RC1

[Autonomous routines that used EZ-Template](https://photos.app.goo.gl/yRwuvmq7hDoM4f6EA)

## Downloading

Download the latest released [here](https://github.com/EZ-Robotics/EZ-Template-Example/releases/latest) and open it as a new project in PROS.

## Features
<details closed>
<summary><bold>Joystick Curve</bold></summary>
<br>

> Using the [5225 curves from 2018](https://www.desmos.com/calculator/rcfjjg83zx), (explained [here](https://www.vexforum.com/t/team-5225a-in-the-zone-code-release-yes-you-read-that-right/63199/10)).  The x-axis is the joystick input and the y-axis is the motor output.  

> Normally, pushing the joystick half way means the robot goes half speed.  With an input curve, pushing the joystick half way may only move the robot at 1/4 power.  This means more of the joystick movement goes to lower speeds, giving you more control of the robot.

> When the robot is on, tapping/holding the left/right arrows will increase/decrease how large the curve is.  When arcade is enabled, each stick will have it's own curve.  The y/a buttons will increase/decrease the curve for the right stick.  

> After you find values you like, in `src/main.cpp` set `chassis.set_curve_default(0, 0)` to whatever you liked!  The first parameter is left stick, second is right stick. 

</details>



<details closed>

<summary><bold>Active Brake</bold></summary>
<br>

> If you put the motors on brake type hold, a robot can still push the robot a bit, and when you let go of the joysticks the robot just locks in place.  Active brake runs a P loop on the drive when you let go of the joysticks.  By adjusting the kP, you adjust how hard the robot fights back.  If you make it smaller, there will be a larger deadzone and you'll coast a little bit.  Active brake vs brake type is personal preference.

> To adjust the kP, in `src/main.cpp` change `chassis.set_active_brake(0)` to whatever you like!  We suggest around 0.1.

</details>



<details closed>

<summary><bold>Autonomous Drive PID with Slew</bold></summary>
<br>

> In autonomous, you input inches, the code converts that to ticks and that's our target position, the robot gets to that position using PD.  The robot also uses the IMU to maintain a heading while driving straight.

> The robot also ramps up from a minimum speed to a maximum speed for X inches, that can be adjusted in `src/autons.cpp` in `default_constants()`.  Make sure to uncomment `default_constants` in `src/main.cpp` too!.

> [Check out the tutorial on adding new autonomous routines here!](https://ez-robotics.github.io/EZ-Template/docs/Tutorials/autons.html)

</details>



<details closed>

<summary><bold>Turns and Simple Swing Turns</bold></summary>
<br>

> In autonomous, you input degrees and the robot turns to that angle using PID.

> The swing turns are `ez::LEFT_SWING` and `ez::RIGHT_SWING`, these functions turn using one side of the drive.

> [Check out the tutorial on adding new autonomous routines here!](https://ez-robotics.github.io/EZ-Template/docs/Tutorials/autons.html)

</details>



<details closed>

<summary><bold>Autonomous Selector</bold></summary>
<br>

> While the robot is in disabled, you can select an autonomous routine by pressing the left/right buttons on the brain!  The page it's on when autonomous is enabled is the routine that will run.

> [Check out the tutorial on adding new autonomous routines here!](https://ez-robotics.github.io/EZ-Template/docs/Tutorials/autons.html)

</details>


## Setup
1) Download the latest release [here](https://github.com/EZ-Robotics/EZ-Template-Example/releases/latest).  Extract it, and open it in PROS.
2) In `src/main.cpp`, configure drive and IMU ports to what they are on your robot.  Be sure to read the comments!
3) Configure your wheel size and cartrige.  Remember that 4" omni wheels are actually 4.125!
4) In `src/main.cpp`, at the bottom in `void opcontrol()`, decide how you'd like to control your robot!  Any flavor of arcade or tank!
5) Turn the robot on and use it in driver control.  Make sure the ports are correct and reversed correctly!
6) To test the test autonomous modes, plug into a competition switch and select the autonomous mode on the brain screen by pressing the left and right buttons!  The current page will be the autonomous that runs.  For making new autonomous routines, check `src/autons.cpp` for examples on how to use the drive functions.

## Additing Autonomous Routines
[Check out the tutorial on adding new autonomous routines here!](https://ez-robotics.github.io/EZ-Template/docs/Tutorials/autons.html)

## License

This project is licensed under the Mozilla Public License, version 2.0 - see the [LICENSE](LICENSE)
file for the full license.
