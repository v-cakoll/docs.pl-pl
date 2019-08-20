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
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605951"
---
# <a name="char-c-reference"></a><span data-ttu-id="7be09-102">char (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7be09-102">char (C# Reference)</span></span>

<span data-ttu-id="7be09-103">Słowo kluczowe jest używane do deklarowania instancji <xref:System.Char?displayProperty=nameWithType> struktury używanej przez .NET Framework do reprezentowania znaku Unicode. `char`</span><span class="sxs-lookup"><span data-stu-id="7be09-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="7be09-104">Wartość `Char` obiektu jest 16-bitową wartością numeryczną (porządkową).</span><span class="sxs-lookup"><span data-stu-id="7be09-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="7be09-105">Znaki Unicode służą do reprezentowania większości języków pisanych na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="7be09-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="7be09-106">Typ</span><span class="sxs-lookup"><span data-stu-id="7be09-106">Type</span></span>|<span data-ttu-id="7be09-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7be09-107">Range</span></span>|<span data-ttu-id="7be09-108">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="7be09-108">Size</span></span>|<span data-ttu-id="7be09-109">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="7be09-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="7be09-110">U + 0000 do U + FFFF</span><span class="sxs-lookup"><span data-stu-id="7be09-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="7be09-111">16-bitowy znak Unicode</span><span class="sxs-lookup"><span data-stu-id="7be09-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="7be09-112">Literały</span><span class="sxs-lookup"><span data-stu-id="7be09-112">Literals</span></span>

<span data-ttu-id="7be09-113">`char` Stałe typu można zapisać jako literały znakowe, szesnastkową sekwencję ucieczki lub reprezentację Unicode.</span><span class="sxs-lookup"><span data-stu-id="7be09-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="7be09-114">Można również rzutować kody znaków całkowitych.</span><span class="sxs-lookup"><span data-stu-id="7be09-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="7be09-115">W poniższym przykładzie są inicjowane cztery `char` zmienne z tym samym znakiem: `X`</span><span class="sxs-lookup"><span data-stu-id="7be09-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="7be09-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="7be09-116">Conversions</span></span>

<span data-ttu-id="7be09-117">[](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/integral-numeric-types.md) [](../builtin-types/floating-point-numeric-types.md) [](../builtin-types/integral-numeric-types.md)Może być niejawnie konwertowany na UShort, int, uint, Double lub Decimal. `char`</span><span class="sxs-lookup"><span data-stu-id="7be09-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="7be09-118">Jednak nie istnieją niejawne konwersje z innych typów do `char` typu.</span><span class="sxs-lookup"><span data-stu-id="7be09-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="7be09-119">Typ zawiera kilka metod statycznych do pracy z `char` wartościami. <xref:System.Char?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7be09-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7be09-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7be09-120">C# language specification</span></span>  

<span data-ttu-id="7be09-121">Aby uzyskać więcej informacji, zobacz [Typy całkowite](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7be09-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="7be09-122">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="7be09-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7be09-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7be09-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="7be09-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7be09-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7be09-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7be09-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7be09-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7be09-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="7be09-127">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="7be09-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="7be09-128">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="7be09-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="7be09-129">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="7be09-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="7be09-130">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="7be09-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="7be09-131">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="7be09-131">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="7be09-132">Ciągi</span><span class="sxs-lookup"><span data-stu-id="7be09-132">Strings</span></span>](../../programming-guide/strings/index.md)
