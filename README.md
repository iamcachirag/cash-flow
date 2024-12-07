<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Result Checking - B. L. Jain Inter College</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
        }
        h1 {
            color: #4CAF50;
            margin-top: 20px;
        }
        .container {
            margin: 20px auto;
            width: 80%;
            max-width: 500px;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #45a049;
        }
        table {
            margin: 20px auto;
            border-collapse: collapse;
            width: 100%;
            max-width: 600px;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #4CAF50;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Result Checking - B. L. Jain Inter College</h1>
    <div class="container">
        <label for="rollNumber">Enter Roll Number:</label>
        <input type="text" id="rollNumber" placeholder="Enter your Roll Number">
        <button onclick="checkResult()">Check Result</button>
    </div>
    <div id="resultTable"></div>

    <script>
        const results = {
            "101": {
                name: "Rahul Kumar",
                fathersName: "Rajesh Kumar",
                class: "12th",
                hindi: 85,
                english: 78,
                accounts: 88,
                economics: 90,
                businessStudies: 87
            },
            "102": {
                name: "Anjali Sharma",
                fathersName: "Sunil Sharma",
                class: "12th",
                hindi: 92,
                english: 89,
                accounts: 95,
                economics: 91,
                businessStudies: 93
            }
        };

        function checkResult() {
            const rollNumber = document.getElementById('rollNumber').value.trim();
            const student = results[rollNumber];
            const resultContainer = document.getElementById('resultTable');

            if (student) {
                const totalMarks = student.hindi + student.english + student.accounts + student.economics + student.businessStudies;
                const percentage = (totalMarks / 500) * 100;
                const grade = percentage >= 90 ? "A+" : percentage >= 75 ? "A" : percentage >= 50 ? "B" : "C";

                resultContainer.innerHTML = `
                    <table>
                        <tr>
                            <th>Field</th>
                            <th>Details</th>
                        </tr>
                        <tr>
                            <td>Name</td>
                            <td>${student.name}</td>
                        </tr>
                        <tr>
                            <td>Father's Name</td>
                            <td>${student.fathersName}</td>
                        </tr>
                        <tr>
                            <td>Class</td>
                            <td>${student.class}</td>
                        </tr>
                        <tr>
                            <td>Hindi</td>
                            <td>${student.hindi}</td>
                        </tr>
                        <tr>
                            <td>English</td>
                            <td>${student.english}</td>
                        </tr>
                        <tr>
                            <td>Accounts</td>
                            <td>${student.accounts}</td>
                        </tr>
                        <tr>
                            <td>Economics</td>
                            <td>${student.economics}</td>
                        </tr>
                        <tr>
                            <td>Business Studies</td>
                            <td>${student.businessStudies}</td>
                        </tr>
                        <tr>
                            <td>Total Marks</td>
                            <td>${totalMarks}/500</td>
                        </tr>
                        <tr>
                            <td>Percentage</td>
                            <td>${percentage.toFixed(2)}%</td>
                        </tr>
                        <tr>
                            <td>Grade</td>
                            <td>${grade}</td>
                        </tr>
                    </table>
                `;
            } else {
                resultContainer.innerHTML = `<p style="color: red;">No result found for Roll Number ${rollNumber}</p>`;
            }
        }
    </script>
</body>
</html>
