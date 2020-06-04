---
title: 'Instrukcje: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 8be585c3e11bc3637b2dd1cfaf3437620aa2ba09
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405020"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="f5459-102">Porady: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5459-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="f5459-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="f5459-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="f5459-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację wykonującą zapytania względem bazy danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f5459-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="f5459-105">Przykład zlicza, sumuje i uśrednia wyniki przy użyciu `Aggregate` `Group By` klauzul i.</span><span class="sxs-lookup"><span data-stu-id="f5459-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="f5459-106">Aby uzyskać więcej informacji, zobacz [klauzula agregująca](../../../language-reference/queries/aggregate-clause.md) i [klauzula GROUP by](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f5459-106">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="f5459-107">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5459-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="f5459-108">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f5459-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="f5459-109">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="f5459-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="f5459-110">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="f5459-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="f5459-111">W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="f5459-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="f5459-112">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="f5459-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="f5459-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5459-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="f5459-114">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f5459-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="f5459-115">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f5459-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="f5459-116">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="f5459-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="f5459-117">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f5459-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="f5459-118">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="f5459-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="f5459-119">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="f5459-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="f5459-120">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f5459-120">Click **Add**.</span></span> <span data-ttu-id="f5459-121">Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="f5459-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="f5459-122">Aby dodać tabele do zapytania do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="f5459-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="f5459-123">W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="f5459-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="f5459-124">Rozwiń folder **tabele** .</span><span class="sxs-lookup"><span data-stu-id="f5459-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="f5459-125">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="f5459-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="f5459-126">Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="f5459-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="f5459-127">Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="f5459-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="f5459-128">Projektant tworzy nowe `Customer` i `Order` obiekty dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f5459-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="f5459-129">Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f5459-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="f5459-130">Na przykład technologia IntelliSense pokazuje, że `Customer` obiekt ma `Orders` Właściwość dla wszystkich zamówień związanych z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="f5459-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="f5459-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="f5459-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="f5459-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="f5459-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="f5459-133">Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="f5459-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="f5459-134">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="f5459-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="f5459-135">Kliknij dwukrotnie przycisk Form1, aby dodać kod do `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="f5459-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="f5459-136">Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f5459-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="f5459-137">Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel i uzyskać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f5459-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="f5459-138"><xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="f5459-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="f5459-139">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="f5459-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="f5459-140">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="f5459-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="f5459-141">Dodaj następujący kod do zdarzenia, `Load` Aby wykonać zapytanie dotyczące tabel, które są ujawniane jako właściwości wartości <xref:System.Data.Linq.DataContext> Liczba, suma i średni wynik.</span><span class="sxs-lookup"><span data-stu-id="f5459-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="f5459-142">Przykład używa `Aggregate` klauzuli do zapytania dla pojedynczego wyniku, a `Group By` klauzula, aby wyświetlić średnią dla zgrupowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="f5459-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="f5459-143">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="f5459-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5459-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5459-144">See also</span></span>

- [<span data-ttu-id="f5459-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="f5459-145">LINQ</span></span>](index.md)
- [<span data-ttu-id="f5459-146">Zapytania</span><span class="sxs-lookup"><span data-stu-id="f5459-146">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="f5459-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f5459-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="f5459-148">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="f5459-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="f5459-149">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="f5459-149">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="f5459-150">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="f5459-150">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
