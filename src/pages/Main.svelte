<script>
  import App from "../App.svelte";

  let currentPositionX = 0; // 현재 이미지의 X축 위치
  let currentPositionY = 0; // 현재 이미지의 Y축 위치
  let imageWidth = 100; // 이미지의 너비
  let imageHeight = 100; // 이미지의 높이
  let windowWidth = window.innerWidth * 3; // 화면의 너비
  let windowHeight = window.innerHeight * 7; // 화면의 높이
  let currentImg = "right.png"; // 움직이는 이미지

  // 키보드 이벤트 핸들러 함수
  function handleKeyDown(event) {
    // 오른쪽 방향키를 누르면
    if (event.key === "ArrowRight") {
      currentPositionX += 10; // 오른쪽으로 10px 이동
      // 오른쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionX > windowWidth - imageWidth) {
        currentPositionX = windowWidth - imageWidth;
      }
      currentImg = "right.png";
    }
    // 왼쪽 방향키를 누르면
    else if (event.key === "ArrowLeft") {
      currentPositionX -= 10; // 왼쪽으로 10px 이동
      // 왼쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionX < 0) {
        currentPositionX = 0;
      }
      currentImg = "left.png";
    }
    // 아래쪽 방향키를 누르면
    else if (event.key === "ArrowDown") {
      currentPositionY += 10; // 아래로 10px 이동
      // 아래쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionY > windowHeight - imageHeight) {
        currentPositionY = windowHeight - imageHeight;
      }
      currentImg = "bottom.png";
    }
    // 위쪽 방향키를 누르면
    else if (event.key === "ArrowUp") {
      currentPositionY -= 10; // 위로 10px 이동
      // 위쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionY < 0) {
        currentPositionY = 0;
      }
      currentImg = "top.png";
    }

    // 화면을 캐릭터 위치에 따라 이동
    window.scrollTo(currentPositionX, currentPositionY);
  }

  // 키보드 이벤트 리스너 등록
  window.addEventListener("keydown", handleKeyDown);

  // 이미지의 스타일을 동적으로 계산
  $: imageStyle = `position: absolute; left: ${currentPositionX}px; top: ${currentPositionY}px;`;
</script>

<header>
  <div class="background-img">
    <img class="character" src={currentImg} alt="" style={imageStyle} />
  </div>
</header>

<!-- <script>
  let currentPositionX = 0; // 현재 이미지의 X축 위치
  let currentPositionY = 0; // 현재 이미지의 Y축 위치
  const imageWidth = 100; // 이미지의 너비
  const imageHeight = 100; // 이미지의 높이
  let backgroundImageWidth = 0; // 배경 이미지의 너비
  let backgroundImageHeight = 0; // 배경 이미지의 높이
  let currentImg = "right.png";

  // 배경 이미지의 크기를 가져오는 함수
  function getBackgroundImageSize() {
    const backgroundImg = document.querySelector(".character");
    backgroundImageWidth = backgroundImg.width;
    backgroundImageHeight = backgroundImg.height;
  }

  // 화면 로드 시 배경 이미지의 크기를 가져옴
  window.onload = getBackgroundImageSize;

  // 키보드 이벤트 핸들러 함수
  function handleKeyDown(event) {
    // 오른쪽 방향키를 누르면
    if (event.key === "ArrowRight") {
      currentPositionX += 10; // 오른쪽으로 10px 이동
      // 오른쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionX > backgroundImageWidth - imageWidth) {
        currentPositionX = backgroundImageWidth - imageWidth;
      }
    }
    // 왼쪽 방향키를 누르면
    else if (event.key === "ArrowLeft") {
      currentPositionX -= 10; // 왼쪽으로 10px 이동
      // 왼쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionX < 0) {
        currentPositionX = 0;
      }
    }
    // 아래쪽 방향키를 누르면
    else if (event.key === "ArrowDown") {
      currentPositionY += 10; // 아래로 10px 이동
      // 아래쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionY > backgroundImageHeight - imageHeight) {
        currentPositionY = backgroundImageHeight - imageHeight;
      }
    }
    // 위쪽 방향키를 누르면
    else if (event.key === "ArrowUp") {
      currentPositionY -= 10; // 위로 10px 이동
      // 위쪽 끝에 닿으면 화면을 벗어나지 않도록 위치를 조정
      if (currentPositionY < 0) {
        currentPositionY = 0;
      }
    }
  }

  // 키보드 이벤트 리스너 등록
  window.addEventListener("keydown", handleKeyDown);

  // 이미지의 스타일을 동적으로 계산
  $: imageStyle = `position: absolute; left: ${currentPositionX}px; top: ${currentPositionY}px;`;
</script>

<header>
  <div class="background-img">
    <img class="character" src={currentImg} alt="" style={imageStyle} />
  </div>
</header> -->
