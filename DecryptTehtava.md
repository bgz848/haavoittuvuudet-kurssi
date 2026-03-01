# Link Decrypt
## 1)
Aloitin kloonaamalla

    git clone https://github.com/robbins/tp-link-decrypt
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt01.png)
Projektia tutkiessa huomasin, että firmware-tiedoston lataaminen vaati AWS CLI -työkalun, jota ei ollut vielä asennettuna. Asensin sen ja latasin tarvittavan firmware-tiedoston suoraan TP-Linkin S3-palvelusta:

    sudo apt install awscli
    aws s3 cp s3://download.tplinkcloud.com/firmware/Tapo_C200v3_en_1.4.2_Build_250313_Rel.40499n_up_boot-signed_1747894968535.bin Tapo_C200v4_en_1.4.2.bin --no-sign-request
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt02.png)
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt03.png)


Ajoin

      ./extract_keys.sh
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt04.png)

Ohjelmaa kääntäessä se valitti puuttuvuudesta. https://stackoverflow.com/questions/13024481/fatal-error-openssl-evp-h-no-such-file-or-directory Googlaamalla sain selville mikä osa puuttui.
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt05.png)
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt06.png)


Ohjelmaa kääntäessä siitä puttui osa. RSA_0.h Epäilin heti sen olleen epäonnistuneen

    ./extract_keys.sh
komennon vika.
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt07.png)


Ohjelmaa pyörittäessä se valitti puuttuvista osista Jefferson ja Ubi Reader.
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt08.png)

Asensin dependancien asentamista tarvittavan ohjelman. Ja sitten tarvittava ohjelmat.

    sudo apt install -y pipx
    pipx install jefferson
    pipx install ubi-reader
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt09.png)

Varmistin että toimivatko ohjelmat tarvittavalla tavalla.

    pipx list
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt11.png)

Näissä oli pieni vika, jonka korjasin.

    pipx ensurepath
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt10.png)
Kun kaikki riippuvuudet oli asennettu ja polut kunnossa, ohjelma kääntyi ja suorittui ilman virheilmoituksia.
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt12.png)
## 2/3/4) 
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt13.png)
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt14.png)

## 5) Search available applications.
![](https://raw.githubusercontent.com/bgz848/haavoittuvuudet-kurssi/refs/heads/main/linkdecrypt15.png)
## 6) Analyse and try to open root password.



