---
title: Wypełnianie zestawu danych z elementu DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: d2d7719c7f6c2cacd6d68ecae226673248bbd680
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149235"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Wypełnianie zestawu danych z elementu DataAdapter
ADO.NET <xref:System.Data.DataSet> jest reprezentacją danych rezydentną w pamięci, która zapewnia spójny model programowania relacyjnego niezależny od źródła danych. Reprezentuje `DataSet` kompletny zestaw danych, który zawiera tabele, ograniczenia i relacje między tabelami. Ponieważ `DataSet` jest niezależna od źródła `DataSet` danych, a może zawierać dane lokalne do aplikacji i dane z wielu źródeł danych. Interakcja z istniejącymi źródłami danych jest kontrolowana za pośrednictwem pliku `DataAdapter`.  
  
 Właściwość `SelectCommand` `DataAdapter` obiektu jest `Command` obiektem pobieranym dane ze źródła danych. Obiekty `InsertCommand` `UpdateCommand`, `DeleteCommand` i właściwości `DataAdapter` obiektów `Command` są, które zarządzają aktualizacjami danych w źródle danych `DataSet`zgodnie z modyfikacjami wprowadzonymi do danych w pliku . Te właściwości są bardziej szczegółowo opisane w [aktualizacji źródeł danych za pomocą programów DataAdapters](updating-data-sources-with-dataadapters.md).  
  
 Metoda `Fill` `DataAdapter` jest używana do zapełnienia `DataSet` a z `SelectCommand` wynikami `DataAdapter`. `Fill`przyjmuje za swoje `DataSet` argumenty a do `DataTable` wypełnienia, a obiekt `DataTable` lub nazwę do wypełnienia wierszami zwróconymi z `SelectCommand`.  
  
