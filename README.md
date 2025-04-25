# csci3753-programming-assignment-3-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/csci3753-programming-assignment-3-solved/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;51260&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSCI3753 Programming Assignment 3  Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
<strong>Goal</strong>: Use Pthreads to code a DNS name resolution engine

<strong>&nbsp;</strong>1. Introduction

&nbsp;

In this assignment you will develop a multi-threaded application, written in C, that resolves domain names to IP addresses. This is similar to the operation performed each time you access a new website in your web browser. The application is composed of two subsystems, each with one thread pool: requesters and resolvers. The subsystems communicate with each other using a bounded array. See Figure 1 for a visual description.

&nbsp;

We have a number of files that list the domain name of a server for which we need an IP address.&nbsp; Your task is to create a program that will process a number of files containing the names of servers we want to reach and supply the list of IP addresses matching those host names.&nbsp;&nbsp; Your program (multi-lookup) will process a number of files containing a list of hostnames using a requester thread to process each file.&nbsp; Each requester thread will read each line of the file, parse the hostname, place the name into a shared data area, and record the processing in a file. You will also create a number of resolver threads that will take the names from the shared data area, find the IP address for that host name and write the results to a file.

Once all the files have been processed the requester threads will terminate. Once all the names have been processed the resolver threads will terminate and the program will terminate.

All the status information that needs to be recorded for the requestor threads will be written to a file named serviced.txt in the current working directory.&nbsp; All the status information that needs to be recorded for the resolver threads will be written to a file named results.txt in the current working directory. Just before termination, your program will print (to standard out) the total time that it took to process all the data.

<strong>&nbsp;</strong>

<strong>&nbsp;</strong>

<h1>2. Description</h1>
<h2>2.1 Input: Name Files</h2>
Your application will take as <strong>input</strong> a set of <strong>name files</strong>. Name files contain one hostname per line. Each name file should be serviced by a single requester thread from the requester thread pool. The number of requester threads may be less than or more than the number of input files.

&nbsp;

<h2>2.2 Requester Threads</h2>
Your application will take as <strong>input</strong> the <strong>number of requester threads</strong>. These threads service a set of name files, each of which contains a list of domain names. Each name that is read from each of the files is placed on a shared array. If a requester thread tries to write to the array but finds that it is full, it should block until a space opens up in the array. After servicing a name file, a requester thread checks if there are any remaining name files to service. If so, it requests one of the remaining name files next. This process goes on until all name files have been serviced. If there are no more name files remaining, the thread writes the number of files it serviced in a new line in a file named serviced.txt in the following format:

Thread &lt;thread id&gt; serviced ### files.

To get the thread id of a thread on Linux systems, use <strong>gettid( )</strong>.

<h2>2.3 Resolver Threads</h2>
The second thread pool is comprised of a set of resolver threads. The resolver thread pool services the shared array by taking a name off the array and querying its IP address. After the name has been mapped to an IP address, the output is written to a line in the results.txt file in the following format: <strong>www.google.com,74.125.224.81</strong>

If a resolver thread tries to read from the array but finds that it is empty, it should block until there is a new item in the array or all names in the input files have been serviced.

<h2>2.4 Synchronization and Deadlock</h2>
Your application should synchronize access to shared resources and avoid any deadlock or busy wait. You should use <strong>mutexes and conditional variables</strong> to meet this requirement. There are at least three shared resources that must be protected: the <strong>shared array, serviced.txt and result.txt</strong>. <strong><u>None of these resources is thread-safe by default.</u></strong>

<h2>2.5 Ending the Program</h2>
Your program must end after all names in each file have been serviced by the application. This means that all the hostnames in all the input files have received a corresponding line in the output file. At the end, your program must print the total runtime on the standard output. Use <strong>gettimeofday( )</strong> system call for this purpose.

&nbsp;

<strong>&nbsp;</strong>

<ol start="3">
<li><strong> What’s included in PA3? </strong></li>
</ol>
&nbsp;

Some files are included with this assignment for your benefit. You are not required to use these files, but they may prove helpful.

<ol>
<li><strong>c</strong> and <strong>util.h</strong>: These two files contain the DNS lookup utility function. This function abstracts away a lot of the complexity involved with performing a DNS lookup. The function accepts a hostname as input and generates a corresponding dot-formatted IPv4 IP address string as output.</li>
</ol>
Please consult the util.h header file for more detailed descriptions of each available function.

