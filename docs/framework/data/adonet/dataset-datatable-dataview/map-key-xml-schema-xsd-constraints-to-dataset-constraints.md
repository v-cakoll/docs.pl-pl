---
title: Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 46a980f06198c6f06bb13824c65cfb5309eec154
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189920"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet
W schemacie, można określić ograniczenia klucza dla elementu lub atrybutu przy użyciu **klucz** elementu. Element lub atrybut, w którym określono ograniczenia klucza musi zawierać unikatowe wartości w żadnym wystąpieniu schematu, a nie może mieć wartości null.  
  
 Ograniczenie klucza jest podobny do ograniczenia unique, z tą różnicą, że kolumny, na którym jest zdefiniowana ograniczenie klucza nie może mieć wartości null.  
  
 W poniższej tabeli przedstawiono **msdata** atrybutów, które można określić w **klucz** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**MSDATA:ConstraintName**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybut zawiera wartość Nazwa ograniczenia.|  
|**msdata:PrimaryKey**|Jeśli `PrimaryKey="true"` jest obecny, **IsPrimaryKey** ograniczenie właściwość jest ustawiona na **true**, co czyni go kluczem podstawowym. **AllowDBNull** ustawiono wartość właściwości column **false**, ponieważ klucze podstawowe nie może mieć wartości null.|  
  
 W celu przeliczenia schematu, w którym określono ograniczenia klucza, proces mapowania tworzy ograniczenia unique wobec tabeli z **AllowDBNull** właściwości column ustawioną **false** dla każdej kolumny w ograniczenie. **IsPrimaryKey** właściwości ograniczenia unique jest również ustawiona na **false** , chyba że określono `msdata:PrimaryKey="true"` na **klucz** elementu. To jest taka sama jak unikatowego ograniczenia w schemacie, w którym `PrimaryKey="true"`.  
  
 W poniższym przykładzie schematu **klucz** element określa ograniczenie klucza na **CustomerID** elementu.  
  
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
  
 **Klucz** elementu Określa, że wartości **CustomerID** element podrzędny elementu **klientów** element musi zawierać unikatowe wartości i nie może mieć wartości null. W tłumaczeniu schematu języka (XSD) definicji schematu XML, proces mapowania tworzy poniższej tabeli:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 Tworzy również mapowanie schematu XML **UniqueConstraint** na **CustomerID** kolumny, jak pokazano w poniższym <xref:System.Data.DataSet>. (Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)  
  
```  
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
  
 W **zestawu danych** , jest generowany, **IsPrimaryKey** właściwość **UniqueConstraint** ustawiono **true** ponieważ schematu Określa `msdata:PrimaryKey="true"` w **klucz** elementu.  
  
 Wartość **ConstraintName** właściwość **UniqueConstraint** w **DataSet** jest wartością **msdata:ConstraintName** atrybutu wskazanego w **klucz** elementu w schemacie.  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
