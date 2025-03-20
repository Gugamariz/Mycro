#Mycro
O Mycro é um projeto de micromouse simples para a competição da robochallenge, o hardware funcionou em geral (menos alguns detalhes que serão comentados após). A publicação nesse github serve para ajudar pessoas que estão entrando na categoria e querem entrar na categoria com um robô mais simples e facíl de se projetar.
## Power 
A placa tem basicamente 3 niveis de tensão: A tensão da bateria (que varia de acordo com que ela se descarrega), 5V e 3.3V. O rail de 5V serve para somente diminuir a tensão para o regulador linear, com exceção de um componente que utiliza os 5V. O rail de 3.3V é utilizado para quase todo o resto da placa com exceção da parte de potência que controla os motores que utiliza a tensão da bateria.
### Os 5V
Os 5V como comentado anteriormente quase não tem uso, servindo basicamente para garantir que o regulador linear não falhe devido a uma grande potência dissipada.

Para regular a tensão foi utilizado um TPS82140, um regulador buck com indutor integrado da Texas Instruments. Ele foi escolhido principalmente para diminuir a complexidade do design e permitir que o projeto fosse terminado mais rapidamente. Além disso um dos benefícios dele por consequencia foi não ocupar tanto espaço na placa, sempre bom ter mais espaço :D.

![[Pasted image 20250320021239.png]]

O circuito final foi o seguinte: 
![[Pasted image 20250320021422.png]]

![[Pasted image 20250320021751.png]]

Vale comentar algumas coisas que atualmente eu mudaria. Utilizar um resistor no valor de 52k3 foi extremamente incomodo depois, enquanto ao comprar em um grande distribuidor como a Mouser ou Digikey você conseguiria achar ele facilmente, no Brasil tentar comprar de um local como o Mercado Livre ou outra loja é extremamente difícil (principalmente considerando o encapsulamento 0603 que muitos tem medo pelo tamanho). Nesse caso o ideal teria sido escolher valores diferente para os resistores de feedback ou até mesmo fazer alguma associação de resistores que fosse adequada.

O capacitor de 22u sofreu do mesmo problema, porém pior. Na tensão de operação dele e encapsulamento é extremamente difícil achar um fabricante que faça capacitores com 22u ou mais. O ideal então seria alterar ele para um encapsulamento maior que faria com que fosse muito mais fácil achar um componente adequado.

### Os 3.3V
Os 3.3V é provavelmente o rail mais importante da placa, ele alimenta o microcontrolador, IMU, sensores de parede e mais. Considerando então que os sensores de parede poderiam ter suas saídas afetadas por uma variação na sua tensão de alimentação foi decidido utilizar um regulador linear que teria menos ruído comparado com um conversor buck que costuma ter uma quantidade considerável de ripple na sua saída.

O circuito em si é muito simples, consistindo basicamente de um CI 1117 que você acha em qualquer lugar e os dois capacitores de desacoplamento adequados na sua saída e entrada.

![[Pasted image 20250320022739.png]]

No esquemático foi anotado que caso fosse necessário ainda uma saída com menos ruído poderia ter sido usado um CI alternativo, no final não foi necessário.

![[Pasted image 20250320022910.png]]

### A bateria
A bateria não dimensionada com todo o cuidado, porém levando em conta projetos anteriores que foram observados foi percebido que 300mAh costuma ser mais do que o suficiente. A bateria então foi uma LiPo 2S high voltage (tensão da célula de 4.25V em vez de 4.2V) de 300mAh.

Vale lembrar também que uma das principais considerações no projeto é o peso final do robô pois ele determina a sua aceleração máxima então escolher a bateria mais leve possível é essencial.

![[Pasted image 20250320023335.png]]

### Vale comentar também
Para que houvesse um indicador visual de que as tensões da placa estão adequadas foi utilizado um LED RGB para uma visualização rápida. Um problema que sempre ocorreu em robôs seguidores de linha quando alguém pedia minha ajuda com um problema era que o regulador de tensão falhou e esqueceram de medir a tensão. Com um indicador visual fica mais difícil esquecer.

