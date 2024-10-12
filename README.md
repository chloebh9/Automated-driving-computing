---

project_overview: |
  이 프로젝트는 두 가지 대표적인 강화 학습 알고리즘인 SARSA와 Q-Learning의 성능을 비교합니다. 
  이 알고리즘들은 다음 두 가지 격자(grid) 환경에서 테스트되었습니다:

  - 빈 격자(Empty Grid): 장애물이 없는 간단한 환경.
  - Lava Gap Grid: 에이전트가 피해야 하는 위험 요소인 라바가 포함된 격자 환경.

  이 프로젝트는 이 두 알고리즘이 어떻게 격자 환경에서 경로를 학습하는지, 그리고 에피소드 수에 따른 경로 최적화 및 수렴 속도를 비교합니다.


---

## 포함된 파일

- **`main.py`**: SARSA와 Q-Learning 알고리즘을 실행하고 결과를 출력하는 메인 스크립트.
- **`environments.py`**: Empty Grid와 Lava Gap Grid 환경을 정의한 파일.
- **`sarsa.py`**: SARSA 알고리즘의 구현 파일.
- **`qlearning.py`**: Q-Learning 알고리즘의 구현 파일.
- **`results/`**: SARSA와 Q-Learning의 성능 비교 결과 그래프가 저장된 폴더.
- **`requirements.txt`**: 프로젝트 실행에 필요한 파이썬 라이브러리 목록.

---

## 설치 및 실행 방법

### 저장소 클론:
```bash
git clone https://github.com/your-repo/reinforcement-learning-sarsa-qlearning.git
cd reinforcement-learning-sarsa-qlearning
```

### 가상 환경 생성 (선택 사항):
```bash
python -m venv rl-env
source rl-env/bin/activate  # Windows에서는 `rl-env\Scripts\activate` 사용
```

### 필수 패키지 설치:
```bash
pip install -r requirements.txt
```

### 메인 스크립트 실행:
```bash
python main.py
```

---

## 프로젝트 상세 내용

이 프로젝트는 **SARSA**와 **Q-Learning**을 사용하여 두 가지 다른 격자 기반 경로 탐색 문제를 해결합니다. 알고리즘 간의 주요 차이점은 **학습 방식**에서 나타납니다:

### SARSA (State-Action-Reward-State-Action):
- **On-policy**: 에이전트는 현재 정책에 따라 행동하고 그 결과를 기반으로 Q 값을 업데이트합니다.
- 더 **보수적인 학습 경향**이 있어 **안전한 경로**를 우선적으로 선택하며 **위험을 회피**합니다.
- **보상**보다 **위험 회피**가 중요한 상황에서 더 효과적일 수 있습니다.

### Q-Learning:
- **Off-policy**: 에이전트는 실제 행동과 상관없이 **최적 행동**을 찾아 Q 값을 업데이트합니다.
- 더 **탐험적인 학습**을 통해 **빠르게 최적 경로**를 찾으며, **위험을 감수**하면서 더 나은 보상을 찾습니다.
- **위험이 적고** 빠른 경로 최적화가 필요한 상황에서 효과적입니다.

---

## 결과 요약

### 빈 격자:
- **Q-Learning**이 더 빠르게 최적 경로를 찾으며, **SARSA**는 더 많은 에피소드가 필요했으나 안전한 경로를 선택함.

### Lava Gap Grid:
- **Q-Learning**은 위험을 감수하며 빠르게 최적 경로를 학습했으나 초기에는 손실이 컸음.
- **SARSA**는 위험 회피에 더 중점을 두어 더 많은 에피소드가 필요했지만, 안전한 경로를 먼저 찾음.

---

## 그래프 해석 방법

- **Y축**: 누적 평균 보상.
- **X축**: 에피소드 수.
- **SARSA (주황색)**: 안전한 경로를 선택하여 보상을 안정적으로 유지하지만, 초기 탐험이 느림.
- **Q-Learning (파란색)**: 탐험적 경로로 최적 경로를 빠르게 찾음.

---
