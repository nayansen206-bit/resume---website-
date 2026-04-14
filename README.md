# resume---website-
<!DOCTYPE html>
<html>
<head>
    <title>AI Resume Generator</title>

    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: white;
            text-align: center;
        }

        h1 {
            margin-top: 20px;
            font-weight: 700;
        }

        .container {
            width: 90%;
            max-width: 500px;
            margin: auto;
            background: rgba(255,255,255,0.05);
            padding: 20px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
        }

        input, textarea {
            width: 100%;
            margin: 8px 0;
            padding: 12px;
            border-radius: 8px;
            border: none;
            outline: none;
        }

        button {
            padding: 12px 25px;
            background: #22c55e;
            border: none;
            color: white;
            cursor: pointer;
            border-radius: 8px;
            font-weight: bold;
            transition: 0.3s;
        }

        button:hover {
            background: #16a34a;
        }

        #resume {
            background: white;
            color: black;
            margin: 30px auto;
            padding: 25px;
            border-radius: 15px;
            display: none;
            max-width: 700px;
            text-align: left;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .header {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .header img {
            border-radius: 50%;
        }

        .section {
            margin-top: 20px;
        }

        .section h3 {
            border-bottom: 2px solid #22c55e;
            padding-bottom: 5px;
        }

    </style>
</head>

<body>

<h1>🚀 AI Resume Generator</h1>

<div class="container">
    <input type="text" id="name" placeholder="Full Name">
    <input type="text" id="email" placeholder="Email">
    <input type="text" id="phone" placeholder="Phone">

    <textarea id="skills" placeholder="Skills"></textarea>
    <textarea id="education" placeholder="Education"></textarea>
    <textarea id="experience" placeholder="Experience"></textarea>

    <input type="file" id="photo">

    <button onclick="generateResume()">Generate Resume</button>
</div>

<div id="resume"></div>

<button onclick="downloadPDF()" id="downloadBtn" style="display:none;">
    Download PDF
</button>

<script>
function generateResume() {
    let name = document.getElementById("name").value;
    let email = document.getElementById("email").value;
    let phone = document.getElementById("phone").value;
    let skills = document.getElementById("skills").value;
    let education = document.getElementById("education").value;
    let experience = document.getElementById("experience").value;

    let photoFile = document.getElementById("photo").files[0];
    let photoURL = photoFile ? URL.createObjectURL(photoFile) : "";

    let resumeHTML = `
        <div class="header">
            ${photoURL ? `<img src="${photoURL}" width="100">` : ""}
            <div>
                <h2>${name}</h2>
                <p>${email}</p>
                <p>${phone}</p>
            </div>
        </div>

        <div class="section">
            <h3>Skills</h3>
            <p>${skills}</p>
        </div>

        <div class="section">
            <h3>Education</h3>
            <p>${education}</p>
        </div>

        <div class="section">
            <h3>Experience</h3>
            <p>${experience}</p>
        </div>
    `;

    let resumeDiv = document.getElementById("resume");
    resumeDiv.innerHTML = resumeHTML;
    resumeDiv.style.display = "block";

    document.getElementById("downloadBtn").style.display = "inline-block";
}

function downloadPDF() {
    window.print();
}
</script>

</body>
</html>
