---
title: 'Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: e0840adba62e10640ef16908db6b57519191f7f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946784"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="fcc71-102">Przewodnik: Prosty model obiektu i zapytanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcc71-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>

<span data-ttu-id="fcc71-103">Ten Instruktaż zawiera podstawowy kompleksowy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusz z minimalnymi złożonością.</span><span class="sxs-lookup"><span data-stu-id="fcc71-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="fcc71-104">Utworzysz klasę jednostki, która będzie modelować tabelę Customers w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="fcc71-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="fcc71-105">Następnie utworzysz proste zapytanie, aby wyświetlić listę klientów, którzy znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="fcc71-106">Ten Instruktaż jest zorientowany na kod według projektu, aby pomóc w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazywania koncepcji.</span><span class="sxs-lookup"><span data-stu-id="fcc71-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="fcc71-107">Zwykle mówiąc, użyj Object Relational Designer do utworzenia modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="fcc71-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="fcc71-108">Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fcc71-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fcc71-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fcc71-109">Prerequisites</span></span>

- <span data-ttu-id="fcc71-110">W tym instruktażu do przechowywania plików służy dedykowany folder ("c:\linqtest").</span><span class="sxs-lookup"><span data-stu-id="fcc71-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="fcc71-111">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="fcc71-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="fcc71-112">Ten Instruktaż wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="fcc71-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="fcc71-113">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcc71-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="fcc71-114">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="fcc71-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="fcc71-115">Po pobraniu bazy danych Skopiuj plik do folderu c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="fcc71-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>

## <a name="overview"></a><span data-ttu-id="fcc71-116">Omówienie</span><span class="sxs-lookup"><span data-stu-id="fcc71-116">Overview</span></span>

<span data-ttu-id="fcc71-117">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="fcc71-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="fcc71-118">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tworzenie rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcc71-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="fcc71-119">Mapowanie klasy do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="fcc71-120">Wyznaczanie właściwości klasy w celu reprezentowania kolumn bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="fcc71-121">Określanie połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="fcc71-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="fcc71-122">Tworzenie prostego zapytania do uruchamiania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="fcc71-123">Wykonywanie zapytania i obserwowanie wyników.</span><span class="sxs-lookup"><span data-stu-id="fcc71-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="fcc71-124">Tworzenie rozwiązania LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fcc71-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="fcc71-125">W tym pierwszym zadaniu utworzysz rozwiązanie programu Visual Studio, które zawiera niezbędne odwołania do kompilowania i uruchamiania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="fcc71-126">Aby utworzyć rozwiązanie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fcc71-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="fcc71-127">W menu **plik** kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-127">On the **File** menu, click **New Project**.</span></span>

2. <span data-ttu-id="fcc71-128">W okienku **typy projektów** okna dialogowego **nowy projekt** kliknij **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>

3. <span data-ttu-id="fcc71-129">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="fcc71-130">W polu **Nazwa** wpisz **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="fcc71-131">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-131">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="fcc71-132">Dodawanie odwołań i dyrektyw LINQ</span><span class="sxs-lookup"><span data-stu-id="fcc71-132">Adding LINQ References and Directives</span></span>

<span data-ttu-id="fcc71-133">W tym instruktażu są używane zestawy, które mogą nie być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="fcc71-134">Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie w projekcie (kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** i rozwiń węzeł **odwołania** ), Dodaj go, jak wyjaśniono w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="fcc71-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="fcc71-135">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="fcc71-135">To add System.Data.Linq</span></span>

1. <span data-ttu-id="fcc71-136">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="fcc71-137">W oknie dialogowym **Dodawanie odwołania** kliknij pozycję **.NET**, kliknij zestaw system. Data. LINQ, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="fcc71-138">Zestaw zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-138">The assembly is added to the project.</span></span>

3. <span data-ttu-id="fcc71-139">W oknie dialogowym **Dodaj odwołanie** kliknij pozycję **.NET**, przewiń do i kliknij pozycję System. Windows. Forms, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>

     <span data-ttu-id="fcc71-140">Ten zestaw, który obsługuje okno komunikatu w instruktażu, jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>

