# Relatório

Gabriel Ferreira Leão - DRE: 122071303

Raisa Christina Nascimento Gonçalves - DRE: 122062516

## Implementação
Para o gerenciamento dos eventos, foi utilizada uma fila de prioridades, implementada com uma heap de mínimo, onde a prioridade é dada pelo momento (em segundos) em que o evento ocorre. As chegadas de jobs constituem um processo de Poisson e são inseridas na fila imediatamente ao início da simulação, já que são independentes de outros eventos.

A amostragem das variáveis aleatórias relevantes (inter-arrival-time e tempos de serviço) foi feita utilizando o método da inversa da CDF. Os cálculos estão disponíveis no notebook. Nos 3 cenários, a média dos tempos de serviço é a mesma, mas a distribuição é diferente.

Ao início da simulação de cada cenário, são inicializadas 3 filas, uma para cada servidor, e o tratamento dos eventos adiciona ou remove jobs nessas filas, além de potencialmente adicionar outros eventos na fila de eventos como efeito colateral. Ex: O tratamento da chegada de um job no servidor 1 pode gerar um evento de saída de job no servidor 1.

## Resultados
Inicialmente, com 10 mil jobs de warmup e 10 mil jobs para colher as métricas, totalizando 20 mil jobs, obtivemos resultados muito variados entre repetições do experimento. Inicialmente, aumentamos o número de jobs de warmup, considerando que 10 mil talvez não fosse o suficiente para o sistema entrar em estacionaridade. Mesmo com essa mudança, os resultados não foram consistentes.

Consideramos então aumentar o número de jobs dos quais as métricas são colhidas, e com essa mudança, totalizando 100 mil jobs de warmup e 100 mil jobs para colher as métricas, obtivemos resultados consistentes.

Esses resultados indicaram que, apesar de os tempos de serviço possuírem a mesma média, as situações 2 e 3 têm tempos médios no sistema maiores, e também com um maior desvio padrão. Isso indica que a variabilidade do job size impacta no acúmulo de jobs nas filas, e não só o tamanho médio do job e a taxa de chegada. O cenário 3, com o job size exponencial, apresentou as maiores métricas (média e desvio padrão do tempo no sistema)
