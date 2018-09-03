---
title: Relacje i ograniczenia schematu XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: bcb6e257a40040701612b73768a98e056bccd6c5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480000"
---
# <a name="xml-schema-constraints-and-relationships"></a>Relacje i ograniczenia schematu XML
W schemacie języka (XSD) definicji schematu XML można określić ograniczenia (unikatowe, klucza i ograniczeń keyref) i relacji (przy użyciu **msdata:Relationship** adnotacji). W tym temacie wyjaśniono, jak interpretować ograniczenia i relacji określony w schemacie XML do generowania <xref:System.Data.DataSet>.  
  
 Ogólnie rzecz biorąc, w schematu XML, należy określić **msdata:Relationship** adnotacji, jeśli chcesz wygenerować tylko relacje w **zestawu danych**. Aby uzyskać więcej informacji, zobacz [Generowanie relacji elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Określ ograniczenia (unikatowe, klucza i keyref) Jeśli chcesz wygenerować ograniczeń **zestawu danych**. Należy pamiętać, że ograniczenia klucza i keyref również są używane do generowania relacji, zgodnie z opisem w dalszej części tego tematu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generowanie relacji z kluczem i ograniczeń keyref  
 Zamiast określania **msdata:Relationship** adnotacji, można określić klucz i keyref ograniczeń, które są używane w procesie mapowanie schematu XML do generowania nie tylko ograniczenia, ale także relacji w  **Zestaw danych**. Jednak w przypadku określenia `msdata:ConstraintOnly="true"` w **keyref** elementu **DataSet** będzie zawierać wyłącznie ograniczeń i nie zostaną uwzględnione w relacji.  
  
 W poniższym przykładzie przedstawiono schematu XML, który zawiera **kolejności** i **OrderDetail** elementy, które nie są zagnieżdżone. Schemat określa również ograniczeń keyref i kluczy.  
  
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
  
 **DataSet** , jest generowany podczas schematu XML zawiera proces mapowania **kolejności** i **OrderDetail** tabel. Ponadto **DataSet** zawiera relacje i ograniczenia. Poniższy kod przedstawia te relacje i ograniczenia. Należy zauważyć, że nie określono schematu **msdata:Relationship** adnotacji; zamiast tego ograniczenia klucza i keyref są używane do generowania relacji.  
  
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
  
 W poprzednim przykładzie schematu **kolejności** i **OrderDetail** elementy nie są zagnieżdżone. W poniższym przykładzie schematu tych elementów jest zagnieżdżanych. Jednak nie **msdata:Relationship** adnotacja jest określona; w związku z tym, przyjmowana jest niejawnych relacji. Aby uzyskać więcej informacji, zobacz [mapy niejawnych relacji między zagnieżdżone elementy schematu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). Schemat określa również ograniczeń keyref i kluczy.  
  
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
  
 **DataSet** wyniku procesu mapowania schematu XML zawiera dwie tabele:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet** obejmuje również dwie relacje (jedną na podstawie **msdata:relationship** adnotacji, a drugi na podstawie klucza i keyref ograniczeń) i różnych ograniczeń. Poniższy przykład pokazuje, relacje i ograniczenia.  
  
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
  
 Jeśli zawiera ograniczenie keyref odwołujące się do tabeli zagnieżdżonej **msdata:IsNested = "true"** adnotacji, **DataSet** spowoduje utworzenie jednego relację zagnieżdżonych, która opiera się na ograniczenie keyref i powiązane ograniczenia unique key.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
