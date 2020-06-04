Getting started with Gumstix Overo
==================================


Mounting Gumstix COM on the Tobi Expansion Board  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. A configuração dos computadores Gumstix Overo consiste em um computador em modulo e uma placa de expansão. O modulo Overo se conecta a uma placa de expansão Tobi através dos dois conectores AVX de 70 pinos localizados na parte inferior do COM. Coloque a placa Tobi em uma superfície plana e antiestética, alinhe a COM com o contorno branco na placa acima dos conectores e pressione delicadamente a COM até que ela se encaixe no lugar.

The configuration of Gumstix Overo computers consists of a module computer and an expansion board. The Overo module connects to a Tobi expansion board via the two 70-pin AVX connectors located on the bottom of the COM. Place the Tobi board on a flat, anti-aesthetic surface, align the COM with the white outline on the board above the connectors and gently press the COM until it snaps into place.

	.. figure:: /img/Aerial/overo_front.png
	    :align: center

	.. figure:: /img/Aerial/gs_tobi.jpg
	    :align: center

.. Para utilizar a câmera, a placa de câmera deve ser conectada à parte superior do Overo COM através de um cabo de fita.

To use the camera, the camera board must be connected to the top of the Overo COM via a ribbon cable.

Overo Connections
~~~~~~~~~~~~~~~~~

	.. figure:: /img/Aerial/Overo_connection.png
	    :align: center

.. A placa de expansão Tobi vem com uma porta USB Host e uma USB On-the-Go (OTG). A porta USB Host é usada exclusivamente para conectar periféricos ao sistema, enquanto a porta USB OTG pode ser usada para conectar periféricos via cabo USB OTG ou para conectar o sistema Gumstix como periférico a um sistema host separado.

The Tobi expansion card comes with a USB Host port and a USB On-the-Go (OTG). The USB Host port is used exclusively to connect peripherals to the system, while the USB OTG port can be used to connect peripherals via USB OTG cable or to connect the Gumstix system as a peripheral to a separate host system.

.. As portas USB Host e as portas USB OTG possuem diferentes taxas de amostragem de dados USB e diferentes correntes elétricas. 

.. A porta USB Host utiliza uma corrente de 500 mA e aceita uma taxa de sinalização de *High-speed* (HS) a 480 Mbit/s, enquanto a porta USB OTG tem uma corrente de 100 mA e suporta três diferentes taxas de sinalização, *Low Speed* (LS) a 1,5 Mbit/s, *Full Speed* (FS) a 12 Mbit/s e *High Speed* (HS) a 480 Mbit/s. 

The USB Host port uses a current of 500 mA and accepts a **High-speed** (HS)signaling rate at 480 Mbit/s, while the USB OTG port has a current of 100 mA and supports three different signaling rates, **Low Speed** (LS) at 1.5 Mbit/s, **Full Speed** (FS) at 12 Mbit/s and **High Speed** (HS) at 480 Mbit/s.

.. Note Muitos periféricos USB usam uma taxa de sinalização de *Full Speed* (FS) e não funcionam na porta USB Host, que é apenas de *High Speed* (HS). Se você estiver com problemas para conectar periféricos USB diretamente ao sistema Gumstix, conectar os periféricos primeiro a um hub USB com alimentação e depois conectar o hub com alimentação ao sistema Gumstix geralmente resolverá o problema.

.. Note::
	Many USB peripherals use a signaling rate of **Full-Speed** (FS) and do not work on the USB Host port, which is only **High Speed** (HS). If you are having trouble connecting USB peripherals directly to the Gumstix system, connecting the peripherals first to a powered USB hub and then connecting the powered hub to the Gumstix system will usually solve the problem.

.. Para a conexão de mais periféricos, além da quantidade de portas USB disponíveis na placa de expansão Tobi, recomendamos a utilização de um hub USB. O hub USB **energizado** deve ser conectado a porta USB Host da placa de expansão e um hub USB **não energizado** deve ser conectado a porta OTG USB da placa de expansão com um cabo USB On-the-Go.

For connecting more peripherals, in addition to the number of USB ports available on the Tobi expansion card, we recommend using a USB hub. The **powered USB hub** must be connected to the USB Host port and a **non-powered USB hub** must be connected to the USB OTG port with a USB On-the-Go cable.

.. Tip	O vídeo `Connecting Gumstix Tobi Expansion Board to Video Monitor`_ demonstra como conectar um Overo COM a um monitor e alguns periféricos através da placa Tobi.

