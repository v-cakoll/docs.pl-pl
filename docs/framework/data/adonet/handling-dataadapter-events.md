---
title: Obsługa zdarzeń elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 864a9072b38054557b2583f505e6e7827c02d2de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180755"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="3ae2e-102">Obsługa zdarzeń elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="3ae2e-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="3ae2e-103">ADO.NET <xref:System.Data.Common.DataAdapter> udostępnia trzy zdarzenia, które umożliwiają reagowanie na zmiany wprowadzone w danych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="3ae2e-104">W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="3ae2e-105">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="3ae2e-105">Event</span></span>|<span data-ttu-id="3ae2e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3ae2e-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="3ae2e-107">W wierszu operacji UPDATE, INSERT czy DELETE (przez wywołanie jednej z `Update` metody) jest gotowy do rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="3ae2e-108">W wierszu operacji UPDATE, INSERT czy DELETE (przez wywołanie jednej z `Update` metody) zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="3ae2e-109">Wystąpił błąd podczas `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="3ae2e-110">— RowUpdating i RowUpdated</span><span class="sxs-lookup"><span data-stu-id="3ae2e-110">RowUpdating and RowUpdated</span></span>  
 `RowUpdating` <span data-ttu-id="3ae2e-111">jest wywoływane przed wykonaniem dowolnej aktualizacji na wiersz z <xref:System.Data.DataSet> został przetworzony w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-111">is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> `RowUpdated` <span data-ttu-id="3ae2e-112">jest wywoływane po dowolnej aktualizacji do wiersza z `DataSet` został przetworzony w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-112">is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="3ae2e-113">W rezultacie, możesz użyć `RowUpdating` Aby zmodyfikować zachowanie aktualizacji przed zdarza się, aby zapewnić obsługę dodatkowych, gdy aktualizacja zostanie przeprowadzona, do przechowywania odwołań do zaktualizowany wiersz, aby anulować bieżącej aktualizacji i harmonogramu, jego partii przetwarzania do przetworzenia później , i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> `RowUpdated` <span data-ttu-id="3ae2e-114">przydaje się w odpowiedzi na błędy i wyjątki, które występują podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-114">is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="3ae2e-115">Można dodać informacji o błędzie do `DataSet`, a także Logika ponawiania próby i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="3ae2e-116"><xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> argumenty przekazywane do `RowUpdating` i `RowUpdated` zdarzenia obejmują następujące elementy: `Command` właściwość, która odwołuje się do `Command` obiekt używany do wykonywania aktualizacji; `Row` Właściwość, która odwołuje się do `DataRow` obiekt, który zawiera zaktualizowane informacje; `StatementType` właściwości, dla jakiego rodzaju aktualizacji jest wykonywana; `TableMapping`, jeśli ma to zastosowanie; i `Status` operacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="3ae2e-117">Możesz użyć `Status` właściwość, aby ustalić, czy wystąpił błąd podczas operacji i, jeśli pożądane, aby kontrolować działania względem wierszy bieżące i planowane wynikowy.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="3ae2e-118">Po wystąpieniu zdarzenia, `Status` właściwości jest równa albo `Continue` lub `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="3ae2e-119">W poniższej tabeli przedstawiono wartości, do których można ustawić `Status` właściwości w celu kontrolowania kolejnych akcjach podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="3ae2e-120">Stan</span><span class="sxs-lookup"><span data-stu-id="3ae2e-120">Status</span></span>|<span data-ttu-id="3ae2e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3ae2e-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="3ae2e-122">Kontynuowanie operacji aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="3ae2e-123">Przerwij operację aktualizacji i zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="3ae2e-124">Ignoruj bieżący wiersz i kontynuowania operacji aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="3ae2e-125">Przerwij operację aktualizacji, ale nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="3ae2e-126">Ustawienie `Status` właściwość `ErrorsOccurred` powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="3ae2e-127">Można kontrolować, które wyjątek jest generowany przez ustawienie `Errors` właściwość do żądanej wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="3ae2e-128">Przy użyciu jednej z innych wartości `Status` zapobiega jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="3ae2e-129">Można również użyć `ContinueUpdateOnError` właściwości do obsługi błędów, aby uzyskać zaktualizowane wiersze.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="3ae2e-130">Jeśli `DataAdapter.ContinueUpdateOnError` jest `true`, gdy aktualizacja wiersza powoduje wyjątek, tekst wyjątku jest umieszczana w `RowError` informacji określonego wiersza i przetwarzanie będzie kontynuowane bez zgłoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="3ae2e-131">Dzięki temu można reagować na błędy podczas `Update` zostało zakończone, w przeciwieństwie do `RowUpdated` zdarzenie, które pozwala odpowiedzieć na błędy po napotkaniu błędu.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="3ae2e-132">Poniższy przykład kodu pokazuje, jak dodawanie i usuwanie programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="3ae2e-133">`RowUpdating` Program obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="3ae2e-134">`RowUpdated` Programu obsługi zdarzeń dodaje informacje o błędzie do `RowError` właściwości wiersza w `DataSet`, pomija wyjątek i kontynuuje przetwarzanie (dublowanie zachowanie `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="3ae2e-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="3ae2e-135">FillError</span><span class="sxs-lookup"><span data-stu-id="3ae2e-135">FillError</span></span>  
 <span data-ttu-id="3ae2e-136">`DataAdapter` Problemów `FillError` zdarzenie, gdy wystąpi błąd w czasie `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="3ae2e-137">Błędy tego typu występuje najczęściej w przypadku, gdy nie można przekonwertować danych w wierszu dodawany typ .NET Framework bez pewną utratą dokładności.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="3ae2e-138">Jeśli wystąpi błąd podczas `Fill` operacji, bieżący wiersz nie został dodany do `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="3ae2e-139">`FillError` Zdarzenie pozwala naprawić błąd i Dodaj wiersz lub wykluczone wiersz zignorować i kontynuować `Fill` operacji.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="3ae2e-140">`FillErrorEventArgs` Przekazany do `FillError` zdarzeń może zawierać kilka właściwości, które umożliwiają reagowanie na i naprawić błędy.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="3ae2e-141">W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="3ae2e-142">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3ae2e-142">Property</span></span>|<span data-ttu-id="3ae2e-143">Opis</span><span class="sxs-lookup"><span data-stu-id="3ae2e-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="3ae2e-144">`Exception` Który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="3ae2e-145">`DataTable` Object wypełniany w momencie wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="3ae2e-146">Tablica obiektów zawierająca wartości wiersza dodawane w momencie wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="3ae2e-147">Numer porządkowy odwołania `Values` tablicy odpowiada porządkowe odwołania kolumny wiersza dodawany.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="3ae2e-148">Na przykład `Values[0]` jest wartością, która została dodawany jako pierwszej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="3ae2e-149">Pozwala określić, czy nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="3ae2e-150">Ustawienie `Continue` właściwości `false` zostanie zatrzymany bieżącego `Fill` operacji, a wyjątek zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="3ae2e-151">Ustawienie `Continue` do `true` nadal `Fill` operację pomimo błędów.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="3ae2e-152">Poniższy przykład kodu dodaje program obsługi zdarzeń dla `FillError` zdarzenia `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="3ae2e-153">W `FillError` kod zdarzenia przykład określa, czy jest ryzyko utraty dokładności, zapewniając możliwość udzielenia odpowiedzi na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3ae2e-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ae2e-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ae2e-154">See also</span></span>

- [<span data-ttu-id="3ae2e-155">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="3ae2e-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="3ae2e-156">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="3ae2e-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="3ae2e-157">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="3ae2e-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="3ae2e-158">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3ae2e-158">Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="3ae2e-159">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="3ae2e-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
