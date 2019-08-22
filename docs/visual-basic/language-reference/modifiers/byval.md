---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666857"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przenoszona [przez wartość](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), dzięki czemu wywołana procedura lub właściwość nie może zmienić wartości zmiennej bazowej argumentu w wywoływanym kodzie. Jeśli modyfikator nie jest określony, ByVal jest wartością domyślną.

> [!NOTE]
> Ponieważ jest to ustawienie domyślne, nie trzeba jawnie określać `ByVal` słowa kluczowego w sygnaturach metod. Ma ona na celu generowanie kodu zakłócenia i często prowadzi do niedomyślnego `ByRef` słowa kluczowego.

## <a name="remarks"></a>Uwagi
 `ByVal` Modyfikator może być używany w tych kontekstach:

 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje użycie `ByVal` mechanizmu przekazywania parametrów z argumentem typu odwołania. W tym przykładzie argumentem jest `c1`wystąpienie klasy. `Class1` `ByVal`zapobiega zmienianiu podstawowej wartości argumentu `c1`odwołania przez kod w procedurach, ale nie chroni dostępnych pól i `c1`właściwości.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
