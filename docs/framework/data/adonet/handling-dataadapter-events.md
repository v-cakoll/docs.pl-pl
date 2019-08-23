---
title: Obsługa zdarzeń elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a63e65289a51a7647270a978cec11ef6bc201e45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962756"
---
# <a name="handling-dataadapter-events"></a>Obsługa zdarzeń elementu DataAdapter
ADO.NET <xref:System.Data.Common.DataAdapter> ujawnia trzy zdarzenia, których można użyć w celu reagowania na zmiany wprowadzone do danych w źródle danych. W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`RowUpdating`|Zostanie rozpoczęta operacja aktualizacji, wstawiania lub usuwania w wierszu (przez wywołanie jednej z `Update` metod).|  
|`RowUpdated`|Operacja aktualizowania, wstawiania lub usuwania w wierszu (przez wywołanie jednej z `Update` metod) została ukończona.|  
|`FillError`|Wystąpił błąd podczas `Fill` operacji.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating i RowUpdated  
 `RowUpdating`jest uruchamiany przed przetworzeniem aktualizacji do wiersza z <xref:System.Data.DataSet> programu w źródle danych. `RowUpdated`jest uruchamiany po przetworzeniu dowolnej aktualizacji wiersza z programu `DataSet` w źródle danych. W związku z tym można użyć `RowUpdating` programu w celu zmodyfikowania zachowania aktualizacji, aby zapewnić dodatkową obsługę w przypadku wystąpienia aktualizacji, aby zachować odwołanie do zaktualizowanego wiersza, anulować bieżącą aktualizację i zaplanować przetwarzanie zadania wsadowego w późniejszym czasie. itd. `RowUpdated`jest przydatne do reagowania na błędy i wyjątki, które występują podczas aktualizacji. Można dodać informacje o błędzie do `DataSet`, a także logiki ponawiania i tak dalej.  
  
 `Command` `Command` `Row` Argumenty <xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> przekazane do `RowUpdating` zdarzeń i`RowUpdated` są następujące: właściwość, która odwołuje się do obiektu używanego do przeprowadzenia aktualizacji; a Właściwość, `DataRow` która odwołuje się do obiektu zawierającego zaktualizowane informacje `StatementType` ; Właściwość `TableMapping`, dla której jest przeprowadzana aktualizacja, a jeśli ma zastosowanie, a także `Status` od operacji.  
  
 Możesz użyć `Status` właściwości, aby określić, czy wystąpił błąd podczas operacji i, w razie potrzeby, kontrolować akcje względem bieżących i powstających wierszy. Gdy wystąpi zdarzenie, właściwość `Status` `Continue` ma wartość lub `ErrorsOccurred`. W poniższej tabeli przedstawiono wartości, do których można ustawić `Status` właściwość w celu kontrolowania późniejszych akcji podczas aktualizacji.  
  
|Stan|Opis|  
|------------|-----------------|  
|`Continue`|Kontynuuj operację aktualizacji.|  
|`ErrorsOccurred`|Przerwij operację aktualizacji i Zgłoś wyjątek.|  
|`SkipCurrentRow`|Zignoruj bieżący wiersz i Kontynuuj operację aktualizacji.|  
|`SkipAllRemainingRows`|Przerwij operację aktualizacji, ale nie zgłaszaj wyjątku.|  
  
 Ustawienie właściwości `Status` w taki `ErrorsOccurred` sposób, aby wywołał wyjątek. Można kontrolować, który wyjątek jest zgłaszany przez ustawienie `Errors` właściwości na żądany wyjątek. Użycie jednej z pozostałych wartości `Status` uniemożliwia zgłaszanie wyjątku.  
  
 Możesz również użyć właściwości, `ContinueUpdateOnError` aby obsłużyć błędy dla zaktualizowanych wierszy. Jeśli `DataAdapter.ContinueUpdateOnError` ma `true`wartość, gdy zostanie zgłoszony wyjątek w aktualizacji wiersza, tekst `RowError` wyjątku zostanie umieszczony w informacjach o określonym wierszu i przetwarzanie będzie kontynuowane bez zgłaszania wyjątku. Dzięki temu można reagować na błędy po `Update` zakończeniu, w przeciwieństwie `RowUpdated` do zdarzenia, które pozwala na reagowanie na błędy po napotkaniu błędu.  
  
 Poniższy przykład kodu pokazuje, jak dodawać i usuwać programy obsługi zdarzeń. Program `RowUpdating` obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnaturą czasową.  =  `DataSet` `ContinueUpdateOnError` `true`Procedura obsługi `RowError` zdarzeń dodaje informacje o błędzie do właściwości wiersza w, pomija wyjątek i kontynuuje przetwarzanie (dublowanie zachowania). `RowUpdated`  
  
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
  
## <a name="fillerror"></a>FillError  
 Generuje zdarzenie, `FillError` gdy wystąpi błąd podczas `Fill` operacji. `DataAdapter` Ten typ błędu często występuje, gdy dane w dodawanym wierszu nie mogą zostać skonwertowane na typ .NET Framework bez utraty dokładności.  
  
 Jeśli wystąpi błąd podczas `Fill` operacji, bieżący wiersz nie zostanie dodany `DataTable`do. Zdarzenie umożliwia rozwiązanie błędu i dodanie wiersza lub zignorowanie wykluczonego wiersza i `Fill` kontynuowanie operacji. `FillError`  
  
 Przesłany`FillError` do zdarzenia może zawierać kilka właściwości, które umożliwiają reagowanie na i `FillErrorEventArgs` Rozwiązywanie błędów. W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`Errors`|, `Exception` Który wystąpił.|  
|`DataTable`|`DataTable` Obiekt wypełniany po wystąpieniu błędu.|  
|`Values`|Tablica obiektów, która zawiera wartości dodawanego wiersza po wystąpieniu błędu. Odwołania porządkowe `Values` tablicy odpowiadają odwołaniem porządkowym kolumn dodawanego wiersza. Na przykład `Values[0]` jest wartością, która była dodawana jako pierwsza kolumna wiersza.|  
|`Continue`|Umożliwia wybranie, czy zgłosić wyjątek. Ustawienie właściwości na `false` zatrzyma bieżącą `Fill` operację i zostanie zgłoszony wyjątek. `Continue` Ustawienie `Continue` do `true` kontynuowania`Fill` operacji pomimo błędu.|  
  
 Poniższy przykład kodu dodaje procedurę obsługi zdarzeń dla `FillError` zdarzenia. `DataAdapter` W kodzie `FillError` zdarzenia, przykład określa, czy jest możliwe zmniejszenie dokładności, zapewniając możliwość reagowania na wyjątek.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Obsługa zdarzeń elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [Obsługa zdarzeń elementu DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [Zdarzenia](../../../standard/events/index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
