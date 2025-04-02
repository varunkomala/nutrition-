<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nutrition Requirement Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, select, button {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Nutrition Requirement Calculator</h2>
        <label for="age">Enter Your Age:</label>
        <input type="number" id="age" placeholder="Enter age in years">
        
        <label for="gender">Select Gender:</label>
        <select id="gender">
            <option value="male">Male</option>
            <option value="female">Female</option>
        </select>
        
        <label for="weight">Enter Your Weight (kg):</label>
        <input type="number" id="weight" placeholder="Enter weight in kg">
        
        <label for="height">Enter Your Height (cm):</label>
        <input type="number" id="height" placeholder="Enter height in cm">
        
        <label for="activity">Select Activity Level:</label>
        <select id="activity">
            <option value="sedentary">Sedentary</option>
            <option value="light">Light Activity</option>
            <option value="moderate">Moderate Activity</option>
            <option value="active">Active</option>
        </select>
        
        <button onclick="calculateNutrition()">Calculate RDA</button>
        
        <h3>Recommended Daily Allowance (RDA):</h3>
        <p id="result"></p>
    </div>

    <script>
        function calculateNutrition() {
            let age = document.getElementById("age").value;
            let gender = document.getElementById("gender").value;
            let weight = document.getElementById("weight").value;
            let height = document.getElementById("height").value;
            let activity = document.getElementById("activity").value;
            
            let rdaData = {
                male: { protein: "56g", fat: "70g", water: "3700ml", vitamins: { A: "900mcg", C: "90mg", D: "15mcg", E: "15mg", K: "120mcg", B1: "1.2mg", B2: "1.3mg", B3: "16mg", B5: "5mg", B6: "1.3mg", B7: "30mcg", B9: "400mcg", B12: "2.4mcg" }, minerals: { calcium: "1000mg", iron: "8mg", magnesium: "420mg", potassium: "3400mg", zinc: "11mg" } },
                female: { protein: "46g", fat: "60g", water: "2700ml", vitamins: { A: "700mcg", C: "75mg", D: "15mcg", E: "15mg", K: "90mcg", B1: "1.1mg", B2: "1.1mg", B3: "14mg", B5: "5mg", B6: "1.3mg", B7: "30mcg", B9: "400mcg", B12: "2.4mcg" }, minerals: { calcium: "1000mg", iron: "18mg", magnesium: "320mg", potassium: "2600mg", zinc: "8mg" } }
            };
            
            let rda = rdaData[gender];
            let resultText = `<strong>Protein:</strong> ${rda.protein}<br>
                <strong>Fat:</strong> ${rda.fat}<br>
                <strong>Water:</strong> ${rda.water}<br>
                <strong>Vitamins:</strong><br>`;
                
            for (let vitamin in rda.vitamins) {
                resultText += `${vitamin}: ${rda.vitamins[vitamin]}<br>`;
            }
            
            resultText += `<strong>Minerals:</strong><br>`;
            for (let mineral in rda.minerals) {
                resultText += `${mineral}: ${rda.minerals[mineral]}<br>`;
            }
            
            document.getElementById("result").innerHTML = resultText;
        }
    </script>
</body>
</html>
