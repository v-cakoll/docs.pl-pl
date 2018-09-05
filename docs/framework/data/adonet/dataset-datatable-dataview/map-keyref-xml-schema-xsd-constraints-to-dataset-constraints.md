---
title: Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 86bc1961fb23b0b2f98a2849eaabd4eecd65cd64
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533060"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
**Keyref** element umożliwia ustanowienie łączy między elementami w dokumencie. Jest to podobne do relacji klucza obcego w relacyjnej bazie danych. Jeśli schemat określa **keyref** elementu, element jest konwertowany podczas procesu mapowania schematu do odpowiedniego ograniczenia klucza obcego dla kolumn w tabelach <xref:System.Data.DataSet>. Domyślnie **keyref** element generuje również relacji z **ParentTable**, **ChildTable**, **ParentColumn**i  **ChildColumn** właściwości określone w relacji.  
  
 W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **keyref** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Jeśli **ConstraintOnly = "true"** jest określona w **keyref** elementu w schemacie, ograniczenie zostanie utworzony, ale żadna relacja jest tworzony. Jeśli ten atrybut nie jest określony (lub jest ustawiona na **False**), ograniczenia i relacji, które są tworzone w **zestawu danych**.|  
|**msdata:ConstraintName**|Jeśli **ConstraintName** atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybutu **keyref** elementu w schemacie zawiera nazwę ograniczenia w **zestawu danych**.|  
|**msdata:UpdateRule**|Jeśli **elementu UpdateRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **elementu UpdateRule** właściwości ograniczenia w  **Zestaw danych**. W przeciwnym razie **elementu UpdateRule** właściwość jest ustawiona na **Cascade**.|  
|**msdata:DeleteRule**|Jeśli **DeleteRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **DeleteRule** właściwości ograniczenia w  **Zestaw danych**. W przeciwnym razie **DeleteRule** właściwość jest ustawiona na **Cascade**.|  
|**msdata:AcceptRejectRule**|Jeśli **AcceptRejectRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **AcceptRejectRule** ograniczenia właściwości  **Zestaw danych**. W przeciwnym razie **AcceptRejectRule** właściwość jest ustawiona na **Brak**.|  
  
 Poniższy przykład zawiera schemat, który określa **klucz** i **keyref** relacje między **OrderNumber** element podrzędny elementu **zamówienia**  elementu i **OrderNo** element podrzędny elementu **OrderDetail** elementu.  
  
 W tym przykładzie **OrderNumber** element podrzędny elementu **OrderDetail** element odwołuje się do **OrderNo** element podrzędny klucza **kolejności**elementu.  
  
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
  
 Proces mapowania schematu języka (XSD) definicji schematu XML generuje następujące **DataSet** z dwoma tabelami:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ponadto **DataSet** definiuje następujące ograniczenia:  
  
-   Ograniczenia unique wobec **kolejności** tabeli.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Relacja między **kolejności** i **OrderDetail** tabel. **Zagnieżdżone** właściwość jest ustawiona na **False** ponieważ dwa elementy nie są zagnieżdżone w schemacie.  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   Ograniczenie klucza obcego w **OrderDetail** tabeli.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
