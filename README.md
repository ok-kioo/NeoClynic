# 🚀 NeoClynic

> Sistema completo e moderno para a gestão de clínicas, integrando agendamentos e registros de pacientes com Node.js, React e Prisma.

![Preview do projeto](./frontend/public/logo-neoclinic.png)

## 📋 Sobre o projeto

O **NeoClynic** é uma plataforma desenvolvida para facilitar a administração de clínicas de saúde. Ele unifica o gerenciamento de registros e a marcação de consultas através de uma interface interativa baseada em calendário, conectada a uma API tipada e segura.

### De forma simples

* **O que o projeto faz:** Centraliza dados de pacientes, prontuários e agendamentos em um único painel.
* **Para quem ele foi desenvolvido:** Médicos, dentistas, recepcionistas e administradores de clínicas médicas.
* **Qual problema resolve:** A desorganização das agendas em papel ou planilhas desconexas, a perda de histórico dos pacientes e a complexidade na configuração inicial de um sistema clínico.

### 🎯 Objetivos

* Garantir uma experiência de usuário (UX) ágil na marcação de consultas;
* Prover uma API REST escalonável com validação forte de tipagem e ORM moderno (Prisma);
* Facilitar a vida do desenvolvedor e da equipe de infraestrutura, entregando o sistema de forma "plug and play" através de containers Docker.

---

## ✨ Funcionalidades

* ✅ Sistema de agendamentos interativo (FullCalendar)
* ✅ Gerenciamento de perfis de pacientes e históricos
* ✅ Autenticação de usuários via JWT
* ✅ Interface responsiva com Styled Components e React Router
* ✅ Orquestração unificada de serviços (DB, API e Web) com Docker Compose
* ✅ Análise de qualidade do código e testes via CI/CD (SonarCloud e Jest)

---

## 🖥️ Demonstração

### Login

<a href="https://ibb.co/Tq2GHQYT"><img src="https://i.ibb.co/jZfYLCb5/Captura-de-tela-de-2026-08-16-03-37-14.png" alt="Captura-de-tela-de-2026-08-16-03-37-14" border="0"></a>

---

## 🛠️ Tecnologias utilizadas

### Front-end

