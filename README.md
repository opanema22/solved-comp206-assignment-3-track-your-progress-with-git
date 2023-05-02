Download Link: https://assignmentchef.com/product/solved-comp206-assignment-3-track-your-progress-with-git
<br>
To provide a light-weight experience with several of the software systems concepts of the past few weeks: Makefiles, Git, C structures, C function pointers, and bash scripting.

<strong><em>NOTE</em></strong>: This Assignment is meant to take *much* less time than the other 3. I estimate you should be able to complete it in 2 hours max, so use this in your time management and do post on My Courses right away if you get stuck on something.

Getting started:

The A3 repository is at: <u><a href="https://github.mcgill.ca/COMP206Winter2018/Assignment3">https://github.mcgill.ca/COMP206Winter2018/Assignment3</a></u><a href="https://github.mcgill.ca/COMP206Winter2018/Assignment3">.</a> Create your own mirror to start working on the code:

<ol>

 <li>Login to <u><a href="https://github.mcgill.ca/">https://github.mcgill.ca/</a></u><a href="https://github.mcgill.ca/">,</a> click the green “New Repository” button</li>

 <li>Enter repository name “Assignment3_submission” and choose “Private”. Press green “Create repository” button. You should now see an empty repo.</li>

 <li>In a terminal, type the following commands to get a mirror of the A3 files:

  <ol start="3">

   <li>$ git clone –bare <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="8cebe5f8ccebe5f8e4f9eea2e1efebe5e0e0a2efed">[email protected]</a>:COMP206Winter2018/Assignment3.git

    <ol>

     <li>If you get any permissions error here, remember you might need to add new</li>

    </ol></li>

  </ol></li>

</ol>

SSH keys here: <u><a href="https://github.mcgill.ca/settings/keys">https://github.mcgill.ca/settings/keys</a></u>

<ol start="3">

 <li>$ cd Assignment3.git</li>

 <li>$ git push <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="ee89879aae89879a869b8cc0838d89878282c08d8f">[email protected]</a>:&lt;YOUR_USERNAME&gt;/Assignment3_submission.git

  <ol>

   <li>Alternative, if you get an error: “$ git push <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="bfd8d6cbffd8d6cbd7cadd91d2dcd8d6d3d391dcde">[email protected]</a>:&lt;YOUR_USERNAME&gt;/Assignment3_submission.git master” d. $ cd ..</li>

  </ol></li>

 <li>$ rm –rf Assignment3.git</li>

 <li>$ git clone <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="a8cfc1dce8cfc1dcc0ddca86c5cbcfc1c4c486cbc9">[email protected]</a>:&lt;YOUR_USERNAME&gt;/Assignment3_submission.git You will now have the folder “Assignment3_submission” in your working directory, and if you refresh your GitHub page, you’ll see the files there also. This is the place to do all your work.</li>

</ol>

Intro: 206-flix

One of the most important operations for a software system these days is to analyze information about a large collection of users. This can be for reasons in the news right now like influencing politics, but it is often for really helpful reasons like finding us good songs and movies we’re likely to enjoy, based on the recommendations of similar people.

In this assignment, we will look at a very simple prediction engine, designed to recommend movies based on your answers to the 13 “silly questions” that we collected in Assignment 0. We’ve provided you all of the necessary C code and data. You will just need to read and understand this code and then write a few supporting software system components so the code can be built and can make predictions for everyone in the class.

<h1>Question 1: Track your progress with Git</h1>

If you completed “Getting Started”, you now have your own GitHub repo and local copy checked out. You must continue to use Git while you complete the other tasks. Make at least 5 commits that are tracked and have reasonable log messages (the number of commits will show up on “code” tab of your GitHub page and starts at 2 which are made by me. Yours should say 7 minimum when you’re done). It’s not necessary to branch, merge or any other complex operation, but feel free to try this if you’d like.

The workflow you’ll probably find most convenient for making a commit is:

<ol>

 <li>Use your text editor to create or modify some files in the repository. Save them.</li>

 <li>Run “$ git add &lt;filenames&gt;” which tells git the changes exist.</li>

 <li>Run “$ git commit –m &lt;log_message&gt;” which tells git you want the changes to stick, and describes them with your log message.</li>

 <li>Run “$ git push”, which shares the commit from your local folder to GitHub. After this, you should see the files changed, and the commit counter should increase.</li>

