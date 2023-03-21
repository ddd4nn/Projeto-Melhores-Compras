# Projeto-Melhores-Compras

Este projeto foi desenvolvido como trabalho para a Faculdade FIAP, com o objetivo de criar um banco de dados para a empresa Melhores Compras utilizando o SGBD Oracle e seguindo todas as Regras de negocio estabelecidas.

Descrição do projeto

O projeto consistiu em criar um modelo lógico, relacional e físico para o banco de dados, seguindo as regras de negócio estabelecidas pela empresa. Foram utilizadas sequences, chaves estrangeiras e constraints para garantir a integridade dos dados e manter a consistência do banco.

O script DDL foi criado a partir do modelo físico e rodado no banco de dados Oracle sem problemas, resultando na criação das tabelas e relacionamentos entre elas.
Tecnologias utilizadas

    Oracle Database
    SQL
    Modelo lógico e relacional
    Sequences
    Chaves estrangeiras e Constraints
    Oracle SQL Developer Data Modeler
    
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
	

Descrição da Regra de Negócio (RN)
----------------------------------------------
**RN01**
	

Um produto pode ter nenhum ou vários vídeos associados e cada vídeo somente pode ser exibido caso seu status esteja em “A” (ativo). O status do vídeo pode receber apenas os seguintes conteúdos: A(tivo) ou I(nativo). Para essa coluna status do produto, crie uma restrição do tipo check constraint, permitindo apenas o conteúdo A ou I.

**RN02**
	

O código de identificação do produto deve ser um número sequencial para ser utilizado como SEQUENCE ou IDENTITY e crescente, de acordo com novos produtos que forem sendo cadastrados.

**RN03**
	

A descrição normal do produto, sua descrição completa, e o preço unitário são obrigatórios. Já o código de barras padrão EAN13 ou correspondente deve ser opcional. A descrição normal do produto deve ser única e a sugestão aqui é criar uma constraint do tipo UNIQUE para essa coluna.

**RN04**
	

Uma categoria de produto pode estar associada a nenhum ou a vários produtos e um produto somente pode estar associado a uma categoria.

**RN05**
	

O código da categoria deve ser um número sequencial para ser utilizado como SEQUENCE ou IDENTITY e crescente, de acordo com novas categorias que forem sendo cadastradas.

**RN06**
	

A descrição da categoria, o status e a data de início devem ter conteúdos obrigatoriamente. Já a data de término deve ser opcional, determinando que a categoria está com status “A” (ativo) e operante. Data de término preenchida identifica uma categoria desativada. A descrição da categoria do produto deve ser única e a sugestão aqui é criar uma constraint do tipo UNIQUE para essa coluna.

**RN07**
	

Existe a necessidade de se armazenar a data, hora, minutos e segundos da visualização do vídeo. Sendo assim, um vídeo pode ter nenhuma ou várias visualizações e uma visualização pertence a um único vídeo. Vídeos que estão inativos não podem ser visualizados.

**RN08**
	

Se o usuário estiver conectado (logado como cliente) é necessário armazenar essa informação. Caso seja um usuário anônimo (não tem login na plataforma), não é necessário armazenar informação.

**RN09**
	

A data e hora da visualização são informações obrigatórias, bem como o código do produto visualizado.

**RN10**
	

Cada vídeo deve ser classificado. A seguir temos alguns exemplos dessas classificações: Vídeo de instalação do produto; Uso no cotidiano; Comercial com personalidade; entre outros. Existem centenas de tipos de vídeos, sendo assim, sugerimos fortemente uma Entidade aqui.

**RN11**
	

Somente o usuário logado (cliente) pode abrir nenhum ou vários chamados de Dúvidas e Sugestões e cada chamado desses deve ser associado a um único cliente.

**RN12**
	

Os chamados de dúvidas e sugestões devem conter uma chave única, do tipo numérica com tamanho máximo de 10 números e que possa ser utilizada como SEQUENCE ou IDENTITY.

**RN13**
	

Os chamados de dúvidas e sugestões devem conter uma data e hora de abertura do chamado e é uma informação obrigatória. Já a data e hora de atendimento do chamado devem ser opcionais, ou seja, preenchida somente quando um funcionário da Melhores Compras atender.

**RN14**
	

Todo chamado tem que ter o código do funcionário associado em algum momento, pois é a partir dele que sabemos quem está realizando o atendimento. Nesse nosso projeto, vamos assumir que o chamado deve ser associado somente a um funcionário e um funcionário pode atender nenhum ou vários chamados.

**RN15**
	

Todo chamado tem um status, que permite saber em que situação ele se encontra. Os principais status são: “A” (aberto), o primeiro status criado no início; “E” (em atendimento); “C” (cancelado)”; “F” (fechado com sucesso); “X” (fechado com insatisfação do cliente), conforme for evoluindo o atendimento. Sendo assim esse status é informação obrigatória.

**RN16**
	

Todo chamado deve ter o tempo total de atendimento computado desde a abertura até a conclusão dele. A unidade de medida é horas, ou seja, em quantas horas o chamado foi concluído desde a sua abertura.

**RN17**
	