4. <span data-ttu-id="fcc71-141">Dodaj powyższe `Module1`dyrektywy poniżej:</span><span class="sxs-lookup"><span data-stu-id="fcc71-141">Add the following directives above `Module1`:</span></span>

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="fcc71-142">Mapowanie klasy do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="fcc71-142">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="fcc71-143">W tym kroku utworzysz klasę i zamapujesz ją do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="fcc71-144">Takie klasy są określane jako *Klasa jednostki*.</span><span class="sxs-lookup"><span data-stu-id="fcc71-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="fcc71-145">Należy pamiętać, że mapowanie jest realizowane przez jedynie dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="fcc71-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="fcc71-147">Aby utworzyć klasę jednostki i zamapować ją na tabelę bazy danych</span><span class="sxs-lookup"><span data-stu-id="fcc71-147">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="fcc71-148">Wpisz lub wklej następujący kod do Module1. vb bezpośrednio powyżej `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="fcc71-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="fcc71-149">Wyznaczanie właściwości klasy do reprezentowania kolumn bazy danych</span><span class="sxs-lookup"><span data-stu-id="fcc71-149">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="fcc71-150">W tym kroku wykonujesz kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="fcc71-150">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="fcc71-151">Użyj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `City` `CustomerID` i właściwości klasy Entity jako reprezentujące kolumny w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="fcc71-152">Należy wyznaczyć `CustomerID` Właściwość reprezentującą kolumnę klucza podstawowego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="fcc71-153">`_CustomerID` Wyznaczysz `_City` pola i dla magazynu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="fcc71-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="fcc71-154">program może następnie przechowywać i pobierać wartości bezpośrednio, zamiast korzystać z publicznych metod dostępu, które mogą zawierać logikę biznesową.</span><span class="sxs-lookup"><span data-stu-id="fcc71-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="fcc71-155">Do reprezentowania cech dwóch kolumn bazy danych</span><span class="sxs-lookup"><span data-stu-id="fcc71-155">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="fcc71-156">Wpisz lub wklej następujący kod do Module1. vb tuż przed `End Class`:</span><span class="sxs-lookup"><span data-stu-id="fcc71-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="fcc71-157">Określanie połączenia z bazą danych Northwind</span><span class="sxs-lookup"><span data-stu-id="fcc71-157">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="fcc71-158">W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu, aby nawiązać połączenie między strukturami danych opartymi na kodzie i samą bazą danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="fcc71-159"><xref:System.Data.Linq.DataContext> Jest głównym kanałem, za pośrednictwem którego można pobrać obiekty z bazy danych i przesłać zmiany.</span><span class="sxs-lookup"><span data-stu-id="fcc71-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="fcc71-160">Deklarujemy również, `Table(Of Customer)` aby pełnić rolę logicznej, wpisanej tabeli dla zapytań względem tabeli Customers w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="fcc71-161">Te zapytania zostaną utworzone i wykonane w dalszych krokach.</span><span class="sxs-lookup"><span data-stu-id="fcc71-161">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="fcc71-162">Aby określić połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="fcc71-162">To specify the database connection</span></span>

- <span data-ttu-id="fcc71-163">Wpisz lub wklej następujący kod w `Sub Main` metodzie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-163">Type or paste the following code into the `Sub Main` method.</span></span>

     <span data-ttu-id="fcc71-164">Należy pamiętać, `northwnd.mdf` że plik jest założono, że znajduje się w folderze linqtest.</span><span class="sxs-lookup"><span data-stu-id="fcc71-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="fcc71-165">Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="fcc71-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="fcc71-166">Tworzenie prostego zapytania</span><span class="sxs-lookup"><span data-stu-id="fcc71-166">Creating a Simple Query</span></span>

<span data-ttu-id="fcc71-167">W tym kroku utworzysz zapytanie, aby sprawdzić, którzy klienci w tabeli Klienci bazy danych znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="fcc71-168">Kod zapytania w tym kroku tylko opisuje zapytanie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="fcc71-169">Nie wykonuje go.</span><span class="sxs-lookup"><span data-stu-id="fcc71-169">It does not execute it.</span></span> <span data-ttu-id="fcc71-170">Takie podejście jest znane jako *odroczone wykonanie*.</span><span class="sxs-lookup"><span data-stu-id="fcc71-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="fcc71-171">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="fcc71-171">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="fcc71-172">Utworzysz również dane wyjściowe dziennika w celu wyświetlenia poleceń SQL, które [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generują.</span><span class="sxs-lookup"><span data-stu-id="fcc71-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="fcc71-173">Ta funkcja rejestrowania (która korzysta <xref:System.Data.Linq.DataContext.Log%2A>z programu) jest przydatna podczas debugowania, a przy określaniu, że polecenia wysyłane do bazy danych dokładnie reprezentują zapytanie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="fcc71-174">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="fcc71-174">To create a simple query</span></span>

- <span data-ttu-id="fcc71-175">Wpisz lub wklej następujący kod do `Sub Main` metody `Table(Of Customer)` po deklaracji:</span><span class="sxs-lookup"><span data-stu-id="fcc71-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a><span data-ttu-id="fcc71-176">Wykonywanie zapytania</span><span class="sxs-lookup"><span data-stu-id="fcc71-176">Executing the Query</span></span>

<span data-ttu-id="fcc71-177">W tym kroku rzeczywiście wykonujesz zapytanie.</span><span class="sxs-lookup"><span data-stu-id="fcc71-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="fcc71-178">Wyrażenia zapytania utworzone w poprzednich krokach nie są oceniane do momentu, gdy będą potrzebne wyniki.</span><span class="sxs-lookup"><span data-stu-id="fcc71-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="fcc71-179">Po rozpoczęciu `For Each` iteracji polecenie SQL jest wykonywane względem bazy danych, a obiekty są w materiałach.</span><span class="sxs-lookup"><span data-stu-id="fcc71-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="fcc71-180">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="fcc71-180">To execute the query</span></span>

1. <span data-ttu-id="fcc71-181">Wpisz lub wklej następujący kod na końcu `Sub Main` metody (po opisie zapytania):</span><span class="sxs-lookup"><span data-stu-id="fcc71-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. <span data-ttu-id="fcc71-182">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcc71-182">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fcc71-183">Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów w temacie [uczenie się według przewodników](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="fcc71-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="fcc71-184">W oknie komunikatu zostanie wyświetlona lista sześciu klientów.</span><span class="sxs-lookup"><span data-stu-id="fcc71-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="fcc71-185">W oknie konsoli jest wyświetlany wygenerowany kod SQL.</span><span class="sxs-lookup"><span data-stu-id="fcc71-185">The Console window displays the generated SQL code.</span></span>

3. <span data-ttu-id="fcc71-186">Kliknij przycisk **OK** , aby odrzucić okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-186">Click **OK** to dismiss the message box.</span></span>

     <span data-ttu-id="fcc71-187">Aplikacja zostanie zamknięta.</span><span class="sxs-lookup"><span data-stu-id="fcc71-187">The application closes.</span></span>

4. <span data-ttu-id="fcc71-188">Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="fcc71-188">On the **File** menu, click **Save All**.</span></span>

     <span data-ttu-id="fcc71-189">Ta aplikacja będzie potrzebna w przypadku kontynuowania następnego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="fcc71-189">You will need this application if you continue with the next walkthrough.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcc71-190">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fcc71-190">Next Steps</span></span>

<span data-ttu-id="fcc71-191">[Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) ) tematu kontynuuje się w przypadku zakończenia tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="fcc71-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="fcc71-192">Instruktaż dotyczący wykonywania zapytań w relacjach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokazuje, jak można wykonywać zapytania między tabelami, podobnie jak w przypadku *sprzężeń* w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fcc71-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="fcc71-193">Jeśli chcesz wykonać zapytania dotyczące instrukcji dotyczących relacji, pamiętaj, aby zapisać rozwiązanie dla przewodnika, który właśnie został ukończony, co jest wymaganiem wstępnym.</span><span class="sxs-lookup"><span data-stu-id="fcc71-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc71-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcc71-194">See also</span></span>

- [<span data-ttu-id="fcc71-195">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="fcc71-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
