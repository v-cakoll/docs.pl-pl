---
title: 'Porady: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ (Visual Basic)'
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
ms.openlocfilehash: 7c56fadfe722f8aaf236fb68e699c9d4d2889924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="4041a-102">Porady: zliczanie, sumowanie, lub uśrednianie danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4041a-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="4041a-103">Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="4041a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="4041a-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4041a-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="4041a-105">Próbki zlicza sumuje i oblicza średnią wyniki za pomocą `Aggregate` i `Group By` klauzul.</span><span class="sxs-lookup"><span data-stu-id="4041a-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="4041a-106">Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4041a-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="4041a-107">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4041a-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4041a-108">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4041a-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="4041a-109">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4041a-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4041a-110">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="4041a-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="4041a-111">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="4041a-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="4041a-112">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="4041a-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="4041a-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4041a-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4041a-114">Aby dodać projekt, który zawiera LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="4041a-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="4041a-115">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4041a-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4041a-116">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="4041a-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="4041a-117">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4041a-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4041a-118">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="4041a-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="4041a-119">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="4041a-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4041a-120">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4041a-120">Click **Add**.</span></span> <span data-ttu-id="4041a-121">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="4041a-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="4041a-122">Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="4041a-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="4041a-123">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4041a-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4041a-124">Rozwiń węzeł **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="4041a-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4041a-125">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4041a-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="4041a-126">Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="4041a-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="4041a-127">Tabela zamówienia kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="4041a-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4041a-128">Projektant tworzy nowy `Customer` i `Order` obiektów dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4041a-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="4041a-129">Zwróć uwagę, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4041a-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="4041a-130">Na przykład IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zleceń związane z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="4041a-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="4041a-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="4041a-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="4041a-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="4041a-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="4041a-133">Aby dodać kod, aby w bazie danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="4041a-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="4041a-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="4041a-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="4041a-135">Kliknij dwukrotnie Form1 kod, aby dodać `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="4041a-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="4041a-136">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4041a-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="4041a-137">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4041a-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="4041a-138"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="4041a-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4041a-139">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="4041a-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4041a-140">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4041a-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="4041a-141">Dodaj następujący kod do `Load` zdarzenie, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości z <xref:System.Data.Linq.DataContext> i liczba Suma i średnie wyniki.</span><span class="sxs-lookup"><span data-stu-id="4041a-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="4041a-142">W przykładzie użyto `Aggregate` klauzuli zapytania dla pojedynczego wyniku i `Group By` klauzuli pokazanie średnia dla pogrupowane wyników.</span><span class="sxs-lookup"><span data-stu-id="4041a-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="4041a-143">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="4041a-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4041a-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4041a-144">See Also</span></span>  
 [<span data-ttu-id="4041a-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="4041a-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="4041a-146">Zapytania</span><span class="sxs-lookup"><span data-stu-id="4041a-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="4041a-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4041a-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="4041a-148">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="4041a-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="4041a-149">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="4041a-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="4041a-150">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="4041a-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
