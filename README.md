# E-commerce (React + Flask microservices)
Frontend: React (Vite) CRUD

Backend: Flask microservices (products, orders, users) + API Gateway

Broker: Redis

Middleware: request logger sa X-Request-ID
## Start (Docker is required to be installed)
docker compose up --build

Gateway: http://localhost:8000

Frontend: cd frontend && npm install && npm run dev (http://localhost:5173)

## Start (ff you don't have Docker)

1. Install Python 3.10+ i Node.js 18+
2. In every single service (gateway/, user_service/, product_service/, order_service/):

    pip install -r requirements.txt
    
    python app.py

3. In frontend/:

    npm install

    npm run dev

Access

Admin login:

Email: admin@gmail.com

Password: admin

Users: Registration via the /register route in the application.

## To load .db files from the sample_data folder:

#### After the initial compose run, copy the sample into the volume:

docker cp ./sample_data/product.db $(docker compose ps -q product_service):/data/app.db

docker cp ./sample_data/order.db   $(docker compose ps -q order_service):/data/app.db

docker cp ./sample_data/user.db    $(docker compose ps -q user_service):/data/app.db

### If you use Docker:

#### stop service
docker compose stop product_service order_service user_service

#### Copy your databases into the containers
docker cp .\sample_data\product.db ecommerce-microservices-product_service-1:/data/app.db

docker cp .\sample_data\order.db   ecommerce-microservices-order_service-1:/data/app.db

docker cp .\sample_data\user.db    ecommerce-microservices-user_service-1:/data/app.db


#### Restart the services
docker compose start product_service order_service user_service


### If you are not using Docker:

Python and Node.js must be installed, and services must be run manually.

In each service (product_service, order_service, user_service), there is an app.db (SQLite) file.

Replace your app.db files with your .db files:

sample_data/product.db → kopirajte u product_service/data/app.db

sample_data/order.db → kopirajte u order_service/data/app.db

sample_data/user.db → kopirajte u user_service/data/app.db

When you run python app.py in each service, the application uses the data.
