---
title: 'Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284588"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock

Biblioteka TPL przepływu danych zawiera <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> klasy i, <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> dzięki czemu można odbierać i buforować dane z jednego lub kilku źródeł, a następnie rozpowszechniać te dane buforowane jako jedną kolekcję. Ten mechanizm przetwarzania wsadowego jest przydatny podczas zbierania danych z jednego lub kilku źródeł, a następnie przetwarzania wielu elementów danych jako partii. Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych. Ta operacja może być wydajniejsza, jeśli w tym samym czasie wstawiono wiele elementów zamiast jednego z nich naraz. W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy w celu zwiększenia wydajności takich operacji wstawiania bazy danych. Opisano w nim również, jak używać <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasy do przechwytywania zarówno wyników, jak i wyjątków, które występują, gdy program odczytuje dane z bazy danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Wymagania wstępne

1. Przed rozpoczęciem tego instruktażu Przeczytaj sekcję Join Blocks w dokumencie [przepływu danych](dataflow-task-parallel-library.md) .

2. Upewnij się, że masz kopię bazy danych Northwind, Northwind. sdf, która jest dostępna na komputerze. Ten plik zazwyczaj znajduje się w folderze% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples \\ .

    > [!IMPORTANT]
    > W niektórych wersjach systemu Windows nie można nawiązać połączenia z serwerem Northwind. sdf, jeśli program Visual Studio jest uruchomiony w trybie innym niż administrator. Aby połączyć się z Northwind. sdf, uruchom program Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w trybie **Uruchom jako administrator** .

Ten Instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji konsoli](#creating)

- [Definiowanie klasy Employee](#employeeClass)

- [Definiowanie operacji w bazie danych pracowników](#operations)

- [Dodawanie danych pracownika do bazy danych bez używania buforowania](#nonBuffering)

- [Używanie buforowania w celu dodania danych pracownika do bazy danych](#buffering)

- [Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych](#bufferedJoin)

- [Kompletny przykład](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Tworzenie aplikacji konsoli

1. W programie Visual Studio Utwórz projekt **aplikacji konsolowej** Visual C# lub Visual Basic. W tym dokumencie projekt ma nazwę `DataflowBatchDatabase` .

2. W projekcie Dodaj odwołanie do System. Data. SqlServerCe. dll i odwołanie do System. Threading. Tasks. przepływu danych. dll.

3. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera `using` następujące `Imports` instrukcje (w Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Dodaj następujące składowe danych do `Program` klasy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definiowanie klasy Employee

Dodaj do `Program` klasy `Employee` klasy.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

`Employee`Klasa zawiera trzy właściwości, `EmployeeID` , `LastName` , i `FirstName` . Te właściwości odpowiadają `Employee ID` , `Last Name` i `First Name` kolumnom w `Employees` tabeli w bazie danych Northwind. Dla tej demonstracji `Employee` Klasa definiuje także `Random` metodę, która tworzy `Employee` obiekt, który ma losowo wartości właściwości.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definiowanie operacji w bazie danych pracowników

Dodaj do `Program` klasy `InsertEmployees` `GetEmployeeCount` metody,, i `GetEmployeeID` .

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees`Metoda dodaje do bazy danych nowe rekordy pracowników. `GetEmployeeCount`Metoda pobiera liczbę wpisów w `Employees` tabeli. `GetEmployeeID`Metoda pobiera identyfikator pierwszego pracownika o podanej nazwie. Każda z tych metod przyjmuje parametry połączenia do bazy danych Northwind i używa funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikacji z bazą danych.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych pracownika do bazy danych bez używania buforowania

Dodaj do `Program` klasy `AddEmployees` `PostRandomEmployees` metody i.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

`AddEmployees`Metoda dodaje losowo dane pracownika do bazy danych za pomocą przepływu danych. Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który wywołuje metodę, `InsertEmployees` Aby dodać wpis pracownika do bazy danych. `AddEmployees`Metoda następnie wywołuje metodę, `PostRandomEmployees` aby ogłosić wiele `Employee` obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. `AddEmployees`Metoda następnie czeka na zakończenie wszystkich operacji wstawiania.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Używanie buforowania w celu dodania danych pracownika do bazy danych

Dodaj do `Program` klasy `AddEmployeesBatched` metodę.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Ta metoda przypomina `AddEmployees` , z tą różnicą, że używa również <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy do buforowania wielu `Employee` obiektów przed wysłaniem tych obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Klasa propaguje wiele elementów jako kolekcję, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt jest modyfikowany do działania na tablicy `Employee` obiektów. Podobnie jak w `AddEmployees` metodzie, `AddEmployeesBatched` wywołuje `PostRandomEmployees` metodę w celu opublikowania wielu `Employee` obiektów, jednak `AddEmployeesBatched` zapisuje te obiekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiektu. `AddEmployeesBatched`Metoda również czeka na zakończenie wszystkich operacji wstawiania.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych

Dodaj do `Program` klasy `GetRandomEmployees` metodę.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Ta metoda drukuje informacje o losowych pracownikach w konsoli programu. Tworzy kilka losowych `Employee` obiektów i wywołuje `GetEmployeeID` metodę, aby pobrać unikatowy identyfikator dla każdego obiektu. Ponieważ `GetEmployeeID` Metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika o podanym imieniu i nazwisku, `GetRandomEmployees` Metoda używa <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasy do przechowywania `Employee` obiektów dla udanych wywołań do `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań, które kończą się niepowodzeniem. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Obiekt w tym przykładzie działa w odniesieniu do <xref:System.Tuple%602> obiektu, który zawiera listę `Employee` obiektów i listę <xref:System.Exception> obiektów. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>Obiekt propaguje te dane, gdy suma odebranych `Employee` i <xref:System.Exception> liczników obiektów jest równa rozmiarowi partii.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletny przykład

Poniższy przykład pokazuje kompletny kod. `Main`Metoda porównuje czas wymagany do wykonania wsadowych wstawień bazy danych w porównaniu do czasu wykonywania operacji wstawiania baz danych bez partii. Przedstawiono w nim także użycie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych, a także zgłaszania błędów.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
