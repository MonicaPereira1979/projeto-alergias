# Sistema Inteligente de Gestão de Alergias Alimentares (Flask + PostgreSQL)

Projeto base para o TCC da Monica da Silva Pereira.

## 🚀 Funcionalidades (MVP)
- Autenticação (login/logout) e perfis: coordenador, professor, nutricionista, responsável.
- Cadastro de alunos e alergias (N:N).
- Cadastro de cardápio diário.
- Verificação automática de risco (alerta) quando o cardápio contém ingrediente incompatível com alergias cadastradas.
- Relatório simples de segurança alimentar.
- Boas práticas LGPD: consentimento, controle de acesso, logs básicos, minimização de dados.

## 🧰 Requisitos
- Python 3.10+
- PostgreSQL 13+

## ⚙️ Setup rápido
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
# configure a URI válida no .env
createdb alergias_db  # ou via GUI
flask db-up  # comando utilitário incluso em app.py para criar tabelas
flask run
```

## 🔒 Notas LGPD
- Dados sensíveis (saúde) protegidos por autenticação e perfis.
- Rotas críticas exigem papéis autorizados.
- Consentimento dos responsáveis é registrado no cadastro do aluno.
- Logs mínimos em `logs/app.log` para auditoria.
- Em produção, habilite HTTPS, rotação de logs e política de retenção de dados.

## 🧪 Usuário demo
- Login: admin@example.com
- Senha: admin123
(gerado no primeiro `flask db-up` se não existir)

## 🏗️ Estrutura
```
projeto-alergias/
├── app.py
├── models.py
├── config.py
├── requirements.txt
├── .env.example
├── templates/
├── static/
└── database/
    └── schema.sql
```

## 📦 Deploy rápido (opcional)
- Render/Railway: defina `DATABASE_URL` e `SECRET_KEY` nas variáveis de ambiente; use `gunicorn app:app`.
