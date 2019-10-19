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
ms.openlocfilehash: 729d0710d65c0cda750061e72309ced527bbcfe7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582057"
---
# <a name="rem-statement-visual-basic"></a>REM — Instrukcja (Visual Basic)
Służy do uwzględnienia uwag objaśniających kod źródłowy programu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Części  
 `comment`  
 Opcjonalny. Tekst komentarza, który ma zostać uwzględniony. Między słowem kluczowym `REM` i `comment` jest wymagana spacja.  
  
## <a name="remarks"></a>Uwagi  
 Można umieścić instrukcję `REM` w wierszu lub można ją umieścić w wierszu po innej instrukcji. Instrukcja `REM` musi być ostatnią instrukcją w wierszu. Jeśli jest ona zgodna z inną instrukcją, `REM` musi być oddzielona od tej instrukcji przez spację.  
  
 Możesz użyć pojedynczego cudzysłowu (`'`), a nie `REM`. Dzieje się tak, gdy komentarz jest podążany za inną instrukcją w tym samym wierszu lub w wierszu.  
  
> [!NOTE]
> Nie można kontynuować instrukcji `REM` przy użyciu sekwencji kontynuacji wiersza (`_`). Po rozpoczęciu komentarza kompilator nie bada znaków pod kątem specjalnego znaczenia. W przypadku komentarza z wieloma wierszami Użyj innej instrukcji `REM` lub symbolu komentarza (`'`) w każdym wierszu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje instrukcję `REM`, która jest używana do dołączania uwag objaśniających do programu. Pokazuje również alternatywę użycia znaku pojedynczego cudzysłowu (`'`), a nie `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Komentarze w kodzie](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
