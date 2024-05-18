<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BlackHat's Mod Menu</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        h1 {
            margin-bottom: 20px;
        }
        .button-container {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #6200ea;
            color: white;
            transition: background-color 0.3s ease;
        }
        button:hover {
            background-color: #3700b3;
        }
    </style>
</head>
<body>

    <h1>BlackHat's Mod Menu</h1>
    <div class="button-container" id="button-container"></div>

    <script>
        class ButtonInfo {
            constructor({
                buttonText = "-",
                method = null,
                toolTip = "Mod Does Not Have A Tooltip.",
                isTogglable = true,
                enableMethod = null,
                disableMethod = null
            } = {}) {
                this.buttonText = buttonText;
                this.method = method;
                this.enabled = false;
                this.isTogglable = isTogglable;
                this.toolTip = toolTip;
                this.enableMethod = enableMethod;
                this.disableMethod = disableMethod;
                this.button = null;
                this.createButton();
            }

            createButton() {
                this.button = document.createElement('button');
                this.button.textContent = this.buttonText;
                this.button.title = this.toolTip;
                this.button.style.backgroundColor = this.enabled ? 'black' : 'darkred';
                
                this.button.onclick = () => {
                    if (this.isTogglable) {
                        this.enabled = !this.enabled;
                        this.button.style.backgroundColor = this.enabled ? 'darkred' : 'black';
                        if (this.enabled && this.enableMethod) {
                            this.enableMethod();
                        } else if (!this.enabled && this.disableMethod) {
                            this.disableMethod();
                        }
                    }
                    if (this.method) {
                        this.method();
                    }
                };

                document.getElementById('button-container').appendChild(this.button);
            }

            setTogglable(isTogglable) {
                this.isTogglable = isTogglable;
                if (!isTogglable) {
                    this.button.style.backgroundColor = 'black';
                    this.enabled = false;
                }
            }
        }
	//put ur mods here :D
	
	
	function changeBackgroundColor() {
            document.body.style.backgroundColor = 
                document.body.style.backgroundColor === 'darkgrey' ? '#f0f0f0' : 'darkgrey';
        }
	//BUTTONSS!!!!!!!!!!!
	
	new ButtonInfo({
            buttonText: 'Change Menu Color',
            method: changeBackgroundColor,
            isTogglable: false,
        });

	</script>
</body>
</html>
