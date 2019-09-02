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
# <a name="map-relations-specified-for-nested-elements"></a>Mapowanie relacji określonych dla zagnieżdżonych elementów
Schemat może zawierać adnotację **msdata: Relationship** , aby jawnie określić mapowanie między dowolnymi dwoma elementami w schemacie. Dwa elementy określone w **msdata: Relationship** mogą być zagnieżdżane w schemacie, ale nie muszą być. Proces mapowania używa **relacji msdata: Relationship** w schemacie do generowania relacji klucza podstawowego/klucza obcego między dwiema kolumnami.  
  
 W poniższym przykładzie przedstawiono schemat XML, w którym element **OrderDetail** jest elementem podrzędnym **zamówienia**. **Msdata: Relationship** identyfikuje tę relację nadrzędny-podrzędny i określa, że kolumna **OrderNumber** tabeli **kolejności** wyników jest powiązana z kolumną **OrderNo** tabeli wyników w **OrderDetail** .  
  
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
  
 Proces mapowania schematu XML tworzy następujące elementy w <xref:System.Data.DataSet>:  
  
- **Zamówienie** i tabela **OrderDetail** .  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail** . Właściwość **zagnieżdżona** dla tej relacji jest ustawiona na **wartość true** , ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapowania nie tworzy żadnych ograniczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
