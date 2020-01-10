---
title: Tabela wartości domyślnych — C# odwołanie
description: Dowiedz się, jakie są wartości C# domyślne typów.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: b15da080c34e2c24ff2a0ecda639f7fe68fb7573
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713644"
---
# <a name="default-values-table-c-reference"></a>Tabela wartości domyślnych (C# odwołanie)

W poniższej tabeli przedstawiono wartości domyślne C# typów:

|Typ|Wartość domyślna|
|---------|------------------|
|Dowolny typ referencyjny|`null`|
|Dowolny [wbudowany typ liczbowy całkowity](../builtin-types/integral-numeric-types.md)|0 (zero)|
|Dowolny [wbudowany typ liczbowy zmiennoprzecinkowy](../builtin-types/floating-point-numeric-types.md)|0 (zero)|
|[bool](../builtin-types/bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U + 0000)|
|[enum](../builtin-types/enum.md)|Wartość wygenerowana przez wyrażenie `(E)0`, gdzie `E` jest identyfikatorem wyliczenia.|
|[struct](struct.md)|Wartość wygenerowana przez ustawienie wszystkich pól typu wartość na wartości domyślne i wszystkie pola typu odwołania do `null`.|
|Dowolny [Typ wartości null](../builtin-types/nullable-value-types.md)|Wystąpienie, dla którego właściwość <xref:System.Nullable%601.HasValue%2A> jest `false` i Właściwość <xref:System.Nullable%601.Value%2A> jest niezdefiniowana. Ta wartość domyślna jest również znana jako wartość *null* typu wartości null.|

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

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
