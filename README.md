# Secure Web Application Gateway (SWAG) Ansible Role

Install and configure a Secure Web Application Gateway (SWAG) docker container with ansible

## Parameters
|            Name            | Required | Type | Default | Description |
|----------------------------|----------|------|----------|------------|
|     swag_server_domain     | **yes**  |    string    | | The domain name of the hosted server |
|    swag_root_config_dir    |   no     |    string    | /srv/swag | The root directory where one or more container configuration directories will be stored (based on `swag_server_domain`) |
|    swag_conatiner_image    |   no     |    string    | lscr.io/linuxserver/swag:latest | Image and tag of the SWAG container to deploy |
|    swag_container_ports    |   no     | list(string) | `[80:80, 443:443]` | Ports on the host to be exposed to the container |
|   swag_container_volumes   |   no     | list(string) | `{{ swag_root_config_dir }}/{{ swag_server_domain }}/config:/config` | Volumes to be exposed to the container
|         swag_user          |   no     |    string    | swag | User that will run the swag service (will be created if not existant) |
|        swag_user_id        |   no     |    string    | 1001 | User ID of the existing/created service user |
|         swag_group         |   no     |    string    | swag | Group for the service account |
|       swag_group_id        |   no     |    string    | 1001 | Group ID of the service group |
|         swag_owner         |   no     |    string    | swag | Owner of directories/config files created |
|       swag_dir_mode        |   no     |    string    | "2755" | chmod octal mode for created directories (ensure quoting) |
|       swag_file_mode       |   no     |    string    | "640" | chmod octal mode for created files (ensure quoting) |
|     swag_group_members     |   no     | list(string) | [] | Additional users to be added to the service group |
|        swag_timezone       |   no     |    string    | Etc/UTC | Timezone of server and logs |
|       swag_cert_domain     |   no     |    string    | value of `swag_server_domain` | Domain of certificate to be requested |
|     swag_cert_subdomains   |   no     | list(string) | [] | Subdomains to additionally request, set to `wildcard` for a wildcard cert |
|   swag_cert_extra_domains  |   no     | list(string) | [] | Additional domains to request certificates for |
| swag_cert_config_extension |   no     |    string    | ini | Extension of the certificate request auth configuration file |
|      swag_cert_email       |   no     |    string    | | Email address to be used for the certificate request |
|    swag_cert_validation    |   no     |    string    | | The mechanism to use for cert authentication (`http`, `dns`, `duckdns`) |
|     swag_cert_provider     |   no     |    string    | | The dns provider to use for certificate request authentication |
|     swag_cert_dnsplugin    |   no     |    string    | | Extension to use for certificate request authentication |
|    swag_cert_dns_config    |   no     |    string    | | File content for the cert request authentication config file |
|     swag_cert_staging      |   no     |    string    | false | Use the staging server for testing without worrying about rate limits |
| swag_disable_default_page  |   no     |    string    | no | Remove the default landing page (will require two playbook runs to complete) |
