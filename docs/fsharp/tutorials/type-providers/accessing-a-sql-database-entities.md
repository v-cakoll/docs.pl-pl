---
title: "Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów i jednostek (F#)"
description: "Dowiedz się, jak uzyskać dostępu do bazy danych SQL oparte na modelu danych jednostki ADO.NET w F # 3.0 typu danych."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: e0e78e06fa1129ba5eeb73bc36c14343c93d6927
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="f7958-104">Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów i jednostek</span><span class="sxs-lookup"><span data-stu-id="f7958-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="f7958-105">Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="f7958-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="f7958-106">Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.</span><span class="sxs-lookup"><span data-stu-id="f7958-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="f7958-107">Linki odwołań interfejsu API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="f7958-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="f7958-108">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="f7958-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f7958-109">W tym przewodniku dotyczącym języka F# 3.0 pokazano, w jaki sposób można uzyskać dostęp do danych mających określony typ w bazie danych SQL opartej na modelu Entity Data Model programu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f7958-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="f7958-110">W tym przewodniku przedstawiono sposób konfigurowania F # `SqlEntityConnection` typ dostawcy do użycia z bazy danych SQL, jak napisać zapytań dotyczących danych, sposób wywołania procedur przechowywanych w bazie danych, a także sposób korzystać z niektórych typów programu ADO.NET Entity Framework i metody upd uj bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="f7958-111">W tym przewodniku opisano następujące zadania, które trzeba wykonać, aby pomyślnie przerobić przewodnik:</span><span class="sxs-lookup"><span data-stu-id="f7958-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="f7958-112">Utworzenie bazy danych School</span><span class="sxs-lookup"><span data-stu-id="f7958-112">Create the School database</span></span>
<br />

- <span data-ttu-id="f7958-113">Utworzenie i skonfigurowanie projektu języka F#</span><span class="sxs-lookup"><span data-stu-id="f7958-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="f7958-114">Skonfiguruj typ dostawcy i połącz się modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f7958-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="f7958-115">W bazie danych</span><span class="sxs-lookup"><span data-stu-id="f7958-115">Query the database</span></span>
<br />

- <span data-ttu-id="f7958-116">Zaktualizowanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="f7958-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="f7958-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f7958-117">Prerequisites</span></span>
<span data-ttu-id="f7958-118">Aby wykonać te kroki, trzeba mieć dostęp do serwera, na którym działa program SQL Server umożliwiający utworzenie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="f7958-119">Utworzenie bazy danych School</span><span class="sxs-lookup"><span data-stu-id="f7958-119">Create the School database</span></span>
<span data-ttu-id="f7958-120">Bazę danych School możesz utworzyć na dowolnym serwerze, na którym działa program SQL Server i do którego masz dostęp administracyjny, ale możesz też użyć programu LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f7958-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="f7958-121">Aby utworzyć bazę danych School</span><span class="sxs-lookup"><span data-stu-id="f7958-121">To create the School database</span></span>

1. <span data-ttu-id="f7958-122">W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych** węzeł, a następnie wybierz pozycję **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="f7958-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="f7958-123">**Dodawanie połączenia** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f7958-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="f7958-124">W **nazwy serwera** polu, określ nazwę wystąpienia programu SQL Server, do których masz dostęp administratora lub określ (localdb\v11.0), jeśli nie masz dostępu do serwera.</span><span class="sxs-lookup"><span data-stu-id="f7958-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="f7958-125">Program SQL Server Express LocalDB dostarcza uproszczony serwer bazy danych, którego można używać na potrzeby tworzenia i testowania na swoim komputerze.</span><span class="sxs-lookup"><span data-stu-id="f7958-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="f7958-126">Aby uzyskać więcej informacji na temat LocalDB, zobacz [wskazówki: Tworzenie lokalnego pliku bazy danych w programie Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7958-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="f7958-127">Nowy węzeł jest tworzony w **Eksploratora serwera** w obszarze **połączenia danych**.</span><span class="sxs-lookup"><span data-stu-id="f7958-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="f7958-128">Otwórz menu skrótów do nowego węzła połączenia, a następnie wybierz pozycję **nowe zapytanie**.</span><span class="sxs-lookup"><span data-stu-id="f7958-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="f7958-129">Otwórz [tworzenie przykładowej bazy danych służbowych](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) w witrynie internetowej firmy Microsoft, a następnie kopiowania i wklejania skryptu bazy danych tworzącą służbowe bazy danych w oknie edytora.</span><span class="sxs-lookup"><span data-stu-id="f7958-129">Open [Creating the School Sample Database](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) on the Microsoft website, and then copy and paste the database script that creates the School database into the editor window.</span></span>
<br />


