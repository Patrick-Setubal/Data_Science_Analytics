    Documentation = https://www.w3schools.com/mysql/mysql_ref_functions.asp
    
    USE database;
    
    
    SELECT A.CPF, A.Col_2, B.CPF, B.Col_2 AS Col_B_2, B.Contry
      FROM table_a A LEFT JOIN tabel_b B ON A.CPF = B.CPF
      WHERE A.Col_2 > 10 
      AND B.Col_2 BETWEEN 10 AND 30
      AND (B.Contry= 'RJ' OR B.Contry = 'SP');

    
    SELECT DISTINCT = No Duplicated
    SELECT A.CPF, COUNT(*) FROM table_compras A GROUP BY A.CPF ORDER BY A.CPF;
    
    select * from tabela_de_clientes 
	    where bairro in (select distinct bairro from tabela_de_vendedores);

    select X.embalagem, x.preco_maximo from 
    	(select embalagem, max(preco_de_lista) as preco_maximo 
        from tabela_de_produtos	group by embalagem) X 
        WHERE X.PRECO_MAXIMO >=10;

    USE `sucos_vendas`;
    CREATE  OR REPLACE VIEW `VW_MAIORES_EMBALAGENS` AS 
    	select embalagem, max(preco_de_lista) as preco_maximo 
        from tabela_de_produtos group by embalagem;

    select A.nome_do_produto, A.embalagem, A.preco_de_lista, X.preco_maximo
	from tabela_de_produtos A inner join vw_maiores_embalagens X
    on A.embalagem = X.embalagem;

    select 
    	A.nome_do_produto, A.embalagem, A.preco_de_lista,
        round(A.preco_de_lista / X.preco_maximo * 100 , 2 ) as 'PERCENTUAL(%)',
        X.preco_maximo     
    		from tabela_de_produtos A inner join vw_maiores_embalagens X
    		on A.embalagem = X.embalagem;



	select 
 	    NF.CPF, TC.NOME,
	    DATE_FORMAT(NF.DATA_VENDA,'%Y-%m' ) as 'Mes_Ano', 
	    SUM(INF.QUANTIDADE) as 'Quantidade_Vendas',
	    MAX(TC.VOLUME_DE_COMPRA) as 'Quantidade_Limite',   
	    case when (MAX(TC.VOLUME_DE_COMPRA) - SUM(INF.QUANTIDADE)) < 0 then 'Inválida'
	    else 'Válida' end as Status_Venda
			from notas_fiscais NF 
				inner join itens_notas_fiscais INF on NF.numero = INF.numero
	            		inner join tabela_de_clientes TC on TC.CPF = NF.CPF
				group by NF.CPF, TC.NOME, Mes_Ano;



    select 
	Venda_SABOR.Sabor, 
    Venda_SABOR.ANO, 
    Venda_SABOR.Total_Por_Sabor,
    ROUND(Venda_SABOR.Total_Por_Sabor/Venda_Total.Venda_Total,2)*100 AS 'Percentual'
    from (select 
		TP.SABOR, 
		YEAR(NF.DATA_VENDA) as 'Ano', 
		SUM(INF.QUANTIDADE) AS 'Total_Por_Sabor'
		from itens_notas_fiscais INF
		INNER JOIN tabela_de_produtos TP ON INF.CODIGO_DO_PRODUTO = TP.CODIGO_DO_PRODUTO
		INNER JOIN notas_fiscais NF ON INF.NUMERO = NF.NUMERO
		WHERE YEAR(NF.DATA_VENDA) = 2016
		GROUP BY TP.SABOR, Ano) as Venda_SABOR
    INNER JOIN (select 
		YEAR(NF.DATA_VENDA) as 'Ano', 
		SUM(INF.QUANTIDADE) AS 'Venda_Total'
		from itens_notas_fiscais INF
			INNER JOIN tabela_de_produtos TP ON INF.CODIGO_DO_PRODUTO = TP.CODIGO_DO_PRODUTO
			INNER JOIN notas_fiscais NF ON INF.NUMERO = NF.NUMERO
			WHERE YEAR(NF.DATA_VENDA) = 2016
			GROUP BY  Ano) as Venda_Total 
	ON Venda_SABOR.ANO = Venda_Total.ANO
	order by Venda_SABOR.Total_Por_Sabor DESC

    
