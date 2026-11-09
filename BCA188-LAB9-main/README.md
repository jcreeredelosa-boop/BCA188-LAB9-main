
# BCA188 — Laboratory Activity 9
## ESP32 Wi-Fi Manager

| | |
|---|---|
| **Name** | JC Ree F. Redelosa |
| **Student No.** | 2024-1587 |

---

## Practice Tasks

| # | Test | Observation |
|---|------|-------------|
| 1 | Testing an incorrect password | When an invalid Wi-Fi password is entered, the ESP32 cannot establish a connection. The configuration portal remains active for three minutes before the device automatically restarts. |
| 2 | Clearing stored Wi-Fi credentials | Pressing and holding the BOOT button for approximately 3–5 seconds removes the previously saved network information from NVS. Afterward, the `ESP32-Setup` access point becomes visible again on the phone. |
| 3 | Modifying the captive portal name | Changing the access point name in the `WiFiManager` configuration and uploading the updated program allows the ESP32 to broadcast the newly assigned SSID. |
| 4 | Connecting to another Wi-Fi network | Once the stored credentials are cleared, the ESP32 can be configured to join **TP-LINK_DA20** using the correct password. After connecting successfully, the device receives the IP address `192.168.0.100`. |

---

## Explanation

The ESP32 was able to switch to another Wi-Fi network without modifying or uploading a new program because the WiFiManager library uses **Non-Volatile Storage (NVS)** to retain network credentials.

Whenever the ESP32 starts, it checks for previously stored Wi-Fi information and attempts to connect using those credentials. If the saved details are valid and the network is available, the device connects automatically without displaying the configuration portal.

However, when the stored credentials are erased through a reset or by holding the BOOT button, the ESP32 returns to setup mode. It then creates a Wi-Fi access point that allows the user to enter new network information through the captive portal.

This feature makes the ESP32 more convenient to configure because users can change Wi-Fi networks without repeatedly editing the source code or uploading a new sketch.


