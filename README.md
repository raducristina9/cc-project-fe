# cc-project-fe

link publicare:  https://infinite-basin-84424.herokuapp.com/

Introducere

Aplicatia dezvoltata de mine afiseza traseul dintre doua puncta alese de utilizator, distanta si durata. Informatiile sunt configurate pentru un drum cu masina, acesta a fost configurat folosind optiunea google.maps.TravelMode.DRIVING. Dupa ce utilizatorul afla care este timpul de deplasare, acesta poate trimite un mail pentru a seta o intalnire in locatia aleasa. Aplicatia isi propune sa ajute utilizatorii sa ajunga la timp in locatia dorita.
	API-urile folosite de mine sunt:
-	Maps JavaScript API , Places API, Geolocation API si Directions API pentru a putea incarca harta de la google maps si de afisa traseul dintre doua puncta. Places API are integrata o metoda, directionsService.route care primeste originea si destinatia si astfel calculeaza ruta facand un apel de tip GET. Apelul returneaza ruta, distanta si durata. Pentru a avea acces la serviciul furnizat de google maps a trebuit sa adaug in fisierul .env al proiectului un API KEY generat din google cloud platform.

Daca utilizatorul intoduce punctul de plecare si destinatia, apasa butonul calculeaza ruta, acesta prmeste inapoi traseul, timpul si distanta.

-	SendGrid este un serviciu cloud-based care se ocupa cu trimiterea de email-uri. Pentru a integra API-ul oferit de SendGrid intr-un proiect este necesar sa iti faci un cont direct pe pagina lor si sa generezi un API KEY care trebuie introdus in fisierul .env din proiect. Pentru a folisii functia de trimitere de email se apeleaza metoda sendMail care primeste ca si parametrii un nume de destinatar, email-ul destinatarului, email-ul celui care ii este adresat mail-ul, dar si un mesaj. Se face un apel de tip POST cu toate aceste informatii pe o ruta aleasa de noi.

 
Fig 4- Apel sendGrid postman

Pentru a avea o evidenta a mail-urilor trimise aceastea sunt salavte in baza de date. Pentru a afisa toate mailu-rile putem sa facem un apel de tip GET.

 
Fig 5- Apel get pentru toate mesajele

Baza de date folosita de mine este MySQL Workbench. Baza de date este formata dintr-o singura tabela in care sunt tinute toate informatiile introduse la trimiterea unui email.

Pentru a vedea care sunt toate datele din baza de date putem face un SELECT * FROM meetinginfo;

Pentru a accesa integrarea API-ului de la SendGrid din aplicatie trebuie sa apasam, dupa calcularea rutei, butonul mai departe. 
Suntem redirectionati intr-o pagina unde putem sa completam campurile pentru a trimite  mail-ul.

Dupa compltarea capului se apasa apelul trimite. Pentru a trimite un mail este necesara competarea tuturor campurilor, altfel este afisata o notificare care anunta utilizatorul ca nu a completat totul.

Pe langa posibilitatea de a trimite amil-uri, utilizatorul poate sa se intoarca la harta sau sa vada in ce locatii se mai intalnesc alti useri, accesand butoanele denumite specific. 

Interfata

Partea de design este facuta cu ajutorul librariei Chakra Ui.

Pagina are un Navbar unde este prezent numele aplicatiei, dar si un avatar care se deschide si un buton care schimba pagina pe tema de noapte.

Afisarea datelor din baza de date se face accesand butonul “Afiseaza ultimele locatii”. Aici este folosit apelul de tip GET pentru toate mesajele (fig 5). In baza de date se gasesc si date de test. Si in aceasta pagina este vizibil Navbarul. Tema intunecata este persistenta intre pagini.
Referinte

https://chakra-ui.com/
https://developers.google.com/maps/documentation
https://docs.sendgrid.com/

Pozele sunt incarcate in variante .pdf de pe online.ase

