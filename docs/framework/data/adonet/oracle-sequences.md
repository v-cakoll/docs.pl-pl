---
title: Sekwencje Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 4ba7b750d48613b80eca0ef3c7c2da127977498d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632342"
---
# <a name="oracle-sequences"></a>Sekwencje Oracle
.NET Framework Data Provider for Oracle zapewnia obsługę pobierania wartości generowanych przez serwer Oracle sekwencja klucza po wykonaniu operacji wstawienia przy użyciu <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server i Oracle obsługuje tworzenie automatycznego przyrostu o wartości kolumn, które mogą być oznaczone jako klucze podstawowe. Te wartości są generowane przez serwer w miarę dodawania wierszy do tabeli. W programie SQL Server Ustaw właściwości tożsamości kolumny; Oracle, należy utworzyć sekwencję. Różnica między kolumn automatycznego przyrostu w programie SQL Server i sekwencje Oracle jest to, że:  
  
- W programie SQL Server Oznacz kolumnę jako kolumny automatycznego przyrostu i programu SQL Server automatycznie generuje nowe wartości dla kolumny, gdy wstawić nowy wiersz.  
  
- Oracle utworzeniem sekwencji można wygenerować nowe wartości dla kolumny w tabeli, ale nie ma żadnego bezpośredniego połączenia między sekwencji i tabeli lub kolumny. Sekwencja Oracle jest obiektem, takich jak tabeli lub procedury składowanej.  
  
 Po utworzeniu sekwencji w bazie danych Oracle, można zdefiniować jej wartość początkową i przyrost między jego wartości. Możesz także zbadać sekwencję dla nowych wartości przed przesłaniem nowych wierszy. Oznacza to, że Twój kod może rozpoznać wartości klucza dla nowych wierszy, przed wstawiania do bazy danych.  
  
 Aby uzyskać więcej informacji na temat tworzenia kolumn automatycznego przyrostu za pomocą programu SQL Server i ADO.NET, zobacz [pobieranie tożsamości lub wartości automatycznych numerów](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) i [Tworzenie kolumn typu AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# pokazano, jak można pobrać nowe wartości sekwencji z bazy danych Oracle. Przykład odwołuje się do sekwencji w zapytaniu INSERT INTO użytego do przesłania nowe wiersze, a następnie zwraca wartość sekwencji wygenerowane przy użyciu klauzuli ZWRÓCENIE wprowadzona w Oracle10g. W przykładzie dodano szereg oczekujące nowych wierszy w arkuszu <xref:System.Data.DataTable> przy użyciu obiektów ADO. Funkcja automatycznego przyrostu przez sieć do generowania wartości klucza podstawowego "— symbol zastępczy". Należy pamiętać, że wartość przyrostu ADO.NET wygenerowany nowy wiersz po prostu "symbol zastępczy". Oznacza to, że baza danych może wygenerować różne wartości z tymi, które generuje ADO.NET.  
  
 Przed przesłaniem oczekujące operacje wstawiania do bazy danych, w przykładzie pokazano zawartość wierszy. Następnie kod tworzy nową <xref:System.Data.OracleClient.OracleDataAdapter> i ustawia jego <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> i <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> właściwości. Przykład dostarcza również logikę do zwrócenia wartości generowanych przez serwer przy użyciu parametrów wyjściowych. Następnie w przykładzie wykonuje aktualizacji można przesłać oczekujące wierszy i wyświetla zawartość <xref:System.Data.DataTable>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
