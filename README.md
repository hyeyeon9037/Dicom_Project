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


<li><b>이전/다음 월 변경 시 유효하지 않은 값 처리</b></li>
: 캘린더 데이터 생성/렌더링의 일반적인 과정

<br>
<br>

<li><b>월 데이터 로드</b></li>
: 월 이동 시 발생할 수 있는 오류를 방지하는 사전 작업
<br>

<br>

```javascript
// 이전 달 이동
document.getElementById("prev-month").addEventListener("click", () => {
    currentMonth--; // 월 감소
    if (currentMonth < 0) { 
        currentMonth = 11; // 12월로 설정
        currentYear--;     // 연도 감소
    }
    renderCalendar(currentMonth, currentYear); // 변경된 값으로 달력 렌더링
});

// 다음 달 이동
document.getElementById("next-month").addEventListener("click", () => {
    currentMonth++; // 월 증가
    if (currentMonth > 11) { 
        currentMonth = 0;  // 1월로 설정
        currentYear++;     // 연도 증가
    }
    renderCalendar(currentMonth, currentYear); // 변경된 값으로 달력 렌더링
});
```

🔎 currentMonth 값의 범위를 명확히 제어하는 로직을 추가하여 월 이동 시 발생할 수 있는 유효하지 않은 값 문제를 해결 <br>
🔎 currentMonth 값의 범위를 명확히 제어하는 로직 추가를 통해 이전/다음 월 이동 시 유효하지 않은 값 발생 문제를 방지




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

<br><br>

<h3><img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Objects/Bell.png" alt="Bell" width="25" height="25" /><b>개발 이슈</b></h3>

<li> <b>데이터 로드 실패</b></li>

<br>
 
```javascript
(() => {
     // studyKey와 seriesKey를 URL에서 추출하여 리포트를 가져오기
    const param = new URLSearchParams(window.location.search);
    const studyKey = param.get("studyKey");
    const seriesKey = param.get("seriesKey");
   
    // 리포트 로드
    axios.get(`/api/report/${studyKey}/${seriesKey}`)
        .then((response) => {
            const report = response.data;
            if (report) {
                // 데이터가 있으면 필드에 채우기
                document.getElementById("comment").value = report.reComment || "";
                document.getElementById("exploration").value = report.reExploration || "";
                document.getElementById("conclusion").value = report.reConclusion || "";
                document.getElementById("recommendation").value = report.reRecommendation || "";
            } else {
                // 데이터가 없으면 초기화
                document.getElementById("comment").value = "";
                document.getElementById("exploration").value = "";
                document.getElementById("conclusion").value = "";
                document.getElementById("recommendation").value = "";
            }
        })
        .catch((error) => {
            console.error("리포트 로드 오류:", error);
        });
})();
```

🔎 데이터로드 시 예외 처리 추가
<br> : 데이터를 로드하지 못했을 경우, 폼 필드를 초기화하여 오류 발생을 방지함

<br>

<li> <b>데이터 저장 실패 </b></li>

<br>

```javascript
function saveKeyReport() {
    const comment = document.getElementById("comment").value;
    const exploration = document.getElementById("exploration").value;
    const conclusion = document.getElementById("conclusion").value;
    const recommendation = document.getElementById("recommendation").value;

    const param = new URLSearchParams(window.location.search);
    const studyKey = param.get("studyKey");
    const seriesKey = param.get("seriesKey");

    // 리포트 저장
    axios.post('/api/saveReport', {
        studyKey: studyKey,
        seriesKey: seriesKey,
        reComment: comment,
        reExploration: exploration,
        reConclusion: conclusion,
        reRecommendation: recommendation
    })
        .then((response) => {
            if (response.status === 200) {
                alert("저장되었습니다.");
            } else {
                alert("저장에 실패했습니다.");
            }
        })
        .catch((error) => {
            console.error("오류 발생:", error);
            alert("저장 중 오류가 발생했습니다.");
        });
}
```

<br>

🔎 데이터 저장 시 유효성 검사
<br> : 저장 요청 전에 필수 값(studyKey, seriesKey)의 유효성을 확인과 저장 요청 결과에 따라 사용자에게 성공 또는 실패 메시지 제공하여 오류 해결
 


</ul>
