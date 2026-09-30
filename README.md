# UiPath 거래처 정보 업데이트

Gmail에서 `Update.xlsx`를 다운로드하고, 국세청 홈택스에서 사업자등록 상태를 조회한 뒤 `Master - 원본.xlsx`를 갱신하여 Gmail로 회신하는 UiPath RPA 실습 프로젝트입니다.

## 주요 기능

1. Gmail의 읽지 않은 대상 메일 조회
2. `Update.xlsx` 첨부파일 다운로드
3. `상태`, `업데이트 일자` 열 초기화
4. 홈택스 사업자등록 상태 조회
5. 조회 결과를 Update Excel에 기록
6. Master Excel의 기존 거래처 갱신 또는 신규 거래처 추가
7. 폐업 거래처를 `폐업` 시트에 반영
8. 최종 Master Excel을 Gmail로 전송

## 프로세스 구조

```text
Main.xaml
├─ Gmail 메일 조회 및 첨부파일 다운로드
├─ Update.xlsx 초기 설정
├─ 홈택스 사업자 상태 조회
├─ Master.xlsx 비교 및 반영
└─ 결과 메일 전송
```

## 실행 환경

- UiPath Studio 2024.10 계열 이상
- Windows 프로젝트
- Google Chrome
- Microsoft Excel
- Gmail 연결

UiPath 패키지 버전은 `project.json`에 정의되어 있습니다.

## 실행 전 설정

1. UiPath Studio에서 `project.json`을 열어 패키지를 복원합니다.
2. `Main.xaml`의 두 `Use Gmail` 액티비티에 본인 Gmail 계정을 연결합니다.
3. `Send Email`의 수신자 `your-email@example.com`을 실제 수신 주소로 변경합니다.
4. Gmail 받은편지함에 `Update.xlsx`가 첨부된 읽지 않은 대상 메일을 준비합니다.
5. `Data/Input/Master - 원본.xlsx`의 필요 초기 데이터를 입력합니다.
6. Chrome에서 홈택스 사업자상태 조회 화면에 정상 접근되는지 확인합니다.

## 파일 경로

실행 파일은 프로젝트 폴더를 기준으로 한 상대 경로를 사용합니다.

```text
Data/Input/Update.xlsx
Data/Input/Master - 원본.xlsx
```

`Update.xlsx`는 실행 중 Gmail에서 다운로드되며 Git에 추적되지 않습니다.

## 공개 저장소 데이터 정책

- Gmail 계정은 `your-email@example.com`으로 대체했습니다.
- Master Excel은 컬럼과 시트 구조만 유지한 빈 템플릿입니다.
- 실제 거래처명, 사업자번호, 전화번호, 주소는 포함하지 않습니다.
- Gmail 인증 정보, 비밀번호, 토큰은 저장소에 커밋하지 않습니다.

## 주의사항

- 홈택스 화면·Selector가 변경되면 UI 액티비티의 대상을 다시 지정해야 할 수 있습니다.
- 메일 조회는 읽지 않은 메일과 `Update.xlsx` 첨부파일을 기준으로 작동합니다.
- 실제 운영 데이터는 공개 저장소에 추가하지 마세요.
