---
title: "Funkcjonalności transformacji XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69cd09a017ab7fbf9fc56a6724abb4cc15b3e1cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functional-transformation-of-xml-visual-basic"></a>Funkcjonalności transformacji XML (Visual Basic)
W tym temacie omówiono podejście czysty przekształcania funkcjonalności do modyfikowania dokumentów XML i zachowanie różni się od jego podejście procedurach.  
  
## <a name="modifying-an-xml-document"></a>Modyfikowanie dokumentu XML  
 Jest jednym z najbardziej typowych zadań dla programisty XML Przekształcanie XML z jednego kształtu do innego. Kształt dokumentu XML jest strukturę dokumentu, który obejmuje następujące elementy:  
  
-   Hierarchia, wyrażone w dokumencie.  
  
-   Nazwy elementów i atrybutów.  
  
-   Typy danych elementów i atrybutów.  
  
 Ogólnie rzecz biorąc najbardziej efektywnym sposobem Przekształcanie XML z jednego kształtu do innego jest czysty transformacji funkcjonalności. Takie podejście zadanie programisty podstawowy jest utworzyć transformację, która jest stosowana do całego dokumentu XML (lub jeden lub więcej węzłów ściśle określonych). Przekształcenie funkcjonalności jest raczej najłatwiejsza do kodu (po programisty jest znany z podejścia), zwraca najbardziej łatwy w obsłudze kodu i jest często bardziej compact niż alternatywnych metod.  
  
### <a name="xml-functional-transformational-technologies"></a>Funkcjonalności technologii Transformational XML  
 Firma Microsoft oferuje dwie technologie przekształcania funkcjonalności do użycia w dokumentach XML: XSLT i LINQ do XML. XSLT jest obsługiwana w <xref:System.Xml.Xsl> zarządzane przestrzeni nazw w implementacji native COM programu MSXML. Mimo że XSLT jest technologią niezawodne do manipulowania dokumentów XML, wymaga doświadczenia w domenie specjalne, czyli języka XSLT i jego obsługi interfejsów API.  
  
 LINQ do XML udostępnia narzędzia niezbędne do przekształcenia funkcjonalności czysty kod w obszerne i wydajny sposób kodem C# lub Visual Basic. Na przykład użyć wiele przykładów w składniku LINQ do XML dokumentacji czysty podejście funkcjonalności. W przypadku [samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczku używamy LINQ do XML w funkcjonalności podejście do manipulowania informacje w dokumencie programu Microsoft Word.  
  
 Bardziej szczegółowy porównanie LINQ do XML z innymi technologiami XML firmy Microsoft, zobacz [LINQ do XML programu vs. Inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 XSLT jest zalecanym narzędziem do przekształcenia zorientowany, gdy dokument źródłowy ma nieprawidłowe strukturę. Jednak LINQ do XML można również wykonywać transformacje skoncentrowane na dokument. Aby uzyskać więcej informacji, zobacz [porady: użycie adnotacji do przekształcania LINQ do XML drzew stylów XSLT (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności czysty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [LINQ do XML programu vs. Inne technologie XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)  
 [LINQ do XML programu vs. Inne technologie XML](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
