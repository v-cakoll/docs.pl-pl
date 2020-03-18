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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091358"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock

Biblioteka przepływu danych TPL <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> zapewnia i klas, dzięki czemu można odbierać i buforować dane z jednego lub więcej źródeł, a następnie propagować, że buforowane dane jako jedną kolekcję. Ten mechanizm przetwarzania wsadowego jest przydatne podczas zbierania danych z jednego lub więcej źródeł, a następnie przetwarzać wiele elementów danych jako partii. Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych. Ta operacja może być bardziej efektywne, jeśli wiele elementów są wstawiane w tym samym czasie, a nie jeden na raz sekwencyjnie. W tym dokumencie opisano sposób używania <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy w celu zwiększenia wydajności takich operacji wstawiania bazy danych. Opisano również, jak <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> używać klasy do przechwytywania zarówno wyniki i wszelkie wyjątki, które występują, gdy program odczytuje z bazy danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Wymagania wstępne

1. Przed rozpoczęciem tego instruktażenia przeczytaj sekcję Dołącz bloki w dokumencie [Przepływ danych.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

2. Upewnij się, że masz kopię bazy danych Northwind, Northwind.sdf, dostępne na komputerze. Ten plik zazwyczaj znajduje się w folderze %Program Files%\Microsoft SQL Server\\Compact Edition\v3.5\Samples .

    > [!IMPORTANT]
    > W niektórych wersjach systemu Windows nie można połączyć się z northwind.sdf, jeśli program Visual Studio jest uruchomiony w trybie nieadministratora. Aby połączyć się z northwind.sdf, uruchom program Visual Studio lub wiersz polecenia dewelopera dla programu Visual Studio w trybie **Uruchom jako administrator.**

Ten instruktaż zawiera następujące sekcje:

- [Tworzenie aplikacji konsoli](#creating)

- [Definiowanie klasy pracownika](#employeeClass)

- [Definiowanie operacji bazy danych pracowników](#operations)

- [Dodawanie danych pracowników do bazy danych bez korzystania z buforowania](#nonBuffering)

- [Używanie buforowania do dodawania danych pracowników do bazy danych](#buffering)

- [Używanie sprzężenia buforowego do odczytywania danych pracownika z bazy danych](#bufferedJoin)

- [Kompletny przykład](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Tworzenie aplikacji konsoli

1. W programie Visual Studio utwórz projekt aplikacji visual C# lub Visual Basic **Console Application.** W tym dokumencie projekt `DataflowBatchDatabase`nosi nazwę .

2. W projekcie dodaj odwołanie do pliku System.Data.SqlServerCe.dll i odwołanie do pliku System.Threading.Tasks.Dataflow.dll.

3. Upewnij się, że Form1.cs (Form1.vb `using` dla`Imports` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Dodaj następujące elementy członkowskie `Program` danych do klasy.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Definiowanie klasy pracownika

Dodaj do `Program` klasy `Employee` klasy.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

Klasa `Employee` zawiera trzy `EmployeeID`właściwości, `LastName`, `FirstName`, i . Właściwości te odpowiadają `Employee ID`, `Last Name`, `First Name` i `Employees` kolumny w tabeli w bazie danych Northwind. Dla tej demonstracji `Employee` klasa definiuje `Random` również metodę, `Employee` która tworzy obiekt, który ma losowe wartości dla jego właściwości.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Definiowanie operacji bazy danych pracowników

Dodaj do `Program` klasy `InsertEmployees` `GetEmployeeCount`, `GetEmployeeID` , i metody.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

Metoda `InsertEmployees` dodaje nowe rekordy pracowników do bazy danych. Metoda `GetEmployeeCount` pobiera liczbę wpisów w `Employees` tabeli. Metoda `GetEmployeeID` pobiera identyfikator pierwszego pracownika, który ma podaną nazwę. Każda z tych metod pobiera parametry połączenia z bazą danych `System.Data.SqlServerCe` Northwind i używa funkcji w przestrzeni nazw do komunikowania się z bazą danych.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych pracowników do bazy danych bez użycia buforowania

Dodaj do `Program` klasy `AddEmployees` `PostRandomEmployees` i metody.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

Metoda `AddEmployees` dodaje losowe dane pracownika do bazy danych przy użyciu przepływu danych. Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który `InsertEmployees` wywołuje metodę, aby dodać wpis pracownika do bazy danych. Metoda `AddEmployees` następnie wywołuje `PostRandomEmployees` metodę, `Employee` aby zaksięgować wiele obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Metoda `AddEmployees` następnie czeka na zakończenie wszystkich operacji wstawiania.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Używanie buforowania do dodawania danych pracowników do bazy danych

Dodaj do `Program` klasy `AddEmployeesBatched` metodę.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Ta metoda `AddEmployees`przypomina , z tą <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> różnicą, `Employee` że używa również klasy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do buforowania wielu obiektów przed wysłaniem tych obiektów do obiektu. Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasa propaguje wiele elementów jako <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> kolekcji, obiekt jest modyfikowany do działania na tablicy `Employee` obiektów. Podobnie jak `AddEmployees` w `AddEmployeesBatched` metodzie wywołuje `PostRandomEmployees` `Employee` metodę do zaksięgowania wielu obiektów; jednak `AddEmployeesBatched` księguje te <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiekty do obiektu. Metoda `AddEmployeesBatched` czeka również na zakończenie wszystkich operacji wstawiania.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Używanie sprzężenia buforowego do odczytywania danych pracownika z bazy danych

Dodaj do `Program` klasy `GetRandomEmployees` metodę.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Ta metoda drukuje informacje o losowych pracowników do konsoli. Tworzy kilka `Employee` losowych obiektów `GetEmployeeID` i wywołuje metodę, aby pobrać unikatowy identyfikator dla każdego obiektu. Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika `GetRandomEmployees` z podanych imion i nazwisk, metoda <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> używa klasy do `Employee` przechowywania obiektów dla pomyślnych wywołań `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań, które kończą się niepowodzeniem. Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> w tym przykładzie <xref:System.Tuple%602> działa na obiekt, `Employee` który zawiera <xref:System.Exception> listę obiektów i listę obiektów. Obiekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propaguje te dane, gdy `Employee` suma <xref:System.Exception> odebranych i liczba obiektów jest równa rozmiarowi partii.

<a name="complete"></a>

## <a name="the-complete-example"></a>Kompletny przykład

W poniższym przykładzie przedstawiono kompletny kod. Metoda `Main` porównuje czas, który jest wymagany do wykonywania wsadowych wstawiania bazy danych w porównaniu do czasu do wykonywania wstawiania bazy danych niewsmażonych. Pokazuje również użycie sprzężenia buforowego do odczytu danych pracownika z bazy danych, a także do zgłaszania błędów.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
