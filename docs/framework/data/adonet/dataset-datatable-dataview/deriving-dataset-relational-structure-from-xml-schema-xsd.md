---
title: Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 7599577c4e0f485e336e7f79a6c3bd17f0f0c316
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)
Ta sekcja zawiera omówienie sposobu schemat relacyjny `DataSet` składa się z dokument schematu schematu XML definition language (XSD). Ogólnie rzecz biorąc, dla każdego `complexType` elementem podrzędnym elementu schematu, tabeli jest generowana w `DataSet`. Struktura tabeli jest określany przez definicję typu złożonego. Tabele są tworzone w `DataSet` dla elementów najwyższego poziomu w schemacie. Jednak tabeli jest tworzony tylko dla najwyższego poziomu `complexType` elementu po `complexType` element jest zagnieżdżony w innym `complexType` element, w którym to przypadku zagnieżdżone `complexType` element jest zamapowany na `DataTable` w `DataSet`.  
  
 Aby uzyskać więcej informacji na temat XSD, zobacz część schematu XML sieci World Wide Web konsorcjum W3C 0: zalecenie Elementarz, część 1 schematu XML: zalecenie struktury i część 2 schematu XML: zalecenie typy danych, w lokalizacji [ http://www.w3.org/ ](http://www.w3.org/TR/).  
  
 W poniższym przykładzie pokazano schematu XML gdzie `customers` jest elementem podrzędnym `MyDataSet` element, który jest **DataSet** elementu.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 W powyższym przykładzie element `customers` jest elementem typu złożonego. W związku z tym jest analizowana definicję typu złożonego, a proces mapowania tworzy poniższej tabeli.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Typ danych każdej kolumny w tabeli pochodzi od typu schematu XML odpowiadającego mu elementu lub atrybutu określony.  
  
> [!NOTE]
>  Jeśli element `customers` jest proste schematu XML typu danych, takich jak **całkowitą**, tabela nie zostanie wygenerowany. Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.  
  
 W schemacie XML następujące **schematu** element ma dwa elementy podrzędne elementu `InStateCustomers` i `OutOfStateCustomers`.  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 Zarówno `InStateCustomers` i `OutOfStateCustomers` elementy podrzędne są elementami typu złożonego (`customerType`). W związku z tym, proces mapowania generuje dwóch poniższych tabelach identyczne w `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia unikatowych obcego klucza ograniczeń i `DataSet`.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Zawiera opis elementów schematu XML używany do tworzenia relacji między kolumnami tabeli w `DataSet`.  
  
 [Relacje i ograniczenia schematu XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 W tym artykule opisano, jak relacje są tworzone niejawnie podczas za pomocą elementów schematu XML, aby utworzyć ograniczenia w `DataSet`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Opisuje sposób obciążenia i zachować relacyjne struktury i dane w `DataSet` danych XML.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
