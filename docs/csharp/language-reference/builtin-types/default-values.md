---
title: Wartości domyślne C# typów — C# odwołanie
description: Poznaj wartości domyślne C# typów takich jak bool, char, int, float, Double i więcej.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625868"
---
# <a name="default-values-of-c-types-c-reference"></a>Wartości domyślne C# typów (C# odwołanie)

W poniższej tabeli przedstawiono wartości domyślne C# typów:

|Typ|Wartość domyślna|
|---------|------------------|
|Dowolny typ referencyjny|`null`|
|Dowolny [wbudowany typ liczbowy całkowity](integral-numeric-types.md)|0 (zero)|
|Dowolny [wbudowany typ liczbowy zmiennoprzecinkowy](floating-point-numeric-types.md)|0 (zero)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|Wartość wygenerowana przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.|
|[struct](struct.md)|Wartość wygenerowana przez ustawienie wszystkich pól typu wartość na wartości domyślne i wszystkie pola typu odwołania do `null`.|
|Dowolny [Typ wartości null](nullable-value-types.md)|Wystąpienie, dla którego właściwość <xref:System.Nullable%601.HasValue%2A> jest `false` i Właściwość <xref:System.Nullable%601.Value%2A> jest niezdefiniowana. Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.|

Użyj [operatora domyślnego](../operators/default.md) , aby utworzyć wartość domyślną typu, jak pokazano w poniższym przykładzie:

```csharp
int a = default(int);
```

Począwszy od C# 7,1, można użyć [literału`default`](../operators/default.md#default-literal) , aby zainicjować zmienną o wartości domyślnej typu:

```csharp
int a = default;
```

Dla typu wartości niejawny Konstruktor bez parametrów tworzy również wartość domyślną typu, jak pokazano w poniższym przykładzie:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

W czasie wykonywania, jeśli wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje typ wartości, można użyć metody <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> do wywołania konstruktora bez parametrów, aby uzyskać wartość domyślną typu.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Wartości domyślne](~/_csharplang/spec/variables.md#default-values)
- [Konstruktory domyślne](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
