---
title: Oczekiwano końca instrukcji
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="end-of-statement-expected"></a>Oczekiwano końca instrukcji
Wykonywanie instrukcji zostało składniowo ukończone, ale dodatkowy element programowania zgodny element kończące instrukcję. Terminator wiersza jest wymagany na końcu każdej instrukcji.
  
 Terminator wiersza dzieli znaki plik źródłowy języka Visual Basic wierszy. Przykłady terminatory wiersza są Unicode karetki zwracanych znaków (& HD), Unicode wysuwu wiersza znak (& HA), a znak Unicode wysuwu wiersza znak powrotu karetki Unicode. Aby uzyskać więcej informacji o wierszu terminatory, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 **Identyfikator błędu:** BC30205
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
1.  Sprawdź, czy dwa różne instrukcje przypadkowo zostały wprowadzone w tym samym wierszu.
  
2.  Wstaw terminator wiersza po elemencie kończące instrukcję.
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
