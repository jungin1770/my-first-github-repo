# Git 8시간 실습 과정 - 강사용 완전 스크립트

> **본 문서 사용 안내**
> - 본 스크립트는 강사가 **단독으로 진행**할 수 있는 완전판입니다 (실습/미니과제 모두 포함)
> - 💬 표시는 실제 강사 발화(멘트) 스크립트입니다
> - 🎬 표시는 시연 순서 가이드입니다
> - 🔧 표시는 실습 단계입니다 (학습자가 직접 입력)
> - 🎯 표시는 미니 과제입니다 (쉬는 시간/숙제용)
> - ⚠️ 표시는 학습자가 자주 막히는 포인트입니다
> - ❓ 표시는 예상 질문과 답변입니다
> - ⏱ 표시는 시간 배분 가이드입니다
> - 📋 표시는 학습자 점검 포인트입니다

---

# 📋 전체 운영 개요

## 수업 운영 철학
이 과정은 **"손으로 익히는 Git"** 을 목표로 합니다. 명령어를 외우게 하기보다, 학습자가 **"왜 이 명령이 필요한지"** 를 상황 속에서 체득하도록 설계되었습니다.

## 50분 구성 표준
```
0~5분    : 출석 확인, 이전 시간 복습
5~15분   : 핵심 개념 강의
15~45분  : 실습 (강사 시연 → 학습자 실습 → 순회 코칭)
45~50분  : 미니 과제 안내 + Q&A
```

## 강사가 지켜야 할 3원칙
1. **"먼저 따라하게 하라"**: 일단 명령어 실행 → 결과 보며 설명
2. **"실패를 환영하라"**: 오류 = 학습 기회로 프레이밍
3. **"손을 따라가게 하라"**: 강사 화면 멍하니 보지 말고 직접 입력하게

---

# 🔧 사전 준비 사항 (수업 시작 30분 전)

## 강사 PC 준비
- [ ] 듀얼 모니터 또는 큰 화면
- [ ] **Git Bash 폰트 키우기**: 우클릭 → Options → Text → Size 14~16
- [ ] **VS Code 폰트 키우기**: `Ctrl + +` 로 확대
- [ ] 브라우저 북마크: GitHub 로그인, PAT 발급 페이지
- [ ] 시연용 GitHub 계정
- [ ] 미리 작성한 예시 저장소 4개 (각 교시용)

## 학습자 환경 점검
- [ ] Windows 11 (또는 10)
- [ ] 관리자 권한 가능
- [ ] 인터넷 접속 (GitHub.com 차단 환경 주의!)
- [ ] 이메일 사용 가능
- [ ] VS Code 사전 설치 권장

## ⚠️ 보안 환경(공공기관) 특이사항
한국표준협회, 한국전력 등에서는 GitHub 접속 차단 가능성:
- **사전 확인 필수**: 다음 도메인 허용 요청
  - `github.com`, `*.github.com`
  - `api.github.com`
  - `objects.githubusercontent.com`
  - `git-scm.com`
- 차단 시 대안: **Gitea/GitLab 사내 서버** 또는 **로컬 실습만 진행**

---

# 🕐 1교시. Git 소개 및 환경 구축

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~5분 | 오프닝 | 자기소개, 과정 안내 |
| 5~15분 | 강의 | Git이 왜 필요한가? |
| 15~35분 | 실습 1-1, 1-2 | Git 설치, VS Code 설치 |
| 35~45분 | 실습 1-3, 1-4 | 초기 설정, Bash 명령어 |
| 45~50분 | 미니 과제 1 + Q&A | 실습 폴더 만들기 |

---

## ⏱ 0~5분: 오프닝

### 💬 강사 멘트

> "안녕하세요, 여러분. 오늘부터 8시간 동안 Git을 배우게 될 텐데요. 한 가지 약속드릴게요. **오늘 수업이 끝날 때쯤에는, 여러분 컴퓨터에 '최종', '진짜최종', '진짜진짜최종.docx' 같은 파일이 사라지게 될 겁니다.**
>
> Git을 못 쓴다고 개발자가 안 되는 건 아니에요. 하지만 **Git을 못 쓰면 팀에 들어갈 수가 없어요.** 그래서 오늘 우리는 '혼자 쓰는 Git'을 넘어서 '같이 쓰는 Git'까지 배워볼 겁니다.
>
> 부담 갖지 마세요. **명령어 외우라고 하지 않을 거예요.** 그냥 손이 자연스럽게 움직이도록, 그게 목표입니다."

### 진행 팁
- 학습자 한 명씩 짧게 자기소개 (이름 + Git 경험 1~5점)
- 1~2점 다수 → 천천히, 4~5점 다수 → 응용 위주

---

## ⏱ 5~15분: Git 개념 강의

### 🎬 Step 1: "최종.docx" 농담으로 시작

> 💬 "여러분, 이런 파일 폴더 본 적 있으시죠?"

화면에 표시:
```
📁 보고서/
   📄 보고서_최종.docx
   📄 보고서_최종_수정.docx
   📄 보고서_진짜최종.docx
   📄 보고서_진짜최종_v2.docx
   📄 보고서_이게진짜최종.docx
   📄 보고서_부장님확인.docx
```

> 💬 "이게 사실 버전 관리의 원시적인 형태예요. 우리는 자연스럽게 버전 관리를 하고 있었던 거죠. 그런데 문제가 뭘까요?"

**예상 답변 받기**: 헷갈린다, 용량 많이 차지한다, 어느게 진짜인지 모른다

> 💬 "맞아요. 그래서 우리는 **자동으로, 체계적으로** 버전을 관리해주는 도구가 필요한 거예요. 그게 바로 **Git**입니다."

### 🎬 Step 2: Git의 핵심 가치 강조

판서:
```
Git의 핵심 가치
─────────────────────
✓ 이력 관리: 누가, 언제, 무엇을, 왜 변경했는지
✓ 협업:    여러 사람 동시 작업
✓ 백업:    분산 저장으로 안전
✓ 브랜치:  병렬로 다양한 시도
```

### 🎬 Step 3: Git vs GitHub 명확히 구분 (★중요)

⚠️ **여기서 헷갈리는 학습자 많음!**

판서:
```
   Git              GitHub
   ────             ──────
   📷 (카메라)      📷 인스타그램
   도구             서비스
   내 PC            인터넷
   무료             무료(공개) / 유료(비공개)
```

> 💬 "비유하자면, **Git은 카메라이고, GitHub은 인스타그램**이에요. 카메라로 찍은 사진을 인스타에 올리듯, Git으로 만든 버전을 GitHub에 올리는 거죠. **카메라 없이도 사진은 찍을 수 있지만, 카메라가 가장 일반적**이라고 생각하시면 됩니다."

### ❓ 예상 질문

**Q1. "GitLab, Bitbucket은 뭐예요?"**
> A: GitHub의 경쟁사예요. GitLab은 회사 내부에 설치해서 쓸 수 있어서 보안 환경에서 인기가 많고, Bitbucket은 Jira와 연동이 잘 됩니다. **명령어는 다 똑같아요.** GitHub만 익히시면 나머지는 자동으로 됩니다.

**Q2. "이미 클라우드(OneDrive, Google Drive)가 있는데 왜 Git을 또 써요?"**
> A: 좋은 질문이에요! 클라우드는 **파일 동기화**고, Git은 **버전 기록**이에요. OneDrive는 '지금 이 상태'를 동기화하지만, Git은 '어제 11시 상태, 오늘 3시 상태'를 다 기억해요. 그리고 **두 사람이 같은 파일을 동시에 수정해도** Git은 자동 병합해주거나 충돌을 알려줍니다.

---

## ⏱ 15~25분: [실습 1-1] Git for Windows 설치

### 🎬 시연 진행

> 💬 "지금부터 같이 설치해볼 건데, **저를 따라하지 마시고** 같이 하시는 게 좋아요. 제가 한 화면 보여드리면, 여러분도 같은 화면이 떴는지 확인하고 다음으로 넘어갑시다."

### 🔧 [실습 1-1] 진행 단계

**Step 1. 다운로드**
1. 브라우저에서 https://git-scm.com/download/win 접속
2. "64-bit Git for Windows Setup" 클릭하여 다운로드
3. 다운로드된 .exe 파일 실행

**Step 2. 설치 옵션 (6개 핵심 화면만 안내)**

⚠️ **여기가 1교시 최대 함정 구간**

| 화면 | 선택 옵션 | 이유 |
|:---|:---|:---|
| Select Components | 기본값 유지 | 일반 사용자에 충분 |
| **Default editor** | **VS Code** 선택 | ★필수★ Vim 회피 |
| Adjust PATH | 가운데 옵션 (기본값) | CLI에서 git 사용 |
| HTTPS transport | OpenSSL (기본값) | 표준 보안 |
| Line endings | Checkout Windows... (기본값) | 협업 시 문제 방지 |
| Terminal emulator | MinTTY (기본값) | 더 예쁜 터미널 |

> 💬 "여기 (Default editor) 화면이 가장 중요해요! **꼭 VS Code를 선택**해주세요. 안 그러면 나중에 'Vim'이라는 무서운 에디터가 떠서 빠져나오기도 어려워요."

**Step 3. 설치 완료 확인**

학습자가 모두 설치 끝났는지 확인:

```bash
# 시작 메뉴에서 "Git Bash" 검색 → 실행
# Git Bash 창에서 입력:

git --version
```

**예상 출력**:
```
git version 2.45.1.windows.1
```
(버전 숫자는 다를 수 있음)

📋 **학습자 점검**: 모든 학습자가 위와 같은 출력이 나오는지 확인

⚠️ **자주 발생하는 문제 1**: Git Bash가 검색되지 않음
- **원인**: 설치 중 어딘가 체크 해제됨
- **해결**: 재설치하면서 기본값 유지

⚠️ **자주 발생하는 문제 2**: `git: command not found`
- **원인**: PATH 설정 옵션 잘못 선택
- **해결**: 재설치, "Adjusting your PATH" 단계에서 가운데 옵션

> 💬 "이렇게 'git version 2.뭐.뭐' 이렇게 나오면 성공이에요. 박수 한 번 쳐주세요!"

---

## ⏱ 25~30분: [실습 1-2] VS Code 설치

### 🔧 [실습 1-2] 진행 단계

이미 설치된 학습자는 건너뛰기.

1. https://code.visualstudio.com/ 접속
2. **Download for Windows** 클릭
3. 설치 시 **다음 옵션 체크**:
   - [ ] "탐색기 파일 상황에 맞는 메뉴에 'Code로 열기' 작업 추가"
   - [ ] "탐색기 디렉터리 상황에 맞는 메뉴에 'Code로 열기' 작업 추가"
   - [ ] "지원되는 파일 형식의 편집기로 Code 등록"
   - [ ] "PATH에 추가" (기본값)

📋 **확인**: 설치 후 임의 폴더에서 우클릭 → "Code로 열기"가 보이는지

---

## ⏱ 30~40분: [실습 1-3] Git 초기 설정

### 🎬 시연

> 💬 "이제 Git에게 '내가 누구인지' 알려줘야 해요. 왜냐면 나중에 우리가 만든 커밋 하나하나에 **'이거 누가 만들었어요'**라고 이름표가 붙거든요. 그 이름과 이메일을 미리 등록하는 거예요."

### 🔧 [실습 1-3] 단계별 명령어

**Step 1. 사용자 이름 설정**
```bash
git config --global user.name "Hong Gildong"
```

⚠️ **함정**: 따옴표 없이 공백 들어가면 오류!
- 잘못된 예: `git config --global user.name Hong Gildong`
- 올바른 예: `git config --global user.name "Hong Gildong"`

**Step 2. 이메일 설정**
```bash
git config --global user.email "your_email@example.com"
```

> 💬 "**이메일은 GitHub 가입 예정 이메일로** 적어주세요. 나중에 GitHub와 연결될 거예요."

**Step 3. 기본 브랜치명을 main으로**
```bash
git config --global init.defaultBranch main
```

> 💬 "원래 Git은 기본 브랜치를 'master'라고 불렀어요. 근데 'master/slave'라는 용어가 차별적이라는 의견이 있어서, 2020년부터 GitHub은 'main'으로 바꿨어요. 그래서 우리도 'main'으로 통일합시다."

**Step 4. 설정 확인**
```bash
git config --list
```

**예상 출력** (부분):
```
user.name=Hong Gildong
user.email=your_email@example.com
init.defaultbranch=main
...
```

📋 **학습자 점검**: 본인 이름과 이메일이 정확히 들어갔는지 확인

⚠️ **추가 권장 설정 (선택)**:
```bash
# 한글 파일명 깨짐 방지
git config --global core.quotepath false

# Windows 줄바꿈 자동 변환
git config --global core.autocrlf true

# 편의를 위한 alias 설정
git config --global alias.lg "log --oneline --graph --all --decorate"
```

---

## ⏱ 40~45분: [실습 1-4] Git Bash 기본 명령어

### 🎬 시연

⚠️ **Windows CMD 사용자**: 명령어가 다르다는 점 강조!

> 💬 "Git Bash는 사실 리눅스 명령어를 써요. Windows의 cmd랑 좀 달라요. 5개만 외우시면 됩니다."

판서:
```
pwd    → 내가 어디 있지?
ls     → 여기 뭐 있지?
cd     → 어디로 가자
mkdir  → 폴더 만들자
clear  → 화면 깨끗하게 (또는 Ctrl + L)
```

### 🔧 [실습 1-4] 단계별 명령어

```bash
# 현재 위치 확인
pwd
```
**예상 출력**: `/c/Users/사용자명` 또는 본인 홈 디렉토리

```bash
# 현재 디렉토리 목록 (간단)
ls

# 숨김 파일 포함 상세 보기
ls -al
```

```bash
# 디렉토리 이동 - 데스크탑으로
cd Desktop
pwd
```
**예상 출력**: `/c/Users/사용자명/Desktop`

```bash
# 상위 디렉토리로 이동
cd ..
pwd
```

```bash
# 다시 데스크탑으로
cd Desktop

# 새 폴더 만들기
mkdir git-study

# 폴더 안으로 이동
cd git-study
pwd
```
**예상 출력**: `/c/Users/사용자명/Desktop/git-study`

```bash
# 빈 파일 만들기
touch hello.txt
ls
```
**예상 출력**: `hello.txt`

```bash
# 화면 지우기
clear
# 또는 Ctrl + L
```

📋 **학습자 점검**: `pwd` 결과가 `git-study` 폴더 안인지 확인

⚠️ **OneDrive 동기화 폴더 주의**
- 일부 학습자의 Desktop이 OneDrive 안에 있을 수 있음
- 경로에 `OneDrive`가 보이면 → 충돌 가능성 알리고, 가능하면 `C:\git-study` 같은 단순 경로 권장
- 단순 경로 사용 시: `cd /c/` 후 `mkdir git-study` → `cd git-study`

---

## ⏱ 45~50분: [미니 과제 1] + 정리

### 🎯 [미니 과제 1] 실습 폴더 만들기

> 💬 "쉬는 시간 동안 다음을 직접 해보세요. **명령어는 칠판에 있는 5개 안에서 다 해결됩니다.**"

**과제 내용**:
1. 홈 디렉토리로 이동
2. Desktop으로 이동
3. `git-study` 폴더가 없으면 생성
4. `git-study` 안에 본인 이름으로 새 폴더 생성 (예: `kim-gildong`)
5. 그 폴더 안에 `hello.txt`, `note.md` 두 파일 생성
6. `ls`로 두 파일이 보이는지 확인
7. `pwd`로 현재 경로 확인 후 캡처

**예상 명령어 시퀀스**:
```bash
cd ~
cd Desktop
mkdir git-study   # 이미 있다면 생략
cd git-study
mkdir kim-gildong
cd kim-gildong
touch hello.txt note.md
ls
pwd
```

📋 **완료 기준**:
- `pwd` 결과: `/c/Users/사용자명/Desktop/git-study/본인이름`
- `ls` 결과: `hello.txt  note.md`

### 💬 정리 멘트

