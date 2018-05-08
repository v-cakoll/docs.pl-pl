---
title: REM — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="rem-statement-visual-basic"></a>REM — Instrukcja (Visual Basic)
Używana do włączenia uwagi wyjaśniające w kodzie źródłowym programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Części  
 `comment`  
 Opcjonalna. Tekst wszelkie komentarze, które chcesz dołączyć. Odstęp jest wymagany między `REM` — słowo kluczowe i `comment`.  
  
## <a name="remarks"></a>Uwagi  
 Możesz też zaznaczyć `REM` instrukcji wyłącznie na wiersz, lub można umieścić w wierszu po instrukcji innego. `REM` Instrukcja musi być ostatnią instrukcją w wierszu. Jeśli wynika z inną instrukcję `REM` musi być oddzielona od tej instrukcji spacją.  
  
 Można użyć pojedynczego cudzysłowu (`'`) zamiast `REM`. Dotyczy to Twojego komentarza następuje innej instrukcji w tym samym wierszu czy samodzielnie znajduje się w wierszu.  
  
> [!NOTE]
>  Nie można kontynuować `REM` instrukcji za pomocą sekwencja kontynuacji wiersza (`_`). Po rozpoczęciu komentarz, kompilator nie bada znaki specjalne znaczenie. Komentarz wielu linii, użyj innego `REM` instrukcji lub symbol komentarza (`'`) w każdym wierszu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia `REM` instrukcja, która jest używana do włączenia uwagi wyjaśniające w programie. Przedstawiono również zamiast używania znak pojedynczego cudzysłowu (`'`) zamiast `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze w kodzie](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
