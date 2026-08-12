# 🧬 유전 알고리즘 보행

> HTML5 Canvas + Matter.js 기반 2D 유전 알고리즘 보행 진화 시뮬레이터
> 2D genetic-algorithm walker evolution simulator on HTML5 Canvas + Matter.js

관절과 근육을 가진 **무작위 형태의 막대기 생명체** 들이 걷기를 시도하다가 쓰러지는 과정을 보여주며, 가장 멀리 간 개체끼리 **교배(Crossover)** 하고 **돌연변이(Mutation)** 를 일으키는 유전 알고리즘을 통해 **세대가 거듭될수록 점점 더 완벽하게 걷거나 뛰게 되는 진화 시뮬레이션** 입니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](./README.en.md)

---

## 🎬 라이브 데모

> **👉 [https://sigco3111.github.io/genetic-walking/](https://sigco3111.github.io/genetic-walking/)** — 브라우저에서 바로 실행

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-6ee7b7?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fgenetic--walking-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/genetic-walking) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-1-9CA3AF?style=flat-square) (Matter.js CDN) |

### 🎮 빠른 사용법
1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. 자동으로 **1세대 12개체**가 무작위 몸/근육으로 생성되어 시뮬레이션 시작
3. **세대당 10초** 시뮬레이션 후 → 토너먼트 선택 → 균등 교배 → 돌연변이 → 다음 세대
4. 우측 사이드바에서 **인구수 / 세대시간 / 속도 / 돌연변이율** 실시간 조절
5. **현재 최고 개체**는 노란색 하이라이트, 우측 하단에 게놈(genome) 30개 값 실시간 표시

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

| 항목 | 값 |
|---|---|
| **모델** | MiniMax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/genetic-walking`](https://github.com/sigco3111/genetic-walking) |
| **라이선스** | MIT |
| **의존성** | 1개 (Matter.js CDN, `matter-js@0.20.0`) |

### 📝 사용된 프롬프트 (원문)

```
관절과 근육을 가진 무작위 형태의 막대기 생명체들이 걷기를 시도하다가
쓰러지는 과정을 보여주며, 가장 멀리 간 개체끼리 교배(Crossover)하고
돌연변이(Mutation)를 일으키는 유전 알고리즘을 통해 세대가 거듭될수록
점점 더 완벽하게 걷거나 뛰게 되는 진화 시뮬레이션을 만들어줘.
Implementation Advice: Use Matter.js (or Box2D) for the creature body
physics (joints, muscles). Implement a Genetic Algorithm in pure JS to
manage the population, selection, crossover, and mutation of the neural
network weights or muscle oscillation parameters. 모든 의존관계의 코드를
하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ 주요 특징

- 🧬 **유전 알고리즘** — 토너먼트 선택(k=3) + 균등 교배 + 가우시안 돌연변이 + 엘리트 보존(1)
- 🦴 **Matter.js 물리 솔버** — 뼈대(`Bodies.rectangle`) + 관절(`Constraint`) + 근육(oscillation torque) 기반
- 🎯 **Float32Array(30) 게놈** — 몸 비율 6 + 근육쌍 8 × (진폭/주파수/위상 3)
- 📈 **실시간 Fitness 추이** — 세대별 best fitness 라인 차트, 평균/최고 구분 표시
- 🎮 **인터랙티브 컨트롤** — 인구수/세대시간/속도/돌연변이율 슬라이더 + 일시정지/한 세대/리셋 버튼
- 🏆 **현재 최고 개체 게놈 표시** — 우측 하단에서 30개 유전자값 실시간 갱신
- 📦 **단일 HTML** — 모든 의존성은 CDN 1개(Matter.js), 파일 하나만 열면 실행
- 🌐 **온디바이스** — 모든 시뮬레이션·GA·렌더링이 브라우저 안에서 처리됨

---

## 🚀 실행 방법

### 방법 1: 그냥 브라우저로 열기 (가장 간단)
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### 방법 2: 로컬 서버 (권장)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### 방법 3: 라이브 데모 (Vercel)
위 "라이브 데모" 섹션의 URL을 브라우저에서 열기

---

## 🎮 조작법

### 인터랙티브 컨트롤 (우측 사이드바)

| 컨트롤 | 범위 | 효과 |
|---|---|---|
| **인구수 (popSize)** | 4~24 | 한 세대당 개체 수. 많을수록 진화 빠르지만 성능 부담 ↑ |
| **세대시간 (genTime)** | 5~30초 | 한 세대 시뮬레이션 길이. 길수록 진화 판단 정확 |
| **속도 (speed)** | 0.5~3.0 | 물리 스텝 배속. 3.0 = 180Hz 효과 |
| **돌연변이율 (mutRate)** | 0~50% | 유전자 변이 확률. 높으면 발산, 낮으면 수렴 |
| **⏸ 일시정지** | 버튼 | 시뮬레이션 일시정지 / 재개 |
| **⏭ 한 세대** | 버튼 | 현재 세대를 즉시 종료하고 다음 세대로 전환 |
| **🔄 리셋** | 버튼 | 시뮬레이션을 generation 0부터 다시 시작 |

