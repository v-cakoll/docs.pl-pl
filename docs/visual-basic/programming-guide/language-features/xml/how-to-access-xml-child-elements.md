---
title: "Porady: dostęp do elementów podrzędnych XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Porady: dostęp do elementów podrzędnych XML (Visual Basic)
Ten przykład przedstawia sposób użycia elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, których nazwa określona w elemencie XML. W szczególności używa <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby uzyskać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi podrzędnej. `name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy podrzędne o nazwie `phone` w `contact` obiektu. W tym przykładzie również używane `phone` właściwości osi elementu podrzędnego na dostęp do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contact` obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [Właściwość osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
