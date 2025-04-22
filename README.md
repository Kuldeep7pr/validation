<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Password Validation</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.5/dist/css/bootstrap.min.css" rel="stylesheet" />
</head>

<body>

  <h1 class="text-center text-capitalize mt-3 fs-2 text-success">This is password validation</h1>
  <hr />

  <div class="d-flex justify-content-center">
    <input oninput="validate(this.value)" id="input" type="text" placeholder="Enter your password"
      class="text-center text-capitalize p-2 w-25 rounded-pill border border-success"
      style="box-shadow: 5px 5px 10px green;" />
  </div>

  <div id="output" class="border border-success w-75 m-auto text-center mt-5 p-3 rounded-2"
    style="box-shadow: 5px 5px 10px rgb(255, 0, 0);"></div>

  <div class="d-flex justify-content-center">
    <div id="success" class="text-center mt-5 bg-primary-subtle w-25 text-capitalize p-3 rounded"></div>
  </div>

  <script>
    function validate(value) {
      const output = document.getElementById('output');
      const success = document.getElementById('success');

      output.innerHTML = "";
      success.innerHTML = "";

      const errors = [];

      if (value.length < 8) {
        errors.push("At least 8 characters");
      }

      if (!/[A-Z]/.test(value)) {
        errors.push("At least one uppercase letter");
      }

      if (!/[a-z]/.test(value)) {
        errors.push("At least one lowercase letter");
      }

      if (!/[0-9]/.test(value)) {
        errors.push("At least one number");
      }

      if (!/[^A-Za-z0-9]/.test(value)) {
        errors.push("At least one special character");
      }

      if (errors.length > 0) {
        output.innerHTML = "❌ " + errors.join("<br>❌ ");
      } else {
        success.innerHTML = "✅ Strong password!";
      }
    }
  </script>

</body>

</html>
