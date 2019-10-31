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
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="fea73-102">Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="fea73-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="fea73-103">Biblioteka TPL przepływu danych zawiera klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>, dzięki czemu można odbierać i buforować dane z jednego lub kilku źródeł, a następnie rozpowszechniać te dane w postaci danych w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fea73-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="fea73-104">Ten mechanizm przetwarzania wsadowego jest przydatny podczas zbierania danych z jednego lub kilku źródeł, a następnie przetwarzania wielu elementów danych jako partii.</span><span class="sxs-lookup"><span data-stu-id="fea73-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="fea73-105">Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="fea73-106">Ta operacja może być wydajniejsza, jeśli w tym samym czasie wstawiono wiele elementów zamiast jednego z nich naraz.</span><span class="sxs-lookup"><span data-stu-id="fea73-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="fea73-107">W tym dokumencie opisano sposób użycia klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> w celu zwiększenia wydajności takich operacji wstawiania baz danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="fea73-108">Opisano w nim również, jak używać klasy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>, aby przechwycić zarówno wyniki, jak i wyjątki, które występują, gdy program odczytuje z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="fea73-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fea73-109">Prerequisites</span></span>

1. <span data-ttu-id="fea73-110">Przed rozpoczęciem tego instruktażu Przeczytaj sekcję Join Blocks w dokumencie [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) .</span><span class="sxs-lookup"><span data-stu-id="fea73-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="fea73-111">Upewnij się, że masz kopię bazy danych Northwind, Northwind. sdf, która jest dostępna na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fea73-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="fea73-112">Ten plik zazwyczaj znajduje się w folderze% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="fea73-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fea73-113">W niektórych wersjach systemu Windows nie można nawiązać połączenia z serwerem Northwind. sdf, jeśli program Visual Studio jest uruchomiony w trybie innym niż administrator.</span><span class="sxs-lookup"><span data-stu-id="fea73-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="fea73-114">Aby połączyć się z Northwind. sdf, uruchom program Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w trybie **Uruchom jako administrator** .</span><span class="sxs-lookup"><span data-stu-id="fea73-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="fea73-115">Ten Instruktaż zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="fea73-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="fea73-116">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="fea73-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="fea73-117">Definiowanie klasy Employee</span><span class="sxs-lookup"><span data-stu-id="fea73-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="fea73-118">Definiowanie operacji w bazie danych pracowników</span><span class="sxs-lookup"><span data-stu-id="fea73-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="fea73-119">Dodawanie danych pracownika do bazy danych bez używania buforowania</span><span class="sxs-lookup"><span data-stu-id="fea73-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="fea73-120">Używanie buforowania w celu dodania danych pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="fea73-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="fea73-121">Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="fea73-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="fea73-122">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="fea73-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="fea73-123">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="fea73-123">Creating the Console Application</span></span>

1. <span data-ttu-id="fea73-124">W programie Visual Studio Utwórz projekt C# **aplikacji konsolowej** wizualizacji lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fea73-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="fea73-125">W tym dokumencie projekt ma nazwę `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="fea73-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="fea73-126">W projekcie Dodaj odwołanie do System. Data. SqlServerCe. dll i odwołanie do System. Threading. Tasks. przepływu danych. dll.</span><span class="sxs-lookup"><span data-stu-id="fea73-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="fea73-127">Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące instrukcje `using` (`Imports` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fea73-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="fea73-128">Dodaj następujące elementy członkowskie danych do klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="fea73-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="fea73-129">Definiowanie klasy Employee</span><span class="sxs-lookup"><span data-stu-id="fea73-129">Defining the Employee Class</span></span>

