---
title: "Obsługa zdarzeń element DataAdapter"
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
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc482e2508dedde88e40390b4e4ce3edcab8189d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="handling-dataadapter-events"></a>Obsługa zdarzeń element DataAdapter
ADO.NET <xref:System.Data.Common.DataAdapter> udostępnia trzy zdarzenia, które służą do reagowania na zmiany wprowadzone w danych w źródle danych. W poniższej tabeli przedstawiono `DataAdapter` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`RowUpdating`|Operacja AKTUALIZOWANIA, WSTAWIANIA lub usuwania wiersza (przez wywołanie do jednego z `Update` metody) ma rozpocząć.|  
|`RowUpdated`|Operacja AKTUALIZOWANIA, WSTAWIANIA lub usuwania w wierszu (przez wywołanie do jednego z `Update` metody) została ukończona.|  
|`FillError`|Wystąpił błąd podczas `Fill` operacji.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating i RowUpdated  
 `RowUpdating`jest wywoływane przed wykonaniem dowolnej aktualizacji na wiersz z <xref:System.Data.DataSet> został przetworzony w źródle danych. `RowUpdated`jest wywoływane po aktualizacji jedną na wiersz z `DataSet` został przetworzony w źródle danych. W związku z tym można użyć `RowUpdating` do modyfikowania zachowania aktualizacji przed zdarza się, w celu zapewnienia obsługi dodatkowych, gdy nastąpi aktualizacja, aby zachować odwołanie do zaktualizowany wiersz, aby anulować harmonogram i bieżącej aktualizacji dla partii przetwarzanie do przetworzenia później , i tak dalej. `RowUpdated`jest przydatne w przypadku odpowiedzi na błędy i wyjątków występujących podczas aktualizacji. Można dodać informacje o błędzie do `DataSet`, a także Logika ponawiania próby i tak dalej.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> i <xref:System.Data.Common.RowUpdatedEventArgs> argumentów przekazanych do `RowUpdating` i `RowUpdated` zdarzenia są następujące: `Command` właściwość, która odwołuje się do `Command` obiekt używany do przeprowadzenia aktualizacji; `Row` Właściwość, która odwołuje się do `DataRow` obiekt zawierający zaktualizowane informacje; `StatementType` właściwości, dla jakiego rodzaju aktualizacji jest wykonywane; `TableMapping`, jeśli ma to zastosowanie; i `Status` operacji.  
  
 Można użyć `Status` właściwości w celu określenia, jeśli wystąpił błąd podczas operacji, a jeśli potrzebne, kontrolowanie akcji względem bieżących i wynikowy wierszy. Po wystąpieniu zdarzenia, `Status` właściwości jest równa albo `Continue` lub `ErrorsOccurred`. W poniższej tabeli przedstawiono wartości, które można ustawić `Status` właściwości w celu kontrolowania późniejsze akcje podczas aktualizacji.  
  
|Stan|Opis|  
|------------|-----------------|  
|`Continue`|Kontynuowanie operacji aktualizacji.|  
|`ErrorsOccurred`|Przerwij operacji aktualizowania i Zgłoś wyjątek.|  
|`SkipCurrentRow`|Ignoruj bieżący wiersz i kontynuowania operacji aktualizacji.|  
|`SkipAllRemainingRows`|Przerwanie operacji aktualizacji, ale zgłosiła wyjątek.|  
  
 Ustawienie `Status` właściwości `ErrorsOccurred` powoduje zgłoszenie wyjątku zostanie wygenerowany. Można kontrolować, które wyjątku przez ustawienie `Errors` właściwości żądaną wyjątek. Przy użyciu jednej z wartości dla `Status` uniemożliwia został zgłoszony wyjątek.  
  
 Można również użyć `ContinueUpdateOnError` właściwości do obsługi błędów dla Zaktualizowano wierszy. Jeśli `DataAdapter.ContinueUpdateOnError` jest `true`, gdy aktualizacja powoduje wiersza wyjątek tekst wyjątku jest umieszczany w `RowError` informacji określonego wiersza i przetwarzanie będzie kontynuowane bez generowania wyjątku. Dzięki temu można odpowiadać na błędy podczas `Update` zakończeniu contrast do `RowUpdated` zdarzeń, dzięki czemu można odpowiadać na błędy, jeśli wystąpi błąd.  
  
 Poniższy przykładowy kod przedstawia sposób zarówno Dodawanie i usuwanie programów obsługi zdarzeń. `RowUpdating` Program obsługi zdarzeń zapisuje dziennik wszystkich usuniętych rekordów z sygnatury czasowej. `RowUpdated` Obsługi zdarzeń dodaje informacje o błędzie do `RowError` właściwości wiersza w `DataSet`pomija wyjątek i kontynuuje przetwarzanie (dublowania zachowanie `ContinueUpdateOnError`  =  `true`).  
  
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
 `DataAdapter` Problemów `FillError` zdarzenie, gdy wystąpi błąd podczas `Fill` operacji. Tego typu błędu często występuje, gdy nie można przekonwertować danych w wierszu dodawany do typu .NET Framework bez utratę dokładności.  
  
 W przypadku wystąpienia błędu podczas `Fill` operacji, bieżący wiersz nie została dodana do `DataTable`. `FillError` Zdarzeń umożliwia Usuń przyczynę błędu, a następnie dodaj wiersz, lub zignorować wykluczonych wiersza i kontynuować `Fill` operacji.  
  
 `FillErrorEventArgs` Przekazany do `FillError` zdarzeń może zawierać kilka właściwości, które pozwalają odpowiedzieć i rozwiąż problemy. W poniższej tabeli przedstawiono właściwości `FillErrorEventArgs` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`Errors`|`Exception` Który wystąpił.|  
|`DataTable`|`DataTable` Obiekt wypełniany w momencie wystąpienia błędu.|  
|`Values`|Tablica obiektów zawierająca wartości wiersza dodawane w momencie wystąpienia błędu. Liczba porządkowa odwołuje się do elementu `Values` tablicy odpowiadają odwołań liczby porządkowej kolumny wiersza dodawany. Na przykład `Values[0]` jest wartość, która została dodawany jako pierwszej kolumny wiersza.|  
|`Continue`|Można wybrać, czy mają zostać zgłoszony wyjątek. Ustawienie `Continue` właściwości `false` spowoduje zatrzymanie bieżącej `Fill` operacji i wyjątek zostanie zgłoszony. Ustawienie `Continue` do `true` nadal `Fill` operacji pomimo błędu.|  
  
 Poniższy przykładowy kod dodaje program obsługi zdarzeń dla `FillError` zdarzenie `DataAdapter`. W `FillError` kodu zdarzenia przykładzie określa, czy jest potencjalnie utrata dokładności, zapewniając możliwość udzielenia odpowiedzi na wyjątek.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
