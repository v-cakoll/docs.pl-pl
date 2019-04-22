---
title: Odstęp w literałach XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832761"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Odstęp w literałach XML (Visual Basic)
Kompilator Visual Basic zawiera znaki istotnych białych literał XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Znaki nieważny biały znak nie są włączone.  
  
## <a name="significant-and-insignificant-white-space"></a>Znaczące i nieznaczne biały  
 Białych znaków w literałach XML są znaczące tylko dla trzech obszarach:  
  
-   Gdy są one w wartości atrybutu.  
  
-   Gdy są one częścią zawartości tekstowej elementu i tekst zawiera również inne znaki.  
  
-   Gdy są one osadzone wyrażenia dla zawartości tekstowej elementu.  
  
 W przeciwnym razie kompilator traktuje znaki odstępu jako nieważny i nie dołącza następnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu dla literału.  
  
 Aby dołączyć literał XML nieważny biały znak, należy użyć wyrażenia osadzone zawierającej ciąg literału z białą przestrzenią.  
  
> [!NOTE]
>  Jeśli `xml:space` atrybutu jest wyświetlany w literał elementu XML, kompilator języka Visual Basic zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekt, ale dodanie tego atrybutu nie zmienia się jak kompilator traktuje biały znak.  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład zawiera dwa elementy XML, zewnętrznych i wewnętrznych. Oba te elementy zawierają biały znak w ich zawartości tekstowej. Odstęp w elementu zewnętrznego będzie miała znaczenia, ponieważ zawiera ona tylko białych znaków i elementem XML. Biały znak w elemencie wewnętrzny jest znacząca, ponieważ zawiera ona białych znaków i tekst.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Podczas uruchamiania, ten kod wyświetla następujący tekst.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
