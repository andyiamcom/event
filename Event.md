**Kasutajad**

* Projektilooja - loob, haldab projektiga seotud evente. Admin õigustega.Collaboratorid:

* Band - omab vaikeõiguseid eventiga seotud oma raideri osas (nt raideri lisamine eventi), näeb eventiga seotud infot

* SndEng - omab vaikeõigusi eventiga seotud raideri osas (channel list ehk sound engineers view)

**Olemid, atribuudid**

Event 

title, date, location, starred_yesno, author, archieved_yesno...

Event_bands

band_name, band_starttime, band_endtime

Event_raidersEvent_collaborators

**Põhilised sündmused ajas**

Eventi algusaja lähenemine - nt. paar päeva ennem eventi algust saab projektilooja (keegi, kellel on admin õigused) keelata ära muudatuste tegemise event’is projekti collaborator’itel.

Eventi algusaeg saabumine - event omandab uue süsteemse staatuse (abiks eventide ja projetktide sorteerimisel library vaates)

Eventi lõpp - saab uue staatuse - "lõpp". 

**Seosed teiste registritega**

Projekt - iga projekt on 1 või mitme evendiga seotud.

Bandid - bandid on seotud eventidega. Ühel evendil on 0...n bandi.

Invite - on seotud eventi, projetkiga ning kasutajatega

Raider - raider on seotud 0...n eventiga



**KASUTUSLOOD****Eventi loomine**

Kes: projektilooja

		Üldkirjeldus: projekti detailvaates saab lisada projektile evente, mis selle projektiga seostuvad. Evente saab luua projekti omanik. Temal on õigused hallata projekti üldparameetreid ja kutsuda juurde collaboratoreid (bande, helirežissööre) ja anda neile õigusi. Kui luuakse uus projekt, siis automaatselt seotakse ühe projektiga ka 1 event.  Saab lisada juurde rohkem. Igale eventile on projektivaates üks tab.

--------------------------------

Tüüpiline kasutusjuht, kuidas luuakse projekti ja eventi.****

* Kasutaja logib

* Library's klikkab projektiloomise ikoonidele või teeb seda sidebar'ilt

* Sisestab projektinime dialoogiaknasse

* Avaneb uus tühi loodud projekt. Avanenud aknas saab sisestada 

    * kas koosneb ühest või mitmest eventist (vaikimisi on üks, null ei saa olla). Antud juhul kasutaja loob projekti, mis koosneb ühest evendist. 

    * kas on tähitud (starred)

    * üldkommentaarid projekti kohta

    * määrab projekti algusaja (juhul, kui projekt koosneb 1 evendist) või ajavahemiku (kui projekt koosneb mitmest evendist)

Juhul, kui luuakse evente juurde, siis nende eventide jaoks on eraldi tab’id (vaated). Seal on võimalik määrata eraldi nendele

eventide kohta käivat infot (info tuleb).

* Avab event’i tab’i. Seal sisestab eventiga seotud andmed 

    * Toimumiskoht (google maps API)

    * Aeg ja kellaajavahemik

    * Kas on olemas lokaalne (ürituse poolt) sound engineer. Projetkilooja saab määrata, kes on see süsteemis (autocomplete abil saab otsida kasutaja).

* Eventi tab’il kutsub juurde bändid.

    * Avaneb otsinguvaade, kust saab otsida süsteemist kasutajaid. Antud juhul huvitab korraldajat kasutajad, kellel on mainrole="artist/band". Kasutaja saab sisestada kõik võimalikud parameetrid kasutaja kohta - koht, nimi, on tal email, on tal pilt, on tal website...

    * Kasutaja valib otsingutulemustest ühe või mitu kasutajat. Kirjutab juurde invite’i sõnumi (a la - "Meil tulemas selline kontsert. Mõtlesime, et tulge bändiga esimena. Vaadake, kas teil on huvi".) Klikib invite.

Invite’tud bandid jäävad event’i tabil seisundisse "peding, waiting" vms. Event’i tab’il on näha rida - 

artist, rider name (juhul kui rider bändi poolt saab uploaditud, kui ei ole uploaditud siis "not uploaded"), status ( waiting for accept, raider uploaded, raider missing vms)

——————————————————————————————————————

* Bänd logib süsteemi sisse.

* Talle on teade -> projekt nimega …. loodud korraldaja … poolt kutsub teid liituma eventiga .... Soovite?"

* Kasutaja valib jah.

* Projektide alla library’sse tekib kasutajale projekt, millesse teda invite’i.

* Kasutaja avab antud projekti.