.. Tip::
	The video `Connecting Gumstix Tobi Expansion Board to Video Monitor`_ demonstrates how to connect an Overo COM to a monitor and some peripherals via the Tobi board.

.. _Connecting Gumstix Tobi Expansion Board to Video Monitor: https://www.youtube.com/watch?v=FxxEBn8Z_PA

Connecting to Overo
~~~~~~~~~~~~~~~~~~~

.. Primeiramente, insira o seu cartão microSD com a imagem do sistema operacional no slot de cartão na parte superior do Overo COM. Certifique-se de que ele se encaixa firmemente no lugar.

First, insert your microSD card with the operating system image in the card slot at the top of Overo COM. Make sure it fits securely in place.

.. O computador Overo pode ser acessado conectando-o a um outro computador Linux ou Windows, ou até mesmo ser ligado diretamente a um monitor DVI e conectado a diversos periféricos, como mouse, teclado, monitor, saída de som, entre outros, através da placa de expansão Tobi.

The Overo computer can be accessed by connecting it to another Linux or Windows computer, or even be connected directly to a DVI monitor and connected to various peripherals, such as mouse, keyboard, monitor, sound output, among others, through the Tobi expansion board.

.. Neste trabalho, iremos optar por liga-lo a um computador Linux e estabelecer uma conexão seria via a porta USB Console por simplicidade. 

In this work, we will choose to connect it to a Linux computer and establish a serious connection via the USB Console port for simplicity.

Establishing a serial connection via console
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Para ligar o computador embarcado ao computador conecte um cabo USB ao computador e ao USB console da placa de expansão tobi. Feito isso, uma luz verde deve se acender indicando a conexão correta. Em seguida verifique em qual porta de comunicação serial a gumstix foi conectada, no Windows isso pode ser verificado acessando o **Gerenciador de Dispositivos** e, em seguida, **Portas(COM e LPT)**. No Linux basta executar o comando:

To connect the embedded computer to the host computer, connect a USB cable to the computer and to the USB console of the Tobi expansion board. Once this is done, a green light should come on indicating the correct connection. Then check which serial communication port Gumstix COM is connected to, in Windows this can be checked by accessing **Device Manager** and then **Ports (COM and LPT)**. On Linux, just run the command:

::

	$ dmesg | grep tty

.. Note	O comando ``dmesg`` é um comando que imprime as mensagens núcleo que, na maioria das vezes, são mensagens dos drivers do dispositivo. Quando acrescentamos ``grep tty`` estamos realizando uma busca nas saídas da função ``dmesg`` pelo termo ``tty`` e restringindo a sua saída aquelas mensagens que contém este termo.

.. Note::
	The ``dmesg`` command is a command that prints the core messages which, in most cases, are messages from the device drivers. When we add `` grep tty``we are performing a search on the outputs of the `` dmesg`` function for the term ``tty`` and restricting its output to those messages that contain this term.

.. A placa Gumstix deve ser a última entrada a aparecer. Por exemplo:

The Gumstix card should be the last entry to appear. For example:

::

	user@Ubuntu:~$ dmesg | grep tty
	[    0.000000] printk: console [tty0] enabled
	[ 4214.120990] usb 2-1: FTDI USB Serial Device converter now attached to **ttyUSB0**


.. Em seguida será necessário executar um programa para emular o terminal, recomenda-se o programa Screen para Linux. Caso ainda não o tenha instalado basta executar a linha de comando ``sudo apt-get install screen``. Ou no caso do sistema operacional Windows, recomenda-se o PuTTY. Estes programas emulam terminais e executam apenas a tarefa de imprimir os caracteres recebidos pela porta serial, ou USB no caso, e enviar por essa mesma porta os caracteres digitados. 

Then it will be necessary to run a program to emulate the terminal, we recommend the Screen program for Linux OS. If you have not yet installed it, just run the command line ``sudo apt-get install screen``. Or in the case of the Windows OS, PuTTY is recommended. These programs emulate terminals and perform only the task of printing the characters received through the serial port, or USB in this case, and sending the characters typed through that same port.

.. Para iniciar a comunicação por terminal com o Gumstix Overo basta executar a seguinte linha de comando:

To start communication by terminal with Gumstix Overo, just run the following command line:

::

	$ sudo screen /dev/<USB Device Name> 115200

.. No caso da linha de comando do exemplo apresentada anteriormente, o termo ``ttyUSB0`` foi a porta encontrada ao utilizar o comando "dmesg" e "115200" é a velocidade de comunicação em *baud*. Nesse momento a comunicação entre a gumstix e o computador deve ser estabelecida e assim que a gumstix for ligada os caracteres devem começar a ser impressos na tela do computador.

