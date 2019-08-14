---
title: 'Przewodnik: Prosty model obiektu i zapytanie (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 43092eb7490d5629f1ababac1d8f8b3aff94299b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971866"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="623b7-102">Przewodnik: Prosty model obiektu i zapytanie (C#)</span><span class="sxs-lookup"><span data-stu-id="623b7-102">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="623b7-103">Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz z minimalnymi złożonością.</span><span class="sxs-lookup"><span data-stu-id="623b7-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="623b7-104">Utworzysz klasę jednostki, która będzie modelować tabelę Customers w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="623b7-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="623b7-105">Następnie utworzysz proste zapytanie, aby wyświetlić listę klientów, którzy znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="623b7-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="623b7-106">Ten Instruktaż jest zorientowany na kod według projektu, aby pomóc w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazywania koncepcji.</span><span class="sxs-lookup"><span data-stu-id="623b7-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="623b7-107">Zwykle mówiąc, użyj Object Relational Designer do utworzenia modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="623b7-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="623b7-108">Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="623b7-108">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="623b7-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="623b7-109">Prerequisites</span></span>

- <span data-ttu-id="623b7-110">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest5").</span><span class="sxs-lookup"><span data-stu-id="623b7-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="623b7-111">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="623b7-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="623b7-112">Ten Instruktaż wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="623b7-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="623b7-113">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="623b7-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="623b7-114">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="623b7-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="623b7-115">Po pobraniu bazy danych Skopiuj plik do folderu c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="623b7-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="623b7-116">Omówienie</span><span class="sxs-lookup"><span data-stu-id="623b7-116">Overview</span></span>

<span data-ttu-id="623b7-117">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="623b7-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="623b7-118">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="623b7-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="623b7-119">Mapowanie klasy do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="623b7-120">Wyznaczanie właściwości klasy w celu reprezentowania kolumn bazy danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="623b7-121">Określanie połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="623b7-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="623b7-122">Tworzenie prostego zapytania do uruchamiania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="623b7-123">Wykonywanie zapytania i obserwowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="623b7-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="623b7-124">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="623b7-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="623b7-125">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="623b7-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="623b7-126">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="623b7-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="623b7-127">W menu **plik** programu Visual Studio wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="623b7-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="623b7-128">W okienku **typy projektów** okna dialogowego **Nowy projekt** kliknij pozycję Wizualizacja. **C#**</span><span class="sxs-lookup"><span data-stu-id="623b7-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="623b7-129">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="623b7-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="623b7-130">W polu **Nazwa** wpisz **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="623b7-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="623b7-131">W polu **Lokalizacja** Sprawdź, gdzie mają być przechowywane pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="623b7-131">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="623b7-132">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="623b7-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="623b7-133">Dodawanie odwołań i dyrektyw LINQ</span><span class="sxs-lookup"><span data-stu-id="623b7-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="623b7-134">W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="623b7-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="623b7-135">Jeśli obiekt system. Data. LINQ nie jest wymieniony jako odwołanie w projekcie (rozwiń węzeł **odwołania** w **Eksplorator rozwiązań**), Dodaj go, jak wyjaśniono w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="623b7-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="623b7-136">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="623b7-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="623b7-137">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="623b7-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="623b7-138">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="623b7-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="623b7-139">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="623b7-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="623b7-140">Dodaj następujące dyrektywy w górnej części **program.cs**:</span><span class="sxs-lookup"><span data-stu-id="623b7-140">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="623b7-141">Mapowanie klasy do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="623b7-141">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="623b7-142">W tym kroku utworzysz klasę i zamapujesz ją do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="623b7-143">Takie klasy są określane jako *Klasa jednostki*.</span><span class="sxs-lookup"><span data-stu-id="623b7-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="623b7-144">Należy pamiętać, że mapowanie jest realizowane przez jedynie dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="623b7-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="623b7-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="623b7-146">Aby utworzyć klasę jednostki i zamapować ją na tabelę bazy danych</span><span class="sxs-lookup"><span data-stu-id="623b7-146">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="623b7-147">Wpisz lub wklej następujący kod do program.cs bezpośrednio powyżej `Program` deklaracji klasy:</span><span class="sxs-lookup"><span data-stu-id="623b7-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="623b7-148">Wyznaczanie właściwości klasy do reprezentowania kolumn bazy danych</span><span class="sxs-lookup"><span data-stu-id="623b7-148">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="623b7-149">W tym kroku wykonujesz kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="623b7-149">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="623b7-150">Użyj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `City` `CustomerID` i właściwości klasy Entity jako reprezentujące kolumny w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="623b7-151">Należy wyznaczyć `CustomerID` Właściwość reprezentującą kolumnę klucza podstawowego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="623b7-152">`_CustomerID` Wyznaczysz `_City` pola i dla magazynu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="623b7-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="623b7-153">program może następnie przechowywać i pobierać wartości bezpośrednio, zamiast korzystać z publicznych metod dostępu, które mogą zawierać logikę biznesową.</span><span class="sxs-lookup"><span data-stu-id="623b7-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="623b7-154">Do reprezentowania cech dwóch kolumn bazy danych</span><span class="sxs-lookup"><span data-stu-id="623b7-154">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="623b7-155">Wpisz lub wklej następujący kod do program.cs wewnątrz nawiasów klamrowych `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="623b7-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="623b7-156">Określanie połączenia z bazą danych Northwind</span><span class="sxs-lookup"><span data-stu-id="623b7-156">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="623b7-157">W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu, aby nawiązać połączenie między strukturami danych opartymi na kodzie i samą bazą danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="623b7-158"><xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pośrednictwem którego można pobrać obiekty z bazy danych i przesłać zmiany.</span><span class="sxs-lookup"><span data-stu-id="623b7-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="623b7-159">Deklarujemy również, `Table<Customer>` aby pełnić rolę logicznej, wpisanej tabeli dla zapytań względem tabeli Customers w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="623b7-160">Te zapytania zostaną utworzone i wykonane w dalszych krokach.</span><span class="sxs-lookup"><span data-stu-id="623b7-160">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="623b7-161">Aby określić połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="623b7-161">To specify the database connection</span></span>

