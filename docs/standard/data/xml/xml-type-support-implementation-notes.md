---
title: "XML uwagi dotyczące implementacji pomocy technicznej dla typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e99573fc3a82db7798426172a13a78e10c65636
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xml-type-support-implementation-notes"></a>XML uwagi dotyczące implementacji pomocy technicznej dla typu
W tym temacie opisano niektóre szczegóły implementacji, które mają być znane.  
  
## <a name="list-mappings"></a>Lista mapowań  
 <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type []**, i <xref:System.String> typy są używane do reprezentowania schematu XML definition language (XSD) listy typów.  
  
## <a name="union-mappings"></a>Mapowania Unii  
 Typy Unii są reprezentowane <xref:System.Xml.Schema.XmlAtomicValue> lub <xref:System.String> typu. Typ źródłowy lub docelowy typ muszą więc być zawsze albo <xref:System.String> lub <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> obiekt reprezentuje typ listy Konwertuje obiekt do listy co najmniej jeden obiekt wartości ciągu wejściowego. Jeśli <xref:System.Xml.Schema.XmlSchemaDatatype> reprezentuje typ Unii, a następnie podejmowana jest próba można przeanalizować wartości wejściowej jako typ elementu Członkowskiego Unii. Jeśli próba analizy nie powiedzie się następnie konwersji jest usiłowano następny element członkowski Unii i tak dalej do momentu konwersji zakończy się pomyślnie lub nie ma żadnych typów elementu członkowskiego próby, w którym to przypadku jest zwracany wyjątek.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Różnice między CLR i typów danych XML  
 Poniżej przedstawiono niektóre niezgodności, które mogą wystąpić między typami CLR i typów danych XML i sposób obsługi.  
  
> [!NOTE]
>  `xs` Prefiks jest mapowany na http://www.w3.org/2001/XMLSchema i identyfikator URI przestrzeni nazw.  
  
### <a name="systemtimespan-and-xsduration"></a>Obiekt System.TimeSpan i DURATION  
 `xs:duration` Typu częściowo porządkowania, w tym brak niektórych wartości czasu trwania, które różnią się jednak równoważne. Oznacza to, że dla `xs:duration` typu wartości, takich jak 1 miesiąc (P1M) jest mniejsza niż 32 dni (P32D), przekracza 27 dni (P27D) i jest odpowiednikiem 28, 29 lub 30 dni.  
  
 <xref:System.TimeSpan> Klasa nie obsługuje częściowe porządkowanie. Zamiast tego należy go wybiera określoną liczbę dni do 1 roku i 1 miesiąc; 365 dni i 30 dni odpowiednio.  
  
 Aby uzyskać więcej informacji na temat `xs:duration` typu, zobacz W3C XML schematu część 2: zalecenie typów danych w http://www.w3.org/TR/xmlschema-2/.  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs: Time, typy data gregoriańska i System.DateTime  
 Gdy `xs:time` wartość jest mapowany na <xref:System.DateTime> obiektu, <xref:System.DateTime.MinValue> pole służy do inicjowania właściwości daty <xref:System.DateTime> obiektu (takich jak <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, i <xref:System.DateTime.Day%2A>) do najmniejszego możliwego <xref:System.DateTime> wartość.  
  
 Podobnie wystąpienia `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` i `xs:gMonthDay` również są mapowane na <xref:System.DateTime> obiektu. Nieużywane właściwości <xref:System.DateTime> zainicjowany z obiektu <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
>  Nie należy polegać na <xref:System.DateTime.Year%2A?displayProperty=nameWithType> wartość, gdy zawartość jest typu `xs:gMonthDay`. <xref:System.DateTime.Year%2A?displayProperty=nameWithType> Ma zawsze wartość 1904 w takim przypadku.  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI i System.Uri  
 Gdy wystąpienie klasy `xs:anyURI` że reprezentuje względny identyfikator URI, jest mapowany na <xref:System.Uri>, <xref:System.Uri> obiekt nie ma podstawowego identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa typu do zestawów System.Xml klas](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