> "오늘 첫 시간이 가장 어려워요. 설치하는 게 늘 그렇죠. 그런데 이제부터는 진짜 Git을 쓰기 시작합니다.
>
> 다음 시간에 우리는 첫 번째 **커밋(commit)** 이라는 걸 만들 거예요. 커밋이 뭐냐면, **사진 찍는 것**과 똑같아요. '이 순간의 내 코드'를 찰칵 찍어두는 거죠. 그렇게 찍은 사진들이 모이면 **타임머신**이 됩니다."

---

# 🕐 2교시. 로컬 저장소 기본

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~5분 | 복습 | 미니 과제 1 점검 |
| 5~15분 | 강의 | Git의 3단계 영역 |
| 15~25분 | 실습 2-1, 2-2 | 저장소 초기화, 파일 만들기 |
| 25~35분 | 실습 2-3, 2-4 | 스테이징, 첫 커밋 |
| 35~40분 | 실습 2-5 | add 후 commit 한 번에 |
| 40~45분 | 강의 | 좋은 커밋 메시지 |
| 45~50분 | 미니 과제 2 + Q&A | 3개 이상 커밋 |

---

## ⏱ 0~5분: 복습

### 💬 복습 멘트

> "쉬는 시간 잘 보내셨나요? 잠깐 손 풀기로 명령어 5개 같이 외쳐볼게요.
> - 폴더 어디 있는지 알고 싶으면? **pwd!**
> - 폴더 안에 뭐 있는지 보고 싶으면? **ls!**
> - 다른 폴더로 가려면? **cd!**
> - 새 폴더 만들려면? **mkdir!**
> - 화면 깨끗하게? **clear!**
>
> 좋아요. 이제 본격적으로 Git을 써봅시다."

📋 **분위기 점검**: 1교시 설치 못 한 학습자가 있다면 조교(또는 빨리 끝낸 학습자)와 짝지어 빠르게 따라잡기

---

## ⏱ 5~15분: Git 3단계 영역 강의

### 🎬 판서/화면 그림 (★중요)

> 💬 "이 그림이 오늘 가장 중요해요. 다 외우실 필요는 없지만, **이 흐름을 머릿속에 그릴 수 있어야** 합니다."

판서:
```
┌─────────────┐  git add   ┌──────────────┐ git commit  ┌─────────────┐
│  작업 영역    │ ────────→ │  스테이징 영역  │ ─────────→ │   저장소     │
│  Working    │             │   Staging    │              │ Repository  │
└─────────────┘             └──────────────┘              └─────────────┘
   실제 파일                    찍을 후보들                    찍힌 사진들
```

### 비유로 설명

> 💬 "사진 찍는 거랑 똑같아요.
> - **작업 영역**은 우리 방, 그냥 일상 공간이에요.
> - **스테이징 영역**은 **사진 찍기 전 포즈 잡는 곳**이에요. 누구 누구 찍을지 정하는 거죠.
> - **저장소**는 **찰칵 찍힌 사진**이 모인 앨범이에요.
>
> 그래서:
> - `git add`는 **'너 사진에 나와!'** 라고 부르는 명령
> - `git commit`은 **'찰칵!'** 셔터 누르는 명령
> 이렇게 기억하세요."

### ❓ 예상 질문

**Q1. "왜 굳이 add를 따로 해요? 그냥 commit 한 번에 하면 안 돼요?"**
> A: 아주 좋은 질문이에요! 사실 그렇게 할 수도 있어요 (`git commit -am` 같은 명령). 그런데 **'어떤 변경을 어떤 커밋에 묶을지' 선택**할 수 있어야 해요. 예를 들어, A 파일은 '버그 수정' 커밋에, B 파일은 '기능 추가' 커밋에 따로 넣고 싶을 수 있잖아요. 그래서 단계를 나눠둔 거예요.

**Q2. "스테이징한 거 취소할 수도 있어요?"**
> A: 네! 5교시에 배울 텐데, `git restore --staged 파일명`으로 취소합니다. 일단 지금은 'add는 되돌릴 수 있다' 정도만 기억하세요.

---

## ⏱ 15~25분: [실습 2-1] 저장소 초기화 + [실습 2-2] 파일 만들기

### 🔧 [실습 2-1] 저장소 초기화

```bash
# Desktop으로 이동
cd ~/Desktop

# 새 폴더 생성
mkdir my-first-repo

# 폴더로 이동
cd my-first-repo

# Git 저장소 초기화
git init
```

**예상 출력**:
```
Initialized empty Git repository in C:/Users/사용자명/Desktop/my-first-repo/.git/
```

⚠️ **자주 발생하는 문제**: `git init` 위치 잘못 잡음
- 학습자가 `Desktop`에서 `git init`을 해버리면 → 데스크탑 전체가 Git 저장소가 됨!
- **반드시 폴더 안으로 들어간 후** `git init`

> 💬 "잠깐! `git init` 누르기 전에 `pwd`로 위치 확인하세요. **`my-first-repo` 안에 들어와 있나요?** 데스크탑에서 그냥 누르면 큰일 납니다!"

```bash
# .git 폴더 확인 (숨김 파일 포함)
ls -al
```

**예상 출력** (부분):
```
drwxr-xr-x 1 ... ./
drwxr-xr-x 1 ... ../
drwxr-xr-x 1 ... .git/
```

> 💬 "`.git`이라는 숨김 폴더가 보이죠? **이 폴더가 Git의 모든 비밀**을 담고 있어요. 이걸 삭제하면? 모든 이력이 사라집니다. 그러니까 절대 손대지 마세요!"

⚠️ **실수로 init한 경우 취소**: `rm -rf .git` (해당 폴더의 Git 추적 해제)

### 🔧 [실습 2-2] 파일 만들기 + 상태 확인

```bash
# README 파일 만들기
echo "# 나의 첫 Git 프로젝트" > README.md

# 파일 내용 확인
cat README.md
```

**예상 출력**:
```
# 나의 첫 Git 프로젝트
```

```bash
# 상태 확인
git status
```

**예상 출력**:
```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

> 💬 "여러분, `git status`는 **마법의 명령어**예요. **막힐 때마다 무조건 `git status`** 부터 누르세요. Git이 친절하게 다음에 뭘 해야 할지 알려줍니다."

> 💬 "보세요! Git이 '이 파일 추적 안 하고 있는데, 추가하려면 `git add` 쓰세요'라고 친절하게 알려주죠? **그대로 하면 됩니다.**"

📋 **학습자 점검**: 모든 학습자의 화면에 빨간색으로 `README.md`가 보이는지 확인

---

## ⏱ 25~30분: [실습 2-3] 스테이징

### 🔧 [실습 2-3] git add 실습

```bash
# 특정 파일 스테이징
git add README.md

# 상태 확인
git status
```

**예상 출력**:
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

> 💬 "이제 색깔이 바뀌었어요. **빨간색 → 초록색**으로 바뀐 거 보이시죠? 빨간색은 '추적 안 됨' 또는 '수정됨', 초록색은 '스테이징됨'이에요. **신호등처럼** 외우세요."

---

## ⏱ 30~35분: [실습 2-4] 첫 커밋

### 🔧 [실습 2-4] git commit

> 💬 "드디어 첫 커밋입니다. 박수 한 번 칠게요. 자, 따라하세요!"

```bash
# 커밋 (메시지 포함)
git commit -m "최초 커밋: README 파일 추가"
```

**예상 출력**:
```
[main (root-commit) a1b2c3d] 최초 커밋: README 파일 추가
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

> 💬 "**`-m`은 message의 m**이에요. 메시지를 한 줄로 적는 옵션이죠. 안 적으면 Vim이 떠서 무서워요."

```bash
# 커밋 이력 확인
git log
```

**예상 출력**:
```
commit a1b2c3d4e5f6789... (HEAD -> main)
Author: Hong Gildong <your_email@example.com>
Date:   Mon Nov 18 10:00:00 2024 +0900

    최초 커밋: README 파일 추가
```

> 💬 "자, 이게 우리가 찍은 **첫 사진**입니다! 누가 찍었는지, 언제 찍었는지, 뭐라고 설명했는지 다 나오죠? 이게 바로 **버전 관리**입니다!"

⚠️ **q로 빠져나오기**: log가 길어지면 페이저 모드 → **`q` 키**

📋 **학습자 점검**: `git log` 결과에 본인 이름과 이메일이 정확히 나오는지

⚠️ **author가 잘못 나오는 경우**: 1교시 `git config` 안 했음 → 다시 설정 후 재커밋

```bash
# 잘못된 author 수정
git config --global user.name "올바른 이름"
git config --global user.email "올바른 이메일"

# 마지막 커밋의 author 수정
git commit --amend --reset-author --no-edit
```

---

## ⏱ 35~40분: [실습 2-5] add와 commit 한 번에

### 🔧 [실습 2-5] 더 빠른 워크플로

```bash
# 파일 수정
echo "이 프로젝트는 Git 학습용입니다." >> README.md

# 변경된 내용 확인
cat README.md
```

**예상 출력**:
```
# 나의 첫 Git 프로젝트
이 프로젝트는 Git 학습용입니다.
```

```bash
# 상태 확인
git status
```

**예상 출력**:
```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
```

```bash
# 새 파일 추가
echo "console.log('hello');" > app.js
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   README.md

Untracked files:
        app.js
```

```bash
# 모든 변경사항 스테이징 (현재 디렉토리)
git add .
git status
```

**예상 출력**:
```
Changes to be committed:
        modified:   README.md
        new file:   app.js
```

```bash
# 커밋
git commit -m "README 내용 추가 및 app.js 생성"

# 이력 확인 (한 줄로)
git log --oneline
```

**예상 출력**:
```
b2c3d4e (HEAD -> main) README 내용 추가 및 app.js 생성
a1b2c3d 최초 커밋: README 파일 추가
```

### 주요 add 옵션 정리

판서:
```
git add 파일명       # 특정 파일만
git add .           # 현재 디렉토리 모든 변경
git add -A          # 저장소 전체 (삭제 포함)
git add *.js        # 패턴 매칭
```

📋 **학습자 점검**: 모든 학습자가 `git log --oneline`에 2개 이상의 커밋이 보이는지

---

## ⏱ 40~45분: 좋은 커밋 메시지

### 💬 강의

> "지금까지 우리가 적은 커밋 메시지, 솔직히 별로죠? '최초 커밋' 이게 뭐예요. 6개월 뒤에 보면 무슨 말인지 본인도 몰라요.
>
> **좋은 커밋 메시지는 미래의 나에게 보내는 편지**예요. '내가 왜 이걸 바꿨더라?' 6개월 뒤에 봐도 알 수 있게 적는 거죠."

### 7가지 규칙 (간단히 소개)

판서:
```
1. 제목과 본문 빈 줄로 분리
2. 제목 50자 이내
3. 영문일 경우 첫 글자 대문자
4. 제목 끝 마침표 X
5. 제목은 명령문 (Add O, Added X)
6. 본문에 무엇을, 왜
7. 한 줄 72자 제한
```

### 비교 예시 (실제로 보여주기)

| 나쁜 예 | 좋은 예 |
|:---|:---|
| "수정함" | "fix: 로그인 폼에서 이메일 유효성 검사 추가" |
| "버그 픽스" | "fix: 빈 입력값 처리 시 발생하는 크래시 수정" |
| "asdf" | "feat: 사용자 프로필 페이지 추가" |
| "최종" | "docs: README에 설치 가이드 보강" |

### Conventional Commits 소개

> 💬 "회사에서는 **컨벤션(약속)**을 정해서 써요. 가장 유명한 게 **Conventional Commits**인데요, 앞에 종류를 붙입니다."

판서:
```
feat:     새 기능
fix:      버그 수정
docs:     문서 변경
style:    코드 스타일 (포맷팅)
refactor: 리팩토링
test:     테스트 코드
chore:    빌드/설정 변경
```

> 💬 "외울 필요 없고, 회사 가시면 그 회사 규칙 따르시면 됩니다."

---

## ⏱ 45~50분: [미니 과제 2] + 정리

### 🎯 [미니 과제 2] 3개 이상 커밋 만들기

> 💬 "쉬는 시간 동안 본인만의 폴더에서 의미있는 커밋을 3개 이상 만들어 보세요. 무엇이든 좋아요. **커밋 메시지는 'feat:', 'fix:', 'docs:' 중 하나로 시작**해 보세요."

**과제 단계**:
1. Desktop에 새 폴더 `commit-practice` 만들기
2. `git init`
3. `index.html` 파일 생성 (간단한 HTML)
4. 첫 번째 커밋: `feat: HTML 기본 구조 추가`
5. `style.css` 파일 생성 (간단한 CSS)
6. 두 번째 커밋: `feat: 기본 스타일 추가`
7. README.md 작성
8. 세 번째 커밋: `docs: README 작성`
9. `git log --oneline`으로 3개 커밋 확인

**예상 명령어 시퀀스**:
```bash
cd ~/Desktop
mkdir commit-practice
cd commit-practice
git init

# 첫 번째 작업
echo "<!DOCTYPE html><html><body><h1>Hello</h1></body></html>" > index.html
git add .
git commit -m "feat: HTML 기본 구조 추가"

# 두 번째 작업
echo "h1 { color: blue; }" > style.css
git add .
git commit -m "feat: 기본 스타일 추가"

# 세 번째 작업
echo "# My Practice Project" > README.md
git add .
git commit -m "docs: README 작성"

# 확인
git log --oneline
```

📋 **완료 기준**:
- `git log --oneline` 결과에 3개의 커밋
- 각 커밋 메시지가 `feat:`, `fix:`, `docs:` 중 하나로 시작

### 💬 마무리

> "이제 여러분은 Git의 가장 핵심인 **add → commit** 사이클을 익히셨어요. **이게 Git 사용의 80%입니다.** 나머지는 다 응용이에요. 자신감 가지세요!"

---

# 🕐 3교시. 히스토리 & 변경 추적

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~5분 | 복습 | 미니 과제 2 결과 공유 |
| 5~20분 | 실습 3-1 | git log 다양한 옵션 |
| 20~30분 | 실습 3-2 | git diff 활용 |
| 30~35분 | 실습 3-3 | 파일 상태 변화 |
| 35~45분 | 실습 3-4 | .gitignore |
| 45~50분 | 미니 과제 3 + Q&A | 종합 실습 |

---

## ⏱ 0~5분: 복습 및 동기부여

### 💬 복습

> "잘 다녀오셨어요? 미니 과제 어떻게 됐나요? 혹시 3개 이상 커밋 만드신 분 손 들어보세요. 와, 좋아요!
>
> 이번 시간엔 **만든 사진(커밋)을 잘 들여다보는 방법**을 배웁니다. **'아 그때 내가 뭘 했더라?', '뭐가 바뀐 거지?'** 이런 질문에 답하는 시간이에요."

---

## ⏱ 5~20분: [실습 3-1] git log 마스터하기

### 🔧 [실습 3-1] log의 다양한 옵션

**Step 1. 기본 log와 한계**

```bash
cd ~/Desktop/my-first-repo
git log
```

**예상 출력**:
```
commit b2c3d4e5f6... (HEAD -> main)
Author: Hong Gildong <your_email@example.com>
Date:   Mon Nov 18 10:30:00 2024 +0900

    README 내용 추가 및 app.js 생성

commit a1b2c3d4e5...
Author: Hong Gildong <your_email@example.com>
Date:   Mon Nov 18 10:00:00 2024 +0900

    최초 커밋: README 파일 추가
```

> 💬 "보세요. 커밋이 많아지면 화면이 꽉 차요. 좀 깔끔하게 보고 싶죠?"

**Step 2. 점진적으로 옵션 추가**

```bash
git log --oneline
```

**예상 출력**:
```
b2c3d4e (HEAD -> main) README 내용 추가 및 app.js 생성
a1b2c3d 최초 커밋: README 파일 추가
```

> 💬 "와! 한 줄로 깔끔해졌죠. 보통 이 옵션을 가장 많이 씁니다."

```bash
git log --oneline --graph
```

> 💬 "**`--graph`는 시각적으로 보여주는 옵션**이에요. 지금은 일자라 별 차이 없지만, 4교시에 브랜치 배우면 **이게 진짜 멋있어집니다.**"

