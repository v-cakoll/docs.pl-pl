---
title: "Porady: określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e2b0cfa6b1e426b38198581c7d493c8907b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Porady: określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)
<xref:System.Enum.GetValues%2A> i <xref:System.Enum.GetNames%2A> metody pozwalają określić parametry i wartości skojarzone z elementy członkowskie wyliczenia.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Aby określić ciągu skojarzonego z wyliczeniem  
  
-   Użyj <xref:System.Enum.GetNames%2A> metoda pobierania ciągów skojarzonymi z elementami członkowskimi wyliczenia. W tym przykładzie deklaruje wyliczenie `flavorEnum`, następnie używa <xref:System.Enum.GetNames%2A> metodę, aby wyświetlić parametry skojarzone z każdym elemencie członkowskim.  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Porady: odwołuje się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Porady: iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Enum — instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
