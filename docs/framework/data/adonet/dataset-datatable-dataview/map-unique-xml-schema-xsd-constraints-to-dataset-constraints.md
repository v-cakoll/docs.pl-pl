---
title: Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150847"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="0cfd6-102">Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="0cfd6-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="0cfd6-103">W schemacie języka definicji schematu schematu schematu schematu XSD **unikatowy** element określa ograniczenie unikatowości elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="0cfd6-104">W procesie tłumaczenia schematu XML do schematu relacyjnego unikatowe ograniczenie określone dla elementu lub atrybutu w schemacie XML jest mapowane na unikatowe ograniczenie <xref:System.Data.DataTable> w odpowiednim, <xref:System.Data.DataSet> który jest generowany.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="0cfd6-105">W poniższej tabeli przedstawiono atrybuty **msdata,** które można określić w elemencie **unikatowym.**</span><span class="sxs-lookup"><span data-stu-id="0cfd6-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="0cfd6-106">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="0cfd6-106">Attribute name</span></span>|<span data-ttu-id="0cfd6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0cfd6-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0cfd6-108">**msdata:Nazwa więzów**</span><span class="sxs-lookup"><span data-stu-id="0cfd6-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="0cfd6-109">Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="0cfd6-110">W przeciwnym razie atrybut **name** zawiera wartość nazwy ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="0cfd6-111">**msdata:Klucz podstawowy**</span><span class="sxs-lookup"><span data-stu-id="0cfd6-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="0cfd6-112">Jeśli `PrimaryKey="true"` jest obecny w **unikatowy** element, unikatowe ograniczenie jest tworzony z **IsPrimaryKey** właściwość ustawiona na **true**.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="0cfd6-113">Poniższy przykład przedstawia schemat XML, który używa **unikatowego** elementu do określenia ograniczenia unikatowości.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="0cfd6-114">**Unikatowy** element w schemacie określa, że dla wszystkich **klientów** elementów w wystąpieniu dokumentu wartość CustomerID element **podrzędny** musi być unikatowy.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="0cfd6-115">Podczas tworzenia **zestawu danych**proces mapowania odczytuje ten schemat i generuje następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="0cfd6-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="0cfd6-116">Proces mapowania tworzy również unikatowe ograniczenie w kolumnie **CustomerID,** jak pokazano w poniższym **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="0cfd6-117">(Dla uproszczenia wyświetlane są tylko odpowiednie właściwości).</span><span class="sxs-lookup"><span data-stu-id="0cfd6-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
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
  
 <span data-ttu-id="0cfd6-118">W **dataset,** który jest generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unikatowego.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="0cfd6-119">**Unikatowa** właściwość w kolumnie wskazuje, że wartości kolumny **CustomerID** muszą być unikatowe (ale mogą być odwołaniem null, określonym przez **właściwość AllowDBNull** kolumny).</span><span class="sxs-lookup"><span data-stu-id="0cfd6-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="0cfd6-120">Jeśli zmodyfikujesz schemat i ustawisz opcjonalną wartość atrybutu **msdata:PrimaryKey** na **True**, w tabeli zostanie utworzone unikatowe ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="0cfd6-121">Właściwość kolumny **AllowDBNull** jest ustawiona na **False,** a właściwość **IsPrimaryKey** ograniczenia ustawiona na **True**, dzięki czemu **kolumna CustomerID** jest kolumną klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="0cfd6-122">Można określić unikatowe ograniczenie kombinacji elementów lub atrybutów w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="0cfd6-123">Poniższy przykład pokazuje, jak określić, że **kombinacja CustomerID** i **CompanyName** wartości musi być unikatowa dla wszystkich **klientów** w dowolnym wystąpieniu, dodając inny **xs:field** element w schemacie.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 <span data-ttu-id="0cfd6-124">Jest to ograniczenie utworzone w wynikowym **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="0cfd6-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cfd6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cfd6-125">See also</span></span>

- [<span data-ttu-id="0cfd6-126">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="0cfd6-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="0cfd6-127">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="0cfd6-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="0cfd6-128">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0cfd6-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
