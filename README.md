<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        .container {
            background-color: #1e272e;
            color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 20px 35px 35px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
            text-align: center;
            max-width: 400px;
            width: 100%;
            margin: auto;
            font-family: Arial, sans-serif;
        }
        input, button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
            border-radius: 5px;
            border: none;
        }
        button {
            background-color: green;
            color: white;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Age Calculator</h1>
    <label for="birthdate">Enter your birthdate:</label>
    <input type="date" id="birthdate">
    <button id="calculateBtn">Calculate Age</button>
    <p id="result"></p>
</div>

<script>
document.getElementById("calculateBtn").addEventListener("click", function() {
    let birthdateInput = document.getElementById("birthdate").value;
    
    if (!birthdateInput) {
        document.getElementById("result").innerText = "Please enter a valid date!";
        return;
    }

    let today = new Date();
    let birthDate = new Date(birthdateInput);
    
    let age = today.getFullYear() - birthDate.getFullYear();
    let monthDifference = today.getMonth() - birthDate.getMonth();
    let dayDifference = today.getDate() - birthDate.getDate();

    // Adjust age if the birthdate hasn't occurred yet this year
    if (monthDifference < 0 || (monthDifference === 0 && dayDifference < 0)) {
        age--;
    }

    document.getElementById("result").innerText = "You are"+ age + "years old.";
});
</script>

</body>
</html>
