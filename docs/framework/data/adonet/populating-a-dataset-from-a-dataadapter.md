---
title: Wypełnianie zestawu danych z elementu DataAdapter
description: Dowiedz się, jak wypełnić zestaw danych z elementu DataAdapter w ADO.NET, który zapewnia spójny relacyjny model programowania niezależnie od źródła danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 3d4da840e1d51ec6f309915787caa8891db3eb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286666"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>Wypełnianie zestawu danych z elementu DataAdapter
ADO.NET <xref:System.Data.DataSet> to reprezentacja danych znajdujących się w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych. `DataSet`Reprezentuje kompletny zestaw danych, który zawiera tabele, ograniczenia i relacje między tabelami. Ponieważ `DataSet` program jest niezależny od źródła danych, `DataSet` może obejmować dane lokalne do aplikacji oraz dane z wielu źródeł danych. Interakcje z istniejącymi źródłami danych są kontrolowane przez program `DataAdapter` .  
  
 `SelectCommand`Właściwość `DataAdapter` jest `Command` obiektem, który pobiera dane ze źródła danych. `InsertCommand`Właściwości, `UpdateCommand` i `DeleteCommand` `DataAdapter` są obiektami, `Command` które zarządzają aktualizacjami danych w źródle danych, w zależności od zmian wprowadzonych w danych w `DataSet` . Te właściwości są szczegółowo omówione w temacie [Aktualizowanie źródeł danych za pomocą adapterów](updating-data-sources-with-dataadapters.md).  
  
 `Fill`Metoda `DataAdapter` jest używana do wypełniania `DataSet` wynikami `SelectCommand` `DataAdapter` . `Fill`przyjmuje jako argumenty `DataSet` , które mają być wypełnione, a `DataTable` obiekt lub nazwę `DataTable` do wypełnienia wierszami zwracanymi z `SelectCommand` .  
  
