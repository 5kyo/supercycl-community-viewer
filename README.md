# Supercycl Community Viewer

Supercycl × YouthMeta 커뮤니티 관리자 대시보드의 조회 전용 데스크톱 웹 목업입니다.

[목업 열기](https://5kyo.github.io/supercycl-community-viewer/) · [GitHub 저장소](https://github.com/5kyo/supercycl-community-viewer)

## 독립 프로젝트로 작업하기

기본 작업 폴더는 `Projects/Supercycl-Community-Viewer/`입니다. Codex나 편집기에서 이 폴더를 프로젝트로 열면 됩니다. Supercycl Mobile과 별도 Git 저장소이며, 빌드 도구나 환경 변수 설치 없이 실행됩니다.

```text
Supercycl-Community-Viewer/
├── index.html                 # 화면·스타일·동작·가상 데이터·로고
├── README.md                  # 실행·검증·배포 안내
├── AGENTS.md                  # 공통 에이전트 작업 지침
├── CLAUDE.md                  # Claude용 작업 지침 진입점
├── docs/
│   └── PROJECT_CONTEXT.md     # 목적·구현 범위·결정 사항·정책 참조
├── .gitignore
└── .nojekyll                  # GitHub Pages 정적 게시 설정
```

`index.html`이 수정 원본입니다. 데스크톱의 `슈퍼사이클_커뮤니티_뷰어_목업.html`은 공유용 복사본으로 관리합니다. 정책 참고 위치와 이전 작업의 맥락은 [프로젝트 컨텍스트](docs/PROJECT_CONTEXT.md)에 정리되어 있습니다.

## 사용 방법

페이지에서 **로그인하고 둘러보기**를 누르면 바로 시연할 수 있습니다. 별도 계정이나 설치가 필요하지 않습니다. 내려받은 `index.html`을 브라우저에서 직접 열어도 동작합니다.

프로젝트 폴더에서 로컬 서버로 확인하려면 다음 명령을 실행하고 `http://localhost:4173`을 엽니다. Python 3만 필요하며 종료는 `Ctrl+C`입니다.

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

## 현재 기능

- 상단 채널 버튼으로 문샷 서클·알파 스쿼드 전환
- 미실현 손익, 기간별 실현 성과, 멤버 연동 현황 조회
- 멤버 검색·필터·정렬 및 포지션 상세 조회
- 주의 멤버와 그룹 정보 확인
- 채널별 신고 사유·처리 상태·조치 결과 및 제재 적용·해제 이력 조회
- 신고·제재 기록 검색, 상태·종류 필터와 관련 기록 간 이동

## 목업 범위

로그인 화면은 시연용입니다. 실제 인증을 수행하지 않으며 모든 인물·계정·수치는 가상 데이터입니다. 서버 연결, 정보 수정, 거래 기능은 없습니다. 실제 계정이나 개인정보를 입력할 필요가 없습니다.

HTML·CSS·JavaScript와 로고가 `index.html` 하나에 포함되어 있습니다. 외부 라이브러리나 외부 데이터 요청은 사용하지 않습니다.

## 신고·제재 조회의 검토 범위

신고 사유는 모바일 커뮤니티의 네 가지 분류(스팸 또는 사기, 괴롭힘 또는 욕설, 오해를 부르는 투자 주장, 기타)를 따릅니다. 채널 강퇴는 해당 채널의 재참여 차단을 포함하며, 차단을 해제해도 자동 복귀하지 않습니다.

신고자 정보와 신고 메모·메시지 원문·첨부는 이 목업에 포함하지 않습니다. 개인 차단과 포지션 경고는 제재 통계에서 제외합니다. 신고만으로 메시지를 자동 숨김·삭제하지 않으며, 신고자 결과 알림과 실제 제재 실행 기능도 없습니다.

신고 현황을 뷰어에게 공개하는 범위, 처리 단계·이력 필드, 운영 제재의 세부 적용 범위·해제 기준은 **유스메타 협의를 위한 제안**입니다. Supercycl 운영이 신고를 심사한다는 가정 역시 합의가 필요합니다. 화면의 접수·검토 중·조치 완료·조치 없음 및 적용 중·해제됨은 확정된 운영 절차를 의미하지 않습니다.

신고는 1건씩, 제재는 조치 1건씩 표시합니다. 적용 중 대상 인원은 선택 채널 관련 기록에서 중복 대상을 한 번만 세며, 커뮤니티 전체 제한 등은 각 기록에 적용 범위를 별도로 표기합니다. 현재 채널의 멤버 명단과 과거 운영 기록의 대상은 다를 수 있습니다.

## 수정 후 확인

`git diff --check`로 공백 오류를 확인합니다. 화면이나 스크립트를 변경했다면 브라우저에서 시연 로그인, 두 채널 전환, 변경한 메뉴와 상세 화면, 로그아웃을 확인합니다. 신고·제재 화면을 바꿀 때는 검색·필터와 관련 기록 이동도 확인합니다.

현재 별도 빌드·패키지 설치·테스트 러너는 없습니다. Supercycl Mobile의 생성기나 검증 명령을 이 저장소에서 실행하지 않습니다.

## Git과 게시

GitHub Pages가 `main` 브랜치의 루트(`/`)를 게시합니다. `index.html` 변경을 커밋하고 푸시하면 새 내용이 반영됩니다. `.nojekyll`은 정적 HTML을 그대로 게시하기 위한 파일입니다.

```sh
git status --short
git fetch origin main
git log --oneline origin/main..HEAD
git push origin main
gh run list --repo 5kyo/supercycl-community-viewer --limit 3
```

작업 전에 원격 변경을 확인하고, 검증한 파일을 커밋한 뒤 푸시합니다. 위 명령의 `origin`은 `https://github.com/5kyo/supercycl-community-viewer.git`이어야 합니다. 이 저장소는 `main`에 게시하며 Supercycl Mobile의 `dev`·릴리스 흐름과 별도로 운영합니다.

저장소 소유 계정은 `5kyo`입니다. `gh auth status`와 저장소 쓰기 권한을 확인하고, 사용자가 선택한 GitHub 활성 계정은 유지합니다. 다른 계정의 인증이 필요하면 해당 게시 명령에만 적용하고 인증 값을 파일·로그·Git에 저장하지 않습니다.

배포 후 [GitHub Actions](https://github.com/5kyo/supercycl-community-viewer/actions)의 Pages 작업 성공과 실제 사이트 반영을 확인합니다. 데스크톱 공유본도 갱신할 때는 프로젝트 루트에서 아래 명령을 실행합니다.

```sh
cp index.html ~/Desktop/슈퍼사이클_커뮤니티_뷰어_목업.html
```
