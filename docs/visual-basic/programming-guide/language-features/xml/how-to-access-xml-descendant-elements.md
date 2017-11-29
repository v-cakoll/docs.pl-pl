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
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Porady: dostęp do elementów podrzędnych XML (Visual Basic)
Ten przykład przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML w tym określonej nazwy, są zawarte w elemencie XML. W szczególności używa `Value` właściwość, aby uzyskać wartość pierwszego elementu w kolekcji `name` zwraca właściwości osi elementu podrzędnego. `name` Właściwości osi elementu podrzędnego pobiera wszystkie elementy o nazwie `name` są zawarte w `contacts` obiektu. W tym przykładzie również używane `phone` właściwości osi elementu podrzędnego można uzyskać dostępu do wszystkich elementów podrzędnych o nazwie `phone` są zawarte w `contacts` obiektu.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System.Xml.Linq> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [Właściwości osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [Właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
