# x) Lue ja tiivistä

- Vagrantin avulla saa tehtyä helposti virtuaalikoneita, ei tarvitse kuin asentaa virtualbox ja vagrant ja muokata Vagrantfilea

- Saltin avulla voi kontrolloida monia koneita, voit asettaa yhden koneen masteriksi ja sille monia orjia ja voit kontrolloida niitä masterilla

# a) Kaksi vkonetta

Tein tämän viikon kansioon uuden kansion, jossa lähden tekemään tehtävää. Tein nanolla sinne Vagrantfilen johon loin kaksi konetta t001 ja t002. 

![eka](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/4bdcda05-2f49-4673-8b35-65ca96cc06da)

![file](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/7614fb6b-c2cd-4abb-a3fd-6e1108617ebd)

Tämän jälkeen ajoin VAGRANT UP komennon ja käynnistin koneet. Otin VAGRANT SSH t001 komennolla yhteyden t001 koneeseen ja pääsin sisään. Sisällä pingasin toista juuri luomaani t002 konetta komennolla PING 192.168.56.102 ja pingit onnistuivat.  

![ssht001](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/d9b8ac7f-1a64-4aec-967e-6929ee62b9eb)

![pingt002](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/75d50cab-16d0-44d2-b7fb-17171e284c55)

Pingin onnistuttua annoin EXIT ja kirjauduin koneesta ulos ja kirjauduin samalla VAGRANT SSH komennolla mutta loppuu vaihdoin toisen koneen nimen t002 ja pääsin koneeseen sisään. Annoin PING 192.168.56.101 komennon ja pingasin t001 konetta ja se onnistui.

![pingt001](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/ae9b39f1-57b7-4a9b-8c0b-218819e21614)

# b) Herra orja

Otin taas ssh yhteyden t001 koneeseen ja päätin, että teen siitä masterin. Päivitin sen SUDO APT-GET UPDATE komennolla ja asensin siihen salt-masterin komennolla SUDO APT-GET -Y ISNTALL SALT-MASTER. Tämän jälkeen kirjauduin exitillä ulos.

![eka](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/c7b0aece-0d59-4ce9-9a01-358a2939cf58)

![tok](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/bb46de11-cdf6-43b3-af9f-e8acccec395e)

Päätin tehdä t002 koneesta orjan joten otin siihen ssh yhteyden. Päivitin sen samalla update komennolla ja sen jälkeen asensin siihen salt-minionin komennolla SUDO APT-GET -Y INSTALL SALT-MINION.

![kol](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/1dfa16ca-6bb1-40ac-af70-17211d21185e)

![nel](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/f96197e1-0924-4c2a-aff4-30bf3417b99c)

Seuraavaksi komennolla SUDOEDIT /ETC/SALT/MINION editoin fileä ja laitoin sinne masterin ip osoitteen, joka on 192.168.56.101 ja tämän jälkeen käynnistin minionin uudestaan komennolla SUDO SYSTEMCTL RESTART SALT-MINION.SERVICE  ja kirjauduin ulos exitillä.

![vis](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/bd70a8b1-7faa-4390-8f61-bfe3d4b5f8dc)

![minionfile](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/ac780212-947e-403e-9148-47412ac034d6)

![kus](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/1a313fcb-fba5-4400-b454-624e524cc7f6)

Tämän jälkeen kirjauduin takaisin masterille eli t001 ja annoin komennon SUDO SALT-KEY -A ja hyväksyin avaimet ja testasin vielä SUDO SALT '*' CMR.RUN 'WHOAMI' komennolla, että se toimi.

![kk](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/182c1013-a2e5-479a-adfd-770eadf62b4e)

# c) Komentoja

Asensin orjalle apache2 serverin komennolla SUDO SALT '*' PKG.INSTALL APACHE2.

![apache](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/57087669-4e94-4ec3-8945-9f8268cc7742)


# e) Grain

Keräsin orjasta tietoa SUDO SALT '*' GRAINS.ITEMS komennolla ja SUDO SALT '*' GRAINS.ITEM VIRTUAL komennolla. 

![grain](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/b77bed75-c43c-4bbf-9f07-f7e8f0f2864d)

![virtual](https://github.com/JoonasKal/Palvelinten-Hallinta-Tehtvt/assets/104196551/df3d36a5-6fc7-46f6-92f1-e1bd5c7803dd)


# Lähteet: 

https://terokarvinen.com/2024/configuration-management-2024-spring/

https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

https://terokarvinen.com/2024/hello-salt-infra-as-code/
