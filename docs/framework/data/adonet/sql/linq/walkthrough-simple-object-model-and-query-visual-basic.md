---
title: 'Przewodnik: Prosty Model obiektu i zapytanie (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: c6d00271f412829cb8e030c2b9a338f73327977b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724177"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="8106a-102">Przewodnik: Prosty Model obiektu i zapytanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8106a-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="8106a-103">Ten przewodnik zawiera podstawowe end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenariusza minimalnej złożoności.</span><span class="sxs-lookup"><span data-stu-id="8106a-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="8106a-104">Utworzy klasę jednostki, który modeluje tabelę Klienci w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8106a-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="8106a-105">Spowoduje to utworzenie prostego zapytania do listy klientów, którzy znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="8106a-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="8106a-106">Ten przewodnik jest zorientowany kodu zgodnie z projektem, aby ułatwić wyświetlanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pojęcia.</span><span class="sxs-lookup"><span data-stu-id="8106a-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="8106a-107">Zwykle rzecz biorąc, należy użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="8106a-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="8106a-108">W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8106a-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8106a-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8106a-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="8106a-110">W tym przewodniku używa dedykowanego folder ("c:\linqtest") do przechowywania plików.</span><span class="sxs-lookup"><span data-stu-id="8106a-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="8106a-111">Przed rozpoczęciem instruktażu, należy utworzyć ten folder.</span><span class="sxs-lookup"><span data-stu-id="8106a-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="8106a-112">Ten poradnik wymaga przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8106a-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="8106a-113">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z witryny pobierania firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8106a-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="8106a-114">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8106a-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="8106a-115">Po pobraniu bazy danych, skopiuj plik do folderu c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="8106a-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8106a-116">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8106a-116">Overview</span></span>  
 <span data-ttu-id="8106a-117">Ten przewodnik składa się z sześciu głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="8106a-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="8106a-118">Tworzenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozwiązania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8106a-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="8106a-119">Mapowanie klasy do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="8106a-120">Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="8106a-121">Określenie połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="8106a-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="8106a-122">Tworzenie prostego zapytania do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="8106a-123">Wykonywanie zapytania i obserwowania wyniki.</span><span class="sxs-lookup"><span data-stu-id="8106a-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="8106a-124">Tworzenie składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8106a-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="8106a-125">W tym pierwszym zadaniu tworzyć rozwiązania programu Visual Studio, który zawiera niezbędne odwołania, aby skompilować i uruchomić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="8106a-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="8106a-126">Aby utworzyć składnika LINQ to SQL rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="8106a-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="8106a-127">Na **pliku** menu, kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="8106a-127">On the **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="8106a-128">W **typów projektów** okienku **nowy projekt** okno dialogowe, kliknij przycisk **języka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="8106a-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="8106a-129">W **szablony** okienku kliknij **aplikację Konsolową**.</span><span class="sxs-lookup"><span data-stu-id="8106a-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="8106a-130">W **nazwa** wpisz **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="8106a-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="8106a-131">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8106a-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="8106a-132">Dodawanie odwołania do zapytań LINQ i dyrektywy</span><span class="sxs-lookup"><span data-stu-id="8106a-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="8106a-133">W tym instruktażu wykorzystano zestawów, które nie mogą być instalowane domyślnie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8106a-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="8106a-134">Jeśli `System.Data.Linq` nie jest wymieniony jako odwołanie do projektu (kliknij **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** i rozwiń **odwołania** węzła), ją dodać, jak wyjaśniono w Poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="8106a-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="8106a-135">To add System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="8106a-135">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="8106a-136">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8106a-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="8106a-137">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**, kliknij zestaw System.Data.Linq, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8106a-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8106a-138">Zestaw został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="8106a-138">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="8106a-139">Również w **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET**przewiń i kliknij przestrzeń nazw System.Windows.Forms, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8106a-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8106a-140">Ten zestaw, który obsługuje okno komunikatu w instruktażu, jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="8106a-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4.  <span data-ttu-id="8106a-141">Dodaj następujące dyrektywy powyżej `Module1`:</span><span class="sxs-lookup"><span data-stu-id="8106a-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="8106a-142">Mapowanie klasy do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="8106a-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="8106a-143">W tym kroku, Utwórz klasę i mapowany do tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="8106a-144">Taka klasa jest określane jako *Klasa jednostki*.</span><span class="sxs-lookup"><span data-stu-id="8106a-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="8106a-145">Należy pamiętać, że mapowanie odbywa się przez dodanie <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8106a-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="8106a-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Właściwość określa nazwę tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="8106a-147">Aby utworzyć klasę jednostki i mapowany do tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="8106a-147">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="8106a-148">Wpisz lub wklej następujący kod bezpośrednio nad Module1.vb `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="8106a-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="8106a-149">Wyznaczanie właściwości klasy do reprezentowania kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="8106a-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="8106a-150">W tym kroku należy wykonać kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="8106a-150">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="8106a-151">Możesz użyć <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć `CustomerID` i `City` właściwości jednostki klasy, reprezentując kolumn w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="8106a-152">Możesz wyznaczyć `CustomerID` właściwości jako kolumna klucza podstawowego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="8106a-153">Możesz wyznaczyć `_CustomerID` i `_City` pól magazynu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="8106a-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8106a-154">można następnie przechowywać i pobierać wartości bezpośrednio, zamiast publiczne metody dostępu, które mogą obejmować logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="8106a-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="8106a-155">Do reprezentowania charakterystyki dwie kolumny bazy danych</span><span class="sxs-lookup"><span data-stu-id="8106a-155">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="8106a-156">Wpisz lub wklej następujący kod do Module1.vb tuż przed `End Class`:</span><span class="sxs-lookup"><span data-stu-id="8106a-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="8106a-157">Określanie połączenia z bazą danych Northwind</span><span class="sxs-lookup"><span data-stu-id="8106a-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="8106a-158">W tym kroku użyjesz <xref:System.Data.Linq.DataContext> obiektów do nawiązania połączenia między struktury danych w oparciu o kod użytkownika, a sama baza danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="8106a-159"><xref:System.Data.Linq.DataContext> Jest głównym kanał za pomocą którego pobieranie obiektów z bazy danych i przesyłanie zmian.</span><span class="sxs-lookup"><span data-stu-id="8106a-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="8106a-160">Można również zadeklarować `Table(Of Customer)` pełnić rolę w logiczne, wpisane tabeli zapytania względem tabeli Klienci w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="8106a-161">Utworzysz i wykonaj następujące zapytania w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="8106a-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="8106a-162">Aby określić połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="8106a-162">To specify the database connection</span></span>  
  
