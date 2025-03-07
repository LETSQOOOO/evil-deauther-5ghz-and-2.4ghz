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
10. [Credits](#credits)

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

## Credits

- Developed by **[letsqooo](https://github.com/letsqooo)**.
- Inspired by [ESP8266 Deauther](https://github.com/SpacehuhnTech/esp8266_deauther).
