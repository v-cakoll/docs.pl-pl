---
title: Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 1bce0c2815ac94787055794942807777232df295
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763631"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu
Schemat schematu XML definition language (XSD) może mieć typów złożonych zagnieżdżona siebie nawzajem. W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące opcje w <xref:System.Data.DataSet>:  
  
-   Jedna tabela dla każdego z typów złożonych (nadrzędnych i podrzędnych).  
  
-   Jeśli nie ograniczenia unique istnieje w nadrzędnej, co dodatkowe kolumny klucza podstawowego dla definicji tabeli o nazwie *TableName*_Id gdzie *TableName* jest nazwą tabeli nadrzędnej.  
  
-   Ograniczenia klucza podstawowego w tabeli nadrzędnej identyfikowanie dodatkowych kolumn jako klucz podstawowy (przez ustawienie **IsPrimaryKey** właściwości **True**). Ograniczenie o nazwie ograniczenie*#* gdzie *#* 1, 2, 3 i tak dalej. Na przykład domyślna nazwa ograniczenia pierwszy to Constraint1.  
  
-   Ograniczenie klucza obcego w tabeli podrzędnej identyfikację dodatkowych kolumn jako klucz obcy odwołujących się do klucza podstawowego tabeli nadrzędnej. Ograniczenie o nazwie *ParentTable_ChildTable* gdzie *ParentTable* jest nazwą tabeli nadrzędnej i *ChildTable* jest nazwą tabeli podrzędnej.  
  
-   Dane relacji między tabelą nadrzędną i podrzędną.  
  
 W poniższym przykładzie przedstawiono schematu gdzie **OrderDetail** jest elementem podrzędnym **kolejności**.  
  
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
  
 Proces mapowania schematu XML tworzy następujące opcje w **zestawu danych**:  
  
-   **Kolejności** i **OrderDetail** tabeli.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Ograniczenia unique wobec **kolejności** tabeli. Należy pamiętać, że **IsPrimaryKey** właściwość jest ustawiona na **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Ograniczenie klucza obcego w **OrderDetail** tabeli.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Relacja między **kolejności** i **OrderDetail** tabel. **Zagnieżdżone** ma ustawioną wartość właściwości dla tej relacji **True** ponieważ **kolejności** i **OrderDetail** elementy są zagnieżdżone w schemacie .  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
