---
title: Mapowanie relacji określonych dla zagnieżdżonych elementów
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 0346ba04fd8af6b5abc81fe994dd40f9a6a37c1d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423864"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="8cfa0-102">Mapowanie relacji określonych dla zagnieżdżonych elementów</span><span class="sxs-lookup"><span data-stu-id="8cfa0-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="8cfa0-103">Schemat może zawierać **msdata:Relationship** adnotacji, aby jawnie określić mapowanie między dowolne dwa elementy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="8cfa0-104">Dwa elementy, które są określone w **msdata:Relationship** może być zagnieżdżona w schemacie, ale nie trzeba być.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="8cfa0-105">Proces mapowania używa **msdata:Relationship** w schemacie, aby wygenerować podstawowy klucz/relacji klucza obcego między dwiema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="8cfa0-106">Poniższy przykład przedstawia schematu XML, w którym **OrderDetail** element jest elementem podrzędnym **kolejności**.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="8cfa0-107">**Msdata:Relationship** identyfikuje tę relację nadrzędny podrzędny i określa, że **OrderNumber** kolumny wynikowe **kolejności** tabela jest powiązana z **OrderNo** kolumny wynikowe **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="8cfa0-108">Proces mapowania schematu XML tworzy następujące <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="8cfa0-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="8cfa0-109">**Kolejności** i **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="8cfa0-110">Relacja między **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="8cfa0-111">**Zagnieżdżone** dla tej relacji jest właściwością **True** ponieważ **kolejności** i **OrderDetail** elementów jest zagnieżdżanych w schemacie .</span><span class="sxs-lookup"><span data-stu-id="8cfa0-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="8cfa0-112">Proces mapowania nie tworzy żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="8cfa0-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfa0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cfa0-113">See Also</span></span>  
 [<span data-ttu-id="8cfa0-114">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="8cfa0-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="8cfa0-115">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="8cfa0-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="8cfa0-116">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8cfa0-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
