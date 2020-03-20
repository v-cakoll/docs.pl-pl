---
title: Relacje i ograniczenia schematu XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150717"
---
# <a name="xml-schema-constraints-and-relationships"></a>Relacje i ograniczenia schematu XML
W schemacie języka definicji schematu schematu schematu XSD (XSD) można określić ograniczenia (unikatowe, kluczowe i keyref) oraz relacje (przy użyciu adnotacji **msdata:Relationship).** W tym temacie wyjaśniono, jak ograniczenia i relacje określone w schemacie XML są interpretowane w celu wygenerowania <xref:System.Data.DataSet>pliku .  
  
 Ogólnie rzecz biorąc w schemacie XML należy określić **adnotację msdata:Relationship,** jeśli chcesz wygenerować tylko relacje w **zestawie danych**. Aby uzyskać więcej informacji, zobacz [Generowanie relacji zestawu danych ze schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md). Należy określić ograniczenia (unikatowe, klucz i odnośnik), jeśli chcesz wygenerować ograniczenia w **zestawie danych**. Należy zauważyć, że ograniczenia klucza i odnośnika są również używane do generowania relacji, jak wyjaśniono w dalszej części tego tematu.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Generowanie relacji z ograniczeń klucza i odnośnika klucza  
 Zamiast określać **adnotację msdata:Relationship,** można określić ograniczenia klucza i odnośnika, które są używane podczas procesu mapowania schematu XML do generowania nie tylko ograniczeń, ale także relacji w **zestawie danych**. Jednak jeśli określisz `msdata:ConstraintOnly="true"` w elemencie **odnośnika,** **DataSet** będzie zawierać tylko ograniczenia i nie będzie zawierać relacji.  
  
 W poniższym przykładzie przedstawiono schemat XML, który zawiera **elementy Order** i **OrderDetail,** które nie są zagnieżdżone. Schemat określa również ograniczenia klucza i odnośnika.  
  
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
  
 **Zestaw danych** generowany podczas procesu mapowania schematu XML zawiera tabele **Kolejność** i **OrderDetail.** Ponadto Zestaw **danych** zawiera relacje i ograniczenia. Poniższy przykład przedstawia te relacje i ograniczenia. Należy zauważyć, że schemat nie określa **msdata:Opis** relacji; Zamiast tego ograniczenia klucza i odnośnika są używane do generowania relacji.  
  
```text
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
  
 W poprzednim przykładzie schematu **Order** i **OrderDetail** elementy nie są zagnieżdżone. W poniższym przykładzie schematu te elementy są zagnieżdżone. Jednak nie **msdata:Opis relacji** jest określony; w związku z tym zakłada się, że niejawna relacja. Aby uzyskać więcej informacji, zobacz [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](map-implicit-relations-between-nested-schema-elements.md). Schemat określa również ograniczenia klucza i odnośnika.  
  
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
  
 Zestaw **danych wynikający** z procesu mapowania schematu XML obejmuje dwie tabele:  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **Zestaw danych** zawiera również dwie relacje (jedna oparta na adnotacji **msdata:relationship,** a druga na podstawie ograniczeń klucza i odnośnika) oraz różne ograniczenia. Poniższy przykład przedstawia relacje i ograniczenia.  
  
```text
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
  
 Jeśli ograniczenie odnośnika odnośnego odnoszące się do tabeli zagnieżdżonej zawiera adnotację **msdata:IsNested="true",** **zestaw danych** utworzy pojedynczą relację zagnieżdżoną opartą na ograniczeniu odnośnika klucza i powiązanym ograniczeniu unikatowego/kluczowego.  
  
## <a name="see-also"></a>Zobacz też

- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
