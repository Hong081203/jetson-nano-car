# ROS2_RC_YOLO11



잭슨나노와 YOLO11을 통해 RC카를 작동 시켜보기로 계획했다.

먼저 잭슨나노를 이용하여 GUI창을 띄웠다.

이후 터미널을 연다. 터미널에서 $를 기준으로 jetson@nano:~는 위치를 나타내고 $ 오른쪽은 명령어를 뜻한다.

터미널을 통해 다음 명령어를 실행시켜줬다.

jetson@nano:~$ sudo apt-get update

jetson@nano:~$ sudo apt-get install fcitx-hangul

위 명령어를 실행한 후 한국어가 나오도록 설정해줬다.

현재 잭슨나노는 해외의 시간으로 흐르므로 다음 명령어를 실행하여 한국의 시간으로 설정해줬다.

jetson@nano:~$ sudo timedatectl set-timezone 'Asia/Seoul'

jetson@nano:~$ timedatectl

메모리 사용량을 확인하기 위해 jetson@nano:~$ free -m 를 실행시켜준다. 여기서 m은 메모리를 뜻한다.

또 디스크 사용량을 확인하기 위해 jetson@nano:~$  df -h 를 실행시켜준다. 여기서 h는 human-readable의 약자다.

와이파이 연결을 위해 jetson@nano:~$ sudo nmcli device wifi connect <ssid_name> password <password>를 실행시킨다.

jetson@nano:~$ ifconfig 를 실행시켜 네트워크 인터페이스의 상태를 확인한다. ifconfig는 인터페이스 설정의 줄임말이다.

우리는 여기서 잭슨나노가 열을 뿜어내는걸 보고 쿨링팬은 작동시키기 위해 cd Downloads 명령어를 실행시키고 jetson@nano:~/Downloads$ cd jetson-fan-ctl를 실행시켜 쿨링팬 디렉토리를 찾는다.

이후 jetson@nano:~/Downloads/jetson-fan-ctl$ sudo sh install.sh 를 통해 쿨링팬 디렉토리를 다운로드 하여 쿨링팬을 작 ROS2_RC_YOLO11

먼저 잭슨나노를 이용하여 GUI창을 띄웠다.

이후 터미널을 연다. 터미널에서 $를 기준으로 jetson@nano:~는 위치를 나타내고 $ 오른쪽은 명령어를 뜻한다.

터미널을 통해 다음 명령어를 실행시켜줬다.

jetson@nano:~$ sudo apt-get update

jetson@nano:~$ sudo apt-get install fcitx-hangul

위 명령어를 실행한 후 한국어가 나오도록 설정해줬다.

현재 잭슨나노는 해외의 시간으로 흐르므로 다음 명령어를 실행하여 한국의 시간으로 설정해줬다.

jetson@nano:~$ sudo timedatectl set-timezone 'Asia/Seoul'

jetson@nano:~$ timedatectl

메모리 사용량을 확인하기 위해 jetson@nano:~$ free -m 를 실행시켜준다. 여기서 m은 메모리를 뜻한다.

또 디스크 사용량을 확인하기 위해 jetson@nano:~$  df -h 를 실행시켜준다. 여기서 h는 human-readable의 약자다.

와이파이 연결을 위해 jetson@nano:~$ sudo nmcli device wifi connect <ssid_name> password <password>를 실행시킨다.

jetson@nano:~$ ifconfig 를 실행시켜 네트워크 인터페이스의 상태를 확인한다. ifconfig는 인터페이스 설정의 줄임말이다.

우리는 여기서 잭슨나노가 열을 뿜어내는걸 보고 쿨링팬은 작동시키기 위해 cd Downloads 명령어를 실행시키고 jetson@nano:~/Downloads$ cd jetson-fan-ctl를 실행시켜 쿨링팬 디렉토리를 찾을 수 있다.

이후 jetson@nano:~/Downloads/jetson-fan-ctl$ sudo sh install.sh 를 통해 쿨링팬 디렉토리를 다운로드 하여 쿨링팬을 작동시켰다.

I2C 장치 연결을 확인하기 위해 jetson@nano:~$ i2cdetect -y -r 1 명령어를 실행한다. (pca9685 통신장치)

ROS2를 이용해야 하므로 ROS2를 깔아줘야한다. 근데 그전 script를 설치해줘야한다. 따라서 다음 명령어들을 순서대로 실행시켜준다.

jetson@nano:~/Downloads$ ls

