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
ms.openlocfilehash: c99afc1121b4f0d6d05ef82681a32437ede06e42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>Wskazówki: uzyskiwanie dostępu do bazy danych SQL Database za pomocą dostawców typów

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym przewodniku opisano sposób korzystania z dostawcy typów SqlDataConnection (LINQ to SQL) dostępnym w F # 3.0 do generowania typów danych w bazie danych SQL, jeśli masz aktywne połączenie z bazą danych. Jeśli nie masz aktywne połączenie z bazą danych, ale masz LINQ do SQL schematu pliku (DBML), zobacz [wskazówki: generowanie typów F #, pliku DBML](generating-fsharp-types-from-dbml.md).

W tym przewodniku przedstawiono następujące zadania. Te zadania odbywa się w następującej kolejności wskazówki powiodła się:


- Trwa przygotowywanie bazy danych testu

- Tworzenie projektu

- Konfigurowanie dostawcy typów

- Wykonywanie zapytań dotyczących danych

- Praca z polami wartości null

- Wywoływanie procedury składowanej

- Zaktualizowanie bazy danych

- Wykonywanie kodu języka Transact-SQL

- Przy użyciu kontekstu danych

- Usuwanie danych

- Tworzenie testowej bazy danych (w razie potrzeby)

## <a name="preparing-a-test-database"></a>Trwa przygotowywanie bazy danych testu
Na serwerze, na którym działa program SQL Server Utwórz bazę danych do celów testowych. Można użyć bazy danych Utwórz skrypt u dołu tej strony w sekcji [tworzenia bazy danych testu](#creating-a-test-database) w tym celu.


#### <a name="to-prepare-a-test-database"></a>Aby przygotować testowej bazy danych

Aby uruchomić skrypt tworzenia mojabazadanych, otwórz **widoku** menu, a następnie wybierz pozycję **Eksplorator obiektów SQL Server** lub wybierz polecenie Ctrl +\, klawiszy Ctrl + S. W **Eksplorator obiektów SQL Server** okna, otwórz menu skrótów odpowiednie wystąpienie, wybierz pozycję **nowe zapytanie**, skopiuj skrypt u dołu tej strony, a następnie wklej skrypt do edytora. Aby uruchomić skrypt SQL, wybierz ikony paska narzędzi trójkątny znak lub klawiszy Ctrl + Q. Aby uzyskać więcej informacji na temat **Eksplorator obiektów SQL Server**, zobacz [programowanie połączonej bazy danych](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).


## <a name="creating-the-project"></a>Tworzenie projektu
Następnie możesz utworzyć projekt aplikacji F #.


#### <a name="to-create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu

1. Utwórz nowy projekt aplikacji w języku F #.

2. Dodaj odwołania do [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), jak również `System.Data`, i `System.Data.Linq`.

3. Otwórz odpowiednie przestrzenie nazw, dodając następujące wiersze kodu do góry pliku Program.fs kodu języka F #.

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. Podobnie jak w przypadku większości F # programów, w tym przewodniku jako skompilowany program umożliwia wykonanie kodu lub można uruchomić w trybie interakcyjnym jako skrypt. Jeśli wolisz korzystać ze skryptów, otwórz menu skrótów węzła projektu, zaznacz **Dodaj nowy element**, Dodaj plik skryptu języka F # i Dodaj kod w każdym kroku do skryptu. Należy dodać następujące wiersze na początku pliku można załadować odwołania do zestawów.

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  Następnie możesz wybrać każdy blok kodu, jak dodać go i naciśnij klawisze Alt + Enter, aby uruchomić go w F # Interactive.

## <a name="setting-up-a-type-provider"></a>Konfigurowanie dostawcy typów
W tym kroku utworzysz typ dostawcy do schematu bazy danych.


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>Aby skonfigurować typ dostawcy z połączenia bezpośredniego bazy danych

Istnieją dwa wiersze krytyczne kodu, które są potrzebne do tworzenia typów, które umożliwiają zapytanie dotyczące bazy danych SQL przy użyciu dostawcy typów. Najpierw należy utworzyć wystąpienia dostawcy typów. W tym celu należy utworzyć wygląd skrót typu `SqlDataConnection` z parametrem ogólnym statycznych. `SqlDataConnection`Dostawca typu SQL i nie należy mylić z `SqlConnection` typu, który jest używany w programowaniu ADO.NET. Jeśli baza danych, który chcesz połączyć się z, a ma parametry połączenia, należy użyć poniższego kodu do wywołania typu dostawcy. Zastąp własne parametry połączenia dla ciągu przykład podane. Na przykład jeśli serwer jest MÓJSERWER i wystąpienie bazy danych jest WYSTĄPIENIEM mojabazadanych jest nazwa bazy danych i chcesz uzyskać dostępu do bazy danych, a następnie parametry połączenia za pomocą uwierzytelniania systemu Windows będzie jako podane w poniższy przykładowy kod.

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

Teraz masz typu `dbSchema`, która jest typu nadrzędny, który zawiera wszystkie wygenerowane typy reprezentujące tabel bazy danych. Masz również obiektu `db`, zainstalowanym jako elementy członkowskie wszystkie tabele w bazie danych. Właściwości są nazwy tabel i typ właściwości jest generowany przez kompilator języka F #. Same typy są wyświetlane jako typy zagnieżdżone w obszarze `dbSchema.ServiceTypes`. W związku z tym wszystkie dane pobierane dla wierszy z tych tabel jest wystąpieniem odpowiedniego typu, który został wygenerowany dla tej tabeli. Nazwa typu jest `ServiceTypes.Table1`.

Aby zapoznać się z języka F # interpretowanie zapytania do zapytania SQL, przejrzyj wiersza, który ustawia `Log` właściwości w kontekście danych.

Umożliwiający dalszą analizę typy utworzone przez typ dostawcy, Dodaj następujący kod.

```fsharp
let table1 = db.Table1
```

Umieść kursor nad `table1` aby zobaczyć jego typu. Jest on typu `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` i argumentów ogólnych oznacza, że typ każdy wiersz jest wygenerowanego typu `dbSchema.ServiceTypes.Table1`. Kompilator tworzy podobny typ dla każdej tabeli w bazie danych.

## <a name="querying-the-data"></a>Wykonywanie zapytań dotyczących danych
W tym kroku należy napisać zapytanie wyrażenia zapytania F #.


#### <a name="to-query-the-data"></a>Aby wykonać zapytanie dotyczące danych

1. Teraz można tworzyć zapytania dla tej tabeli w bazie danych. Dodaj następujący kod.

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  Wygląd Word `query` wskazuje, czy jest to wyrażenie zapytania typu obliczenia wyrażenia, które generuje kolekcji podobnych wyników zapytania typowe bazy danych. Aktywuj zapytania, będzie mógł przeglądać jest wystąpienie [LINQ.querybuilder — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), typu, który definiuje query — wyrażenie obliczeń. Jeśli w ustawieniu kursora `query1`, zobaczysz, że jest wystąpienie `System.Linq.IQueryable`. Jak wynika z nazwy, `System.Linq.IQueryable` reprezentuje dane, które można zbadać, nie wyniku zapytania. Zapytanie podlega obliczanie leniwe, co oznacza, że baza danych jest tylko zbadać, gdy obliczyć wyniku zapytania. Końcowego wiersza przekazuje zapytanie za pomocą `Seq.iter`. Zapytania są wyliczalny i może należy powtórzyć jak sekwencji. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytania](../../language-reference/query-expressions.md).

