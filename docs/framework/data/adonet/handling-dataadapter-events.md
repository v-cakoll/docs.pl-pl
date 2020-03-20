---
title: Obsługa zdarzeń elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: d01198d158c4e1c64f12e8a0756c3d4e599fce74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149547"
---
# <a name="handling-dataadapter-events"></a>Obsługa zdarzeń elementu DataAdapter
ADO.NET <xref:System.Data.Common.DataAdapter> udostępnia trzy zdarzenia, których można użyć do reagowania na zmiany wprowadzone do danych w źródle danych. W poniższej `DataAdapter` tabeli przedstawiono zdarzenia.  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|`RowUpdating`|Operacja UPDATE, INSERT lub DELETE w wierszu (wywołaniem `Update` jednej z metod) ma się rozpocząć.|  
|`RowUpdated`|Operacja UPDATE, INSERT lub DELETE w wierszu (wywołaniem `Update` jednej z metod) została zakończona.|  
|`FillError`|Wystąpił błąd podczas `Fill` operacji.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating i RowUpdated  
 `RowUpdating`jest wywoływana przed każdą aktualizacją wiersza z <xref:System.Data.DataSet> został przetworzony w źródle danych. `RowUpdated`jest wywoływana po każdej aktualizacji `DataSet` wiersza z został przetworzony w źródle danych. W rezultacie można użyć `RowUpdating` do modyfikowania zachowania aktualizacji, zanim to się stanie, aby zapewnić dodatkową obsługę, gdy nastąpi aktualizacja, aby zachować odwołanie do zaktualizowanego wiersza, aby anulować bieżącą aktualizację i zaplanować proces wsadowy do przetworzenia później i tak dalej. `RowUpdated`jest przydatne do reagowania na błędy i wyjątki, które występują podczas aktualizacji. Można dodać informacje o `DataSet`błędzie do , a także logiki ponawiania próby i tak dalej.  
  
 Argumenty <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> i przekazywane `RowUpdating` do `RowUpdated` zdarzeń i są `Command` następujące: właściwość, która odwołuje się do `Command` obiektu używanego do wykonywania aktualizacji; `Row` właściwość, która `DataRow` odwołuje się do obiektu zawierającego zaktualizowane informacje; `StatementType` właściwość dla tego, jaki rodzaj aktualizacji jest wykonywana; , `TableMapping`w stosownych przypadkach; `Status` i operacji.  
  
 Za pomocą `Status` właściwości można określić, czy wystąpił błąd podczas operacji i, w razie potrzeby, kontrolować akcje względem bieżących i wynikowych wierszy. Po wystąpieniu `Status` zdarzenia właściwość jest `Continue` `ErrorsOccurred`równa jednej lub . W poniższej tabeli przedstawiono wartości, do których można ustawić `Status` właściwość w celu kontrolowania późniejszych akcji podczas aktualizacji.  
  
|Stan|Opis|  
|------------|-----------------|  
|`Continue`|Kontynuuj operację aktualizacji.|  
|`ErrorsOccurred`|Przerwij operację aktualizacji i zgłosić wyjątek.|  
|`SkipCurrentRow`|Zignoruj bieżący wiersz i kontynuuj operację aktualizacji.|  
|`SkipAllRemainingRows`|Przerwij operację aktualizacji, ale nie zgłaszaj wyjątku.|  
  
 Ustawienie `Status` właściwości `ErrorsOccurred` powoduje wyjątek. Można kontrolować, który wyjątek `Errors` jest zgłaszany przez ustawienie właściwości do żądanego wyjątku. Przy użyciu jednej z `Status` innych wartości dla zapobiega wyjątek.  
  
 Można również użyć `ContinueUpdateOnError` właściwości do obsługi błędów dla zaktualizowanych wierszy. Jeśli `DataAdapter.ContinueUpdateOnError` `true`jest , gdy aktualizacja wiersza powoduje wyjątek, tekst wyjątku jest `RowError` umieszczany w informacjach o określonym wierszu, a przetwarzanie jest kontynuowane bez zgłaszania wyjątku. Dzięki temu można reagować na `Update` błędy po zakończeniu, `RowUpdated` w przeciwieństwie do zdarzenia, które umożliwia reagowanie na błędy po napotkaniu błędu.  
  
 Poniższy przykładowy kod pokazuje, jak zarówno dodać i usunąć programy obsługi zdarzeń. Program `RowUpdating` obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów za pomocą sygnatury czasowej. Program `RowUpdated` obsługi zdarzeń dodaje `RowError` informacje o błędzie `DataSet`do właściwości wiersza w , pomija wyjątek `ContinueUpdateOnError`  =  `true`i kontynuuje przetwarzanie (dublowanie zachowanie ).  
  
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
  
## <a name="fillerror"></a>Fillerror  
 Problemy `DataAdapter` zdarzenie, `FillError` gdy wystąpi błąd `Fill` podczas operacji. Ten typ błędu często występuje, gdy dane w wierszu dodawany nie można przekonwertować na typ .NET Framework bez utraty precyzji.  
  
 Jeśli podczas `Fill` operacji wystąpi błąd, bieżący wiersz `DataTable`nie zostanie dodany do pliku . Zdarzenie `FillError` umożliwia rozwiązanie błędu i dodanie wiersza lub zignorowanie wykluczonego `Fill` wiersza i kontynuowanie operacji.  
  
 Przekazywane `FillErrorEventArgs` do `FillError` zdarzenia może zawierać kilka właściwości, które umożliwiają reagowanie na błędy i rozwiązywania. W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`Errors`|To `Exception` się wydarzyło.|  
|`DataTable`|Obiekt `DataTable` jest wypełniany po wystąpieniu błędu.|  
|`Values`|Tablica obiektów, która zawiera wartości wiersza dodawany po wystąpieniu błędu. Odwołania porządkowe `Values` tablicy odpowiadają odwołaniach porządkowych kolumn dodawanych wierszy. Na przykład `Values[0]` jest wartością, która została dodana jako pierwsza kolumna wiersza.|  
|`Continue`|Umożliwia wybranie, czy zgłosić wyjątek. Ustawienie `Continue` właściwości, `false` aby zatrzymać `Fill` bieżącą operację i zostanie zgłoszony wyjątek. `Continue` Ustawienie, `true` aby `Fill` kontynuować operację pomimo błędu.|  
  
 Poniższy przykład kodu dodaje program `FillError` obsługi `DataAdapter`zdarzeń dla zdarzenia . W `FillError` kodzie zdarzenia w przykładzie określa, czy istnieje możliwość utraty precyzji, zapewniając możliwość odpowiedzi na wyjątek.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Obsługa zdarzeń elementu DataSet](./dataset-datatable-dataview/handling-dataset-events.md)
- [Obsługa zdarzeń elementu DataTable](./dataset-datatable-dataview/handling-datatable-events.md)
- [Zdarzenia](../../../standard/events/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
