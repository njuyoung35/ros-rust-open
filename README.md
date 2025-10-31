# adp-ros-packages

## start.sh 이주

`start.sh` 이런 스크립트는 사실상 특정 `forza_ws`, `f1tenth_ws`와 같은 워크스페이스에 대해 작동하기 때문에 _deprecated 디렉토리로 격리시켰습니다.

워크스페이스에 대한 이해가 적을 때 만든 스크립트라 그렇습니다.

## adprs_ws 생성

그리고 ros2_rust 관련 패키지 설정을 위한 워크스페이스 및 스크립트를 만들도록 하겠습니다. > adprs_ws

adprs_ws/init.sh는 반드시 `source` 또는 `.`으로 실행해주시길 바랍니다. 패키지 설정을 위한 sudo 관련 요청이 있습니다.

init.sh에 rustup(러스트 컴파일러, 패키지 관리자 통합 관리자) 설치, rust 관련 colcon 패키지 설치 등이 포함되어 있습니다.

rustup을 설치할 때, 프롬프트에 옵션을 물어보는 게 있는데, `1)` 옵션으로 기본 설치를 하시면 됩니다.

init.sh는 rustup 및 파이썬 패키지를 설치하고 `source ~/.bashrc`를 실행합니다. 이를 통해 커맨드들이 환경변수 경로에 반영됩니다.

init.sh은 이후 build_ros2_rust.sh를 실행합니다. 따로 나눈 이유는, init.sh는 최초 한 번 실행하면 되고, build_ros2_rust.sh의 경우 별도로 실행할 수 있도록 나눠놓기 위함입니다.

build_ros2_rust.sh는 필요한 레포지토리들을 불러오고, 러스트 의존성 충돌을 해결하고 (3줄, sed 명령어로 간략히) colcon build를 수행합니다.

즉, 그 빌드가 성공하면 /install/setup.bash 실행을 통해 다른 forza_ws, f1tenth_ws 같이 overlay로서 동작하는 rust 스타일의 ros2 개발을 할 수 있습니다.
# ros-rust-open
