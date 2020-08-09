# HackerSifu's Command Cheat Sheet
Collection of commands that are helpful for pen testing and other command line activities.

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