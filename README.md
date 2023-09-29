# Determinando a temperatura de um corpo negro pelo método Monte Carlo

## Resumo

Este código é um exemplo de ajuste de espectro de corpo negro em Python e pode ser adaptado para ajustar outros tipos de dados espectrais. O código em Python tem o objetivo de determinar a temperatura T de um corpo negro, ajustando um espectro à função de Planck utilizando o método de Monte Carlo. No fim, espera-se que seja possível determinar os parâmetros que melhor descrevem a um corpo negro, como a temperatura e o fator de escala, e excluindo as bandas de absorção identificadas.

## Sobre o repositório

- ‘corpo_negro.txt’: Um arquivo de exemplo contendo dados de um espectro de corpo negro. Os dados se apresentam em duas colunas, onde a primeira coluna representa o comprimento de onda em micrômetros e a segunda coluna representa a potência emissiva espectral (W / (m^2 * micron)).

- ‘corpo_negro_fit.py’: Código em Python que realiza o ajuste.

## Dependências

- NumPy
- Matplotlib
- SciPy

## Como usar o código

Clone este repositório ou baixe o arquivo ‘corpo_negro_fit.py’para o seu ambiente de trabalho. Execute o código Python ‘corpo_negro_fit.ipynb’ em seu ambiente. Você pode fazer isso usando um ambiente Python de sua escolha, como Jupyter Notebook ou um ambiente de desenvolvimento integrado (IDE).

Primeiro, certifique-se de que o arquivo de dados ‘corpo_negro.txt’ está presente no mesmo diretório que o arquivo Python. Os dados no arquivo `corpo_negro.txt` precisam estar formatados corretamente, com duas colunas separadas por espaços ou vírgulas. As bibliotecas devem estar instaladas em seu ambiente Python.

## Metodologia

O código segue a seguinte metodologia para ajustar o espectro de corpo negro:

A função de ajuste criada é  formulada com base na Lei de Planck, que descreve a intensidade espectral de um corpo negro em termos de temperatura e comprimento de onda. A função planck_lambda é definida para calcular a intensidade espectral teórica usando a Lei de Planck. As bandas de absorção do espectro são identificadas encontrando mínimos locais na potência emissiva, indicando onde a intensidade provavelmente cai devido à absorção de energia. Uma máscara, [mask], booleana é criada para excluir automaticamente essas bandas do ajuste. Posteriormente, usaremos esta mesma máscara com o objetivo inverso, para identificarmos e listarmos estas bandas. A incerteza da temperatura será calculada a partir do desvio padrão das amostras de temperatura.

O método de Monte Carlo irá estimar os parâmetros de ajuste (temperatura e fator de escala). Foram geradas 1000 amostras, a fim de perturbar os parâmetros iniciais com ruído aleatório, assim, a cada iteração, os dados perturbados são ajustados à função de Planck usando a função curve_fit da biblioteca SciPy. O número de amostras pode ser ajustado para equilibrar a precisão e o tempo de execução, entretanto resultados mais precisos irão sacrificar o tempo, demorando mais para que os outputs sejam gerados. O valor do Chi² é calculado para cada conjunto de parâmetros que foram estimados, permitindo uma comparação da potência emissiva observada com a potência emissiva teórica.


## Outputs

Os resultados incluem os seguintes itens:

- Um gráfico com o ajuste em relação aos dados originais
- Um gráfico identificando as bandas de absorção dentro da amostra 
- Valores de temperatura, incerteza, Chi² e uma lista das bandas de absorção identificadas
