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
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="3d1e8-102">Przewodnik: Poprawa wydajności przy użyciu klas BatchBlock i BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="3d1e8-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="3d1e8-103">Biblioteka TPL przepływu danych zawiera <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> klasy i <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , dzięki czemu można odbierać i buforować dane z jednego lub kilku źródeł, a następnie rozpowszechniać te dane buforowane jako jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="3d1e8-104">Ten mechanizm przetwarzania wsadowego jest przydatny podczas zbierania danych z jednego lub kilku źródeł, a następnie przetwarzania wielu elementów danych jako partii.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="3d1e8-105">Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="3d1e8-106">Ta operacja może być wydajniejsza, jeśli w tym samym czasie wstawiono wiele elementów zamiast jednego z nich naraz.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="3d1e8-107">W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy w celu zwiększenia wydajności takich operacji wstawiania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="3d1e8-108">Opisano w nim również, jak używać <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> klasy do przechwytywania zarówno wyników, jak i wyjątków, które występują, gdy program odczytuje dane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="3d1e8-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3d1e8-109">Prerequisites</span></span>

1. <span data-ttu-id="3d1e8-110">Przed rozpoczęciem tego instruktażu Przeczytaj sekcję Join Blocks w dokumencie [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) .</span><span class="sxs-lookup"><span data-stu-id="3d1e8-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="3d1e8-111">Upewnij się, że masz kopię bazy danych Northwind, Northwind. sdf, która jest dostępna na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="3d1e8-112">Ten plik zazwyczaj znajduje się w folderze% Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3d1e8-113">W niektórych wersjach systemu Windows nie można nawiązać połączenia z serwerem Northwind. sdf, jeśli program Visual Studio jest uruchomiony w trybie innym niż administrator.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="3d1e8-114">Aby połączyć się z Northwind. sdf, uruchom program Visual Studio lub wiersz polecenia dla deweloperów dla programu Visual Studio w trybie **Uruchom jako administrator** .</span><span class="sxs-lookup"><span data-stu-id="3d1e8-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="3d1e8-115">Ten Instruktaż zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="3d1e8-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="3d1e8-116">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="3d1e8-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="3d1e8-117">Definiowanie klasy Employee</span><span class="sxs-lookup"><span data-stu-id="3d1e8-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="3d1e8-118">Definiowanie operacji w bazie danych pracowników</span><span class="sxs-lookup"><span data-stu-id="3d1e8-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="3d1e8-119">Dodawanie danych pracownika do bazy danych bez używania buforowania</span><span class="sxs-lookup"><span data-stu-id="3d1e8-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="3d1e8-120">Używanie buforowania w celu dodania danych pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="3d1e8-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="3d1e8-121">Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="3d1e8-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="3d1e8-122">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="3d1e8-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="3d1e8-123">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="3d1e8-123">Creating the Console Application</span></span>

<a name="consoleApp"></a>
1. <span data-ttu-id="3d1e8-124">W programie Visual Studio Utwórz projekt C# **aplikacji konsolowej** wizualizacji lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="3d1e8-125">W tym dokumencie projekt ma nazwę `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="3d1e8-126">W projekcie Dodaj odwołanie do System. Data. SqlServerCe. dll i odwołanie do System. Threading. Tasks. przepływu danych. dll.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="3d1e8-127">Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera `using` następujące`Imports` instrukcje (w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3d1e8-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="3d1e8-128">Dodaj następujące składowe danych do `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="3d1e8-129">Definiowanie klasy Employee</span><span class="sxs-lookup"><span data-stu-id="3d1e8-129">Defining the Employee Class</span></span>

