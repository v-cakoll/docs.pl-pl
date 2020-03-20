---
title: Pobieranie danych przy użyciu elementu DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149027"
---
# <a name="retrieve-data-using-a-datareader"></a>Pobieranie danych przy użyciu czytnika danych
Aby pobrać dane przy użyciu **programu DataReader,** należy utworzyć wystąpienie obiektu **Command,** a następnie utworzyć **program DataReader,** wywołując **program Command.ExecuteReader** w celu pobrania wierszy ze źródła danych. **DataReader** zapewnia niebuforowany strumień danych, który umożliwia logiki proceduralnej skutecznie przetwarzać wyniki ze źródła danych sekwencyjnie. **DataReader** jest dobrym wyborem podczas pobierania dużych ilości danych, ponieważ dane nie są buforowane w pamięci.

Poniższy przykład ilustruje przy użyciu **DataReader**, gdzie `reader` reprezentuje prawidłowy DataReader i `command` reprezentuje prawidłowy Obiekt Polecenia.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Użyj **DataReader.Read** metody, aby uzyskać wiersz z wyników kwerendy. Dostęp do każdej kolumny zwróconego wiersza można uzyskać, przekazując nazwę lub numer porządkowy kolumny do **programu DataReader**. Jednak dla najlepszej wydajności **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości kolumn w ich natywnych typów danych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, i tak dalej). Aby uzyskać listę metod akcesora wpisanego dla <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.SqlClient.SqlDataReader> **czytników danych**specyficznych dla dostawcy danych, zobacz i . Za pomocą metody akcesora wpisane, gdy wiesz, że typ danych bazowych zmniejsza ilość konwersji typu wymagane podczas pobierania wartości kolumny.  
  
 Poniższy przykład iteruje za pośrednictwem **obiektu DataReader** i zwraca dwie kolumny z każdego wiersza.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zamykanie czytnika danych  
 Zawsze wywołać **Close** metody po zakończeniu przy użyciu **DataReader** obiektu.  
  
 Jeśli **polecenie** zawiera parametry wyjściowe lub zwracane wartości, wartości te nie są dostępne, dopóki **datareader** nie zostanie zamknięty.  
  
 Gdy **datareader** jest otwarty, **połączenie** jest używane wyłącznie przez tego **DataReader**. Nie można wykonać żadnych poleceń dla **połączenia**, w tym tworzenia innego **DataReader**, dopóki oryginalny **DataReader** zostanie zamknięty.  
  