In the case of the command line in the example presented above, the term ``ttyUSB0`` was the port found when using the command "dmesg" and "115200" is the communication speed in *baud*. At this point, communication between gumstix and the computer must be established and as soon as the gumstix is turned on, the characters must begin to be printed on the computer screen.

Booting the Overo COM
~~~~~~~~~~~~~~~~~~~~~~~

Feita conexão com o console, o Overo COM estará pronta para ser ligado. Para inicializar o sistema basta conectar a fonte de alimentação de 5 Volts à sua placa de expansão. Os indicadores LED no COM devem acender em azul e verde. O processo de inicialização será exibido no terminal da sua máquina host. 

Porém, antes de ligá-la, é importante comentar que o fabricante recomenda a limpeza de variáveis da memória flash sempre que iniciar uma **nova versão do sistema operacional no computador embarcado pela primeira vez**. Para fazê-lo basta interromper o processo de boot antes de seu início no momento em que aparece uma contagem regressiva na tela. O processo tipico de inicialização será similar ao seguinte:

::

	reading u-boot.img
	reading u-boot.img


	U-Boot 2012.04.01 (Jul 19 2012 - 17:31:34)

	OMAP36XX/37XX-GP ES1.2, CPU-OPP2, L3-165MHz, Max CPU Clock 1 Ghz
	Gumstix Overo board + LPDDR/NAND
	I2C:   ready
	DRAM:  512 MiB
	NAND:  512 MiB
	MMC:   OMAP SD/MMC: 0
	In:    serial
	Out:   serial
	Err:   serial
	Board revision: 1
	Direct connection on mmc2
	timed out in wait_for_pin: I2C_STAT=1000
	I2C read: I/O error
	Unrecognized expansion board
	Die ID #2d3800229ff8000001683b060a00b012
	Net:   smc911x-0
	Hit any key to stop autoboot:  0
	Overo # 

Uma vez interrompido o boot do sistema basta executar o comando ``nand erase 240000 20000`` para limpar as variáveis salvas e ``reset`` para reiniciar o processo de boot, como mostrado a seguir:

::

	# nand erase 240000 20000
	# reset


.. Note:: 
	Se os LEDs azul e verde no COM não acenderem e não for exibido nada no seu terminal, tente pressionar o botão de reset na placa de expansão até ver um processo de inicialização. Se o problema persistir, a imagem pode não ter sido instalada com sucesso. Recomenda-se que você tente instalar novamente ou usar uma imagem diferente.

A figura a seguir ilustra este procedimento. Os caracteres são impressos rapidamente e a contagem de tempo é de apenas 1 segundo para os núcleos do projeto Yocto, portanto é necessário ficar atento para interromper o processo.

.. adicionar imagem

Feito isso o processo de boot deve iniciar e diversas mensagens irão aparecer na tela. É importante verificar, na primeira vez que se inicia o sistema operacional, se nenhuma mensagem de erro aparece e, se tudo ocorrer bem, ao final do processo será exigido uma senha, se o computador embarcado chegou a esse ponto provavelmente tudo está em ordem.
A senha de acesso ao sistema Yocto é "root" e para o sistema Ubuntu gumstix, caso necessário, a senha é igual ao usuário.

Salvando a imagem do SO na memória flash
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

O computador embarcado Overo WaterSTORM COM da Gumstix R conta com uma memória interna não volátil de 1 GB do tipo Flash, memória suficiente para armazenarmos o sistema operacional. Apesar de o mais recomendado ser continuar usando o cartão SD, por possuir mais memória e ser transferido entre dispositivos com mais facilidade, ter o sistema operacional salvo na memória flash do computador embarcado pode ser útil. 

O site do fabricante descreve quatro maneiras distintas de se realizar este procedimento a maneira
que apresentou o melhor resultado foi a última das opções explicadas e é resumida a instalar na memória flash tudo o que foi instalado no cartão de memória e somado ao binário do núcleo através de um script fornecido em seu endereço eletrônico. O script desejado está disponivel em `Flashing with U-Boot - Write Images to Flash`_, porém, todo o processo será detalhadamente descrito a seguir.

.. _Flashing with U-Boot - Write Images to Flash: https://www.gumstix.com/support/faq/write-images-flash#flash-with-uboot

