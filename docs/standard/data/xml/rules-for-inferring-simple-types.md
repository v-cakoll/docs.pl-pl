---
title: Zasady wnioskowania typów prostych
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd5426de388ba2c7a22d66ce01d56a3139e36e38
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339386"
---
# <a name="rules-for-inferring-simple-types"></a>Zasady wnioskowania typów prostych
W tym artykule opisano sposób, w jaki <xref:System.Xml.Schema.XmlSchemaInference> klasy wnioskuje typ danych dla atrybutów i elementów.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy wnioskuje typ danych dla atrybuty i elementy jako typy proste. W tej sekcji opisano potencjalne typów wykrywany, w wielu różnych wartości są uzgodnione do jednego typu i sposobu definiowania schematu `xsi` atrybutów są obsługiwane.  
  
## <a name="inferred-types"></a>Wywnioskowane typów  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy wnioskuje element i atrybut wartości jako typy proste i obejmuje atrybutu typu Wynikowe schemat. Wszystkie wywnioskować, że typy są typy proste. Nie typów podstawowych lub zestawów reguł są dołączane jako część wynikowe schemat.  
  
 Wartości są badane pojedynczo po ich napotkaniu w dokumencie XML. Typ jest wnioskowany dla wartości w czasie, który jest sprawdzany pod. Jeśli typem została wykryta dla atrybutu lub elementu, a wartość atrybutu lub elementu okaże się, że nie jest zgodny z typem obecnie wykrywany, <xref:System.Xml.Schema.XmlSchemaInference> klasy promuje typ dla każdego zestawu reguł. Te reguły są omówione w sekcji promocji typu w dalszej części tego tematu.  
  
 Poniższa tabela zawiera listę możliwych typów wnioskowany dla wynikowe schemat.  
  
|Typ prosty|Opis|  
|-----------------|-----------------|  
|wartość logiczna|True, false, 0, 1.|  
|byte|Liczby całkowite z zakresu od – 128 do 127.|  
|unsignedByte|Liczby całkowite z zakresu od 0 do 255.|  
|short|Liczby całkowite z zakresu –32768 do 32767.|  
|unsignedShort|Liczby całkowite z zakresu od 0 do 65535.|  
|int|Liczby całkowite z zakresu –2147483648 do 2147483647.|  
|unsignedInt|Liczby całkowite z zakresu od 0, 4294967295.|  
|long|Liczby całkowite z zakresu –9223372036854775808 do 9223372036854775807.|  
|unsignedLong|Liczby całkowite z zakresu od 0 do 18446744073709551615 są.|  
|integer|Skończoną liczbę cyfr, prawdopodobnie z prefiksem "-".|  
|decimal|Wartości liczbowe, które zawierają z zakresu od 0 do 28 cyfr precyzji.|  
|float|Miejsca dziesiętne, opcjonalnie, "E" lub "e", po którym następuje wartość całkowitą reprezentującą wykładnik potęgi. Wartości dziesiętnych może być w zakresie-16777216 do 16777216. Wartości wykładnika mogą być w zakresie –149 do 104.<br /><br /> Float umożliwia specjalnych wartości do reprezentowania nieskończoności i wartości nieliczbowe. Specjalne wartości zmiennoprzecinkowe są: 0, - 0, INF, -INF, NaN.|  
|double|Taka sama jak zmiennoprzecinkową, z wyjątkiem wartości dziesiętnych może być w zakresie-9007199254740992 do 9007199254740992 i wykładnika wartości mogą być w zakresie –1075 do 970.<br /><br /> Umożliwia podwójnej precyzji dla specjalnych wartości do reprezentowania nieskończoności i wartości nieliczbowe. Specjalne wartości zmiennoprzecinkowe są: 0, - 0, INF, -INF, NaN.|  
|czas trwania|Format czasu trwania W3C.|  
|Data i godzina|Format daty/godziny W3C.|  
|czas|Format czasu W3C.|  
|Data|Wartości roku, są ograniczone od 0001 do 9999.|  
|gYearMonth|Format miesiąca i roku gregoriański W3C.|  
|string|Jeden lub więcej znaków Unicode.|  
  
## <a name="type-promotion"></a>Promocja typu  
 <xref:System.Xml.Schema.XmlSchemaInference> Klasy sprawdza, czy wartości atrybutu i elementu jednego naraz. Po napotkaniu wartości jest wnioskowany typ najbardziej restrykcyjne, bez znaku. Jeśli typem została wykryta dla atrybutu lub elementu, a nowa wartość okaże się, że jest niezgodny z aktualnie wnioskowany typ, wnioskowany typ zostanie podwyższony do nowego typu, który dotyczy zarówno obecnie wnioskowany typ, jak i nową wartość. <xref:System.Xml.Schema.XmlSchemaInference> Klasy należy wziąć pod uwagę poprzednie wartości podczas podwyższania poziomu wnioskowany typ.  
  
 Na przykład należy wziąć pod uwagę następujące fragmenty XML z dwóch dokumentów XML:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Po pierwsze `attr1` napotkano wartość typu `attr1` jest wnioskowany jako `unsignedByte` na podstawie wartości `12`. Podczas drugiego `attr1` jest napotkano typ zostanie podwyższony do `unsignedShort` oparte na aktualnie wnioskowany typ `unsignedByte` i bieżącą wartość `52344`.  
  
 Rozważmy następujący kod XML z dwóch dokumentów XML:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Po pierwsze `attr2` napotkano wartość typu `attr2` jest wnioskowany jako `unsignedByte` na podstawie wartości `0`. Podczas drugiego `attr2` jest napotkano typ zostanie podwyższony do `string` oparte na aktualnie wnioskowany typ `unsignedByte` i bieżącą wartość `true` ponieważ <xref:System.Xml.Schema.XmlSchemaInference> klasy należy wziąć pod uwagę poprzednie wartości podczas podwyższania poziomu wnioskowany typ. Jednak jeśli oba wystąpienia elementu `attr2` napotkano w dokumencie XML, a nie w dwóch różnych dokumentów XML, jak pokazano powyżej, `attr2` może wywnioskować jako `boolean`.  
  
### <a name="ignored-attributes-from-the-httpwwww3org2001xmlschema-instance-namespace"></a>Ignorowane atrybuty z http://www.w3.org/2001/XMLSchema-instance Namespace  
 Poniżej przedstawiono definiowania schematu atrybutów, które są ignorowane podczas wnioskowania schematu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xsi:type`|Jeśli element zostanie osiągnięty przy użyciu `xsi:type` określony, `xsi:type` jest ignorowana.|  
|`xsi:nil`|Jeśli element z `xsi:nil` atrybut zostanie osiągnięty, jego deklaracji elementu w schemacie wywnioskowane z wartością `nillable="true"`. Element z `xsi:nil` ustawioną wartość atrybutu `true` nie może mieć elementów podrzędnych.|  
|`xsi:schemaLocation`|Jeśli `xsi:schemaLocation` jest wystąpił, jest ignorowany.|  
|`xsi:noNamespaceSchemaLocation`|Jeśli `xsi:noNamespaceSchemaLocation` jest wystąpił, jest ignorowany.|  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
- [Wnioskowanie schematów na podstawie dokumentów XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
- [Zasady wnioskowania typów węzłów schematu i struktury](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
