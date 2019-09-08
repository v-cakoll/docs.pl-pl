---
title: Wykonywanie operacji wsadowych za pomocą elementów DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 8667cffb032daf0043915d3bee7127ef9b70756b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794507"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Wykonywanie operacji wsadowych za pomocą elementów DataAdapter
Obsługa usługi Batch w programie ADO.NET <xref:System.Data.Common.DataAdapter> umożliwia grupowanie operacji wstawiania, aktualizowania i usuwania <xref:System.Data.DataSet> z serwera lub <xref:System.Data.DataTable> na serwerze, a nie wysyłanie jednej operacji jednocześnie. Zmniejszenie liczby rund do serwera zwykle skutkuje znaczącym wzrostem wydajności. Aktualizacje usługi Batch są obsługiwane dla dostawców danych platformy .NET dla SQL Server<xref:System.Data.SqlClient>() i Oracle<xref:System.Data.OracleClient>().  
  
 Podczas aktualizowania bazy danych przy użyciu zmian z <xref:System.Data.DataSet> poprzednich wersji programu ADO.NET `Update` , Metoda `DataAdapter` wykonanych aktualizacji bazy danych o jeden wiersz w danym momencie. Podczas iteracji przez wiersze w określonym <xref:System.Data.DataTable>, zbadano każdy <xref:System.Data.DataRow> , aby sprawdzić, czy został on zmodyfikowany. Jeśli wiersz został zmodyfikowany, nazywa się `UpdateCommand`odpowiednim, `InsertCommand`lub `DeleteCommand` <xref:System.Data.DataRow.RowState%2A> , w zależności od wartości właściwości dla tego wiersza. Każda aktualizacja wiersza dotyczy sieci z przejazdem do bazy danych.  
  
 Począwszy od ADO.NET 2,0, <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> uwidacznia właściwość. `UpdateBatchSize` Ustawienie dodatniej wartości całkowitej powoduje, że aktualizacje bazy danych mają być wysyłane jako partie o określonym rozmiarze. Na przykład ustawienie wartości `UpdateBatchSize` 10 spowoduje grupowanie 10 oddzielnych instrukcji i przesłanie ich jako pojedynczej partii. Ustawienie wartości `UpdateBatchSize` 0 spowoduje <xref:System.Data.Common.DataAdapter> użycie największego rozmiaru partii, który może obsłużyć serwer. Ustawienie tej opcji na 1 powoduje wyłączenie aktualizacji wsadowych, ponieważ wiersze są wysyłane pojedynczo.  
  
 Wykonanie bardzo dużej partii może obniżyć wydajność. W związku z tym należy przetestować optymalne ustawienie rozmiaru partii przed wdrożeniem aplikacji.  
  