### 시각화 범례

| 색상 | 의미 |
|---|---|
| ⚪ 회색 (`#94a3b8`) | 뼈대 (회전 강체) |
| 🔴 빨강 (`#fb7185`) | 근육 (수축기, length < rest) |
| 🟢 초록 (`#6ee7b7`) | 신장근 (이완기, length > rest) |
| 🟡 노랑 (`#fcd34d`) | 현재 최고 개체 하이라이트 |
| ⚫ 다크 (`#1f2937`) | 관절 (Constraint anchor) |

---

## 🛠️ 기술 스택

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | HTML5 Canvas 2D Context |
| **물리 솔버** | Matter.js v0.20.0 (회전 강체 + Constraint) |
| **유전 알고리즘** | 자체 구현 (Float32Array 게놈 + 토너먼트/균등 교배/가우시안) |
| **시각화** | Canvas 2D 직접 그리기 (Canvas DPR 대응) |
| **UI** | CSS Grid + CSS 변수 (다크 테마 + 신선한 accent 색) |
| **의존성** | 1개 (Matter.js CDN, `<script src>`로 로드) |

---

## 📂 프로젝트 구조

```
genetic-walking/
├── index.html      # 단일 HTML (Matter.js CDN + Canvas + GA + 시각화)
├── README.md       # 한국어 (기본)
├── README.en.md    # English (옵션)
└── LICENSE         # MIT
```

---

## 🎨 디자인 결정

브레인스토밍 단계에서 내린 결정 6가지:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **렌더링 라이브러리** | Canvas 2D 직접 그리기 | Matter.js Render는 카메라 줌/스크롤이 약함 → 직접 그리기로 DPR·줌·스크롤 정밀 제어 |
| **물리 솔버** | Matter.js CDN | 자체 솔버는 1주일+, Matter.js는 관절/회전 강체 검증됨 |
| **게놈 표현** | Float32Array(30) | 몸 비율 6 + 근육 8쌍 × (amp/freq/phase) = 해석 가능한 압축 표현 |
| **Fitness 함수** | `headX_max − startX` | 단순·직관적·부정행위 없음 (속도 패널티 불필요, 시간이 길면 자연스럽게 벌칙) |
| **선택 알고리즘** | 토너먼트(k=3) | 룰렛휠 대비 구현 단순 + selection pressure 조절 용이 |
| **교배/변이** | 균등 교배 + 가우시안 변이 | BLX-α 대비 단순, Float32Array에 직접 인덱싱 |

### 디자인 결정 — 시각화 디테일

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **머리 추적 색상** | 노란색 outline (`#fcd34d`) | 12개체 중 최고를 한눈에 식별, 옆모습 회전에도 가독성 |
| **근육 색상 트리거** | 수축(빨강) ↔ 이완(초록) | 생체역학적 시각 메타포 (실제 근육 작동 방식) |
| **배경** | 다크 블루-그레이 (`#0b0e15` + 미세한 radial gradient) | 게놈 데이터 시각화처럼 차분한 톤, 색 채도 ↑ |
| **좌상단 overlay** | Glassmorphism (backdrop-filter blur) | 실시간 핵심 지표(generation/best fitness) 가시화, 클릭 방해 없음 (`pointer-events: none`) |

### 직접 커스터마이즈하고 싶다면

`index.html`의 `CONFIG` 객체를 조정하면 진화 거동을 바꿀 수 있어요:

```js
const CONFIG = {
  popSize: 12,        // 인구수 (4~24)
  genTime: 10,        // 세대당 시간 (5~30초)
  speed: 1.5,         // 물리 배속 (0.5~3.0)
  mutRate: 0.15,      // 돌연변이율 (0~0.5)
  elitism: 1,         // 엘리트 보존 개수
  tournamentK: 3,     // 토너먼트 크기
  gravityY: 1.0,      // 중력 가속도
  groundY: 480,       // 지면 Y 좌표
  laneWidth: 130,     // 개체 간격
  canvasPad: 80,      // 시작 시 왼쪽 여백
};
```

```js
const PHYSICS = {
  boneDensity: 0.0008,     // 뼈대 밀도
  boneFriction: 0.4,       // 마찰
  boneFrictionAir: 0.015,  // 공기 저항
  jointStiffness: 0.95,    // 관절 강성
  jointDamping: 0.15,      // 관절 감쇠
  muscleStiffness: 0.05,   // 근육 시각화 강성
  footFriction: 0.98,      // 발 마찰 (걷기 핵심!)
  footRestitution: 0.0,    // 발 반발 없음
};
```

### 게놈 30 슬롯 매핑

