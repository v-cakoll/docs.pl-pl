---
title: GoTo — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351085"
---
# <a name="goto-statement"></a>GoTo — Instrukcja
Rozgałęzienia bezwarunkowo do określonego wiersza procedury.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Części  
 `line`  
 Wymagana. Dowolna etykieta wiersza.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `GoTo` może rozgałęziać tylko do wierszy w procedurze, w której występuje. Wiersz musi mieć etykietę linii, do której może odwoływać się `GoTo`. Aby uzyskać więcej informacji, zobacz [instrukcje: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> instrukcje `GoTo` mogą utrudniać odczytywanie i konserwację kodu. Jeśli to możliwe, zamiast tego użyj struktury formantu. Aby uzyskać więcej informacji, zobacz [sterowanie przepływem](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Nie można użyć instrukcji `GoTo` do rozgałęzienia spoza `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, lub `Using`...`End Using` z konstrukcji do etykiety wewnątrz.  
  
## <a name="branching-and-try-constructions"></a>Rozgałęzianie i próba konstrukcji  
 W ramach konstrukcji `Try`...`Catch`...`Finally` zastosowana jest następująca reguła rozgałęziania przy użyciu instrukcji `GoTo`.  
  
|Blok lub region|Rozgałęzianie od zewnątrz|Rozgałęzianie od wewnątrz|  
|---------------------|-------------------------------|-------------------------------|  
|blok `Try`|Tylko z bloku `Catch` tej samej konstrukcji <sup>1</sup>|Tylko poza całością konstrukcji|  
|blok `Catch`|Nigdy niedozwolone|Tylko poza całościową budową lub do bloku `Try` tej samej konstrukcji <sup>1</sup>|  
|blok `Finally`|Nigdy niedozwolone|Nigdy niedozwolone|  
  
 <sup>1</sup> jeśli jedna `Try`...`Catch`...`Finally` konstrukcja jest zagnieżdżona w innym, blok `Catch` może rozgałęzić do bloku `Try` na jego własnym poziomie zagnieżdżenia, ale nie w żadnym innym bloku `Try`. Zagnieżdżona `Try`...`Catch`...`Finally` konstrukcja musi być całkowicie zawarta w `Try` lub `Catch` bloku konstrukcji, w której jest zagnieżdżony.  
  
 Na poniższej ilustracji przedstawiono jedną `Try` konstrukcji zagnieżdżoną w innej. Różne gałęzie między blokami dwóch konstrukcji są wskazywane jako prawidłowe lub nieprawidłowe.  
  
 ![Diagram graficzny rozgałęzień w konstrukcjach try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `GoTo`, aby rozgałęziać etykiety linii w procedurze.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case, instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
