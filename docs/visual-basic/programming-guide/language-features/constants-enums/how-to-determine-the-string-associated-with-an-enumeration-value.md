---
title: 'Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4fa04fa621347ae961975bfb636734e6c9df39fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829216"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)
<xref:System.Enum.GetValues%2A> i <xref:System.Enum.GetNames%2A> metody umożliwiają określenie parametrów i wartości skojarzone z elementów członkowskich wyliczenia.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Aby określić parametry skojarzone z wyliczeniem  
  
-   Użyj <xref:System.Enum.GetNames%2A> metodę, aby pobrać parametry skojarzone z elementów członkowskich wyliczenia. W tym przykładzie deklaruje wyliczenie `flavorEnum`, następnie używa <xref:System.Enum.GetNames%2A> metodę w celu wyświetlenia ciągi skojarzonych z każdym elementem członkowskim.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Instrukcje: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
