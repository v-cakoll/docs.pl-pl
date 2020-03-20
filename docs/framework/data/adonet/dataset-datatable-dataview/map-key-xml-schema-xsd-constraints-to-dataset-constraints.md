---
title: Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150938"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="aa3c7-102">Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="aa3c7-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="aa3c7-103">W schemacie można określić ograniczenie klucza dla elementu lub atrybutu przy użyciu elementu **klucza.**</span><span class="sxs-lookup"><span data-stu-id="aa3c7-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="aa3c7-104">Element lub atrybut, na którym określono ograniczenie klucza musi mieć unikatowe wartości w każdym wystąpieniu schematu i nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="aa3c7-105">Ograniczenie klucza jest podobne do ograniczenia unikatowego, z tą różnicą, że kolumna, w której zdefiniowano ograniczenie klucza, nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="aa3c7-106">W poniższej tabeli przedstawiono atrybuty **msdata,** które można określić w **elemencie klucza.**</span><span class="sxs-lookup"><span data-stu-id="aa3c7-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="aa3c7-107">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="aa3c7-107">Attribute name</span></span>|<span data-ttu-id="aa3c7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="aa3c7-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="aa3c7-109">**msdata:Nazwa więzów**</span><span class="sxs-lookup"><span data-stu-id="aa3c7-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="aa3c7-110">Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="aa3c7-111">W przeciwnym razie atrybut **name** zawiera wartość nazwy ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="aa3c7-112">**msdata:Klucz podstawowy**</span><span class="sxs-lookup"><span data-stu-id="aa3c7-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="aa3c7-113">Jeśli `PrimaryKey="true"` jest obecny, **IsPrimaryKey** constraint właściwość jest ustawiona na **true,** co czyni go kluczem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="aa3c7-114">Właściwość kolumny **AllowDBNull** jest ustawiona na **false,** ponieważ klucze podstawowe nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="aa3c7-115">Podczas konwertowania schematu, w którym określono ograniczenie klucza, proces mapowania tworzy unikatowe ograniczenie w tabeli z właściwość **Kolumny AllowDBNull** **ustawiona** na false dla każdej kolumny w ograniczeniu.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="aa3c7-116">**Właściwość IsPrimaryKey** unikatowego ograniczenia jest również ustawiona `msdata:PrimaryKey="true"` na **false,** chyba że określono w elemencie **klucza.**</span><span class="sxs-lookup"><span data-stu-id="aa3c7-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="aa3c7-117">Jest to identyczne z unikatowym ograniczeniem w schemacie, w którym `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="aa3c7-118">W poniższym przykładzie schematu **element klucza** określa ograniczenie klucza na **CustomerID** elementu.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="aa3c7-119">Element **klucza** określa, że wartości **customerID** element podrzędny **CustomerID** elementu Customers element musi mieć unikatowe wartości i nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="aa3c7-120">Podczas tłumaczenia schematu języka XSD (XSD) schemat definicji schematu schematu schematu schematu xsd proces mapowania tworzy następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="aa3c7-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="aa3c7-121">Mapowanie schematu XML tworzy również **uniqueconstraint** w kolumnie **CustomerID,** jak pokazano w poniższej . <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="aa3c7-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="aa3c7-122">(Dla uproszczenia wyświetlane są tylko odpowiednie właściwości).</span><span class="sxs-lookup"><span data-stu-id="aa3c7-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="aa3c7-123">W **DataSet,** który jest generowany, **IsPrimaryKey** właściwość **UniqueConstraint** jest ustawiona `msdata:PrimaryKey="true"` na **true,** ponieważ schemat określa w **kluczowym** elemencie.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="aa3c7-124">Wartość właściwości **Nazwana ograniczeń** **uniqueconstraint** w **zestawie danych** jest wartością atrybutu **msdata:ConstraintName** określoną w **kluczowym** elemencie w schemacie.</span><span class="sxs-lookup"><span data-stu-id="aa3c7-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3c7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa3c7-125">See also</span></span>

- [<span data-ttu-id="aa3c7-126">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="aa3c7-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="aa3c7-127">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="aa3c7-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="aa3c7-128">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa3c7-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