```bash
git log --oneline --graph --all
```

> 💬 "**`--all`은 모든 브랜치 다 보여주는 옵션**이에요. 나중에 또 쓸 거예요."

```bash
# 최근 3개만
git log -3

# 변경량 함께 보기
git log --stat

# 모든 변경 내용까지 (q로 빠져나옴)
git log -p

# 특정 파일의 이력만
git log --oneline README.md

# 예쁘게 포맷
git log --pretty=format:"%h - %an, %ar : %s"
```

**예상 출력** (마지막 명령):
```
b2c3d4e - Hong Gildong, 1 hour ago : README 내용 추가 및 app.js 생성
a1b2c3d - Hong Gildong, 2 hours ago : 최초 커밋: README 파일 추가
```

**Step 3. alias 등록 (편의)**

> 💬 "매번 옵션 4개 치기 귀찮죠? **단축어를 만드는 기능**이 있어요. 한 번만 등록해두면 평생 편해요."

```bash
git config --global alias.lg "log --oneline --graph --all --decorate"

# 사용
git lg
```

**예상 출력**:
```
* b2c3d4e (HEAD -> main) README 내용 추가 및 app.js 생성
* a1b2c3d 최초 커밋: README 파일 추가
```

> 💬 "이제 `git lg` 한 단어로 멋진 그래프가 나옵니다!"

### log 포맷 옵션 정리

판서:
```
%H : 커밋 해시 (전체)
%h : 커밋 해시 (축약)
%an: 작성자 이름
%ae: 작성자 이메일
%ad: 작성 날짜
%ar: 상대 시간 (3 hours ago)
%s : 커밋 메시지
```

### ❓ 예상 질문

**Q. "git log를 빠져나오려면 어떻게 해요?"**
> A: `q` 키를 누르세요. quit의 q예요.

**Q. "스크롤은요?"**
> A: 위/아래 화살표, Space(다음 페이지), b(이전 페이지)

---

## ⏱ 20~30분: [실습 3-2] git diff

### 🔧 [실습 3-2] 변경 사항 확인

**Step 1. 작업 영역의 변경 확인**

```bash
# 파일 수정
echo "새로운 줄 추가" >> README.md

# 상태 확인
git status

# 변경 사항 보기
git diff
```

**예상 출력**:
```
diff --git a/README.md b/README.md
index abc1234..def5678 100644
--- a/README.md
+++ b/README.md
@@ -1,2 +1,3 @@
 # 나의 첫 Git 프로젝트
 이 프로젝트는 Git 학습용입니다.
+새로운 줄 추가
```

> 💬 "**`git diff`는 '뭐가 달라졌는지' 비교**해주는 명령이에요. **'+' 표시는 추가된 줄, '-' 표시는 삭제된 줄**입니다."

### diff 결과 같이 읽기

> 💬 "**`@@ -1,2 +1,3 @@`** 이게 '1번째 줄부터 2줄이었는데, 3줄이 됐다'는 뜻이에요. 한 줄 추가됐다는 거죠. 처음엔 어려워 보이는데, 곧 익숙해집니다."

**Step 2. 영역별 diff**

```bash
# 스테이징
git add README.md

# 작업 영역 vs 스테이징 영역 (변경 없음!)
git diff
# → 출력 없음

# 스테이징 영역 vs 마지막 커밋 비교
git diff --staged
# 또는
git diff --cached
```

⚠️ **헷갈리는 포인트**: 학습자가 `add` 한 후에 `git diff` 했는데 아무것도 안 나와서 당황
- 해결: **add 후에는 `--staged` 옵션** 사용

> 💬 "이게 함정이에요. `add` 하고 나면 `git diff`만으로는 안 보여요. **`--staged`를 붙여야** 스테이징된 내용이 보입니다."

**Step 3. 커밋 후 비교**

```bash
# 커밋
git commit -m "docs: README에 줄 추가"

# 이력 확인
git log --oneline
```

**예상 출력**:
```
c3d4e5f (HEAD -> main) docs: README에 줄 추가
b2c3d4e README 내용 추가 및 app.js 생성
a1b2c3d 최초 커밋: README 파일 추가
```

```bash
# 두 커밋 비교 (해시는 본인 것으로)
git diff a1b2c3d c3d4e5f
```

> 💬 "이건 마치 **두 사진을 겹쳐서 다른 점 찾기** 같은 거예요. 디자이너분들 좋아하실 거예요!"

---

## ⏱ 30~35분: [실습 3-3] 파일 상태 변화

### 🎬 시각화 판서

```
파일 상태 흐름도:

┌─────────────┐  git add   ┌─────────────┐ git commit  ┌─────────────┐
│ Untracked   │ ─────────→ │ Staged      │ ──────────→ │ Committed   │
│ (추적 안됨)  │             │ (스테이징됨)  │              │ (커밋됨)     │
└─────────────┘             └─────────────┘              └─────────────┘
                                  ↑                              │
                                  │   파일 수정                    │
                                  └──────────────────────────────┘
                                          ↓
                                    ┌─────────────┐
                                    │ Modified    │
                                    │ (수정됨)     │
                                    └─────────────┘
```

### 🔧 [실습 3-3] 파일 상태 변화 직접 확인

```bash
# 1. 새 파일 = Untracked
touch new-file.txt
git status
```

**예상 출력**:
```
Untracked files:
        new-file.txt
```

```bash
# 2. add 후 = Staged
git add new-file.txt
git status
```

**예상 출력**:
```
Changes to be committed:
        new file:   new-file.txt
```

```bash
# 3. commit 후 = Committed (clean)
git commit -m "feat: 새 파일 추가"
git status
```

**예상 출력**:
```
On branch main
nothing to commit, working tree clean
```

```bash
# 4. 파일 수정 후 = Modified
echo "내용 추가" > new-file.txt
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   new-file.txt
```

📋 **학습자 점검**: 4가지 상태가 모두 보이는지 한 명씩 순회 확인

---

## ⏱ 35~45분: [실습 3-4] .gitignore

### 🎬 도입

> 💬 "여러분, **세상엔 Git에 올리면 안 되는 파일들**이 있어요.
> - **비밀번호 파일** (.env)
> - **운영체제가 만든 파일** (Thumbs.db, .DS_Store)
> - **너무 큰 파일** (동영상, 빌드 결과물)
> - **자동 생성되는 파일** (node_modules)
>
> 이런 거 일일이 빼고 add 하기 귀찮죠? 그래서 **'얘들은 Git에서 보지도 마'** 라고 미리 알려주는 게 `.gitignore` 파일이에요."

### 🔧 [실습 3-4] .gitignore 만들기

**Step 1. 파일 생성**

```bash
# .gitignore 파일 생성
touch .gitignore

# VS Code로 열기
code .gitignore
```

**Step 2. 내용 작성** (VS Code에서)

```gitignore
# 운영체제
.DS_Store
Thumbs.db

# 로그 파일
*.log

# 임시 파일
*.tmp
*.temp

# 빌드 결과물
build/
dist/
*.exe

# 환경 변수
.env
.env.local

# IDE 설정
.vscode/
.idea/

# 의존성
node_modules/
__pycache__/
*.pyc
```

> 💬 "`#`은 주석이에요. 카테고리로 정리해두면 나중에 보기 좋아요. `*.log`처럼 **별표는 모든 파일**을 의미합니다."

**Step 3. 동작 확인**

```bash
# 무시되는 파일 만들어보기
touch test.log
git status
```

**예상 출력**: `test.log`는 보이지 않아야 함

> 💬 "**.log 파일은 status에 안 보이죠?** `.gitignore`가 작동하는 거예요. 이게 마법입니다."

```bash
# 보통 파일은 잘 보임
touch normal.txt
git status
```

**예상 출력**:
```
Untracked files:
        .gitignore
        normal.txt
```

```bash
# .gitignore 커밋
git add .gitignore
git commit -m "chore: .gitignore 추가"
```

⚠️ **함정 1**: 이미 추적 중인 파일을 .gitignore에 추가
- 학습자가 자주 묻는 질문: "왜 .gitignore에 넣었는데 계속 보여요?"
- 답: 이미 커밋된 파일은 .gitignore가 적용 안 됨
- 해결:
  ```bash
  git rm --cached 파일명
  git commit -m "chore: 추적 해제"
  ```

> 💬 "이미 한 번 사진 찍힌 사람은 '나 빼줘' 해도 안 빼져요. **`git rm --cached`** 로 강제로 빼야 합니다. 단, 파일 자체가 삭제되는 건 아니에요. **Git의 추적에서만 제외**됩니다."

⚠️ **함정 2**: gitignore 템플릿 활용 팁

> 💬 "프로젝트마다 .gitignore가 달라요. Python, Java, React 다 다르죠. 그럴 땐 **github.com/github/gitignore** 에 가시면 모든 언어/프레임워크별 템플릿이 있어요. 복사해서 쓰세요!"

📋 **학습자 점검**: test.log를 만들었을 때 `git status`에 안 보이는지 확인

---

## ⏱ 45~50분: [미니 과제 3] + 정리

### 🎯 [미니 과제 3] 종합 실습

> 💬 "쉬는 시간 동안 본인이 잘 아는 언어로 새 프로젝트를 만들고, .gitignore와 함께 5개 이상 의미있는 커밋을 만들어보세요."

**과제 단계**:
1. 새 폴더 `git-history-practice` 생성
2. `git init`
3. 다음 파일들 만들기:
   - `index.html` (간단한 HTML)
   - `style.css` (간단한 CSS)
   - `app.js` (간단한 JS)
4. `.gitignore` 작성 (다음 항목 포함):
   - `*.log`
   - `node_modules/`
   - `.env`
   - `.vscode/`
5. 다음 5개 커밋 만들기:
   - `chore: 프로젝트 초기 구조 설정`
   - `feat: HTML 기본 구조 추가`
   - `feat: CSS 스타일 적용`
   - `feat: JS 기능 추가`
   - `docs: README 작성`
6. `git log --oneline --graph` 또는 `git lg`로 결과 확인

**예상 명령어 시퀀스**:
```bash
cd ~/Desktop
mkdir git-history-practice
cd git-history-practice
git init

# .gitignore 먼저
cat > .gitignore << 'EOF'
*.log
node_modules/
.env
.vscode/
EOF
git add .gitignore
git commit -m "chore: 프로젝트 초기 구조 설정"

# HTML
echo "<!DOCTYPE html><html><body><h1>Project</h1></body></html>" > index.html
git add .
git commit -m "feat: HTML 기본 구조 추가"

# CSS
echo "h1 { color: navy; font-family: sans-serif; }" > style.css
git add .
git commit -m "feat: CSS 스타일 적용"

# JS
echo "console.log('Hello, Git!');" > app.js
git add .
git commit -m "feat: JS 기능 추가"

# README
echo "# Git History Practice" > README.md
git add .
git commit -m "docs: README 작성"

# 결과 확인
git log --oneline --graph
```

📋 **완료 기준**:
- 5개의 커밋이 시간 순으로 보임
- 각 커밋 메시지가 컨벤션 따름

### 💬 마무리

> "다음 시간엔 드디어 **브랜치(branch)**라는 Git의 꽃을 배웁니다. **평행우주** 영화 보신 분, 기대하세요!"

---

# 🕐 4교시. 브랜치 (Branch)

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~10분 | 강의 | 브랜치 개념 |
| 10~20분 | 실습 4-1, 4-2 | 브랜치 생성, 이동 |
| 20~30분 | 실습 4-3 | 브랜치에서 작업 |
| 30~40분 | 실습 4-4, 4-5 | Fast-Forward, 3-way Merge |
| 40~45분 | 실습 4-6 + 강의 | 브랜치 삭제, 전략 |
| 45~50분 | 미니 과제 4 | 브랜치 시나리오 |

---

## ⏱ 0~10분: 브랜치 개념 강의

### 💬 동기부여

> "오늘 가장 재밌는 시간입니다. **브랜치(branch)**. 이게 Git의 진짜 매력이에요. 이거 못 하면 사실 Git을 쓰는 의미가 절반 사라져요."

### 🎬 비유로 설명 (★중요)

> 💬 "여러분, **평행우주** 영화 좋아하시나요? 마블 '닥터 스트레인지'나 '에브리띵 에브리웨어 올 앳 원스' 같은 거요. 어떤 시점에서 **'만약 내가 그때 다른 선택을 했다면?'** 하고 갈라지는 우주들이 있죠?
>
> **브랜치가 바로 그거예요.** 메인 줄기에서 갈라져 나와서 다른 시도를 해보는 거죠. 망하면 갖다 버리고, 잘 되면 메인에 합치고. 안전하게 실험할 수 있어요."

### 판서 (★중요)

```
[브랜치 없을 때]
A --- B --- C --- D --- E    
       (망하면? 처음부터 다시...)

[브랜치 있을 때]
              feature ----- F --- G --- H
             /                              \
A --- B --- C --- D --- E --------------------- I (merge)

     ↑ 메인은 안전하게 계속 진행하면서
       feature는 자유롭게 실험!
```

### 실제 사례

> 💬 "카카오톡 같은 앱을 만든다고 해봐요:
> - **main 브랜치**: 지금 출시된 안정 버전
> - **develop 브랜치**: 다음 출시 준비 중
> - **feature/dark-mode 브랜치**: 다크 모드 개발 중
> - **feature/voice-call 브랜치**: 음성 통화 개발 중
> - **hotfix/login-bug 브랜치**: 긴급 로그인 버그 수정 중
>
> 이게 다 동시에 진행돼요. 충돌 없이!"

---

## ⏱ 10~20분: [실습 4-1] + [실습 4-2]

### 🔧 [실습 4-1] 브랜치 생성 및 확인

```bash
# 새 실습 폴더
cd ~/Desktop
mkdir branch-practice
cd branch-practice
git init

# 초기 커밋 (★브랜치 작업하려면 최소 1개 커밋 필요)
echo "# Branch 실습" > README.md
git add .
git commit -m "초기 커밋"
```

⚠️ **중요**: 브랜치 작업하려면 **최소 1개 이상의 커밋** 필요

> 💬 "이게 함정인데요, Git은 커밋이 하나도 없으면 브랜치를 못 만들어요. 그러니까 항상 **`git init` 다음엔 일단 한 번 커밋부터** 하는 습관을 들이세요."

```bash
# 현재 브랜치 확인
git branch
```

**예상 출력**:
```
* main
```

> 💬 "**`* main`**이라고 별표가 있죠? 별표가 **'내가 지금 여기 있어요'**라는 뜻이에요."

```bash
# 새 브랜치 생성
git branch feature-login

# 브랜치 목록 확인
git branch
```

**예상 출력**:
```
  feature-login
* main
```

> 💬 "어? 별표는 아직 main에 있죠? **만들기만 했지 이동은 안 한 거예요.** Git은 친절하지 않아요. 알아서 안 옮겨줍니다."

### 🔧 [실습 4-2] 브랜치 이동

```bash
# 브랜치 이동 (최신 방식)
git switch feature-login

# 확인
git branch
```

**예상 출력**:
```
* feature-login
  main
```

> 💬 "이제 별표가 feature-login으로 옮겨갔죠? **`git switch 브랜치명`이 이동 명령**이에요."

```bash
# 다시 main으로
git switch main

# 또는 (옛날 방식, 자료에 많이 나옴)
git checkout main
```

> 💬 "**잠깐!** 옛날 명령어로는 `git checkout 브랜치명`이라고 썼어요. 인터넷에서 자료 찾으면 이게 더 많아요. 둘 다 똑같이 동작하니까 둘 다 알아두시는 게 좋아요."

```bash
# 브랜치 생성과 동시에 이동 (한 번에)
git switch -c feature-signup

git branch
```

**예상 출력**:
```
  feature-login
* feature-signup
  main
```

> 💬 "**`-c`는 create의 c**예요. 만들기와 동시에 이동까지. 이걸 가장 많이 씁니다."

### switch vs checkout 정리표

판서:
```
git switch 브랜치    : 이동 (Git 2.23+)
git switch -c 브랜치  : 생성 + 이동
git checkout 브랜치  : 이동 (구식)
git checkout -b 브랜치: 생성 + 이동 (구식)
```

