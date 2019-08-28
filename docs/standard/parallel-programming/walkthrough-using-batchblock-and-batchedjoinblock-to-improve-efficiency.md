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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d704702e74b5f7d4a315bd14a467296245f90257
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046500"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock

Biblioteka TPL przepływu danych zawiera <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> klasy i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , dzięki czemu można odbierać i buforować dane z jednego lub kilku źródeł, a następnie rozpowszechniać te dane buforowane jako jedną kolekcję. Ten mechanizm przetwarzania wsadowego jest przydatny podczas zbierania danych z jednego lub kilku źródeł, a następnie przetwarzania wielu elementów danych jako partii. Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych. Ta operacja może być wydajniejsza, jeśli w tym samym czasie wstawiono wiele elementów zamiast jednego z nich naraz. W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy w celu zwiększenia wydajności takich operacji wstawiania bazy danych. Opisano w nim również, jak używać <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasy do przechwytywania zarówno wyników, jak i wyjątków, które występują, gdy program odczytuje dane z bazy danych.

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

<a name="consoleApp"></a>
1. W programie Visual Studio Utwórz projekt C# **aplikacji konsolowej** wizualizacji lub Visual Basic. W tym dokumencie projekt ma nazwę `DataflowBatchDatabase`.

2. W projekcie Dodaj odwołanie do System. Data. SqlServerCe. dll i odwołanie do System. Threading. Tasks. przepływu danych. dll.

3. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera `using` następujące`Imports` instrukcje (w Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Dodaj następujące składowe danych do `Program` klasy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definiowanie klasy Employee

Dodaj do `Program` `Employee` klasy klasy.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Klasa zawiera trzy właściwości, `EmployeeID`, `LastName`, i `FirstName`. `Employee` Te właściwości odpowiadają `Employee ID`, `Last Name`i `First Name` kolumnom w `Employees` tabeli w bazie danych Northwind. Dla tej demonstracji `Employee` Klasa `Random` definiuje także `Employee` metodę, która tworzy obiekt, który ma losowo wartości właściwości.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definiowanie operacji w bazie danych pracowników

Dodaj do `Program` `GetEmployeeCount`klasy metody `GetEmployeeID`,,i. `InsertEmployees`

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

`InsertEmployees` Metoda dodaje do bazy danych nowe rekordy pracowników. Metoda pobiera liczbę wpisów `Employees` w tabeli. `GetEmployeeCount` `GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika o podanej nazwie. Każda z tych metod przyjmuje parametry połączenia do bazy danych Northwind i używa funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikacji z bazą danych.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych pracownika do bazy danych bez używania buforowania

Dodaj do `Program` `AddEmployees` klasy metody i. `PostRandomEmployees`

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

`AddEmployees` Metoda dodaje losowo dane pracownika do bazy danych za pomocą przepływu danych. Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który `InsertEmployees` wywołuje metodę, aby dodać wpis pracownika do bazy danych. Metoda następnie wywołuje metodę, `PostRandomEmployees` `Employee` Aby<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> ogłosić wiele obiektów do obiektu. `AddEmployees` `AddEmployees` Metoda następnie czeka na zakończenie wszystkich operacji wstawiania.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Używanie buforowania w celu dodania danych pracownika do bazy danych

Dodaj do `Program` `AddEmployeesBatched` klasy metodę.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Ta metoda przypomina `AddEmployees`, z tą różnicą, że <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> używa również klasy do buforowania `Employee` wielu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów przed wysłaniem tych obiektów do obiektu. Ponieważ Klasa propaguje wiele elementów jako kolekcję <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> , obiekt jest modyfikowany do `Employee` działania na tablicy obiektów. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Podobnie jak w `AddEmployees` metodzie `AddEmployeesBatched` , wywołuje `PostRandomEmployees` `Employee` metodęw<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> celu opublikowania wielu obiektów, jednak zapisujeteobiektydoobiektu.`AddEmployeesBatched` `AddEmployeesBatched` Metoda również czeka na zakończenie wszystkich operacji wstawiania.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych

Dodaj do `Program` `GetRandomEmployees` klasy metodę.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Ta metoda drukuje informacje o losowych pracownikach w konsoli programu. Tworzy kilka losowych `Employee` obiektów i `GetEmployeeID` wywołuje metodę, aby pobrać unikatowy identyfikator dla każdego obiektu. `GetEmployeeID` `Employee` <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `GetRandomEmployees` Ponieważ metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika o podanym imieniu i nazwisku, metoda używa klasy do przechowywania obiektów dla udanych wywołań do i `GetEmployeeID` <xref:System.Exception?displayProperty=nameWithType> obiekty dla wywołań, które kończą się niepowodzeniem. Obiekt w tym przykładzie działa <xref:System.Tuple%602> w odniesieniu do obiektu `Employee` , który zawiera listę obiektów i listę <xref:System.Exception> obiektów. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt propaguje te dane, gdy suma odebranych `Employee` i <xref:System.Exception> liczników obiektów jest równa rozmiarowi partii. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletny przykład

Poniższy przykład pokazuje kompletny kod. `Main` Metoda porównuje czas wymagany do wykonania wsadowych wstawień bazy danych w porównaniu do czasu wykonywania operacji wstawiania baz danych bez partii. Przedstawiono w nim także użycie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych, a także zgłaszania błędów.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
