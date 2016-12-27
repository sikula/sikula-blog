Title: The Hackers Sandbox: Destiny   
Date: 2016-12-26
Category: CTF


<h3>The Hackers Sandbox Walkthrough: Destiny (Default Mission Package)</h3>


<p>The Hackers Sandbox is a interactive hacking simulator. It is a standalone application that can be run on Windows, Linux and OSX that is used to emulate Virtual Machines. From their website: "It features an advanced and scriptable gaming engine which is extendable using Lua Script. You can create your own playable mission-packs to share with your friends or the community."
<br>This walkthrough will cover the default mission pack called Destiny that comes with The Hackers Sandbox.</p>


<p>You find more about The Hackers Sandbox on its official website: <a href src="http://www.flyingmonkeyarmy.com/">www.flyingmonkeyarmy.com</a></p>

<!-- ### Level 1 ### -->
<br>
<h2>Level 1: area6</h2>
<p>First step is straight forward, login with the credentials provided.</p>
Username = m101
<br>
Password = area6
<br>

<p>Using the <i>ls</i> command we can see there is a file, using <i>cat welcome</i> to view the contents of the file we learn the goal of this level is to gain root access.  Lets being by probing around and seeing which directories and file we have access to. On this machine there are 9 primary directories.</p>

<i><b>Figure 1.1: Output of the command 'ls /'</b></i>
<br>
<img src="/images/level1_1.png" />

<p>Next lets go through each of the directories and any sub-directories and try and see the contents of any files or interesting commands.  The first directory <i>/bin</i> contains 3 more commands, <i>nmap, wget, wwwlook</i>.  Let's continue on for now, these commands may be helpful later down the road.  The next directory <i>/etc/</i> gives us access to <i>/etc/passwd</i> which even gives us what looks like the hashes of all users, including root!</p>

<i><b>Figure 1.2: Contents of /etc/passwd file</b></i>
<br>
<img src="/images/level1_2.png" />
<br>
From here we have 2 possible paths:

  - Use a search engine to search for the hash and see if anything comes up
  - Keep searching on the local machine

<p>As of writing this using a search engine only turns up 2 websites that clearly solutions or a forum trying to solve this same puzzle. Since its not a common hash type like MD5 lets go back to the local machine! Simply looking at someone elses password is just cheating :P</p>
<br>
<p>After looking through more directories we find that the tool <i>hashcat</i> is on the machine, lets run it and see what we need to do to crack the root password hash.  <i>Hashcat</i> wants only 1 input parameter, the hash. Lets try the root user account hash. SUCCESS!</p>

<i><b>Figure 1.3: The Password to the root account is: gravity98</b></i>
<br>
<img src="/images/level1_3.png" />



<!-- ### Level 2 ### -->
<br>
<h2>Level 2:</h2>

