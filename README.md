## UNDER PROGRESS

# Taken
Takeover AWS ips and have a working POC for Subdomain Takeover.

## Pre-requisites
- AWS Account
(API keys and few instances running)
- A separate linux server for running the takeover script in "screen" session. So it runs 24*7. 

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
1) Create one instance t2.medium (attack machine), free 24*365.
2) Create 5-10 instances (higher the no. better chances but more the charges) in one or more region, takes 5min.s, have SG Group opened to only your public ip.
3) Create AWS API keys to stop/start instances
4) SSH to your attack machine.
5) Set up email notification utility using SSMTP utility.
6) Set up subfinder and sublist3r.py tools for collecting subdomains. 
7) Clone this repo and Open a screen session. export AWS credentials.
8) Run the fetch subdomain script which uses subfinder and sublist3r.py, You can add more tools to it. This shall generate a list of all the subdomains for
one or more domains in the format "subdomain:IP" in each line. 
9) Run the takeover script in a screen session in multiple session for each region. 
Reasoning - Each Region in AWS has associated different IP subnets. To target companies sitting in 
US, there are high chances they are running in any of US regions, but may also have assets in other regions like Ireland, Frankfurt etc. So instead of running 
10 assets in one region, try running 5 assets in the region company is based and other 5 in different regions. 

## Installation
`export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
   # The access key for your AWS account.` <br/>
`export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   # The secret access key for your AWS account.`<br/> 
   
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
