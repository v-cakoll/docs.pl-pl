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
# <a name="map-relations-specified-for-nested-elements"></a>Mapowanie relacji określonych dla zagnieżdżonych elementów
Schemat może zawierać **adnotację msdata:Relationship,** aby jawnie określić mapowanie między dowolnymi dwoma elementami w schemacie. Dwa elementy określone w **msdata:Relationship** mogą być zagnieżdżone w schemacie, ale nie muszą być. Proces mapowania używa **msdata:Relationship** w schemacie do generowania relacji klucz podstawowy/klucz obcy między dwiema kolumnami.  
  
 W poniższym przykładzie pokazano schemat XML, w którym **OrderDetail** element jest elementem podrzędnym **Order**. **Msdata:Relationship** identyfikuje tę relację nadrzędny-podrzędny i określa, że kolumna **OrderNumber** wynikowej tabeli **Order** jest powiązana z kolumną **OrderNo** wynikowej tabeli **OrderDetail.**  
  
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
  
 Proces mapowania schematu XML tworzy <xref:System.Data.DataSet>następujące elementy w:  
  
- **Zamówienie** i **orderDetail** tabeli.  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail.** Właściwość **Zagnieżdżona** dla tej relacji jest ustawiona na **True,** ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapowania nie tworzy żadnych ograniczeń.  
  
## <a name="see-also"></a>Zobacz też

- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
