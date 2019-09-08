---
title: Obsługa zdarzeń elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 8438a7b54ca19625687ab96386384cf62ae62d11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783800"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="59810-102">Obsługa zdarzeń elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="59810-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="59810-103">ADO.NET <xref:System.Data.Common.DataAdapter> ujawnia trzy zdarzenia, których można użyć w celu reagowania na zmiany wprowadzone do danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="59810-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="59810-104">W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="59810-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="59810-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="59810-105">Event</span></span>|<span data-ttu-id="59810-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59810-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="59810-107">Zostanie rozpoczęta operacja aktualizacji, wstawiania lub usuwania w wierszu (przez wywołanie jednej z `Update` metod).</span><span class="sxs-lookup"><span data-stu-id="59810-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="59810-108">Operacja aktualizowania, wstawiania lub usuwania w wierszu (przez wywołanie jednej z `Update` metod) została ukończona.</span><span class="sxs-lookup"><span data-stu-id="59810-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="59810-109">Wystąpił błąd podczas `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="59810-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="59810-110">RowUpdating i RowUpdated</span><span class="sxs-lookup"><span data-stu-id="59810-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="59810-111">`RowUpdating`jest uruchamiany przed przetworzeniem aktualizacji do wiersza z <xref:System.Data.DataSet> programu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="59810-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="59810-112">`RowUpdated`jest uruchamiany po przetworzeniu dowolnej aktualizacji wiersza z programu `DataSet` w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="59810-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="59810-113">W związku z tym można użyć `RowUpdating` programu w celu zmodyfikowania zachowania aktualizacji, aby zapewnić dodatkową obsługę w przypadku wystąpienia aktualizacji, aby zachować odwołanie do zaktualizowanego wiersza, anulować bieżącą aktualizację i zaplanować przetwarzanie zadania wsadowego w późniejszym czasie. itd.</span><span class="sxs-lookup"><span data-stu-id="59810-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="59810-114">`RowUpdated`jest przydatne do reagowania na błędy i wyjątki, które występują podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="59810-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="59810-115">Można dodać informacje o błędzie do `DataSet`, a także logiki ponawiania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="59810-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="59810-116">`Command` `Command` `Row` Argumenty <xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> przekazane do `RowUpdating` zdarzeń i`RowUpdated` są następujące: właściwość, która odwołuje się do obiektu używanego do przeprowadzenia aktualizacji; a Właściwość, `DataRow` która odwołuje się do obiektu zawierającego zaktualizowane informacje `StatementType` ; Właściwość `TableMapping`, dla której jest przeprowadzana aktualizacja, a jeśli ma zastosowanie, a także `Status` od operacji.</span><span class="sxs-lookup"><span data-stu-id="59810-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="59810-117">Możesz użyć `Status` właściwości, aby określić, czy wystąpił błąd podczas operacji i, w razie potrzeby, kontrolować akcje względem bieżących i powstających wierszy.</span><span class="sxs-lookup"><span data-stu-id="59810-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="59810-118">Gdy wystąpi zdarzenie, właściwość `Status` `Continue` ma wartość lub `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="59810-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="59810-119">W poniższej tabeli przedstawiono wartości, do których można ustawić `Status` właściwość w celu kontrolowania późniejszych akcji podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="59810-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="59810-120">Stan</span><span class="sxs-lookup"><span data-stu-id="59810-120">Status</span></span>|<span data-ttu-id="59810-121">Opis</span><span class="sxs-lookup"><span data-stu-id="59810-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="59810-122">Kontynuuj operację aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="59810-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="59810-123">Przerwij operację aktualizacji i Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59810-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="59810-124">Zignoruj bieżący wiersz i Kontynuuj operację aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="59810-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="59810-125">Przerwij operację aktualizacji, ale nie zgłaszaj wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59810-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="59810-126">Ustawienie właściwości `Status` w taki `ErrorsOccurred` sposób, aby wywołał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59810-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="59810-127">Można kontrolować, który wyjątek jest zgłaszany przez ustawienie `Errors` właściwości na żądany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59810-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="59810-128">Użycie jednej z pozostałych wartości `Status` uniemożliwia zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59810-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="59810-129">Możesz również użyć właściwości, `ContinueUpdateOnError` aby obsłużyć błędy dla zaktualizowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="59810-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="59810-130">Jeśli `DataAdapter.ContinueUpdateOnError` ma `true`wartość, gdy zostanie zgłoszony wyjątek w aktualizacji wiersza, tekst `RowError` wyjątku zostanie umieszczony w informacjach o określonym wierszu i przetwarzanie będzie kontynuowane bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59810-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="59810-131">Dzięki temu można reagować na błędy po `Update` zakończeniu, w przeciwieństwie `RowUpdated` do zdarzenia, które pozwala na reagowanie na błędy po napotkaniu błędu.</span><span class="sxs-lookup"><span data-stu-id="59810-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="59810-132">Poniższy przykład kodu pokazuje, jak dodawać i usuwać programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="59810-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="59810-133">Program `RowUpdating` obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnaturą czasową.</span><span class="sxs-lookup"><span data-stu-id="59810-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="59810-134"> =  `DataSet` `ContinueUpdateOnError` `true`Procedura obsługi `RowError` zdarzeń dodaje informacje o błędzie do właściwości wiersza w, pomija wyjątek i kontynuuje przetwarzanie (dublowanie zachowania). `RowUpdated`</span><span class="sxs-lookup"><span data-stu-id="59810-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="59810-135">FillError</span><span class="sxs-lookup"><span data-stu-id="59810-135">FillError</span></span>  
 <span data-ttu-id="59810-136">Generuje zdarzenie, `FillError` gdy wystąpi błąd podczas `Fill` operacji. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="59810-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="59810-137">Ten typ błędu często występuje, gdy dane w dodawanym wierszu nie mogą zostać skonwertowane na typ .NET Framework bez utraty dokładności.</span><span class="sxs-lookup"><span data-stu-id="59810-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="59810-138">Jeśli wystąpi błąd podczas `Fill` operacji, bieżący wiersz nie zostanie dodany `DataTable`do.</span><span class="sxs-lookup"><span data-stu-id="59810-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="59810-139">Zdarzenie umożliwia rozwiązanie błędu i dodanie wiersza lub zignorowanie wykluczonego wiersza i `Fill` kontynuowanie operacji. `FillError`</span><span class="sxs-lookup"><span data-stu-id="59810-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="59810-140">Przesłany`FillError` do zdarzenia może zawierać kilka właściwości, które umożliwiają reagowanie na i `FillErrorEventArgs` Rozwiązywanie błędów.</span><span class="sxs-lookup"><span data-stu-id="59810-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="59810-141">W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="59810-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="59810-142">Właściwość</span><span class="sxs-lookup"><span data-stu-id="59810-142">Property</span></span>|<span data-ttu-id="59810-143">Opis</span><span class="sxs-lookup"><span data-stu-id="59810-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="59810-144">, `Exception` Który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="59810-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="59810-145">`DataTable` Obiekt wypełniany po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="59810-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="59810-146">Tablica obiektów, która zawiera wartości dodawanego wiersza po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="59810-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="59810-147">Odwołania porządkowe `Values` tablicy odpowiadają odwołaniem porządkowym kolumn dodawanego wiersza.</span><span class="sxs-lookup"><span data-stu-id="59810-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="59810-148">Na przykład `Values[0]` jest wartością, która była dodawana jako pierwsza kolumna wiersza.</span><span class="sxs-lookup"><span data-stu-id="59810-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="59810-149">Umożliwia wybranie, czy zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59810-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="59810-150">Ustawienie właściwości na `false` zatrzyma bieżącą `Fill` operację i zostanie zgłoszony wyjątek. `Continue`</span><span class="sxs-lookup"><span data-stu-id="59810-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="59810-151">Ustawienie `Continue` do `true` kontynuowania`Fill` operacji pomimo błędu.</span><span class="sxs-lookup"><span data-stu-id="59810-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="59810-152">Poniższy przykład kodu dodaje procedurę obsługi zdarzeń dla `FillError` zdarzenia. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="59810-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="59810-153">W kodzie `FillError` zdarzenia, przykład określa, czy jest możliwe zmniejszenie dokładności, zapewniając możliwość reagowania na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59810-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
    myRow.RowError = _  
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
    myRow.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="59810-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59810-154">See also</span></span>

- [<span data-ttu-id="59810-155">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="59810-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="59810-156">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="59810-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="59810-157">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="59810-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="59810-158">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="59810-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="59810-159">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="59810-159">ADO.NET Overview</span></span>](ado-net-overview.md)