## <span data-ttu-id="f7958-130"><a name="BKMK_CreateConfigFSProj"></a></span><span class="sxs-lookup"><span data-stu-id="f7958-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="f7958-131">Utworzenie i skonfigurowanie projektu języka F#</span><span class="sxs-lookup"><span data-stu-id="f7958-131">Create and configure an F# project</span></span>
<span data-ttu-id="f7958-132">W tym kroku należy utworzyć projekt i skonfigurować go do używania dostawcy typów.</span><span class="sxs-lookup"><span data-stu-id="f7958-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="f7958-133">Aby utworzyć i skonfigurować projekt języka F#</span><span class="sxs-lookup"><span data-stu-id="f7958-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="f7958-134">Zamknij projekt poprzedniej, Utwórz innego projektu i nadaj mu nazwę **SchoolEDM**.</span><span class="sxs-lookup"><span data-stu-id="f7958-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="f7958-135">W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f7958-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="f7958-136">Wybierz **Framework** węzeł, a następnie w **Framework** wybierz **system.dane**, **System.Data.Entity**i **System.Data.Linq**.</span><span class="sxs-lookup"><span data-stu-id="f7958-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="f7958-137">Wybierz **rozszerzenia** węzła, Dodaj odwołanie do [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) zestawu, a następnie wybierz pozycję **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f7958-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="f7958-138">Dodaj następujący kod, aby zdefiniować moduł wewnętrzny i otworzyć odpowiednie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="f7958-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="f7958-139">Dostawca typów może wprowadzać typy tylko do prywatnej lub wewnętrznej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f7958-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="f7958-140">Aby uruchomić kod w tym przewodniku interaktywnie jako skrypt zamiast jako skompilowany program, otwórz menu skrótów węzła projektu, wybierz pozycję **Dodaj nowy element**, Dodaj plik skryptu języka F #, a następnie dodaj kod w każdym kroku do skryptu.</span><span class="sxs-lookup"><span data-stu-id="f7958-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="f7958-141">Aby załadować odwołania do zestawu, dodaj następujące wiersze.</span><span class="sxs-lookup"><span data-stu-id="f7958-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="f7958-142">Wyróżnij każdy blok kodu, który dodajesz, i użyj klawiszy Alt+Enter, aby uruchomić go w interakcyjnej wersji języka F#.</span><span class="sxs-lookup"><span data-stu-id="f7958-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="f7958-143">Skonfigurowanie dostawcy typów i nawiązanie połączenia z modelem Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="f7958-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="f7958-144">W tym kroku należy skonfigurować dostawcę typów z połączeniem danych i uzyskać kontekst danych, który umożliwi pracę z danymi.</span><span class="sxs-lookup"><span data-stu-id="f7958-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="f7958-145">Aby skonfigurować dostawcę typów i nawiązać połączenie z modelem Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="f7958-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="f7958-146">Wprowadź następujący kod, aby skonfigurować `SqlEntityConnection` typ dostawcy, który generuje typów F # oparte na modelu danych jednostki utworzonego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f7958-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="f7958-147">Zamiast pełnych parametrów połączenia EDMX, użyj jedynie parametrów połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="f7958-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="f7958-148">Ta akcja konfiguruje dostawcę typów z połączeniem z bazą danych, które zostało utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f7958-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="f7958-149">Właściwość `MultipleActiveResultSets` jest wymagana, gdy używasz programu ADO.NET Entity Framework, ponieważ ta właściwość umożliwia wielu poleceń do wykonania asynchronicznie w bazie danych jednego połączenia, które może nastąpić, często w kodzie programu ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f7958-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="f7958-150">Aby uzyskać więcej informacji, zobacz [wielu aktywnych zestawów wyników (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span><span class="sxs-lookup"><span data-stu-id="f7958-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="f7958-151">Pobierz kontekst danych, który jest obiektem zawierającym tabele bazy danych jako właściwości oraz procedury składowane i funkcje bazy danych jako metody.</span><span class="sxs-lookup"><span data-stu-id="f7958-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="f7958-152">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="f7958-152">Querying the database</span></span>
<span data-ttu-id="f7958-153">W tym kroku należy użyć wyrażeń zapytania języka F#, aby wykonać różne zapytania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="f7958-154">Aby wykonać zapytanie dotyczące danych</span><span class="sxs-lookup"><span data-stu-id="f7958-154">To query the data</span></span>

- <span data-ttu-id="f7958-155">Wprowadź następujący kod, aby utworzyć zapytanie dotyczące danych w modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="f7958-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="f7958-156">Należy zwrócić uwagę na efekt działania właściwości Pluralize = true, która powoduje zmianę nazw tabel bazy danych z Course na Courses i z Person na People.</span><span class="sxs-lookup"><span data-stu-id="f7958-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a><span data-ttu-id="f7958-157">Zaktualizowanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="f7958-157">Updating the database</span></span>
<span data-ttu-id="f7958-158">Aby zaktualizować bazę danych, należy użyć klas i metod programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f7958-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="f7958-159">Z dostawcą typów SQLEntityConnection można używać dwóch typów kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="f7958-160">Najpierw `ServiceTypes.SimpleDataContextTypes.EntityContainer` jest kontekst uproszczony danych, który zawiera tylko podane właściwości reprezentujących tabele i kolumny.</span><span class="sxs-lookup"><span data-stu-id="f7958-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="f7958-161">Po drugie, kontekst danych jest wystąpienia klasy Entity Framework `System.Data.Objects.ObjectContext`, który zawiera metodę `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` dodawania wierszy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="f7958-162">Program Entity Framework rozpoznaje tabele i relacje między nimi, a więc wymusza spójność bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f7958-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="f7958-163">Aby zaktualizować bazę danych</span><span class="sxs-lookup"><span data-stu-id="f7958-163">To update the database</span></span>

1. <span data-ttu-id="f7958-164">Dodaj poniższy kod do programu.</span><span class="sxs-lookup"><span data-stu-id="f7958-164">Add the following code to your program.</span></span> <span data-ttu-id="f7958-165">W tym przykładzie należy dodać dwa obiekty powiązane relacją, a następnie należy dodać instruktora oraz przypisane biuro.</span><span class="sxs-lookup"><span data-stu-id="f7958-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="f7958-166">Tabela `OfficeAssignments` zawiera `InstructorID` kolumny, która odwołuje się do `PersonID` kolumny w `Person` tabeli.</span><span class="sxs-lookup"><span data-stu-id="f7958-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

<span data-ttu-id="f7958-167">Nic nie zostanie zmieniona w bazie danych do czasu wywołania `System.Data.Objects.ObjectContext.SaveChanges`.</span><span class="sxs-lookup"><span data-stu-id="f7958-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="f7958-168">Teraz przywróć bazę danych do wcześniejszego stanu, usuwając obiekty, które zostały dodane.</span><span class="sxs-lookup"><span data-stu-id="f7958-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
<span data-ttu-id="f7958-169">Gdy jest używane wyrażenie zapytania, musisz pamiętać, że zapytanie jest obliczane z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="f7958-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="f7958-170">Z tego powodu baza danych pozostaje otwarta do odczytu podczas dowolnych obliczeń łańcuchowych, takich jak bloki wyrażenia lambda po każdym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f7958-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="f7958-171">Dowolna operacja w bazie danych, która jawnie lub niejawnie używa transakcji, musi nastąpić po zakończeniu operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="f7958-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="f7958-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f7958-172">Next Steps</span></span>
<span data-ttu-id="f7958-173">Eksploruj inne opcje zapytania, przeglądając operatorów zapytań dostępnych w [wyrażenia zapytania](../../language-reference/query-expressions.md), a także przejrzeć [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) zrozumieć, jakie funkcje są dostępne, gdy Korzystając z tego typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f7958-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="f7958-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7958-174">See Also</span></span>
[<span data-ttu-id="f7958-175">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="f7958-175">Type Providers</span></span>](index.md)  
[<span data-ttu-id="f7958-176">Sqlentityconnection — dostawca typów</span><span class="sxs-lookup"><span data-stu-id="f7958-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[<span data-ttu-id="f7958-177">Wskazówki: Generowanie typów F # za pomocą pliku schematu EDMX</span><span class="sxs-lookup"><span data-stu-id="f7958-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)  
[<span data-ttu-id="f7958-178">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7958-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)  
[<span data-ttu-id="f7958-179">Omówienie plików edmx</span><span class="sxs-lookup"><span data-stu-id="f7958-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[<span data-ttu-id="f7958-180">EDM Generator &#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="f7958-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)  