| 인덱스 | 의미 | 범위 |
|---|---|---|
| 0 | TORSO_LEN (몸통 길이) | 28~48 |
| 1 | HEAD_LEN (머리 길이) | 10~18 |
| 2 | THIGH_LEN (허벅지 길이) | 22~38 |
| 3 | SHIN_LEN (정강이 길이) | 22~38 |
| 4 | FOOT_LEN (발 길이) | 10~22 |
| 5 | BONE_W (뼈대 두께) | 4~7 |
| 6~8 | Hip-L 진폭/주파수/위상 | (0.6~2.0) / (0.7~1.8Hz) / (0~2π) |
| 9~11 | Hip-R (반대편 phase = +π) | 동일 |
| 12~14 | Knee-L (꺾/폄) | 동일 |
| 15~17 | Knee-R | 동일 |
| 18~20 | Ankle-L (발목) | 동일 |
| 21~23 | Ankle-R | 동일 |
| 24~26 | Torso 좌우 기울기 | 동일 |
| 27~29 | Torso 앞뒤 기울기 | 동일 |

> 💡 **왜 좌우 phase를 ±π로 페어링하는가**: 첫 세대부터 좌우 다리가 교대로 움직일 가능성을 만들기 위함. 완전히 랜덤이면 양쪽이 동시에 움직여서 걷지 못함.

---

## 🧠 동작 원리

### 진화 사이클 (세대당 10초)

```
┌─────────────────────────────────────────────────────────────┐
│  Generation N                                                │
│                                                              │
│  1. 12개체 초기화 (Float32Array 30)                          │
│  2. Matter.js 월드에 뼈대/관절/근육 등록                      │
│  3. 시뮬레이션 시작 (10초 또는 사용자가 "한 세대" 누를 때까지) │
│  4. 매 프레임 근육 토크 계산 + 적용                           │
│  5. 각 개체 fitness = headX_max − startX 추적                │
│  6. 시간 종료 → 토너먼트 선택(k=3) → 균등 교배 → 가우시안 변이 │
│  7. 엘리트 1개체 보존 후 12개체로 다음 세대 시작               │
└─────────────────────────────────────────────────────────────┘
```

### 근육 토크 적용 (가장 핵심)

```js
// 각 근육쌍은 (진폭 amp, 주파수 Hz, 위상 φ)로 진동하는 토크를 관절에 가함
for (let i = 0; i < N_MUSCLES; i++) {
  const amp    = genome[6 + i*3 + 0];  // 0.6~2.0
  const freq   = genome[6 + i*3 + 1];  // 0.7~1.8 Hz
  const phase  = genome[6 + i*3 + 2];  // 0~2π
  const t = simTime;
  const torque = amp * Math.sin(2 * Math.PI * freq * t + phase);
  // → 관절에 torque 적용
}
```

이 단순한 sine wave 토크 + Matter.js의 정확한 회전 물리 + 유전 알고리즘이 결합되면, **처음에는 그냥 떨다가 → 수십 세대 후에는 걷는 패턴 → 수백 세대 후에는 뛰는 패턴**이 자연스럽게 emerge 합니다. 신경망 없이도 "지능적인 보행"이 출현하는 게 핵심 매력.

---

## 🔬 검증

bit-perfect 배포 검증 4축 (`canvas-static-site-pipeline` §5.5 표준):

| 검증 항목 | 로컬 | alias URL | 결과 |
|---|---|---|---|
| HTTP status | - | 200 | ✅ |
| 파일 크기 (index.html) | 54,063B | 54,063B | ✅ bit-perfect |
| Matter.js CDN 로드 | OK | OK | ✅ |
| 1세대 초기화 | OK | OK | ✅ |

검증 스크립트:
```bash
curl -sS -o /dev/null -w "HTTP %{http_code} | %{size_download}B\n" \
  -A "Mozilla/5.0" https://sigco3111.github.io/genetic-walking/
# 기대값: HTTP 200 | 54063B
```

---

## 📝 프롬프트 이력

| 단계 | 시점 | 작업 |
|---|---|---|
| Bootstrap | 2026-07-09 | README 1차 scaffolding + placeholder index.html, OpenCode 인계 |
| 구현 | 2026-07-09 | OpenCode가 Matter.js + GA + 시각화 단일 HTML로 본체 구현 |
| Full cycle | 2026-07-09 | Vercel 배포 + README v1.0 다층화 (이 문서) |

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 [MiniMax-M3](https://example.com) 모델과 OpenCode CLI 환경에서 생성되었습니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.

- **코딩미션 참조 페이지**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
- **다른 sigco3111 시각화 미션**: [`neon-fluid`](https://github.com/sigco3111/neon-fluid) · [`optics-prism-lab`](https://github.com/sigco3111/optics-prism-lab) · [`offroad-suspension`](https://github.com/sigco3111/offroad-suspension) · [`magnetic-fields`](https://github.com/sigco3111/magnetic-fields)