* [React 18/19](https://react.dev/)
* [Vite](https://vitejs.dev/)
* [Styled Components](https://styled-components.com/)
* [FullCalendar](https://fullcalendar.io/)
* [React Router DOM](https://reactrouter.com/)

### Back-end

* [Node.js](https://nodejs.org/) & [Express](https://expressjs.com/)
* [TypeScript](https://www.typescriptlang.org/)
* [Prisma ORM](https://www.prisma.io/)
* [Jest](https://jestjs.io/) (Testes Unitários)

### Banco de dados & Infra

* [PostgreSQL 17](https://www.postgresql.org/)
* [Docker](https://www.docker.com/) & Docker Compose
* [GitHub Actions](https://github.com/features/actions) & SonarCloud

---

## 📦 Pré-requisitos

Para rodar a aplicação em seu ambiente, recomendamos fortemente o uso do Docker.

Certifique-se de ter instalado:

* [Git](https://git-scm.com/)
* [Docker](https://www.docker.com/) e **Docker Compose**

Verifique a instalação:

```bash
docker --version
docker compose version
```

---

## 🚀 Instalação (Via Docker Compose)

A melhor maneira de rodar a stack completa (Banco de Dados, Backend e Frontend) é através do `docker-compose-dev.yml`.

### 1. Clone o repositório

```bash
git clone https://github.com/usuario/NeoClynic.git
cd NeoClynic
```

### 2. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto com as chaves necessárias. Utilize o arquivo de exemplo caso ele exista:

```bash
cp .env.example .env
```

Exemplo das variáveis utilizadas pelo `docker-compose-dev.yml`:

```env
DATABASE_URL=seu-url

JWT_SECRET=sua-chave-secreta

FRONTEND_URL='http://localhost:5173'
VITE_API_BASE_URL='http://localhost:8050'

INIT_ADMIN_EMAIL=seu@email.com
INIT_ADMIN_PASSWORD=sua-senha

SMTP_CLIENT_ID=smtp-id
SMTP_CLIENT_SECRET=smtp-client-secret
SMTP_REFRESH_TOKEN=smtp-refresh-token
SMTP_ACCESS_TOKEN=smtp-token
SMTP_USER=seu@email.com
```

### 3. Inicie os containers

```bash
docker compose -f docker-compose-dev.yml up -d --build
```

Isso fará o build do Frontend e do Backend e subirá o PostgreSQL 17.4.

### 4. Execute as migrations

Se for a primeira vez rodando o projeto, aplique as tabelas no banco executando o Prisma dentro do container do backend:

```bash
docker compose -f docker-compose-dev.yml exec backend npx prisma migrate dev
```

O projeto estará disponível em:

* **Front-end:** http://localhost:5173
* **Back-end:** http://localhost:8050

---

## 📖 Como usar

### Acessando o Sistema Web

Abra:

```text
http://localhost:5173
```

Utilize as credenciais de `INIT_ADMIN_EMAIL` e `INIT_ADMIN_PASSWORD` definidas no `.env` para o primeiro acesso.

No painel, você poderá:

* Navegar até o calendário;
* Gerenciar consultas;
* Visualizar o cadastro dos pacientes;
* Consultar históricos e registros.

---

## 🧪 Testes

Os testes da API são executados via Jest.

Para testar localmente, sem Docker:

```bash
cd backend
npm install
npm test
```

O pipeline automatizado no arquivo `.github/workflows/tests.yml` verifica a estabilidade a cada novo Pull Request.

---

## 📁 Estrutura do projeto

```text
NeoClynic/
├── .github/workflows/        # Rotinas de CI/CD (Testes e SonarCloud)
├── backend/                  # API Node.js/Express
│   ├── prisma/               # Schemas do BD, migrations e seeds
│   ├── src/                  # Controllers, Models, Infraestrutura
│   ├── Dockerfile
│   ├── app.ts
│   └── package.json
├── frontend/                 # Interface React + Vite
│   ├── public/
│   ├── src/                  # Componentes, Páginas, Styled Components
│   ├── Dockerfile
│   └── package.json
├── docker-compose-dev.yml    # Orquestração do ambiente de desenvolvimento
├── docker-compose-prod.yml   # Orquestração do ambiente de produção
└── CONTRIBUTING.md           # Guia de contribuição da equipe
```

---

## 📄 Licença

Este projeto está licenciado sob a **MIT License**.

Consulte o arquivo `LICENSE` para mais detalhes.

---

## 🤝 Contribuindo

Contribuições são bem-vindas!

Antes de contribuir:

* Siga o padrão descrito em `CONTRIBUTING.md`;
* Utilize **Conventional Commits**;
* Concorde com o licenciamento MIT para suas contribuições.

---

## ⭐ Apoie o projeto

Se este projeto foi útil para você:

* ⭐ Dê uma estrela no repositório.
* 🐛 Reporte problemas.
* 💡 Sugira melhorias.
* 🤝 Envie contribuições.
* 📢 Compartilhe o projeto.

**Obrigado pelo apoio! ❤️**

---

## 📞 Suporte

Ao abrir uma Issue, informe:

* Descrição do problema;
* Passos para reproduzir;
* Comportamento esperado;
* Comportamento obtido;
* Logs de erro;
* Sistema operacional;
* Versão do projeto.

---

## 📚 Documentação

A documentação do projeto está organizada em:

* `README.md` — documentação principal;
* `CONTRIBUTING.md` — guia de contribuição;
* `LICENSE` — licença do projeto.

---

## 👥 Equipe

<a href="https://github.com/ok-kioo">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/f7da043e-005d-4c5c-a4ab-75fdec3ed861" />
</a>

<a href="https://github.com/lazarosantos1011">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/53da9ab6-aad9-413c-8872-3dbd645eafd0" />

</a>

<a href="https://github.com/DeyvidMariano">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/a0954540-ea74-4e46-9684-da027d63b9af" />
</a>

<a href="https://github.com/KaelanyS">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/27dfcb8e-8bba-4980-af4a-abca98aedaeb" />

</a>

<a href="https://github.com/GabrielSLima01">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/b03d34af-22c0-4611-a0e4-de37adf339a4" />
</a>

<a href="https://github.com/Marcelo-Spacca">
  <img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/bc56fabc-df26-438a-a0cc-c6244ebae2c7" />


</a>
