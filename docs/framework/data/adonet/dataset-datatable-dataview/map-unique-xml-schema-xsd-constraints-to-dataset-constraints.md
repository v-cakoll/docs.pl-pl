---
title: Mapowanie ograniczeń unique schematu XML (XSD) elementu DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: c35dcadfb40fcb73104af7ee7456e64a68c9e023
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677078"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="63fb0-102">Mapowanie ograniczeń unique schematu XML (XSD) elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="63fb0-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="63fb0-103">W schemacie języka (XSD) definicji schematu XML **unikatowy** element określa ograniczenie unikatowości elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="63fb0-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="63fb0-104">W trakcie tłumaczenie schematu XML na schemat relacyjny, unikatowego ograniczenia określone w element lub atrybut w schemacie XML jest mapowany do unikatowego ograniczenia w <xref:System.Data.DataTable> w odpowiednich <xref:System.Data.DataSet> generowany.</span><span class="sxs-lookup"><span data-stu-id="63fb0-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="63fb0-105">W poniższej tabeli przedstawiono **msdata** atrybutów, które można określić w **unikatowy** elementu.</span><span class="sxs-lookup"><span data-stu-id="63fb0-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="63fb0-106">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="63fb0-106">Attribute name</span></span>|<span data-ttu-id="63fb0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="63fb0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="63fb0-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="63fb0-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="63fb0-109">Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="63fb0-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="63fb0-110">W przeciwnym razie **nazwa** atrybut zawiera wartość Nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="63fb0-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="63fb0-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="63fb0-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="63fb0-112">Jeśli `PrimaryKey="true"` znajduje się w **unikatowy** unikatowego ograniczenia elementu jest tworzony z **IsPrimaryKey** właściwością **true**.</span><span class="sxs-lookup"><span data-stu-id="63fb0-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="63fb0-113">W poniższym przykładzie przedstawiono schematu XML, który używa **unikatowy** elementu, aby określić ograniczenie unikatowości.</span><span class="sxs-lookup"><span data-stu-id="63fb0-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="63fb0-114">**Unikatowy** elementu w schemacie Określa, że dla wszystkich **klientów** elementów w dokumencie wystąpienia, wartość **CustomerID** element podrzędny musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="63fb0-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="63fb0-115">W budynku **DataSet**, proces mapowania odczytuje ten schemat i generuje poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="63fb0-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="63fb0-116">Proces mapowania wzrasta, powstaje unikatowego ograniczenia na **CustomerID** kolumny, jak pokazano w poniższym **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="63fb0-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="63fb0-117">(Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)</span><span class="sxs-lookup"><span data-stu-id="63fb0-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 <span data-ttu-id="63fb0-118">W **DataSet** , jest generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unique.</span><span class="sxs-lookup"><span data-stu-id="63fb0-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="63fb0-119">**Unikatowy** właściwość w kolumnie oznacza, że **CustomerID** wartości kolumn muszą być unikatowe (ale mogą być odwołanie o wartości null, określony przez **AllowDBNull** Właściwości kolumny).</span><span class="sxs-lookup"><span data-stu-id="63fb0-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="63fb0-120">Jeśli modyfikacji schematu opcjonalnego **msdata:PrimaryKey** wartość do atrybutu **True**, unikatowego ograniczenia jest tworzona w tabeli.</span><span class="sxs-lookup"><span data-stu-id="63fb0-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="63fb0-121">**AllowDBNull** ustawiono wartość właściwości column **False**i **IsPrimaryKey** właściwości ograniczenia równa **True**, a w związku z tym **CustomerID** kolumny to kolumna klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="63fb0-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="63fb0-122">Można określić ograniczenia unique na kombinacji elementów lub atrybutów w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="63fb0-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="63fb0-123">Poniższy przykład pokazuje, jak określić, że kombinacji **CustomerID** i **CompanyName** wartości muszą być unikatowe dla wszystkich **klientów** w żadnym wystąpieniu przez Dodawanie innego **xs:field** elementu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="63fb0-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="63fb0-124">Jest to ograniczenie, który jest tworzony w wynikowym **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="63fb0-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="63fb0-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63fb0-125">See also</span></span>
- [<span data-ttu-id="63fb0-126">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="63fb0-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="63fb0-127">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="63fb0-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="63fb0-128">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="63fb0-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
