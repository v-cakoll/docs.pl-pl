---
title: "Podczas pobierania danych przy użyciu elementu DataReader"
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
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b36f76516d4ddf94e177a5ecbb705e1d729318b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-data-using-a-datareader"></a>Podczas pobierania danych przy użyciu elementu DataReader
Podczas pobierania danych przy użyciu **DataReader** obejmuje utworzenie wystąpienia **polecenia** obiektu, a następnie utworzenie **DataReader** przez wywołanie metody  **Command.ExecuteReader** pobieranie wierszy ze źródła danych. Poniższy przykład przedstawia przy użyciu **DataReader** gdzie `reader` reprezentuje prawidłową DataReader i `command` reprezentuje prawidłowy obiekt polecenia.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Możesz użyć **odczytu** metody **DataReader** obiektu można uzyskać wiersza z wyników zapytania. Dostęp do każdej kolumny wiersza zwrócone przez przekazanie nazwa lub numer porządkowy odwołania do kolumny, która ma **DataReader**. Jednak w celu uzyskania najlepszej wydajności **DataReader** udostępnia szereg metod, które umożliwiają dostęp do wartości w kolumnie w ich typach danych natywnych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**i tak dalej). Aby uzyskać listę metod dostępu typu danych specyficznych dla dostawcy **DataReaders**, zobacz <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader>. Przy użyciu metody typu dostępu, przy założeniu podstawowy typ danych jest znany, zmniejsza ilość konwersji typu wymagane podczas pobierania wartości kolumny.  
  
> [!NOTE]
>  Wersja systemu Windows Server 2003 programu .NET Framework zawiera dodatkowe właściwości dla **DataReader**, **HasRows**, co pozwala określić, czy **DataReader**zwróciło żadnych wyników przed dokonaniem odczytu z niego.  
  
 Poniższy przykład kodu iteruje **DataReader** obiektu i zwraca dwie kolumny z każdego wiersza.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** zapewnia Niebuforowane strumień danych, które umożliwia procedurach logiki wydajnie sekwencyjnie przetworzyć wyniki ze źródła danych. **DataReader** jest dobrym rozwiązaniem, gdy trwa pobieranie dużych ilości danych, ponieważ dane nie są buforowane w pamięci.  
  
## <a name="closing-the-datareader"></a>Zamykanie elementu DataReader  
 Zawsze należy wywołać **Zamknij** metody po zakończeniu przy użyciu **DataReader** obiektu.  
  
 Jeśli Twoje **polecenia** dane wyjściowe zawierają parametrów lub zwracanych wartości nie będą one dostępne do **DataReader** jest zamknięty.  
  
 Należy pamiętać, że podczas **DataReader** jest otwarty, **połączenia** jest używany wyłącznie przez to **DataReader**. Nie można wykonać żadnych poleceń **połączenia**, łącznie z utworzyć inny **DataReader**, aż do oryginalnej **DataReader** jest zamknięty.  
  
