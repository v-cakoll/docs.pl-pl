---
title: "Określanie relacji między elementami z nie zagnieżdżania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 036085160e9e4817964754a85db627e4d4ba8654
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="109f4-102">Określanie relacji między elementami z nie zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="109f4-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="109f4-103">Gdy nie są zagnieżdżone elementy, nie niejawnych relacji są tworzone.</span><span class="sxs-lookup"><span data-stu-id="109f4-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="109f4-104">Można jednak jawnie określić relacji między elementami, które nie są zagnieżdżone za pomocą **msdata:Relationship** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="109f4-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="109f4-105">W poniższym przykładzie przedstawiono schematu XML, w którym **msdata:Relationship** adnotacji określono między **kolejności** i **OrderDetail** elementy, które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="109f4-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="109f4-106">**Msdata:Relationship** adnotacji jest określony jako element podrzędny elementu **schematu** elementu.</span><span class="sxs-lookup"><span data-stu-id="109f4-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
             xmlns:xs="http://www.w3.org/2001/XMLSchema"   
             xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="109f4-107">Proces mapowania schematu XML definition language (XSD) schematu tworzy <xref:System.Data.DataSet> z **kolejności** i **OrderDetail** tabel i podana relacja między tymi dwiema tabelami, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="109f4-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="109f4-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="109f4-108">See Also</span></span>  
 [<span data-ttu-id="109f4-109">Generowanie relacji zestawu danych na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="109f4-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="109f4-110">Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych</span><span class="sxs-lookup"><span data-stu-id="109f4-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="109f4-111">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="109f4-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