O Mycro é um projeto de micromouse simples para a competição da robochallenge, o hardware funcionou em geral (menos alguns detalhes que serão comentados após). A publicação nesse github serve para ajudar pessoas que estão entrando na categoria e querem entrar na categoria com um robô mais simples e facíl de se projetar.
## Power 
A placa tem basicamente 3 niveis de tensão: A tensão da bateria (que varia de acordo com que ela se descarrega), 5V e 3.3V. O rail de 5V serve para somente diminuir a tensão para o regulador linear, com exceção de um componente que utiliza os 5V. O rail de 3.3V é utilizado para quase todo o resto da placa com exceção da parte de potência que controla os motores que utiliza a tensão da bateria.
### Os 5V
Os 5V como comentado anteriormente quase não tem uso, servindo basicamente para garantir que o regulador linear não falhe devido a uma grande potência dissipada.

Para regular a tensão foi utilizado um TPS82140, um regulador buck com indutor integrado da Texas Instruments. Ele foi escolhido principalmente para diminuir a complexidade do design e permitir que o projeto fosse terminado mais rapidamente. Além disso um dos benefícios dele por consequencia foi não ocupar tanto espaço na placa, sempre bom ter mais espaço :D.

![[Pasted image 20250320021239.png]]

O circuito final foi o seguinte: 
![[Pasted image 20250320021422.png]]

![[Pasted image 20250320021751.png]]

Vale comentar algumas coisas que atualmente eu mudaria. Utilizar um resistor no valor de 52k3 foi extremamente incomodo depois, enquanto ao comprar em um grande distribuidor como a Mouser ou Digikey você conseguiria achar ele facilmente, no Brasil tentar comprar de um local como o Mercado Livre ou outra loja é extremamente difícil (principalmente considerando o encapsulamento 0603 que muitos tem medo pelo tamanho). Nesse caso o ideal teria sido escolher valores diferente para os resistores de feedback ou até mesmo fazer alguma associação de resistores que fosse adequada.

O capacitor de 22u sofreu do mesmo problema, porém pior. Na tensão de operação dele e encapsulamento é extremamente difícil achar um fabricante que faça capacitores com 22u ou mais. O ideal então seria alterar ele para um encapsulamento maior que faria com que fosse muito mais fácil achar um componente adequado.

### Os 3.3V
Os 3.3V é provavelmente o rail mais importante da placa, ele alimenta o microcontrolador, IMU, sensores de parede e mais. Considerando então que os sensores de parede poderiam ter suas saídas afetadas por uma variação na sua tensão de alimentação foi decidido utilizar um regulador linear que teria menos ruído comparado com um conversor buck que costuma ter uma quantidade considerável de ripple na sua saída.

O circuito em si é muito simples, consistindo basicamente de um CI 1117 que você acha em qualquer lugar e os dois capacitores de desacoplamento adequados na sua saída e entrada.

![[Pasted image 20250320022739.png]]

No esquemático foi anotado que caso fosse necessário ainda uma saída com menos ruído poderia ter sido usado um CI alternativo, no final não foi necessário.

![[Pasted image 20250320022910.png]]

### A bateria
A bateria não dimensionada com todo o cuidado, porém levando em conta projetos anteriores que foram observados foi percebido que 300mAh costuma ser mais do que o suficiente. A bateria então foi uma LiPo 2S high voltage (tensão da célula de 4.25V em vez de 4.2V) de 300mAh.

Vale lembrar também que uma das principais considerações no projeto é o peso final do robô pois ele determina a sua aceleração máxima então escolher a bateria mais leve possível é essencial.

![[Pasted image 20250320023335.png]]

### Vale comentar também
Para que houvesse um indicador visual de que as tensões da placa estão adequadas foi utilizado um LED RGB para uma visualização rápida. Um problema que sempre ocorreu em robôs seguidores de linha quando alguém pedia minha ajuda com um problema era que o regulador de tensão falhou e esqueceram de medir a tensão. Com um indicador visual fica mais difícil esquecer.

