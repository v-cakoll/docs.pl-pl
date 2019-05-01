---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 076e3ec6e5a00fd294fa3c6d7998cfab3a136240
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879596"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
Schemat języka (XSD) definicji schematu XML może mieć typy złożone, zagnieżdżone wewnątrz siebie nawzajem. W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące <xref:System.Data.DataSet>:  
  
- Jedną tabelę dla każdego z typów złożonych (nadrzędnych i podrzędnych).  
  
- Jeśli nie ograniczenia unique znajduje się na element nadrzędny, co dodatkowe kolumny klucza podstawowego dla definicji tabeli o nazwie *TableName*_identyfikator gdzie *TableName* jest nazwą tabeli nadrzędnej.  
  
- Ograniczenia klucza podstawowego w tabeli nadrzędnej identyfikowanie dodatkową kolumnę jako klucz podstawowy (przez ustawienie **IsPrimaryKey** właściwości **True**). Ograniczenie o nazwie ograniczenie\# gdzie \# to 1, 2, 3 i tak dalej. Na przykład domyślna nazwa pierwszego ograniczenia jest Constraint1.  
  
- Ograniczenia klucza obcego dla tabeli podrzędnej identyfikuje dodatkową kolumnę jako klucz obcy odwołujące się do klucza podstawowego tabeli nadrzędnej. Ograniczenie o nazwie *ParentTable_ChildTable* gdzie *ParentTable* jest nazwą tabeli nadrzędnej i *ChildTable* jest nazwą tabeli podrzędnej.  
  
- Relacje danych między tabelami nadrzędnymi i podrzędnymi.  
  
 Poniższy przykład przedstawia schematu gdzie **OrderDetail** jest elementem podrzędnym **kolejności**.  
  
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
  
 Proces mapowania schematu XML tworzy następujące **zestawu danych**:  
  
- **Kolejności** i **OrderDetail** tabeli.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Ograniczenia unique wobec **kolejności** tabeli. Należy pamiętać, że **IsPrimaryKey** właściwość jest ustawiona na **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- Ograniczenie klucza obcego w **OrderDetail** tabeli.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- Relacja między **kolejności** i **OrderDetail** tabel. **Zagnieżdżone** dla tej relacji jest właściwością **True** ponieważ **kolejności** i **OrderDetail** elementów jest zagnieżdżanych w schemacie .  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
