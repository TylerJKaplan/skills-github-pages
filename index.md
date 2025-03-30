<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="theme-styles.css">
<script src="theme-switcher.js"></script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tyler Kaplan's Portfolio</title>
    <link rel="stylesheet" href="https://unpkg.com/98.css">
    <style>
        body {
            background-color: #008080; /* Classic teal Windows background */
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        
        .window {
            width: 500px;
            height: 400px;
            position: relative;
        }
        
        .window-body {
            display: flex;
            flex-direction: column;
            height: calc(100% - 58px);
        }
        
        .window-content {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow: auto;
        }
        
        .folder {
            width: 75px;
            height: 80px;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            cursor: pointer;
        }
        
        .folder-selected {
            background-color: rgba(0, 0, 128, 0.2);
        }
        
        .folder-icon {
            width: 32px;
            height: 32px;
            margin-bottom: 5px;
            background-repeat: no-repeat;
            background-position: center;
        }
        
        .folder-label {
            font-size: 11px;
            max-width: 75px;
            word-wrap: break-word;
        }
        
        .folder-opening {
            animation: folder-open 0.2s ease-in-out;
        }
        
        @keyframes folder-open {
            0% { transform: scale(1); }
            50% { transform: scale(0.9); }
            100% { transform: scale(1); }
        }
        
        .folder-icon.main-folder {
            background-image: url('https://win98icons.alexmeub.com/icons/png/directory_closed-0.png');
        }
    </style>
</head>
<body>
    <div class="window">
        <div class="title-bar">
            <div class="title-bar-text">Tyler Kaplan's Portfolio</div>
            <div class="title-bar-controls">
                <button aria-label="Minimize"></button>
                <button aria-label="Maximize"></button>
                <button aria-label="Close" onclick="window.close()"></button>
            </div>
        </div>
        <div class="window-body">
            <div class="window-content">
                <div id="main-folder" class="folder" onclick="folderClick(this, 'contents.html')">
                    <div class="folder-icon main-folder"></div>
                    <div class="folder-label">Everything</div>
                </div>
            </div>
        </div>
        <div class="status-bar">
            <p class="status-bar-field">1 item</p>
            <p class="status-bar-field"></p>
            <p class="status-bar-field">Windows 98</p>
        </div>
    </div>

    <script>
        // Folder click functionality
        let clickCount = 0;
        let clickTimer;
        
        function folderClick(element, destination) {
            clickCount++;
            
            if (clickCount === 1) {
                element.classList.add('folder-selected');
                
                clickTimer = setTimeout(function() {
                    clickCount = 0;
                    // Single click action here (select)
                }, 300);
            } else {
                clearTimeout(clickTimer);
                clickCount = 0;
                
                // Double click action - open folder
                element.classList.add('folder-opening');
                
                // Navigate after a short delay for animation
                setTimeout(function() {
                    window.location.href = destination;
                }, 200);
            }
        }
    </script>
</body>
</html>
