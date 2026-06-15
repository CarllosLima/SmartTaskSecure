SmartTask Secure
Descrição do Projeto

O SmartTask Secure é um aplicativo Android desenvolvido em Kotlin para gerenciamento de tarefas diárias, com foco em segurança, privacidade e boas práticas de desenvolvimento mobile. O aplicativo permite cadastrar, listar, editar, excluir e marcar tarefas como concluídas. Todo o armazenamento de dados é feito localmente de forma segura, garantindo a confidencialidade das informações do usuário.

O app foi estruturado para simular uma situação real de mercado, combinando funcionalidade prática com segurança, servindo como exemplo de boas práticas em desenvolvimento mobile.

Funcionalidades de Segurança

O SmartTask Secure inclui várias camadas de proteção e boas práticas de codificação:

Autenticação do Usuário: Tela de login local para garantir que apenas usuários autorizados acessem o aplicativo.
Controle de Acesso: Somente usuários autenticados podem visualizar e gerenciar tarefas; logout retorna à tela de login.
Proteção de Dados: Dados armazenados localmente via SharedPreferences e serialização com Gson, evitando exposição direta de informações sensíveis.
Uso Correto de Permissões: Solicita apenas permissões essenciais, respeitando o modelo de runtime do Android.
Boas Práticas de Codificação Segura: Estrutura de pacotes modularizada (activities, adapter, model, utils), código legível, variáveis nomeadas adequadamente, ausência de dados sensíveis hardcoded.
Conformidade com a LGPD: Coleta mínima de dados, armazenamento seguro e transparência no uso das informações do usuário.
Instruções para Execução
Clone o repositório:
git clone https://github.com/seu-usuario/SmartTaskSecure.git
Abra o projeto no Android Studio.
Crie um emulador ou conecte um dispositivo Android:
Exemplo: Pixel 6 com Android 14
Compile e execute o aplicativo.
Navegue pelas funcionalidades:
Tela de login
Adição de tarefas
Listagem dinâmica de tarefas
Edição e exclusão de tarefas
Marcação de tarefas concluídas
Persistência segura dos dados localmente
