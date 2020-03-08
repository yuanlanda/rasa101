# Dialogue management with RASA 101



## Step 1 Reflection

- First of all, I have spent a lot of time on installing rasa on my Mac. I have tried `pip install rasa ` , the terminal keeps popping errors like: 

  `python setup.py egg_info" failed with error code 1`

  I guess maybe the version of python2 on my computer is a little bit too old, so I changed to use `pip3 ` to install rasa. It worked but when I tried `rasa init` in the next step, it throws an error:

  `rasa:command not found`

  I have googled and tried a number of solutions like creating a virtual environment by using **virtualenv**, but they didn't work. After installing and uninstalling many related support libraries, changing the `$PATH` Variable several hours later, I just installed rasa on my computer miraculously without knowing why :)

- I followed the instructions as the assignment described. In step 9 & 10, I got another error when I try `gactions update` and  `gactions test` , it keeps throwing errors like:

  ​	`Incorrect Usage: flag provided but not defined: -project help-test-3f213`

  Then I deleted `action.json` in the repo, and tried to use `gactions init` to generate `action.json` again. It worked and I finally got the output:

  ```
  	Gactions needs access to your Google account. Please copy & paste the URL below into a web browser and follow the instructions there. Then copy and paste the authorization code from the browser back here.
  Visit this URL:
  .......
  ```

- After I updating the action to Google successfully. I copied the test link from terminal and tried to test on Google Actions console. I got an error after I sending the first message in the Google simulator:

  `Sorry, Arrange an appointment isn't responding right now. Please try again soon.`

  So I read the tutorial [Going beyond ‘Hey Google’: building a Rasa-powered](https://blog.rasa.com/going-beyond-hey-google-building-a-rasa-powered-google-assistant/) again. I followed the **Step 5** instruction, and change the url in `action.json` (lines 32 & 37) to my local ngrok url `http://65683391.ngrok.io/webhooks/google_assistant/webhook`.

  And it finally works! 



## Step 2 Reflection & Remain Questions

- Rasa markdown syntax:

  ​	In `nlu.md`, I tried to include some numbers and alphabets combination(e.g. `9:00 p.m.`) inside some intents. However, rasa does not support the combination of different data types very well. I tried inputing `9:00 p.m.` in terminal, but rasa didn't recognize that and stop going to the next utterance. 

  I also tried using regular expressions to represent time and date like this:

  ```
  ## intent:inform_time
  - [create_time](time)
  
  ## regex:create_time
  - [0-9]{2}:[0-9]{2}
  ```

  But they do not work. So I only have a very limited time slots(9,10,13,15) and the same goes for date range(Monday-Friday, tomorrow). 

  The interesting thing is that Rasa sometimes has a strict case sensitive when analyzing input(e.g. Yoanda, yolanda) and sometimes doesn't.

  <img src="Screen Shot 2020-03-08 at 23.16.53.png" alt="Screen Shot 2020-03-08 at 23.16.53" style="zoom:50%;" />

  

  <img src="Screen Shot 2020-03-08 at 23.18.09.png" alt="Screen Shot 2020-03-08 at 23.18.09" style="zoom:50%;" />

