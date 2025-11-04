# 🍴 Livro de Receitas "Forkável"
### Autora: Thais Gomes

## 📖 Descrição
Plataforma social de receitas inspirada no GitHub, onde usuários podem **postar**, **favoritar** e **forkar** receitas — criando versões derivadas que mantêm referência à original.

---

## 👥 Perfis
- **Chefe (Usuário):** cria, edita, favorita e forka receitas.  
- **Administrador:** gerencia usuários e conteúdo.

---

## ⚙️ Lógica de Negócio
1. **Usuário A** posta a receita `ID 10`.  
2. **Usuário B** pode:
   - **Favoritar** a receita (ManyToMany).  
   - **Forkar** a receita, criando uma nova (`ID 11`, `forked_from_id: 10`).  
3. **Usuário C** pode forkar a receita de B (`ID 12`, `forked_from_id: 11`).  
4. O sistema exibe a linhagem:  
   > “Versão de C, derivada da receita de B, que foi derivada da receita de A.”

---

## 📋 Requisitos Funcionais
| Código | Descrição |
|:-------|:-----------|
| **RF-01** | Postar receita original |
| **RF-02** | Forkar receita existente |
| **RF-03** | Forkar fork (cadeia de derivação) |
| **RF-04** | Favoritar receitas (ManyToMany) |

---

## ⚡ Requisitos Não Funcionais
| Código | Descrição |
|:--------|:-----------|
| **RNF-01** | Otimizar exibição da árvore de forks (Recursive CTEs). |
| **RNF-02** | Permitir upload de fotos das receitas. |

---

## 🧩 Estrutura Simplificada
**Usuário**
- id, nome, email, senha  
- favoritos (N:N com Receita)

**Receita**
- id, título, descrição, autor_id  
- forked_from_id (auto-relacionamento)  
- foto (upload)

---

## 🧠 Tecnologias Sugeridas
- **Backend:** Node.js (Express) ou Django REST  
- **Banco:** PostgreSQL (CTEs recursivas)  
- **Frontend:** React ou Vue  
- **Upload:** Cloudinary / S3  
- **Auth:** JWT

---

## 🌳 Exemplo de Fork
```json
{
  "id": 11,
  "titulo": "Bolo de Cenoura (versão B)",
  "forked_from_id": 10,
  "autor_id": 2
}
