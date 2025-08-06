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
