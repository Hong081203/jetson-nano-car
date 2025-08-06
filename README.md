# ROS2_RC_YOLO11
잭슨나노를 이용하여 GUI창을 띄웠다.

터미널을 열어 다음 명령어를 실행했다.
[~$ sudo apt-get update]
~$ sudo apt-get install fcitx-hangul
위 명령어를 실행한 후 한국어가 나오도록 설정해줬다.

현재 잭슨나노는 해외의 시간으로 흐르므로 다음 명령어를 실행하여 내가 있는 한국의 시간으로 설정해줬다.
jetson@nano:~$ sudo timedatectl set-timezone 'Asia/Seoul'
jetson@nano:~$ timedatectl
