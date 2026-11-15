# EX01 Developing a Simple Webserver
## Date:15/11/2026
## Regn0:26018783

## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:
~~~
from http.server import HTTPServer, BaseHTTPRequestHandler
content = """
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Network Protocols</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    min-height: 100vh;
    background: linear-gradient(120deg, #d9eaff, #fce4ec);
    padding: 50px 5%;
}

.container {
    max-width: 1250px;
    margin: auto;
}

h1 {
    text-align: center;
    color: #7136c9;
    margin-bottom: 30px;
    font-size: 32px;
}

.search-box {
    display: block;
    width: 100%;
    max-width: 450px;
    padding: 14px;
    margin: 0 auto 25px;
    border: 2px solid #8b45e8;
    border-radius: 25px;
    outline: none;
    font-size: 16px;
}

.table-container {
    overflow-x: auto;
    background: white;
    border-radius: 12px;
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

table {
    width: 100%;
    border-collapse: collapse;
    text-align: center;
}

th {
    background: linear-gradient(90deg, #7834e8, #923ce0);
    color: white;
    padding: 17px;
    font-size: 17px;
}

td {
    padding: 15px;
    border-bottom: 1px solid #ddd;
    font-size: 16px;
}

tbody tr:nth-child(odd) {
    background: #eeeaff;
}

tbody tr:nth-child(even) {
    background: #fff2f7;
}

tbody tr:hover {
    background: #d9c8ff;
    transition: 0.3s;
    cursor: pointer;
}

footer {
    text-align: center;
    margin-top: 25px;
    color: #555;
}

@media(max-width: 600px) {
    body {
        padding: 30px 12px;
    }

    h1 {
        font-size: 23px;
    }

    th, td {
        padding: 12px;
        font-size: 13px;
        white-space: nowrap;
    }
}
</style>
</head>

<body>

<div class="container">

    <h1>🌐 List of Network Protocols</h1>

    <input
        type="text"
        id="search"
        class="search-box"
        placeholder="🔍 Search Network Protocol..."
        onkeyup="searchProtocol()"
    >

    <div class="table-container">
        <table id="protocolTable">

            <thead>
                <tr>
                    <th>S.No</th>
                    <th>Protocol</th>
                    <th>Full Form</th>
                    <th>Purpose</th>
                </tr>
            </thead>

            <tbody>
                <tr><td>1</td><td>HTTP</td><td>Hypertext Transfer Protocol</td><td>Transfers web pages</td></tr>
                <tr><td>2</td><td>HTTPS</td><td>Hypertext Transfer Protocol Secure</td><td>Secure web communication</td></tr>
                <tr><td>3</td><td>FTP</td><td>File Transfer Protocol</td><td>Transfers files</td></tr>
                <tr><td>4</td><td>TCP</td><td>Transmission Control Protocol</td><td>Reliable data transmission</td></tr>
                <tr><td>5</td><td>IP</td><td>Internet Protocol</td><td>Routes data packets</td></tr>
                <tr><td>6</td><td>DNS</td><td>Domain Name System</td><td>Finds IP addresses</td></tr>
                <tr><td>7</td><td>SMTP</td><td>Simple Mail Transfer Protocol</td><td>Sends emails</td></tr>
                <tr><td>8</td><td>SSH</td><td>Secure Shell</td><td>Secure remote access</td></tr>
                <tr><td>9</td><td>UDP</td><td>User Datagram Protocol</td><td>Fast data transmission</td></tr>
                <tr><td>10</td><td>DHCP</td><td>Dynamic Host Configuration Protocol</td><td>Assigns IP addresses</td></tr>
                <tr><td>11</td><td>POP3</td><td>Post Office Protocol Version 3</td><td>Retrieves emails</td></tr>
                <tr><td>12</td><td>IMAP</td><td>Internet Message Access Protocol</td><td>Manages emails</td></tr>
            </tbody>

        </table>
    </div>

    <footer>
        © 2026 Network Protocols | Designed with HTML & CSS
    </footer>

</div>

<script>
function searchProtocol() {
    let input = document.getElementById("search").value.toLowerCase();
    let rows = document.querySelectorAll("#protocolTable tbody tr");

    rows.forEach(row => {
        let text = row.innerText.toLowerCase();
        row.style.display = text.includes(input) ? "" : "none";
    });
}
</script>

</body>
</html>
"""
class myhandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())
server_address = ('',80)
httpd = HTTPServer(server_address,myhandler)
print("my webserver is running...")
httpd.serve_forever()
~~~



## OUTPUT:
![alt text](<Screenshot (16).png>)


## RESULT:
The program for implementing simple webserver is executed successfully.

