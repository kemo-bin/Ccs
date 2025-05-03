<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <title>Send Email</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <form id="form">
    <div class="field">
      <label for="time">time</label>
      <input type="text" name="time" id="time" />
    </div>
    <div class="field">
      <label for="email">email</label>
      <input type="text" name="email" id="email" />
    </div>
    <input type="submit" id="button" value="Send Email" />
  </form>

  <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
  <script type="text/javascript">
    emailjs.init("AkXxMxJH1PnvTsS3e");
    const btn = document.getElementById("button");
    document.getElementById("form").addEventListener("submit", function (event) {
      event.preventDefault();
      btn.value = "Sending...";
      const serviceID = "default_service";
      const templateID = "template_7m1lh0f";
      emailjs.sendForm(serviceID, templateID, this).then(
        () => {
          btn.value = "Send Email";
          alert("Sent!");
        },
        (err) => {
          btn.value = "Send Email";
          alert(JSON.stringify(err));
        }
      );
    });
  </script>
</body>
</html>
