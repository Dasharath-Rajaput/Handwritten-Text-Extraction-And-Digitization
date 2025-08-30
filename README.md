# Handwritten-Text-Extraction-And-Digitization
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hand Written Text Extraction And Digitization</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
      background: rgb(1, 40, 64);
    }

    button {
      padding: 15px 30px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      margin: 20px;
      cursor: pointer;
      background-color: #4a90e2;
      color: white;
    }

    button:hover {
      background-color: #0c87f3;
    }

    #backBtn {
      position: absolute;
      top: 20px;
      left: 20px;
      background-color: rgb(4, 136, 243);
      font-size: 16px;
      padding: 10px 20px;
    }

    #languagePage, #uploadPage {
      display: none;
      padding-top: 100px;
    }

    #languagePage {
      display: block;
    }

    .upload-box {
      background: rgb(5, 180, 233);
      padding: 40px;
      margin: auto;
      width: 90%;
      max-width: 500px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(8, 208, 141, 0.2);
    }

    .upload-box h2 {
      margin-bottom: 20px;
    }

    .upload-box input[type="file"] {
      margin: 20px 0;
    }

    #preview {
      display: none;
      margin-top: 10px;
      max-width: 100%;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
  </style>
</head>
<body>

  <!-- Language Selection Page -->
  <div id="languagePage">
    <h1 style="color: white;">Select Language</h1>
    <button onclick="openUploadPage('Kannada')">Kannada</button>
    <button onclick="openUploadPage('English')">English</button>
  </div>

  <!-- Upload Page -->
  <div id="uploadPage">
    <button id="backBtn" onclick="goBack()">⬅ Back</button>
    <div class="upload-box">
      <h2 style="color: white; background-color: rgb(4, 135, 243);">Upload Your Image</h2>
      <p id="selectedLang" style="color: white;"></p>

      <!-- Camera or file input -->
      <input type="file" id="imageInput" accept="image/*" capture="environment" onchange="previewImage(event)" />
      
      <!-- Preview image -->
      <img id="preview" alt="Image Preview" />

      <br>
      <button onclick="Submit()" style="color: white; background-color: rgb(4, 135, 243);" >Submit</button>
    </div>
  </div>

  <script>
    let selectedLanguage = "";

    function openUploadPage(language) {
      document.getElementById('languagePage').style.display = 'none';
      document.getElementById('uploadPage').style.display = 'block';
      selectedLanguage = language;
      document.getElementById('selectedLang').textContent = "Selected Language: " + language;
    }

    function goBack() {
      document.getElementById('uploadPage').style.display = 'none';
      document.getElementById('languagePage').style.display = 'block';
      document.getElementById('preview').style.display = 'none';
      document.getElementById('imageInput').value = '';
    }

    function previewImage(event) {
      const preview = document.getElementById('preview');
      const file = event.target.files[0];

      if (file) {
        preview.src = URL.createObjectURL(file);
        preview.style.display = 'block';
      } else {
        preview.style.display = 'none';
      }
    }

    function Submit() {
      const input = document.getElementById('imageInput');
      if (!input.files.length) {
        alert("Please select or capture an image first.");
        return;
      }

      alert(`Processing image for ${selectedLanguage} language...`);
      // Yaha backend OCR code ka API call karna hoga
      // Example: fetch('/process', { method: 'POST', body: formData })...
    }
  </script>

</body>
</html>
