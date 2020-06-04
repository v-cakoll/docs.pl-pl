---
title: Odstęp w literałach XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: b3caf7ac052f3fed3fe5427da0cc96bbdd955ea6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360478"
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
> Jeśli `xml:space` atrybut pojawia się w literale elementu XML, kompilator Visual Basic zawiera atrybut w <xref:System.Xml.Linq.XElement> obiekcie, ale dodanie tego atrybutu nie zmienia, jak kompilator traktuje biały znak.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie XML w Visual Basic](creating-xml.md)
