---
title: nowe ograniczenie — odwołanie w C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 6f6d1b663d03dc9b3adf0e7055dcffacc79d83dc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795342"
---
# <a name="new-constraint-c-reference"></a>New — ograniczenie (odwołanie w C#)

`new` Ograniczenie określa, że argument typu w deklaracji klasy ogólnej musi mieć publiczny Konstruktor bez parametrów. Aby użyć `new` ograniczenia, typ nie może być abstrakcyjny.

Zastosuj `new` ograniczenie do parametru typu, gdy Klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w następującym przykładzie:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

W `new()` przypadku użycia ograniczenia z innymi ograniczeniami należy je określić Last:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Możesz również użyć słowa kluczowego, `new` aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji składowej](new-modifier.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [ograniczenia parametrów typu](~/_csharplang/spec/classes.md#type-parameter-constraints) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy ogólne](../../programming-guide/generics/index.md)
