---
title: Domyślne wartości typów C# — odwołanie do języka C#
description: Poznaj wartości domyślne typów języka C#, takich jak bool, char, int, float, double i inne.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507259"
---
# <a name="default-values-of-c-types-c-reference"></a>Domyślne wartości typów C# (odwołanie do języka C#)

W poniższej tabeli przedstawiono wartości domyślne typów języka C#:

|Typ|Wartość domyślna|
|---------|------------------|
|Dowolny typ odwołania|`null`|
|Dowolny [wbudowany integralny typ numeryczny](integral-numeric-types.md)|0 (zero)|
|Dowolny [wbudowany zmiennoprzecinowy typ numeryczny](floating-point-numeric-types.md)|0 (zero)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U+0000)|
|[Enum](enum.md)|Wartość wyprodukowana przez `(E)0`wyrażenie `E` , gdzie jest identyfikator wyliczenia.|
|[Struct](struct.md)|Wartość powstała przez ustawienie wszystkich pól typu wartości na ich `null`wartości domyślne i wszystkie pola typu odwołania na .|
|Dowolny [typ wartości z do wartości możliwej do wartości null](nullable-value-types.md)|Wystąpienie, dla <xref:System.Nullable%601.HasValue%2A> którego `false` właściwość jest i <xref:System.Nullable%601.Value%2A> właściwość jest niezdefiniowana. Ta wartość domyślna jest również znana jako wartość *null* typu wartości możliwej do wartości null.|

Operator [ `default` służy](../operators/default.md#default-operator) do tworzenia wartości domyślnej typu, jak pokazano w poniższym przykładzie:

```csharp
int a = default(int);
```

Począwszy od języka C# 7.1, można użyć [ `default` literału](../operators/default.md#default-literal) do zainicjowania zmiennej z domyślną wartością jej typu:

```csharp
int a = default;
```

Dla typu wartości niejawny konstruktor bez parametrów również tworzy wartość domyślną typu, jak pokazano w poniższym przykładzie:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

W czasie wykonywania, <xref:System.Type?displayProperty=nameWithType> jeśli wystąpienie reprezentuje typ <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> wartości, można użyć metody do wywołania konstruktora bez parametrów, aby uzyskać domyślną wartość typu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Wartości domyślne](~/_csharplang/spec/variables.md#default-values)
- [Konstruktory domyślne](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
