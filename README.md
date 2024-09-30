<p align="center">
  <h3 align="center">MACOS Havoc C2 Client</h3>
  <h4 align="center">Paper Compile MacOS Havoc C2 Client</h4>
</p>

###### Today I had some issues compiling the Havoc Client on my MacOS, and after finding very little content to help, I decided to create this repository to assist others who might be facing the same problem on their MacOS.
###### Well, I will only talk about the Client because that was the only one I had trouble with, and the only one I needed, as my teamserver is on another Ubuntu server.
> [!Important]
> ###### Note: I imagine there might be other ways to compile everything without any errors, but this was the only one that worked for me. Downloading the CPP dependencies via brew, as I saw in some issues and even in Havoc's own manual, was a complete disaster.

##### 1. Installing cmake, qt, python, go
```
brew install cmake qt@5 python@3.10 && brew link --overwrite qt@5
```

##### 1. Cloning the Havoc repository
```
git clone https://github.com/HavocFramework/Havoc
```

###### After cloning the Havoc repository, go to the client and external folders with your terminal, and delete everything.
```
cd Havoc/client/external && rm -rf *
```

##### 2. Downloading Havoc's CPP dependencies.
```
git clone https://github.com/ToruNiina/toml11 && \
git clone https://github.com/fmtlib/fmt && \
git clone https://github.com/gabime/spdlog && \
git clone https://github.com/nlohmann/json && \
cd toml11 && git checkout tags/v3.0.0 && cd ..
```

##### 3. Configuring the CPP dependencies in Havoc.
###### To do this, open the CMakeLists.txt file located in the client folder.
###### Go to line 30, and the code should look like this:

<img width="351" alt="image" src="https://github.com/user-attachments/assets/a4c4d0af-6e47-4817-a489-7d6cc4a2a6bc">

###### Comment out the code in the screenshot above and configure each folder for the dependencies you cloned into the external folder. It should look something like this:

<img width="834" alt="image" src="https://github.com/user-attachments/assets/e34c8aeb-6e95-4a44-8a21-88a800537e0e">

###### Now just run `make` in the client folder, and the Havoc Client will compile perfectly.
```
make
```

###### After the compilation is finished, you just need to start Havoc from the project's root folder.
```
$ ./client/Havoc client
```

<img width="612" alt="image" src="https://github.com/user-attachments/assets/092c65a0-e91f-47f9-92f9-60f90a9828e1">
