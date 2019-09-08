---
title: Dodawanie adnotacji do typizowanych elementów DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 351175b96d354a264a9280018ce21de8870beda2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784804"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="a2616-102">Dodawanie adnotacji do typizowanych elementów DataSet</span><span class="sxs-lookup"><span data-stu-id="a2616-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="a2616-103">Adnotacje umożliwiają modyfikowanie nazw elementów w określonym typie <xref:System.Data.DataSet> bez modyfikowania bazowego schematu.</span><span class="sxs-lookup"><span data-stu-id="a2616-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="a2616-104">Modyfikacja nazw elementów w schemacie źródłowym spowoduje, że określony **zestaw danych** odwołuje się do obiektów, które nie istnieją w źródle danych, a także utraci odwołanie do obiektów, które istnieją w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a2616-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="a2616-105">Przy użyciu adnotacji można dostosować nazwy obiektów w określonym **zestawie danych** o bardziej zrozumiałych nazwach, zwiększyć czytelność kodu i ułatwić klientom korzystanie z tego **zestawu danych** , pozostawiając jednocześnie nienaruszony schemat.</span><span class="sxs-lookup"><span data-stu-id="a2616-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="a2616-106">Na przykład następujący element schematu dla tabeli **Customers** w bazie danych **Northwind** spowoduje powstanie <xref:System.Data.DataRowCollection> nazwy obiektu **DataRow** **CustomersRow** i nazwanych **klientów**.</span><span class="sxs-lookup"><span data-stu-id="a2616-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="a2616-107">Nazwa elementu **DataRowCollection** **klientów** ma znaczenie w kodzie klienta, ale nazwa elementu **DataRow** **CustomersRow** jest myląca, ponieważ jest to pojedynczy obiekt.</span><span class="sxs-lookup"><span data-stu-id="a2616-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="a2616-108">Ponadto w typowych scenariuszach obiekt zostałby odnosił się do bez identyfikatora **wiersza** i zamiast niego będzie po prostu określany jako obiekt **klienta** .</span><span class="sxs-lookup"><span data-stu-id="a2616-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="a2616-109">Rozwiązaniem jest dodawanie adnotacji do schematu i identyfikowanie nowych nazw obiektów **DataRow** i **DataRowCollection** .</span><span class="sxs-lookup"><span data-stu-id="a2616-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="a2616-110">Poniżej znajduje się adnotacja wersja poprzedniego schematu.</span><span class="sxs-lookup"><span data-stu-id="a2616-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="a2616-111">Określenie wartości **typu** nazwa **klienta** spowoduje powstanie nazwy obiektu **DataRow** dla **klienta**.</span><span class="sxs-lookup"><span data-stu-id="a2616-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="a2616-112">Określenie wartości **TypedPlural** **klientów** zachowuje nazwę elementu **DataRowCollection** **klientów**.</span><span class="sxs-lookup"><span data-stu-id="a2616-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="a2616-113">W poniższej tabeli przedstawiono adnotacje dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="a2616-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="a2616-114">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="a2616-114">Annotation</span></span>|<span data-ttu-id="a2616-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a2616-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="a2616-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="a2616-116">**typedName**</span></span>|<span data-ttu-id="a2616-117">Nazwa obiektu.</span><span class="sxs-lookup"><span data-stu-id="a2616-117">Name of the object.</span></span>|  
|<span data-ttu-id="a2616-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="a2616-118">**typedPlural**</span></span>|<span data-ttu-id="a2616-119">Nazwa kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2616-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="a2616-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="a2616-120">**typedParent**</span></span>|<span data-ttu-id="a2616-121">Nazwa obiektu, gdy jest on określony w relacji nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a2616-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="a2616-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="a2616-122">**typedChildren**</span></span>|<span data-ttu-id="a2616-123">Nazwa metody zwracającej obiekty z relacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a2616-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="a2616-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="a2616-124">**nullValue**</span></span>|<span data-ttu-id="a2616-125">Wartość, jeśli wartość podstawowa to **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="a2616-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="a2616-126">Zapoznaj się z poniższą tabelą dla adnotacji **NullValue** .</span><span class="sxs-lookup"><span data-stu-id="a2616-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="a2616-127">Wartość domyślna to **_throw**.</span><span class="sxs-lookup"><span data-stu-id="a2616-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="a2616-128">W poniższej tabeli przedstawiono wartości, które można określić dla adnotacji **NullValue** .</span><span class="sxs-lookup"><span data-stu-id="a2616-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="a2616-129">nullValue wartość</span><span class="sxs-lookup"><span data-stu-id="a2616-129">nullValue Value</span></span>|<span data-ttu-id="a2616-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a2616-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="a2616-131">*Wartość zastępcza*</span><span class="sxs-lookup"><span data-stu-id="a2616-131">*Replacement Value*</span></span>|<span data-ttu-id="a2616-132">Określ wartość, która ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="a2616-132">Specify a value to be returned.</span></span> <span data-ttu-id="a2616-133">Zwracana wartość musi być zgodna z typem elementu.</span><span class="sxs-lookup"><span data-stu-id="a2616-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="a2616-134">Na przykład użyj `nullValue="0"` , aby zwrócić 0 dla pól o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a2616-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="a2616-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="a2616-135">**_throw**</span></span>|<span data-ttu-id="a2616-136">Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a2616-136">Throw an exception.</span></span> <span data-ttu-id="a2616-137">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a2616-137">This is the default.</span></span>|  
|<span data-ttu-id="a2616-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="a2616-138">**_null**</span></span>|<span data-ttu-id="a2616-139">Zwraca odwołanie o wartości null lub Zgłoś wyjątek, jeśli napotkany jest typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="a2616-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="a2616-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="a2616-140">**_empty**</span></span>|<span data-ttu-id="a2616-141">W przypadku ciągów zwraca **ciąg. Empty**, w przeciwnym razie zwraca obiekt utworzony na podstawie pustego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a2616-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="a2616-142">Jeśli zostanie napotkany typ pierwotny, Zgłoś wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a2616-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="a2616-143">W poniższej tabeli przedstawiono wartości domyślne dla obiektów w określonym **zestawie danych** i dostępnych adnotacji.</span><span class="sxs-lookup"><span data-stu-id="a2616-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="a2616-144">Obiekt/Metoda/zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a2616-144">Object/Method/Event</span></span>|<span data-ttu-id="a2616-145">Domyślny</span><span class="sxs-lookup"><span data-stu-id="a2616-145">Default</span></span>|<span data-ttu-id="a2616-146">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="a2616-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="a2616-147">**Columns**</span><span class="sxs-lookup"><span data-stu-id="a2616-147">**DataTable**</span></span>|<span data-ttu-id="a2616-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="a2616-148">TableNameDataTable</span></span>|<span data-ttu-id="a2616-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="a2616-149">typedPlural</span></span>|  
|<span data-ttu-id="a2616-150">**Tabela DataTable** Form</span><span class="sxs-lookup"><span data-stu-id="a2616-150">**DataTable** Methods</span></span>|<span data-ttu-id="a2616-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="a2616-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="a2616-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="a2616-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="a2616-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="a2616-153">DeleteTableNameRow</span></span>|<span data-ttu-id="a2616-154">typedName</span><span class="sxs-lookup"><span data-stu-id="a2616-154">typedName</span></span>|  
|<span data-ttu-id="a2616-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="a2616-155">**DataRowCollection**</span></span>|<span data-ttu-id="a2616-156">TableName</span><span class="sxs-lookup"><span data-stu-id="a2616-156">TableName</span></span>|<span data-ttu-id="a2616-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="a2616-157">typedPlural</span></span>|  
|<span data-ttu-id="a2616-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="a2616-158">**DataRow**</span></span>|<span data-ttu-id="a2616-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="a2616-159">TableNameRow</span></span>|<span data-ttu-id="a2616-160">typedName</span><span class="sxs-lookup"><span data-stu-id="a2616-160">typedName</span></span>|  
|<span data-ttu-id="a2616-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="a2616-161">**DataColumn**</span></span>|<span data-ttu-id="a2616-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="a2616-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="a2616-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="a2616-163">DataRow.ColumnName</span></span>|<span data-ttu-id="a2616-164">typedName</span><span class="sxs-lookup"><span data-stu-id="a2616-164">typedName</span></span>|  
|<span data-ttu-id="a2616-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="a2616-165">**Property**</span></span>|<span data-ttu-id="a2616-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="a2616-166">PropertyName</span></span>|<span data-ttu-id="a2616-167">typedName</span><span class="sxs-lookup"><span data-stu-id="a2616-167">typedName</span></span>|  
|<span data-ttu-id="a2616-168">**Element podrzędny** Metoda</span><span class="sxs-lookup"><span data-stu-id="a2616-168">**Child** Accessor</span></span>|<span data-ttu-id="a2616-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="a2616-169">GetChildTableNameRows</span></span>|<span data-ttu-id="a2616-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="a2616-170">typedChildren</span></span>|  
|<span data-ttu-id="a2616-171">**Element nadrzędny** Metoda</span><span class="sxs-lookup"><span data-stu-id="a2616-171">**Parent** Accessor</span></span>|<span data-ttu-id="a2616-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="a2616-172">TableNameRow</span></span>|<span data-ttu-id="a2616-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="a2616-173">typedParent</span></span>|  
|<span data-ttu-id="a2616-174">**Zestaw danych** Wydarzeniach</span><span class="sxs-lookup"><span data-stu-id="a2616-174">**DataSet** Events</span></span>|<span data-ttu-id="a2616-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="a2616-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="a2616-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="a2616-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="a2616-177">typedName</span><span class="sxs-lookup"><span data-stu-id="a2616-177">typedName</span></span>|  
  
 <span data-ttu-id="a2616-178">Aby użyć wpisanych adnotacji **zestawu danych** , należy uwzględnić następujące odwołanie **xmlns** w schemacie języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="a2616-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="a2616-179">Aby utworzyć XSD z tabel baz danych, zobacz <xref:System.Data.DataSet.WriteXmlSchema%2A> lub [Working with datasetss in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a2616-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="a2616-180">Poniżej znajduje się przykładowy schemat z adnotacjami, który uwidacznia tabelę **Customers** bazy danych **Northwind** z relacją do uwzględnionej tabeli **Orders** .</span><span class="sxs-lookup"><span data-stu-id="a2616-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="a2616-181">Poniższy przykład kodu używa jednoznacznie określonego **zestawu danych** utworzonego na podstawie przykładowego schematu.</span><span class="sxs-lookup"><span data-stu-id="a2616-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="a2616-182">Używa one <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania tabeli **Customers** , a <xref:System.Data.SqlClient.SqlDataAdapter> druga do wypełniania tabeli **Orders** .</span><span class="sxs-lookup"><span data-stu-id="a2616-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="a2616-183">**Zestaw danych** o jednoznacznie określonym typie definiuje **relacje DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="a2616-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2616-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2616-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="a2616-185">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="a2616-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="a2616-186">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="a2616-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a2616-187">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2616-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
