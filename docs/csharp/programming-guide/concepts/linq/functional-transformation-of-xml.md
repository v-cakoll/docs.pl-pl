---
title: Przekształcanie funkcjonalne kodu XML (C#)
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 2747ee98bd8df1261388270166b353755282ca96
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747210"
---
# <a name="functional-transformation-of-xml-c"></a>Przekształcanie funkcjonalne kodu XML (C#)
W tym temacie omówiono czyste Przekształcanie funkcjonalne podejście modyfikowanie dokumentów XML i zestawiono ze sobą przy użyciu podejścia proceduralnego.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jednym z najbardziej typowych zadań związanych z programista XML jest Przekształcanie XML z jednego kształtu do innego. Kształt dokumentu XML jest strukturę dokumentu, w którym znajdują się następujące:  
  
-   Hierarchia, wyrażone w dokumencie.  
  
-   Nazwy elementów i atrybutów.  
  
-   Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc najbardziej skutecznym sposobem Przekształcanie XML z jednego kształtu do innego jest czyste Przekształcanie funkcjonalne. W tym podejściu zadań programisty podstawowy jest utworzenie przekształcenia, która jest stosowana do całego dokumentu XML (lub jeden lub więcej węzłów ściśle zdefiniowane). Przekształcanie funkcjonalne jest prawdopodobnie najłatwiejsze do kodu (po programistą są zaznajomieni z podejściem), daje najbardziej łatwego w utrzymaniu kod i jest często bardziej oszczędny niż alternatywnych metod.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkcjonalności innowacyjne technologie XML  
 Firma Microsoft oferuje dwie technologie Przekształcanie funkcjonalne do użycia w dokumentach XML: XSLT i LINQ to XML. XSLT jest obsługiwana w <xref:System.Xml.Xsl> zarządzane przestrzeni nazw i w natywnych implementacji COM programu MSXML. Mimo że XSLT jest niezawodne technologii do manipulowania dokumentów XML, wymaga doświadczenia w domenie specjalistyczne, czyli języka XSLT i towarzyszących interfejsów API.  
  
 LINQ to XML udostępnia narzędzia niezbędne do czystych przekształceń funkcjonalnych kodu w ekspresyjny i zaawansowany sposób, w kodzie języka C# lub Visual Basic. Na przykład użyć wiele przykładów w LINQ do XML dokumentacji czystego podejście funkcjonalności. Ponadto [samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczku używamy LINQ to XML w funkcjonalne podejście do manipulowania informacje zawarte w dokumencie programu Microsoft Word.  
  
 Bardziej szczegółowy porównanie LINQ to XML z innymi technologiami XML firmy Microsoft, zobacz [LINQ to XML a. Inne technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT jest zalecanym narzędziem do przekształcenia skoncentrowane na dokument, gdy dokument źródłowy ma strukturę nieregularne. Jednak LINQ to XML można również wykonywać przekształcenia skoncentrowane na dokumencie. Aby uzyskać więcej informacji, zobacz [porady: użycie adnotacji do Przekształcanie drzew LINQ to XML w stylu XSLT (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przekształceń funkcjonalnych (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [LINQ to XML a inne technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
