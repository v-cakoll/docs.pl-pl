---
title: FALSE — operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45648928"
---
# <a name="false-operator-c-reference"></a>FALSE — operator (odwołanie w C#)

Zwraca [bool](bool.md) wartość `true` do wskazania, że argument jest `false` i zwraca `false` inaczej.

Przed C# w wersji 2.0 `true` i `false` operatorów były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`. Jednak język teraz udostępnia wbudowaną obsługę typy o wartości zerowalnej i w miarę możliwości należy używać tych zamiast przeciążenia `true` i `false` operatorów. Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/index.md).

Za pomocą wartości logicznych dopuszczającego wartość null, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` , ponieważ co najmniej jeden z wartości może mieć wartości null. Masz oba przeciążenia `true` i `false` operatory oddzielnie, aby poprawnie Obsługa wartości zerowych w wyrażeniu. Poniższy przykład pokazuje, jak przeciążenia i użyj `true` i `false` operatorów.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Typ, który przeciążenia `true` i `false` operatorzy mogą służyć do kontrolowania wyrażenia w [Jeśli](if-else.md), [czy](do.md), [podczas](while.md), i [ Aby uzyskać](for.md) instrukcji i [wyrażenia warunkowe](../operators/conditional-operator.md).

Jeśli typ definiuje operator `false`, również muszą definiować operator [true](true.md).

Typem bezpośrednio nie mogą przeciążać operatory logiczne warunkowe [ && ](../operators/conditional-and-operator.md) i [ &#124; &#124; ](../operators/conditional-or-operator.md), ale taki sam efekt można osiągnąć przez przeciążania operatorów logicznych regularne operatory i `true` i `false`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Operatory języka C#](../operators/index.md)  
- [true](true.md)  