Todo chamado dever ter um índice de satisfação, computado como um valor simples de 1 a 10, onde 1 refere-se ao cliente menos satisfeito e 10 o cliente mais satisfeito. Esse índice de satisfação é opcional e informado pelo cliente ao final do atendimento.

**RN18**
	

Todo chamado deve ser classificado em 2 tipos: Tipo 1: Sugestão e Tipo 2: Reclamação. Essa informação é obrigatória.

**RN19**
	

Todo chamado deve ser associado a um produto. Então um produto pode possuir nenhum ou vários chamados e um chamado pertence a um único produto.

**RN20**
	

Todo chamado pode receber um texto escrito pelo cliente internauta contendo no máximo 4.000 caracteres e seu conteúdo é obrigatório. Essa preciosa informação será analisada posteriormente pelo funcionário da Melhores Compras.

**RN21**
	

As principais informações do funcionário que trabalha na Melhores  Compras são: código do funcionário (PK); nome do funcionário, CPF, data de nascimento, telefone com DDD, e-mail, cargo e nome do departamento em que trabalha. Todas essas informações são obrigatórias. O número do CPF do funcionário deve ser único e a sugestão aqui é criar uma constraint do tipo UNIQUE para essa coluna.

**RN22**
	

Para os clientes pessoas físicas que abrem chamado, as principais informações são: código do cliente (PK); nome do cliente (conteúdo obrigatório), quantidade de estrelas (conteúdo opcional), status do cliente (ativo ou inativo) com conteúdo obrigatório, número do telefone (conteúdo opcional), login e senha (conteúdo obrigatório). Não podemos esquecer também o número do CPF (conteúdo obrigatório), data de nascimento (conteúdo obrigatório), sexo biológico (conteúdo obrigatório) e gênero de nascimento (conteúdo opcional).

**RN23**
	

Para os clientes pessoas jurídicas que abrem chamado, as principais informações são: código do cliente (PK); nome do cliente (conteúdo obrigatório), quantidade de estrelas (conteúdo opcional), status do cliente (ativo ou inativo) com conteúdo obrigatório, número do telefone (conteúdo opcional), login e senha (conteúdo obrigatório). Não podemos esquecer também a data de fundação (conteúdo opcional), o número no CNPJ (conteúdo opcional) e o número de inscrição estadual (conteúdo opcional).

**RN24**
	

Regra de negócio a ser definida pelo grupo. Escreva uma regra de negócio adicional e única de seu grupo que resulte em criar uma nova Entidade (tabela no modelo físico) que se relacione com qualquer outra Entidade já definida no seu projeto de banco de dados e que tenha no mínimo 3 atributos (sem contar a chave PK). 
**(Foi disponibilizado um arquivo contendo a regra de negócio 24 neste repositório)**

Boas práticas para a criação das estruturas de dados, tabelas e relacionamentos:
------------------------------------------------------------------------
Agora que temos as principais regras de negócio definidas, seu desafio será construir o modelo de banco de dados relacional lógico e físico, que deve atender a todas as regras listadas acima, utilizando as boas práticas recomendadas, tais como:

    Nome significativo de cada Entidade (tabela) com a sigla de seu projeto.
    Nome significativo dos atributos, com tipo de dados e tamanho adequado.
    Obrigatoriedade e opcionalidade para cada atributo.
    Comentários significativos em cada Entidade (tabela) e atributo, inclusive informando a máscara de dados e formato de armazenamento (maiúsculo, minúsculo ou InitCap)
    Relacionamentos entre as Entidades


Como executar o projeto
-----------------------------
Para executar o projeto, basta importar o script DDL no Oracle Database e executá-lo para criar o banco de dados. Após isso, o banco de dados estará pronto para receber os dados da empresa Melhores Compras.
Contribuição

Este projeto foi desenvolvido como trabalho acadêmico e não está mais em desenvolvimento. No entanto, sinta-se à vontade para clonar este repositório e utilizá-lo como referência para projetos futuros. Se você encontrar algum erro ou tiver alguma sugestão de melhoria, sinta-se à vontade para abrir uma issue neste repositório.

Créditos e Agradecimentos
------------------------------
Gostaria de expressar meus sinceros agradecimentos aos meus companheiros de grupo Felipe José Rodrigues dos Reis, Gabriela Moreno Rocha dos Santos, Marcella Arícia de Jesus Dias Melo de Araujo e Raphaela Longo Marcondes Dias pelo excelente trabalho em equipe durante o projeto "Melhores Compras".

Cada um de vocês contribuiu com habilidades únicas e conhecimentos valiosos que foram essenciais para o sucesso do projeto. Desde a criação do modelo lógico até a implementação do script DDL, vocês foram comprometidos e trabalharam duro para garantir que cada etapa fosse realizada com precisão e eficiência.

Agradeço pela paciência, pela colaboração e pelo esforço em tornar o projeto um sucesso. O resultado final foi excelente e tenho certeza que isso só foi possível graças à dedicação de cada um de vocês.

Mais uma vez, obrigado pelo trabalho em equipe e pela realização de um projeto tão importante e significativo. Vocês são um exemplo de profissionalismo e excelência no trabalho em grupo.
