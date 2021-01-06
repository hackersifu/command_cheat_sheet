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

### Adding text to the end of a file name:
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

### Run a detached screen command, for running commands in the background
```
screen -dmS <name> sh -c "<command>; exec bash"
```
