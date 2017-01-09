# IOT-surveillance (kannattaa avata tiedosto omassaan niin näyttää vähän fiksummalta)
SeAMKin tietotekniikan Teollisen internetin (IOT) kurssia varten tehty harjoitustyö, jonka tarkoituksena on toimia yksinkertaisena liiketunnistinrekisterinä hyödyntämällä Raspberry Pi:n kameraa ja raspberry-pi-cam -ohjelmaa.

#Asennusohjeet 
Tämä projekti käyttää LAMP-stackia perustanaan Raspberry Pi:llä
 	-sudo apt-get update
 	-sudo apt-get install apache2 mysql-server php5
 	-käynnistä uudelleen
 	-konfiguroi mysql
   	-salasanana käytetään Salasana123
		-avataan MySQL terminaali kirjoittamalla mysql ja painamalla enter linuxin terminaalissa
		-luodaan tietokanta iot ja sinne taulukko log
			-CREATE DATABASE iot;
			-USE iot;
			CREATE TABLE log (
				id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
				year INT,
				month INT,
				day INT,
				hour INT,
				minute INT,
				second INT
				)
	
  
Liiketunnistusohjelman asentaminen
https://github.com/skl/raspberry-pi-cam ohjeiden mukaan
  	git clone https://github.com/skl/raspberry-pi-cam.git
  	sudo -s
  	cp raspberry-pi-cam/picam /etc/init.d
  	update-rc.d picam defaults
  
	Korvaa (tai lisää) picam.py tiedostoon tässä projektissa olevan picam.py tiedoston mukaan (rivit 11, 17 ja 165)
	
	
#Toimintaperiaate
PiCam ottaa tietyn väliajan välein kuvia ja vertaa niitä pikseli kerrallaan, jos riittävän monta pikseliä on muuttunut, kuva tallennetaan ja SQL-tietokantaan tehdään merkintä. Tietokannasta voidaan tietoja viedä halutessaan verkkosivulle vaikka PHP:n kautta tai tuoda niitä Google Charts -muotoon (http://stackoverflow.com/questions/12994282/php-mysql-google-chart-json-complete-example).
Tämä on kaikkea muuta kuin hyvin suojattu projekti, mutta se toimi noin 25 päivää ennen sähkökatkoa jolloin Raspberry Pi kesken tallennuksen korruptoi koko kortin.

#Tulevaisuutta ajatellen
Turvallisuus olisi hieno lisä, piilottaa vaikka MySQL tietokannan käyttäjätunnukset ja salasanat omaan tiedostoonsa ja kaivaa ne jollain turvallisemmalla metodilla kuin raakatekstinä tiedostossa.
Raspberry Pi:lle oma "UPS" varavirtalähteen muodossa ettei sähkökatkot tekisi temppuja niin helposti.
Tarkkailusivun tekeminen, Google Chartsin lisääminen, HTML-puolen tekeminen jne.
