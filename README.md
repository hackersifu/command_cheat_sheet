# HackerSifu's Command Cheat Sheet
This is a collection of commands that I've found helpful, and a lot of times end up reusing (and trying to find them again in some of these cases as well). I'll continue to add to this list, and feel free to provide any suggestions or additions.

### Adding text to the end of each line in a file:
```
sed -e 's/$/<text to insert here>/' -i <filename>.txt
```

### Uncompressing tar files:
```
tar -xvf <filename>
```

### Adding text to the end of a file:
```
echo '<text to insert here>' >> <filename>
```

### Redirecting stdout to a file, as well as redirecting stderr to stdout:
```
<command> >out 2>&1
```

### One liner update command (Debian):
```
sudo apt-get update -y && sudo apt-get dist-upgrade -y
```

### Count directories/files within a directory:
```
tree -L 1 | tail 1
```

### grep simulator for AND operator
```
grep -E "item1.*item2" .
```

### (Athena SQL) Using if statement within a WHERE clause
```
# format:  if( condition, value_if_true, value_if_false)
WHERE if(<field_name> = '<field value>','true','false')
```

### (Athena SQL) Counting aggragated records
```
SELECT <field_name> , count(*) AS <count_field_name>
```

### (Athena SQL) Show partitions for a table
```
SHOW PARTITIONS <table>
```

### (Athena SQL) Skip the first line when creating a table for data
```
TBLPROPERTIES
(
 "skip.header.line.count"="1"
)
```

### Review open Linux ports
```
netstat -l
```

### Append text to end of file (quickly)
```
echo 'text' >> file
```

### Append text to beginning of file (quickly)
```
sed -i "1iTEXTHERE" file
```

### Quick Base64 Decode
```
# In bash:
echo <base 64 coded string here> | base64 -d
```

### Search for text within files (quickly)
```
grep -rnw . -e "<pattern>"
```

### Beginner screen commands
```
# Starting a screen:
screen -S my_screen_session_name
# List running screens:
screen -ls
# Return to running screen (if only one is running):
screen -r
# If multiple are running:
screen -r my_screen_session_name
```

### Run a detached screen command, for running commands in the background
```
screen -dmS <name> sh -c "<command>; exec bash"
```

### Search for text while ignoring case (quickly)
```
grep -i <texthere> *
```

### (Git) Git Setup Commands
```
# Configuring Git User
git config --global user.name <user>
# Clone a Git Repo
git clone <url>
```

### (Git) Start ssh-agent
```
eval "$(ssh-agent -s)"
```

### Perform a difference between two lists (Python)
```
final_list = (list(set(first_list) - set(second_list)))
```

### How to check out an existing branch into VSCode (Git)
```
git pull origin <new_branch>
git fetch origin <new_branch>
git checkout <new_branch>
```

### Check sudo version
```
sudo -V
```

### Search script.db for nmap scripts (shows type of script)
```
cat /usr/share/nmap/scripts/script.db
```

### Various awk commands
```
# Add line number to awk command
awk '{print NR,$0} file.txt
```

### Check to see if a directory exist, then create it if it doesn't (Bash)
```
if [ ! -f /home/user ]: then
  mkdir /home/user
fi
```

### (Python) Handy imports for starting a script
```
import logging
import os
import json
import boto3
import time
import datetime
from botocore.exceptions import ClientError


logger = logging.getLogger()
logger.setLevel(logging.INFO)
current_date = datetime.datetime.now()
current_date_string = str(current_date)
```

### (AWS CLI) Parse S3 and place into a file
```
aws s3 ls %s --recursive | tail -n +1 | head -1" % file_name
```

### (Git) How to checkout a remote branch
```
git pull
# List current branches after pull
git branch
# Switch to branch
git checkout new branch
```

### (Git) How to commit and push
```
# Commit and comment your code
git commit -m "comment here"
# Push your code
git push
```

### How to beautify large JSON files
```
cat <file_name> | python -m json.tool > <new_file_name>
```

### Output raw string from jq
```
jq --raw-output '.field,.sub_field'
```

### (VSCode) Mass Comment/Uncomment of lines in VSCode
```
Windows: Ctrl + /
Mac: Command + /
```

### (VSCode) Go to beginning of all lines
```
Mac: Ctrl + A (to select all lines), Shift + Alt + I (to put cursor at end of all lines), Home key (to go to beginning of each line)
```

### (argparse) How to use an option with no required argument
```
parser.add_argument('--fake-option', action='store_true')
select = parser.parse_args()
if select.fake-option:
    dostuff()
```

### (Bash) Create virtual environment for running Python
```
virtualenv --python=python3 venv
source venv/bin/activate
```

### (Bash) Starting an Apache2 server
```
sudo apt update
sudo apt install apache2 -y
service apache2 start
```

### (Python) Iterate cleanly on JSON Keys that may or may not exist
```
if 'JSONKey' in json:
    variable = json['JSONKey']
    print(variable)
```

### (Ruby) Create vulnerable SSRF server for testing 
* Credit to HackerOne: https://www.hackerone.com/blog-How-To-Server-Side-Request-Forgery-SSRF
```
# Create a Ruby file for running a vulnerable server
vim vuln-server.rb
# Add the following content to the file:
require 'sinatra'
require 'open-uri'

set :bind, '0.0.0.0'
set :port, 80

get '/' do
  format 'RESPONSE: %s', open(params[:url]).read
end
# Install Sinatra using Ruby
gem install sinatra
# Run the server in the background
ruby vuln-server.rb
```

### (Python) Advanced setup of logging module
```
# Code to print out info within the terminal
logFormatter = '%(asctime)s - %(levelname)s - %(message)s'
logging.basicConfig(format=logFormatter, level=logging.INFO)

# Code to set the logger up
logger = logging.getLogger()
logger.setLevel(logging.INFO)

# Code to set up the logging file locally for review
output_handle = logging.FileHandler('loggertest.log')
output_handle.setLevel(logging.INFO)
logger.addHandler(output_handle)

# Code to set up the logging format for logs within the logging file
formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
output_handle.setFormatter(formatter)

# Code for the handler needed for inputting the logs into the logging file
logger.addHandler(output_handle)
logger.info("Logs are contained in loggertest.log")
```

### (Python) Add timestamp function to replace print
```
original_print = print

def timestamp(*args, **kwargs):
    original_print(datetime.datetime.now(), *args, **kwargs)
print = timestamp
```
