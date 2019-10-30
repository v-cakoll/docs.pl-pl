---
title: Delegowanie operatora C# — odwołanie
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 9a78faaccffa9e7d4bf2829d8dfa0fa62a788bba
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039039"
---
# <a name="delegate-operator-c-reference"></a>Delegate — operatorC# (odwołanie)

Operator `delegate` tworzy anonimową metodę, która może zostać przekonwertowana na typ delegata:

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Począwszy od C# 3, wyrażenia lambda zapewniają bardziej zwięzły i jednoznaczny sposób tworzenia anonimowej funkcji. Użyj [operatora = >](lambda-operator.md) , aby utworzyć wyrażenie lambda:
>
> [!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Aby uzyskać więcej informacji na temat funkcji wyrażeń lambda, na przykład przechwytywania zmiennych zewnętrznych, zobacz [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Gdy używasz operatora `delegate`, możesz pominąć listę parametrów. W takim przypadku utworzona Metoda anonimowa może zostać przekonwertowana na typ delegata z dowolną listą parametrów, co ilustruje poniższy przykład:

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Jest to jedyna funkcja metod anonimowych, które nie są obsługiwane przez wyrażenia lambda. We wszystkich innych przypadkach wyrażenie lambda jest preferowanym sposobem pisania kodu śródwierszowego.

Możesz również użyć słowa kluczowego `delegate`, aby zadeklarować [typ delegata](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [= > — operator](lambda-operator.md)
