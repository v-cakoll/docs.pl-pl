---
title: "Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bb7b970d42a44ad925883b7a935aae386b1f1d5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="cff23-102">Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cff23-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="cff23-103">Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do informacji z bazy danych, łącznie z bazy danych obiektów, takich jak przechowywane procedury.</span><span class="sxs-lookup"><span data-stu-id="cff23-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="cff23-104">Poniższy przykład przedstawia sposób tworzenia aplikacji, która wywołuje procedurę przechowywaną w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cff23-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="cff23-105">Przykład przedstawia sposób wywołania dwie różne procedury przechowywanej w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="cff23-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="cff23-106">Każdej procedury zwraca wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="cff23-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="cff23-107">Jednej procedury przyjmuje parametry wejściowe i inne procedury nie przyjmuje parametry.</span><span class="sxs-lookup"><span data-stu-id="cff23-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="cff23-108">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cff23-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="cff23-109">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cff23-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="cff23-110">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="cff23-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="cff23-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="cff23-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="cff23-112">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="cff23-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="cff23-113">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="cff23-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="cff23-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cff23-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="cff23-115">Aby dodać projekt, który zawiera LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="cff23-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="cff23-116">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="cff23-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="cff23-117">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="cff23-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="cff23-118">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="cff23-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="cff23-119">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="cff23-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="cff23-120">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="cff23-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="cff23-121">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="cff23-121">Click **Add**.</span></span> <span data-ttu-id="cff23-122">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla pliku northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="cff23-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="cff23-123">Aby dodać procedur składowanych do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="cff23-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="cff23-124">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="cff23-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="cff23-125">Rozwiń węzeł **procedur składowanych** folderu.</span><span class="sxs-lookup"><span data-stu-id="cff23-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="cff23-126">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="cff23-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="cff23-127">Kliknij przycisk **sprzedaży przez rok** procedury składowanej i przeciągnij go w okienku po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="cff23-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="cff23-128">Kliknij przycisk **10 najbardziej kosztowne produktów** procedury składowanej przeciągnij go w okienku po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="cff23-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="cff23-129">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="cff23-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="cff23-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="cff23-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="cff23-131">Aby dodać kod, aby wyświetlić wyniki procedury składowane</span><span class="sxs-lookup"><span data-stu-id="cff23-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="cff23-132">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="cff23-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="cff23-133">Kliknij dwukrotnie Form1, aby dodać kod, aby jego `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cff23-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="cff23-134">Po dodaniu procedur składowanych do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu.</span><span class="sxs-lookup"><span data-stu-id="cff23-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="cff23-135">Ten obiekt zawiera kod, który jest potrzebny dostęp do tych procedur.</span><span class="sxs-lookup"><span data-stu-id="cff23-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="cff23-136"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="cff23-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="cff23-137">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="cff23-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="cff23-138">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i wywołanie metody procedury składowanej określony przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="cff23-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="cff23-139">Aby powiązać <xref:System.Windows.Forms.DataGridView> obiektów, może zajść potrzeba wymuszenia zapytanie, aby natychmiast wykonać przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> metody w wynikach procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="cff23-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="cff23-140">Dodaj następujący kod do `Load` zdarzeń do wywołania jedną z procedur składowanych udostępniony jako metody dla kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="cff23-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  <span data-ttu-id="cff23-141">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="cff23-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff23-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cff23-142">See Also</span></span>  
 [<span data-ttu-id="cff23-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="cff23-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="cff23-144">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cff23-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="cff23-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cff23-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="cff23-146">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="cff23-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="cff23-147">Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="cff23-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
