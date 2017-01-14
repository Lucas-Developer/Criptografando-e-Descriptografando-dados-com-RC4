O RC4 é um algoritmo que promove transformações lineares não sendo necessários cálculos complexos, visto que o sistema funciona basicamente por meio de permutações e somas de valores inteiros, o que o torna muito simples e rápido.

A chave pode ter de zero (inexistente) até 256 bytes. Ele é utilizado nos padrões SSL/TLS, WEP e WPA, ou seja, é muito utilizado em aplicações web e redes sem fio sendo o primeiro algoritmo disponível nas redes sem fio. É a cifragem simétrica de fluxo mais utilizada e possui como princípio de funcionamento o segredo criptográfico perfeito, ou seja, a chave do tamanho da mensagem. É considerado seguro num contexto prático (duração das transações). No entanto, de forma geral os adeptos da criptografia não consideram o RC4 um dos melhores sistemas criptográficos, e em algumas aplicações são considerados como sendo muito inseguros.

O RC4 foi inicialmente desenvolvido por Ronald Rivest para a empresa a RSA Data Security, Inc., líder mundial em algoritmos de criptografia e foi durante muito tempo um segredo comercial muito bem guardado e popular utilizando por grandes softwares como Lotus Notes, Apple, Oracle Secure SQL, Internet Explorer, Netscape, Adobe Acrobat, entre outros.

De uma forma geral, o algoritmo RC4 consiste em utilizar um array que a cada utilização tem os seus valores permutados, e misturados com a chave, o que provoca uma dependência muito forte com esta chave. Esta chave, utilizada na inicialização do array, pode ter até 256 bytes (2048 bits). Entretanto o algoritmo é mais eficiente quando temos uma chave menor devido a superior perturbação aleatória induzida no array.

_____________________________________________________________________________________________________________________________

Inicialmente criamos uma instância de Cipher e especificamos o nome do algoritmo, o modo e o esquema de padding que é opcional, tudo separado por uma barra "/" conforme o código abaixo:

Cipher cifraDES;
  // Cria a cifra 
  cifraDES = Cipher.getInstance("DES/ECB/PKCS5Padding");


Após isso convertemos o texto para byte conforme destacado abaixo:

  // Texto puro
  byte[] textoPuro = "Exemplo de texto puro".getBytes();
Para criptografar o texto puro utilizamos o método Cipher.doFinal(), conforme mostra o código abaixo:

  // Inicializa a cifra para o processo de encriptação
  cifraDES.init(Cipher.ENCRYPT_MODE, chaveDES);
  // Texto encriptado
  byte[] textoEncriptado = cifraDES.doFinal(textoPuro);

Podemos verificar que o método doFinal também espera um array de bytes, por isso realizamos a conversão anteriormente.


Por fim, utilizamos o método Cipher.doFinal() em modo de decriptação para descriptografar o texto puro conforme o código destacado abaixo:

  // Inicializa a cifra também para o processo de decriptação
  cifraDES.init(Cipher.DECRYPT_MODE, chaveDES); 
  // Decriptografa o texto
  byte[] textoDecriptografado = cifraDES.doFinal(textoEncriptado);
