---
title: Wypełnianie zestawu danych z elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ecfd2c3a31b42b380c593aef0bbc23775874cc7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076825"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Wypełnianie zestawu danych z elementu DataAdapter
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Jest rezydentnego reprezentację danych, który zapewnia spójne relacyjnych programowania modelu niezależnie od źródła danych. `DataSet` Przedstawia kompletny zestaw danych, który zawiera tabele, ograniczenia i relacje między tabelami. Ponieważ `DataSet` jest niezależna od źródła danych `DataSet` mogą obejmować dane lokalne do aplikacji i danych z wielu źródeł danych. Interakcja z istniejących źródeł danych jest kontrolowany za pośrednictwem `DataAdapter`.  
  
 `SelectCommand` Właściwość `DataAdapter` jest `Command` obiekt, który pobiera dane ze źródła danych. `InsertCommand`, `UpdateCommand`, I `DeleteCommand` właściwości `DataAdapter` są `Command` obiektów zarządzanych aktualizacji względem danych w źródle danych, zgodnie z modyfikacje wprowadzone do danych w `DataSet`. Te właściwości są omówione bardziej szczegółowo w [aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Metody `DataAdapter` używany do wypełnienia `DataSet` z wynikami `SelectCommand` z `DataAdapter`. `Fill` przyjmuje jako argumenty `DataSet` wypełniona, a `DataTable` obiektu lub nazwę `DataTable` trzeba napełniać wierszy zwróconych `SelectCommand`.  
  
> [!NOTE]
>  Za pomocą `DataAdapter` do pobrania wszystkich tabeli wymaga czasu, szczególnie w przypadku wielu wierszy w tabeli. Jest to spowodowane dostęp do bazy danych, lokalizuje i przetwarzania danych, a następnie przesyłania danych do klienta jest czasochłonne. Pobieranie wszystkich tabeli do klienta również blokuje wszystkie wiersze na serwerze. Aby poprawić wydajność, można użyć `WHERE` klauzulę, aby znacznie zmniejszyć liczbę wierszy jest zwracana do klienta. Można także zmniejszyć ilość danych zwracanych do klienta, wyświetlając tylko jawnie wymaganych kolumn w `SELECT` instrukcji. Innym dobrym rozwiązaniem problemu jest pobieranie wierszy w partii (na przykład kilka wierszy kilkaset w danym momencie) i tylko pobieranie następnej partii, gdy klient jest gotowy, z użyciem bieżącej partii.  
  
 `Fill` Metoda używa `DataReader` obiektu niejawnie, aby zwrócić nazwy kolumn i typy, które są używane do tworzenia tabel w `DataSet`i danych do wypełnienia wierszy w tabelach w `DataSet`. Tabele i kolumny są tworzone tylko jeśli ich jeszcze nie istnieje; w przeciwnym razie `Fill` wykorzystuje istniejące `DataSet` schematu. Typy kolumn są tworzone jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów zgodnie z tabelami w [mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Klucze podstawowe nie są tworzone, chyba że istnieją one w źródle danych i `DataAdapter` **.**`MissingSchemaAction` ustawiono `MissingSchemaAction` **.** `AddWithKey`. Jeśli `Fill` stwierdza, że istnieje klucz podstawowy w tabeli, spowoduje zastąpienie danych w `DataSet` z danymi ze źródła danych dla wierszy, w których wartości kolumny klucza podstawowego pasują do właściwości wiersza zwrócone ze źródła danych. Jeśli zostanie znaleziony żaden klucz podstawowy, dane są dołączane do tabel w `DataSet`. `Fill` korzysta z żadnych mapowań, które mogą występować podczas wypełniania `DataSet` (zobacz [DataAdapter DataTable i mapowania elementu DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Jeśli `SelectCommand` zwraca wyniki OUTER JOIN `DataAdapter` nie ustawia `PrimaryKey` wartości wynikowe `DataTable`. Należy zdefiniować `PrimaryKey` sobie, aby upewnić się, że poprawnie rozpoznać zduplikowane wiersze. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy przykład kodu tworzy wystąpienie <xref:System.Data.SqlClient.SqlDataAdapter> , który używa <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` bazy danych i wypełnienie <xref:System.Data.DataTable> w `DataSet` listę klientów. Instrukcja SQL i <xref:System.Data.SqlClient.SqlConnection> argumenty przekazywane do <xref:System.Data.SqlClient.SqlDataAdapter> Konstruktor są używane do tworzenia <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> właściwość <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
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
>  Kod przedstawiony w tym przykładzie nie jawnie można otworzyć i zamknąć `Connection`. `Fill` Metodę niejawnie otwiera `Connection` , `DataAdapter` używa, jeśli wykryje, że połączenie nie jest już otwarty. Jeśli `Fill` otwarte połączenia, również zamyka połączenie podczas `Fill` zostało zakończone. Może to uprościć kod, podczas operacji jednej operacji takich jak `Fill` lub `Update`. Jednak jeśli wykonują wiele operacji, które wymagają otwarcia połączenia, możesz zwiększyć wydajność aplikacji przez jawne wywołanie `Open` metody `Connection`, wykonywanie operacji względem źródła danych i następnie wywoływania `Close` metody `Connection`. Należy starać się zachować połączeń ze źródłem danych Otwórz możliwie krótki aby zwolnić zasoby do użytku przez inne aplikacje klienckie.  
  
## <a name="multiple-result-sets"></a>Wiele zestawów wyników  
 Jeśli `DataAdapter` zestawy wielu wyników napotka, powoduje to utworzenie wielu tabel w `DataSet`. Tabele są podane przyrostowe domyślną nazwę tabeli*N*, począwszy od Table0 "tabeli". Jeśli nazwa tabeli jest przekazywany jako argument do `Fill` metody tabele są podane przyrostowe domyślną nazwę TableName*N*, począwszy od "TableName", aby uzyskać TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Wypełnianie zestawu danych z wielu elementów DataAdapters  
 Dowolną liczbę `DataAdapter` obiekty mogą być używane z `DataSet`. Każdy `DataAdapter` może służyć do wypełnienia co najmniej jeden `DataTable` obiektów i rozwiąż aktualizacje z powrotem do źródła danych. `DataRelation` i `Constraint` obiekty mogą być dodawane do `DataSet` lokalnie, co umożliwia powiązać dane z różnych źródeł. Na przykład `DataSet` może zawierać dane z bazy danych programu Microsoft SQL Server, bazy danych programu IBM DB2 udostępniane za pośrednictwem OLE DB i źródła danych, które strumieni XML. Co najmniej jeden `DataAdapter` obiektów może obsługiwać komunikację z każdego źródła danych.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wypełnia listę klientów z `Northwind` bazy danych, program Microsoft SQL Server i listę zamówień z `Northwind` bazy danych programu Microsoft Access 2000. Wypełniony tabele są powiązane z `DataRelation`, a następnie zostanie wyświetlona lista klientów przy użyciu zamówień tego klienta. Aby uzyskać więcej informacji na temat `DataRelation` obiekty, zobacz [Dodawanie elementów DataRelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) i [przejść elementów DataRelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>Typu dziesiętnego programu SQL Server  
 Domyślnie `DataSet` przechowuje dane przy użyciu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów danych. W przypadku większości aplikacji te zapewniają wygodny reprezentacja informacje o źródle danych. Jednak taka reprezentacja może powodować problem, jeśli typ danych w źródle danych jest typu dziesiętnego lub liczbowego danych programu SQL Server. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` — Typ danych pozwala maksymalnie 28 cyfr znaczących, podczas gdy program SQL Server `decimal` typ danych umożliwia 38 cyfr znaczących. Jeśli `SqlDataAdapter` określa podczas `Fill` operacji, dokładność programu SQL Server `decimal` pola jest większy niż 28 znaków, bieżący wiersz nie jest dodawany do `DataTable`. Zamiast tego `FillError` wystąpi zdarzenie, co pozwala określić, czy utratę dokładności będą występować reagować odpowiednio. Aby uzyskać więcej informacji na temat `FillError` zdarzeń, zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Można pobrać serwera SQL `decimal` wartości, można również użyć <xref:System.Data.SqlClient.SqlDataReader> obiektu, a następnie wywołać <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metody.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono rozszerzoną obsługę <xref:System.Data.SqlTypes> w `DataSet`. Aby uzyskać więcej informacji, zobacz [SqlTypes i zestaw danych](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB rozdziałów  
 Hierarchiczna zestawów wierszy i rozdziałami (typ OLE DB `DBTYPE_HCHAPTER`, typ ADO `adChapter`) może służyć do wypełnienia zawartość `DataSet`. Podczas <xref:System.Data.OleDb.OleDbDataAdapter> napotka podzielony na rozdziały kolumny podczas `Fill` operacji `DataTable` jest tworzony w kolumnie podzielony na rozdziały i tej tabeli jest wypełniany kolumn i wierszy od działu. Tabela utworzona dla podzielony na rozdziały kolumna nosiła nazwę za pomocą nazwy tabeli nadrzędnej i nazwę kolumny podzielony na rozdziały w formie "*ParentTableNameChapteredColumnName*". Jeśli tabela już istnieje w `DataSet` który pasuje do nazwy kolumny podzielony na rozdziały, bieżącej tabeli jest wypełniony przy użyciu danych działu. Jeśli nie ma żadnej kolumny w istniejącej tabeli, która jest zgodna z kolumną znaleźć w rozdziale, nowa kolumna zostanie dodana.  
  
 Przed tabel w `DataSet` są wypełniane przy użyciu danych w kolumnach podzielony na rozdziały relacji jest tworzony między nadrzędnym a podrzędnym tabel hierarchiczne zestawu wierszy, dodając kolumna liczb całkowitych do tabeli nadrzędne i podrzędne, ustawienie kolumny nadrzędnej automatycznego przyrostu i tworzenie `DataRelation` przy użyciu dodanych kolumn z obu tabel. Dodano relacji nosi nazwę przy użyciu nazw kolumn tabeli i rozdział nadrzędnego w formie "*ParentTableNameChapterColumnName*".  
  
 Należy zauważyć, że istnieje tylko powiązane kolumny w `DataSet`. Kolejne wypełnienia ze źródła danych może spowodować nowe wiersze, które mają zostać dodane do tabel, zamiast zmiany są scalane w istniejących wierszy.  
  
 Należy zauważyć, że, jeśli używasz `DataAdapter.Fill` przeciążenia przyjmującego `DataTable`, tylko w tej tabeli zostaną wypełnione. Kolumna liczb całkowitych o wartości auto nadal będzie dodawany do tabeli, ale nie tabeli podrzędnej będzie można utworzyć ani wypełnione, a zostanie utworzona żadna relacja.  
  
 W poniższym przykładzie użyto dostawcy MSDataShape do generowania kolumny rozdziałów zamówień dla każdego klienta na liście klientów. Element `DataSet` jest następnie wypełniana przy użyciu danych.  
  
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
  
 Gdy `Fill` operacja została zakończona, `DataSet` zawiera dwie tabele: `Customers` i `CustomersOrders`, gdzie `CustomersOrders` reprezentuje podzielony na rozdziały kolumnę. Dodatkową kolumnę o nazwie `Orders` jest dodawany do `Customers` tabeli i dodatkową kolumnę o nazwie `CustomersOrders` jest dodawany do `CustomersOrders` tabeli. `Orders` Kolumny w `Customers` tabeli jest ustawiony do automatycznego przyrostu. A `DataRelation`, `CustomersOrders`, jest tworzona przy użyciu kolumn, które zostały dodane do tabel `Customers` jako tabelę nadrzędną. W poniższej tabeli przedstawiono niektóre przykładowe wyniki.  
  
### <a name="tablename-customers"></a>Właściwość TableName: Klienci  
  
|CustomerID|CompanyName|Zamówienia|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Helados y ana Trujillo Emparedados|1|  
  
### <a name="tablename-customersorders"></a>Właściwość TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [Wiele aktywnych zestawów wyników (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
