# Alterações do Projeto --- Parte 3 --- 20/08/2026

Nesta etapa, o projeto **Catálogo de Produtos** evolui para completar as
operações de **alteração e exclusão**, tanto no Back-end quanto no
Front-end.

As alterações realizadas nesta etapa estão identificadas no código.

------------------------------------------------------------------------

## BACK-END

## 1. produtoController.js

-   Mantidas as funções existentes `listarProdutos` e
    `cadastrarProduto`.
-   Criada a função `alterarProduto`.
-   O ID recebido pela rota é obtido por `req.params.id`.
-   O produto é localizado utilizando `find()`.
-   Adicionado tratamento para produto não encontrado com status `404`.
-   Mantida a validação de nome e preço obrigatórios.
-   Os dados `nome`, `descricao` e `preco` são atualizados no produto
    encontrado.
-   Criada a função `excluirProduto`.
-   O índice do produto é localizado utilizando `findIndex()`.
-   Adicionado tratamento para produto não encontrado.
-   O produto é removido do vetor utilizando `splice()`.
-   `alterarProduto` e `excluirProduto` foram adicionadas ao
    `module.exports`.

## 2. produtoRoutes.js

-   Mantidas as rotas `GET /` e `POST /`.
-   Importadas as funções `alterarProduto` e `excluirProduto`.
-   Adicionada a rota `PUT /:id` para alteração.
-   Adicionada a rota `DELETE /:id` para exclusão.

Com isso, o Back-end passa a trabalhar com as quatro operações
principais do CRUD:

-   **CREATE** → POST
-   **READ** → GET
-   **UPDATE** → PUT
-   **DELETE** → DELETE

------------------------------------------------------------------------

## FRONT-END

## 3. App.jsx

-   Adicionado estado `produtoEmEdicao`.
-   Criada função para selecionar o produto que será editado.
-   Criada função `alterarProduto`.
-   A alteração é enviada ao Back-end utilizando `fetch()` com método
    `PUT`.
-   O ID do produto é enviado pela URL da API.
-   Após a resposta do Back-end, o produto é atualizado no estado
    utilizando `map()`.
-   Criada função `excluirProduto`.
-   A exclusão é enviada ao Back-end utilizando `fetch()` com método
    `DELETE`.
-   Após a exclusão, o produto é removido da lista utilizando
    `filter()`.
-   Ao excluir um produto que estava sendo editado, o estado de edição é
    limpo.
-   `FormProduto` passou a receber os dados e ações relacionadas à
    edição.
-   `ListaProdutos` passou a receber as ações de editar e excluir.

## 4. FormProduto.jsx

-   Adicionada prop `produtoEmEdicao`.
-   Adicionada ação `aoAlterar`.
-   Utilizado `useEffect()` para preencher o formulário quando um
    produto for selecionado para edição.
-   O mesmo formulário passa a funcionar em dois modos: cadastrar e
    alterar.
-   Criada função para limpar o formulário.
-   Criada opção para cancelar a edição.
-   O texto do botão é alterado conforme o modo atual do formulário.
-   Mantidas as validações de nome e preço.

## 5. ListaProdutos.jsx

-   Adicionadas as props `aoEditar` e `aoExcluir`.
-   As ações são repassadas para cada componente `Produto`.
-   Mantidas a busca, a quantidade de resultados e a renderização da
    lista.

## 6. Produto.jsx

-   Adicionadas as props `aoEditar` e `aoExcluir`.
-   Adicionado botão **Editar**.
-   O botão Editar envia o produto selecionado para a função de edição.
-   Adicionado botão **Excluir**.
-   O botão Excluir envia o ID do produto para a função de exclusão.

## 7. style.css

-   Adicionados estilos para os novos botões de ação dos cards.
-   Adicionados estilos relacionados ao modo de edição do formulário.
-   Mantido o tema visual e a responsividade da etapa anterior.

------------------------------------------------------------------------

## Resultado da Parte 3

Ao final desta etapa, o Catálogo de Produtos permite:

-   listar produtos;
-   cadastrar produtos;
-   buscar produtos;
-   validar o formulário;
-   alterar produtos;
-   excluir produtos.

O projeto agora possui um **CRUD completo**, utilizando **React no
Front-end** e **Node.js + Express no Back-end**, ainda com os dados
armazenados em memória.

A persistência dos dados será evoluída nas próximas etapas do projeto.
