3) MVVM erottaa UI:n (View) logiikasta (ViewModel) ja datasta (Model). ViewModel hallitsee tilaa ja liiketoimintalogiikkaa,
jolloin Compose UI pysyy yksinkertaisena ja reaktiivisena.
   
StateFlow on Coroutine-pohjainen tilavirta, joka säilyttää viimeisimmän arvon ja emittoi muutokset.
Compose voi kuunnella sitä collectAsState() avulla, jolloin UI päivittyy automaattisesti.

2) Miten Compose-tilanhallinta toimii:
- Compose-tilanhallinta perustuu reaktiivisuuteen: UI päivittyy automaattisesti aina, kun siihen liittyvä tila muuttuu.
- Tila voidaan säilyttää paikallisesti remember-funktiolla tai pidempään ViewModelin avulla.

Miksi ViewModel on parempi kuin pelkkä remember:
- ViewModel säilyttää datan sovelluksen elinkaaren yli, esim. ruudun kierron yhteydessä.
  Se pitää logiikan erillään käyttöliittymästä, mikä tekee koodista selkeämpää ja helpommin ylläpidettävää.
  Composables voivat seurata ViewModelin tilaa reaktiivisesti, jolloin UI päivittyy automaattisesti muutosten yhteydessä.
  
1) Sovelluksessa käytetään Task-data classia, joka sisältää seuraavat kentät:
- id: yksilöllinen tunniste
- 
- title: tehtävän nimi
- description: tehtävän kuvaus
- priority: tehtävän tärkeys
- dueDate: eräpäivä merkkijonona
- done: boolean, onko tehtävä valmis

Funktiot:
- addTask(list, task): List<Task> - lisää uuden tehtävän listan loppuun ja palauttaa uuden listan
- toggleDone(list, id): List<Task> - vaihtaa tehtävän done-tilan TRUE FALSE
- filterByDone(list, done): List<Task> - palauttaa listan, jossa näkyvät vain done-tilassa olevat tehtävät
- sortByDueDate(list): List<Task> - palauttaa listan, joka on järjestetty eräpäivän mukaan
