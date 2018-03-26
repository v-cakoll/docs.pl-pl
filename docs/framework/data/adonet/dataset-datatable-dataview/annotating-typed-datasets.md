---
title: Dodawanie adnotacji do Typizowane zbiory danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: cc09f3f9b43b70b7f9b302d7a9d75428b5a0e6c7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="7ff62-102">Dodawanie adnotacji do Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="7ff62-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="7ff62-103">Adnotacje umożliwiają modyfikowanie nazwy elementów w wpisaną <xref:System.Data.DataSet> bez modyfikowania schematu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7ff62-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="7ff62-104">Modyfikowanie nazwy elementów w źródłowej schemat spowodowałoby wpisanego **DataSet** do odwoływania się do obiektów, które nie istnieje w źródle danych, jak również utracić odwołania do obiektów, które istnieją w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="7ff62-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="7ff62-105">Korzystanie z adnotacji, można dostosować nazwy obiektów w wpisaną **DataSet** z bardziej zrozumiałej nazwy, dzięki czemu czytelność kodu i wpisaną **zestawu danych** ułatwia klientom na użycie, pozostawiając Podstawowy schemat bez zmian.</span><span class="sxs-lookup"><span data-stu-id="7ff62-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="7ff62-106">Na przykład następujący element schematu dla **klientów** spis **Northwind** bazy danych spowoduje powstanie **DataRow** nazwę obiektu  **CustomersRow** i <xref:System.Data.DataRowCollection> o nazwie **klientów**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="7ff62-107">A **kolekcji DataRowCollection** nazwa **klientów** znaczenie w kodu klienta, ale **DataRow** nazwa **CustomersRow** jest błąd ponieważ jest to pojedynczy obiekt.</span><span class="sxs-lookup"><span data-stu-id="7ff62-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="7ff62-108">Wspólnych scenariuszy, obiekt może być również określany bez **wiersza** identyfikator i zamiast tego będzie można po prostu nazywany **klienta** obiektu.</span><span class="sxs-lookup"><span data-stu-id="7ff62-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="7ff62-109">Rozwiązanie to adnotacji schematu i identyfikować nowe nazwy **DataRow** i **kolekcji DataRowCollection** obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ff62-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="7ff62-110">Poniżej znajduje się adnotacjami wersja poprzedniego schematu.</span><span class="sxs-lookup"><span data-stu-id="7ff62-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="7ff62-111">Określanie **nazwy wpisanej** wartość **klienta** spowoduje **DataRow** nazwę obiektu **klienta**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="7ff62-112">Określanie **typedPlural** wartość **klientów** zachowuje **kolekcji DataRowCollection** nazwa **klientów**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="7ff62-113">W poniższej tabeli przedstawiono dostępne do użycia adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7ff62-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="7ff62-114">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="7ff62-114">Annotation</span></span>|<span data-ttu-id="7ff62-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7ff62-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="7ff62-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="7ff62-116">**typedName**</span></span>|<span data-ttu-id="7ff62-117">Nazwa obiektu.</span><span class="sxs-lookup"><span data-stu-id="7ff62-117">Name of the object.</span></span>|  
|<span data-ttu-id="7ff62-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="7ff62-118">**typedPlural**</span></span>|<span data-ttu-id="7ff62-119">Nazwa kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="7ff62-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="7ff62-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="7ff62-120">**typedParent**</span></span>|<span data-ttu-id="7ff62-121">Nazwa obiektu określonego w relacji nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="7ff62-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="7ff62-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="7ff62-122">**typedChildren**</span></span>|<span data-ttu-id="7ff62-123">Nazwa metody zwracać obiekty z relacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7ff62-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="7ff62-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="7ff62-124">**nullValue**</span></span>|<span data-ttu-id="7ff62-125">Wartość, gdy jest odpowiednia wartość **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="7ff62-126">Zobacz poniższą tabelę dla **nullValue** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7ff62-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="7ff62-127">Wartość domyślna to **_throw**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="7ff62-128">W poniższej tabeli przedstawiono wartości, które można określić dla **nullValue** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7ff62-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="7ff62-129">nullValue wartość</span><span class="sxs-lookup"><span data-stu-id="7ff62-129">nullValue Value</span></span>|<span data-ttu-id="7ff62-130">Opis</span><span class="sxs-lookup"><span data-stu-id="7ff62-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="7ff62-131">*Wartość zastępczą*</span><span class="sxs-lookup"><span data-stu-id="7ff62-131">*Replacement Value*</span></span>|<span data-ttu-id="7ff62-132">Określ wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="7ff62-132">Specify a value to be returned.</span></span> <span data-ttu-id="7ff62-133">Zwracana wartość musi odpowiadać typowi elementu.</span><span class="sxs-lookup"><span data-stu-id="7ff62-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="7ff62-134">Na przykład użyć `nullValue="0"` do zwraca wartość 0 dla pól całkowitych wartości null.</span><span class="sxs-lookup"><span data-stu-id="7ff62-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="7ff62-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="7ff62-135">**_throw**</span></span>|<span data-ttu-id="7ff62-136">Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7ff62-136">Throw an exception.</span></span> <span data-ttu-id="7ff62-137">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="7ff62-137">This is the default.</span></span>|  
|<span data-ttu-id="7ff62-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="7ff62-138">**_null**</span></span>|<span data-ttu-id="7ff62-139">Zwraca odwołanie o wartości null lub zgłosić wyjątek, jeśli typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="7ff62-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="7ff62-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="7ff62-140">**_empty**</span></span>|<span data-ttu-id="7ff62-141">Ciągi, zwróć **String.Empty**, w przeciwnym razie zwraca obiekt, który został utworzony na podstawie pustego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7ff62-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="7ff62-142">Jeśli typ pierwotny, Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7ff62-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="7ff62-143">W poniższej tabeli przedstawiono wartości domyślne dla obiektów w typizowanych **DataSet** i dostępne adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7ff62-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="7ff62-144">Metody obiektu lub zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7ff62-144">Object/Method/Event</span></span>|<span data-ttu-id="7ff62-145">Domyślny</span><span class="sxs-lookup"><span data-stu-id="7ff62-145">Default</span></span>|<span data-ttu-id="7ff62-146">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="7ff62-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="7ff62-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="7ff62-147">**DataTable**</span></span>|<span data-ttu-id="7ff62-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="7ff62-148">TableNameDataTable</span></span>|<span data-ttu-id="7ff62-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="7ff62-149">typedPlural</span></span>|  
|<span data-ttu-id="7ff62-150">**Element DataTable** metody</span><span class="sxs-lookup"><span data-stu-id="7ff62-150">**DataTable** Methods</span></span>|<span data-ttu-id="7ff62-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="7ff62-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="7ff62-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="7ff62-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="7ff62-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="7ff62-153">DeleteTableNameRow</span></span>|<span data-ttu-id="7ff62-154">typedName</span><span class="sxs-lookup"><span data-stu-id="7ff62-154">typedName</span></span>|  
|<span data-ttu-id="7ff62-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="7ff62-155">**DataRowCollection**</span></span>|<span data-ttu-id="7ff62-156">TableName</span><span class="sxs-lookup"><span data-stu-id="7ff62-156">TableName</span></span>|<span data-ttu-id="7ff62-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="7ff62-157">typedPlural</span></span>|  
|<span data-ttu-id="7ff62-158">**Element DataRow**</span><span class="sxs-lookup"><span data-stu-id="7ff62-158">**DataRow**</span></span>|<span data-ttu-id="7ff62-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="7ff62-159">TableNameRow</span></span>|<span data-ttu-id="7ff62-160">typedName</span><span class="sxs-lookup"><span data-stu-id="7ff62-160">typedName</span></span>|  
|<span data-ttu-id="7ff62-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="7ff62-161">**DataColumn**</span></span>|<span data-ttu-id="7ff62-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="7ff62-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="7ff62-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="7ff62-163">DataRow.ColumnName</span></span>|<span data-ttu-id="7ff62-164">typedName</span><span class="sxs-lookup"><span data-stu-id="7ff62-164">typedName</span></span>|  
|<span data-ttu-id="7ff62-165">**Właściwość**</span><span class="sxs-lookup"><span data-stu-id="7ff62-165">**Property**</span></span>|<span data-ttu-id="7ff62-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="7ff62-166">PropertyName</span></span>|<span data-ttu-id="7ff62-167">typedName</span><span class="sxs-lookup"><span data-stu-id="7ff62-167">typedName</span></span>|  
|<span data-ttu-id="7ff62-168">**Podrzędne** metody dostępu</span><span class="sxs-lookup"><span data-stu-id="7ff62-168">**Child** Accessor</span></span>|<span data-ttu-id="7ff62-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="7ff62-169">GetChildTableNameRows</span></span>|<span data-ttu-id="7ff62-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="7ff62-170">typedChildren</span></span>|  
|<span data-ttu-id="7ff62-171">**Nadrzędny** metody dostępu</span><span class="sxs-lookup"><span data-stu-id="7ff62-171">**Parent** Accessor</span></span>|<span data-ttu-id="7ff62-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="7ff62-172">TableNameRow</span></span>|<span data-ttu-id="7ff62-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="7ff62-173">typedParent</span></span>|  
|<span data-ttu-id="7ff62-174">**Zestaw danych** zdarzeń</span><span class="sxs-lookup"><span data-stu-id="7ff62-174">**DataSet** Events</span></span>|<span data-ttu-id="7ff62-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="7ff62-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="7ff62-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="7ff62-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="7ff62-177">typedName</span><span class="sxs-lookup"><span data-stu-id="7ff62-177">typedName</span></span>|  
  
 <span data-ttu-id="7ff62-178">Aby użyć wpisane **zestawu danych** adnotacje, należy uwzględnić następujące **xmlns** odwołania w schemat schematu XML definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="7ff62-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="7ff62-179">(Aby utworzyć xsd z tabel bazy danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Praca z zestawami danych w programie Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span><span class="sxs-lookup"><span data-stu-id="7ff62-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="7ff62-180">Poniżej przedstawiono przykładowe schematu adnotacjami, udostępniający **klientów** spis **Northwind** bazy danych z relacji do **zamówień** tabeli uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="7ff62-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="7ff62-181">Poniższy przykład kodu wykorzystuje silnie typizowaną **DataSet** utworzone na podstawie schematu próbki.</span><span class="sxs-lookup"><span data-stu-id="7ff62-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="7ff62-182">Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia **klientów** tabelami <xref:System.Data.SqlClient.SqlDataAdapter> do wypełnienia **zamówień** tabeli.</span><span class="sxs-lookup"><span data-stu-id="7ff62-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="7ff62-183">Silnie typizowaną **DataSet** definiuje **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="7ff62-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ff62-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ff62-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="7ff62-185">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="7ff62-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="7ff62-186">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7ff62-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="7ff62-187">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="7ff62-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
