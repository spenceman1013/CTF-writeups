#*RAirways*

###200 Points

####*Problem*
Agent. We found a target posting strange images of boarding passes to his Instagram. None of the guys at base can figure it out, but we think he's been using the images to exfiltrate data. We've attached a high-quality version of the image below, here's the one from his Instagram: 

![alt text](files/RAirways.jpg "Airline Ticket")


####*Solution*
I didn't see anything immediatley obvious in the picture. My first guess was their might be something hidden in the barcode. After some quick research I found that the type of barcode that this boarding pass had was PDF417 Barcode. I found a barcode scanner app and scanned the barcode and it contained the following:
>M1TECHY/BEN           EDED833FZRHSFORA A67D 069F035A0007 100
>ractf{B0ard1ngP4ssD4t4}

There is our flag: *ractf{B0ard1ngP4ssD4t4}*
