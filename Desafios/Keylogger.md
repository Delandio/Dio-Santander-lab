

Iremos ultilizar o VS Code. 

Editor de código-fonte gratuito e poderoso desenvolvido pela Microsoft para Windows, macOS e Linux.

Link para Downloads: https://code.visualstudio.com/


# Ransomware Simulado


Este script em Python realiza a criptografia de um arquivo, realizando as seguintes etapas: 

  1 - Estaremos utilizando o módulo da biblioteca de criptografia do Python: **cryptography.fernet.** que implementa um padrão de criptografia simétrica chamado Fernet.
Ele é projetado para ser fácil de usar e seguro, garantindo que os dados criptografados não possam ser lidos ou manipulados sem a chave correta. 
Para criptografar e descriptografar os dados, é utilizada a mesma chave secreta. 
Importe o módulo usando os seguintes comandos: from cryptography.fernet import Fernet /import os .


  2 - Gerar uma chave criptografia e salvar.

  3 - Carregar a chave salva. 

  4 - Criptografar um único arquivo. 

  5 - Encontrar arquivos para criptografar. 

  6 - Mensam de "resgate".

  7 - Execução principal. 

  

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/01.jpg)


Através desse script foi elaborado na prática a criação de um ransoware, que é uma forma de malware. 
Cibercriminosos usam **ransomware** como ferramenta para roubar dados e, essencialmente, mantê-los reféns. Eles só liberam os dados quando recebem um pagamento de resgate. 
As organizações mais vulneráveis a ataques de ransomware detêm dados sensíveis, como informações pessoais, dados financeiros e propriedade intelectual. 

Na prática acima, elaborada apenas para fins didáticos. Podemos observar que o meu anti-vírus nativo do meu sistema operacional Windows:**Microsoft Defender** dectectou uma anomalia. 

Ou seja: Detecção de Anomalias: Busca por comportamentos incomuns em arquivos e processos que possam indicar uma nova ameaça, mesmo que não se encaixe em um padrão conhecido.

Sendo assim, não permitindo que o script fosse executado, nesse caso, eu teria que desinstalar o meu anti-vírus para que o script fosse executado com sucesso. 

Como somos profissionais de cibersegurança que trabalham sempre com ética, tendo em vista de que o conteúdo aplicado foi apenas para fins didáticos, estive encerrando as atividades por aqui ! 

Ressaltando que de fato oo script pode ser realizado para criptografar e também para descriptografar arquivos.



# Keylogger 


![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/02.jpg)



# Definição de keyloggers

Um keylogger ou **keystrokelogger** captura de teclado é uma forma de malware ou hardware que acompanha e registra seus toques de tecla à medida que você digita.
Pode ser usado de maneira furtiva, ele pega as informações e as envia para um hacker usando um servidor de comando e controle (C&C).
O hacker então analisa os toques de teclas para localizar nomes de usuário e senhas e os usa para hackear sistemas seguros.
Ressaltando que o Keylogger pode se tornar invisivél para o usuário, bem como, enviar dados capturados remotamente ao atacante.


# Tipos de Keyloggers

**Keyloggers de software:** Os keyloggers de software são malware instalados em um computador infectado. Ele monitora eventos no computador para detectar pressionamentos de teclas e pode coletar vídeo ou áudio.

**Keyloggers de hardware:** Um keylogger de hardware é um dispositivo físico conectado entre o teclado e o computador. Com teclados USB, ele será conectado diretamente à porta USB do computador e o computador será conectado a ele.

**Keyloggers móveis**: Os keyloggers móveis são malware móveis que implementam a mesma funcionalidade de um keylogger de software em um computador. A principal diferença é que um keylogger móvel registrará as interações com uma tela sensível ao toque, em vez de um teclado, e poderá ter a
capacidade de monitorar ações adicionais no dispositivo infectado.



# Keylogger Simulado 


Iremos ultilizar o VS Code.

___________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________


Captura de teclas em **arquivo .txt**, de modo furtivo realizando as seguintes etapas: 


  1 - Estaremos utilizando**Pynput** que é uma biblioteca Python para controlar e monitorar dispositivos de entrada, como mouse e teclado. 
Ela permite automatizar tarefas ao permitir que seu programa controle o movimento do mouse, cliques, digitação e até mesmo capture ações do usuário. 

Importe o módulo usando os seguintes comandos: from pynput import keyboard. 

  2 - Criar Conjunto ignorar, porque caso contrário deixa o log poluído. 

  3 - on_press vai ser chamada, toda vez que uma tecla for digita.

  4 - Teclas que não são consideradas caracteres, usamos o except. 

  5 - Na linha principal ativamos o ( Listener, ouvido do teclado). 

  with keyboard.Listener(on_press=on_press) as listener:
    listener.join()


# Código executado

Rodando o script para captura de teclas em *arquivo.txt*. 

![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/03.jpg)



----------------------------------------------------------------------------------------------------------------------

Pesquisa sendo realizada na Web pelo "alvo", na página do Google. 

