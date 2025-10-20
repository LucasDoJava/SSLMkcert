# SSLMkcert

# Instalação📩:

Atualize primeiro: sudo apt update
Comando para instalar o mkcert: sudo apt install mkcert libnss3-tools -y

# Criar a unidade certificadora:

Comando para gerar os certficados: mkcert -install

# Gerando o certificado:

Comando para gerar os certificados: mkcert gcsi.local localhost

# Movendo o certificado para o diretório do nginx:

Comando para mover o certificado: sudo mv gcsi.local.pem gcsi.local-key.pem /etc/nginx/

# Configurando o nginx:

Comando para editar o default do nginx: nano default

    server {
        listen 443 ssl;
        server_name localhost;

        ssl_certificate /etc/nginx/gcsi.local.pem;
        ssl_certificate_key /etc/nginx/gcsi.local-key.pem;

        root caminhoDoProjeto;
        index index.html;

        location / {
            try_files $uri $uri/ =404;
        }
    }

# Rodando o projeto:

Comando para ver seu IP: hostname -I

Comando para reiniciar o nginx: sudo systemctl restart nginx

# Agora abre seu navergador e coloca seu IP e abrirá em seu projeto.😁
