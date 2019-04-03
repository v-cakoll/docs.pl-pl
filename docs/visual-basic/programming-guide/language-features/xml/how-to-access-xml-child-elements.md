---
title: 'Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: cd1b0db5305c7879d89cfdfff6cd458d6dea14f4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836821"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Instrukcje: Elementów podrzędnych XML dostępu (Visual Basic)
W tym przykładzie pokazano, jak używać elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, które mają określoną nazwą w elemencie XML. W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi podrzędnej. `name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy podrzędne, o nazwie `phone` w `contact` obiektu. W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego na dostęp do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contact` obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Właściwości osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
