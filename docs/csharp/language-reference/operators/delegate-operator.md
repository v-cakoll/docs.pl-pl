---
title: Delegowanie operatora C# — odwołanie
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 02b0bfaccbd727b1f86a1668012f02b315fd88d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239303"
---
# <a name="delegate-operator-c-reference"></a>Delegate — operatorC# (odwołanie)

Operator `delegate` tworzy anonimową metodę, która może zostać przekonwertowana na typ delegata:

[!code-csharp-interactive[anonymous method](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Począwszy od C# 3, wyrażenia lambda zapewniają bardziej zwięzły i jednoznaczny sposób tworzenia anonimowej funkcji. Użyj [operatora = >](lambda-operator.md) , aby utworzyć wyrażenie lambda:
>
> [!code-csharp-interactive[lambda expression](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Aby uzyskać więcej informacji na temat funkcji wyrażeń lambda, na przykład przechwytywania zmiennych zewnętrznych, zobacz [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Gdy używasz operatora `delegate`, możesz pominąć listę parametrów. W takim przypadku utworzona Metoda anonimowa może zostać przekonwertowana na typ delegata z dowolną listą parametrów, co ilustruje poniższy przykład:

[!code-csharp-interactive[no parameter list](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Jest to jedyna funkcja metod anonimowych, które nie są obsługiwane przez wyrażenia lambda. We wszystkich innych przypadkach wyrażenie lambda jest preferowanym sposobem pisania kodu śródwierszowego.

Możesz również użyć słowa kluczowego `delegate`, aby zadeklarować [typ delegata](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [= > — operator](lambda-operator.md)
