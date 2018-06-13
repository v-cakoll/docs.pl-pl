---
title: Odstęp w literałach XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649753"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Odstęp w literałach XML (Visual Basic)
Kompilator Visual Basic zawiera znaki znaczące białe literał XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Nie są włączane znaków nieznaczne biały znak.  
  
## <a name="significant-and-insignificant-white-space"></a>Znaczące i nieznaczne biały znak  
 Białe znaki w literałach XML są znaczące tylko trzech obszarach:  
  
-   Gdy są one w wartości atrybutu.  
  
-   Gdy są one częścią zawartości tekstowej elementu i tekst zawiera również inne znaki.  
  
-   Gdy są one osadzone wyrażenia dla zawartości tekstowej elementu.  
  
 W przeciwnym razie kompilator traktuje jako nieważny białych znaków i nie obejmuje następnie w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu dla literału.  
  
 Aby uwzględnić nieważny biały znak w literał XML, użyj wyrażenia osadzonego, który zawiera ciąg literału z białą przestrzenią.  
  
> [!NOTE]
>  Jeśli `xml:space` atrybut występuje w literał elementu XML, kompilator Visual Basic zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekt, ale dodanie tego atrybutu nie zmienia sposób kompilator traktuje biały znak.  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład zawiera dwa elementy XML zewnętrznych i wewnętrznych. Oba elementy zawierają biały znak w ich zawartości tekstowej. Biały znak w elemencie zewnętrzne jest nieważny, ponieważ zawiera tylko biały znak i jest elementem XML. Biały znak w elemencie wewnętrzny jest ważna, ponieważ zawiera białe i tekst.  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Podczas uruchamiania, ten kod wyświetla następujący tekst.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
