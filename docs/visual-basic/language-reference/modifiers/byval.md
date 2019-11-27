---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351596"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przenoszona [przez wartość](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), dzięki czemu wywołana procedura lub właściwość nie może zmienić wartości zmiennej bazowej argumentu w wywoływanym kodzie. Jeśli modyfikator nie jest określony, ByVal jest wartością domyślną.

> [!NOTE]
> Ponieważ jest to ustawienie domyślne, nie trzeba jawnie określać słowa kluczowego `ByVal` w sygnaturach metod. Ma ona na celu generowanie kodu zakłócenia i często prowadzi do niedomyślnego `ByRef`go słowa kluczowego.

## <a name="remarks"></a>Uwagi
 Modyfikator `ByVal` może być używany w tych kontekstach:

 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje użycie mechanizmu przekazywania parametrów `ByVal` z argumentem typu odwołania. W tym przykładzie argument jest `c1`, wystąpienie klasy `Class1`. `ByVal` uniemożliwia kod w procedurach zmiany podstawowej wartości argumentu odwołania, `c1`, ale nie chroni dostępnych pól i właściwości `c1`.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
