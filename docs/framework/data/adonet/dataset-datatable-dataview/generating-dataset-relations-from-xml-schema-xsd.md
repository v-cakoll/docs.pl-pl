---
title: Generowanie relacji zestawu danych na podstawie schematu XML (XSD)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>Generowanie relacji zestawu danych na podstawie schematu XML (XSD)
W <xref:System.Data.DataSet>, formularz skojarzenia między co najmniej dwie kolumny przez utworzenie relacji nadrzędny podrzędny. Istnieją trzy sposoby do reprezentowania **DataSet** relacji w ramach schematu schematu XML definition language (XSD):  
  
-   Określ zagnieżdżonych typów złożonych.  
  
-   Użyj **msdata:Relationship** adnotacji.  
  
-   Określ **xs:keyref** bez **msdata:ConstraintOnly** adnotacji.  
  
## <a name="nested-complex-types"></a>Zagnieżdżone typy złożone  
 Definicje typu złożonego zagnieżdżonego w schemacie wskazują relacji nadrzędny podrzędny elementów. Poniższy fragment schematu XML wskazuje, że **OrderDetail** jest elementem podrzędnym **kolejności** elementu.  
  
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
  
 Proces mapowania schematu XML tworzy tabele w **DataSet** odpowiada zagnieżdżone typy złożone w schemacie. Tworzy również dodatkowe kolumny, które są używane jako element nadrzędny**-**kolumn podrzędnych dla wygenerowanego tabel. Należy pamiętać, że te nadrzędnego**-**kolumn podrzędnych Określ relacje, które nie jest taka sama jak określenie ograniczeń klucza podstawowego/klucz obcy.  
  
## <a name="msdatarelationship-annotation"></a>MSDATA:Relationship adnotacji  
 **Msdata:Relationship** adnotacji można jawnie określić relacji nadrzędny podrzędny między elementami, które nie są zagnieżdżone w schemacie. W poniższym przykładzie przedstawiono struktury **relacji** elementu.  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 Atrybuty **msdata:Relationship** adnotacji zidentyfikować elementy uczestniczących w relacji nadrzędny podrzędny, a także jako **elementy parentkey** i **childkey** elementy i atrybuty uczestniczących w relacji. Proces mapowania używa tych informacji do wygenerowania tabel w **DataSet** i utworzyć podstawowy klucz/relacji klucza obcego między tymi tabelami.  
  
 Na przykład poniższy fragment schemat określa **kolejności** i **OrderDetail** elementów na tym samym poziomie (nie było zagnieżdżone). Określa schemat **msdata:Relationship** adnotacji, który określa relacji nadrzędny podrzędny między tymi dwoma elementami. W takim przypadku jawnej relacji należy określić przy użyciu **msdata:Relationship** adnotacji.  
  
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
  
 Proces mapowania **relacji** elementu do utworzenia relacji nadrzędny podrzędny między **OrderNumber** kolumny w **kolejności** tabeli i **OrderNo** kolumny w **OrderDetail** tabeli w **zestawu danych**. Proces mapowania tylko określa relację; nie automatycznie określa żadnych ograniczeń na wartościach w tych kolumn, tak jak podstawowy klucz/ograniczeń klucza obcego w relacyjnych baz danych.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 Opisuje warunki ograniczające i relacje, które są domyślnie tworzone w **DataSet** gdy wystąpi elementów zagnieżdżonych w schemacie XML.  
  
 [Mapowanie relacji określonych dla zagnieżdżonych elementów](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 Opisuje sposób jawnie ustawiona relacji **zestawu danych** dla elementów zagnieżdżonych w schemacie XML.  
  
 [Określanie relacji między elementami bez zagnieżdżania](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 Opisuje sposób tworzenia relacji w **DataSet** między elementami schematu XML, które nie są zagnieżdżone.  
  
### <a name="related-sections"></a>Sekcje pokrewne  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje relacyjne struktury lub schematu z **DataSet** utworzonego ze schematu (XSD) języka definicji schematu XML.  
  
 [Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Zawiera opis elementów schematu XML używany do tworzenia unikatowych obcego klucza ograniczeń i **zestawu danych**.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
