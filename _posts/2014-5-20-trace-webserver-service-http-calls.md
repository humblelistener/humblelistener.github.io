---
layout: post
title: "Profile http requests made by webserver"
date: 2014-05-20
categories:
  - programming
description:
image: https://source.unsplash.com/collection/599894/800x600
image-sm: https://source.unsplash.com/collection/599894/1600x900
---

Tracing http requests made from server


Once in a while, we need to trace the http calls made from the web/app
server. It will be very useful especially in scenarios where you are
having performance problems with web services and not sure where to look
for. We all know fiddler is very useful in tracking the http calls from
the browser, but, put in right configuration this tool will be handy in
tracking web service calls as well. I am going to briefly write some of
the configurations that may have to be done for getting this working.
(consider its more of a personal reference document)

1. Run your fiddler under the context of app pool user.
2. Recycle the app pool
3. The above steps did not solve your problem, under system.net element in your
web.config,
insert the following    

  ```
  <defaultProxy>
    <proxy autoDetect="true" proxyaddress="http://127.0.0.1:8888"/>        
  </defaultProxy>
  ```

4. If all this did not solve, ensure that fiddler is point to port 8888
(which is does by default)
5. sometimes fiddler though captures https
handshakes, it may not be able to decrypt the actual http requests In
such cases

  ``goto fiddler options -&gt; Https tab, ensure "Decrypt Https
traffic"``  is checked.

[Telerik fiddler documentation](http://docs.telerik.com/fiddler/configure-fiddler/tasks/decrypthttps/)
