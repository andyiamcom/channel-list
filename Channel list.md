**Channel list’i eesmärk**

Helirezissööri tööle keskendunud vaade, genereeritud raideri põhjal. Info struktuur põhineb helipuldi kanalitel. Täpsemalt, igale kanalile helipuldil seatakse vastavusse raideris olev istrument või instrumendi osa.

**Kasutajad**

Peamine on soundengineer rollis projektikasutaja. See roll antakse kasutajatele "raideri kasutajate haldamise" kasutusloo juures. (Vt. raideri spec). Soundengineeril on õigused channel listi lugeda, muuta.Admin õigustega kasutaja saab samamoodi lugeda, muuta.

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

Esmane channel listi genereerimine

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

1. Kui hakatakse tegema muudatusi ja need muudatused on erinevad algselt süsteemi poolt geneeeritud channel list’st, siis tekib võimalus (lisafunktsionaalsus) taastada algne seis.

2. Kasutaja vajutab "revert to default"

3. Süsteem küsib kinnitust

		

Channel listi share’imineKõik kasutajad, kellel channel listi suhtes lugemisõigus

Võimalus süsteemist välja eksportida pdf kujul channel list.

Infovaade: funktsionaalsus on channel listi vaates. Channel listi jagamine toimub PDF kujul.

Channel listi muutmine

	Admin õigustega kasutaja, sound engineer õigustega kasutaja

		Channel listi kohandamine vastavalt soovile; algse raiderist tuleneva teisenduse ümbertegemine. Protsess sarnane ise raideri tabeli. muutmisele.

			Infovaade: channel listi vaade

Täpsemalt:1. Channel listi numbreid ei saa muuta, need on süsteemi poolt fikseeritud jadamisi.

2. Väljade nagu instrument, mikrofon, stand sisu saab valida dropdown’ist, millele toeks input field, mis aitab tulemusi filteerida. Näiteks sisestades instrument fieldi "kitarr", siis süsteem pakub erinevaid kitarri variante (basskitarr, elektrikitarr jne), millest kasutaja valib dropdown menüüst sobiva. Kasutaja sisestada ka vabas vormis pilli. Sel juhul on ta “other” tüüpi süsteemi jaoks ja ei saa olla aluseks stageplani koostamiseks. Aluseks on see, kas kasutaja poolt sisestatud pilli nimi kattub süsteemis oleva pilli nimega. 

3. Veergude mikrofon ja stand puhul sama sisestusmehhanism, küll aga ei ole kohustuslik sisestada.NB! Tabelis olevaid ridu saab liigutada ülesalla üksida ja koos teiste ridadega. -  Juhul kui liigutan ühte eset, siis teised peavad sellega koos kaasa liikuma (näiteks saan valida kolm eset ja neid korraga liigutada). NB! Kui koos ridasid liigutada, siis saab liigutada järjestikku olevaid ridasid.NB! Tabelisse saab lisada juurde ka uusi veerge.

NB! Sisestamisloogika on sarnane Excelile -  saan tab’iga edasi liikuda, Enteriga uut rida tekitada. Juhul kui olen rea lõpus ja vajutab tab tekitatakse mulle uus rida uuesti juurde. Ei pea kasutama hiir, et tabelit täita!

NB! Kogu protsessi jooksul toimub automaatne salvestamine. Küll aga on olemas undo võimalus. Kasutajaliideses selleks vastav funktsioon.

* **Sound engineer**** näeb ka bändi raiderit, AGA talle tehakse bändi raiderist süsteemi poolt automaatselt koopia see tähendab, et ta ei muuda bändi raiderit!!!! Kui muudatused on tehtud, siis sound engineer saab saata koopia bändile (vajadusel) ehk shareda vastu neile.** 

* **sound engineer saab kaks raiderit kokku tõsta ühe sound engineer tabeli alla**

