---
title: Określanie relacji między elementami bez zagnieżdżania
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 3aa9976ccde426eeda1d869164409c5235a629fe
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040052"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="64aa8-102">Określanie relacji między elementami bez zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="64aa8-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="64aa8-103">Gdy elementy nie są zagnieżdżone, nie są tworzone żadne niejawne relacje.</span><span class="sxs-lookup"><span data-stu-id="64aa8-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="64aa8-104">Można jednak jawnie określić relacje między elementami, które nie są zagnieżdżone przy użyciu adnotacji **msdata: Relationship** .</span><span class="sxs-lookup"><span data-stu-id="64aa8-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="64aa8-105">W poniższym przykładzie przedstawiono schemat XML, w którym jest określona adnotacja **msdata: Relationship** między elementami **Order** i **OrderDetail** , które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="64aa8-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="64aa8-106">Adnotacja **msdata: Relationship** jest określana jako element podrzędny elementu **Schema** .</span><span class="sxs-lookup"><span data-stu-id="64aa8-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="64aa8-107">Proces mapowania schematu języka definicji schematu XML (XSD) tworzy <xref:System.Data.DataSet> z tabelami **Order** i **OrderDetail** oraz relacją określoną między tymi dwiema tabelami, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="64aa8-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="64aa8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64aa8-108">See also</span></span>

- [<span data-ttu-id="64aa8-109">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="64aa8-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="64aa8-110">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="64aa8-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="64aa8-111">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64aa8-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
