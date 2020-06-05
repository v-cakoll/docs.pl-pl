---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392821"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Porady: dostęp do elementów podrzędnych XML (Visual Basic)
Ten przykład pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML. W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać wartość pierwszego elementu w kolekcji, która `name` zwraca właściwość osi podrzędnej. `name`Właściwość oś podrzędna pobiera wszystkie elementy podrzędne o nazwie `phone` w `contact` obiekcie. Ten przykład używa również `phone` Właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych o nazwie `phone` , które są zawarte w `contact` obiekcie.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Ten przykład wymaga:  
  
- Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [Właściwości osi elementu podrzędnego XML](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwość wartości XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](accessing-xml.md)
- [XML](index.md)
