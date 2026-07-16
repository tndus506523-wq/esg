# ESG Overnight at 다락재 — 최종 실시간 배포판

## 구성 파일

- `index.html`: 행사 사이트 본체
- `firebase-config.js`: Firebase 웹 앱 설정값
- `firestore.rules`: Firestore 보안 규칙
- `images/`: 첫 화면 추억 사진 13장

## 이번 버전의 주요 기능

- 13장의 추억 사진을 첫 화면 폴라로이드와 가로 갤러리로 표시
- 사진 클릭 시 확대 보기
- 6명의 휴대폰에서 사전 Mission 제출 현황 실시간 동기화
- 진행자의 Activity Room `다음/공개` 조작 실시간 동기화
- 사전 Mission은 이름별 **최초 1회만 제출 가능**
- 제출 후 수정·재제출·삭제 차단
- 마니또는 본인을 제외한 멤버로 1:1 배정
- 2026년 7월 25일 23:00(KST)에 결과 화면 오픈
- 결과 화면에서 다음 항목 공개
  - 가장 일찍 잘 것으로 예측된 사람
  - 멤버별 득표수
  - 마니또 전체 매칭

## 1. Firebase 설정

1. Firebase Console에서 새 프로젝트를 만듭니다.
2. **프로젝트 설정 → 내 앱 → 웹 앱 추가**를 선택합니다.
3. 표시되는 `firebaseConfig` 값을 `firebase-config.js`에 복사합니다.
4. **Authentication → Sign-in method → Anonymous**를 활성화합니다.
5. **Firestore Database → Create database**로 데이터베이스를 생성합니다.
6. Firestore의 **Rules** 탭에 `firestore.rules` 내용을 전부 붙여 넣고 게시합니다.
7. Authentication의 **Settings → Authorized domains**에
   `본인아이디.github.io`를 추가합니다.

## 2. GitHub Pages 배포

1. GitHub에서 새 저장소를 만듭니다. 예: `esg-darakjae`
2. ZIP의 내용물을 압축 해제합니다.
3. 아래 항목을 저장소 최상위에 그대로 업로드합니다.
   - `index.html`
   - `firebase-config.js`
   - `images` 폴더 전체
   - 선택 사항: `README.md`, `firestore.rules`
4. 저장소의 **Settings → Pages**로 이동합니다.
5. Source는 **Deploy from a branch**를 선택합니다.
6. Branch는 `main`, 폴더는 `/(root)`를 선택하고 저장합니다.
7. 주소는 보통 아래와 같습니다.

   `https://본인아이디.github.io/esg-darakjae/`

## 3. 휴대폰 접속 및 운영

1. GitHub Pages 주소를 카카오톡 단체방에 공유합니다.
2. 각자 본인의 휴대폰으로 접속합니다.
3. 이름을 선택하고 모든 항목을 검토한 뒤 한 번만 제출합니다.
4. 제출이 완료되면 마니또가 개인 화면에 표시됩니다.
5. 행사 당일 진행자 한 명이 Activity Room의 다음·공개 버튼을 조작합니다.
6. 다른 휴대폰에도 동일한 Activity 카드와 공개 상태가 실시간 반영됩니다.
7. 7월 25일 밤 11시 이후 `예측·마니또 결과 공개하기` 버튼을 누릅니다.

## 중요 주의 사항

- 제출은 이름별 최초 1회만 가능합니다.
- 제출 이후 오타나 답변을 수정할 수 없습니다.
- Firestore 규칙도 update/delete를 거부하므로, 관리자도 Firebase Console에서 직접 문서를 삭제하지 않는 한 웹 화면에서 수정할 수 없습니다.
- 이름을 잘못 선택하면 해당 이름의 제출 기회가 소진되므로 반드시 확인해야 합니다.
- 결과 오픈 시간은 화면상 KST 2026-07-25 23:00으로 설정되어 있습니다.
- 클라이언트 기반 소규모 행사 도구이므로 고도의 보안이 필요한 비밀 투표 용도로는 적합하지 않습니다.
