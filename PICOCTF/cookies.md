# COOKIES
Who doesn't love cookies? Try to figure out the best one. http://mercury.picoctf.net:27177/.

## My Solve:
1) SO basically, as the name Cookie suggests i started by opening the developer tools in my browser to inspect the website's data.
2) Navigated to the Application tab within the developer tools to look at the cookies stored for the site.
3) Noticed a key cookie whose numerical value seemed to control the page content. The challenge's initial hint, "snickerdoodle," changed this value from -1 to 0.
4) Decided to manually edit the cookie value to test my hypothesis. I changed it to 1 and refreshed the page, which resulted in a different cookie type ("chocolate chip") being displayed.
5) This confirmed the vulnerability: by changing the cookie's numerical value, I could change the content the server delivered.
6) My goal became finding the specific numerical value that would trigger the display of the flag.
7) Now by various hit and trial values, found the correct value was 18, This got me the flag.

*Flag:* picoCTF{3v3ry1_l0v3s_c00k135_064663be}

## Concepts learnt
Dealing with and manipulating cookies.

## Notes:
Always accdept cookies when a website asks you to!
