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
ms.openlocfilehash: c4cdafafa6bae3246c0512e28f94fde7e88d230b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373027"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Określa, że argument jest przenoszona [przez wartość](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), dzięki czemu wywołana procedura lub właściwość nie może zmienić wartości zmiennej bazowej argumentu w wywoływanym kodzie. Jeśli modyfikator nie jest określony, ByVal jest wartością domyślną.

> [!NOTE]
> Ponieważ jest to ustawienie domyślne, nie trzeba jawnie określać `ByVal` słowa kluczowego w sygnaturach metod. Ma ona na celu generowanie kodu zakłócenia i często prowadzi do niedomyślnego `ByRef` słowa kluczowego.

## <a name="remarks"></a>Uwagi
 `ByVal`Modyfikator może być używany w tych kontekstach:

 [Declare — Instrukcja](../statements/declare-statement.md)

 [Function, instrukcja](../statements/function-statement.md)
  
 [Operator — Instrukcja](../statements/operator-statement.md)
  
 [Property — Instrukcja](../statements/property-statement.md)
  
 [Sub, instrukcja](../statements/sub-statement.md)

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje użycie `ByVal` mechanizmu przekazywania parametrów z argumentem typu odwołania. W tym przykładzie argumentem jest `c1` wystąpienie klasy `Class1` . `ByVal`zapobiega zmienianiu podstawowej wartości argumentu odwołania przez kod w procedurach, `c1` ale nie chroni dostępnych pól i właściwości `c1` .

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe](../keywords/index.md)
- [Przekazywanie argumentów według wartości i według odwołania](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
