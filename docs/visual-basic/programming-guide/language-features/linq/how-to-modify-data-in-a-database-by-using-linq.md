---
title: 'Instrukcje: modyfikowanie danych w bazie danych za pomocą LINQ'
ms.date: 07/20/2015
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
ms.openlocfilehash: eb076d9156fa66858f2e560422eef0dc61ba22b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403488"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="e973f-102">Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e973f-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="e973f-103">Zapytania dotyczące języka (LINQ) w języku zintegrowanym z językiem umożliwiają łatwe uzyskiwanie dostępu do informacji o bazie danych i modyfikowanie wartości w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e973f-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="e973f-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która pobiera i aktualizuje informacje w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e973f-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="e973f-105">Przykłady w tym temacie korzystają z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e973f-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="e973f-106">Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z centrum pobierania Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e973f-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="e973f-107">Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e973f-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="e973f-108">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="e973f-108">To create a connection to a database</span></span>

1. <span data-ttu-id="e973f-109">W programie Visual Studio Otwórz **Server Explorer** / **Eksplorator bazy danych** Eksplorator serwera, klikając menu **Widok** , a następnie wybierając **Eksplorator serwera** / **Eksplorator bazy danych**.</span><span class="sxs-lookup"><span data-stu-id="e973f-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="e973f-110">Kliknij prawym przyciskiem myszy pozycję **połączenia danych** w **Eksplorator serwera** / **Eksplorator bazy danych**, a następnie kliknij pozycję **Dodaj połączenie**.</span><span class="sxs-lookup"><span data-stu-id="e973f-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="e973f-111">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e973f-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="e973f-112">Aby dodać projekt z plikiem LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e973f-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="e973f-113">W programie Visual Studio w menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e973f-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="e973f-114">Wybierz Visual Basic **Windows Forms aplikacji** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="e973f-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="e973f-115">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="e973f-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="e973f-116">Wybierz szablon elementu **LINQ to SQL klas** .</span><span class="sxs-lookup"><span data-stu-id="e973f-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="e973f-117">Nazwij plik `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="e973f-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="e973f-118">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e973f-118">Click **Add**.</span></span> <span data-ttu-id="e973f-119">Zostanie otwarty Object Relational Designer (Projektant O/R) dla tego `northwind.dbml` pliku.</span><span class="sxs-lookup"><span data-stu-id="e973f-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="e973f-120">Aby dodać tabele do zapytania i modyfikować do projektanta</span><span class="sxs-lookup"><span data-stu-id="e973f-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="e973f-121">W **Server Explorer** / **Eksplorator bazy danych**Eksplorator serwera rozwiń połączenie z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e973f-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="e973f-122">Rozwiń folder **tabele** .</span><span class="sxs-lookup"><span data-stu-id="e973f-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="e973f-123">Jeśli zamknąłeś projektanta O/R, możesz otworzyć go ponownie, dwukrotnie klikając `northwind.dbml` dodany wcześniej plik.</span><span class="sxs-lookup"><span data-stu-id="e973f-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="e973f-124">Kliknij tabelę Customers i przeciągnij ją do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="e973f-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="e973f-125">Projektant tworzy nowy obiekt klienta dla projektu.</span><span class="sxs-lookup"><span data-stu-id="e973f-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="e973f-126">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="e973f-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="e973f-127">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="e973f-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="e973f-128">Aby dodać kod w celu zmodyfikowania bazy danych i wyświetlenia wyników</span><span class="sxs-lookup"><span data-stu-id="e973f-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="e973f-129">Z **przybornika**przeciągnij <xref:System.Windows.Forms.DataGridView> kontrolkę na domyślny formularz systemu Windows dla projektu, formularz Form1.</span><span class="sxs-lookup"><span data-stu-id="e973f-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="e973f-130">Po dodaniu tabel do projektanta O/R Projektant dodał <xref:System.Data.Linq.DataContext> obiekt do projektu.</span><span class="sxs-lookup"><span data-stu-id="e973f-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="e973f-131">Ten obiekt zawiera kod, którego można użyć w celu uzyskania dostępu do tabeli Customers.</span><span class="sxs-lookup"><span data-stu-id="e973f-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="e973f-132">Zawiera również kod definiujący lokalny obiekt klienta i kolekcję Customers dla tabeli.</span><span class="sxs-lookup"><span data-stu-id="e973f-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="e973f-133"><xref:System.Data.Linq.DataContext>Obiekt dla projektu jest nazwany na podstawie nazwy pliku. dbml.</span><span class="sxs-lookup"><span data-stu-id="e973f-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="e973f-134">Dla tego projektu <xref:System.Data.Linq.DataContext> obiekt ma nazwę `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="e973f-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="e973f-135">Można utworzyć wystąpienie <xref:System.Data.Linq.DataContext> obiektu w kodzie i zapytania i zmodyfikować kolekcję klientów określoną przez projektanta O/R.</span><span class="sxs-lookup"><span data-stu-id="e973f-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="e973f-136">Zmiany wprowadzane w kolekcji Customers nie są odzwierciedlane w bazie danych, dopóki nie zostaną przesłane przez wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.DataContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e973f-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="e973f-137">Kliknij dwukrotnie formularz systemu Windows, Form1, aby dodać kod do <xref:System.Windows.Forms.Form.Load> zdarzenia w celu zbadania tabeli Customers, która jest udostępniona jako właściwość <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="e973f-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="e973f-138">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e973f-138">Add the following code:</span></span>

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

