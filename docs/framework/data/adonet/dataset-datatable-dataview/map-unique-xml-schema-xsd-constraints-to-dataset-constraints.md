---
title: Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150847"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
W schemacie języka definicji schematu schematu schematu schematu XSD **unikatowy** element określa ograniczenie unikatowości elementu lub atrybutu. W procesie tłumaczenia schematu XML do schematu relacyjnego unikatowe ograniczenie określone dla elementu lub atrybutu w schemacie XML jest mapowane na unikatowe ograniczenie <xref:System.Data.DataTable> w odpowiednim, <xref:System.Data.DataSet> który jest generowany.  
  
 W poniższej tabeli przedstawiono atrybuty **msdata,** które można określić w elemencie **unikatowym.**  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:Nazwa więzów**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie atrybut **name** zawiera wartość nazwy ograniczenia.|  
|**msdata:Klucz podstawowy**|Jeśli `PrimaryKey="true"` jest obecny w **unikatowy** element, unikatowe ograniczenie jest tworzony z **IsPrimaryKey** właściwość ustawiona na **true**.|  
  
 Poniższy przykład przedstawia schemat XML, który używa **unikatowego** elementu do określenia ograniczenia unikatowości.  
  
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
  
 **Unikatowy** element w schemacie określa, że dla wszystkich **klientów** elementów w wystąpieniu dokumentu wartość CustomerID element **podrzędny** musi być unikatowy. Podczas tworzenia **zestawu danych**proces mapowania odczytuje ten schemat i generuje następującą tabelę:  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapowania tworzy również unikatowe ograniczenie w kolumnie **CustomerID,** jak pokazano w poniższym **zestawie danych**. (Dla uproszczenia wyświetlane są tylko odpowiednie właściwości).  
  
```text  
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
  
 W **dataset,** który jest generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unikatowego. **Unikatowa** właściwość w kolumnie wskazuje, że wartości kolumny **CustomerID** muszą być unikatowe (ale mogą być odwołaniem null, określonym przez **właściwość AllowDBNull** kolumny).  
  
 Jeśli zmodyfikujesz schemat i ustawisz opcjonalną wartość atrybutu **msdata:PrimaryKey** na **True**, w tabeli zostanie utworzone unikatowe ograniczenie. Właściwość kolumny **AllowDBNull** jest ustawiona na **False,** a właściwość **IsPrimaryKey** ograniczenia ustawiona na **True**, dzięki czemu **kolumna CustomerID** jest kolumną klucza podstawowego.  
  
 Można określić unikatowe ograniczenie kombinacji elementów lub atrybutów w schemacie XML. Poniższy przykład pokazuje, jak określić, że **kombinacja CustomerID** i **CompanyName** wartości musi być unikatowa dla wszystkich **klientów** w dowolnym wystąpieniu, dodając inny **xs:field** element w schemacie.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 Jest to ograniczenie utworzone w wynikowym **zestawie danych**.  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Zobacz też

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