> [!NOTE]
> Nie należy wywoływać **Zamknij** lub **Dispose** na **połączenie**, **DataReader**lub inny obiekt zarządzany w **Finalize** metody klasy. W finalizatorze tylko zwolnić niezarządzanych zasobów, które posiada bezpośrednio klasy. Jeśli klasa nie jest właścicielem żadnych zasobów niezarządzanych, nie należy **uwzględniać Finalize** metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Pobieranie wielu zestawów wyników przy użyciu funkcji NextResult  
 Jeśli **DataReader** zwraca wiele zestawów wyników, wywołać **NextResult** metoda iteracji za pośrednictwem zestawów wyników sekwencyjnie. W poniższym <xref:System.Data.SqlClient.SqlDataReader> przykładzie przedstawiono przetwarzanie wyników <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dwóch instrukcji SELECT przy użyciu metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Uzyskiwanie informacji o schemacie z czytnika danych  
 Gdy **DataReader** jest otwarty, można pobrać informacje o schemacie o bieżącym zestawie wyników przy użyciu **GetSchemaTable** metody. **GetSchemaTable** zwraca <xref:System.Data.DataTable> obiekt wypełniony wierszami i kolumnami, które zawierają informacje o schemacie dla bieżącego zestawu wyników. **DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników. Każda kolumna tabeli schematu jest mapowana do właściwości kolumn zwracanych w wierszach zestawu wyników, gdzie **ColumnName** jest nazwą właściwości, a wartość kolumny jest wartością właściwości. W poniższym przykładzie zapisuje informacje o schemacie dla **programu DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Praca z rozdziałami OLE DB  
 Hierarchiczne zestawy wierszy lub rozdziały (typ OLE DB **DBTYPE_HCHAPTER**, ADO type **adChapter**) można pobrać za pomocą <xref:System.Data.OleDb.OleDbDataReader>pliku . Gdy kwerenda zawierająca rozdział jest zwracana jako **DataReader**, rozdział jest zwracany jako kolumna w tym **DataReader** i jest narażony jako obiekt **DataReader.**  
  
 ADO.NET **DataSet** może również służyć do reprezentowania hierarchicznych zestawów wierszy przy użyciu relacji nadrzędny-podrzędny między tabelami. Aby uzyskać więcej informacji, zobacz [Zestawy danych, Tablice informacyjne i DataViews](./dataset-datatable-dataview/index.md).  
  
 Poniższy przykład kodu używa dostawcy MSDataShape do generowania kolumny rozdział zamówień dla każdego klienta na liście odbiorców.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Zwracanie wyników dzięki oracle ref cursor  
 Dostawca danych .NET Framework dla Oracle obsługuje korzystanie z oracle ref cursors do zwracania wyników kwerendy. Kursor ref Oracle jest zwracany jako . <xref:System.Data.OracleClient.OracleDataReader>  
  
 Można pobrać obiekt, <xref:System.Data.OracleClient.OracleDataReader> który reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody. Można również <xref:System.Data.OracleClient.OracleCommand> określić, który zwraca jeden lub więcej oracle ref cursors jako **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używane do wypełnienia . <xref:System.Data.DataSet>  
  
 Aby uzyskać dostęp do ref cursor zwrócony <xref:System.Data.OracleClient.OracleCommand> ze źródła danych Oracle, należy utworzyć dla kwerendy <xref:System.Data.OracleClient.OracleCommand.Parameters> i <xref:System.Data.OracleClient.OracleCommand>dodać parametr wyjściowy, który odwołuje się do REF CURSOR do kolekcji . . Nazwa parametru musi być zgodna z nazwą parametru REF CURSOR w kwerendzie. Ustaw typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>na . Metoda <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> zwraca <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> dla REF CURSOR.  
  
 Jeśli <xref:System.Data.OracleClient.OracleCommand> zwraca wiele kursorów REF, dodaj wiele parametrów wyjściowych. Można uzyskać dostęp do różnych ref cursors wywołując <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metodę. Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwraca <xref:System.Data.OracleClient.OracleDataReader> odwołanie się do pierwszego KURSORA REF. Następnie można wywołać metodę, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> aby uzyskać dostęp do kolejnych ref cursorów. Mimo że parametry <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> w kolekcji odpowiadają parametrom wyjściowym <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR według nazwy, uzyskuje <xref:System.Data.OracleClient.OracleCommand.Parameters> do nich dostęp w kolejności, w jakiej zostały dodane do kolekcji.  
  
 Rozważmy na przykład następujący pakiet Oracle i treść pakietu.  
  
```sql
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
  
 Poniższy kod <xref:System.Data.OracleClient.OracleCommand> tworzy, który zwraca ref cursors z poprzedniego pakietu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> Oracle <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> przez dodanie dwóch parametrów typu do kolekcji.  
  
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
  
 Poniższy kod zwraca wyniki poprzedniego polecenia <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> przy użyciu <xref:System.Data.OracleClient.OracleDataReader>i metod . Parametry RE CURSOR są zwracane w kolejności.  
  
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
  
 W poniższym przykładzie użyto poprzedniego <xref:System.Data.DataSet> polecenia do wypełniania a z wynikami pakietu Oracle.  
  
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
> Aby uniknąć **nadmiernego przepełnienia,** zaleca się również obsługę dowolnej konwersji z typu Oracle NUMBER do prawidłowego typu .NET Framework przed zapisaniem wartości w pliku <xref:System.Data.DataRow>. Można użyć <xref:System.Data.Common.DataAdapter.FillError> zdarzenia, aby ustalić, czy wystąpił **przepełnieniePrzezstaw.** Aby uzyskać więcej <xref:System.Data.Common.DataAdapter.FillError> informacji na temat zdarzenia, zobacz [Obsługa zdarzeń dataadapter](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [Omówienie ADO.NET](ado-net-overview.md)
