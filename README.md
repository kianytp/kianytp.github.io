<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Timetable</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        h1 {
            margin-top: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Today's Timetable</h1>
        <p id="timetable"></p>
    </div>

    <script>
        const weekATimetable = {
            "Monday": "For Period 2, you have English. For Period 3, you have Graphics. Then you have breaktime. Then, you have Computer Science at Period 4. After, during Period 5, you have Maths. Then, you have Lunch Time. After Lunch, you have Physics, and then French. Have a great day!",
            "Tuesday": "For Period 2, you have Graphic Communication. For Period 3, you have Computer Science. Then you have breaktime. Then, you have French at Period 4. After, during Period 5, you have Study. Then, you have Lunch Time. After Lunch, you have Mathematics, and then Chemistry. Have a great day!",
            "Wednesday": "For Period 2, you have Study. For Period 3, you have Religious Studies. Then you have breaktime. Then, you have Mathematics at Period 4. After, during Period 5, you have Physical Education. Then, you have Lunch Time. After Lunch, you have Biology, and then English. Have a great day!",
            "Thursday": "For Period 2, you have Biology. For Period 3, you have Graphic Communication. Then you have breaktime. Then, you have Religious Studies at Period 4. After, during Period 5, you have Physical Education. Then, you have Lunch Time. After Lunch, you have Games, and then Games. Have a great day!",
            "Friday": "For Period 2, you have Chemistry. For Period 3, you have Religious Studies. Then you have breaktime. Then, you have Computer Science at Period 4. After, during Period 5, you have Physics. Then, you have Lunch Time. After Lunch, you have French, and then Mathematics. Have a great day!"
        };

        const weekBTimetable = {
            "Monday": "For Period 2, you have Biology. For Period 3, you have French. Then you have breaktime. Then, you have Graphic Communication at Period 4. After, during Period 5, you have Chemistry. Then, you have Lunch Time. After Lunch, you have Computer Science, and then Mathematics. Have a great day!",
            "Tuesday": "For Period 2, you have French. For Period 3, you have Graphic Communication. Then you have breaktime. Then, you have English at Period 4. After, during Period 5, you have Religious Studies. Then, you have Lunch Time. After Lunch, you have Study, and then Computer Science. Have a great day!",
            "Wednesday": "For Period 2, you have Religious Studies. For Period 3, you have English. Then you have breaktime. Then, you have Biology at Period 4. After, during Period 5, you have Physical Education. Then, you have Lunch Time. After Lunch, you have Mathematics, and then Physics. Have a great day!",
            "Thursday": "For Period 2, you have PSHE. For Period 3, you have Graphic Communication. Then you have breaktime. Then, you have French at Period 4. After, during Period 5, you have Physical Education. Then, you have Lunch Time. After Lunch, you have Games, and then Games. Have a great day!",
            "Friday": "For Period 2, you have Chemistry. For Period 3, you have Mathematics. Then you have breaktime. Then, you have Physics at Period 4. After, during Period 5, you have English. Then, you have Lunch Time. After Lunch, you have English again, and then Religious Studies. Have a great day!"
        };

        const startDate = new Date("2024-06-10");

        function getWeekType() {
            const today = new Date();
            const timeDifference = today.getTime() - startDate.getTime();
            const daysDifference = Math.floor(timeDifference / (1000 * 3600 * 24));
            const weeksDifference = Math.floor(daysDifference / 7);
            return weeksDifference % 2 === 0 ? "A" : "B";
        }

        function getTodayDayName() {
            const today = new Date();
            return today.toLocaleDateString('en-GB', { weekday: 'long' });
        }

        function getTimetable() {
            const weekType = getWeekType();
            const dayName = getTodayDayName();

            if (weekType === "A") {
                return weekATimetable[dayName] || "No lessons today!";
            } else {
                return weekBTimetable[dayName] || "No lessons today!";
            }
        }

        document.getElementById("timetable").textContent = getTimetable();
    </script>
</body>
</html>
