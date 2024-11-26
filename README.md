<!DOCTYPE html>
<html>
<head>
    <title>QR Redirect</title>
    <script>
        // Түс бойынша санақты сақтау
        const storageKeyRed = "red_count";
        const storageKeyBlue = "blue_count";

        // Санақты жүктеу немесе бастау
        let redCount = parseInt(localStorage.getItem(storageKeyRed)) || 0;
        let blueCount = parseInt(localStorage.getItem(storageKeyBlue)) || 0;

        window.onload = function() {
            // Жалпы сканерлеу санын есептеу
            const total = redCount + blueCount;

            // 50% пропорцияны сақтау үшін шарт қою
            let targetUrl = "";
            if (redCount <= blueCount) {
                redCount++;
                targetUrl = "https://example.com/red"; // Қызыл топқа сілтеме
            } else {
                blueCount++;
                targetUrl = "https://example.com/blue"; // Көк топқа сілтеме
            }

            // Жаңа мәндерді сақтау
            localStorage.setItem(storageKeyRed, redCount);
            localStorage.setItem(storageKeyBlue, blueCount);

            // Қолданушыны бағыттау
            window.location.href = targetUrl;
        };
    </script>
</head>
<body>
    <p>Redirecting... Please wait.</p>
</body>
</html>