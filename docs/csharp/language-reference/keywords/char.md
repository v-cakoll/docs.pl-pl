---
title: CHAR — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: b58730d945582ded7b76fcd5c4c65bc1dd9324da
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661456"
---
# <a name="char-c-reference"></a><span data-ttu-id="feb37-102">char (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="feb37-102">char (C# Reference)</span></span>

<span data-ttu-id="feb37-103">`char` — Słowo kluczowe jest używane do deklarowania wystąpienie <xref:System.Char?displayProperty=nameWithType> strukturę, która używa .NET Framework, który reprezentuje znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="feb37-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="feb37-104">Wartość `Char` obiekt jest wartość liczbowa 16-bitowych (numer).</span><span class="sxs-lookup"><span data-stu-id="feb37-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="feb37-105">Znaki Unicode są używane do reprezentowania większość języki pisane świata.</span><span class="sxs-lookup"><span data-stu-id="feb37-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="feb37-106">Typ</span><span class="sxs-lookup"><span data-stu-id="feb37-106">Type</span></span>|<span data-ttu-id="feb37-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="feb37-107">Range</span></span>|<span data-ttu-id="feb37-108">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="feb37-108">Size</span></span>|<span data-ttu-id="feb37-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="feb37-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="feb37-110">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="feb37-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="feb37-111">Znak 16-bitowych Unicode</span><span class="sxs-lookup"><span data-stu-id="feb37-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="feb37-112">Literały</span><span class="sxs-lookup"><span data-stu-id="feb37-112">Literals</span></span>

<span data-ttu-id="feb37-113">Stałe `char` typu mogą być zapisywane jako literały znakowe, szesnastkowa sekwencja unikowa lub reprezentację Unicode.</span><span class="sxs-lookup"><span data-stu-id="feb37-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="feb37-114">Można również rzutowania kody znaków typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="feb37-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="feb37-115">W poniższym przykładzie czterech `char` zmienne są inicjowane za pomocą takiego samego znaku `X`:</span><span class="sxs-lookup"><span data-stu-id="feb37-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="feb37-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="feb37-116">Conversions</span></span>

<span data-ttu-id="feb37-117">A `char` mogą być niejawnie konwertowane na [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), lub [dziesiętnych](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="feb37-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="feb37-118">Jednak nie istnieją żadne niejawne konwersje z innych typów `char` typu.</span><span class="sxs-lookup"><span data-stu-id="feb37-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="feb37-119"><xref:System.Char?displayProperty=nameWithType> Typu udostępnia kilka metod statycznych do pracy z `char` wartości.</span><span class="sxs-lookup"><span data-stu-id="feb37-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="feb37-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="feb37-120">C# language specification</span></span>  

<span data-ttu-id="feb37-121">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="feb37-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="feb37-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="feb37-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="feb37-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feb37-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="feb37-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="feb37-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="feb37-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="feb37-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="feb37-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="feb37-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="feb37-127">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="feb37-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="feb37-128">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="feb37-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="feb37-129">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="feb37-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="feb37-130">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="feb37-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="feb37-131">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="feb37-131">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
- [<span data-ttu-id="feb37-132">Ciągi</span><span class="sxs-lookup"><span data-stu-id="feb37-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
