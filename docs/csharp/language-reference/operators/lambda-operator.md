---
title: = > — odwołanie C# do operatora
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971229"
---
# <a name="-operator-c-reference"></a>= > — operatorC# (odwołanie)

`=>` Token jest obsługiwany w dwóch formach: jako operator lambda oraz jako separator nazwy elementu członkowskiego i implementacji elementu członkowskiego w definicji treści wyrażenia.

## <a name="lambda-operator"></a>Operator lambda

W [wyrażeniach lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operator `=>` lambda oddziela zmienne wejściowe po lewej stronie od treści lambda po prawej stronie.

W poniższym przykładzie użyto funkcji [LINQ](../../programming-guide/concepts/linq/index.md) z składnią metody, aby pokazać użycie wyrażeń lambda:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Zmienne wejściowe wyrażeń lambda są silnie wpisywane w czasie kompilacji. Gdy kompilator może wywnioskować typy zmiennych wejściowych, jak w poprzednim przykładzie, można pominąć deklaracje typu. Jeśli musisz określić typ zmiennych wejściowych, należy to zrobić dla każdej zmiennej, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Poniższy przykład pokazuje, jak zdefiniować wyrażenie lambda bez zmiennych wejściowych:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definicja treści wyrażenia

Definicja treści wyrażenia ma następującą składnię ogólną:

```csharp
member => expression;
```

gdzie `expression` jest prawidłowym wyrażeniem. Zwracany typ elementu `expression` musi być niejawnie konwertowany na typ zwracany elementu członkowskiego. Jeśli typem zwracanym elementu członkowskiego `void` jest lub, jeśli element członkowski jest konstruktorem, finalizatorem lub akcesorem `set` właściwości, `expression` musi być [*wyrażeniem instrukcji*](~/_csharplang/spec/statements.md#expression-statements); może to być dowolny typ.

W poniższym przykładzie przedstawiono definicję treści wyrażenia dla `Person.ToString` metody:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Jest to skrócona wersja następującej definicji metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Definicje treści wyrażenia dla metod i właściwości tylko do odczytu są obsługiwane począwszy od C# 6. Definicje treści wyrażenia dla konstruktorów, finalizatorów, metod dostępu do właściwości i indeksatorów są obsługiwane począwszy C# od 7,0.

Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniami](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operator `=>` nie może być przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Elementy członkowskie z wyrażeniem w treści](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
