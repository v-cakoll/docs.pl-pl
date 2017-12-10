---
title: "Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69e2fc7a6860ad2ff43742d37cd35671ebe35acf
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="4b8e8-102">Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b8e8-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="4b8e8-103">Zintegrowane języka zapytań zapytania (LINQ) ułatwiają dostęp do bazy danych i modyfikować wartości w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="4b8e8-104">Poniższy przykład przedstawia sposób tworzenia nowej aplikacji, które są pobierane i informacji o aktualizacjach w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="4b8e8-105">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4b8e8-106">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="4b8e8-107">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4b8e8-107">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4b8e8-108">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="4b8e8-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="4b8e8-109">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **widoku** menu, a następnie wybierz **wEksploratorzeserwera** / **Bazy danych Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="4b8e8-110">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych**i kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="4b8e8-111">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="4b8e8-112">Aby dodać projekt za pomocą LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="4b8e8-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="4b8e8-113">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4b8e8-114">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="4b8e8-115">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4b8e8-116">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="4b8e8-117">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4b8e8-118">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-118">Click **Add**.</span></span> <span data-ttu-id="4b8e8-119">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla `northwind.dbml` pliku.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="4b8e8-120">Aby dodać tabele, aby zapytania i modyfikować do projektanta</span><span class="sxs-lookup"><span data-stu-id="4b8e8-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="4b8e8-121">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4b8e8-122">Rozwiń węzeł **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4b8e8-123">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go przez dwukrotne kliknięcie `northwind.dbml` pliku dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="4b8e8-124">Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4b8e8-125">Projektant tworzy nowy obiekt klienta dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="4b8e8-126">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="4b8e8-127">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="4b8e8-128">Aby dodać kod do modyfikowania bazy danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="4b8e8-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="4b8e8-129">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="4b8e8-130">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="4b8e8-131">Ten obiekt zawiera kod, który można uzyskać dostępu do tabeli klientów.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="4b8e8-132">Zawiera kod, który definiuje obiekt klienta i kolekcję klientów dla tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="4b8e8-133"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4b8e8-134">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4b8e8-135">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> obiektu w kodzie i zapytania i modyfikować kolekcji klientów określony przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="4b8e8-136">Zmiany wprowadzone do kolekcji klientów nie są uwzględniane w bazie danych do czasu przesłania przez wywołanie metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.DataContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="4b8e8-137">Kliknij dwukrotnie formularza systemu Windows, Formularz1, aby dodać kod, aby <xref:System.Windows.Forms.Form.Load> zdarzenia kwerendę klientów tabelę, która jest ujawniona jako właściwość z <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="4b8e8-138">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4b8e8-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="4b8e8-139">Z **przybornika**, przeciągnij trzy <xref:System.Windows.Forms.Button> formantów do formularza.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="4b8e8-140">Wybierz pierwsze `Button` formantu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-140">Select the first `Button` control.</span></span> <span data-ttu-id="4b8e8-141">W **właściwości** ustaw `Name` z `Button` formant `AddButton` i `Text` do `Add`.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="4b8e8-142">Wybierz przycisk drugi i ustaw `Name` właściwości `UpdateButton` i `Text` właściwości `Update`.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="4b8e8-143">Wybierz przycisk trzeci i ustaw `Name` właściwości `DeleteButton` i `Text` właściwości `Delete`.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="4b8e8-144">Kliknij dwukrotnie **Dodaj** przycisk, aby dodać kod, aby jego `Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="4b8e8-145">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4b8e8-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="4b8e8-146">Kliknij dwukrotnie **aktualizacji** przycisk, aby dodać kod, aby jego `Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="4b8e8-147">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4b8e8-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="4b8e8-148">Kliknij dwukrotnie **usunąć** przycisk, aby dodać kod, aby jego `Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="4b8e8-149">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4b8e8-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="4b8e8-150">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-150">Press F5 to run your project.</span></span> <span data-ttu-id="4b8e8-151">Kliknij przycisk **Dodaj** do dodawania nowego rekordu.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="4b8e8-152">Kliknij przycisk **aktualizacji** można zmodyfikować w nowym rekordzie.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="4b8e8-153">Kliknij przycisk **usunąć** do usunięcia w nowym rekordzie.</span><span class="sxs-lookup"><span data-stu-id="4b8e8-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8e8-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b8e8-154">See Also</span></span>  
 [<span data-ttu-id="4b8e8-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="4b8e8-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="4b8e8-156">Zapytania</span><span class="sxs-lookup"><span data-stu-id="4b8e8-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="4b8e8-157">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="4b8e8-157">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="4b8e8-158">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="4b8e8-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="4b8e8-159">Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="4b8e8-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
