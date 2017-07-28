# AirSimMulti

AirSimMulti is a fork of Microsoft AirSim with the main aim of simulating multiple drones. It is a work in progress, and uses an older version of Microsoft AirSim as its base. Basic features such as simulating multiple vehicles, independent control and image recording from different vehicles are working. 

In order to try it out for yourself, please clone the repository, and use it within Unreal Engine similar to the default version of AirSim. Three changes that would have to be made are:

1. Within Unreal Engine, splitscreen would have to be disabled. This can be done by navigating to Unreal->Project Settings->Maps and Modes and by unchecking splitscreen.

2. Depending on the number of drones being simulated, additional PlayerStarts would have to be added to specify the accurate spawn locations for each drone. Each of these PlayerStart icons contains a tag in "PlayerStart->Details", which needs to be named as One, Two, Three and so on.

3. For HIL to work, within the settings.json file, the right COMports need to be specified based on where the PIXHAWK modules are enumerated. This code has not been tested with SITL yet.

Each drone that is simulated within Unreal uses its own IP address (127.0.0.1, 0.2, 0.3...) in order to facilitate offboard control from external modules such as DroneShell and PythonClient. The branches 2uav and 3uav simulate 2 and 3 drones respectively, whereas 'swarm' simulates 5 UAVs and also acts as a base for extending the functionality to more drones.

Documentation about how to extend AirSimMulti to a custom number of vehicles is coming soon.

# Welcome to AirSim

AirSim is a simulator for drones (and soon other vehicles) built on Unreal Engine. It is open-source, cross platform and supports hardware-in-loop 
with popular flight controllers such as Pixhawk for physically and visually realistic simulations. It is developed as an Unreal plugin that can 
simply be dropped in to any Unreal environment you want. 

Our goal is to develop AirSim as a platform for AI research to experiment with deep learning, computer vision and reinforcement learning algorithms 
for autonomous vehicles. For this purpose, AirSim also exposes APIs to retrieve data and control vehicles in a platform independent way.

**Check out the quick 1.5 minute demo**

[![AirSim Demo Video](docs/images/demo_video.png)](https://youtu.be/-WfTr1-OBGQ)

# Development Status

This project is under heavy development. The current release is in beta and all APIs are subject to change. The next major features currently in works are standalone mode, 
several API enhancements and Python client support. We welcome contributions!

# How to Get It
## Prerequisites
To get the best experience you will need Pixhawk or compatible device and a RC controller. This enables the "hardware-in-loop simulation" for 
more realistic experience. [Follow these instructions](docs/prereq.md) on how to get it, set it up and other alternatives.

## Windows
There are two ways to get AirSim working on your machine. Click on below links and follow the instructions.

1.  [Build it and use it with Unreal](docs/build.md)
2.  [Use the precompiled binaries](docs/use_precompiled.md)

## Linux
Good news! Several people have reported that they have been running in Linux as well as OSX successfully. Please check [conversations on Linux](https://github.com/microsoft/airsim/issues?utf8=%E2%9C%93&q=linux). 
You can find our experimental [Linux build instruction here](docs/linux_build.md). We are still in process of making this little bit nicer and release official Linux build soon! 
AirSim code is designed to be cross platform and we would love to make AirSim available on other platforms as well. 

# How to Use It

## Video Tutorials
- [Walkthrough Demo Video](https://youtu.be/HNWdYrtw3f0)
- [AirSim Setup  Video](https://youtu.be/1oY8Qu5maQQ) (shows you all the setup steps)

## Manual flights
If you have a Pixhawk flight controller (or compatible device) and a remote control you can manually control the drones in the simulator 
and fly around.

![record screenshot](docs/images/DroneGIF-03.gif)

[More details](docs/manual_flight.md)

## Gathering training data
There are two ways you can generate training data from AirSim for deep learning. The easiest way is to simply press the record button on the lower right corner. 
This will start writing pose and images for each frame. 

![record screenshot](docs/images/record_data.png)

If you would like more data logging capabilities and other features, [file a feature request](https://github.com/Microsoft/AirSim/issues) or contribute changes. 
The data logging code is pretty simple and you can modify it to your heart's desire.

A more complex way to generate training data is by writing client code that uses our APIs. This allows you to be in full control of how, what, where and when 
you want to log data. See the next section for more details.

For MavLink enabled drones, you can also use our [Log Viewer](docs/log_viewer.md) to visualize the streams of data.

## Programmatic control
The AirSim exposes easy to use APIs in order to retrieve data from the drones that includes ground truth, sensor data as well as various images. It also exposes 
APIs to control the drones in a platform independent way. This allows you to use your code to control different drones platforms, for example, Pixhawk or DJI Matrice, 
without making changes as well as without having to learn internal protocols details. 

These APIs are also available as a part of a separate independent cross-platform library so you can deploy them on an offboard computer on your vehicle. 
This way you can write and test your code in simulator and later execute it on the real drones. Transfer learning and related research is one of our focus areas.

[More details](docs/apis.md)

# Participate
## Paper
You can get additional technical details in [our paper (work in progress)](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/02/aerial-informatics-robotics-TR.pdf). Please cite this as:
```
@techreport{MSR-TR-2017-9,
     title = {{A}erial {I}nformatics and {R}obotics Platform},
     author = {Shital Shah and Debadeepta Dey and Chris Lovett and Ashish Kapoor},
     year = {2017},
     institution = {Microsoft Research},
     number = {{M}{S}{R}-{T}{R}-2017-9}}
}
```

## Contribute
We welcome contributions to help advance research frontiers. 

- [More on our design](docs/design.md)
- [More on our code structure](docs/code_structure.md)
- [Contribution Guidelines](docs/contributing.md)

## Contact
Join the [AirSim group at Facebook](https://www.facebook.com/groups/1225832467530667/) to stay up to date or ask any questions.

## FAQ

If you run into problems, check the [FAQ](docs/faq.md) and feel free to post issues on the [AirSim github](https://github.com/Microsoft/AirSim/issues).

## License
This project is released under MIT License. Please review [License file](LICENSE) for more details.
