# Open Source Doorbell System  

An open-source DIY **smart doorbell system** that combines audio, video, and networking to create a customizable home doorbell solution.  
This project is designed to give anyone the ability to build and modify their own doorbell, without being locked into proprietary ecosystems.  

---

## Features  
- Live video streaming from the camera  
- Two-way audio (microphone and speaker)  
- Loud chime with amplifier and speaker  
- HDMI display for real-time monitoring  
- Ethernet connectivity for reliable network access  
- Runs on a small single-board computer (SBC)  
- Optional integration with [Home Assistant](https://www.home-assistant.io/) for smart home automation  

---

## Components  
All parts can be purchased from common online marketplaces:  

- [Camera](https://nl.aliexpress.com/item/1005009234829192.html?gatewayAdapt=glo2nld)  
- [Sound interface](https://nl.aliexpress.com/item/1005006196572718.html?gatewayAdapt=glo2nld)  
- [Audio amplifier](https://nl.aliexpress.com/item/1005005926858790.html?gatewayAdapt=glo2nld)  
- [Loudspeaker](https://nl.aliexpress.com/item/32832795528.html?gatewayAdapt=glo2nld)  
- [Microphone](https://nl.aliexpress.com/item/1005007483195353.html?gatewayAdapt=glo2nld)  
- [HDMI display](https://nl.aliexpress.com/item/1005009442086364.html?gatewayAdapt=glo2nld)  
- [Ethernet HAT](https://nl.aliexpress.com/item/1005004437789277.html?gatewayAdapt=glo2nld)  
- [Single Board Computer](https://nl.aliexpress.com/item/32839074880.html?gatewayAdapt=glo2nld)  

---

## Getting Started  

### Hardware Setup  
1. Assemble the camera and microphone for input.  
2. Connect the amplifier and loudspeaker for output.  
3. Attach the HDMI display to the computer.  
4. Use the Ethernet HAT to connect the system to your network.  

### Software Setup  
1. Install an operating system on the SBC (e.g., Raspberry Pi OS, Armbian, or Debian).  
2. Install the required audio and video packages (`ffmpeg`, `gstreamer`, etc.).  
3. Configure the camera and microphone drivers.  
4. Run the provided software to launch the doorbell system.  

---

## Home Assistant Integration  
This project can integrate seamlessly with [Home Assistant](https://www.home-assistant.io/) to extend functionality:  

- Receive real-time notifications when the doorbell is pressed  
- View the live camera feed directly from the Home Assistant dashboard  
- Automate actions (for example, play a sound on smart speakers or turn on lights when someone rings)  
- Store snapshots or recordings locally or in cloud storage  

A detailed integration guide is available in [`docs/home-assistant.md`](./docs/home-assistant.md).  


## Project Structure  

```
/doorbell-system
│── docs/ # Documentation and diagrams
│ └── home-assistant.md # Home Assistant integration guide
│── hardware/ # Schematics and wiring
│── software/ # Source code
│── configs/ # Configuration files
│── README.md # This file
```

## Contributing  
This is an open-source project—contributions are welcome!  
- Report issues  
- Suggest improvements  
- Submit pull requests  



## License  
This project is licensed under the **MIT License**.  
