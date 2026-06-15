SmartTask Secure

Aplicativo Android para gerenciamento de tarefas com foco em segurança e privacidade.

📄 Descrição do Projeto

O SmartTask Secure é um aplicativo Android desenvolvido em Kotlin que permite aos usuários gerenciar tarefas diárias de forma prática e segura. O app combina funcionalidade, boa experiência do usuário e camadas de segurança, garantindo que dados pessoais e profissionais sejam protegidos e tratados de acordo com a LGPD.

Principais objetivos:

Organizar tarefas do dia a dia
Garantir segurança e privacidade dos dados
Seguir boas práticas de desenvolvimento mobile
🔐 Funcionalidades de Segurança
Autenticação do usuário: tela de login local com validação de credenciais.
Controle de acesso: apenas usuários autenticados podem visualizar ou modificar tarefas.
Proteção de dados: armazenamento seguro de tarefas com SharedPreferences e Gson.
Uso correto de permissões: solicita apenas permissões essenciais, respeitando o modelo de runtime do Android.
Boas práticas de codificação segura: código modularizado, organizado por pacotes, com nomes significativos e sem dados sensíveis hardcoded.
Conformidade com a LGPD: coleta mínima de dados, armazenamento seguro e transparência no uso das informações do usuário.
⚙️ Instruções para Execução
Abra o projeto no Android Studio.
Crie um emulador ou conecte um dispositivo Android:
Exemplo: Pixel 6 com Android 14
Compile e execute o aplicativo.
Explore as funcionalidades:
Tela de login
Adição, edição e exclusão de tarefas
Marcação de tarefas concluídas
Lista dinâmica com RecyclerView
Persistência segura dos dados localmente

📂 Estrutura do Projeto
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
🛠️ Tecnologias Utilizadas
Android Studio
Kotlin
RecyclerView
SharedPreferences + Gson
