---
title: = > — operator - C# odwołania
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: a7fea9810cb02269278638ec71cd106463b029e9
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025015"
---
# <a name="-operator-c-reference"></a>= > — operator (C# odwołania)

`=>` Tokenu jest obsługiwana w dwóch formach: jako operatora lambda i separator nazwę elementu członkowskiego i implementacji elementu członkowskiego w definicji treści wyrażenia.

## <a name="lambda-operator"></a>Lambda operator

W [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), operatora lambda `=>` zmienne wejściowe po lewej stronie są oddzielone od treści lambda po prawej stronie.

W poniższym przykładzie użyto [LINQ](../../programming-guide/concepts/linq/index.md) funkcję za pomocą składni metody, aby zademonstrować użycie wyrażenia lambda:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Zmienne wejściowe wyrażeń lambda są silnie typizowane w czasie kompilacji. Gdy kompilator może wywnioskować rodzaje zmiennych wejściowych, podobnie jak w poprzednim przykładzie, możesz pominąć deklaracje typu. Jeśli musisz określić typ zmiennych wejściowych, należy użyć dla każdej zmiennej, co ilustruje poniższy przykład:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Poniższy przykład pokazuje jak zdefiniować wyrażenia lambda bez zmienne wejściowe:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definicja treści wyrażenia

Definicja treści wyrażenia ma następującą składnię ogólne:

```csharp
member => expression;
```

gdzie *wyrażenie* jest prawidłowym wyrażeniem. Należy pamiętać, że *wyrażenie* może być *wyrażenie instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub, jeśli element jest konstruktorem, finalizator lub właściwość `set` metody dostępu.

W poniższym przykładzie pokazano definicję treści wyrażenia dla `Person.ToString` metody:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Jest wersją skróconą następującą definicję metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Definicje treści wyrażenia dla metod i właściwości tylko do odczytu są obsługiwane, począwszy od C# 6. Definicje treści wyrażenia dla konstruktorów, finalizatorów, metod dostępu do właściwości i indeksatorów są obsługiwane, począwszy od C# 7.0.

Aby uzyskać więcej informacji, zobacz [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Operator `=>` nie może być przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji anonimowych](~/_csharplang/spec/expressions.md#anonymous-function-expressions) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Elementy członkowskie z wyrażeniem w treści](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
