## DIV 
Implementei a instrução DIV, apenas com o valor do quociente, sem o resto. 

![DIV-manual](https://github.com/user-attachments/assets/629bdc45-77c4-4e70-a2d6-97da9e9ac292)

### ALU
Na ALU, adicionei o bloco de divisão, que está no índice 011 do MUX. 

![ALU](https://github.com/user-attachments/assets/7959bdde-6906-4d2f-9dbb-e5387cbb0baf)

### ALU Control

No controle da ULA, adicionei lógica para que, caso a instrução fosse a de divisão, o código correspondesse com o índice de divisão no MUX. 
Anteriormente, o código que saia desse controle era 111. Assim, a lógica que usei altera o primeiro bit para 0. A ideia é usar
o resultado de um XOR para verificar se o código da instrução corresponde ao código da divisão, usar um OR com todas as saídas do XOR para ter uma saída 0
apenas quando o valor corresponder, e usar um AND para que, caso essa saída seja 1, o valor da porta que já estava implementada defina 
o primeiro bit. 
![ALU_control](https://github.com/user-attachments/assets/39eba752-ae01-4ff3-8d57-1077df3bf296)

![opcode-011](https://github.com/user-attachments/assets/37a6ff1b-58b5-46a0-bffd-2e2cddeab413)
