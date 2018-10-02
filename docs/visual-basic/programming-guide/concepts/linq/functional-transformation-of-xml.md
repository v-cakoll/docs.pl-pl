---
title: Przekształcanie funkcjonalne kodu XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 06803feb0fe23ae4afe2237b64bf920f6e229060
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046318"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Przekształcanie funkcjonalne kodu XML (Visual Basic)
W tym temacie omówiono czyste Przekształcanie funkcjonalne podejście modyfikowanie dokumentów XML i zestawiono ze sobą przy użyciu podejścia proceduralnego.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jednym z najbardziej typowych zadań związanych z programista XML jest Przekształcanie XML z jednego kształtu do innego. Kształt dokumentu XML jest strukturę dokumentu, w którym znajdują się następujące:  
  
-   Hierarchia, wyrażone w dokumencie.  
  
-   Nazwy elementów i atrybutów.  
  
-   Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc najbardziej skutecznym sposobem Przekształcanie XML z jednego kształtu do innego jest czyste Przekształcanie funkcjonalne. W tym podejściu zadań programisty podstawowy jest utworzenie przekształcenia, która jest stosowana do całego dokumentu XML (lub jeden lub więcej węzłów ściśle zdefiniowane). Przekształcanie funkcjonalne jest prawdopodobnie najłatwiejsze do kodu (po programistą są zaznajomieni z podejściem), daje najbardziej łatwego w utrzymaniu kod i jest często bardziej oszczędny niż alternatywnych metod.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkcjonalności innowacyjne technologie XML  
 Firma Microsoft oferuje dwie technologie Przekształcanie funkcjonalne do użycia w dokumentach XML: XSLT i LINQ to XML. XSLT jest obsługiwana w <xref:System.Xml.Xsl> zarządzane przestrzeni nazw i w natywnych implementacji COM programu MSXML. Mimo że XSLT jest niezawodne technologii do manipulowania dokumentów XML, wymaga doświadczenia w domenie specjalistyczne, czyli języka XSLT i towarzyszących interfejsów API.  
  
 LINQ to XML udostępnia narzędzia niezbędne do czystych przekształceń funkcjonalnych kodu w ekspresyjny i zaawansowany sposób, w kodzie języka C# lub Visual Basic. Na przykład użyć wiele przykładów w LINQ do XML dokumentacji czystego podejście funkcjonalności. Ponadto [samouczek: manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczku używamy LINQ to XML w funkcjonalne podejście do manipulowania informacje zawarte w dokumencie programu Microsoft Word.  
  
 Bardziej szczegółowy porównanie LINQ to XML z innymi technologiami XML firmy Microsoft, zobacz [LINQ to XML a. Inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT jest zalecanym narzędziem do przekształcenia skoncentrowane na dokument, gdy dokument źródłowy ma strukturę nieregularne. Jednak LINQ to XML można również wykonywać przekształcenia skoncentrowane na dokumencie. Aby uzyskać więcej informacji, zobacz [porady: użycie adnotacji do Przekształcanie drzew LINQ to XML w stylu XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [LINQ to XML a inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
