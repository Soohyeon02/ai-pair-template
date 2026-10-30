# ai-pair-template

AI 코딩 에이전트(Codex 등)와 협업할 때 쓰는 개인 작업 템플릿입니다.
특정 과제의 코드는 포함하지 않으며, 작업 방식과 문서 양식만 담고 있습니다.

## 구성

| 파일 | 용도 |
| --- | --- |
| `AGENTS.md` | 에이전트가 매 요청마다 읽는 규칙. 맨 위 "과제 요약"만 채워서 사용 |
| `templates/PLAN.md` | 요구사항, 구현 순서, 단계별 검증 방법 |
| `templates/DECISIONS.md` | 결정, 근거, 검증 결과, 남은 한계 기록 (협업 기록) |
| `PROMPTS.md` | 자주 쓰는 요청 문장 |
| `CHECKLIST.md` | 시작, 작업 중, 제출 전 점검표 |

## 사용 방법

### 0. 위치 확인
```bash
pwd   # 작업 폴더인지 확인. 아니면 cd로 이동
ls    # PLAN.md, DECISIONS.md가 이미 있는지 확인 (있으면 덮어쓰지 않기)
git status   # 이미 git 저장소인지 확인
```

### 계획 A: 작업 폴더 바깥(~/tpl)에 받기 (기본)
작업 폴더를 깨끗하게 유지하고, 템플릿이 커밋과 제출물에 섞이지 않는다.

```bash
git clone https://github.com/Soohyeon02/ai-pair-template.git ~/tpl
cp ~/tpl/AGENTS.md .
cp ~/tpl/templates/PLAN.md ~/tpl/templates/DECISIONS.md .
```

참고 파일은 터미널에서 연다.
```bash
cat ~/tpl/PROMPTS.md
cat ~/tpl/CHECKLIST.md
```

### 계획 B: ~/tpl이 안 될 때 (권한 오류, 재접속 후 사라짐 등)
작업 폴더 안에 받고, 복사한 뒤 바로 삭제한다.

```bash
git clone https://github.com/Soohyeon02/ai-pair-template.git _tpl
cp _tpl/AGENTS.md .
cp _tpl/templates/PLAN.md _tpl/templates/DECISIONS.md .
cat _tpl/PROMPTS.md _tpl/CHECKLIST.md   # 필요한 내용 확인
rm -rf _tpl
```

- 첫 커밋 전에 반드시 `rm -rf _tpl`로 지운다. 지우지 않고 `git add .`를 하면 저장소 안에 저장소가 들어가고, 제출물에도 템플릿이 섞인다.
- 나중에 다시 보고 싶으면 같은 명령으로 다시 받고, 확인 후 다시 지운다.

### 주의
- 이 README.md는 작업 폴더로 복사하지 않는다. 과제용 README.md를 덮어쓰게 된다.
- PROMPTS.md, CHECKLIST.md는 참고용이라 복사하지 않는다.

## 작업 흐름
1. `AGENTS.md`의 "과제 요약"을 README와 과제 안내를 읽고 직접 채운다
2. 에이전트에게 PLAN.md 작성을 요청하고, 직접 검토해서 고친다
3. 단계마다 구현 → 실행·확인 → 이해 → 기록 → 커밋을 반복한다
