---
title: Ograniczenia unikalne schematu XML (XSD) mapy do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3700e4010176abed05677043469476fe34cd564c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="61b6b-102">Ograniczenia unikalne schematu XML (XSD) mapy do ograniczenia zestawu danych</span><span class="sxs-lookup"><span data-stu-id="61b6b-102">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="61b6b-103">W schemacie schematu XML definition language (XSD) **unikatowy** element określa ograniczenie unikatowości element lub atrybut.</span><span class="sxs-lookup"><span data-stu-id="61b6b-103">In an XML Schema definition language (XSD) schema, the **unique** element specifies the uniqueness constraint on an element or attribute.</span></span> <span data-ttu-id="61b6b-104">Właśnie tłumaczenie schematu XML na schemat relacyjny, unikatowego ograniczenia określone na element lub atrybut w schemacie XML jest zamapowana do ograniczenia unique w <xref:System.Data.DataTable> w odpowiednich <xref:System.Data.DataSet> generowany.</span><span class="sxs-lookup"><span data-stu-id="61b6b-104">In the process of translating an XML Schema into a relational schema, the unique constraint specified on an element or attribute in the XML Schema is mapped to a unique constraint in the <xref:System.Data.DataTable> in the corresponding <xref:System.Data.DataSet> that is generated.</span></span>  
  
 <span data-ttu-id="61b6b-105">W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **unikatowy** elementu.</span><span class="sxs-lookup"><span data-stu-id="61b6b-105">The following table outlines the **msdata** attributes that you can specify in the **unique** element.</span></span>  
  
|<span data-ttu-id="61b6b-106">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="61b6b-106">Attribute name</span></span>|<span data-ttu-id="61b6b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="61b6b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="61b6b-108">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="61b6b-108">**msdata:ConstraintName**</span></span>|<span data-ttu-id="61b6b-109">Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="61b6b-109">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="61b6b-110">W przeciwnym razie **nazwa** atrybutu zawiera wartości nazwy ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="61b6b-110">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="61b6b-111">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="61b6b-111">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="61b6b-112">Jeśli `PrimaryKey="true"` znajduje się w **unikatowy** unikatowego ograniczenia elementu, jest tworzony z **IsPrimaryKey** ustawioną właściwość **true**.</span><span class="sxs-lookup"><span data-stu-id="61b6b-112">If `PrimaryKey="true"` is present in the **unique** element, a unique constraint is created with the **IsPrimaryKey** property set to **true**.</span></span>|  
  
 <span data-ttu-id="61b6b-113">W poniższym przykładzie przedstawiono schematu XML, który używa **unikatowy** element, aby określić ograniczenie unikatowości.</span><span class="sxs-lookup"><span data-stu-id="61b6b-113">The following example shows an XML Schema that uses the **unique** element to specify a uniqueness constraint.</span></span>  
  
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
  
 <span data-ttu-id="61b6b-114">**Unikatowy** elementu w schemacie Określa, że wszystkie **klientów** elementów w dokumencie wystąpienia wartość **CustomerID** element podrzędny musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="61b6b-114">The **unique** element in the schema specifies that for all **Customers** elements in a document instance, the value of the **CustomerID** child element must be unique.</span></span> <span data-ttu-id="61b6b-115">W budynku **DataSet**, proces mapowania odczytuje ten schemat i generuje poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="61b6b-115">In building the **DataSet**, the mapping process reads this schema and generates the following table:</span></span>  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="61b6b-116">Proces mapowania tworzy także unikatowego ograniczenia na **CustomerID** kolumny, jak pokazano w poniższym **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="61b6b-116">The mapping process also creates a unique constraint on the **CustomerID** column, as shown in the following **DataSet**.</span></span> <span data-ttu-id="61b6b-117">(Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)</span><span class="sxs-lookup"><span data-stu-id="61b6b-117">(For simplicity, only relevant properties are shown.)</span></span>  
  
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
  
 <span data-ttu-id="61b6b-118">W **DataSet** generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unique.</span><span class="sxs-lookup"><span data-stu-id="61b6b-118">In the **DataSet** that is generated, the **IsPrimaryKey** property is set to **False** for the unique constraint.</span></span> <span data-ttu-id="61b6b-119">**Unikatowy** właściwość kolumna wskazuje, że **CustomerID** wartości kolumny muszą być unikatowe (, ale można je odwołanie o wartości null, określony przez **AllowDBNull** Właściwość kolumny).</span><span class="sxs-lookup"><span data-stu-id="61b6b-119">The **unique** property on the column indicates that the **CustomerID** column values must be unique (but they can be a null reference, as specified by the **AllowDBNull** property of the column).</span></span>  
  
 <span data-ttu-id="61b6b-120">Jeśli zmodyfikujesz schematu i ustawić opcjonalny **msdata:PrimaryKey** wartość do atrybutu **True**, ograniczenia unique jest tworzona w tabeli.</span><span class="sxs-lookup"><span data-stu-id="61b6b-120">If you modify the schema and set the optional **msdata:PrimaryKey** attribute value to **True**, the unique constraint is created on the table.</span></span> <span data-ttu-id="61b6b-121">**AllowDBNull** ma ustawioną wartość właściwości column **False**i **IsPrimaryKey** właściwości ograniczenia ustawioną **True**, w związku z tym wprowadzania **CustomerID** kolumny kolumna klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="61b6b-121">The **AllowDBNull** column property is set to **False**, and the **IsPrimaryKey** property of the constraint set to **True**, thus making the **CustomerID** column a primary key column.</span></span>  
  
 <span data-ttu-id="61b6b-122">Można określić unikatowego ograniczenia na kombinacji elementów lub atrybutów w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="61b6b-122">You can specify a unique constraint on a combination of elements or attributes in the XML Schema.</span></span> <span data-ttu-id="61b6b-123">W poniższym przykładzie pokazano sposób określić, że kombinację **CustomerID** i **NazwaFirmy** wartości muszą być unikatowe dla wszystkich **klientów** w żadnym wystąpieniu przez dodanie kolejnego **xs:field** elementu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="61b6b-123">The following example demonstrates how to specify that a combination of **CustomerID** and **CompanyName** values must be unique for all **Customers** in any instance, by adding another **xs:field** element in the schema.</span></span>  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 <span data-ttu-id="61b6b-124">Jest to ograniczenie, która jest tworzona w wynikowym **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="61b6b-124">This is the constraint that is created in the resulting **DataSet**.</span></span>  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="61b6b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61b6b-125">See Also</span></span>  
 [<span data-ttu-id="61b6b-126">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="61b6b-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="61b6b-127">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="61b6b-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="61b6b-128">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="61b6b-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
