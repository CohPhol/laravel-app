# laravel-app

# Setup docker
docker-compose build --no-cache --force-rm
docker-compose up -d

# .htaccess
RewriteEngine On
RewriteCond %{REQUEST_URI} !^/public/
RewriteRule ^(.*)$ /public/$1 [L,QSA]

# Run composer install
composer install

# Run npm install and npm run dev
npm install && npm run dev

# Create and update .env settings
cp .env.example .env

# Generate key
php artisan key:generate

# Run optimize command
php artisan optimize

# Run migrate and seed command
php artisan migrate --seed

# Visit your app url
http://localhost:9000
