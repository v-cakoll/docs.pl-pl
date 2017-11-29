---
title: "Za pomocą obiektów DataAdapter operacji wsadowych."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66395e8011b5ea25bb3b52b25e0067dc5d8fc1ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="69566-102">Za pomocą obiektów DataAdapter operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="69566-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="69566-103">Umożliwia obsługę partii w ADO.NET <xref:System.Data.Common.DataAdapter> do grupowania operacji INSERT, UPDATE i DELETE <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> na serwerze, zamiast wysyłać jedną operację naraz.</span><span class="sxs-lookup"><span data-stu-id="69566-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="69566-104">Zmniejszenie liczby rund do serwera zwykle powoduje znaczący wzrost wydajności.</span><span class="sxs-lookup"><span data-stu-id="69566-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="69566-105">Aktualizacje wsadowe są obsługiwane dla dostawcy danych .NET dla programu SQL Server (<xref:System.Data.SqlClient>) i Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="69566-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="69566-106">Aktualizowanie bazy danych o zmiany z <xref:System.Data.DataSet> w poprzednich wersjach programu ADO.NET, `Update` metody `DataAdapter` wykonywana aktualizacji do bazy danych o jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="69566-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="69566-107">Zgodnie z jego iterowane za pośrednictwem wierszy w określonym <xref:System.Data.DataTable>, jego zbadaniu <xref:System.Data.DataRow> do sprawdzania, czy ma zostać zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="69566-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="69566-108">Jeśli wiersz gdyby został zmodyfikowany, nazywany odpowiednie `UpdateCommand`, `InsertCommand`, lub `DeleteCommand`w zależności od wartości <xref:System.Data.DataRow.RowState%2A> właściwości dla tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="69566-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="69566-109">Każda aktualizacja wiersza zaangażowane sieci przesłania danych do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69566-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="69566-110">Począwszy od ADO.NET 2.0 <xref:System.Data.Common.DbDataAdapter> przedstawia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="69566-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="69566-111">Ustawienie `UpdateBatchSize` jako dodatnią liczbę całkowitą wartość powoduje, że aktualizacje bazy danych do wysłania jako partii o określonym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="69566-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="69566-112">Na przykład ustawienie `UpdateBatchSize` 10 będzie grupy 10 osobnych instrukcji i przesłać je jako pojedyncza partia.</span><span class="sxs-lookup"><span data-stu-id="69566-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="69566-113">Ustawienie `UpdateBatchSize` na 0 spowoduje, że <xref:System.Data.Common.DataAdapter> do użycia największy rozmiar partii, serwer może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="69566-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="69566-114">Opcja 1 wyłącza aktualizacje wsadowe, jako wiersze są wysyłane pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="69566-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="69566-115">Wykonywanie wsadowe bardzo dużą może obniżyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="69566-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="69566-116">W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed wdrożeniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69566-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="69566-117">Za pomocą właściwości UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="69566-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="69566-118">Gdy są włączone aktualizacje wsadowe, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości element DataAdapter `UpdateCommand`, `InsertCommand`, i `DeleteCommand` powinien być ustawiony na <xref:System.Data.UpdateRowSource.None> lub <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="69566-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="69566-119">Podczas wykonywania partii zaktualizować, polecenia <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> lub <xref:System.Data.UpdateRowSource.Both> jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="69566-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="69566-120">W poniższej procedurze przedstawiono użycie `UpdateBatchSize` właściwości.</span><span class="sxs-lookup"><span data-stu-id="69566-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="69566-121">Procedury przyjmuje dwa argumenty <xref:System.Data.DataSet> obiektu, który ma kolumn reprezentujących **ProductCategoryID** i **nazwa** pól w **Production.ProductCategory**tabeli i liczbę całkowitą reprezentującą rozmiar partii (liczba wierszy w partii).</span><span class="sxs-lookup"><span data-stu-id="69566-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="69566-122">Kod tworzy nową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu ustawienie jej <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="69566-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="69566-123">Kod, przy założeniu, że <xref:System.Data.DataSet> obiekt zmodyfikowany wierszy.</span><span class="sxs-lookup"><span data-stu-id="69566-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="69566-124">Ustawia `UpdateBatchSize` właściwości i wykonuje aktualizację.</span><span class="sxs-lookup"><span data-stu-id="69566-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="69566-125">Obsługa zdarzeń związanych z aktualizacji partii i błędów</span><span class="sxs-lookup"><span data-stu-id="69566-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="69566-126">**Element DataAdapter** ma dwa zdarzenia związane z aktualizacji: **RowUpdating** i **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="69566-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="69566-127">W poprzednich wersjach programu ADO.NET wyłączenia przetwarzania wsadowego każde z tych wydarzeń generowany jest jeden raz dla każdego wiersza przetworzone.</span><span class="sxs-lookup"><span data-stu-id="69566-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="69566-128">**RowUpdating** jest generowany, zanim nastąpi aktualizacja, i **RowUpdated** jest generowany po ukończeniu aktualizacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69566-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="69566-129">Zdarzenie zmiany sposobu działania z aktualizacje wsadowe</span><span class="sxs-lookup"><span data-stu-id="69566-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="69566-130">Po włączeniu przetwarzania wsadowego wiele wierszy są aktualizowane w ramach operacji pojedynczej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69566-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="69566-131">W związku z tym tylko jeden `RowUpdated` zdarzenie dla każdej z partii, podczas gdy `RowUpdating` zdarzenie dla każdego wiersza przetworzone.</span><span class="sxs-lookup"><span data-stu-id="69566-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="69566-132">Podczas przetwarzania wsadowego jest wyłączona, gdy jedna dwa zdarzenia są uruchamiane z jeden do jednego z przeplotem `RowUpdating` zdarzeń i jeden `RowUpdated` fire zdarzenia dla wiersza, a następnie wykonaj `RowUpdating` i jeden `RowUpdated` fire zdarzenia dla następnego wiersza, aż wszystkie wiersze są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="69566-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="69566-133">Dostęp do zaktualizowanych wierszy</span><span class="sxs-lookup"><span data-stu-id="69566-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="69566-134">Podczas przetwarzania wsadowego jest wyłączona, można uzyskać dostępu do aktualizacji wiersza przy użyciu <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> właściwość <xref:System.Data.Common.RowUpdatedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="69566-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="69566-135">Po włączeniu przetwarzania wsadowego, pojedynczy `RowUpdated` zdarzenie jest generowane dla wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="69566-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="69566-136">W związku z tym wartość `Row` właściwości dla każdego wiersza ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="69566-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="69566-137">`RowUpdating`zdarzenia są nadal generowane dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="69566-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="69566-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metody <xref:System.Data.Common.RowUpdatedEventArgs> klasa pozwala na dostęp przez kopiowanie odwołania do wierszy w tablicy przetworzonych wierszy.</span><span class="sxs-lookup"><span data-stu-id="69566-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="69566-139">Jeśli żadne wiersze są przetwarzane, `CopyToRows` zgłasza <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="69566-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="69566-140">Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości Zwróć liczbę wierszy przetworzone przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="69566-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="69566-141">Obsługa błędów danych</span><span class="sxs-lookup"><span data-stu-id="69566-141">Handling Data Errors</span></span>  
 <span data-ttu-id="69566-142">Wsadowe ma ten sam efekt co wykonanie każdej poszczególnych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69566-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="69566-143">Instrukcje są wykonywane w kolejności, że instrukcje zostały dodane do wykonywania zadania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="69566-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="69566-144">Błędy są obsługiwane w trybie wsadowym tak samo, jak po wyłączeniu trybu partii.</span><span class="sxs-lookup"><span data-stu-id="69566-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="69566-145">Każdy wiersz jest przetwarzany osobno.</span><span class="sxs-lookup"><span data-stu-id="69566-145">Each row is processed separately.</span></span> <span data-ttu-id="69566-146">Tylko wiersze, które zostały pomyślnie przetworzone w bazie danych zostanie zaktualizowany w odpowiedniej <xref:System.Data.DataRow> w <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="69566-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="69566-147">Dostawca danych i serwera wewnętrznej bazy danych należy określić konstrukcji SQL, które są obsługiwane w przypadku wykonywania wsadowego usługi.</span><span class="sxs-lookup"><span data-stu-id="69566-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="69566-148">Może zostać zgłoszony wyjątek, jeśli instrukcji z systemem innym niż obsługiwany jest przesyłany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="69566-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69566-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69566-149">See Also</span></span>  
 [<span data-ttu-id="69566-150">Obiektów DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="69566-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="69566-151">Aktualizowanie źródła danych za pomocą obiektów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="69566-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="69566-152">Obsługa zdarzeń element DataAdapter</span><span class="sxs-lookup"><span data-stu-id="69566-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="69566-153">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="69566-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
