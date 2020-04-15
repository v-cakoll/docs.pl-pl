---
title: Typy wbudowane — odwołanie do języka C#
description: Poznaj wbudowaną wartość i typy odwołań w języku C#
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: bf8823c6674b1ff3f0028a50df8ce8d0f803cfc1
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389491"
---
# <a name="built-in-types-c-reference"></a>Typy wbudowane (odwołanie do języka C#)

W poniższej tabeli wymieniono wbudowane [typy wartości](value-types.md) języka C#:

|Słowo kluczowe typu C#|Typ .NET|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

W poniższej tabeli wymieniono wbudowane typy [odwołań](../keywords/reference-types.md) języka C#:

|Słowo kluczowe typu C#|Typ .NET|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

W poprzednich tabelach każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET. Są wymienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Słowo [`void`](void.md) kluczowe reprezentuje brak typu. Używasz go jako typ zwracany metody, która nie zwraca wartości.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Domyślne wartości typów języka C#](default-values.md)
- [`dynamic`Słowa kluczowego](reference-types.md#the-dynamic-type)
