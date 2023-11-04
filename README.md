registradores é que permitem o armazenamento de informações no meu fluxo de dados

=========================================================================================================================================================================

1) PC → Memória de instruções -> Banco de registradores → ULA → Banco de registradores
PC → Memória de instruções → Banco de Registradores  ULA → Unidade de Memória

2) As tags OrigALU (UALFonte), EscreveReg, LeMem e EscreveMem são 0,
RegDst e MemparaReg são don't care. Duas flags são ativadas, ULAOp e Branch:
ULAOp vai definir que a ULA será utilizada, no caso para compara o valor dos
dois registradores lidos (se 0, são iguais) e o Branch manda um sinal positivo
na porta and que vai esperar o Zero da ULA para dizer se são iguais os valores
comparados para, se for verdadeiro, realizar o salto.

7 flags:
	- RegDest e MemParaReg são don't care por que o beq n vai escrever nada no BDR.
	 
	- O UALFonte (ou OrigUAL) é 0 para definir que o segundo operando da ULA vem do reg
	  istrador lido 2
	 
	- o EscReg é 0, definindo que o valor de escrita vem de dados, apesar de não o fazer
	 
	- o LerMem e o EscMem são 0, pois não meche na memória.
	 
	- O DvC manda sinal positivo para o FontePC, deixando para o resultado do Zero da
	  ULA decidir se vai realizar o salto ou não.

3) Com isso, um nand teria ambos Binvert e BinvertA setados em 1 e o mux de op
em 1, para, de acordo com a Lei de DeMorgan, termos com a negação das entradas
em uma porta OR, um equivalente á negação da saída de um AND, portanto um nand.

Para o nor, ambos os Binvert estariam em 1 e o Op em 0, para, com a negação das
entradas de um and, termos um equivalente à negação da saída de um or, portanto
um nor.

Para o not, contanto que o valor de rs esteja em A e B, aplicando as mesmas opera
ções do nand traria o mesmo resultado.

Ref: https://sabermatematica.com.br/leis-de-morgan.html

4) De acordo com meus cálculos pouco confiáveis (a questão não ajuda também), a
resposta das duas é C1.

5) Ambas são arquiteturas de processadores,  diferenciando-se em sua propostas e casos de uso. A RISC (Reudcted Instruction Set Computer) é caracterizada por 
sua simplicidade, sendo melhor utilizado em sistemas que precisam de menor gasto energético, menor preço, hardware mais simples e maior velocidade, como os
celulares (Snapdragon), o MIPS                     (Poucas instruções que fazem pouco -> muitas instruções para fazer pouco)

Já os processadores CISC (Complex Instruction Set Computer) se destacam em operações mais complexas e na facilidade na construção de compiladores, o que facilita a vida
dos programadores por ter um maior número de instruções para utilizar em seus programas, usado em processadores Intel e AMD, para computadores pessoais
(Muitas instruções que fazem muito -> poucas instruções para fazer muito)

6) A máquina de Von Neumann é composta por Unidade de Controle, Unidade Lógica Aritmética (ULA), Unidade de Memória e Unidades de E/S. A Unidade de Controle gerencia os
recursos do computador e cordena o funcionamento dos componentes. A ULA executa as principais ações lógicas e aritméticas do computador. A Unidade de Memória é
responsável por armazenar os dados durante a execução. Por fim, as Unidades de Entrada e Saída oferecem um meio para o computador se comunicar com o usuário, através da
inserção de dados e a transmissão do resultado do processamento destes.

