---
title: Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 93f766003326fd41357581196015fd58c71d7508
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040367"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
Element **keyref** umożliwia ustanowienie linków między elementami w dokumencie. Jest to podobne do relacji klucza obcego w relacyjnej bazie danych. Jeśli schemat określa element **keyref** , element jest konwertowany podczas procesu mapowania schematu do odpowiedniego ograniczenia klucza obcego w kolumnach w tabelach <xref:System.Data.DataSet>. Domyślnie element **keyref** również generuje relację z właściwościami **Parent**, **Child**, **ParentColumn**i **ChildColumn** określonymi w relacji.  
  
 Poniższa tabela zawiera opis atrybutów **msdata** , które można określić w elemencie **keyref** .  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Jeśli **ConstraintOnly = "true"** jest określony w elemencie **keyref** w schemacie, zostanie utworzone ograniczenie, ale nie jest tworzone żadne powiązanie. Jeśli ten atrybut nie jest określony (lub jest ustawiony na **wartość false**), zarówno ograniczenie, jak i relacja są tworzone w **zestawie danych**.|  
|**msdata: ConstraintName**|Jeśli określono atrybut **ConstraintName** , jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie atrybut **name** elementu **keyref** w schemacie zawiera nazwę ograniczenia w **zestawie danych**.|  
|**msdata:UpdateRule**|Jeśli atrybut **UpdateRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **UpdateRule** w **zestawie danych**. W przeciwnym razie Właściwość **UpdateRule** jest ustawiona na **Kaskada**.|  
|**msdata:DeleteRule**|Jeśli atrybut **DeleteRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **DeleteRule** w **zestawie danych**. W przeciwnym razie Właściwość **DeleteRule** jest ustawiona na **Kaskada**.|  
|**msdata:AcceptRejectRule**|Jeśli atrybut **AcceptRejectRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **AcceptRejectRule** w **zestawie danych**. W przeciwnym razie Właściwość **AcceptRejectRule** ma wartość **none**.|  
  
 Poniższy przykład zawiera schemat, który określa relacje **Key** i **keyref** między elementem podrzędnym **OrderNumber** elementu **Order** i elementem podrzędnym **OrderNo** **OrderDetail** postaci.  
  
 W przykładzie element podrzędny **OrderNumber** elementu **OrderDetail** odwołuje się do elementu podrzędnego klucza **OrderNo** elementu **Order** .  
  
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
  
 Proces mapowania schematu języka definicji schematu XML (XSD) generuje następujący **zestaw danych** z dwiema tabelami:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ponadto **zestaw danych** definiuje następujące ograniczenia:  
  
- Unikatowe ograniczenie tabeli **Order** .  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail** . Właściwość **zagnieżdżona** jest ustawiona na **false** , ponieważ dwa elementy nie są zagnieżdżone w schemacie.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- Ograniczenie klucza obcego w tabeli **OrderDetail** .  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
