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
ms.openlocfilehash: b25910f5215585914094b7bc4420f537a400934b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968009"
---
# <a name="rem-statement-visual-basic"></a>REM — Instrukcja (Visual Basic)
Używane, aby uwzględnić uwagi wyjaśniające w kodzie źródłowym programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Części  
 `comment`  
 Opcjonalna. Tekst dodatkowe uwagi, które chcesz dołączyć. Obszar jest wymagany między `REM` — słowo kluczowe i `comment`.  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `REM` instrukcji wyłącznie w wierszu, możesz ją umieścić w wierszu po innej instrukcji. `REM` Instrukcja musi być ostatnią instrukcją w wierszu. Jeśli jest zgodna z innej instrukcji `REM` muszą być oddzielone od tej instrukcji spacjami.  
  
 Można użyć pojedynczego cudzysłowu (`'`) zamiast `REM`. Ta zasada obowiązuje, czy Twój komentarz poniżej innej instrukcji w tym samym wierszu lub samodzielnie znajduje się w wierszu.  
  
> [!NOTE]
>  Nie można kontynuować `REM` instrukcji przy użyciu sekwencji kontynuacji wiersza (`_`). Po rozpoczęciu komentarz, kompilator nie analizuje znaki specjalne znaczenie. Komentarz do wielu linii, użyj innego `REM` instrukcji lub symbol komentarza (`'`) w każdym wierszu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `REM` instrukcję, która jest używana do włączenia uwagi wyjaśniające w programie. Pokazuje także alternatywne przy użyciu znaku pojedynczego cudzysłowu (`'`) zamiast `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- [Komentarze w kodzie](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
