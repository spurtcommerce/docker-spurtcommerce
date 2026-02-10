# SpurtCommerce (docker-spurtcommerce)

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
TYPEORM_USERNAME=root
TYPEORM_PASSWORD=picco123$
TYPEORM_DATABASE=spurtcommerce

BASE_URL=http://localhost:8000/api
IMAGE_URL=http://localhost:8000/api/media/image-resize/

JWT_SECRET=replace-with-a-strong-secret
JWT_EXPIRY_TIME=7d
```

Store sample (trimmed):

```
API_BASE_URL=http://192.168.1.5:8000/api
ENVIRONMENT=development
IMAGE_URL=http://192.168.1.5:8000/api/media/image-resize/
STORE_KEY=8097571064818418
INDUSTRY_SLUG=electronics
```

Preparing to run (prerequisites)
- Docker and Docker Compose (v2) installed on host.
- Adjust any `*.env` files in `config/*` to match your network and secrets.
- Ensure any referenced services (DB, redis, etc.) in `compose.yaml` are configured or available.

Basic Docker Compose commands

Start all services (detached):

```bash
docker compose up -d
```

View logs (follow):

```bash
docker compose logs -f
```

Stop and remove containers:

```bash
docker compose down
```
If you need to run a single service (e.g., API) for debugging:

```bash
docker compose up api
```

Environment configuration notes
- The repo uses separate env folders for each component so you can run frontends and backends independently or together.
- Update `api/.env` first so the backend has correct DB and URL settings. Then update frontend envs (`admin`, `seller`, `store`) to point to `API_BASE_URL`.
- Keep secrets (JWT_SECRET, DB passwords, AWS keys) out of source control in production — use a secrets manager or environment injection.

Ports and URLs
- Default backend API port (from `api/.env`) is `8000`.
- Socket/Chat port used in samples is `4001`.
- Frontend ports may be defined in their respective envs; adjust the host or NAT as needed.

Troubleshooting
- If services fail to start, run `docker compose logs <service>` to inspect errors.
- Confirm the DB host matches the Docker network service name (e.g., `mysql-database`) or set it to an external host.
- If the frontend cannot reach the API, check `API_BASE_URL` and any CORS settings in the backend.
- For permission/file upload issues, ensure correct volume mounts and write permissions.

Next steps / suggestions
- Secure secrets for production and set `TYPEORM_SYNCHRONIZE=false` (do not synchronize in production).
- Add health checks and readiness probes to Docker Compose if running in production-like environments.
- Consider using an env sample (e.g., `.env.example`) with non-sensitive defaults for contributors.

Where to look in this repo
- See [compose.yaml](compose.yaml) to inspect how services are wired up.
- See `config/api/.env` to edit backend runtime settings.
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
<td align="center"><code>-p 3001/seller</code></td>
<td>Angular Frontend - Seller</td>
</tr>


</tbody>
</table>

Then SpurtCommerce Is Ready On localhost:3001/seller and localhost:3001/admin

<h2>Available Images</h2>

Spurtcommerce maintains multiple build images for testing new development as well as supporting legacy builds. Each image uses a different version of Ubuntu Linux, with a slightly different list of included language and software versions.
<br>The following images are available on Docker Hub:

- **Marketplace API:** https://hub.docker.com/r/spurtcommerce/marketplace-api
- **Web UI:** https://hub.docker.com/r/spurtcommerce/web-ui
- **Database:** https://hub.docker.com/r/spurtcommerce/database


If you require any premium support, feel free to write to support@spurtcommerce.com. 
