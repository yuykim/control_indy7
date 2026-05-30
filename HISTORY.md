# History

## 2026-01-12

### Project start

- Started the Indy7 control repository.
- Set the project direction as a Python-based teleoperation workspace for a Neuromeka Indy7 robot arm.
- Used the robot controller IP `192.168.1.10` as the default connection target.

### Robot bringup and safety utilities

- Added `indy7/indy7_start.py` to check the robot connection, enable all servos, and inspect `op_state` before control.
- Added `indy7/error.py` as a recovery script for stopping teleoperation, running `recover()`, enabling servos again, and checking whether the robot is still in an error state.
- Added `indy7/indy7_shutdown.py` to return the robot to home position, stop motion, and turn servos off before shutting down.
- Added `indy7/restart.py` for controller/system restart experiments.

### Teleoperation prototype

- Added `indy7/indy7_keyboard_control_v1.py` as the main keyboard teleoperation script.
- Used Pygame as the input loop and Neuromeka `IndyDCP3` as the robot control interface.
- Implemented relative task teleoperation with 6-DOF controls:
  - `W/S`: X axis
  - `A/D`: Y axis
  - `Q/E`: Z axis
  - `U/O`: RX
  - `I/K`: RY
  - `J/L`: RZ
- Added step-size adjustment with `[` and `]`.
- Added `SPACE` home-position return while preserving the teleoperation flow.
- Ran control commands at about 30 Hz for smoother continuous input.

### Diagnostics and controller experiments

- Added `indy7/check_teleop.py` to inspect teleoperation device/state behavior.
- Added `check_controller.py` to monitor a connected game controller with Pygame:
  - axes
  - buttons
  - D-pad hats
- Kept `indy7/indy7_controller.py` as an unfinished controller-control direction for future work.
- Added `indy7/indydcp3_example.ipynb` as a reference/example notebook for the Neuromeka DCP3 SDK.

### Documentation

- Added `readme.md` with:
  - hardware connection notes
  - Windows network setup
  - robot start position
  - keyboard control mapping
  - execution guide
  - safety notes
- Added documentation assets under `doc/`:
  - `which_lan_port.png`
  - `ping_test_result.png`
  - `indy7_teleop_start_position.png`
  - `move.gif`

## 2026-05-30

### Workspace organization

- Moved the repository into the workspace personal project area as `personal/robot-control-indy7`.
- Set `origin` to `https://github.com/yuykim/control_indy7.git`.
- Preserved the previous organization remote as `upstream`: `https://github.com/SIRLab-RobotArm/control_indy7.git`.

### Dev Diary connection

- Connected this repository to yuykim Dev Diary.
- Added the first public project log.
- Fixed the publish workflow token check for automatic dispatch.
- Verified automatic dispatch to `yuykim_Dev_Diary`.

### Blog publish files

- Added `.devlog.yml` with project metadata for `control-indy7`.
- Added `dev_diary/2026-05-30.md` as the first public diary entry.
- Added `.github/workflows/publish-devlog.yml` so pushes to `HISTORY.md`, `dev_diary/**`, or `.devlog.yml` send a repository dispatch to the blog.
