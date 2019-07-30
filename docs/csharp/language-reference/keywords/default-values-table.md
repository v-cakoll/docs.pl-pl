---
title: Tabela wartości domyślnych — C# odwołanie
ms.custom: seodec18
description: Dowiedz się, jakie są wartości C# domyślne typów.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627743"
---
# <a name="default-values-table-c-reference"></a>Tabela wartości domyślnych (C# odwołanie)

W poniższej tabeli przedstawiono wartości domyślne C# typów:

|Typ|Wartość domyślna|
|---------|------------------|
|Dowolny typ referencyjny|`null`|
|Dowolny [wbudowany typ liczbowy całkowity](../builtin-types/integral-numeric-types.md)|0 (zero)|
|Dowolny [wbudowany typ liczbowy zmiennoprzecinkowy](../builtin-types/floating-point-numeric-types.md)|0 (zero)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U + 0000)|
|[enum](enum.md)|Wartość wygenerowana przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.|
|[struct](struct.md)|Wartość wygenerowana przez ustawienie wszystkich pól typu wartość na wartości domyślne i wszystkie pola typu odwołania do `null`.|
|Dowolny [Typ wartości null](../../programming-guide/nullable-types/index.md)|Wystąpienie, dla którego <xref:System.Nullable%601.HasValue%2A> właściwość jest `false` i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana. Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.|

Użyj [wyrażenia wartości domyślnej](../../programming-guide/statements-expressions-operators/default-value-expressions.md) , aby utworzyć wartość domyślną typu, jak pokazano w poniższym przykładzie:

```csharp
int a = default(int);
```

Począwszy od C# 7,1, można użyć [ `default` literału](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) , aby zainicjować zmienną o wartości domyślnej typu:

```csharp
int a = default;
```

Dla typu wartości niejawny Konstruktor bez parametrów tworzy również wartość domyślną typu, jak pokazano w poniższym przykładzie:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Wartości domyślne](~/_csharplang/spec/variables.md#default-values)
- [Konstruktory domyślne](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
