# "Open address" for an EC2 instance opens with HTTPS, even if it's not supported

While working through freeCodeCamp.org's [AWS Basics for Beginners](https://www.youtube.com/watch?v=ulprqHHWlng&t=5268s) course, I was unable to view our simple `index.html` file on my EC2 instance.

Initially, I thought my [instance may be in a private subnet](https://stackoverflow.com/questions/26706683/ec2-t2-micro-instance-has-no-public-dns) or that my Security Group may have been set up incorrectly.

As it turns out, clicking "open address" under "Public IPv4 address" will open the address with `https://` even if your instance does not support HTTPS.

To use `http://`, copy and paste the IP address into your browser instead.