1. Com o cartão SD bootavel conectado ao seu computador host, acesse o diretorio **/boot** na partição **rootfs**. Por exemplo, caso o **rootfs** esteja montado em **/media/<Nome_de_Usuário>/rootfs/**:

:: 

	$ cd /media/<Nome_de_Usuário>/rootfs/boot

2. Devemos armazenar dentro da pasta **boot** da partição **rootfs** o novo **MLO**, **u-boot.img** e o **binário do núcleo**. Observe que esses *bootloaders* que serão adicionados à pasta **boot** não são os mesmos que estão na partição **boot** pois estes novos *bootloaders* devem ser específicos para operar da memória flash. Esses novos arquivos podem ser obtidos com os seguintes comandos:

::

	$ sudo wget https://s3-us-west-2.amazonaws.com/gumstix-yocto/2015-02-25/overo/master/MLO
	$ sudo wget https://s3-us-west-2.amazonaws.com/gumstix-yocto/2015-02-25/overo/master/u-boot.img
	$ sudo wget https://s3-us-west-2.amazonaws.com/gumstix-yocto/2015-02-25/overo/master/gumstix-console-image-overo.ubi -O rootfs.ubi

3. Crie um script para gravar os arquivos na memoria flash com o nome *flash-all.cmd*. Para isso basta executar o comando:

::

	$ sudo nano flash-all.cmd

Copiar e colar o script:

::

	nand erase.chip

	# switch to 1-bit ECC and write MLO
	load mmc 0:2 ${loadaddr} /boot/MLO
	nandecc hw
	nand write ${loadaddr} 0x0 ${filesize}
	nand write ${loadaddr} 0x20000 ${filesize}
	nand write ${loadaddr} 0x40000 ${filesize}
	nand write ${loadaddr} 0x60000 ${filesize}

	# switch back to BCH8 and write u-boot
	nandecc sw bch8
	load mmc 0:2 ${loadaddr} /boot/u-boot.img
	nand write ${loadaddr} u-boot ${filesize}

	# write the kernel (if uImage...otherwise skip)
	load mmc 0:2 ${loadaddr} /boot/uImage
	nand write ${loadaddr} linux ${filesize}

	# write the filesystem
	load mmc 0:2 ${loadaddr} /boot/rootfs.ubi
	nand write ${loadaddr} rootfs ${filesize}

Em seguida confirme o nome do arquivo (**Ctrl+O**) e saia do editor de texto (**Ctrl+X**).

.. figure:: /img/Aerial/flash-all.png
	:align: center

4. Para tornar o script executável e adiciona-lo à partição de boot do cartão SD bootável, basta executar e seguinte linha de comando (assumindo que a partição de inicialização esteja montada em /media/boot):

.. Warning::	
	Lembre-se de editar os nomes dos arquivos no script para coincidirem com os nomes dos arquivos que serão adicionados a seguir.

::

	$ mkimage -A arm -O linux -T script -C none -a 0 -e 0 -n "flash-all" -d flash-all.cmd /media/<Nome_de_Usuário>/boot/flash-all.scr

.. figure:: /img/Aerial/flashSD.png
	:align: center

.. Note::
	Caso o comando ``mkimage`` não seja encontrado, basta executar o comando ``sudo apt install u-boot-tools`` para instalar o pacote de ferramentes em seu computador. O comando ``mkimage`` é um comando utilizado para fazer imagens para serem utilizadas pelo **u-boot**. As opções de comando e suas explicações são facilmente obtidas digitando ``man mkimage`` no terminal do Linux.

5. Desmonte o cartão SD e o insira em seu computador embarcado, inicie o sistema e aguarde o carregamento do u-boot. Interrompa o processo de inicialização quando vir "**Hit any key to stop autoboot**" e insira o comando:

::

	# mmc rescan 0; load mmc 0 ${loadaddr} flash-all.scr; source ${loadaddr}

Essa linha de comando irá executar o script passando os bootloaders, o binário do núcleo e os arquivos raiz do sistema operacional para a memória flash do sistema embarcado e as mensagens apresentadas na figura abaixo devem ser impressas.

.. figure:: /img/Aerial/flasing.png
	:align: center

Retire o cartão SD e reinicie o seu sistema. Se tudo correu bem, seu sistema deve iniciar normalmente.

.. sudo screen /dev/ttyUSB0 115200

References
----------

   	* PITA, H. C. Desenvolvimento de sistema de comunicação multiplataforma para veículos aéreos de asa fixa. Faculdade de Tecnologia, Universidade de Brasília, 2018.
      
	* `4. Boot Your System`_ - gumstix.com

	* `Write Images to Flash`_ - gumstix.com

.. _4. Boot Your System: https://www.gumstix.com/support/getting-started/boot-system

.. _Write Images to Flash: https://www.gumstix.com/support/faq/write-images-flash
