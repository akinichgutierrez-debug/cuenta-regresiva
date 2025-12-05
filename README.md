<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cuenta Regresiva Navideña</title>
<style>
    body {
        font-family: 'Segoe UI', sans-serif;
        background: linear-gradient(135deg, #b30000, #006400);
        color: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }
    .countdown {
        text-align: center;
        background: rgba(255, 255, 255, 0.1);
        padding: 30px;
        border-radius: 15px;
        box-shadow: 0 0 20px rgba(0,0,0,0.5);
    }
    .countdown h1 {
        font-size: 2.5rem;
        margin-bottom: 20px;
        color: #fff;
        text-shadow: 2px 2px 4px #000;
    }
    .time {
        display: flex;
        justify-content: center;
        gap: 20px;
        font-size: 2rem;
    }
    .time div {
        background: #fff;
        color: #b30000;
        padding: 20px;
        border-radius: 10px;
        min-width: 100px;
        font-weight: bold;
        box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }
    .label {
        font-size: 1rem;
        color: #006400;
        font-weight: normal;
    }
    /* Animación */
    .time div span {
        display: block;
        font-size: 2.5rem;
        animation: pulse 1s infinite alternate;
    }
    @keyframes pulse {
        from { transform: scale(1); }
        to { transform: scale(1.1); }
    }
</style>
</head>
<body>
<div class="countdown">
    <h1>🎄 ¡Cuenta regresiva para el evento! 🎅</h1>
    <div class="time">
        <div><span id="days">0</span><div class="label">Días</div></div>
        <div><span id="hours">0</span><div class="label">Horas</div></div>
        <div><span id="minutes">0</span><div class="label">Minutos</div></div>
        <div><span id="seconds">0</span><div class="label">Segundos</div></div>
    </div>
</div>

<script>
    const eventDate = new Date("Dec 6, 2025 18:00:00").getTime();

    const countdown = setInterval(() => {
        const now = new Date().getTime();
        const distance = eventDate - now;

        if (distance < 0) {
            clearInterval(countdown);
            document.querySelector(".countdown").innerHTML = "<h1>🎉 ¡El evento ha comenzado! 🎉</h1>";
            return;
        }

        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distance % (1000 * 60)) / 1000);

        document.getElementById("days").textContent = days;
        document.getElementById("hours").textContent = hours;
        document.getElementById("minutes").textContent = minutes;
        document.getElementById("seconds").textContent = seconds;
    }, 1000);
</script>
</body>
</html>