> [!NOTE]
> Za `DataAdapter` pomocą do pobrania wszystkich tabeli wymaga czasu, zwłaszcza jeśli istnieje wiele wierszy w tabeli. Dzieje się tak, ponieważ uzyskiwanie dostępu do bazy danych, lokalizowanie i przetwarzanie danych, a następnie przesyłanie danych do klienta jest czasochłonne. Ciągnięcie całej tabeli do klienta blokuje również wszystkie wiersze na serwerze. Aby zwiększyć wydajność, można `WHERE` użyć klauzuli, aby znacznie zmniejszyć liczbę wierszy zwróconych do klienta. Można również zmniejszyć ilość danych zwróconych do klienta tylko jawnie aukcji `SELECT` wymaganych kolumn w instrukcji. Innym dobrym rozwiązaniem jest pobranie wierszy w partiach (na przykład kilkaset wierszy naraz) i pobieranie następnej partii tylko po zakończeniu klienta z bieżącą partią.  
  
 Metoda `Fill` używa `DataReader` obiektu niejawnie do zwrócenia nazw kolumn i typów, które `DataSet`są używane do tworzenia tabel w , i `DataSet`danych do wypełniania wierszy tabel w . Tabele i kolumny są tworzone tylko wtedy, gdy jeszcze nie istnieją; w `Fill` przeciwnym razie `DataSet` używa istniejącego schematu. Typy kolumn są tworzone jako typy programu .NET Framework zgodnie z tabelami w [mapowaniach typów danych w ADO.NET](data-type-mappings-in-ado-net.md). Klucze podstawowe nie są tworzone, chyba `DataAdapter`że istnieją w źródle danych i **.**`MissingSchemaAction` jest ustawiona na `MissingSchemaAction` **.** `AddWithKey`. Jeśli `Fill` stwierdzi, że klucz podstawowy istnieje dla tabeli, `DataSet` zastąpi dane z danymi ze źródła danych dla wierszy, w których wartości kolumny klucza podstawowego są zgodne z wartościami wiersza zwróconego ze źródła danych. Jeśli nie zostanie znaleziony żaden klucz podstawowy, dane są `DataSet`dołączane do tabel w pliku . `Fill`używa wszelkich mapowań, które mogą istnieć `DataSet` podczas wypełniania (zobacz [DataAdapter DataTable i DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Jeśli `SelectCommand` zwraca wyniki SPRZĘŻENIA `DataAdapter` ZEWNĘTRZNEGO, nie `PrimaryKey` ustawia wartości `DataTable`wynikowego . Należy zdefiniować `PrimaryKey` samodzielnie, aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy przykład kodu tworzy <xref:System.Data.SqlClient.SqlDataAdapter> wystąpienie, <xref:System.Data.SqlClient.SqlConnection> które używa do `Northwind` bazy danych programu <xref:System.Data.DataTable> Microsoft `DataSet` SQL Server i wypełnia w a z listy klientów. Instrukcja SQL <xref:System.Data.SqlClient.SqlConnection> i argumenty <xref:System.Data.SqlClient.SqlDataAdapter> przekazywane do konstruktora są używane do tworzenia <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> właściwości <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
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
> Kod pokazany w tym przykładzie nie otwiera `Connection`jawnie i zamyka plik . Metoda `Fill` niejawnie `Connection` otwiera, `DataAdapter` że używa, jeśli stwierdzi, że połączenie nie jest jeszcze otwarte. Po `Fill` otwarciu połączenia, to również `Fill` zamyka połączenie po zakończeniu. Może to uprościć kod, gdy masz `Fill` do `Update`czynienia z pojedynczą operacją, taką jak a lub . Jeśli jednak wykonujesz wiele operacji, które wymagają otwartego połączenia, możesz poprawić wydajność `Open` aplikacji, `Connection`jawnie wywołując metodę , wykonując operacje `Close` ze `Connection`źródłem danych, a następnie wywołując metodę . Należy starać się zachować połączenia ze źródłem danych otwarte tak krótko, jak to możliwe, aby zwolnić zasoby do użytku przez inne aplikacje klienckie.  
  
## <a name="multiple-result-sets"></a>Wiele zestawów wyników  
 Jeśli `DataAdapter` napotka wiele zestawów wyników, `DataSet`tworzy wiele tabel w . Tabele otrzymują przyrostową domyślną nazwę tabeli*N,* zaczynając od "Tabela" dla tabeli0. Jeśli nazwa tabeli jest przekazywana jako argument do `Fill` metody, tabele otrzymują przyrostową domyślną nazwę TableName*N,* począwszy od "TableName" dla TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Wypełnianie zestawu danych z wielu danychAdapters  
 Z dowolnym obiektem `DataAdapter` `DataSet`można używać dowolnej liczby obiektów z obiektem . Każdy `DataAdapter` może służyć do wypełnienia `DataTable` jednego lub więcej obiektów i rozpoznać aktualizacje z powrotem do odpowiedniego źródła danych. `DataRelation`i `Constraint` obiekty mogą być `DataSet` dodawane do lokalnie, co umożliwia powiązanie danych z różnych źródeł danych. Na przykład `DataSet` może zawierać dane z bazy danych programu Microsoft SQL Server, bazy danych IBM DB2 udostępniane za pośrednictwem ole DB i źródła danych, które strumieniuje XML. Jeden lub `DataAdapter` więcej obiektów może obsługiwać komunikację z każdym źródłem danych.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wypełnia listę klientów `Northwind` z bazy danych na programie Microsoft SQL `Northwind` Server oraz listę zamówień z bazy danych przechowywanej w programie Microsoft Access 2000. Wypełnione tabele są `DataRelation`powiązane z programem , a lista odbiorców jest następnie wyświetlana z zamówieniami dla tego odbiorcy. Aby uzyskać `DataRelation` więcej informacji o obiektach, zobacz [Dodawanie danychrelacji](./dataset-datatable-dataview/adding-datarelations.md) i [nawigowanie do danych](./dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>Typ dziesiętny programu SQL Server  
 Domyślnie przechowuje `DataSet` dane przy użyciu typów danych .NET Framework. W przypadku większości aplikacji zapewniają one wygodną reprezentację informacji o źródle danych. Jednak ta reprezentacja może powodować problem, gdy typ danych w źródle danych jest typem danych dziesiętnych lub liczbowych programu SQL Server. Typ danych `decimal` programu .NET Framework umożliwia maksymalnie 28 cyfr znaczących, podczas gdy typ danych programu SQL Server `decimal` umożliwia 38 cyfr znaczących. Jeśli `SqlDataAdapter` podczas `Fill` operacji zostanie stwierdzi, że `decimal` dokładność pola programu SQL Server jest większa niż `DataTable`28 znaków, bieżący wiersz nie zostanie dodany do pliku . Zamiast tego `FillError` występuje zdarzenie, które umożliwia określenie, czy wystąpi utrata precyzji i odpowiednio reagować. Aby uzyskać więcej `FillError` informacji na temat zdarzenia, zobacz [Obsługa zdarzeń dataadapter](handling-dataadapter-events.md). Aby uzyskać wartość `decimal` programu SQL Server, <xref:System.Data.SqlClient.SqlDataReader> można również <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> użyć obiektu i wywołać metodę.  
  
 ADO.NET 2.0 wprowadzono rozszerzone wsparcie <xref:System.Data.SqlTypes> w `DataSet`. Aby uzyskać więcej informacji, zobacz [SqlTypes i DataSet](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>Rozdziały OLE DB  
 Hierarchiczne zestawy wierszy lub rozdziały (typ `DBTYPE_HCHAPTER`OLE `adChapter`DB , typ ADO `DataSet`) mogą być używane do wypełniania zawartości pliku . Gdy <xref:System.Data.OleDb.OleDbDataAdapter> napotka roz chaptered `Fill` kolumny `DataTable` podczas operacji, a jest tworzony dla kolumny rozdziałów, a tabela jest wypełniona kolumn i wierszy z rozdziału. Tabela utworzona dla kolumny rozdzielanej nosi nazwę zarówno nazwy tabeli nadrzędnej, jak i nazwy kolumny rozdzielanej w formularzu "*ParentTableNameChapteredColumnName*". Jeśli tabela już istnieje `DataSet` w nazwie kolumny roz chaptered, bieżąca tabela jest wypełniona danymi rozdziału. Jeśli w istniejącej tabeli nie ma kolumny zgodnej z kolumną znalezioną w rozdziale, dodawana jest nowa kolumna.  
  
 Przed wypełnionymi `DataSet` tabelami w kolumnach rozdziałów tworzona jest relacja między tabelami nadrzędnymi i podrzędnymi hierarchicznego zestawu wierszy przez dodanie kolumny całkowitej do tabeli nadrzędnej i `DataRelation` podrzędnej, ustawienie kolumny nadrzędnej na automatyczny przyrost i utworzenie przy użyciu dodanych kolumn z obu tabel. Dodana relacja jest nazywana przy użyciu nazw tabeli nadrzędnej i kolumn rozdziału w formularzu "*ParentTableNameChapterColumnName*".  
  
 Należy zauważyć, że powiązana `DataSet`kolumna istnieje tylko w pliku . Kolejne wypełnienia ze źródła danych mogą powodować dodawanie nowych wierszy do tabel zamiast scalania zmian z istniejącymi wierszami.  
  
 Należy również zauważyć, że `DataAdapter.Fill` w przypadku `DataTable`użycia przeciążenia, które ma , tylko ta tabela zostanie wypełniona. Kolumna liczby całkowitej automatycznego zwiększania liczby całkowitej nadal będzie dodawana do tabeli, ale nie zostanie utworzona ani wypełniona żadna tabela podrzędna i nie zostanie utworzona żadna relacja.  
  
 W poniższym przykładzie użyto dostawcy MSDataShape do generowania kolumny rozdział zamówień dla każdego klienta na liście odbiorców. A `DataSet` jest następnie wypełniona danymi.  
  
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
  
 Po `Fill` zakończeniu `DataSet` operacji zawiera dwie `Customers` tabele: i `CustomersOrders`, gdzie `CustomersOrders` reprezentuje kolumnę rozdziałów. Dodatkowa kolumna `Orders` o nazwie `Customers` zostanie dodana do `CustomersOrders` tabeli, `CustomersOrders` a do tabeli zostanie dodana dodatkowa kolumna o nazwie. Kolumna `Orders` w `Customers` tabeli jest ustawiona na automatyczne zwiększanie. A `DataRelation` `CustomersOrders`, jest tworzony przy użyciu kolumn, które `Customers` zostały dodane do tabel z jako tabela nadrzędna. W poniższych tabelach przedstawiono niektóre przykładowe wyniki.  
  
### <a name="tablename-customers"></a>Nazwa tabeli: Klienci  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|Alfki|Alfreds Futterkiste|0|  
|ANATR (ANATR)|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>Nazwa tabeli: CustomersOrders  
  
|CustomerID|OrderID|Liczba zamówień na klientów|  
|----------------|-------------|---------------------|  
|Alfki|10643|0|  
|Alfki|10692|0|  
|ANATR (ANATR)|10308|1|  
|ANATR (ANATR)|10625|1|  
  
## <a name="see-also"></a>Zobacz też

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Wiele aktywnych zestawów wyników (MARS)](./sql/multiple-active-result-sets-mars.md)
- [Omówienie ADO.NET](ado-net-overview.md)