- <span data-ttu-id="623b7-162">Wpisz lub wklej następujący kod w `Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="623b7-162">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="623b7-163">Należy pamiętać, `northwnd.mdf` że plik jest założono, że znajduje się w folderze linqtest5.</span><span class="sxs-lookup"><span data-stu-id="623b7-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="623b7-164">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="623b7-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="623b7-165">Tworzenie prostego zapytania</span><span class="sxs-lookup"><span data-stu-id="623b7-165">Creating a Simple Query</span></span>

<span data-ttu-id="623b7-166">W tym kroku utworzysz zapytanie, aby sprawdzić, którzy klienci w tabeli Klienci bazy danych znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="623b7-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="623b7-167">Kod zapytania w tym kroku tylko opisuje zapytanie.</span><span class="sxs-lookup"><span data-stu-id="623b7-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="623b7-168">Nie wykonuje go.</span><span class="sxs-lookup"><span data-stu-id="623b7-168">It does not execute it.</span></span> <span data-ttu-id="623b7-169">Takie podejście jest znane jako *odroczone wykonanie*.</span><span class="sxs-lookup"><span data-stu-id="623b7-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="623b7-170">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="623b7-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="623b7-171">Utworzysz również dane wyjściowe dziennika w celu wyświetlenia poleceń SQL, które [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generują.</span><span class="sxs-lookup"><span data-stu-id="623b7-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="623b7-172">Ta funkcja rejestrowania (która korzysta <xref:System.Data.Linq.DataContext.Log%2A>z programu) jest przydatna podczas debugowania, a przy określaniu, że polecenia wysyłane do bazy danych dokładnie reprezentują zapytanie.</span><span class="sxs-lookup"><span data-stu-id="623b7-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="623b7-173">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="623b7-173">To create a simple query</span></span>

- <span data-ttu-id="623b7-174">Wpisz lub wklej następujący kod do `Main` metody `Table<Customer>` po deklaracji.</span><span class="sxs-lookup"><span data-stu-id="623b7-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="623b7-175">Wykonywanie zapytania</span><span class="sxs-lookup"><span data-stu-id="623b7-175">Executing the Query</span></span>

<span data-ttu-id="623b7-176">W tym kroku rzeczywiście wykonujesz zapytanie.</span><span class="sxs-lookup"><span data-stu-id="623b7-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="623b7-177">Wyrażenia zapytania utworzone w poprzednich krokach nie są oceniane do momentu, gdy będą potrzebne wyniki.</span><span class="sxs-lookup"><span data-stu-id="623b7-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="623b7-178">Po rozpoczęciu `foreach` iteracji polecenie SQL jest wykonywane względem bazy danych, a obiekty są w materiałach.</span><span class="sxs-lookup"><span data-stu-id="623b7-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="623b7-179">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="623b7-179">To execute the query</span></span>

1. <span data-ttu-id="623b7-180">Wpisz lub wklej następujący kod na końcu `Main` metody (po opisie zapytania).</span><span class="sxs-lookup"><span data-stu-id="623b7-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="623b7-181">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="623b7-181">Press F5 to debug the application.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="623b7-182">Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów w temacie [uczenie się według przewodników](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="623b7-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="623b7-183">Wyniki zapytania w oknie konsoli powinny wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="623b7-183">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="623b7-184">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="623b7-184">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="623b7-185">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="623b7-185">Next Steps</span></span>

<span data-ttu-id="623b7-186">[Przewodnik: Wykonywanie zapytań w relacjachC#(](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) ) jest kontynuowane, gdy ten przewodnik zakończy się.</span><span class="sxs-lookup"><span data-stu-id="623b7-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="623b7-187">Wskazówki dotyczące zapytania między relacjami pokazują [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , jak można wykonywać zapytania między tabelami, podobnie jak *sprzężenia* w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="623b7-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="623b7-188">Jeśli chcesz wykonać zapytanie w przewodniku dotyczącym relacji, pamiętaj o zapisaniu rozwiązania dla przewodnika, który właśnie został ukończony, co jest wymaganiem wstępnym.</span><span class="sxs-lookup"><span data-stu-id="623b7-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="623b7-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="623b7-189">See also</span></span>

- [<span data-ttu-id="623b7-190">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="623b7-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
