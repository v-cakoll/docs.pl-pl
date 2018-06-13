---
title: 'Wskazówki: Prosty Model obiektów i kwerendy (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 2c2529c828c0b02ec2f53c7ea899bbe728ba88d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362367"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="14bd0-102">Wskazówki: Prosty Model obiektów i kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="14bd0-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="14bd0-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza z minimalnym złożoności.</span><span class="sxs-lookup"><span data-stu-id="14bd0-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="14bd0-104">Utworzy klasę jednostki, która modele tabeli klientów Northwind przykładowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="14bd0-105">Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="14bd0-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="14bd0-106">Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić Pokaż [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia.</span><span class="sxs-lookup"><span data-stu-id="14bd0-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="14bd0-107">Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do utworzenia obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="14bd0-108">W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="14bd0-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="14bd0-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="14bd0-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="14bd0-110">W tym przewodniku zastosowano dedykowanych folderów ("c:\linqtest5") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="14bd0-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="14bd0-111">Utwórz ten folder przed rozpoczęciem przewodnika.</span><span class="sxs-lookup"><span data-stu-id="14bd0-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="14bd0-112">W tym przewodniku wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="14bd0-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="14bd0-113">Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14bd0-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="14bd0-114">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="14bd0-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="14bd0-115">Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="14bd0-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="14bd0-116">Omówienie</span><span class="sxs-lookup"><span data-stu-id="14bd0-116">Overview</span></span>  
 <span data-ttu-id="14bd0-117">Ten przewodnik obejmuje sześć głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="14bd0-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="14bd0-118">Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14bd0-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="14bd0-119">Mapowania klasy tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="14bd0-120">Wyznaczenie właściwości klasy do reprezentowania kolumnach bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="14bd0-121">Określanie połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="14bd0-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="14bd0-122">Tworzenie prostego zapytania do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="14bd0-123">Wykonywanie zapytania i obserwowania wyniki.</span><span class="sxs-lookup"><span data-stu-id="14bd0-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="14bd0-124">Tworzenie składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="14bd0-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="14bd0-125">W tym zadaniu pierwszego tworzenia rozwiązania Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="14bd0-126">Aby utworzyć składnika LINQ to SQL rozwiązania</span><span class="sxs-lookup"><span data-stu-id="14bd0-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="14bd0-127">W programie Visual Studio **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="14bd0-128">W **typy projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="14bd0-129">W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="14bd0-130">W **nazwa** wpisz **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="14bd0-131">W **lokalizacji** upewnij się, którym chcesz przechowywać pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="14bd0-132">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="14bd0-133">Dodawanie odwołań LINQ i dyrektywy</span><span class="sxs-lookup"><span data-stu-id="14bd0-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="14bd0-134">W tym przewodniku zastosowano zestawy, które nie mogą być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="14bd0-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="14bd0-135">Jeśli System.Data.Linq nie jest wymieniony jako odwołanie do projektu (rozwiń **odwołania** w węźle **Eksploratora rozwiązań**), dodaj ją, zgodnie z objaśnieniem w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="14bd0-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="14bd0-136">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="14bd0-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="14bd0-137">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="14bd0-138">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="14bd0-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="14bd0-139">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="14bd0-140">Dodaj następujące dyrektywy w górnej części **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="14bd0-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="14bd0-141">Mapowanie klasę do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="14bd0-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="14bd0-142">W tym kroku Utwórz klasę i mapowanie go do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="14bd0-143">Taka klasa jest określane jako *klasy jednostka*.</span><span class="sxs-lookup"><span data-stu-id="14bd0-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="14bd0-144">Należy pamiętać, że mapowanie odbywa się po prostu dodając <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="14bd0-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="14bd0-146">Aby utworzyć klasę jednostki i mapowanie go do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="14bd0-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="14bd0-147">Wpisz lub wklej następujący kod do pliku Program.cs bezpośrednio nad `Program` deklaracji klasy:</span><span class="sxs-lookup"><span data-stu-id="14bd0-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="14bd0-148">Wyznaczenie właściwości klasy do reprezentowania kolumnach bazy danych</span><span class="sxs-lookup"><span data-stu-id="14bd0-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="14bd0-149">W tym kroku należy wykonać kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="14bd0-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="14bd0-150">Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybut do wyznaczenia `CustomerID` i `City` właściwości w obiekcie klasy reprezentujące kolumn w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="14bd0-151">Możesz określić `CustomerID` właściwość jako kolumna klucza podstawowego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="14bd0-152">Możesz określić `_CustomerID` i `_City` pól dla prywatnych magazynu.</span><span class="sxs-lookup"><span data-stu-id="14bd0-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="14bd0-153"> można następnie przechowywać i pobierać wartości bezpośrednio, zamiast metody dostępu publicznego, które może obejmować logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="14bd0-153"> can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="14bd0-154">Do reprezentowania właściwości dwie kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="14bd0-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="14bd0-155">Wpisz lub wklej następujący kod do pliku Program.cs wewnątrz nawiasów klamrowych dla `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="14bd0-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="14bd0-156">Określanie połączenia z bazą danych Northwind</span><span class="sxs-lookup"><span data-stu-id="14bd0-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="14bd0-157">W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektu do nawiązywania połączenia między struktury kodu na podstawie danych użytkownika i bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="14bd0-158"><xref:System.Data.Linq.DataContext> Jest głównym kanału, za pomocą którego możesz pobrać obiektów z bazy danych i przesyłanie zmian.</span><span class="sxs-lookup"><span data-stu-id="14bd0-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="14bd0-159">Deklarować także `Table<Customer>` do działania jako logiczne, typu tabeli dla zapytań względem tabeli klientów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="14bd0-160">Utworzysz i wykonaj następujące kwerendy w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="14bd0-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="14bd0-161">Aby określić połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="14bd0-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="14bd0-162">Wpisz lub wklej następujący kod do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="14bd0-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="14bd0-163">Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest5.</span><span class="sxs-lookup"><span data-stu-id="14bd0-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="14bd0-164">Aby uzyskać więcej informacji zobacz sekcję wymagań wstępnych we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="14bd0-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="14bd0-165">Tworzenie prostego zapytania</span><span class="sxs-lookup"><span data-stu-id="14bd0-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="14bd0-166">W tym kroku możesz utworzyć zapytanie w celu określenia, którzy klienci tabeli bazy danych znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="14bd0-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="14bd0-167">Kod zapytania w tym kroku opisano tylko zapytania.</span><span class="sxs-lookup"><span data-stu-id="14bd0-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="14bd0-168">Nie wykonać go.</span><span class="sxs-lookup"><span data-stu-id="14bd0-168">It does not execute it.</span></span> <span data-ttu-id="14bd0-169">Takie podejście jest nazywany *odroczonego wykonania*.</span><span class="sxs-lookup"><span data-stu-id="14bd0-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="14bd0-170">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="14bd0-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="14bd0-171">Należy również produktów wyjściowych dziennika do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="14bd0-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="14bd0-172">Ta funkcja rejestrowania (który korzysta z <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne w debugowaniu i w określeniu, czy polecenia wysyłane do bazy danych dokładnie reprezentować zapytania.</span><span class="sxs-lookup"><span data-stu-id="14bd0-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="14bd0-173">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="14bd0-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="14bd0-174">Wpisz lub wklej następujący kod do `Main` metody po `Table<Customer>` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="14bd0-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="14bd0-175">Wykonywanie zapytania</span><span class="sxs-lookup"><span data-stu-id="14bd0-175">Executing the Query</span></span>  
 <span data-ttu-id="14bd0-176">W tym kroku faktycznie wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="14bd0-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="14bd0-177">Wyrażenia zapytań, utworzone w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="14bd0-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="14bd0-178">Jeśli rozpoczniesz `foreach` iteracji, wykonywania polecenia SQL z bazą danych i obiektów jest zmaterializowany.</span><span class="sxs-lookup"><span data-stu-id="14bd0-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="14bd0-179">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="14bd0-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="14bd0-180">Wpisz lub wklej następujący kod na końcu `Main` — metoda (po opis kwerendy).</span><span class="sxs-lookup"><span data-stu-id="14bd0-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="14bd0-181">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="14bd0-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="14bd0-182">Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [uczenia przez wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="14bd0-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="14bd0-183">Wyniki zapytania w oknie konsoli powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="14bd0-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="14bd0-184">Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="14bd0-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="14bd0-185">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="14bd0-185">Next Steps</span></span>  
 <span data-ttu-id="14bd0-186">[Wskazówki: wykonywanie zapytania na relacje (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) temat będzie kontynuowane, gdy kończy się w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="14bd0-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="14bd0-187">Przedstawia wskazówki zapytania w relacji jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można zbadać między tabelami, podobnie jak *sprzężenia* relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="14bd0-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="14bd0-188">Jeśli chcesz wykonać wskazówki zapytania w relacji, upewnij się zapisać rozwiązanie, aby uzyskać wskazówki, który właśnie został ukończony, które jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="14bd0-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bd0-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14bd0-189">See Also</span></span>  
 [<span data-ttu-id="14bd0-190">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="14bd0-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
