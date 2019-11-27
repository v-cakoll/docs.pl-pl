---
title: 'Porady: określanie ciągu skojarzonego z wartością wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351134"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Porady: określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)
Metody <xref:System.Enum.GetValues%2A> i <xref:System.Enum.GetNames%2A> umożliwiają określenie ciągów i wartości skojarzonych z elementami członkowskimi wyliczenia.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Aby określić ciąg skojarzony z wyliczeniem  
  
- Użyj metody <xref:System.Enum.GetNames%2A>, aby pobrać ciągi skojarzone z elementami członkowskimi wyliczenia. Ten przykład deklaruje Wyliczenie, `flavorEnum`, następnie używa metody <xref:System.Enum.GetNames%2A> do wyświetlania ciągów skojarzonych z poszczególnymi elementami członkowskimi.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Iterowanie przez Wyliczenie w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum, instrukcja](../../../../visual-basic/language-reference/statements/enum-statement.md)