<ol start="2">
<li><strong>input/names*.txt</strong>: This is a set of sample name files. They follow the same format as mentioned earlier. Use them to test your program.</li>
<li><strong>results-ref.txt</strong>: This result file is a sample output of the IPs for the hostnames from the names1.txt file.</li>
<li><strong>py</strong>: This is a program to assist you in plotting performance metrics from running your program with different amounts of requesters and resolver threads. It is encouraged but not required to understand how this program works.</li>
</ol>
&nbsp;

<h1>4. Additional Specifications</h1>
&nbsp;

Many of the specifications for your program are embedded in the descriptions above. This section details additional specifications you must adhere to.

&nbsp;

<h2>4.1 Program Arguments</h2>
<strong>NAME</strong>

multi-lookup – resolve a set of hostnames to IP addresses

<strong>SYNOPSIS&nbsp; </strong>

multi-lookup &lt;# requester&gt; &lt;# resolver&gt; &lt;requester log&gt; &lt;resolver log&gt; [ &lt;data file&gt; …]

<strong>DESCRIPTION&nbsp; </strong>

The file names specified by &lt;data file&gt; are passed to the pool of requester threads which place information into a shared data area.&nbsp; Resolver threads read the shared data area and find the corresponding IP address.

&lt;# requesters&gt; number of requestor threads to place into the thread pool.

&lt;# resolvers&gt; number of resolver threads to place into the thread pool.

&lt;requester log&gt; name of the file into which all the requester status information is written.

&lt;resolver log&gt; name of the file into which all the resolver status information is written.

&lt;data file&gt; list of filenames that are to be processed.&nbsp; Each file contains a list of host names, one per line,&nbsp; that are to be resolved.

<strong>&nbsp;</strong>

<h2>4.2 Limits</h2>
If necessary, you may impose the following limits on your program. If the user specifies input that would require the violation of an imposed limit, your program should gracefully alert the user to the limit and exit with an error.

<ul>
<li><strong>MAX INPUT FILES</strong>: 10 Files (This is an optional upper-limit. Your program may also handle more files, or an unbounded number of files, but may not be limited to less than 10 input files.)</li>
<li><strong>MAX RESOLVER THREADS</strong>: 10 Threads. This is an upper-limit. Your program may also handle more threads.</li>
<li><strong>MAX REQUESTER THREADS</strong>: 5 Threads. This is an upper-limit. Your program may also handle more threads.</li>
<li><strong>MAX NAME LENGTH</strong>: 1025 Characters, including the null terminator (This is an optional upper-limit. Your program may handle longer names, but you may not limit the name length to less than 1025 characters.)</li>
<li><strong>MAX IP LENGTH: </strong>INET6 ADDRSTRLEN (This is an optional upper-limit. Your program may handle longer IP address strings, but you may not limit the name length to less than INET6 ADDRSTRLEN characters including the null terminator.)</li>
</ul>
&nbsp;

<h2>4.3 Error Handling</h2>
You must handle the following errors in the following manners:

<ul>
<li><strong>Bogus Hostname</strong>: Given a hostname that can not be resolved, your program should output a blank string for the IP address, such that the output file continues the hostname, followed by a comma, followed by a line return. You should also print a message to stderr alerting the user to the bogus hostname.</li>
<li><strong>Bogus Output File Path</strong>: Given a bad output file path, your program should exit and print an appropriate error to stderr.</li>
<li><strong>Bogus Input File Path</strong>: Given a bad input file path, your program should print an appropriate error to stderr and move on to the next file.</li>
</ul>
All system and library calls should be checked for errors. If you encounter errors not listed above, you should print an appropriate message to stderr, and then either exit or continue, depending upon whether or not you can recover from the error gracefully.

&nbsp;

<h1>5. External Resources</h1>
&nbsp;

You may use the following libraries and code to complete this assignment, as well as anything you have written for this assignment:

<ul>
<li>Any functions listed in util.h</li>
<li>Any functions in the C Standard Library</li>
<li>Standard Linux pthread functions</li>
<li>Standard Linux Random Number Generator functions</li>
<li>Standard Linux file i/o functions</li>
</ul>
&nbsp;