> [!NOTE]
>  Nie wywołuj **Zamknij** lub **Dispose** na **połączenia**, **DataReader**, lub innego obiektu zarządzanego w **Finalize**  metody klasy. W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj **Finalize** metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Pobieranie wielu zestawów wyników przy użyciu NextResult  
 Jeśli wiele zestawów wyników są zwracane, **DataReader** zapewnia **NextResult** Ustawia metodę do iteracji wynik w kolejności. W poniższym przykładzie przedstawiono <xref:System.Data.SqlClient.SqlDataReader> przetwarzania wyników dwóch instrukcji "SELECT" przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Uzyskiwanie informacji schematu z elementu DataReader  
 Gdy **DataReader** jest otwarty, możesz pobierać schematu informacje o bieżącym wyniku ustawić za pomocą **GetSchemaTable** metody. **GetSchemaTable** zwraca <xref:System.Data.DataTable> obiektu wypełnione wiersze i kolumny, które zawierają informacje o schemacie dla bieżącego zestawu wyników. **DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników. Każda kolumna wiersza tabeli schematu mapowany na właściwość kolumny zwracane w zestaw wyników, których **ColumnName** jest nazwą właściwości i wartość w kolumnie jest wartością właściwości. Poniższy przykład kodu zapisuje informacji schematu dla **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Praca z OLE DB rozdziałach  
 Hierarchiczna zestawów wierszy lub działami (typ OLE DB **DBTYPE_HCHAPTER**, typu ADO **adChapter**) można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader>. Gdy kwerendę, która obejmuje rozdział są zwracane jako **DataReader**, rozdziału jest zwracana jako kolumny w tym **DataReader** i jest udostępniany jako **DataReader** obiektu.  
  
 ADO.NET **DataSet** mogą służyć do reprezentowania hierarchiczne zestawy wierszy przy użyciu relacji nadrzędny podrzędny między tabelami. Aby uzyskać więcej informacji, zobacz [zestawów danych, DataTables i DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Poniższy przykład kodu wykorzystuje dostawcy MSDataShape do generowania kolumną rozdziału zamówień dla każdego klienta w listę klientów.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Zwracania wyników z kursorami REF Oracle  
 .NET Framework Data Provider for Oracle obsługuje Oracle REF kursory zwracanie wyniku zapytania. Oracle REF CURSOR jest zwracana jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Możesz pobrać **OracleDataReader** obiektu, które reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody, a także określić <xref:System.Data.OracleClient.OracleCommand> zwracającą co najmniej jeden kursory REF Oracle jako  **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używaną do wypełniania <xref:System.Data.DataSet>.  
  
 Aby uzyskać dostęp do REF CURSOR zwracane ze źródła danych Oracle, należy utworzyć **OracleCommand** zapytania i Dodaj parametr wyjściowy, który odwołuje się do REF CURSOR do **parametry** kolekcji Twojego **OracleCommand**. Nazwa parametru musi odpowiadać nazwie parametru REF CURSOR w zapytaniu. Ustaw typ parametru **OracleType.Cursor**. **ExecuteReader** metody z **OracleCommand** zwróci **OracleDataReader** dla REF CURSOR.  
  
 Jeśli Twoje **OracleCommand** zwraca wiele KURSORY REF, Dodaj wiele parametrów wyjściowych. Dostęp do różnych kursorów REF wywołując **OracleCommand.ExecuteReader** metody. Wywołanie **ExecuteReader** zwraca **OracleDataReader** odwołuje się do pierwszej REF CURSOR. Następnie można wywołać **OracleDataReader.NextResult** metodę dostępu kolejnych kursory REF. Mimo że parametrów w Twojej **OracleCommand.Parameters** dopasowania kolekcji REF CURSOR output parametry nazwę **OracleDataReader** uzyskuje dostęp do nich w kolejności, że zostały one dodane do  **Parametry** kolekcji.  
  
 Rozważmy na przykład następujący pakiet Oracle i treść pakietu.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 Poniższy kod tworzy **OracleCommand** zwracającą kursory REF z poprzednim pakiecie Oracle, dodając dwa parametry typu **OracleType.Cursor** do **parametry** kolekcji.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 Poniższy kod zwraca wyniki poprzedniego przy użyciu polecenia **odczytu** i **NextResult** metody **OracleDataReader**. Parametry REF CURSOR są zwracane w kolejności.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 W poniższym przykładzie użyto poprzednie polecenie, aby wypełnić **DataSet** z wynikami pakietu programu Oracle.  
  
> [!NOTE]
>  Aby uniknąć **overflowexception —**, zalecamy również obsługiwać żadnych konwersja z typu numer Oracle do prawidłowego typu .NET Framework przed zapisaniem wartości w **DataRow**. Można użyć **FillError** zdarzeń, aby ustalić, czy **overflowexception —** wystąpił. Aby uzyskać więcej informacji na temat **FillError** zdarzeń, zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
