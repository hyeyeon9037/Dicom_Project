<h1>📃 프로젝트 정보<br> </h1>

<h3>1. 제작 기간 <br></h3>
2024.10.07 ~ 2024.11.25

<h3>2. 프로젝트 멤버</h3>

|Name|Position|explanation|
|------|---|---|
|현민환(팀장)|Back||
|김광훈|Back||
|박혜연|Back, Front|회원가입&로그인, 캘린더, 리포트, UI|
|유병수|Back, Front||


<h3> 
3. 프로젝트 소개<br></h3>
<b> HealScope </b> <br>
<b> : 의료(Healing)과 스코프(Scope)의 조합으로 질환을 관찰하며 치유를 돕는다는 의미입니다.</b> <br> <br>
<ul>
  <li>사용자 접근성을 최우선으로 고려한 의료 정보 통합 플랫폼 구현</li>
  <li>의료 정보를 한눈에 확인할 수 있는 직관적인 통합 정보 시스템 제공</li>
  <li>의료 협업과 연구를 촉진하는 원활한 커뮤니케이션 및 파일 공유 기능 추가</li>
</ul>

<br><br>


<ul>
<h2>회원가입 & 로그인</h2>

<img src="https://github.com/user-attachments/assets/408a3e8f-1313-4fe7-a5ba-51a841f595a9">
<br><br>

📍 기능구현
<br><br>


🔑<b> 회원가입</b>
<br>

<img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Paperclip.png" alt="Paperclip" width="25" height="25" /> <b> 회원정보 입력 및 전송</b>
<li>PasswordEncoder로 암호화 후 저장</li>
<li>Axios를 사용해 /signUp API로 POST 요청 전송</li>

<br>

<img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Paperclip.png" alt="Paperclip" width="25" height="25" /> <b>중복 확인</b>
<li>LoginRepository를 통해 ID 중복 여부 검사</li>

<br><br>

🔑 <b>로그인</b>
<br>

<img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Paperclip.png" alt="Paperclip" width="25" height="25" /> <b> Spring Security를 활용한 로그인 구성</b>
<li><b>HttpSecurity 설정</b></li>
: Spring Security를 활용하여 URL 접근 권한을 설정
<br>
<br>
<li><b>BCrypt 기반 비밀번호 암호화</b></li> 
: PasswordEncoder를 Bean으로 등록하여 비밀번호를 BCrypt 해시 알고리즘으로 암호화 및 검증
<br> (PasswordEncoderFactories.createDelegatingPasswordEncoder()로 BCrypt 알고리즘을 설정)

<br><br>

<h2>캘린더</h2>

![ezgif com-video-to-gif-converter (3)](https://github.com/user-attachments/assets/4423df88-2e1d-4566-91cf-f87f214f9d20)

<br>

📍 기능구현
<br>

이 프로젝트의 캘린더 기능은 주로 순수 JavaScript를 사용하여 구현되었으며, 년도 선택에 한해 사용자 경험을 개선하기 위해 최소한의 라이브러리를 사용하였습니다.

<br>

📅 <b> 년도 달력 렌더링</b>
<li>Flatpickr 라이브러리를 활용하여 년도 선택 UI를 렌더링</li>
<li>월별 이전/다음 버튼을 통해 달 이동이 가능하며, 선택된 날짜를 강조 표시</li>

<br>

📅 <b> 날짜 범위 선택</b>
<br> : 날짜 선택 및 범위 설정은 라이브러리 없이 순수 JavaScript와 DOM API로 구현<br>
<li>날짜를 클릭하면 시작일과 종료일을 설정</li>
<li>전체, 1일, 3일, 1주일 버튼을 눌러 날짜 범위를 간편하게 설정 가능</li>
<li>highlightSelectedRange 함수를 이용해 선택된 날짜 범위를 시각적으로 표시</li>

<br>
📅 <b> 데이터 바인딩</b>
<li>선택한 날짜가 입력 필드(start-date, end-date)에 자동 반영</li>

<br>

<h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Bell.png" alt="Bell" width="25" height="25" /><b>개발 이슈</b></h3>


<b>이전/다음 월 변경 시 유효하지 않은 값 처리</b>
<br>
🔎 currentMonth 값의 범위를 명확히 제어하는 제어문을 추가해 오류 해결

<br>

<b>월 데이터 로드</b>
<br>
🔎 



  <br><br>
  
<h2>리포트</h2>

![ezgif com-video-to-gif-converter (4)](https://github.com/user-attachments/assets/0a66705e-dd19-4a88-9618-a9cfb4fe2883)

<br>

📍 기능구현
<br>

🎫 <b> 데이터 로드및 표시</b>
<li>axios.get을 사용해 서버에서 데이터를 받아와 UI에 렌더링</li>
<li>코멘트, 탐색, 결론, 권장사항 등의 필드에 자동으로 값 채우기</li>

<br>

🎫 <b> 데이터 저장</b>
<li>axios.post를 통해 작성된 데이터를 서버로 전송하며 저장 성공/실패 메시지를 제공 </li>

<br>

🎫 <b> 검사 키 기반 데이터 관리</b>
<li>studyKey 및 seriesKey를 통해 데이터를 개별적으로 관리하여 유연한 API 요청 구현 </li>

</ul>