2. Teraz Dodaj operator zapytania do zapytania. Istnieje wiele operatorów zapytań dostępne, można tworzyć bardziej złożone zapytania. W tym przykładzie przedstawiono również można wyeliminować zmienną zapytania i zamiast tego użyj operatora potoku.

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. Dodaj bardziej złożonego zapytania z sprzężenia dwóch tabel.

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

4. W kodzie rzeczywistych parametrów w zapytaniu są zazwyczaj wartości lub zmienne, stałe nie kompilacji. Dodaj następujący kod, który opakowuje kwerendy w funkcji, która przyjmuje parametr, a następnie wywołuje tej funkcji na wartość 10.

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Praca z polami wartości null
W bazach danych pola często dopuszcza wartości null. System typów .NET nie można używać zwykłych danych liczbowych typów danych, które umożliwia wartości null, ponieważ te typy nie mają wartości null jako możliwą wartość. W związku z tym te wartości są reprezentowane przez wystąpień `System.Nullable` typu. Zamiast wartości tych pól bezpośrednio z nazwę pola, musisz dodać kilka dodatkowych czynności. Można użyć `System.Nullable.Value` właściwość, aby uzyskać dostęp do podstawowych wartości typu dopuszczającego wartość null. `System.Nullable.Value` Właściwość zgłasza wyjątek, jeśli obiekt ma wartość null zamiast wartości. Można użyć `System.Nullable.HasValue` logiczna metody w celu określenia, czy istnieje wartość lub użyj `System.Nullable.GetValueOrDefault()` zapewnienie ma wartość rzeczywistą we wszystkich przypadkach. Jeśli używasz `System.Nullable.GetValueOrDefault()` i jest on wartość null w bazie danych, a następnie zostanie zastąpiony z wartości, takich jak ciągu pustego ciągu typów, punkt typy 0 dla typów całkowitych lub 0,0 dla zmiennoprzecinkową.

