---
title: Zasady wnioskowania typów prostych
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
ms.openlocfilehash: 17429e77f7764873e607a8feaa62da1cc6e014a4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710235"
---
# <a name="rules-for-inferring-simple-types"></a>Zasady wnioskowania typów prostych
Opisuje sposób, <xref:System.Xml.Schema.XmlSchemaInference> w jaki Klasa wnioskuje typ danych dla atrybutów i elementów.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa wnioskuje typ danych dla atrybutów i elementów jako typy proste. W tej sekcji opisano potencjalne wywnioskowane typy, sposób uzgadniania wielu różnych wartości z pojedynczym typem oraz sposób obsługi atrybutów definiujących `xsi` schemat.  
  
## <a name="inferred-types"></a>Typy wywnioskowane  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa wnioskuje wartości elementów i atrybutów jako typy proste i zawiera atrybut typu w efekcie schemat. Wszystkie typy wywnioskowane to typy proste. Żadne typy podstawowe ani zestawy reguł nie są dołączone jako część wyniku schematu.  
  
 Wartości są badane pojedynczo w miarę ich napotkania w dokumencie XML. Typ jest wnioskowany dla wartości podczas badania. Jeśli typ został wywnioskowany dla atrybutu lub elementu, a napotkasz wartość atrybutu lub elementu, który jest niezgodny z aktualnie wywnioskowanym typem, <xref:System.Xml.Schema.XmlSchemaInference> Klasa promuje typ dla każdego zestawu reguł. Te reguły zostały omówione w sekcji Promocja typu w dalszej części tego tematu.  
  
 Poniższa tabela zawiera listę możliwych wywnioskowanych typów dla zwracanego schematu.  
  
|Typ prosty|Opis|  
|-----------------|-----------------|  
|wartość logiczna|Prawda, FAŁSZ, 0, 1.|  
|byte|Liczby całkowite z zakresu od – 128 do 127.|  
|unsignedByte|Liczby całkowite z zakresu od 0 do 255.|  
|short|Liczby całkowite z zakresu od – 32768 do 32767.|  
|unsignedShort|Liczby całkowite z zakresu od 0 do 65535.|  
|int|Liczby całkowite z zakresu od – 2147483648 do 2147483647.|  
|unsignedInt|Liczby całkowite z zakresu od 0 do 4294967295.|  
|długi|Liczby całkowite z zakresu od – zakresu od do 9223372036854775807.|  
|unsignedLong|Liczby całkowite z zakresu od 0 do 18446744073709551615 są.|  
|liczba całkowita|Skończona liczba cyfr prawdopodobnie poprzedzona znakiem "-".|  
|decimal|Wartości liczbowe, które zawierają od 0 do 28 cyfr dokładności.|  
|float|Liczba miejsc dziesiętnych, po których następuje znak "E" lub "e", a następnie liczba całkowita reprezentująca wykładnik. Wartości dziesiętne mogą należeć do zakresu od-16777216 do 16777216. Wartości wykładnika mogą mieścić się w zakresie od – 149 do 104.<br /><br /> Float pozwala na wartości specjalne reprezentujące nieskończoność i wartości nieliczbowe. Specjalne wartości zmiennoprzecinkowe to: 0,-0, INF,-INF, NaN.|  
|double|Takie same jak zmiennoprzecinkowe z wyjątkiem wartości dziesiętnych mogą należeć do zakresu od-9007199254740992 do 9007199254740992, a wartości wykładnika mogą mieścić się w zakresie od – 1075 do 970.<br /><br /> Wartość Double pozwala na wartości specjalne reprezentujące nieskończoność i wartości nieliczbowe. Specjalne wartości zmiennoprzecinkowe to: 0,-0, INF,-INF, NaN.|  
|czas trwania|Format czasu trwania W3C.|  
|Data i godzina|Format W3C dateTime.|  
|time|Format czasu W3C.|  
|date|Wartości roku są ograniczone od 0001 do 9999.|  
|gYearMonth|Format wieloletniego kalendarza W3C i miesiąca.|  
|ciąg|Co najmniej jeden znak Unicode.|  
  
## <a name="type-promotion"></a>Promocja typu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasa bada wartości atrybutów i elementów po jednym naraz. Po napotkaniu wartości jest wywnioskowany najbardziej restrykcyjny, niepodpisany typ. Jeśli typ został wywnioskowany dla atrybutu lub elementu, a napotkana zostanie nowa wartość, która nie jest zgodna z aktualnie wywnioskowanym typem, wywnioskowany typ zostanie podwyższony do nowego typu, który odnosi się zarówno do aktualnie wywnioskowanego typu, jak i nowej wartości. <xref:System.Xml.Schema.XmlSchemaInference> Klasa uwzględnia poprzednie wartości podczas podwyższania poziomu wywnioskowanego.  
  
 Rozważmy na przykład następujące fragmenty kodu XML z dwóch dokumentów XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Po napotkaniu `attr1` pierwszej wartości typ `attr1` jest wnioskowany na `unsignedByte` podstawie wartości. `12` `attr1` Gdy zostanie napotkana druga, typ zostanie podwyższony do `unsignedShort` na podstawie aktualnie wnioskowanego typu `unsignedByte` i bieżącej wartości. `52344`  
  
 Teraz Rozważmy następujące XML z dwóch dokumentów XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Po napotkaniu `attr2` pierwszej wartości typ `attr2` jest wnioskowany na `unsignedByte` podstawie wartości. `0` Gdy zostanie napotkana `attr2` druga, typ zostanie podwyższony do `string` na podstawie aktualnie wnioskowanego typu `unsignedByte` i bieżącej wartości `true` , ponieważ <xref:System.Xml.Schema.XmlSchemaInference> Klasa rozważa poprzednie wartości podczas podwyższania poziomu wywnioskowanego. Jeśli jednak oba wystąpienia programu `attr2` zostały napotkane w tym samym dokumencie XML, a nie w dwóch różnych dokumentach XML, jak pokazano powyżej `attr2` , zostałyby wywnioskowane jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Zignorowano atrybuty z <https://www.w3.org/2001/XMLSchema-instance> przestrzeni nazw

Poniżej znajdują się atrybuty definiujące schemat, które są ignorowane podczas wnioskowania schematu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xsi:type`|Jeśli element zostanie napotkany z `xsi:type` określonym, `xsi:type` jest ignorowany.|  
|`xsi:nil`|Jeśli wystąpi element z `xsi:nil` atrybutem, jego Deklaracja elementu w wywnioskowanym schemacie ma wartość. `nillable="true"` Element z `xsi:nil` atrybutem ustawionym na `true` nie może mieć elementów podrzędnych.|  
|`xsi:schemaLocation`|Jeśli `xsi:schemaLocation` wystąpi, zostanie zignorowany.|  
|`xsi:noNamespaceSchemaLocation`|Jeśli `xsi:noNamespaceSchemaLocation` wystąpi, zostanie zignorowany.|  
  
## <a name="see-also"></a>Zobacz też

- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