3. <span data-ttu-id="e973f-139">Z **przybornika**przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki na formularz.</span><span class="sxs-lookup"><span data-stu-id="e973f-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="e973f-140">Wybierz pierwszy `Button` formant.</span><span class="sxs-lookup"><span data-stu-id="e973f-140">Select the first `Button` control.</span></span> <span data-ttu-id="e973f-141">W oknie **Właściwości** ustaw wartość `Name` `Button` kontrolki na i na wartość `AddButton` `Text` `Add` .</span><span class="sxs-lookup"><span data-stu-id="e973f-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="e973f-142">Wybierz drugi przycisk i ustaw `Name` Właściwość na `UpdateButton` , a właściwość na `Text` `Update` .</span><span class="sxs-lookup"><span data-stu-id="e973f-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="e973f-143">Wybierz trzeci przycisk i ustaw `Name` Właściwość na wartość `DeleteButton` `Text` `Delete` .</span><span class="sxs-lookup"><span data-stu-id="e973f-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="e973f-144">Kliknij dwukrotnie przycisk **Dodaj** , aby dodać kod do jego `Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e973f-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="e973f-145">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e973f-145">Add the following code:</span></span>

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

5. <span data-ttu-id="e973f-146">Kliknij dwukrotnie przycisk **Aktualizuj** , aby dodać kod do jego `Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e973f-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="e973f-147">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e973f-147">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="e973f-148">Kliknij dwukrotnie przycisk **Usuń** , aby dodać kod do jego `Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e973f-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="e973f-149">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e973f-149">Add the following code:</span></span>

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

7. <span data-ttu-id="e973f-150">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="e973f-150">Press F5 to run your project.</span></span> <span data-ttu-id="e973f-151">Kliknij przycisk **Dodaj** , aby dodać nowy rekord.</span><span class="sxs-lookup"><span data-stu-id="e973f-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="e973f-152">Kliknij przycisk **Aktualizuj** , aby zmodyfikować nowy rekord.</span><span class="sxs-lookup"><span data-stu-id="e973f-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="e973f-153">Kliknij przycisk **Usuń** , aby usunąć nowy rekord.</span><span class="sxs-lookup"><span data-stu-id="e973f-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="e973f-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e973f-154">See also</span></span>

- [<span data-ttu-id="e973f-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="e973f-155">LINQ</span></span>](index.md)
- [<span data-ttu-id="e973f-156">Zapytania</span><span class="sxs-lookup"><span data-stu-id="e973f-156">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="e973f-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e973f-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="e973f-158">Metody DataContext (Object Relational Designer)</span><span class="sxs-lookup"><span data-stu-id="e973f-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="e973f-159">Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="e973f-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
