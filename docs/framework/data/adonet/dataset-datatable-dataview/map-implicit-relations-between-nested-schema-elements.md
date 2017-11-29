---
title: "Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b3e3243384bd1dd55661a87ee67cc3052b94e923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu
Schemat schematu XML definition language (XSD) może mieć typów złożonych zagnieżdżona siebie nawzajem. W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące opcje w <xref:System.Data.DataSet>:  
  
-   Jedna tabela dla każdego z typów złożonych (nadrzędnych i podrzędnych).  
  
-   Jeśli nie ograniczenia unique istnieje w nadrzędnej, co dodatkowe kolumny klucza podstawowego dla definicji tabeli o nazwie *TableName*_Id gdzie *TableName* jest nazwą tabeli nadrzędnej.  
  
-   Ograniczenia klucza podstawowego w tabeli nadrzędnej identyfikowanie dodatkowych kolumn jako klucz podstawowy (przez ustawienie **IsPrimaryKey** właściwości **True**). Ograniczenie o nazwie ograniczenie *#*  gdzie  *#*  1, 2, 3 i tak dalej. Na przykład domyślna nazwa ograniczenia pierwszy to Constraint1.  
  
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
 [Generowanie relacji zestawu danych na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
