---
title: 'Porady: określanie ciągu skojarzonego z wartością wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414469"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>Porady: określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)
<xref:System.Enum.GetValues%2A>Metody i <xref:System.Enum.GetNames%2A> umożliwiają określanie ciągów i wartości skojarzonych z elementami członkowskimi wyliczenia.  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>Aby określić ciąg skojarzony z wyliczeniem  
  
- Użyj <xref:System.Enum.GetNames%2A> metody, aby pobrać ciągi skojarzone z elementami członkowskimi wyliczenia. Ten przykład deklaruje Wyliczenie, `flavorEnum` a następnie używa <xref:System.Enum.GetNames%2A> metody do wyświetlania ciągów skojarzonych z poszczególnymi elementami członkowskimi.  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Porady: iterowanie za pomocą wyliczania w Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)
- [Enum, instrukcja](../../../language-reference/statements/enum-statement.md)
