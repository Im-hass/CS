### 📌 브라우저 렌더링 과정

> **렌더링이란, 브라우저가 서버로부터 요청해 받은 내용(HTML, CSS, JS)을 브라우저 화면에 표시해 주는 작업을 말한다.**
> 
1. **[Parsing]** HTML과 CSS 파일을 파싱하여 각각 Tree를 생성한다.
    - DOM Tree, CSSOM Tree 생성
2. **[Style]** 두 Tree를 결합하여 Rendering Tree를 생성한다.
3. **[Layout]** Rendering Tree에서 각 Node의 크기와 위치를 계산한다.
4. **[Paint]** 계산된 값을 이용하여 각 노드를 화면상의 실제 픽셀로 변환하고 Layer를 만든다.
5. **[Composite]** Layer를 합성하여 실제 화면에 나타낸다.
