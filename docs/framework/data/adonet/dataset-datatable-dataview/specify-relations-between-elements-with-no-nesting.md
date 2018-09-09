---
title: Określanie relacji między elementami bez zagnieżdżania
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: d04a3d946b87c7203497313c6e21a75ef69f50eb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251748"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="7155e-102">Określanie relacji między elementami bez zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="7155e-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="7155e-103">Jeśli elementy nie są zagnieżdżone, są tworzone nie niejawnych relacji.</span><span class="sxs-lookup"><span data-stu-id="7155e-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="7155e-104">Możliwe, jednak jawnie określić relacji między elementami, które nie są osadzone za pomocą **msdata:Relationship** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="7155e-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="7155e-105">Poniższy przykład przedstawia schematu XML, w którym **msdata:Relationship** adnotacja jest określona między **kolejności** i **OrderDetail** elementy, które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="7155e-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="7155e-106">**Msdata:Relationship** adnotacja jest określona jako element podrzędny elementu **schematu** elementu.</span><span class="sxs-lookup"><span data-stu-id="7155e-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="7155e-107">Tworzy proces mapowania schematu języka (XSD) definicji schematu XML <xref:System.Data.DataSet> z **kolejności** i **OrderDetail** tabel i podana relacja między tymi dwiema tabelami, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="7155e-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="7155e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7155e-108">See Also</span></span>  
 [<span data-ttu-id="7155e-109">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7155e-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="7155e-110">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="7155e-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="7155e-111">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7155e-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
