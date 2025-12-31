<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>محاسبه‌گر انرژی eprimo</title>
    <style>
        :root {
            --primary: #2c3e50;
            --elec-color: #3498db; 
            --gas-color: #27ae60; 
            --bg: #f4f7f9;
            --card-bg: #ffffff;
            --text-muted: #64748b;
        }

        body { 
            font-family: 'Tahoma', sans-serif; 
            background-color: var(--bg); 
            display: flex; 
            justify-content: center; 
            padding: 20px 15px; 
            margin: 0; 
        }

        .app-container { width: 100%; max-width: 550px; }

        .card {
            background: var(--card-bg); 
            border-radius: 20px; 
            padding: 25px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05); 
            margin-bottom: 30px;
            border: 1px solid #e2e8f0; 
            border-top: 8px solid var(--primary);
        }

        h2 { color: var(--primary); text-align: center; margin-top: 0; }
        
        .input-group { margin-bottom: 20px; }
        
        label { display: block; margin-bottom: 8px; font-weight: bold; color: var(--primary); }
        
        input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            box-sizing: border-box;
            font-size: 16px;
            outline: none;
            transition: border-color 0.3s;
        }

        input:focus { border-color: var(--elec-color); }

        button {
            width: 100%;
            padding: 15px;
            background-color: var(--elec-color);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s;
        }

        button:active { transform: scale(0.98); }

        .result {
            margin-top: 20px;
            padding: 15px;
            background: #eef2f7;
            border-radius: 10px;
            text-align: center;
            font-weight: bold;
            display: none;
        }
    </style>
</head>
<body>

<div class="app-container">
    <div class="card">
        <h2>محاسبه‌گر eprimo</h2>
        
        <div class="input-group">
            <label>میزان مصرف (کیلووات ساعت):</label>
            <input type="number" id="usage" placeholder="مثلاً 2500">
        </div>

        <div class="input-group">
            <label>قیمت هر واحد (سنت/یورو):</label>
            <input type="number" id="price" placeholder="مثلاً 0.30">
        </div>

        <button onclick="calculate()">محاسبه هزینه</button>

        <div id="resultBox" class="result"></div>
    </div>
</div>

<script>
    function calculate() {
        const usage = document.getElementById('usage').value;
        const price = document.getElementById('price').value;
        const resultBox = document.getElementById('resultBox');

        if(usage && price) {
            const total = (usage * price).toLocaleString();
            resultBox.style.display = 'block';
            resultBox.innerHTML = `هزینه نهایی: ${total} واحد`;
            resultBox.style.color = 'var(--gas-color)';
        } else {
            alert('لطفاً تمامی مقادیر را وارد کنید');
        }
    }
</script>

</body>
</html>
