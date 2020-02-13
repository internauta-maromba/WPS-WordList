# WPS-WordList
Python Script to make a WPS Pin Wordlist

Some routers use default WPA password as the number of the WPS PIN, and some users just let the default password. Using this script you can make a wordlist to use in aircrack-ng.


#---Python2
'''
Have problems to pins that start with zero, so crunch this way "crunch 7 7 123456789 -o crunch-7-7.txt -d 3% -t @%%%%%%"

And this crunch output is large, some machines can freezy, in this case "split crunch-7-7.txt -n l/2 -d crunch" can be used

To get something close to bully random, use "sort input.txt -R -o output.txt"
'''
#---input 7num wordlist
with open("crunch01") as f:
    content = f.read().splitlines()
    Lista = content
#---input 7num wordlist

NovaLista = []

for i in range (0, len(Lista)) :
    n = int(i)
    pin = int(Lista[n])

#---checksum log
    class WPS(object):

        def algoritimo(self, pin):

            num = 0

            while pin:
                num += (3 * (pin % 10))
                pin = int(pin / 10)
                num += (pin % 10)
                pin = int(pin / 10)

            return ((10 - num % 10) % 10)
    checksum = WPS().algoritimo(pin)
#---chechsum log

    i = i + 1
    NovaLista.append(str(pin) + str(checksum))

#---output wordlist

with open('wps2.txt', 'w') as f:
    for item in NovaLista:
        print >> f, item

#---output wordlist

