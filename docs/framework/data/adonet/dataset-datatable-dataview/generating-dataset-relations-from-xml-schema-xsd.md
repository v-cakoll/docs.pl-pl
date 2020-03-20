---
title: Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151133"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)
W <xref:System.Data.DataSet>polu , tworzysz skojarzenie między dwiema lub więcej kolumnami, tworząc relację nadrzędny podrzędny. Istnieją trzy sposoby reprezentowania relacji **DataSet** w schemacie języka XSD (XSD) języka schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu:  
  
- Określ zagnieżdżone typy złożone.  
  
- Użyj **adnotacji msdata:Relationship.**  
  
- Określ **xs:keyref** bez **msdata:ConstraintOnly** adnotacji.  
  
## <a name="nested-complex-types"></a>Zagnieżdżone typy złożone  
 Definicje typów złożonych zagnieżdżonych w schemacie wskazują relacje nadrzędny-podrzędny elementów. Poniższy fragment schematu XML pokazuje, że **OrderDetail** jest elementem podrzędnym **elementu Order.**  
  
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
  
 Proces mapowania schematu XML tworzy tabele w **zestawie danych,** które odpowiadają zagnieżdżonych typom złożonym w schemacie. Tworzy również dodatkowe kolumny, które**-** są używane jako nadrzędne kolumny podrzędne dla wygenerowanych tabel. Należy zauważyć,**-** że te nadrzędne kolumny podrzędne określają relacje, które nie są takie same jak określanie ograniczeń klucza podstawowego/klucza obcego.  
  
## <a name="msdatarelationship-annotation"></a>msdata:Adnotacja relacji  
 Adnotacja **msdata:Relationship** umożliwia jawne określenie relacji nadrzędny-podrzędny między elementami w schemacie, które nie są zagnieżdżone. Poniższy przykład przedstawia strukturę **Relationship** element.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 Atrybuty **msdata:Relationship** adnotacji zidentyfikować elementy zaangażowane w relacji nadrzędny podrzędny, a także **parentkey** i **childkey** elementy i atrybuty zaangażowane w relacji. Proces mapowania używa tych informacji do generowania tabel w **zestawie danych** i tworzenia relacji klucz podstawowy/klucz obcy między tymi tabelami.  
  
 Na przykład poniższy fragment schematu określa **Order** i **OrderDetail** elementów na tym samym poziomie (nie zagnieżdżone). Schemat określa **adnotację msdata:Relationship,** która określa relację nadrzędny-podrzędny między tymi dwoma elementami. W takim przypadku jawna relacja musi być określona przy użyciu **adnotacji msdata:Relationship.**  
  
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
  
 Proces mapowania używa elementu **Relacja** do utworzenia relacji nadrzędny-podrzędny między kolumną **OrderNumber** w tabeli **Order** **i OrderNo** w tabeli **OrderDetail** w **zestawie danych**. Proces mapowania określa tylko relację; nie określa automatycznie żadnych ograniczeń wartości w tych kolumnach, podobnie jak ograniczenia klucza podstawowego/klucza obcego w relacyjnych bazach danych.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](map-implicit-relations-between-nested-schema-elements.md)  
 Opisuje ograniczenia i relacje, które są niejawnie tworzone w **zestawie danych,** gdy elementy zagnieżdżone są napotkane w schemacie XML.  
  
 [Mapowanie relacji określonych dla zagnieżdżonych elementów](map-relations-specified-for-nested-elements.md)  
 Opisuje sposób jawnego ustawiania relacji w **zestawie danych** dla elementów zagnieżdżonych w schemacie XML.  
  
 [Określanie relacji między elementami bez zagnieżdżania](specify-relations-between-elements-with-no-nesting.md)  
 W tym artykule opisano sposób tworzenia relacji w **zestawie danych** między elementami schematu XML, które nie są zagnieżdżone.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje strukturę relacyjną lub schemat **zestawu danych** utworzonego na podstawie schematu języka XSD (XSD) schematu definicji schematu schematu XSD.  
  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 W tym artykule opisano elementy schematu XML używane do tworzenia unikatowych i obcych ograniczeń klucza w **zestawie danych**.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie ADO.NET](../ado-net-overview.md)
