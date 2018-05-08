---
title: Sekwencje Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 9f89234168351191c63d81fd4f3b68b01bfac2da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="oracle-sequences"></a>Sekwencje Oracle
.NET Framework Data Provider for Oracle umożliwia pobieranie wartości generowanych przez serwer kluczy sekwencji Oracle po wykonaniu operacji wstawiania przy użyciu <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server i Oracle obsługuje tworzenie automatycznie zwiększany kolumn, które mogą być oznaczone jako klucze podstawowe. Wartości te są generowane przez serwer jako wiersze są dodawane do tabeli. W programie SQL Server należy ustawić właściwość Identity kolumny; Oracle służy do tworzenia sekwencji. Różnica między kolumny automatycznego przyrostu w programie SQL Server i sekwencje w oprogramowaniu Oracle jest to, że:  
  
-   W programie SQL Server oznaczenie kolumny jako kolumny automatycznego przyrostu i programu SQL Server automatycznie generuje nowe wartości dla kolumny, gdy wstawić nowy wiersz.  
  
-   W oprogramowaniu Oracle należy utworzyć sekwencję, aby wygenerować nowe wartości dla kolumny w tabeli, ale nie ma bezpośredniego połączenia między sekwencji i tabeli lub kolumny. Sekwencja Oracle jest obiekt, takich jak tabelę lub procedury składowanej.  
  
 Po utworzeniu sekwencji w bazie danych programu Oracle można zdefiniować swojej wartości początkowej i przyrost między jego wartości. Możesz także zbadać sekwencji dla nowej wartości przed przesłaniem nowych wierszy. Oznacza to, że kod może rozpoznać wartości klucza dla nowych wierszy przed wstawieniem ich do bazy danych.  
  
 Aby uzyskać więcej informacji na temat tworzenia kolumn automatycznego przyrostu za pomocą programu SQL Server i ADO.NET, zobacz [pobierania tożsamości lub wartości automatycznie numerowane](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) i [Tworzenie kolumny typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# pokazano, jak można pobrać nowe wartości sekwencji z bazą danych Oracle. Przykład odwołuje się sekwencja w zapytaniu INSERT INTO używany do przesyłania nowych wierszy, a następnie zwraca wartość sekwencji wygenerowanych przy użyciu klauzuli ZWRÓCENIE wprowadzone w Oracle10g. W przykładzie dodano szereg oczekujących nowych wierszy w <xref:System.Data.DataTable> przy użyciu ADO. Funkcja automatycznego przyrostu przez sieć do generowania wartości klucza podstawowego "— symbol zastępczy". Należy pamiętać, że wartość przyrostu ADO.NET wygenerowany dla nowego wiersza po prostu "symbol zastępczy". Oznacza to, że bazy danych może generować różne wartości z tymi, które generuje ADO.NET.  
  
 Przed przesłaniem oczekujących operacji wstawienia do bazy danych, w przykładzie przedstawiono zawartość wiersze. Następnie kod tworzy nową <xref:System.Data.OracleClient.OracleDataAdapter> obiekt i ustawia jej <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> i <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> właściwości. Przykład udostępnia również logikę do zwrócenia wartości generowanych przez serwer przy użyciu parametrów wyjściowych. Następnie, w przykładzie wykonuje tę aktualizację, aby przesłać wierszy oczekujących i wyświetla zawartość <xref:System.Data.DataTable>.  
  
```csharp  
public void OracleSequence(String connectionString)  
{  
   String insertString =   
      "INSERT INTO SequenceTest_Table (ID, OtherColumn)" +  
      "VALUES (SequenceTest_Sequence.NEXTVAL, :OtherColumn)" +  
      "RETURNING ID INTO :ID";  
  
   using (OracleConnection conn = new OracleConnection(connectionString))  
   {  
      //Open a connection.  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
  
      // Prepare the database.  
      cmd.CommandText = "DROP SEQUENCE SequenceTest_Sequence";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "DROP TABLE SequenceTest_Table";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "CREATE TABLE SequenceTest_Table " +  
                     "(ID int PRIMARY KEY, OtherColumn varchar(255))";  
      cmd.ExecuteNonQuery();  
  
      cmd.CommandText = "CREATE SEQUENCE SequenceTest_Sequence " +  
                        "START WITH 100 INCREMENT BY 5";  
      cmd.ExecuteNonQuery();  
  
      DataTable testTable = new DataTable();  
      DataColumn column = testTable.Columns.Add("ID", typeof(int));  
      column.AutoIncrement = true;  
      column.AutoIncrementSeed = -1;  
      column.AutoIncrementStep = -1;  
      testTable.PrimaryKey = new DataColumn[] { column };  
      testTable.Columns.Add("OtherColumn", typeof(string));  
      for (int rowCounter = 1; rowCounter <= 15; rowCounter++)  
      {  
         testTable.Rows.Add(null, "Row #" + rowCounter.ToString());  
      }  
  
      Console.WriteLine("Before Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      Console.WriteLine();  
  
      cmd.CommandText =   
        "SELECT ID, OtherColumn FROM SequenceTest_Table";  
      OracleDataAdapter da = new OracleDataAdapter(cmd);  
      da.InsertCommand = new OracleCommand(insertString, conn);  
      da.InsertCommand.Parameters.Add(":ID", OracleType.Int32, 0, "ID");  
      da.InsertCommand.Parameters[0].Direction = ParameterDirection.Output;  
      da.InsertCommand.Parameters.Add(":OtherColumn", OracleType.VarChar, 255, "OtherColumn");  
      da.InsertCommand.UpdatedRowSource = UpdateRowSource.OutputParameters;  
      da.UpdateBatchSize = 10;  
  
      da.Update(testTable);  
  
      Console.WriteLine("After Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      // Close the connection.  
      conn.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
