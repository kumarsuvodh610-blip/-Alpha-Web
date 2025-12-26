<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Alpha Web – Safe Search</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Alpha Web is a safe search engine for education, jobs and government services.">
  <meta name="robots" content="index, follow">

  <style>
    body{font-family:Arial;background:#fff;margin:0;padding:20px}
    h1{text-align:center}
    input{width:100%;padding:12px;font-size:16px}
    button{width:100%;padding:12px;margin-top:10px}
    .result{border-bottom:1px solid #ccc;padding:10px 0}
  </style>
</head>

<body>
  <h1>Alpha Web</h1>
  <input type="text" id="search" placeholder="Search education, jobs, govt">
  <button onclick="searchSite()">Search</button>
  <div id="results"></div>

  <script>
    const sites = [
      { title: "UIDAI Aadhaar", url: "https://uidai.gov.in", category: "Govt" },
      { title: "Sarkari Result", url: "https://www.sarkariresult.com", category: "Job" },
      { title: "CBSE", url: "https://cbse.gov.in", category: "Education" },
      { title: "Indian Railways", url: "https://indianrailways.gov.in", category: "Govt" }
    ];

    function searchSite() {
      const q = document.getElementById("search").value.toLowerCase();
      const resultDiv = document.getElementById("results");
      resultDiv.innerHTML = "";

      const filtered = sites.filter(site =>
        site.title.toLowerCase().includes(q)
      );

      if (filtered.length === 0) {
        resultDiv.innerHTML = "<p>No safe results found</p>";
        return;
      }

      filtered.forEach(site => {
        resultDiv.innerHTML += `
          <div class="result">
            <strong>${site.title}</strong><br>
            <a href="${site.url}" target="_blank">${site.url}</a><br>
            <small>${site.category}</small>
          </div>
        `;
      });
    }
  </script>
</body>
</html>