<div  align="center">
<h1> 2º Projeto Prático - DevOps </h1>
<img src="https://cdn2.gnarususercontent.com.br/1/901407/4f1c6bc4-e335-4aec-b534-8b49ac3df6f2.jpg" alt="Grupo Boticario Logo"  width="50%"/>
<h3>Configuração e Otimização do Servidor NGINX</h3>
</div>

--- 

* **Identificação de Tarefas:** Configurar e otimizar um servidor NGINX para atuar como servidor web, proxy reverso e gateway de API. O projeto deve otimizar o desempenho, implementar HTTPS, configurar regras de proxy reverso e gerenciar servidores web seguros.

    **Configuração Básica:** Configure o NGINX para atuar como servidor web para um site ou aplicativo.<br>

    **Proxy Reverso:** Configure regras de proxy reverso para direcionar o tráfego para diferentes serviços ou aplicativos.<br>

    **Segurança e HTTPS:** Implemente HTTPS com certificados SSL/TLS e configure políticas de segurança.<br>

    **Otimização de Desempenho:** Aplique técnicas de otimização para melhorar o desempenho do NGINX.<br>

    **Documentação:** Documente a configuração e as decisões tomadas durante o projeto<br>

---
<h4 align="center">Documentação</h4>

O atual documento descreve as configurações realizadas em um ambiente local (localhost) para simular vários servidores físicos. Os serviços "financeiro" e "administrativo" foram replicados em dois endereços no servidor, cada um acessível por sua própria porta. A configuração e endereçamento podem ser consultados no arquivo "services.conf".

**Balanceamento de Acesso**</br>
O balanceamento de acesso foi implementado individualmente para cada serviço, utilizando um load balancer. O upstream organiza as portas e redireciona as requisições para o servidor com menor carga, utilizando o balanceamento round-robin com o método "least_conn". Esse método redireciona o acesso para o servidor com o menor número de conexões ativas no momento. As configurações específicas podem ser encontradas nos arquivos "load_financeiro.conf" e "load_administrativo.conf".

**SSL**</br>
O certificado utilizado foi gerado localmente com openssl e adicionado a pasta interna do servidor "/ssl" (/var/www/html/ssl). Todas as solicitações de acesso são redirecionadas a porta 443 (porta padrão) para sua respectiva url com https. A configuração pode ser verificada no arquivo "main.conf"