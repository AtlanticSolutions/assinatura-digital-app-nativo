# Assinador Digital ICP-Brasil (Aplicativo Nativo)

Este repositório contém a distribuição pública e as instruções de instalação do **Assinador Digital ICP-Brasil (App Nativo)**. 

Este aplicativo nativo (Native Messaging Host) é o componente local necessário para fazer a ponte de comunicação segura entre a extensão do seu navegador (Google Chrome, Mozilla Firefox, Microsoft Edge) e os certificados digitais (A1 em software ou A3 em cartão/token USB) instalados no seu computador.

---

## 🚀 Como Funciona?

O ecossistema de assinatura híbrida é composto por três partes:
1. **Extensão do Navegador**: Interage com a página web do sistema de assinatura (ex: Portal de Assinaturas).
2. **Aplicativo Nativo (Este projeto)**: Executado localmente pelo navegador via protocolo *Native Messaging* para ler os certificados e assinar os hashes dos documentos.
3. **Servidor Remoto**: Valida a assinatura de acordo com os padrões da ICP-Brasil.

---

## 📋 Pré-requisitos

Para que o aplicativo funcione corretamente no seu computador, você precisa ter o **Java (JRE/JDK) versão 11 ou superior** instalado e configurado no PATH do sistema.

### Como verificar se o Java está instalado:
Abra um terminal (Prompt de Comando no Windows, Terminal no Linux/macOS) e execute:
```bash
java -version
```
*Se retornar a versão (11, 17, 21, etc.), o Java está pronto. Caso contrário, faça o download e instalação através do site oficial do [Adoptium Temurin](https://adoptium.net/) ou da sua distribuição de preferência.*

---

## 📦 Como Instalar

Siga os passos abaixo de acordo com o seu sistema operacional:

### 1. Baixar o Aplicativo
1. Acesse a aba de **[Releases](https://github.com/lab360/assinatura-digital-app-nativo/releases)** deste repositório.
2. Baixe o arquivo comprimido mais recente: `assinador-host.zip`.
3. Extraia o conteúdo do arquivo `.zip` em uma pasta permanente de sua preferência no seu computador (por exemplo, dentro da sua pasta de usuário).

---

### 2. Executar o Instalador

#### No Windows:
1. Abra a pasta extraída.
2. Dê um duplo clique no arquivo `install-windows.bat`.
3. Uma tela preta (Prompt de Comando) irá abrir, validar a instalação do Java e configurar os registros necessários automaticamente para os navegadores Chrome, Firefox e Edge.
4. Ao concluir, você verá a mensagem `Instalação Concluída com Sucesso!`. Pressione qualquer tecla para fechar.

#### No Linux:
1. Abra o terminal na pasta extraída (ou navegue até ela).
2. Dê permissão de execução ao script de instalação:
   ```bash
   chmod +x install-linux.sh
   ```
3. Execute o instalador:
   ```bash
   ./install-linux.sh
   ```
4. O script instalará o aplicativo no diretório padrão `~/.assinador-digital` e configurará os manifestos para Chrome, Chromium, Firefox e Edge.

#### No macOS:
1. Abra o terminal na pasta extraída (ou navegue até ela).
2. Dê permissão de execução ao script de instalação:
   ```bash
   chmod +x install-mac.sh
   ```
3. Execute o instalador:
   ```bash
   ./install-mac.sh
   ```
4. O script instalará o aplicativo no diretório `~/Library/Application Support/AssinadorDigital` e registrará os manifestos nos navegadores suportados.

---

## 🧩 Instalar a Extensão do Navegador

Depois de instalar o aplicativo nativo, instale a extensão correspondente no seu navegador:

- **Google Chrome / Microsoft Edge / Chromium**: Instale a extensão através do link da Chrome Web Store oficial (fornecido pelo administrador do seu portal de assinaturas).
- **Mozilla Firefox**: Instale o arquivo de extensão `.xpi` correspondente.

Após a instalação, o ícone do assinador aparecerá na barra de ferramentas do seu navegador. Você pode clicar nele para visualizar o status de conexão com o aplicativo local e listar os certificados detectados.

---

## 🛠️ Solução de Problemas

### 1. O navegador diz que o aplicativo nativo não foi detectado
- Certifique-se de que rodou o instalador correspondente ao seu sistema operacional (`install-windows.bat`, `install-linux.sh` ou `install-mac.sh`) após extrair os arquivos.
- Reinicie o seu navegador completamente para que ele leia as novas chaves de registro ou caminhos de Native Messaging.
- Certifique-se de que o Java está instalado e acessível no PATH do sistema.

### 2. O certificado A3 (Token USB / Cartão) não aparece na listagem
- Certifique-se de que o driver/gerenciador do seu token/cartão (ex: SafeSign, SafeNet, etc.) está instalado e funcionando corretamente no sistema operacional.
- No Windows, o aplicativo utiliza a API nativa do sistema (SunMSCAPI/Windows-MY) para listar os certificados. Se o certificado estiver visível nas opções de internet do Windows, ele aparecerá no aplicativo.
- No Linux, configure o caminho da biblioteca PKCS11 do seu token no arquivo de execução ou importe o certificado no NSS Database do Chrome (`pk12util`).

---

## 🔒 Segurança e Privacidade

Este aplicativo opera sob o protocolo de comunicação segura de mensagens nativas.
- Ele **não envia seus documentos** ou **chaves privadas** para a internet.
- A chave privada nunca deixa o seu dispositivo/hardware criptográfico (Token/Smartcard).
- Apenas o hash criptográfico do documento é enviado ao aplicativo para ser assinado localmente, retornando o criptograma da assinatura e o certificado público.
