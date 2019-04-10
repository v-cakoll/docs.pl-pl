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
ms.openlocfilehash: 79bbf33ff1b1e843836aa1b93188970b6a1c8ede
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302984"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock
Biblioteka przepływu danych TPL zapewnia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> klasy tak, że może odbierać i buforować dane z jednego lub kilku źródeł i następnie rozpropagować te buforowane dane jako jedną kolekcję. Ten mechanizm łączenia we wsady jest przydatny, podczas zbierania danych z co najmniej jednego źródła, a następnie przetwarzania wielu elementów danych jako zadania wsadowego. Na przykład rozważmy aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych. Ta operacja może być bardziej skuteczna, jeśli wiele elementów jest wstawianych jednocześnie zamiast pojedynczo po kolei. W tym dokumencie opisano, jak używać <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operacje wstawiania klasy, aby zwiększyć wydajność takiej bazy danych. Opisano również sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasa do przechwytywania zarówno wyników jak i wyjątków, które występują, gdy program czyta z bazy danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Wymagania wstępne  
  
1. Przeczytaj sekcję łączenia bloków w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumencie przed rozpoczęciem tego instruktażu.  
  
2. Upewnij się, że masz kopię bazy danych Northwind, Northwind.sdf, dostępną na komputerze. Ten plik znajduje się w folderze % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.  
  
    > [!IMPORTANT]
    >  W niektórych wersjach systemu Windows możesz nie może połączyć się z Northwind.sdf, jeśli program Visual Studio jest uruchomiony w trybie administratora. Aby połączyć się z Northwind.sdf, uruchom Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w **Uruchom jako administrator** trybu.  
  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Tworzenie aplikacji konsoli](#creating)  
  
-   [Definiowanie klasy pracownika](#employeeClass)  
  
-   [Definiowanie operacji w bazie danych pracownika](#operations)  
  
-   [Dodawanie danych pracownika do bazy danych bez używania buforowania.](#nonBuffering)  
  
-   [Używanie buforowania, aby dodać dane pracownika do bazy danych](#buffering)  
  
-   [Używanie buforowanego połączenia do odczytu danych pracowników z bazy danych](#bufferedJoin)  
  
-   [Kompletny przykład](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Tworzenie aplikacji konsoli  
  
<a name="consoleApp"></a>   
1. W programie Visual Studio Utwórz Visual C# lub Visual Basic **aplikację Konsolową** projektu. W tym dokumencie projekt nazwano `DataflowBatchDatabase`.  
  
2. W projekcie Dodaj odwołanie do System.Data.SqlServerCe.dll oraz odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
3. Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` (`Imports` w języku Visual Basic) instrukcji.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4. Dodaj następujące elementy członkowskie danych do `Program` klasy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Definiowanie klasy pracownika  
 Dodaj do `Program` klasy `Employee` klasy.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Klasa zawiera trzy właściwości `EmployeeID`, `LastName`, i `FirstName`. Te właściwości odpowiadają `Employee ID`, `Last Name`, i `First Name` kolumn w `Employees` tabeli w bazie danych Northwind. W tej prezentacji `Employee` klasa definiuje również `Random` metody, która tworzy `Employee` obiekt, który ma losowe wartości dla jego właściwości.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Definiowanie operacji w bazie danych pracownika  
 Dodaj do `Program` klasy `InsertEmployees`, `GetEmployeeCount`, i `GetEmployeeID` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Metoda dodaje nowe rekordy pracowników do bazy danych. `GetEmployeeCount` Metoda pobiera liczbę wpisów w `Employees` tabeli. `GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika o podanej nazwie. Każda z tych metod pobiera parametry połączenia z bazą danych Northwind i używa funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikowania się z bazą danych.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych pracownika do bazy danych bez używania buforowania.  
 Dodaj do `Program` klasy `AddEmployees` i `PostRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Metoda dodaje dane losowego pracownika do bazy danych za pomocą przepływu danych. Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, który wywołuje `InsertEmployees` metodę, aby dodać wpis pracownika do bazy danych. `AddEmployees` Następnie wywołuje metodę `PostRandomEmployees` metodę przesyłania wielu `Employee` obiekty do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. `AddEmployees` Metoda następnie oczekuje na zakończenie wszystkich operacje wstawiania.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Używanie buforowania, aby dodać dane pracownika do bazy danych  
 Dodaj do `Program` klasy `AddEmployeesBatched` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Ta metoda przypomina `AddEmployees`, z tą różnicą, że użyto także <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy do zbuforowania wielu `Employee` obiektów przed wysłaniem tych obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy propaguje wiele elementów w kolekcji <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt zostanie zmodyfikowany zajmującym się tablica `Employee` obiektów. Podobnie jak w `AddEmployees` metody `AddEmployeesBatched` wywołania `PostRandomEmployees` metodę przesyłania wielu `Employee` obiekty; jednak `AddEmployeesBatched` posyła te obiekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiektu. `AddEmployeesBatched` Metoda także oczekuje na zakończenie wszystkich operacje wstawiania.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Używanie buforowanego połączenia do odczytu danych pracowników z bazy danych  
 Dodaj do `Program` klasy `GetRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Ta metoda drukuje informacje dotyczące losowych pracowników do konsoli. Tworzy kilka losowych `Employee` obiektów i wywołuje `GetEmployeeID` metodę, aby pobrać Unikatowy identyfikator dla każdego obiektu. Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika o danym imiona i nazwiska, `GetRandomEmployees` metoda używa <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasę do przechowywania `Employee` obiektów dla zakończonych powodzeniem wywołań do `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiekty do wywołania, które się nie powieść. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt w tym przykładzie działa na <xref:System.Tuple%602> obiekt, który zawiera listę `Employee` obiekty i listy <xref:System.Exception> obiektów. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Obiektu rozdaje te dane podczas sumy otrzymanej `Employee` i <xref:System.Exception> liczniki obiektu jest równe wielkości partii.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod. `Main` Metoda porównuje czas wymagany do wykonania wstawienia wsadowej bazy danych w zależności od czasu do wykonania-przetwarzanej wsadowo bazy danych. Ilustruje też użycie buforowanego sprzężenia do odczytu danych pracowników z bazy danych, a także raportowania błędów.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
