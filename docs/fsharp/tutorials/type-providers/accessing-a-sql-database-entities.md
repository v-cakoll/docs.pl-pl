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
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów i jednostek

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](https://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym przewodniku dotyczącym języka F# 3.0 pokazano, w jaki sposób można uzyskać dostęp do danych mających określony typ w bazie danych SQL opartej na modelu Entity Data Model programu ADO.NET. W tym przewodniku przedstawiono sposób konfigurowania F # `SqlEntityConnection` typ dostawcy do użycia z bazy danych SQL, jak napisać zapytań dotyczących danych, sposób wywołania procedur przechowywanych w bazie danych, a także sposób korzystać z niektórych typów programu ADO.NET Entity Framework i metody upd uj bazy danych.

W tym przewodniku opisano następujące zadania, które trzeba wykonać, aby pomyślnie przerobić przewodnik:


- Utworzenie bazy danych School
<br />

- Utworzenie i skonfigurowanie projektu języka F#
<br />

- Skonfiguruj typ dostawcy i połącz się modelu danych jednostki
<br />

- W bazie danych
<br />

- Zaktualizowanie bazy danych
<br />


## <a name="prerequisites"></a>Wymagania wstępne
Aby wykonać te kroki, trzeba mieć dostęp do serwera, na którym działa program SQL Server umożliwiający utworzenie bazy danych.

## <a name="create-the-school-database"></a>Utworzenie bazy danych School
Bazę danych School możesz utworzyć na dowolnym serwerze, na którym działa program SQL Server i do którego masz dostęp administracyjny, ale możesz też użyć programu LocalDB.


#### <a name="to-create-the-school-database"></a>Aby utworzyć bazę danych School

1. W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych** węzeł, a następnie wybierz pozycję **Dodawanie połączenia**.
<br />  **Dodawanie połączenia** zostanie wyświetlone okno dialogowe.
<br />

2. W **nazwy serwera** polu, określ nazwę wystąpienia programu SQL Server, do których masz dostęp administratora lub określ (localdb\v11.0), jeśli nie masz dostępu do serwera.
<br />  Program SQL Server Express LocalDB dostarcza uproszczony serwer bazy danych, którego można używać na potrzeby tworzenia i testowania na swoim komputerze. Aby uzyskać więcej informacji na temat LocalDB, zobacz [wskazówki: Tworzenie lokalnego pliku bazy danych w programie Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).
<br />  Nowy węzeł jest tworzony w **Eksploratora serwera** w obszarze **połączenia danych**.
<br />

3. Otwórz menu skrótów do nowego węzła połączenia, a następnie wybierz pozycję **nowe zapytanie**.
<br />

4. Otwórz [tworzenie przykładowej bazy danych służbowych](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) w witrynie internetowej firmy Microsoft, a następnie kopiowania i wklejania skryptu bazy danych tworzącą służbowe bazy danych w oknie edytora.
<br />


## <a name="BKMK_CreateConfigFSProj"></a>

## <a name="create-and-configure-an-f-project"></a>Utworzenie i skonfigurowanie projektu języka F#
W tym kroku należy utworzyć projekt i skonfigurować go do używania dostawcy typów.


#### <a name="to-create-and-configure-an-f-project"></a>Aby utworzyć i skonfigurować projekt języka F#

1. Zamknij projekt poprzedniej, Utwórz innego projektu i nadaj mu nazwę **SchoolEDM**.
<br />

2. W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.
<br />

3. Wybierz **Framework** węzeł, a następnie w **Framework** wybierz **system.dane**, **System.Data.Entity**i **System.Data.Linq**.
<br />

4. Wybierz **rozszerzenia** węzła, Dodaj odwołanie do [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) zestawu, a następnie wybierz pozycję **OK** przycisk, aby zamknąć okno dialogowe.
<br />

5. Dodaj następujący kod, aby zdefiniować moduł wewnętrzny i otworzyć odpowiednie przestrzenie nazw. Dostawca typów może wprowadzać typy tylko do prywatnej lub wewnętrznej przestrzeni nazw.
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. Aby uruchomić kod w tym przewodniku interaktywnie jako skrypt zamiast jako skompilowany program, otwórz menu skrótów węzła projektu, wybierz pozycję **Dodaj nowy element**, Dodaj plik skryptu języka F #, a następnie dodaj kod w każdym kroku do skryptu. Aby załadować odwołania do zestawu, dodaj następujące wiersze.
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. Wyróżnij każdy blok kodu, który dodajesz, i użyj klawiszy Alt+Enter, aby uruchomić go w interakcyjnej wersji języka F#.
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Skonfigurowanie dostawcy typów i nawiązanie połączenia z modelem Entity Data Model
W tym kroku należy skonfigurować dostawcę typów z połączeniem danych i uzyskać kontekst danych, który umożliwi pracę z danymi.


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Aby skonfigurować dostawcę typów i nawiązać połączenie z modelem Entity Data Model

1. Wprowadź następujący kod, aby skonfigurować `SqlEntityConnection` typ dostawcy, który generuje typów F # oparte na modelu danych jednostki utworzonego wcześniej. Zamiast pełnych parametrów połączenia EDMX, użyj jedynie parametrów połączenia SQL.
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  Ta akcja konfiguruje dostawcę typów z połączeniem z bazą danych, które zostało utworzone wcześniej. Właściwość `MultipleActiveResultSets` jest wymagana, gdy używasz programu ADO.NET Entity Framework, ponieważ ta właściwość umożliwia wielu poleceń do wykonania asynchronicznie w bazie danych jednego połączenia, które może nastąpić, często w kodzie programu ADO.NET Entity Framework. Aby uzyskać więcej informacji, zobacz [wielu aktywnych zestawów wyników (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).
<br />

2. Pobierz kontekst danych, który jest obiektem zawierającym tabele bazy danych jako właściwości oraz procedury składowane i funkcje bazy danych jako metody.
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>Wykonywanie zapytania w bazie danych
W tym kroku należy użyć wyrażeń zapytania języka F#, aby wykonać różne zapytania w bazie danych.


#### <a name="to-query-the-data"></a>Aby wykonać zapytanie dotyczące danych

- Wprowadź następujący kod, aby utworzyć zapytanie dotyczące danych w modelu Entity Data Model. Należy zwrócić uwagę na efekt działania właściwości Pluralize = true, która powoduje zmianę nazw tabel bazy danych z Course na Courses i z Person na People.
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

## <a name="updating-the-database"></a>Zaktualizowanie bazy danych
Aby zaktualizować bazę danych, należy użyć klas i metod programu Entity Framework. Z dostawcą typów SQLEntityConnection można używać dwóch typów kontekstu danych. Najpierw `ServiceTypes.SimpleDataContextTypes.EntityContainer` jest kontekst uproszczony danych, który zawiera tylko podane właściwości reprezentujących tabele i kolumny. Po drugie, kontekst danych jest wystąpienia klasy Entity Framework `System.Data.Objects.ObjectContext`, który zawiera metodę `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` dodawania wierszy w bazie danych. Program Entity Framework rozpoznaje tabele i relacje między nimi, a więc wymusza spójność bazy danych.


#### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych

1. Dodaj poniższy kod do programu. W tym przykładzie należy dodać dwa obiekty powiązane relacją, a następnie należy dodać instruktora oraz przypisane biuro. Tabela `OfficeAssignments` zawiera `InstructorID` kolumny, która odwołuje się do `PersonID` kolumny w `Person` tabeli.
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

Nic nie zostanie zmieniona w bazie danych do czasu wywołania `System.Data.Objects.ObjectContext.SaveChanges`.
<br />

2. Teraz przywróć bazę danych do wcześniejszego stanu, usuwając obiekty, które zostały dodane.
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
Gdy jest używane wyrażenie zapytania, musisz pamiętać, że zapytanie jest obliczane z opóźnieniem. Z tego powodu baza danych pozostaje otwarta do odczytu podczas dowolnych obliczeń łańcuchowych, takich jak bloki wyrażenia lambda po każdym wyrażeniu zapytania. Dowolna operacja w bazie danych, która jawnie lub niejawnie używa transakcji, musi nastąpić po zakończeniu operacji odczytu.


## <a name="next-steps"></a>Następne kroki
Eksploruj inne opcje zapytania, przeglądając operatorów zapytań dostępnych w [wyrażenia zapytania](../../language-reference/query-expressions.md), a także przejrzeć [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) zrozumieć, jakie funkcje są dostępne, gdy Korzystając z tego typu dostawcy.


## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)  
[Sqlentityconnection — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[Wskazówki: Generowanie typów F # za pomocą pliku schematu EDMX](generating-fsharp-types-from-edmx.md)  
[Program Entity Framework na platformie ADO.NET](https://msdn.microsoft.com/library/bb399572)  
[Omówienie plików edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[EDM Generator &#40;EdmGen.exe&#41;](https://msdn.microsoft.com/library/bb387165)  
