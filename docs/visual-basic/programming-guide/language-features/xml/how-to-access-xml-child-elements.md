---
title: 'Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 92ecea2c2e6e117add37b30498f5fb34adfeac6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626660"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)
W tym przykładzie pokazano, jak używać elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, które mają określoną nazwą w elemencie XML. W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi podrzędnej. `name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy podrzędne, o nazwie `phone` w `contact` obiektu. W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego na dostęp do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contact` obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Właściwości osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
