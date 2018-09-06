---
title: CHAR — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 95ecfaaf1397f7a4598faba6528b38170062145a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742029"
---
# <a name="char-c-reference"></a><span data-ttu-id="03823-102">char (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="03823-102">char (C# Reference)</span></span>

<span data-ttu-id="03823-103">`char` — Słowo kluczowe jest używane do deklarowania wystąpienie <xref:System.Char?displayProperty=nameWithType> strukturę, która używa .NET Framework, który reprezentuje znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="03823-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="03823-104">Wartość `Char` obiekt jest wartość liczbowa 16-bitowych (numer).</span><span class="sxs-lookup"><span data-stu-id="03823-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="03823-105">Znaki Unicode są używane do reprezentowania większość języki pisane świata.</span><span class="sxs-lookup"><span data-stu-id="03823-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="03823-106">Typ</span><span class="sxs-lookup"><span data-stu-id="03823-106">Type</span></span>|<span data-ttu-id="03823-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="03823-107">Range</span></span>|<span data-ttu-id="03823-108">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="03823-108">Size</span></span>|<span data-ttu-id="03823-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="03823-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="03823-110">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="03823-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="03823-111">Znak 16-bitowych Unicode</span><span class="sxs-lookup"><span data-stu-id="03823-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="03823-112">Literały</span><span class="sxs-lookup"><span data-stu-id="03823-112">Literals</span></span>

<span data-ttu-id="03823-113">Stałe `char` typu mogą być zapisywane jako literały znakowe, szesnastkowa sekwencja unikowa lub reprezentację Unicode.</span><span class="sxs-lookup"><span data-stu-id="03823-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="03823-114">Można również rzutowania kody znaków typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="03823-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="03823-115">W poniższym przykładzie czterech `char` zmienne są inicjowane za pomocą takiego samego znaku `X`:</span><span class="sxs-lookup"><span data-stu-id="03823-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="03823-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="03823-116">Conversions</span></span>

<span data-ttu-id="03823-117">A `char` mogą być niejawnie konwertowane na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="03823-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="03823-118">Jednak nie istnieją żadne niejawne konwersje z innych typów `char` typu.</span><span class="sxs-lookup"><span data-stu-id="03823-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="03823-119"><xref:System.Char?displayProperty=nameWithType> Typu udostępnia kilka metod statycznych do pracy z `char` wartości.</span><span class="sxs-lookup"><span data-stu-id="03823-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03823-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03823-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03823-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03823-121">See also</span></span>

- <xref:System.Char>  
- [<span data-ttu-id="03823-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03823-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="03823-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03823-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="03823-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="03823-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="03823-125">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="03823-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="03823-126">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="03823-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="03823-127">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="03823-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="03823-128">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="03823-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="03823-129">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="03823-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="03823-130">Ciągi</span><span class="sxs-lookup"><span data-stu-id="03823-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)