#README Query.txt

A Query deste exemplo recebe os dados de corrente e potência instantânea. Para a manipulação destes dados os mesmos foram separados em 3 saídas, criando 3 outputs seguindo os passos descritos neste [link](), a primeira saída enviando somente dados de corrente, a segunda dados de potência por sensor e a terceira dados de potência total.
As funções utilizadas bem como outras funções podem ser encontradas em [Stream Analytics Query Language Reference](https://msdn.microsoft.com/en-us/library/azure/dn834998.aspx).

Os cálculos aqui utilizados são uma forma aproximada do cálculo da potência consumida em KWh. Para obter um cálculo do real consumo deve-se lançar mão de fórmulas que envolvam o cálculo da integral desta potência no tempo analisado. Uma vez que a finalidade deste artigo é somente ilustrar o envio de dados e análise e visualização dos mesmos, não nos preocupamos com uma análise matemática fiel dos dados de consumo.


## Irms

Para a saída utilizando dados de corrente,neste caso não utilisei nenhum tipo de agrupamento de dados simplesmente enviei os dados que entravam para a saída, sem nenhuma manipulação. 

##Consumo [KWh]

Somente para ilustrar o cálculo aproximado do consumo de cada sensor ao longo de 1 hora, utilizou-se a soma das potências lidas através da função `SUM()`, e multiplicamos por 3, que é a janela de tempo utilizada nas medições. Para agrupar estes dados em uma janela de 1 hora, através da função `TumblingWindow(hh, 1)`, obtivemos os cálculos do consumo em KWh de um aparelho ligado a esta tomada. 

##Consumo Total [KWh]

Já para a terceira saída calculamos a potência aproximada total de todos os sensores, somente somando as potências totais de cada sensor, como calculada na saída anterior.  

