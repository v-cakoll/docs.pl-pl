---
title: 'Instrukcje: Zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 5ccd71d93185f9478f6720419369df713d590c39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334942"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="d6227-102">Instrukcje: Zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6227-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="d6227-103">Language-Integrated Query (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="d6227-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="d6227-104">Domyślnie zapytania LINQ zwracają listę obiektów jako typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="d6227-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="d6227-105">Można również określić, że zapytanie zwraca listę określonego typu przy użyciu `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d6227-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="d6227-106">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania względem bazy danych programu SQL Server i projektami wyniki jako określonego typu nazwanego.</span><span class="sxs-lookup"><span data-stu-id="d6227-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="d6227-107">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d6227-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="d6227-108">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d6227-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d6227-109">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="d6227-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d6227-110">Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d6227-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d6227-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="d6227-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="d6227-112">W programie Visual Studio, otwórz **Eksploratora serwera**/**Eksplorator bazy danych** , klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="d6227-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="d6227-113">Kliknij prawym przyciskiem myszy **połączeń danych** w **Eksploratora serwera**/**Eksplorator bazy danych** a następnie kliknij przycisk **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="d6227-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="d6227-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d6227-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d6227-115">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d6227-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="d6227-116">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d6227-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d6227-117">Wybierz pozycję Visual Basic **aplikacja interfejsu Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="d6227-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="d6227-118">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d6227-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d6227-119">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="d6227-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="d6227-120">Nadaj plikowi nazwę `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="d6227-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d6227-121">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d6227-121">Click **Add**.</span></span> <span data-ttu-id="d6227-122">Zostanie otwarty plik northwind.dbml Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="d6227-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="d6227-123">Aby dodać tabele do zapytania O/R Designer</span><span class="sxs-lookup"><span data-stu-id="d6227-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="d6227-124">W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d6227-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d6227-125">Rozwiń **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="d6227-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="d6227-126">Po zamknięciu O/R Designer, możesz otworzyć go ponownie, klikając dwukrotnie plik northwind.dbml, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d6227-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="d6227-127">Kliknij tabelę klientów i przeciągnij go do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="d6227-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="d6227-128">Projektant tworzy nową `Customer` obiektu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d6227-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="d6227-129">Można poddawać projekcji wynik kwerendy w postaci `Customer` typu lub jako typ, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="d6227-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="d6227-130">W tym przykładzie utworzysz nowy typ w dalszej części procedury i projektu jako typu wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="d6227-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="d6227-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="d6227-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="d6227-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d6227-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="d6227-133">Aby dodać kod do wykonywania zapytań bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="d6227-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="d6227-134">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza Windows do projektu formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="d6227-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="d6227-135">Kliknij dwukrotnie Form1, aby zmodyfikować klasy Form1.</span><span class="sxs-lookup"><span data-stu-id="d6227-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="d6227-136">Po `End Class` instrukcji Form1 klasy, Dodaj następujący kod, aby utworzyć `CustomerInfo` typu do przechowywania wyników zapytania dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="d6227-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="d6227-137">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodano <xref:System.Data.Linq.DataContext> obiektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="d6227-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="d6227-138">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel i uzyskiwać dostęp do poszczególnych obiektów i kolekcji, dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d6227-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="d6227-139"><xref:System.Data.Linq.DataContext> Obiektu dla Twojego projektu jest nazwany na podstawie nazwy pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="d6227-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="d6227-140">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d6227-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d6227-141">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="d6227-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="d6227-142">W `Load` zdarzeń klasy Form1, Dodaj następujący kod, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="d6227-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="d6227-143">`Select` Klauzuli zapytania zostanie utworzony nowy `CustomerInfo` typu zamiast typu anonimowego dla każdego elementu wyniku kwerendy.</span><span class="sxs-lookup"><span data-stu-id="d6227-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="d6227-144">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="d6227-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6227-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6227-145">See also</span></span>

- [<span data-ttu-id="d6227-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="d6227-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d6227-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d6227-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d6227-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d6227-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d6227-149">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="d6227-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
