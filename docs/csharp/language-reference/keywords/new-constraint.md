---
title: nowe ograniczenie — C# odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713357"
---
# <a name="new-constraint-c-reference"></a>nowe ograniczenie (C# odwołanie)

Ograniczenie `new` określa, że argument typu w deklaracji klasy ogólnej musi mieć publiczny Konstruktor bez parametrów. Aby użyć ograniczenia `new`, typ nie może być abstrakcyjny.

Zastosuj ograniczenie `new` do parametru typu, gdy Klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w następującym przykładzie:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

W przypadku użycia ograniczenia `new()` z innymi ograniczeniami należy określić wartość Last:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Można również użyć słowa kluczowego `new`, aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji składowej](new-modifier.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [ograniczenia parametrów typu](~/_csharplang/spec/classes.md#type-parameter-constraints) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy ogólne](../../programming-guide/generics/index.md)