Kiedy należy przeprowadzić testy równości lub porównania o wartości null w `where` klauzuli w zapytaniu, można użyć operatory dopuszczające wartość null w [LINQ.nullableoperators — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d). Są to takie jak operatory porównania regularne `=`, `>`, `<=`i tak dalej z tą różnicą, że znak zapytania pojawia się po lewej stronie lub po prawej stronie operatora skutkującej wartości null. Na przykład operator `>?` jest większy-niż operator o wartości null po prawej stronie. Sposób pracy tych operatorów jest, że jeśli którejś wyrażenie ma wartość null, wyrażenie daje w wyniku `false`. W `where` klauzuli, zazwyczaj oznacza to, że wiersze zawierające pól o wartości null są niezaznaczone i nie są zwracane w wynikach zapytania.


#### <a name="to-work-with-nullable-fields"></a>Aby pracować z polami wartości null

Poniższy kod przedstawia pracy z wartości null. przyjęto założenie, że **TestData1** jest polem Liczba całkowita, która zezwala na wartości null.

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

## <a name="calling-a-stored-procedure"></a>Wywoływanie procedury składowanej
Wszystkie procedury przechowywane w bazie danych może być wywołana z F #. Należy ustawić parametr statyczny `StoredProcedures` do `true` w wystąpienia typu dostawcy. Typ dostawcy `SqlDataConnection` zawiera kilka metod statycznych, których można użyć do skonfigurowania typy, które są generowane. Aby uzyskać pełny opis tych, zobacz [sqldataconnection — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d). Metody w typie kontekstu danych jest generowany dla każdej procedury składowanej.


#### <a name="to-call-a-stored-procedure"></a>Aby wywołać procedurę składowaną

Jeśli procedury składowane pobiera parametry, które dopuszczają wartości null, należy przekazać odpowiedni `System.Nullable` wartość. Wartość zwracaną przez metodę procedury przechowywanej, która zwraca skalarnej lub tabela jest `System.Data.Linq.ISingleResult`, który zawiera właściwości, które umożliwiają dostęp do danych zwracanych. Typ argumentu dla `System.Data.Linq.ISingleResult` zależy od określonej procedury i jest również jeden z typów, które generuje typ dostawcy. Dla procedury składowanej o nazwie `Procedure1`, jest typu `Procedure1Result`. Typ `Procedure1Result` zawiera nazwy kolumn w tabeli zwracane lub procedury przechowywanej, która zwraca wartość skalarną reprezentuje wartość zwracaną.

Poniższy kod przyjęto założenie, że istnieje procedura `Procedure1` bazy danych, która przyjmuje dwa nullable liczb całkowitych jako parametry, uruchamia zapytanie zwracające kolumny o nazwie `TestData1`i zwraca liczbę całkowitą.

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

## <a name="updating-the-database"></a>Zaktualizowanie bazy danych
Typ LINQ DataContext zawiera metody, które ułatwiają wykonywanie aktualizacji transakcyjne bazy danych w sposób wpisaniu z wygenerowane typy.


#### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych

1. W poniższym kodzie kilka wierszy są dodawane do bazy danych. Jeśli dodajesz wiersza, możesz użyć `System.Data.Linq.Table.InsertOnSubmit()` Aby określić nowy wiersz do dodania. W przypadku wstawiania wiele wierszy, należy umieścić je do kolekcji i wywołania `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`. Podczas wywoływania jednej z tych metod, bazy danych nie ulega zmianie natychmiast. Należy wywołać `System.Data.Linq.DataContext.SubmitChanges` faktycznie zatwierdzić zmiany. Domyślny, wszystko, co należy wykonać przed wywołać `System.Data.Linq.DataContext.SubmitChanges` niejawnie jest częścią tej samej transakcji.

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

2. Teraz wyczyścić wiersze wywołując operację usuwania.

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

## <a name="executing-transact-sql-code"></a>Wykonywanie kodu języka Transact-SQL
Można również określić bezpośrednio przy użyciu języka Transact-SQL `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` metoda `DataContext` klasy.


#### <a name="to-execute-custom-sql-commands"></a>Do wykonania polecenia SQL niestandardowe

