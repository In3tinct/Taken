# Tekken
Takeover AWS ips and have a working POC for Subdomain Takeover.

## Pre-requisites
- AWS Account
(API keys and few instances running)

## Tech/framework used
<b>Built with</b>
- `Bash`

## Features
- Gather subdomains.
- Rotate IPs by restarting ec2 instance until it matches one of the ips in the list. 
- On a match that IP/host is added in a whitelist file, so it doesn't gets rotated again and send an email notification.

## How to use?
Set up one instance on AWS which would run this script.
Set up few more instances with instance type (a3.nano cheapeast in one or more region).
Run the script in a screen session.

## Detailed step 
- Run the fetch subdomain script which uses subfinder and sublist3r.py, You can add more tools to it. This shall generate a list of all the subdomains for
one or more domains in the format "subdomain:IP" in each line. 
- Run the takeover script in a screen session in multiple session for each region. Each Region in AWS has associated different IP subnets. To target companies sitting in 
US, there are high chances they are running in any of US regions, but may also have assets in other regions like Ireland, Frankfurt etc.

## Installation
`export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
   # The access key for your AWS account.` <br/>
`export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   # The secret access key for your AWS account.`<br/> 


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
