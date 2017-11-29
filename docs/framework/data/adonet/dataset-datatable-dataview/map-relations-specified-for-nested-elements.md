---
title: "Mapowanie relacji określonych dla elementów zagnieżdżonych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9866b556f2ba09cef7616fea4a2a6d8135e6b8e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="22c49-102">Mapowanie relacji określonych dla elementów zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="22c49-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="22c49-103">Schemat mogą obejmować **msdata:Relationship** adnotacji, aby jawnie określić mapowanie między wszelkie dwa elementy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="22c49-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="22c49-104">Dwa elementy określone **msdata:Relationship** mogą być zagnieżdżane w schemacie, ale nie trzeba być.</span><span class="sxs-lookup"><span data-stu-id="22c49-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="22c49-105">Proces mapowania **msdata:Relationship** w schemacie wygenerować podstawowy klucz/relacji klucza obcego między dwiema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="22c49-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="22c49-106">W poniższym przykładzie przedstawiono schematu XML, w którym **OrderDetail** element jest elementem podrzędnym **kolejności**.</span><span class="sxs-lookup"><span data-stu-id="22c49-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="22c49-107">**Msdata:Relationship** identyfikuje tę relację nadrzędny podrzędny i określa, że **OrderNumber** kolumny powstałe w ten sposób **kolejności** tabela jest powiązana z **OrderNo** kolumny powstałe w ten sposób **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="22c49-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="22c49-108">Proces mapowania schematu XML tworzy następujące opcje w <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="22c49-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="22c49-109">**Kolejności** i **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="22c49-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="22c49-110">Relacja między **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="22c49-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="22c49-111">**Zagnieżdżone** ma ustawioną wartość właściwości dla tej relacji **True** ponieważ **kolejności** i **OrderDetail** elementy są zagnieżdżone w schemacie .</span><span class="sxs-lookup"><span data-stu-id="22c49-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="22c49-112">Proces mapowania nie tworzy żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="22c49-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c49-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22c49-113">See Also</span></span>  
 [<span data-ttu-id="22c49-114">Generowanie relacji zestawu danych na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="22c49-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="22c49-115">Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych</span><span class="sxs-lookup"><span data-stu-id="22c49-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="22c49-116">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="22c49-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
