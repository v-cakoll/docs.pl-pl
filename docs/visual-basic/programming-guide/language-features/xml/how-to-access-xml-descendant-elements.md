---
title: 'Porady: dostęp do elementów podrzędnych XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 63a094c3c2b20736f0ef6589c76d53b7cc96b29a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332311"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Porady: dostęp do elementów podrzędnych XML (Visual Basic)
Ten przykład pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w elemencie XML. W szczególności używa właściwości `Value`, aby pobrać wartość pierwszego elementu w kolekcji, która zwraca `name` Właściwość osi elementu podrzędnego. Właściwość osi elementu podrzędnego `name` pobiera wszystkie elementy o nazwie `name`, które są zawarte w obiekcie `contacts`. W tym przykładzie używane jest również `phone` Właściwość osi elementu podrzędnego, aby uzyskać dostęp do wszystkich elementów podrzędnych o nazwach `phone` zawartych w obiekcie `contacts`.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do przestrzeni nazw <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Właściwości osi obiektu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do pliku XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
