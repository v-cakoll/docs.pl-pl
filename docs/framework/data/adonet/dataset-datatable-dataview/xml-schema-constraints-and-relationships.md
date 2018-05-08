---
title: Ograniczenia schematu XML i relacje
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 4b62b6bafa9ceeafd250e722314c4bd6c594bf82
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="xml-schema-constraints-and-relationships"></a>Ograniczenia schematu XML i relacje
W schemacie schematu XML definition language (XSD) można określić ograniczenia (unikatowe, key i keyref ograniczenia) i relacje (przy użyciu **msdata:Relationship** adnotacji). W tym temacie wyjaśniono, jak wygenerować interpretowania ograniczenia i relacje określonej w schemacie XML <xref:System.Data.DataSet>.  
  
 Ogólnie rzecz biorąc, w schematu XML możesz określić **msdata:Relationship** adnotacji, jeśli chcesz wygenerować tylko relacje w **zestawu danych**. Aby uzyskać więcej informacji, zobacz [generowania relacji zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Określ ograniczenia (unikatowe, key i keyref) Jeśli chcesz wygenerować ograniczeń **zestawu danych**. Należy pamiętać, że ograniczeń key i keyref są również używane do generowania relacje, zgodnie z objaśnieniem w dalszej części tego tematu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generowanie relacji z kluczy i keyref ograniczenia  
 Zamiast określania **msdata:Relationship** adnotacji, można określić ograniczenia key i keyref, które są używane podczas procesu mapowania schematu XML do generowania nie tylko ograniczenia, ale także relacji w  **Zestaw danych**. Jednak jeśli określisz `msdata:ConstraintOnly="true"` w **keyref** elementu **DataSet** uwzględni tylko ograniczenia i nie ma relacji.  
  
 W poniższym przykładzie przedstawiono schematu XML, który zawiera **kolejności** i **OrderDetail** elementów, które nie są zagnieżdżone. Schemat określa również ograniczeń key i keyref.  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 **DataSet** wygenerowanych podczas schematu XML zawiera proces mapowania **kolejności** i **OrderDetail** tabel. Ponadto **DataSet** zawiera relacje i ograniczenia. W poniższym przykładzie przedstawiono te zależności i ograniczeń. Należy pamiętać, że nie określono schematu **msdata:Relationship** adnotacji; zamiast tego ograniczeń key i keyref są używane do generowania relacji.  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 W poprzednim przykładzie schematu **kolejności** i **OrderDetail** elementy nie są zagnieżdżone. W poniższym przykładzie schematu te elementy są zagnieżdżone. Jednak nie **msdata:Relationship** adnotacji jest określona; w związku z tym założono niejawnych relacji. Aby uzyskać więcej informacji, zobacz [mapy niejawnych relacji między zagnieżdżone elementy schematu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Schemat określa również ograniczeń key i keyref.  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 **DataSet** wynikające z proces mapowania schematu XML zawiera dwie tabele:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** zawiera również dwie relacje (jedną na podstawie **msdata:relationship** adnotacji i innych oparte na ograniczeń key i keyref) i różne ograniczenia. W poniższym przykładzie przedstawiono zależności i ograniczeń.  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 Jeśli zawiera ograniczenie keyref odwołujących się do tabeli zagnieżdżonej **msdata:IsNested = "true"** adnotacji, **DataSet** spowoduje utworzenie relacji zagnieżdżonych pojedynczego opiera się na ograniczenie keyref i powiązane ograniczenia unique key.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
