# Spring MVC 파일 업로드 예제

Spring MVC를 활용한 다양한 방식의 파일 업로드 기능 구현.

## ✨ 주요 기능

* **ex01:** 단일 파일 업로드
    * `onsubmit` 자바스크립트로 파일 크기 및 확장자 유효성 검사 실행.
* **ex02:** 다중 파일 업로드 (`multiple` 속성)
    * `<input type="file" multiple>` 속성을 이용해 여러 파일 동시 선택.
    * `onsubmit`에서 모든 파일의 총합 용량 및 개별 파일 유효성 검사 실행.
* **ex03:** 드래그 앤 드롭(Drag & Drop) 파일 업로드
    * `ondrop` 이벤트를 사용해 파일을 드래그하여 업로드 영역에 추가.
    * 드롭된 파일 목록을 숨겨진 `<input type="file">`에 바인딩하여 폼 전송.
* **ex04:** AJAX 비동기 파일 업로드
    * jQuery와 `FormData` 객체를 사용해 페이지 새로고침 없이 파일 전송.
    * `processData: false`, `contentType: false` 옵션 사용.

## 🛠️ 사용 기술

* **Backend:** Spring MVC, `MultipartFile`
* **Frontend:** JSP, JavaScript, jQuery
* **Server:** Apache Tomcat

## ⚙️ 서버 로직 (FileController.java)

* `@PostMapping`으로 각 폼 요청 처리.
* `MultipartFile` (단일) 또는 `MultipartFile[]` (다중) 객체로 업로드된 파일 수신.
* `getServletContext().getRealPath()`를 사용해 서버의 실제 저장 경로 획득.
* `UUID.randomUUID()`를 이용해 중복되지 않는 고유한 파일명 생성 (파일명 충돌 방지).
* `File.mkdirs()`: 파일 저장 전, 디렉터리가 없으면 자동 생성 (`NoSuchFileException` 방지).
* `attach.transferTo(file)`: 임시 폴더의 파일을 실제 저장 경로로 이동.

## 🚀 실행

1.  프로젝트를 IDE(Eclipse, STS 등)로 임포트.
2.  Maven 의존성 설치.
3.  Apache Tomcat 서버에 프로젝트 배포 후 실행.
4.  웹 브라우저에서 `/file/ex01.do`, `/file/ex02.do` 등으로 접근.
