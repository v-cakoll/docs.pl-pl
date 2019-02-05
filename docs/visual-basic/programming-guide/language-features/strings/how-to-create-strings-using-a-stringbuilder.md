---
title: 'Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: dec1afdbd3ca6c0ba719a95906de8cf6fc7ba378
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738802"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic
Ten przykład tworzy ciąg z wielu mniejszych ciągów za pomocą <xref:System.Text.StringBuilder> klasy. <xref:System.Text.StringBuilder> Klasy jest bardziej wydajne niż `&=` operator łączenie wielu ciągów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągów do tego wystąpienia, a następnie zwraca jego reprezentację ciągu.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&=, operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)
- [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)
