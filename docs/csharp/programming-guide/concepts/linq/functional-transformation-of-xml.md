---
title: Przekształcenie funkcjonalne XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 3c563c5dde1543c6ede53de0a9bb627f34108eaf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594303"
---
# <a name="functional-transformation-of-xml-c"></a>Przekształcenie funkcjonalne XML (C#)
W tym temacie omówiono ścisłe podejście do transformacji funkcjonalnej w celu modyfikowania dokumentów XML i kontrastu z podejściem proceduralnym.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jednym z najbardziej typowych zadań dla programisty XML jest przekształcanie XML z jednego kształtu do drugiego. Kształt dokumentu XML jest strukturą dokumentu, która obejmuje następujące elementy:  
  
- Hierarchia wyrażona w dokumencie.  
  
- Nazwy elementów i atrybutów.  
  
- Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc, najbardziej efektywne podejście do przekształcania kodu XML z jednego kształtu na drugi to czysty przekształcenie funkcjonalne. W ramach tego podejścia podstawowe zadanie programisty polega na utworzeniu transformacji, która jest stosowana do całego dokumentu XML (lub do jednego lub większej liczby ściśle zdefiniowanych węzłów). Przekształcanie funkcjonalne jest raczej najłatwiejszym w kodzie (po zapoznaniu się z podejściem programisty), zapewnia najbardziej łatwość obsługi kod i jest często bardziej zwarty niż alternatywne podejścia.  
  
### <a name="xml-functional-transformational-technologies"></a>Technologie transformacji funkcjonalnej XML  
 Firma Microsoft oferuje dwie funkcjonalne technologie przekształcania do użycia w dokumentach XML: XSLT i LINQ to XML. Język XSLT jest obsługiwany w <xref:System.Xml.Xsl> zarządzanej przestrzeni nazw i natywnej implementacji COM programu MSXML. Chociaż XSLT jest niezawodną technologią do manipulowania dokumentami XML, wymaga znajomości specjalistycznej domeny, a mianowicie języka XSLT i obsługujących je interfejsów API.  
  
 LINQ to XML udostępnia narzędzia niezbędne do kodu przekształceń czystych funkcjonalnie w sposób wyraźny i zaawansowany, C# w ramach kodu lub Visual Basic. Przykładowo wiele przykładów w dokumentacji LINQ to XML używa czystego podejścia funkcjonalnego. Ponadto w [samouczku: Manipulowanie zawartością w samouczku WordprocessingML DocumentC#(](./shape-of-wordprocessingml-documents.md) ), używamy LINQ to XML w funkcjonalne podejścia do manipulowania informacjami w dokumencie programu Microsoft Word.  
  
 Aby zapoznać się z bardziej szczegółowym porównaniem LINQ to XML z innymi technologiami [Microsoft XML, zobacz LINQ to XML a. Inne technologie](./linq-to-xml-vs-other-xml-technologies.md)XML.  
  
 Język XSLT jest zalecanym narzędziem dla transformacji skoncentrowanych na dokumentach, gdy dokument źródłowy ma nieregularną strukturę. Jednak LINQ to XML mogą również wykonywać transformacje skoncentrowane na dokumentach. Aby uzyskać więcej informacji, zobacz [jak: Przekształć drzewa LINQ to XML w stylu XSLT (C#)](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)przy użyciu adnotacji.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ to XML a inne technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
