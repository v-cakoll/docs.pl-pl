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
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>Wskazówki: generowanie typów F# za pomocą pliku schematu EDMX

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym przewodniku dotyczącym języka F# 3.0 pokazano, jak tworzyć typy danych reprezentowane przez model Entity Data Model (EDM), którego schemat jest określony w pliku edmx. W tym przewodniku pokazano również sposób użycia dostawcy typów EdmxFile. Przed rozpoczęciem należy zastanowić się, czy nie będzie lepiej używać dostawcy typów SqlEntityConnection. Dostawca typów SqlEntityConnection sprawdza się najlepiej w scenariuszach obejmujących aktywną bazę danych, z którą można łączyć się podczas fazy opracowywania projektu i nie trzeba pamiętać o określaniu parametrów połączenia w czasie kompilacji. Jednak ten dostawca typów ma również ograniczenia, ponieważ nie uwidacznia tak wielu funkcji bazy danych, jak dostawca typów EdmxFile. Ponadto jeśli dla projektu, w którym jest używany model Entity Data Model, nie jest używane aktywne połączenie z bazą danych, do tworzenia kodu operacji wykonywanych w bazie danych można używać pliku edmx. Użycie dostawcy typów EdmxFile powoduje, że kompilator języka F# uruchamia program EdmGen.exe w celu wygenerowania dostarczanych przez siebie typów.

W tym przewodniku opisano następujące zadania, które trzeba wykonać, aby pomyślnie przerobić przewodnik:


- Tworzenie pliku EDMX
<br />

- Tworzenie projektu
<br />

- Znajdowanie lub tworzenie danych jednostki modelu parametrów połączenia
<br />

- Konfigurowanie dostawcy typów
<br />

- Wykonywanie zapytań dotyczących danych
<br />

- Wywoływanie procedury składowanej
<br />


## <a name="prerequisites"></a>Wymagania wstępne

## <a name="creating-an-edmx-file"></a>Tworzenie pliku EDMX
Jeśli masz już plik EDMX, możesz pominąć ten krok.


#### <a name="to-create-an-edmx-file"></a>Aby utworzyć plik EDMX

- Jeśli nie masz jeszcze pliku EDMX, można postępuj zgodnie z instrukcjami na końcu tego przewodnika w kroku [Konfigurowanie modelu Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).
<br />

## <a name="creating-the-project"></a>Tworzenie projektu
W tym kroku należy utworzyć projekt i dodać do niego odpowiednie odwołania w celu użycia dostawcy typów EDMX.


#### <a name="to-create-and-set-up-an-f-project"></a>Aby utworzyć i skonfigurować projekt języka F#

1. Zamknij poprzedni projekt i utwórz nowy projekt o nazwie SchoolEDM.
<br />

2. W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.
<br />

3. W **zestawy** obszarze, wybierz **Framework** węzła.
<br />

4. Na liście dostępnych zestawów, wybierz **System.Data.Entity** i **System.Data.Linq** zestawy, a następnie wybierz pozycję **Dodaj** przycisk, aby dodać odwołania do tych zestawy do projektu.
<br />

5. W **zestawy** wybierz opcję **rozszerzenia** węzła.
<br />

6. Z listy dostępnych rozszerzeń dodaj odwołanie do zestawu FSharp.Data.TypeProviders.
<br />

7. Dodaj poniższy kod, aby otworzyć odpowiednie przestrzenie nazw.
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>Znajdowanie lub tworzenie parametrów połączenia dla modelu Entity Data Model
Parametry połączenia dla modelu Entity Data Model (parametry połączenia EDMX) zawierają nie tylko parametry połączenia dla dostawcy bazy danych, ale również dodatkowe informacje. Na przykład parametry połączenia EDMX dla prostej bazy danych programu SQL Server przypominają poniższy kod.

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