> 💬 "`checkout`은 여러 용도로 쓰여 혼란스러워, `switch`와 `restore`로 분리되었습니다."

---

## ⏱ 20~30분: [실습 4-3] 브랜치별 다른 작업 (★핵심)

### 🔧 [실습 4-3] 평행우주 시연

> 💬 "지금부터 마법을 보여드릴게요."

```bash
# 일단 main으로
git switch main

# main에서 작업
echo "main 브랜치에서 작업한 내용" >> README.md
git add .
git commit -m "feat: main 브랜치 수정"

# main의 파일 상태 확인
cat README.md
```

**예상 출력**:
```
# Branch 실습
main 브랜치에서 작업한 내용
```

```bash
# feature-login으로 이동
git switch feature-login

# 파일 상태 확인 - main의 변경이 없음! (독립적)
cat README.md
```

**예상 출력**:
```
# Branch 실습
```

> 💬 "**보세요! main에서 작업한 내용이 안 보여요!** 진짜 사라진 게 아니라, **feature-login 브랜치는 분기 시점의 상태**예요. 평행우주죠?"

```bash
# feature-login에서 작업
echo "로그인 기능 추가" > login.html
git add .
git commit -m "feat: 로그인 페이지 추가"

# 파일 목록
ls
```

**예상 출력**:
```
README.md  login.html
```

```bash
# 다시 main으로
git switch main

# login.html이 사라짐!
ls
```

**예상 출력**:
```
README.md
```

> 💬 "**login.html이 사라졌죠?!** 진짜 사라진 게 아니라, **main 브랜치에는 그 파일이 없는 상태**인 거예요. 다시 feature-login으로 가면? 짠!"

```bash
git switch feature-login
ls
```

**예상 출력**:
```
README.md  login.html
```

> 💬 "이게 평행우주예요. **브랜치는 완전히 다른 상태의 파일 세계**입니다. 신기하죠?"

📋 **학습자 점검**: 학습자들이 진짜 "와!" 하는 반응이 나오는지 확인 - 이 단계의 핵심

---

## ⏱ 30~40분: [실습 4-4] + [실습 4-5] 병합

### 🔧 [실습 4-4] Fast-Forward 병합

```bash
# 새 브랜치 만들고 작업
git switch main
git switch -c feature-button
echo "<button>클릭</button>" > button.html
git add .
git commit -m "feat: 버튼 추가"

# main으로 이동
git switch main

# 현재 main의 파일
ls
```

**예상 출력**:
```
README.md
```

```bash
# main에 feature-button 병합
git merge feature-button
```

**예상 출력**:
```
Updating a1b2c3d..e4f5g6h
Fast-forward
 button.html | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 button.html
```

```bash
ls
```

**예상 출력**:
```
README.md  button.html
```

> 💬 "이걸 **Fast-Forward 병합**이라고 해요. main에 변화가 없는 상태에서 feature만 진행했으니까, 그냥 **main을 앞으로 당겨주면 끝**이에요."

```bash
# 그래프 확인
git log --oneline --graph
```

**예상 출력**:
```
* e4f5g6h (HEAD -> main, feature-button) feat: 버튼 추가
* a1b2c3d 초기 커밋
```

### 🔧 [실습 4-5] 3-way Merge

> 💬 "근데 보통은 그렇게 단순하지 않아요. main도 따로 진행되고 feature도 따로 진행되거든요."

```bash
# 새 브랜치 만들고 작업
git switch -c feature-header
echo "<header>헤더</header>" > header.html
git add .
git commit -m "feat: 헤더 추가"

# main으로 이동
git switch main

# main에서도 별도 작업
echo "main에서 README 추가 수정" >> README.md
git add .
git commit -m "docs: README 수정"
```

```bash
# main에 feature-header 병합
git merge feature-header
```

⚠️ **Vim 에디터 등장!**

> 💬 "어! 갑자기 무서운 화면이 떴죠? 이게 **Vim 에디터**예요. 컴퓨터 전공 안 하신 분들은 평생 보고 싶지 않은 화면이죠.
>
> **빠져나오는 방법**: `ESC` 누르고, `:wq` 입력하고, Enter. 외워두세요!
> - `:w`는 write(저장), `:q`는 quit(종료)
> - `:wq` = 저장하고 나가기"

**Vim 빠져나오기 단계**:
1. `ESC` 키 누르기
2. `:wq` 입력
3. `Enter`

```bash
# 그래프 확인
git log --oneline --graph --all
```

**예상 출력**:
```
*   m1n2o3p (HEAD -> main) Merge branch 'feature-header'
|\
| * h1i2j3k (feature-header) feat: 헤더 추가
* | k1l2m3n docs: README 수정
|/
* e4f5g6h (feature-button) feat: 버튼 추가
* a1b2c3d 초기 커밋
```

> 💬 "**보세요! 진짜 그래프가 나왔어요!** 갈라졌다가 다시 만나는 게 보이죠? 이게 진짜 Git의 멋진 모습입니다."

📋 **학습자 점검**: 학습자들의 그래프에 V자 머지 패턴이 보이는지

⚠️ **Vim 못 빠져나오는 학습자 처리**:
1. 같이 천천히 `ESC` 누르기 → `:wq` 입력 → `Enter`
2. 그래도 안 되면: `:q!` (변경 무시하고 강제 종료)

---

## ⏱ 40~45분: [실습 4-6] 브랜치 삭제 + 브랜치 전략

### 🔧 [실습 4-6] 사용 끝난 브랜치 정리

```bash
# 병합된 브랜치 삭제 (안전)
git branch -d feature-button
git branch -d feature-header
```

**예상 출력**:
```
Deleted branch feature-button (was e4f5g6h).
Deleted branch feature-header (was h1i2j3k).
```

```bash
# 병합 안된 브랜치는 -d로 안 됨
# feature-login은 main으로 머지 안 했음
git branch -d feature-login
```

**예상 출력 (오류)**:
```
error: The branch 'feature-login' is not fully merged.
```

```bash
# 정말 삭제하고 싶다면 강제 (-D)
git branch -D feature-login
```

**예상 출력**:
```
Deleted branch feature-login (was xxx).
```

```bash
# 현재 브랜치 목록
git branch
```

**예상 출력**:
```
* main
```

⚠️ **`-d` vs `-D`**:
- `-d`: 안전 삭제 (병합된 것만)
- `-D`: 강제 삭제 (위험!)

> 💬 "`-D`는 대문자죠? 대문자는 **'강제'**라는 뜻이에요. Git에서 대문자 D는 위험한 명령이 많아요. 신중하게 쓰세요!"

### 💬 브랜치 전략 짧게 소개

**Git Flow** (전통적):
```
main (운영 중인 진짜 코드)
  ↓
develop (다음 버전 개발 중)
  ├─ feature/A (기능 A 개발)
  ├─ feature/B (기능 B 개발)
  └─ release (배포 직전 점검)
      └─ hotfix (운영 중 긴급 수정)
```

**GitHub Flow** (단순, 모던):
```
main (항상 배포 가능 상태)
  ├─ feature/A (PR로 합치고 삭제)
  └─ feature/B (PR로 합치고 삭제)
```

> 💬 "큰 회사, 정기 출시 제품 → Git Flow. 스타트업, 웹 서비스 → GitHub Flow. **요즘 트렌드는 GitHub Flow**입니다. 일단은 단순한 게 좋아요. 나중에 회사 가시면 그 회사 룰을 따르세요."

⚠️ **너무 깊게 들어가지 말 것**: 학습자가 머리 아파함

---

## ⏱ 45~50분: [미니 과제 4] + 정리

### 🎯 [미니 과제 4] 브랜치 시나리오 실습

> 💬 "쉬는 시간 동안 다음 시나리오를 직접 구현해보세요. 5교시 시작할 때 이 결과 확인합니다."

**시나리오**:
1. 새 폴더 `branch-scenario` 생성, `git init`
2. README.md 작성 후 초기 커밋
3. `feature/login` 브랜치 생성 (main에서)
4. login.html 추가 후 커밋
5. main으로 돌아가서
6. `feature/signup` 브랜치 생성 (main에서)
7. signup.html 추가 후 커밋
8. main으로 돌아가서 README 한 줄 추가, 커밋
9. main에 feature/login 병합
10. main에 feature/signup 병합
11. `git log --oneline --graph --all` 결과 캡처

**예상 명령어 시퀀스**:
```bash
cd ~/Desktop
mkdir branch-scenario
cd branch-scenario
git init

echo "# Branch Scenario" > README.md
git add .
git commit -m "초기 커밋"

# login 브랜치
git switch -c feature/login
echo "<form>login</form>" > login.html
git add .
git commit -m "feat: 로그인 페이지 추가"

# main으로 복귀
git switch main

# signup 브랜치
git switch -c feature/signup
echo "<form>signup</form>" > signup.html
git add .
git commit -m "feat: 회원가입 페이지 추가"

# main에서 별도 작업
git switch main
echo "프로젝트 설명" >> README.md
git add .
git commit -m "docs: README 보강"

# 병합 (Vim 뜨면 :wq)
git merge feature/login
git merge feature/signup

# 그래프 확인
git log --oneline --graph --all
```

📋 **예상 결과 그래프**:
```
*   merge feature/signup
|\
| * feat: 회원가입 페이지 추가
* |   merge feature/login
|\ \
| |/
| * feat: 로그인 페이지 추가
* | docs: README 보강
|/
* 초기 커밋
```

### 💬 마무리

> "이제 여러분은 평행우주를 만들고 합치는 기술을 익히셨어요. 다음 시간엔 **충돌(conflict)**과 **되돌리기**를 배웁니다. **드디어 Git을 무서워하지 않게 되는 시간**이에요!"

---

# 🕐 5교시. 되돌리기 & 충돌 해결

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~5분 | 도입 | "Git의 안전망" |
| 5~25분 | 실습 5-1, 5-2 | 머지 충돌 해결 |
| 25~30분 | 실습 5-3, 5-4 | git restore |
| 30~40분 | 실습 5-5 | git reset |
| 40~45분 | 실습 5-6 | git revert |
| 45~50분 | 미니 과제 5 + Q&A | 충돌 시뮬레이션 |

---

## ⏱ 0~5분: 도입

### 💬 동기부여 멘트 (★중요)

> "지금까지 Git의 좋은 점만 배웠죠? **이번 시간엔 Git의 진짜 매력**을 배웁니다.
>
> 사람들이 Git을 무서워하는 이유가 뭘까요? **'실수하면 어떡하지?'**예요. 'commit 잘못 했어요', '머지하다 깨졌어요', '충돌 났어요'.
>
> 그런데 사실은요, **Git은 실수해도 거의 다 복구가 됩니다.** 오늘 끝나면 **'아, Git에서 실수해도 괜찮구나'** 라는 자신감을 얻으실 거예요."

### 비유

> 💬 "Git은 **'무한 Ctrl+Z'** 같은 거예요. 한글 워드에서 실수하면 Ctrl+Z 누르잖아요? Git에선 **몇 시간 전, 몇 일 전, 몇 달 전 상태**로도 돌아갈 수 있어요. 안심하세요."

---

## ⏱ 5~15분: [실습 5-1] 충돌 만들기

### 🔧 [실습 5-1] 의도적으로 충돌 만들기

```bash
# 새 실습 폴더
cd ~/Desktop
mkdir conflict-practice
cd conflict-practice
git init

# 초기 파일
echo "Hello World" > greeting.txt
git add .
git commit -m "초기 커밋"

# A 브랜치 만들고 작업
git switch -c feature-a
echo "Hello from A" > greeting.txt
git add .
git commit -m "feat: A 브랜치에서 인사말 변경"

# main으로 이동
git switch main

# main에서도 같은 파일 같은 줄 수정 (충돌의 원인!)
echo "Hello from Main" > greeting.txt
git add .
git commit -m "feat: main에서 인사말 변경"
```

```bash
# 충돌 발생!
git merge feature-a
```

**예상 출력 (★빨간색!)**:
```
Auto-merging greeting.txt
CONFLICT (content): Merge conflict in greeting.txt
Automatic merge failed; fix conflicts and then commit the result.
```

> 💬 "**짜잔! 빨간색 'CONFLICT'**가 떴죠? 무서워하지 마세요. Git이 친절하게 알려주는 거예요. '**같은 파일의 같은 줄을 둘이 다르게 바꿔서, 내가 결정 못 하겠어. 네가 정해줘**'라는 뜻이에요."

📋 **학습자 점검**: 모든 학습자에게 CONFLICT 메시지가 떴는지 확인

---

## ⏱ 15~25분: [실습 5-2] 충돌 해결

### 🔧 [실습 5-2] 충돌 해결 단계

**Step 1. 상태 확인**

```bash
git status
```

**예상 출력**:
```
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   greeting.txt
```

**Step 2. 충돌 파일 열어보기**

```bash
cat greeting.txt
```

**예상 출력**:
```
<<<<<<< HEAD
Hello from Main
=======
Hello from A
>>>>>>> feature-a
```

> 💬 "이 이상한 기호들이 보이죠? 해석해드릴게요:
> - **`<<<<<<< HEAD`**: '여기서부터는 현재 브랜치(HEAD = main) 내용이야'
> - **`=======`**: '경계선이야'
> - **`>>>>>>> feature-a`**: '여기까지가 합치려던 브랜치 내용이야'
>
> 그러니까 **사이에 있는 내용 중에서 선택**하면 됩니다."

**Step 3. VS Code로 열어 해결**

```bash
code greeting.txt
```

> 💬 "VS Code가 친절하죠? **버튼 4개**가 뜹니다.
> - **Accept Current Change**: 현재 브랜치 것만 (Main)
> - **Accept Incoming Change**: 들어오는 것만 (A)
> - **Accept Both Changes**: 둘 다 유지
> - **Compare Changes**: 자세히 비교
>
> 여러분이 원하는 걸 선택하세요. 이번엔 'Accept Both Changes' 한번 해볼까요?"

**Accept Both 결과**:
```
Hello from Main
Hello from A
```

또는 **수동 편집**:
```
Hello from Main and Hello from A
```

⚠️ **꼭 확인할 것**: `<<<<<<<`, `=======`, `>>>>>>>` 기호가 **모두 사라졌는지** 확인!

> 💬 "**이 기호가 하나라도 남아있으면** 망합니다. 코드에 'CONFLICT' 같은 글자가 그대로 남은 채로 커밋된 적도 있어요. 꼭 확인하세요!"

**Step 4. 충돌 해결 완료**

```bash
# 저장된 파일 확인
cat greeting.txt

# 스테이징
git add greeting.txt

# 상태 확인
git status
```

**예상 출력**:
```
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)
```

```bash
# 커밋 (Vim 뜨면 :wq)
git commit
```

> 💬 "**충돌 해결의 3단계 외우세요**:
> 1. 파일 열어서 수정
> 2. `git add`
> 3. `git commit`
>
> 이게 전부예요!"

```bash
git log --oneline --graph --all
```

**예상 출력**:
```
*   abc1234 (HEAD -> main) Merge branch 'feature-a'
|\
| * def5678 (feature-a) feat: A 브랜치에서 인사말 변경
* | ghi9012 feat: main에서 인사말 변경
|/
* jkl3456 초기 커밋
```

> 💬 "**머지 커밋**이 생겼죠? 두 줄기가 만나는 V자 모양이 보이실 거예요."

### ❓ 자주 묻는 질문

**Q. "충돌이 무서워요. 미리 막을 수는 없나요?"**
> A: 100% 막을 순 없지만 줄일 수는 있어요:
> - 한 사람이 한 파일에 집중 (역할 분담)
> - 자주 main을 받아오기 (git pull)
> - 작은 단위로 자주 커밋
> - 같은 줄 수정을 피하기 위한 커뮤니케이션

**Q. "충돌 도중에 그만하고 싶어요. 취소 가능해요?"**
> A: 네! **`git merge --abort`** 한 줄로 머지 직전 상태로 돌아갑니다. 안심하세요.

```bash
# 충돌 머지 취소 (해결 전에)
git merge --abort
```

