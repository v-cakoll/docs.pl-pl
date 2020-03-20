---
title: Mapowanie relacji określonych dla zagnieżdżonych elementów
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150899"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="2b71c-102">Mapowanie relacji określonych dla zagnieżdżonych elementów</span><span class="sxs-lookup"><span data-stu-id="2b71c-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="2b71c-103">Schemat może zawierać **adnotację msdata:Relationship,** aby jawnie określić mapowanie między dowolnymi dwoma elementami w schemacie.</span><span class="sxs-lookup"><span data-stu-id="2b71c-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="2b71c-104">Dwa elementy określone w **msdata:Relationship** mogą być zagnieżdżone w schemacie, ale nie muszą być.</span><span class="sxs-lookup"><span data-stu-id="2b71c-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="2b71c-105">Proces mapowania używa **msdata:Relationship** w schemacie do generowania relacji klucz podstawowy/klucz obcy między dwiema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="2b71c-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="2b71c-106">W poniższym przykładzie pokazano schemat XML, w którym **OrderDetail** element jest elementem podrzędnym **Order**.</span><span class="sxs-lookup"><span data-stu-id="2b71c-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="2b71c-107">**Msdata:Relationship** identyfikuje tę relację nadrzędny-podrzędny i określa, że kolumna **OrderNumber** wynikowej tabeli **Order** jest powiązana z kolumną **OrderNo** wynikowej tabeli **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="2b71c-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
 <xs:complexType>  
  <xs:choice maxOccurs="unbounded">  
   <xs:element name="Order">  
    <xs:complexType>  
     <xs:sequence>  
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="2b71c-108">Proces mapowania schematu XML tworzy <xref:System.Data.DataSet>następujące elementy w:</span><span class="sxs-lookup"><span data-stu-id="2b71c-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="2b71c-109">**Zamówienie** i **orderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="2b71c-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="2b71c-110">Relacja między tabelami **Order** i **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="2b71c-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="2b71c-111">Właściwość **Zagnieżdżona** dla tej relacji jest ustawiona na **True,** ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="2b71c-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="2b71c-112">Proces mapowania nie tworzy żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="2b71c-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b71c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b71c-113">See also</span></span>

- [<span data-ttu-id="2b71c-114">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2b71c-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="2b71c-115">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="2b71c-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2b71c-116">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2b71c-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
