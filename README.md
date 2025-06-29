# SICREDI 2025 - Sistema de Gestão Centralizada

## Visão Geral
O SICREDI 2025 é um sistema web desenvolvido em Flask para gestão centralizada de ambientes, documentos, equipamentos, reservas e usuários (gestores e analistas) de uma instituição. O sistema oferece autenticação, controle de acesso por perfil, gerenciamento de ambientes físicos, controle de equipamentos, reservas, avisos internos, além de módulos para documentação e relatórios.

---

## Funcionalidades Principais
- **Autenticação de Usuários**: Login seguro com senha criptografada.
- **Gestão de Ambientes**: Cadastro, consulta e gerenciamento de ambientes/setores, com controle de acesso para analistas e gestores.
- **Gestão de Equipamentos**: Controle de equipamentos imobilizados e mobilizados, incluindo reservas e histórico de uso.
- **Gestão de Documentos**: Upload, aprovação, reprovação e histórico de documentos por setor e usuário.
- **Gestão de Avisos Internos**: Envio e leitura de avisos para setores e usuários específicos.
- **Gestão de Analistas**: Cadastro, edição e exclusão de analistas vinculados a setores.
- **Reservas de Equipamentos**: Sistema de reservas com aprovação e controle de status.
- **Relatórios e Dashboards**: Visualização de dados gerenciais (dependendo do perfil).

---

## Estrutura de Pastas
```
SICREDI_2025-main/
├── app/
│   ├── db/                  # Scripts de banco de dados e conexão
│   │   ├── execute_db/      # Scripts de criação/inicialização de tabelas
│   │   ├── db_connection.py # Função para conectar ao SQLite
│   ├── main/                # Blueprints principais (gestor, analista, etc.)
│   ├── routes/              # Rotas Flask organizadas por módulo
│   ├── utils/               # Utilitários e helpers
├── static/                  # Arquivos estáticos (CSS, JS, imagens)
│   ├── css/
│   ├── js/
│   ├── img/
├── templates/               # Templates HTML Jinja2
│   ├── principal/
│   ├── gestao_ambientes/
│   ├── gestao_equipamentos/
│   ├── gestao_documentos/
│   ├── gestao_avisos/
│   ├── gerenciar_analistas/
├── instance/
│   └── sicredi.db           # Banco de dados SQLite
├── requirements.txt         # Dependências do projeto
├── run.py                   # Ponto de entrada da aplicação Flask
├── README.md                # Este arquivo
```

---

## Instalação e Execução

### Pré-requisitos
- Python 3.10+
- SQLite3

### Passos para rodar no Linux:
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python run.py
```

### Passos para rodar no Windows:
```bat
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python run.py
```

O servidor Flask estará disponível em `http://127.0.0.1:5000/`.

---

## Inicialização do Banco de Dados
A primeira execução do sistema cria automaticamente as tabelas necessárias no banco SQLite (`instance/sicredi.db`). Caso precise resetar ou criar tabelas manualmente, utilize os scripts em `app/db/execute_db/`.

---

## Principais Blueprints e Módulos
- `app/main/gestao_ambientes/gestor.py` e `analista.py`: Gestão de ambientes para gestores e analistas
- `app/main/gestao_equipamentos/gestor.py`, `gestor_imobilizados.py`, `analista.py`: Equipamentos
- `app/main/gestao_documentos/gestor.py`, `analista.py`: Documentos
- `app/main/gestao_avisos/gestor.py`, `analista.py`: Avisos internos
- `app/main/gerenciar_analistas/analistas.py`: Cadastro de analistas
- `app/routes/principal/principal.py`: Rotas principais e autenticação

---

## Usuários de Teste (Padrão)
- **Admin**: `admin@gmail.com` / senha: `12345` (Gestor)
- **Analista**: `analista@gmail.com` / senha: `12345` (Analista)

---

## Dependências
Veja o arquivo `requirements.txt` para todas as dependências. Algumas principais:
- Flask
- Werkzeug
- Flask-Session
- Jinja2
- SQLAlchemy

---

## Observações Importantes
- Os arquivos estáticos (CSS/JS) devem ser referenciados corretamente nos templates, usando `url_for('static', filename='css/...')`.
- O banco de dados é criado automaticamente na pasta `instance/`.
- Para adicionar novos módulos ou funcionalidades, siga o padrão de blueprints e organização já existente.

---

## Contato e Suporte
Para dúvidas, sugestões ou suporte, entre em contato com o desenvolvedor responsável.

---

© SICREDI 2025 - Todos os direitos reservados.
