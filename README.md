## UNDER PROGRESS

# Taken
Takeover AWS ips and have a working POC for Subdomain Takeover.

## Pre-requisites
- AWS Account
- Knowledge of Linux and Bash script

## Tech/framework used
<b>Built with</b>
- `Bash`

## Features
- Gather subdomains.
- Rotate IPs by restarting ec2 instance until it matches one of the ips in the list. 
- On a match that IP/host is added in a whitelist file, so it doesn't gets rotated again and send an email notification.

## How to use?
- Set up one instance on AWS which would run this script on a screen session.
- Set up few more instances with instance type a3.nano (cheapeast if i'm correct) in one or more region.
- Run the takeover script in a screen session and wait for email notification.

## Detailed step 
1) Create one instance t2.medium (attack machine), free of cost 24*365.
2) Create 5-10 instances (higher the no. better chances but more the charges around $50/month for 10 machines) in one or more region, takes 5min.s, have SG Group opened to only your public ip.
3) Create AWS API keys to stop/start instances.
4) SSH to your attack machine.
5) Install email notification utility SSMTP.
6) Install subfinder and sublist3r.py tools for collecting subdomains. (Or any other tools you want but that would require you adding it in the script) 
7) Clone this repo, CD into the directory and open a screen session. export AWS credentials in that session.
8) Run the fetch subdomain script which uses subfinder and sublist3r.py, You can add more tools to it. This shall generate a list of all the subdomains for
one or more domains in the format "subdomain:IP" in each line. 
9) Run the takeover script in a screen session in multiple session for each region. <br/>
`Reasoning` - Each Region in AWS has associated different IP subnets. To target companies sitting in 
US, there are high chances they are running in any of US regions, but may also have assets in other regions like Ireland, Frankfurt etc. So instead of running 
10 assets in one region, try running 5 assets in the region company HQ is based and other 5 in different regions.

Screen session example- 
![alt text](https://user-images.githubusercontent.com/18059590/95270320-22a95400-07f0-11eb-8010-0b628037b2c3.png)
<br/><br/>
Email Notification - 
![alt text](https://user-images.githubusercontent.com/18059590/95270397-42407c80-07f0-11eb-9e48-e5967f890ef0.png)

`Took over a subdomain what next` - 
SSH into that host, create a simple HTML file and start a python server and you have a running POC.
(I plan on automating this as well in next release)

## Installation
`export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
   The access key for your AWS account.` <br/>
`export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   The secret access key for your AWS account.`<br/> 
   
## Reference



## Contribute
- Report bugs.
- Suggestions for improvement.
- Suggestions for future extensions.

## Future Extensions
- Creating ec2 instances using the same script.
- Adding auto deploy of http service using AWS beanstalk.

## License
GNUV3 © [In3tinct]

Twitter - https://twitter.com/_In3tinct
