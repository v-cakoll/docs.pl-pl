---
title: Mapowanie klucz ograniczenia schematu XML (XSD) do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 249cb8419d4f032c37a922c9aa640f02f6efbd56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="f75b3-102">Mapowanie klucz ograniczenia schematu XML (XSD) do ograniczenia zestawu danych</span><span class="sxs-lookup"><span data-stu-id="f75b3-102">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="f75b3-103">W schemacie, można określić ograniczenie klucza dla elementu lub atrybutu przy użyciu **klucza** elementu.</span><span class="sxs-lookup"><span data-stu-id="f75b3-103">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="f75b3-104">Element lub atrybut, w którym określono ograniczenie klucza muszą mieć unikatowe wartości w żadnym wystąpieniu schematu, a nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="f75b3-104">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="f75b3-105">Ograniczenie klucza jest podobny do ograniczenia unique, z wyjątkiem tego, czy kolumna, w którym zdefiniowano ograniczenie klucza nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="f75b3-105">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="f75b3-106">W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **klucza** elementu.</span><span class="sxs-lookup"><span data-stu-id="f75b3-106">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="f75b3-107">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="f75b3-107">Attribute name</span></span>|<span data-ttu-id="f75b3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f75b3-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f75b3-109">**MSDATA:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="f75b3-109">**msdata:ConstraintName**</span></span>|<span data-ttu-id="f75b3-110">Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="f75b3-110">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="f75b3-111">W przeciwnym razie **nazwa** atrybutu zawiera wartości nazwy ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="f75b3-111">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="f75b3-112">**MSDATA:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="f75b3-112">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="f75b3-113">Jeśli `PrimaryKey="true"` jest obecny, **IsPrimaryKey** ograniczenia właściwości ustawiono **true**, co czyni go po klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="f75b3-113">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="f75b3-114">**AllowDBNull** ma ustawioną wartość właściwości column **false**, ponieważ klucze podstawowe nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="f75b3-114">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="f75b3-115">Podczas konwertowania schematu, w którym określono ograniczenie klucza, proces mapowania tworzy unikatowego ograniczenia tabeli z **AllowDBNull** właściwości column ustawioną **false** dla każdej kolumny w ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="f75b3-115">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="f75b3-116">**IsPrimaryKey** również ustawiono właściwość unikatowego ograniczenia **false** , chyba że określono `msdata:PrimaryKey="true"` na **klucza** elementu.</span><span class="sxs-lookup"><span data-stu-id="f75b3-116">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="f75b3-117">Jest to identyczne unikatowego ograniczenia w schemacie, w którym `PrimaryKey="true"`.</span><span class="sxs-lookup"><span data-stu-id="f75b3-117">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="f75b3-118">W poniższym przykładzie schematu **klucza** element określa ograniczenia klucza w **CustomerID** elementu.</span><span class="sxs-lookup"><span data-stu-id="f75b3-118">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
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
  
 <span data-ttu-id="f75b3-119">**Klucza** element określa, że wartości **CustomerID** elementem podrzędnym **klientów** element muszą mieć unikatowe wartości i nie może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="f75b3-119">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="f75b3-120">W tłumaczeniu schematu (XSD) języka definicji schematu XML, proces mapowania tworzy poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="f75b3-120">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="f75b3-121">Tworzy również mapowanie schematu XML **UniqueConstraint** na **CustomerID** kolumny, jak pokazano w poniższym <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f75b3-121">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f75b3-122">(Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)</span><span class="sxs-lookup"><span data-stu-id="f75b3-122">(For simplicity, only relevant properties are shown.)</span></span>  
  
```  
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
  
 <span data-ttu-id="f75b3-123">W **DataSet** generowany, **IsPrimaryKey** właściwość **UniqueConstraint** ustawiono **true** ponieważ schematu Określa `msdata:PrimaryKey="true"` w **klucza** elementu.</span><span class="sxs-lookup"><span data-stu-id="f75b3-123">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="f75b3-124">Wartość **ConstraintName** właściwość **UniqueConstraint** w **DataSet** jest wartością **msdata:ConstraintName** Podany atrybut w **klucza** elementu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="f75b3-124">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75b3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f75b3-125">See Also</span></span>  
 [<span data-ttu-id="f75b3-126">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="f75b3-126">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="f75b3-127">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f75b3-127">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="f75b3-128">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="f75b3-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
