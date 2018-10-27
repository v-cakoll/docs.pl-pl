---
title: Uwagi dotyczące implementacji pomocy technicznej od typu w XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f786c8f1080d0046889958e8b3bd3165870569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187455"
---
# <a name="xml-type-support-implementation-notes"></a>Uwagi dotyczące implementacji pomocy technicznej od typu w XML
W tym temacie opisano niektóre szczegóły implementacji, które ma pod uwagę.  
  
## <a name="list-mappings"></a>Lista mapowań  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Wpisz []**, i <xref:System.String> typów są używane do reprezentowania typów list języka (XSD) definicji schematu XML.  
  
## <a name="union-mappings"></a>Mapowania Unii  
 Typy Unii są reprezentowane przy użyciu <xref:System.Xml.Schema.XmlAtomicValue> lub <xref:System.String> typu. Typ źródłowy lub docelowy typ w związku z tym zawsze musi być albo <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> obiekt reprezentuje typ listy Konwertuje obiekt ciągu wejściowego wartości do listy co najmniej jeden obiekt. Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ union, a następnie zostanie podjęta próba można przeanalizować wartości wejściowej jako typ elementu Członkowskiego Unii. Jeśli nie powiedzie się próba analizy konwersji jest podejmowana z następny element członkowski Unii i tak dalej aż do konwersji zakończy się pomyślnie lub nie ma żadnych typów elementu członkowskiego do wypróbowania, w którym to przypadku jest zgłaszany wyjątek.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Różnice między środowiska CLR i typów danych XML  
 Poniżej przedstawiono niektóre niezgodności, które mogą wystąpić między typy CLR i typów danych XML i jak są obsługiwane.  
  
> [!NOTE]
> `xs` Prefiks jest zamapowana <https://www.w3.org/2001/XMLSchema> i identyfikator URI przestrzeni nazw.
  
### <a name="systemtimespan-and-xsduration"></a>Obiekt System.TimeSpan i DURATION  
 `xs:duration` Typu jest częściowo uporządkowanych w, istnieją pewne wartości czasu trwania, które różnią się ale równoważne. Oznacza to, że dla `xs:duration` typu wartością, taką jak 1 miesiąc (P1M) jest mniejszy niż 32 dni (P32D), przekracza 27 dni (P27D) i jest to równoważne z 28, 29 lub 30 dni.  
  
 <xref:System.TimeSpan> Klasa nie obsługuje częściowe porządkowanie. Zamiast tego wybiera określoną liczbę dni w przypadku 1 rok i miesiąc; 365 dni lub 30 dni odpowiednio.  
  
 Aby uzyskać więcej informacji na temat `xs:duration` typu, zobacz W3C [XML schematu część 2: zalecenie typy danych](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, typy daty gregoriańskiego i System.DateTime  
 Gdy `xs:time` wartość jest mapowany na <xref:System.DateTime> obiektu, <xref:System.DateTime.MinValue> pole jest używane do zainicjowania właściwości daty <xref:System.DateTime> obiektu (takich jak <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, i <xref:System.DateTime.Day%2A>) do najmniejszej możliwej <xref:System.DateTime> wartość.  
  
 Podobnie, wystąpień `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` i `xs:gMonthDay` również są mapowane na <xref:System.DateTime> obiektu. Nieużywane właściwości <xref:System.DateTime> obiektu są inicjowane na wartość od <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Nie można polegać na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> wartości po wpisaniu zawartość jako `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Ma zawsze wartość 1904 w tym przypadku.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI i System.Uri  
 Jeśli wystąpienie `xs:anyURI` czy reprezentuje względny identyfikator URI, jest mapowane na <xref:System.Uri>, <xref:System.Uri> obiekt nie ma podstawowy identyfikator URI.  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
