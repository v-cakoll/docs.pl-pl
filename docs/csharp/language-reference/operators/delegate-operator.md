---
title: operator delegata — odwołanie do języka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847342"
---
# <a name="delegate-operator-c-reference"></a>operator delegata (odwołanie do języka C#)

Operator `delegate` tworzy metodę anonimową, która może być konwertowana na typ delegata:

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Począwszy od c# 3 wyrażenia lambda zapewniają bardziej zwięzły i wyrazisty sposób tworzenia funkcji anonimowych. Użyj [=> operatora](lambda-operator.md) do skonstruowania wyrażenia lambda:
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> Aby uzyskać więcej informacji na temat funkcji wyrażeń lambda, na przykład przechwytywania zmiennych zewnętrznych, zobacz [Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Korzystając z `delegate` operatora, można pominąć listę parametrów. Jeśli to zrobisz, utworzona metoda anonimowa może zostać przekonwertowana na typ delegata z dowolną listą parametrów, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

Jest to jedyna funkcja metod anonimowych, która nie jest obsługiwana przez wyrażenia lambda. We wszystkich innych przypadkach wyrażenie lambda jest preferowanym sposobem pisania kodu w wierszu.

Słowo `delegate` kluczowe służy również do deklarowania [typu pełnomocnika](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [= operator>](lambda-operator.md)
