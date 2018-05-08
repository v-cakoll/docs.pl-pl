---
title: 'Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 49f3271d41e9e858c6ecafe1dde5330ebff767f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Porady: tworzenie ciągów za pomocą StringBuilder w Visual Basic
Ten przykład tworzy ciąg z dużo mniejszym ciągów za pomocą <xref:System.Text.StringBuilder> klasy. <xref:System.Text.StringBuilder> Klasy jest bardziej efektywne niż `&=` operator łączenie wielu ciągów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągi do tego wystąpienia, a następnie zwraca reprezentacji ciągu.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [&=, operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)  
 [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)  
 [Przykładowe ciągów](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))
