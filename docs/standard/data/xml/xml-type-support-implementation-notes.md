---
title: Obsługiwane typy XML — uwagi dotyczące implementacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 40ab0f746ef82ccd195fc6b873f5c8edb255f868
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709871"
---
# <a name="xml-type-support-implementation-notes"></a>Obsługiwane typy XML — uwagi dotyczące implementacji
W tym temacie opisano niektóre szczegóły implementacji, które mają być świadome.  
  
## <a name="list-mappings"></a>Mapowania list  
 Typy <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []** i <xref:System.String> są używane do reprezentowania typów list języka XSD (XML Schema Definition Language).  
  
## <a name="union-mappings"></a>Mapowania Unii  
 Typy Unii są reprezentowane przy użyciu typu <xref:System.Xml.Schema.XmlAtomicValue> lub <xref:System.String>. W związku z tym typ źródła lub typ docelowy muszą być zawsze <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Jeśli obiekt <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ listy, obiekt konwertuje wartość ciągu wejściowego na listę co najmniej jednego obiektu. Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ złożenia, podejmowana jest próba przeanalizowania wartości wejściowej jako typu elementu członkowskiego Unii. Jeśli próba przeanalizowania nie powiedzie się, konwersja zostanie podjęta przy użyciu następnego elementu członkowskiego Unii i tak dalej, aż do chwili, gdy konwersja zakończy się pomyślnie lub nie ma żadnych innych typów elementów członkowskich do wypróbowania. w takim przypadku wyjątek jest zgłaszany.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Różnice między typami danych CLR i XML  
 Poniżej opisano niektóre niezgodności, które mogą wystąpić między typami CLR a typami danych XML i jak są obsługiwane.  
  
> [!NOTE]
> Prefiks `xs` jest mapowany na <https://www.w3.org/2001/XMLSchema> i identyfikator URI przestrzeni nazw.
  
### <a name="systemtimespan-and-xsduration"></a>Wartość System. TimeSpan i xs: duration  
 Typ `xs:duration` jest częściowo uporządkowany w taki sposób, że istnieją pewne wartości czasu trwania, które są różne, ale równoważne. Oznacza to, że dla wartości typu `xs:duration`, takiej jak 1 miesiąc (P1M) jest mniejsza niż 32 dni (P32D), większa niż 27 dni (P27D) i równa 28, 29 lub 30 dni.  
  
 Klasa <xref:System.TimeSpan> nie obsługuje tego porządku częściowego. Zamiast tego wybiera określoną liczbę dni przez 1 rok i 1 miesiąc; odpowiednio 365 dni i 30 dni.  
  
 Aby uzyskać więcej informacji na temat typu `xs:duration`, zobacz [część 2 W3C XML schematu: rekomendacja typów](https://www.w3.org/TR/xmlschema-2/)danych.
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>XS: godzina, typy dat gregoriańskich i system. DateTime  
 Gdy `xs:time` wartość jest zamapowana do obiektu <xref:System.DateTime>, pole <xref:System.DateTime.MinValue> służy do inicjowania właściwości daty obiektu <xref:System.DateTime> (takich jak <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>i <xref:System.DateTime.Day%2A>) do najmniejszej możliwej wartości <xref:System.DateTime>.  
  
 Podobnie wystąpienia `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` i `xs:gMonthDay` są również mapowane na obiekt <xref:System.DateTime>. Nieużywane właściwości obiektu <xref:System.DateTime> są inicjowane dla tych z <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
> Nie można polegać na wartości <xref:System.DateTime.Year%2A?displayProperty=nameWithType>, gdy zawartość jest wpisana jako `xs:gMonthDay`. Wartość <xref:System.DateTime.Year%2A?displayProperty=nameWithType> jest zawsze ustawiona na 1904 w tym przypadku.  
  
### <a name="xsanyuri-and-systemuri"></a>XS: anyURI i system. URI  
 Gdy wystąpienie `xs:anyURI` reprezentujące względny identyfikator URI jest zamapowane na <xref:System.Uri>, obiekt <xref:System.Uri> nie ma podstawowego identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
