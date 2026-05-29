# 시작 가이드 (Getting Started)

## 요구 사항

- Python 3.x (`tkinter` 포함된 표준 배포판)
- `pygame` (오디오 재생용 — 유일한 외부 의존성)

```bash
pip install pygame
```

> macOS에서 `tkinter`가 없다고 나오면 python.org 공식 배포판을 설치하거나
> `brew install python-tk` 를 사용한다.

## ⚠️ 에셋 경로 이슈 (반드시 읽기)

이 프로젝트의 코드는 모든 에셋을 **파일명만으로** 불러온다. 예:

```python
start_img = tkinter.PhotoImage(file="start_screen.png")
```

경로를 다루는 코드(`os`, `os.path`, `__file__`, `chdir` 등)가 **전혀 없다**. 즉, 코드는 모든
이미지/사운드가 **현재 작업 디렉토리(CWD)** 에 평평하게 존재한다고 가정한다.

그러나 이 레포에서는 가독성을 위해 에셋을 하위 폴더로 정리해 두었다:

```
Character_Image/  Map_Etc_Image/  Skill_Image/  Sound/
```

따라서 **그대로 실행하면 `_tkinter.TclError: couldn't open "start_screen.png"` 류의 에러**가 난다.
실행하려면 에셋을 작업 디렉토리로 모아야 한다.

## 실행 방법

### 방법 A — 에셋을 루트로 복사 후 실행 (권장)

```bash
cd python_project

# 모든 에셋을 현재 디렉토리로 복사
cp Character_Image/* Map_Etc_Image/* Skill_Image/* Sound/* .

python Kangnam_University.py
```

> 작업 디렉토리를 더럽히고 싶지 않다면, 복사본을 임시 폴더에 만들어 거기서 실행한다:
> ```bash
> mkdir -p /tmp/kangnam_run && cp Kangnam_University.py Character_Image/* \
>   Map_Etc_Image/* Skill_Image/* Sound/* /tmp/kangnam_run/
> cd /tmp/kangnam_run && python Kangnam_University.py
> ```

### 방법 B — 심볼릭 링크 (디스크 절약)

```bash
cd python_project
for d in Character_Image Map_Etc_Image Skill_Image Sound; do ln -sf "$d"/* .; done
python Kangnam_University.py
```

## 조작

- 시작 화면에서 **게임시작** 버튼 → 인트로 만화 → 캐릭터 선택
- 캐릭터 선택: 원하는 캐릭터 이미지를 클릭
- 맵 이동 및 상호작용: 키보드(이동) / `space`(상호작용·전투 진입)
- 대화 진행: `z`(대화 다음)
- 전투: 화면의 스킬/아이템 위에 커서를 올려 선택

> 정확한 키 매핑은 입력 핸들러(`key_press`/`mouse_click` 등)와 각 전투 함수의 `root.bind`를 참고.
> 데모 영상에서 실제 플레이 흐름을 확인할 수 있다: https://youtu.be/bvAGlPi2S08

## 트러블슈팅

| 증상 | 원인 | 해결 |
|---|---|---|
| `couldn't open "*.png"` | 에셋이 CWD에 없음 | 위 "에셋 경로 이슈"대로 에셋을 루트로 모은다 |
| 소리가 안 남 | `pygame` 미설치 / 오디오 장치 | `pip install pygame`, 시스템 오디오 확인 |
| `No module named tkinter` | tkinter 미포함 배포판 | python.org 배포판 또는 `brew install python-tk` |
| 창이 바로 닫힘 | 에셋 누락으로 로드 중 예외 | 터미널 에러 로그 확인 후 누락 파일 보강 |

## 관련 문서

- [프로젝트 개요](../00-overview/PROJECT_BRIEF.md)
- [게임 디자인](../02-gameplay/GAME_DESIGN.md)
