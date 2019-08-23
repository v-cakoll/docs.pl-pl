---
title: Wypełnianie zestawu danych z elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 5e86eb4c37d20be53d271aba9f4913f2eeccd923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928345"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Wypełnianie zestawu danych z elementu DataAdapter
ADO.NET <xref:System.Data.DataSet> to reprezentacja danych znajdujących się w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych. `DataSet` Reprezentuje kompletny zestaw danych, który zawiera tabele, ograniczenia i relacje między tabelami. Ponieważ program jest niezależny od źródła danych, możeobejmowaćdanelokalnedoaplikacjiorazdanezwieluźródełdanych.`DataSet` `DataSet` Interakcje z istniejącymi źródłami danych są `DataAdapter`kontrolowane przez program.  
  
 `SelectCommand` Właściwość `DataAdapter` jest obiektem`Command` , który pobiera dane ze źródła danych. `InsertCommand`Właściwości ,`UpdateCommand`i `DeleteCommand` `DataSet`są obiektami`Command` , które zarządzają aktualizacjami danych w źródle danych, w zależności od zmian wprowadzonych w danych w. `DataAdapter` Te właściwości są szczegółowo omówione w temacie [Aktualizowanie źródeł danych za pomocą adapterów](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `SelectCommand` `DataAdapter`Metoda `Fill` `DataAdapter` jest`DataSet` używana do wypełniania wynikami. `Fill`przyjmuje jako argumenty `DataSet` , które mają być wypełnione, `DataTable` a obiekt `DataTable` lub nazwę do wypełnienia wierszami zwracanymi z `SelectCommand`.  
  
> [!NOTE]
> `DataAdapter` Pobieranie całej tabeli trwa przy użyciu programu, zwłaszcza jeśli w tabeli znajduje się wiele wierszy. Dzieje się tak dlatego, że dostęp do bazy danych, lokalizowanie i przetwarzanie danych, a następnie Transferowanie danych do klienta odbywa się czasochłonnie. Przeciągnięcie całej tabeli do klienta spowoduje również zablokowanie wszystkich wierszy na serwerze. Aby zwiększyć wydajność, można użyć `WHERE` klauzuli, aby znacznie zmniejszyć liczbę wierszy zwracanych do klienta. Możesz również zmniejszyć ilość danych zwracanych do klienta, tylko jawnie wymieniając wymagane kolumny w `SELECT` instrukcji. Innym dobrym rozwiązaniem jest pobranie wierszy w partiach (takich jak kilka setek wierszy w danym momencie) i pobranie kolejnej partii, gdy klient zostanie zakończony przy użyciu bieżącej partii.  
  
 Metoda używa obiektu niejawnie do zwracania nazw kolumn i typów, które są używane do `DataSet`tworzenia tabel w, i danych do `DataSet`wypełniania wierszy tabel w. `DataReader` `Fill` Tabele i kolumny są tworzone tylko wtedy, gdy jeszcze nie istnieją; w `Fill` przeciwnym razie stosuje `DataSet` istniejący schemat. Typy kolumn są tworzone jako typy .NET Framework zgodnie z tabelami w [mapowaniu typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Klucze podstawowe nie są tworzone, chyba że istnieją w źródle danych i `DataAdapter` **.** `MissingSchemaAction` jest ustawiony na `MissingSchemaAction` **.** `AddWithKey`. Jeśli `Fill` okaże się, że klucz podstawowy istnieje dla tabeli, spowoduje to zastąpienie danych `DataSet` w danych z danymi ze źródła danych dla wierszy, w których wartości kolumny klucza podstawowego są zgodne z wierszami zwróconymi ze źródła danych. Jeśli klucz podstawowy nie zostanie znaleziony, dane są dołączane do tabel w `DataSet`. `Fill`używa wszelkich mapowań, które mogą istnieć podczas wypełniania `DataSet` (zobacz [mapowania DataAdapter DataTable i DataColumn](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Jeśli zwraca wyniki sprzężenia zewnętrznego `DataAdapter` , obiekt `PrimaryKey` nie ustawia wartości wynikowej `DataTable`. `SelectCommand` Należy zdefiniować siebie, `PrimaryKey` aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy <xref:System.Data.SqlClient.SqlDataAdapter> przykład kodu tworzy wystąpienie, które <xref:System.Data.SqlClient.SqlConnection> używa do bazy danych Microsoft SQL Server `Northwind` i wypełnia <xref:System.Data.DataTable> listę klientów w a `DataSet` . Instrukcja SQL i <xref:System.Data.SqlClient.SqlConnection> argumenty przekazane <xref:System.Data.SqlClient.SqlDataAdapter> do konstruktora <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> są używane do <xref:System.Data.SqlClient.SqlDataAdapter>tworzenia właściwości.  
  
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
> Kod przedstawiony w tym przykładzie nie jest jawnie otwarty i zamknięty `Connection`. Metoda niejawnie `Connection` otwiera, czy `DataAdapter` jest używana, jeśli stwierdzi, że połączenie nie jest jeszcze otwarte. `Fill` Jeśli `Fill` połączenie zostało otwarte, zamyka również połączenie po `Fill` zakończeniu. Może to uprościć kod, gdy zajmujesz się jedną operacją, taką `Fill` jak `Update`lub. Jednak w przypadku wykonywania wielu operacji, które wymagają otwartego połączenia, można zwiększyć wydajność aplikacji przez jawne wywołanie `Open` metody `Connection`, wykonanie operacji względem źródła danych i następnie wywoływanie `Close` metody `Connection`. Aby zwolnić zasoby używane przez inne aplikacje klienckie, należy podjąć próbę zablokowania połączenia ze źródłem danych.  
  
## <a name="multiple-result-sets"></a>Wiele zestawów wyników  
 Jeśli napotkają wiele zestawów wyników, tworzy wiele tabel `DataSet`w. `DataAdapter` Tabele uzyskują przyrostową domyślną nazwę tabeli*N*, zaczynając od "Table" dla TABLE0. Jeśli nazwa tabeli jest przenoszona jako argument do `Fill` metody, tabele uzyskują przyrostową domyślną nazwę tabeliname*N*, rozpoczynając od "TableName" dla TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Wypełnianie zestawu danych z wielu kart DataAdapters  
 Dowolna liczba `DataAdapter` obiektów może być używana `DataSet`z. Każdy `DataAdapter` z nich może służyć do wypełnienia jednego lub `DataTable` większej liczby obiektów i rozwiązania aktualizacji z powrotem do odpowiedniego źródła danych. `DataRelation`i `Constraint` obiekty można dodać `DataSet` do lokalnego, co umożliwia powiązanie danych z niepodobnymi źródłami danych. Na przykład `DataSet` może zawierać dane z Microsoft SQL Server bazy danych, bazy danych IBM DB2 uwidocznionej za pośrednictwem OLE DB i źródła danych, które przesyła strumieniowo XML. Co najmniej jeden obiekt może obsługiwać komunikację z każdym źródłem danych. `DataAdapter`  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wypełnia listę klientów z `Northwind` bazy danych w Microsoft SQL Server i listę zamówień `Northwind` z bazy danych przechowywanej w programie Microsoft Access 2000. Wypełnione tabele są powiązane z `DataRelation`, a lista klientów jest następnie wyświetlana wraz z zamówieniami dla tego klienta. Aby uzyskać więcej informacji `DataRelation` na temat obiektów, zobacz [Dodawanie relacji](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) danych i nawigowanie po [relacjach](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)danych.  
  
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
  
## <a name="sql-server-decimal-type"></a>SQL Server Typ dziesiętny  
 Domyślnie `DataSet` dane są przechowywane przy użyciu .NET Framework typów danych. W przypadku większości aplikacji zapewniają one wygodną reprezentację informacji o źródle danych. Jednakże ta reprezentacja może spowodować problem, gdy typ danych w źródle danych jest SQL Server dziesiętny lub numeryczny typ danych. Typ danych `decimal` .NET Framework dopuszcza maksymalnie 28 cyfr znaczących, podczas gdy typ danych SQL Server `decimal` umożliwia 38 cyfr znaczących. Jeśli podczas operacji decyduje, że dokładność pola SQL Server `decimal` jest większa niż 28 znaków, bieżący wiersz nie zostanie dodany do `DataTable`. `SqlDataAdapter` `Fill` Zamiast tego wystąpi zdarzenie, które pozwala określić, czy nastąpi utrata dokładności i odpowiednio reagować. `FillError` Aby uzyskać więcej informacji o `FillError` zdarzeniu, zobacz [Obsługa zdarzeń DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). Aby uzyskać SQL Server `decimal` wartość, można również <xref:System.Data.SqlClient.SqlDataReader> użyć obiektu i wywołać <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metodę.  
  
 W programie ADO.NET 2,0 wprowadzono rozszerzoną obsługę programuwprogramie.`DataSet` <xref:System.Data.SqlTypes> Aby uzyskać więcej informacji, zobacz SqlTypes [i zestaw danych](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>Rozdziały OLE DB  
 Hierarchiczne zestawy wierszy lub rozdziały (typ `DBTYPE_HCHAPTER`OLE DB, typ `adChapter`ADO) mogą być używane do `DataSet`wypełniania zawartości. Gdy napotkają kolumnę z rozdziałem `Fill` podczas operacji, `DataTable` jest tworzona dla kolumny z rozdziałem, a ta tabela jest wypełniana kolumnami i wierszami z rozdziału. <xref:System.Data.OleDb.OleDbDataAdapter> Tabela utworzona dla kolumny z rozdziałem jest nazywana przy użyciu nazwy tabeli nadrzędnej i nazwy kolumny rozdziału w postaci "*ParentTableNameChapteredColumnName*". Jeśli tabela już istnieje w `DataSet` , która jest zgodna z nazwą kolumny z rozdziałem, bieżąca tabela jest wypełniana danymi rozdziału. Jeśli w istniejącej tabeli nie ma kolumn pasujących do kolumny znalezionej w rozdziale, zostanie dodana nowa kolumna.  
  
 Przed zapełnieniem tabel `DataSet` w obiekcie, które znajdują się w kolumnie z rozdziałem, relacja jest tworzona między tabelami nadrzędnymi i podrzędnymi hierarchicznego zestawu wierszy przez dodanie kolumny Integer do tabeli nadrzędnej i podrzędnej, ustawienie kolumny nadrzędnej na Funkcja autoprzyrost i tworzenie `DataRelation` przy użyciu dodanych kolumn z obu tabel. Dodana relacja nosi nazwę przy użyciu tabeli nadrzędnej i nazw kolumn rozdziałów w postaci "*ParentTableNameChapterColumnName*".  
  
 Zwróć uwagę, że kolumna powiązane istnieje tylko w `DataSet`. Kolejne wypełnienia ze źródła danych mogą spowodować dodanie nowych wierszy do tabel zamiast zmian scalanych do istniejących wierszy.  
  
 Należy również pamiętać, że jeśli używasz `DataAdapter.Fill` przeciążenia, które `DataTable`pobiera, tylko ta tabela zostanie wypełniona. Do tabeli zostanie dodana kolumna o podwójnej liczbie całkowitej, ale żadna tabela podrzędna nie zostanie utworzona lub nie zostanie wypełniona, a relacja nie zostanie utworzona.  
  
 Poniższy przykład używa dostawcy MSDataShape w celu wygenerowania kolumny rozdział zamówień dla każdego klienta na liście klientów. A `DataSet` następnie jest wypełniony danymi.  
  
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
  
 `Customers` `CustomersOrders`Po zakończeniu `Fill` `DataSet` operacji zawiera dwie tabele: i, gdzie `CustomersOrders` reprezentuje kolumnę z rozdziałem. Dodatkowa kolumna o nazwie `Orders` zostanie dodana `Customers` do tabeli, a dodatkowa kolumna `CustomersOrders` o nazwie `CustomersOrders` zostanie dodana do tabeli. `Orders` Kolumna`Customers` w tabeli ma ustawioną funkcję autoprzyrost. A `DataRelation` `Customers` , `CustomersOrders`, jest tworzony przy użyciu kolumn, które zostały dodane do tabel jako tabela nadrzędna. W poniższych tabelach przedstawiono niektóre przykładowe wyniki.  
  
### <a name="tablename-customers"></a>TableName Klientów  
  
|Identyfikator|CompanyName|Zamówienie|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|P Trujillo Emparedados y Helados|1|  
  
### <a name="tablename-customersorders"></a>TableName CustomersOrders  
  
|Identyfikator|Wartooć|CustomersOrders|  
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