---

## ⏱ 25~30분: [실습 5-3] + [실습 5-4] git restore

### 💬 강의

판서:
```
명령어              언제 쓰나?                      위험도
─────────────────────────────────────────────────────
git restore        파일 수정 취소 (커밋 전)          ★
git restore        스테이징 취소
--staged
git reset          커밋 자체를 되돌림 (혼자 작업)    ★★★
git revert         이미 push한 커밋 취소 (협업)     ★★
```

### 🔧 [실습 5-3] 작업 영역 되돌리기

```bash
# 새 폴더
cd ~/Desktop
mkdir restore-practice
cd restore-practice
git init

# 초기 파일과 커밋
echo "원본 내용" > sample.txt
git add .
git commit -m "초기 커밋"

# 파일 수정 (실수했다고 가정)
echo "실수로 수정" > sample.txt
cat sample.txt
```

**예상 출력**:
```
실수로 수정
```

```bash
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   sample.txt
```

```bash
# 작업 영역 되돌리기
git restore sample.txt
cat sample.txt
```

**예상 출력**:
```
원본 내용
```

> 💬 "**'아 이거 수정 안 할 걸!' 할 때 쓰는 명령**이에요. 마지막 커밋 상태로 돌아갑니다."

⚠️ **경고**: `git restore`는 수정 내용을 **완전히 삭제**합니다. 복구 불가!

> 💬 "이건 진짜 사라져요. 신중하게 쓰세요. **'정말 다 버릴 거야?' 한 번 더 생각**하시고요."

### 🔧 [실습 5-4] 스테이징 취소

```bash
# 파일 수정 후 스테이징
echo "수정 내용" > sample.txt
git add sample.txt
git status
```

**예상 출력**:
```
Changes to be committed:
        modified:   sample.txt
```

```bash
# 스테이징만 취소 (파일은 그대로)
git restore --staged sample.txt
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   sample.txt
```

> 💬 "스테이징은 취소했지만 **파일 수정은 그대로 남아있어요.** 두 단계라는 거 기억나시죠?"

```bash
# 수정도 취소하고 싶으면
git restore sample.txt
git status
```

**예상 출력**:
```
nothing to commit, working tree clean
```

---

## ⏱ 30~40분: [실습 5-5] git reset

### 💬 강의

> 💬 "**`reset`은 강력한 만큼 위험**해요. 3가지 모드가 있는데, 차이를 정확히 알아야 해요."

판서:
```
모드               작업 영역    스테이징     커밋
────────────────────────────────────────────
--soft           유지         유지         되돌림
--mixed (기본)    유지         되돌림       되돌림
--hard           되돌림        되돌림       되돌림   ← ★위험★
```

### 🔧 [실습 5-5] reset 실습

```bash
# 여러 커밋 만들기
echo "v1" > version.txt
git add .
git commit -m "v1 추가"

echo "v2" >> version.txt
git add .
git commit -m "v2 추가"

echo "v3" >> version.txt
git add .
git commit -m "v3 추가"

# 이력 확인
git log --oneline
```

**예상 출력**:
```
abc3456 v3 추가
def2345 v2 추가
ghi1234 v1 추가
```

**Step 1. --mixed (기본) 모드**

```bash
# 가장 최근 커밋만 되돌리기
git reset HEAD~1

# 또는 명시적으로
git reset --mixed HEAD~1

# 이력 확인
git log --oneline
```

**예상 출력**:
```
def2345 v2 추가
ghi1234 v1 추가
```

```bash
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   version.txt
```

> 💬 "**`HEAD~1`은 '바로 직전 커밋'**이라는 뜻이에요. `~2`면 두 칸 전, `~3`이면 세 칸 전이죠. v3 커밋은 사라졌지만, v3에서 수정한 내용은 작업 영역에 남아있죠?"

**Step 2. --soft 모드**

```bash
# 다시 v3 커밋
git add .
git commit -m "v3 추가"

# soft로 되돌리기
git reset --soft HEAD~1
git status
```

**예상 출력**:
```
Changes to be committed:
        modified:   version.txt
```

> 💬 "**`--soft`는 스테이징 상태까지 유지**해줘요. 커밋만 취소하고 싶을 때 좋아요."

**Step 3. --hard 모드 (★위험★)**

```bash
# 다시 커밋
git commit -m "v3 다시 추가"

# hard로 완전히 날리기
git reset --hard HEAD~1
cat version.txt
```

**예상 출력**:
```
v1
v2
```

```bash
git log --oneline
```

**예상 출력**:
```
def2345 v2 추가
ghi1234 v1 추가
```

> 💬 "**v3가 완전히 사라졌어요!** `--hard`는 **핵폭탄**이에요. 진짜 사라져요. **혼자 작업할 때만** 쓰세요. 협업 중에는 절대 금지!"

⚠️ **그래도 복구 방법은 있음**:
```bash
# Git의 비밀 백업 장부
git reflog
```

**예상 출력**:
```
def2345 (HEAD -> main) HEAD@{0}: reset: moving to HEAD~1
xyz9876 HEAD@{1}: commit: v3 다시 추가
def2345 HEAD@{2}: reset: moving to HEAD~1
...
```

```bash
# 사라진 커밋으로 복귀
git reset --hard xyz9876
git log --oneline
```

> 💬 "**`git reflog`는 Git의 비밀 백업장부**입니다. 거의 모든 실수가 복구돼요! 다만 30일 정도만 보관되니까 빨리 발견해야 해요."

---

## ⏱ 40~45분: [실습 5-6] git revert

### 💬 강의

> 💬 "**`revert`는 안전한 되돌리기**예요. 이력을 지우지 않고, **'취소하는 새 커밋'**을 만들어요."

### 🔧 [실습 5-6] revert 실습

```bash
# 새 폴더
cd ~/Desktop
mkdir revert-practice
cd revert-practice
git init

# 커밋 여러 개 만들기
echo "v1" > file.txt
git add . && git commit -m "v1"
echo "v2" >> file.txt
git add . && git commit -m "v2"
echo "v3" >> file.txt
git add . && git commit -m "v3"

# 이력 확인
git log --oneline
```

**예상 출력**:
```
abc3456 v3
def2345 v2
ghi1234 v1
```

```bash
# v2 커밋을 revert (HEAD~1 = v2)
git revert HEAD~1
# Vim 떠도 :wq

# 이력 확인
git log --oneline
```

**예상 출력**:
```
xyz9876 Revert "v2"
abc3456 v3
def2345 v2
ghi1234 v1
```

```bash
cat file.txt
```

**예상 출력**:
```
v1
v3
```

> 💬 "이력에 기록이 남았죠? **'우리가 v2를 만들었지만, 그 다음에 취소했다'**는 역사가 보이는 거예요. **협업할 때는 이게 정답**입니다."

### reset vs revert 선택 가이드

판서:
```
상황                              선택
────────────────────────────────────────
혼자 작업 중, 아직 push 안 함        reset
이미 push 했음                     revert
협업 중인 브랜치                    무조건 revert
비밀번호를 실수로 커밋 (지워야 함)    reset --hard + 강제 push
```

---

## ⏱ 45~50분: [미니 과제 5] + 정리

### 🎯 [미니 과제 5] 충돌 시뮬레이션

> 💬 "쉬는 시간에 충돌 시뮬레이션을 한 번 더 해보세요. 완전히 익숙해질 때까지요."

**과제 단계**:
1. 새 폴더 `conflict-scenario` 생성, `git init`
2. `index.html` 만들기: 내용 `<h1>제목</h1>`, 커밋
3. `feature` 브랜치 생성
4. feature에서 `<h1>새 제목</h1>`으로 변경, 커밋
5. main으로 복귀
6. main에서 `<h1>메인 제목</h1>`으로 변경, 커밋
7. main에 feature 병합 → 충돌!
8. VS Code로 열어서 해결 (둘 다 살리거나 새로 작성)
9. 커밋 완료
10. `git log --oneline --graph --all` 확인

**예상 명령어 시퀀스**:
```bash
cd ~/Desktop
mkdir conflict-scenario
cd conflict-scenario
git init

echo "<h1>제목</h1>" > index.html
git add .
git commit -m "초기 커밋"

# feature 작업
git switch -c feature
echo "<h1>새 제목</h1>" > index.html
git add .
git commit -m "feat: feature 브랜치에서 제목 변경"

# main 작업
git switch main
echo "<h1>메인 제목</h1>" > index.html
git add .
git commit -m "feat: main에서 제목 변경"

# 병합 시도 → 충돌!
git merge feature
# 충돌 발생

# 해결
code index.html
# VS Code에서 수정 후 저장

# 마무리
git add .
git commit
# Vim에서 :wq

# 결과 확인
git log --oneline --graph --all
```

📋 **완료 기준**:
- 충돌 발생 확인
- VS Code에서 해결
- 머지 커밋 생성됨
- `<<<<<<<`, `=======`, `>>>>>>>` 기호 모두 사라짐

### 💬 마무리

> "**Git에서 실수해도 거의 다 복구 가능**하다는 걸 이제 아셨죠? 자신감을 가지세요. 두려움 없이 시도하세요. 그게 빨리 배우는 비결입니다.
>
> 다음 시간엔 드디어 **GitHub**과 연결합니다! 세상과 연결되는 시간이에요."

---

# 🕐 6교시. 원격 저장소 (GitHub)

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~10분 | 실습 6-1 | GitHub 가입 |
| 10~20분 | 실습 6-2, 6-3 | 저장소 생성, 원격 연결 |
| 20~30분 | 강의 + PAT 발급 | PAT 토큰 |
| 30~40분 | 실습 6-4 | push, pull, fetch |
| 40~45분 | 실습 6-5 | git clone |
| 45~50분 | 실습 6-6 + 미니 과제 6 | README 작성 |

---

## ⏱ 0~10분: [실습 6-1] GitHub 가입

### 💬 도입

> "드디어! **세상과 연결되는 시간**입니다. 지금까지 우리는 내 컴퓨터 안에서만 Git을 썼죠. 이제 **GitHub**라는 클라우드에 올려서, 어디서나 접근하고, 다른 사람과 협업할 수 있게 만들 거예요."

### 🔧 [실습 6-1] GitHub 가입

⚠️ **유의사항**:
- 이미 GitHub 계정 있는 학습자: 그대로 사용
- 새 가입자: 5~10분 정도 소요
- **단체 메일 환경**: 회사 메일은 인증 메일이 차단될 수 있음 → 개인 메일 권장

**단계**:
1. https://github.com 접속
2. 우측 상단 **Sign up** 클릭
3. 이메일 입력 (개인 메일 권장)
4. 비밀번호 (15자 이상 또는 8자 이상 + 숫자 + 영어)
5. **사용자명** (Username) 입력 (★중요★)
6. 봇 인증 (퍼즐)
7. **Create account**
8. 이메일로 온 6자리 코드 입력
9. 설문 (Skip 가능)

> 💬 "사용자명 정할 때 신중하세요. **나중에 바꾸기 어려워요.** 가능하면:
> - 본명 또는 영문 이름
> - 짧고 외우기 쉬운 것
> - 다른 곳에서도 쓸 ID와 통일
>
> 예: 김철수 → kimcheolsu, chulsu-kim, cskim 등
>
> **이상한 닉네임은 피하세요** (예: cute_unicorn_2025). 나중에 면접에서 GitHub 보여드릴 일 생기니까요."

📋 **완료 확인**: 모든 학습자가 GitHub 메인 페이지에서 본인 프로필 보이는지

---

## ⏱ 10~20분: [실습 6-2] + [실습 6-3]

### 🔧 [실습 6-2] 원격 저장소 생성

화면 공유하면서 단계별로:

1. GitHub 로그인 후 우측 상단 **+** 클릭
2. **New repository** 선택
3. 설정:
   - **Repository name**: `my-first-github-repo`
   - **Description**: (선택) `Git 학습용 첫 저장소`
   - **Public** 선택 (Private도 무료지만 일단 Public)
   - **Add a README file**: **체크 해제!** (★중요★ 로컬에 이미 있을 거니까)
   - **.gitignore**: None
   - **License**: None
4. **Create repository** 클릭

⚠️ **자주 발생하는 문제**: README를 체크해서 만들고, 로컬에도 README 만들어서 push할 때 충돌!
- 해결: 처음엔 **빈 저장소**로 만들기
- 또는: 로컬에서 `git pull --rebase origin main` 후 push

> 💬 "**README 체크는 일단 해제**하세요. 우리는 로컬에서 만든 걸 올릴 거니까요."

**Step 2. 안내 화면 이해**

GitHub가 친절하게 명령어를 보여줍니다:
```
…or create a new repository on the command line
echo "# my-first-github-repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/사용자명/my-first-github-repo.git
git push -u origin main

…or push an existing repository from the command line
git remote add origin https://github.com/사용자명/my-first-github-repo.git
git branch -M main
git push -u origin main
```

> 💬 "**이 화면에 모든 답이 있어요!** 외울 필요 없고, 매번 새 저장소 만들 때마다 이 화면 보고 따라하면 됩니다."

### 🔧 [실습 6-3] 로컬 ↔ 원격 연결

```bash
# 로컬 폴더 준비
cd ~/Desktop
mkdir github-practice
cd github-practice
git init

# 첫 파일 만들기
echo "# GitHub 연동 실습" > README.md
git add .
git commit -m "최초 커밋"

# 원격 저장소 연결 (URL은 본인 것으로!)
git remote add origin https://github.com/사용자명/my-first-github-repo.git

# 연결 확인
git remote -v
```

**예상 출력**:
```
origin  https://github.com/사용자명/my-first-github-repo.git (fetch)
origin  https://github.com/사용자명/my-first-github-repo.git (push)
```

```bash
# 기본 브랜치명 확인 후 main으로
git branch -M main
```

> 💬 "**`origin`**이라는 이름은 그냥 별명이에요. '원본 원격 저장소'라는 뜻으로 관례적으로 씁니다. 다른 이름 써도 되지만, 다들 origin 써요."

---

## ⏱ 20~30분: PAT 발급

### 💬 도입 (헷갈리는 부분 미리 정리)

> "여기서 좀 충격적인 사실을 말씀드리면, **GitHub은 비밀번호로 push 못 합니다.** 2021년부터 그렇게 바뀌었어요. 비밀번호 대신 **Personal Access Token(PAT)**이라는 걸 발급받아서 써야 해요. 마치 **임시 비밀번호** 같은 거예요."

### 🔧 PAT 발급 시연

화면 공유:

**Step 1. Settings 접근**
1. 우측 상단 프로필 아이콘 클릭
2. **Settings** 클릭

**Step 2. Developer settings**
1. 좌측 메뉴 **맨 아래로 스크롤**
2. **Developer settings** 클릭

**Step 3. PAT 생성**
1. **Personal access tokens** 클릭
2. **Tokens (classic)** 선택
3. **Generate new token** → **Generate new token (classic)**
4. 비밀번호 재입력
5. 설정:
   - **Note**: `Git 실습용 토큰`
   - **Expiration**: `30 days` (실습 기간만)
   - **Select scopes**: **`repo` 체크** (이것만! 나머지는 X)
6. 페이지 맨 아래 **Generate token** 클릭

**Step 4. 토큰 복사**

화면에 토큰이 표시됨 (예: `ghp_AbCdEfGhIjKlMnOpQrStUvWxYz1234567890`)

⚠️ **★ 절대 주의 ★**:
- **이 페이지를 떠나면 토큰을 다시 볼 수 없음!**
- 메모장에 임시 저장 필수
- 잃어버리면 재발급해야 함

> 💬 "**이 토큰, 다른 사람한테 절대 보여주지 마세요.** 보여주면 그 사람이 여러분 GitHub 코드를 마음대로 바꿀 수 있어요. **노트북 화면 노출 주의!** 강사인 저한테도 절대 보여주지 마세요."

**Step 5. 메모장에 저장**

```
Windows 메모장 열기 → 토큰 붙여넣기 → 안전한 곳에 저장
```

---

## ⏱ 30~40분: [실습 6-4] push, pull, fetch

### 🔧 [실습 6-4] push 실행

