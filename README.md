# DrivingLog
Zero-Emission vehicle driving data collection

<!DOCTYPE html>
<html>
<head>
  <title>Driving Log - Volvo BEV</title>
</head>
<body>
  <h2>Submit Your Info</h2>
  <form id="myForm">
    <input type="text" name="name" placeholder="Name"><br><br>
    <input type="text" name="email" placeholder="Email"><br><br>
    <input type="text" name="message" placeholder="Message"><br><br>
    <button type="submit">Submit</button>
  </form>

  <p id="status"></p>

  <script>
    const form = document.getElementById("myForm");
    const status = document.getElementById("status");

    form.addEventListener("submit", async (e) => {
      e.preventDefault();

      const formData = new FormData(form);
      const data = {};
      formData.forEach((value, key) => (data[key] = value));

      status.innerText = "Submitting...";

      try {
        const response = await fetch("https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec", {
          method: "POST",
          body: JSON.stringify(data),
          headers: {
            "Content-Type": "application/json",
          },
        });

        const result = await response.text();
        status.innerText = "Submitted successfully!";
        form.reset();
      } catch (error) {
        status.innerText = "Submission failed. Try again.";
        console.error(error);
      }
    });
  </script>
</body>
</html>

