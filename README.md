# Fully Functional DualSense Haptic Feedback on Linux

After weeks of investigating, I finally found a definitive way to get the DualSense's cool Haptic Feedback effects to work on Linux, in games such as Deathloop, Ghostwire: Tokyo, Final Fantasy VII Remake, etc. This is only possible thanks to ClearlyClaire's awesome patches made for Wine.
There'll be two ways to make this work: 
- The first and easiest is to just download one of the Releases I've precompiled. You'll just need to extract the .tar.xz to ```~/.steam/root/compatibilitytools.d```, then select this Proton version within Steam.
- The second and more involved is to compile Proton from scratch and applying the patches. The main advantage of doing it this way is that you won't depend on me to update this, so there's that. But worry not, I will try to update this regularly, so you probably won't need to do this at all. If you want to, however, lucky for you, because the steps are quite simple!

#### Only follow the steps below if you want to build it from scratch! If you download from the releases, you absolutely do NOT need to do the following!
First, you'll need to open a Terminal window and (if you haven't already) install git.

Then,

- ``` git clone https://github.com/Mutcholoko/Haptic-Feedback-Linux.git ```
- ``` git clone --recursive https://github.com/ValveSoftware/Proton.git ``` (this may take a while)
- ``` cd Proton ```
- ``` cd wine ```
- ```git apply /home/Haptic-Feedback-Linux/patch1.patch ```
- ```git apply /home/Haptic-Feedback-Linux/patch2.patch ```
- ```git apply /home/Haptic-Feedback-Linux/patch3.patch ```
- ```cd .. ```
- ``` make install ```

Now, take a seat and relax. It will take a few minutes. Some dependencies will probably be missing, so just download them with dnf or apt or whatever your distro uses. Also, if you use Fedora like me, you'll need to disable SELinux to compile this, as it relies on Docker.
After compiling, the makefile will already put Proton on the right place, so all you need to do is to restart Steam and then (remember to change the compatibility tool to be the one you just compiled) open up any game with Haptic Feedback.

Honestly, I am so happy with this. Being able to play games with Haptic Feedback on Linux is something I've been wanting for a long time now. Glad to finally get it to work. Again, all thanks to @ClearlyClaire for making these patches!
