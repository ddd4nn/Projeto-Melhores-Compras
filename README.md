# Projeto-Melhores-Compras
--------------------------
Este projeto foi desenvolvido como trabalho para a Faculdade FIAP, com o objetivo de criar um banco de dados para a empresa Melhores Compras utilizando o SGBD Oracle e seguindo todas as Regras de negocio estabelecidas.

Descrição do projeto

O projeto consistiu em criar um modelo lógico, relacional e físico para o banco de dados, seguindo as regras de negócio estabelecidas pela empresa. Foram utilizadas sequences, chaves estrangeiras e constraints para garantir a integridade dos dados e manter a consistência do banco.

O script DDL foi criado a partir do modelo físico e rodado no banco de dados Oracle sem problemas, resultando na criação das tabelas e relacionamentos entre elas.
Tecnologias utilizadas

    Oracle Database
    SQL
    Modelo lógico e relacional
    Sequences
    Chaves estrangeiras
    Constraints
    
ESTUDO DE CASO: SGV (SISTEMA DE GERENCIAMENTO DE VÍDEOS)
----------------------------------------------------------------
A empresa Melhores Compras precisa ter, em muito breve, um gerenciamento dos vídeos dos produtos disponíveis em sua poderosa plataforma de e-commerce.

Para isso, ela contratou seu grupo, para traduzir as informações necessárias oriundas das regras de negócio e implementá-las em um banco de dados do tipo relacional. A seguir, temos informações relevantes sobre essa nova solução, declaradas pelos PO’s (Product Owner) do projeto:

A empresa Melhores Compras comercializa milhares de produtos na plataforma de e-commerce, relacionados às mais variadas categorias, como: Artesanato; Áudio; Brinquedos; Celular e Smartphone; Colchões; Esporte e Lazer; Ferramentas; Games; Informática; Livros; Pet Shop; TV; Utilidades Domésticas entre outras.

Os clientes, em sua grande maioria, são pessoas físicas, mas também ocorre de vendas serem feitas para pessoas jurídicas. Uma regra muito importante é que não comercializamos produtos no atacado.

Dados que precisam ser armazenados:
----------------------------------------
    Cliente: são as pessoas físicas ou jurídicas que já possuem login e senha de acesso à plataforma de e-commerce. Atualmente temos mais de 5.000.000 de clientes cadastrados no país, sendo que 95% deles são pessoas físicas.
    Produto: são os objetos comercializados e disponíveis na plataforma. Para que ele esteja disponível, é necessário que seu status esteja com a sigla “A” de ativo, pois existem situações em que o produto não deve ser visualizado pelos clientes e que podem estar com outros status como: “I” (inativo) ou “P” (prospecção).

Em relação aos produtos comercializados, precisamos das seguintes informações: código de identificação do produto, descrição do produto (nome comum utilizado durante a comercialização do produto), descrição completa do produto (detalhamento do produto comercializado, utilizado internamente pela empresa), código de barras do produto padrão EAN13, preço unitário (preço atual do produto) e status do produto.

    Vídeo do produto: são os vídeos disponibilizados pelas áreas de negócio e que devem estar associados aos produtos. Um produto pode ter vários vídeos e um vídeo possui status de “A” (ativo) e “I” (inativo).  É muito importante saber a data que o vídeo foi cadastrado na plataforma e somente os vídeos com status ativo estão disponíveis para serem exibidos na plataforma. Vídeos com status inativo ou em prospecção compõem o restante desses dados.
    Categoria do produto: é a classificação do produto dentro da plataforma de e-commerce. Categorizar produtos é uma forma de deixar o e-commerce organizado. Assim, quando o cliente acessa o site em busca de um produto, tem sua vida facilitada pela categoria, além de permitir novas oportunidades de compra a partir da busca feita. Sendo assim, a categorização é um fator de conversão em vendas e também ajuda no ranqueamento do site nos mecanismos de buscas na internet.

As seguintes informações são necessárias: código da categoria, descrição da categoria, status “A” (ativo) e “I” (inativo), data de início e data de término. Somente as categorias ativas são exibidas na plataforma para serem visualizadas.

    Visualização do vídeo: será necessário, a cada visualização feita pelo usuário, armazenar as seguintes informações: Data e hora da visita feita pelo internauta, usuário logado (caso esteja logado como cliente). Caso o usuário seja anônimo, assumir esse conteúdo como valor nulo.


Como executar o projeto
-----------------------------
Para executar o projeto, basta importar o script DDL no Oracle Database e executá-lo para criar o banco de dados. Após isso, o banco de dados estará pronto para receber os dados da empresa Melhores Compras.
Contribuição

Este projeto foi desenvolvido como trabalho acadêmico e não está mais em desenvolvimento. No entanto, sinta-se à vontade para clonar este repositório e utilizá-lo como referência para projetos futuros. Se você encontrar algum erro ou tiver alguma sugestão de melhoria, sinta-se à vontade para abrir uma issue neste repositório.
