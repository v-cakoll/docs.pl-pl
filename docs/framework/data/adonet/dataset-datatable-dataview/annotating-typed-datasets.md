---
title: Dodawanie adnotacji do Typizowane zbiory danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 1974ac71e367203b8b94375e43d4fde13f2df51f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="annotating-typed-datasets"></a>Dodawanie adnotacji do Typizowane zbiory danych
Adnotacje umożliwiają modyfikowanie nazwy elementów w wpisaną <xref:System.Data.DataSet> bez modyfikowania schematu podstawowego. Modyfikowanie nazwy elementów w źródłowej schemat spowodowałoby wpisanego **DataSet** do odwoływania się do obiektów, które nie istnieje w źródle danych, jak również utracić odwołania do obiektów, które istnieją w źródle danych.  
  
 Korzystanie z adnotacji, można dostosować nazwy obiektów w wpisaną **DataSet** z bardziej zrozumiałej nazwy, dzięki czemu czytelność kodu i wpisaną **zestawu danych** ułatwia klientom na użycie, pozostawiając Podstawowy schemat bez zmian. Na przykład następujący element schematu dla **klientów** spis **Northwind** bazy danych spowoduje powstanie **DataRow** nazwę obiektu  **CustomersRow** i <xref:System.Data.DataRowCollection> o nazwie **klientów**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **kolekcji DataRowCollection** nazwa **klientów** znaczenie w kodu klienta, ale **DataRow** nazwa **CustomersRow** jest błąd ponieważ jest to pojedynczy obiekt. Wspólnych scenariuszy, obiekt może być również określany bez **wiersza** identyfikator i zamiast tego będzie można po prostu nazywany **klienta** obiektu. Rozwiązanie to adnotacji schematu i identyfikować nowe nazwy **DataRow** i **kolekcji DataRowCollection** obiektów. Poniżej znajduje się adnotacjami wersja poprzedniego schematu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Określanie **nazwy wpisanej** wartość **klienta** spowoduje **DataRow** nazwę obiektu **klienta**. Określanie **typedPlural** wartość **klientów** zachowuje **kolekcji DataRowCollection** nazwa **klientów**.  
  
 W poniższej tabeli przedstawiono dostępne do użycia adnotacji.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**typedName**|Nazwa obiektu.|  
|**typedPlural**|Nazwa kolekcji obiektów.|  
|**typedParent**|Nazwa obiektu określonego w relacji nadrzędny.|  
|**typedChildren**|Nazwa metody zwracać obiekty z relacji podrzędnych.|  
|**nullValue**|Wartość, gdy jest odpowiednia wartość **DBNull**. Zobacz poniższą tabelę dla **nullValue** adnotacji. Wartość domyślna to **_throw**.|  
  
 W poniższej tabeli przedstawiono wartości, które można określić dla **nullValue** adnotacji.  
  
|nullValue wartość|Opis|  
|---------------------|-----------------|  
|*Wartość zastępczą*|Określ wartość zwracaną. Zwracana wartość musi odpowiadać typowi elementu. Na przykład użyć `nullValue="0"` do zwraca wartość 0 dla pól całkowitych wartości null.|  
|**_throw**|Zgłoś wyjątek. Domyślnie włączone.|  
|**_null**|Zwraca odwołanie o wartości null lub zgłosić wyjątek, jeśli typ pierwotny.|  
|**_empty**|Ciągi, zwróć **String.Empty**, w przeciwnym razie zwraca obiekt, który został utworzony na podstawie pustego konstruktora. Jeśli typ pierwotny, Zgłoś wyjątek.|  
  
 W poniższej tabeli przedstawiono wartości domyślne dla obiektów w typizowanych **DataSet** i dostępne adnotacji.  
  
|Metody obiektu lub zdarzenia|Domyślny|Adnotacja|  
|---------------------------|-------------|----------------|  
|**Element DataTable**|TableNameDataTable|typedPlural|  
|**Element DataTable** metody|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**Element DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Właściwość**|PropertyName|typedName|  
|**Podrzędne** metody dostępu|GetChildTableNameRows|typedChildren|  
|**Nadrzędny** metody dostępu|TableNameRow|typedParent|  
|**Zestaw danych** zdarzeń|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Aby użyć wpisane **zestawu danych** adnotacje, należy uwzględnić następujące **xmlns** odwołania w schemat schematu XML definition language (XSD). (Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Poniżej przedstawiono przykładowe schematu adnotacjami, udostępniający **klientów** spis **Northwind** bazy danych z relacji do **zamówień** tabeli uwzględnione.  
  
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
  
 Poniższy przykład kodu wykorzystuje silnie typizowaną **DataSet** utworzone na podstawie schematu próbki. Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia **klientów** tabelami <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia **zamówień** tabeli. Silnie typizowaną **DataSet** definiuje **DataRelations**.  
  
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
    customers.Customers.NewCustomeromer()  
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
    customers.Customers.NewCustomeromer();  
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
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
