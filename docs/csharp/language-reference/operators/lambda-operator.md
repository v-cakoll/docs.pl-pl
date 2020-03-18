---
title: = operator> - odwołanie do języka C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846259"
---
# <a name="-operator-c-reference"></a>= operator> (odwołanie do języka C#)

Token `=>` jest obsługiwany w dwóch formach: jako [operator lambda](#lambda-operator) i jako separator nazwy elementu członkowskiego i implementacji elementu członkowskiego w [definicji treści wyrażenia](#expression-body-definition).

## <a name="lambda-operator"></a>Operator Lambda

W [wyrażeniach lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operator `=>` lambda oddziela parametry wejściowe po lewej stronie od obiektu lambda po prawej stronie.

W poniższym przykładzie użyto funkcji [LINQ](../../programming-guide/concepts/linq/index.md) ze składnią metody w celu zademonstrowania użycia wyrażeń lambda:

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Parametry wejściowe wyrażenia lambda są silnie typowane w czasie kompilacji. Gdy kompilator można wywnioskować typy parametrów wejściowych, jak w poprzednim przykładzie, można pominąć deklaracje typu. Jeśli trzeba określić typ parametrów wejściowych, należy to zrobić dla każdego parametru, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

W poniższym przykładzie pokazano, jak zdefiniować wyrażenie lambda bez parametrów wejściowych:

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definicja treści wyrażeń

Definicja treści wyrażenia ma następującą ogólną składnię:

```csharp
member => expression;
```

gdzie `expression` jest prawidłowe wyrażenie. Typ zwracany `expression` musi być niejawnie konwertowalny do typu zwracanego elementu członkowskiego. Jeśli typ zwracany elementu `void` członkowskiego jest lub jeśli element członkowski `set` jest konstruktorem, finalizatorem lub akcesorem właściwości, `expression` musi być [*wyrażeniem instrukcji*](~/_csharplang/spec/statements.md#expression-statements), które może być dowolnego typu.

W poniższym przykładzie przedstawiono definicję treści wyrażeń `Person.ToString` dla metody:

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

Definicje treści wyrażeń dla metod, operatorów i właściwości tylko do odczytu są obsługiwane począwszy od języka C# 6. Definicje treści wyrażeń dla konstruktorów, finalizatorów oraz akcesorów właściwości i indeksatora są obsługiwane począwszy od języka C# 7.0.

Aby uzyskać więcej informacji, zobacz [Elementy członkowskie zabudowane wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Przeciążenie operatora

Operator `=>` nie może być przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji na temat operatora lambda, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
