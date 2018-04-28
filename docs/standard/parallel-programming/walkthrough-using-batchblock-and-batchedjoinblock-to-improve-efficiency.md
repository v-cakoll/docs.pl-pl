---
title: 'Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock'
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
ms.openlocfilehash: e9305fd2a0e61a71f6875d6061f835e9cdae5dd1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="533b8-102">Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="533b8-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="533b8-103">Biblioteka przepływu danych tpl zapewnia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> klasy, aby mogli otrzymywać i buforu danych z jednego lub więcej źródeł i rozpropagowane limit buforowane dane jako jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="533b8-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="533b8-104">Ten mechanizm przetwarzanie wsadowe jest przydatne, gdy zbieranie danych z jednego lub więcej źródeł, a następnie przetworzyć wielu elementów danych, takich jak partii.</span><span class="sxs-lookup"><span data-stu-id="533b8-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="533b8-105">Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="533b8-106">Ta operacja może być bardziej wydajne, jeśli wiele elementów są wstawiane jednocześnie zamiast pojedynczo po kolei.</span><span class="sxs-lookup"><span data-stu-id="533b8-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="533b8-107">W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> liczba operacji wstawienia klasę, aby zwiększyć wydajność takiej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="533b8-108">Opisuje również sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasa do przechwytywania zarówno wyniki oraz wszystkie wyjątki, które wystąpić, gdy program odczytuje z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="533b8-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="533b8-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="533b8-110">Przeczytać sekcję Join bloków w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumentów przed skorzystaniem z tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="533b8-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="533b8-111">Upewnij się, że masz kopię bazy danych Northwind Northwind.sdf dostępnego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="533b8-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="533b8-112">Ten plik znajduje się w folderze % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="533b8-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="533b8-113">W niektórych wersjach systemu Windows nie można nawiązać połączenia Northwind.sdf Jeśli Visual Studio działa w trybie bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="533b8-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="533b8-114">Aby połączyć się Northwind.sdf, uruchom Visual Studio lub w wierszu polecenia programu Visual Studio **Uruchom jako administrator** tryb.</span><span class="sxs-lookup"><span data-stu-id="533b8-114">To connect to Northwind.sdf, start Visual Studio or a Visual Studio command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="533b8-115">Ten przewodnik zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="533b8-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="533b8-116">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="533b8-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="533b8-117">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="533b8-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="533b8-118">Definiowanie pracowników operacje bazy danych</span><span class="sxs-lookup"><span data-stu-id="533b8-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="533b8-119">Dodawanie danych o pracownikach w bazie danych bez korzystania z buforowania</span><span class="sxs-lookup"><span data-stu-id="533b8-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="533b8-120">Aby dodać do bazy danych o pracownikach przy użyciu buforowania</span><span class="sxs-lookup"><span data-stu-id="533b8-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="533b8-121">Za pomocą buforowanego sprzężenia można odczytać danych o pracownikach z bazy danych</span><span class="sxs-lookup"><span data-stu-id="533b8-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="533b8-122">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="533b8-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="533b8-123">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="533b8-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="533b8-124">W programie Visual Studio Utwórz Visual C# lub Visual Basic **aplikacji konsoli** projektu.</span><span class="sxs-lookup"><span data-stu-id="533b8-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="533b8-125">W tym dokumencie projektu o nazwie `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="533b8-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="533b8-126">W projekcie Dodaj odwołanie do System.Data.SqlServerCe.dll i odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="533b8-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="533b8-127">Upewnij się, że pliku Form1.cs (Form1.vb w języku Visual Basic) zawiera następujące `using` (`Imports` w języku Visual Basic) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="533b8-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="533b8-128">Dodaj następujące elementy członkowskie danych, aby `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="533b8-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="533b8-129">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="533b8-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="533b8-130">Dodaj do `Program` klasy `Employee` klasy.</span><span class="sxs-lookup"><span data-stu-id="533b8-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="533b8-131">`Employee` Klasa zawiera trzy właściwości `EmployeeID`, `LastName`, i `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="533b8-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="533b8-132">Te właściwości odpowiadają `Employee ID`, `Last Name`, i `First Name` kolumn w `Employees` tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="533b8-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="533b8-133">Dla tego pokazu `Employee` klasy definiuje również `Random` metodę, która tworzy `Employee` obiektu, który ma losowych wartości jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="533b8-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="533b8-134">Definiowanie pracowników operacje bazy danych</span><span class="sxs-lookup"><span data-stu-id="533b8-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="533b8-135">Dodaj do `Program` klasy `InsertEmployees`, `GetEmployeeCount`, i `GetEmployeeID` metody.</span><span class="sxs-lookup"><span data-stu-id="533b8-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="533b8-136">`InsertEmployees` Metoda dodaje nowe rekordy pracowników w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="533b8-137">`GetEmployeeCount` Metoda pobiera liczba wpisów w `Employees` tabeli.</span><span class="sxs-lookup"><span data-stu-id="533b8-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="533b8-138">`GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika, która została podana nazwa.</span><span class="sxs-lookup"><span data-stu-id="533b8-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="533b8-139">Każda z tych metod przyjmuje parametry połączenia z bazą danych Northwind i korzysta z funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikowania się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="533b8-140">Dodawanie danych o pracownikach w bazie danych bez korzystania z buforowania</span><span class="sxs-lookup"><span data-stu-id="533b8-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="533b8-141">Dodaj do `Program` klasy `AddEmployees` i `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="533b8-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="533b8-142">`AddEmployees` Metody dodaje pracownika losowe dane do bazy danych za pomocą przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="533b8-143">Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, który wywołuje `InsertEmployees` metody, aby dodać wpis pracownika w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="533b8-144">`AddEmployees` Metoda wywołuje `PostRandomEmployees` metodę publikowania wielu `Employee` obiekty do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="533b8-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="533b8-145">`AddEmployees` Metody czeka Wstaw wszystkie operacje, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="533b8-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="533b8-146">Aby dodać do bazy danych o pracownikach przy użyciu buforowania</span><span class="sxs-lookup"><span data-stu-id="533b8-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="533b8-147">Dodaj do `Program` klasy `AddEmployeesBatched` metody.</span><span class="sxs-lookup"><span data-stu-id="533b8-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="533b8-148">Ta metoda jest podobny `AddEmployees`, ale również używa <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy do zbuforowania wielu `Employee` obiekty przed wysłaniem tych obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="533b8-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="533b8-149">Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy rozprzestrzenia się wiele elementów jako kolekcję <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt jest zmodyfikowany do działania na tablicę `Employee` obiektów.</span><span class="sxs-lookup"><span data-stu-id="533b8-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="533b8-150">Podobnie jak w `AddEmployees` metody `AddEmployeesBatched` wywołania `PostRandomEmployees` metodę publikowania wielu `Employee` obiekty; jednak `AddEmployeesBatched` zapisuje te obiekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="533b8-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="533b8-151">`AddEmployeesBatched` — Metoda oczekuje także dla wszystkich Wstaw na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="533b8-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="533b8-152">Za pomocą buforowanego sprzężenia można odczytać danych o pracownikach z bazy danych</span><span class="sxs-lookup"><span data-stu-id="533b8-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="533b8-153">Dodaj do `Program` klasy `GetRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="533b8-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="533b8-154">Ta metoda Wyświetla informacje o pracownikach losowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="533b8-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="533b8-155">Tworzy kilka losowych `Employee` obiektów i wywołania `GetEmployeeID` metoda pobierania Unikatowy identyfikator dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="533b8-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="533b8-156">Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie istnieje żaden pracownik zgodnego z danym imiona i nazwiska, `GetRandomEmployees` używa metody <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasę do przechowywania `Employee` obiektów w przypadku pomyślnych wywołań `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań, które nie.</span><span class="sxs-lookup"><span data-stu-id="533b8-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="533b8-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiektu w tym przykładzie zostanie wykonane <xref:System.Tuple%602> obiektu, który zawiera listę `Employee` obiektów oraz listę <xref:System.Exception> obiektów.</span><span class="sxs-lookup"><span data-stu-id="533b8-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="533b8-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Obiektu rozprzestrzenia się te dane podczas sumę odebranej `Employee` i <xref:System.Exception> rozmiar partii jest równe liczby obiektów.</span><span class="sxs-lookup"><span data-stu-id="533b8-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="533b8-159">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="533b8-159">The Complete Example</span></span>  
 <span data-ttu-id="533b8-160">Poniższy przykład przedstawia kompletny kod.</span><span class="sxs-lookup"><span data-stu-id="533b8-160">The following example shows the complete code.</span></span> <span data-ttu-id="533b8-161">`Main` Metoda porównuje czas, który jest wymagany do wykonania operacji wstawienia wsadów bazy danych do czasu do wykonania operacji wstawienia niewsadowego bazy danych.</span><span class="sxs-lookup"><span data-stu-id="533b8-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="533b8-162">Ilustruje też korzystanie z buforowanego sprzężenia odczytywanie danych o pracownikach z bazy danych i również raportów o błędach.</span><span class="sxs-lookup"><span data-stu-id="533b8-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="533b8-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="533b8-163">See Also</span></span>  
 [<span data-ttu-id="533b8-164">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="533b8-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