> [!NOTE]
> `DataAdapter`Pobieranie całej tabeli trwa przy użyciu programu, zwłaszcza jeśli w tabeli znajduje się wiele wierszy. Dzieje się tak dlatego, że dostęp do bazy danych, lokalizowanie i przetwarzanie danych, a następnie Transferowanie danych do klienta odbywa się czasochłonnie. Przeciągnięcie całej tabeli do klienta spowoduje również zablokowanie wszystkich wierszy na serwerze. Aby zwiększyć wydajność, można użyć klauzuli, `WHERE` aby znacznie zmniejszyć liczbę wierszy zwracanych do klienta. Możesz również zmniejszyć ilość danych zwracanych do klienta, tylko jawnie wymieniając wymagane kolumny w `SELECT` instrukcji. Innym dobrym rozwiązaniem jest pobranie wierszy w partiach (takich jak kilka setek wierszy w danym momencie) i pobranie kolejnej partii, gdy klient zostanie zakończony przy użyciu bieżącej partii.  
  
 `Fill`Metoda używa `DataReader` obiektu niejawnie do zwracania nazw kolumn i typów, które są używane do tworzenia tabel w `DataSet` , i danych do wypełniania wierszy tabel w `DataSet` . Tabele i kolumny są tworzone tylko wtedy, gdy jeszcze nie istnieją; w przeciwnym razie `Fill` stosuje istniejący `DataSet` schemat. Typy kolumn są tworzone jako typy .NET Framework zgodnie z tabelami w [mapowaniu typu danych w ADO.NET](data-type-mappings-in-ado-net.md). Klucze podstawowe nie są tworzone, chyba że istnieją w źródle danych i `DataAdapter` **.**`MissingSchemaAction` jest ustawiona na `MissingSchemaAction` **.** `AddWithKey` . Jeśli `Fill` okaże się, że klucz podstawowy istnieje dla tabeli, spowoduje to zastąpienie danych w danych z `DataSet` danymi ze źródła danych dla wierszy, w których wartości kolumny klucza podstawowego są zgodne z wierszami zwróconymi ze źródła danych. Jeśli klucz podstawowy nie zostanie znaleziony, dane są dołączane do tabel w `DataSet` . `Fill`używa wszelkich mapowań, które mogą istnieć podczas wypełniania `DataSet` (zobacz [mapowania DataAdapter DataTable i DataColumn](dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> Jeśli `SelectCommand` zwraca wyniki sprzężenia zewnętrznego, `DataAdapter` obiekt nie ustawia `PrimaryKey` wartości wynikowej `DataTable` . Należy zdefiniować siebie, `PrimaryKey` Aby upewnić się, że zduplikowane wiersze są poprawnie rozpoznawane. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Poniższy przykład kodu tworzy wystąpienie <xref:System.Data.SqlClient.SqlDataAdapter> , które używa <xref:System.Data.SqlClient.SqlConnection> do `Northwind` bazy danych Microsoft SQL Server i wypełnia <xref:System.Data.DataTable> `DataSet` listę klientów w a. Instrukcja SQL i <xref:System.Data.SqlClient.SqlConnection> argumenty przekazane do <xref:System.Data.SqlClient.SqlDataAdapter> konstruktora są używane do tworzenia <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> właściwości <xref:System.Data.SqlClient.SqlDataAdapter> .  
  
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
> Kod przedstawiony w tym przykładzie nie jest jawnie otwarty i zamknięty `Connection` . `Fill`Metoda niejawnie otwiera `Connection` , czy `DataAdapter` jest używana, jeśli stwierdzi, że połączenie nie jest jeszcze otwarte. Jeśli `Fill` połączenie zostało otwarte, zamyka również połączenie po `Fill` zakończeniu. Może to uprościć kod, gdy zajmujesz się jedną operacją, taką jak `Fill` lub `Update` . Jednak w przypadku wykonywania wielu operacji, które wymagają otwartego połączenia, można zwiększyć wydajność aplikacji, jawnie wywołując `Open` metodę `Connection` , wykonując operacje względem źródła danych, a następnie wywołując `Close` metodę `Connection` . Aby zwolnić zasoby używane przez inne aplikacje klienckie, należy podjąć próbę zablokowania połączenia ze źródłem danych.  
  
## <a name="multiple-result-sets"></a>Wiele zestawów wyników  
 Jeśli `DataAdapter` napotkają wiele zestawów wyników, tworzy wiele tabel w `DataSet` . Tabele uzyskują przyrostową domyślną nazwę tabeli*N*, zaczynając od "Table" dla TABLE0. Jeśli nazwa tabeli jest przenoszona jako argument do `Fill` metody, tabele uzyskują przyrostową domyślną nazwę tabeliname*N*, rozpoczynając od "TableName" dla TableName0.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Wypełnianie zestawu danych z wielu kart DataAdapters  
 Dowolna liczba `DataAdapter` obiektów może być używana z `DataSet` . Każdy `DataAdapter` z nich może służyć do wypełnienia jednego lub większej liczby `DataTable` obiektów i rozwiązania aktualizacji z powrotem do odpowiedniego źródła danych. `DataRelation`i `Constraint` obiekty można dodać do `DataSet` lokalnego, co umożliwia powiązanie danych z niepodobnymi źródłami danych. Na przykład `DataSet` może zawierać dane z Microsoft SQL Server bazy danych, bazy danych IBM DB2 uwidocznionej za pośrednictwem OLE DB i źródła danych, które przesyła strumieniowo XML. Co najmniej jeden `DataAdapter` obiekt może obsługiwać komunikację z każdym źródłem danych.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wypełnia listę klientów z `Northwind` bazy danych w Microsoft SQL Server i listę zamówień z `Northwind` bazy danych przechowywanej w programie Microsoft Access 2000. Wypełnione tabele są powiązane z `DataRelation` , a lista klientów jest następnie wyświetlana wraz z zamówieniami dla tego klienta. Aby uzyskać więcej informacji na temat `DataRelation` obiektów, zobacz [Dodawanie relacji](./dataset-datatable-dataview/adding-datarelations.md) danych i [nawigowanie po relacjach](./dataset-datatable-dataview/navigating-datarelations.md)danych.  
  
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
 Domyślnie `DataSet` dane są przechowywane przy użyciu .NET Framework typów danych. W przypadku większości aplikacji zapewniają one wygodną reprezentację informacji o źródle danych. Jednakże ta reprezentacja może spowodować problem, gdy typ danych w źródle danych jest SQL Server dziesiętny lub numeryczny typ danych. `decimal`Typ danych .NET Framework dopuszcza maksymalnie 28 cyfr znaczących, podczas gdy `decimal` typ danych SQL Server umożliwia 38 cyfr znaczących. Jeśli `SqlDataAdapter` podczas operacji decyduje, `Fill` że dokładność `decimal` pola SQL Server jest większa niż 28 znaków, bieżący wiersz nie zostanie dodany do `DataTable` . Zamiast tego `FillError` wystąpi zdarzenie, które pozwala określić, czy nastąpi utrata dokładności i odpowiednio reagować. Aby uzyskać więcej informacji o `FillError` zdarzeniu, zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md). Aby uzyskać SQL Server `decimal` wartość, można również użyć <xref:System.Data.SqlClient.SqlDataReader> obiektu i wywołać <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> metodę.  
  
 W programie ADO.NET 2,0 wprowadzono rozszerzoną obsługę programu <xref:System.Data.SqlTypes> w programie `DataSet` . Aby uzyskać więcej informacji, zobacz [SqlTypes i zestaw danych](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>Rozdziały OLE DB  
 Hierarchiczne zestawy wierszy lub rozdziały (typ OLE DB `DBTYPE_HCHAPTER` , typ ADO `adChapter` ) mogą być używane do wypełniania zawartości `DataSet` . Gdy <xref:System.Data.OleDb.OleDbDataAdapter> napotkają kolumnę z rozdziałem podczas `Fill` operacji, `DataTable` jest tworzona dla kolumny z rozdziałem, a ta tabela jest wypełniana kolumnami i wierszami z rozdziału. Tabela utworzona dla kolumny z rozdziałem jest nazywana przy użyciu nazwy tabeli nadrzędnej i nazwy kolumny rozdziału w postaci "*ParentTableNameChapteredColumnName*". Jeśli tabela już istnieje w, `DataSet` która jest zgodna z nazwą kolumny z rozdziałem, bieżąca tabela jest wypełniana danymi rozdziału. Jeśli w istniejącej tabeli nie ma kolumn pasujących do kolumny znalezionej w rozdziale, zostanie dodana nowa kolumna.  
  
 Przed `DataSet` zapełnieniem tabel w obiekcie, które znajdują się w kolumnie z rozdziałem, relacja jest tworzona między tabelami nadrzędnymi i podrzędnymi hierarchicznego zestawu wierszy poprzez dodanie kolumny liczb całkowitych do tabeli nadrzędnej i podrzędnej, ustawienie kolumny nadrzędnej na automatycznie przyrostowe i utworzenie `DataRelation` przy użyciu dodanych kolumn z obu tabel. Dodana relacja nosi nazwę przy użyciu tabeli nadrzędnej i nazw kolumn rozdziałów w postaci "*ParentTableNameChapterColumnName*".  
  
 Zwróć uwagę, że kolumna powiązane istnieje tylko w `DataSet` . Kolejne wypełnienia ze źródła danych mogą spowodować dodanie nowych wierszy do tabel zamiast zmian scalanych do istniejących wierszy.  
  
 Należy również pamiętać, że jeśli używasz `DataAdapter.Fill` przeciążenia, które pobiera `DataTable` , tylko ta tabela zostanie wypełniona. Do tabeli zostanie dodana kolumna o podwójnej liczbie całkowitej, ale żadna tabela podrzędna nie zostanie utworzona lub nie zostanie wypełniona, a relacja nie zostanie utworzona.  
  
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
  
 Po `Fill` zakończeniu operacji `DataSet` zawiera dwie tabele: `Customers` i `CustomersOrders` , gdzie `CustomersOrders` reprezentuje kolumnę z rozdziałem. Dodatkowa kolumna o nazwie `Orders` zostanie dodana do `Customers` tabeli, a dodatkowa kolumna o nazwie `CustomersOrders` zostanie dodana do `CustomersOrders` tabeli. `Orders`Kolumna w `Customers` tabeli ma ustawioną funkcję autoprzyrost. A `DataRelation` , `CustomersOrders` , jest tworzony przy użyciu kolumn, które zostały dodane do tabel `Customers` jako tabela nadrzędna. W poniższych tabelach przedstawiono niektóre przykładowe wyniki.  
  
### <a name="tablename-customers"></a>TableName: Customers  
  
|CustomerID|CompanyName|Orders|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|P Trujillo Emparedados y Helados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataAdapter i DataReader](dataadapters-and-datareaders.md)
- [Mapowanie typu danych w ADO.NET](data-type-mappings-in-ado-net.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Wiele aktywnych zestawów wyników (MARS)](./sql/multiple-active-result-sets-mars.md)
- [Omówienie ADO.NET](ado-net-overview.md)
