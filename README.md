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
    <label for="pt-time">Enter Pacific Time (PT) [HH:MM[:SS]]: </label>
    <input type="text" id="pt-time" placeholder="HH:MM[:SS]">
    <button onclick="convertPTtoPHT()">Convert PT to PHT</button>

    <h3>Converted Manila Time (PHT): </h3>
    <p><strong>12-hour format:</strong> <span id="manila-time-12"></span></p>
    <p><strong>24-hour format:</strong> <span id="manila-time-24"></span></p>

    <hr>

    <!-- Input for Manila Time to Pacific Time -->
    <label for="pht-time">Enter Manila Time (PHT) [HH:MM[:SS]]: </label>
    <input type="text" id="pht-time" placeholder="HH:MM[:SS]">
    <button onclick="convertPHTtoPT()">Convert PHT to PT</button>

    <h3>Converted Pacific Time (PT): </h3>
    <p><strong>12-hour format:</strong> <span id="pacific-time-12"></span></p>
    <p><strong>24-hour format:</strong> <span id="pacific-time-24"></span></p>

    <script>
        // Function to convert Pacific Time (PT) to Manila Time (PHT)
        function convertPTtoPHT() {
            const ptInput = document.getElementById('pt-time').value;

            // Check if the input is in the correct format (HH:MM or HH:MM:SS)
            const timePattern = /^([01]?[0-9]|2[0-3]):([0-5]?[0-9])(:([0-5]?[0-9]))?$/;
            if (!timePattern.test(ptInput)) {
                alert("Please enter a valid time in HH:MM[:SS] format.");
                return;
            }

            // Split the input into hours, minutes, and optionally seconds
            const [hours, minutes, , seconds = '00'] = ptInput.split(":").map(num => parseInt(num));

            // Create a Date object for Pacific Time (PT)
            let ptDate = new Date();
            ptDate.setHours(hours);
            ptDate.setMinutes(minutes);
            ptDate.setSeconds(seconds);
            
            // Convert PT to PHT (add 15 hours)
            ptDate.setHours(ptDate.getHours() + 15); 

            // Format the Manila time in 24-hour format
            let manilaHours24 = ptDate.getHours().toString().padStart(2, "0");
            let manilaMinutes = ptDate.getMinutes().toString().padStart(2, "0");
            let manilaSeconds = ptDate.getSeconds().toString().padStart(2, "0");

            // Convert to 12-hour format
            let manilaHours12 = ptDate.getHours();
            let ampm = manilaHours12 >= 12 ? 'PM' : 'AM';
            manilaHours12 = manilaHours12 % 12;
            manilaHours12 = manilaHours12 ? manilaHours12 : 12; // handle '12:00' case

            // Display the converted Manila time in both formats
            document.getElementById('manila-time-12').innerText = `${manilaHours12}:${manilaMinutes}:${manilaSeconds} ${ampm}`;
            document.getElementById('manila-time-24').innerText = `${manilaHours24}:${manilaMinutes}:${manilaSeconds}`;
        }

        // Function to convert Manila Time (PHT) to Pacific Time (PT)
        function convertPHTtoPT() {
            const phtInput = document.getElementById('pht-time').value;

            // Check if the input is in the correct format (HH:MM or HH:MM:SS)
            const timePattern = /^([01]?[0-9]|2[0-3]):([0-5]?[0-9])(:([0-5]?[0-9]))?$/;
            if (!timePattern.test(phtInput)) {
                alert("Please enter a valid time in HH:MM[:SS] format.");
                return;
            }

            // Split the input into hours, minutes, and optionally seconds
            const [hours, minutes, , seconds = '00'] = phtInput.split(":").map(num => parseInt(num));

            // Create a Date object for Manila Time (PHT)
            let phtDate = new Date();
            phtDate.setHours(hours);
            phtDate.setMinutes(minutes);
            phtDate.setSeconds(seconds);

            // Convert PHT to PT (subtract 15 hours)
            phtDate.setHours(phtDate.getHours() - 15);

            // Format the Pacific time in 24-hour format
            let pacificHours24 = phtDate.getHours().toString().padStart(2, "0");
            let pacificMinutes = phtDate.getMinutes().toString().padStart(2, "0");
            let pacificSeconds = phtDate.getSeconds().toString().padStart(2, "0");

            // Convert to 12-hour format
            let pacificHours12 = phtDate.getHours();
            let ampm = pacificHours12 >= 12 ? 'PM' : 'AM';
            pacificHours12 = pacificHours12 % 12;
            pacificHours12 = pacificHours12 ? pacificHours12 : 12; // handle '12:00' case

            // Display the converted Pacific time in both formats
            document.getElementById('pacific-time-12').innerText = `${pacificHours12}:${pacificMinutes}:${pacificSeconds} ${ampm}`;
            document.getElementById('pacific-time-24').innerText = `${pacificHours24}:${pacificMinutes}:${pacificSeconds}`;
        }
    </script>
</body>
</html>


```