-   <span data-ttu-id="8106a-163">Wpisz lub wklej następujący kod do `Sub Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8106a-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="8106a-164">Należy pamiętać, że `northwnd.mdf` pliku zakłada, że w folderze linqtest.</span><span class="sxs-lookup"><span data-stu-id="8106a-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="8106a-165">Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne we wcześniejszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="8106a-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="8106a-166">Tworzenie prostego zapytania</span><span class="sxs-lookup"><span data-stu-id="8106a-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="8106a-167">W tym kroku utworzysz zapytanie w celu określenia, których klientów w tabeli Klienci bazy danych znajdują się w Londynie.</span><span class="sxs-lookup"><span data-stu-id="8106a-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="8106a-168">Kod zapytania w tym kroku opisano tylko zapytania.</span><span class="sxs-lookup"><span data-stu-id="8106a-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="8106a-169">Nie wykonuje on.</span><span class="sxs-lookup"><span data-stu-id="8106a-169">It does not execute it.</span></span> <span data-ttu-id="8106a-170">To podejście jest nazywane *wykonanie odroczone*.</span><span class="sxs-lookup"><span data-stu-id="8106a-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="8106a-171">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="8106a-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="8106a-172">Należy również wygenerować dziennika danych wyjściowych do wyświetlenia SQL polecenia, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje.</span><span class="sxs-lookup"><span data-stu-id="8106a-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="8106a-173">Ta funkcja rejestrowania (wykonującemu <xref:System.Data.Linq.DataContext.Log%2A>) jest przydatne podczas debugowania i określenie, że polecenia są wysyłane do bazy danych, dokładnie reprezentują zapytanie.</span><span class="sxs-lookup"><span data-stu-id="8106a-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="8106a-174">Aby utworzyć proste zapytanie</span><span class="sxs-lookup"><span data-stu-id="8106a-174">To create a simple query</span></span>  
  
-   <span data-ttu-id="8106a-175">Wpisz lub wklej następujący kod do `Sub Main` metody `Table(Of Customer)` deklaracji:</span><span class="sxs-lookup"><span data-stu-id="8106a-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="8106a-176">Wykonywanie zapytania</span><span class="sxs-lookup"><span data-stu-id="8106a-176">Executing the Query</span></span>  
 <span data-ttu-id="8106a-177">W tym kroku faktycznie wykonaj zapytanie.</span><span class="sxs-lookup"><span data-stu-id="8106a-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="8106a-178">Wyrażenia zapytań, który został utworzony w poprzednich krokach nie są oceniane, dopóki wyniki są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="8106a-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="8106a-179">Po rozpoczęciu `For Each` iteracji, za pomocą polecenia SQL jest wykonywane względem bazy danych i obiektów jest zmaterializowany.</span><span class="sxs-lookup"><span data-stu-id="8106a-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="8106a-180">Aby wykonać zapytanie</span><span class="sxs-lookup"><span data-stu-id="8106a-180">To execute the query</span></span>  
  
1.  <span data-ttu-id="8106a-181">Wpisz lub wklej następujący kod na końcu `Sub Main` metody (opis kwerendy):</span><span class="sxs-lookup"><span data-stu-id="8106a-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="8106a-182">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="8106a-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8106a-183">Jeśli aplikacja generuje błąd w czasie wykonywania, zobacz sekcję Rozwiązywanie problemów z [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="8106a-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="8106a-184">W oknie komunikatu Wyświetla listę sześcioma klientami.</span><span class="sxs-lookup"><span data-stu-id="8106a-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="8106a-185">W oknie konsoli zostaną wyświetlone wygenerowanego kodu SQL.</span><span class="sxs-lookup"><span data-stu-id="8106a-185">The Console window displays the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="8106a-186">Kliknij przycisk **OK** aby odrzucić okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8106a-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="8106a-187">Zamyka aplikację.</span><span class="sxs-lookup"><span data-stu-id="8106a-187">The application closes.</span></span>  
  
4.  <span data-ttu-id="8106a-188">Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="8106a-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="8106a-189">Należy tej aplikacji, jeśli będziesz korzystać z poniższych wskazówek.</span><span class="sxs-lookup"><span data-stu-id="8106a-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8106a-190">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8106a-190">Next Steps</span></span>  
 <span data-ttu-id="8106a-191">[Instruktażu: Querying w relacjach (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tematu będzie kontynuowane, gdy kończy się w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="8106a-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="8106a-192">Wykonywanie zapytań w relacjach instruktażu pokazano, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można wykonywanie zapytań względem tabel, podobnie jak *sprzężeń* relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8106a-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="8106a-193">Jeśli chcesz wykonać instrukcje przedstawione zapytań w relacjach, upewnij się zapisać rozwiązanie przewodnik, który właśnie został ukończony, który jest wymaganiem wstępnym.</span><span class="sxs-lookup"><span data-stu-id="8106a-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8106a-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8106a-194">See also</span></span>
- [<span data-ttu-id="8106a-195">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="8106a-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