Aby uzyskać więcej informacji dotyczących parametrów połączenia w pliku EDMX, zobacz [parametry połączenia](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>Aby znaleźć lub utworzyć parametry połączenia dla modelu Entity Data Model

1. Ręczne generowanie parametrów połączenia EDMX może być trudne, więc można zaoszczędzić czas, generując je programowo. Jeśli znasz parametry połączenia EDMX, możesz pominąć ten krok i po prostu użyć tych parametrów w następnym kroku. Jeśli ich nie znasz, użyj poniższego kodu w celu wygenerowania parametrów połączenia EDMX na podstawie podanych parametrów połączenia z bazą danych.
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

## <a name="configuring-the-type-provider"></a>Konfigurowanie dostawcy typów
W tym kroku należy utworzyć i skonfigurować dostawcę typów, używając parametrów połączenia EDMX, i wygenerować typy dla schematu zdefiniowanego w pliku edmx.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Aby skonfigurować dostawcę typów i wygenerować typy

1. Skopiuj plik edmx wygenerowany w pierwszym kroku tego przewodnika do folderu projektu.
<br />

2. Otwórz menu skrótów węzła projektu w F # projektu, wybierz **Dodaj istniejący element**, a następnie wybierz pozycję pliku edmx, aby dodać go do projektu.
<br />

3. Wprowadź następujący kod, aby aktywować dostawcę typów dla pliku edmx. Zastąp *serwera*\*wystąpienia * z nazwą serwera, który jest uruchomiony program SQL Server i nazwę wystąpienia i użyj nazwy pliku edmx z pierwszym krokiem w ramach tego przewodnika.
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>Wykonywanie zapytań dotyczących danych
W tym kroku należy użyć wyrażeń zapytania języka F# w celu wykonania zapytania w bazie danych.


#### <a name="to-query-the-data"></a>Aby wykonać zapytanie dotyczące danych

- Wprowadź poniższy kod w celu wykonania zapytania dotyczącego danych w modelu Entity Data Model.
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

## <a name="calling-a-stored-procedure"></a>Wywoływanie procedury składowanej
Za pomocą dostawcy typów EDMX można wywoływać procedury składowane. W poniższej procedurze służbowe baza danych zawiera procedurę składowaną **UpdatePerson**, aktualizacje rekord danego nowe wartości w kolumnach. Można użyć tej procedury składowanej, ponieważ jest ona uwidoczniona jako metoda w typie DataContext.


#### <a name="to-call-a-stored-procedure"></a>Aby wywołać procedurę składowaną

- Dodaj następujący kod w celu aktualizacji rekordów.
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

W przypadku pomyślnego wywołania wynik wyniesie 1. Zwróć uwagę, że **exactlyOne** jest używany w wyrażeniu zapytania, aby upewnić się, że tylko jeden wynik zostanie zwrócony; w przeciwnym, jest zwracany wyjątek. Również, aby łatwiej pracować z wartości null, można użyć prostej **nullable** funkcji, która jest zdefiniowana w tym kodzie można utworzyć wartości null wartości poza wartością zwykłej.

<br />

## <a name="configuring-the-entity-data-model"></a>Konfigurowanie modelu Entity Data Model
Tę procedurę należy wykonać tylko wtedy, gdy użytkownik chce wiedzieć, jak wygenerować pełny model Entity Data Model na podstawie bazy danych, a nie ma bazy danych, której można by użyć do testowania.


#### <a name="to-configure-the-entity-data-model"></a>Aby skonfigurować model Entity Data Model

1. Na pasku menu wybierz **SQL**, **edytora języka Transact-SQL**, **nowe zapytanie** tworzenia bazy danych. Jeśli zostanie wyświetlony monit, określ serwer bazy danych i wystąpienie.
<br />

2. Skopiuj i Wklej zawartość skryptu bazy danych, który utworzy bazę danych dla użytkowników domowych, zgodnie z opisem w [dokumentację programu Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) w Centrum deweloperów danych.
<br />

3. Wybranie przycisku paska narzędzi z symbolem trójkąt lub wybierając pozycję klawiszy Ctrl + Q, uruchom skrypt SQL.
<br />

4. W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych**, wybierz **Dodawanie połączenia**, a następnie wprowadź nazwę serwera bazy danych, nazwę wystąpienia , a bazą danych służbowych.
<br />

5. Tworzenie projektu C# lub Visual Basic aplikacji konsoli, otwórz menu skrótów, wybierz pozycję **Dodaj nowy element**, a następnie wybierz pozycję **modelu danych jednostki ADO.NET**.
<br />  Zostanie otwarty Kreator modelu Entity Data Model. Za pomocą tego kreatora można wybrać sposób tworzenia modelu Entity Data Model.
<br />

6. W obszarze **wybierz zawartość modelu**, wybierz pozycję **generowania z bazy danych** pole wyboru.
<br />

7. Na następnej stronie wybierz nowo utworzoną bazę danych School jako połączenia danych.
<br />  To połączenie powinno przypominać  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.
<br />

8. Skopiuj parametry połączenia obiektu do Schowka, ponieważ te parametry mogą okazać się później ważne.
<br />

9. Upewnij się, że pole wyboru, aby zapisać parametry połączenia jednostki do **App.Config** plików jest zaznaczona i zanotuj wartość ciągu w polu tekstowym, które powinny pomóc Ci w znalezieniu ciągu połączenia później, w razie potrzeby.
<br />

10. Na następnej stronie wybierz **tabel** i **procedury składowane i funkcje**.
<br />  Wybranie tych węzłów najwyższego poziomu powoduje wybranie wszystkich tabel, procedur składowanych i funkcji. Można je także wybrać indywidualnie.
<br />

11. Upewnij się, że są też zaznaczone pola wyboru dla innych ustawień.
<br />  Pierwszy **Pluralize lub nadaj wygenerowanym nazwom obiektów** pole wyboru wskazuje, czy można zmienić pojedynczej formularze na liczbie mnogiej odpowiadające konwencje w nazywania obiektów, które reprezentują tabel bazy danych. **Dołącz kolumny klucza obcego do modelu** pole wyboru określa, czy dołączać pól, dla których ma na celu dołączenia do innych pól typów obiektów, które są generowane dla schematu bazy danych. Trzecie pole wyboru wskazuje, czy w modelu mają być uwzględniane procedury składowane i funkcje.
<br />

12. Wybierz **Zakończ** przycisk, aby wygenerować plik edmx, który zawiera modelu Entity Data Model oparty na bazie danych służbowych.
<br />  Plik, **Model1.edmx**, zostanie dodany do projektu, a schemat bazy danych są wyświetlane.
<br />

13. Na pasku menu wybierz **widoku**, **inne okna**, **przeglądarka modeli danych jednostki** umożliwia wyświetlenie wszystkich szczegółów modelu lub **szczegóły mapowania modelu danych jednostki**  można otworzyć okna, pokazujący sposób mapowania modelu wygenerowanego obiektu do bazy danych, tabel i kolumn.
<br />


## <a name="next-steps"></a>Następne kroki
Eksploruj inne zapytania, analizując operatorów zapytań dostępne wymienionych w [wyrażenia zapytania](../../language-reference/query-expressions.md).


## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)

[Edmxfile — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów i jednostek](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[Omówienie plików edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM Generator &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

