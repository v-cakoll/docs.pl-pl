---
title: Dodawanie adnotacji do typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: df6da84dfc120e3f6c3cb0e46729ca2cecc9fe3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040396"
---
# <a name="annotating-typed-datasets"></a>Dodawanie adnotacji do typizowanych elementów DataSet
Adnotacje umożliwiają modyfikowanie nazw elementów w wpisanych <xref:System.Data.DataSet> bez modyfikowania bazowego schematu. Modyfikacja nazw elementów w schemacie źródłowym spowoduje, że określony **zestaw danych** odwołuje się do obiektów, które nie istnieją w źródle danych, a także utraci odwołanie do obiektów, które istnieją w źródle danych.  
  
 Przy użyciu adnotacji można dostosować nazwy obiektów w określonym **zestawie danych** o bardziej zrozumiałych nazwach, zwiększyć czytelność kodu i ułatwić klientom korzystanie z tego **zestawu danych** , pozostawiając jednocześnie nienaruszony schemat. Na przykład następujący element schematu dla tabeli **Customers** w bazie danych **Northwind** spowoduje, że nazwa obiektu **DataRow** **CustomersRow** i <xref:System.Data.DataRowCollection> nazwanych **klientów**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Nazwa elementu **DataRowCollection** **klientów** ma znaczenie w kodzie klienta, ale nazwa elementu **DataRow** **CustomersRow** jest myląca, ponieważ jest to pojedynczy obiekt. Ponadto w typowych scenariuszach obiekt zostałby odnosił się do bez identyfikatora **wiersza** i zamiast niego będzie po prostu określany jako obiekt **klienta** . Rozwiązaniem jest dodawanie adnotacji do schematu i identyfikowanie nowych nazw obiektów **DataRow** i **DataRowCollection** . Poniżej znajduje się adnotacja wersja poprzedniego schematu.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Określenie wartości **typu** nazwa **klienta** spowoduje powstanie nazwy obiektu **DataRow** dla **klienta**. Określenie wartości **TypedPlural** **klientów** zachowuje nazwę elementu **DataRowCollection** **klientów**.  
  
 W poniższej tabeli przedstawiono adnotacje dostępne do użycia.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**typname**|Nazwa obiektu.|  
|**typedPlural**|Nazwa kolekcji obiektów.|  
|**typedParent**|Nazwa obiektu, gdy jest on określony w relacji nadrzędnej.|  
|**typedChildren**|Nazwa metody zwracającej obiekty z relacji podrzędnej.|  
|**nullValue**|Wartość, jeśli wartość podstawowa to **DBNull**. Zapoznaj się z poniższą tabelą dla adnotacji **NullValue** . Wartość domyślna to **_throw**.|  
  
 W poniższej tabeli przedstawiono wartości, które można określić dla adnotacji **NullValue** .  
  
|nullValue wartość|Opis|  
|---------------------|-----------------|  
|*Wartość zastępcza*|Określ wartość, która ma zostać zwrócona. Zwracana wartość musi być zgodna z typem elementu. Na przykład użyj `nullValue="0"`, aby zwrócić 0 dla pól o wartości null.|  
|**_throw**|Zgłoś wyjątek. Domyślnie włączone.|  
|**_null**|Zwraca odwołanie o wartości null lub Zgłoś wyjątek, jeśli napotkany jest typ pierwotny.|  
|**_empty**|W przypadku ciągów zwraca **ciąg. Empty**, w przeciwnym razie zwraca obiekt utworzony na podstawie pustego konstruktora. Jeśli zostanie napotkany typ pierwotny, Zgłoś wyjątek.|  
  
 W poniższej tabeli przedstawiono wartości domyślne dla obiektów w określonym **zestawie danych** i dostępnych adnotacji.  
  
|Obiekt/Metoda/zdarzenie|Domyślny|Adnotacja|  
|---------------------------|-------------|----------------|  
|**Columns**|TableNameDataTable|typedPlural|  
|**Tabela DataTable** Form|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typname|  
|**Obiekt DataRowcollection**|tableName|typedPlural|  
|**DataRow**|TableNameRow|typname|  
|**DataColumn**|DataTable. ColumnNameColumn<br /><br /> DataRow. ColumnName|typname|  
|**Wartość**|Funkcja|typname|  
|**Element podrzędny** Metoda|GetChildTableNameRows|typedChildren|  
|**Element nadrzędny** Metoda|TableNameRow|typedParent|  
|**Zestaw danych** Wydarzeniach|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typname|  
  
 Aby użyć wpisanych adnotacji **zestawu danych** , należy uwzględnić następujące odwołanie **xmlns** w schemacie języka definicji schematu XML (XSD). Aby utworzyć XSD z tabeli bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Working with datasetss in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Poniżej znajduje się przykładowy schemat z adnotacjami, który uwidacznia tabelę **Customers** bazy danych **Northwind** z relacją do uwzględnionej tabeli **Orders** .  
  
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
  
 Poniższy przykład kodu używa jednoznacznie określonego **zestawu danych** utworzonego na podstawie przykładowego schematu. Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter>, aby wypełnić tabelę **Customers** i inne <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia tabeli **Orders** . **Zestaw danych** o jednoznacznie określonym typie definiuje **relacje DataRelations**.  
  
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
- [Typizowane elementy DataSet](typed-datasets.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
