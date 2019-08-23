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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957757"
---
# <a name="rem-statement-visual-basic"></a>REM — Instrukcja (Visual Basic)
Służy do uwzględnienia uwag objaśniających kod źródłowy programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Części  
 `comment`  
 Opcjonalna. Tekst komentarza, który ma zostać uwzględniony. Między `REM` słowem kluczowym i `comment`.  
  
## <a name="remarks"></a>Uwagi  
 `REM` Instrukcję można umieścić samodzielnie w wierszu lub można ją umieścić w wierszu po innej instrukcji. `REM` Instrukcja musi być ostatnią instrukcją w wierszu. Jeśli jest ona zgodna z inną instrukcją, `REM` musi być oddzielona od tej instrukcji spacją.  
  
 Można użyć pojedynczego cudzysłowu (`'`) `REM`zamiast. Dzieje się tak, gdy komentarz jest podążany za inną instrukcją w tym samym wierszu lub w wierszu.  
  
> [!NOTE]
> Nie można kontynuować `REM` instrukcji przy użyciu sekwencji kontynuacji wiersza (`_`). Po rozpoczęciu komentarza kompilator nie bada znaków pod kątem specjalnego znaczenia. W przypadku komentarza z wieloma wierszami Użyj `REM` innej instrukcji lub symbolu komentarza`'`() w każdym wierszu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje `REM` instrukcję, która jest używana do dołączania uwag objaśniających do programu. Pokazuje również alternatywę użycia znaku pojedynczego cudzysłowu (`'`) `REM`zamiast.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Komentarze w kodzie](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
