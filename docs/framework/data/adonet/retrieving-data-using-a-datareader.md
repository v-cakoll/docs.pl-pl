---
title: Pobieranie danych przy użyciu elementu DataReader
description: Dowiedz się, jak pobierać dane przy użyciu elementu DataReader w ADO.NET przy użyciu tego przykładowego kodu. Element DataReader udostępnia niebuforowany strumień danych.
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286601"
---
# <a name="retrieve-data-using-a-datareader"></a>Pobieranie danych przy użyciu elementu DataReader
Aby pobrać dane przy użyciu elementu **DataReader**, Utwórz wystąpienie obiektu **Command** , a następnie Utwórz element **DataReader** , wywołując **polecenie Command. ExecuteReader** , aby pobrać wiersze ze źródła danych. Element **DataReader** zawiera niebuforowany strumień danych, który umożliwia logiki proceduralnej efektywnie przetwarzać wyniki ze źródła danych sekwencyjnie. Element **DataReader** jest dobrym rozwiązaniem w przypadku pobierania dużej ilości danych, ponieważ dane nie są buforowane w pamięci.

Poniższy przykład ilustruje użycie elementu **DataReader**, gdzie `reader` reprezentuje prawidłowy element DataReader i `command` reprezentuje prawidłowy obiekt polecenia.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Użyj metody **DataReader. Read** , aby uzyskać wiersz z wyników zapytania. Możesz uzyskać dostęp do każdej kolumny zwracanego wiersza, przekazując nazwę lub numer porządkowy kolumny do elementu **DataReader**. Jednak w celu uzyskania najlepszej wydajności element **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości kolumn w ich natywnych typach danych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**itd.). Aby zapoznać się z listą metod akcesora typu dla specyficznych dla dostawcy **danych, zobacz** <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader> . Przy użyciu metod metody dostępu typu, Jeśli wiesz, że typ danych jest mniejszy niż wymagana podczas pobierania wartości kolumny.  
  
 Poniższy przykład wykonuje iterację przez obiekt **DataReader** i zwraca dwie kolumny z każdego wiersza.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zamykanie elementu DataReader  
 Zawsze wywołuj metodę **Close** po zakończeniu korzystania z obiektu **DataReader** .  
  
 Jeśli **polecenie** zawiera parametry wyjściowe lub wartości zwracane, te wartości są niedostępne, dopóki element **DataReader** nie zostanie zamknięty.  
  
 Gdy element **DataReader** jest otwarty, **połączenie** jest używane wyłącznie przez ten element **DataReader**. Nie można wykonać żadnych poleceń dla **połączenia**, w tym tworzenia innego elementu **DataReader**do momentu zamknięcia oryginalnego elementu **DataReader** .  
  
