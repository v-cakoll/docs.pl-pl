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
# <a name="annotating-typed-datasets"></a><span data-ttu-id="7059f-102">Dodawanie adnotacji do typizowanych elementów DataSet</span><span class="sxs-lookup"><span data-stu-id="7059f-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="7059f-103">Adnotacje umożliwiają modyfikowanie nazw elementów wpisywanych <xref:System.Data.DataSet> bez modyfikowania schematu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7059f-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="7059f-104">Modyfikowanie nazw elementów w podstawowym schemacie spowodowałoby wpisane **DataSet** odwoływać się do obiektów, które nie istnieją w źródle danych, a także utracić odwołanie do obiektów, które istnieją w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="7059f-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="7059f-105">Za pomocą adnotacji można dostosować nazwy obiektów w typie **DataSet** z bardziej znaczących nazw, dzięki czemu kod bardziej czytelny i wpisane **DataSet** łatwiejsze dla klientów, pozostawiając podstawowy schemat nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="7059f-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="7059f-106">Na przykład następujący element schematu dla tabeli **Klienci** bazy danych **Northwind** spowoduje nazwę obiektu <xref:System.Data.DataRowCollection> **DataRow** **customersrow** i **nazwanych klientów**.</span><span class="sxs-lookup"><span data-stu-id="7059f-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="7059f-107">A **DataRowCollection** nazwa **klientów** ma znaczenie w kodzie klienta, ale **DataRow** nazwa **CustomersRow** jest mylące, ponieważ jest pojedynczy obiekt.</span><span class="sxs-lookup"><span data-stu-id="7059f-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="7059f-108">Ponadto w typowych scenariuszach obiekt będzie się odwoływać bez **identyfikatora wiersza** i zamiast tego będzie po prostu określany jako **Customer** obiektu.</span><span class="sxs-lookup"><span data-stu-id="7059f-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="7059f-109">Rozwiązaniem jest dodawanie adnotacji do schematu i identyfikowanie nowych nazw obiektów **DataRow** i **DataRowCollection.**</span><span class="sxs-lookup"><span data-stu-id="7059f-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="7059f-110">Poniżej znajduje się wersja z adnotacjami poprzedniego schematu.</span><span class="sxs-lookup"><span data-stu-id="7059f-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="7059f-111">Określenie **wpisanej wartościName** **klienta** spowoduje nazwę obiektu **DataRow** **klienta**.</span><span class="sxs-lookup"><span data-stu-id="7059f-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="7059f-112">Określenie **wpisanej** Wartość wartość wartość **klienta** jest zachowywana przez **datarową** nazwę **klientów.**</span><span class="sxs-lookup"><span data-stu-id="7059f-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="7059f-113">W poniższej tabeli przedstawiono adnotacje dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="7059f-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="7059f-114">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="7059f-114">Annotation</span></span>|<span data-ttu-id="7059f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7059f-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="7059f-116">**wpisaneName**</span><span class="sxs-lookup"><span data-stu-id="7059f-116">**typedName**</span></span>|<span data-ttu-id="7059f-117">Nazwa obiektu.</span><span class="sxs-lookup"><span data-stu-id="7059f-117">Name of the object.</span></span>|  
|<span data-ttu-id="7059f-118">**typwzrówno-foniczny**</span><span class="sxs-lookup"><span data-stu-id="7059f-118">**typedPlural**</span></span>|<span data-ttu-id="7059f-119">Nazwa kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="7059f-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="7059f-120">**wpisaneParent**</span><span class="sxs-lookup"><span data-stu-id="7059f-120">**typedParent**</span></span>|<span data-ttu-id="7059f-121">Nazwa obiektu, o którym mowa w relacji nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="7059f-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="7059f-122">**typedDzieci**</span><span class="sxs-lookup"><span data-stu-id="7059f-122">**typedChildren**</span></span>|<span data-ttu-id="7059f-123">Nazwa metody zwracania obiektów z relacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="7059f-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="7059f-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="7059f-124">**nullValue**</span></span>|<span data-ttu-id="7059f-125">Wartość, jeśli wartością bazową jest **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="7059f-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="7059f-126">Zobacz poniższą tabelę adnotacji **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="7059f-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="7059f-127">Wartość domyślna to **_throw**.</span><span class="sxs-lookup"><span data-stu-id="7059f-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="7059f-128">W poniższej tabeli przedstawiono wartości, które można określić dla adnotacji **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="7059f-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="7059f-129">Wartość nullValue</span><span class="sxs-lookup"><span data-stu-id="7059f-129">nullValue Value</span></span>|<span data-ttu-id="7059f-130">Opis</span><span class="sxs-lookup"><span data-stu-id="7059f-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="7059f-131">*Wartość zamienna*</span><span class="sxs-lookup"><span data-stu-id="7059f-131">*Replacement Value*</span></span>|<span data-ttu-id="7059f-132">Określ wartość, która ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="7059f-132">Specify a value to be returned.</span></span> <span data-ttu-id="7059f-133">Zwracana wartość musi być zgodna z typem elementu.</span><span class="sxs-lookup"><span data-stu-id="7059f-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="7059f-134">Na przykład `nullValue="0"` użyj do zwrócenia 0 dla pól całkowitej null.</span><span class="sxs-lookup"><span data-stu-id="7059f-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="7059f-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="7059f-135">**_throw**</span></span>|<span data-ttu-id="7059f-136">Zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7059f-136">Throw an exception.</span></span> <span data-ttu-id="7059f-137">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="7059f-137">This is the default.</span></span>|  
|<span data-ttu-id="7059f-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="7059f-138">**_null**</span></span>|<span data-ttu-id="7059f-139">Zwraca odwołanie null lub zgłoć wyjątek, jeśli zostanie napotkany typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="7059f-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="7059f-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="7059f-140">**_empty**</span></span>|<span data-ttu-id="7059f-141">W przypadku ciągów zwraca **ciąg.Pusty**, w przeciwnym razie zwraca obiekt utworzony z pustego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7059f-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="7059f-142">Jeśli napotkany jest typ pierwotny, zgłoć wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7059f-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="7059f-143">W poniższej tabeli przedstawiono wartości domyślne dla obiektów w wpisanym **zestawie danych** i dostępne adnotacje.</span><span class="sxs-lookup"><span data-stu-id="7059f-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="7059f-144">Obiekt/metoda/zdarzenie</span><span class="sxs-lookup"><span data-stu-id="7059f-144">Object/Method/Event</span></span>|<span data-ttu-id="7059f-145">Domyślne</span><span class="sxs-lookup"><span data-stu-id="7059f-145">Default</span></span>|<span data-ttu-id="7059f-146">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="7059f-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="7059f-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="7059f-147">**DataTable**</span></span>|<span data-ttu-id="7059f-148">Tabela TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="7059f-148">TableNameDataTable</span></span>|<span data-ttu-id="7059f-149">typwzrówno-foniczny</span><span class="sxs-lookup"><span data-stu-id="7059f-149">typedPlural</span></span>|  
|<span data-ttu-id="7059f-150">**DataTable (DataTable)** Metody</span><span class="sxs-lookup"><span data-stu-id="7059f-150">**DataTable** Methods</span></span>|<span data-ttu-id="7059f-151">Nowy Nazwamowa</span><span class="sxs-lookup"><span data-stu-id="7059f-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="7059f-152">Dodaj pozycjęNamerow</span><span class="sxs-lookup"><span data-stu-id="7059f-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="7059f-153">Usuń pozycjęNamerow</span><span class="sxs-lookup"><span data-stu-id="7059f-153">DeleteTableNameRow</span></span>|<span data-ttu-id="7059f-154">wpisaneName</span><span class="sxs-lookup"><span data-stu-id="7059f-154">typedName</span></span>|  
|<span data-ttu-id="7059f-155">**Datarowcollection**</span><span class="sxs-lookup"><span data-stu-id="7059f-155">**DataRowCollection**</span></span>|<span data-ttu-id="7059f-156">TableName</span><span class="sxs-lookup"><span data-stu-id="7059f-156">TableName</span></span>|<span data-ttu-id="7059f-157">typwzrówno-foniczny</span><span class="sxs-lookup"><span data-stu-id="7059f-157">typedPlural</span></span>|  
|<span data-ttu-id="7059f-158">**Datarow**</span><span class="sxs-lookup"><span data-stu-id="7059f-158">**DataRow**</span></span>|<span data-ttu-id="7059f-159">Nazwa tabeli</span><span class="sxs-lookup"><span data-stu-id="7059f-159">TableNameRow</span></span>|<span data-ttu-id="7059f-160">wpisaneName</span><span class="sxs-lookup"><span data-stu-id="7059f-160">typedName</span></span>|  
|<span data-ttu-id="7059f-161">**Datacolumn**</span><span class="sxs-lookup"><span data-stu-id="7059f-161">**DataColumn**</span></span>|<span data-ttu-id="7059f-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="7059f-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="7059f-163">DataRow.ColumnName (Nazwa.kolumna datarowa)</span><span class="sxs-lookup"><span data-stu-id="7059f-163">DataRow.ColumnName</span></span>|<span data-ttu-id="7059f-164">wpisaneName</span><span class="sxs-lookup"><span data-stu-id="7059f-164">typedName</span></span>|  
|<span data-ttu-id="7059f-165">**Właściwość**</span><span class="sxs-lookup"><span data-stu-id="7059f-165">**Property**</span></span>|<span data-ttu-id="7059f-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="7059f-166">PropertyName</span></span>|<span data-ttu-id="7059f-167">wpisaneName</span><span class="sxs-lookup"><span data-stu-id="7059f-167">typedName</span></span>|  
|<span data-ttu-id="7059f-168">**Dziecko** Akcesor</span><span class="sxs-lookup"><span data-stu-id="7059f-168">**Child** Accessor</span></span>|<span data-ttu-id="7059f-169">GetChildTableNameRows (Wychocie Na łańszeń)</span><span class="sxs-lookup"><span data-stu-id="7059f-169">GetChildTableNameRows</span></span>|<span data-ttu-id="7059f-170">typedDzieci</span><span class="sxs-lookup"><span data-stu-id="7059f-170">typedChildren</span></span>|  
|<span data-ttu-id="7059f-171">**Rodzic** Akcesor</span><span class="sxs-lookup"><span data-stu-id="7059f-171">**Parent** Accessor</span></span>|<span data-ttu-id="7059f-172">Nazwa tabeli</span><span class="sxs-lookup"><span data-stu-id="7059f-172">TableNameRow</span></span>|<span data-ttu-id="7059f-173">wpisaneParent</span><span class="sxs-lookup"><span data-stu-id="7059f-173">typedParent</span></span>|  
|<span data-ttu-id="7059f-174">**Zestaw danych** Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7059f-174">**DataSet** Events</span></span>|<span data-ttu-id="7059f-175">Nazwamiorowasvent</span><span class="sxs-lookup"><span data-stu-id="7059f-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="7059f-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="7059f-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="7059f-177">wpisaneName</span><span class="sxs-lookup"><span data-stu-id="7059f-177">typedName</span></span>|  
  
 <span data-ttu-id="7059f-178">Aby używać wpisanych adnotacji **DataSet,** należy dołączyć następujące odwołanie xmlns do schematu języka XM (XSD) w języku xml schemacie definicji schematu schematu schematu schematu schematu schematu.To use typed DataSet adnotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span><span class="sxs-lookup"><span data-stu-id="7059f-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="7059f-179">Aby utworzyć xsd z tabel <xref:System.Data.DataSet.WriteXmlSchema%2A> bazy danych, zobacz lub [Praca z zestawami danych w programie Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7059f-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="7059f-180">Poniżej przedstawiono przykładowy schemat z adnotacjami, który udostępnia tabelę **Klienci** bazy danych **Northwind** z relacją z tabelą **Zamówienia.**</span><span class="sxs-lookup"><span data-stu-id="7059f-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="7059f-181">Poniższy przykład kodu używa silnie **typizowanego zestawu danych** utworzonego na podstawie przykładowego schematu.</span><span class="sxs-lookup"><span data-stu-id="7059f-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="7059f-182">Używa jednego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania **tabeli Klienci,** a drugiego <xref:System.Data.SqlClient.SqlDataAdapter> do wypełniania tabeli **Zamówienia.**</span><span class="sxs-lookup"><span data-stu-id="7059f-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="7059f-183">Silnie typiwany **zestaw danych** definiuje **datarelations**.</span><span class="sxs-lookup"><span data-stu-id="7059f-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7059f-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7059f-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="7059f-185">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="7059f-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="7059f-186">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7059f-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="7059f-187">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7059f-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
