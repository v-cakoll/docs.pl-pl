---
title: Pobieranie danych przy użyciu elementu DataReader
ms.date: 10/259/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: d3c59b667c05be083e44de8cc3e7e44d50fefc71
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43516794"
---
# <a name="retrieve-data-using-a-datareader"></a>Pobierają dane przy użyciu elementu DataReader
Do pobierania danych przy użyciu **DataReader**, Utwórz wystąpienie obiektu **polecenia** obiektu, a następnie utwórz **DataReader** przez wywołanie metody **Command.ExecuteReader**  pobieranie wierszy ze źródła danych. **DataReader** zapewnia Niebuforowane strumienia danych, które umożliwia procedurach logikę w celu wydajnego przetwarzania wyników ze źródła danych, po kolei. **DataReader** to dobry wybór w przypadku, gdy w przypadku pobierania dużych ilości danych, ponieważ dane nie są buforowane w pamięci.

Poniższy przykład ilustruje użycie **DataReader**, gdzie `reader` reprezentuje prawidłowy element DataReader i `command` reprezentuje prawidłowy obiekt polecenia.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Użyj **DataReader.Read** metodę, aby uzyskać wiersz z wyników zapytania. Dostęp do poszczególnych kolumn zwracany wiersz, przekazując nazwę lub liczbę porządkową kolumny do **DataReader**. Jednak w celu uzyskania najlepszej wydajności **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości w kolumnie w ich typach danych natywnych (**GetDateTime**, **GetDouble**, **Getguid —**, **GetInt32**i tak dalej). Lista metod typizowane metody dostępu do danych specyficznych dla dostawcy **DataReaders**, zobacz <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader>. Za pomocą metody dostępu wpisane, gdy wiesz, podstawowych danych typu zmniejsza konwersji typu wymagane podczas pobierania wartości kolumny.  
  
 Poniższy przykład wykonuje iterację przez **DataReader** obiektu i zwraca dwie kolumny z każdego wiersza.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zamykanie elementu DataReader  
 Zawsze wywołuj **Zamknij** metody po zakończeniu korzystania z **DataReader** obiektu.  
  
 Jeśli Twoje **polecenia** dane wyjściowe zawierają parametrów lub zwracanych wartości tych wartości nie są dostępne do momentu **DataReader** jest zamknięty.  
  
 Gdy **DataReader** jest otwarty, **połączenia** jest używana wyłącznie przez to **DataReader**. Nie można wykonać żadnych poleceń **połączenia**, takich jak tworzenie drugiego **DataReader**, aż do oryginalnego **DataReader** jest zamknięty.  
  