```bash
# 원격으로 푸시
git push -u origin main
```

**인증 창 등장**:
- **Username**: GitHub 사용자명
- **Password**: 메모장의 PAT 붙여넣기 (★ 비밀번호 아님 ★)

> 💬 "**비밀번호 입력란이 떠도, 진짜 비밀번호를 넣지 마세요!** 아까 복사한 PAT 토큰을 붙여넣으세요. 한 번 성공하면 Windows가 기억해줘서, 다음부턴 안 물어봅니다."

**예상 출력**:
```
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 226 bytes | 226.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/사용자명/my-first-github-repo.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

⚠️ **자주 발생하는 문제 1**: PAT 잘못 붙여넣음
- 증상: `Authentication failed`
- 해결: 메모장에서 다시 복사, 또는 재발급

⚠️ **자주 발생하는 문제 2**: 인증 창이 안 뜸
- 원인: Windows 자격증명에 잘못된 정보 캐시됨
- 해결:
  1. **제어판 → 사용자 계정 → 자격 증명 관리자**
  2. **Windows 자격 증명** 탭
  3. `git:https://github.com` 찾아서 제거
  4. 다시 push

> 💬 "**`-u`는 upstream 설정**이에요. 한 번만 하면 됩니다. 그 다음부터는 `git push`만 쳐도 자동으로 origin/main으로 갑니다."

**Step. 성공 확인**

GitHub 저장소 페이지 새로고침 → README.md 보이는지 확인

> 💬 "**축하합니다! 여러분의 코드가 인터넷에 올라갔습니다!** 친구에게 링크 공유할 수도 있고, 어디서든 다운로드 받을 수도 있어요."

📋 **학습자 점검**: 모든 학습자가 GitHub 웹에서 본인 저장소의 README.md를 볼 수 있는지

### 🔧 추가 실습: pull

**Step 1. GitHub 웹에서 직접 편집**

1. README.md 클릭
2. 우측 연필 아이콘 클릭
3. 내용 추가: "GitHub 웹에서 수정"
4. 페이지 아래 **Commit changes**

**Step 2. 로컬에서 받아오기**

```bash
git pull
```

**예상 출력**:
```
From https://github.com/사용자명/my-first-github-repo
   abc1234..def5678  main       -> origin/main
Updating abc1234..def5678
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

```bash
cat README.md
```

**예상 출력**:
```
# GitHub 연동 실습
GitHub 웹에서 수정
```

> 💬 "**`pull`은 원격에서 가져오는 명령**이에요. GitHub에서 누군가 바꾼 걸 내 컴퓨터로 가져오는 거죠."

### fetch vs pull

```bash
# fetch는 가져오기만, 합치진 않음
git fetch

# 가져온 후 직접 병합
git merge origin/main
```

> 💬 "**`fetch`는 가져오기만 하고, `pull`은 가져와서 합치기까지**합니다.
> - **fetch + merge = pull**
> - 처음엔 그냥 pull만 써도 돼요."

---

## ⏱ 40~45분: [실습 6-5] git clone

### 🔧 [실습 6-5] clone 시연

```bash
# 새 위치로 이동
cd ~/Desktop

# 본인 저장소 클론
git clone https://github.com/사용자명/my-first-github-repo.git cloned-repo

# 폴더 이동
cd cloned-repo

# 이력 확인 (원격의 모든 커밋이 그대로!)
git log --oneline
```

**예상 출력**:
```
def5678 (HEAD -> main, origin/main, origin/HEAD) Update README.md
abc1234 최초 커밋
```

```bash
# remote 자동 설정됨
git remote -v
```

**예상 출력**:
```
origin  https://github.com/사용자명/my-first-github-repo.git (fetch)
origin  https://github.com/사용자명/my-first-github-repo.git (push)
```

> 💬 "**`clone`은 다 한방에**입니다. 폴더 만들기, init, remote 연결, pull까지 한 줄로 끝나요. **남의 코드를 가져올 때나, 다른 PC에서 작업할 때** 가장 많이 씁니다."

### 응용 시나리오

> 💬 "회사에서 자주 있는 일이에요:
> - **출근**: `git pull` (밤사이 동료가 올린 거 받기)
> - **작업**: 코딩 + `git add` + `git commit`
> - **퇴근**: `git push` (올리기)
>
> 매일 이 사이클입니다. 이게 GitHub 협업의 80%예요."

---

## ⏱ 45~50분: [실습 6-6] + [미니 과제 6]

### 🔧 [실습 6-6] README 꾸미기

```bash
cd ~/Desktop/github-practice
code README.md
```

VS Code에서 함께 작성:

```markdown
# 나의 첫 GitHub 프로젝트

## 📖 소개
Git 학습용 저장소입니다.

## 🚀 시작하기

### 설치 방법
\```bash
git clone https://github.com/사용자명/my-first-github-repo.git
\```

### 실행
\```bash
echo "Hello GitHub!"
\```

## 🛠 기술 스택
- HTML / CSS / JavaScript

## 📝 라이선스
MIT License

## 👤 작성자
- 이름: 홍길동
- GitHub: [@username](https://github.com/username)
```

```bash
# 커밋 후 푸시
git add README.md
git commit -m "docs: README 멋지게 작성"
git push
```

GitHub에서 확인:
- README가 멋지게 렌더링됨

> 💬 "**짠! 멋진 페이지가 되었죠?** VS Code에서 `Ctrl + Shift + V` 누르면 미리보기도 됩니다."

### 🎯 [미니 과제 6] 포트폴리오 시작하기

> 💬 "쉬는 시간에 본인만의 포트폴리오 저장소를 만들어 보세요. 나중에 이력서에 쓸 수도 있어요!"

**과제 단계**:
1. GitHub에 새 저장소 `portfolio` 생성 (Public, README 체크 X)
2. 로컬에 `portfolio` 폴더 생성, `git init`
3. README.md 작성 (본인 소개)
4. `about.md` 추가 (자세한 소개)
5. `projects.md` 추가 (만든 프로젝트 목록 - 가상이라도 OK)
6. 각각 별도 커밋
7. 원격 연결 후 push
8. GitHub 웹에서 확인

**예상 명령어 시퀀스**:
```bash
cd ~/Desktop
mkdir portfolio
cd portfolio
git init

# README
cat > README.md << 'EOF'
# 홍길동의 포트폴리오

## 안녕하세요! 👋
저는 Git을 배우는 학습자 홍길동입니다.

## 📂 페이지
- [About Me](./about.md)
- [Projects](./projects.md)
EOF

git add .
git commit -m "docs: README 작성"

# about.md
cat > about.md << 'EOF'
# 자기소개

## 기본 정보
- 이름: 홍길동
- 직업: 개발자 지망생

## 관심사
- 웹 개발
- 오픈소스
EOF

git add .
git commit -m "docs: about 페이지 추가"

# projects.md
cat > projects.md << 'EOF'
# 프로젝트 목록

## 1. Git 학습 프로젝트
8시간 Git 마스터 과정 수료

## 2. 포트폴리오 사이트
GitHub Pages로 배포 예정
EOF

git add .
git commit -m "docs: projects 페이지 추가"

# 원격 연결 (URL은 본인 것!)
git remote add origin https://github.com/사용자명/portfolio.git
git branch -M main
git push -u origin main
```

📋 **완료 기준**:
- GitHub 웹에서 portfolio 저장소가 보임
- 3개 이상의 커밋이 GitHub에 표시됨
- README, about.md, projects.md 모두 표시됨

### 💬 마무리

> "다음 시간엔 **다른 사람과 함께 코드를 짜는 협업**을 배웁니다. 짝꿍과 함께 진행하니까 옆 사람과 인사해 두세요!"

---

# 🕐 7교시. 협업 워크플로우

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~10분 | 강의 | 협업 방식 비교 |
| 10~25분 | 실습 7-1 | Collaborator 방식 |
| 25~40분 | 실습 7-2 | Fork & Pull Request |
| 40~50분 | 실습 7-3 + 미니 과제 7 | PR 충돌 해결 + 종합 협업 |

---

## ⏱ 사전 준비 (★중요)

### 짝 정하기

> 💬 "이번 시간엔 **짝 활동**이 핵심이에요. 옆 사람과 짝을 정해주세요. 짝의 GitHub 사용자명을 메모해두세요!"

판서:
```
A 학생: GitHub ID = _________
B 학생: GitHub ID = _________
```

### ⚠️ 인원 홀수 대비

- 강사가 짝이 되어주기 (강사 임시 계정 활용)
- 또는 3인 1조 (A→B→C→A 순환)

---

## ⏱ 0~10분: 협업 방식 비교

### 💬 강의

> "협업 방식엔 크게 두 가지가 있어요:
> 1. **Collaborator (공동 작업자)**: 같은 저장소에 직접 push (빠름, 신뢰)
> 2. **Fork & Pull Request**: 복사본에서 작업 후 요청 (안전, 검토)"

판서:
```
Collaborator → 회사 동료, 팀 프로젝트
Fork & PR    → 오픈소스 기여, 외부 contributors
```

### 실제 예시

> 💬 "여러분이 회사 입사하면 보통 **Collaborator로** 추가될 거예요. 회사 GitHub 조직(Organization)에 들어가서 push 권한 받죠.
>
> 반면에 **리눅스 커널, React, VS Code** 같은 큰 오픈소스에 기여하고 싶다면? 그 저장소를 Fork해서 PR 보내야 합니다. **'세계의 코드에 내 이름을 새기는 방법'**이에요."

---

## ⏱ 10~25분: [실습 7-1] Collaborator 방식

### 🔧 [실습 7-1] 협업자 초대 - A 학생

**A 학생 (저장소 소유자) 단계**:
1. 본인 저장소 → **Settings** → **Collaborators**
2. (비밀번호 재인증) → **Add people**
3. B의 GitHub ID 또는 이메일 입력
4. 검색 결과에서 정확한 사람 선택
5. **Add 본인이름/저장소명 to this repository**

> 💬 "**B의 GitHub ID를 정확히 입력**하세요. 이메일로도 가능합니다."

**B 학생 (초대받은 협업자) 단계**:
1. GitHub 우측 상단 🔔 (알림) 또는 이메일 확인
2. 초대 링크 클릭
3. **Accept invitation**

⚠️ **알림이 안 보이는 경우**:
- 이메일 확인 (스팸 폴더도!)
- 직접 URL 접속: `https://github.com/A사용자명/저장소/invitations`

### 🔧 B 학생: 클론 및 작업

```bash
cd ~/Desktop
git clone https://github.com/A사용자명/my-first-github-repo.git collab-test
cd collab-test
```

```bash
# 본인 정보로 작업
echo "B 학생($USER)이 추가한 내용" >> README.md

# 새 파일 추가
echo "## 협업 테스트" > collaboration.md
echo "B 학생이 만든 협업 페이지입니다." >> collaboration.md

git add .
git commit -m "feat: B 학생의 협업 기여"
git push
```

⚠️ **PAT 인증**: B는 본인의 PAT으로 인증해야 함

> 💬 "**B 학생, 본인 PAT으로 인증하세요.** A의 PAT 쓰면 안 돼요. 본인 계정으로 작업하는 거니까요."

### 🔧 A 학생: B의 변경 받기

```bash
cd ~/Desktop/github-practice  # A의 원본 저장소
git pull
```

**예상 출력**:
```
Updating abc1234..xyz9876
Fast-forward
 README.md         | 1 +
 collaboration.md  | 2 ++
 2 files changed, 3 insertions(+)
 create mode 100644 collaboration.md
```

```bash
cat README.md
cat collaboration.md
```

> 💬 "**B의 내용이 보이죠?** 이게 협업입니다! 동시에 작업하고, 서로 변경사항을 주고받는 거예요."

### 역할 바꿔서 다시 (10분 추가)

A↔B 역할 바꿔서 동일하게 진행:
1. B의 저장소에 A를 초대
2. A가 클론 후 작업
3. push 후 B가 pull로 확인

📋 **학습자 점검**: 양쪽 모두 collaboration이 성공했는지 확인

---

## ⏱ 25~40분: [실습 7-2] Fork & Pull Request

### 🔧 [실습 7-2] Fork 단계

> 💬 "이번엔 짝의 저장소를 **Fork**해보세요. Fork는 **'내 계정으로 복사'**입니다."

**Step 1. Fork**

각자 짝의 GitHub 저장소 페이지로 이동:
1. 우측 상단 **Fork** 클릭
2. 본인 계정 선택
3. **Create fork** 클릭
4. URL이 본인 계정으로 바뀜 확인

> 💬 "Fork 끝나면 URL이 본인 계정으로 바뀌어 있을 거예요. **`github.com/본인ID/...`** 이렇게요."

**Step 2. Fork한 저장소 클론**

```bash
cd ~/Desktop
git clone https://github.com/본인ID/저장소.git fork-test
cd fork-test
```

**Step 3. 브랜치 만들고 작업**

> 💬 "**중요!** main에 직접 커밋하지 말고, **새 브랜치를 만드세요.** 이게 협업 매너입니다."

```bash
git switch -c feature/my-contribution

# 작업
cat > CONTRIBUTORS.md << 'EOF'
# 기여자 목록

## 핵심 기여자
- @본인GitHub아이디

## 감사의 말
이 프로젝트에 기여하게 되어 영광입니다.
EOF

git add .
git commit -m "feat: CONTRIBUTORS 파일 추가"

# 본인 Fork에 푸시
git push -u origin feature/my-contribution
```

**Step 4. Pull Request 생성**

1. GitHub 본인 Fork 페이지로 이동
2. 노란색 배너: **Compare & pull request** 클릭
   - 또는: **Pull requests** 탭 → **New pull request**
3. PR 작성:
   - **Title**: `feat: CONTRIBUTORS 파일 추가`
   - **Description**:
     ```markdown
     ## 변경 내용
     - CONTRIBUTORS.md 파일 추가
     - 기여자 명단 정리
     
     ## 변경 이유
     프로젝트 기여자를 명시적으로 관리하기 위함
     
     ## 테스트
     - [x] 파일 정상 생성 확인
     - [x] 마크다운 렌더링 확인
     
     ## 관련 이슈
     없음
     ```
4. **Create pull request** 클릭

> 💬 "**PR 설명을 잘 쓰세요.** 받는 사람이 한눈에 이해할 수 있게요. 변경 내용, 이유, 테스트 결과까지. 좋은 PR이 좋은 협업의 시작입니다."

**Step 5. 원본 소유자: 리뷰 & 머지**

원본 저장소 소유자(짝)가:
1. 본인 저장소 → **Pull requests** 탭
2. 받은 PR 확인
3. **Files changed** 탭 → 코드 확인
4. (선택) 라인별 코멘트 남기기:
   - 코드 라인 옆 `+` 버튼 클릭
   - 코멘트 작성 후 **Add single comment** 또는 **Start a review**
5. **Review changes** (우측 상단 초록 버튼):
   - **Comment**: 단순 의견
   - **Approve**: 승인
   - **Request changes**: 수정 요청
6. **Merge pull request** 클릭
7. **Confirm merge**

> 💬 "**리뷰 코멘트는 정중하게**:
> - ❌ '이거 왜 이렇게 했어요?'
> - ✅ '여기 더 좋은 방법이 있을 것 같은데요. 예를 들면...'
>
> 코드 리뷰는 **사람을 비판하는 게 아니라 코드를 개선하는 자리**예요."

**Step 6. 원본 저장소에 반영 확인**

PR이 머지된 후, 원본 저장소(원래 짝의 저장소)에서:
- 메인 페이지에 CONTRIBUTORS.md가 보이는지 확인

### ❓ 자주 묻는 질문

**Q. "Fork는 언제까지 가지고 있어야 해요?"**
> A: PR이 머지되거나 거절되면 Fork는 삭제해도 됩니다. 단, 계속 그 프로젝트에 기여할 거면 Fork를 유지하고 주기적으로 원본과 동기화하세요 (`git fetch upstream`).

**Q. "PR 보낸 후 더 수정할 수 있어요?"**
> A: 네! 같은 브랜치에 추가 커밋하고 push하면 자동으로 PR에 반영됩니다.

