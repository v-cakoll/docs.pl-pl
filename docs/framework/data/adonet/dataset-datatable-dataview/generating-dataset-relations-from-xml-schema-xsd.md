---
title: Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: fd32d024acca393dcc8241f047a305e763682866
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204858"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)
<xref:System.Data.DataSet>W programie można utworzyć skojarzenie między dwiema lub więcej kolumnami przez utworzenie relacji nadrzędny-podrzędny. Istnieją trzy sposoby reprezentowania relacji **zestawu danych** w schemacie języka definicji schematu XML (XSD):  
  
- Określ zagnieżdżone typy złożone.  
  
- Użyj adnotacji **msdata: Relationship** .  
  
- Określ element **xs: keyref** bez adnotacji **msdata: ConstraintOnly** .  
  
## <a name="nested-complex-types"></a>Zagnieżdżone typy złożone  
 Zagnieżdżone definicje typu złożonego w schemacie wskazują relacje nadrzędny-podrzędny elementów. Poniższy fragment schematu XML pokazuje, że **OrderDetail** jest elementem podrzędnym elementu **Order** .  
  
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
  
 Proces mapowania schematu XML tworzy tabele w **zestawie danych** , które odnoszą się do zagnieżdżonych typów złożonych w schemacie. Tworzy również dodatkowe kolumny, które są używane jako nadrzędne **-** kolumny podrzędne dla wygenerowanych tabel. Należy zauważyć, że **-** te nadrzędne kolumny podrzędne określają relacje, które nie są takie same jak określanie ograniczeń klucza podstawowego/klucza obcego.  
  
## <a name="msdatarelationship-annotation"></a>msdata: adnotacja relacji  
 Adnotacja **msdata: Relationship** pozwala jawnie określić relacje nadrzędny-podrzędny między elementami w schemacie, które nie są zagnieżdżone. Poniższy przykład pokazuje strukturę elementu **Relationship** .  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atrybuty **msdata:** adnotacja relacji identyfikują elementy należące do relacji nadrzędny-podrzędny, a także elementy **ParentKey** i **ChildKey** oraz atrybuty powiązane z relacją. Proces mapowania używa tych informacji do generowania tabel w **zestawie danych** i tworzenia relacji klucz podstawowy/klucz obcy między tymi tabelami.  
  
 Na przykład poniższy fragment schematu określa **kolejność** i **OrderDetail** elementów na tym samym poziomie (niezagnieżdżony). Schemat określa **msdata:** adnotację relacji, która określa relację nadrzędny-podrzędny między tymi dwoma elementami. W takim przypadku należy określić jawną relację przy użyciu adnotacji **msdata: Relationship** .  
  
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
  
 Proces mapowania używa elementu **Relationship** , aby utworzyć relację nadrzędny-podrzędny między kolumną **OrderNumber** w tabeli **Order** i kolumną **OrderNo** w tabeli **OrderDetail** w **zestawie danych**. Proces mapowania określa tylko relację; nie określa ona automatycznie żadnych ograniczeń dotyczących wartości w tych kolumnach, tak jak ograniczenia klucz podstawowy/klucz obcy w relacyjnych bazach danych.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](map-implicit-relations-between-nested-schema-elements.md)  
 Opisuje ograniczenia i relacje, które są niejawnie tworzone w **zestawie danych** podczas napotkania zagnieżdżonych elementów w schemacie XML.  
  
 [Mapowanie relacji określonych dla zagnieżdżonych elementów](map-relations-specified-for-nested-elements.md)  
 Opisuje, jak jawnie ustawić relacje w **zestawie danych** dla zagnieżdżonych elementów w schemacie XML.  
  
 [Określanie relacji między elementami bez zagnieżdżania](specify-relations-between-elements-with-no-nesting.md)  
 Opisuje sposób tworzenia relacji w **zestawie danych** między elementami schematu XML, które nie są zagnieżdżone.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje strukturę relacyjną lub schemat **zestawu danych** , który jest tworzony na podstawie schematu definicji schematu XML (XSD).  
  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Opisuje elementy schematu XML używane do tworzenia ograniczeń unikatowych i obcych kluczy w **zestawie danych**.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