> [!NOTE]
>  Nie wywołuj **Zamknij** lub **Dispose** na **połączenia**, **DataReader**, lub inne obiekt zarządzany w **Finalize**  metody klasy. W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj **Finalize** metody w swojej definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Trwa pobieranie wielu wyników ustawia przy użyciu NextResult  
 Jeśli **DataReader** zwraca wiele zestawów wyników, wywołanie **NextResult** metodę, aby wykonać iterację wynik ustawia sekwencyjnie. W poniższym przykładzie przedstawiono <xref:System.Data.SqlClient.SqlDataReader> przetwarzania wyników dwóch instrukcji "SELECT" przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Pobieranie informacji o schemacie z elementu DataReader  
 Gdy **DataReader** jest otwarty, możesz pobrać informacji o schemacie o wyniku bieżącego zestawu przy użyciu **GetSchemaTable** metody. **GetSchemaTable** zwraca <xref:System.Data.DataTable> obiektu wypełnione z wierszami i kolumnami, które zawierają informacje o schemacie dla bieżącego zestawu wyników. **DataTable** zawiera ona jeden wiersz dla każdej kolumny zestawu wyników. Każda kolumna tabeli schematów mapuje właściwość kolumny zwracane w wiersze wynik ustawione, gdzie **ColumnName** jest nazwę właściwości, a wartość kolumny jest wartość właściwości. Poniższy przykład zapisuje się informacji o schemacie dla **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Praca z działami OLE DB  
 Hierarchiczna zestawów wierszy lub rozdziałów (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**), można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader>. Gdy zapytanie, które zawiera rozdział jest zwracana jako **DataReader**, rozdziału jest zwracana jako kolumny w tym **DataReader** i jest udostępniany jako **DataReader** obiektu.  
  
 ADO.NET **DataSet** może również służyć do reprezentowania hierarchiczne zestawy wierszy przy użyciu relacji nadrzędny podrzędny między tabelami. Aby uzyskać więcej informacji, zobacz [DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Poniższy przykład kodu używa dostawcy MSDataShape do generowania kolumny rozdziałów zamówień dla każdego klienta na liście klientów.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Zwracanie wyników z Oracle REF CURSOR  
 .NET Framework Data Provider for Oracle obsługuje Oracle REF CURSOR do zwrócenia wyniku zapytania. Oracle REF CURSOR jest zwracana jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Możesz pobrać <xref:System.Data.OracleClient.OracleDataReader> obiekt, który reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody. Można również określić <xref:System.Data.OracleClient.OracleCommand> zwracającego co najmniej jeden Oracle REF CURSOR jako **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używany do wypełniania <xref:System.Data.DataSet>.  
  
 Dostępu REF CURSOR zwrócone ze źródła danych Oracle, należy utworzyć <xref:System.Data.OracleClient.OracleCommand> dla zapytania i Dodaj parametr wyjściowy, odwołujący się do kursora REF <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcję usługi <xref:System.Data.OracleClient.OracleCommand>. Nazwa parametru musi odpowiadać Nazwa parametru REF CURSOR w zapytaniu. Ustaw typ parametru, aby <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Metody usługi <xref:System.Data.OracleClient.OracleCommand> zwraca <xref:System.Data.OracleClient.OracleDataReader> kursora REF.  
  
 Jeśli Twoje <xref:System.Data.OracleClient.OracleCommand> zwraca wielu kursorów REF CURSOR, dodać wiele parametrów wyjściowych. Dostęp do różnych kursora REF CURSOR, wywołując <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody. Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwraca <xref:System.Data.OracleClient.OracleDataReader> odwołuje się do pierwszego REF CURSOR. Następnie możesz wywołać <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodę, aby dostęp do kolejnych kursora REF CURSOR. Mimo że parametrów w swojej <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> dopasowanie kolekcji REF CURSOR output parametrów przy użyciu nazwy, <xref:System.Data.OracleClient.OracleDataReader> uzyskuje do nich dostęp w kolejności, w jakiej zostały dodane do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji.  
  
 Na przykład rozważmy następujący pakiet oprogramowania Oracle i treść pakietu.  
  
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
  
 Poniższy kod tworzy <xref:System.Data.OracleClient.OracleCommand> zwracającego z poprzedniego pakietu programu Oracle REF CURSOR, dodając dwa parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji.  
  
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
  
 Poniższy kod zwraca wyniki do poprzedniego polecenia przy użyciu <xref:System.Data.OracleClient.OracleDataReader.Read> i <xref:System.Data.OracleClient.OracleDataReader.NextResult> metody <xref:System.Data.OracleClient.OracleDataReader>. Parametry kursora REF są zwracane w porządku.  
  
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
  
 W poniższym przykładzie użyto poprzednie polecenie, aby wypełnić <xref:System.Data.DataSet> z wynikami pakietu programu Oracle.  
  
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

> [!NOTE]
>  Aby uniknąć **overflowexception —**, firma Microsoft zaleca również obsługiwać każda konwersja z typu Liczba Oracle na prawidłowy typ .NET Framework przed zapisaniem wartości w <xref:System.Data.DataRow>. Możesz użyć <xref:System.Data.Common.DataAdapter.FillError> zdarzenia w celu określenia, czy **overflowexception —** wystąpił. Aby uzyskać więcej informacji na temat <xref:System.Data.Common.DataAdapter.FillError> zdarzeń, zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z DataReaders](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