<span data-ttu-id="fea73-130">Dodaj do klasy `Program` klasy `Employee`.</span><span class="sxs-lookup"><span data-stu-id="fea73-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="fea73-131">Klasa `Employee` zawiera trzy właściwości, `EmployeeID`, `LastName`i `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="fea73-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="fea73-132">Te właściwości odpowiadają kolumnom `Employee ID`, `Last Name`i `First Name` w tabeli `Employees` w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="fea73-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="fea73-133">Dla tej demonstracji Klasa `Employee` definiuje również metodę `Random`, która tworzy obiekt `Employee`, który ma losowo wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="fea73-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="fea73-134">Definiowanie operacji w bazie danych pracowników</span><span class="sxs-lookup"><span data-stu-id="fea73-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="fea73-135">Dodaj do klasy `Program` metod `InsertEmployees`, `GetEmployeeCount`i `GetEmployeeID`.</span><span class="sxs-lookup"><span data-stu-id="fea73-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="fea73-136">Metoda `InsertEmployees` dodaje do bazy danych nowe rekordy pracowników.</span><span class="sxs-lookup"><span data-stu-id="fea73-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="fea73-137">Metoda `GetEmployeeCount` Pobiera liczbę wpisów w tabeli `Employees`.</span><span class="sxs-lookup"><span data-stu-id="fea73-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="fea73-138">Metoda `GetEmployeeID` Pobiera identyfikator pierwszego pracownika o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="fea73-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="fea73-139">Każda z tych metod przyjmuje parametry połączenia do bazy danych Northwind i używa funkcji w przestrzeni nazw `System.Data.SqlServerCe`, aby komunikować się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="fea73-140">Dodawanie danych pracownika do bazy danych bez używania buforowania</span><span class="sxs-lookup"><span data-stu-id="fea73-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="fea73-141">Dodaj do klasy `Program` metod `AddEmployees` i `PostRandomEmployees`.</span><span class="sxs-lookup"><span data-stu-id="fea73-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="fea73-142">Metoda `AddEmployees` dodaje losowo dane pracownika do bazy danych za pomocą przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="fea73-143">Tworzy obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, który wywołuje metodę `InsertEmployees`, aby dodać wpis pracownika do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fea73-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="fea73-144">Metoda `AddEmployees` następnie wywołuje metodę `PostRandomEmployees`, aby ogłosić wiele obiektów `Employee` do obiektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="fea73-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="fea73-145">Metoda `AddEmployees` następnie czeka na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="fea73-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="fea73-146">Używanie buforowania w celu dodania danych pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="fea73-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="fea73-147">Dodaj do klasy `Program` metody `AddEmployeesBatched`.</span><span class="sxs-lookup"><span data-stu-id="fea73-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="fea73-148">Ta metoda przypomina `AddEmployees`, z tą różnicą, że używa również klasy <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> do buforowania wielu obiektów `Employee` przed wysłaniem tych obiektów do obiektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="fea73-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="fea73-149">Ponieważ Klasa <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propaguje wiele elementów jako kolekcja, obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> jest modyfikowany do działania na tablicy obiektów `Employee`.</span><span class="sxs-lookup"><span data-stu-id="fea73-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="fea73-150">Podobnie jak w metodzie `AddEmployees`, `AddEmployeesBatched` wywołuje metodę `PostRandomEmployees`, aby ogłosić wiele obiektów `Employee`; jednak `AddEmployeesBatched` ogłasza te obiekty w obiekcie <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="fea73-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="fea73-151">Metoda `AddEmployeesBatched` czeka również na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="fea73-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="fea73-152">Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="fea73-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="fea73-153">Dodaj do klasy `Program` metody `GetRandomEmployees`.</span><span class="sxs-lookup"><span data-stu-id="fea73-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="fea73-154">Ta metoda drukuje informacje o losowych pracownikach w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="fea73-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="fea73-155">Tworzy kilka losowo `Employee` obiektów i wywołuje metodę `GetEmployeeID`, aby pobrać unikatowy identyfikator dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fea73-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="fea73-156">Ponieważ metoda `GetEmployeeID` zgłasza wyjątek, jeśli nie ma pasującego pracownika z podanym imieniem i nazwiskiem, Metoda `GetRandomEmployees` używa klasy <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> do przechowywania obiektów `Employee` dla udanych wywołań do `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań zakończonych niepowodzeniem .</span><span class="sxs-lookup"><span data-stu-id="fea73-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="fea73-157">Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> w tym przykładzie działa na obiekcie <xref:System.Tuple%602>, który zawiera listę obiektów `Employee` i listę obiektów <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="fea73-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="fea73-158">Obiekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propaguje te dane, gdy suma odebranych `Employee` i <xref:System.Exception> liczby obiektów jest równa rozmiarowi partii.</span><span class="sxs-lookup"><span data-stu-id="fea73-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="fea73-159">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="fea73-159">The Complete Example</span></span>

<span data-ttu-id="fea73-160">Poniższy przykład pokazuje kompletny kod.</span><span class="sxs-lookup"><span data-stu-id="fea73-160">The following example shows the complete code.</span></span> <span data-ttu-id="fea73-161">Metoda `Main` porównuje czas wymagany do wykonania wsadowych wstawień bazy danych zamiast czasu na wykonanie wstawiania baz danych bez partii.</span><span class="sxs-lookup"><span data-stu-id="fea73-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="fea73-162">Przedstawiono w nim także użycie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych, a także zgłaszania błędów.</span><span class="sxs-lookup"><span data-stu-id="fea73-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="fea73-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fea73-163">See also</span></span>

- [<span data-ttu-id="fea73-164">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="fea73-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
