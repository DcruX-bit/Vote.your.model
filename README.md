# Vote.your.model
Help people to vote for their favorite models and brands that they love

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Model Voting</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f0f0f5;
            padding: 30px;
            text-align: center;
        }

        h1 {
            color: #333;
            margin-bottom: 5px;
        }

        p {
            color: #666;
            margin-top: 0;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            max-width: 900px;
            margin: 40px auto;
        }

        .card {
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.12);
            overflow: hidden;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
        }

        .card:hover {
            transform: scale(1.04);
            box-shadow: 0 6px 18px rgba(0,0,0,0.18);
        }

        .card img {
            width: 100%;
            height: 260px;
            object-fit: cover;
        }

        .card h3 {
            margin: 10px 0;
            color: #333;
        }

        button {
            background: #4CAF50;
            padding: 12px 20px;
            border: none;
            color: white;
            font-size: 16px;
            border-radius: 6px;
            cursor: pointer;
            margin-top: 25px;
        }

        button:hover {
            background: #45a049;
        }

        /* Results popup */
        #resultsBox {
            display: none;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.25);
            max-width: 300px;
            margin: 20px auto;
        }
    </style>
</head>

<body>

    <h1>Vote for Your Favourite Model</h1>
    <p>Choose your favourite model from below!</p>

    <div class="gallery">
        
        <label class="card">
            <img src="https://source.unsplash.com/random/300x300?model,fashion" alt="Model 1">
            <h3>Model 1</h3>
            <input type="radio" name="model" value="Model 1" style="margin-bottom: 15px;">
        </label>

        <label class="card">
            <img src="https://source.unsplash.com/random/301x300?portrait,model" alt="Model 2">
            <h3>Model 2</h3>
            <input type="radio" name="model" value="Model 2" style="margin-bottom: 15px;">
        </label>

        <label class="card">
            <img src="https://source.unsplash.com/random/302x300?fashion,woman" alt="Model 3">
            <h3>Model 3</h3>
            <input type="radio" name="model" value="Model 3" style="margin-bottom: 15px;">
        </label>

        <label class="card">
            <img src="https://source.unsplash.com/random/303x300?style,model" alt="Model 4">
            <h3>Model 4</h3>
            <input type="radio" name="model" value="Model 4" style="margin-bottom: 15px;">
        </label>

    </div>

    <button onclick="submitVote()">Submit Vote</button>

    <div id="resultsBox"></div>

    <script>
        let votes = {
            "Model 1": 0,
            "Model 2": 0,
            "Model 3": 0,
            "Model 4": 0
        };

        function submitVote() {
            let selected = document.querySelector('input[name="model"]:checked');
            
            if (!selected) {
                alert("Please choose a model before voting!");
                return;
            }

            let choice = selected.value;
            votes[choice]++;

            let resultBox = document.getElementById("resultsBox");
            resultBox.style.display = "block";
            resultBox.innerHTML = `
                <h2>Results</h2>
                <p><strong>${choice}</strong> received your vote!</p>
                <hr>
                <p>Model 1: ${votes["Model 1"]}</p>
                <p>Model 2: ${votes["Model 2"]}</p>
                <p>Model 3: ${votes["Model 3"]}</p>
                <p>Model 4: ${votes["Model 4"]}</p>
            `;
        }
    </script>

</body>
</html>