* Sealt kasutaja näeb projekti eventi, millesse teda täpselt kutsuti. 

    * Kes kutsus, millal event toimub, kus kohas, mis on projektilooja notification ("Meil tulemas selline kontsert. Mõtlesime, et tulge bändiga esimena. Vaadake, kas teil on huvi"), kas on olemas lokaalne helirezissöör (seda määras projektilooja eventi üldparameetrite all)

* Bänd paneb staatuse accept.

* Nüüd on bändil ligipääs projekti.

* Eventi üldvaates, millesse bändi kutsuti, on bändil rohkem võimalusi asju määrata.

    * Bänd määrab, kas tal on helirezissöör olemas endal, kumbat helirezissööri ta eelistab - kas enda või lokaalset (juhul, kui on lokaalne).

    * Saab uploadida raideri

    * Saab otsida süsteemikasutajatest helirezissööre, keda eventiga liidestada. Otsinguprotsess analoogne sellele, kus projektikorraldaja otsis eventile bandi (autocomplete). Saab saata helirezissöörile notificationi ("Tuleb selline event. Tahad tulla ja teha soundi?" vms)

* Soundengineer logib süsteemi sissse. Näeb, et on tulnud library vaatesse invite sisuga "Kasutaja….saatis kutse liituda eventiga …:  Tuleb selline event. Tahad tulla ja teha soundi?. Accept?")

* Soundengineer vajutab accept

* Nüüd on kõigil kolmel osapoolel näha, kes mida projektis saab teha ja teeb. 

* ...Event tuleb…(eventi muutmine, kustutamine, raideri lisamine jm kasutuslood siin)Event möödub.

* Event omab uue staatuse - möödunud.

**Eventide nimekiri, eventi detailandmete vaatamine projektis**

	Kes saavad: kõik kasutajad

		Projektilooja näeb oma projektis kõiki evente. Band näeb projektis, millega ta on liitunud, kõiki evente. Samas spetsiifilist eventi informatsiooni (algusajad, lõppajad, message’d projektijuhiga) näeb ta eventis, millega ta on liitunud. Teiste projektis olevate eventide kohta näeb üldist eventiinfot. 

Infovaade: eventide nimekirja näeb projekti üldvaates, sealt saab minna ka detailvaatesse.

---------------

Näiteks, kus võib vaja minna:

* Projektijuht on loonud evendi, lisanud sinna collaboratorid, andnud neile õigused (õiguste halduse kasutuslugu)

* ....Eventi tähtaeg läheneb.

* Bändil on soov näha, mis ajal ta ntx esineb või ntx on soov teha viimase hetke muudatusi raideris.

* Selleks avab ta library

* Seal on kõik tema projektid

* Sorteerib projektid tähtaja järgi. Nüüd näeb ta lähenevat projekti esimesena.

* Avab projekti, mille eventi kohta ta soovib detailsed infot.

* Projektis on palju evente. Seal ta näeb detailandmeid ainult eventi kohta, mille collaborator ta on. St kas bandina või helirežissöörina. Teiste kohta on ainult üldandmed - millal, kus ….

* Avab eventi detailvaate.

* Siin saab muuta ja lugeda oma andmeid, mis käivad projekti kohta. Samuti saab muuta raiderit jne.

    * On teatud reeglid. Nt. kui muuta raiderit kaks päeva ennem üritust, siis see eeldab projektijuhi kinnitust. 

    * Muudatused, mis on olulised (nt. muudeti raiderit) ja/või tehakse muudatusi bandi poolt liiga hilja st. paar päevan ennem kontserti, saadetakse notificationi kujul näol ka projektiloojale. 

* Projektilooja näeb teateid, kui logib sisse.

    * Osad muudatused võib nõuda projektijuhi kinnitust. Ntx raideri muutmine jne.

**Eventide tähistamine (starred)**

Kes saavad - kõik kasutajad	

		Iga kasutaja saab temaga seostatud projekti (kas looja või osaline projektis)

ära märgistada oluliseks (starred). Tähistatud projekte saab eraldi vaadata nimekirjana library vaates. 

		Infovaated: tähistada saab eventi detailvaates, eventide nimekirjas projekti üldvaates, library vaates.

---------------------------

Näiteks:

* Kasutaja soovib märgistada temale vajalikku eventi, kuna on veel esitamata raider või näiteks bandi poolt esitatud andmed on veel puudulikud.

* Valib selleks library vaates, sidebar’ilt või otsingust otsides projekti, mis sisaldab soovitud eventi.

* Avanenud projektidetailvaatest avab event’i tabi, kust saab event’i ära tähistada..

