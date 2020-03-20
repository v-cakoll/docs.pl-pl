---
title: Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150938"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet
W schemacie można określić ograniczenie klucza dla elementu lub atrybutu przy użyciu elementu **klucza.** Element lub atrybut, na którym określono ograniczenie klucza musi mieć unikatowe wartości w każdym wystąpieniu schematu i nie może mieć wartości null.  
  
 Ograniczenie klucza jest podobne do ograniczenia unikatowego, z tą różnicą, że kolumna, w której zdefiniowano ograniczenie klucza, nie może mieć wartości null.  
  
 W poniższej tabeli przedstawiono atrybuty **msdata,** które można określić w **elemencie klucza.**  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:Nazwa więzów**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie atrybut **name** zawiera wartość nazwy ograniczenia.|  
|**msdata:Klucz podstawowy**|Jeśli `PrimaryKey="true"` jest obecny, **IsPrimaryKey** constraint właściwość jest ustawiona na **true,** co czyni go kluczem podstawowym. Właściwość kolumny **AllowDBNull** jest ustawiona na **false,** ponieważ klucze podstawowe nie mogą mieć wartości null.|  
  
 Podczas konwertowania schematu, w którym określono ograniczenie klucza, proces mapowania tworzy unikatowe ograniczenie w tabeli z właściwość **Kolumny AllowDBNull** **ustawiona** na false dla każdej kolumny w ograniczeniu. **Właściwość IsPrimaryKey** unikatowego ograniczenia jest również ustawiona `msdata:PrimaryKey="true"` na **false,** chyba że określono w elemencie **klucza.** Jest to identyczne z unikatowym ograniczeniem w schemacie, w którym `PrimaryKey="true"`.  
  
 W poniższym przykładzie schematu **element klucza** określa ograniczenie klucza na **CustomerID** elementu.  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 Element **klucza** określa, że wartości **customerID** element podrzędny **CustomerID** elementu Customers element musi mieć unikatowe wartości i nie może mieć wartości null. Podczas tłumaczenia schematu języka XSD (XSD) schemat definicji schematu schematu schematu schematu xsd proces mapowania tworzy następującą tabelę:  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Mapowanie schematu XML tworzy również **uniqueconstraint** w kolumnie **CustomerID,** jak pokazano w poniższej . <xref:System.Data.DataSet> (Dla uproszczenia wyświetlane są tylko odpowiednie właściwości).  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 W **DataSet,** który jest generowany, **IsPrimaryKey** właściwość **UniqueConstraint** jest ustawiona `msdata:PrimaryKey="true"` na **true,** ponieważ schemat określa w **kluczowym** elemencie.  
  
 Wartość właściwości **Nazwana ograniczeń** **uniqueconstraint** w **zestawie danych** jest wartością atrybutu **msdata:ConstraintName** określoną w **kluczowym** elemencie w schemacie.  
  
## <a name="see-also"></a>Zobacz też

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