> [!NOTE]
> Nie wywołuj metody **Close** ani **Dispose** dla **połączenia**, elementu **DataReader**lub innego obiektu zarządzanego w metodzie **Finalize** klasy. W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio. Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie dołączaj metody **Finalize** w definicji klasy. Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Pobieranie wielu zestawów wyników przy użyciu NextResult  
 Jeśli element **DataReader** zwraca wiele zestawów wyników, wywołaj metodę **NextResult** , aby wykonać iterację w zestawach wyników sekwencyjnie. Poniższy przykład pokazuje <xref:System.Data.SqlClient.SqlDataReader> Przetwarzanie wyników dwóch instrukcji SELECT przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Pobieranie informacji o schemacie z elementu DataReader  
 Gdy element **DataReader** jest otwarty, można pobrać informacje o schemacie bieżącego zestawu wyników przy użyciu metody **GetSchema** . **Getschemaing** zwraca <xref:System.Data.DataTable> obiekt wypełniony wierszami i kolumnami zawierającymi informacje o schemacie dla bieżącego zestawu wyników. Element **DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników. Każda kolumna tabeli schematu jest mapowana na właściwość kolumn zwracanych w wierszach zestawu wyników, gdzie **ColumnName** jest nazwą właściwości, a wartością kolumny jest wartość właściwości. Poniższy przykład zapisuje informacje o schemacie dla elementu **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Praca z rozdziałami OLE DB  
 Hierarchiczne zestawy wierszy lub rozdziały (OLE DB typu **DBTYPE_HCHAPTER**, ADO Type **adChapter**) można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader> . Gdy zapytanie zawierające rozdział jest zwracane jako element **DataReader**, rozdział jest zwracany jako kolumna w tym elemencie **DataReader** i jest udostępniany jako obiekt **DataReader** .  
  
 **Zestaw danych** ADO.NET może być również używany do reprezentowania hierarchicznych zestawów wierszy przy użyciu relacji nadrzędny-podrzędny między tabelami. Aby uzyskać więcej informacji, zobacz [zestawy danych, DataTables i DataViews](./dataset-datatable-dataview/index.md).  
  
 Poniższy przykład kodu używa dostawcy MSDataShape w celu wygenerowania kolumny rozdział zamówień dla każdego klienta na liście klientów.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Zwracanie wyników przy użyciu kursorów REF Oracle  
 .NET Framework Dostawca danych dla programu Oracle obsługuje używanie kursorów REF Oracle do zwracania wyniku zapytania. WSKAŹNIK REF Oracle jest zwracany jako <xref:System.Data.OracleClient.OracleDataReader> .  
  
 Można pobrać <xref:System.Data.OracleClient.OracleDataReader> obiekt, który reprezentuje kursor ref Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody. Można również określić <xref:System.Data.OracleClient.OracleCommand> , że zwraca co najmniej jeden wskaźnik ref Oracle jako **Właściwość SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> użyta do wypełnienia <xref:System.Data.DataSet> .  
  
 Aby uzyskać dostęp do kursora REF zwróconego ze źródła danych Oracle, Utwórz <xref:System.Data.OracleClient.OracleCommand> dla zapytania i Dodaj parametr wyjściowy, który odwołuje się do kursora ref do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji <xref:System.Data.OracleClient.OracleCommand> . Nazwa parametru musi być zgodna z nazwą parametru REF CURSOR w zapytaniu. Ustaw typ parametru na <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> . <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>Metoda <xref:System.Data.OracleClient.OracleCommand> zwraca <xref:System.Data.OracleClient.OracleDataReader> dla kursora ref.  
  
 Jeśli <xref:System.Data.OracleClient.OracleCommand> zwracasz wiele kursorów ref, Dodaj wiele parametrów wyjściowych. Możesz uzyskać dostęp do różnych kursorów REF przez wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody. Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwracające odwołanie do <xref:System.Data.OracleClient.OracleDataReader> pierwszego kursora ref. Następnie można wywołać metodę, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> Aby uzyskać dostęp do kolejnych kursorów ref. Chociaż parametry w <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji są zgodne z parametrami wyjściowymi kursora ref według nazwy, <xref:System.Data.OracleClient.OracleDataReader> uzyskują dostęp do nich w kolejności, w której zostały dodane do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji.  
  
 Rozważmy na przykład poniższy pakiet Oracle i treść pakietu.  
  
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
  
 Poniższy kod tworzy <xref:System.Data.OracleClient.OracleCommand> , który zwraca kursory ref z poprzedniego pakietu Oracle, dodając dwa parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji.  
  
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
  
 Poniższy kod zwraca wyniki poprzedniego polecenia przy użyciu <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> metod i <xref:System.Data.OracleClient.OracleDataReader> . Parametry kursora REF są zwracane w kolejności.  
  
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
  
 W poniższym przykładzie użyte zostało poprzednie polecenie do wypełnienia <xref:System.Data.DataSet> wynikami pakietu Oracle.  
  
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
> Aby uniknąć **przepełnienia**, zalecamy również obsługę konwersji z typu numeru Oracle na prawidłowy typ .NET Framework przed zapisaniem wartości w <xref:System.Data.DataRow> . Możesz użyć zdarzenia, <xref:System.Data.Common.DataAdapter.FillError> Aby określić, czy wystąpił wyjątek **przepełnienia** . Aby uzyskać więcej informacji o <xref:System.Data.Common.DataAdapter.FillError> zdarzeniu, zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [Omówienie ADO.NET](ado-net-overview.md)
