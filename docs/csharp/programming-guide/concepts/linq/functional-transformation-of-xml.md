---
title: Transformacja funkcjonalna języka XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 83ecd97f9319027dc50f346abf7a9888b5c23862
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75336796"
---
# <a name="functional-transformation-of-xml-c"></a>Transformacja funkcjonalna języka XML (C#)
W tym temacie omówiono podejście do czystej transformacji funkcjonalnej do modyfikowania dokumentów XML i kontrastuje je z podejściem proceduralnym.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jednym z najczęstszych zadań programisty XML jest przekształcanie języka XML z jednego kształtu do drugiego. Kształt dokumentu XML jest strukturą dokumentu, która zawiera następujące elementy:  
  
- Hierarchia wyrażona w dokumencie.  
  
- Nazwy elementów i atrybutów.  
  
- Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc najbardziej skuteczne podejście do przekształcania XML z jednego kształtu do drugiego jest to, że czystej transformacji funkcjonalnej. W tym podejściu podstawowym zadaniem programisty jest utworzenie transformacji, która jest stosowana do całego dokumentu XML (lub do jednego lub więcej ściśle zdefiniowanych węzłów). Transformacja funkcjonalna jest prawdopodobnie najłatwiejsza do kodu (po programista jest zaznajomiony z podejściem), daje najbardziej konserwacji kodu i jest często bardziej kompaktowy niż alternatywne podejścia.  
  
### <a name="xml-functional-transformational-technologies"></a>Technologie transformacji funkcjonalnej XML  
 Firma Microsoft oferuje dwie technologie transformacji funkcjonalnej do użycia w dokumentach XML: XSLT i LINQ do XML. XSLT jest obsługiwany <xref:System.Xml.Xsl> w zarządzanym obszarze nazw i w natywnej implementacji COM msxml. Chociaż XSLT jest niezawodną technologią do manipulowania dokumentami XML, wymaga specjalistycznej wiedzy w specjalistycznej domenie, a mianowicie w języku XSLT i jego wspierających interfejsach API.  
  
 LINQ do XML zapewnia narzędzia niezbędne do kodowania czystej transformacji funkcjonalnych w sposób ekspresyjny i potężny, w c# lub visual basic kodu. Na przykład wiele przykładów w dokumentacji LINQ do XML używa czystego podejścia funkcjonalnego. Ponadto w [samouczku: Manipulowanie zawartością w samouczku dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) używamy LINQ do XML w funkcjonalnym podejściu do manipulowania informacjami w dokumencie programu Microsoft Word.  
  
 Aby uzyskać pełniejsze porównanie linq z XML z innymi technologiami Microsoft XML, zobacz [LINQ do XML vs. Inne technologie XML](./linq-to-xml-vs-other-xml-technologies.md).  
  
XSLT jest zalecanym narzędziem do przekształceń zorientowanych na dokument, gdy dokument źródłowy ma nieregularną strukturę. Jednak LINQ do XML można również wykonywać przekształcenia zorientowane na dokument. Aby uzyskać więcej informacji, zobacz [Jak używać adnotacji do przekształcania linq do drzew XML w stylu XSLT (C#).](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przemian funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
- [LINQ do XML w porównaniu z innymi technologiami XML](./linq-to-xml-vs-other-xml-technologies.md)
