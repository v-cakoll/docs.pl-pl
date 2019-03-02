---
title: 'Instrukcje: Liczba, Sum lub uśrednianie danych za pomocą LINQ (Visual Basic)'
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
ms.openlocfilehash: 9ff57029768c89e584fd2d7381fd79e38fbed14f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203457"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="ddd08-102">Instrukcje: Liczba, Sum lub uśrednianie danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddd08-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="ddd08-103">Language-Integrated Query (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="ddd08-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="ddd08-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania względem bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ddd08-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="ddd08-105">Próbka jest liczona sumuje i średnie wyniki za pomocą `Aggregate` i `Group By` klauzul.</span><span class="sxs-lookup"><span data-stu-id="ddd08-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="ddd08-106">Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzulę](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ddd08-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="ddd08-107">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="ddd08-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="ddd08-108">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="ddd08-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="ddd08-109">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ddd08-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="ddd08-110">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="ddd08-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="ddd08-111">W programie Visual Studio, otwórz **Eksploratora serwera**/**Eksplorator bazy danych** , klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="ddd08-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ddd08-112">Kliknij prawym przyciskiem myszy **połączeń danych** w **Eksploratora serwera**/**Eksplorator bazy danych** a następnie kliknij przycisk **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="ddd08-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="ddd08-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="ddd08-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="ddd08-114">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ddd08-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="ddd08-115">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ddd08-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="ddd08-116">Wybierz pozycję Visual Basic **aplikacja interfejsu Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="ddd08-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="ddd08-117">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ddd08-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="ddd08-118">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="ddd08-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="ddd08-119">Nadaj plikowi nazwę `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="ddd08-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="ddd08-120">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ddd08-120">Click **Add**.</span></span> <span data-ttu-id="ddd08-121">Zostanie otwarty plik northwind.dbml Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="ddd08-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="ddd08-122">Aby dodać tabele do zapytania O/R Designer</span><span class="sxs-lookup"><span data-stu-id="ddd08-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="ddd08-123">W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="ddd08-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="ddd08-124">Rozwiń **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="ddd08-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="ddd08-125">Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ddd08-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="ddd08-126">Kliknij tabelę klientów i przeciągnij go do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="ddd08-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="ddd08-127">Kliknij w tabeli zamówienia, a następnie przeciągnij go do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="ddd08-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="ddd08-128">Projektant tworzy nowe `Customer` i `Order` obiektów dla Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="ddd08-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="ddd08-129">Należy zauważyć, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ddd08-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="ddd08-130">Na przykład, IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zamówień związane z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="ddd08-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="ddd08-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="ddd08-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="ddd08-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="ddd08-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="ddd08-133">Aby dodać kod do wykonywania zapytań bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="ddd08-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="ddd08-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="ddd08-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="ddd08-135">Kliknij dwukrotnie Form1, aby dodać kod, aby `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="ddd08-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="ddd08-136">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodano <xref:System.Data.Linq.DataContext> obiektu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ddd08-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="ddd08-137">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji, dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ddd08-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="ddd08-138"><xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="ddd08-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="ddd08-139">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="ddd08-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="ddd08-140">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="ddd08-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="ddd08-141">Dodaj następujący kod do `Load` zdarzenie, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości usługi <xref:System.Data.Linq.DataContext> count, Suma i średniej dla otrzymanych wyników.</span><span class="sxs-lookup"><span data-stu-id="ddd08-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="ddd08-142">W przykładzie użyto `Aggregate` klauzuli do wykonywania zapytań w jeden wynik i `Group By` klauzuli, aby pokazać średnią dla pogrupowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ddd08-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4.  <span data-ttu-id="ddd08-143">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="ddd08-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd08-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddd08-144">See also</span></span>
- [<span data-ttu-id="ddd08-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="ddd08-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="ddd08-146">Zapytania</span><span class="sxs-lookup"><span data-stu-id="ddd08-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ddd08-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ddd08-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="ddd08-148">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="ddd08-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="ddd08-149">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="ddd08-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ddd08-150">Klauzula Group By</span><span class="sxs-lookup"><span data-stu-id="ddd08-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
