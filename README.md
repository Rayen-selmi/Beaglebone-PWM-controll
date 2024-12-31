# PWM Control on BeagleBone Black via Web Interface

## Description

This project enables real-time control of a DC motor via Pulse Width Modulation (PWM) on a **BeagleBone Black** board, managed through a simple and intuitive web interface. The web server allows users to adjust the **duty cycle** to control the motor's speed and performance.

The interface communicates with the BeagleBone Black through **WebSockets**, sending PWM values that are used to adjust the motor's speed in real time.

## Features

- **Web interface** to input PWM values (0-100%) and control the DC motor speed.
- Real-time communication with BeagleBone Black using **Socket.IO**.
- Input validation ensures that PWM values are between 0 and 100.
- Feedback to the user on the success or failure of the PWM update.

## Prerequisites


- **Node.js** and **npm** to run the web server.
- **Socket.IO** for real-time communication between the client and the server.
- **Bash** and the appropriate permissions to interact with the PWM device on BeagleBone Black.
- **Real-Time Kernel** for enhanced performance and more precise PWM control.

### Installing the Real-Time Kernel

In order to achieve precise control over PWM and ensure your system runs with real-time capabilities, you need to install the real-time kernel on your BeagleBone Black.

Follow the instructions provided in the official BeagleBone Cookbook to install the real-time kernel:

- Go to the [BeagleBone Cookbook Kernel Installation Guide](https://docs.beagleboard.org/books/beaglebone-cookbook/07kernel/kernel.html)
- Follow the steps to install the **Real-Time Kernel** on your BeagleBone Black.

Once the real-time kernel is installed, reboot the BeagleBone Black for the changes to take effect.

## Components

- **change_pwm.sh**: This shell script directly modifies the duty cycle by interacting with the system's PWM paths.
- **server.js**: This is the Node.js server that hosts the web interface and handles WebSocket communication.
- **index.html**: The user interface, which provides a slider to adjust the PWM duty cycle.

## Utilisation

1. **Connect to BeagleBone Black**: SSH into the BeagleBone Black to access it remotely and run commands.
   - Open a terminal on your local machine and run:
     ```bash
     ssh debian@192.168.6.2
     ```
     Replace `<192.168.6.2>` with the actual IP address of your BeagleBone Black.

2. **Install the Real-Time Kernel**: Install the real-time kernel to enable precise PWM control, as per the guide provided.

3. **Clone the Repository**: Clone the project repository to your BeagleBone Black to get the necessary project files.
   - In the terminal, navigate to the desired directory and run the following command:
     ```bash
     git clone https://github.com/Rayen-selmi/Beaglebone-PWM-controll.git
     cd Beaglebone-PWM-controll
     ```
   - This will download the project files into a folder named `pwm-control-beaglebone`.

4. **Install Node.js**: Install Node.js to run the server that powers the web interface.
   - Run the following commands to install Node.js and npm:
     ```bash
     sudo apt update
     sudo apt install nodejs
     sudo apt install npm
     ```
   - Verify the installation by checking the version of Node.js:
     ```bash
     node -v
     ```
     This should return the installed Node.js version.

5. **Run the Server**: Start the server with `node server.js` to begin controlling the PWM via a web interface.
   - In the project directory, run the following command:
     ```bash
     node server.js
     ```
   - This will start the Node.js server, and you should see a message indicating that the server is running.

6. **Access the Web Interface**: Open a browser and navigate to the provided URL to interact with the PWM control system.
   - In your browser, go to:
     ```
     http://168.6.2:3000
     ```
   - You will see the web interface where you can adjust the PWM duty cycle to control the DC motor speed.
