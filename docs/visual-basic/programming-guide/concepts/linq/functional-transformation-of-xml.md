---
title: Przekształcanie funkcjonalne kodu XML
ms.date: 07/20/2015
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
ms.openlocfilehash: 7e029fd562ae3f221a8aaef40f332a1e3fa896eb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353425"
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Przekształcanie funkcjonalne kodu XML (Visual Basic)
W tym temacie omówiono ścisłe podejście do transformacji funkcjonalnej w celu modyfikowania dokumentów XML i kontrastu z podejściem proceduralnym.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jednym z najbardziej typowych zadań dla programisty XML jest przekształcanie XML z jednego kształtu do drugiego. Kształt dokumentu XML jest strukturą dokumentu, która obejmuje następujące elementy:  
  
- Hierarchia wyrażona w dokumencie.  
  
- Nazwy elementów i atrybutów.  
  
- Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc, najbardziej efektywne podejście do przekształcania kodu XML z jednego kształtu na drugi to czysty przekształcenie funkcjonalne. W ramach tego podejścia podstawowe zadanie programisty polega na utworzeniu transformacji, która jest stosowana do całego dokumentu XML (lub do jednego lub większej liczby ściśle zdefiniowanych węzłów). Przekształcanie funkcjonalne jest raczej najłatwiejszym w kodzie (po zapoznaniu się z podejściem programisty), zapewnia najbardziej łatwość obsługi kod i jest często bardziej zwarty niż alternatywne podejścia.  
  
### <a name="xml-functional-transformational-technologies"></a>Technologie transformacji funkcjonalnej XML  
 Firma Microsoft oferuje dwie funkcjonalne technologie przekształcania do użycia w dokumentach XML: XSLT i LINQ to XML. Język XSLT jest obsługiwany w <xref:System.Xml.Xsl> zarządzanej przestrzeni nazw i w natywnej implementacji COM programu MSXML. Chociaż XSLT jest niezawodną technologią do manipulowania dokumentami XML, wymaga znajomości specjalistycznej domeny, a mianowicie języka XSLT i obsługujących je interfejsów API.  
  
 LINQ to XML udostępnia narzędzia niezbędne do kodu przekształceń czystych funkcjonalnie w sposób wyraźny i zaawansowany, C# w ramach kodu lub Visual Basic. Przykładowo wiele przykładów w dokumentacji LINQ to XML używa czystego podejścia funkcjonalnego. Ponadto w [samouczku: manipulowanie zawartością w samouczku WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) używamy LINQ to XML w celu manipulowania informacjami w dokumencie programu Microsoft Word.  
  
 Aby zapoznać się z bardziej szczegółowym porównaniem LINQ to XML z innymi technologiami Microsoft XML, zobacz [LINQ to XML a inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 Język XSLT jest zalecanym narzędziem dla transformacji skoncentrowanych na dokumentach, gdy dokument źródłowy ma nieregularną strukturę. Jednak LINQ to XML mogą również wykonywać transformacje skoncentrowane na dokumentach. Aby uzyskać więcej informacji, zobacz [jak: używanie adnotacji do przekształcania drzew LINQ to XML w stylu XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [LINQ to XML a inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
