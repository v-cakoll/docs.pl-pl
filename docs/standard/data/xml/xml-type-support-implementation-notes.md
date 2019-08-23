---
title: Obsługiwane typy XML — uwagi dotyczące implementacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 817d48e15f3a1d370e1953ca9c9aa8e10baa7f29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916033"
---
# <a name="xml-type-support-implementation-notes"></a>Obsługiwane typy XML — uwagi dotyczące implementacji
W tym temacie opisano niektóre szczegóły implementacji, które mają być świadome.  
  
## <a name="list-mappings"></a>Mapowania list  
 <xref:System.Collections.IList>, ,<xref:System.Collections.ICollection> <xref:System.String>,Typ **[]** , i typy są używane do reprezentowania typów list języka definicji schematu XML (XSD). <xref:System.Collections.IEnumerable>  
  
## <a name="union-mappings"></a>Mapowania Unii  
 Typy Unii są reprezentowane przy użyciu <xref:System.Xml.Schema.XmlAtomicValue> typu <xref:System.String> lub. W związku z tym typ źródłowy lub docelowy musi zawsze mieć wartość <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 <xref:System.Xml.Schema.XmlSchemaDatatype> Jeśli obiekt reprezentuje typ listy, obiekt konwertuje wartość ciągu wejściowego na listę co najmniej jednego obiektu. <xref:System.Xml.Schema.XmlSchemaDatatype> Jeśli reprezentuje typ złożenia, podejmowana jest próba przeanalizowania wartości wejściowej jako typu elementu członkowskiego Unii. Jeśli próba przeanalizowania nie powiedzie się, konwersja zostanie podjęta przy użyciu następnego elementu członkowskiego Unii i tak dalej, aż do chwili, gdy konwersja zakończy się pomyślnie lub nie ma żadnych innych typów elementów członkowskich do wypróbowania. w takim przypadku wyjątek jest zgłaszany.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Różnice między typami danych CLR i XML  
 Poniżej opisano niektóre niezgodności, które mogą wystąpić między typami CLR a typami danych XML i jak są obsługiwane.  
  
> [!NOTE]
> Prefiks jest mapowany <https://www.w3.org/2001/XMLSchema> na identyfikator URI i przestrzeń nazw. `xs`
  
### <a name="systemtimespan-and-xsduration"></a>Wartość System. TimeSpan i xs: duration  
 `xs:duration` Typ jest częściowo uporządkowany w tym, że istnieją pewne wartości czasu trwania, które są różne, ale równoważne. Oznacza to, że dla `xs:duration` wartości typu, takiej jak 1 miesiąc (P1M) jest mniejsza niż 32 dni (P32D), większa niż 27 dni (P27D) i równa 28, 29 lub 30 dni.  
  
 <xref:System.TimeSpan> Klasa nie obsługuje tego porządku częściowego. Zamiast tego wybiera określoną liczbę dni przez 1 rok i 1 miesiąc; odpowiednio 365 dni i 30 dni.  
  
 Aby uzyskać więcej informacji na `xs:duration` temat typu, zobacz część [2 W3C XML schematu: Zalecenie](https://www.w3.org/TR/xmlschema-2/)dotyczące typów danych.
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>XS: godzina, typy dat gregoriańskich i system. DateTime  
 <xref:System.DateTime> <xref:System.DateTime.Day%2A> <xref:System.DateTime.Year%2A> <xref:System.DateTime.Month%2A>Gdy wartość jest zmapowana <xref:System.DateTime> do obiektu, <xref:System.DateTime.MinValue> pole jest używane do inicjowania właściwości daty obiektu (takich jak, i) do najmniejszej możliwej `xs:time` <xref:System.DateTime> wartość.  
  
 Podobnie `xs:gMonth`wystąpienia `xs:gDay`, ,i`xs:gMonthDay`są również mapowane na<xref:System.DateTime> obiekt. `xs:gYear` `xs:gYearMonth` Nieużywane właściwości <xref:System.DateTime> obiektu są inicjowane do tych z <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
> Nie można polegać na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> wartości, gdy zawartość jest wpisana jako `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Wartość jest zawsze ustawiona na 1904 w tym przypadku.  
  
### <a name="xsanyuri-and-systemuri"></a>XS: anyURI i system. URI  
 Gdy wystąpienie `xs:anyURI` reprezentujące względny identyfikator URI jest zamapowane <xref:System.Uri>na <xref:System.Uri> obiekt, nie ma podstawowego identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
