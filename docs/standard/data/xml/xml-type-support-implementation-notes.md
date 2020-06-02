---
title: Obsługiwane typy XML — uwagi dotyczące implementacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 91a685f122ff846217ea7a8677b29df430b65363
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290282"
---
# <a name="xml-type-support-implementation-notes"></a>Obsługiwane typy XML — uwagi dotyczące implementacji
W tym temacie opisano niektóre szczegóły implementacji, które mają być świadome.  
  
## <a name="list-mappings"></a>Mapowania list  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection> ,, <xref:System.Collections.IEnumerable> **Typ []**, i <xref:System.String> typy są używane do reprezentowania typów list języka definicji schematu XML (XSD).  
  
## <a name="union-mappings"></a>Mapowania Unii  
 Typy Unii są reprezentowane przy użyciu <xref:System.Xml.Schema.XmlAtomicValue> <xref:System.String> typu lub. W związku z tym typ źródłowy lub docelowy musi zawsze mieć wartość <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue> .  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> obiekt reprezentuje typ listy, obiekt konwertuje wartość ciągu wejściowego na listę co najmniej jednego obiektu. Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ złożenia, podejmowana jest próba przeanalizowania wartości wejściowej jako typu elementu członkowskiego Unii. Jeśli próba przeanalizowania nie powiedzie się, konwersja zostanie podjęta przy użyciu następnego elementu członkowskiego Unii i tak dalej, aż do chwili, gdy konwersja zakończy się pomyślnie lub nie ma żadnych innych typów elementów członkowskich do wypróbowania. w takim przypadku wyjątek jest zgłaszany.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Różnice między typami danych CLR i XML  
 Poniżej opisano niektóre niezgodności, które mogą wystąpić między typami CLR a typami danych XML i jak są obsługiwane.  
  
> [!NOTE]
> `xs`Prefiks jest mapowany na <https://www.w3.org/2001/XMLSchema> Identyfikator URI i przestrzeń nazw.
  
### <a name="systemtimespan-and-xsduration"></a>Wartość System. TimeSpan i xs: duration  
 `xs:duration`Typ jest częściowo uporządkowany w tym, że istnieją pewne wartości czasu trwania, które są różne, ale równoważne. Oznacza to, że dla `xs:duration` wartości typu, takiej jak 1 miesiąc (P1M) jest mniejsza niż 32 dni (P32D), większa niż 27 dni (P27D) i równa 28, 29 lub 30 dni.  
  
 <xref:System.TimeSpan>Klasa nie obsługuje tego porządku częściowego. Zamiast tego wybiera określoną liczbę dni przez 1 rok i 1 miesiąc; odpowiednio 365 dni i 30 dni.  
  
 Aby uzyskać więcej informacji na temat `xs:duration` typu, zobacz [część 2 W3C XML schematu: rekomendacja typów](https://www.w3.org/TR/xmlschema-2/)danych.
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>XS: godzina, typy dat gregoriańskich i system. DateTime  
 Gdy `xs:time` wartość jest zmapowana do <xref:System.DateTime> obiektu, <xref:System.DateTime.MinValue> pole jest używane do inicjowania właściwości daty <xref:System.DateTime> obiektu (takich jak <xref:System.DateTime.Year%2A> , <xref:System.DateTime.Month%2A> i <xref:System.DateTime.Day%2A> ) do najmniejszej możliwej <xref:System.DateTime> wartości.  
  
 Podobnie wystąpienia,, `xs:gMonth` `xs:gDay` `xs:gYear` `xs:gYearMonth` i `xs:gMonthDay` są również mapowane na <xref:System.DateTime> obiekt. Nieużywane właściwości <xref:System.DateTime> obiektu są inicjowane do tych z <xref:System.DateTime.MinValue> .  
  
> [!NOTE]
> Nie można polegać na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> wartości, gdy zawartość jest wpisana jako `xs:gMonthDay` . <xref:System.DateTime.Year%2A?displayProperty=nameWithType>Wartość jest zawsze ustawiona na 1904 w tym przypadku.  
  
### <a name="xsanyuri-and-systemuri"></a>XS: anyURI i system. URI  
 Gdy wystąpienie `xs:anyURI` reprezentujące względny identyfikator URI jest zamapowane na <xref:System.Uri> <xref:System.Uri> obiekt, nie ma podstawowego identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa typu w ramach klas zestawu System.Xml](type-support-in-the-system-xml-classes.md)
