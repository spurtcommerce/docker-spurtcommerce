<h2>Overview</h2>
This is the official repository of Spurtcommerce. Using these Docker Images, you can easily deploy Spurtcommerce Multi-Vendor Marketplace in your local server.
<h2>Start Spurtcommerce with Docker Compose</h2>
By following these two simple commands, you can quickly launch Spurtcommerce in your local server. 
<br>

If you have not yet installed Docker in your local server, then follow this first step. <br><br>

<code> $ sudo snap install docker </code><br>

<br>

Having already built the Docker images you can run docker compose without the --build flag.

<br>
<code> $ sudo docker compose up </code>
<br>


<h2> Spurtcommerce port </h2>
Your local Spurtcommerce setup is now running with each of the services occupying the following ports:
<br><table>
<thead>
<tr>
<th align="center">Parameter</th>
<th>Function</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><code>-p 8080</code></td>
<td>The port for the spurtcommerce api</td>
</tr>
<tr>
<td align="center"><code>-p 400</code></td>
<td>The port for the spurtcommerce Ui</td>
</tr>


</tbody>
</table>

Then SpurtCommerce Is Ready On localhost:{your-port} or default localhost/(hostname)


<h2>Avilable Images</h2><br>

Spurtcommerce maintains multiple build images for testing new development as well as supporting legacy builds. Each image uses a different version of Ubuntu Linux, with a slightly different list of included language and software versions.
<br>The following image is currently available:
<br><br>


* <b> Marketplace API:</b> [https://hub.docker.com/repository/docker/spurtcommerce/marketplace-api/general](https://hub.docker.com/r/spurtcommerce/marketplace-api)

* <b> Web UI:</b> [https://hub.docker.com/r/spurtcommerce/web-ui](https://hub.docker.com/r/spurtcommerce/web-ui)

* <b> Database:</b> [https://hub.docker.com/r/spurtcommerce/database](https://hub.docker.com/r/spurtcommerce/database)


<br>

Should you require any premium support, feel free to write to support@spurtcommerce.com. 


