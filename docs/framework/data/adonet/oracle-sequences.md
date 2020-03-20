---
title: Sekwencje Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: d6e6bb51b8bd317c7161500b89993be689659fad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149417"
---
# <a name="oracle-sequences"></a>Sekwencje Oracle
Dostawca danych .NET Framework dla oracle zapewnia obsługę pobierania wartości klucza Oracle Sequence <xref:System.Data.OracleClient.OracleDataAdapter>generowanego przez serwer po wykonaniu wstawiania przy użyciu pliku .  
  
 SQL Server i Oracle obsługują tworzenie automatycznie zwiększających się kolumn, które można wyznaczyć jako klucze podstawowe. Wartości te są generowane przez serwer, gdy wiersze są dodawane do tabeli. W programie SQL Server można ustawić właściwość tożsamości kolumny; w Oracle tworzysz sekwencję. Różnica między kolumnami automatycznego przyrostu w programie SQL Server i sekwencjami w oracle polega na tym, że:  
  
- W programie SQL Server oznaczasz kolumnę jako kolumnę automatycznego przyrostu, a program SQL Server automatycznie generuje nowe wartości dla kolumny po wstawieniu nowego wiersza.  
  
- W Oracle tworzysz sekwencję do generowania nowych wartości dla kolumny w tabeli, ale nie ma bezpośredniego związku między sekwencją a tabelą lub kolumną. Sekwencja Oracle jest obiektem, takim jak tabela lub procedura składowana.  
  
 Podczas tworzenia sekwencji w bazie danych Oracle, można zdefiniować jego wartość początkową i przyrost między jego wartości. Można również zbadać sekwencji dla nowych wartości przed przesłaniem nowych wierszy. Oznacza to, że kod może rozpoznać wartości klucza dla nowych wierszy przed wstawieniem ich do bazy danych.  
  
 Aby uzyskać więcej informacji na temat tworzenia kolumn automatycznego zwiększania za pomocą programu SQL Server i ADO.NET, zobacz [Pobieranie wartości tożsamości lub autonumerowania](retrieving-identity-or-autonumber-values.md) i tworzenie kolumn [autoinkreacji](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład języka C# pokazuje, jak można pobrać nowe wartości sekwencji z bazy danych Oracle. Przykład odwołuje się do sekwencji w wstaw do kwerendy używanej do przesyłania nowych wierszy, a następnie zwraca wartość sekwencji wygenerowaną przy użyciu klauzuli RETURNING wprowadzonej w Oracle10g. W przykładzie dodaje serię oczekujących <xref:System.Data.DataTable> nowych wierszy w a przy użyciu ADO. Funkcja automatycznego zwiększania przyrostu net do generowania "zastępczych" wartości klucza podstawowego. Należy zauważyć, że wartość przyrostu ADO.NET wygenerowana dla nowego wiersza jest tylko "symbolem zastępczym". Oznacza to, że baza danych może generować różne wartości niż te, które generuje ADO.NET.  
  
 Przed przesłaniem oczekujących wstawia do bazy danych, w przykładzie wyświetla zawartość wierszy. Następnie kod tworzy nowy <xref:System.Data.OracleClient.OracleDataAdapter> obiekt i <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> ustawia <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> jego i właściwości. W przykładzie dostarcza również logiki do zwracania wartości generowanych przez serwer przy użyciu parametrów wyjściowych. Następnie w przykładzie wykonuje aktualizację, aby przesłać oczekujące <xref:System.Data.DataTable>wiersze i wyświetla zawartość pliku .  
  
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

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
