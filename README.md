# -Vaga-de-Estagio-Para-a-Empresa-Target-Sistemas
Códigos resolvidos das questões referente a vaga de estágio da empresa Target Sistemas

1)	Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0; 
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA); 
Ao final do processamento, qual será o valor da variável SOMA? 

# Inicialização das variáveis
indice = 13
soma = 0
k = 0

# Loop para calcular a soma
while k < indice:
    k += 1
    soma += k

# Imprimir o resultado
print("O valor da variável SOMA é:", soma)

# O valor da variável SOMA é: 91 é isso que vai sair no termina.

2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência. 

IMPORTANTE: Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código; 

def pertence_a_fibonacci(num):
    a, b = 0, 1
    while a < num:
        a, b = b, a + b
    return a == num

# Exemplo de uso
numero = int(input("Informe um número para verificar se pertence à sequência de Fibonacci: "))
if pertence_a_fibonacci(numero):
    print(f"O número {numero} pertence à sequência de Fibonacci.")
else:
    print(f"O número {numero} não pertence à sequência de Fibonacci.")

# Ao colocar no terminal qualquer número que for menor que 35, ele vai para o print que pertence à sequência. 
# Caso o número for 35 ou maior, ou se forem números negativos, o print vai retornar que não pertence à sequência.

3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne: 
• O menor valor de faturamento ocorrido em um dia do mês; 
• O maior valor de faturamento ocorrido em um dia do mês; 
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal. 

IMPORTANTE: 
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal; 
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média; 

# Nesta Questão, usei apenas o Arquivo JSON. Importar a biblioteca para fazer este uso. Caso eu fosse fazer com o XML, 
# também bastava eu importar a biblioteca do XML no Python e trazer os scripts que vocês me mandaram, mas se quiser esta resolução, 
# me mande um e-mail que eu faço para vocês também com o script do XML.

import json

# Dados do faturamento em JSON
json_data = '''
[
    {"dia": 1, "valor": 22174.1664},
    {"dia": 2, "valor": 24537.6698},
    {"dia": 3, "valor": 26139.6134},
    {"dia": 4, "valor": 0.0},
    {"dia": 5, "valor": 0.0},
    {"dia": 6, "valor": 26742.6612},
    {"dia": 7, "valor": 0.0},
    {"dia": 8, "valor": 42889.2258},
    {"dia": 9, "valor": 46251.174},
    {"dia": 10, "valor": 11191.4722},
    {"dia": 11, "valor": 0.0},
    {"dia": 12, "valor": 0.0},
    {"dia": 13, "valor": 3847.4823},
    {"dia": 14, "valor": 373.7838},
    {"dia": 15, "valor": 2659.7563},
    {"dia": 16, "valor": 48924.2448},
    {"dia": 17, "valor": 18419.2614},
    {"dia": 18, "valor": 0.0},
    {"dia": 19, "valor": 0.0},
    {"dia": 20, "valor": 35240.1826},
    {"dia": 21, "valor": 43829.1667},
    {"dia": 22, "valor": 18235.6852},
    {"dia": 23, "valor": 4355.0662},
    {"dia": 24, "valor": 13327.1025},
    {"dia": 25, "valor": 0.0},
    {"dia": 26, "valor": 0.0},
    {"dia": 27, "valor": 25681.8318},
    {"dia": 28, "valor": 1718.1221},
    {"dia": 29, "valor": 13220.495},
    {"dia": 30, "valor": 8414.61}
]
'''

# Carregar os dados
dados = json.loads(json_data)

# Filtrar valores de faturamento
valores = [item['valor'] for item in dados if item['valor'] > 0]

# Calcular o menor e maior valor
menor_valor = min(valores)
maior_valor = max(valores)

# Calcular a média mensal
media_mensal = sum(valores) / len(valores)

# Calcular o número de dias com faturamento acima da média
dias_acima_da_media = sum(1 for valor in valores if valor > media_mensal)

print(f"Menor valor de faturamento: R${menor_valor:.2f}")
print(f"Maior valor de faturamento: R${maior_valor:.2f}")
print(f"Número de dias com faturamento acima da média mensal: {dias_acima_da_media}")

# Para esta resolução a saida ficou assim: 
# Menor valor de faturamento: R$373.78
# Maior valor de faturamento: R$48924.24
# Número de dias com faturamento acima da média mensal: 10

4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado: 
•	SP – R$67.836,43 
•	RJ – R$36.678,66 
•	MG – R$29.229,88 
•	ES – R$27.165,48 
•	Outros – R$19.849,53 

Escreva um programa na linguagem que desejar onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.  

# Dados do faturamento por estado
faturamento = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53
}

# Calcular o valor total
valor_total = sum(faturamento.values())

# Calcular e exibir o percentual de cada estado
percentuais = {estado: (valor / valor_total) * 100 for estado, valor in faturamento.items()}

for estado, percentual in percentuais.items():
    print(f"{estado}: {percentual:.2f}%")

# Aqui esta a resolução no terminal: 
# SP: 37.53%
# RJ: 20.29%
# MG: 16.17%
# ES: 15.03%
# Outros: 10.98%

5) Escreva um programa que inverta os caracteres de um string. 
IMPORTANTE: 
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código; 
b) Evite usar funções prontas, como, por exemplo, reverse; 

def inverter_string(s):
    invertida = ''
    for char in s:
        invertida = char + invertida
    return invertida

# Exemplo de uso
entrada = input("Digite uma string para inverter: ")
string_invertida = inverter_string(entrada)
print("String invertida:", string_invertida)

# Se no terminar como exemplo escrever a frase: mob otium é nohtyP. 
# ele inverte deixando a frase como escrevemos: Python é muito bom.
