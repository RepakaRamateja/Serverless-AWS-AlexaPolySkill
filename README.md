# Alexapolyskill

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/overview.png)




Architecture:

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/Architecure.png)


Amazon s3 contains all the html files and converted audio files

Api gateway invokes lambda functions basing on user request type 

for instance 

    get  request invokes get post lambda function
    post request invokes New Post lambda function etc.


Each lambda function has a unique responsibility.

get post lambda function retrives all the posts from dynamo db and audio files from s3

New post lambda function inserts posts into dynamo db and inserts a message into SNS topic which inturn triggers another lambda function
(Convert to Audio) which uses text from dynamo db and converts it into mp3 and store it in s3 service.

Amazon poly is aws service which converts text to Audio.

Amazon SNS(simple notification service) is asynchronous service which invokes convert to audio lambda function when message is arrived.

Amazon Dynamodb is amazon nosql db service which is used for storing  and retriving of the posts.




Overview:

Converts text to audio mp3 files using Amazon Poly service

Alexa skill created uses generated audio files by Poly.




Features:

  First user need to enter input text and then select voice from the list.

  Then click on button Say it

  Now in the background processing happens and then mp3 files are generated.

  To retrive the files type * in the text box and then click on search button.

  It retrives all the mp3 files that are converted and stored in S3 bucket.


![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/files.png)


  Now user can download all the files.

  Last but not least build  amazon alexa skill which uses the audio files present in s3 bucket. 

  

  