**Eventi muutmine**

	Kes saavad - kõik kasutajad

		Kõige suuremad võimalused projektiloojal. Projektilooja admin õigustega. Tema saab hallata eventiga seotud andmeid. Nt lisada, kustutada bande. Teistel collaboratoritel - bandil, sound engineeril - on eventi suhtes piiratud õigused. Nt saab lisada oma raiderit, hallata  sound engineer viewi’, kuid ei saa muuta eventi üldandmeid.

			Infovaade: toiminguid tehakse eventi detailvaates

--------------------------

Näiteks eventi muutmine bandide osas:

* Projektilooja tahab lisada bände, kes on seotud ühe projektiga.

* Selleks projekti üldvaate.

* Avanenud projektivaates avab eventi.

    * Kõik bandi ja evente seostavad toimingud saavad notifikatsiooni. 

    * Lisades nt bändi eventi, saab bänd süsteemis teate. Teate sisu kirjeldab, et kasutaja …. soovib teid lisada üritusele … Kas soovite?

    * Või kui näiteks band eemaldatakse ürituselt, siis samuti bandi kasutaja saab sõnumi - Kasutaja …. eemaldas teid ürituselt…

* Sõltuvalt sellest, mida tehti, võib osa notifikatsioone eeldada bändilt või sound engineerilt confirmvastust (jah/ei).

* Nt lisades collaboratoreid üritusele, on igal collaboratoril teatud vaikeõigused. Õiguseid on võimalik muuta õiguste tab’is.

**Eventi ****kustutamine**

Projektilooja

	Saab kustutada projektis olevaid evente. See õigus ainult projektiloojal, kellel admin õigused. 

		Infovaade: projekti üldvaates, samuti eventi detailvaates saab kustutada.

--------------------

Näiteks:

* Projektilooja tegi projekti eventi, kuid selgus,et  see on üleliigne. Samas bändid ja muud event’iga seotud andmed on event’i lisatud. 

* Projektilooja kustutab eventi, lisades juurde põhjenduse.

* Eventi kustutamisel saavad projektis olevad collaboratorid vastava teate. ("Projekti…. event …. on kustutatud kasutaja … poolt põhjusega….")

    * Eventi kustutamisel kustutatakse süsteemist ka kõik sellega seotud objektid - raiderid, lavaplaanid jne.

**Eventi**** collaboratite (bandid, soundengineerid) lisamine**

projektilooja, band

	Projektilooja saab lisada bande,soundengineer’e  eventi. Band saab ka ise lisada soundengineeri projekti. 

		Infovaade: Eventi detailvaates teostatakse 

------------------------------

Täpsemalt:

* Projektilooja on admin õigustega. See tähendab kõige suuremaid õigusi projekti suhtes. 

* Projektilooja saab määrata teisi süsteemi kasutajaid eventi.

* Igal projekti kaasliikmel - collaboratoril - on omad õigused. 

* Lisades collaboratori, näiteks bandi, võime anda ka talle admin õiguseid (õiguste haldamise kasutuslugu). See tähendab, et ka tema saab lisada kaaskasutajaid.

* Collaboratorite lisamine toimub **autocomplete** alusel. St. emaili põhjal.

* Iga kollaborator saab süsteemis vastava notifikatsiooni. Eeldab kasutaja poolset kinnitust.

	

**Raideri lisamine eventi**

Kes saavad: projektilooja, band

Band lisab eventile, millega ta on liitunud, raideri. Projektilooja aktsepteerib bandi poolt lisatud raideri. Samuti saab raidereid lisada admin õigustega kasutaja (nt. projektilooja).

	infovaade: eventi detailvaates teostatakse.

--------------------------

Täpsemalt:

* Raideri lisamine kasutaja poolt tähendab selle süsteemset kopeerimist. Iga event sisaldab kopeeritud raiderit. See tähendab, et iga raider on sõltumatu ja muudatused ei kajastu bandi originaalraideril.

* Samuti on sõltumatud stage plan ja teised raideriga seotud objektid.

*Venue parameetrite **määramine** eventile*

*projektilooja*

*	Saab määrata evendile venue parameetrid. See oleks aluseks raideri vaates stageplani geneerimisele, lähtudes venue parameetritest ja raideris olevatest pillidest.*

*		Infovaade: eventi detailvaade*

*Eventi **sheerimine*

*projektilooja, **soundeng, band*

*	Võimalus eksportida süsteemist välja projekt (pdf kujul ntx)*

*		infovaade: projekti detailvaade*

*Bändi soov liituda eventiga*

*projektilooja, band*

*	Band esitab taotluse projektiloojale liitumaks eventiga. Projektilooja aktpsepteerib või mitte.*

*		Infovaade: avalike eventide nimekiri*-----

