---
title: Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785376"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet
W schemacie języka (XSD) definicji schematu XML **unikatowy** element określa ograniczenie unikatowości elementu lub atrybutu. W trakcie tłumaczenie schematu XML na schemat relacyjny, unikatowego ograniczenia określone w element lub atrybut w schemacie XML jest mapowany do unikatowego ograniczenia w <xref:System.Data.DataTable> w odpowiednich <xref:System.Data.DataSet> generowany.  
  
 W poniższej tabeli przedstawiono **msdata** atrybutów, które można określić w **unikatowy** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybut zawiera wartość Nazwa ograniczenia.|  
|**msdata:PrimaryKey**|Jeśli `PrimaryKey="true"` znajduje się w **unikatowy** unikatowego ograniczenia elementu jest tworzony z **IsPrimaryKey** właściwością **true**.|  
  
 W poniższym przykładzie przedstawiono schematu XML, który używa **unikatowy** elementu, aby określić ograniczenie unikatowości.  
  
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
  
 **Unikatowy** elementu w schemacie Określa, że dla wszystkich **klientów** elementów w dokumencie wystąpienia, wartość **CustomerID** element podrzędny musi być unikatowa. W budynku **DataSet**, proces mapowania odczytuje ten schemat i generuje poniższej tabeli:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapowania wzrasta, powstaje unikatowego ograniczenia na **CustomerID** kolumny, jak pokazano w poniższym **zestawu danych**. (Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)  
  
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
  
 W **DataSet** , jest generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unique. **Unikatowy** właściwość w kolumnie oznacza, że **CustomerID** wartości kolumn muszą być unikatowe (ale mogą być odwołanie o wartości null, określony przez **AllowDBNull** Właściwości kolumny).  
  
 Jeśli modyfikacji schematu opcjonalnego **msdata:PrimaryKey** wartość do atrybutu **True**, unikatowego ograniczenia jest tworzona w tabeli. **AllowDBNull** ustawiono wartość właściwości column **False**i **IsPrimaryKey** właściwości ograniczenia równa **True**, a w związku z tym **CustomerID** kolumny to kolumna klucza podstawowego.  
  
 Można określić ograniczenia unique na kombinacji elementów lub atrybutów w schemacie XML. Poniższy przykład pokazuje, jak określić, że kombinacji **CustomerID** i **CompanyName** wartości muszą być unikatowe dla wszystkich **klientów** w żadnym wystąpieniu przez Dodawanie innego **xs:field** elementu w schemacie.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Jest to ograniczenie, który jest tworzony w wynikowym **zestawu danych**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
