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
ms.openlocfilehash: 0367b4224b49377d8d17045e044976e1c511a8ed
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222109"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="c065f-102">Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="c065f-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="c065f-103">Biblioteka przepływu danych TPL zapewnia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> klasy tak, że może odbierać i buforować dane z jednego lub kilku źródeł i następnie rozpropagować te buforowane dane jako jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="c065f-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="c065f-104">Ten mechanizm łączenia we wsady jest przydatny, podczas zbierania danych z co najmniej jednego źródła, a następnie przetwarzania wielu elementów danych jako zadania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="c065f-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="c065f-105">Na przykład rozważmy aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="c065f-106">Ta operacja może być bardziej skuteczna, jeśli wiele elementów jest wstawianych jednocześnie zamiast pojedynczo po kolei.</span><span class="sxs-lookup"><span data-stu-id="c065f-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="c065f-107">W tym dokumencie opisano, jak używać <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operacje wstawiania klasy, aby zwiększyć wydajność takiej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="c065f-108">Opisano również sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasa do przechwytywania zarówno wyników jak i wyjątków, które występują, gdy program czyta z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="c065f-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c065f-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="c065f-110">Przeczytaj sekcję łączenia bloków w [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) dokumencie przed rozpoczęciem tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="c065f-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="c065f-111">Upewnij się, że masz kopię bazy danych Northwind, Northwind.sdf, dostępną na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c065f-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="c065f-112">Ten plik znajduje się w folderze % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="c065f-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c065f-113">W niektórych wersjach systemu Windows możesz nie może połączyć się z Northwind.sdf, jeśli program Visual Studio jest uruchomiony w trybie administratora.</span><span class="sxs-lookup"><span data-stu-id="c065f-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="c065f-114">Aby połączyć się z Northwind.sdf, uruchom Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w **Uruchom jako administrator** trybu.</span><span class="sxs-lookup"><span data-stu-id="c065f-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="c065f-115">Ten przewodnik zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="c065f-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="c065f-116">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="c065f-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="c065f-117">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="c065f-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="c065f-118">Definiowanie operacji w bazie danych pracownika</span><span class="sxs-lookup"><span data-stu-id="c065f-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="c065f-119">Dodawanie danych pracownika do bazy danych bez używania buforowania.</span><span class="sxs-lookup"><span data-stu-id="c065f-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="c065f-120">Używanie buforowania, aby dodać dane pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="c065f-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="c065f-121">Używanie buforowanego połączenia do odczytu danych pracowników z bazy danych</span><span class="sxs-lookup"><span data-stu-id="c065f-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="c065f-122">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="c065f-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="c065f-123">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="c065f-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="c065f-124">W programie Visual Studio Utwórz Visual C# lub Visual Basic **aplikację Konsolową** projektu.</span><span class="sxs-lookup"><span data-stu-id="c065f-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="c065f-125">W tym dokumencie projekt nazwano `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="c065f-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="c065f-126">W projekcie Dodaj odwołanie do System.Data.SqlServerCe.dll oraz odwołanie do System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="c065f-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="c065f-127">Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` (`Imports` w języku Visual Basic) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c065f-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="c065f-128">Dodaj następujące elementy członkowskie danych do `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="c065f-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="c065f-129">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="c065f-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="c065f-130">Dodaj do `Program` klasy `Employee` klasy.</span><span class="sxs-lookup"><span data-stu-id="c065f-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="c065f-131">`Employee` Klasa zawiera trzy właściwości `EmployeeID`, `LastName`, i `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="c065f-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="c065f-132">Te właściwości odpowiadają `Employee ID`, `Last Name`, i `First Name` kolumn w `Employees` tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="c065f-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="c065f-133">W tej prezentacji `Employee` klasa definiuje również `Random` metody, która tworzy `Employee` obiekt, który ma losowe wartości dla jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="c065f-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="c065f-134">Definiowanie operacji w bazie danych pracownika</span><span class="sxs-lookup"><span data-stu-id="c065f-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="c065f-135">Dodaj do `Program` klasy `InsertEmployees`, `GetEmployeeCount`, i `GetEmployeeID` metody.</span><span class="sxs-lookup"><span data-stu-id="c065f-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="c065f-136">`InsertEmployees` Metoda dodaje nowe rekordy pracowników do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="c065f-137">`GetEmployeeCount` Metoda pobiera liczbę wpisów w `Employees` tabeli.</span><span class="sxs-lookup"><span data-stu-id="c065f-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="c065f-138">`GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c065f-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="c065f-139">Każda z tych metod pobiera parametry połączenia z bazą danych Northwind i używa funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikowania się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="c065f-140">Dodawanie danych pracownika do bazy danych bez używania buforowania.</span><span class="sxs-lookup"><span data-stu-id="c065f-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="c065f-141">Dodaj do `Program` klasy `AddEmployees` i `PostRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="c065f-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="c065f-142">`AddEmployees` Metoda dodaje dane losowego pracownika do bazy danych za pomocą przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="c065f-143">Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu, który wywołuje `InsertEmployees` metodę, aby dodać wpis pracownika do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="c065f-144">`AddEmployees` Następnie wywołuje metodę `PostRandomEmployees` metodę przesyłania wielu `Employee` obiekty do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c065f-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="c065f-145">`AddEmployees` Metoda następnie oczekuje na zakończenie wszystkich operacje wstawiania.</span><span class="sxs-lookup"><span data-stu-id="c065f-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="c065f-146">Używanie buforowania, aby dodać dane pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="c065f-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="c065f-147">Dodaj do `Program` klasy `AddEmployeesBatched` metody.</span><span class="sxs-lookup"><span data-stu-id="c065f-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="c065f-148">Ta metoda przypomina `AddEmployees`, z tą różnicą, że użyto także <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy do zbuforowania wielu `Employee` obiektów przed wysłaniem tych obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c065f-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="c065f-149">Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy propaguje wiele elementów w kolekcji <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt zostanie zmodyfikowany zajmującym się tablica `Employee` obiektów.</span><span class="sxs-lookup"><span data-stu-id="c065f-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="c065f-150">Podobnie jak w `AddEmployees` metody `AddEmployeesBatched` wywołania `PostRandomEmployees` metodę przesyłania wielu `Employee` obiekty; jednak `AddEmployeesBatched` posyła te obiekty do <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c065f-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="c065f-151">`AddEmployeesBatched` Metoda także oczekuje na zakończenie wszystkich operacje wstawiania.</span><span class="sxs-lookup"><span data-stu-id="c065f-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="c065f-152">Używanie buforowanego połączenia do odczytu danych pracowników z bazy danych</span><span class="sxs-lookup"><span data-stu-id="c065f-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="c065f-153">Dodaj do `Program` klasy `GetRandomEmployees` metody.</span><span class="sxs-lookup"><span data-stu-id="c065f-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="c065f-154">Ta metoda drukuje informacje dotyczące losowych pracowników do konsoli.</span><span class="sxs-lookup"><span data-stu-id="c065f-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="c065f-155">Tworzy kilka losowych `Employee` obiektów i wywołuje `GetEmployeeID` metodę, aby pobrać Unikatowy identyfikator dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c065f-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="c065f-156">Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika o danym imiona i nazwiska, `GetRandomEmployees` metoda używa <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasę do przechowywania `Employee` obiektów dla zakończonych powodzeniem wywołań do `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiekty do wywołania, które się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="c065f-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="c065f-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Obiekt w tym przykładzie działa na <xref:System.Tuple%602> obiekt, który zawiera listę `Employee` obiekty i listy <xref:System.Exception> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c065f-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="c065f-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Obiektu rozdaje te dane podczas sumy otrzymanej `Employee` i <xref:System.Exception> liczniki obiektu jest równe wielkości partii.</span><span class="sxs-lookup"><span data-stu-id="c065f-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="c065f-159">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="c065f-159">The Complete Example</span></span>  
 <span data-ttu-id="c065f-160">Poniższy przykład pokazuje kompletny kod.</span><span class="sxs-lookup"><span data-stu-id="c065f-160">The following example shows the complete code.</span></span> <span data-ttu-id="c065f-161">`Main` Metoda porównuje czas wymagany do wykonania wstawienia wsadowej bazy danych w zależności od czasu do wykonania-przetwarzanej wsadowo bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c065f-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="c065f-162">Ilustruje też użycie buforowanego sprzężenia do odczytu danych pracowników z bazy danych, a także raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="c065f-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="c065f-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c065f-163">See also</span></span>

- [<span data-ttu-id="c065f-164">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="c065f-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
