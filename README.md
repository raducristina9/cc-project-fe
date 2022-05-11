# cc-project-fe

link publicare:  https://infinite-basin-84424.herokuapp.com/

Introducere

Aplicatia dezvoltata de mine afiseza traseul dintre doua puncta alese de utilizator, distanta si durata. Informatiile sunt configurate pentru un drum cu masina, acesta a fost configurat folosind optiunea google.maps.TravelMode.DRIVING. Dupa ce utilizatorul afla care este timpul de deplasare, acesta poate trimite un mail pentru a seta o intalnire in locatia aleasa. Aplicatia isi propune sa ajute utilizatorii sa ajunga la timp in locatia dorita.
	API-urile folosite de mine sunt:
-	Maps JavaScript API , Places API, Geolocation API si Directions API pentru a putea incarca harta de la google maps si de afisa traseul dintre doua puncta. Places API are integrata o metoda, directionsService.route care primeste originea si destinatia si astfel calculeaza ruta facand un apel de tip GET. Apelul returneaza ruta, distanta si durata. Pentru a avea acces la serviciul furnizat de google maps a trebuit sa adaug in fisierul .env al proiectului un API KEY generat din google cloud platform.
-	
![image](https://user-images.githubusercontent.com/72069032/167889229-23efc97c-b445-46f9-ab08-1f9947d57b49.png)

![image](https://user-images.githubusercontent.com/72069032/167889251-0e11807e-0c04-48ca-9608-fc286e5c720f.png)

![image](https://user-images.githubusercontent.com/72069032/167889261-4c2004f9-58a8-4985-9fd3-db48f683aa0c.png)

Daca utilizatorul intoduce punctul de plecare si destinatia, apasa butonul calculeaza ruta, acesta prmeste inapoi traseul, timpul si distanta.

-	SendGrid este un serviciu cloud-based care se ocupa cu trimiterea de email-uri. Pentru a integra API-ul oferit de SendGrid intr-un proiect este necesar sa iti faci un cont direct pe pagina lor si sa generezi un API KEY care trebuie introdus in fisierul .env din proiect. Pentru a folisii functia de trimitere de email se apeleaza metoda sendMail care primeste ca si parametrii un nume de destinatar, email-ul destinatarului, email-ul celui care ii este adresat mail-ul, dar si un mesaj. Se face un apel de tip POST cu toate aceste informatii pe o ruta aleasa de noi.

 ![image](https://user-images.githubusercontent.com/72069032/167889296-86e041fe-c2bd-46d5-87a0-193ab39cdb72.png)

Fig 4- Apel sendGrid postman

Pentru a avea o evidenta a mail-urilor trimise aceastea sunt salavte in baza de date. Pentru a afisa toate mailu-rile putem sa facem un apel de tip GET.

 ![image](https://user-images.githubusercontent.com/72069032/167889311-988572c3-3e9e-4679-b383-8aaed3a085f9.png)

Fig 5- Apel get pentru toate mesajele

Baza de date folosita de mine este MySQL Workbench. Baza de date este formata dintr-o singura tabela in care sunt tinute toate informatiile introduse la trimiterea unui email.
![image](https://user-images.githubusercontent.com/72069032/167889344-c4ea5b67-1b5e-43df-a2df-09f27d060858.png)
Pentru a vedea care sunt toate datele din baza de date putem face un SELECT * FROM meetinginfo;

![image](https://user-images.githubusercontent.com/72069032/167889507-07023580-61c1-4273-9950-5f20588eec09.png)

Pentru a accesa integrarea API-ului de la SendGrid din aplicatie trebuie sa apasam, dupa calcularea rutei, butonul mai departe. 
Suntem redirectionati intr-o pagina unde putem sa completam campurile pentru a trimite  mail-ul.
![image](https://user-images.githubusercontent.com/72069032/167889553-3d013c9c-9d29-4a65-aaf1-9919ce41281c.png)

Dupa compltarea capului se apasa apelul trimite. Pentru a trimite un mail este necesara competarea tuturor campurilor, altfel este afisata o notificare care anunta utilizatorul ca nu a completat totul.
![image](https://user-images.githubusercontent.com/72069032/167889568-eb61fc04-40e3-40f8-8225-a70a4d71d356.png)

Pe langa posibilitatea de a trimite amil-uri, utilizatorul poate sa se intoarca la harta sau sa vada in ce locatii se mai intalnesc alti useri, accesand butoanele denumite specific. 

Interfata

Partea de design este facuta cu ajutorul librariei Chakra Ui.

Pagina are un Navbar unde este prezent numele aplicatiei, dar si un avatar care se deschide si un buton care schimba pagina pe tema de noapte.
![image](https://user-images.githubusercontent.com/72069032/167889606-d2ed5fa1-2fab-4ee7-9d76-52ca5d584835.png)
![image](https://user-images.githubusercontent.com/72069032/167889619-b971f246-eeba-4a7d-a465-059b35d4f688.png)
![image](https://user-images.githubusercontent.com/72069032/167889645-ec310602-78cd-4316-b9ac-10e234c01fcf.png)


Afisarea datelor din baza de date se face accesand butonul “Afiseaza ultimele locatii”. Aici este folosit apelul de tip GET pentru toate mesajele (fig 5). In baza de date se gasesc si date de test. Si in aceasta pagina este vizibil Navbarul. Tema intunecata este persistenta intre pagini.
![image](https://user-images.githubusercontent.com/72069032/167889678-ec5e0d97-1c39-44d8-8dda-b565cc294e3d.png)

Referinte

https://chakra-ui.com/
https://developers.google.com/maps/documentation
https://docs.sendgrid.com/



