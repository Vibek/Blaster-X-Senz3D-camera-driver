# Blaster-X-Senz3D-camera-driver

The is package for Create Blaster-X senz3D camera. The instruction for isntalltion the DepthSenseSDK and Softkinetic installion for ROS Groovy in Ubuntu 12.04 LTS 32 bit system.

Normal installtion in ubuntu 12.04 LTS can be done by the following step: 1. Download the SDK DepthSenseSDK-1.9.0-5.i386-tar.run from our repository. 2. Go to folder where it is downloaded

           chmod +x DepthSenseSDK-1.2.2.958-i386-gcc-tar.run
           sudo ./DepthSenseSDK-1.2.2.958-i386-gcc-tar.run
1. check the installation is succesfull by check the /opt/softkinetic/DepthSenseSDK/lib exist or not
2. Then run sudo ldconfig to regenerate the ld.so cache or what ever. Now you can link agianst the libraries.
3. Next, you need to fake having libudev.so.0. Thankfully libudev.so.1 worked fine so run

             sudo ln -s /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0

5. Once you done with step 7 successfully, your next task to run a sample file to check out if everything works well.

             Cd /opt/softkinetic/DepthSenseSDK/bin 

             ./DepthSenseViewer 
6. If once you will run the above command, DepthSenseViewer will appeared. In some case it might be show "No device or node Selected". At-least in my case it does happens. Best to resolve the problem is to give a permission to the USB ports to access the camera. One can done with following installation.

             sudo apt-get install gstreamer-tools

             gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! xvimagesink
7. If all done according the suggestion a window will pop up with RGB stream.
