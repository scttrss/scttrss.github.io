---
layout: post
title:  "Netscaler and Websockets"
date:   2020-09-01 06:00:00 -0800
categories: jekyll update netscaler
---
We use the Netscaler MPX ADC, and had a need to load balance web servers that support wss on port 5650.

Netscaler does support SSL offload of WSS on LB VIPs (not CS VIPs).

Enabling that support is as simple as binding an HTTP profile to the VIP that includes the option "Enable WebSocket connection"

The easiest way to do that without breaking anything is to:

1. Login to your Netscaler ADC, navigate to System / Profiles / HTTP Profiles

2. Click the existing HTTP profile you use (or would use), and then click Add.  Doing it this way copies the settings from the existing profile

![Jira query](/assets/20200901-netscaler-websocket-1.PNG)

3. Give the new profile a descriptive name and at the bottom enable WebSocket connections

![Jira query](/assets/20200901-netscaler-websocket-2.PNG)

4. Save your profile and either go back to the LB VIP or create a new one.

5. Under Profiles, select the HTTP Profile you just created

![Jira query](/assets/20200901-netscaler-websocket-3.PNG)
