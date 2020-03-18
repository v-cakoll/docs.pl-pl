---
title: nowe ograniczenie — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713357"
---
# <a name="new-constraint-c-reference"></a>nowe ograniczenie (odwołanie do języka C#)

Ograniczenie `new` określa, że argument typu w deklaracji klasy ogólnej musi mieć konstruktora public parameterless. Aby użyć `new` ograniczenia, typ nie może być abstrakcyjny.

Zastosuj `new` ograniczenie do parametru typu, gdy klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

W przypadku `new()` używania ograniczenia z innymi ograniczeniami należy je określić jako ostatnie:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Aby uzyskać więcej informacji, zobacz [Ograniczenia parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).

Można również użyć `new` słowa kluczowego, aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji elementu członkowskiego](new-modifier.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Ograniczeń parametrów type](~/_csharplang/spec/classes.md#type-parameter-constraints) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy ogólne](../../programming-guide/generics/index.md)
