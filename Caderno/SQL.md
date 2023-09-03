    USE database;
    
    SELECT A.CPF, A.Col_2, B.CPF, B.Col_2 AS Col_B_2, B.Contry
      FROM table_a A LEFT JOIN tabel_b B ON A.CPF = B.CPF
      WHERE A.Col_2 > 10 
      AND B.Col_2 BETWEEN 10 AND 30
      AND (B.Contry= 'RJ' OR B.Contry = 'SP');

    
    SELECT DISTINCT = No Duplicated
    SELECT A.CPF, COUNT(*) FROM table_compras A GROUP BY A.CPF ORDER BY A.CPF;

    
