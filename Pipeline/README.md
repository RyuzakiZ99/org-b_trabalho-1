# JAL: 

Para implementar a instrução de JAL no pipeline, primeiro foi adicionado um sinal de controle para a instrução na UC. Esse sinal é passado até a etapa de WB, e é utilizado como seletor em um multiplexador, permitindo escrever no banco de registradores o endereço de PC + 4. Também foi necessário adicionar registradores de barramento temporal extras para guardar o valor de PC + 4 nos barramentos de EX/MEM E MEM/WB.
Para adicionar o novo sinal de controle, foi inserido no endereço 0b000011 da memória de instruções o valor 0b110 0000 0001, correspondendo aos sinais ativos de JAL, Jump e RegWrite, respectivamente.

# BGEZ:

Primeiro, foi adicionado na ULA uma sinal de saída que indica se o resultado da operação foi negativo. Ele será utilizado na operação de teste, que somará o operando com zero para saber se é maior ou igual a zero. O multiplexador do segundo operando da ALU agora recebe o sinal BGEZ como segundo bit de seleção, que faz o operando receber o valor 0, para ser adicionado com o registrador. Outra mudança foi a entrada de operação da ALU, que agora passa por um mux selecionado por BGEZ, forçando a operação de ADD (0b010).

Para adicionar o novo sinal de controle, foi inserido no endereço 0b000001 da memória de instruções o valor 0b1000 0000 0000, correspondendo ao sinal ativo de BGEZ

# LB:

Para implementar a instrução, foi adicionado o sinal de controle LB à unidade de controle, usado na hora de converter o conteúdo da memória em um byte. Esse sinal também é utilizado na hora de selecionar a operação da ALU, para calcular o endereço efetivo da memória. No estágio de MEM/WB, o valor do byte retornado da memória passa por signal extension, ficando com 32 bits antes de ser escrito no registrador de destino.
A instrução possui opcode 0b100000 e esse endereço na memória de instruções terá como saída o valor 0b1 0000 0010 1011, que corresponde, respectivamente, aos sinais de controle ativos de LB, ALU_SRC, MEM_READ, MEM_TO_REG e REG_WRITE.

# DIV: 
Segue mesma lógica implementada em Monociclo.
