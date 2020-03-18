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
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="43283-102">Wskazówki: Poprawa wydajności z wykorzystaniem klas BatchBlock i BatchedJoinBlock</span><span class="sxs-lookup"><span data-stu-id="43283-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="43283-103">Biblioteka przepływu danych TPL <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> zapewnia i klas, dzięki czemu można odbierać i buforować dane z jednego lub więcej źródeł, a następnie propagować, że buforowane dane jako jedną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="43283-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="43283-104">Ten mechanizm przetwarzania wsadowego jest przydatne podczas zbierania danych z jednego lub więcej źródeł, a następnie przetwarzać wiele elementów danych jako partii.</span><span class="sxs-lookup"><span data-stu-id="43283-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="43283-105">Rozważmy na przykład aplikację, która używa przepływu danych do wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43283-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="43283-106">Ta operacja może być bardziej efektywne, jeśli wiele elementów są wstawiane w tym samym czasie, a nie jeden na raz sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="43283-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="43283-107">W tym dokumencie opisano sposób używania <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasy w celu zwiększenia wydajności takich operacji wstawiania bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43283-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="43283-108">Opisano również, jak <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> używać klasy do przechwytywania zarówno wyniki i wszelkie wyjątki, które występują, gdy program odczytuje z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43283-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="43283-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="43283-109">Prerequisites</span></span>

1. <span data-ttu-id="43283-110">Przed rozpoczęciem tego instruktażenia przeczytaj sekcję Dołącz bloki w dokumencie [Przepływ danych.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)</span><span class="sxs-lookup"><span data-stu-id="43283-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="43283-111">Upewnij się, że masz kopię bazy danych Northwind, Northwind.sdf, dostępne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43283-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="43283-112">Ten plik zazwyczaj znajduje się w folderze %Program Files%\Microsoft SQL Server\\Compact Edition\v3.5\Samples .</span><span class="sxs-lookup"><span data-stu-id="43283-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="43283-113">W niektórych wersjach systemu Windows nie można połączyć się z northwind.sdf, jeśli program Visual Studio jest uruchomiony w trybie nieadministratora.</span><span class="sxs-lookup"><span data-stu-id="43283-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="43283-114">Aby połączyć się z northwind.sdf, uruchom program Visual Studio lub wiersz polecenia dewelopera dla programu Visual Studio w trybie **Uruchom jako administrator.**</span><span class="sxs-lookup"><span data-stu-id="43283-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="43283-115">Ten instruktaż zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="43283-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="43283-116">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="43283-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="43283-117">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="43283-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="43283-118">Definiowanie operacji bazy danych pracowników</span><span class="sxs-lookup"><span data-stu-id="43283-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="43283-119">Dodawanie danych pracowników do bazy danych bez korzystania z buforowania</span><span class="sxs-lookup"><span data-stu-id="43283-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="43283-120">Używanie buforowania do dodawania danych pracowników do bazy danych</span><span class="sxs-lookup"><span data-stu-id="43283-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="43283-121">Używanie sprzężenia buforowego do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="43283-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="43283-122">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="43283-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="43283-123">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="43283-123">Creating the Console Application</span></span>

1. <span data-ttu-id="43283-124">W programie Visual Studio utwórz projekt aplikacji visual C# lub Visual Basic **Console Application.**</span><span class="sxs-lookup"><span data-stu-id="43283-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="43283-125">W tym dokumencie projekt `DataflowBatchDatabase`nosi nazwę .</span><span class="sxs-lookup"><span data-stu-id="43283-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="43283-126">W projekcie dodaj odwołanie do pliku System.Data.SqlServerCe.dll i odwołanie do pliku System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="43283-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="43283-127">Upewnij się, że Form1.cs (Form1.vb `using` dla`Imports` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="43283-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="43283-128">Dodaj następujące elementy członkowskie `Program` danych do klasy.</span><span class="sxs-lookup"><span data-stu-id="43283-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="43283-129">Definiowanie klasy pracownika</span><span class="sxs-lookup"><span data-stu-id="43283-129">Defining the Employee Class</span></span>

