---
title: "Wskazówki: generowanie typów F# za pomocą pliku DBML (F#)"
description: "Informacje o sposobie tworzenia typów F # dla danych z bazy danych w F # 3.0, jeśli masz zakodowane w pliku .dbml informacji o schemacie."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: a919c2acb2b5b8c2ce93124f2f541bd092d15c35
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="3ad49-104">Wskazówki: generowanie typów F# za pomocą pliku DBML</span><span class="sxs-lookup"><span data-stu-id="3ad49-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="3ad49-105">Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="3ad49-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="3ad49-106">Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.</span><span class="sxs-lookup"><span data-stu-id="3ad49-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="3ad49-107">Linki odwołań interfejsu API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="3ad49-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="3ad49-108">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="3ad49-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="3ad49-109">Tego przewodnika w celu F # 3.0 zawiera opis sposobu tworzenia typów danych z bazy danych, jeśli masz zakodowane w pliku .dbml informacji o schemacie.</span><span class="sxs-lookup"><span data-stu-id="3ad49-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="3ad49-110">LINQ do SQL korzysta z tego formatu pliku do reprezentowania schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3ad49-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="3ad49-111">LINQ do SQL pliku schematu w programie Visual Studio można wygenerować za pomocą Projektanta obiektów relacyjnych (obiektów relacyjnych).</span><span class="sxs-lookup"><span data-stu-id="3ad49-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="3ad49-112">Aby uzyskać więcej informacji, zobacz [Omówienie projektanta obiektów relacyjnych](https://msdn.microsoft.com/library/bb384511.aspx) i [generowanie kodu w składniku LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ad49-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="3ad49-113">Typ dostawcy bazy danych Markup Language (DBML) służy do pisania kodu, który używa typy oparte na schemat bazy danych bez konieczności Określ ciąg połączenia statycznych w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3ad49-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="3ad49-114">Może to być przydatne, jeśli konieczne jest zezwolenie na możliwość, że końcowego aplikacja będzie korzystać z innej bazy danych, innych poświadczeń lub ciąg połączenia innego niż jeden, którego używasz do opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ad49-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="3ad49-115">Jeśli masz połączenie z bazą danych bezpośrednio używanej w czasie kompilacji i są to te same bazy danych i poświadczenia, które będą używane po pewnym czasie zbudowany aplikacji, można również użyć sqldataconnection — dostawca typów.</span><span class="sxs-lookup"><span data-stu-id="3ad49-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="3ad49-116">Aby uzyskać więcej informacji, zobacz [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="3ad49-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="3ad49-117">W tym przewodniku przedstawiono następujące zadania.</span><span class="sxs-lookup"><span data-stu-id="3ad49-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="3ad49-118">One należy wykonać w następującej kolejności wskazówki powiodła się:</span><span class="sxs-lookup"><span data-stu-id="3ad49-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="3ad49-119">Tworzenie pliku .dbml</span><span class="sxs-lookup"><span data-stu-id="3ad49-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="3ad49-120">Tworzenie i konfigurowanie projektu programu F #</span><span class="sxs-lookup"><span data-stu-id="3ad49-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="3ad49-121">Typ dostawcy konfiguracji i generowania typów</span><span class="sxs-lookup"><span data-stu-id="3ad49-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="3ad49-122">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="3ad49-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="3ad49-123">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3ad49-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="3ad49-124">Tworzenie pliku .dbml</span><span class="sxs-lookup"><span data-stu-id="3ad49-124">Creating a .dbml file</span></span>
<span data-ttu-id="3ad49-125">Jeśli nie masz bazę danych do testu na, utwórz ją zgodnie z instrukcjami w dolnej części [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="3ad49-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="3ad49-126">Wykonaj te instrukcje, utworzysz bazę danych o nazwie mojabazadanych, który zawiera kilka prostych tabele i procedury przechowywane na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="3ad49-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="3ad49-127">Jeśli masz już plik .dbml, możesz przejść do sekcji **tworzenie i ustaw się F # projekt**.</span><span class="sxs-lookup"><span data-stu-id="3ad49-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="3ad49-128">W przeciwnym razie możesz utworzyć plik .dbml na podstawie istniejącej bazy danych SQL i przy użyciu wiersza polecenia narzędzia SqlMetal.exe.</span><span class="sxs-lookup"><span data-stu-id="3ad49-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="3ad49-129">Aby utworzyć plik .dbml przy użyciu SqlMetal.exe</span><span class="sxs-lookup"><span data-stu-id="3ad49-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="3ad49-130">Otwórz **wiersza polecenia dewelopera**.</span><span class="sxs-lookup"><span data-stu-id="3ad49-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="3ad49-131">Upewnij się, że masz dostęp do SqlMetal.exe, wprowadzając `SqlMetal.exe /?` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ad49-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="3ad49-132">SqlMetal.exe jest instalowane w obszarze **SDKs Microsoft** folderu w **Program Files** lub **Program Files (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3ad49-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="3ad49-133">Uruchom SqlMetal.exe z poniższych opcji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ad49-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="3ad49-134">Zastąp odpowiednią ścieżkę zamiast `c:\destpath` do tworzenia pliku .dbml i Wstaw odpowiednie wartości dla serwera bazy danych, wystąpienia nazwy i nazwy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3ad49-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="3ad49-135">Jeśli SqlMetal.exe ma problemy podczas tworzenia pliku z powodu problemów z uprawnień, zmień bieżący katalog w folderze, który ma dostęp do zapisu.</span><span class="sxs-lookup"><span data-stu-id="3ad49-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="3ad49-136">Możesz także przeglądać inne dostępne opcje wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ad49-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="3ad49-137">Na przykład są opcje, których można używać widoków i funkcji SQL uwzględnionych w wygenerowane typy.</span><span class="sxs-lookup"><span data-stu-id="3ad49-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="3ad49-138">Aby uzyskać więcej informacji, zobacz [SqlMetal.exe &#40; Narzędzie generowania kodu &#41; ](https://msdn.microsoft.com/library/bb386987).</span><span class="sxs-lookup"><span data-stu-id="3ad49-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="3ad49-139">Tworzenie i konfigurowanie projektu programu F #</span><span class="sxs-lookup"><span data-stu-id="3ad49-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="3ad49-140">W tym kroku utworzenie projektu i dodaj odpowiednie odwołania do używania dostawcy typów DBML.</span><span class="sxs-lookup"><span data-stu-id="3ad49-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="3ad49-141">Aby utworzyć i skonfigurować projekt języka F#</span><span class="sxs-lookup"><span data-stu-id="3ad49-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="3ad49-142">Dodaj nowy projekt aplikacji konsoli F # do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3ad49-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="3ad49-143">W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="3ad49-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="3ad49-144">W **zestawy** obszarze, wybierz **Framework** węzeł, a następnie na liście dostępnych zestawów, wybierz **system.dane** i **System.Data.Linq**  zestawów.</span><span class="sxs-lookup"><span data-stu-id="3ad49-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="3ad49-145">W **zestawy** obszarze, wybierz **rozszerzenia**, a następnie na liście dostępnych zestawów, wybierz **FSharp.Data.TypeProviders**.</span><span class="sxs-lookup"><span data-stu-id="3ad49-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="3ad49-146">Wybierz **OK** przycisk, aby dodać odwołania do tych zestawów do projektu.</span><span class="sxs-lookup"><span data-stu-id="3ad49-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="3ad49-147">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="3ad49-147">(Optional).</span></span> <span data-ttu-id="3ad49-148">Skopiuj plik .dbml, który został utworzony w poprzednim kroku, a następnie wklej go w folderze głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="3ad49-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="3ad49-149">Ten folder zawiera plik projektu (.fsproj) i plików kodu.</span><span class="sxs-lookup"><span data-stu-id="3ad49-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="3ad49-150">Na pasku menu wybierz **projektu**, **Dodaj istniejący element**, a następnie wskaż plik .dbml, aby dodać go do projektu.</span><span class="sxs-lookup"><span data-stu-id="3ad49-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="3ad49-151">Po wykonaniu tych kroków można pominąć parametr statyczny ResolutionFolder w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="3ad49-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="3ad49-152">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="3ad49-152">Configuring the type provider</span></span>
<span data-ttu-id="3ad49-153">W tej sekcji Tworzenie dostawcy typów i generowania typów ze schematu opisaną w pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="3ad49-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="3ad49-154">Aby skonfigurować typ dostawcy i wygenerować typy</span><span class="sxs-lookup"><span data-stu-id="3ad49-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="3ad49-155">Dodaj kod, którego kliknięcie spowoduje otwarcie **TypeProviders** przestrzeni nazw i tworzy wystąpienie dostawcy typów dla pliku .dbml, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="3ad49-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="3ad49-156">Jeśli plik .dbml zostało dodane do projektu, można pominąć parametr statyczny ResolutionFolder.</span><span class="sxs-lookup"><span data-stu-id="3ad49-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="3ad49-157">Typ DataContext zapewnia dostęp do wszystkich typów wygenerowany i dziedziczy `System.Data.Linq.DataContext`.</span><span class="sxs-lookup"><span data-stu-id="3ad49-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="3ad49-158">Dbmlfile — dostawca typów ma różnych parametrów statycznych, które można ustawić.</span><span class="sxs-lookup"><span data-stu-id="3ad49-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="3ad49-159">Na przykład można użyć inną nazwę dla typu DataContext, określając `DataContext=MyDataContext`.</span><span class="sxs-lookup"><span data-stu-id="3ad49-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="3ad49-160">W takim przypadku kodu podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="3ad49-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="3ad49-161">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="3ad49-161">Querying the database</span></span>
<span data-ttu-id="3ad49-162">W tej sekcji umożliwiają wyrażenia zapytania F # w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3ad49-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="3ad49-163">Aby wykonać zapytanie dotyczące danych</span><span class="sxs-lookup"><span data-stu-id="3ad49-163">To query the data</span></span>

- <span data-ttu-id="3ad49-164">Dodaj kod, aby w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3ad49-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="3ad49-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3ad49-165">Next Steps</span></span>
<span data-ttu-id="3ad49-166">Możesz przejść do użycia inne wyrażenia zapytania lub pobrać z kontekstu danych połączenia z bazą danych, a wykonywanie zwykłych operacji danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3ad49-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="3ad49-167">Dodatkowe czynności, zobacz sekcje po "Dane zapytania" w [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="3ad49-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="3ad49-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ad49-168">See Also</span></span>
[<span data-ttu-id="3ad49-169">Dbmlfile — dostawca typów</span><span class="sxs-lookup"><span data-stu-id="3ad49-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="3ad49-170">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="3ad49-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="3ad49-171">Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów</span><span class="sxs-lookup"><span data-stu-id="3ad49-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="3ad49-172">SqlMetal.exe &#40; Narzędzie generowania kodu &#41;</span><span class="sxs-lookup"><span data-stu-id="3ad49-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="3ad49-173">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="3ad49-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