## <a name="using-the-updatebatchsize-property"></a>Używanie właściwości UpdateBatchSize  
 Po włączeniu <xref:System.Data.IDbCommand.UpdatedRowSource%2A> aktualizacji wsadowych wartość właściwości elementu `InsertCommand` `UpdateCommand`DataAdapter, i `DeleteCommand` powinna być ustawiona na <xref:System.Data.UpdateRowSource.None> lub <xref:System.Data.UpdateRowSource.OutputParameters>. Podczas wykonywania aktualizacji wsadowej, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> <xref:System.Data.UpdateRowSource.FirstReturnedRecord> wartość właściwości polecenia lub <xref:System.Data.UpdateRowSource.Both> jest nieprawidłowa.  
  
 Poniższa procedura ilustruje użycie `UpdateBatchSize` właściwości. Procedura przyjmuje dwa argumenty <xref:System.Data.DataSet> , obiekt, który ma kolumny reprezentujące pola **ProductCategoryID** i **name** w tabeli **Production. ProductCategory** , oraz liczbę całkowitą reprezentującą rozmiar wsadu (liczbę wiersze w partii). Kod tworzy nowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt, ustawia jego <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>właściwości, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> . W kodzie założono, <xref:System.Data.DataSet> że obiekt ma zmodyfikowane wiersze. Ustawia `UpdateBatchSize` Właściwość i wykonuje aktualizację.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Obsługa zdarzeń i błędów związanych z aktualizacją partii  
 Element **DataAdapter** ma dwa zdarzenia związane z aktualizacją: **RowUpdating** i **RowUpdated**. W poprzednich wersjach programu ADO.NET, gdy przetwarzanie wsadowe jest wyłączone, każde z tych zdarzeń jest generowane jednokrotnie dla każdego przetworzonego wiersza. **RowUpdating** jest generowany przed wystąpieniem aktualizacji, a **RowUpdated** jest generowany po zakończeniu aktualizacji bazy danych.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Zmiany zachowań zdarzeń przy użyciu aktualizacji wsadowych  
 Gdy przetwarzanie wsadowe jest włączone, wiele wierszy jest aktualizowanych w ramach jednej operacji bazy danych. W związku z `RowUpdating` tym `RowUpdated` dla każdej partii występuje tylko jedno zdarzenie, podczas gdy zdarzenie występuje dla każdego przetworzonego wiersza. Gdy przetwarzanie wsadowe jest wyłączone, dwa zdarzenia są generowane `RowUpdating` z przeplotem jeden do jednego, gdzie jedno zdarzenie i jedno `RowUpdated` zdarzenie wyzwalające dla wiersza, a następnie jedno `RowUpdating` i jedno `RowUpdated` zdarzenie wyzwalające dla następnego wiersza, aż wszystkie wiersze są przetwarzane.  
  
### <a name="accessing-updated-rows"></a>Uzyskiwanie dostępu do zaktualizowanych wierszy  
 Gdy przetwarzanie wsadowe jest wyłączone, do aktualizowanego wiersza można uzyskać dostęp za <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> pomocą właściwości <xref:System.Data.Common.RowUpdatedEventArgs> klasy.  
  
 Po włączeniu przetwarzania wsadowego jest generowane pojedyncze `RowUpdated` zdarzenie dla wielu wierszy. W związku z tym wartość `Row` właściwości dla każdego wiersza jest równa null. `RowUpdating`zdarzenia są nadal generowane dla każdego wiersza. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metoda<xref:System.Data.Common.RowUpdatedEventArgs> klasy pozwala uzyskać dostęp do przetworzonych wierszy przez skopiowanie odwołań do wierszy do tablicy. Jeśli żaden wiersz nie jest przetwarzany `CopyToRows` , <xref:System.ArgumentNullException>zgłasza. Użyj właściwości <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> , aby zwrócić liczbę wierszy przetworzonych przed <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> wywołaniem metody.  
  
### <a name="handling-data-errors"></a>Obsługa błędów danych  
 Wykonanie wsadowe ma ten sam skutek co wykonanie każdej pojedynczej instrukcji. Instrukcje są wykonywane w kolejności, w jakiej instrukcje zostały dodane do partii. Błędy są obsługiwane w taki sam sposób w trybie wsadowym, jak w przypadku wyłączenia trybu wsadowego. Każdy wiersz jest przetwarzany osobno. Tylko wiersze, które zostały pomyślnie przetworzone w bazie danych, zostaną zaktualizowane w odpowiednim <xref:System.Data.DataRow> <xref:System.Data.DataTable>obszarze.  
  
 Dostawca danych i serwer baz danych zaplecza określają, które konstrukcje SQL są obsługiwane na potrzeby wykonywania wsadowego. Wyjątek może być zgłaszany, jeśli nieobsługiwana instrukcja zostanie przesłana do wykonania.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](updating-data-sources-with-dataadapters.md)
- [Obsługa zdarzeń elementu DataAdapter](handling-dataadapter-events.md)
- [Omówienie ADO.NET](ado-net-overview.md)
