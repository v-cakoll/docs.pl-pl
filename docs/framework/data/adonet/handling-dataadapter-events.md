---
title: Obsługa zdarzeń element DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: f2b07b8d42069fa98ba51dea75f9695e7adce0b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="6060f-102">Obsługa zdarzeń element DataAdapter</span><span class="sxs-lookup"><span data-stu-id="6060f-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="6060f-103">ADO.NET <xref:System.Data.Common.DataAdapter> udostępnia trzy zdarzenia, które służą do reagowania na zmiany wprowadzone w danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6060f-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="6060f-104">W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6060f-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="6060f-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6060f-105">Event</span></span>|<span data-ttu-id="6060f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6060f-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="6060f-107">Operacja AKTUALIZOWANIA, WSTAWIANIA lub usuwania wiersza (przez wywołanie do jednego z `Update` metody) ma rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="6060f-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="6060f-108">Operacja AKTUALIZOWANIA, WSTAWIANIA lub usuwania w wierszu (przez wywołanie do jednego z `Update` metody) została ukończona.</span><span class="sxs-lookup"><span data-stu-id="6060f-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="6060f-109">Wystąpił błąd podczas `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="6060f-110">RowUpdating i RowUpdated</span><span class="sxs-lookup"><span data-stu-id="6060f-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="6060f-111">`RowUpdating` jest wywoływane przed wykonaniem dowolnej aktualizacji na wiersz z <xref:System.Data.DataSet> został przetworzony w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6060f-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="6060f-112">`RowUpdated` jest wywoływane po aktualizacji jedną na wiersz z `DataSet` został przetworzony w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6060f-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="6060f-113">W związku z tym można użyć `RowUpdating` do modyfikowania zachowania aktualizacji przed zdarza się, w celu zapewnienia obsługi dodatkowych, gdy nastąpi aktualizacja, aby zachować odwołanie do zaktualizowany wiersz, aby anulować harmonogram i bieżącej aktualizacji dla partii przetwarzanie do przetworzenia później , i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6060f-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="6060f-114">`RowUpdated` jest przydatne w przypadku odpowiedzi na błędy i wyjątków występujących podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="6060f-115">Można dodać informacje o błędzie do `DataSet`, a także Logika ponawiania próby i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6060f-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="6060f-116"><xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> argumentów przekazanych do `RowUpdating` i `RowUpdated` zdarzenia są następujące: `Command` właściwość, która odwołuje się do `Command` obiekt używany do przeprowadzenia aktualizacji; `Row` Właściwość, która odwołuje się do `DataRow` obiekt zawierający zaktualizowane informacje; `StatementType` właściwości, dla jakiego rodzaju aktualizacji jest wykonywane; `TableMapping`, jeśli ma to zastosowanie; i `Status` operacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="6060f-117">Można użyć `Status` właściwości w celu określenia, jeśli wystąpił błąd podczas operacji, a jeśli potrzebne, kontrolowanie akcji względem bieżących i wynikowy wierszy.</span><span class="sxs-lookup"><span data-stu-id="6060f-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="6060f-118">Po wystąpieniu zdarzenia, `Status` właściwości jest równa albo `Continue` lub `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="6060f-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="6060f-119">W poniższej tabeli przedstawiono wartości, które można ustawić `Status` właściwości w celu kontrolowania późniejsze akcje podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="6060f-120">Stan</span><span class="sxs-lookup"><span data-stu-id="6060f-120">Status</span></span>|<span data-ttu-id="6060f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6060f-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="6060f-122">Kontynuowanie operacji aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="6060f-123">Przerwij operacji aktualizowania i Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="6060f-124">Ignoruj bieżący wiersz i kontynuowania operacji aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="6060f-125">Przerwanie operacji aktualizacji, ale zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="6060f-126">Ustawienie `Status` właściwości `ErrorsOccurred` powoduje zgłoszenie wyjątku zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6060f-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="6060f-127">Można kontrolować, które wyjątku przez ustawienie `Errors` właściwości żądaną wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="6060f-128">Przy użyciu jednej z wartości dla `Status` uniemożliwia został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="6060f-129">Można również użyć `ContinueUpdateOnError` właściwości do obsługi błędów dla Zaktualizowano wierszy.</span><span class="sxs-lookup"><span data-stu-id="6060f-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="6060f-130">Jeśli `DataAdapter.ContinueUpdateOnError` jest `true`, gdy aktualizacja powoduje wiersza wyjątek tekst wyjątku jest umieszczany w `RowError` informacji określonego wiersza i przetwarzanie będzie kontynuowane bez generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6060f-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="6060f-131">Dzięki temu można odpowiadać na błędy podczas `Update` zakończeniu contrast do `RowUpdated` zdarzeń, dzięki czemu można odpowiadać na błędy, jeśli wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="6060f-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="6060f-132">Poniższy przykładowy kod przedstawia sposób zarówno Dodawanie i usuwanie programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6060f-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="6060f-133">`RowUpdating` Program obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="6060f-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="6060f-134">`RowUpdated` Obsługi zdarzeń dodaje informacje o błędzie do `RowError` właściwości wiersza w `DataSet`pomija wyjątek i kontynuuje przetwarzanie (dublowania zachowanie `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="6060f-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,   
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="6060f-135">FillError</span><span class="sxs-lookup"><span data-stu-id="6060f-135">FillError</span></span>  
 <span data-ttu-id="6060f-136">`DataAdapter` Problemów `FillError` zdarzenie, gdy wystąpi błąd podczas `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="6060f-137">Tego typu błędu często występuje, gdy nie można przekonwertować danych w wierszu dodawany do typu .NET Framework bez utratę dokładności.</span><span class="sxs-lookup"><span data-stu-id="6060f-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="6060f-138">W przypadku wystąpienia błędu podczas `Fill` operacji, bieżący wiersz nie została dodana do `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="6060f-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="6060f-139">`FillError` Zdarzeń umożliwia Usuń przyczynę błędu, a następnie dodaj wiersz, lub zignorować wykluczonych wiersza i kontynuować `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="6060f-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="6060f-140">`FillErrorEventArgs` Przekazany do `FillError` zdarzeń może zawierać kilka właściwości, które pozwalają odpowiedzieć i rozwiąż problemy.</span><span class="sxs-lookup"><span data-stu-id="6060f-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="6060f-141">W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6060f-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="6060f-142">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6060f-142">Property</span></span>|<span data-ttu-id="6060f-143">Opis</span><span class="sxs-lookup"><span data-stu-id="6060f-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="6060f-144">`Exception` Który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="6060f-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="6060f-145">`DataTable` Obiekt wypełniany w momencie wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="6060f-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="6060f-146">Tablica obiektów zawierająca wartości wiersza dodawane w momencie wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="6060f-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="6060f-147">Liczba porządkowa odwołuje się do elementu `Values` tablicy odpowiadają odwołań liczby porządkowej kolumny wiersza dodawany.</span><span class="sxs-lookup"><span data-stu-id="6060f-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="6060f-148">Na przykład `Values[0]` jest wartość, która została dodawany jako pierwszej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="6060f-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="6060f-149">Można wybrać, czy mają zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="6060f-150">Ustawienie `Continue` właściwości `false` spowoduje zatrzymanie bieżącej `Fill` operacji i wyjątek zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="6060f-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="6060f-151">Ustawienie `Continue` do `true` nadal `Fill` operacji pomimo błędu.</span><span class="sxs-lookup"><span data-stu-id="6060f-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="6060f-152">Poniższy przykładowy kod dodaje program obsługi zdarzeń dla `FillError` zdarzenie `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="6060f-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="6060f-153">W `FillError` kodu zdarzenia przykładzie określa, czy jest potencjalnie utrata dokładności, zapewniając możliwość udzielenia odpowiedzi na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6060f-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    args.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6060f-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6060f-154">See Also</span></span>  
 [<span data-ttu-id="6060f-155">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="6060f-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="6060f-156">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="6060f-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="6060f-157">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="6060f-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="6060f-158">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6060f-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="6060f-159">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="6060f-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
