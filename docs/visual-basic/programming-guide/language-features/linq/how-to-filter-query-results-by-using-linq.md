---
title: 'Instrukcje: Filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 1250f2fe0ccd7661b9bc1986000143ec4a15a9f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053286"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="d4530-102">Instrukcje: Filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4530-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="d4530-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="d4530-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="d4530-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania względem bazy danych SQL Server i filtruje wyniki według określonej wartości przy użyciu `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d4530-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="d4530-105">Aby uzyskać więcej informacji, zobacz [klauzula WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d4530-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="d4530-106">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4530-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d4530-107">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d4530-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d4530-108">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d4530-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d4530-109">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="d4530-109">To create a connection to a database</span></span>

1. <span data-ttu-id="d4530-110">W programie Visual Studio Otwórz**Eksplorator bazy danych** **Eksplorator serwera**/, klikając pozycję **Eksplorator serwera**/**Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="d4530-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="d4530-111">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera**/**Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="d4530-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="d4530-112">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4530-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d4530-113">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d4530-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="d4530-114">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d4530-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d4530-115">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="d4530-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="d4530-116">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d4530-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d4530-117">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="d4530-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="d4530-118">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="d4530-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d4530-119">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d4530-119">Click **Add**.</span></span> <span data-ttu-id="d4530-120">Object Relational Designer (Projektant/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="d4530-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="d4530-121">Aby dodać tabele do zapytania do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="d4530-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="d4530-122">W**Eksplorator bazy danych** **Eksplorator serwera**/rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4530-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d4530-123">Rozwiń folder **tabele** .</span><span class="sxs-lookup"><span data-stu-id="d4530-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="d4530-124">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="d4530-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="d4530-125">Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="d4530-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="d4530-126">Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="d4530-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="d4530-127">Projektant tworzy nowe `Customer` i `Order` obiekty dla projektu.</span><span class="sxs-lookup"><span data-stu-id="d4530-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="d4530-128">Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4530-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="d4530-129">Na przykład technologia IntelliSense pokazuje, że `Customer` obiekt `Orders` ma właściwość dla wszystkich zamówień związanych z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="d4530-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="d4530-130">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="d4530-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="d4530-131">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d4530-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="d4530-132">Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="d4530-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="d4530-133">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="d4530-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="d4530-134">Kliknij dwukrotnie przycisk Form1, aby dodać kod do `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="d4530-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="d4530-135">Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="d4530-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="d4530-136">Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel, oprócz pojedynczych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d4530-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="d4530-137"><xref:System.Data.Linq.DataContext> Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="d4530-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="d4530-138">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d4530-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="d4530-139">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="d4530-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="d4530-140">Dodaj następujący kod do `Load` zdarzenia, aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="d4530-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="d4530-141">Zapytanie filtruje wyniki i zwraca tylko klientów, którzy znajdują się `London`w.</span><span class="sxs-lookup"><span data-stu-id="d4530-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="d4530-142">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="d4530-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="d4530-143">Poniżej znajdują się inne filtry, które można wypróbować.</span><span class="sxs-lookup"><span data-stu-id="d4530-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="d4530-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4530-144">See also</span></span>

- [<span data-ttu-id="d4530-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="d4530-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d4530-146">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d4530-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d4530-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d4530-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d4530-148">Metody DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="d4530-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
