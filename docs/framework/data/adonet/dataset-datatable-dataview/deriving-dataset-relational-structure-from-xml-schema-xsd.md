---
title: Wyprowadzanie relacyjnej struktury DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 8d11fdbcb973eb3e4b7487eb6aacb28374c4c654
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717945"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Wyprowadzanie relacyjnej struktury DataSet ze schematu XML (XSD)
Ta sekcja zawiera omówienie sposobów schemat relacyjnej `DataSet` została stworzona od do dokumentu schematu języka (XSD) definicji schematu XML. Ogólnie rzecz biorąc, dla każdego `complexType` element podrzędny elementu schematu, tabeli jest generowany w `DataSet`. Struktura tabeli jest określana zgodnie z definicją typu złożonego. Tabele zostały utworzone w `DataSet` najwyższego poziomu elementów w schemacie. Jednak tabeli jest tworzone tylko dla najwyższego poziomu `complexType` elementu po `complexType` element jest zagnieżdżony w innym `complexType` zamierzone, Zapisz zagnieżdżonego elementu, w którym `complexType` element jest mapowany na `DataTable` w ramach `DataSet`.  
  
 Aby uzyskać więcej informacji na temat XSD, zobacz World Wide Web Consortium (W3C) [XML schematu część 0: Elementarz zalecenie](https://www.w3.org/TR/xmlschema-0/), [XML schematu część 1: Zalecenie struktur](https://www.w3.org/TR/xmlschema-1/)i [XML schematu część 2: Typy danych zalecenie](https://www.w3.org/TR/xmlschema-2/).  
  
 W poniższym przykładzie pokazano schematu XML gdzie `customers` jest elementem podrzędnym `MyDataSet` elementu, który jest **DataSet** elementu.  
  
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
  
 W powyższym przykładzie elementu `customers` jest elementem typu złożonego. W związku z tym definicji typu złożonego jest analizowany, a proces mapowania tworzy w poniższej tabeli.  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 Typ danych każdej kolumny w tabeli jest pochodną typu schematu XML odpowiedniego elementu lub atrybutu.  
  
> [!NOTE]
>  Jeśli element `customers` jest prosty typ danych schematu XML, takie jak **całkowitą**, tabela nie jest generowany. Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typy złożone.  
  
 W poniższym schemacie XML **schematu** element ma dwa elementy podrzędne, `InStateCustomers` i `OutOfStateCustomers`.  
  
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
  
 Zarówno `InStateCustomers` i `OutOfStateCustomers` elementy podrzędne są elementami typu złożonego (`customerType`). W związku z tym, proces mapowania generuje dwóch następujących tabelach identyczne w `DataSet`.  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisano elementy schematu XML, używany do tworzenia unikatowych obcych kluczy ograniczeń i `DataSet`.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Opisano elementy schematu XML, używany do tworzenia relacji między kolumnami tabeli w `DataSet`.  
  
 [Relacje i ograniczenia schematu XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 W tym artykule opisano, jak relacje są tworzone niejawnie za pomocą elementów schematu XML do utworzenia ograniczeń `DataSet`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Opisuje sposób ładowania i zachować relacyjnej struktury i danych w `DataSet` jako danych XML.  
  
## <a name="see-also"></a>Zobacz także
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
