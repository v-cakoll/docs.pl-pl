---
title: Mapowanie klucz ograniczenia schematu XML (XSD) do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b999e6b1d6d73f107b7e1f4cb0d7e14c099a1f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapowanie klucz ograniczenia schematu XML (XSD) do ograniczenia zestawu danych
W schemacie, można określić ograniczenie klucza dla elementu lub atrybutu przy użyciu **klucza** elementu. Element lub atrybut, w którym określono ograniczenie klucza muszą mieć unikatowe wartości w żadnym wystąpieniu schematu, a nie może mieć wartości null.  
  
 Ograniczenie klucza jest podobny do ograniczenia unique, z wyjątkiem tego, czy kolumna, w którym zdefiniowano ograniczenie klucza nie może mieć wartości null.  
  
 W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **klucza** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybutu zawiera wartości nazwy ograniczenia.|  
|**msdata:PrimaryKey**|Jeśli `PrimaryKey="true"` jest obecny, **IsPrimaryKey** ograniczenia właściwości ustawiono **true**, co czyni go po klucz podstawowy. **AllowDBNull** ma ustawioną wartość właściwości column **false**, ponieważ klucze podstawowe nie może mieć wartości null.|  
  
 Podczas konwertowania schematu, w którym określono ograniczenie klucza, proces mapowania tworzy unikatowego ograniczenia tabeli z **AllowDBNull** właściwości column ustawioną **false** dla każdej kolumny w ograniczenia. **IsPrimaryKey** również ustawiono właściwość unikatowego ograniczenia **false** , chyba że określono `msdata:PrimaryKey="true"` na **klucza** elementu. Jest to identyczne unikatowego ograniczenia w schemacie, w którym `PrimaryKey="true"`.  
  
 W poniższym przykładzie schematu **klucza** element określa ograniczenia klucza w **CustomerID** elementu.  
  
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
  
 **Klucza** element określa, że wartości **CustomerID** elementem podrzędnym **klientów** element muszą mieć unikatowe wartości i nie może mieć wartości null. W tłumaczeniu schematu (XSD) języka definicji schematu XML, proces mapowania tworzy poniższej tabeli:  
  
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
  
 W **DataSet** generowany, **IsPrimaryKey** właściwość **UniqueConstraint** ustawiono **true** ponieważ schematu Określa `msdata:PrimaryKey="true"` w **klucza** elementu.  
  
 Wartość **ConstraintName** właściwość **UniqueConstraint** w **DataSet** jest wartością **msdata:ConstraintName** Podany atrybut w **klucza** elementu w schemacie.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