If you would like to use additional external libraries, you must clear it with the TA first.&nbsp; <strong>You will not be allowed to use pre-existing thread-safe queue or file i/o libraries.</strong>&nbsp; One of the goals of this assignment is to teach you how to make non-thread-safe resources thread-safe. Specifically, when you are interacting with these data resources, you will need to look up whether whatever any functions you want to use are thread safe or not.&nbsp; <a href="http://man7.org/linux/man-pages/man7/attributes.7.html">http://man7.org/linux/man</a><a href="http://man7.org/linux/man-pages/man7/attributes.7.html">–</a><a href="http://man7.org/linux/man-pages/man7/attributes.7.html">pages/man7/attributes.7.html</a> is a helpful page that formally defines MT-safe code. You can look for this safety value on man pages for the functions you are interested in using.

&nbsp;

<h1>6. What you must submit</h1>
&nbsp;

To receive full credit, you must submit the following items to Moodle by the due date. Please combine the files into a single zip or tar archive.

<ul>
<li><strong>multi-lookup.c</strong>: Your program, conforming to the above requirements.</li>
<li><strong>multi-lookup.h</strong>: A header file containing prototypes for any function you write as part of your program.</li>
<li><strong>Makefile</strong>: A makefile that builds your program as the default target. It should also contain a “clean” target that will remove any files generated during the course of building and/or running your program.</li>
<li><strong>README</strong>: A readme describing how to build and run your program.</li>
<li><strong>txt</strong>: Run your program over the five input files provided in the input directory for six different scenarios: 1 requester thread and 1 resolver thread, 1 requester thread and 3 resolver threads, 3 requester threads and 1 resolver thread, 3 requester threads and 3 resolver threads, 5 requester threads and 5 resolver threads, and 8 requester threads and 5 resolver threads.</li>
</ul>
For each scenario, provide the following information in a file named performance.txt. Use the following format:

Number for requester thread = xxx

Number for resolver thread = xxx

Total run time: xxx

For each thread, thread id and the number of input files serviced

&nbsp;

<strong><u>NOTE:</u></strong> This should be trivial to implement in a script or in another C program, although you are not required to do so.&nbsp; Later, you can run your program with the provided <strong><em>performance.py</em></strong> script to generate a 3D graph displaying these relationships. This step is <strong>OPTIONAL</strong>. Use the following command to run the script. Sending output to <strong><em>/dev/null</em></strong> will keep your terminal clear and the ‘&amp;’ will run the program in the background.

<h2>./performance.py multi-lookup &gt; /dev/null &amp;</h2>
If your program can work with the python code, at the end of your performance.txt file, you can provide a 1-2 paragraph explanation of the differences in runtimes among the six scenarios, comparing your results to those generated by the graph.

Any additional files necessary to build or run your program.

&nbsp;

&nbsp;

<h1>7. Grading</h1>
&nbsp;

<strong>Implementation</strong>: <strong>50%</strong> of your grade will be based on the performance of the best implementation that you&nbsp; provide, and the quality of your submitted code. We will test your implementation on a number of test cases.

<strong>Interview</strong>: <strong>50%</strong> of your grade will be based on your interview. You will be expected to explain your work and answer additional questions. You are expected to understand all concepts pertaining to the assignment.

&nbsp;

To receive full credit your program <strong>must</strong>:

<ul>
<li>Meet all requirements elicited in this document.</li>
<li>Assuming your code compiles and does all functional requirements of this assignment:
<ul>
<li>Build with “-Wall” and “-Wextra” enabled, producing no errors or warnings o Run without leaking any memory, as measured using <strong><em>valgrind</em></strong> o You are not allowed to use global variables</li>
<li>Don’t use pre-existing thread safe queues or i/o functions</li>
</ul>
</li>
<li><strong>If your code does not run, you will not get any points for the code part! </strong></li>
</ul>
To verify that you do not leak memory, the TAs may use <em>valgrind</em> to test your program. To install <em>valgrind</em>, use the following command:

<strong>sudo apt-get install valgrind</strong>

And to use <em>valgrind</em> to monitor your program, use this command:

<h2>valgrind ./pa3main text1.txt text2.txt …. textN.txt results.txt</h2>
<em>Valgrind</em> should report that you have freed all allocated memory and should not produce any additional warnings or errors.

You can write your code in any environment you like. But you have to make sure that your programs can be compiled and executed in the Virtual Machine that has been provided for this class or on the CSEL machines.

Do not use global variables – instead pass parameters you need in via a struct to the pthread_create function.

&nbsp;

<h1>8. References</h1>
&nbsp;

Refer to your textbook and class notes on the Moodle for descriptions of producer/consumer and reader/writer problems and the different strategies used to solve them.

&nbsp;
