# RV32FD Extension

## Intro
* Embora existam duas extensões distintas: RV32F (Extensão de ponto flutuante de precisão simples) e RV32D (Extensão de ponto flutuante de precisão dupla), elas costumam ser incluídas juntas.
* Precisão Simples: 32 bits.
* Precisão Dupla: 64 bits.
* RISC-V obedece ao padrão de ponto flutuante IEEE 754-2008

## Registradores de Ponto Flutuante
* RV32F e RV32D usam 32 registradores de ponto flutuante (f0-f31) em vez do registradores inteiros (x0-x31).
* A principal razão para termos 2 conjuntos de registradores é que os processadores podem melhorar o desempenho dobrando a capacidade de armazenamento e a largura de banda, tendo dois conjuntos de registradores sem aumentar o espaço para o especificador de registradores no formato de instrução RISC-V.
* Se um processador tiver ambos RV32F e RV32D, os dados de precisão simples usarão apenas os 32 bits inferiores dos registradores f(f0-f31).
* __Ao contrário de x0 em RV32I, o registrador f0 não é hardwired para 0, mas é um registrador alterável como todos os outros registradores de ponto flutuante(f1-f31).__
* __Abaixo temos uma imagem mostrando os 32 registradores de ponto-flutuante.__
![[rv32fdregisters](https://http://riscv.org/)](rv32fd_registers.png)

## Elaboração: A extensão RV32FD permite que o modo de arredondamento seja "setado" por instrução.
* Esse modo de arredondamento (chamado de "static rounding") ajuda o desempenho quando você só precisa alterar o modo de arredondamento para uma instrução específica.
* O padrão é usar o modo de arredondamento dinâmico em fcsr. __O arredondamento estático é especificado como um último argumento opcional, pois fadd.s ft0, ft1, ft2, rtz irá arredondar para zero, independentemente de fcsr.__
* Existem outros modos de arredondamento que serão apresentandos a seguir:
![[rv32fd_rounding_modes](https://http://riscv.org/)](rv32fd_rounding_modes.png)

## Instruções
![[rv32fd](https://http://riscv.org/)](rv32fd.png)


