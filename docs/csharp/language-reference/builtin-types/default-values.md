---
title: Domyślne wartości typów C# — odwołanie do języka C#
description: Poznaj domyślne wartości typów Języka C#, takich jak bool, char, int, float, double i inne.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625868"
---
# <a name="default-values-of-c-types-c-reference"></a>Domyślne wartości typów C# (odwołanie c#)

W poniższej tabeli przedstawiono wartości domyślne typów języka C#:

|Typ|Wartość domyślna|
|---------|------------------|
|Dowolny typ odwołania|`null`|
|Każdy [wbudowany integralny typ numeryczny](integral-numeric-types.md)|0 (zero)|
|Dowolny [wbudowany typ numeryczny zmiennoprzecinkowych](floating-point-numeric-types.md)|0 (zero)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U+0000)|
|[Enum](enum.md)|Wartość tworzona przez `(E)0`wyrażenie `E` , gdzie jest identyfikator emancypacji.|
|[Struct](struct.md)|Wartość tworzona przez ustawienie wszystkich pól typu wartości na ich wartości `null`domyślne i wszystkie pola typu odwołania do .|
|Każdy [typ wartości z wartością null](nullable-value-types.md)|Wystąpienie, dla <xref:System.Nullable%601.HasValue%2A> którego `false` właściwość <xref:System.Nullable%601.Value%2A> jest i właściwość jest niezdefiniowana. Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.|

Użyj [domyślnego operatora,](../operators/default.md) aby wygenerować domyślną wartość typu, jak pokazano w poniższym przykładzie:

```csharp
int a = default(int);
```

Począwszy od języka C# 7.1, można użyć [ `default` literału](../operators/default.md#default-literal) do zainicjowania zmiennej z wartością domyślną jej typu:

```csharp
int a = default;
```

Dla typu wartości niejawny konstruktor bezparametrów tworzy również domyślną wartość tego typu, jak pokazano w poniższym przykładzie:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

W czasie wykonywania, jeśli <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje typ wartości, można użyć <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> metody do wywołania konstruktora bezparametrowego w celu uzyskania wartości domyślnej typu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Wartości domyślne](~/_csharplang/spec/variables.md#default-values)
- [Konstruktory domyślne](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
