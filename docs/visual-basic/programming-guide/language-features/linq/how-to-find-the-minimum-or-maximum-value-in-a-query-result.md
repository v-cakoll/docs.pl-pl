---
title: "Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1af5b590310e966f7d27c02e2835a9e959f40c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="a7628-102">Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7628-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="a7628-103">Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="a7628-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="a7628-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a7628-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="a7628-105">Przykład określa wartości minimalną i maksymalną dla wyników za pomocą `Aggregate` i `Group By` klauzul.</span><span class="sxs-lookup"><span data-stu-id="a7628-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="a7628-106">Aby uzyskać więcej informacji, zobacz [Aggregate — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [grupy przez klauzuli](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a7628-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="a7628-107">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7628-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="a7628-108">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a7628-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="a7628-109">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="a7628-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="a7628-110">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="a7628-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="a7628-111">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="a7628-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="a7628-112">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="a7628-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="a7628-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7628-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="a7628-114">Aby dodać projekt, który zawiera LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="a7628-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="a7628-115">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a7628-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="a7628-116">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="a7628-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="a7628-117">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a7628-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="a7628-118">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="a7628-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="a7628-119">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="a7628-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="a7628-120">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a7628-120">Click **Add**.</span></span> <span data-ttu-id="a7628-121">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="a7628-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="a7628-122">Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="a7628-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="a7628-123">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7628-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="a7628-124">Rozwiń węzeł **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="a7628-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="a7628-125">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a7628-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="a7628-126">Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="a7628-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="a7628-127">Tabela zamówienia kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="a7628-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="a7628-128">Projektant tworzy nowy `Customer` i `Order` obiektów dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a7628-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="a7628-129">Zwróć uwagę, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a7628-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="a7628-130">Na przykład IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zleceń związane z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="a7628-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="a7628-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="a7628-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="a7628-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="a7628-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="a7628-133">Aby dodać kod, aby w bazie danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="a7628-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="a7628-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="a7628-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="a7628-135">Kliknij dwukrotnie Form1 kod, aby dodać `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="a7628-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="a7628-136">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a7628-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="a7628-137">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel, oprócz poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a7628-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="a7628-138"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="a7628-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="a7628-139">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a7628-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="a7628-140">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a7628-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="a7628-141">Dodaj następujący kod do `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a7628-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="a7628-142">Ten kod wysyła zapytanie do tabel, które są widoczne jako właściwości kontekstu danych i określa wartości minimalną i maksymalną dla wyników.</span><span class="sxs-lookup"><span data-stu-id="a7628-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="a7628-143">Przykład używa on `Aggregate` klauzuli zapytania dla pojedynczego wyniku i `Group By` klauzuli pokazanie średnia dla pogrupowane wyników.</span><span class="sxs-lookup"><span data-stu-id="a7628-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  <span data-ttu-id="a7628-144">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="a7628-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7628-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7628-145">See Also</span></span>  
 [<span data-ttu-id="a7628-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="a7628-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="a7628-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="a7628-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="a7628-148">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="a7628-148">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="a7628-149">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="a7628-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