Poniższy kod przedstawia sposób wysłania poleceń SQL do wstawienia rekordu do tabeli, a także aby usunąć rekord z tabeli.

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

## <a name="using-the-full-data-context"></a>Przy użyciu kontekstu danych
W poprzednich przykładach `GetDataContext` użyto metody można uzyskać, co jest nazywane *kontekstu danych uproszczony* do schematu bazy danych. Kontekst danych uproszczony jest łatwiejsze w są tworzenia zapytań, ponieważ nie są dostępne jako wiele elementów członkowskich. W związku z tym podczas przeglądania właściwości w IntelliSense można skoncentrować się na temat struktury bazy danych, takich jak tabele i procedury składowane. Jest jednak ograniczona co można zrobić z kontekstu danych uproszczone. Kontekst pełnych danych, która pozwala, aby wykonywać inne akcje. jest również dostępna to znajduje się w `ServiceTypes` i ma nazwę *DataContext* parametr statyczny, jeśli została podana. Jeśli nie podano go, nazwa typu kontekstu danych zostanie wygenerowany przez SqlMetal.exe oparte na innych danych wejściowych. Dziedziczy kontekstu danych `System.Data.Linq.DataContext` i udostępnia elementów członkowskich klasy podstawowej, takie jak tym odwołania do typów danych ADO.NET `Connection` obiektu, metody, takie jak `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` i `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` można pisać zapytania w programie SQL a także sposób pracy z transakcji jawnie.


#### <a name="to-use-the-full-data-context"></a>Aby używać kontekstu danych

Poniższy kod przedstawia pobierania obiektu kontekstu pełnych danych i użyciem jej do wykonania polecenia bezpośrednio w bazie danych. W takim przypadku dwa polecenia są wykonywane w ramach tej samej transakcji.

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

## <a name="deleting-data"></a>Usuwanie danych
W tym kroku przedstawiono sposób usuwania wierszy w tabeli danych.


#### <a name="to-delete-rows-from-the-database"></a>Aby usunąć wierszy z bazy danych

Teraz, czyszczenie żadnego dodanych wierszy pisząc funkcję, która usuwa wiersze z tabeli określonej instancji `System.Data.Linq.Table` klasy. Następnie napisz zapytanie, aby znaleźć wszystkie wiersze, które chcesz usunąć, a wyniki zapytania do potoku `deleteRows` funkcji. Ten kod korzysta z możliwości zapewnienia aplikacja częściowa argumentów funkcji.

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

## <a name="creating-a-test-database"></a>Tworzenie testowej bazy danych
W tej sekcji przedstawiono sposób konfigurowania bazy danych testu do użycia w tym przewodniku.

Należy pamiętać o tym, w przypadku modyfikowania bazy danych w określony sposób, konieczne będzie zresetować typ dostawcy. Aby zresetować typ dostawcy, odbudować lub wyczyścić projektu, który zawiera typ dostawcy.


#### <a name="to-create-the-test-database"></a>Aby utworzyć testowej bazy danych

1. W **Eksploratora serwera**, otwórz menu skrótów **połączenia danych** węzeł i wybierz polecenie **Dodawanie połączenia**. **Dodawanie połączenia** zostanie wyświetlone okno dialogowe.

2. W **nazwy serwera** polu, określ nazwę wystąpienia programu SQL Server, które mają dostęp administracyjny do lub jeśli nie masz dostępu do serwera, określ (localdb\v11.0). SQL Express LocalDB zapewnia serwer lekkie bazy danych dla projektowania i testowania na tym komputerze. Nowy węzeł jest tworzony w **Eksploratora serwera** w obszarze **połączenia danych**. Aby uzyskać więcej informacji na temat LocalDB, zobacz [wskazówki: Tworzenie lokalnego pliku bazy danych w programie Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).

3. Otwórz menu skrótów do nowego węzła połączenie i wybierz **nowe zapytanie**.

4. Skopiuj poniższy skrypt SQL, wklej go w edytorze zapytań, a następnie wybierz **Execute** znajdującego się na pasku narzędzi lub wybierz klawiszy Ctrl + Shift + E.

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


## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)

[Sqldataconnection — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[Wskazówki: Generowanie typów F # za pomocą pliku DBML](generating-fsharp-types-from-dbml.md)

[Wyrażenia zapytań](../../language-reference/query-expressions.md)

[LINQ do SQL](https://msdn.microsoft.com/library/bb386976)

[SqlMetal.exe &#40; Narzędzie generowania kodu &#41;](https://msdn.microsoft.com/library/bb386987)
