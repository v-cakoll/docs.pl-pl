---
title: Określanie relacji między elementami bez zagnieżdżania
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150821"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="a70e3-102">Określanie relacji między elementami bez zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="a70e3-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="a70e3-103">Gdy elementy nie są zagnieżdżone, nie są tworzone niejawne relacje.</span><span class="sxs-lookup"><span data-stu-id="a70e3-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="a70e3-104">Można jednak jawnie określić relacje między elementami, które nie są zagnieżdżone przy użyciu **adnotacji msdata:Relationship.**</span><span class="sxs-lookup"><span data-stu-id="a70e3-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="a70e3-105">Poniższy przykład przedstawia schemat XML, w którym **adnotacja msdata:Relationship** jest określona między elementami **Order** i **OrderDetail,** które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="a70e3-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="a70e3-106">Adnotacja **msdata:Relationship** jest określona jako element podrzędny elementu **Schema.**</span><span class="sxs-lookup"><span data-stu-id="a70e3-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="a70e3-107">Proces mapowania języka xsd (XSD) schematu schematu schematu schematu XML tworzy <xref:System.Data.DataSet> tabele **Order** i **OrderDetail** oraz relację określoną między tymi dwiema tabelami, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="a70e3-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="a70e3-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a70e3-108">See also</span></span>

- [<span data-ttu-id="a70e3-109">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a70e3-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="a70e3-110">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a70e3-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="a70e3-111">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a70e3-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