<span data-ttu-id="43283-130">Dodaj do `Program` klasy `Employee` klasy.</span><span class="sxs-lookup"><span data-stu-id="43283-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="43283-131">Klasa `Employee` zawiera trzy `EmployeeID`właściwości, `LastName`, `FirstName`, i .</span><span class="sxs-lookup"><span data-stu-id="43283-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="43283-132">Właściwości te odpowiadają `Employee ID`, `Last Name`, `First Name` i `Employees` kolumny w tabeli w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="43283-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="43283-133">Dla tej demonstracji `Employee` klasa definiuje `Random` również metodę, `Employee` która tworzy obiekt, który ma losowe wartości dla jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="43283-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="43283-134">Definiowanie operacji bazy danych pracowników</span><span class="sxs-lookup"><span data-stu-id="43283-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="43283-135">Dodaj do `Program` klasy `InsertEmployees` `GetEmployeeCount`, `GetEmployeeID` , i metody.</span><span class="sxs-lookup"><span data-stu-id="43283-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="43283-136">Metoda `InsertEmployees` dodaje nowe rekordy pracowników do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43283-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="43283-137">Metoda `GetEmployeeCount` pobiera liczbę wpisów w `Employees` tabeli.</span><span class="sxs-lookup"><span data-stu-id="43283-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="43283-138">Metoda `GetEmployeeID` pobiera identyfikator pierwszego pracownika, który ma podaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="43283-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="43283-139">Każda z tych metod pobiera parametry połączenia z bazą danych `System.Data.SqlServerCe` Northwind i używa funkcji w przestrzeni nazw do komunikowania się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="43283-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="43283-140">Dodawanie danych pracowników do bazy danych bez użycia buforowania</span><span class="sxs-lookup"><span data-stu-id="43283-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="43283-141">Dodaj do `Program` klasy `AddEmployees` `PostRandomEmployees` i metody.</span><span class="sxs-lookup"><span data-stu-id="43283-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="43283-142">Metoda `AddEmployees` dodaje losowe dane pracownika do bazy danych przy użyciu przepływu danych.</span><span class="sxs-lookup"><span data-stu-id="43283-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="43283-143">Tworzy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który `InsertEmployees` wywołuje metodę, aby dodać wpis pracownika do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43283-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="43283-144">Metoda `AddEmployees` następnie wywołuje `PostRandomEmployees` metodę, `Employee` aby zaksięgować wiele obiektów do <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu.</span><span class="sxs-lookup"><span data-stu-id="43283-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="43283-145">Metoda `AddEmployees` następnie czeka na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="43283-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="43283-146">Używanie buforowania do dodawania danych pracowników do bazy danych</span><span class="sxs-lookup"><span data-stu-id="43283-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="43283-147">Dodaj do `Program` klasy `AddEmployeesBatched` metodę.</span><span class="sxs-lookup"><span data-stu-id="43283-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="43283-148">Ta metoda `AddEmployees`przypomina , z tą <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> różnicą, `Employee` że używa również klasy <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> do buforowania wielu obiektów przed wysłaniem tych obiektów do obiektu.</span><span class="sxs-lookup"><span data-stu-id="43283-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="43283-149">Ponieważ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> klasa propaguje wiele elementów jako <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> kolekcji, obiekt jest modyfikowany do działania na tablicy `Employee` obiektów.</span><span class="sxs-lookup"><span data-stu-id="43283-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="43283-150">Podobnie jak `AddEmployees` w `AddEmployeesBatched` metodzie wywołuje `PostRandomEmployees` `Employee` metodę do zaksięgowania wielu obiektów; jednak `AddEmployeesBatched` księguje te <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> obiekty do obiektu.</span><span class="sxs-lookup"><span data-stu-id="43283-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="43283-151">Metoda `AddEmployeesBatched` czeka również na zakończenie wszystkich operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="43283-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="43283-152">Używanie sprzężenia buforowego do odczytywania danych pracownika z bazy danych</span><span class="sxs-lookup"><span data-stu-id="43283-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="43283-153">Dodaj do `Program` klasy `GetRandomEmployees` metodę.</span><span class="sxs-lookup"><span data-stu-id="43283-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="43283-154">Ta metoda drukuje informacje o losowych pracowników do konsoli.</span><span class="sxs-lookup"><span data-stu-id="43283-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="43283-155">Tworzy kilka `Employee` losowych obiektów `GetEmployeeID` i wywołuje metodę, aby pobrać unikatowy identyfikator dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="43283-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="43283-156">Ponieważ `GetEmployeeID` metoda zgłasza wyjątek, jeśli nie ma żadnego pasującego pracownika `GetRandomEmployees` z podanych imion i nazwisk, metoda <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> używa klasy do `Employee` przechowywania obiektów dla pomyślnych wywołań `GetEmployeeID` i <xref:System.Exception?displayProperty=nameWithType> obiektów dla wywołań, które kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="43283-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="43283-157">Obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> w tym przykładzie <xref:System.Tuple%602> działa na obiekt, `Employee` który zawiera <xref:System.Exception> listę obiektów i listę obiektów.</span><span class="sxs-lookup"><span data-stu-id="43283-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="43283-158">Obiekt <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propaguje te dane, gdy `Employee` suma <xref:System.Exception> odebranych i liczba obiektów jest równa rozmiarowi partii.</span><span class="sxs-lookup"><span data-stu-id="43283-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="43283-159">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="43283-159">The Complete Example</span></span>

<span data-ttu-id="43283-160">W poniższym przykładzie przedstawiono kompletny kod.</span><span class="sxs-lookup"><span data-stu-id="43283-160">The following example shows the complete code.</span></span> <span data-ttu-id="43283-161">Metoda `Main` porównuje czas, który jest wymagany do wykonywania wsadowych wstawiania bazy danych w porównaniu do czasu do wykonywania wstawiania bazy danych niewsmażonych.</span><span class="sxs-lookup"><span data-stu-id="43283-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="43283-162">Pokazuje również użycie sprzężenia buforowego do odczytu danych pracownika z bazy danych, a także do zgłaszania błędów.</span><span class="sxs-lookup"><span data-stu-id="43283-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="43283-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43283-163">See also</span></span>

- [<span data-ttu-id="43283-164">Przepływ danych</span><span class="sxs-lookup"><span data-stu-id="43283-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
