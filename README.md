# Relatório

## Implementação
Para o gerenciamento dos eventos, foi utilizada uma fila de prioridades, implementada com uma heap de mínimo, onde a prioridade é dada pelo momento (em segundos) em que o evento ocorre. As chegadas de jobs constituem um processo de Poisson e são inseridas na fila imediatamente ao início da simulação, já que são independentes de outros eventos.

A amostragem das variáveis aleatórias relevantes (inter-arrival-time e tempos de serviço) foi feita utilizando o método da inversa da CDF. Os cálculos estão disponíveis no notebook. Nos 3 cenários, a média dos tempos de serviço é a mesma, mas a distribuição é diferente.

Ao início da simulação de cada cenário, são inicializadas 3 filas, uma para cada servidor, e o tratamento dos eventos adiciona ou remove jobs nessas filas, além de potencialmente adicionar outros eventos na fila de eventos como efeito colateral. Ex: O tratamento da chegada de um job no servidor 1 pode gerar um evento de saída de job no servidor 1.

## Resultados
Apesar de os tempos de serviço possuírem a mesma média, as situações 2 e 3 apresentaram tempos médios no sistema maiores, em média, e também com um maior desvio padrão. Isso indica que a variabilidade do job size impacta no acúmulo de filas, e não só o tamanho médio do job.
