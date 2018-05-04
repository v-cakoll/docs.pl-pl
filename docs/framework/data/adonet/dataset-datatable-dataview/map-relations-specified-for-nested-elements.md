---
title: Mapowanie relacji określonych dla elementów zagnieżdżonych
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: e1fde0ef585621a6821838613a7e77dedf7042b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapowanie relacji określonych dla elementów zagnieżdżonych
Schemat mogą obejmować **msdata:Relationship** adnotacji, aby jawnie określić mapowanie między wszelkie dwa elementy w schemacie. Dwa elementy określone **msdata:Relationship** mogą być zagnieżdżane w schemacie, ale nie trzeba być. Proces mapowania **msdata:Relationship** w schemacie wygenerować podstawowy klucz/relacji klucza obcego między dwiema kolumnami.  
  
 W poniższym przykładzie przedstawiono schematu XML, w którym **OrderDetail** element jest elementem podrzędnym **kolejności**. **Msdata:Relationship** identyfikuje tę relację nadrzędny podrzędny i określa, że **OrderNumber** kolumny powstałe w ten sposób **kolejności** tabela jest powiązana z **OrderNo** kolumny powstałe w ten sposób **OrderDetail** tabeli.  
  
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
  
 Proces mapowania schematu XML tworzy następujące opcje w <xref:System.Data.DataSet>:  
  
-   **Kolejności** i **OrderDetail** tabeli.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Relacja między **kolejności** i **OrderDetail** tabel. **Zagnieżdżone** ma ustawioną wartość właściwości dla tej relacji **True** ponieważ **kolejności** i **OrderDetail** elementy są zagnieżdżone w schemacie .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 Proces mapowania nie tworzy żadnych ograniczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
