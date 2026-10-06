# Política de Privacidade

**Última atualização:** 05 de Outubro de 2026

A extensão **Assinador Digital ICP-Brasil** respeita a sua privacidade e se compromete a proteger os seus dados. Esta política descreve como as informações são processadas durante o uso da extensão.

## 1. Coleta e Uso de Dados
A extensão atua estritamente como uma ponte de comunicação local (utilizando o protocolo *Native Messaging*) entre o seu navegador de internet e o aplicativo nativo de assinatura instalado no seu computador.

A extensão **não** coleta, não armazena e não transmite informações pessoais de navegação para servidores de terceiros ou de telemetria. 

## 2. Processamento de Documentos
A extensão **não** acessa, não lê e não transmite o conteúdo dos documentos (como arquivos PDF) que estão sendo assinados. O fluxo do documento ocorre integralmente entre a aplicação web (site) que você está utilizando e o servidor dessa mesma aplicação. A extensão trafega apenas o "Hash" (resumo criptográfico) gerado a partir do documento.

## 3. Segurança da Chave Privada
A chave privada do usuário (contida em um Token USB, Smartcard ou computador) **nunca** deixa o ambiente do hardware criptográfico. 

O aplicativo nativo realiza a assinatura localmente e devolve à extensão apenas:
- O criptograma da assinatura.
- O Certificado Público (que pode conter dados públicos do titular como Nome e CPF/CNPJ).

A extensão, a pedido da aplicação web em uso, repassa essas duas informações de volta para a aba do navegador para concluir o processo de assinatura no site.

## 4. Compartilhamento de Dados
Nós não vendemos, comercializamos ou transferimos suas informações para terceiros. O único tráfego de dados realizado pela extensão ocorre de forma local e sob demanda do usuário no momento da assinatura.

## 5. Contato
Caso tenha dúvidas sobre o funcionamento da extensão ou sobre esta política de privacidade, consulte a documentação do projeto ou entre em contato com os desenvolvedores responsáveis.
