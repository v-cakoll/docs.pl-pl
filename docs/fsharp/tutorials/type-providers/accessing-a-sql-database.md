---
title: "Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów (F#)"
description: "Informacje o sposobie użycia dostawcy typów SqlDataConnection (LINQ to SQL) w F # 3.0 do generowania typów bazy danych SQL, jeśli masz połączenie z bazą danych na żywo."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: dbc5d889fb7883b4327180fdf34accf45bf519e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="41711-104">Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów</span><span class="sxs-lookup"><span data-stu-id="41711-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="41711-105">Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="41711-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="41711-106">Zobacz [FSharp.Data](https://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.</span><span class="sxs-lookup"><span data-stu-id="41711-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="41711-107">Linki odwołań interfejsu API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="41711-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="41711-108">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="41711-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="41711-109">W tym przewodniku opisano sposób korzystania z dostawcy typów SqlDataConnection (LINQ to SQL) dostępnym w F # 3.0 do generowania typów danych w bazie danych SQL, jeśli masz aktywne połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="41711-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="41711-110">Jeśli nie masz aktywne połączenie z bazą danych, ale masz LINQ do SQL schematu pliku (DBML), zobacz [wskazówki: generowanie typów F #, pliku DBML](generating-fsharp-types-from-dbml.md).</span><span class="sxs-lookup"><span data-stu-id="41711-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="41711-111">W tym przewodniku przedstawiono następujące zadania.</span><span class="sxs-lookup"><span data-stu-id="41711-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="41711-112">Te zadania odbywa się w następującej kolejności wskazówki powiodła się:</span><span class="sxs-lookup"><span data-stu-id="41711-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="41711-113">Trwa przygotowywanie bazy danych testu</span><span class="sxs-lookup"><span data-stu-id="41711-113">Preparing a test database</span></span>

- <span data-ttu-id="41711-114">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="41711-114">Creating the project</span></span>

- <span data-ttu-id="41711-115">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="41711-115">Setting up a type provider</span></span>

- <span data-ttu-id="41711-116">Wykonywanie zapytań dotyczących danych</span><span class="sxs-lookup"><span data-stu-id="41711-116">Querying the data</span></span>

- <span data-ttu-id="41711-117">Praca z polami wartości null</span><span class="sxs-lookup"><span data-stu-id="41711-117">Working with nullable fields</span></span>

- <span data-ttu-id="41711-118">Wywoływanie procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="41711-118">Calling a stored procedure</span></span>

- <span data-ttu-id="41711-119">Zaktualizowanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-119">Updating the database</span></span>

- <span data-ttu-id="41711-120">Wykonywanie kodu języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41711-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="41711-121">Przy użyciu kontekstu danych</span><span class="sxs-lookup"><span data-stu-id="41711-121">Using the full data context</span></span>

- <span data-ttu-id="41711-122">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="41711-122">Deleting data</span></span>

- <span data-ttu-id="41711-123">Tworzenie testowej bazy danych (w razie potrzeby)</span><span class="sxs-lookup"><span data-stu-id="41711-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="41711-124">Trwa przygotowywanie bazy danych testu</span><span class="sxs-lookup"><span data-stu-id="41711-124">Preparing a Test Database</span></span>
<span data-ttu-id="41711-125">Na serwerze, na którym działa program SQL Server Utwórz bazę danych do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="41711-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="41711-126">Można użyć bazy danych Utwórz skrypt u dołu tej strony w sekcji [tworzenia bazy danych testu](#creating-a-test-database) w tym celu.</span><span class="sxs-lookup"><span data-stu-id="41711-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="41711-127">Aby przygotować testowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-127">To prepare a test database</span></span>

<span data-ttu-id="41711-128">Aby uruchomić skrypt tworzenia mojabazadanych, otwórz **widoku** menu, a następnie wybierz pozycję **Eksplorator obiektów SQL Server** lub wybierz polecenie Ctrl +\, klawiszy Ctrl + S.</span><span class="sxs-lookup"><span data-stu-id="41711-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="41711-129">W **Eksplorator obiektów SQL Server** okna, otwórz menu skrótów odpowiednie wystąpienie, wybierz pozycję **nowe zapytanie**, skopiuj skrypt u dołu tej strony, a następnie wklej skrypt do edytora.</span><span class="sxs-lookup"><span data-stu-id="41711-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="41711-130">Aby uruchomić skrypt SQL, wybierz ikony paska narzędzi trójkątny znak lub klawiszy Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="41711-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="41711-131">Aby uzyskać więcej informacji na temat **Eksplorator obiektów SQL Server**, zobacz [programowanie połączonej bazy danych](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span><span class="sxs-lookup"><span data-stu-id="41711-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="41711-132">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="41711-132">Creating the project</span></span>
<span data-ttu-id="41711-133">Następnie możesz utworzyć projekt aplikacji F #.</span><span class="sxs-lookup"><span data-stu-id="41711-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="41711-134">Tworzenie i konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="41711-134">To create and set up the project</span></span>

1. <span data-ttu-id="41711-135">Utwórz nowy projekt aplikacji w języku F #.</span><span class="sxs-lookup"><span data-stu-id="41711-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="41711-136">Dodaj odwołania do [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), jak również `System.Data`, i `System.Data.Linq`.</span><span class="sxs-lookup"><span data-stu-id="41711-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="41711-137">Otwórz odpowiednie przestrzenie nazw, dodając następujące wiersze kodu do góry pliku Program.fs kodu języka F #.</span><span class="sxs-lookup"><span data-stu-id="41711-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="41711-138">Podobnie jak w przypadku większości F # programów, w tym przewodniku jako skompilowany program umożliwia wykonanie kodu lub można uruchomić w trybie interakcyjnym jako skrypt.</span><span class="sxs-lookup"><span data-stu-id="41711-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="41711-139">Jeśli wolisz korzystać ze skryptów, otwórz menu skrótów węzła projektu, zaznacz **Dodaj nowy element**, Dodaj plik skryptu języka F # i Dodaj kod w każdym kroku do skryptu.</span><span class="sxs-lookup"><span data-stu-id="41711-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="41711-140">Należy dodać następujące wiersze na początku pliku można załadować odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="41711-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="41711-141">Następnie możesz wybrać każdy blok kodu, jak dodać go i naciśnij klawisze Alt + Enter, aby uruchomić go w F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="41711-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="41711-142">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="41711-142">Setting up a type provider</span></span>
<span data-ttu-id="41711-143">W tym kroku utworzysz typ dostawcy do schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41711-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="41711-144">Aby skonfigurować typ dostawcy z połączenia bezpośredniego bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="41711-145">Istnieją dwa wiersze krytyczne kodu, które są potrzebne do tworzenia typów, które umożliwiają zapytanie dotyczące bazy danych SQL przy użyciu dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="41711-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="41711-146">Najpierw należy utworzyć wystąpienia dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="41711-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="41711-147">W tym celu należy utworzyć wygląd skrót typu `SqlDataConnection` z parametrem ogólnym statycznych.</span><span class="sxs-lookup"><span data-stu-id="41711-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="41711-148">`SqlDataConnection` Dostawca typu SQL i nie należy mylić z `SqlConnection` typu, który jest używany w programowaniu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="41711-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="41711-149">Jeśli baza danych, który chcesz połączyć się z, a ma parametry połączenia, należy użyć poniższego kodu do wywołania typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41711-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="41711-150">Zastąp własne parametry połączenia dla ciągu przykład podane.</span><span class="sxs-lookup"><span data-stu-id="41711-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="41711-151">Na przykład jeśli serwer jest MÓJSERWER i wystąpienie bazy danych jest WYSTĄPIENIEM mojabazadanych jest nazwa bazy danych i chcesz uzyskać dostępu do bazy danych, a następnie parametry połączenia za pomocą uwierzytelniania systemu Windows będzie jako podane w poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="41711-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="41711-152">Teraz masz typu `dbSchema`, która jest typu nadrzędny, który zawiera wszystkie wygenerowane typy reprezentujące tabel bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41711-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="41711-153">Masz również obiektu `db`, zainstalowanym jako elementy członkowskie wszystkie tabele w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="41711-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="41711-154">Właściwości są nazwy tabel i typ właściwości jest generowany przez kompilator języka F #.</span><span class="sxs-lookup"><span data-stu-id="41711-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="41711-155">Same typy są wyświetlane jako typy zagnieżdżone w obszarze `dbSchema.ServiceTypes`.</span><span class="sxs-lookup"><span data-stu-id="41711-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="41711-156">W związku z tym wszystkie dane pobierane dla wierszy z tych tabel jest wystąpieniem odpowiedniego typu, który został wygenerowany dla tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="41711-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="41711-157">Nazwa typu jest `ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="41711-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="41711-158">Aby zapoznać się z języka F # interpretowanie zapytania do zapytania SQL, przejrzyj wiersza, który ustawia `Log` właściwości w kontekście danych.</span><span class="sxs-lookup"><span data-stu-id="41711-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="41711-159">Umożliwiający dalszą analizę typy utworzone przez typ dostawcy, Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="41711-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="41711-160">Umieść kursor nad `table1` aby zobaczyć jego typu.</span><span class="sxs-lookup"><span data-stu-id="41711-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="41711-161">Jest on typu `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` i argumentów ogólnych oznacza, że typ każdy wiersz jest wygenerowanego typu `dbSchema.ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="41711-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="41711-162">Kompilator tworzy podobny typ dla każdej tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="41711-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="41711-163">Wykonywanie zapytań dotyczących danych</span><span class="sxs-lookup"><span data-stu-id="41711-163">Querying the data</span></span>
<span data-ttu-id="41711-164">W tym kroku należy napisać zapytanie wyrażenia zapytania F #.</span><span class="sxs-lookup"><span data-stu-id="41711-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="41711-165">Aby wykonać zapytanie dotyczące danych</span><span class="sxs-lookup"><span data-stu-id="41711-165">To query the data</span></span>

1. <span data-ttu-id="41711-166">Teraz można tworzyć zapytania dla tej tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="41711-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="41711-167">Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="41711-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="41711-168">Wygląd Word `query` wskazuje, czy jest to wyrażenie zapytania typu obliczenia wyrażenia, które generuje kolekcji podobnych wyników zapytania typowe bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41711-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="41711-169">Aktywuj zapytania, będzie mógł przeglądać jest wystąpienie [LINQ.querybuilder — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), typu, który definiuje query — wyrażenie obliczeń.</span><span class="sxs-lookup"><span data-stu-id="41711-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="41711-170">Jeśli w ustawieniu kursora `query1`, zobaczysz, że jest wystąpienie `System.Linq.IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="41711-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="41711-171">Jak wynika z nazwy, `System.Linq.IQueryable` reprezentuje dane, które można zbadać, nie wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="41711-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="41711-172">Zapytanie podlega obliczanie leniwe, co oznacza, że baza danych jest tylko zbadać, gdy obliczyć wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="41711-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="41711-173">Końcowego wiersza przekazuje zapytanie za pomocą `Seq.iter`.</span><span class="sxs-lookup"><span data-stu-id="41711-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="41711-174">Zapytania są wyliczalny i może należy powtórzyć jak sekwencji.</span><span class="sxs-lookup"><span data-stu-id="41711-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="41711-175">Aby uzyskać więcej informacji, zobacz [wyrażenia zapytania](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="41711-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="41711-176">Teraz Dodaj operator zapytania do zapytania.</span><span class="sxs-lookup"><span data-stu-id="41711-176">Now add a query operator to the query.</span></span> <span data-ttu-id="41711-177">Istnieje wiele operatorów zapytań dostępne, można tworzyć bardziej złożone zapytania.</span><span class="sxs-lookup"><span data-stu-id="41711-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="41711-178">W tym przykładzie przedstawiono również można wyeliminować zmienną zapytania i zamiast tego użyj operatora potoku.</span><span class="sxs-lookup"><span data-stu-id="41711-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="41711-179">Dodaj bardziej złożonego zapytania z sprzężenia dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="41711-179">Add a more complex query with a join of two tables.</span></span>

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. <span data-ttu-id="41711-180">W kodzie rzeczywistych parametrów w zapytaniu są zazwyczaj wartości lub zmienne, stałe nie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41711-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="41711-181">Dodaj następujący kod, który opakowuje kwerendy w funkcji, która przyjmuje parametr, a następnie wywołuje tej funkcji na wartość 10.</span><span class="sxs-lookup"><span data-stu-id="41711-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="41711-182">Praca z polami wartości null</span><span class="sxs-lookup"><span data-stu-id="41711-182">Working with nullable fields</span></span>
<span data-ttu-id="41711-183">W bazach danych pola często dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="41711-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="41711-184">System typów .NET nie można używać zwykłych danych liczbowych typów danych, które umożliwia wartości null, ponieważ te typy nie mają wartości null jako możliwą wartość.</span><span class="sxs-lookup"><span data-stu-id="41711-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="41711-185">W związku z tym te wartości są reprezentowane przez wystąpień `System.Nullable` typu.</span><span class="sxs-lookup"><span data-stu-id="41711-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="41711-186">Zamiast wartości tych pól bezpośrednio z nazwę pola, musisz dodać kilka dodatkowych czynności.</span><span class="sxs-lookup"><span data-stu-id="41711-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="41711-187">Można użyć `System.Nullable.Value` właściwość, aby uzyskać dostęp do podstawowych wartości typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="41711-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="41711-188">`System.Nullable.Value` Właściwość zgłasza wyjątek, jeśli obiekt ma wartość null zamiast wartości.</span><span class="sxs-lookup"><span data-stu-id="41711-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="41711-189">Można użyć `System.Nullable.HasValue` logiczna metody w celu określenia, czy istnieje wartość lub użyj `System.Nullable.GetValueOrDefault()` zapewnienie ma wartość rzeczywistą we wszystkich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="41711-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="41711-190">Jeśli używasz `System.Nullable.GetValueOrDefault()` i jest on wartość null w bazie danych, a następnie zostanie zastąpiony z wartości, takich jak ciągu pustego ciągu typów, punkt typy 0 dla typów całkowitych lub 0,0 dla zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="41711-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="41711-191">Kiedy należy przeprowadzić testy równości lub porównania o wartości null w `where` klauzuli w zapytaniu, można użyć operatory dopuszczające wartość null w [LINQ.nullableoperators — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="41711-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="41711-192">Są to takie jak operatory porównania regularne `=`, `>`, `<=`i tak dalej z tą różnicą, że znak zapytania pojawia się po lewej stronie lub po prawej stronie operatora skutkującej wartości null.</span><span class="sxs-lookup"><span data-stu-id="41711-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="41711-193">Na przykład operator `>?` jest większy-niż operator o wartości null po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="41711-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="41711-194">Sposób pracy tych operatorów jest, że jeśli którejś wyrażenie ma wartość null, wyrażenie daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="41711-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="41711-195">W `where` klauzuli, zazwyczaj oznacza to, że wiersze zawierające pól o wartości null są niezaznaczone i nie są zwracane w wynikach zapytania.</span><span class="sxs-lookup"><span data-stu-id="41711-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="41711-196">Aby pracować z polami wartości null</span><span class="sxs-lookup"><span data-stu-id="41711-196">To work with nullable fields</span></span>

<span data-ttu-id="41711-197">Poniższy kod przedstawia pracy z wartości null. przyjęto założenie, że **TestData1** jest polem Liczba całkowita, która zezwala na wartości null.</span><span class="sxs-lookup"><span data-stu-id="41711-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="41711-198">Wywoływanie procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="41711-198">Calling a stored procedure</span></span>
<span data-ttu-id="41711-199">Wszystkie procedury przechowywane w bazie danych może być wywołana z F #.</span><span class="sxs-lookup"><span data-stu-id="41711-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="41711-200">Należy ustawić parametr statyczny `StoredProcedures` do `true` w wystąpienia typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41711-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="41711-201">Typ dostawcy `SqlDataConnection` zawiera kilka metod statycznych, których można użyć do skonfigurowania typy, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="41711-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="41711-202">Aby uzyskać pełny opis tych, zobacz [sqldataconnection — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="41711-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="41711-203">Metody w typie kontekstu danych jest generowany dla każdej procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="41711-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="41711-204">Aby wywołać procedurę składowaną</span><span class="sxs-lookup"><span data-stu-id="41711-204">To call a stored procedure</span></span>

<span data-ttu-id="41711-205">Jeśli procedury składowane pobiera parametry, które dopuszczają wartości null, należy przekazać odpowiedni `System.Nullable` wartość.</span><span class="sxs-lookup"><span data-stu-id="41711-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="41711-206">Wartość zwracaną przez metodę procedury przechowywanej, która zwraca skalarnej lub tabela jest `System.Data.Linq.ISingleResult`, który zawiera właściwości, które umożliwiają dostęp do danych zwracanych.</span><span class="sxs-lookup"><span data-stu-id="41711-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="41711-207">Typ argumentu dla `System.Data.Linq.ISingleResult` zależy od określonej procedury i jest również jeden z typów, które generuje typ dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41711-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="41711-208">Dla procedury składowanej o nazwie `Procedure1`, jest typu `Procedure1Result`.</span><span class="sxs-lookup"><span data-stu-id="41711-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="41711-209">Typ `Procedure1Result` zawiera nazwy kolumn w tabeli zwracane lub procedury przechowywanej, która zwraca wartość skalarną reprezentuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="41711-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="41711-210">Poniższy kod przyjęto założenie, że istnieje procedura `Procedure1` bazy danych, która przyjmuje dwa nullable liczb całkowitych jako parametry, uruchamia zapytanie zwracające kolumny o nazwie `TestData1`i zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="41711-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a><span data-ttu-id="41711-211">Zaktualizowanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-211">Updating the database</span></span>
<span data-ttu-id="41711-212">Typ LINQ DataContext zawiera metody, które ułatwiają wykonywanie aktualizacji transakcyjne bazy danych w sposób wpisaniu z wygenerowane typy.</span><span class="sxs-lookup"><span data-stu-id="41711-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="41711-213">Aby zaktualizować bazę danych</span><span class="sxs-lookup"><span data-stu-id="41711-213">To update the database</span></span>

1. <span data-ttu-id="41711-214">W poniższym kodzie kilka wierszy są dodawane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41711-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="41711-215">Jeśli dodajesz wiersza, możesz użyć `System.Data.Linq.Table.InsertOnSubmit()` Aby określić nowy wiersz do dodania.</span><span class="sxs-lookup"><span data-stu-id="41711-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="41711-216">W przypadku wstawiania wiele wierszy, należy umieścić je do kolekcji i wywołania `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span><span class="sxs-lookup"><span data-stu-id="41711-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="41711-217">Podczas wywoływania jednej z tych metod, bazy danych nie ulega zmianie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="41711-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="41711-218">Należy wywołać `System.Data.Linq.DataContext.SubmitChanges` faktycznie zatwierdzić zmiany.</span><span class="sxs-lookup"><span data-stu-id="41711-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="41711-219">Domyślny, wszystko, co należy wykonać przed wywołać `System.Data.Linq.DataContext.SubmitChanges` niejawnie jest częścią tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="41711-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. <span data-ttu-id="41711-220">Teraz wyczyścić wiersze wywołując operację usuwania.</span><span class="sxs-lookup"><span data-stu-id="41711-220">Now clean up the rows by calling a delete operation.</span></span>

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a><span data-ttu-id="41711-221">Wykonywanie kodu języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="41711-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="41711-222">Można również określić bezpośrednio przy użyciu języka Transact-SQL `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` metoda `DataContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="41711-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="41711-223">Do wykonania polecenia SQL niestandardowe</span><span class="sxs-lookup"><span data-stu-id="41711-223">To execute custom SQL commands</span></span>

<span data-ttu-id="41711-224">Poniższy kod przedstawia sposób wysłania poleceń SQL do wstawienia rekordu do tabeli, a także aby usunąć rekord z tabeli.</span><span class="sxs-lookup"><span data-stu-id="41711-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a><span data-ttu-id="41711-225">Przy użyciu kontekstu danych</span><span class="sxs-lookup"><span data-stu-id="41711-225">Using the full data context</span></span>
<span data-ttu-id="41711-226">W poprzednich przykładach `GetDataContext` użyto metody można uzyskać, co jest nazywane *kontekstu danych uproszczony* do schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41711-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="41711-227">Kontekst danych uproszczony jest łatwiejsze w są tworzenia zapytań, ponieważ nie są dostępne jako wiele elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="41711-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="41711-228">W związku z tym podczas przeglądania właściwości w IntelliSense można skoncentrować się na temat struktury bazy danych, takich jak tabele i procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="41711-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="41711-229">Jest jednak ograniczona co można zrobić z kontekstu danych uproszczone.</span><span class="sxs-lookup"><span data-stu-id="41711-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="41711-230">Kontekst pełnych danych, która pozwala, aby wykonywać inne akcje.</span><span class="sxs-lookup"><span data-stu-id="41711-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="41711-231">jest również dostępna to znajduje się w `ServiceTypes` i ma nazwę *DataContext* parametr statyczny, jeśli została podana.</span><span class="sxs-lookup"><span data-stu-id="41711-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="41711-232">Jeśli nie podano go, nazwa typu kontekstu danych zostanie wygenerowany przez SqlMetal.exe oparte na innych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="41711-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="41711-233">Dziedziczy kontekstu danych `System.Data.Linq.DataContext` i udostępnia elementów członkowskich klasy podstawowej, takie jak tym odwołania do typów danych ADO.NET `Connection` obiektu, metody, takie jak `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` i `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` można pisać zapytania w programie SQL a także sposób pracy z transakcji jawnie.</span><span class="sxs-lookup"><span data-stu-id="41711-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="41711-234">Aby używać kontekstu danych</span><span class="sxs-lookup"><span data-stu-id="41711-234">To use the full data context</span></span>

<span data-ttu-id="41711-235">Poniższy kod przedstawia pobierania obiektu kontekstu pełnych danych i użyciem jej do wykonania polecenia bezpośrednio w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="41711-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="41711-236">W takim przypadku dwa polecenia są wykonywane w ramach tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="41711-236">In this case, two commands are executed as part of the same transaction.</span></span>

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a><span data-ttu-id="41711-237">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="41711-237">Deleting data</span></span>
<span data-ttu-id="41711-238">W tym kroku przedstawiono sposób usuwania wierszy w tabeli danych.</span><span class="sxs-lookup"><span data-stu-id="41711-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="41711-239">Aby usunąć wierszy z bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-239">To delete rows from the database</span></span>

<span data-ttu-id="41711-240">Teraz, czyszczenie żadnego dodanych wierszy pisząc funkcję, która usuwa wiersze z tabeli określonej instancji `System.Data.Linq.Table` klasy.</span><span class="sxs-lookup"><span data-stu-id="41711-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="41711-241">Następnie napisz zapytanie, aby znaleźć wszystkie wiersze, które chcesz usunąć, a wyniki zapytania do potoku `deleteRows` funkcji.</span><span class="sxs-lookup"><span data-stu-id="41711-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="41711-242">Ten kod korzysta z możliwości zapewnienia aplikacja częściowa argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="41711-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a><span data-ttu-id="41711-243">Tworzenie testowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-243">Creating a test database</span></span>
<span data-ttu-id="41711-244">W tej sekcji przedstawiono sposób konfigurowania bazy danych testu do użycia w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="41711-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="41711-245">Należy pamiętać o tym, w przypadku modyfikowania bazy danych w określony sposób, konieczne będzie zresetować typ dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41711-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="41711-246">Aby zresetować typ dostawcy, odbudować lub wyczyścić projektu, który zawiera typ dostawcy.</span><span class="sxs-lookup"><span data-stu-id="41711-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="41711-247">Aby utworzyć testowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="41711-247">To create the test database</span></span>

1. <span data-ttu-id="41711-248">W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych** węzeł i wybierz polecenie **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="41711-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="41711-249">**Dodawanie połączenia** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="41711-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="41711-250">W **nazwy serwera** polu, określ nazwę wystąpienia programu SQL Server, które mają dostęp administracyjny do lub jeśli nie masz dostępu do serwera, określ (localdb\v11.0).</span><span class="sxs-lookup"><span data-stu-id="41711-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="41711-251">SQL Express LocalDB zapewnia serwer lekkie bazy danych dla projektowania i testowania na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="41711-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="41711-252">Nowy węzeł jest tworzony w **Eksploratora serwera** w obszarze **połączenia danych**.</span><span class="sxs-lookup"><span data-stu-id="41711-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="41711-253">Aby uzyskać więcej informacji na temat LocalDB, zobacz [wskazówki: Tworzenie lokalnego pliku bazy danych w programie Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="41711-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="41711-254">Otwórz menu skrótów do nowego węzła połączenie i wybierz **nowe zapytanie**.</span><span class="sxs-lookup"><span data-stu-id="41711-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="41711-255">Skopiuj poniższy skrypt SQL, wklej go w edytorze zapytań, a następnie wybierz **Execute** znajdującego się na pasku narzędzi lub wybierz klawiszy Ctrl + Shift + E.</span><span class="sxs-lookup"><span data-stu-id="41711-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a><span data-ttu-id="41711-256">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41711-256">See Also</span></span>
[<span data-ttu-id="41711-257">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="41711-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="41711-258">Sqldataconnection — dostawca typów</span><span class="sxs-lookup"><span data-stu-id="41711-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="41711-259">Wskazówki: Generowanie typów F # za pomocą pliku DBML</span><span class="sxs-lookup"><span data-stu-id="41711-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="41711-260">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="41711-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="41711-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="41711-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="41711-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span><span class="sxs-lookup"><span data-stu-id="41711-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
