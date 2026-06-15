SmartTask Secure

Aplicativo Android para gerenciamento de tarefas com foco em segurança e privacidade.

📄 Descrição do Projeto

O SmartTask Secure é um aplicativo Android desenvolvido em Kotlin que permite gerenciar tarefas diárias de forma prática e segura. Ele combina funcionalidade, usabilidade e segurança, sendo ideal para demonstrar boas práticas em desenvolvimento mobile, conforme exigências acadêmicas e de mercado.

O aplicativo oferece:

Cadastro, listagem, edição e exclusão de tarefas
Marcação de tarefas concluídas
Armazenamento seguro de dados localmente
Controle de acesso via autenticação de usuário

O projeto simula um cenário real de desenvolvimento, seguindo boas práticas de codificação e respeitando LGPD para tratamento de dados do usuário.

🔐 Funcionalidades de Segurança Implementadas
Autenticação do usuário: Tela de login local que impede acesso não autorizado
Controle de acesso: Apenas usuários autenticados podem visualizar ou modificar tarefas; logout retorna à tela de login
Proteção de dados: Dados armazenados de forma segura usando SharedPreferences e Gson
Uso correto de permissões: Apenas permissões essenciais solicitadas, com explicação de cada uma
Boas práticas de codificação: Estrutura modularizada (activities, adapter, model, utils), código legível, nomes de variáveis significativos e sem dados sensíveis hardcoded
Conformidade LGPD: Coleta mínima de dados, armazenamento seguro e transparência quanto ao uso das informações
🧩 Estrutura do Projeto
com.example.smarttask
│
├── activities
│   ├── MainActivity.kt
│   └── NovaTarefaActivity.kt
│
├── adapter
│   └── TarefaAdapter.kt
│
├── model
│   └── Tarefa.kt
│
├── utils
│   └── Prefs.kt
│
├── res/layout
│   ├── activity_main.xml
│   └── item_tarefa.xml
⚙️ Funcionalidades do Aplicativo
Adicionar tarefas
Listar tarefas dinamicamente com RecyclerView
Editar e excluir tarefas existentes
Marcar tarefas como concluídas
Persistência segura de dados no dispositivo
Interface organizada e intuitiva
🛠️ Tecnologias Utilizadas
Android Studio
Kotlin
RecyclerView
SharedPreferences + Gson
Boas práticas de codificação segura
🚀 Instruções para Execução
Clone o repositório:
git clone https://github.com/seu-usuario/SmartTaskSecure.git
Abra o projeto no Android Studio.
Crie um emulador ou conecte um dispositivo Android:
Exemplo: Pixel 6, Android 14
Compile e execute o aplicativo.
Teste todas as funcionalidades:
Login e logout
Adição, edição e exclusão de tarefas
Marcação de tarefas concluídas
Persistência de dados localmente
