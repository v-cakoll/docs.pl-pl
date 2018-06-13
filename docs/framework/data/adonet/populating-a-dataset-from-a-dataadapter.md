---
title: Wypełnianie zestawu danych z element DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ced280be0fa14077be893c59596ed65b424172c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356943"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Wypełnianie zestawu danych z element DataAdapter
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Jest rezydentny reprezentację danych, który zapewnia spójne relacyjne programowania modelu niezależnie od źródła danych. `DataSet` Reprezentuje pełny zestaw danych, który zawiera tabele, ograniczenia i relacje między tabelami. Ponieważ `DataSet` jest niezależna od źródła danych, `DataSet` mogą obejmować dane lokalne aplikacji i danych z wielu źródeł danych. Interakcja z istniejących źródeł danych są kontrolowane poprzez `DataAdapter`.  
  
 `SelectCommand` Właściwość `DataAdapter` jest `Command` obiekt, który pobiera dane ze źródła danych. `InsertCommand`, `UpdateCommand`, I `DeleteCommand` właściwości `DataAdapter` są `Command` obiektów zarządzanych aktualizacje danych w źródle danych, zgodnie ze zmian wprowadzonych w danych w `DataSet`. Te właściwości są opisane bardziej szczegółowo w [aktualizowanie źródła danych z obiektów DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Metody `DataAdapter` używany do wypełnienia `DataSet` z wynikami `SelectCommand` z `DataAdapter`. `Fill` przyjmuje jako argumenty `DataSet` wypełnianie, a `DataTable` obiektu lub nazwę `DataTable` należy podać wierszy zwróconych `SelectCommand`.  
  
> [!NOTE]
>  Przy użyciu `DataAdapter` pobranie wszystkich tabeli wymaga czasu, zwłaszcza, jeśli istnieje wiele wierszy w tabeli. Jest to spowodowane dostęp do bazy danych, lokalizuje i przetwarzania danych, a następnie przekazania danych do klienta jest czasochłonne. Ściąganie wszystkich tabeli klientowi również blokuje wszystkie wiersze na serwerze. Aby zwiększyć wydajność, można użyć `WHERE` klauzuli znacznie zmniejszyć liczbę wierszy zwracanych do klienta. Można także zmniejszyć ilość danych do klienta zwracany przez wyświetlanie tylko jawnie wymaganych kolumn w `SELECT` instrukcji. Inne obejście dobrej jest pobieranie wierszy w partii (na przykład kilka wierszy kilkuset jednocześnie) i tylko pobieranie następnej partii, gdy klient jest gotowy z użyciem bieżącej partii.  
  
 `Fill` Używa metody `DataReader` obiektu niejawnie zwraca nazwy kolumn i typy, które są używane do tworzenia tabel w `DataSet`i dane do zapełnienia wierszy w tabelach w `DataSet`. Tabele i kolumny są tworzone tylko jeśli już nie istnieją; w przeciwnym razie `Fill` wykorzystuje istniejące `DataSet` schematu. Typy kolumn są tworzone jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów zgodnie z tabelami w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Klucze podstawowe nie są tworzone, jeśli nie istnieją w źródle danych i `DataAdapter` **.**`MissingSchemaAction` ustawiono `MissingSchemaAction` **.** `AddWithKey`. Jeśli `Fill` stwierdza, że istnieje klucz podstawowy dla tabeli, spowoduje zastąpienie danych w `DataSet` z danymi ze źródła danych dla wierszy, w których wartości kolumny klucza podstawowego pasują do wiersza zwracane ze źródła danych. Jeśli zostanie znaleziony żaden klucz podstawowy, dane są dołączane do tabel w `DataSet`. `Fill` używa mapowań, które mogą wystąpić podczas wypełniania `DataSet` (zobacz [element DataAdapter DataTable i mapowania elementu DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Jeśli `SelectCommand` zwraca wyniki OUTER JOIN `DataAdapter` nie ustawia `PrimaryKey` wartość powstałe w ten sposób `DataTable`. Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są rozpoznawane poprawnie. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy przykład kodu tworzy wystąpienie <xref:System.Data.SqlClient.SqlDataAdapter> używającą <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` bazy danych i wypełnienie <xref:System.Data.DataTable> w `DataSet` z listy odbiorców. Instrukcja SQL i <xref:System.Data.SqlClient.SqlConnection> argumentów przekazanych do <xref:System.Data.SqlClient.SqlDataAdapter> konstruktora są używane do tworzenia <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> właściwość <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
## <a name="example"></a>Przykład  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =   
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  Kod w poniższym przykładzie jawnie nie powoduje otwarcia i zamknięcia `Connection`. `Fill` Metoda niejawnie otwiera `Connection` który `DataAdapter` używa jeśli stwierdzi, że połączenie nie jest już otwarty. Jeśli `Fill` otwarte połączenia, również zamyka połączenie podczas `Fill` zostało zakończone. Może to uprościć kodu podczas operacji jednej operacji takich jak `Fill` lub `Update`. Jednak jeśli przeprowadzasz wiele operacji, które wymagają otwartego połączenia można poprawić wydajność aplikacji jawnie wywołując `Open` metody `Connection`, wykonywanie operacji względem źródła danych i następnie podczas wywoływania `Close` metody `Connection`. Należy starać się zachować połączenia ze źródłem danych, Otwórz możliwie krótki aby zwolnić zasoby do użytku przez inne aplikacje klienckie.  
  
## <a name="multiple-result-sets"></a>Wiele zestawów wyników  
 Jeśli `DataAdapter` zestawy wielu wyników czynnościach, tworzy wiele tabel w `DataSet`. Tabele są podane przyrostowe domyślną nazwę tabeli*N*począwszy Table0 "tabeli". Jeśli nazwa tabeli jest przekazywany jako argument `Fill` metody, tabelach podano przyrostowe domyślną nazwę TableName*N*począwszy "Nazwa_tabeli" dla TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Wypełnianie zestawu danych z wielu obiektów DataAdapter  
 Dowolną liczbę `DataAdapter` obiekty mogą być używane z `DataSet`. Każdy `DataAdapter` może być użyta do wypełnienia co najmniej jeden `DataTable` obiektów i rozwiąż aktualizacje z powrotem do źródła danych. `DataRelation` i `Constraint` obiekty mogą być dodawane do `DataSet` lokalnie, co umożliwia powiązać dane z różnych źródeł. Na przykład `DataSet` mogą zawierać dane z bazy danych programu Microsoft SQL Server, bazy danych programu IBM DB2 za pośrednictwem OLE DB i strumieni XML źródła danych. Co najmniej jeden `DataAdapter` obiektów może obsłużyć komunikacji dla każdego źródła danych.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wypełnia listę klientów z `Northwind` bazy danych w programie Microsoft SQL Server oraz listę zleceń `Northwind` bazy danych programu Microsoft Access 2000. Wypełniony tabel powiązanych z `DataRelation`, a następnie wyświetlona lista klientów z zamówień tego klienta. Aby uzyskać więcej informacji na temat `DataRelation` obiekty, zobacz [Dodawanie DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) i [nawigowanie po DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _   
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a>Typ Decimal serwera SQL  
 Domyślnie `DataSet` przechowuje dane przy użyciu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów danych. Większość aplikacji te zapewniają wygodne reprezentację informacje o źródle danych. Taka reprezentacja może jednak spowodować problem, gdy typ danych w źródle danych jest typu dziesiętnego lub liczbowego danych programu SQL Server. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` — Typ danych pozwala maksymalnie 28 cyfr znaczących, podczas gdy program SQL Server `decimal` 38 cyfr znaczących zezwala na typ danych. Jeśli `SqlDataAdapter` określa podczas `Fill` operacji który dokładność programu SQL Server `decimal` pole jest większy niż 28 znaków, bieżący wiersz nie została dodana do `DataTable`. Zamiast tego `FillError` wystąpi zdarzenie, co pozwala określić, czy utratę dokładności będą występować i reagowania. Aby uzyskać więcej informacji na temat `FillError` zdarzeń, zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Można pobrać programu SQL Server `decimal` wartości, można również użyć <xref:System.Data.SqlClient.SqlDataReader> obiekt i wywołanie <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metody.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono rozszerzoną obsługę <xref:System.Data.SqlTypes> w `DataSet`. Aby uzyskać więcej informacji, zobacz [właściwości SqlTypes i zestawie danych](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB rozdziałach  
 Hierarchiczna zestawów wierszy lub działami (typ OLE DB `DBTYPE_HCHAPTER`, typu ADO `adChapter`) może być użyta do wypełnienia zawartość `DataSet`. Gdy <xref:System.Data.OleDb.OleDbDataAdapter> napotka podzielony na rozdziały kolumny podczas `Fill` operacji, `DataTable` jest tworzony w kolumnie podzielony na rozdziały i ta tabela jest wypełniany kolumn i wierszy od działu. Tabela utworzona dla podzielony na rozdziały kolumna nosiła nazwę, używając nazwy tabeli nadrzędnej i nazwę kolumny podzielony na rozdziały w formie "*ParentTableNameChapteredColumnName*". Jeśli tabela już istnieje w `DataSet` odpowiadającej nazwie kolumny podzielony na rozdziały, bieżącej tabeli jest wypełniony danych działu. Jeśli w istniejącej tabeli, która odpowiada kolumny znaleźć w rozdziale nie ma żadnej kolumny, jest dodawana nowa kolumna.  
  
 Przed tabele w `DataSet` są wypełnione z danymi w kolumnach podzielony na rozdziały relacji jest tworzony między nadrzędnym a podrzędnym tabel hierarchiczną zestawu wierszy, dodając kolumnę liczb całkowitych do tabeli nadrzędne i podrzędne, ustawienie kolumny nadrzędnej automatycznego przyrostu i tworzenie `DataRelation` przy użyciu dodanych kolumn z obu tabel. Dodano relacji nosi nazwę przy użyciu nazw kolumn tabeli i rozdział nadrzędnego w formie "*ParentTableNameChapterColumnName*".  
  
 Należy pamiętać, że istnieje tylko powiązane kolumny w `DataSet`. Kolejne wypełnienia ze źródła danych może spowodować nowych wierszy dodawanych do tabeli zamiast zmiany scalane w istniejących wierszy.  
  
 Należy zauważyć, że, jeśli używasz `DataAdapter.Fill` przeciążenia, które przyjmuje `DataTable`, tylko w tej tabeli zostaną wypełnione. Kolumna liczb całkowitych wartości auto nadal zostaną dodane do tabeli, ale nie tabeli podrzędnej będzie można utworzyć ani wypełnione, a zostanie utworzona relacja.  
  
 W poniższym przykładzie użyto dostawcy MSDataShape do generowania kolumną rozdziału zamówień dla każdego klienta w listę klientów. A `DataSet` jest następnie wypełnione z danymi.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 Gdy `Fill` zakończeniu operacji `DataSet` zawiera dwie tabele: `Customers` i `CustomersOrders`, gdzie `CustomersOrders` reprezentuje podzielony na rozdziały kolumny. Dodatkowa kolumna o nazwie `Orders` jest dodawany do `Customers` tabeli i dodatkową kolumnę o nazwie `CustomersOrders` jest dodawany do `CustomersOrders` tabeli. `Orders` Kolumny w `Customers` tabeli ustawiono automatycznego przyrostu. A `DataRelation`, `CustomersOrders`, jest tworzona przy użyciu kolumn, które zostały dodane do tabel z `Customers` jako tabeli nadrzędnej. W poniższej tabeli przedstawiono niektóre przykładowe wyniki.  
  
### <a name="tablename-customers"></a>TableName: klientów  
  
|CustomerID|Nazwa firmy|Zlecenia|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Helados y ana Trujillo Emparedados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [Wiele aktywnych zestawów wyników (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
