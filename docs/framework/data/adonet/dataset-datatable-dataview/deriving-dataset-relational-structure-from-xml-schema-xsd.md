---
title: Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151172"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
Ta sekcja zawiera omówienie sposobu, w `DataSet` jaki schemat relacyjny a jest zbudowany z dokumentu schematu języka XSD (XSD) języka schematu schematu schematu XMD. Ogólnie rzecz biorąc `complexType` dla każdego elementu podrzędnego elementu schematu `DataSet`tabela jest generowana w pliku . Struktura tabeli jest określana przez definicję typu złożonego. Tabele są `DataSet` tworzone w forach elementów najwyższego poziomu w schemacie. Jednak tabela jest tworzona tylko `complexType` dla `complexType` elementu najwyższego poziomu, gdy element jest `complexType` zagnieżdżony `DataTable` wewnątrz `DataSet`innego `complexType` elementu, w którym to przypadku zagnieżdżony element jest mapowany na w obrębie . .  
  
 Aby uzyskać więcej informacji na temat XSD, zobacz World Wide Web Consortium (W3C) [XML Schema Część 0: Primer Zalecenie](https://www.w3.org/TR/xmlschema-0/), [Schemat XML Część 1: Zalecenia struktur](https://www.w3.org/TR/xmlschema-1/)i Schemat [XML Część 2: Datatypes Zalecenie](https://www.w3.org/TR/xmlschema-2/).  
  
 Poniższy przykład pokazuje schemat XML, gdzie `customers` jest `MyDataSet` elementem podrzędnym elementu, który jest **elementem DataSet.**  
  
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
  
 W poprzednim przykładzie element `customers` jest elementem typu złożonego. W związku z tym definicja typu złożonego jest analizowana, a proces mapowania tworzy następującą tabelę.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Typ danych każdej kolumny w tabeli jest pochodną typu schematu XML odpowiedniego określonego elementu lub atrybutu.  
  
> [!NOTE]
> Jeśli element `customers` ma prosty typ danych schematu XML, taki jak **liczba całkowita,** nie jest generowana żadna tabela. Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.  
  
 W poniższym schemacie XML element **Schemat** ma `InStateCustomers` `OutOfStateCustomers`dwa elementy podrzędne i .  
  
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
  
 Zarówno `InStateCustomers` elementy `OutOfStateCustomers` podrzędne, jak i`customerType`elementy podrzędne są złożonymi elementami typu ( ). W związku z tym proces mapowania generuje `DataSet`następujące dwie identyczne tabele w .  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 W tym artykule opisano elementy schematu XML używane `DataSet`do tworzenia unikatowych i obcych ograniczeń klucza w pliku .  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Opisuje elementy schematu XML używane do tworzenia relacji `DataSet`między kolumnami tabel w programie .  
  
 [Relacje i ograniczenia schematu XML](xml-schema-constraints-and-relationships.md)  
 Opisuje, jak relacje są tworzone niejawnie podczas tworzenia ograniczeń `DataSet`przy użyciu elementów schematu XML w programie .  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)  
 Opisuje sposób ładowania i utrwalania relacyjnej struktury i danych w `DataSet` danych XML jako.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie ADO.NET](../ado-net-overview.md)
