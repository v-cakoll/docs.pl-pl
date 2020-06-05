---
title: 'Porady: zwracanie wyniku zapytania LINQ jako określonego typu'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404955"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="1548a-102">Porady: zwracanie wyniku zapytania LINQ jako określonego typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1548a-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="1548a-103">Program Query Integrated Language (LINQ) ułatwia dostęp do informacji o bazie danych i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="1548a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="1548a-104">Domyślnie zapytania LINQ zwracają listę obiektów jako typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="1548a-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="1548a-105">Możesz również określić, że zapytanie zwróci listę określonego typu przy użyciu `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1548a-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="1548a-106">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje zapytania dotyczące bazy danych SQL Server i projektuje wyniki jako określony nazwany typ.</span><span class="sxs-lookup"><span data-stu-id="1548a-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="1548a-107">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../objects-and-classes/anonymous-types.md) i [klauzula SELECT](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1548a-107">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="1548a-108">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="1548a-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1548a-109">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1548a-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1548a-110">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1548a-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1548a-111">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="1548a-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="1548a-112">W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając pozycję **Eksplorator serwera** / **Eksplorator bazy danych** w menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="1548a-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="1548a-113">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych** a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="1548a-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="1548a-114">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="1548a-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="1548a-115">Aby dodać projekt, który zawiera plik LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1548a-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="1548a-116">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="1548a-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1548a-117">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="1548a-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="1548a-118">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="1548a-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1548a-119">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="1548a-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="1548a-120">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1548a-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1548a-121">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="1548a-121">Click **Add**.</span></span> <span data-ttu-id="1548a-122">Object Relational Designer (Projektant O/R) zostanie otwarty dla pliku Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="1548a-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="1548a-123">Aby dodać tabele do zapytania do projektanta O/R</span><span class="sxs-lookup"><span data-stu-id="1548a-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="1548a-124">W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="1548a-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1548a-125">Rozwiń folder **tabele** .</span><span class="sxs-lookup"><span data-stu-id="1548a-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="1548a-126">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając dodany wcześniej plik Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="1548a-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="1548a-127">Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="1548a-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="1548a-128">Projektant tworzy nowy `Customer` obiekt dla projektu.</span><span class="sxs-lookup"><span data-stu-id="1548a-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="1548a-129">Wyniki zapytania można projektować jako `Customer` Typ lub jako typ, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="1548a-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="1548a-130">Ten przykład utworzy nowy typ w późniejszej procedurze i projektuje wynik zapytania jako ten typ.</span><span class="sxs-lookup"><span data-stu-id="1548a-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="1548a-131">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="1548a-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="1548a-132">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="1548a-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="1548a-133">Aby dodać kod do zapytania do bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="1548a-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="1548a-134">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="1548a-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="1548a-135">Kliknij dwukrotnie przycisk Form1, aby zmodyfikować klasę Form1.</span><span class="sxs-lookup"><span data-stu-id="1548a-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="1548a-136">Po `End Class` instrukcji klasy Form1 Dodaj następujący kod, aby utworzyć `CustomerInfo` Typ do przechowywania wyników zapytania dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="1548a-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="1548a-137">Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="1548a-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="1548a-138">Ten obiekt zawiera kod, który musi być konieczny, aby uzyskać dostęp do tych tabel i uzyskać dostęp do poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1548a-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="1548a-139"><xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="1548a-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1548a-140">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="1548a-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="1548a-141">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> w kodzie i zbadać tabele określone przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="1548a-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="1548a-142">W `Load` przypadku klasy Form1 Dodaj następujący kod, aby wykonać zapytanie dotyczące tabel, które są uwidocznione jako właściwości kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="1548a-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="1548a-143">`Select`Klauzula zapytania utworzy nowy `CustomerInfo` Typ zamiast typu anonimowego dla każdego elementu wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="1548a-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="1548a-144">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="1548a-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1548a-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1548a-145">See also</span></span>

- [<span data-ttu-id="1548a-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="1548a-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="1548a-147">Zapytania</span><span class="sxs-lookup"><span data-stu-id="1548a-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="1548a-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1548a-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="1548a-149">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="1548a-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
