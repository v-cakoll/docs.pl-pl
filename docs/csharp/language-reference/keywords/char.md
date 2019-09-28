---
title: char — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 255e69d3715a22e7933b4036e968e610657748cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353769"
---
# <a name="char-c-reference"></a><span data-ttu-id="90d47-102">char (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="90d47-102">char (C# Reference)</span></span>

<span data-ttu-id="90d47-103">Słowo kluczowe `char` służy do deklarowania instancji struktury <xref:System.Char?displayProperty=nameWithType> używanej przez .NET Framework do reprezentowania znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="90d47-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="90d47-104">Wartość obiektu `Char` jest wartością 16-bitową liczbową (porządkową).</span><span class="sxs-lookup"><span data-stu-id="90d47-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="90d47-105">Znaki Unicode służą do reprezentowania większości języków pisanych na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="90d47-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="90d47-106">Type</span><span class="sxs-lookup"><span data-stu-id="90d47-106">Type</span></span>|<span data-ttu-id="90d47-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="90d47-107">Range</span></span>|<span data-ttu-id="90d47-108">Size</span><span class="sxs-lookup"><span data-stu-id="90d47-108">Size</span></span>|<span data-ttu-id="90d47-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="90d47-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="90d47-110">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="90d47-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="90d47-111">16-bitowy znak Unicode</span><span class="sxs-lookup"><span data-stu-id="90d47-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="90d47-112">Literały</span><span class="sxs-lookup"><span data-stu-id="90d47-112">Literals</span></span>

<span data-ttu-id="90d47-113">Stałe typu `char` można zapisać jako literały znakowe, szesnastkową sekwencję ucieczki lub reprezentację Unicode.</span><span class="sxs-lookup"><span data-stu-id="90d47-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="90d47-114">Można również rzutować kody znaków całkowitych.</span><span class="sxs-lookup"><span data-stu-id="90d47-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="90d47-115">W poniższym przykładzie są inicjowane cztery zmienne `char` z tym samym znakiem `X`:</span><span class="sxs-lookup"><span data-stu-id="90d47-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="90d47-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="90d47-116">Conversions</span></span>

<span data-ttu-id="90d47-117">@No__t-0 może być niejawnie konwertowany na [UShort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)lub [Decimal](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="90d47-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="90d47-118">Niejawne konwersje z innych typów nie są jednak typu `char`.</span><span class="sxs-lookup"><span data-stu-id="90d47-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="90d47-119">Typ <xref:System.Char?displayProperty=nameWithType> zawiera kilka metod statycznych do pracy z wartościami `char`.</span><span class="sxs-lookup"><span data-stu-id="90d47-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="90d47-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="90d47-120">C# language specification</span></span>  

<span data-ttu-id="90d47-121">Aby uzyskać więcej informacji, zobacz [Typy całkowite](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="90d47-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="90d47-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="90d47-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="90d47-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90d47-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="90d47-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="90d47-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="90d47-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="90d47-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="90d47-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="90d47-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="90d47-127">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="90d47-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="90d47-128">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="90d47-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="90d47-129">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="90d47-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="90d47-130">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="90d47-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="90d47-131">Ciągi</span><span class="sxs-lookup"><span data-stu-id="90d47-131">Strings</span></span>](../../programming-guide/strings/index.md)
