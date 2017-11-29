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
ms.openlocfilehash: 50e0a2bb6378c82b5c6425589da8a982b5fc496a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>Wskazówki: generowanie typów F# za pomocą pliku DBML

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Tego przewodnika w celu F # 3.0 zawiera opis sposobu tworzenia typów danych z bazy danych, jeśli masz zakodowane w pliku .dbml informacji o schemacie. LINQ do SQL korzysta z tego formatu pliku do reprezentowania schematu bazy danych. LINQ do SQL pliku schematu w programie Visual Studio można wygenerować za pomocą Projektanta obiektów relacyjnych (obiektów relacyjnych). Aby uzyskać więcej informacji, zobacz [Omówienie projektanta obiektów relacyjnych](https://msdn.microsoft.com/library/bb384511.aspx) i [generowanie kodu w składniku LINQ to SQL](https://msdn.microsoft.com/library/bb386976).

Typ dostawcy bazy danych Markup Language (DBML) służy do pisania kodu, który używa typy oparte na schemat bazy danych bez konieczności Określ ciąg połączenia statycznych w czasie kompilacji. Może to być przydatne, jeśli konieczne jest zezwolenie na możliwość, że końcowego aplikacja będzie korzystać z innej bazy danych, innych poświadczeń lub ciąg połączenia innego niż jeden, którego używasz do opracowywania aplikacji. Jeśli masz połączenie z bazą danych bezpośrednio używanej w czasie kompilacji i są to te same bazy danych i poświadczenia, które będą używane po pewnym czasie zbudowany aplikacji, można również użyć sqldataconnection — dostawca typów. Aby uzyskać więcej informacji, zobacz [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md).

W tym przewodniku przedstawiono następujące zadania. One należy wykonać w następującej kolejności wskazówki powiodła się:


- Tworzenie pliku .dbml
<br />

- Tworzenie i konfigurowanie projektu programu F #
<br />

- Typ dostawcy konfiguracji i generowania typów
<br />

- Wykonywanie zapytania w bazie danych
<br />


## <a name="prerequisites"></a>Wymagania wstępne

## <a name="creating-a-dbml-file"></a>Tworzenie pliku .dbml
Jeśli nie masz bazę danych do testu na, utwórz ją zgodnie z instrukcjami w dolnej części [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md). Wykonaj te instrukcje, utworzysz bazę danych o nazwie mojabazadanych, który zawiera kilka prostych tabele i procedury przechowywane na serwerze SQL.

Jeśli masz już plik .dbml, możesz przejść do sekcji **tworzenie i ustaw się F # projekt**. W przeciwnym razie możesz utworzyć plik .dbml na podstawie istniejącej bazy danych SQL i przy użyciu wiersza polecenia narzędzia SqlMetal.exe.


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>Aby utworzyć plik .dbml przy użyciu SqlMetal.exe

1. Otwórz **wiersza polecenia dewelopera**.
<br />

2. Upewnij się, że masz dostęp do SqlMetal.exe, wprowadzając `SqlMetal.exe /?` w wierszu polecenia. SqlMetal.exe jest instalowane w obszarze **SDKs Microsoft** folderu w **Program Files** lub **Program Files (x86)**.
<br />

3. Uruchom SqlMetal.exe z poniższych opcji wiersza polecenia. Zastąp odpowiednią ścieżkę zamiast `c:\destpath` do tworzenia pliku .dbml i Wstaw odpowiednie wartości dla serwera bazy danych, wystąpienia nazwy i nazwy bazy danych.
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
Jeśli SqlMetal.exe ma problemy podczas tworzenia pliku z powodu problemów z uprawnień, zmień bieżący katalog w folderze, który ma dostęp do zapisu.


4. Możesz także przeglądać inne dostępne opcje wiersza polecenia. Na przykład są opcje, których można używać widoków i funkcji SQL uwzględnionych w wygenerowane typy. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe &#40; Narzędzie generowania kodu &#41; ](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>Tworzenie i konfigurowanie projektu programu F #
W tym kroku utworzenie projektu i dodaj odpowiednie odwołania do używania dostawcy typów DBML.


#### <a name="to-create-and-set-up-an-f-project"></a>Aby utworzyć i skonfigurować projekt języka F#

1. Dodaj nowy projekt aplikacji konsoli F # do rozwiązania.
<br />

2. W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.
<br />

3. W **zestawy** obszarze, wybierz **Framework** węzeł, a następnie na liście dostępnych zestawów, wybierz **system.dane** i **System.Data.Linq**  zestawów.
<br />

4. W **zestawy** obszarze, wybierz **rozszerzenia**, a następnie na liście dostępnych zestawów, wybierz **FSharp.Data.TypeProviders**.
<br />

5. Wybierz **OK** przycisk, aby dodać odwołania do tych zestawów do projektu.
<br />

6. (Opcjonalnie). Skopiuj plik .dbml, który został utworzony w poprzednim kroku, a następnie wklej go w folderze głównym projektu. Ten folder zawiera plik projektu (.fsproj) i plików kodu. Na pasku menu wybierz **projektu**, **Dodaj istniejący element**, a następnie wskaż plik .dbml, aby dodać go do projektu. Po wykonaniu tych kroków można pominąć parametr statyczny ResolutionFolder w następnym kroku.
<br />

## <a name="configuring-the-type-provider"></a>Konfigurowanie dostawcy typów
W tej sekcji Tworzenie dostawcy typów i generowania typów ze schematu opisaną w pliku .dbml.


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>Aby skonfigurować typ dostawcy i wygenerować typy

- Dodaj kod, którego kliknięcie spowoduje otwarcie **TypeProviders** przestrzeni nazw i tworzy wystąpienie dostawcy typów dla pliku .dbml, który ma być używany. Jeśli plik .dbml zostało dodane do projektu, można pominąć parametr statyczny ResolutionFolder.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

Typ DataContext zapewnia dostęp do wszystkich typów wygenerowany i dziedziczy `System.Data.Linq.DataContext`. Dbmlfile — dostawca typów ma różnych parametrów statycznych, które można ustawić. Na przykład można użyć inną nazwę dla typu DataContext, określając `DataContext=MyDataContext`. W takim przypadku kodu podobnego do następującego:
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>Wykonywanie zapytania w bazie danych
W tej sekcji umożliwiają wyrażenia zapytania F # w bazie danych.


#### <a name="to-query-the-data"></a>Aby wykonać zapytanie dotyczące danych

- Dodaj kod, aby w bazie danych.
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>Następne kroki
Możesz przejść do użycia inne wyrażenia zapytania lub pobrać z kontekstu danych połączenia z bazą danych, a wykonywanie zwykłych operacji danych ADO.NET. Dodatkowe czynności, zobacz sekcje po "Dane zapytania" w [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md).


## <a name="see-also"></a>Zobacz też
[Dbmlfile — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[Dostawcy typów](index.md)

[Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md)

[SqlMetal.exe &#40; Narzędzie generowania kodu &#41;](https://msdn.microsoft.com/library/bb386987)

[Wyrażenia zapytań](../../language-reference/query-expressions.md)
