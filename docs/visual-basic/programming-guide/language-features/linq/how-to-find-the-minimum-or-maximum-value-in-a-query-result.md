---
title: 'Instrukcje: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ'
ms.date: 07/20/2015
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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112365"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="42623-102">Porady: znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42623-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="42623-103">Zintegrowana z językiem kwerenda (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="42623-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="42623-104">W poniższym przykładzie pokazano, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="42623-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="42623-105">Próbka określa minimalne i maksymalne wartości dla `Aggregate` `Group By` wyników przy użyciu i klauzul.</span><span class="sxs-lookup"><span data-stu-id="42623-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="42623-106">Aby uzyskać więcej informacji, zobacz [Klauzula agregująca](../../../../visual-basic/language-reference/queries/aggregate-clause.md) i [Klauzula grupy według](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="42623-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="42623-107">Przykłady w tym temacie użyć bazy danych Northwind przykład.</span><span class="sxs-lookup"><span data-stu-id="42623-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="42623-108">Jeśli ta baza danych nie jest zabezpieczone na komputerze deweloperskim, można ją pobrać z Centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42623-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="42623-109">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="42623-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="42623-110">Tworzenie połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="42623-110">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="42623-111">W programie Visual Studio otwórz**Eksploratora bazy danych** **Eksploratora**/serwerów, klikając polecenie**Eksplorator baz danych** **Eksploratora**/serwerów w menu **Widok.**</span><span class="sxs-lookup"><span data-stu-id="42623-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="42623-112">Kliknij prawym przyciskiem myszy pozycję **Połączenia danych** w Eksploratorze bazy danych **Eksploratora**/**serwerów,** a następnie kliknij polecenie **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="42623-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="42623-113">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="42623-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="42623-114">Aby dodać projekt zawierający linq do pliku SQL</span><span class="sxs-lookup"><span data-stu-id="42623-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="42623-115">W programie Visual Studio w menu **Plik** wskaż polecenie **Nowy,** a następnie kliknij polecenie **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="42623-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="42623-116">Jako typ projektu wybierz opcję Visual Basic **Windows Forms Application.**</span><span class="sxs-lookup"><span data-stu-id="42623-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="42623-117">W menu **Projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="42623-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="42623-118">Wybierz szablon elementu **LINQ do klas SQL.**</span><span class="sxs-lookup"><span data-stu-id="42623-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="42623-119">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="42623-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="42623-120">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="42623-120">Click **Add**.</span></span> <span data-ttu-id="42623-121">Projektant relacyjnego obiektu (O/R Designer) jest otwarty dla pliku northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="42623-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="42623-122">Dodawanie tabel do kwerendy do projektanta o/r</span><span class="sxs-lookup"><span data-stu-id="42623-122">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="42623-123">W/**Eksploratorze bazy danych** **Eksploratora serwerów**rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="42623-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="42623-124">Rozwiń folder **Tabele.**</span><span class="sxs-lookup"><span data-stu-id="42623-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="42623-125">Jeśli projektant o/r został zamknięty, można go ponownie otworzyć, klikając dwukrotnie dodany wcześniej plik northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="42623-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="42623-126">Kliknij tabelę Klienci i przeciągnij ją w lewe okienko projektanta.</span><span class="sxs-lookup"><span data-stu-id="42623-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="42623-127">Kliknij tabelę Zamówienia i przeciągnij ją w lewe okienko projektanta.</span><span class="sxs-lookup"><span data-stu-id="42623-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="42623-128">Projektant tworzy `Customer` nowe `Order` i obiekty dla projektu.</span><span class="sxs-lookup"><span data-stu-id="42623-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="42623-129">Należy zauważyć, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości podrzędne dla powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="42623-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="42623-130">Na przykład IntelliSense pokaże, `Customer` że `Orders` obiekt ma właściwość dla wszystkich zamówień związanych z tym klientem.</span><span class="sxs-lookup"><span data-stu-id="42623-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="42623-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="42623-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="42623-132">Zapisz swój projekt.</span><span class="sxs-lookup"><span data-stu-id="42623-132">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="42623-133">Dodaj kod, aby zbadać bazę danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="42623-133">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="42623-134">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślny formularz systemu Windows dla projektu Form1.</span><span class="sxs-lookup"><span data-stu-id="42623-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="42623-135">Kliknij dwukrotnie form1, aby `Load` dodać kod do zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="42623-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="42623-136">Po dodaniu tabel do projektanta O/R <xref:System.Data.Linq.DataContext> projektant dodał obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="42623-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="42623-137">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel, oprócz poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="42623-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="42623-138">Obiekt <xref:System.Data.Linq.DataContext> dla projektu ma nazwę na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="42623-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="42623-139">W przypadku tego <xref:System.Data.Linq.DataContext> projektu `northwindDataContext`obiekt nosi nazwę .</span><span class="sxs-lookup"><span data-stu-id="42623-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="42623-140">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i kwerendy tabel określonych przez Projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="42623-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="42623-141">Dodaj następujący kod `Load` do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="42623-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="42623-142">Ten kod wysyła kwerendy tabel, które są udostępniane jako właściwości kontekstu danych i określa minimalne i maksymalne wartości dla wyników.</span><span class="sxs-lookup"><span data-stu-id="42623-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="42623-143">W przykładzie `Aggregate` używa klauzuli do kwerendy `Group By` dla pojedynczego wyniku i klauzuli, aby wyświetlić średnią dla wyników grupowanych.</span><span class="sxs-lookup"><span data-stu-id="42623-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="42623-144">Naciśnij **klawisz F5,** aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="42623-144">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42623-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42623-145">See also</span></span>

- [<span data-ttu-id="42623-146">Linq</span><span class="sxs-lookup"><span data-stu-id="42623-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="42623-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="42623-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="42623-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="42623-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="42623-149">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="42623-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
