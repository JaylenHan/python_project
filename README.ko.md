<div align="center">

# 🌽 강냉이의 학교정복기

**대학 캠퍼스를 배경으로 한 2D 턴제 RPG — Python + Tkinter + Pygame으로 처음부터 직접 개발.**

[![Language](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![GUI](https://img.shields.io/badge/GUI-Tkinter-FFD43B?logo=python&logoColor=black)](https://docs.python.org/3/library/tkinter.html)
[![Audio](https://img.shields.io/badge/Audio-Pygame-000000?logo=pygame)](https://www.pygame.org/)
[![Award](https://img.shields.io/badge/🏆_강남대-우수작품_선정-success)](https://sae.kangnam.ac.kr)

🇺🇸 [English README](./README.md) · 📚 [문서](./docs) · ▶️ [시연 영상](https://youtu.be/bvAGlPi2S08)

</div>

> ℹ️ **미러 저장소.** 이 레포는 원본 **[`python-project`](https://github.com/JaylenHan/python-project)**
> (2023.12 최종 제출본)의 미러입니다. 게임 코드(`Kangnam_University.py`)는 동일합니다.
> 공식 원본과 히스토리는 canonical 레포를 참고하세요.

---

## 소개

**「강냉이의 학교정복기」** 는 강남대학교 ICT융합공학부(가상현실전공) **파이썬응용 기말고사 프로젝트**로 개발한
2D 턴제 RPG입니다. *포켓몬*과 *메이플스토리* 같은 인기 RPG의 모험·성장 요소를 도입하고, 실제 대학교
생활을 모티브로 삼아 친근하고 몰입감 있는 게임 환경을 구현했습니다. 네 명의 학우 캐릭터 중 하나를 골라
캠퍼스를 탐험하고, 점점 강해지는 세 보스(학생회 → 교수님 → 총장님)를 격파하며, 미니게임으로 코인을 벌어
상점에서 아이템을 구매합니다.

본 프로젝트는 학부 **우수작품으로 선정**되었습니다.

> 4인 팀("지민아 뭐라도 좀 해봐")이 약 2,100줄 단일 Python 모듈로 완성했으며,
> 렌더링은 표준 `tkinter` 캔버스만, 오디오는 `pygame.mixer`만 사용했습니다.

## 핵심 특징

- 🎮 **플레이어블 캐릭터 4종** — 각기 다른 능력치(HP / 공격력 / 게이지)와 전용 아트
- ⚔️ **턴제 전투 시스템** — 기본 공격, 게이지 충전형 특수 스킬, 아이템, 도망
- 👹 **점층형 보스전 3종** — 전/후 대화 분기(승리·패배 경로) 포함
- 🕹️ **내장 미니게임 3종** — 코인 파밍용 (과녁 맞히기 · 팩맨 · 학점 게임)
- 🛒 **상점 & 아이템 경제** — 벌어들인 코인으로 HP/MP/에너지 물약·능력 강화 구매
- 🗺️ **격자 기반 맵 탐험** — 캠퍼스 7개 지역, 상호작용 칸과 랜덤 상자
- 🔊 **풀 오디오** — 지역별 루프 BGM, 보스 전용 테마, 공격 효과음 (`pygame.mixer`)
- 📖 **스토리 모드** — 6컷 인트로 만화와 대화 시스템 기반 캠페인

## 기술 스택

| 분류 | 도구 |
|---|---|
| 언어 | Python 3.x |
| 렌더링 / UI | `tkinter` (Canvas, Toplevel, 위젯) |
| 오디오 | `pygame.mixer` (채널 + `Sound`) |
| 표준 라이브러리 | `time`, `random` |
| 협업/도구 | Visual Studio Code, GitHub, Notion, Discord, Google Drive |

## 한눈에 보는 게임플레이

### 플레이어 캐릭터

| 캐릭터 | HP | 공격력 | 게이지 | 특징 |
|---|---:|---:|---:|---|
| King 승헌 | 200 | 20 | 2 | 탱커형 리더 |
| Clown 지민 | 150 | 30 | 2 | 글래스 캐넌 |
| Baby 민서 | 170 | 25 | 2 | 밸런스형 |
| Oldest 병찬 | 100 | 50 | 2 | 고위험·고화력 |

### 보스 (순서대로)

| 보스 | HP | 공격력 범위 |
|---|---:|---|
| 학생회 | 300 | 10–15 |
| 교수님 | 600 | 15–20 |
| 총장님 | 1,200 | 20–30 |

### 미니게임

| 인게임 명칭 | 클래스 | 제작 | 메커니즘 |
|---|---|---|---|
| 과녁 맞히기 | `Targetgame` | 민서 | 제한시간 내 표적 명중 |
| 팩맨 / "King-man" | `PackMan` | 승헌 | 팩맨식 추격, 아이템·코인 획득 |
| 대학 학점 먹기 | `CollegeGame` | 지민 | 학점·코인 수집 |

전체 설계는 [docs/02-gameplay/GAME_DESIGN.md](./docs/02-gameplay/GAME_DESIGN.md) 참고.

## 시작하기

> ⚠️ **주의:** 게임 코드가 모든 에셋을 **파일명만으로**(예: `PhotoImage(file="start_screen.png")`) 불러오는데,
> 이 레포의 에셋은 하위 폴더로 정리돼 있습니다. 실행 전 에셋을 작업 디렉토리로 모아야 합니다.

```bash
# 1. 유일한 외부 의존성 설치
pip install pygame

# 2. 에셋을 스크립트 옆으로 모으기 (에셋은 하위 폴더에 보관돼 있음)
#    macOS / Linux:
cp Character_Image/* Map_Etc_Image/* Skill_Image/* Sound/* .

# 3. 실행
python Kangnam_University.py
```

전체 설치·트러블슈팅·에셋 경로 설명: [docs/03-guides/GETTING_STARTED.md](./docs/03-guides/GETTING_STARTED.md).

## 프로젝트 구조

```
python_project/
├── Kangnam_University.py   # 게임 전체 (~2,100줄, 단일 모듈)
├── Character_Image/        # 42개 — 플레이어 4 + 보스 3 (대기/이동/전투/대화/스킬)
├── Map_Etc_Image/          # 44개 — 맵, UI, 커서, 스토리 컷, 이벤트
├── Skill_Image/            # 16개 — 스킬·공격 모션 프레임
├── Sound/                  # 10개 — BGM, 보스 테마, 공격 효과음 (.ogg)
└── docs/                   # 프로젝트 문서 (본 세트)
```

코드는 단일 모듈이며 다섯 클래스(`GameCharacter`, `Targetgame`, `PackMan`, `CollegeGame`, `Store`)와
전역 상태로 구동되는 게임 흐름 함수들로 구성됩니다. 상세:
[docs/01-architecture/SYSTEM_ARCHITECTURE.md](./docs/01-architecture/SYSTEM_ARCHITECTURE.md).

## 문서

| 문서 | 내용 |
|---|---|
| [00 · 프로젝트 개요](./docs/00-overview/PROJECT_BRIEF.md) | 목표, 팀, 역할, 성과, 범위 |
| [01 · 시스템 아키텍처](./docs/01-architecture/SYSTEM_ARCHITECTURE.md) | 모듈 구성, 클래스, 상태 모델, 렌더/오디오 루프 |
| [02 · 게임 디자인](./docs/02-gameplay/GAME_DESIGN.md) | 캐릭터, 보스, 맵, 전투, 미니게임, 상점 |
| [03 · 시작 가이드](./docs/03-guides/GETTING_STARTED.md) | 설치, 에셋 준비, 실행, 트러블슈팅 |
| [04 · 회고 & 로드맵](./docs/04-devlog/RETROSPECTIVE.md) | 깨달은 점, 한계, 향후 방향 |

## 로드맵

개발 중 정리한 향후 방향성(미구현):

- 캐릭터 커스터마이징(헤어·의상·액세서리)
- 미니게임·상점 아이템 다양화
- 멀티플레이어 협동/경쟁 전투
- 스토리·퀘스트 라인 확장

## 크레딧

**팀 "지민아 뭐라도 좀 해봐"** — 강남대학교 파이썬응용 기말고사 프로젝트.

**한승헌 (Jaylen Han)** — 팀장 · 기획 · 메인 및 미니게임 개발 · 최적화 · 발표.

- 🏆 ICT융합공학부(가상현실전공) 파이썬응용 **우수작품 선정**
- ▶️ [최종 시연 영상](https://youtu.be/bvAGlPi2S08)
- 📦 원본 레포: [`python-project`](https://github.com/JaylenHan/python-project)

## 라이선스

교육용 프로젝트. 현재 별도 라이선스가 부착돼 있지 않으며, 재사용 전 작성자에게 문의 바랍니다.
