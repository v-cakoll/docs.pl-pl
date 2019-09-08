---
title: Sekwencje Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 772aeda94215ccc8e1eff0e1145ed0399791197d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794588"
---
# <a name="oracle-sequences"></a>Sekwencje Oracle
.NET Framework Dostawca danych dla programu Oracle zapewnia obsługę pobierania wartości sekwencji programu Oracle klucza generowanych przez serwer po wykonaniu operacji Inserts <xref:System.Data.OracleClient.OracleDataAdapter>przy użyciu.  
  
 SQL Server i Oracle obsługują tworzenie automatycznie zwiększających się kolumn, które można wyznaczyć jako klucze podstawowe. Te wartości są generowane przez serwer, ponieważ wiersze są dodawane do tabeli. W SQL Server ustaw właściwość Identity kolumny. w programie Oracle utworzysz sekwencję. Różnica między kolumnami AutoIncrement w SQL Server i sekwencjami w programie Oracle to:  
  
- W SQL Server oznaczasz kolumnę jako kolumnę automatycznego przyrostu i SQL Server automatycznie generuje nowe wartości dla kolumny podczas wstawiania nowego wiersza.  
  
- W programie Oracle utworzysz sekwencję, aby wygenerować nowe wartości dla kolumny w tabeli, ale nie ma bezpośredniego powiązania między sekwencją a tabelą lub kolumną. Sekwencja Oracle to obiekt, taki jak tabela lub procedura składowana.  
  
 Podczas tworzenia sekwencji w bazie danych Oracle można zdefiniować jej początkową wartość i przyrost między jej wartościami. Możesz również zbadać sekwencję nowych wartości przed przesłaniem nowych wierszy. Oznacza to, że kod może rozpoznać wartości klucza dla nowych wierszy przed wstawieniem ich do bazy danych.  
  
 Aby uzyskać więcej informacji na temat tworzenia autoprzyrostowych kolumn przy użyciu SQL Server i ADO.NET, zobacz [pobieranie tożsamości lub wartości AutoNumber](retrieving-identity-or-autonumber-values.md) i [Tworzenie kolumn typu AutoIncrement](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Przykład  
 W poniższym C# przykładzie pokazano, jak można pobrać nowe wartości sekwencji z bazy danych Oracle Database. Przykład odwołuje się do sekwencji w kwerendzie INSERT INTO użytej do przesłania nowych wierszy, a następnie zwraca wartość sekwencji wygenerowaną przy użyciu klauzuli Return wprowadzonej w Oracle10g. Przykład dodaje serię oczekujących nowych wierszy w a <xref:System.Data.DataTable> za pomocą ADO. Funkcja autoprzyrostu netto w celu wygenerowania wartości klucza podstawowego "PlaceHolder". Zwróć uwagę, że wartość przyrostu ADO.NET wygenerowana dla nowego wiersza to "symbol zastępczy". Oznacza to, że baza danych może generować różne wartości z tych ADO.NET.  
  
 Przed przesłaniem oczekujących operacji wstawiania do bazy danych, w przykładzie zostanie wyświetlona zawartość wierszy. Następnie kod tworzy nowy <xref:System.Data.OracleClient.OracleDataAdapter> obiekt i ustawia jego <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> właściwości i. W przykładzie pokazano również, że logika zwraca wartości generowane przez serwer przy użyciu parametrów wyjściowych. Następnie przykład wykonuje aktualizację w celu przesłania oczekujących wierszy i wyświetla zawartość <xref:System.Data.DataTable>.  
  
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

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
