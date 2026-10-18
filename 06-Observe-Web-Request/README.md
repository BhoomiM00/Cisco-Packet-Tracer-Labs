# Packet Tracer – Observe Web Request

## Aim
To observe the client-server communication that occurs when a PC requests a webpage from a web server using HTTP.

## Objectives
- Verify connectivity to a web server using the `ping` command.
- Access a website using a web browser.
- Examine the HTML code stored on the web server.
- Observe TCP and HTTP traffic in Simulation Mode.
- Understand the sequence of packets exchanged between a client and a server.

## Tools Used
- Cisco Packet Tracer
- External Client PC
- Web server (`ciscolearn.web.com`)
- Command Prompt
- Web Browser
- Simulation Mode and Complex PDU tool

## Background
When a user opens a website, the client communicates with a web server to request webpage content.

DNS (Domain Name System) translates a domain name into an IP address. The client then uses the server's IP address to communicate across the network.

HTTP (Hypertext Transfer Protocol) is used to request and transfer webpage content. HTTP typically operates over TCP, which establishes a connection and provides reliable data delivery.

HTML (Hypertext Markup Language) defines the structure and content displayed by a web browser.

## Procedure

### Part 1: Verify Connectivity to the Web Server

1. Open the **External Client**.
2. Select **Desktop → Command Prompt**.
3. Enter the following command:

   ```text
   ping ciscolearn.web.com
   ```

4. Observe the IP address shown in the ping output.
5. Check whether the server responds to the ping requests.

The domain name is resolved to an IP address using DNS before the client sends the ping requests.

**Screenshot:** `images/01-ping-web-server.png`

### Part 2: Connect to the Web Server

1. Open the External Client's **Desktop → Web Browser**.
2. Enter `ciscolearn.web.com` in the URL field.
3. Press Enter to load the webpage.
4. Read the webpage displayed in the browser.

**Screenshot:** `images/02-webpage-on-client.png`

### Part 3: View the HTML Code

1. Select the `ciscolearn.web.com` server in the network topology.
2. Open the **Services** tab.
3. Select **HTTP**.
4. Locate `index.html` and click **Edit**.
5. Examine the HTML markup.
6. Compare the code with the webpage displayed on the External Client.

The web server stores the HTML content, and the browser interprets this markup to display the webpage.

**Screenshot:** `images/03-server-html-code.png`

### Part 4: Observe Traffic Between the Client and Web Server

1. Switch Packet Tracer to **Simulation Mode**.
2. Open the Simulation Panel.
3. Select **Edit Filters**.
4. Under the **Misc** tab, ensure that only TCP and HTTP are selected, as instructed by the activity.
5. Select the **Add Complex PDU** tool.
6. Click the External Client to set it as the source.
7. In the Complex PDU window, set the application to **HTTP**.
8. Click the `ciscolearn.web.com` server to set it as the destination.
9. Set the Starting Source Port to `1000`.
10. Set the simulation interval to **Periodic** and enter `120` seconds.
11. Click **Create PDU**.
12. Click **Play** in the Simulation Panel to observe the traffic.
13. If the Buffer Full window appears, select **View Previous Events**.
14. Examine the Event List and observe the packets travelling between the client and server.

**Screenshots:**
- `images/04-simulation-panel.png`
- `images/05-complex-pdu-settings.png`
- `images/06-http-traffic-events.png`

## Observations

- The `ping` command tests IP connectivity to the web server.
- DNS resolves the domain name to an IP address.
- The web browser requests webpage content from the server.
- The server's `index.html` file contains the markup used to generate the webpage.
- HTTP traffic is carried over TCP in this activity.
- TCP connection establishment, data transfer, and acknowledgements generate multiple network events.
- Simulation Mode allows individual events and packet details to be examined.

## Result
The client-server web request process was studied in Cisco Packet Tracer. Connectivity was tested using `ping`, the webpage and its HTML source were examined, and TCP/HTTP traffic was observed in Simulation Mode.

## Key Learnings
- DNS translates domain names into IP addresses.
- A web browser requests content from a web server.
- HTML defines the structure of a webpage.
- HTTP is an application-layer protocol that commonly uses TCP for reliable communication.
- Simulation Mode helps visualize packet movement and protocol interactions.

## Conclusion
This activity demonstrates how a client accesses a website and how network protocols support web communication. It also provides practical experience in examining DNS resolution, HTML content, and TCP/HTTP traffic using Cisco Packet Tracer.
