# DDOS Prevention Techniques

## Step-by-Step Guide

### STEP 1: Clone the Repository
Copy and paste the following command into your terminal (to paste, press **Ctrl+Shift+V**):
```bash
git clone https://github.com/rishiakrishnan/DDOS.git
```

### STEP 2: Locate the Folder
The cloned folder (named `DDOS`) will be located in your **Home** directory.

### STEP 3: Navigate to the DDOS Folder
Use your file explorer to open the `DDOS` folder.

### STEP 4: Open the `index.html` File
Double-click on the `index.html` file to open it in your default browser (e.g., Chrome or Firefox).

### STEP 5: Test the Login Form
1. Enter **password**: `3456`
2. Enter any **username**.
3. If both are correct, the page will redirect to `google.com`.
4. After redirection, press the **back** button in Chrome/Firefox to return to the form.

### STEP 6: Reopen the `index.html` File
Navigate back to the `DDOS` folder and double-click the `index.html` file to reopen it in your browser.

> **Note:** If using Chrome, right-click the file and select **Open With Other Application**, then choose Chrome.

### STEP 7: Open Developer Tools
1. Press **Ctrl+Shift+I** to open Developer Tools.
2. A side menu will appear.

#### Substeps:
1. Click the **"console"** option.
2. Click the **"top"** option near the eye symbol and select **"dev"**.
3. Click the **eye symbol**, and a new line will appear.
4. Paste the following code in the new line, press **Enter**, wait 2 seconds, and delete the pasted code:

```javascript
(function testAllPins() {
    const start = 0;  // Start from 0000
    const end = 9999; // End at 9999
    const correctPin = 3456; // Replace with actual checking logic
    let attempts = 0;

    console.log(`Starting test from ${start.toString().padStart(4, '0')} to ${end}`);

    for (let pin = start; pin <= end; pin++) {
        attempts++;
        let formattedPin = pin.toString().padStart(4, '0'); // Ensure 4-digit formatting
        
        if (pin === correctPin) {
            console.log(`Correct PIN found: ${formattedPin} after ${attempts} attempts`);
            return; // Stop execution when correct PIN is found
        }
    }

    console.log("Test completed. Correct PIN not found in the range.");
})();
```

### STEP 8: Observe the Attack Simulation
Scroll through the console output to see the brute force attempts. This demonstrates a model of a DDOS attack using brute force PIN testing.

---

## Prevention Techniques

### A) **Rate Limiting**
Rate limiting restricts the number of login attempts within a given period. For example:
- The user is allowed a maximum of 5 login attempts.
- After exceeding the limit, the user is temporarily blocked (e.g., for 5 minutes).
- Refreshing the page resets the limit.

**Implementation:(open b.html)**
We created a JavaScript script to block the user after 5 failed attempts.

### B) **CAPTCHA Verification**
CAPTCHA adds an additional layer of security by requiring users to input a code from an image. The goal is to prevent automated scripts (bots) from successfully completing the form.

**Implementation:(OPEN c.html)**
1. A folder named `./captcha` contains images with filenames such as `1234.png`.
2. The script randomly selects an image from the folder and displays it to the user.
3. The user enters the code displayed in the image.
4. The script checks if the filename (without the `.png` extension) matches the user-entered CAPTCHA.

**Example:**
- The script selects `1234.png`.
- The image displays the number `1234`.
- The user enters `1234`.
- The script verifies the input and allows access if it matches the filename.

---

These techniques demonstrate how to mitigate the risks of brute force and DDOS attacks through rate limiting and CAPTCHA verification.

