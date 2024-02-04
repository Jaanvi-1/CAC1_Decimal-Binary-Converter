# CAC1_Decimal-Binary-Converter
#INDEX.HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Decimal-Binary Converter</title>
    <!-- Google Fonts -->
    <link
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap"
      rel="stylesheet"
    />
    <!-- Stylesheet -->
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="background-image"></div>
    <div class="container">
      <h2>Decimal Binary Converter</h2>
      <div class="wrapper">
        <div class="input-wrapper">
          <label for="dec-inp">Decimal:</label>
          <input type="number" id="dec-inp" />
        </div>
        <div class="input-wrapper">
          <label for="bin-inp">Binary:</label>
          <input type="number" id="bin-inp" />
        </div>
      </div>
      <p id="error-msg"></p>
    </div>

    <!-- Script -->
    <script src="script.js"></script>
  </body>
</html>

#STYLE.CSS
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: "Times New Roman", sans-serif;
  }
  body {
    background-color: goldenrod;
  }
  .background-image {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsEFHekrTFBYwi9ehTK0an05V_Il6S8KA2Tw&usqp=CAU'); 
    background-size: cover;
    background-position: center;
    filter: brightness(0.7); 
    z-index: -1; 
  }
  .container {
    background-color: rgb(0, 255, 255);
    width: 80vmin;
    max-width: 37.5em;
    padding: 3em 2.5em;
    position: absolute;
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    border-radius: 0.62em;
    box-shadow: 0 1.2em 2.5em rgba(0, 21, 44, 0.18);
  }
  h2 {
    font-size: 1.8em;
    color: rgb(20, 19, 19);
    text-align: center;
    font-weight: 600;
    letter-spacing: 0.5px;
    margin-bottom: 1.3em;
  }
  .wrapper {
    display: flex;
    justify-content: space-between;
    gap: 1.8em;
  }
  label {
    display: block;
    margin-bottom: 0.5em;
    font-weight: 500;
    color: #050121;
  }
  input {
    position: relative;
    font-size: 1.1em;
    width: 100%;
    padding: 0.5em;
    border-radius: 0.2em;
    border: 1.5px solid #43405c;
    color: #43405c;
    outline: none;
  }
  input:focus {
    border-color: #0075ff;
  }
  #error-msg {
    text-align: center;
    margin-top: 1.25em;
    color: #ff4362;
  }
  .container::before {
    content: "😄"; 
    font-size: 3em;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    color: #fff; 
    z-index: 1;
  }

#SCRIPT.JS
// Initial References
let decInp = document.getElementById("dec-inp");
let binInp = document.getElementById("bin-inp");
let errorMsg = document.getElementById("error-msg");

// Convert decimal to binary when user inputs in the decimal field
decInp.addEventListener("input", () => {
  let decValue = parseInt(decInp.value);
  // Converts the decimal value to binary
  binInp.value = decValue.toString(2);
});

// Convert binary to decimal when user inputs in the binary field
binInp.addEventListener("input", () => {
  let binValue = binInp.value;
  // If the binary number is valid convert it to decimal
  if (binValidator(binValue)) {
    decInp.value = parseInt(binValue, 2);
    errorMsg.textContent = "";
  }
  // Else display an error message
  else {
    errorMsg.textContent = "Please Enter A Valid Binary Input";
  }

  // Function to check if the binary number is valid i.e it does not contain any number other than 0 and 1
  function binValidator(num) {
    for (let i = 0; i < num.length; i++) {
      if (num[i] != "0" && num[i] != "1") {
        return false;
      }
    }
    return true;
  }
});
