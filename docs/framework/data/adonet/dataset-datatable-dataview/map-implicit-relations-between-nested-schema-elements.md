---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 25fc2c427727273038f7b4267376d6ba6446b811
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040392"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
Schemat języka definicji schematu XML (XSD) może mieć złożone typy zagnieżdżone wewnątrz siebie. W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące elementy w <xref:System.Data.DataSet>:  
  
- Jedna tabela dla każdego z typów złożonych (nadrzędnych i podrzędnych).  
  
- Jeśli w obiekcie nadrzędnym nie istnieje ograniczenie UNIQUE, jedna dodatkowa kolumna klucza podstawowego dla definicji tabeli o nazwie *TableName*_Id, gdzie *TableName* jest nazwą tabeli nadrzędnej.  
  
- Ograniczenie PRIMARY KEY w tabeli nadrzędnej identyfikujące dodatkową kolumnę jako klucz podstawowy (przez ustawienie właściwości **IsPrimaryKey** na **wartość true**). Ograniczenie ma nazwę ograniczenia\# gdzie \# ma wartość 1, 2, 3 i tak dalej. Na przykład domyślna nazwa pierwszego ograniczenia to Constraint1.  
  
- Ograniczenie klucza obcego w tabeli podrzędnej identyfikującej dodatkową kolumnę jako klucz obcy odwołujący się do klucza podstawowego tabeli nadrzędnej. Ograniczenie ma nazwę *ParentTable_ChildTable* , gdzie *element parentname* jest nazwą tabeli nadrzędnej i *elementem podrzędnym* jest nazwa tabeli podrzędnej.  
  
- Relacja danych między tabelami nadrzędnymi i podrzędnymi.  
  
 W poniższym przykładzie przedstawiono schemat, gdzie **OrderDetail** jest elementem podrzędnym **zamówienia**.  
  
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
  
 Proces mapowania schematu XML tworzy następujące elementy w **zestawie danych**:  
  
- **Zamówienie** i tabela **OrderDetail** .  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Unikatowe ograniczenie tabeli **Order** . Należy pamiętać, że właściwość **IsPrimaryKey** jest ustawiona na **wartość true**.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- Ograniczenie klucza obcego w tabeli **OrderDetail** .  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail** . Właściwość **zagnieżdżona** dla tej relacji jest ustawiona na **wartość true** , ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.  
  
    ```text  
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

- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
