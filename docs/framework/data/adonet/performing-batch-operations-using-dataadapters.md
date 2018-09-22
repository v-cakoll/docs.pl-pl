---
title: Wykonywanie operacji wsadowych za pomocą elementów DataAdapters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696164"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="78274-102">Wykonywanie operacji wsadowych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="78274-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="78274-103">Umożliwia obsługę usługi Batch w ADO.NET <xref:System.Data.Common.DataAdapter> do grupy operacji INSERT, UPDATE i DELETE z <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> do serwera, zamiast wysyłać jedną operację naraz.</span><span class="sxs-lookup"><span data-stu-id="78274-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="78274-104">Zmniejszenie liczby rund do serwera zwykle powoduje znaczący wzrost wydajności.</span><span class="sxs-lookup"><span data-stu-id="78274-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="78274-105">Aktualizacje usługi Batch są obsługiwane dla dostawcy danych .NET dla programu SQL Server (<xref:System.Data.SqlClient>) i Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="78274-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="78274-106">Aktualizacja bazy danych za pomocą zmiany z <xref:System.Data.DataSet> w poprzednich wersjach programu ADO.NET, `Update` metody `DataAdapter` wykonywane aktualizacji do bazy danych o jeden wiersz w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="78274-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="78274-107">Jak powtórzyć go za pośrednictwem wierszy w określonym <xref:System.Data.DataTable>, zbadaniu, każdego <xref:System.Data.DataRow> do sprawdzania, czy ma zostać zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="78274-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="78274-108">Jeśli wiersz ma zmodyfikowany, wywołuje odpowiednią `UpdateCommand`, `InsertCommand`, lub `DeleteCommand`, w zależności od wartości <xref:System.Data.DataRow.RowState%2A> właściwości dla tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="78274-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="78274-109">Każda aktualizacja wiersza zaangażowane sieci przesłania danych do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="78274-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="78274-110">Począwszy od wersji 2.0 programu ADO.NET, <xref:System.Data.Common.DbDataAdapter> udostępnia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="78274-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="78274-111">Ustawienie `UpdateBatchSize` na dodatnią liczbą całkowitą wartość powoduje, że aktualizacje bazy danych do wysłania jako partie o określonym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="78274-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="78274-112">Na przykład ustawienie `UpdateBatchSize` 10 zostanie grupy 10 osobnych instrukcji i przesłać je jako jedna partia.</span><span class="sxs-lookup"><span data-stu-id="78274-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="78274-113">Ustawienie `UpdateBatchSize` na 0 spowoduje, że <xref:System.Data.Common.DataAdapter> używać największy rozmiar partii, która może obsłużyć serwer.</span><span class="sxs-lookup"><span data-stu-id="78274-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="78274-114">Ustawienie 1 wyłącza aktualizacji wsadowych, jak wiersze są wysyłane pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="78274-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="78274-115">Wykonując bardzo dużych partii może obniżyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="78274-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="78274-116">W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed wdrożeniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78274-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="78274-117">Przy użyciu właściwości UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="78274-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="78274-118">Po włączeniu aktualizacji wsadowych <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartości właściwości elementu DataAdapter `UpdateCommand`, `InsertCommand`, i `DeleteCommand` powinna być równa <xref:System.Data.UpdateRowSource.None> lub <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="78274-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="78274-119">Podczas wykonywania partii aktualizacji, polecenia <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> lub <xref:System.Data.UpdateRowSource.Both> jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="78274-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="78274-120">Poniższa procedura demonstruje użycie `UpdateBatchSize` właściwości.</span><span class="sxs-lookup"><span data-stu-id="78274-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="78274-121">Procedury przyjmuje dwa argumenty <xref:System.Data.DataSet> obiekt, który ma kolumn reprezentujących **ProductCategoryID** i **nazwa** pola w **Production.ProductCategory**tabeli i liczba całkowita reprezentująca rozmiar partii (liczba wierszy w zadaniu wsadowym).</span><span class="sxs-lookup"><span data-stu-id="78274-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="78274-122">Ten kod tworzy nową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu, ustawiając jego <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="78274-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="78274-123">Kod zakłada, że <xref:System.Data.DataSet> obiekt zmodyfikowany wierszy.</span><span class="sxs-lookup"><span data-stu-id="78274-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="78274-124">Ustawia `UpdateBatchSize` właściwości i wykonuje aktualizację.</span><span class="sxs-lookup"><span data-stu-id="78274-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="78274-125">Obsługa zdarzeń związanych z aktualizacji usługi Batch i błędów</span><span class="sxs-lookup"><span data-stu-id="78274-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="78274-126">**DataAdapter** ma dwa zdarzenia związane z aktualizacji: **— RowUpdating** i **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="78274-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="78274-127">W poprzednich wersjach programu ADO.NET podczas przetwarzania wsadowego jest wyłączona, każde z tych wydarzeń jest generowany raz dla każdego wiersza przetworzone.</span><span class="sxs-lookup"><span data-stu-id="78274-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="78274-128">**— RowUpdating** jest generowany, zanim nastąpi aktualizacja, i **RowUpdated** jest generowany po zakończeniu aktualizacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="78274-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="78274-129">Zdarzenie zmiany zachowania za pomocą aktualizacji usługi Batch</span><span class="sxs-lookup"><span data-stu-id="78274-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="78274-130">Po włączeniu przetwarzanie wsadowe wiele wierszy są aktualizowane w ramach operacji pojedynczej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="78274-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="78274-131">W związku z tym tylko jeden `RowUpdated` wystąpi zdarzenie dla każdej partii, natomiast `RowUpdating` wystąpi zdarzenie dla każdego wiersza przetworzone.</span><span class="sxs-lookup"><span data-stu-id="78274-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="78274-132">Po wyłączeniu przetwarzania wsadowego dwa zdarzenia są uruchamiane przy użyciu jednego z przeplotem, gdy jedna `RowUpdating` zdarzeń i jeden `RowUpdated` pożaru zdarzeń do wiersza, a następnie jeden `RowUpdating` i jeden `RowUpdated` pożaru zdarzeń do następnego wiersza, aż wszystkie wiersze są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="78274-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="78274-133">Uzyskiwanie dostępu do zaktualizowanych wierszy</span><span class="sxs-lookup"><span data-stu-id="78274-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="78274-134">Podczas przetwarzania wsadowego jest wyłączona, można uzyskać dostępu do aktualizacji wiersza przy użyciu <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> właściwość <xref:System.Data.Common.RowUpdatedEventArgs> klasy.</span><span class="sxs-lookup"><span data-stu-id="78274-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="78274-135">Po włączeniu przetwarzania wsadowego, pojedynczy `RowUpdated` zdarzenie jest generowane dla wielu wierszy.</span><span class="sxs-lookup"><span data-stu-id="78274-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="78274-136">W związku z tym, wartość `Row` właściwości dla każdego wiersza ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="78274-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="78274-137">`RowUpdating` zdarzenia są nadal generowane dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="78274-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="78274-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metody <xref:System.Data.Common.RowUpdatedEventArgs> klasy umożliwia dostęp do wierszy przetworzonych przez kopiowanie odwołania do wierszy do tablicy.</span><span class="sxs-lookup"><span data-stu-id="78274-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="78274-139">Jeśli żadne wiersze nie są przetwarzane, `CopyToRows` zgłasza <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="78274-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="78274-140">Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości, aby zwrócić liczbę wierszy przetworzone przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="78274-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="78274-141">Obsługa błędów danych</span><span class="sxs-lookup"><span data-stu-id="78274-141">Handling Data Errors</span></span>  
 <span data-ttu-id="78274-142">Wykonywanie wsadowe ma taki sam skutek jak wykonanie każdej pojedynczych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="78274-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="78274-143">Instrukcje są wykonywane w kolejności, że instrukcje zostały dodane do usługi batch.</span><span class="sxs-lookup"><span data-stu-id="78274-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="78274-144">Błędy są obsługiwane taki sam sposób, w trybie wsadowym, ponieważ są one po wyłączeniu trybu wsadowego.</span><span class="sxs-lookup"><span data-stu-id="78274-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="78274-145">Każdy wiersz jest przetwarzany osobno.</span><span class="sxs-lookup"><span data-stu-id="78274-145">Each row is processed separately.</span></span> <span data-ttu-id="78274-146">Tylko wiersze, które zostały pomyślnie przetworzone w bazie danych zostanie zaktualizowany w odpowiednich <xref:System.Data.DataRow> w ramach <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="78274-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="78274-147">Dostawca danych i serwera wewnętrznej bazy danych należy określić struktur SQL, które są obsługiwane w przypadku wykonywania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="78274-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="78274-148">Nieobsługiwane instrukcji jest przesyłany w celu wykonania może zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="78274-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78274-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78274-149">See Also</span></span>  
 [<span data-ttu-id="78274-150">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="78274-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="78274-151">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="78274-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="78274-152">Obsługa zdarzeń elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="78274-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="78274-153">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="78274-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
