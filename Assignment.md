# Description
- In this assignment, you will need to develop a Python-based IoT simulator for a smart home automation system.
- The simulator should emulate the behaviour of various IoT devices commonly found in a smart home, such as smart lights, thermostats, and security cameras.
- You will also create a central automation system that manages these devices and build a monitoring dashboard to visualize and control the smart home.
- This assignment will help you apply your Python programming skills, including OOP, data handling, real-time data monitoring, and graphical user interfaces (GUIs)

# Objective
- Develop a Python-based IoT device simulator.
- Implement basic data analytics and processing.
- Create an eye-catching monitoring dashboard to display sensor data and analytics results.
- Use Python data structures, classes, OOP objects, instance and class variables, OOP methods, pip, static.
- methods, files & standard library, exception handling, modules, and packages.

# Requirements & Grading

## Part1: IoT Device Emulation (25 %)
### Device Classes
- **Device Classes**: Create Python classes for each type of IoT device you want to simulate, such as SmartLight, Thermostat, and SecurityCamera.
- Each class should have attributes like device ID, status (on/off), and relevant properties (e.g., temperature for thermostats, brightness for lights, and security status for cameras).
#### Device Behaviours
-  **Device Behavior**: Implement methods for each device class that allow for turning devices on/off and changing their properties.
- Simulate realistic behavior, such as gradual dimming for lights or setting temperature ranges for thermostats.
-  Randomization: Include a randomization mechanism to simulate changing device states and properties over time.

## Part 2: Central Automation System (25 %)
### Automation System and Automation Rule
- Automation System Class: Create a central automation system class, e.g., AutomationSystem, responsible for managing and controlling all devices.
- It should provide methods for discovering devices, adding them to the system, and executing automation tasks.
-  Simulation Loop: Implement a simulation loop that runs periodically (e.g., every few seconds) to trigger automation rules, update device states, and simulate device behaviors.
## Part 3: Documentation (30%)
- Documentation: Provide clear documentation for your code, including class descriptions, method explanations, and instructions on how to run the simulation and use the dashboard.
- Develop test cases to ensure that the simulator and automation system behave as expected.
- Test various scenarios, such as different automation rules and user interactions.
## Part 4: Monitoring Dashboard (20%)

### Tkinter
- Graphical User Interface (GUI): Create a GUI for monitoring and controlling the smart home system.
- You can use Python GUI libraries like Tkinter.
- The GUI should display the status and properties of each device, provide controls to interact with them, and visualize data.
-  Real-time Data Monitoring: Display real-time data from the simulated devices on the dashboard.
- This includes temperature graphs for thermostats, motion detection status for cameras, and brightness levels for lights.
-  User Interaction: Allow users to interact with devices through the GUI, such as toggling lights on/off, adjusting thermostat settings, and arming/disarming security cameras.

## Hints (See Tutorials Below for More Info):
-  While implementing the code, make sure you're writing docstrings for methods and classes. This way you can generate the documentation easily. 
-  Use Python's random library for generating sensor data.
-  Use a simulation loop for rule execution.
-  Design a GUI (try to be creative) using Tkinter.
-  Feel free to use ChatGPT, but make sure to be able understand and explain your solution!
-  Do not hesitate to ask your instructor for help and asking for the template for the GUI!

## Tutorials 

