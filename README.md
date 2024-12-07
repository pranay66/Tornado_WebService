# Tornado_WebService

# Project Outline
A new type of malware, known as 'Tornado', has been found through a connected portal. Though it has some security measures, there’s still a test to see if those protections are capable of protecting.

The idea is to see if it can be worked around those defenses. Will the challenge work or will the security hold.

# Software and Tools
Kali Linux

Burpsuite

Html

Json

Curl

# Process
Enumerate available endpoints and Get and Post requests on burpsuite:

/get_tornados

/update_tornado

/login

/stats

/report_tornado

# Tools used for testing
curl

Burp Suite

# The Plan to Explotting the vulnerability.
First, you should locate flaws inside the system. This is how someone can get unauthorized entry or control over your system.

Among the many important vulnerabilities to search for, Cross-Site Request Forgery (CSRF) is one of them. The flaw tricks the bot into running evil JavaScript on your page. This way, without the bot’s knowledge, it uses the bot’s already authenticated session to act.

Then you inject malicious higher level of data into the system like a user credentials (kittykat) that is fake. This is a manipulation to let you break through the security measures put in place or to manipulate whatever is in there in unintended manners.

Then inject the data and login, use exploit to get at stuff like the /stats endpoint, which would otherwise be off limits.

# creating and hosting script payload.

To start, you will have to create a malicious JavaScript payload that you will refer to an index.html file that pulls the data from the /get_tornados endpoint.

Following this, you’ll use the injected credentials to update machine details by posting them to the /update_tornado endpoint.

After that payload is ready, you can host it on local server or if you have an NGROK subscription then you can either use your local server to allow this payload to run or you can use one of the NGROK’s public server.

# Steps for Server Exploitation and Flag Retrieval

1. Make sure to update the IP address and port numbers to match your machine's settings.
2. Use the following command to get the current status of the machine:
   curl -X GET "http://94.237.63.109:45919/stats" -b cookie.txt
3. To start the server, run this command to host the index.html file on your local machine:
   python -m http.server 1337
4. Use this command to report a tornado on the Box server:
   curl "http://94.237.59.207:47563/report_tornado?ip=127.0.0.1"
5. Inject a new user to the server by logging in with the following credentials. The server will return a cookie, which you’ll need to store:
   curl -X POST "http://94.237.59.207:47563/login" \
     -H "Content-Type: application/json" \
     -d '{"username": "kittykat", "password": "kittykat"}' \
     -c cookie.txt
6. After logging in, use this command to access the protected stats page, which will provide the cookie data:
    curl -X GET "http://94.237.59.207:47563/stats" -b cookie.txt
7. Finally use the retrived flag txt for submission at HACk the boX.




