# html-ip-webcam
Streaming the IP Webcamera to HTML page.

<br>

Click [here](https://play.google.com/store/apps/details?id=com.pas.webcam) for installation the `IP Webcam` android app from Play Store

## Code Implementation
```html
<!DOCTYPE html>
<html>
<head>
    <title>IP Webcam</title>
</head>
<body>
    <h1>IP Webcam</h1>
    <img id="webCam" src="http://<REPLACE-YOUR-WEBCAM-IP>/video" alt="IP Webcam Loading..." height="600">
    
    <button id="capturePhoto">SNAP</button>
    
    <script>
        const cameraFeed = document.getElementById("webCam");
        const capturePhotoButton = document.getElementById("capturePhoto");
        
        capturePhotoButton.addEventListener("click", () => {
            fetch("http://<REPLACE-YOUR-WEBCAM-IP>/photo.jpg", { method: "GET" })
                .then(response => {
                    if (response.ok) {
                        return response.blob();
                    } else {
                        console.error("Failed to capture photo.");
                    }
                })
                .then(blob => {
                    const url = URL.createObjectURL(blob);
                    const a = document.createElement("a");
                    a.href = url;
                    a.download = "webCam.jpg";
                    a.click();
                    URL.revokeObjectURL(url);
                });
        });
    </script>
</body>
</html>
```
<br>

**Note:** `REPLACE-YOUR-WEBCAM-IP` portion with your actual IP.

<br>
<br>

### _Author: [Mahfuz Hasan Reza](https://github.com/mahfuzhasanreza/)_
 - _Connect with me on [LinkedIn](https://www.linkedin.com/in/mahfuzhasanreza/)_
 - _Follow me on [Instagram](https://www.instagram.com/mahfuzhasanreza/)_
 - _Connect with me on [Facebook](https://www.facebook.com/mahfuzhasanreza/)_
