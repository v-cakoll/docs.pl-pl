---
title: "REM — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 Opcjonalny. Tekst wszelkie komentarze, które chcesz dołączyć. Odstęp jest wymagany między `REM` — słowo kluczowe i `comment`.  
  
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
 [Porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
