---
title: "Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 49056607d84b48584660ff62bba13147d6aa43ec
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock
Biblioteka przepływu danych tpl zapewnia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> klasy, aby mogli otrzymywać i buforu danych z jednego lub więcej źródeł i rozpropagowane limit buforowane dane jako jedną kolekcję. Ten mechanizm przetwarzanie wsadowe jest przydatne, gdy zbieranie danych z jednego lub więcej źródeł, a następnie przetworzyć wielu elementów danych, takich jak partii. Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów w bazie danych. Ta operacja może być bardziej wydajne, jeśli wiele elementów są wstawiane jednocześnie zamiast pojedynczo po kolei. W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> liczba operacji wstawienia klasę, aby zwiększyć wydajność takiej bazy danych. Opisuje również sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasa do przechwytywania zarówno wyniki oraz wszystkie wyjątki, które wystąpić, gdy program odczytuje z bazy danych.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Wymagania wstępne  
  
1.  Przeczytać sekcję Join bloków w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumentów przed skorzystaniem z tego przewodnika.  
  
2.  Upewnij się, że masz kopię bazy danych Northwind Northwind.sdf dostępnego na komputerze. Ten plik znajduje się w folderze % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.  
  
    > [!IMPORTANT]
    >  W niektórych wersjach systemu Windows nie można nawiązać połączenia Northwind.sdf Jeśli [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] działa w trybie bez uprawnień administratora. Aby nawiązać połączenie Northwind.sdf, uruchom [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] lub [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] wiersza polecenia **Uruchom jako administrator** tryb.  
  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Tworzenie aplikacji konsoli](#creating)  
  
-   [Definiowanie klasy pracownika](#employeeClass)  
  
-   [Definiowanie pracowników operacje bazy danych](#operations)  
  
-   [Dodawanie danych o pracownikach w bazie danych bez korzystania z buforowania](#nonBuffering)  
  
-   [Aby dodać do bazy danych o pracownikach przy użyciu buforowania](#buffering)  
  
-   [Za pomocą buforowanego sprzężenia można odczytać danych o pracownikach z bazy danych](#bufferedJoin)  
  
-   [Pełny przykład](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Tworzenie aplikacji konsoli  
  
<a name="consoleApp"></a>   
1.  W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], utworzyć Visual C# lub Visual Basic **aplikacji konsoli** projektu. W tym dokumencie projektu o nazwie `DataflowBatchDatabase`.  
  
2.  W projekcie Dodaj odwołanie do System.Data.SqlServerCe.dll i odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
3.  Upewnij się, że pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) zawiera następujące `using` (`Imports` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) instrukcje.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Dodaj następujące elementy członkowskie danych, aby `Program` klasy.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Definiowanie klasy pracownika  
 Dodaj do `Program` klasy `Employee` klasy.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` Klasa zawiera trzy właściwości `EmployeeID`, `LastName`, i `FirstName`. Te właściwości odpowiadają `Employee ID`, `Last Name`, i `First Name` kolumn w `Employees` tabeli w bazie danych Northwind. Dla tego pokazu `Employee` klasy definiuje również `Random` metodę, która tworzy `Employee` obiektu, który ma losowych wartości jego właściwości.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Definiowanie pracowników operacje bazy danych  
 Dodaj do `Program` klasy `InsertEmployees`, `GetEmployeeCount`, i `GetEmployeeID` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` Metoda dodaje nowe rekordy pracowników w bazie danych. `GetEmployeeCount` Metoda pobiera liczba wpisów w `Employees` tabeli. `GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika, która została podana nazwa. Każda z tych metod przyjmuje parametry połączenia z bazą danych Northwind i korzysta z funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikowania się z bazą danych.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Dodawanie danych o pracownikach w bazie danych bez korzystania z buforowania  
 Dodaj do `Program` klasy `AddEmployees` i `PostRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` Metody dodaje pracownika losowe dane do bazy danych za pomocą przepływu danych. Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, który wywołuje `InsertEmployees` metody, aby dodać wpis pracownika w bazie danych. `AddEmployees` Metoda wywołuje `PostRandomEmployees` metodę publikowania wielu `Employee` obiekty do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. `AddEmployees` Metody czeka Wstaw wszystkie operacje, aby zakończyć.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Aby dodać do bazy danych o pracownikach przy użyciu buforowania  
 Dodaj do `Program` klasy `AddEmployeesBatched` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Ta metoda jest podobny `AddEmployees`, ale również używa <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy do zbuforowania wielu `Employee` obiekty przed wysłaniem tych obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu. Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy rozprzestrzenia się wiele elementów jako kolekcję <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt jest zmodyfikowany do działania na tablicę `Employee` obiektów. Podobnie jak w `AddEmployees` metody `AddEmployeesBatched` wywołania `PostRandomEmployees` metodę publikowania wielu `Employee` obiekty; jednak `AddEmployeesBatched` zapisuje te obiekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiektu. `AddEmployeesBatched` — Metoda oczekuje także dla wszystkich Wstaw na zakończenie operacji.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Za pomocą buforowanego sprzężenia można odczytać danych o pracownikach z bazy danych  
 Dodaj do `Program` klasy `GetRandomEmployees` metody.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Ta metoda Wyświetla informacje o pracownikach losowe do konsoli. Tworzy kilka losowych `Employee` obiektów i wywołania `GetEmployeeID` metoda pobierania Unikatowy identyfikator dla każdego obiektu. Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie istnieje żaden pracownik zgodnego z danym imiona i nazwiska, `GetRandomEmployees` używa metody <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasę do przechowywania `Employee` obiektów w przypadku pomyślnych wywołań `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań, które nie. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiektu w tym przykładzie zostanie wykonane <xref:System.Tuple%602> obiektu, który zawiera listę `Employee` obiektów oraz listę <xref:System.Exception> obiektów. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Obiektu rozprzestrzenia się te dane podczas sumę odebranej `Employee` i <xref:System.Exception> rozmiar partii jest równe liczby obiektów.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład przedstawia kompletny kod. `Main` Metoda porównuje czas, który jest wymagany do wykonania operacji wstawienia wsadów bazy danych do czasu do wykonania operacji wstawienia niewsadowego bazy danych. Ilustruje też korzystanie z buforowanego sprzężenia odczytywanie danych o pracownikach z bazy danych i również raportów o błędach.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
