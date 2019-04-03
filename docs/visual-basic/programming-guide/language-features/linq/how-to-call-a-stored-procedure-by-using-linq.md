---
title: 'Instrukcje: Wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 2d05d43ae8f9b93fd3e5e405bb7ff0d59832e830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823353"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="0a12b-102">Instrukcje: Wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a12b-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="0a12b-103">Language-Integrated Query (LINQ) ułatwia dostęp do informacji z bazy danych, łącznie z procedurami obiektów, takich jak przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0a12b-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="0a12b-104">Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę składowaną w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0a12b-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="0a12b-105">Przykład pokazuje sposób wywoływania dwie różne procedury składowane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0a12b-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="0a12b-106">Każda procedura zwraca wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="0a12b-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="0a12b-107">Jednej procedury pobiera parametry wejściowe, a inne procedury nie przyjmuje parametrów.</span><span class="sxs-lookup"><span data-stu-id="0a12b-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="0a12b-108">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a12b-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="0a12b-109">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="0a12b-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="0a12b-110">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="0a12b-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="0a12b-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="0a12b-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="0a12b-112">W programie Visual Studio, otwórz **Eksploratora serwera**/**Eksplorator bazy danych** , klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="0a12b-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="0a12b-113">Kliknij prawym przyciskiem myszy **połączeń danych** w **Eksploratora serwera**/**Eksplorator bazy danych** a następnie kliknij przycisk **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="0a12b-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="0a12b-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a12b-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="0a12b-115">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a12b-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="0a12b-116">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="0a12b-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="0a12b-117">Wybierz pozycję Visual Basic **aplikacja interfejsu Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="0a12b-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="0a12b-118">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="0a12b-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="0a12b-119">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="0a12b-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="0a12b-120">Nadaj plikowi nazwę `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="0a12b-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="0a12b-121">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="0a12b-121">Click **Add**.</span></span> <span data-ttu-id="0a12b-122">Zostanie otwarty plik northwind.dbml Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="0a12b-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="0a12b-123">Aby dodać procedur składowanych do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="0a12b-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="0a12b-124">W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a12b-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="0a12b-125">Rozwiń **procedur składowanych** folderu.</span><span class="sxs-lookup"><span data-stu-id="0a12b-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="0a12b-126">Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="0a12b-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="0a12b-127">Kliknij przycisk **sprzedaż według roku** procedury składowanej i przeciągnij go do prawego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="0a12b-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="0a12b-128">Kliknij przycisk **dziesięć najbardziej kosztowne produktów** procedury składowanej przeciągnij go do prawego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="0a12b-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="0a12b-129">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="0a12b-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="0a12b-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="0a12b-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="0a12b-131">Aby dodać kod, aby wyświetlić wyniki procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="0a12b-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="0a12b-132">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="0a12b-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="0a12b-133">Kliknij dwukrotnie Form1, aby dodać kod do jego `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0a12b-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="0a12b-134">Po dodaniu procedur składowanych do projektanta O/R designer dodano <xref:System.Data.Linq.DataContext> obiektu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="0a12b-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="0a12b-135">Ten obiekt zawiera kod, który musi mieć, aby dostęp do tych procedur.</span><span class="sxs-lookup"><span data-stu-id="0a12b-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="0a12b-136"><xref:System.Data.Linq.DataContext> Obiektu dla projektu jest nazwany na podstawie nazwy pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="0a12b-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="0a12b-137">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="0a12b-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="0a12b-138">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i wywołanie metody procedury składowanej określony przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="0a12b-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="0a12b-139">Aby powiązać <xref:System.Windows.Forms.DataGridView> obiektu może być konieczne wymuszenie kwerenda do wykonania od razu, wywołując <xref:System.Linq.Enumerable.ToList%2A> metody w wynikach procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="0a12b-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="0a12b-140">Dodaj następujący kod do `Load` zdarzenie, aby wywołać jedną z procedur składowanych, widoczne jako metody dla kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="0a12b-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4.  <span data-ttu-id="0a12b-141">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="0a12b-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a12b-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a12b-142">See also</span></span>

- [<span data-ttu-id="0a12b-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="0a12b-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="0a12b-144">Zapytania</span><span class="sxs-lookup"><span data-stu-id="0a12b-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0a12b-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a12b-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="0a12b-146">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="0a12b-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="0a12b-147">Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="0a12b-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
