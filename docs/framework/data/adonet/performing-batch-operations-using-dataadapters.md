---
title: Wykonywanie operacji wsadowych za pomocą elementów DataAdapters
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780001"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Wykonywanie operacji wsadowych za pomocą elementów DataAdapters
Umożliwia obsługę usługi Batch w ADO.NET <xref:System.Data.Common.DataAdapter> do grupy operacji INSERT, UPDATE i DELETE z <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> do serwera, zamiast wysyłać jedną operację naraz. Zmniejszenie liczby rund do serwera zwykle powoduje znaczący wzrost wydajności. Aktualizacje usługi Batch są obsługiwane dla dostawcy danych .NET dla programu SQL Server (<xref:System.Data.SqlClient>) i Oracle (<xref:System.Data.OracleClient>).  
  
 Aktualizacja bazy danych za pomocą zmiany z <xref:System.Data.DataSet> w poprzednich wersjach programu ADO.NET, `Update` metody `DataAdapter` wykonywane aktualizacji do bazy danych o jeden wiersz w danym momencie. Jak powtórzyć go za pośrednictwem wierszy w określonym <xref:System.Data.DataTable>, zbadaniu, każdego <xref:System.Data.DataRow> do sprawdzania, czy ma zostać zmodyfikowany. Jeśli wiersz ma zmodyfikowany, wywołuje odpowiednią `UpdateCommand`, `InsertCommand`, lub `DeleteCommand`, w zależności od wartości <xref:System.Data.DataRow.RowState%2A> właściwości dla tego wiersza. Każda aktualizacja wiersza zaangażowane sieci przesłania danych do bazy danych.  
  
 Począwszy od wersji 2.0 programu ADO.NET, <xref:System.Data.Common.DbDataAdapter> udostępnia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości. Ustawienie `UpdateBatchSize` na dodatnią liczbą całkowitą wartość powoduje, że aktualizacje bazy danych do wysłania jako partie o określonym rozmiarze. Na przykład ustawienie `UpdateBatchSize` 10 zostanie grupy 10 osobnych instrukcji i przesłać je jako jedna partia. Ustawienie `UpdateBatchSize` na 0 spowoduje, że <xref:System.Data.Common.DataAdapter> używać największy rozmiar partii, która może obsłużyć serwer. Ustawienie 1 wyłącza aktualizacji wsadowych, jak wiersze są wysyłane pojedynczo.  
  
 Wykonując bardzo dużych partii może obniżyć wydajność. W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed wdrożeniem aplikacji.  
  
## <a name="using-the-updatebatchsize-property"></a>Przy użyciu właściwości UpdateBatchSize  
 Po włączeniu aktualizacji wsadowych <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartości właściwości elementu DataAdapter `UpdateCommand`, `InsertCommand`, i `DeleteCommand` powinna być równa <xref:System.Data.UpdateRowSource.None> lub <xref:System.Data.UpdateRowSource.OutputParameters>. Podczas wykonywania partii aktualizacji, polecenia <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> lub <xref:System.Data.UpdateRowSource.Both> jest nieprawidłowy.  
  
 Poniższa procedura demonstruje użycie `UpdateBatchSize` właściwości. Procedury przyjmuje dwa argumenty <xref:System.Data.DataSet> obiekt, który ma kolumn reprezentujących **ProductCategoryID** i **nazwa** pola w **Production.ProductCategory**tabeli i liczba całkowita reprezentująca rozmiar partii (liczba wierszy w zadaniu wsadowym). Ten kod tworzy nową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu, ustawiając jego <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości. Kod zakłada, że <xref:System.Data.DataSet> obiekt zmodyfikowany wierszy. Ustawia `UpdateBatchSize` właściwości i wykonuje aktualizację.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Obsługa zdarzeń związanych z aktualizacji usługi Batch i błędów  
 **DataAdapter** ma dwa zdarzenia związane z aktualizacji: **— RowUpdating** i **RowUpdated**. W poprzednich wersjach programu ADO.NET podczas przetwarzania wsadowego jest wyłączona, każde z tych wydarzeń jest generowany raz dla każdego wiersza przetworzone. **— RowUpdating** jest generowany, zanim nastąpi aktualizacja, i **RowUpdated** jest generowany po zakończeniu aktualizacji bazy danych.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Zdarzenie zmiany zachowania za pomocą aktualizacji usługi Batch  
 Po włączeniu przetwarzanie wsadowe wiele wierszy są aktualizowane w ramach operacji pojedynczej bazy danych. W związku z tym tylko jeden `RowUpdated` wystąpi zdarzenie dla każdej partii, natomiast `RowUpdating` wystąpi zdarzenie dla każdego wiersza przetworzone. Po wyłączeniu przetwarzania wsadowego dwa zdarzenia są uruchamiane przy użyciu jednego z przeplotem, gdy jedna `RowUpdating` zdarzeń i jeden `RowUpdated` pożaru zdarzeń do wiersza, a następnie jeden `RowUpdating` i jeden `RowUpdated` pożaru zdarzeń do następnego wiersza, aż wszystkie wiersze są przetwarzane.  
  
### <a name="accessing-updated-rows"></a>Uzyskiwanie dostępu do zaktualizowanych wierszy  
 Podczas przetwarzania wsadowego jest wyłączona, można uzyskać dostępu do aktualizacji wiersza przy użyciu <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> właściwość <xref:System.Data.Common.RowUpdatedEventArgs> klasy.  
  
 Po włączeniu przetwarzania wsadowego, pojedynczy `RowUpdated` zdarzenie jest generowane dla wielu wierszy. W związku z tym, wartość `Row` właściwości dla każdego wiersza ma wartość null. `RowUpdating` zdarzenia są nadal generowane dla każdego wiersza. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metody <xref:System.Data.Common.RowUpdatedEventArgs> klasy umożliwia dostęp do wierszy przetworzonych przez kopiowanie odwołania do wierszy do tablicy. Jeśli żadne wiersze nie są przetwarzane, `CopyToRows` zgłasza <xref:System.ArgumentNullException>. Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości, aby zwrócić liczbę wierszy przetworzone przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.  
  
### <a name="handling-data-errors"></a>Obsługa błędów danych  
 Wykonywanie wsadowe ma taki sam skutek jak wykonanie każdej pojedynczych instrukcji. Instrukcje są wykonywane w kolejności, że instrukcje zostały dodane do usługi batch. Błędy są obsługiwane taki sam sposób, w trybie wsadowym, ponieważ są one po wyłączeniu trybu wsadowego. Każdy wiersz jest przetwarzany osobno. Tylko wiersze, które zostały pomyślnie przetworzone w bazie danych zostanie zaktualizowany w odpowiednich <xref:System.Data.DataRow> w ramach <xref:System.Data.DataTable>.  
  
 Dostawca danych i serwera wewnętrznej bazy danych należy określić struktur SQL, które są obsługiwane w przypadku wykonywania wsadowego. Nieobsługiwane instrukcji jest przesyłany w celu wykonania może zgłoszony wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
