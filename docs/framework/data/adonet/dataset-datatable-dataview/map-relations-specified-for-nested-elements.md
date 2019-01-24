---
title: Mapowanie relacji określonych dla zagnieżdżonych elementów
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cec7be5bea466c353e5320c04c76b37764a87e1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527526"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapowanie relacji określonych dla zagnieżdżonych elementów
Schemat może zawierać **msdata:Relationship** adnotacji, aby jawnie określić mapowanie między dowolne dwa elementy w schemacie. Dwa elementy, które są określone w **msdata:Relationship** może być zagnieżdżona w schemacie, ale nie trzeba być. Proces mapowania używa **msdata:Relationship** w schemacie, aby wygenerować podstawowy klucz/relacji klucza obcego między dwiema kolumnami.  
  
 Poniższy przykład przedstawia schematu XML, w którym **OrderDetail** element jest elementem podrzędnym **kolejności**. **Msdata:Relationship** identyfikuje tę relację nadrzędny podrzędny i określa, że **OrderNumber** kolumny wynikowe **kolejności** tabela jest powiązana z **OrderNo** kolumny wynikowe **OrderDetail** tabeli.  
  
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
  
 Proces mapowania schematu XML tworzy następujące <xref:System.Data.DataSet>:  
  
-   **Kolejności** i **OrderDetail** tabeli.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   Relacja między **kolejności** i **OrderDetail** tabel. **Zagnieżdżone** dla tej relacji jest właściwością **True** ponieważ **kolejności** i **OrderDetail** elementów jest zagnieżdżanych w schemacie .  
  
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
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
