---
title: "Mapa keyref ograniczeń schematu XML (XSD) do ograniczenia zestawu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ca72292bd2c43fec6f3833d521ddb83c01c32c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapa keyref ograniczeń schematu XML (XSD) do ograniczenia zestawu danych
**Keyref** element służy do ustanawiania łącza między elementami w dokumencie. Jest to podobna do relacji klucza obcego w relacyjnej bazie danych. Jeśli schemat określa **keyref** elementu, element jest konwertowana podczas procesu mapowania schematu do odpowiedniego ograniczenie klucza obcego dla kolumn w tabelach <xref:System.Data.DataSet>. Domyślnie **keyref** element również generuje relacji z **ParentTable**, **ChildTable**, **ParentColumn**i  **ChildColumn** właściwości określony w relacji.  
  
 W poniższej tabeli przedstawiono **msdata** atrybutów, można określić w **keyref** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**MSDATA:ConstraintOnly**|Jeśli **ConstraintOnly = "true"** jest określona w **keyref** elementu w schemacie, ograniczenie zostało utworzone, ale jest tworzona żadna relacja. Jeśli ten atrybut nie jest określony (lub ma ustawioną wartość **False**), zarówno ograniczenie, jak i relacji są tworzone w **zestawu danych**.|  
|**MSDATA:ConstraintName**|Jeśli **ConstraintName** atrybut został określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybutu **keyref** element w schemacie udostępnia Nazwa ograniczenia w **zestawu danych**.|  
|**MSDATA:UpdateRule**|Jeśli **elementu UpdateRule** atrybut został określony w **keyref** element w schemacie, jego wartość jest przypisany do **elementu UpdateRule** właściwości ograniczenia w  **Zestaw danych**. W przeciwnym razie **elementu UpdateRule** właściwość jest ustawiona na **Cascade**.|  
|**MSDATA:DeleteRule**|Jeśli **DeleteRule** atrybut został określony w **keyref** element w schemacie, jego wartość jest przypisany do **DeleteRule** właściwości ograniczenia w  **Zestaw danych**. W przeciwnym razie **DeleteRule** właściwość jest ustawiona na **Cascade**.|  
|**MSDATA:AcceptRejectRule**|Jeśli **AcceptRejectRule** atrybut został określony w **keyref** element w schemacie, jego wartość jest przypisany do **AcceptRejectRule** właściwości ograniczenia w  **Zestaw danych**. W przeciwnym razie **AcceptRejectRule** właściwość jest ustawiona na **Brak**.|  
  
 Poniżej przedstawiono przykład zawierający schemat, który określa **klucza** i **keyref** relacje między **OrderNumber** elementem podrzędnym **kolejności**  elementu i **OrderNo** elementem podrzędnym **OrderDetail** elementu.  
  
 W tym przykładzie **OrderNumber** elementem podrzędnym **OrderDetail** element odwołuje się do **OrderNo** klucza podrzędnego elementu **kolejności**elementu.  
  
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
  
 Proces mapowania schematu XML definition language (XSD) schematu tworzy następujące **DataSet** dwóch tabel:  
  
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
 [Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generowanie relacji zestawu danych na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
