---
title: Obsługa zdarzeń elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 7013f855fb54f6c67c569ccabda91727359d22b2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398763"
---
# <a name="handling-dataadapter-events"></a>Obsługa zdarzeń elementu DataAdapter
ADO.NET <xref:System.Data.Common.DataAdapter> udostępnia trzy zdarzenia, które umożliwiają reagowanie na zmiany wprowadzone w danych w źródle danych. W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`RowUpdating`|W wierszu operacji UPDATE, INSERT czy DELETE (przez wywołanie jednej z `Update` metody) jest gotowy do rozpoczęcia.|  
|`RowUpdated`|W wierszu operacji UPDATE, INSERT czy DELETE (przez wywołanie jednej z `Update` metody) zostało ukończone.|  
|`FillError`|Wystąpił błąd podczas `Fill` operacji.|  
  
## <a name="rowupdating-and-rowupdated"></a>— RowUpdating i RowUpdated  
 `RowUpdating` jest wywoływane przed wykonaniem dowolnej aktualizacji na wiersz z <xref:System.Data.DataSet> został przetworzony w źródle danych. `RowUpdated` jest wywoływane po dowolnej aktualizacji do wiersza z `DataSet` został przetworzony w źródle danych. W rezultacie, możesz użyć `RowUpdating` Aby zmodyfikować zachowanie aktualizacji przed zdarza się, aby zapewnić obsługę dodatkowych, gdy aktualizacja zostanie przeprowadzona, do przechowywania odwołań do zaktualizowany wiersz, aby anulować bieżącej aktualizacji i harmonogramu, jego partii przetwarzania do przetworzenia później , i tak dalej. `RowUpdated` przydaje się w odpowiedzi na błędy i wyjątki, które występują podczas aktualizacji. Można dodać informacji o błędzie do `DataSet`, a także Logika ponawiania próby i tak dalej.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> argumenty przekazywane do `RowUpdating` i `RowUpdated` zdarzenia obejmują następujące elementy: `Command` właściwość, która odwołuje się do `Command` obiekt używany do wykonywania aktualizacji; `Row` Właściwość, która odwołuje się do `DataRow` obiekt, który zawiera zaktualizowane informacje; `StatementType` właściwości, dla jakiego rodzaju aktualizacji jest wykonywana; `TableMapping`, jeśli ma to zastosowanie; i `Status` operacji.  
  
 Możesz użyć `Status` właściwość, aby ustalić, czy wystąpił błąd podczas operacji i, jeśli pożądane, aby kontrolować działania względem wierszy bieżące i planowane wynikowy. Po wystąpieniu zdarzenia, `Status` właściwości jest równa albo `Continue` lub `ErrorsOccurred`. W poniższej tabeli przedstawiono wartości, do których można ustawić `Status` właściwości w celu kontrolowania kolejnych akcjach podczas aktualizacji.  
  
|Stan|Opis|  
|------------|-----------------|  
|`Continue`|Kontynuowanie operacji aktualizacji.|  
|`ErrorsOccurred`|Przerwij operację aktualizacji i zgłosić wyjątek.|  
|`SkipCurrentRow`|Ignoruj bieżący wiersz i kontynuowania operacji aktualizacji.|  
|`SkipAllRemainingRows`|Przerwij operację aktualizacji, ale nie zgłasza wyjątku.|  
  
 Ustawienie `Status` właściwość `ErrorsOccurred` powoduje zgłoszenie wyjątku. Można kontrolować, które wyjątek jest generowany przez ustawienie `Errors` właściwość do żądanej wyjątku. Przy użyciu jednej z innych wartości `Status` zapobiega jest zgłaszany wyjątek.  
  
 Można również użyć `ContinueUpdateOnError` właściwości do obsługi błędów, aby uzyskać zaktualizowane wiersze. Jeśli `DataAdapter.ContinueUpdateOnError` jest `true`, gdy aktualizacja wiersza powoduje wyjątek, tekst wyjątku jest umieszczana w `RowError` informacji określonego wiersza i przetwarzanie będzie kontynuowane bez zgłoszenia wyjątku. Dzięki temu można reagować na błędy podczas `Update` zostało zakończone, w przeciwieństwie do `RowUpdated` zdarzenie, które pozwala odpowiedzieć na błędy po napotkaniu błędu.  
  
 Poniższy przykład kodu pokazuje, jak dodawanie i usuwanie programów obsługi zdarzeń. `RowUpdating` Program obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnatury czasowej. `RowUpdated` Programu obsługi zdarzeń dodaje informacje o błędzie do `RowError` właściwości wiersza w `DataSet`, pomija wyjątek i kontynuuje przetwarzanie (dublowanie zachowanie `ContinueUpdateOnError`  =  `true`).  
  
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
 `DataAdapter` Problemów `FillError` zdarzenie, gdy wystąpi błąd w czasie `Fill` operacji. Błędy tego typu występuje najczęściej w przypadku, gdy nie można przekonwertować danych w wierszu dodawany typ .NET Framework bez pewną utratą dokładności.  
  
 Jeśli wystąpi błąd podczas `Fill` operacji, bieżący wiersz nie został dodany do `DataTable`. `FillError` Zdarzenie pozwala naprawić błąd i Dodaj wiersz lub wykluczone wiersz zignorować i kontynuować `Fill` operacji.  
  
 `FillErrorEventArgs` Przekazany do `FillError` zdarzeń może zawierać kilka właściwości, które umożliwiają reagowanie na i naprawić błędy. W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`Errors`|`Exception` Który wystąpił.|  
|`DataTable`|`DataTable` Object wypełniany w momencie wystąpienia błędu.|  
|`Values`|Tablica obiektów zawierająca wartości wiersza dodawane w momencie wystąpienia błędu. Numer porządkowy odwołania `Values` tablicy odpowiada porządkowe odwołania kolumny wiersza dodawany. Na przykład `Values[0]` jest wartością, która została dodawany jako pierwszej kolumny wiersza.|  
|`Continue`|Pozwala określić, czy nie zgłasza wyjątku. Ustawienie `Continue` właściwości `false` zostanie zatrzymany bieżącego `Fill` operacji, a wyjątek zostanie zgłoszony. Ustawienie `Continue` do `true` nadal `Fill` operację pomimo błędów.|  
  
 Poniższy przykład kodu dodaje program obsługi zdarzeń dla `FillError` zdarzenia `DataAdapter`. W `FillError` kod zdarzenia przykład określa, czy jest ryzyko utraty dokładności, zapewniając możliwość udzielenia odpowiedzi na wyjątek.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Obsługa zdarzeń elementu DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [Obsługa zdarzeń elementu DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
