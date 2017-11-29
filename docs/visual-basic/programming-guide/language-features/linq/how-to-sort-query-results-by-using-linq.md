---
title: "Porady: sortowanie wyników zapytania za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c880924b8091d3af28f5353fec2083d635bb4078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="7c98e-102">Porady: sortowanie wyników zapytania za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c98e-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="7c98e-103">Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="7c98e-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="7c98e-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server i sortujące wyniki według wielu pól przy użyciu `Order By` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7c98e-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="7c98e-105">Porządek sortowania dla każdego pola można kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="7c98e-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="7c98e-106">Aby uzyskać więcej informacji, zobacz [klauzula Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7c98e-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="7c98e-107">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c98e-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="7c98e-108">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7c98e-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="7c98e-109">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="7c98e-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="7c98e-110">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="7c98e-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="7c98e-111">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="7c98e-112">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="7c98e-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="7c98e-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c98e-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="7c98e-114">Aby dodać projekt, który zawiera LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="7c98e-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="7c98e-115">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7c98e-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="7c98e-116">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="7c98e-117">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="7c98e-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7c98e-118">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="7c98e-119">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="7c98e-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="7c98e-120">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="7c98e-120">Click **Add**.</span></span> <span data-ttu-id="7c98e-121">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="7c98e-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="7c98e-122">Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="7c98e-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="7c98e-123">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c98e-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="7c98e-124">Rozwiń węzeł **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="7c98e-125">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7c98e-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="7c98e-126">Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="7c98e-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="7c98e-127">Tabela zamówienia kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="7c98e-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="7c98e-128">Projektant tworzy nowy `Customer` i `Order` obiektów dla projektu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="7c98e-129">Zwróć uwagę, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7c98e-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="7c98e-130">Na przykład IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zleceń związane z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="7c98e-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="7c98e-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="7c98e-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="7c98e-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="7c98e-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="7c98e-133">Aby dodać kod, aby w bazie danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="7c98e-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="7c98e-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="7c98e-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="7c98e-135">Kliknij dwukrotnie Form1 kod, aby dodać `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="7c98e-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="7c98e-136">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="7c98e-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="7c98e-137">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c98e-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="7c98e-138"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="7c98e-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="7c98e-139">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="7c98e-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="7c98e-140">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="7c98e-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="7c98e-141">Dodaj następujący kod do `Load` zdarzenia do tabel, które są widoczne jako właściwości kontekstu danych i sortowanie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="7c98e-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="7c98e-142">Zapytanie wyniki są sortowane według numerów zamówień klienta, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="7c98e-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="7c98e-143">Klienci, którzy mają taką samą liczbę zamówień są uporządkowane według nazwy firmy Rosnąco (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7c98e-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="7c98e-144">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="7c98e-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c98e-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c98e-145">See Also</span></span>  
 [<span data-ttu-id="7c98e-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="7c98e-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="7c98e-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="7c98e-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="7c98e-148">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="7c98e-148">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="7c98e-149">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="7c98e-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
