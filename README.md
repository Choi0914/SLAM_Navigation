# 2D_LiDAR_SLAM_Navigation
이 레포지토리는 MORAI simulator 환경에서 2d lidar를 사용해 SLAM을 하고 SLAM으로 얻은 map을 바탕으로 지정한 장소로 로봇을 이동시키는 프로젝트입니다.<br>

### 사용 운영체제
- Ubuntu 18.04LTS
- ROS melodic

### 사용 시뮬레이션 환경
- MORAI simulator
    - scout-mini 모델 사용

### 실행 전 작업
- MORAI simulator 실행
    - map 선택 및 scout-mini 모델 선택
    - 3D LiDAR 설치
- ros-bridge 실행
```
$ roslaunch rosbridge_server rosbridge_websocket.launch
```
- tf-setting
```
$ roslaunch kw_tf tf_setting.launch
```

### 1. 3D Lidar -> 2D Lidar 전환
3D Lidar의 heigtht 조절해 2D Lidar처럼 사용
- 3D Lidar
![lidar_3D](https://github.com/Choi0914/SLAM_Navigation/assets/121415776/c5679427-c3a8-4b47-820a-c8309d739370)

- 3D Lidar -> 2D Lidar 전환
```
$ roslaunch pointcloud_to_laserscan sample_node.launch
```
![convert_to_lidar2D](https://github.com/Choi0914/SLAM_Navigation/assets/121415776/300b6db0-463b-49c2-8b9c-7ae61515a7f4)

### 2. SLAM
- SLAM 시작
```
$ roslaunch gmapping slam_gmapping.launch
```
![gmappig_render](https://github.com/Choi0914/SLAM_Navigation/assets/121415776/3192cb91-7cf9-4a82-b148-ba6610a11622)

- SLAM 종료
```
$ rosrun map_server map_saver
```
- 완성된 map

![map2](https://github.com/Choi0914/SLAM_Navigation/assets/121415776/e126e443-cfa8-4cdb-a810-4533f90c9ee7)



### 3. Navigation
2D-navi-goal을 통해 목표 위치 지정하면 로봇 이동
```
$ roslaunch kw_tf navigation.launch
```
![navigation_render](https://github.com/Choi0914/SLAM_Navigation/assets/121415776/8348bdd9-c86c-4bce-b84d-312c590fa00b)

