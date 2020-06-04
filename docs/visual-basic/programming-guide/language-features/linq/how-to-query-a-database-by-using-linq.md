---
title: 'Instrukcje: zapytanie dotyczące bazy danych za pomocą LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- query samples [LINQ]
- database querying [LINQ]
- queries [LINQ in Visual Basic], database querying
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: bcf5e9c3-a236-4399-9a7f-3991eca7cf56
ms.openlocfilehash: ad4744e1734fd968f610ec02b60814eadd3ebe9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404968"
---
# <a name="how-to-query-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="4fcf6-102">Porady: zapytanie dotyczące bazy danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fcf6-102">How to: Query a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="4fcf6-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="4fcf6-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację wykonującą zapytania względem bazy danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span>  
  
 <span data-ttu-id="4fcf6-105">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4fcf6-106">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="4fcf6-107">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4fcf6-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4fcf6-108">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="4fcf6-108">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="4fcf6-109">W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="4fcf6-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="4fcf6-110">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="4fcf6-111">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4fcf6-112">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4fcf6-112">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="4fcf6-113">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4fcf6-114">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="4fcf6-115">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4fcf6-116">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="4fcf6-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="4fcf6-117">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4fcf6-118">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-118">Click **Add**.</span></span> <span data-ttu-id="4fcf6-119">Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-119">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="4fcf6-120">Aby dodać tabele do zapytania do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="4fcf6-120">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="4fcf6-121">W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4fcf6-122">Rozwiń folder **tabele** .</span><span class="sxs-lookup"><span data-stu-id="4fcf6-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4fcf6-123">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-123">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="4fcf6-124">Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-124">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="4fcf6-125">Kliknij tabelę Orders (zamówienia) i przeciągnij ją do okienka po lewej stronie projektanta.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-125">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4fcf6-126">Projektant tworzy nowe `Customer` i `Order` obiekty dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-126">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="4fcf6-127">Zauważ, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-127">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="4fcf6-128">Na przykład technologia IntelliSense pokazuje, że `Customer` obiekt ma `Orders` Właściwość dla wszystkich zamówień związanych z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-128">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="4fcf6-129">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="4fcf6-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-130">Save your project.</span></span>  
  
## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="4fcf6-131">Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="4fcf6-131">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="4fcf6-132">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="4fcf6-133">Kliknij dwukrotnie przycisk Form1, aby dodać kod do `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-133">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="4fcf6-134">Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-134">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="4fcf6-135">Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel, oprócz pojedynczych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-135">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="4fcf6-136"><xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-136">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4fcf6-137">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="4fcf6-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4fcf6-138">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="4fcf6-139">Dodaj następujący kod do zdarzenia, `Load` Aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-139">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#3)]  
  
4. <span data-ttu-id="4fcf6-140">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="4fcf6-140">Press F5 to run your project and view the results.</span></span>  
  
5. <span data-ttu-id="4fcf6-141">Poniżej znajdują się dodatkowe zapytania, które można wypróbować:</span><span class="sxs-lookup"><span data-stu-id="4fcf6-141">Following are some additional queries that you can try:</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#4)]  
    [!code-vb[VbLINQToSQLHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form2.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4fcf6-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fcf6-142">See also</span></span>

- [<span data-ttu-id="4fcf6-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="4fcf6-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="4fcf6-144">Zapytania</span><span class="sxs-lookup"><span data-stu-id="4fcf6-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="4fcf6-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4fcf6-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="4fcf6-146">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="4fcf6-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
