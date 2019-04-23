---
title: Dodawanie adnotacji do typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085132"
---
# <a name="annotating-typed-datasets"></a>Dodawanie adnotacji do typizowanych elementów DataSet
Adnotacje umożliwiają modyfikowanie nazwy elementów w wpisaną <xref:System.Data.DataSet> bez modyfikowania schemat źródłowy. Modyfikowanie nazwy elementów w schemacie bazowego spowodowałoby wpisanego **DataSet** do odwoływania się do obiektów, które nie istnieją w źródle danych, a także stracić odwołania do obiektów, które istnieją w źródle danych.  
  
 Korzystanie z adnotacji, można dostosować nazwy obiektów w wpisaną **zestawu danych** z bardziej zrozumiałej nazwy, dzięki czemu czytelność kodu i wpisaną **DataSet** ułatwia klientom na użycie przy równoczesnym zachowaniu Schemat źródłowy bez zmian. Na przykład, następujący element schematu dla **klientów** tabeli **Northwind** bazy danych mogłoby spowodować **DataRow** nazwę obiektu  **CustomersRow** i <xref:System.Data.DataRowCollection> o nazwie **klientów**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **kolekcji DataRowCollection** nazwa **klientów** ma znaczenie w kodzie klienta, ale **DataRow** nazwa **CustomersRow** jest mylące ponieważ jest on pojedynczy obiekt. W typowych scenariuszy, obiekt może być również określany bez **wiersz** identyfikator i zamiast tego może być po prostu nazywany **klienta** obiektu. Rozwiązaniem jest dodawanie adnotacji do schematu i zidentyfikować nowe nazwy **DataRow** i **kolekcji DataRowCollection** obiektów. Poniżej przedstawiono adnotacjami wersja poprzedniego schematu.  
  
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
  
 W poniższej tabeli przedstawiono dostępne do użycia adnotacje.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**typedName**|Nazwa obiektu.|  
|**typedPlural**|Nazwa kolekcji obiektów.|  
|**typedParent**|Nazwa obiektu określonych w relacji nadrzędny.|  
|**typedChildren**|Nazwa metody, aby przywrócić obiekty z relacji podrzędnej.|  
|**nullValue**|Wartość, jeśli jest podstawową wartość **DBNull**. Zobacz w poniższej tabeli **nullValue** adnotacji. Wartość domyślna to **_throw**.|  
  
 W poniższej tabeli przedstawiono wartości, które mogą być określone dla **nullValue** adnotacji.  
  
|nullValue wartość|Opis|  
|---------------------|-----------------|  
|*Wartość zastąpienia*|Określ wartość do zwrócenia. Zwracana wartość musi odpowiadać typowi elementu. Na przykład użyć `nullValue="0"` do zwracają wartość 0 dla pola liczb całkowitych o wartości null.|  
|**_throw**|Zgłoś wyjątek. Domyślnie włączone.|  
|**_null**|Zwraca odwołanie o wartości null lub zgłosić wyjątek, jeśli typem pierwotnym zostanie osiągnięty.|  
|**_pusty**|W przypadku ciągów, zwracają **String.Empty**, w przeciwnym razie zwraca obiekt, który został utworzony na podstawie pustego konstruktora. Jeśli typ pierwotny, należy zgłosić wyjątek.|  
  
 W poniższej tabeli przedstawiono wartości domyślne dla obiektów w typizowanych **DataSet** i dostępne adnotacji.  
  
|Obiekt lub metoda/zdarzenia|Domyślny|Adnotacja|  
|---------------------------|-------------|----------------|  
|**Elementu DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** metody|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|Właściwość TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Property**|PropertyName|typedName|  
|**Podrzędne** metody dostępu|GetChildTableNameRows|typedChildren|  
|**Nadrzędny** metody dostępu|TableNameRow|typedParent|  
|**Zestaw danych** zdarzenia|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Aby użyć wpisane **zestawu danych** adnotacji, należy uwzględnić następujące **xmlns** odwołania w schemacie języka (XSD) definicji schematu XML. Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Poniżej przedstawiono przykładowe schemat adnotacjami, który udostępnia **klientów** tabeli **Northwind** bazy danych za pomocą relacji do **zamówienia** tabelę zawartą.  
  
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
  
 Poniższy przykład kodu używa silnie typizowaną **DataSet** utworzone na podstawie schematu próbki. Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania **klientów** tabeli, a drugi <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania **zamówienia** tabeli. Silnie typizowane **DataSet** definiuje **elementów DataRelation**.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
