# 🧬 유전 알고리즘 보행

> HTML5 Canvas + Matter.js 기반 2D 유전 알고리즘 보행 진화 시뮬레이터
> 2D genetic-algorithm walker evolution simulator on HTML5 Canvas + Matter.js

관절과 근육을 가진 **무작위 형태의 막대기 생명체** 들이 걷기를 시도하다가 쓰러지는 과정을 보여주며, 가장 멀리 간 개체끼리 **교배(Crossover)** 하고 **돌연변이(Mutation)** 를 일으키는 유전 알고리즘을 통해 **세대가 거듭될수록 점점 더 완벽하게 걷거나 뛰게 되는 진화 시뮬레이션** 입니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](./README.en.md)

---

## 🧬 라이브 데모

> 🚧 **배포 후 활성화 예정** — Vercel alias URL이 발급되면 이 줄이 라이브 데모로 교체됩니다.

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**됩니다.

| 항목 | 값 |
|---|---|
| **모델** | MiniMax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/genetic-walking`](https://github.com/sigco3111/genetic-walking) |
| **라이선스** | MIT |
| **의존성** | 0~2개 (Matter.js + poly-decomp CDN 가능, 또는 자체 솔버) |

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

## 🚧 Status

코딩미션 진행 단계 — 1차 작업은 저장소 bootstrap + OpenCode에게 작업 자리 인계까지.

- [x] 저장소 생성 + README 1차 커밋 (현재 단계)
- [ ] OpenCode가 `index.html` 본체 구현 (Matter.js 솔버 + 유전 알고리즘 + 진화 시각화)
- [ ] Vercel 배포 + 라이브 데모 URL 발급
- [ ] README 다층화 v1.0 (Live Demo URL + Design Choices + Config 표 + 세대별 fitness 추이)

---

## 🚀 실행 방법 (예정)

```bash
# 옵션 A: 브라우저에서 직접 열기
open index.html

# 옵션 B: 로컬 정적 서버 (권장)
python3 -m http.server 8000
# → http://localhost:8000 접속

# 옵션 C: Vercel 라이브 데모 (배포 후 활성화)
# 위 "라이브 데모" 섹션의 URL을 브라우저에서 열기
```

> **참고**: 모든 의존관계가 `index.html` 하나에 인라인됩니다. Matter.js + poly-decomp CDN을 쓰는 경우도 HTML에 `<script src>` 로만 포함되며, 자체 솔버를 쓸 경우 완전한 단일 HTML이 됩니다.

---

## 🧠 구현 힌트

Implementation Advice가 권장하는 핵심 설계:

- **신체 (Physics Body)** — Matter.js `Bodies.rectangle` (각 뼈대) + `Constraint` (관절) + 근육은 진폭/주기를 가지는 spring/constraint oscillation
- **유전 알고리즘 (GA)** — `Float32Array` 게놈 (근육 파라미터 + 신경망 가중치) + Tournament Selection + Uniform Crossover + Gaussian Mutation
- **시각화** — `Matter.Render` 또는 Canvas 2D 직접 그리기, 세대별 best fitness line chart
- **자가 적응** — fitness = `headX - startX` (오른쪽으로 얼마나 멀리 갔나), 일정 generation 후 명확한 보행 패턴 등장

> **판단 기준**: 본 미션은 `optics-prism-lab` / `offroad-suspension`의 Matter.js 패턴을 차용 가능 (`Bodies.fromVertices` + `Constraint` + `poly-decomp`). 하지만 Offroad의 차량 모델보다 자유도가 훨씬 높으므로 `Bodies.rectangle` + `Constraint` 만으로 충분할 가능성 큼 → CDN 2개 또는 1개.

---

## 🤖 생성 워크플로

이 저장소는 동일한 sigco3111 코딩미션 패턴으로 작업됩니다:

1. **1차 (현재)** — README + placeholder `index.html` + `.gitignore` 생성, OpenCode 인계
2. **OpenCode가 본체 구현** — `index.html`에 Matter.js 솔버 + GA 루프 + 진화 시각화 모두 인라인
3. **Vercel 배포 + README 다층화** — `offroad-suspension` / `optics-prism-lab` / `heat-conduction-heatmap` 등의 다층 README 형식으로 v1.0 완성

다른 미션 사례: [`optics-prism-lab`](https://github.com/sigco3111/optics-prism-lab) · [`offroad-suspension`](https://github.com/sigco3111/offroad-suspension) · [`heat-conduction-heatmap`](https://github.com/sigco3111/heat-conduction-heatmap) · [`neon-fluid`](https://github.com/sigco3111/neon-fluid)

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 [MiniMax-M3](https://example.com) 모델과 OpenCode CLI 환경에서 생성됩니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행합니다.

- **코딩미션 참조 페이지**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
