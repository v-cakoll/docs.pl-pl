---
title: Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: ef77030b4e847f91fea074b68e223ac622539048
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040106"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
Ta sekcja zawiera omówienie sposobu kompilowania schematu relacyjnego `DataSet` z dokumentu schematu języka definicji schematu XML (XSD). Ogólnie rzecz biorąc dla każdego `complexType` elementu podrzędnego elementu schematu tabela jest generowana w `DataSet`. Struktura tabeli jest określana na podstawie definicji typu złożonego. Tabele są tworzone w `DataSet` dla elementów najwyższego poziomu w schemacie. Jednak tabela jest tworzona tylko dla elementu `complexType` najwyższego poziomu, gdy element `complexType` jest zagnieżdżony wewnątrz innego `complexType` elementu, w którym to przypadku zagnieżdżony element `complexType` jest mapowany na `DataTable` w `DataSet`.  
  
 Aby uzyskać więcej informacji na temat pliku XSD, zobacz temat schemat XML organizacja World Wide Web Consortium (W3C), [część 0: zalecenie podstawowe](https://www.w3.org/TR/xmlschema-0/), [część schematu XML 1: rekomendacja struktur](https://www.w3.org/TR/xmlschema-1/)i [schemat XML schematu część 2: rekomendacja typów](https://www.w3.org/TR/xmlschema-2/)danych.  
  
 Poniższy przykład ilustruje schemat XML, gdzie `customers` jest elementem podrzędnym elementu `MyDataSet`, który jest elementem **DataSet** .  
  
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
  
 W poprzednim przykładzie element `customers` jest elementem typu złożonego. W związku z tym definicja typu złożonego jest analizowana, a proces mapowania tworzy poniższą tabelę.  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 Typ danych każdej kolumny w tabeli pochodzi od typu schematu XML określonego elementu lub atrybutu.  
  
> [!NOTE]
> Jeśli element `customers` ma prostego typu danych schematu XML, takiego jak **Integer**, nie jest generowana żadna tabela. Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.  
  
 W poniższym schemacie XML element **Schema** ma dwa elementy podrzędne, `InStateCustomers` i `OutOfStateCustomers`.  
  
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
  
 Elementy podrzędne `InStateCustomers` i `OutOfStateCustomers` są elementami typu złożonego (`customerType`). W związku z tym proces mapowania generuje następujące dwie identyczne tabele w `DataSet`.  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisuje elementy schematu XML używane do tworzenia ograniczeń unikatowych i obcych kluczy w `DataSet`.  
  
 [Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)  
 Opisuje elementy schematu XML używane do tworzenia relacji między kolumnami tabeli w `DataSet`.  
  
 [Relacje i ograniczenia schematu XML](xml-schema-constraints-and-relationships.md)  
 Opisuje, w jaki sposób relacje są tworzone niejawnie podczas używania elementów schematu XML do tworzenia ograniczeń w `DataSet`.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)  
 Opisuje sposób ładowania i utrwalania relacyjnej struktury i danych w `DataSet` jako dane XML.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../ado-net-overview.md)
