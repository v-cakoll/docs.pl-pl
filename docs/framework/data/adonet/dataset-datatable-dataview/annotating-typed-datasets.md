---
title: Dodawanie adnotacji do typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151523"
---
# <a name="annotating-typed-datasets"></a>Dodawanie adnotacji do typizowanych elementów DataSet
Adnotacje umożliwiają modyfikowanie nazw elementów wpisywanych <xref:System.Data.DataSet> bez modyfikowania schematu źródłowego. Modyfikowanie nazw elementów w podstawowym schemacie spowodowałoby wpisane **DataSet** odwoływać się do obiektów, które nie istnieją w źródle danych, a także utracić odwołanie do obiektów, które istnieją w źródle danych.  
  
 Za pomocą adnotacji można dostosować nazwy obiektów w typie **DataSet** z bardziej znaczących nazw, dzięki czemu kod bardziej czytelny i wpisane **DataSet** łatwiejsze dla klientów, pozostawiając podstawowy schemat nienaruszone. Na przykład następujący element schematu dla tabeli **Klienci** bazy danych **Northwind** spowoduje nazwę obiektu <xref:System.Data.DataRowCollection> **DataRow** **customersrow** i **nazwanych klientów**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection** nazwa **klientów** ma znaczenie w kodzie klienta, ale **DataRow** nazwa **CustomersRow** jest mylące, ponieważ jest pojedynczy obiekt. Ponadto w typowych scenariuszach obiekt będzie się odwoływać bez **identyfikatora wiersza** i zamiast tego będzie po prostu określany jako **Customer** obiektu. Rozwiązaniem jest dodawanie adnotacji do schematu i identyfikowanie nowych nazw obiektów **DataRow** i **DataRowCollection.** Poniżej znajduje się wersja z adnotacjami poprzedniego schematu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Określenie **wpisanej wartościName** **klienta** spowoduje nazwę obiektu **DataRow** **klienta**. Określenie **wpisanej** Wartość wartość wartość **klienta** jest zachowywana przez **datarową** nazwę **klientów.**  
  
 W poniższej tabeli przedstawiono adnotacje dostępne do użycia.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**wpisaneName**|Nazwa obiektu.|  
|**typwzrówno-foniczny**|Nazwa kolekcji obiektów.|  
|**wpisaneParent**|Nazwa obiektu, o którym mowa w relacji nadrzędnej.|  
|**typedDzieci**|Nazwa metody zwracania obiektów z relacji podrzędnej.|  
|**nullValue**|Wartość, jeśli wartością bazową jest **DBNull**. Zobacz poniższą tabelę adnotacji **nullValue.** Wartość domyślna to **_throw**.|  
  
 W poniższej tabeli przedstawiono wartości, które można określić dla adnotacji **nullValue.**  
  
|Wartość nullValue|Opis|  
|---------------------|-----------------|  
|*Wartość zamienna*|Określ wartość, która ma zostać zwrócona. Zwracana wartość musi być zgodna z typem elementu. Na przykład `nullValue="0"` użyj do zwrócenia 0 dla pól całkowitej null.|  
|**_throw**|Zgłosić wyjątek. Domyślnie włączone.|  
|**_null**|Zwraca odwołanie null lub zgłoć wyjątek, jeśli zostanie napotkany typ pierwotny.|  
|**_empty**|W przypadku ciągów zwraca **ciąg.Pusty**, w przeciwnym razie zwraca obiekt utworzony z pustego konstruktora. Jeśli napotkany jest typ pierwotny, zgłoć wyjątek.|  
  
 W poniższej tabeli przedstawiono wartości domyślne dla obiektów w wpisanym **zestawie danych** i dostępne adnotacje.  
  
|Obiekt/metoda/zdarzenie|Domyślne|Adnotacja|  
|---------------------------|-------------|----------------|  
|**DataTable**|Tabela TableNameDataTable|typwzrówno-foniczny|  
|**DataTable (DataTable)** Metody|Nowy Nazwamowa<br /><br /> Dodaj pozycjęNamerow<br /><br /> Usuń pozycjęNamerow|wpisaneName|  
|**Datarowcollection**|TableName|typwzrówno-foniczny|  
|**Datarow**|Nazwa tabeli|wpisaneName|  
|**Datacolumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName (Nazwa.kolumna datarowa)|wpisaneName|  
|**Właściwość**|PropertyName|wpisaneName|  
|**Dziecko** Akcesor|GetChildTableNameRows (Wychocie Na łańszeń)|typedDzieci|  
|**Rodzic** Akcesor|Nazwa tabeli|wpisaneParent|  
|**Zestaw danych** Zdarzenia|Nazwamiorowasvent<br /><br /> TableNameRowChangeEventHandler|wpisaneName|  
  
 Aby używać wpisanych adnotacji **DataSet,** należy dołączyć następujące odwołanie xmlns do schematu języka XM (XSD) w języku xml schemacie definicji schematu schematu schematu schematu schematu schematu.To use typed DataSet adnotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema. Aby utworzyć xsd z tabel <xref:System.Data.DataSet.WriteXmlSchema%2A> bazy danych, zobacz lub [Praca z zestawami danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Poniżej przedstawiono przykładowy schemat z adnotacjami, który udostępnia tabelę **Klienci** bazy danych **Northwind** z relacją z tabelą **Zamówienia.**  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 Poniższy przykład kodu używa silnie **typizowanego zestawu danych** utworzonego na podstawie przykładowego schematu. Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania **tabeli Klienci,** a drugiego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania tabeli **Zamówienia.** Silnie typiwany **zestaw danych** definiuje **datarelations**.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typizowane elementy DataSet](typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
