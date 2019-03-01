---
title: 'Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 74dff310ccba0bebcf96576d769bf50420ca7397
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971692"
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
