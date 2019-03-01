---
title: 'Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 5cd118ddd196bdf84045ae8b02fe590e5b087e4e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967961"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic
Ten przykład tworzy ciąg z wielu mniejszych ciągów za pomocą <xref:System.Text.StringBuilder> klasy. <xref:System.Text.StringBuilder> Klasy jest bardziej wydajne niż `&=` operator łączenie wielu ciągów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągów do tego wystąpienia, a następnie zwraca jego reprezentację ciągu.  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a>Zobacz także
- [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&=, operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Ciągi](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)
- [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)
