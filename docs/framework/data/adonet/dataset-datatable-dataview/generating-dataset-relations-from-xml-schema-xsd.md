---
title: Generowanie relacji elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 7c73dcec3d23b094436791af6649de83b9eacad9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416355"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generowanie relacji elementu DataSet ze schematu XML (XSD)
W <xref:System.Data.DataSet>, formularza skojarzenia między co najmniej dwóch kolumn, tworząc relację nadrzędny podrzędny. Istnieją trzy sposoby do reprezentowania **DataSet** relacji w ramach schematu języka (XSD) definicji schematu XML:  
  
-   Określ zagnieżdżonych typów złożonych.  
  
-   Użyj **msdata:Relationship** adnotacji.  
  
-   Określ **xs:keyref** bez **msdata:ConstraintOnly** adnotacji.  
  
## <a name="nested-complex-types"></a>Zagnieżdżone typy złożone  
 Definicje zagnieżdżonych typów złożonych w schemacie wskazują relacje nadrzędny podrzędny elementów. Poniższy fragment schematu XML pokazują, że **OrderDetail** jest elementem podrzędnym **kolejności** elementu.  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Proces mapowania schematu XML tworzy tabele w **DataSet** odpowiadające zagnieżdżone typy złożone w schemacie. Tworzy również dodatkowe kolumny, które są używane jako element nadrzędny**-** kolumn podrzędnych dla wygenerowanego tabel. Należy zauważyć, że te nadrzędnego**-** kolumn podrzędnych określa relacje, które nie jest taka sama jak określanie ograniczeń klucza podstawowego/klucza obcego.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship adnotacji  
 **Msdata:Relationship** adnotacji można jawnie określić relacji nadrzędny podrzędny między elementami w schemacie, które nie są osadzone. Poniższy przykład pokazuje strukturę **relacji** elementu.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atrybuty **msdata:Relationship** adnotacji identyfikowania elementów uczestniczących w relacji nadrzędny podrzędny, jak również jako **elementy parentkey** i **childkey** elementy i atrybuty uczestniczących w relacji. Proces mapowania używa tych informacji w celu wygenerowania tabel w **DataSet** i utworzyć podstawowy klucz/relacji klucza obcego między tymi tabelami.  
  
 Na przykład poniższy fragment schemat określa **kolejności** i **OrderDetail** elementów na tym samym poziomie (niezagnieżdżony). Schemat określa **msdata:Relationship** adnotacji, który określa relacji nadrzędny podrzędny między tymi dwoma elementami. W tym przypadku wyraźnej relacji musi być określony przy użyciu **msdata:Relationship** adnotacji.  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 Proces mapowania używa **relacji** elementu do utworzenia relacji nadrzędny podrzędny między **OrderNumber** kolumny w **kolejności** tabeli i **OrderNo** kolumny w **OrderDetail** tabelę **zestawu danych**. Proces mapowania określa tylko relacji; nie automatycznie określa wszelkie ograniczenia na podstawie wartości w tych kolumnach, tak jak podstawowego klucza/ograniczenia klucza obcego w relacyjnych baz danych.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 W tym artykule opisano ograniczenia i relacje, które są tworzone niejawnie w **DataSet** po napotkaniu elementów zagnieżdżonych w schemacie XML.  
  
 [Mapowanie relacji określonych dla zagnieżdżonych elementów](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Opisuje sposób jawnie ustawić relacji między deweloperami rozwiązań **zestawu danych** dla elementów zagnieżdżonych w schematu XML.  
  
 [Określanie relacji między elementami bez zagnieżdżania](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 W tym artykule opisano sposób tworzenia relacji w **DataSet** między elementami schematu XML, które nie są osadzone.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 W tym artykule opisano relacyjnej struktury lub schematu z **DataSet** , jest tworzona na podstawie schematu języka (XSD) definicji schematu XML.  
  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisano elementy schematu XML, używany do tworzenia unikatowych obcych kluczy ograniczeń i **zestawu danych**.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