<span data-ttu-id="3d1e8-130">Dodaj do `Program` `Employee` klasy klasy.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="3d1e8-131">Klasa zawiera trzy właściwości, `EmployeeID`, `LastName`, i `FirstName`. `Employee`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="3d1e8-132">Te właściwości odpowiadają `Employee ID`, `Last Name`i `First Name` kolumnom w `Employees` tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="3d1e8-133">Dla tej demonstracji `Employee` Klasa `Random` definiuje także `Employee` metodę, która tworzy obiekt, który ma losowo wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="3d1e8-134">Definiowanie operacji w bazie danych pracowników</span><span class="sxs-lookup"><span data-stu-id="3d1e8-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="3d1e8-135">Dodaj do `Program` `GetEmployeeCount`klasy metody `GetEmployeeID`,,i. `InsertEmployees`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="3d1e8-136">`InsertEmployees` Metoda dodaje do bazy danych nowe rekordy pracowników.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="3d1e8-137">Metoda pobiera liczbę wpisów `Employees` w tabeli. `GetEmployeeCount`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="3d1e8-138">`GetEmployeeID` Metoda pobiera identyfikator pierwszego pracownika o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="3d1e8-139">Każda z tych metod przyjmuje parametry połączenia do bazy danych Northwind i używa funkcji w `System.Data.SqlServerCe` przestrzeni nazw do komunikacji z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="3d1e8-140">Dodawanie danych pracownika do bazy danych bez używania buforowania</span><span class="sxs-lookup"><span data-stu-id="3d1e8-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="3d1e8-141">Dodaj do `Program` `AddEmployees` klasy metody i. `PostRandomEmployees`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="3d1e8-142">`AddEmployees` Metoda dodaje losowo dane pracownika do bazy danych za pomocą przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="3d1e8-143">Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który `InsertEmployees` wywołuje metodę, aby dodać wpis pracownika do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="3d1e8-144">Metoda następnie wywołuje metodę, `PostRandomEmployees` `Employee` Aby<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> ogłosić wiele obiektów do obiektu. `AddEmployees`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="3d1e8-145">`AddEmployees` Metoda następnie czeka na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="3d1e8-146">Używanie buforowania w celu dodania danych pracownika do bazy danych</span><span class="sxs-lookup"><span data-stu-id="3d1e8-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="3d1e8-147">Dodaj do `Program` `AddEmployeesBatched` klasy metodę.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="3d1e8-148">Ta metoda przypomina `AddEmployees`, z tą różnicą, że <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> używa również klasy do buforowania `Employee` wielu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów przed wysłaniem tych obiektów do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="3d1e8-149">Ponieważ Klasa propaguje wiele elementów jako kolekcję <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> , obiekt jest modyfikowany do `Employee` działania na tablicy obiektów. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601></span><span class="sxs-lookup"><span data-stu-id="3d1e8-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="3d1e8-150">Podobnie jak w `AddEmployees` metodzie `AddEmployeesBatched` , wywołuje `PostRandomEmployees` `Employee` metodęw<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> celu opublikowania wielu obiektów, jednak zapisujeteobiektydoobiektu.`AddEmployeesBatched`</span><span class="sxs-lookup"><span data-stu-id="3d1e8-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="3d1e8-151">`AddEmployeesBatched` Metoda również czeka na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="3d1e8-152">Używanie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="3d1e8-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="3d1e8-153">Dodaj do `Program` `GetRandomEmployees` klasy metodę.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="3d1e8-154">Ta metoda drukuje informacje o losowych pracownikach w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="3d1e8-155">Tworzy kilka losowych `Employee` obiektów i `GetEmployeeID` wywołuje metodę, aby pobrać unikatowy identyfikator dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="3d1e8-156">`GetEmployeeID` `Employee` <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `GetRandomEmployees` Ponieważ metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika o podanym imieniu i nazwisku, metoda używa klasy do przechowywania obiektów dla udanych wywołań do i `GetEmployeeID` <xref:System.Exception?displayProperty=nameWithType> obiekty dla wywołań, które kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="3d1e8-157">Obiekt w tym przykładzie działa <xref:System.Tuple%602> w odniesieniu do obiektu `Employee` , który zawiera listę obiektów i listę <xref:System.Exception> obiektów. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601></span><span class="sxs-lookup"><span data-stu-id="3d1e8-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="3d1e8-158">Obiekt propaguje te dane, gdy suma odebranych `Employee` i <xref:System.Exception> liczników obiektów jest równa rozmiarowi partii. <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602></span><span class="sxs-lookup"><span data-stu-id="3d1e8-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="3d1e8-159">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="3d1e8-159">The Complete Example</span></span>

<span data-ttu-id="3d1e8-160">Poniższy przykład pokazuje kompletny kod.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-160">The following example shows the complete code.</span></span> <span data-ttu-id="3d1e8-161">`Main` Metoda porównuje czas wymagany do wykonania wsadowych wstawień bazy danych w porównaniu do czasu wykonywania operacji wstawiania baz danych bez partii.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="3d1e8-162">Przedstawiono w nim także użycie buforowanego sprzężenia do odczytywania danych pracownika z bazy danych, a także zgłaszania błędów.</span><span class="sxs-lookup"><span data-stu-id="3d1e8-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="3d1e8-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d1e8-163">See also</span></span>

- [<span data-ttu-id="3d1e8-164">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="3d1e8-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
