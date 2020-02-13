# WPS-WordList
Python Script to make a WPS Pin Wordlist

Some routers use default WPA password as the number of the WPS PIN, and some users just let the default password. Using this script you can make a wordlist to use in aircrack-ng.

The ideia in this project is: 

1 - Make a wordlist with crunch without starts with zero -> "crunch 7 7 123456789 -o crunch-7-7.txt -d 3% -t @%%%%%%"

2 - Split crunch-7-7.txt to not freezy the machine -> "split crunch-7-7.txt -n l/2 -d crunch"

3 - Run WPS-script.py in crunch00 and crunch01 to output wps1.txt and wps2.txt"

4 - Opitionaly you can randomize like Bully does -> "sort wps1.txt -R -o wps-rand.txt"

5 - Finaly glue everything -> "cat wps-rand.txt wps-rand2 > wps-wordlist.txt"
