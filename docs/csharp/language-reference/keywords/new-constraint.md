---
title: New — ograniczenie - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401493"
---
# <a name="new-constraint-c-reference"></a>New — ograniczenie (odwołanie w C#)

`new` Ograniczenie Określa, że argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów. Aby użyć `new` ograniczenia, typ nie może być abstrakcyjna.

Zastosuj `new` ograniczenie parametru typu, gdy klasa generyczna tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Można również użyć `new` słowa kluczowego [utworzenia wystąpienia typu](../operators/new-operator.md) lub jako [modyfikator deklaracji elementu członkowskiego](new-modifier.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [ograniczenia parametru typu](~/_csharplang/spec/classes.md#type-parameter-constraints) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy ogólne](../../programming-guide/generics/index.md)
