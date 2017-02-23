**Channel list’i eesmärk**

Helirezissööri tööle keskendunud vaade, genereeritud raideri põhjal. Info struktuur põhineb helipuldi kanalitel. Täpsemalt, igale kanalile helipuldil seatakse vastavusse raideris olev istrument või instrumendi osa.

**Kasutajad**

Peamine on soundengineer rollis projektikasutaja. See roll antakse kasutajatele "raideri kasutajate haldamise" kasutusloo juures. (Vt. raideri spec). Soundengineeril on õigused channel listi lugeda, muuta.

**Olemid+atribuudid**

Channel_list (name,FOH_contact, Monitoring_contact)

Channel (number, instrumentk, mikrofon, stand, FOH insert)

**Põhiolemid, alamolemid**

Channel_list

	Channel

**Sündmused ajas, mis mõjutavad channel list’i**

**Seosed teiste registritega**

Users - 1...n - Üks channel_list on seotud vähemalt ühe kasutajaga (projekti looja st admin). Saab olla jagatud enamate kasutajate vahel. Tüüpiliselt on jagatud lisaks sound_engineerile. Igal kasutajal on 

Stage plan - 1 - Iga channel_list on seotud stageplaniga (läbi raideri enda).

Raider- 1 - Iga raider on seotud ühe channel listiga.

Rights 1...n  - Igal kasutajal on teatud õigused channel listi suhtes suhtes (lugemine, muutmine, loomine või kombinatsioon nendest). 

Invite - 0...n - Igal channel list võib olla seotud invite’tega, mis saadetud välja kasutajatele, keda soovitakse siduda antud channel listiga.

Project 1 - Iga channel list on seotud projektiga (läbi raideri).

**Kasutusjuhud+kasutajad+eesmärk+vaade+kirjeldus**



	Süsteemi poolt teostatav automaatne toiming

		Vastavalt raideri andmetele transformeerida andmed heliinsenerile sobivasse kujju.

			Toimub automaatselt raideri lisamisel esmakordselt projekti. Hiljem, kui lisatakse teine raider ja eelnevalt on olemas juba channel list, siis küsitakse kasutajalt, kas soovitakse "overwrite’ida" olemasolevat channel listi.

Näide:

1. Kasutaja loob projekti ja lisab projekti raideri

2. Süsteem genereerib automaatselt channel listi

3. Kasutaja saab channel listi muuta (kasutusjuht eraldi allpool). Kui on juba tehtud muudatused channel listis, siis saab tagasi revertida vajadusel.

Reeglid transformatsioonil:

1. Igale pillile raideris seatakse vastavusse n-arv kanaleid channel listis koos vastavate alamintrumentidega. Nt. trumm raideris jaotub nt. soolotrummiks, basstrummiks, OH, tommideks.

2. Kanalite arv on helipultidel piiratud. Lähtudes kanalite arvust süsteem genereerib optimaalse lahenduse, et pillid ja kanalid saaksid kaetud. Nt. kui on kanaleid 8 vs 16, siis 8 kanaliga puhul trummi puhul eraldi tomme igale kanalile ei seata.

3. Igal kanalil seatakse vastavalt temal olevale instrumendile/instrumendiosale vastavuse stand. Nt. kui on basstrumm, siis vaikimisi süsteem seab vastavusse talle mini-standi.

Channel listi algoleku taastamine (revert to default)

	Projektilooja, admin õigustega kasutaja, heliinsener (kasutaja, kellel on "muutmisõigused").

		Kasutaja saab taastada algse seisundi channel list’is (peale raideri lisamist projekti). Taoline vajadus võib tekkida, kui kasutaja ei soovi enda poolt tehtud muudatusi üldse.

			infovaade: selleks on nupp "Revert to default" vms channel listi vaates

Näide:

1. 

2. Kasutaja vajutab "revert to default"

3. Süsteem küsib kinnitust

		

Channel listi share’imine

Võimalus süsteemist välja eksportida pdf kujul channel list.

Infovaade: funktsionaalsus on channel listi vaates. Channel listi jagamine toimub PDF kujul.

Channel listi muutmine

	Admin õigustega kasutaja, sound engineer õigustega kasutaja

		Channel listi kohandamine vastavalt soovile; algse raiderist tuleneva teisenduse ümbertegemine. Protsess sarnane ise raideri tabeli. muutmisele.

			Infovaade: channel listi vaade

Täpsemalt:

2. Väljade nagu instrument, mikrofon, stand sisu saab valida dropdown’ist, millele toeks input field, mis aitab tulemusi filteerida. 

3. Veergude mikrofon ja stand puhul sama sisestusmehhanism, küll aga ei ole kohustuslik sisestada.





* **Sound engineer**** näeb ka bändi raiderit, AGA talle tehakse bändi raiderist süsteemi poolt automaatselt koopia see tähendab, et ta ei muuda bändi raiderit!!!! Kui muudatused on tehtud, siis sound engineer saab saata koopia bändile (vajadusel) ehk shareda vastu neile.** 

* **sound engineer saab kaks raiderit kokku tõsta ühe sound engineer tabeli alla**