O Mycro é um projeto de micromouse simples para a competição da robochallenge, o hardware funcionou em geral (menos alguns detalhes que serão comentados após). A publicação nesse github serve para ajudar pessoas que estão entrando na categoria e querem entrar na categoria com um robô mais simples e facíl de se projetar.
## Power 
A placa tem basicamente 3 niveis de tensão: A tensão da bateria (que varia de acordo com que ela se descarrega), 5V e 3.3V. O rail de 5V serve para somente diminuir a tensão para o regulador linear, com exceção de um componente que utiliza os 5V. O rail de 3.3V é utilizado para quase todo o resto da placa com exceção da parte de potência que controla os motores que utiliza a tensão da bateria.
### Os 5V
Os 5V como comentado anteriormente quase não tem uso, servindo basicamente para garantir que o regulador linear não falhe devido a uma grande potência dissipada.

Para regular a tensão foi utilizado um TPS82140, um regulador buck com indutor integrado da Texas Instruments. Ele foi escolhido principalmente para diminuir a complexidade do design e permitir que o projeto fosse terminado mais rapidamente. Além disso um dos benefícios dele por consequencia foi não ocupar tanto espaço na placa, sempre bom ter mais espaço :D.

![[Pasted image 20250320021239.png]]

O circuito final foi o seguinte: 
![[Pasted image 20250320021422.png]]

![[Pasted image 20250320021751.png]]

Vale comentar algumas coisas que atualmente eu mudaria. Utilizar um resistor no valor de 52k3 foi extremamente incomodo depois, enquanto ao comprar em um grande distribuidor como a Mouser ou Digikey você conseguiria achar ele facilmente, no Brasil tentar comprar de um local como o Mercado Livre ou outra loja é extremamente difícil (principalmente considerando o encapsulamento 0603 que muitos tem medo pelo tamanho). Nesse caso o ideal teria sido escolher valores diferente para os resistores de feedback ou até mesmo fazer alguma associação de resistores que fosse adequada.

O capacitor de 22u sofreu do mesmo problema, porém pior. Na tensão de operação dele e encapsulamento é extremamente difícil achar um fabricante que faça capacitores com 22u ou mais. O ideal então seria alterar ele para um encapsulamento maior que faria com que fosse muito mais fácil achar um componente adequado.

### Os 3.3V
Os 3.3V é provavelmente o rail mais importante da placa, ele alimenta o microcontrolador, IMU, sensores de parede e mais. Considerando então que os sensores de parede poderiam ter suas saídas afetadas por uma variação na sua tensão de alimentação foi decidido utilizar um regulador linear que teria menos ruído comparado com um conversor buck que costuma ter uma quantidade considerável de ripple na sua saída.

O circuito em si é muito simples, consistindo basicamente de um CI 1117 que você acha em qualquer lugar e os dois capacitores de desacoplamento adequados na sua saída e entrada.

![[Pasted image 20250320022739.png]]

No esquemático foi anotado que caso fosse necessário ainda uma saída com menos ruído poderia ter sido usado um CI alternativo, no final não foi necessário.

![[Pasted image 20250320022910.png]]

### A bateria
A bateria não dimensionada com todo o cuidado, porém levando em conta projetos anteriores que foram observados foi percebido que 300mAh costuma ser mais do que o suficiente. A bateria então foi uma LiPo 2S high voltage (tensão da célula de 4.25V em vez de 4.2V) de 300mAh.

Vale lembrar também que uma das principais considerações no projeto é o peso final do robô pois ele determina a sua aceleração máxima então escolher a bateria mais leve possível é essencial.

![[Pasted image 20250320023335.png]]

### Vale comentar também
Para que houvesse um indicador visual de que as tensões da placa estão adequadas foi utilizado um LED RGB para uma visualização rápida. Um problema que sempre ocorreu em robôs seguidores de linha quando alguém pedia minha ajuda com um problema era que o regulador de tensão falhou e esqueceram de medir a tensão. Com um indicador visual fica mais difícil esquecer.

