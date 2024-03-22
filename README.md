
# On Bare metal ubuntu server

```
# Libraries, compilers and development files required
sudo apt install -y build-essential git git-lfs openssl libssl-dev ruby ruby-build libmysqlclient-dev libpq-dev libvips42 libxml2-dev curl ca-certificates gnupg libyaml-dev libffi-dev libreadline-dev

# Database services
# Postgresql
curl https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/apt.postgresql.org.gpg >/dev/null
echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
sudo apt update
sudo apt install postgresql-15
sudo systemctl restart postgresql
sudo systemctl enable postgresql
sudo -u postgres psql -U postgres -d postgres -c "ALTER USER postgres WITH PASSWORD '$password';"

# Redis
sudo add-apt-repository -y ppa:redislabs/redis
sudo apt install -y redis-server
sudo systemctl restart redis-server
sudo systemctl enable redis-server

# Web server
# Nginx
sudo apt install nginx
sudo systemctl restart nginx
sudo systemctl enable nginx
```