```bash
# 추가 수정
echo "추가 내용" >> CONTRIBUTORS.md
git add .
git commit -m "docs: CONTRIBUTORS 보강"
git push
# → 기존 PR에 자동 반영됨
```

📋 **학습자 점검**: 모든 짝이 서로의 PR을 머지하는 데 성공했는지

---

## ⏱ 40~50분: [실습 7-3] + [미니 과제 7]

### 🔧 [실습 7-3] PR 충돌 해결

**상황 시뮬레이션**: PR을 보낸 사이 main이 변경됨

**A 학생: PR을 받았는데 그동안 main도 변경된 경우**

```bash
# A의 원본 저장소에서
cd ~/Desktop/github-practice

# main에 추가 작업 (예: README 수정)
echo "## A의 추가 작업" >> README.md
git add .
git commit -m "docs: README 보강"
git push

# 이제 B가 보낸 PR과 충돌 가능
```

**B 학생: PR 충돌 해결**

```bash
cd ~/Desktop/fork-test

# 원본 저장소를 upstream으로 추가
git remote add upstream https://github.com/A사용자명/저장소.git

# upstream 확인
git remote -v
```

**예상 출력**:
```
origin    https://github.com/B사용자명/저장소.git (fetch)
origin    https://github.com/B사용자명/저장소.git (push)
upstream  https://github.com/A사용자명/저장소.git (fetch)
upstream  https://github.com/A사용자명/저장소.git (push)
```

```bash
# 원본 main의 최신 변경 가져오기
git fetch upstream

# 본인 작업 브랜치로 이동
git switch feature/my-contribution

# upstream/main을 merge
git merge upstream/main
# 충돌 시: 해결 → git add → git commit

# 다시 push
git push
# → 기존 PR이 자동으로 업데이트됨
```

> 💬 "**PR이 'Conflicts must be resolved'라고 뜨면** 위 방법으로 해결하세요. GitHub 웹에서도 해결 가능하지만, 로컬에서 하는 게 더 안전합니다."

### 🎯 [미니 과제 7] 협업 시뮬레이션

> 💬 "쉬는 시간에 짝과 함께 더 복잡한 협업 시나리오를 해보세요."

**과제 단계 (짝 협업)**:

**1단계: A가 새 저장소 준비**
```bash
# A 학생
cd ~/Desktop
mkdir team-project
cd team-project
git init

echo "# Team Project" > README.md
echo "팀 협업 프로젝트입니다." >> README.md
git add .
git commit -m "초기 커밋"

# GitHub에 새 저장소 만든 후
git remote add origin https://github.com/A사용자명/team-project.git
git branch -M main
git push -u origin main

# B를 Collaborator로 추가 (GitHub Settings에서)
```

**2단계: B가 클론**
```bash
# B 학생
cd ~/Desktop
git clone https://github.com/A사용자명/team-project.git
cd team-project
```

**3단계: A와 B가 각각 다른 브랜치에서 작업**

A 학생:
```bash
git switch -c feature/header
cat > header.html << 'EOF'
<header>
  <h1>우리 팀 프로젝트</h1>
  <nav>홈 | 소개 | 연락</nav>
</header>
EOF
git add .
git commit -m "feat: 헤더 컴포넌트 추가"
git push -u origin feature/header
```

B 학생:
```bash
git switch -c feature/footer
cat > footer.html << 'EOF'
<footer>
  <p>&copy; 2024 Team Project</p>
</footer>
EOF
git add .
git commit -m "feat: 푸터 컴포넌트 추가"
git push -u origin feature/footer
```

**4단계: 각자 PR 생성**

GitHub 웹에서:
- A는 feature/header → main PR
- B는 feature/footer → main PR

**5단계: 서로의 PR 리뷰 & 머지**

A의 PR을 B가 검토 → Approve → A가 머지
B의 PR을 A가 검토 → Approve → A가 머지 (저장소 소유자라서)

**6단계: 양쪽 다 최신 받기**

```bash
git switch main
git pull
ls
# → README.md, header.html, footer.html 모두 보임
```

**7단계: 의도적 충돌 만들기 (도전 과제)**

A 학생:
```bash
git switch -c hotfix/title-a
# README.md 첫 줄 변경
echo "# A가 수정한 제목" > README.md
echo "팀 협업 프로젝트입니다." >> README.md
git add .
git commit -m "fix: A 버전 제목"
git push -u origin hotfix/title-a
# PR 생성, 머지
```

B 학생 (동시에):
```bash
git switch main
git switch -c hotfix/title-b
echo "# B가 수정한 제목" > README.md
echo "팀 협업 프로젝트입니다." >> README.md
git add .
git commit -m "fix: B 버전 제목"
git push -u origin hotfix/title-b
# PR 생성 시 → 충돌 발생!
```

**8단계: 충돌 해결**

B 학생:
```bash
# 최신 main 받아오기
git fetch origin
git merge origin/main
# 충돌 발생!

# VS Code로 해결
code README.md

# 둘 다 살리거나 새 버전으로
git add .
git commit
git push
# → PR 자동 업데이트, 머지 가능
```

📋 **완료 기준**:
- 각자 최소 1개씩 PR 생성, 머지
- 서로의 PR 리뷰 코멘트 작성
- 충돌 시나리오 해결

### 💬 마무리

> "이제 여러분은 **세계 어떤 개발자와도 협업할 준비**가 되었습니다. 진심이에요. **'리눅스 만든 사람한테 PR 보내기'**도 기술적으로는 다 가능해요.
>
> 다음 시간에 마지막으로, **고급 기능 몇 가지와 미니 프로젝트**로 마무리하겠습니다. **GitHub Pages로 본인 블로그까지** 만들 거예요!"

---

# 🕐 8교시. 실전 활용 & 미니 프로젝트

## 수업 흐름표 (50분)

| 시간 | 활동 | 내용 |
|:---:|:---|:---|
| 0~5분 | 도입 | 마지막 시간 안내 |
| 5~10분 | 실습 8-1 | git stash |
| 10~15분 | 실습 8-2 | git tag |
| 15~20분 | 실습 8-3 | git rebase (간단히) |
| 20~25분 | 강의 | 자주 발생하는 문제 |
| 25~45분 | 종합 미니 프로젝트 | GitHub Pages 블로그 |
| 45~50분 | 정리 | 수료 체크리스트 |

---

## ⏱ 0~5분: 도입

### 💬 멘트

> "드디어 마지막 시간입니다. 여기까지 오신 여러분, 정말 대단해요. 박수 한 번 칠게요!
>
> 오늘은 **실무에서 자주 쓰는 기능 몇 가지**와, **GitHub Pages로 본인 웹사이트 만들기** 미니 프로젝트로 마무리합니다. **여러분의 이름으로 된 웹사이트**를 인터넷에 띄우는 게 오늘의 목표입니다."

---

## ⏱ 5~10분: [실습 8-1] git stash

### 💬 도입

> 💬 "**stash**는 '나중에 하려고 미뤄두기'예요. 작업 중인데 갑자기 다른 일이 생겼을 때 씁니다. 회의 들어가야 할 때 책상 위 정리해서 서랍에 넣어두는 느낌이에요."

### 🔧 [실습 8-1] stash 사용하기

```bash
# 새 실습 폴더
cd ~/Desktop
mkdir stash-practice
cd stash-practice
git init

# 초기 파일과 커밋
echo "원본" > work.txt
git add .
git commit -m "초기 커밋"
```

**Step 1. 작업 시작**

```bash
# 작업 중 (커밋 안 함)
echo "작업 중인 내용" >> work.txt
git status
```

**예상 출력**:
```
Changes not staged for commit:
        modified:   work.txt
```

**Step 2. stash로 임시 저장**

```bash
git stash
git status
```

**예상 출력**:
```
On branch main
nothing to commit, working tree clean
```

```bash
cat work.txt
```

**예상 출력**:
```
원본
```

> 💬 "**작업 내용이 사라졌죠?** 진짜 사라진 게 아니라 서랍(stash)에 들어간 거예요."

**Step 3. stash 목록 확인**

```bash
git stash list
```

**예상 출력**:
```
stash@{0}: WIP on main: abc1234 초기 커밋
```

**Step 4. 다른 작업**

```bash
echo "급한 작업" > urgent.txt
git add .
git commit -m "fix: 급한 수정"
```

**Step 5. stash 다시 꺼내기**

```bash
git stash pop
```

**예상 출력**:
```
On branch main
Changes not staged for commit:
        modified:   work.txt
```

```bash
cat work.txt
```

**예상 출력**:
```
원본
작업 중인 내용
```

> 💬 "**짠! 작업 내용이 돌아왔어요.** stash list도 비어있을 거예요."

### stash 주요 명령

판서:
```
git stash                # 임시 저장
git stash save "메시지"   # 메시지와 함께 저장
git stash list           # 목록 보기
git stash show stash@{0} # 내용 보기
git stash pop            # 가장 최근 stash 꺼내기 (목록에서 삭제)
git stash apply stash@{0}# 적용만 (목록 유지)
git stash drop stash@{0} # 특정 stash 삭제
git stash clear          # 전체 삭제
```

---

## ⏱ 10~15분: [실습 8-2] git tag

### 💬 도입

> 💬 "**tag**는 특정 커밋에 '버전 라벨'을 다는 거예요. 책에 책갈피 끼우는 느낌이죠. 회사에서 'v1.0 출시!' 같은 마일스톤을 표시할 때 씁니다."

### 🔧 [실습 8-2] 태그 활용

```bash
# 새 폴더에서
cd ~/Desktop
mkdir tag-practice
cd tag-practice
git init

# 커밋 몇 개 만들기
echo "v1 기능" > version.md
git add . && git commit -m "feat: 초기 기능"

echo "v1.1 버그 수정" >> version.md
git add . && git commit -m "fix: 버그 수정"

# 이력 확인
git log --oneline
```

**Step 1. 가벼운 태그 (lightweight)**

```bash
git tag v1.0.0
```

**Step 2. 주석 태그 (annotated, 권장)**

```bash
git tag -a v1.1.0 -m "버전 1.1.0 릴리스: 버그 수정"
```

> 💬 "**주석 태그를 권장**합니다. 메시지와 작성자 정보가 포함되어 더 의미있어요."

**Step 3. 태그 확인**

```bash
git tag
```

**예상 출력**:
```
v1.0.0
v1.1.0
```

```bash
git show v1.1.0
```

**예상 출력**:
```
tag v1.1.0
Tagger: Hong Gildong <your_email@example.com>
Date:   ...

버전 1.1.0 릴리스: 버그 수정

commit abc1234...
...
```

**Step 4. 원격에 태그 푸시 (GitHub 저장소가 있을 경우)**

```bash
# 원격 저장소가 있다면
git push origin v1.1.0

# 모든 태그 푸시
git push origin --tags
```

**Step 5. 태그 삭제**

```bash
# 로컬에서 삭제
git tag -d v1.0.0

# 원격에서도 삭제
git push origin --delete v1.0.0
```

### Semantic Versioning (시맨틱 버저닝)

판서:
```
v 2 . 1 . 3
  │   │   └─ PATCH: 버그 수정
  │   └───── MINOR: 기능 추가 (호환 유지)
  └───────── MAJOR: 큰 변경 (호환 깨짐)
```

> 💬 "**v1.0.0 → v1.0.1**은 버그 수정, **v1.0.0 → v1.1.0**은 기능 추가, **v1.0.0 → v2.0.0**은 큰 변화로 호환성 깨짐을 의미해요. 회사 입사하면 이 룰을 따르게 될 거예요."

---

## ⏱ 15~20분: [실습 8-3] git rebase

### 💬 강의 (★깊이 들어가지 말 것)

> "**rebase**라는 게 있어요. 너무 깊이 들어가면 머리 아프니까 **개념만** 짧게 알려드릴게요."

판서:
```
[merge 결과]                  [rebase 결과]
A---B---C---F                 A---B---C---D'---E'
     \     /
      D---E

(분기와 병합이 보임)            (깔끔한 직선)
```

> 💬 "쉽게 말하면:
> - **merge**: 역사를 보존 (지저분하지만 안전)
> - **rebase**: 역사를 다시 씀 (깔끔하지만 위험)
>
> **rebase 황금률**: '이미 push해서 다른 사람이 받아간 커밋'은 **절대** rebase 하지 마세요. 협업이 망가집니다."

### 🔧 [실습 8-3] rebase 시도 (선택)

```bash
# 새 폴더
cd ~/Desktop
mkdir rebase-practice
cd rebase-practice
git init

echo "main 1" > file.txt
git add . && git commit -m "main: v1"
echo "main 2" >> file.txt
git add . && git commit -m "main: v2"

# feature 브랜치
git switch -c feature
echo "feature 1" >> file.txt
git add . && git commit -m "feature: f1"
echo "feature 2" >> file.txt
git add . && git commit -m "feature: f2"

# main에 추가 커밋
git switch main
echo "main 3" >> file.txt
git add . && git commit -m "main: v3"

# 현재 그래프 확인 (분기 상태)
git log --oneline --all --graph
```

**예상 출력 (rebase 전)**:
```
* abc1234 (HEAD -> main) main: v3
| * def5678 (feature) feature: f2
| * ghi9012 feature: f1
|/
* jkl3456 main: v2
* mno7890 main: v1
```

```bash
# feature를 main 기준으로 rebase
git switch feature
git rebase main
# 충돌 시: 해결 후 git add → git rebase --continue

# 그래프 확인 - 직선이 됨
git log --oneline --all --graph
```

**예상 출력 (rebase 후)**:
```
* pqr1234 (HEAD -> feature) feature: f2
* stu5678 feature: f1
* abc1234 (main) main: v3
* jkl3456 main: v2
* mno7890 main: v1
```

> 💬 "**직선이 됐죠?** 보기엔 좋은데, 커밋 해시가 다 바뀌어 있어요. 그래서 협업 중에는 위험한 거예요."

> 💬 "처음엔 그냥 **merge만 쓰세요.** 익숙해진 후 rebase를 배워도 늦지 않아요. 회사 가서 사수에게 배우세요."

⚠️ **rebase 중단 명령어**:
```bash
git rebase --abort  # rebase 취소
```

---

## ⏱ 20~25분: 자주 발생하는 문제 강의

### 💬 강의

> "마지막으로, **실무에서 자주 마주치는 5가지 문제**와 해결법을 알려드릴게요."

### 문제 1: 커밋 메시지 잘못 작성

```bash
# 가장 최근 커밋 메시지만 수정
git commit --amend -m "올바른 메시지"
```

⚠️ **주의**: 이미 push했다면 force push 필요 (`git push --force`)

### 문제 2: 커밋에 파일 빠뜨림

```bash
# 빠진 파일 추가
git add forgot-file.txt

# 직전 커밋에 합치기 (메시지는 그대로)
git commit --amend --no-edit
```

### 문제 3: 잘못된 브랜치에 커밋함

```bash
# 1. 최근 커밋 해시 메모
git log --oneline
# 예: abc1234

# 2. 잘못 커밋한 브랜치에서 되돌리기
git reset --hard HEAD~1

# 3. 올바른 브랜치로 이동
git switch correct-branch

# 4. 커밋 가져오기
git cherry-pick abc1234
```

> 💬 "**cherry-pick은 특정 커밋을 다른 브랜치로 옮기는 명령**이에요. 이름처럼 '체리 골라 따기'죠."

### 문제 4: 큰 파일 실수로 커밋

```bash
# .gitignore에 추가
echo "big-file.zip" >> .gitignore

# 커밋에서 파일 제거
git rm --cached big-file.zip
git commit -m "chore: 큰 파일 추적 제외"
```

### 문제 5: push가 거부됨 (rejected)

```bash
# 원격 변경 가져온 후 push
git pull --rebase origin main
git push
```

### 응급 명령어 정리

판서:
```
어디까지 했는지 모르겠다              → git status
실수했을 때 백업 장부 보기             → git reflog
방금 한 작업 취소                     → git restore 파일
방금 add 한 거 취소                   → git restore --staged 파일
방금 commit 한 거 취소 (혼자)          → git reset HEAD~1
방금 commit 한 거 취소 (협업)          → git revert HEAD
작업 중인 거 잠깐 치워두기              → git stash
merge 중에 그만하기                   → git merge --abort
rebase 중에 그만하기                  → git rebase --abort
```

