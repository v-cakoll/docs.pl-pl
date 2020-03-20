---
title: Wykonywanie operacji wsadowych za pomocą elementów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 62a61051e5b9d896f8a89ed3d2745859fc07a7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149261"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="7e0be-102">Wykonywanie operacji wsadowych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7e0be-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="7e0be-103">Obsługa wsadowa w ADO.NET <xref:System.Data.Common.DataAdapter> umożliwia grupowanie operacji INSERT, <xref:System.Data.DataSet> UPDATE <xref:System.Data.DataTable> i DELETE z a lub do serwera, zamiast wysyłać jedną operację naraz.</span><span class="sxs-lookup"><span data-stu-id="7e0be-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="7e0be-104">Zmniejszenie liczby rund na serwer zazwyczaj powoduje znaczny wzrost wydajności.</span><span class="sxs-lookup"><span data-stu-id="7e0be-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="7e0be-105">Aktualizacje wsadowe są obsługiwane dla dostawców<xref:System.Data.SqlClient>danych .NET<xref:System.Data.OracleClient>dla programu SQL Server ( ) i Oracle ( ).</span><span class="sxs-lookup"><span data-stu-id="7e0be-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="7e0be-106">Podczas aktualizowania bazy danych <xref:System.Data.DataSet> ze zmianami z poprzednich `Update` wersji ADO.NET, metoda `DataAdapter` wykonywane aktualizacje bazy danych jeden wiersz na raz.</span><span class="sxs-lookup"><span data-stu-id="7e0be-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="7e0be-107">Jak iterowane przez wiersze w <xref:System.Data.DataTable>określonym , <xref:System.Data.DataRow> zbadał każdy, aby sprawdzić, czy został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="7e0be-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="7e0be-108">Jeśli wiersz został zmodyfikowany, nazwał `UpdateCommand`odpowiednie `InsertCommand`, `DeleteCommand`lub , w <xref:System.Data.DataRow.RowState%2A> zależności od wartości właściwości dla tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7e0be-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="7e0be-109">Każda aktualizacja wiersza obejmowała sieć w obie strony do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7e0be-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="7e0be-110">Począwszy od ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> udostępnia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e0be-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="7e0be-111">Ustawienie `UpdateBatchSize` dodatniej wartości całkowitej powoduje, że aktualizacje bazy danych mają być wysyłane jako partie o określonym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="7e0be-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="7e0be-112">Na przykład ustawienie `UpdateBatchSize` na 10 spowoduje grupowanie 10 oddzielnych instrukcji i przesłanie ich jako pojedynczej partii.</span><span class="sxs-lookup"><span data-stu-id="7e0be-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="7e0be-113">Ustawienie `UpdateBatchSize` na 0 spowoduje <xref:System.Data.Common.DataAdapter> użycie największego rozmiaru partii, który może obsłużyć serwer.</span><span class="sxs-lookup"><span data-stu-id="7e0be-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="7e0be-114">Ustawienie go na 1 powoduje wyłączenie aktualizacji wsadowych, ponieważ wiersze są wysyłane po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="7e0be-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="7e0be-115">Wykonywanie bardzo dużej partii może zmniejszyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="7e0be-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="7e0be-116">W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed zaimplementowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e0be-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="7e0be-117">Korzystanie z UpdateBatchSize Właściwość</span><span class="sxs-lookup"><span data-stu-id="7e0be-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="7e0be-118">Gdy aktualizacje partii są <xref:System.Data.IDbCommand.UpdatedRowSource%2A> włączone, `UpdateCommand`wartość właściwości DataAdapter's , `InsertCommand`i <xref:System.Data.UpdateRowSource.OutputParameters> `DeleteCommand` powinny być ustawione na <xref:System.Data.UpdateRowSource.None> lub .</span><span class="sxs-lookup"><span data-stu-id="7e0be-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="7e0be-119">Podczas wykonywania aktualizacji partii, wartość <xref:System.Data.IDbCommand.UpdatedRowSource%2A> właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> polecenia <xref:System.Data.UpdateRowSource.Both> lub jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="7e0be-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="7e0be-120">Poniższa procedura pokazuje korzystanie `UpdateBatchSize` z właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e0be-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="7e0be-121">Procedura ma dwa <xref:System.Data.DataSet> argumenty, obiekt, który ma kolumny reprezentujące **ProductCategoryID** i **Nazwa** pola w **Production.ProductCategory** tabeli i liczba całkowita reprezentująca rozmiar partii (liczba wierszy w partii).</span><span class="sxs-lookup"><span data-stu-id="7e0be-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="7e0be-122">Kod tworzy nowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>ustawiając jego , <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e0be-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="7e0be-123">Kod zakłada, że <xref:System.Data.DataSet> obiekt zmodyfikował wiersze.</span><span class="sxs-lookup"><span data-stu-id="7e0be-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="7e0be-124">Ustawia `UpdateBatchSize` właściwość i wykonuje aktualizację.</span><span class="sxs-lookup"><span data-stu-id="7e0be-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="7e0be-125">Obsługa zdarzeń i błędów związanych z aktualizacją wsadową</span><span class="sxs-lookup"><span data-stu-id="7e0be-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="7e0be-126">**DataAdapter** ma dwa zdarzenia związane z aktualizacją: **RowUpdating** i **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="7e0be-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="7e0be-127">W poprzednich wersjach ADO.NET, gdy przetwarzanie wsadowe jest wyłączone, każde z tych zdarzeń jest generowane raz dla każdego przetworzonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7e0be-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="7e0be-128">**RowUpdating** jest generowany przed wystąpieniem aktualizacji, a **RowUpdated** jest generowany po zakończeniu aktualizacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7e0be-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="7e0be-129">Zmiany zachowania zdarzeń z aktualizacjami wsadowym</span><span class="sxs-lookup"><span data-stu-id="7e0be-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="7e0be-130">Gdy przetwarzanie wsadowe jest włączone, wiele wierszy są aktualizowane w jednej operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7e0be-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="7e0be-131">W związku z `RowUpdated` tym tylko jedno zdarzenie `RowUpdating` występuje dla każdej partii, podczas gdy zdarzenie występuje dla każdego wiersza przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="7e0be-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="7e0be-132">Gdy przetwarzanie wsadowe jest wyłączone, dwa zdarzenia są uruchamiane z `RowUpdating` interleaving jeden do jednego, gdzie jedno zdarzenie i jedno `RowUpdated` zdarzenie jest uruchamiane dla wiersza, a następnie jeden `RowUpdating` i jeden `RowUpdated` pożar zdarzenia dla następnego wiersza, aż wszystkie wiersze są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="7e0be-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="7e0be-133">Uzyskiwanie dostępu do zaktualizowanych wierszy</span><span class="sxs-lookup"><span data-stu-id="7e0be-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="7e0be-134">Gdy przetwarzanie wsadowe jest wyłączone, aktualizowany <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> wiersz jest <xref:System.Data.Common.RowUpdatedEventArgs> dostępny przy użyciu właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="7e0be-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="7e0be-135">Gdy przetwarzanie wsadowe jest `RowUpdated` włączone, dla wielu wierszy jest generowane pojedyncze zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7e0be-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="7e0be-136">W związku z tym `Row` wartość właściwości dla każdego wiersza jest null.</span><span class="sxs-lookup"><span data-stu-id="7e0be-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="7e0be-137">`RowUpdating`zdarzenia są nadal generowane dla każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7e0be-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="7e0be-138">Metoda <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> <xref:System.Data.Common.RowUpdatedEventArgs> klasy umożliwia dostęp do przetworzonych wierszy, kopiując odwołania do wierszy do tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e0be-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="7e0be-139">Jeśli nie są przetwarzane żadne `CopyToRows` wiersze, zgłasza plik <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="7e0be-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="7e0be-140">Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości, aby zwrócić liczbę wierszy przetworzonych przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7e0be-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="7e0be-141">Obsługa błędów danych</span><span class="sxs-lookup"><span data-stu-id="7e0be-141">Handling Data Errors</span></span>  
 <span data-ttu-id="7e0be-142">Wykonywanie wsadowe ma taki sam efekt jak wykonanie każdej pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7e0be-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="7e0be-143">Instrukcje są wykonywane w kolejności, w.</span><span class="sxs-lookup"><span data-stu-id="7e0be-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="7e0be-144">Błędy są obsługiwane w taki sam sposób w trybie wsadowym, jak są, gdy tryb wsadowy jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="7e0be-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="7e0be-145">Każdy wiersz jest przetwarzany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="7e0be-145">Each row is processed separately.</span></span> <span data-ttu-id="7e0be-146">Tylko wiersze, które zostały pomyślnie przetworzone w bazie <xref:System.Data.DataRow> danych <xref:System.Data.DataTable>zostaną zaktualizowane w odpowiednich w ramach .</span><span class="sxs-lookup"><span data-stu-id="7e0be-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="7e0be-147">Dostawca danych i serwer bazy danych zaplecza określają, które konstrukcje SQL są obsługiwane do wykonywania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="7e0be-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="7e0be-148">Wyjątek może zostać zgłoszony, jeśli nieobjęta instrukcją jest przesyłana do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7e0be-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0be-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e0be-149">See also</span></span>

- [<span data-ttu-id="7e0be-150">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="7e0be-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="7e0be-151">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7e0be-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="7e0be-152">Obsługa zdarzeń elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7e0be-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="7e0be-153">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7e0be-153">ADO.NET Overview</span></span>](ado-net-overview.md)
