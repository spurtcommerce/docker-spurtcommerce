<h2>Overview</h2>
This is the official repository of Spurtcommerce. Using these Docker Images, you can easily deploy Spurtcommerce Multi-Vendor Marketplace in your local server.
<h2>Start Spurtcommerce with Docker Compose</h2>
By following these two simple commands, you can quickly launch Spurtcommerce in your local server. 
<br>

Additionally, you should have <code> docker </code> and <code> docker-compose </code> installed on your system.

If you have not yet installed Docker in your local server, then follow this first step. <br><br>

<pre><code>sudo snap install docker</code></pre>
  
<h3>Step 1 :  </h3>

<pre><code>
git clone https://github.com/spurtcommerce/docker-spurtcommerce.git && cd docker-spurtcommerce
</code></pre>

Having already built the Docker images you can run docker compose command

<h3>Step 2 : </h3>
<pre><code>
docker compose up
</code></pre>
<p>If the above command gives an error, try running it with <code>sudo</code>:</p>
<pre><code>
sudo docker compose up
</code></pre>


<h2> Spurtcommerce port </h2>
Your local Spurtcommerce setup is now running with each of the services occupying the following ports:
<br><br>

<table>
<thead>
<tr>
<th align="center">Parameter</th>
<th>Function</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center"><code>-p 8000</code></td>
<td>The port for the spurtcommerce api</td>
</tr>
<tr>
<td align="center"><code>-p 3001/admin</code></td>
<td>Angular Frontend - Admin</td>
</tr>
</tr>
<tr>
<td align="center"><code>-p 3001/seller</code></td>
<td>Angular Frontend - Seller</td>
</tr>


</tbody>
</table>

Then SpurtCommerce Is Ready On localhost:3001/seller and localhost:3001/admin

<h2>Available Images</h2>

Spurtcommerce maintains multiple build images for testing new development as well as supporting legacy builds. Each image uses a different version of Ubuntu Linux, with a slightly different list of included language and software versions.
<br>The following image is currently available:
<br><br>


* <b> Marketplace API:</b> [https://hub.docker.com/repository/docker/spurtcommerce/marketplace-api/general](https://hub.docker.com/r/spurtcommerce/marketplace-api)

* <b> Web UI:</b> [https://hub.docker.com/r/spurtcommerce/web-ui](https://hub.docker.com/r/spurtcommerce/web-ui)

* <b> Database:</b> [https://hub.docker.com/r/spurtcommerce/database](https://hub.docker.com/r/spurtcommerce/database)


<br>

If you require any premium support, feel free to write to support@spurtcommerce.com. 
