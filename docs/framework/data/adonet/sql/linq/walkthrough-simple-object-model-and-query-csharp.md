---
title: 'Przewodnik: Prosty model obiektu i zapytanie (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: a9b3b57e37331cd13f2cd30b8a7663f2fb39d8c1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792131"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Przewodnik: Prosty model obiektu i zapytanie (C#)

Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz z minimalnymi złożonością. Utworzysz klasę jednostki, która będzie modelować tabelę Customers w przykładowej bazie danych Northwind. Następnie utworzysz proste zapytanie, aby wyświetlić listę klientów, którzy znajdują się w Londynie.

Ten Instruktaż jest zorientowany na kod według projektu, aby pomóc w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazywania koncepcji. Zwykle mówiąc, użyj Object Relational Designer do utworzenia modelu obiektów.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.

## <a name="prerequisites"></a>Wymagania wstępne

- W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest5"). Utwórz ten folder przed rozpoczęciem przewodnika.

- Ten Instruktaż wymaga przykładowej bazy danych Northwind. Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft. Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md). Po pobraniu bazy danych Skopiuj plik do folderu c:\linqtest5.

## <a name="overview"></a>Omówienie

Ten przewodnik składa się z sześciu głównych zadań:

- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.

- Mapowanie klasy do tabeli bazy danych.

- Wyznaczanie właściwości klasy w celu reprezentowania kolumn bazy danych.

- Określanie połączenia z bazą danych Northwind.

- Tworzenie prostego zapytania do uruchamiania w bazie danych.

- Wykonywanie zapytania i obserwowanie wyników.

## <a name="creating-a-linq-to-sql-solution"></a>Tworzenie rozwiązania LINQ to SQL

W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.

### <a name="to-create-a-linq-to-sql-solution"></a>Aby utworzyć rozwiązanie LINQ to SQL

1. W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję **Wizualizacja C#** .

3. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.

4. W polu **Nazwa** wpisz **LinqConsoleApp**.

5. W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.

6. Kliknij przycisk **OK**.

## <a name="adding-linq-references-and-directives"></a>Dodawanie odwołań i dyrektyw LINQ

W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie. Jeśli obiekt system. Data. LINQ nie jest wymieniony jako odwołanie w projekcie (rozwiń węzeł **odwołania** w **Eksplorator rozwiązań**), Dodaj go, jak wyjaśniono w poniższych krokach.

### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.

     Zestaw zostanie dodany do projektu.

3. Dodaj następujące dyrektywy w górnej części **program.cs**:

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Mapowanie klasy do tabeli bazy danych

W tym kroku utworzysz klasę i zamapujesz ją do tabeli bazy danych. Takie klasy są określane jako *Klasa jednostki*. Należy pamiętać, że mapowanie jest realizowane przez jedynie dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Aby utworzyć klasę jednostki i zamapować ją na tabelę bazy danych

- Wpisz lub wklej następujący kod do program.cs bezpośrednio powyżej `Program` deklaracji klasy:

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Wyznaczanie właściwości klasy do reprezentowania kolumn bazy danych

W tym kroku wykonujesz kilka zadań.

- Użyj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `City` `CustomerID` i właściwości klasy Entity jako reprezentujące kolumny w tabeli bazy danych.

- Należy wyznaczyć `CustomerID` Właściwość reprezentującą kolumnę klucza podstawowego w bazie danych.

- `_CustomerID` Wyznaczysz `_City` pola i dla magazynu prywatnego. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]program może następnie przechowywać i pobierać wartości bezpośrednio, zamiast korzystać z publicznych metod dostępu, które mogą zawierać logikę biznesową.

### <a name="to-represent-characteristics-of-two-database-columns"></a>Do reprezentowania cech dwóch kolumn bazy danych

- Wpisz lub wklej następujący kod do program.cs wewnątrz nawiasów klamrowych `Customer` klasy.

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Określanie połączenia z bazą danych Northwind

W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu, aby nawiązać połączenie między strukturami danych opartymi na kodzie i samą bazą danych. <xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pośrednictwem którego można pobrać obiekty z bazy danych i przesłać zmiany.

Deklarujemy również, `Table<Customer>` aby pełnić rolę logicznej, wpisanej tabeli dla zapytań względem tabeli Customers w bazie danych. Te zapytania zostaną utworzone i wykonane w dalszych krokach.

### <a name="to-specify-the-database-connection"></a>Aby określić połączenie z bazą danych

- Wpisz lub wklej następujący kod w `Main` metodzie.

     Należy pamiętać, `northwnd.mdf` że plik jest założono, że znajduje się w folderze linqtest5. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a>Tworzenie prostego zapytania

W tym kroku utworzysz zapytanie, aby sprawdzić, którzy klienci w tabeli Klienci bazy danych znajdują się w Londynie. Kod zapytania w tym kroku tylko opisuje zapytanie. Nie wykonuje go. Takie podejście jest znane jako *odroczone wykonanie*. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Utworzysz również dane wyjściowe dziennika w celu wyświetlenia poleceń SQL, które [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generują. Ta funkcja rejestrowania (która korzysta <xref:System.Data.Linq.DataContext.Log%2A>z programu) jest przydatna podczas debugowania, a przy określaniu, że polecenia wysyłane do bazy danych dokładnie reprezentują zapytanie.

### <a name="to-create-a-simple-query"></a>Aby utworzyć proste zapytanie

- Wpisz lub wklej następujący kod do `Main` metody `Table<Customer>` po deklaracji.

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a>Wykonywanie zapytania

W tym kroku rzeczywiście wykonujesz zapytanie. Wyrażenia zapytania utworzone w poprzednich krokach nie są oceniane do momentu, gdy będą potrzebne wyniki. Po rozpoczęciu `foreach` iteracji polecenie SQL jest wykonywane względem bazy danych, a obiekty są w materiałach.

### <a name="to-execute-the-query"></a>Aby wykonać zapytanie

1. Wpisz lub wklej następujący kod na końcu `Main` metody (po opisie zapytania).

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. Naciśnij klawisz F5, aby debugować aplikację.

    > [!NOTE]
    > Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów w temacie [uczenie się według przewodników](learning-by-walkthroughs.md).

     Wyniki zapytania w oknie konsoli powinny wyglądać następująco:

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć aplikację.

## <a name="next-steps"></a>Następne kroki

[Przewodnik: Wykonywanie zapytań w relacjachC#(](walkthrough-querying-across-relationships-csharp.md) ) jest kontynuowane, gdy ten przewodnik zakończy się. Wskazówki dotyczące zapytania między relacjami pokazują [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , jak można wykonywać zapytania między tabelami, podobnie jak *sprzężenia* w relacyjnej bazie danych.

Jeśli chcesz wykonać zapytanie w przewodniku dotyczącym relacji, pamiętaj o zapisaniu rozwiązania dla przewodnika, który właśnie został ukończony, co jest wymaganiem wstępnym.

## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](learning-by-walkthroughs.md)