</ol>

<h1>Question 2: Code Reading (30 marks)</h1>

The first important thing is for you to understand the provided code. It uses structs, function pointers and pre-compiler macros to deal with the various types of data that were entered to answer the questions. You should open the C files in the src and include directories, trace through and understand how they work, and then answer the following 3 questions with 5 lines of text maximum each:

<ul>

 <li>Explain the overall function-call structure of the program. Starting with main, which functions are called and in what order. Include those abstracted through function pointers and precompiler macros, but stop before you get to C built-ins like strcpy or atoi.</li>

 <li>Consider the <strong>LOAD_FIELD</strong> function, which converts all data from the user’s text input into the struct’s fields. Explain how this single function can handle various types of data.</li>

 <li>Consider the global integer array Explain why this is the correct way to compute the offset to each field in the struct, based on what we learned in class. It may be helpful to check the documentation of <strong>offsetof </strong>here<a href="http://en.cppreference.com/w/c/types/offsetof">: </a><u><a href="http://en.cppreference.com/w/c/types/offsetof">http://en.cppreference.com/w/c/types/offsetof</a></u><a href="http://en.cppreference.com/w/c/types/offsetof">.</a></li>

</ul>

Write your answers in the README.md file located in the git repository. Use mark-down syntax, including at least 2 levels of header and 1 list. Instructions here:

<u><a href="https://guides.github.com/features/mastering-markdown/">https://guides.github.com/features/mastering</a><a href="https://guides.github.com/features/mastering-markdown/">–</a><a href="https://guides.github.com/features/mastering-markdown/">markdown/</a></u>

<h1>Question 3: Create the Makefile</h1>

The project currently has no Makefile, and therefore must be built manually with the command:

$ gcc -Iinclude src/movie_recommender.c src/preferences.c src/distances.c -o movie_recommender

(Note the first option is read out “minus capital eye”, which tells gcc to look for .h headers in the directory called include.)

Add a Makefile to the repository (use git add, commit, push). When complete, simply typing “$ make” in the directory must produce the file “movie_recommender”, recompiling it only if one of the .c or .h files has changed. You are not meant to change any C files for this assignment, but you can test with “$ touch src/preferences.c” for example, which simply updates the modification time, and triggers recompile Typing “$ make clean” must then delete this file. You are allowed to create the simplest  Makefile that accomplishes this and are not obliged to use any make macros or complex features.

<h1>Question 4: Create generate_all_predictions.bash</h1>

After building, the code can be run with the following example: $ ./movie_recommender query/daves_preferences.txt data/* Top movie pick for user David Meger is: Brooklyn.




The program’s first argument is a filename for the target user (the one who needs a recommendation) and all other files listed are considered “data”, which are mined to make a good suggestion. Note that the “*” character expands to give your program every filename in the data directory. Because the prediction is based on finding the “nearest” user, it’s important that the target is not also listed in the “data” list, otherwise they will always just be told to watch their own favorite movie.

Write “generate_all_predictions.bash” that generates predictions for all users looping over all files in the data directory and treating them one by one as the “target”. For each target:

<ol>

 <li>Move the target out of the data directory and into the query folder</li>

 <li>Run the movie_recommender program as shown</li>

 <li>Move the target back into the data folder so it can be used next time.</li>

</ol>

Slide 43 of Lecture15 is a good resource to get started here. When complete, your script should be around 5-10 lines long and should get 205 lines out output that look as follows:

$ bash generate_all_predictions.bash

Top movie pick for user Benjamin Labrecque is: Spirited Away.

Top movie pick for user Susan Matuszewski is: Ile Flottante.

Top movie pick for user Brendan Furtado is: La La Land.

Top movie pick for user Andy Zhen is: .

Top movie pick for user Andy Zhen is: .

Top movie pick for user Shayan Sheikh is: Brooklyn.

Top movie pick for user Kathy Tam is: About Time.

Top movie pick for user Yuxue Zhu is: Across the the Universe.




<strong>Note</strong>: The code is imperfect and some users have entered their preferences in slightly different formats. So, you may see segmentation faults and core dumps occasionally. This is not your responsibility to fix, just ignore them as long as you get mostly good predictions