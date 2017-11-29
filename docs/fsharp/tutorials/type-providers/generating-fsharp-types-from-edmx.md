---
title: "Wskazówki: generowanie typów F# za pomocą pliku schematu EDMX (F#)"
description: "Dowiedz się, jak tworzyć typy F # dla danych reprezentowanego przez modelu danych jednostki (EDM) w F # 3.0, gdzie schemat jest określony w pliku edmx."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 5c59911f5f880493080ef1838bc015045ce4336a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="ae045-104">Wskazówki: generowanie typów F# za pomocą pliku schematu EDMX</span><span class="sxs-lookup"><span data-stu-id="ae045-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="ae045-105">Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="ae045-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="ae045-106">Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.</span><span class="sxs-lookup"><span data-stu-id="ae045-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="ae045-107">Linki odwołań interfejsu API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="ae045-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="ae045-108">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="ae045-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ae045-109">W tym przewodniku dotyczącym języka F# 3.0 pokazano, jak tworzyć typy danych reprezentowane przez model Entity Data Model (EDM), którego schemat jest określony w pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="ae045-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="ae045-110">W tym przewodniku pokazano również sposób użycia dostawcy typów EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="ae045-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="ae045-111">Przed rozpoczęciem należy zastanowić się, czy nie będzie lepiej używać dostawcy typów SqlEntityConnection.</span><span class="sxs-lookup"><span data-stu-id="ae045-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="ae045-112">Dostawca typów SqlEntityConnection sprawdza się najlepiej w scenariuszach obejmujących aktywną bazę danych, z którą można łączyć się podczas fazy opracowywania projektu i nie trzeba pamiętać o określaniu parametrów połączenia w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ae045-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="ae045-113">Jednak ten dostawca typów ma również ograniczenia, ponieważ nie uwidacznia tak wielu funkcji bazy danych, jak dostawca typów EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="ae045-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="ae045-114">Ponadto jeśli dla projektu, w którym jest używany model Entity Data Model, nie jest używane aktywne połączenie z bazą danych, do tworzenia kodu operacji wykonywanych w bazie danych można używać pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="ae045-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="ae045-115">Użycie dostawcy typów EdmxFile powoduje, że kompilator języka F# uruchamia program EdmGen.exe w celu wygenerowania dostarczanych przez siebie typów.</span><span class="sxs-lookup"><span data-stu-id="ae045-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="ae045-116">W tym przewodniku opisano następujące zadania, które trzeba wykonać, aby pomyślnie przerobić przewodnik:</span><span class="sxs-lookup"><span data-stu-id="ae045-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="ae045-117">Tworzenie pliku EDMX</span><span class="sxs-lookup"><span data-stu-id="ae045-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="ae045-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ae045-118">Creating the project</span></span>
<br />

- <span data-ttu-id="ae045-119">Znajdowanie lub tworzenie danych jednostki modelu parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="ae045-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="ae045-120">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae045-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="ae045-121">Wykonywanie zapytań dotyczących danych</span><span class="sxs-lookup"><span data-stu-id="ae045-121">Querying the data</span></span>
<br />

- <span data-ttu-id="ae045-122">Wywoływanie procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="ae045-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="ae045-123">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ae045-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="ae045-124">Tworzenie pliku EDMX</span><span class="sxs-lookup"><span data-stu-id="ae045-124">Creating an EDMX file</span></span>
<span data-ttu-id="ae045-125">Jeśli masz już plik EDMX, możesz pominąć ten krok.</span><span class="sxs-lookup"><span data-stu-id="ae045-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="ae045-126">Aby utworzyć plik EDMX</span><span class="sxs-lookup"><span data-stu-id="ae045-126">To create an EDMX file</span></span>