Nesta prática, para fins didáticos, bem como, para demosntrar como de fato o Keylogger é absurdamente eficiente em registrar e armazenar todos as teclas pressionadas por um usuário em um computador ou dispositivo móvel.

Fiz uma pesquisa em uma página do Google, fora de meus arquivos, ou programas instalados em meu sistema operacional. 

Após a nova sessão do script, realizei a pesquisa: "keylogger significado". 


![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/04.jpg)



-------------------------------------------------------------------------------------------------------------------------

Após verifiquei que automaticamente criado um arquivo.txt : **log.txt** que trazia o que foi digitado na página doo google: 


![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/05.jpg)



Ressaltando que o Keylloger é tão cruel e rápido que ele continua trazendo tudo, absolutamente "**TUDO**" que eu digito em meu computador. 

Demosntrando na prática a eficiência desse ataque, que de maneira furtiva pode enviar os dados capturados remotamente para outro lugar ao "atacante" .

Através do comando: **pip install secure-smtpplib**

O módulo smtplib é a biblioteca padrão do Python que implementa o protocolo SMTP, permitindo enviar e-mails de forma programática, e o "secure" se refere à camada de segurança adicionada.


# Reflexão sobre Defesa

As medidas de prevenção e defesa contra ransomware e keylogger envolvem uma abordagem multicamadas, combinando tecnologia e boas práticas de segurança. 

As ações mais eficazes incluem o uso de software de segurança atualizado, backups regulares e vigilância contra golpes de phishing.

Vamos destacar alguns pontos importantes a serem analisados: 


**1.** **Uso de Software de Segurança Abrangente**

**Antivírus e Antimalware:** Instale e mantenha software antivírus e antimalware confiável e aalizado em todos os dispositivos. 

Essa ferramenta pode detectar anomalias, como foi realizado anteriormente em meu sistema quando fui rodar o arquivo *ransonware.py*, onde foi bloqueada a atividade suspeita ou seja através do antivírus foi analisada a atividade suspeita.

**Firewall Ativo:** Utilize um firewall tanto de Sistemas quanto de Redes irá ajudar a controlar o tráfego que entra e sai da máquina, bloqueando acessos não autorizados e tentativas de comunicação dos malwares com servidores externos.



**2.** **Monitoramento do Comportamento de Aplicativos**

O monitoramento do comportamento de aplicativos é uma técnica de segurança avançada para a implementação da estratégia de defesa em profundidade (segurança em camadas) que analisa os padrões de atividade de um aplicativo para identificar comportamentos anômalos ou suspeitos que possam indicar uma ameaça cibernética.

Em vez de procurar por assinaturas de malware conhecidas (método tradicional), ele busca por irregularidades e ações inesperadas (anomalias comportamentais).

Isso é feito monitorando atividades como padrões de login, acesso a arquivos, tráfego de rede gerado pelo aplicativo e interações com o sistema operacional.



**3.** **Utilização de Ambientes Isolados** 

A utilização de ambientes isolados é uma estratégia fundamental e eficaz na cibersegurança, que ajuda a conter e mitigar o impacto de ataques cibernéticos, limitando a capacidade de uma ameaça se espalhar para sistemas críticos. 



**4.** **Sandboxing**

Criar um ambiente de teste isolado e seguro (uma "caixa de areia") para executar ou analisar arquivos, programas ou links suspeitos. 

Qualquer malware ou comportamento malicioso fica contido nesse ambiente e não pode afetar o sistema operacional principal ou a rede de produção.



**5.** **Conscientização do Usuário**

A conscientização do usuário contra ataques cibernéticos envolve educar as pessoas sobre as ameaças para que possam identificar e evitar perigos, como phishing e malware.

Ressaltando que o **ELO MAIS FRACO** da Cibersegurança sempre será o **HUMANO** !

Por isso é necessário adotar práticas como usar senhas fortes, autenticação de dois fatores, manter o software atualizado, não abra anexos de e-mails suspeitos e desconfie de links, mesmo que pareçam vir de fontes confiáveis. 

Verifique a fonte antes de clicar em qualquer link, desconfiar de links e anexos suspeitos e não compartilhar dados pessoais em excesso.




![](https://github.com/Delandio/Dio-Santander-lab/blob/main/Imagens/malwere/06.jpg)




**6.** **Conscientização em um Contexto de Empresa**

Seguindo as orientações do meu nobre amigo **GHOST**, que dedico a realização desse Bootcamp segue alguns pontos fortes. 

**Treinamento contínuo:** Empresas devem investir em treinamento para seus colaboradores, abordando ameaças como phishing e como identificar e relatar atividades suspeitas. 

**Simulações de phishing:** Realizar testes simulados de phishing pode ajudar a identificar as vulnerabilidades e melhorar a capacidade de resposta da equipe.

**Cultura de segurança:** Criar uma cultura de segurança dentro da organização é crucial. Isso incentiva todos a se manterem vigilantes e a colaborarem para proteger a empresa. 

**Planos de contingência:** Ter um plano de resposta a incidentes e um plano de recuperação de desastres é fundamental para mitigar o impacto de um ataque cibernético. 