O Mycro é um projeto de micromouse simples para a competição da robochallenge, o hardware funcionou em geral (menos alguns detalhes que serão comentados após). A publicação nesse github serve para ajudar pessoas que estão entrando na categoria e querem entrar na categoria com um robô mais simples e facíl de se projetar.
## Power 
A placa tem basicamente 3 niveis de tensão: A tensão da bateria (que varia de acordo com que ela se descarrega), 5V e 3.3V. O rail de 5V serve para somente diminuir a tensão para o regulador linear, com exceção de um componente que utiliza os 5V. O rail de 3.3V é utilizado para quase todo o resto da placa com exceção da parte de potência que controla os motores que utiliza a tensão da bateria.
### Os 5V
Os 5V como comentado anteriormente quase não tem uso, servindo basicamente para garantir que o regulador linear não falhe devido a uma grande potência dissipada.

Para regular a tensão foi utilizado um TPS82140, um regulador buck com indutor integrado da Texas Instruments. Ele foi escolhido principalmente para diminuir a complexidade do design e permitir que o projeto fosse terminado mais rapidamente. Além disso um dos benefícios dele por consequencia foi não ocupar tanto espaço na placa, sempre bom ter mais espaço :D.

![[Pasted image 20250320021239.png]]

O circuito final foi o seguinte: 
![[Pasted image 20250320021422.png]]

![[Pasted image 20250320021751.png]]

Vale comentar algumas coisas que atualmente eu mudaria. Utilizar um resistor no valor de 52k3 foi extremamente incomodo depois, enquanto ao comprar em um grande distribuidor como a Mouser ou Digikey você conseguiria achar ele facilmente, no Brasil tentar comprar de um local como o Mercado Livre ou outra loja é extremamente difícil (principalmente considerando o encapsulamento 0603 que muitos tem medo pelo tamanho). Nesse caso o ideal teria sido escolher valores diferente para os resistores de feedback ou até mesmo fazer alguma associação de resistores que fosse adequada.

O capacitor de 22u sofreu do mesmo problema, porém pior. Na tensão de operação dele e encapsulamento é extremamente difícil achar um fabricante que faça capacitores com 22u ou mais. O ideal então seria alterar ele para um encapsulamento maior que faria com que fosse muito mais fácil achar um componente adequado.

### Os 3.3V
Os 3.3V é provavelmente o rail mais importante da placa, ele alimenta o microcontrolador, IMU, sensores de parede e mais. Considerando então que os sensores de parede poderiam ter suas saídas afetadas por uma variação na sua tensão de alimentação foi decidido utilizar um regulador linear que teria menos ruído comparado com um conversor buck que costuma ter uma quantidade considerável de ripple na sua saída.

O circuito em si é muito simples, consistindo basicamente de um CI 1117 que você acha em qualquer lugar e os dois capacitores de desacoplamento adequados na sua saída e entrada.

![[Pasted image 20250320022739.png]]

No esquemático foi anotado que caso fosse necessário ainda uma saída com menos ruído poderia ter sido usado um CI alternativo, no final não foi necessário.

![[Pasted image 20250320022910.png]]

### A bateria
A bateria não dimensionada com todo o cuidado, porém levando em conta projetos anteriores que foram observados foi percebido que 300mAh costuma ser mais do que o suficiente. A bateria então foi uma LiPo 2S high voltage (tensão da célula de 4.25V em vez de 4.2V) de 300mAh.

Vale lembrar também que uma das principais considerações no projeto é o peso final do robô pois ele determina a sua aceleração máxima então escolher a bateria mais leve possível é essencial.

![[Pasted image 20250320023335.png]]

### Vale comentar também
Para que houvesse um indicador visual de que as tensões da placa estão adequadas foi utilizado um LED RGB para uma visualização rápida. Um problema que sempre ocorreu em robôs seguidores de linha quando alguém pedia minha ajuda com um problema era que o regulador de tensão falhou e esqueceram de medir a tensão. Com um indicador visual fica mais difícil esquecer.

![[Pasted image 20250320023630.png]]



















