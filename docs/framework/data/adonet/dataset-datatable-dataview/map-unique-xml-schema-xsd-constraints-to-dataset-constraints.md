---
title: Ograniczenia unikalne schematu XML (XSD) mapy do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5276697ebdc065965d970afc4ac2ef6be61c8f20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Ograniczenia unikalne schematu XML (XSD) mapy do ograniczenia zestawu danych
W schemacie schematu XML definition language (XSD) **unikatowy** element określa ograniczenie unikatowości element lub atrybut. Właśnie tłumaczenie schematu XML na schemat relacyjny, unikatowego ograniczenia określone na element lub atrybut w schemacie XML jest zamapowana do ograniczenia unique w <xref:System.Data.DataTable> w odpowiednich <xref:System.Data.DataSet> generowany.  
  
 W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **unikatowy** elementu.  
  
|Nazwa atrybutu|Opis|  
|--------------------|-----------------|  
|**MSDATA:ConstraintName**|Jeśli ten atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia. W przeciwnym razie **nazwa** atrybutu zawiera wartości nazwy ograniczenia.|  
|**MSDATA:PrimaryKey**|Jeśli `PrimaryKey="true"` znajduje się w **unikatowy** unikatowego ograniczenia elementu, jest tworzony z **IsPrimaryKey** ustawioną właściwość **true**.|  
  
 W poniższym przykładzie przedstawiono schematu XML, który używa **unikatowy** element, aby określić ograniczenie unikatowości.  
  
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
  
 **Unikatowy** elementu w schemacie Określa, że wszystkie **klientów** elementów w dokumencie wystąpienia wartość **CustomerID** element podrzędny musi być unikatowa. W budynku **DataSet**, proces mapowania odczytuje ten schemat i generuje poniższej tabeli:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Proces mapowania tworzy także unikatowego ograniczenia na **CustomerID** kolumny, jak pokazano w poniższym **zestawu danych**. (Dla uproszczenia tylko odpowiednie właściwości są wyświetlane.)  
  
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
  
 W **DataSet** generowany, **IsPrimaryKey** właściwość jest ustawiona na **False** dla ograniczenia unique. **Unikatowy** właściwość kolumna wskazuje, że **CustomerID** wartości kolumny muszą być unikatowe (, ale można je odwołanie o wartości null, określony przez **AllowDBNull** Właściwość kolumny).  
  
 Jeśli zmodyfikujesz schematu i ustawić opcjonalny **msdata:PrimaryKey** wartość do atrybutu **True**, ograniczenia unique jest tworzona w tabeli. **AllowDBNull** ma ustawioną wartość właściwości column **False**i **IsPrimaryKey** właściwości ograniczenia ustawioną **True**, w związku z tym wprowadzania **CustomerID** kolumny kolumna klucza podstawowego.  
  
 Można określić unikatowego ograniczenia na kombinacji elementów lub atrybutów w schemacie XML. W poniższym przykładzie pokazano sposób określić, że kombinację **CustomerID** i **NazwaFirmy** wartości muszą być unikatowe dla wszystkich **klientów** w żadnym wystąpieniu przez dodanie kolejnego **xs:field** elementu w schemacie.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Jest to ograniczenie, która jest tworzona w wynikowym **zestawu danych**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
