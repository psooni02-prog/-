# 헬스장 직원 체크리스트

## 포함 파일
- `index.html`: 모바일 대응 체크리스트 웹사이트
- `supabase_setup.sql`: 날짜별 클라우드 저장 테이블 및 접근 정책

## 1) 바로 테스트하기
`index.html` 파일을 브라우저에서 여세요. 직원명, 날짜, 근무 구분을 입력하고 체크한 뒤 **저장하기**를 누르면 현재 브라우저에 저장됩니다.
이 방식은 해당 브라우저에만 저장되므로 다른 기기에서 공유되지 않습니다. 중요한 기록은 CSV로 내보내 백업하세요.

## 2) 여러 기기에서 기록 공유하기 (권장)
1. Supabase 프로젝트를 생성하세요.
2. Supabase 대시보드의 SQL Editor에서 `supabase_setup.sql` 내용을 실행하세요.
3. Authentication에서 직원별 계정을 생성하세요. 공개 회원가입은 꺼두는 편을 권장합니다.
4. Project Settings > API에서 Project URL과 공개용 anon/publishable key를 확인하세요.
5. 사이트의 `index.html`에서 클라우드 저장 설정에 URL과 공개용 키를 입력하고 **클라우드 연결**을 누르세요.
6. 직원 계정 이메일/비밀번호로 로그인한 뒤 기록을 저장하고 검색하세요.

### 보안 주의
- `service_role` / secret key를 브라우저 코드에 절대 넣지 마세요.
- SQL 정책은 로그인한 직원 모두가 같은 기록을 조회·수정할 수 있게 합니다. 직원별 권한을 더 세밀하게 나누려면 정책을 조정하세요.
- 기록 수정 시 현재 불러온 기록을 업데이트합니다. 새 근무 기록을 작성할 때는 새 날짜/직원/근무 기록인지 확인하세요.

## 3) GitHub Pages 배포
1. GitHub에서 새 저장소(repository)를 만드세요.
2. `index.html`을 저장소 최상위(root)에 올리세요.
3. 저장소의 Settings > Pages로 이동하세요.
4. Build and deployment에서 `Deploy from a branch`를 선택하고 `main` 브랜치와 `/(root)`를 선택해 저장하세요.
5. 표시되는 Pages 주소로 접속해 테스트하세요.

Supabase URL과 공개용 anon/publishable key는 브라우저에 입력하거나 코드에 넣어도 되는 공개용 값이지만, 실제 데이터 접근은 반드시 Supabase 로그인 및 RLS 정책으로 제한하세요.
