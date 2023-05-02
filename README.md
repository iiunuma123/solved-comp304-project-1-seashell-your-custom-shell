Download Link: https://assignmentchef.com/product/solved-comp304-project-1-seashell-your-custom-shell
<br>
This project aims to familiarize you with the Unix system call interface and the shell by letting you implement several features in a shell, called <strong>seashell</strong>, using C/C++. A shell is a program that provides interface to the operating system by gathering input from the user and executing programs based on that input. Once executed, the <strong>seashell </strong>will read both system and user-defined commands from the user. The projects has six parts:

<h2>Part I</h2>




<ul>

 <li>Use the skeleton program provided as a starting point for your implementation. The skeleton program reads the next command line, parses and separates it into distinct arguments using blanks as delimiters. You will implement the action that needs to be taken based on the command and its arguments entered in <strong>seashell</strong>. Feel free to modify the command line prompt and parser as you wish.</li>

 <li>Read <em>”Project 1- Unix Shell” </em>at the end of Chapter 3 in the book starting from P12 (10th edition). That will be useful.</li>

 <li>Use <strong>execv() </strong>system call (instead of <strong>execvp()</strong>) to execute common Linux programs (e.g. ls, mkdir, cp, mv, date, gcc) and user programs by the child process. The difference is that <strong>execvp() </strong>will automatically resolve the path when finding binaries, whereas for <strong>execv() </strong>your program should search the path for the command invoked, and execute accordingly.</li>

</ul>

<h2>Part II</h2>

(10 points) <strong>shortdir</strong>: In this part, you will implement a new command, <strong>shortdir</strong>, to associate short names with the current directory. The purpose is to reach the directory (change

1

<em>Part III</em>

to the directory) with a short name instead of typing the whole path. For instance, we associate the name <em>matlab </em>with the directory <em>/usr/local/MATLAB/R2018b/ </em>and use it to change to that directory by using the name <em>matlab</em>. You will also implement supportive options for the <em>shortdir </em>as follows:

<ul>

 <li><em>shortdir set name</em>: associates <em>name </em>with the current directory. Overwrites an existing association.</li>

 <li><em>shortdir jump name</em>: changes to the directory associated with <em>name</em>.</li>

 <li><em>shortdir del name</em>: deletes the name-directory association.</li>

 <li><em>shortdir clear</em>: deletes all the name-directory associations.</li>

 <li><em>shortdir list</em>: lists all the name-directory associations.</li>

</ul>

Note that this command <strong>lives across shell sessions</strong>; when a new shell session is started, it should remember the associations from the previous sessions. Refer to Listing 1 for sample usage of shortdir.

Listing 1: Setting alias for a directory using shortdir

<table width="633">

 <tbody>

  <tr>

   <td width="633">seashell&gt; pwd/usr/local/MATLAB/R2018b seashell&gt; shortdir set matlabmatlab is set as an alias <strong>for </strong>/usr/local/MATLAB/R2018b/ …seashell&gt; shortdir jump matlab seashell&gt; pwd/usr/local/MATLAB/R2018b</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

<h2>Part III</h2>

<strong>highlight</strong>: In this part, you will implement the <em>highlight </em>command that takes a word-color pair and a text file as an input. For each instance of the word appearing in the text file, the command prints the line where the word appears and highlights the word with that color. The colors can be one of the r (red), g (green) or b (blue) colors. The word check is not case-sensitive. The command syntax and its sample usage are as shown below:

seashell&gt; highlight &lt;word&gt; &lt;r | g | b &gt; &lt;filename&gt; seashell&gt; highlight language r file.txt

The programming <strong>language </strong>used for this code is C.

The first three letters of English <strong>language </strong>are A B and C.

<em>Part IV</em>

<h2>Part IV</h2>

In this part of the project, you will implement a new <strong>seashell </strong>command, <em>goodMorning</em>:

<ul>

 <li>This command will take a time and a music file as arguments and set an alarm to wake you up by playing the music using rhythmbox. In order to implement <em>goodMorning</em>, you may want to use the crontab command.</li>

</ul>

Listing 2: Sample usage of goodMorning command

<table width="599">

 <tbody>

  <tr>

   <td width="599">seashell&gt; goodMorning 7.15 /home/musics/muse.mp3</td>

  </tr>

 </tbody>

</table>

1

Before implementing the new command inside <strong>seashell</strong>, you should get familiar with crontab (if you decide to use crontab) and rhythmbox on a regular shell.

More info about rhythmbox:

http://manpages.ubuntu.com/manpages/hardy/man1/rhythmbox-client.1.html More info about crontab: http://www.computerhope.com/unix/ucrontab.htm

<h2>Part V</h2>

In this part, you will implement the <em>kdiff </em>utility to compare two files in given paths. Sample usage of <em>kdiff </em>to compare two files is given in Listing 3. The utility will operate in two modes:

<ul>

 <li>−<em>a</em>: the utility reads the input files (<em>txt </em>and <em>file2.txt</em>) as text files and compares them line-by-line. If the two files are different, the utility first prints the differing lines from each file and then prints the count of differing lines as shown in Listing 3. The utility checks for file extensions and if they are not .txt, flags an error. If the two files are identical, it displays the message ”The two files are identical”.</li>

 <li>−<em>b</em>: the utility reads the input files as binary files and compares them byte-by-byte. If the two files are different, the utility prints the message ”The two files are different in xyz bytes”, where xyz is the number of bytes different between the files. The utility accepts files with any extension in this case. If the files are identical, the message saying ”The two files are identical” is displayed. Refer to Listing 3 for the sample output.</li>

</ul>

If the user does not provide either −<em>a </em>or −<em>b</em>, −<em>a </em>is assumed by default.

<strong>Note</strong>: You are not allowed to use existing file comparison tools (such as <em>diff</em>) to compare the files. We expect you to use C/C++ file I/O operations to complete this task. You may use the existing tools to verify your output.

Listing 3: <em>kdiff </em>utility sample output

<table width="633">

 <tbody>

  <tr>

   <td width="633">seashell&gt; kidff -a file1.txt file2.txtThe two text files are identical</td>

  </tr>

 </tbody>

</table>

1

2

3

<em>Part VI</em>

<table width="633">

 <tbody>

  <tr>

   <td width="633">seashell&gt; kdiff -a file1.txt file2.txtfile1.txt:Line 23: A quick brown fox jumps over the lazy dog file2.txt:Line 23: A swift squirrel climbs the tree file1.txt:Line 41: Corona cases today = 1200 file2.txt:Line 41: Corona cases today = 6892 different lines foundseashell&gt; kdiff -a file.txt file2.txt The two files are identicalseashell&gt; kdiff -b file1.bin file2.bin The two files are identicalseashell&gt; kdiff -b file1.bin file21.binThe two files are different in 8213 bytes</td>

  </tr>

 </tbody>

</table>

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

<h2>Part VI</h2>

In this final part, you will implement a command of your choice in <strong>seashell</strong>. Come with a new, non-trivial command and implement it inside <strong>seashell</strong>. Creativity will be rewarded and selected commands will be shared with your peers in the class. It is possible that command you come up with is already implemented in Unix. That should not stop you from implementing your own but do not simply execute the existing Unix version of it.