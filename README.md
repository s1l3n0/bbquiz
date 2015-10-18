# bbquiz

**bbquiz**
*quiz importer for BlackBoard* 

(still quite a prototype)

BlackBoard is the online didactic environment in use at the UvA and the VU, and plausibly in other university (its full name is BlackBoard Learn 9.1).

In order to fasten the process of creating new quizzes for automatized evaluation, it allows to upload them offline. 
Unfortunately, the batch file format is not easy to be handled by humans (see doc/bbguidelines.txt for further details).

Therefore, I made this script to convert text files with a much simpler template (named .bbquiz) into the Black Board file format, ready to be uploaded!

## .bbquiz File template

* A bbquiz file consists of multiple answers (MA), multiple choice (MC), and essay (ESS) questions.  
* MA and MC are composed by a question and answers. The first line counts as the question; the following line as the answers. An empty line means that the quiz has finished. The correct answers end with *<tab> + X*. Pay attention: there is a tabulation, not empty spaces! The distinction between MA and MC is made automatically by the script. 
* ESS questions consist of a line with a text with the request, and *some empty space* in the following line.

example: ./examples/test.bbquiz
```
Multiple answer question?
This is a wrong response.
This is correct.	X

Multiple choice question?
This is a wrong response.
This is correct.	X
This is not correct as well.
This is correct, too.   X

Please write an essay.
 

Another question?
No, it is enough.   X
Yes, please.

'''

output: ./examples/test.2bb
```
MC	Multiple answer question?	This is a wrong response.	incorrect	This is correct.	correct
MC	Multiple choice question?	This is a wrong response.	incorrect	This is correct.	correct	This is not correct as well.	incorrect	This is correct, too.   X	incorrect
ESS	Please write an essay.
MC	Another question?	No, it is enough.   X	incorrect	Yes, please.	incorrect
'''

## Usage examples

**conversion**
```
> java -jar bbquiz.jar ./examples/test.bbquiz
'''

**upload**
Once the .2bb file is ready, go on BlackBoard, and then 
*Control Panel > Course Tools > Tests, Surveys and Pools > Tests* 
Click on *Import Test* and select your .2bb file.
