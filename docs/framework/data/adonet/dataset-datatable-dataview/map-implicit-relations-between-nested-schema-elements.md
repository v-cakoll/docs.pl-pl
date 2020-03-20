---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150966"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
Schemat języka XM (XSD) może mieć złożone typy zagnieżdżone wewnątrz siebie. W takim przypadku proces mapowania stosuje mapowanie domyślne i tworzy następujące elementy w: <xref:System.Data.DataSet>  
  
- Jedna tabela dla każdego z typów złożonych (nadrzędny i podrzędny).  
  
- Jeśli w chyłce element nadrzędny nie istnieje żadne unikatowe ograniczenie, jedna dodatkowa kolumna klucza podstawowego na definicję tabeli o nazwie *TableName*_Id gdzie *Nazwa tabeli* jest nazwą tabeli nadrzędnej.  
  
- Ograniczenie klucza podstawowego w tabeli nadrzędnej identyfikujące dodatkową kolumnę jako klucz podstawowy (przez ustawienie właściwości **IsPrimaryKey** na **True).** Ograniczenie nosi nazwę\# \# Ograniczenie, gdzie jest 1, 2, 3 i tak dalej. Na przykład domyślną nazwą pierwszego ograniczenia jest Constraint1.  
  
- Ograniczenie klucza obcego w tabeli podrzędnej identyfikujące dodatkową kolumnę jako klucz obcy odnoszący się do klucza podstawowego tabeli nadrzędnej. Ograniczenie nosi nazwę *ParentTable_ChildTable* gdzie *Tabela nadrzędna* jest nazwą tabeli nadrzędnej, a *Tabela podrzędna* jest nazwą tabeli podrzędnej.  
  
- Relacja danych między tabelami nadrzędnymi i podrzędnymi.  
  
 W poniższym przykładzie pokazano schemat, w którym **OrderDetail** jest elementem podrzędnym **Order**.  
  
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
  
 Proces mapowania schematu XML tworzy w **zestawie danych**następujące elementy:  
  
- **Zamówienie** i **orderDetail** tabeli.  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Unikatowe ograniczenie w tabeli **Kolejność.** Należy zauważyć, że **właściwość IsPrimaryKey** jest ustawiona na **True**.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- Ograniczenie klucza obcego w tabeli **OrderDetail.**  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail.** Właściwość **Zagnieżdżona** dla tej relacji jest ustawiona na **True,** ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
