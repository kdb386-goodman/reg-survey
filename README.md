# 회원사 설문 랜딩 페이지

협회가 회원사에 배포할 링크의 도착 지점이다.

## 현재 상태 (2026-09-12)

| | |
|---|---|
| 저장소 | `kdb386-goodman/reg-survey` — **비공개** |
| GitHub Pages | **꺼짐** |
| 공개 예정 주소 | `https://kdb386-goodman.github.io/reg-survey/` |
| Google Form | 완성, 연결됨 |
| 응답 스프레드시트 | 연결됨 |

공정거래위원회 협조문 확정본을 받기 전까지 비공개로 둔다. 확정되면
`go_public.ps1` 한 번으로 공개 전환 + Pages 활성화 + `.env` 기록까지 끝난다.

```powershell
powershell -ExecutionPolicy Bypass -File go_public.ps1 -WhatIf   # 확인만
powershell -ExecutionPolicy Bypass -File go_public.ps1           # 실행
```

`go_public.ps1`은 저장소에 올리지 않는다(.gitignore). 공개 직전에 올라간 파일이
`index.html` · `privacy.html` · `README.md` · `.gitignore` 넷뿐인지 스스로 검사한다.

## 연결된 값

```js
var FORM_URL  = "https://docs.google.com/forms/d/e/1FAIpQLScQ6IliwpvM32RtRb9gj18cLwX-QjAck0lQvF7_OiJe-_Fw7Q/viewform";
var ENTRY_SRC = "entry.1815859227";   // MEM-SRC 문항
```

`?src=koraia` 로 들어오면 폼의 `이 설문을 안내받은 경로 [MEM-SRC]` 칸에 `koraia`가
자동으로 채워진다. 실제로 확인했다.

## 협회별 링크
`?src=` 뒤에 협회 코드를 붙이면 유입 경로가 폼에 자동 기록된다.

| 협회 | 배포 링크 |
|---|---|
| 한국인공지능협회 | `…/reg-survey/?src=koraia` |
| 코리아스타트업포럼 | `…/reg-survey/?src=kstartup` |
| 한국핀테크산업협회 | `…/reg-survey/?src=korfin` |
| 한국AI·로봇산업협회 | `…/reg-survey/?src=korearobot` |

만든 링크는 설문대상자 통합 파일 `5.회원사 배포 관리` 시트에 기록한다.

## .env
```
LANDING_URL=https://kdb386-goodman.github.io/reg-survey/
```
`go_public.ps1`이 자동으로 넣는다. 비어 있는 동안에는 회원사 안내문
발송이 차단된다(본문이 완성되지 않으므로).

## 미리 보기
브라우저로 `index.html` 파일을 직접 열면 된다. 서버가 필요 없다.
`FORM_URL`이 비어 있으면 버튼이 "설문 준비 중입니다"로 표시된다.

## 유의사항
- **차단 대비** : 일부 공공기관·협회 망에서 `github.io` 가 막히는 사례가 있다.
  안내문에 폼 직접 주소를 함께 적어 두는 것이 안전하다.
- **개인정보처리방침** : `privacy.html` 은 설문 고지 의무를 위한 것이다.
  구글 OAuth 앱을 프로덕션으로 올릴 때 요구하는 URL로도 쓸 수 있다.
- **다크 모드** : 두 페이지 모두 시스템 설정을 따라간다.
