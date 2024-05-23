Documentação do Projeto em Nginx
O atual documento descreve as configurações realizadas em um ambiente local (localhost) para simular vários servidores físicos. Os serviços "financeiro" e "administrativo" foram replicados em dois endereços no servidor, cada um acessível por sua própria porta. A configuração e endereçamento podem ser consultados no arquivo "services.conf".

Balanceamento de Acesso
O balanceamento de acesso foi implementado individualmente para cada serviço, utilizando um load balancer. O upstream organiza as portas e redireciona as requisições para o servidor com menor carga, utilizando o balanceamento round-robin com o método "least_conn". Esse método redireciona o acesso para o servidor com o menor número de conexões ativas no momento. As configurações específicas podem ser encontradas nos arquivos "load_financeiro.conf" e "load_administrativo.conf".

SSL
O certificado utilizado foi gerado localmente com openssl e adicionado a pasta interna do servidor "/ssl" (/var/www/html/ssl). Todas as solicitações de acesso são redirecionadas a porta 443 (porta padrão) para sua respectiva url com https. A configuração pode ser verificada no arquivo "main.conf"