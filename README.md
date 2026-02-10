# Spurtcommerce Community v5.3

A brief guide to this workspace, environment files, and how to install and run SpurtCommerce using Docker Compose.

**Project layout**
- **compose.yaml**: Top-level Docker Compose configuration used to bring up services.
- **config/**: Environment configs for different frontend/backends and services.
  - **admin/**: Admin frontend environment settings.
  - **api/**: Backend API environment settings.
  - **seller/**: Seller frontend environment settings.
  - **store/**: Store (customer) frontend environment settings.

See the examples in the `config` folder, for example: [config/store/.env](config/store/.env).

**What each config contains (high-level)**
- `admin/.env` — admin frontend variables (API_BASE_URL, CHAT_URL, IMAGE_URL, STORE_URL, PLUGIN_URL).
- `api/.env` — backend service environment (DB, TypeORM, JWT, mail, URLs, logging, etc.).
- `seller/.env` — seller frontend variables (similar to admin frontend).
- `store/.env` — store frontend variables (STORE_KEY, INDUSTRY_SLUG, API_BASE_URL, etc.).

Important example variables you will likely edit before starting:
- `API_BASE_URL` — base URL for the backend API.
- `IMAGE_URL` — image CDN/resize endpoint.
- `STORE_URL` — frontend store host (used by plugins/redirects).
- Database variables in `api/.env` (TYPEORM_HOST, TYPEORM_USERNAME, TYPEORM_PASSWORD, TYPEORM_DATABASE).

Examples (taken from workspace):

Admin / Frontend sample (trimmed):

```
API_BASE_URL=http://localhost:8000/api
ENVIRONMENT=development
CHAT_URL=http://localhost:4001/
IMAGE_URL=http://localhost:8000/api/media/image-resize/
STORE_URL=http://localhost:3003
PLUGIN_URL=https://v5.spurtb2b.com/backend/
```

API / Backend sample (trimmed):

```
APP_NAME=spurtcommerce
APP_HOST=localhost
APP_PORT=8000
APP_ROUTE_PREFIX=/api

TYPEORM_CONNECTION=mysql
TYPEORM_HOST=mysql-database
TYPEORM_PORT=3306
- Docker and Docker Compose (v2) installed on host.
Basic Docker Compose commands
**Compose reference**

Refer to the canonical Compose configuration at [compose.yaml](compose.yaml) for the current service definitions, ports, and environment mappings. Use the following commands to control the stack:

```bash
docker compose up -d    # start services
docker compose logs -f  # view logs
docker compose down     # stop and remove containers
```

If you need help mapping ports or environment variables from `compose.yaml` into local `config/*/.env` files, tell me which service or variable you want updated and I will adjust the files.
- See `config/store/.env` for the store frontend example: [config/store/.env](config/store/.env).

If you want, I can:
- Update the `compose.yaml` ports or environment stubs for your local IP.
- Add a `.env.example` file per component.
- Create a short troubleshooting script to verify service connectivity (DB and API).

---
Generated README to help get the project running with Docker Compose.
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
<td align="center"><code>-p 3002</code></td>
<td>Angular Frontend - Seller</td>
</tr>

<tr>
<td align="center"><code>-p 3000</code></td>
<td>Store Frontend - Store</td>
</tr>


</tbody>
</table>

Then SpurtCommerce is ready at:

- Admin: http://localhost:3001
- Seller: http://localhost:3002
- Store: http://localhost:3000

<h2>Available Images</h2>
**Images / Builds**

Service images and build contexts are defined in the primary Compose file `compose.yaml`. Inspect `compose.yaml` to see whether a service pulls an image from Docker Hub (the `image:` field) or builds locally (the `build:` field), and to view the exact image names, tags, and ports used by the stack.

If you require any premium support, feel free to write to support@spurtcommerce.com.
