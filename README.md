# TimeConverter
PT TO PH AND PH TO PT

```HTML


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Time Conversion: Manila <-> Pacific Time</title>
</head>
<body>
    <h1>Convert Time Between Pacific Time (PT) and Manila Time (PHT)</h1>

    <!-- Input for Pacific Time to Manila Time -->
    <label for="pt-time">Enter Pacific Time (PT) [HH:MM:SS]: </label>
    <input type="text" id="pt-time" placeholder="HH:MM:SS">
    <button onclick="convertPTtoPHT()">Convert PT to PHT</button>

    <h3>Converted Manila Time (PHT): <span id="manila-time"></span></h3>

    <hr>

    <!-- Input for Manila Time to Pacific Time -->
    <label for="pht-time">Enter Manila Time (PHT) [HH:MM:SS]: </label>
    <input type="text" id="pht-time" placeholder="HH:MM:SS">
    <button onclick="convertPHTtoPT()">Convert PHT to PT</button>

    <h3>Converted Pacific Time (PT): <span id="pacific-time"></span></h3>

    <script>
        // Convert Pacific Time (PT) to Manila Time (PHT)
        function convertPTtoPHT() {
            const ptInput = document.getElementById('pt-time').value;
            
            // Check if the input is in the correct format (HH:MM:SS)
            const timePattern = /^([01]?[0-9]|2[0-3]):([0-5]?[0-9]):([0-5]?[0-9])$/;
            if (!timePattern.test(ptInput)) {
                alert("Please enter a valid time in HH:MM:SS format.");
                return;
            }

            // Split the input into hours, minutes, and seconds
            const [hours, minutes, seconds] = ptInput.split(":").map(num => parseInt(num));

            // Create a Date object for Pacific Time (PT)
            let ptDate = new Date();
            ptDate.setHours(hours);
            ptDate.setMinutes(minutes);
            ptDate.setSeconds(seconds);
            
            // Convert PT to PHT (add 15 hours)
            ptDate.setHours(ptDate.getHours() + 15); 

            // Format the Manila time in HH:MM:SS
            let manilaHours = ptDate.getHours().toString().padStart(2, "0");
            let manilaMinutes = ptDate.getMinutes().toString().padStart(2, "0");
            let manilaSeconds = ptDate.getSeconds().toString().padStart(2, "0");

            // Display the converted Manila time
            document.getElementById('manila-time').innerText = `${manilaHours}:${manilaMinutes}:${manilaSeconds}`;
        }

        // Convert Manila Time (PHT) to Pacific Time (PT)
        function convertPHTtoPT() {
            const phtInput = document.getElementById('pht-time').value;

            // Check if the input is in the correct format (HH:MM:SS)
            const timePattern = /^([01]?[0-9]|2[0-3]):([0-5]?[0-9]):([0-5]?[0-9])$/;
            if (!timePattern.test(phtInput)) {
                alert("Please enter a valid time in HH:MM:SS format.");
                return;
            }

            // Split the input into hours, minutes, and seconds
            const [hours, minutes, seconds] = phtInput.split(":").map(num => parseInt(num));

            // Create a Date object for Manila Time (PHT)
            let phtDate = new Date();
            phtDate.setHours(hours);
            phtDate.setMinutes(minutes);
            phtDate.setSeconds(seconds);

            // Convert PHT to PT (subtract 15 hours)
            phtDate.setHours(phtDate.getHours() - 15);

            // Format the Pacific time in HH:MM:SS
            let pacificHours = phtDate.getHours().toString().padStart(2, "0");
            let pacificMinutes = phtDate.getMinutes().toString().padStart(2, "0");
            let pacificSeconds = phtDate.getSeconds().toString().padStart(2, "0");

            // Display the converted Pacific time
            document.getElementById('pacific-time').innerText = `${pacificHours}:${pacificMinutes}:${pacificSeconds}`;
        }
    </script>
</body>
</html>


```
