Keepalive script for MAC OSX
============================

I build art installs using LibCinder and OpenFrameWorks. These installs are intended to run unmanaged, this script helps ensure they stay up and running and that the computer shuts down at a pre-determined time.

Download the code and place it in the same directory as your application.

In your application set it to write to a file every 2 seconds, I refer to this as as heartbeat. So long as the application is running and it is being modified the keepalive script remains dormant. If your application either quits unexpectedly or locks up then the heartbeat won't be updated and the keepalive script is triggered. It will kill the application and restart it for us.

How to use:
<pre>
	./keepalive My_App heartbeat.txt 18:00
</pre>

In this example my application 'My_App' is located in the same directory as the keep alive script, it is watching 'heartbeat.txt' for changes and at 18:00 it will terminate the application and shutdown the computer.

I use schedule the computer to turn back on at a set time and add a script to my 'Login Items' in order to restart the whole process.

In order for the script to be able to run 'shutdown' you will need to run 'visudo' to add permission for your user account. Check Google, plenty of instructions how to do this.

The script uses an additional helper script 'email' written in python to notify administrators of restarts and shutdowns.

