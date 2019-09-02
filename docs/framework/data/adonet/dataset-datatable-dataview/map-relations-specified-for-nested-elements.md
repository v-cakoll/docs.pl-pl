---
title: Mapowanie relacji określonych dla zagnieżdżonych elementów
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 510a5e676df7bac274c6086b94e9a23e7540da20
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204638"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="37375-102">Mapowanie relacji określonych dla zagnieżdżonych elementów</span><span class="sxs-lookup"><span data-stu-id="37375-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="37375-103">Schemat może zawierać adnotację **msdata: Relationship** , aby jawnie określić mapowanie między dowolnymi dwoma elementami w schemacie.</span><span class="sxs-lookup"><span data-stu-id="37375-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="37375-104">Dwa elementy określone w **msdata: Relationship** mogą być zagnieżdżane w schemacie, ale nie muszą być.</span><span class="sxs-lookup"><span data-stu-id="37375-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="37375-105">Proces mapowania używa **relacji msdata: Relationship** w schemacie do generowania relacji klucza podstawowego/klucza obcego między dwiema kolumnami.</span><span class="sxs-lookup"><span data-stu-id="37375-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="37375-106">W poniższym przykładzie przedstawiono schemat XML, w którym element **OrderDetail** jest elementem podrzędnym **zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="37375-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="37375-107">**Msdata: Relationship** identyfikuje tę relację nadrzędny-podrzędny i określa, że kolumna **OrderNumber** tabeli **kolejności** wyników jest powiązana z kolumną **OrderNo** tabeli wyników w **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="37375-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="37375-108">Proces mapowania schematu XML tworzy następujące elementy w <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="37375-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="37375-109">**Zamówienie** i tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="37375-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="37375-110">Relacja między tabelami **Order** i **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="37375-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="37375-111">Właściwość **zagnieżdżona** dla tej relacji jest ustawiona na **wartość true** , ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="37375-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="37375-112">Proces mapowania nie tworzy żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="37375-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37375-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37375-113">See also</span></span>

- [<span data-ttu-id="37375-114">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="37375-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="37375-115">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="37375-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="37375-116">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="37375-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