- <span data-ttu-id="ae045-127">Jeśli nie masz jeszcze pliku EDMX, można postępuj zgodnie z instrukcjami na końcu tego przewodnika w kroku [Konfigurowanie modelu Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span><span class="sxs-lookup"><span data-stu-id="ae045-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="ae045-128">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="ae045-128">Creating the project</span></span>
<span data-ttu-id="ae045-129">W tym kroku należy utworzyć projekt i dodać do niego odpowiednie odwołania w celu użycia dostawcy typów EDMX.</span><span class="sxs-lookup"><span data-stu-id="ae045-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="ae045-130">Aby utworzyć i skonfigurować projekt języka F#</span><span class="sxs-lookup"><span data-stu-id="ae045-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="ae045-131">Zamknij poprzedni projekt i utwórz nowy projekt o nazwie SchoolEDM.</span><span class="sxs-lookup"><span data-stu-id="ae045-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="ae045-132">W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="ae045-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="ae045-133">W **zestawy** obszarze, wybierz **Framework** węzła.</span><span class="sxs-lookup"><span data-stu-id="ae045-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="ae045-134">Na liście dostępnych zestawów, wybierz **System.Data.Entity** i **System.Data.Linq** zestawy, a następnie wybierz pozycję **Dodaj** przycisk, aby dodać odwołania do tych zestawy do projektu.</span><span class="sxs-lookup"><span data-stu-id="ae045-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="ae045-135">W **zestawy** wybierz opcję **rozszerzenia** węzła.</span><span class="sxs-lookup"><span data-stu-id="ae045-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="ae045-136">Z listy dostępnych rozszerzeń dodaj odwołanie do zestawu FSharp.Data.TypeProviders.</span><span class="sxs-lookup"><span data-stu-id="ae045-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="ae045-137">Dodaj poniższy kod, aby otworzyć odpowiednie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="ae045-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="ae045-138">Znajdowanie lub tworzenie parametrów połączenia dla modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ae045-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="ae045-139">Parametry połączenia dla modelu Entity Data Model (parametry połączenia EDMX) zawierają nie tylko parametry połączenia dla dostawcy bazy danych, ale również dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="ae045-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="ae045-140">Na przykład parametry połączenia EDMX dla prostej bazy danych programu SQL Server przypominają poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="ae045-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="ae045-141">Aby uzyskać więcej informacji dotyczących parametrów połączenia w pliku EDMX, zobacz [parametry połączenia](https://msdn.microsoft.com/library/ms254494.aspx).</span><span class="sxs-lookup"><span data-stu-id="ae045-141">For more information about EDMX connection strings, see [Connection Strings](https://msdn.microsoft.com/library/ms254494.aspx).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="ae045-142">Aby znaleźć lub utworzyć parametry połączenia dla modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ae045-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="ae045-143">Ręczne generowanie parametrów połączenia EDMX może być trudne, więc można zaoszczędzić czas, generując je programowo.</span><span class="sxs-lookup"><span data-stu-id="ae045-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="ae045-144">Jeśli znasz parametry połączenia EDMX, możesz pominąć ten krok i po prostu użyć tych parametrów w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="ae045-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="ae045-145">Jeśli ich nie znasz, użyj poniższego kodu w celu wygenerowania parametrów połączenia EDMX na podstawie podanych parametrów połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="ae045-146">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae045-146">Configuring the type provider</span></span>
<span data-ttu-id="ae045-147">W tym kroku należy utworzyć i skonfigurować dostawcę typów, używając parametrów połączenia EDMX, i wygenerować typy dla schematu zdefiniowanego w pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="ae045-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="ae045-148">Aby skonfigurować dostawcę typów i wygenerować typy</span><span class="sxs-lookup"><span data-stu-id="ae045-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="ae045-149">Skopiuj plik edmx wygenerowany w pierwszym kroku tego przewodnika do folderu projektu.</span><span class="sxs-lookup"><span data-stu-id="ae045-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="ae045-150">Otwórz menu skrótów węzła projektu w F # projektu, wybierz **Dodaj istniejący element**, a następnie wybierz pozycję pliku edmx, aby dodać go do projektu.</span><span class="sxs-lookup"><span data-stu-id="ae045-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="ae045-151">Wprowadź następujący kod, aby aktywować dostawcę typów dla pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="ae045-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="ae045-152">Zastąp *serwera*\*wystąpienia * z nazwą serwera, który jest uruchomiony program SQL Server i nazwę wystąpienia i użyj nazwy pliku edmx z pierwszym krokiem w ramach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="ae045-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="ae045-153">Wykonywanie zapytań dotyczących danych</span><span class="sxs-lookup"><span data-stu-id="ae045-153">Querying the data</span></span>
<span data-ttu-id="ae045-154">W tym kroku należy użyć wyrażeń zapytania języka F# w celu wykonania zapytania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="ae045-155">Aby wykonać zapytanie dotyczące danych</span><span class="sxs-lookup"><span data-stu-id="ae045-155">To query the data</span></span>

- <span data-ttu-id="ae045-156">Wprowadź poniższy kod w celu wykonania zapytania dotyczącego danych w modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ae045-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="ae045-157">Wywoływanie procedury składowanej</span><span class="sxs-lookup"><span data-stu-id="ae045-157">Calling a stored procedure</span></span>
<span data-ttu-id="ae045-158">Za pomocą dostawcy typów EDMX można wywoływać procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="ae045-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="ae045-159">W poniższej procedurze służbowe baza danych zawiera procedurę składowaną **UpdatePerson**, aktualizacje rekord danego nowe wartości w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="ae045-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="ae045-160">Można użyć tej procedury składowanej, ponieważ jest ona uwidoczniona jako metoda w typie DataContext.</span><span class="sxs-lookup"><span data-stu-id="ae045-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="ae045-161">Aby wywołać procedurę składowaną</span><span class="sxs-lookup"><span data-stu-id="ae045-161">To call a stored procedure</span></span>

- <span data-ttu-id="ae045-162">Dodaj następujący kod w celu aktualizacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="ae045-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="ae045-163">W przypadku pomyślnego wywołania wynik wyniesie 1.</span><span class="sxs-lookup"><span data-stu-id="ae045-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="ae045-164">Zwróć uwagę, że **exactlyOne** jest używany w wyrażeniu zapytania, aby upewnić się, że tylko jeden wynik zostanie zwrócony; w przeciwnym, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ae045-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="ae045-165">Również, aby łatwiej pracować z wartości null, można użyć prostej **nullable** funkcji, która jest zdefiniowana w tym kodzie można utworzyć wartości null wartości poza wartością zwykłej.</span><span class="sxs-lookup"><span data-stu-id="ae045-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="ae045-166">Konfigurowanie modelu Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ae045-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="ae045-167">Tę procedurę należy wykonać tylko wtedy, gdy użytkownik chce wiedzieć, jak wygenerować pełny model Entity Data Model na podstawie bazy danych, a nie ma bazy danych, której można by użyć do testowania.</span><span class="sxs-lookup"><span data-stu-id="ae045-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="ae045-168">Aby skonfigurować model Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ae045-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="ae045-169">Na pasku menu wybierz **SQL**, **edytora języka Transact-SQL**, **nowe zapytanie** tworzenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="ae045-170">Jeśli zostanie wyświetlony monit, określ serwer bazy danych i wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="ae045-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="ae045-171">Skopiuj i Wklej zawartość skryptu bazy danych, który utworzy bazę danych dla użytkowników domowych, zgodnie z opisem w [dokumentację programu Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) w Centrum deweloperów danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](http://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="ae045-172">Wybranie przycisku paska narzędzi z symbolem trójkąt lub wybierając pozycję klawiszy Ctrl + Q, uruchom skrypt SQL.</span><span class="sxs-lookup"><span data-stu-id="ae045-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="ae045-173">W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych**, wybierz **Dodawanie połączenia**, a następnie wprowadź nazwę serwera bazy danych, nazwę wystąpienia , a bazą danych służbowych.</span><span class="sxs-lookup"><span data-stu-id="ae045-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="ae045-174">Tworzenie projektu C# lub Visual Basic aplikacji konsoli, otwórz menu skrótów, wybierz pozycję **Dodaj nowy element**, a następnie wybierz pozycję **modelu danych jednostki ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="ae045-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="ae045-175">Zostanie otwarty Kreator modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ae045-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="ae045-176">Za pomocą tego kreatora można wybrać sposób tworzenia modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ae045-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="ae045-177">W obszarze **wybierz zawartość modelu**, wybierz pozycję **generowania z bazy danych** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="ae045-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="ae045-178">Na następnej stronie wybierz nowo utworzoną bazę danych School jako połączenia danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="ae045-179">To połączenie powinno przypominać  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.</span><span class="sxs-lookup"><span data-stu-id="ae045-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="ae045-180">Skopiuj parametry połączenia obiektu do Schowka, ponieważ te parametry mogą okazać się później ważne.</span><span class="sxs-lookup"><span data-stu-id="ae045-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="ae045-181">Upewnij się, że pole wyboru, aby zapisać parametry połączenia jednostki do **App.Config** plików jest zaznaczona i zanotuj wartość ciągu w polu tekstowym, które powinny pomóc Ci w znalezieniu ciągu połączenia później, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ae045-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="ae045-182">Na następnej stronie wybierz **tabel** i **procedury składowane i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="ae045-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="ae045-183">Wybranie tych węzłów najwyższego poziomu powoduje wybranie wszystkich tabel, procedur składowanych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae045-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="ae045-184">Można je także wybrać indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="ae045-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="ae045-185">Upewnij się, że są też zaznaczone pola wyboru dla innych ustawień.</span><span class="sxs-lookup"><span data-stu-id="ae045-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="ae045-186">Pierwszy **Pluralize lub nadaj wygenerowanym nazwom obiektów** pole wyboru wskazuje, czy można zmienić pojedynczej formularze na liczbie mnogiej odpowiadające konwencje w nazywania obiektów, które reprezentują tabel bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="ae045-187">**Dołącz kolumny klucza obcego do modelu** pole wyboru określa, czy dołączać pól, dla których ma na celu dołączenia do innych pól typów obiektów, które są generowane dla schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ae045-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="ae045-188">Trzecie pole wyboru wskazuje, czy w modelu mają być uwzględniane procedury składowane i funkcje.</span><span class="sxs-lookup"><span data-stu-id="ae045-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="ae045-189">Wybierz **Zakończ** przycisk, aby wygenerować plik edmx, który zawiera modelu Entity Data Model oparty na bazie danych służbowych.</span><span class="sxs-lookup"><span data-stu-id="ae045-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="ae045-190">Plik, **Model1.edmx**, zostanie dodany do projektu, a schemat bazy danych są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="ae045-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="ae045-191">Na pasku menu wybierz **widoku**, **inne okna**, **przeglądarka modeli danych jednostki** umożliwia wyświetlenie wszystkich szczegółów modelu lub **szczegóły mapowania modelu danych jednostki**  można otworzyć okna, pokazujący sposób mapowania modelu wygenerowanego obiektu do bazy danych, tabel i kolumn.</span><span class="sxs-lookup"><span data-stu-id="ae045-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="ae045-192">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ae045-192">Next Steps</span></span>
<span data-ttu-id="ae045-193">Eksploruj inne zapytania, analizując operatorów zapytań dostępne wymienionych w [wyrażenia zapytania](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ae045-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="ae045-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae045-194">See Also</span></span>
[<span data-ttu-id="ae045-195">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="ae045-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="ae045-196">Edmxfile — dostawca typów</span><span class="sxs-lookup"><span data-stu-id="ae045-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="ae045-197">Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów i jednostek</span><span class="sxs-lookup"><span data-stu-id="ae045-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="ae045-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ae045-198">Entity Framework</span></span>](http://msdn.microsoft.com/data/ef)

[<span data-ttu-id="ae045-199">Omówienie plików edmx</span><span class="sxs-lookup"><span data-stu-id="ae045-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="ae045-200">EDM Generator &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="ae045-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

