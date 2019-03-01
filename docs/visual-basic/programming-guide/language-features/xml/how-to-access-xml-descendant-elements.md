---
title: 'Instrukcje: Dostęp do elementów podrzędnych XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 1edbbc052bbf319d91f1f944451312e7d67594ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973863"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Instrukcje: Dostęp do elementów podrzędnych XML (Visual Basic)
W tym przykładzie pokazano, jak dostęp do wszystkich elementów XML, które mają określoną nazwą i znajdujących się w obszarze elementu XML przy użyciu właściwości osi elementu podrzędnego. W szczególności używa `Value` właściwość, aby pobrać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi elementu podrzędnego. `name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy o nazwie `name` są zawarte w `contacts` obiektu. W tym przykładzie również użyto `phone` właściwości osi elementu podrzędnego do dostępu do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contacts` obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [Właściwości osi obiektu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
