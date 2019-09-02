---
title: Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 231f23ccf47f60b902fdd5c66b63fe1a750445f9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203418"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
W schemacie języka definicji schematu XML (XSD) **unikatowy** element określa ograniczenie unikatowości dla elementu lub atrybutu. W procesie tłumaczenia schematu XML na schemat relacyjny, unikatowe ograniczenie określone dla elementu lub atrybutu w schemacie XML jest zamapowane na unikatowe ograniczenie w <xref:System.Data.DataTable> polu w odpowiedniej <xref:System.Data.DataSet> generacji.  
  
 Poniższa tabela zawiera opis atrybutów **msdata** , które można określić w unikatowym elemencie .  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie atrybut **name** zawiera wartość nazwy ograniczenia.|  
|**msdata:PrimaryKey**|Jeśli `PrimaryKey="true"` jest obecny w elemencie **unikatowym** , zostanie utworzone unikatowe ograniczenie z właściwością IsPrimaryKey ustawioną na **wartość true**.|  
  
 W poniższym przykładzie przedstawiono schemat XML, który używa **unikatowego** elementu do określenia ograniczenia unikatowości.  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 **Unikatowy** element w schemacie określa, że dla wszystkich elementów **klientów** w wystąpieniu dokumentu wartość elementu podrzędnego **CustomerID** musi być unikatowa. Podczas kompilowania **zestawu danych**proces mapowania odczytuje ten schemat i generuje poniższą tabelę:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapowania powoduje także utworzenie unikatowego ograniczenia kolumny **CustomerID** , jak pokazano w poniższym **zestawie danych**. (Dla uproszczenia są wyświetlane tylko odpowiednie właściwości.)  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 W wygenerowanym **zestawie danych** Właściwość IsPrimaryKey jest ustawiona na **wartość false** dla ograniczenia UNIQUE. Właściwość **Unique** kolumny wskazuje, że wartości kolumny **CustomerID** muszą być unikatowe (ale mogą być odwołaniem null, jak określono przez właściwość **AllowDBNull** kolumny).  
  
 Jeśli zmodyfikujesz schemat i ustawisz opcjonalną wartość atrybutu **msdata: PrimaryKey** na **true**, w tabeli zostanie utworzone ograniczenie UNIQUE. Właściwość **Column AllowDBNull** jest ustawiona na **false**, a właściwość IsPrimaryKey ograniczenia ma **wartość true**, co sprawia, że kolumna klucza podstawowego zostanie określona jako kolumna.  
  
 Można określić unikatowe ograniczenie kombinacji elementów lub atrybutów w schemacie XML. W poniższym przykładzie pokazano, jak określić, że kombinacja wartości **CustomerID** i **NazwaFirmy** musi być unikatowa dla wszystkich **klientów** w dowolnym wystąpieniu, dodając inny element **xs: Field** w schemacie.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Jest to ograniczenie, które jest tworzone w powstałym **zestawie danych**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