jetson@nano:~/Downloads$ git clone -b galactic https://github.com/zeta0707/installROS2.git

jetson@nano:~/Downloads$ ls

jetson@nano:~/Downloads$ cd installROS2/

jetson@nano:~/Downloads/installROS2$ ls

jetson@nano:~/Downloads$ cd installROS2

jetson@nano:~/Downloads/installROS2$ ./install-ros2.sh

다음으로 jetson@nano:~$  gedit ~/.bashrc를 실행시켜 에디터를 열고 117~118줄에 받은 코드를 넣는다. 그리고 ROS2 ID를 106으로 바꿨다.

이제 에디터를 닫고 jetson@nano:~$ source ~/.bashrc를 실행시켰다.

jetson@nano:~/ros2_ws$ cca

jetson@nano:~/ros2_ws$ cba

위 두 명령어를 실행시켜 ros2 workspace를 설치해준다. 이는 내가 만드는 ROS2 프로젝트들의 집합을 관리하는 폴더 구조로 볼 수 있다.

이제 ROS2가 제대로 설치됐는지 확인하기 위해 터미널을 추가로 열고 각각 따로 다음 명령어를 실행시켜준다.

터미널1  jetson@nano:~/ros2_ws$ ros2 run demo_nodes_cpp talker

터미널2  jetson@nano:~/ros2_ws$ ros2 run demo_nodes_py listener

Hello World가 나타나는 것을 볼 수 있다.

turtlesim test를 하기위해 다음 명령어를 순서대로 실행시켜줬다.

jetson@nano:~/ros2_ws$ sudo apt update

sudo apt install ros-foxy-turtlesim

jetson@nano:~/ros2_ws$ sudo apt install ros-foxy-turtlesim

jetson@nano:~/ros2_ws$ ros2 pkg list | grep turtlesim

jetson@nano:~/ros2_ws$ ros2 pkg executables turtlesim

그리고 터미널 2개 모두 open이라 쓰고 실행시키면 거북이가 있는 창이 등장하고 화살표로 조종이 가능하다.

또한 거북이의 동작을 확인하기 위해 topic list를 통해 알 수 있다.

이제 젝슨에 monicar3를 설치하기 위해 jetson@nano:~/ros2_ws$  cd ~/ros2_ws/src를 실행하고

jetson@nano:~/ros2_ws/src$ cd monicar3/

jetson@nano:~/ros2_ws/src/monicar3$ cd script/

jetson@nano:~/ros2_ws/src/monicar3/script$ ./carSelect.sh pca9685Steer

jetson@nano:~/ros2_ws/src/monicar3/script$  ./camSelect.sh usbcam

jetson@nano:~/ros2_ws/src/monicar3/script$  cd ~/ros2_ws

jetson@nano:~/ros2_ws$ cba

jetson@nano:~/ros2_ws$ source ~/.bashrc

위 명령어를 실행시켜준다.

추가로 jetson@nano:~/ros2_ws$ sudo apt update와

jetson@nano:~/ros2_ws$ sudo apt install libgomp1 ros-galactic-joy-* ros-galactic-ackermann-msgs ros-galactic-image-pipeline -y를 실행시켜 또 다른 페키지를 받아줬다.

이제 자동차와 카메라가 서로 연결되도록 해야한다.

 jetson@nano:~/ros2_ws$ ls /dev/vi* 를 실행시키고

USB camera port 번호 설정을 위해 다음 명령어를 실행시켜줬다.

jetson@nano:~/ros2_ws$ ls /dev/video*

jetson@nano:~$ cd ~/ros2_ws/src/monicar3/monicar3_cv/param

jetson@nano:~/ros2_ws/src/monicar3/monicar3_cv/param$ gedit camera.yaml

jetson@nano:~$ cd ~/ros2_ws/

jetson@nano:~$ cbpa monicar3

이후 카메라 확인을 위해

터미널1에는 jetson@nano:~/ros2_ws$ ros2 launch monicar3_cv usbcam.launch.py

           jetson@nano:~/ros2_ws$  ros2 launch monicar3_cv usbcam.launch.py를 실행시키고

터미널2에는 jetson@nano:~$ ros2 run image_view image_view --ros-args --remap /image:=/image_raw

           jetson@nano:~/ros2_ws$  ros2 run image_view image_view --ros-args --remap 를 실행시켜줬다.

그 결과 카메라가 작동하는 것을 확인할 수 있었다.
