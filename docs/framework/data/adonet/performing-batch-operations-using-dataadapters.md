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
# <a name="performing-batch-operations-using-dataadapters"></a>Wykonywanie operacji wsadowych za pomocą elementów DataAdapter
Obsługa wsadowa w ADO.NET <xref:System.Data.Common.DataAdapter> umożliwia grupowanie operacji INSERT, <xref:System.Data.DataSet> UPDATE <xref:System.Data.DataTable> i DELETE z a lub do serwera, zamiast wysyłać jedną operację naraz. Zmniejszenie liczby rund na serwer zazwyczaj powoduje znaczny wzrost wydajności. Aktualizacje wsadowe są obsługiwane dla dostawców<xref:System.Data.SqlClient>danych .NET<xref:System.Data.OracleClient>dla programu SQL Server ( ) i Oracle ( ).  
  
 Podczas aktualizowania bazy danych <xref:System.Data.DataSet> ze zmianami z poprzednich `Update` wersji ADO.NET, metoda `DataAdapter` wykonywane aktualizacje bazy danych jeden wiersz na raz. Jak iterowane przez wiersze w <xref:System.Data.DataTable>określonym , <xref:System.Data.DataRow> zbadał każdy, aby sprawdzić, czy został zmodyfikowany. Jeśli wiersz został zmodyfikowany, nazwał `UpdateCommand`odpowiednie `InsertCommand`, `DeleteCommand`lub , w <xref:System.Data.DataRow.RowState%2A> zależności od wartości właściwości dla tego wiersza. Każda aktualizacja wiersza obejmowała sieć w obie strony do bazy danych.  
  
 Począwszy od ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> udostępnia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości. Ustawienie `UpdateBatchSize` dodatniej wartości całkowitej powoduje, że aktualizacje bazy danych mają być wysyłane jako partie o określonym rozmiarze. Na przykład ustawienie `UpdateBatchSize` na 10 spowoduje grupowanie 10 oddzielnych instrukcji i przesłanie ich jako pojedynczej partii. Ustawienie `UpdateBatchSize` na 0 spowoduje <xref:System.Data.Common.DataAdapter> użycie największego rozmiaru partii, który może obsłużyć serwer. Ustawienie go na 1 powoduje wyłączenie aktualizacji wsadowych, ponieważ wiersze są wysyłane po jednym naraz.  
  
 Wykonywanie bardzo dużej partii może zmniejszyć wydajność. W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed zaimplementowanie aplikacji.  
  
## <a name="using-the-updatebatchsize-property"></a>Korzystanie z UpdateBatchSize Właściwość  
 Gdy aktualizacje partii są <xref:System.Data.IDbCommand.UpdatedRowSource%2A> włączone, `UpdateCommand`wartość właściwości DataAdapter's , `InsertCommand`i <xref:System.Data.UpdateRowSource.OutputParameters> `DeleteCommand` powinny być ustawione na <xref:System.Data.UpdateRowSource.None> lub . Podczas wykonywania aktualizacji partii, wartość <xref:System.Data.IDbCommand.UpdatedRowSource%2A> właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> polecenia <xref:System.Data.UpdateRowSource.Both> lub jest nieprawidłowa.  
  
 Poniższa procedura pokazuje korzystanie `UpdateBatchSize` z właściwości. Procedura ma dwa <xref:System.Data.DataSet> argumenty, obiekt, który ma kolumny reprezentujące **ProductCategoryID** i **Nazwa** pola w **Production.ProductCategory** tabeli i liczba całkowita reprezentująca rozmiar partii (liczba wierszy w partii). Kod tworzy nowy <xref:System.Data.SqlClient.SqlDataAdapter> obiekt, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>ustawiając jego , <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości. Kod zakłada, że <xref:System.Data.DataSet> obiekt zmodyfikował wiersze. Ustawia `UpdateBatchSize` właściwość i wykonuje aktualizację.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Obsługa zdarzeń i błędów związanych z aktualizacją wsadową  
 **DataAdapter** ma dwa zdarzenia związane z aktualizacją: **RowUpdating** i **RowUpdated**. W poprzednich wersjach ADO.NET, gdy przetwarzanie wsadowe jest wyłączone, każde z tych zdarzeń jest generowane raz dla każdego przetworzonego wiersza. **RowUpdating** jest generowany przed wystąpieniem aktualizacji, a **RowUpdated** jest generowany po zakończeniu aktualizacji bazy danych.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Zmiany zachowania zdarzeń z aktualizacjami wsadowym  
 Gdy przetwarzanie wsadowe jest włączone, wiele wierszy są aktualizowane w jednej operacji bazy danych. W związku z `RowUpdated` tym tylko jedno zdarzenie `RowUpdating` występuje dla każdej partii, podczas gdy zdarzenie występuje dla każdego wiersza przetwarzane. Gdy przetwarzanie wsadowe jest wyłączone, dwa zdarzenia są uruchamiane z `RowUpdating` interleaving jeden do jednego, gdzie jedno zdarzenie i jedno `RowUpdated` zdarzenie jest uruchamiane dla wiersza, a następnie jeden `RowUpdating` i jeden `RowUpdated` pożar zdarzenia dla następnego wiersza, aż wszystkie wiersze są przetwarzane.  
  
### <a name="accessing-updated-rows"></a>Uzyskiwanie dostępu do zaktualizowanych wierszy  
 Gdy przetwarzanie wsadowe jest wyłączone, aktualizowany <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> wiersz jest <xref:System.Data.Common.RowUpdatedEventArgs> dostępny przy użyciu właściwości klasy.  
  
 Gdy przetwarzanie wsadowe jest `RowUpdated` włączone, dla wielu wierszy jest generowane pojedyncze zdarzenie. W związku z tym `Row` wartość właściwości dla każdego wiersza jest null. `RowUpdating`zdarzenia są nadal generowane dla każdego wiersza. Metoda <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> <xref:System.Data.Common.RowUpdatedEventArgs> klasy umożliwia dostęp do przetworzonych wierszy, kopiując odwołania do wierszy do tablicy. Jeśli nie są przetwarzane żadne `CopyToRows` wiersze, zgłasza plik <xref:System.ArgumentNullException>. Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości, aby zwrócić liczbę wierszy przetworzonych przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.  
  
### <a name="handling-data-errors"></a>Obsługa błędów danych  
 Wykonywanie wsadowe ma taki sam efekt jak wykonanie każdej pojedynczej instrukcji. Instrukcje są wykonywane w kolejności, w. Błędy są obsługiwane w taki sam sposób w trybie wsadowym, jak są, gdy tryb wsadowy jest wyłączony. Każdy wiersz jest przetwarzany oddzielnie. Tylko wiersze, które zostały pomyślnie przetworzone w bazie <xref:System.Data.DataRow> danych <xref:System.Data.DataTable>zostaną zaktualizowane w odpowiednich w ramach .  
  
 Dostawca danych i serwer bazy danych zaplecza określają, które konstrukcje SQL są obsługiwane do wykonywania wsadowego. Wyjątek może zostać zgłoszony, jeśli nieobjęta instrukcją jest przesyłana do wykonania.  
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](updating-data-sources-with-dataadapters.md)
- [Obsługa zdarzeń elementu DataAdapter](handling-dataadapter-events.md)
- [Omówienie ADO.NET](ado-net-overview.md)
