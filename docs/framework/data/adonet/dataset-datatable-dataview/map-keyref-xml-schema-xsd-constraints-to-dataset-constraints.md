---
title: Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150886"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
Element **keyref** umożliwia ustanowienie łączy między elementami w dokumencie. Jest to podobne do relacji klucza obcego w relacyjnej bazie danych. Jeśli schemat określa element **keyref,** element jest konwertowany podczas procesu mapowania schematu na odpowiednie ograniczenie <xref:System.Data.DataSet>klucza obcego w kolumnach w tabelach programu . Domyślnie **keyref** element generuje również relację, z **ParentTable**, **ChildTable**, **ParentColumn**i **ChildColumn** właściwości określonych w relacji.  
  
 W poniższej tabeli przedstawiono atrybuty **msdata,** które można określić w elemencie **odnośnika.**  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:OgraniczenieOnowo**|Jeśli **ConstraintOnly="true"** jest określony w elemencie **keyref** w schemacie, tworzone jest ograniczenie, ale nie jest tworzony żadna relacja. Jeśli ten atrybut nie jest określony (lub jest ustawiony na **False),** zarówno ograniczenie, jak i relacja są tworzone w **zestawie danych**.|  
|**msdata:Nazwa więzów**|Jeśli atrybut **ConstraintName** jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie atrybut **name** elementu **odnośnika w** schemacie zawiera nazwę ograniczenia w **zestawie danych**.|  
|**msdata:UpdateRule**|Jeśli atrybut **UpdateRule** jest określony w **elemencie keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **UpdateRule** w **zestawie danych**. W przeciwnym razie **UpdateRule** Właściwość jest ustawiona na **Kaskada**.|  
|**msdata:Usuń Regułę**|Jeśli atrybut **DeleteRule** jest określony w **elemencie odnośnika w** schemacie, jego wartość jest przypisywana do właściwości ograniczenia **DeleteRule** w **zestawie danych**. W przeciwnym razie **właściwość DeleteRule** jest ustawiona na **Kaskada**.|  
|**msdata:AcceptRejectRule**|Jeśli **atrybut AcceptRejectRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **AcceptRejectRule** w **zestawie danych**. W przeciwnym razie **AcceptRejectRule** Właściwość jest ustawiona na **Brak**.|  
  
 Poniższy przykład zawiera schemat, który określa relacje **klucza** i **odnośnika** między elementem podrzędnym **OrderNumber** elementu **Order** elementu i **OrderNo** element podrzędny **OrderDetail elementu OrderDetail.**  
  
 W przykładzie **OrderNumber** element podrzędny **OrderDetail** element odwołuje się do **OrderNo** klucz element podrzędny Order elementu **Order.**  
  
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
  
 Proces mapowania języka xsd (XSD) tworzy następujący zestaw **danych** z dwiema tabelami:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ponadto zestaw **danych** definiuje następujące ograniczenia:  
  
- Unikatowe ograniczenie w tabeli **Kolejność.**  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Relacja między tabelami **Order** i **OrderDetail.** Właściwość **Nested** jest ustawiona na **False,** ponieważ dwa elementy nie są zagnieżdżone w schemacie.  
  
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
  
- Ograniczenie klucza obcego w tabeli **OrderDetail.**  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
