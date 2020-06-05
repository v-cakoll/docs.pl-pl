---
title: 'Instrukcje: wywoływanie procedury składowanej za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: b451642a16f36c4f7fd19c853fdfd2282f5bede5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405033"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="feab2-102">Porady: wywoływanie procedury przechowywanej za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feab2-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="feab2-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych, takich jak obiekty bazy danych, takie jak procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="feab2-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="feab2-104">Poniższy przykład pokazuje, jak utworzyć aplikację, która wywołuje procedurę przechowywaną w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="feab2-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="feab2-105">Przykład pokazuje, jak wywoływać dwie różne procedury składowane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="feab2-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="feab2-106">Każda procedura zwraca wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="feab2-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="feab2-107">Jedna procedura przyjmuje parametry wejściowe, a druga procedura nie przyjmuje parametrów.</span><span class="sxs-lookup"><span data-stu-id="feab2-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="feab2-108">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="feab2-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="feab2-109">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="feab2-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="feab2-110">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="feab2-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="feab2-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="feab2-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="feab2-112">W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="feab2-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="feab2-113">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="feab2-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="feab2-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="feab2-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="feab2-115">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="feab2-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="feab2-116">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="feab2-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="feab2-117">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="feab2-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="feab2-118">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="feab2-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="feab2-119">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="feab2-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="feab2-120">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="feab2-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="feab2-121">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="feab2-121">Click **Add**.</span></span> <span data-ttu-id="feab2-122">Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="feab2-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="feab2-123">Aby dodać procedury składowane do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="feab2-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="feab2-124">W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="feab2-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="feab2-125">Rozwiń folder **procedury składowane** .</span><span class="sxs-lookup"><span data-stu-id="feab2-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="feab2-126">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="feab2-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="feab2-127">Kliknij procedurę składowaną **sprzedaż według roku** i przeciągnij ją do okienka po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="feab2-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="feab2-128">Kliknij **dziesięć najbardziej kosztowne** procedury przechowywane produkty przeciągnij ją do okienka po prawej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="feab2-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="feab2-129">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="feab2-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="feab2-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="feab2-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="feab2-131">Aby dodać kod, aby wyświetlić wyniki procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="feab2-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="feab2-132">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="feab2-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="feab2-133">Kliknij dwukrotnie przycisk Form1, aby dodać kod do jego `Load` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="feab2-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="feab2-134">Po dodaniu procedur składowanych do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="feab2-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="feab2-135">Ten obiekt zawiera kod, który musi być wymagany, aby uzyskać dostęp do tych procedur.</span><span class="sxs-lookup"><span data-stu-id="feab2-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="feab2-136"><xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="feab2-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="feab2-137">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="feab2-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="feab2-138">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i wywołać metody procedury składowanej określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="feab2-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="feab2-139">Aby powiązać z <xref:System.Windows.Forms.DataGridView> obiektem, może być konieczne wymuszenie natychmiastowego wykonania zapytania przez wywołanie <xref:System.Linq.Enumerable.ToList%2A> metody na wynikach procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="feab2-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="feab2-140">Dodaj następujący kod do zdarzenia, `Load` Aby wywołać jedną z procedur składowanych dostępnych jako metody dla kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="feab2-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="feab2-141">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="feab2-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feab2-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="feab2-142">See also</span></span>

- [<span data-ttu-id="feab2-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="feab2-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="feab2-144">Zapytania</span><span class="sxs-lookup"><span data-stu-id="feab2-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="feab2-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="feab2-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="feab2-146">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="feab2-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="feab2-147">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="feab2-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
