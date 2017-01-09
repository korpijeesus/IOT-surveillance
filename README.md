# IOT-surveillance
SeAMKin tietotekniikan Teollisen internetin (IOT) kurssia varten tehty harjoitustyö, jonka tarkoituksena on toimia yksinkertaisena liiketunnistinrekisterinä hyödyntämällä Raspberry Pi:n kameraa ja raspberry-pi-cam -ohjelmaa.

#Asennusohjeet 
Tämä projekti käyttää LAMP-stackia perustanaan Raspberry Pi:llä
  -sudo apt-get update
  -sudo apt-get install apache2 mysql-server php5
  -käynnistä uudelleen
  -konfiguroi mysql haluamasi tavalla
  
Liiketunnistusohjelman asentaminen
https://github.com/skl/raspberry-pi-cam ohjeiden muukaan
  git clone https://github.com/skl/raspberry-pi-cam.git
  sudo -s
  cp raspberry-pi-cam/picam /etc/init.d
  update-rc.d picam defaults
  
