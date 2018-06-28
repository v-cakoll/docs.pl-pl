---
title: CHAR — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: ea465e240a1d74b3f473316ca63b05bd0ba90777
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028035"
---
# <a name="char-c-reference"></a><span data-ttu-id="e0a63-102">char (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e0a63-102">char (C# Reference)</span></span>

<span data-ttu-id="e0a63-103">`char` — Słowo kluczowe służy do deklarowania wystąpienia <xref:System.Char?displayProperty=nameWithType> struktury, który używa programu .NET Framework do reprezentowania znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="e0a63-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="e0a63-104">Wartość `Char` obiektu jest wartością numeryczną 16-bitowych (numer).</span><span class="sxs-lookup"><span data-stu-id="e0a63-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="e0a63-105">Znaki Unicode są używane do reprezentowania większość języków pisanych na świecie.</span><span class="sxs-lookup"><span data-stu-id="e0a63-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="e0a63-106">Typ</span><span class="sxs-lookup"><span data-stu-id="e0a63-106">Type</span></span>|<span data-ttu-id="e0a63-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="e0a63-107">Range</span></span>|<span data-ttu-id="e0a63-108">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="e0a63-108">Size</span></span>|<span data-ttu-id="e0a63-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="e0a63-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e0a63-110">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="e0a63-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e0a63-111">Znak Unicode 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="e0a63-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="e0a63-112">Literały</span><span class="sxs-lookup"><span data-stu-id="e0a63-112">Literals</span></span>

<span data-ttu-id="e0a63-113">Stałe `char` typu mogą być zapisywane jako literały znaków, szesnastkowa sekwencja unikowa lub reprezentacja Unicode.</span><span class="sxs-lookup"><span data-stu-id="e0a63-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="e0a63-114">Można również rzutować kody znaków wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e0a63-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="e0a63-115">W poniższym przykładzie czterech `char` zmienne są inicjowane z tym samym `X`:</span><span class="sxs-lookup"><span data-stu-id="e0a63-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="e0a63-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="e0a63-116">Conversions</span></span>

<span data-ttu-id="e0a63-117">A `char` można niejawnie przekonwertować [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="e0a63-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="e0a63-118">Jednak nie istnieją żadne niejawne konwersje z innych typów do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="e0a63-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="e0a63-119"><xref:System.Char?displayProperty=nameWithType> Typ zapewnia kilka metod statycznych do pracy z `char` wartości.</span><span class="sxs-lookup"><span data-stu-id="e0a63-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0a63-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0a63-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e0a63-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0a63-121">See also</span></span>

<xref:System.Char>  
[<span data-ttu-id="e0a63-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0a63-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="e0a63-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e0a63-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="e0a63-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e0a63-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="e0a63-125">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="e0a63-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
[<span data-ttu-id="e0a63-126">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="e0a63-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="e0a63-127">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="e0a63-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="e0a63-128">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="e0a63-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[<span data-ttu-id="e0a63-129">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="e0a63-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
[<span data-ttu-id="e0a63-130">Ciągi</span><span class="sxs-lookup"><span data-stu-id="e0a63-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)