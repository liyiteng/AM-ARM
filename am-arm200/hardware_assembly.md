# Hardware Assembly Guide

This guide covers the AM-ARM200 follower arm assembly. Install all screws loosely at first, then tighten them after the parts are aligned.

## Servo ID Setup

Before assembly, assign the correct ID to each servo. We recommend using the [`lerobot_alohamini`](https://github.com/liyiteng/lerobot_alohamini)debug command.

### Option 1: lerobot_alohamini (Recommended)

Set the servo ID with the `lerobot_alohamini` [debug command](https://github.com/liyiteng/lerobot_alohamini/blob/main/examples/debug):
```bash
python examples/debug/motors.py configure_motor_id \
  --id 1 \
  --set_id 2 \
  --port /dev/ttyACM0
```

### Option 2: FD Debug Tool

You can also use the Feetech [FD Debug Tool](https://www.feetechrc.com/Data/feetechrc/upload/file/20240622/FD1.9.8.3.zip), for example FD Debug Tool v1.9.8.3.

1. Download and install the FD Debug Tool.
2. Connect one servo to your computer through the Waveshare Bus Servo Controller.
3. Open the FD Debug Tool.
4. Select the correct COM port and baud rate. The typical baud rate is `1000000`.
5. Click `Scan Servo` to detect the connected servo and read its current ID.
6. Enter the target ID in the ID field.
7. Click `Write` or `Save` to update the servo ID.
8. Disconnect the servo and repeat the process for the remaining servos.

## Leader Arm (5V)

### 1. Configure the servos

Connect the 5V power supply to the servo controller, connect the controller to your PC with a USB-C cable, and connect one servo to the controller.

![Leader servo ID wiring](media/assembly/leader/01-servo-id-wiring.jpg)

Set the servo IDs one by one.

![Leader servo ID sequence](media/assembly/leader/02-servo-id-sequence.jpg)

Use the following layout as the reference for servo IDs 1-7 on the leader arm.

![Leader servo ID layout](media/assembly/leader/20-servo-id-layout.jpg)

The 5V 1/147 servos are configured for multi-turn mode at the factory. Using the same `lerobot_alohamini` [debug command](https://github.com/liyiteng/lerobot_alohamini/blob/main/examples/debug) setup, set the servo phase to `12` to reset them to single-turn mode:

```bash
python examples/debug/motors.py configure_motor_phase \
  --set_phase 12 \
  --port /dev/ttyACM0
```

After configuration, use `get_motors_states` to check the servo status:

```bash
python examples/debug/motors.py get_motors_states \
  --port /dev/ttyACM0
```

### 2. Assemble the base and shoulder

After the servo IDs and phase are configured, start the mechanical assembly.

![Leader base servo installed](media/assembly/leader/03-base-servo-installed.jpg)

![Leader shoulder servo installed](media/assembly/leader/04-shoulder-servo-installed.jpg)

![Leader shoulder upright installed](media/assembly/leader/05-shoulder-upright-installed.jpg)

![Leader upper arm link installed](media/assembly/leader/06-upper-arm-link-installed.jpg)

![Leader elbow servo installed](media/assembly/leader/07-elbow-servo-installed.jpg)

![Leader elbow link installed](media/assembly/leader/08-elbow-link-installed.jpg)

### 3. Install heat-set inserts

Install the heat-set inserts into the J56 printed part.

![J56 heat-set inserts](media/assembly/leader/09-j56-heat-set-inserts.jpg)

![J56 heat-set inserts installed](media/assembly/leader/10-j56-inserts-installed.jpg)

### 4. Assemble the wrist

Install the wrist servo, bearing, and wrist cover.

![Leader wrist servo installed](media/assembly/leader/11-wrist-servo-installed.jpg)

Install the pin and bearing. Alternatively, use the no-bearing version: `O_L_J5_Pin_No_Bearing.stl`.
![Leader bearing and wrist parts](media/assembly/leader/12-bearing-and-wrist-parts.jpg)

![Leader wrist bearing installed](media/assembly/leader/13-wrist-bearing-installed.jpg)

![Leader wrist cover installed](media/assembly/leader/14-wrist-cover-installed.jpg)

### 5. Assemble the gripper

Install the gripper linkage and gripper servo.

![Leader gripper linkage installed](media/assembly/leader/15-gripper-linkage-installed.jpg)

![Leader gripper servo installed](media/assembly/leader/16-gripper-servo-installed.jpg)

![Leader gripper installed](media/assembly/leader/17-gripper-installed.jpg)

### 6. Install the servo controller

Install the servo controller on the base and check the wiring.

![Leader controller board installed](media/assembly/leader/18-controller-board-installed.jpg)

### 7. Final check

The leader arm assembly is complete. Check that each joint moves freely and that no cables are pinched.

![Leader arm complete](media/assembly/leader/19-leader-arm-complete.jpg)


## Follower Arm (12V)

### 1. Prepare the servos

Label the servos before assembly so each joint can be identified later during calibration. The servo ID setup process is the same as the leader arm, but the follower arm does not require phase configuration.

![Follower servo ID labels](media/assembly/follower/01-servo-id-labels.jpg)

### 2. Assemble the base and shoulder

Install the base servo into the base printed part and route the cable through the opening.

![Base servo and base parts](media/assembly/follower/02-base-servo-and-base-parts.jpg)

![Install the base servo](media/assembly/follower/03-install-base-servo.jpg)

![Route the base servo cable](media/assembly/follower/04-route-base-servo-cable.jpg)

Mount the shoulder servos and install the shoulder link.

![Mount the shoulder servo](media/assembly/follower/05-mount-shoulder-servo.jpg)

![Attach the shoulder link](media/assembly/follower/06-attach-shoulder-link.jpg)

![Install the opposite shoulder servo](media/assembly/follower/07-install-opposite-shoulder-servo.jpg)

![Install the upper arm shell](media/assembly/follower/08-install-upper-arm-shell.jpg)

![Upper arm side view](media/assembly/follower/09-upper-arm-side-view.jpg)

### 3. Assemble the elbow joint

Install the bearing and spacer, then assemble the elbow servo and printed housing.

![Bearing and spacer](media/assembly/follower/10-bearing-and-spacer.jpg)
Install the pin and bearing. Alternatively, use the no-bearing version: `OB_F_J5_Pin_No_Bearing.stl`.

![Install the bearing spacer](media/assembly/follower/11-install-bearing-spacer.jpg)

![Elbow parts and servos](media/assembly/follower/12-elbow-parts-and-servos.jpg)

![Assemble the elbow servo](media/assembly/follower/13-assemble-elbow-servo.jpg)

![Attach the elbow housing](media/assembly/follower/14-attach-elbow-housing.jpg)

![Close the elbow housing](media/assembly/follower/15-close-elbow-housing.jpg)

### 4. Install heat-set inserts

Melt the heat-set inserts into the corresponding holes. Keep the inserts straight and flush with the printed surface.

![Heat-set inserts](media/assembly/follower/16-heat-set-inserts.jpg)

![Heat-set inserts installed](media/assembly/follower/17-inserts-installed.jpg)

### 5. Install the wrist and gripper linkage

Route the wrist servo cable before closing the wrist section. Then install the wrist extension and gripper linkage.

![Route the wrist servo cable](media/assembly/follower/18-route-wrist-servo-cable.jpg)

![Main link assembled](media/assembly/follower/19-main-link-assembled.jpg)

![Wrist extension installed](media/assembly/follower/20-wrist-extension-installed.jpg)

![Gripper linkage installed](media/assembly/follower/21-gripper-linkage-installed.jpg)

![Arm with gripper linkage](media/assembly/follower/22-arm-with-gripper-linkage.jpg)

### 6. Install the camera mount

Install the camera mount parts at the wrist end.

![Camera mount parts](media/assembly/follower/23-camera-mount-parts.jpg)

![Camera and mount plate](media/assembly/follower/24-camera-and-mount-plate.jpg)
Secure the camera mount with M2x12 screws.
![Install the camera mount](media/assembly/follower/25-install-camera-mount.jpg)

![Camera mount installed](media/assembly/follower/26-camera-mount-installed.jpg)

### 7. Optional gripper friction pads

You can add custom friction pads to the gripper fingers. Use rubber, silicone, or another high-friction material to improve grip.

![Optional gripper friction pads](media/assembly/follower/27-optional-gripper-friction-pads.jpg)

### 8. Install the servo controller

Place the servo controller into the printed cover, then slide the cover into the slot on the base.

![Controller board and cover](media/assembly/follower/28-controller-board-and-cover.jpg)

![Controller board installed](media/assembly/follower/29-controller-board-installed.jpg)

### 9. Final check

The follower arm assembly is complete. Check that each joint can rotate through its expected range without cable tension or mechanical interference.

![Follower arm complete](media/assembly/follower/30-follower-arm-complete.jpg)
