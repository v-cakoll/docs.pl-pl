---
title: Odstęp w literałach XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: f72dcc25b158d793850069e5cc32c3a3c02fad17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939211"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Odstęp w literałach XML (Visual Basic)
Kompilator Visual Basic obejmuje tylko znaczące białe znaki ze literału XML podczas tworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Nieznaczące białe znaki nie są dołączone.  
  
## <a name="significant-and-insignificant-white-space"></a>Znaczący i nieznaczący biały znak  
 Znaki białych znaków w literałach XML są znaczące tylko w trzech obszarach:  
  
- Gdy znajdują się w wartości atrybutu.  
  
- Gdy są częścią zawartości tekstowej elementu, a tekst zawiera również inne znaki.  
  
- Gdy znajdują się w osadzonym wyrażeniu dla zawartości tekstowej elementu.  
  
 W przeciwnym razie kompilator traktuje znaki odstępu jako nieważne i nie uwzględnia następnie w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekcie dla literału.  
  
 Aby uwzględnić nieznaczny biały znak w literale XML, należy użyć osadzonego wyrażenia zawierającego literał ciągu z białym znakiem.  
  
> [!NOTE]
> Jeśli atrybut pojawia się w literale elementu XML, kompilator Visual Basic zawiera atrybut <xref:System.Xml.Linq.XElement> w obiekcie, ale dodanie tego atrybutu nie zmienia, jak kompilator traktuje biały znak. `xml:space`  
  
## <a name="examples"></a>Przykłady  
 Poniższy przykład zawiera dwa elementy XML, zewnętrzne i wewnętrzne. Oba elementy zawierają biały znak w zawartości tekstowej. Biały znak w elemencie zewnętrznym jest nieistotny, ponieważ zawiera tylko białe znaki i element XML. Biały znak w elemencie wewnętrznym jest znaczący, ponieważ zawiera biały znak i tekst.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Po uruchomieniu ten kod wyświetla następujący tekst.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
