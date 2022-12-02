# The UX of MCS Turtle Tracker
https://turtletracker.mcsynergy.nl
## Why have I researched UX?
It's really important that the usability of the site is most optimal for the users, when the site is slow, unclear or completely broken users will quickly leave the site. To make sure that the users are staying on the site and know what every aspect does, I've conducted a UX Survey with some questions about the UI of the site. I've also heard over the development of my site that test users had some issues with some UI elements but I've never really documented theses issues, this survey is also for them to clarify what they think that can be improved.

## Who were my test subjects?
I've performed this test with two different test groups, the MCS Players and a group of friends who are all studying ICT. Why have I chosen to conduct this survey with my friends? Well I wanted to see how users, who have noting to do with the application, see the application. Because they have no clue what the site is about, they might see different things that need to be fixed. Also most of the MCS team has seen my application before and therefore might be a little bit bias because they already know that some things exist.

## What have I tested
As said earlier, I've conducted an online survey. In this survey I firstly if the contestant is an active MCS player and if they have ever played with the ComputerCraft mod, I ask this to seperate the answers between test groups and see the difference. Then I proceed to ask that every contestant opens my application and starts looking around for a few minutes and try to find every page and functionality.

When they are done with that, they proceed to the actual UX questions. I asked them what their general opinion was about the website, if they found anything unclear and what things they would like to see changed or added.

I then proceed to ask some specific questions about certain components.

### Return to first log page
![Logs](https://lh4.googleusercontent.com/FXpNpodQ7JI6IsuiQYSTpuDYBtRAiwLPeWqIPmh9kueOUFINOzs5JpGD2itvnbGbf1sEFRyz-NUcAR-i7aNDYjaaoEQslLKIzGXgJa_8FiKQf1OtN275c7wXqqKFg9geHhtQj-wiFmiWf6RDdjymSjbWcb4_SMnnnCFkusb3QubEH4OSxnWhp0O3rzjtcHrz3uTu)

When the user clicked on "Logs", it would return the log page to the first page. I found this feature very usefull because there can be over 200 pages but I didn't know if it was obvious that the feature was there so I asked if the contestants noticed and if they didn't, how I could maybe clarify it.

### Return to portal or previous page
![Logo button](https://lh4.googleusercontent.com/FjAXWtGohu1WcoIyUYCOltcjAVtkH4_76rt8qrxwz9h-IdR0xSdEL55SYRIwV29ZDNlXbmPSOmeYH5UY-tnC28PUnQYefS24mzm9KCMaq8oH_5hl8q2IqUrKPW57ozBhBi02cpIOGDHtdT42E8HHe6welRf4L-F9tGl-immhtnRm3bU6BO0GP3pDcJH7ec2Ne0E-)

The second compontent was the "Logo" button, I have programmed that clicking on the logo would return you to the portal or the previous page. I found it very helpfull but I thought that is might not be obvious and that the switching between functionality would confuse users. That's why I asked the same questions about this component.

### Go to computer detail page
![Clickable computers](https://lh4.googleusercontent.com/nh5q7N7O5S2aipvHJu-_RUQ5l-cEN1421GLhFYIFAHZb0Vmu7ufEKQ8gd0Yu2h6qu-VFera-bc0D1GenaB0uwg9IwAdJL0hNrtaYveSVaYL1Pvg96xOqwLu2-B2WKq5ola6qdxTb6PjdLKUSZVp_e7tsn9iXgB1ZLJnZ3IO7LjK6yE7Vz8sXpcQqBfP8kEmrLeB5)

The last component I tested was the ability to click on the computers to go to a detail page. I didn't think anyone would be confused bu this because I found it pretty obvious, however I wanted to make sure that that was actually true.

If the contestant selected that they found out that the feature existed, they would be given more questions about their general opinion about the detail page and if they found any thing unclear or they wanted to see things added/changed.
## What are the results?
The results were very usefull for me, I really got an idea on what is wrong/unclear about my application and I've even received some ideas on how to fix it.

### Too cluttered
The main feedback that I received from both groups was that the site felt too cluttered and overwhelming, there was too much information on the home page and it was too much text to read. They found that they didn't know where to look and that they couldn't find the specific thing they were looking for. This will only get worse when more systems and computers are being added to MCST.

This is going to be a pretty big change so I'm going to reduce the amount of text and simplify some text components to a more visual component, I'm also going to work with things like tooltips so that you won't see all the information all the time but that you can get more details (like seeing the id) when you hover over things.

The second big solution that I received was the ability to collapse systems, that way you can easily select what systems you want to see and hide all the ones that are not relevant for the user.

### "Logs" button
![Pie chart log button](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/piechartlogsbutton.png)

I think the pie chart speaks for itself, non of the contestants realized that you could click on "Logs" to return to the first page. So this needs to be changed.

The most easy solution for this is to add a << button next to the < button, this is something that most sites do and is familiar for everyone.

### "Logo" button
![Pie chart logo button](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/piechartlogobutton.png)

This one surprised me more, every contestant found out that the logo was clickable. I have now realized that this is something that alot of websites do so I shouldn't be surprised that people click on the logo. However they didn't like that the behaviour changed depending on what page you are, some contestants were searching for a simple "back" button but they couldn't find it and were confused when the logo acted as a "back" button.

What I will probably be doing is moving the logo to the middle and make it solely act as a "home" button, so clicking it will always result ending up on the home page. To also have a "back" and "back to portal" button, I will place a seperate button for this on the location where the logo now is.

### Clickable computer
![Pie chart clickable computer](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/piechartclickablecomputer.png)

Everyone but one of the contestants found out that you could click on the computers, the main reason for this is probably because the color will change then hovering over a computer. Furthermore the functionality was pretty clear for everyone so I won't be changing anything about this component.

### Computer Detail Page

There weren't any major UX problems with this page, only some minor UI things like that when the system was 0, it would show "System 0 - " and "producing: ". This is because that information doesn't exist and I should place a check in place so that it doesn't show it when there is no information.

They also found that the dynmap (live map of the minecraft world) was a little bit too much in the center, so I sould maybe place it somewhere in a corner or only show it when the user wants to.

I do need to better specify what the functionality is of some components, like is the dynmap for the precise location of the turtle or for the general area? and are the logs the ones sent by just this computer?

### MCS Players vs Non MCS Players
There was a significant difference in feedback between players and non players. You could see that the non players had no idea what the site was about and they were more easily overwelmed by all the information. They were also asking questions like, what does "junk" logs mean and what does the red text mean, the MCS players did know what these things mean. Because this app is only for players, I won't be changing those things.

There were also some things that non players would like changed, but most of these things were just technically not possible or were outside the scope of my application. The players knew that this was the case and therefore didn't request it.

But because non players weren't looking at the information itself as much, they were looking more at the styling of the website. They found that on mobile some UI elements need more margins or borders.

## Conclusion
The home page is too cluttered and there is too much text and information to read, I need to simplify most of the elements. The "return to log page 0" button was not clear, nobody found out that this was a feature so I will be changing it to a << button. Everyone found out that the logo was clickable but they were confused about its functionality, it would behave differently on different pages. I need to make a seperate "back" and "back to portal" button. The clickable computer part was pretty obvious for almost everyone. The computer page was also fine for the most part, there were some minor UI changes requested and the dynmap needs to change a little bit.

I will be changing these things and when I have done so, I will ask them again for their feedback to see if the problems are resolved.
