---
title: 'Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: 4b2b6a6124bf8cc0fb3b379607135283678e3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091358"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock

Biblioteka TPL przepływu danych zawiera klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>, dzięki czemu można odbierać i buforować dane z jednego lub kilku źródeł, a następnie rozpowszechniać te dane w postaci danych w jednej kolekcji. Ten mechanizm przetwarzania wsadowego jest przydatny podczas zbierania danych z jednego lub kilku źródeł, a następnie przetwarzania wielu elementów danych jako partii. Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych. Ta operacja może być wydajniejsza, jeśli w tym samym czasie wstawiono wiele elementów zamiast jednego z nich naraz. W tym dokumencie opisano sposób użycia klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> w celu zwiększenia wydajności takich operacji wstawiania baz danych. Opisano w nim również, jak używać klasy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>, aby przechwycić zarówno wyniki, jak i wyjątki, które występują, gdy program odczytuje z bazy danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Wymagania wstępne

1. Przed rozpoczęciem tego instruktażu Przeczytaj sekcję Join Blocks w dokumencie [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) .

2. Upewnij się, że masz kopię bazy danych Northwind, Northwind. sdf, która jest dostępna na komputerze. Ten plik zazwyczaj znajduje się w folderze% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.

    > [!IMPORTANT]
    > W niektórych wersjach systemu Windows nie można nawiązać połączenia z serwerem Northwind. sdf, jeśli program Visual Studio jest uruchomiony w trybie innym niż administrator. Aby połączyć się z Northwind. sdf, uruchom program Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w trybie **Uruchom jako administrator** .

Ten Instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji konsolowej](#creating)

- [Definiowanie klasy Employee](#employeeClass)

- [Definiowanie operacji w bazie danych pracowników](#operations)

- [Dodawanie danych pracownika do bazy danych bez używania buforowania](#nonBuffering)

- [Używanie buforowania w celu dodania danych pracownika do bazy danych](#buffering)

- [Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych](#bufferedJoin)

- [Kompletny przykład](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Tworzenie aplikacji konsoli

1. W programie Visual Studio Utwórz projekt C# **aplikacji konsolowej** wizualizacji lub Visual Basic. W tym dokumencie projekt ma nazwę `DataflowBatchDatabase`.

2. W projekcie Dodaj odwołanie do System. Data. SqlServerCe. dll i odwołanie do System. Threading. Tasks. przepływu danych. dll.

3. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące instrukcje `using` (`Imports` w Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Dodaj następujące elementy członkowskie danych do klasy `Program`.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definiowanie klasy Employee

Dodaj do klasy `Program` klasy `Employee`.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Klasa `Employee` zawiera trzy właściwości, `EmployeeID`, `LastName`i `FirstName`. Te właściwości odpowiadają kolumnom `Employee ID`, `Last Name`i `First Name` w tabeli `Employees` w bazie danych Northwind. Dla tej demonstracji Klasa `Employee` definiuje również metodę `Random`, która tworzy obiekt `Employee`, który ma losowo wartości właściwości.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definiowanie operacji w bazie danych pracowników

Dodaj do klasy `Program` metod `InsertEmployees`, `GetEmployeeCount`i `GetEmployeeID`.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

Metoda `InsertEmployees` dodaje do bazy danych nowe rekordy pracowników. Metoda `GetEmployeeCount` Pobiera liczbę wpisów w tabeli `Employees`. Metoda `GetEmployeeID` Pobiera identyfikator pierwszego pracownika o podanej nazwie. Każda z tych metod przyjmuje parametry połączenia do bazy danych Northwind i używa funkcji w przestrzeni nazw `System.Data.SqlServerCe`, aby komunikować się z bazą danych.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych pracownika do bazy danych bez używania buforowania

Dodaj do klasy `Program` metod `AddEmployees` i `PostRandomEmployees`.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Metoda `AddEmployees` dodaje losowo dane pracownika do bazy danych za pomocą przepływu danych. Tworzy obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, który wywołuje metodę `InsertEmployees`, aby dodać wpis pracownika do bazy danych. Metoda `AddEmployees` następnie wywołuje metodę `PostRandomEmployees`, aby ogłosić wiele obiektów `Employee` do obiektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Metoda `AddEmployees` następnie czeka na zakończenie wszystkich operacji wstawiania.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Używanie buforowania w celu dodania danych pracownika do bazy danych

Dodaj do klasy `Program` metody `AddEmployeesBatched`.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Ta metoda przypomina `AddEmployees`, z tą różnicą, że używa również klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> do buforowania wielu obiektów `Employee` przed wysłaniem tych obiektów do obiektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Ponieważ Klasa <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propaguje wiele elementów jako kolekcja, obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> jest modyfikowany do działania na tablicy obiektów `Employee`. Podobnie jak w metodzie `AddEmployees`, `AddEmployeesBatched` wywołuje metodę `PostRandomEmployees`, aby ogłosić wiele obiektów `Employee`; jednak `AddEmployeesBatched` ogłasza te obiekty w obiekcie <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>. Metoda `AddEmployeesBatched` czeka również na zakończenie wszystkich operacji wstawiania.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych

Dodaj do klasy `Program` metody `GetRandomEmployees`.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Ta metoda drukuje informacje o losowych pracownikach w konsoli programu. Tworzy kilka losowo `Employee` obiektów i wywołuje metodę `GetEmployeeID`, aby pobrać unikatowy identyfikator dla każdego obiektu. Ponieważ metoda `GetEmployeeID` zgłasza wyjątek, jeśli nie ma pasującego pracownika z podanym imieniem i nazwiskiem, Metoda `GetRandomEmployees` używa klasy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> do przechowywania obiektów `Employee` dla udanych wywołań do `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań zakończonych niepowodzeniem . Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> w tym przykładzie działa na obiekcie <xref:System.Tuple%602>, który zawiera listę obiektów `Employee` i listę obiektów <xref:System.Exception>. Obiekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propaguje te dane, gdy suma odebranych `Employee` i <xref:System.Exception> liczby obiektów jest równa rozmiarowi partii.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletny przykład

Poniższy przykład pokazuje kompletny kod. Metoda `Main` porównuje czas wymagany do wykonania wsadowych wstawień bazy danych zamiast czasu na wykonanie wstawiania baz danych bez partii. Przedstawiono w nim także użycie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych, a także zgłaszania błędów.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
