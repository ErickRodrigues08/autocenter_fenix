# Autocenter Fenix (Sistema Web + Painel Admin)

Sistema web para apresentação do “Autocenter Fenix” com **painel administrativo** para gerenciar conteúdo (Banners, Serviços, Trabalhos, Equipe, Página Sobre e Configurações do site). O projeto é feito em **PHP** e utiliza **MySQL** para armazenamento de configurações e conteúdo.

---

## Funcionalidades

### 1) Tela de Login (Acesso ao Painel)
- Login por **email** e **senha**
- Envio via `POST`
- Direcionamento para o painel quando as credenciais estão corretas
- Arquivos relacionados:
  - `sistema/index.php` (form de login)
  - `sistema/autenticar.php` (validação)
  - `sistema/conexao.php` (carrega credenciais do sistema e configurações)

---

### 2) Painel Administrativo (CRUD de Conteúdo)
Ao entrar, o admin consegue gerenciar as áreas abaixo:

#### 2.1) Configurações do Site
- Editar informações base:
  - **Nome do site**
  - **Email**
  - **Senha do site (do login)**
  - **Telefone**
  - **Endereço**
  - **Redes sociais**: Instagram, Twitter, Facebook, Linkedin, Youtube
  - **Cor template (hex)**
  - **Texto do rodapé**
  - **Título e Subtítulo de Contato**
- Upload:
  - **Logo** (PNG)
  - **Ícone** (PNG)
- Arquivo principal:
  - `sistema/painel/index.php`
- Salvamento via AJAX:
  - `sistema/painel/scripts/salvar-config.php`

---

#### 2.2) Banner
- Criar, listar e excluir banners
- Campos comuns do banner (modal):
  - **Título**
  - **Subtítulo**
  - **Imagem** (aprox. 2000x900)
- Arquivos principais:
  - `sistema/painel/banner.php`
  - `sistema/painel/banner/listar.php`
  - `sistema/painel/banner/salvar.php`
  - `sistema/painel/banner/excluir.php`

---

#### 2.3) Serviços
- Editar título e subtítulo dos serviços
- CRUD de serviços:
  - **Título**
  - **Descrição** (editor nicEdit)
  - **Vídeo** (URL incorporável)
  - **Tipo de exibição**: **Imagem** ou **Vídeo**
  - **Imagem** (500x500)
- Arquivos principais:
  - `sistema/painel/servicos.php`
  - `sistema/painel/servicos/listar.php`
  - `sistema/painel/servicos/salvar.php`
  - `sistema/painel/servicos/excluir.php`

---

#### 2.4) Trabalhos
- Editar título e subtítulo dos trabalhos
- CRUD de trabalhos:
  - **Título**
  - **Descrição** (editor nicEdit)
  - **Vídeo** (URL incorporável)
  - **Tipo de exibição**: **Imagem** ou **Vídeo**
  - **Link externo** (opcional)
  - **Imagem** (500x500 quadrada)
- Arquivos principais:
  - `sistema/painel/trabalhos.php`
  - `sistema/painel/trabalhos/listar.php`
  - `sistema/painel/trabalhos/salvar.php`
  - `sistema/painel/trabalhos/excluir.php`

---

#### 2.5) Equipe
- Editar título e subtítulo da equipe
- CRUD de integrantes:
  - **Nome**
  - **Cargo**
  - **Imagem** (500x500 quadrada)
- Arquivos principais:
  - `sistema/painel/equipe.php`
  - `sistema/painel/equipe/listar.php`
  - `sistema/painel/equipe/salvar.php`
  - `sistema/painel/equipe/excluir.php`

---

#### 2.6) Sobre
- Conteúdo da página “Sobre” (título, subtítulo, descrição, imagem e opção de exibir)
- Arquivos relacionados:
  - `sistema/painel/sobre.php`
- Base do “Sobre” é inicializada em:
  - `sistema/conexao.php` (quando a tabela `sobre` está vazia)

---

### 3) Logout
- Encerra a sessão e retorna para a tela de login
- Arquivo:
  - `sistema/painel/logout.php`

---

## Credenciais de Login

### Padrão (quando a tabela `config` está vazia)
No `sistema/conexao.php`:
- **Email**: `admin@gmail.com`
- **Senha**: `123`

> Se a tabela `config` já tiver registros, as credenciais usadas serão as salvas no banco.

---

## Tecnologias Utilizadas
- PHP
- MySQL (PDO)
- Bootstrap 5
- jQuery
- DataTables
- nicEdit (editor de texto para descrições)

---

## Estrutura de Pastas (principais)
- `index.php` (site público / base do projeto)
- `sistema/`
  - `index.php` (login)
  - `autenticar.php` (validação)
  - `conexao.php` (PDO + config + seeds)
  - `painel/` (admin)
- `sistema/painel/`
  - `scripts/` (salvamentos via AJAX)
  - `banner/`, `servicos/`, `trabalhos/`, `equipe/` (CRUD)
- `contactform/` (form de contato público)

---

## Requisitos para Rodar Localmente
1. Servidor com PHP habilitado (ex.: Apache/Nginx + PHP)
2. MySQL rodando
3. Banco criado com o nome **`autocenter_fenix`**
4. Ajustar credenciais do banco no:
   - `sistema/conexao.php`
   (variáveis: `$usuario`, `$senha`, `$banco`, `$servidor`)

---

## Observações de Segurança (importante)
- O login atual compara email/senha com valores fixos/da tabela `config`.
- As senhas estão no código como exemplo e/ou em `config` sem hashing no trecho analisado.
- Para produção, recomenda-se:
  - usar hashing (bcrypt/argon2)
  - evitar credenciais hardcoded
  - proteger melhor rotas e validar uploads/inputs

---

## Como Usar
1. Acesse `sistema/index.php`
2. Faça login com o email e senha
3. Use o menu do painel para gerenciar:
   - Configurações
   - Banner
   - Serviços
   - Trabalhos
   - Equipe
   - Sobre
4. Use Uploads de imagem e clique em **Salvar**

