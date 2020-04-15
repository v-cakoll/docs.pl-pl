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
# <a name="built-in-types-c-reference"></a><span data-ttu-id="42c39-103">Typy wbudowane (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="42c39-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="42c39-104">W poniższej tabeli wymieniono wbudowane [typy wartości](value-types.md) języka C#:</span><span class="sxs-lookup"><span data-stu-id="42c39-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="42c39-105">Słowo kluczowe typu C#</span><span class="sxs-lookup"><span data-stu-id="42c39-105">C# type keyword</span></span>|<span data-ttu-id="42c39-106">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="42c39-106">.NET type</span></span>|
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

<span data-ttu-id="42c39-107">W poniższej tabeli wymieniono wbudowane typy [odwołań](../keywords/reference-types.md) języka C#:</span><span class="sxs-lookup"><span data-stu-id="42c39-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="42c39-108">Słowo kluczowe typu C#</span><span class="sxs-lookup"><span data-stu-id="42c39-108">C# type keyword</span></span>|<span data-ttu-id="42c39-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="42c39-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|

<span data-ttu-id="42c39-110">W poprzednich tabelach każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="42c39-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="42c39-111">Są wymienne.</span><span class="sxs-lookup"><span data-stu-id="42c39-111">They are interchangeable.</span></span> <span data-ttu-id="42c39-112">Na przykład następujące deklaracje deklarują zmienne tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="42c39-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="42c39-113">Słowo [`void`](void.md) kluczowe reprezentuje brak typu.</span><span class="sxs-lookup"><span data-stu-id="42c39-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="42c39-114">Używasz go jako typ zwracany metody, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="42c39-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="42c39-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42c39-115">See also</span></span>

- [<span data-ttu-id="42c39-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="42c39-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="42c39-117">Domyślne wartości typów języka C#</span><span class="sxs-lookup"><span data-stu-id="42c39-117">Default values of C# types</span></span>](default-values.md)
- [<span data-ttu-id="42c39-118">`dynamic`Słowa kluczowego</span><span class="sxs-lookup"><span data-stu-id="42c39-118">`dynamic` keyword</span></span>](reference-types.md#the-dynamic-type)
