---
title: FALSE — operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027840"
---
# <a name="false-operator-c-reference"></a>FALSE — operator (odwołanie w C#)

Zwraca [bool](bool.md) wartość `true` do wskazywania operand `false` i zwraca `false` inaczej.

Przed C# 2.0 `true` i `false` operatory były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`. Jednak język teraz udostępnia wbudowaną obsługę dla typów wartości null, a w miarę możliwości należy używać tych zamiast przeładowanie `true` i `false` operatorów. Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../programming-guide/nullable-types/index.md).

O wartości null wartości logiczne, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` ponieważ jedną lub obie wartości może mieć wartości null. Masz przeciążenia obu `true` i `false` operatorom oddzielnie poprawnie Obsługa wartości zerowych w wyrażeniu. Poniższy przykład przedstawia sposób przeciążenia i użyj `true` i `false` operatorów.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Typ, który overloads `true` i `false` operatorów można używać do kontrolowania wyrażenie w [Jeśli](if-else.md), [czy](do.md), [podczas](while.md), i [ Aby uzyskać](for.md) instrukcje i [wyrażenia warunkowe](../operators/conditional-operator.md).

Jeśli typ definiuje operator `false`, również muszą definiować operator [true](true.md).

Typem bezpośrednio nie mogą przeciążać operatory logiczne warunkowe [ && ](../operators/conditional-and-operator.md) i [ &#124; &#124; ](../operators/conditional-or-operator.md), ale sam efekt można osiągnąć przez przeładowanie operatorów logicznych regularne operatory i `true` i `false`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../index.md)  
[Przewodnik programowania w języku C#](../../programming-guide/index.md)  
[Słowa kluczowe języka C#](index.md)  
[Operatory języka C#](../operators/index.md)  
[true](true.md)  