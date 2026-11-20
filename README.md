Sistema desktop para controlar o empréstimo de livros pessoais: cadastro de livros e de pessoas, registro de empréstimos e devoluções, com aviso de atraso.


ESTRUTURA
main.py                    arquivo principal
config.exemplo.ini         modelo de configuração (sem senha)
sql/criar_tabelas.sql      script que cria o banco e as tabelas
interface/                 camada de interface (telas.glade + handlers GTK)
modelo/                    camada de modelo (entidades e validações)
dados/                     camada de acesso a dados (conexão e DAOs)
Requisitos
Python 3.8+
GTK 3 com PyGObject
Servidor MySQL (local) ou TiDB Cloud Starter
Biblioteca mysql-connector-python
Instalação das dependências (Debian/Ubuntu)
bash
sudo apt install python3-gi gir1.2-gtk-3.0 python3-pip
pip install mysql-connector-python

(Se o pip reclamar de "externally managed environment", use pip install --break-system-packages mysql-connector-python ou crie um venv com --system-site-packages.)





COMO CONFIGURAR
Crie o banco e as tabelas:
bash
mysql -u SEU_USUARIO -p < sql/criar_tabelas.sql
Copie o arquivo de configuração e preencha com seus dados:
bash
cp config.exemplo.ini config.ini

Edite o config.ini (host, porta, usuário, senha e banco). No TiDB Cloud, preencha também ssl_ca.







COMO EXECUTAR
bash
python3 main.py
Funcionalidades
Livros: cadastrar, listar, buscar por título/autor, alterar e excluir.
Pessoas: cadastrar, listar, alterar e excluir.
Empréstimos: emprestar um livro disponível, listar com situação (em dia, atrasado, devolvido) e registrar devolução.

Livros e pessoas com empréstimos registrados não podem ser excluídos.
