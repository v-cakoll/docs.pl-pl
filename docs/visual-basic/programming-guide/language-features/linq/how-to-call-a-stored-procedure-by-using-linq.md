---
title: 'Instrukcje: wywoływanie procedury składowanej przy użyciu LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345027"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="62116-102">Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62116-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="62116-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych, takich jak obiekty bazy danych, takie jak procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="62116-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="62116-104">Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę przechowywaną w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="62116-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="62116-105">Przykład pokazuje, jak wywoływać dwie różne procedury składowane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="62116-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="62116-106">Każda procedura zwraca wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="62116-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="62116-107">Jedna procedura przyjmuje parametry wejściowe, a druga procedura nie przyjmuje parametrów.</span><span class="sxs-lookup"><span data-stu-id="62116-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="62116-108">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="62116-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="62116-109">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="62116-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="62116-110">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="62116-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="62116-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="62116-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="62116-112">W programie Visual Studio Otwórz **Eksplorator serwera**/**Eksplorator bazy danych** , klikając pozycję **Eksplorator serwera**/**Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="62116-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="62116-113">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera**/**Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="62116-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="62116-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="62116-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="62116-115">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="62116-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="62116-116">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="62116-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="62116-117">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="62116-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="62116-118">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="62116-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="62116-119">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="62116-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="62116-120">Nadaj plikowi nazwę `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="62116-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="62116-121">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="62116-121">Click **Add**.</span></span> <span data-ttu-id="62116-122">Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="62116-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="62116-123">Aby dodać procedury składowane do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="62116-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="62116-124">W **Eksplorator serwera**/**Eksplorator bazy danych**rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="62116-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="62116-125">Rozwiń folder **procedury składowane** .</span><span class="sxs-lookup"><span data-stu-id="62116-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="62116-126">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="62116-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="62116-127">Kliknij procedurę składowaną **sprzedaż według roku** i przeciągnij ją do okienka po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="62116-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="62116-128">Kliknij **dziesięć najbardziej kosztowne** procedury przechowywane produkty przeciągnij ją do okienka po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="62116-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="62116-129">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="62116-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="62116-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="62116-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="62116-131">Aby dodać kod, aby wyświetlić wyniki procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="62116-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="62116-132">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.DataGridView> do domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="62116-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="62116-133">Kliknij dwukrotnie przycisk Form1, aby dodać kod do jego zdarzenia `Load`.</span><span class="sxs-lookup"><span data-stu-id="62116-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="62116-134">Po dodaniu procedur składowanych do projektanta O/R Projektant dodał obiekt <xref:System.Data.Linq.DataContext> dla projektu.</span><span class="sxs-lookup"><span data-stu-id="62116-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="62116-135">Ten obiekt zawiera kod, który musi być wymagany, aby uzyskać dostęp do tych procedur.</span><span class="sxs-lookup"><span data-stu-id="62116-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="62116-136">Obiekt <xref:System.Data.Linq.DataContext> dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="62116-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="62116-137">Dla tego projektu obiekt <xref:System.Data.Linq.DataContext> ma nazwę `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="62116-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="62116-138">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i wywoływać metody procedury składowanej określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="62116-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="62116-139">Aby powiązać z obiektem <xref:System.Windows.Forms.DataGridView>, może być konieczne wymuszenie natychmiastowego wykonania zapytania przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> na wynikach procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="62116-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="62116-140">Dodaj następujący kod do zdarzenia `Load`, aby wywołać jedną z procedur składowanych dostępnych jako metody dla kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="62116-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="62116-141">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="62116-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62116-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62116-142">See also</span></span>

- [<span data-ttu-id="62116-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="62116-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="62116-144">Zapytania</span><span class="sxs-lookup"><span data-stu-id="62116-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="62116-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="62116-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="62116-146">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="62116-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="62116-147">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="62116-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
