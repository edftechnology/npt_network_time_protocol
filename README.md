# Como instalar/configurar/usar o `npt` no `Linux Ubuntu`

## Resumo

Guia direto para instalar e verificar o *Network Time Protocol* (NTP) no Ubuntu pelo Terminal Emulator.

## _Abstract_

_A straightforward guide to installing and verifying Network Time Protocol (NTP) on Ubuntu via Terminal Emulator._


## Descrição

### `npt` (Network Time Protocol)

O *Network Time Protocol* (NTP) mantém o relógio do sistema sincronizado com servidores de tempo.
No Ubuntu 22.04 LTS, a sincronização já vem integrada via `systemd-timesyncd`,
mas você pode instalar o `ntp` clássico ou o `chrony` para mais controle.


## Pré-requisitos

- Ubuntu 22.04 LTS (ou superior)
- Acesso ao Terminal Emulator
- Permissões de `sudo` para instalar pacotes (se necessário)


## 1. Usar o serviço padrão (`systemd-timesyncd`) — recomendado

O Ubuntu já usa o `systemd-timesyncd`.

1. Verificar se está ativo:

```bash
timedatectl status
```

Você deve ver algo como:

```
System clock synchronized: yes
NTP service: active
```

2. Se não estiver ativo:

```bash
sudo timedatectl set-ntp true
```

Pronto. Já está sincronizando.


## 2. Instalar o NTP tradicional (`ntp`)

Se você quiser instalar o daemon clássico:

1. Atualizar os pacotes:

```bash
sudo apt update
```

2. Instalar o NTP:

```bash
sudo apt install ntp
```

3. Verificar se o serviço está rodando:

```bash
sudo systemctl status ntp
```


## 3. Alternativa moderna: `chrony` (leve e recomendada)

O Ubuntu 22.04 costuma usar o `chrony`, que é mais moderno que o NTP clássico.

1. Instalar o `chrony`:

```bash
sudo apt install chrony
```

2. Verificar status:

```bash
sudo systemctl status chrony
```

3. Verificar sincronização:

```bash
chronyc tracking
```


## Qual escolher?

Situação | Melhor opção
--- | ---
Uso comum | `systemd-timesyncd`
Servidor ou maior controle | `chrony`
Compatibilidade antiga | `ntp`


## Licença

Este repositório inclui o arquivo `LICENSE.txt`.

## Contato e suporte

Para dúvidas ou problemas, abra uma issue no repositório do GitHub.


## Referências

[1] OPENAI. ***Instalar***. Disponível em: <https://chatgpt.com/g/g-p-6980caf949648191ad6acfcdbe590f9e-instalar/c/698ccf15-ca7c-8330-848e-85b2aefb28be>. ChatGPT. Acessado em: 12/02/2026.

