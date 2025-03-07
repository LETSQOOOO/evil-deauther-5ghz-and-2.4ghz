# Evil-Deauther: 5GHz + 2.4GHz Wi-Fi Deauther and Evil Portal

![Platform](https://img.shields.io/badge/Platform-BW16-blue)
![License](https://img.shields.io/badge/License-MIT-green)

A powerful Wi-Fi deauthentication and evil portal tool for the **BW16 (RTL8720DN)** module. This project combines **deauthentication attacks**, **evil portal creation**, and **credential capture** into a single, easy-to-use device. It supports both **2.4GHz and 5GHz Wi-Fi networks**.

---

## Table of Contents

1. [Features](#features)
2. [Hardware Requirements](#hardware-requirements)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Code Structure](#code-structure)
6. [Troubleshooting](#troubleshooting)
7. [License](#license)
8. [Contributing](#contributing)
9. [Disclaimer](#disclaimer)
10. [example](#Example)
11. [Credits](#credits)

---

## Features

- **Dual-Band Deauthentication**:
  - Deauthenticate devices on both **2.4GHz and 5GHz** Wi-Fi networks.
  - Supports multiple target networks simultaneously.

- **Evil Portal**:
  - Create a fake Wi-Fi network with the same SSID as the target.
  - Redirect users to a login page to capture **Wi-Fi passwords**.

- **Google Login Portal**:
  - Mimic a Google login page to capture **email and password credentials**.
  - Logs client **IP and MAC addresses**.

- **Web Interface**:
  - Modern, responsive web interface for controlling the device.
  - Tabs for **Deauth**, **Deauth+Clone**, **Evil Portal**, and **Settings**.

- **Password-Protected Settings**:
  - Secure configuration page to change AP credentials.

---

## Hardware Requirements

- **BW16 (RTL8720DN) Module**:
  - Dual-band Wi-Fi support (2.4GHz + 5GHz).
  - Ameba SDK compatible.

- **USB-to-Serial Adapter** (for programming).
- **Power Supply** (5V/1A recommended).

---

## Installation

### 1. Install Arduino IDE
Download and install the [Arduino IDE](https://www.arduino.cc/en/software).

### 2. Add BW16 Board Support
1. Open Arduino IDE.
2. Go to **File > Preferences**.
3. Add the following URL to **Additional Boards Manager URLs**: https://raw.githubusercontent.com/ambiot/ambd_arduino/master/Arduino_package/package_realtek.com_amebad_index.json
4. 4. Go to **Tools > Board > Boards Manager**.
5. Search for `Ameba` and install the latest version.

### 3. Install Required Libraries
1. Go to **Tools > Manage Libraries**.
2. Install the following libraries:
- `ESPAsyncWebServer`
- `AsyncTCP`

### 4. Upload the Code
1. Clone this repository or download the `.ino` file.
2. Open the `.ino` file in Arduino IDE.
3. Select the board: **Tools > Board > BW16 (RTL8720DN)**.
4. Select the correct port: **Tools > Port**.
5. Click **Upload**.

---

## Usage

### 1. Connect to the Device
1. Power on the BW16 module.
2. Connect to the Wi-Fi network: `BW16-Deauther` (password: `12345678`).
3. Open a browser and go to `http://192.168.4.1`.

### 2. Web Interface
- **Deauth**:
- Select target networks and start deauthentication.

- **Deauth+Clone**:
- Deauthenticate the target network and create a clone AP with the same SSID.
- Users connecting to the clone AP will be prompted to enter their Wi-Fi password.

- **Evil Portal**:
- Activate a Google login portal to capture email and password credentials.

- **Settings**:
- Change the device's AP credentials (password required).

### 3. Monitor Captured Data
- Open the **Serial Monitor** in Arduino IDE (115200 baud) to view captured credentials and logs.

---

## Code Structure

- **`setup()`**:
- Initializes Wi-Fi, starts the web server, and begins network scanning.

- **`loop()`**:
- Handles periodic network scanning and deauthentication.

- **Web Server**:
- Serves the web interface and handles form submissions.

- **Deauthentication**:
- Uses `wifi_send_pkt_freedom()` to send deauthentication frames.

- **Evil Portal**:
- Creates a fake AP and serves login pages.

---

## Troubleshooting

### 1. Deauth Not Working
- Ensure the target network is within range.
- Check if the target network is 5GHz (requires line-of-sight).

### 2. Web Interface Not Loading
- Verify the BW16 is powered and broadcasting the AP.
- Check if the correct IP address is used (`http://192.168.4.1`).

### 3. Memory Issues
- Reduce the number of networks scanned by modifying `SCAN_INTERVAL`.

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

---

## Disclaimer

This project is for **educational purposes only**. Unauthorized use of deauthentication or credential capture is illegal and unethical. Always ensure you have explicit permission before using this tool.

---

## Example

here is an html paste this in to any AI or html player i recommend 
https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_video_all


        <!DOCTYPE html> <html> <head> <title>BW16 Deauther</title> <meta name="viewport" content="width=device-width, initial-scale=1">  <style>
    :root { 
      --primary: #dc3545; 
      --bg: #1a1a1a; 
      --card: #262626; 
    }
   
    body { 
      font-family: Arial, sans-serif; 
      background: var(--bg); 
      color: white; 
      margin: 0; 
    }
    
    .container { 
      max-width: 800px; 
      margin: 0 auto; 
      padding: 20px; 
    }
    
    .nav { 
      display: flex; 
      gap: 10px; 
      margin-bottom: 30px; 
    }
    
    .nav-btn { 
      flex: 1; 
      padding: 15px; 
      text-align: center; 
      background: var(--card); 
      color: white; 
      border: none; 
      border-radius: 8px; 
      cursor: pointer; 
      transition: background 0.3s;
    }
    
    .nav-btn.active, 
    .nav-btn:hover { 
      background: var(--primary); 
    }
    
    .card { 
      background: var(--card); 
      border-radius: 10px; 
      padding: 20px; 
      margin-bottom: 20px; 
    }
    
    table { 
      width: 100%; 
      border-collapse: collapse; 
      margin: 20px 0;
    }
    
    th, td { 
      padding: 12px; 
      text-align: left; 
      border-bottom: 1px solid #333; 
    }
    
    input[type="text"], 
    input[type="password"] { 
      width: 100%; 
      padding: 10px; 
      margin: 8px 0; 
      background: #333; 
      border: none; 
      color: white; 
      border-radius: 5px; 
    }
    
    button { 
      background: var(--primary); 
      color: white; 
      padding: 12px 20px; 
      border: none; 
      border-radius: 5px; 
      cursor: pointer; 
      width: 100%; 
      transition: opacity 0.3s;
    }
    
    button:hover {
      opacity: 0.9;
    }
    
    .log-info {
      color: #888;
      font-size: 0.9em;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>BW16 Deauther</h1>
    
    <div class="nav">
      <button class="nav-btn active" onclick="showTab('deauth')">Deauth</button>
      <button class="nav-btn" onclick="showTab('deauth-clone')">Deauth+Clone</button>
      <button class="nav-btn" onclick="showTab('evil')">Evil Portal</button>
      <button class="nav-btn" onclick="showTab('settings')">Settings</button>
    </div>

    <!-- Deauth Tab -->
    <div id="deauth" class="tab-content card">
      <h2>Deauth Networks</h2>
      <form action="/deauth" method="POST">
        <table>
          <tr><th></th><th>SSID</th><th>Channel</th><th>Band</th><th>Signal</th></tr>
          <tr>
            <td><input type="checkbox" name="target" value="HomeWiFi"></td>
            <td>HomeWiFi</td>
            <td>6</td>
            <td>2.4GHz</td>
            <td>-65 dBm</td>
          </tr>
          <tr>
            <td><input type="checkbox" name="target" value="OfficeNet"></td>
            <td>OfficeNet</td>
            <td>36</td>
            <td>5GHz</td>
            <td>-72 dBm</td>
          </tr>
        </table>
        <button type="submit">Start Deauth</button>
      </form>
    </div>

    <!-- Deauth+Clone Tab -->
    <div id="deauth-clone" class="tab-content card" style="display:none">
      <h2>Deauth + Clone</h2>
      <form action="/deauth-clone" method="POST">
        <table>
          <tr><th></th><th>SSID</th><th>Channel</th><th>Band</th><th>Signal</th></tr>
          <tr>
            <td><input type="checkbox" name="target" value="HomeWiFi"></td>
            <td>HomeWiFi</td>
            <td>6</td>
            <td>2.4GHz</td>
            <td>-65 dBm</td>
          </tr>
        </table>
        <button type="submit">Start Deauth+Clone</button>
      </form>
    </div>

    <!-- Evil Portal Tab -->
    <div id="evil" class="tab-content card" style="display:none">
      <h2>Evil Portal</h2>
      <form action="/evilportal" method="POST">
        <input type="text" name="ssid" placeholder="Portal SSID" required>
        <button type="submit">Activate</button>
      </form>
    </div>

    <!-- Settings Tab -->
    <div id="settings" class="tab-content card" style="display:none">
      <h2>Settings</h2>
      <form action="/settings" method="POST">
        <input type="password" name="password" placeholder="Admin Password" required>
        <input type="text" name="apssid" value="BW16-Deauther" placeholder="AP SSID" required>
        <input type="password" name="appass" value="12345678" placeholder="AP Password" required>
        <button type="submit">Save Settings</button>
      </form>
      
      <div class="log-info">
        <h3>Log Management</h3>
        <form action="/download-logs">
          <button type="submit">Download Log File</button>
        </form>
        <p>Log file contains captured credentials and client information</p>
      </div>
    </div>
  </div>

  <script>
    function showTab(tabName) {
      // Hide all tabs
      document.querySelectorAll('.tab-content').forEach(tab => {
        tab.style.display = 'none';
      });
      
      // Show selected tab
      document.getElementById(tabName).style.display = 'block';
      
      // Update button states
      document.querySelectorAll('.nav-btn').forEach(btn => {
        btn.classList.remove('active');
      });
      event.target.classList.add('active');
    }
  </script>
</body>
</html>

---

## Credits

- Developed by **[letsqooo](https://github.com/LETSQOOOO)**.
- Inspired by [ESP8266 Deauther](https://github.com/SpacehuhnTech/esp8266_deauther).
