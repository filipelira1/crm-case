# CRM compl_t: captura de leads integrada à cobrança, de ponta a ponta

> Estudo de caso de engenharia de software, por **Filipe Lira**. O código é privado; aqui estão **as decisões, os cuidados e o resultado**.

---

## Em uma frase

Um CRM que leva o contato do formulário do site até o cliente ativo e cobrando, sem planilha nem passo manual no meio.

## Meu papel

Modelagem, backend, telas do admin, integrações (pagamento e mensagens) e testes no navegador.

## Desafios de engenharia

| Desafio | Como resolvi |
|---|---|
| **Saber de onde vem cada cliente** | o lead guarda a campanha e a página de entrada desde o primeiro segundo. |
| **Formulário que nunca quebra** | avisos e integrações rodam em fila, depois da gravação; se um serviço externo cair, o visitante não vê erro. |
| **Documentos sensíveis** | anexos criptografados em repouso (AES-256-GCM) com a biblioteca do próprio framework, sem criptografia feita à mão. |
| **Converter sem retrabalho** | um clique cria o cliente, a licença e a assinatura recorrente. |
| **Cobrança que manda no acesso** | webhook do pagamento ativa a licença; inadimplência suspende. Ninguém precisa lembrar de liberar ou bloquear. |
| **Rastreabilidade** | mudanças no funil e nas licenças ficam em auditoria consultável. |

## Bugs reais que o processo pegou

- Um serviço gravava o **valor do pagamento a partir de uma variável inexistente**: todo pagamento ficava sem valor. Achado ao ligar o painel a dados reais.
- Uma tela mostrava **"ativo" para um cliente bloqueado**, porque a API não devolvia os campos de bloqueio. Achado testando clique a clique no navegador.

Os dois viraram regra no checklist, para o mesmo tipo de erro não voltar.

## Resultado

| | |
|---|---|
| Período | janeiro a outubro de 2026 |
| Commits meus em 2026 | 122 |
| Integrações | gateway de pagamento (assinatura e webhook), WhatsApp, fila de avisos |

## Stack

PHP 8.3 · Laravel · Vue · Blade · PostgreSQL · Redis (filas) · Docker · webhooks

**Demonstração e detalhes:** sob pedido, numa conversa.

## Outros cases

[pep-case](https://github.com/filipelira1/pep-case) · [plataforma-case](https://github.com/filipelira1/plataforma-case) · [mermaid-case](https://github.com/filipelira1/mermaid-case) · [pacs-case](https://github.com/filipelira1/pacs-case)

---

*Sou **Filipe Lira**, engenheiro de software em São Paulo (ABC Paulista). [LinkedIn](https://www.linkedin.com/in/filipe-lira-a54217167) · [GitHub](https://github.com/filipelira1)*
