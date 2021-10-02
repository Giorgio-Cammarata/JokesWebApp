---------------------------------------------------------------------
-GUIDA PER CREARE DA ZERO UNA WEB APP IN ASPNET Core MVC (DEMO/LOCALE)
---------------------------------------------------------------------
Fonte del materiale per lo sviluppo dell'app:
-ASP.NET Core Crash Course - Shad Sluiter (Computer Science and Programming Professor)
---------------------------------------------------------------------

1 - Creare un progetto di tipo "ASPNET Core MVC".

2 - Aggiungere/scrivere manualmente le classi model e definirne le proprietà.

3 - Aggiungere i controller, come segue:
	> folder Controllers > tasto dx Add > Controller...
	 > MVC Controller with views, using EF > click Add
	  > scegliere la model class (creata prima, una per una)
	  > Aggiungere "+" una Data context class > click Add
	  (Nota: da ogni Model vengono generati i Controller contenenti i web method REST (CRUD),
	  e le razor page Create/Delete/Details/Edit/Index nella folder Views).

4 - Aprire la Package Manager Console (PMC) e digitare i comandi:
	PM> enable-migrations  
	PM> Add-Migration "initialsetup"
	PM> Update-Database
	(Nota: il DB è stato creato a partire dalle classi -> approccio CODE-FIRST;
	avviare la web app e andare manualmente nella pagina /jokes).

5 - Nella folder Shared > _Layout.cshtml aggiungere nella NAV bar altri elementi Jokes/Search.

6 - Nel controller JokesController aggiungere un web method ShowSearchForm (che avrà endpoint ../Jokes/ShowSearchForm)
	> click tasto dx sul web method > Add View > Razor View, click Add (Add Razor View)
     	> View name: ShowSearchForm
       	  Template: Create
       	  Model class: Joke
          Options: selezionare anche Create as a partial view (tutte flaggate), click Add.

7 - Andare nella page appena creata ShowSearchForm e modificarla a piacere.

8 - Aggiungere al JokesController un metodo POST: Jokes/ShowSearchResults, ShowSearchResult(string testoDaCercare),
    e filtrare la lista dei results tramite LINQ.

9 - Eliminare dalla Index principale la colonna delle JokeAnswer in modo da non visualizzarle lì, ma solo nella sezione details.

10 - E' molto importante per la sicurezza degli input nei form, aggiungere l'attributo [Authorize] nei web method. 
     Nello specifico, nel JokesController, aggiungere [Authorize] ai web method "Create/Edit/Delete/DeleteConfirmed", ovvero: 
      - "GET: Jokes/Create";
      - "POST: Jokes/Create";
      - "GET: Jokes/Edit/5";
      -	"POST: Jokes/Edit/5";
      -	"GET: Jokes/Delete/5";
      -	"POST: Jokes/Delete/5".

11 - Nella folder wwwroot, i file css/js possono essere modificati per customizzare le pagine a piacere.



