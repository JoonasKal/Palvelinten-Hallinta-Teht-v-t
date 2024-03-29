# h1 Viisikko

## x)

Kertasin tunnilla käymämme saltin tärkeimmät komennot eli pkg, file, service, user ja cmd. Kävin läpi myös sen, kuinka Githubiin tehdään nettisivu ja kuinka kirjoitetaan raportti.

## a) Hello Windows/Mac Salt World!

Käytin "sudo salt-call --version" komentoa, näen että olen asentanut saltin.

![Screenshot_2024-03-29_11-31-38](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/1445afa7-dfdd-4ced-9abd-5754c8a58a21)

## b) Hello Vagrant!

Käytin komentoa "vagrant up" tämä käynnisti tunnilla luomamme virtuaali koneen.

![Screenshot_2024-03-29_11-37-02](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/b717faab-6fa3-4728-b46f-2c745aa3ab47)

## c) Virtuaalikone

Tämän jälkee otin siihen ssh yhteyden ja pääsin koneeseen sisälle.

![Screenshot_2024-03-29_11-37-28](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/06e38360-6ed8-444a-b2bf-6203b1b528a2)

## a) Asenna Salt (salt minion)

Ensiksi ajoin "sudo apt-get update komennon" joka päivitti virtuaalikoneen.

![Screenshot_2024-03-29_12-01-59](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/a1a29538-add3-4941-881f-cd1c5fd26aea)

Tämän jälkeen ajoin "sudo apt-get -y install salt-minion" komennon asentaakseni salt-minionin.

![Screenshot_2024-03-29_12-02-17](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/d545c8f0-934c-4fac-a888-bdacb90caaef)

Tarkistin vielä lopuksi "sudo salt-call --version" komennolla, että asennus onnistui.

![Screenshot_2024-03-29_12-03-09](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/7d3d7c0b-2009-4b52-8dfb-5eb846595d38)

## b) Viisi tärkeintä

### - pkg.installed
ajoin "sudo salt-call --local -l info state.single pkg.installed tree" komennon, joka asensi tree-paketin.

![Screenshot_2024-03-29_12-12-44](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/2dd82317-53fe-4453-91f2-5216e6c3c462)

### - file.managed
ajoin "sudo salt-call --local -l info state.single file.managed /tmp/moijoonas" komennon, joka loi tiedoston "moijoonas" tmp-kansioon.

![Screenshot_2024-03-29_12-18-24](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/b468c1dc-7c97-4925-8ae4-5378874f678f)

Kuten kuvasta näkyy tiedosto luotiin.

![Screenshot_2024-03-29_12-18-48](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/0adcb670-9fc4-495f-9225-f4d151b7bc20)

### - service.running
ajoin "sudo salt-call --local -l info state.single service.running apache2 enable=True" komennon ja se ei onnistunut. Oletan tämän johtuvan siitä, että en ole asentanut virtuaalikoneeseen Apache2.

![Screenshot_2024-03-29_12-26-40](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/1fa9abf8-f58d-4e92-a28e-5dde937c679d)

### - user
ajoin "sudo salt-call --local -l info state.single user.present joonas" komennon ja se teki koneeseen käyttäjän nimeltä joonas

![Screenshot_2024-03-29_12-30-59](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/32929cde-09e5-4c2d-840c-fdff2155f00a)
![Screenshot_2024-03-29_12-31-11](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/28913481-9f75-4de0-8b97-53d0ca25231a)

### - cmd
ajoin "sudo salt-call --local -l info state.single cmd.run 'touch /tmp/testi' " komennon ja se teki tmp-kansionn testi tiedoston

![Screenshot_2024-03-29_12-35-33](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/cfe6136a-03b5-4c8e-9851-af9e55e26dfb)
![Screenshot_2024-03-29_12-36-07](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/45b25ede-ea30-4c84-9b42-7d7c7f600561)

## c) Idempotentti

Ajoin uudelleen komennon "sudo salt-call --local -l info state.single pkg.installed tree", jotta näkisin, että muuttuuko mikään.

![Screenshot_2024-03-29_12-40-30](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/baf1d129-7034-4c5f-aabb-38a8833fc014)

Komento on idempotentti koska mitään ei muuttunut.

## d) Tietoa koneesta

Ajoin komennon "sudo salt-call --local grains.items | less" joka listasi tietoa koneesta.

### - grains.item ip4_interfaces

- listaa ip4 ethernet ja paikallisen osoitteen

![Screenshot_2024-03-29_12-52-45](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/3ac4cee3-f065-4f34-a720-d373b1601cbf)

### - grains.item osfinger

- listaa koneen nykyisen käyttöjärjestelmän

![Screenshot_2024-03-29_12-52-57](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/464d9d4e-24d3-42ae-b2e3-3e4e38077258)

### - grains.item osfinger virtual

- listaa koneen nykyisen käyttiksen ja käytössä olevan virtualisointi softan

![Screenshot_2024-03-29_12-53-09](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/b7df8dac-838b-4101-ad45-96d5ed8286e6)



## Lähteet:

https://terokarvinen.com/2024/configuration-management-2024-spring/ Luettu 29.3.2024

https://terokarvinen.com/2021/salt-run-command-locally/ Luettu 29.3.2024
