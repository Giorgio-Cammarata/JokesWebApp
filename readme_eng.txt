---------------------------------------------------------------------
-GUIDE TO CREATE A WEB APP IN ASPNET Core MVC FROM SCRATCH (DEMO/LOCAL)
---------------------------------------------------------------------
Source of app development material:
-ASP.NET Core Crash Course - Shad Sluiter (Computer Science and Programming Professor)
---------------------------------------------------------------------

1 - Create an "ASPNET Core MVC" type project.

2 - Manually add/write model classes and define their properties.

3 - Add controllers, as follows:
	> folder Controllers > right button Add > Controller ...
	 > MVC Controller with views, using EF > click Add
	  > choose the model class (created before, one by one)
	  > Add "+" a Data context class > click Add
	  (Note: Controllers containing the REST web methods (CRUD) are generated from each Model,
	  and the razor pages Create/Delete/Details/Edit/Index in the Views folder).

4 - Open the Package Manager Console (PMC) and type the commands:
	PM> enable-migrations
	PM> Add-Migration "initialsetup"
	PM> Update-Database
	(Note: the DB was created starting from the classes -> CODE-FIRST approach;
	start the web app and manually go to the /jokes page).

5 - In the folder Shared > _Layout.cshtml add other Jokes/Search elements in the NAV bar.

6 - In the JokesController controller add a ShowSearchForm web method (which will have endpoint ../Jokes/ShowSearchForm)
	> right click on web method > Add View > Razor View, click Add (Add Razor View)
        > View name: ShowSearchForm
          Template: Create
          Model class: Joke
          Options: also select Create as a partial view (all flagged), click Add.

7 - Go to the newly created ShowSearchForm page and modify it as desired.

8 - Add a POST method to the JokesController: Jokes/ShowSearchResults, ShowSearchResult (string testoDaCercare),
    and filter the list of results via LINQ.

9 - Delete the JokeAnswer column from the main Index so as not to display them there, but only in the details section.

10 - It is very important for the security of the inputs in the forms, to add the [Authorize] attribute in the web methods.
     Specifically, in the JokesController, add [Authorize] to the "Create/Edit/Delete/DeleteConfirmed" web methods, that is:
      - "GET: Jokes/Create";
      - "POST: Jokes/Create";
      - "GET: Jokes/Edit/5";
      - "POST: Jokes/Edit/5";
      - "GET: Jokes/Delete/5";
      - "POST: Jokes/Delete/5".

11 - In the wwwroot folder, the css/js files can be edited to customize the pages as desired.