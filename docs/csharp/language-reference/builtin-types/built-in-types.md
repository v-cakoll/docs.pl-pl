---
title: Typy wbudowane — odwołanie do języka C#
description: Naucz się wbudowanych typów wartości i odwołań języka C#
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 4f748373350ed0596a5f1d595c273243ae3227c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77095310"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="b8a46-103">Typy wbudowane (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="b8a46-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="b8a46-104">W poniższej tabeli wymieniono wbudowane typy [wartości](value-types.md) języka C#:</span><span class="sxs-lookup"><span data-stu-id="b8a46-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="b8a46-105">Słowo kluczowe typu C#</span><span class="sxs-lookup"><span data-stu-id="b8a46-105">C# type keyword</span></span>|<span data-ttu-id="b8a46-106">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="b8a46-106">.NET type</span></span>|
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

<span data-ttu-id="b8a46-107">W poniższej tabeli wymieniono wbudowane typy [odwołań](../keywords/reference-types.md) języka C#:</span><span class="sxs-lookup"><span data-stu-id="b8a46-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="b8a46-108">Słowo kluczowe typu C#</span><span class="sxs-lookup"><span data-stu-id="b8a46-108">C# type keyword</span></span>|<span data-ttu-id="b8a46-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="b8a46-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="b8a46-110">W poprzednich tabelach każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="b8a46-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b8a46-111">Są wymienne.</span><span class="sxs-lookup"><span data-stu-id="b8a46-111">They are interchangeable.</span></span> <span data-ttu-id="b8a46-112">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="b8a46-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

## <a name="see-also"></a><span data-ttu-id="b8a46-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8a46-113">See also</span></span>

- [<span data-ttu-id="b8a46-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b8a46-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b8a46-115">Domyślne wartości typów Języka C#</span><span class="sxs-lookup"><span data-stu-id="b8a46-115">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="b8a46-116">`dynamic`Słowa kluczowego</span><span class="sxs-lookup"><span data-stu-id="b8a46-116">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
