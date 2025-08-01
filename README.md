# 디지털 트윈 기반 turtlebot3 오토 레이스

가상-실제 환경 연동 TurtleBot3 자율주행 시스템

---

## 📌 프로젝트 개요

- 자율주행 기술의 테스트와 평가를 목적으로, 운전면허 기능시험 코스를 디지털 트윈 환경(Gazebo)으로 구축하고 TurtleBot3를 활용해 다양한 실제 시나리오(곡선 주행, 급정거, 신호등 반응, 주차 등)를 자동 주행하는 시스템을 개발
- GUI를 통한 속도(PID제어)와 현재 위치 확인가능
- 로봇팔 Pick & Place 기능 추가

---

## 📦 주요 기능

- **디지털 트윈**: Gazebo 내 운전면허 기능시험장을 정밀 재현 (방지턱, 주차구간, 교차로 등)
- **Lane Detection**:
    - Hybrid 방식 (HSV 마스킹 + Canny + Kalman Filter + Sliding Window)
    - HoughLines + Polyfit로 곡선/직선 판단, 차선 중심 위치 예측
- **신호등/표지판 인식**:
    - HSV 기반 컬러 마스킹
    - Hough알고리즘을 통한 라인 인식
    - 신뢰도 누적 기반의 상태 추론 로직 구현
- **GUI 개발**:
    - 속도 제어, 실시간 카메라 화면, 미니맵, 로봇 위치 추적 기능 포함
- **PID 제어기 구현**:
    - 각속도 제어
- **Pick & Place**:
    - ArUco 마커 인식 기반 4축 로봇팔 제어

---

## 🛠️ 사용 기술 및 라이브러리

- TurtleBot3

- ROS2 Humble

- Gazebo

- OpenCV

- PID 제어

- RViz
---

## 🎬 시연 영상

> 📺 [시연 영상 링크 ](https://www.youtube.com/watch?v=lTQ8aKC-O8E&ab_channel=%EC%A0%95%EC%9E%AC%EC%A2%85)


## 💡 주요 성과 및 깨달은 점

- 4축 로봇팔의 역기구학 문제와 정확도 제한을 고려해 우선순위를 조절하고, 실현 가능한 기능으로 시스템을 조정하는 시스템 안정화 설계의 중요성을 깨달음
- 단순한 라인 감지(색상 기반, 직선 검출 등)만으로는 빛 반사나 영상 노이즈로 인해 오류가 쉽게 발생한다는 점을 직접 경험하며, 정확한 알고리즘 설계와 정밀한 파라미터 튜닝의 중요성을 깨달음.
- 또한 이미지 전처리 과정에서 빛 반사나 조명 변화에 RGB 색공간은 매우 취약하다는 점을 직접 경험하며, 이를 보완하기 위해 HSV 색공간을 활용하는 것이 훨씬 더 효과적이라는 것을 깨달음.
- Hue(색상) 성분을 중심으로 마스킹할 경우 조도 변화에 덜 민감하여 더 안정적인 라인 감지가 가능했습니다.

---

## 👥 팀 소개

> **TEAM 4 – 테크놀로지아**
> 정재종(팀장), 김재권, 제민수, 조주안   
> 멘토: 김루진 멘토님

---

