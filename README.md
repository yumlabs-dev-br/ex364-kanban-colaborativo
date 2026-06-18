# Quadro Kanban Colaborativo

API REST de um quadro Kanban com colunas, cartões ordenáveis e atribuição de membros.

> 📦 **Template de trabalho em grupo da WebForge.** Clique em **Use this template** (botão verde acima) para criar o repositório do seu grupo.

## 🚀 Como rodar

```bash
npm install
npm start        # inicia em http://localhost:3005
```

O projeto já sobe com uma rota raiz `GET /`. Todo o resto é com o grupo.

## 📋 Requisitos

- **Auth/Membros** — login JWT; `POST /quadros/:id/membros` (só o dono) e listagem de membros.
- **Quadros/Colunas** — criar quadro (o criador vira dono); CRUD de colunas com reordenação.
- **Cartões** — criar/editar/remover; `PATCH /cartoes/:id/mover` (mover entre colunas + reordenar); `GET /quadros/:id` com colunas e cartões ordenados.
- **Atividades** — `GET /quadros/:id/atividades` com o histórico de ações.

> Persistam os dados (arquivo JSON ou SQLite) — os testes podem reiniciar o servidor entre etapas.

## ✅ O que os testes de correção validam

Os testes automáticos sobem o **seu** servidor e fazem requisições HTTP reais contra a API. Eles verificam **comportamento** (status HTTP e corpo das respostas), não a estrutura interna do código — organizem os arquivos como preferirem. Para ser aprovado, a API precisa:

- [ ] `GET /` responde **200**.
- [ ] `POST /quadros` cria o quadro e define o criador como dono.
- [ ] Quem **não é membro** do quadro recebe **403** ao acessá-lo.
- [ ] `POST /colunas/:id/cartoes` cria um cartão na coluna.
- [ ] `PATCH /cartoes/:id/mover` move o cartão para outra coluna mantendo a **ordem** consistente.
- [ ] `GET /quadros/:id` retorna as colunas com os cartões na ordem correta.
- [ ] Cada movimentação gera um registro em `GET /quadros/:id/atividades`.

## 👥 Trabalho em equipe (obrigatório)

Este é um ambiente o mais próximo possível do mercado:

- O repositório deve pertencer a **um** dos membros do grupo. Os **demais membros entram como colaboradores** em `Settings → Collaborators → Add people`.
- Cada membro trabalha em sua **própria branch** e abre **Pull Request** para a `main`, pedindo revisão de outro colega.
- A WebForge mede as **contribuições individuais** de cada membro (commits, linhas adicionadas e removidas) direto do histórico do GitHub. Distribuam bem o trabalho.

## 🧱 Stack

- Node.js + Express (CommonJS)
