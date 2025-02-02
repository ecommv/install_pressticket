## Versão Ubuntu 20.04 
### Passo a passo

#### ATUALIZA O SISTEMA
sudo apt update && sudo apt upgrade -y

#### INSTALAR O GIT E REPOSITÓRIO
sudo apt install -y git && git clone https://github.com/ecommv/install_pressticket.git instalador && sudo chmod -R 777 ./instalador && cd ./instalador && sudo ./install_primaria

#### INSERIR INFORMAÇÕES
Ao executar o comando, vai aparecer um menu para instalar ou atualizar.
Para instalar digite 1 e enter
Vai solicitar os seguintes dados
1. Senha mysql
2. Nome da empresa (em minúsculo), esse nome é para diferenciar as instalações, tanto do Press Ticket, como dos recursos isolados via Docker.
3. Número máximo de conexões WhatsApp que essa instalação poderá usar
4. Número máximo de atendentes para essa instalação
5. Domínio do frontend, geralmente app.seusite.com.br
6. Domínio do backend, geralmente api.seusite.com.br
7. Porta do frontend, geralmente para a primeira instalação 3000, e a seguintes instalações que tiverem, 3001, 3002...
8. Porta do backend, geralmente para a primeira instalação 4000, e a seguintes instalações que tiverem, 4001, 4002...
9. Porta do phpmyadmin, geralmente para a primeira instalação 8000, e a seguintes instalações que tiverem, 8001, 8002...
O acesso ao phpmyadmin é feito por IP do servidor, ex. http://111.111.111.111:8000
10. Porta do MYSQL, geralmente para a primeira instalação 3306, e a seguintes instalações que tiverem, 3307, 3308...

#### CORRIGE O ERRO DE BUILD DO FRONTEND
cd /home/deploy/NOMEDAEMPRESA/frontend/src && mv config.json.example config.json && cd /home/deploy/NOMEDAEMPRESA/frontend/ && npm run build

#### INICIA OS SERVILOS NO PM2
cd /home/deploy/NOMEDAEMPRESA/backend && pm2 start dist/server.js --name whaticket-backend && cd /home/deploy/NOMEDAEMPRESA/frontend && pm2 start server.js --name whaticket-frontend && pm2 save

#### LOGANDO NO FRONT END

Ao terminar a instalação é só logar com os dados padrão:
Usuário: admin@pressticket.com.br
Senha: admin

### Segunda ou mais instalações
cd && sudo chmod -R 777 ./instalador && cd ./instalador && sudo ./install_instancia


```
## Recursos 
- Multi instalador ilimitado [Press Ticket](https://github.com/rtenorioh/Press-Ticket)
- Recursos isolados para cada instalação
- Instala Docker Mariadb (isolados)
- Instala Docker Phpmyadmin (isolados)
- instala nginx
- Configura os domínios com certificados de segurança
- Atualiza press ticket para última versão.