---

## ⏱ 25~45분: [종합 미니 프로젝트] GitHub Pages 블로그

### 💬 도입

> "자, 이제 **여러분의 결과물을 인터넷에 띄우는 시간**입니다! GitHub Pages라는 무료 서비스로, **`사용자명.github.io`** 주소로 본인 웹사이트를 만들 수 있어요. 무료에, 광고도 없고, 한 번 설정하면 평생 갑니다."

### 🎯 [종합 미니 프로젝트] 단계별 진행

### 🔧 Step 1: 저장소 생성 (★규칙 엄수)

GitHub에서 새 저장소:
1. 우측 상단 **+** → **New repository**
2. **Repository name**: **`사용자명.github.io`** (정확히 본인 GitHub ID!)
   - 예: 사용자명이 `kimcheolsu`라면 → `kimcheolsu.github.io`
3. **Public** 선택 (Pages는 Public 필수)
4. **Add a README file** 체크
5. **Create repository**

⚠️ **★ 가장 중요한 규칙 ★**
- 저장소 이름은 **정확히 'GitHub사용자명.github.io'** 여야 함
- 한 글자라도 다르면 안 됨!

> 💬 "**여기서 실수하면 안 돼요.** 본인 GitHub ID를 정확히 적고, 뒤에 `.github.io`를 붙이세요. 대소문자 구분 X, 하지만 띄어쓰기는 안 됩니다."

### 🔧 Step 2: 클론 후 작업

```bash
cd ~/Desktop
git clone https://github.com/사용자명/사용자명.github.io.git
cd 사용자명.github.io
```

### 🔧 Step 3: index.html 만들기

```bash
code index.html
```

VS Code에서 함께 작성:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나의 블로그</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>안녕하세요, 홍길동입니다 👋</h1>
        <nav>
            <a href="index.html">홈</a>
            <a href="about.html">소개</a>
        </nav>
    </header>
    <main>
        <article>
            <h2>최근 글</h2>
            <p>Git 8시간 마스터하기!</p>
            <p>오늘 8시간의 Git 과정을 수료했습니다. 새로운 시작입니다.</p>
        </article>
    </main>
    <footer>
        <p>© 2024 홍길동</p>
    </footer>
</body>
</html>
```

### 🔧 Step 4: style.css 만들기

```bash
code style.css
```

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', -apple-system, sans-serif;
    line-height: 1.6;
    padding: 20px;
    background: #f5f5f5;
    color: #333;
}

header {
    border-bottom: 2px solid #2c3e50;
    padding-bottom: 20px;
    margin-bottom: 30px;
}

h1 {
    color: #2c3e50;
    margin-bottom: 10px;
}

nav a {
    margin-right: 15px;
    color: #3498db;
    text-decoration: none;
    font-weight: 500;
}

nav a:hover {
    text-decoration: underline;
}

main {
    max-width: 800px;
    margin: 0 auto;
    background: white;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

article h2 {
    color: #34495e;
    margin-bottom: 15px;
}

article p {
    margin-bottom: 10px;
}

footer {
    text-align: center;
    margin-top: 40px;
    color: #777;
    font-size: 0.9em;
}
```

### 🔧 Step 5: 첫 커밋 및 push

```bash
git add .
git commit -m "feat: 홈 페이지 추가"
git push
```

### 🔧 Step 6: 브랜치로 about 페이지 추가

> 💬 "지금까지 배운 거 종합해서 써봅시다. **브랜치 만들고 → 작업 → 머지** 사이클!"

```bash
git switch -c feature/about-page
code about.html
```

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>소개 - 나의 블로그</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>나에 대하여</h1>
        <nav>
            <a href="index.html">홈</a>
            <a href="about.html">소개</a>
        </nav>
    </header>
    <main>
        <article>
            <h2>안녕하세요</h2>
            <p>Git을 배우고 있는 학습자입니다.</p>
            
            <h2>관심사</h2>
            <ul>
                <li>웹 개발</li>
                <li>오픈소스 기여</li>
                <li>새로운 기술 학습</li>
            </ul>
            
            <h2>연락처</h2>
            <p>GitHub: <a href="https://github.com/본인ID">@본인ID</a></p>
        </article>
    </main>
    <footer>
        <p>© 2024 홍길동</p>
    </footer>
</body>
</html>
```

```bash
git add .
git commit -m "feat: about 페이지 추가"

# main에 머지
git switch main
git merge feature/about-page

# 푸시
git push
```

### 🔧 Step 7: GitHub Pages 활성화 (★중요)

화면 공유:
1. GitHub 저장소 → **Settings**
2. 좌측 메뉴 → **Pages**
3. **Source**: `Deploy from a branch`
4. **Branch**: `main` / `/ (root)`
5. **Save**

> 💬 "**1~2분 정도 기다리세요.** 자동으로 배포됩니다. 새로고침 하면서 **'Your site is live at https://사용자명.github.io'**가 뜨면 성공!"

### 🔧 Step 8: 접속 확인

브라우저에서 `https://사용자명.github.io` 접속

⚠️ **즉시 안 보이는 경우**:
- 브라우저 강제 새로고침: `Ctrl + F5`
- 시크릿 모드로 다시 시도
- 5~10분 더 기다리기
- CSS가 안 보이면: 파일 이름 대소문자 확인

### 🔧 Step 9: 태그 달기

```bash
git tag -a v1.0.0 -m "🎉 블로그 첫 배포!"
git push origin v1.0.0
```

GitHub 저장소 우측 → **Releases** 클릭 → 태그 확인

> 💬 "**이게 여러분의 첫 릴리스**입니다. 평생 기억할 순간이에요! 화면 캡처 해두세요."

📋 **종합 미니 프로젝트 완료 기준**:
- [ ] 저장소 이름이 `사용자명.github.io`
- [ ] index.html과 about.html 모두 작동
- [ ] CSS 스타일 적용됨
- [ ] 브랜치 사용 흔적 (그래프 확인)
- [ ] 의미있는 커밋 5개 이상
- [ ] 사이트가 실제로 접속됨
- [ ] v1.0.0 태그 생성

---

## ⏱ 45~50분: 수료 정리

### 💬 수료 멘트

> "여러분, 정말 수고 많으셨습니다. 8시간 전에 Git이 뭔지도 잘 모르셨던 분들이, 이제 **본인 웹사이트를 인터넷에 띄우고**, **세계 어떤 개발자와도 협업할 수 있는** 사람이 되었어요.
>
> 솔직히 말씀드리면, 여기서 배운 거는 **Git의 30%** 정도예요. 하지만 **이 30%로 회사 업무의 90%**를 처리할 수 있어요. 나머지는 필요할 때 하나씩 더 배우면 됩니다."

### 수료 체크리스트 (소리내어 함께)

> 💬 "오늘 배운 거 한번 점검해볼까요?"

**1단계: 로컬 (1~3교시)**
- "Git 설치 및 설정 - 네!"
- "init, add, commit - 네!"
- "log, diff - 네!"
- ".gitignore 작성 - 네!"

**2단계: 브랜치 (4~5교시)**
- "브랜치 생성/이동 - 네!"
- "브랜치 병합 - 네!"
- "충돌 해결 - 네!"
- "restore, reset, revert - 네!"

**3단계: 원격 (6교시)**
- "GitHub 저장소 생성 - 네!"
- "push, pull, clone - 네!"

**4단계: 협업 (7교시)**
- "Fork & Pull Request - 네!"
- "코드 리뷰 - 네!"

**5단계: 활용 (8교시)**
- "stash, tag - 네!"
- "GitHub Pages 배포 - 네!"

### 다음 학습 안내

> "더 배우고 싶으시면:
> 1. **Learn Git Branching** (learngitbranching.js.org) - 게임처럼 배우는 사이트, 정말 추천!
> 2. **Pro Git 책 (한글)** (git-scm.com/book/ko/v2) - 무료. 깊이 들어갈 때
> 3. **실전 프로젝트**: 본인 코드를 매일 GitHub에 올리세요. 1년 후 잔디(commit history)가 빼곡해질 거예요"

### 마지막 한 마디

> "**Git은 머리로 외우는 게 아니라 손으로 익히는 거**예요. 매일 작은 거라도 git을 쓰세요. **하루 1 commit**이 목표예요. 1년 후 여러분의 GitHub 프로필이 여러분의 이력서가 됩니다.
>
> 여기까지 함께 해주셔서 감사합니다. **여러분의 첫 commit을 기억하세요. 그게 시작이었습니다.**"

---

# 📊 평가 가이드

## 평가 항목

### A. 미니 과제 점검 (60%)

각 교시별 미니 과제 수행 여부:

| 교시 | 점검 항목 | 배점 |
|:---:|:---|:---:|
| 1 | Git 설치 및 폴더 생성 | 5 |
| 2 | 3개 이상 커밋 (컨벤션 적용) | 10 |
| 3 | .gitignore 작성, 5개 이상 커밋 | 10 |
| 4 | 브랜치 시나리오, 그래프 캡처 | 10 |
| 5 | 충돌 시뮬레이션 및 해결 | 10 |
| 6 | GitHub portfolio 저장소 | 5 |
| 7 | 협업 시뮬레이션 (PR 생성/머지) | 5 |
| 8 | 종합 미니 프로젝트 완료 | 5 |

### B. 최종 프로젝트 (40%)

GitHub Pages 블로그 배포:

| 항목 | 배점 |
|:---|:---:|
| 저장소 정상 생성 및 명명 | 10 |
| 최소 2개 이상 HTML 페이지 | 10 |
| CSS 스타일 적용 | 5 |
| 브랜치 사용 흔적 | 5 |
| 의미있는 커밋 메시지 (5개 이상) | 5 |
| 사이트 정상 접속 | 5 |

---

# 🆘 트러블슈팅 가이드

## 자주 발생하는 문제 (강사용 즉시 대응)

### 1. 설치 관련

**문제**: `'git' is not recognized as an internal or external command`
- **원인**: PATH 설정 안 됨
- **해결**: Git 재설치, "Use Git from the Windows Command Prompt" 또는 가운데 옵션 선택

**문제**: Git Bash 한글 깨짐
- **해결**:
  ```bash
  git config --global core.quotepath false
  ```
  Git Bash 설정 → Options → Text → Locale: ko_KR, Character set: UTF-8

### 2. 인증 관련

**문제**: `Authentication failed for 'https://github.com/...'`
- **원인 1**: PAT 잘못 입력 또는 만료
- **해결 1**: GitHub에서 PAT 재발급
- **원인 2**: Windows 자격증명에 옛 정보 캐시됨
- **해결 2**: 제어판 → 자격 증명 관리자 → Windows 자격 증명 → `git:https://github.com` 제거

### 3. push/pull 관련

**문제**: `! [rejected] main -> main (fetch first)`
- **원인**: 원격에 로컬에 없는 변경사항 있음
- **해결**:
  ```bash
  git pull --rebase origin main
  git push
  ```

**문제**: `fatal: refusing to merge unrelated histories`
- **원인**: 로컬과 원격이 별도 히스토리
- **해결**:
  ```bash
  git pull origin main --allow-unrelated-histories
  ```

### 4. 브랜치/머지 관련

**문제**: `error: Your local changes would be overwritten by checkout`
- **원인**: 작업 중인 변경사항이 있어서 브랜치 이동 불가
- **해결**:
  ```bash
  # 옵션 1: 일단 커밋
  git add . && git commit -m "WIP"
  
  # 옵션 2: stash로 임시 저장
  git stash
  git switch 다른브랜치
  ```

**문제**: 머지하다 망함, 처음 상태로 돌아가고 싶음
- **해결**:
  ```bash
  git merge --abort
  ```

### 5. 실수 복구

**문제**: 마지막 커밋 메시지 잘못 적음
- **해결**:
  ```bash
  git commit --amend -m "올바른 메시지"
  ```

**문제**: `git reset --hard` 하고 후회됨
- **해결**:
  ```bash
  git reflog
  # 되돌아갈 해시 찾기
  git reset --hard 해시
  ```

### 6. Windows 특이사항

**문제**: 줄바꿈 경고 (`LF will be replaced by CRLF`)
- **설명**: Windows는 CRLF, Linux/Mac은 LF
- **해결**:
  ```bash
  git config --global core.autocrlf true
  ```

**문제**: 파일명 대소문자 변경이 인식 안 됨
- **해결**:
  ```bash
  git config --global core.ignorecase false
  ```

### 7. GitHub Pages 관련

**문제**: 페이지가 404로 뜸
- **확인**:
  - 저장소 이름이 정확히 `사용자명.github.io`인가?
  - Public 저장소인가?
  - index.html이 루트에 있는가?
  - Settings → Pages에서 source 설정했는가?
  - 5~10분 기다렸는가?

**문제**: CSS가 적용 안 됨
- **확인**:
  - `<link href="style.css">` 경로 정확한가?
  - 대소문자 구분 (예: `Style.css`로 만들고 `style.css`로 링크하면 X)

---

# 📚 부록

## A. 강사용 시연 저장소 사전 준비

수업 전 다음 저장소를 미리 만들어두면 시연이 매끄럽습니다.

### 1. 기본 시연 저장소 (1~3교시용)
- 폴더명: `demo-basic`
- 커밋 5개 이상
- README.md, app.js, .gitignore 포함

### 2. 브랜치 시연 저장소 (4교시용)
- 폴더명: `demo-branch`
- main, develop, feature/login, feature/signup, hotfix 브랜치
- 머지 커밋 여러 개

### 3. 충돌 시연 저장소 (5교시용)
- 폴더명: `demo-conflict`
- 의도적으로 충돌 발생 준비

### 4. 협업 시연 저장소 (7교시용)
- 강사 메인 계정과 시연용 계정 두 개로
- PR 미리 1~2개 만들어두기

---

## B. 학습자 수준별 운영 팁

### 초급자 (개발 경험 없음)
- 1~2교시에 시간 더 할애
- 4교시 브랜치 전략 부분 짧게
- 7교시는 시연 위주

### 중급자 (다른 VCS 사용 경험)
- 1교시 빠르게
- 8교시 rebase 부분 확장

### 고급자 (Git 일부 사용)
- 표준 커리큘럼 유지하되 깊이 ↑
- 추가: cherry-pick, interactive rebase, GitHub Actions 맛보기

---

## C. 시간 단축 운영

### 8시간 → 6시간
- 유지: 1, 2, 4, 5, 6, 8교시
- 통합: 3교시 → 2교시에 흡수, 7교시 → 8교시에 흡수 (Fork 생략)

### 8시간 → 4시간
- 1교시: 설치 + init + add + commit
- 2교시: log + 브랜치 기초
- 3교시: GitHub push
- 4교시: 미니 프로젝트

---

## D. 강사 후속 활동 제안

1. **수료 후 1주일 챌린지**: "하루 1 commit 인증"
2. **포트폴리오 리뷰**: 본인 GitHub 페이지 강사가 1:1 피드백
3. **오픈소스 첫 PR 도전**: `good-first-issue` 라벨 프로젝트 안내
4. **온라인 커뮤니티 연결**: Discord, 카카오톡 오픈챗 등

---

## E. 강사 자신을 위한 체크리스트

수업 끝나면 본인 평가:
- [ ] 모든 학습자가 GitHub Pages 배포까지 성공했는가?
- [ ] 충돌 해결 실습에서 모두가 직접 해결했는가?
- [ ] 강사 시연 시간이 실습 시간보다 길지는 않았는가?
- [ ] 학습자 질문에 충분히 응답했는가?
- [ ] 실무 사례를 충분히 들었는가?
- [ ] "Git이 무섭지 않다"는 자신감을 심어주었는가?

---

**🎓 8시간 Git 실습 강사용 완전 스크립트 완료!**

> "최고의 강사는 학습자가 **'나도 할 수 있겠다'**라는 자신감을 갖게 만드는 사람입니다.
> Git처럼 처음엔 무서워 보이는 도구일수록, 더더욱 그 자신감이 중요합니다."
