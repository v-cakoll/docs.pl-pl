---
title: "Za pomocą obiektów DataAdapter operacji wsadowych."
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
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e5c584bcd825e390b24da6c95ecb159a8280c639
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="performing-batch-operations-using-dataadapters"></a>Za pomocą obiektów DataAdapter operacji wsadowych.
Umożliwia obsługę partii w ADO.NET <xref:System.Data.Common.DataAdapter> do grupowania operacji INSERT, UPDATE i DELETE <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> na serwerze, zamiast wysyłać jedną operację naraz. Zmniejszenie liczby rund do serwera zwykle powoduje znaczący wzrost wydajności. Aktualizacje wsadowe są obsługiwane dla dostawcy danych .NET dla programu SQL Server (<xref:System.Data.SqlClient>) i Oracle (<xref:System.Data.OracleClient>).  
  
 Aktualizowanie bazy danych o zmiany z <xref:System.Data.DataSet> w poprzednich wersjach programu ADO.NET, `Update` metody `DataAdapter` wykonywana aktualizacji do bazy danych o jeden wiersz. Zgodnie z jego iterowane za pośrednictwem wierszy w określonym <xref:System.Data.DataTable>, jego zbadaniu <xref:System.Data.DataRow> do sprawdzania, czy ma zostać zmodyfikowany. Jeśli wiersz gdyby został zmodyfikowany, nazywany odpowiednie `UpdateCommand`, `InsertCommand`, lub `DeleteCommand`w zależności od wartości <xref:System.Data.DataRow.RowState%2A> właściwości dla tego wiersza. Każda aktualizacja wiersza zaangażowane sieci przesłania danych do bazy danych.  
  
 Począwszy od ADO.NET 2.0 <xref:System.Data.Common.DbDataAdapter> przedstawia <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> właściwości. Ustawienie `UpdateBatchSize` jako dodatnią liczbę całkowitą wartość powoduje, że aktualizacje bazy danych do wysłania jako partii o określonym rozmiarze. Na przykład ustawienie `UpdateBatchSize` 10 będzie grupy 10 osobnych instrukcji i przesłać je jako pojedyncza partia. Ustawienie `UpdateBatchSize` na 0 spowoduje, że <xref:System.Data.Common.DataAdapter> do użycia największy rozmiar partii, serwer może obsłużyć. Opcja 1 wyłącza aktualizacje wsadowe, jako wiersze są wysyłane pojedynczo.  
  
 Wykonywanie wsadowe bardzo dużą może obniżyć wydajność. W związku z tym należy przetestować ustawienie rozmiaru partii optymalne przed wdrożeniem aplikacji.  
  
## <a name="using-the-updatebatchsize-property"></a>Za pomocą właściwości UpdateBatchSize  
 Gdy są włączone aktualizacje wsadowe, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości element DataAdapter `UpdateCommand`, `InsertCommand`, i `DeleteCommand` powinien być ustawiony na <xref:System.Data.UpdateRowSource.None> lub <xref:System.Data.UpdateRowSource.OutputParameters>. Podczas wykonywania partii zaktualizować, polecenia <xref:System.Data.IDbCommand.UpdatedRowSource%2A> wartość właściwości <xref:System.Data.UpdateRowSource.FirstReturnedRecord> lub <xref:System.Data.UpdateRowSource.Both> jest nieprawidłowy.  
  
 W poniższej procedurze przedstawiono użycie `UpdateBatchSize` właściwości. Procedury przyjmuje dwa argumenty <xref:System.Data.DataSet> obiektu, który ma kolumn reprezentujących **ProductCategoryID** i **nazwa** pól w **Production.ProductCategory**tabeli i liczbę całkowitą reprezentującą rozmiar partii (liczba wierszy w partii). Kod tworzy nową <xref:System.Data.SqlClient.SqlDataAdapter> obiektu ustawienie jej <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, i <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> właściwości. Kod, przy założeniu, że <xref:System.Data.DataSet> obiekt zmodyfikowany wierszy. Ustawia `UpdateBatchSize` właściwości i wykonuje aktualizację.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Obsługa zdarzeń związanych z aktualizacji partii i błędów  
 **Element DataAdapter** ma dwa zdarzenia związane z aktualizacji: **RowUpdating** i **RowUpdated**. W poprzednich wersjach programu ADO.NET wyłączenia przetwarzania wsadowego każde z tych wydarzeń generowany jest jeden raz dla każdego wiersza przetworzone. **RowUpdating** jest generowany, zanim nastąpi aktualizacja, i **RowUpdated** jest generowany po ukończeniu aktualizacji bazy danych.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Zdarzenie zmiany sposobu działania z aktualizacje wsadowe  
 Po włączeniu przetwarzania wsadowego wiele wierszy są aktualizowane w ramach operacji pojedynczej bazy danych. W związku z tym tylko jeden `RowUpdated` zdarzenie dla każdej z partii, podczas gdy `RowUpdating` zdarzenie dla każdego wiersza przetworzone. Podczas przetwarzania wsadowego jest wyłączona, gdy jedna dwa zdarzenia są uruchamiane z jeden do jednego z przeplotem `RowUpdating` zdarzeń i jeden `RowUpdated` fire zdarzenia dla wiersza, a następnie wykonaj `RowUpdating` i jeden `RowUpdated` fire zdarzenia dla następnego wiersza, aż wszystkie wiersze są przetwarzane.  
  
### <a name="accessing-updated-rows"></a>Dostęp do zaktualizowanych wierszy  
 Podczas przetwarzania wsadowego jest wyłączona, można uzyskać dostępu do aktualizacji wiersza przy użyciu <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> właściwość <xref:System.Data.Common.RowUpdatedEventArgs> klasy.  
  
 Po włączeniu przetwarzania wsadowego, pojedynczy `RowUpdated` zdarzenie jest generowane dla wielu wierszy. W związku z tym wartość `Row` właściwości dla każdego wiersza ma wartość null. `RowUpdating`zdarzenia są nadal generowane dla każdego wiersza. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metody <xref:System.Data.Common.RowUpdatedEventArgs> klasa pozwala na dostęp przez kopiowanie odwołania do wierszy w tablicy przetworzonych wierszy. Jeśli żadne wiersze są przetwarzane, `CopyToRows` zgłasza <xref:System.ArgumentNullException>. Użyj <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> właściwości Zwróć liczbę wierszy przetworzone przed wywołaniem <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.  
  
### <a name="handling-data-errors"></a>Obsługa błędów danych  
 Wsadowe ma ten sam efekt co wykonanie każdej poszczególnych instrukcji. Instrukcje są wykonywane w kolejności, że instrukcje zostały dodane do wykonywania zadania wsadowego. Błędy są obsługiwane w trybie wsadowym tak samo, jak po wyłączeniu trybu partii. Każdy wiersz jest przetwarzany osobno. Tylko wiersze, które zostały pomyślnie przetworzone w bazie danych zostanie zaktualizowany w odpowiedniej <xref:System.Data.DataRow> w <xref:System.Data.DataTable>.  
  
 Dostawca danych i serwera wewnętrznej bazy danych należy określić konstrukcji SQL, które są obsługiwane w przypadku wykonywania wsadowego usługi. Może zostać zgłoszony wyjątek, jeśli instrukcji z systemem innym niż obsługiwany jest przesyłany do wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
