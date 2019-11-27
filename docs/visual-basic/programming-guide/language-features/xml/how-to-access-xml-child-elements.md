---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332340"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Porady: dostęp do elementów podrzędnych XML (Visual Basic)
Ten przykład pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML. W szczególności używa właściwości <xref:System.Xml.Linq.XElement.Value%2A>, aby pobrać wartość pierwszego elementu w kolekcji, która zwraca `name` właściwości osi podrzędnej. Właściwość osi elementu podrzędnego `name` pobiera wszystkie elementy podrzędne o nazwie `phone` w obiekcie `contact`. W tym przykładzie użyta jest również właściwość `phone` osi podrzędnej, aby uzyskać dostęp do wszystkich elementów podrzędnych o nazwach `phone` zawartych w obiekcie `contact`.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do przestrzeni nazw <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Właściwości osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do pliku XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
