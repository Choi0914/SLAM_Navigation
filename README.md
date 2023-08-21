# 2D_LiDAR_SLAM_Navigation
---
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

![lidar_3D](https://github.com/Choi0914/2D_LiDAR_SLAM-Navigation/assets/121415776/9494a8a1-4ed5-432f-856d-32e60e92e2dc)

- 3D Lidar -> 2D Lidar 전환
```
$ roslaunch pointcloud_to_laserscan sample_node.launch
```
![convert_to_lidar2D](https://github.com/Choi0914/2D_LiDAR_SLAM-Navigation/assets/121415776/e2ffec72-8c93-497c-9d78-267609a3df6b)

### 2. SLAM
- SLAM 시작
```
$ roslaunch gmapping slam_gmapping.launch
```
![gmappig_render](https://github.com/Choi0914/2D_LiDAR_SLAM-Navigation/assets/121415776/94fda1e6-d1de-4ebe-ae09-bea63cf01cb0)
- SLAM 종료
```
$ rosrun map_server map_saver
```
- 완성된 map
![map2](https://github.com/Choi0914/2D_LiDAR_SLAM-Navigation/assets/121415776/3178eccb-14c9-460a-9c37-dc69fbb58d18)

### 3. Navigation
```
$ roslaunch kw_tf navigation.launch
```
![navigation_render](https://github.com/Choi0914/2D_LiDAR_SLAM-Navigation/assets/121415776/772eb254-17d0-4b82-87dd-43e16565fb1b)