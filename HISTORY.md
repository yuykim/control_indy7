# History

## 2026-01-12

### 프로젝트 시작

- Indy7 제어용 저장소를 시작했다.
- Neuromeka Indy7 로봇팔을 Python 기반으로 직접 조작하는 teleoperation 작업 공간으로 방향을 잡았다.
- 로봇 컨트롤러 기본 접속 대상으로 `192.168.1.10`을 사용했다.

### 로봇 구동 전 확인 및 안전 유틸리티

- `indy7/indy7_start.py`를 추가해 로봇 연결, 전체 서보 활성화, `op_state` 확인 흐름을 만들었다.
- `indy7/error.py`를 추가해 teleop 중단, `recover()`, 서보 재활성화, 에러 상태 확인을 한 번에 수행하는 복구 루틴을 만들었다.
- `indy7/indy7_shutdown.py`를 추가해 home 위치 복귀, motion stop, servo off를 거쳐 안전하게 종료하는 루틴을 만들었다.
- `indy7/restart.py`를 추가해 컨트롤러/시스템 재시작 실험을 분리했다.

### 키보드 teleoperation 프로토타입

- `indy7/indy7_keyboard_control_v1.py`를 메인 키보드 제어 스크립트로 만들었다.
- Pygame 입력 루프와 Neuromeka `IndyDCP3` 제어 인터페이스를 연결했다.
- 상대 task teleop 방식으로 6자유도 제어를 구현했다.
  - `W/S`: X축 이동
  - `A/D`: Y축 이동
  - `Q/E`: Z축 이동
  - `U/O`: RX 회전
  - `I/K`: RY 회전
  - `J/L`: RZ 회전
- `[` / `]` 키로 이동 step size를 조절할 수 있게 했다.
- `SPACE`로 home 위치에 복귀한 뒤 teleop 흐름을 다시 이어갈 수 있게 했다.
- 연속 입력이 부드럽게 들어가도록 약 30Hz 입력 루프를 사용했다.

### 진단 및 컨트롤러 실험

- `indy7/check_teleop.py`를 추가해 teleop device/state 동작을 확인했다.
- `check_controller.py`를 추가해 Pygame으로 외부 컨트롤러 입력을 확인했다.
  - axes
  - buttons
  - D-pad hats
- `indy7/indy7_controller.py`는 이후 조이패드 제어로 확장하기 위한 미완성 방향으로 남겨두었다.
- `indy7/indydcp3_example.ipynb`를 Neuromeka DCP3 SDK 참고 예제로 보관했다.

### 문서화

- `readme.md`에 다음 내용을 정리했다.
  - 하드웨어 연결 방법
  - Windows 네트워크 설정
  - 로봇 시작 자세
  - 키보드 조작 키맵
  - 실행 방법
  - 안전 주의사항
- `doc/` 아래에 작업 참고 이미지를 추가했다.
  - `which_lan_port.png`
  - `ping_test_result.png`
  - `indy7_teleop_start_position.png`
  - `move.gif`

## 2026-05-30

### 워크스페이스 정리

- 저장소를 워크스페이스 개인 프로젝트 영역인 `personal/robot-control-indy7`로 옮겼다.
- `origin`을 `https://github.com/yuykim/control_indy7.git`로 맞췄다.
- 기존 조직 원격 저장소는 `upstream`으로 보존했다: `https://github.com/SIRLab-RobotArm/control_indy7.git`.

### Dev Diary 연결

- 이 저장소를 `yuykim_Dev_Diary`에 연결했다.
- 첫 공개 개발 일지를 추가했다.
- 블로그 자동 반영 workflow의 token 조건을 수정했다.
- `yuykim_Dev_Diary`로 자동 dispatch가 정상 동작하는지 확인했다.

### 블로그 발행 파일

- `.devlog.yml`에 `control-indy7` 프로젝트 메타데이터를 추가했다.
- `dev_diary/2026-05-30.md`를 첫 공개 diary로 추가했다.
- `.github/workflows/publish-devlog.yml`를 추가해 `HISTORY.md`, `dev_diary/**`, `.devlog.yml` 변경 시 블로그로 자동 반영되게 했다.
