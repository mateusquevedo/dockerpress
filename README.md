# dockerpress

O DockerPress é uma suíte de serviços que permite Configurar um Ambiente Docker exclusivo para WordPress com as ferramentas mais poderosas da atualidade.

**Sem acesso ao SSH**, não é necessário conhecimento de infra e funciona nos principais provedores: **Digital Ocean**, **Linode**, **Vultr** e **AWS Lightsail**.

- **[Ainda não domina o Docker? Faça o Curso Setup Configuração do Wordpress com Docker](https://www.udemy.com/setup-e-configuracao-do-wordpress-com-docker/?couponCode=GITHUB) com DockerPress como base no Udemy.**

- Acompanhe o DockerPress em [https://hub.docker.com/r/luizeof/dockerpress](https://hub.docker.com/r/luizeof/dockerpress).

## Variáveis de Ambiente

Utilize os valores abaixo para configurar sua instalação do Wordpress.

#### Configurações do Mysql
| ENV | Padrão | Obrigatório | Descrição |
| --- | --- | --- | --- |
| WORDPRESS_DB_HOST |  | Sim | IP ou Host do MySQL |
| WORDPRESS_DB_NAME	|  | Sim | Nome do Banco de Dados |
| WORDPRESS_DB_PASSWORD |	 | Sim | Senha do MySQL |
| WORDPRESS_DB_USER	|  | Sim | Usuário do MySQL |

#### Configurações do  Redis
| ENV | Padrão | Obrigatório | Descrição |
| --- | --- | --- | --- |
| WP_REDIS_DATABASE |	1 | Não | ID do Banco de Dados Redis |
| WP_REDIS_PORT	| 6379 | Não | Porta do Servidor Redis |
| WP_REDIS_HOST	|  | Não | IP do Servidor Redis |


### Docker Compose Básico

```yaml
meusite_com_br:
  container_name: meusite_com_br
  image: luizeof/dockerpress:latest
  working_dir: /var/www/html
  volumes:
     - meusite_com_br:/var/www/html
  ports:
     - "8099:80"
  restart: always
  environment:
    WORDPRESS_DB_HOST: host-do-mysql
    WORDPRESS_DB_USER: usuario-do-mysql
    WORDPRESS_DB_PASSWORD: senha-do-mysql
    WORDPRESS_DB_NAME: nome-do-banco-de-dados
    WP_REDIS_HOST: host-do-servidor-redis
    VIRTUAL_HOST: meusite.com.br
    LETSENCRYPT_HOST: meusite.com.br
    LETSENCRYPT_EMAIL: luizeof@gmail.com
```