### Threading
[(32) Python Threading Tutorial: Run Code Concurrently Using the Threading Module - YouTube](https://www.youtube.com/watch?v=IEEhzQoKtQU)

### Tkinter
[(32) Tkinter Beginner Course - Python GUI Development - YouTube](https://www.youtube.com/watch?v=ibf5cx221hk)

### Unit Testing
[(32) Python Tutorial: Unit Testing Your Code with the unittest Module - YouTube](https://www.youtube.com/watch?v=6tNS--WetLI)
### Generating Documentation from DocString

[Python Docstrings (With Examples) (programiz.com)](https://www.programiz.com/python-programming/docstrings)
[Easy Documentation Generation in Python using PDoc. | by Daniel Ellis Research | CEMAC | Medium](https://medium.com/cemac/simple-documentation-generation-in-python-using-pdoc-16fb86eb5cd5)

### How to use packages and modules? & How to organize your code? 
[(32) 5 Tips To Organize Python Code - YouTube](https://www.youtube.com/watch?v=e9yMYdnSlUA)
### Sample GUI
![[Lab7_assignment-1.png]]

## Sample Documentation
[src API documentation (ahmedelagami.github.io)](https://ahmedelagami.github.io/Smart_Home_Simulator_Documentation/)





















# Entities

## Devices
#### SmartDevice (SuperClass)
##### Fields
- device_id
- status
##### Functions
- toggle_status 
	Switches the device status (on/off)

#### SmartLight (SmartDevice)
##### Fields
- brightness
##### Functions
- set_brightness
	Sets the brightness level of the light.
#### Thermostat (SmartDevice)
##### Fields
- temperature
##### Functions
- set_temperature
	Sets the temperature of the thermostat.
#### SecurityCamera (SmartDevice)
##### Fields
- motion_detected
##### Functions
- detect_motion
	Sets the motion detection status randomly.

## Automation
#### AutomationSystem
##### Fields
- devices
- rules
##### Functions
- add_device: 
	Adds a device to the system
- add_rule
	Adds a rule to the system
- execute_rule
	Executes all the added rules
#### AutomationRule
##### Fields
- condition
- action
##### Functions
- apply
	checks the condition and if true, applied the associated action to the devices
## GUI
#### Dashboard
##### Fields
- root
- system
- root.title
- labels
- automation_on
- automation_text
- device_listbox
- update_thread
- update_thread.daemon
##### Functions
- toggle_random
- create_device_controls
- toggle_helper
- update_values

- create_light_controls
- create_thermostat_controls
- create_camera_controls
- create_rule_controls
=> add controls to the GUI for the particular devices

- update_device_list
- simulation_loop
	A loop that updates the device states and UI periodically.
 
- set_brightness
- set_temperature
- detect_motion 
- create_automation_rule 
	Creates a rule to turn on lights when motion is detected.
 
- randomize_device_states
	Randomizes the state of active devices:
	- SmartLight's brightness is randomized.
	- Thermostat's temperature is randomized.
	- SecurityCamera's motion detection is randomiz

## Packages Used 
- **random**: For generating random numbers and choices.
- **time**: For introducing delays.
- **tkinter**: For creating the graphical user interface.
- **threading**: For creating threads that can run parallel tasks

# Problems 
To improve modularity, error handling, and rule implementation, here are some suggestions:

### **1. Modularity**:

**Separate Device Classes into Their Own Files**:
To maintain cleaner code, each device type (`SmartLight`, `Thermostat`, `SecurityCamera`) can be moved into its own file.

For instance:
- `smart_light.py` for the `SmartLight` class.
- `thermostat.py` for the `Thermostat` class.
- `security_camera.py` for the `SecurityCamera` class.

**Separate GUI Logic**:
GUI logic for each device can also be modularized into separate components or files. 

- Create a folder named `gui_components` or similar.
- Within this, have individual files like `light_gui.py`, `thermostat_gui.py`, etc., each containing GUI components and logic for its respective device.

### **2. Error Handling**:

**Input Validation**:
For the GUI components that receive user input, such as sliders for brightness and temperature, ensure there's validation. This will prevent out-of-range values or incorrect inputs.

```python
def set_brightness(self, light, brightness):
    try:
        brightness_val = int(brightness)
        if 0 <= brightness_val <= 100:
            light.set_brightness(brightness_val)
        else:
            raise ValueError("Invalid brightness value")
    except ValueError as e:
        # Handle or display the error appropriately
        print(e)
```

**Exception Handling**:
Add exception handling for possible runtime issues. For instance, when interacting with real IoT devices, one might encounter connectivity issues. 

```python
def toggle_status(self):
    try:
        self.status = not self.status
    except Exception as e:
        print(f"Error toggling device status: {e}")
```

### **3. Rule Implementation**:

**Dynamic Rule Creation**:
Instead of hardcoding rules, create a more dynamic mechanism for adding rules. 

- Store conditions and actions as lambda functions or similar constructs.
- Allow the user to create a rule by selecting a condition and an action from available options in the GUI.

**Rule Activation Feedback**:
Provide feedback when a rule is triggered. This can be through a GUI notification or simply printing to the console.

```python
def apply(self, devices):
    if self.condition(devices):
        self.action(devices)
        print(f"Rule triggered: {self.condition.__name__} -> {self.action.__name__}")
```

**Separate Rule File**:
Rules, just like devices, can also be modularized. Consider having a separate `rules.py` which can contain a library of predefined conditions and actions, as well as the logic to create and apply custom rules.

### **Conclusion**:
Improving modularity makes the codebase cleaner and more maintainable. Enhanced error handling ensures robustness and a better user experience. Improved rule implementation provides versatility, making it easier to extend functionalities. Remember, these suggestions are a starting point, and actual implementation might require further refinements based on specific requirements and use cases.

1. There are some commented out sections in the code, like setting text for automation and a button for toggling it, which might have been used in a previous version or for debugging/testing purposes.
2. The automation rule of turning on the lights when motion is detected is defined within the `Dashboard` class (in `create_automation_rule`), but it doesn't seem to be invoked in the provided code. So, this functionality might not be active in the current version.