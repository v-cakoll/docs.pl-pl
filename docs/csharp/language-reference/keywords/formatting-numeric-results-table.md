---
title: Formatowanie tabeli wyników liczbowych C# — odwołanie
ms.custom: seodec18
description: Więcej informacji C# na temat standardowych ciągów formatu liczbowego
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 2cba5e704787ae6368b2543c985babf2fde3b4dd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422754"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="ccd95-103">Formatowanie tabeli wyników liczbowychC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ccd95-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="ccd95-104">W poniższej tabeli przedstawiono obsługiwane specyfikatory formatu do formatowania wyników liczbowych.</span><span class="sxs-lookup"><span data-stu-id="ccd95-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="ccd95-105">Sformatowany wynik w ostatniej kolumnie odpowiada <xref:System.Globalization.CultureInfo>"pl-US".</span><span class="sxs-lookup"><span data-stu-id="ccd95-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="ccd95-106">Specyfikator formatu</span><span class="sxs-lookup"><span data-stu-id="ccd95-106">Format specifier</span></span>|<span data-ttu-id="ccd95-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ccd95-107">Description</span></span>|<span data-ttu-id="ccd95-108">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ccd95-108">Examples</span></span>|<span data-ttu-id="ccd95-109">Wynik</span><span class="sxs-lookup"><span data-stu-id="ccd95-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="ccd95-110">C lub c</span><span class="sxs-lookup"><span data-stu-id="ccd95-110">C or c</span></span>|<span data-ttu-id="ccd95-111">Waluta</span><span class="sxs-lookup"><span data-stu-id="ccd95-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="ccd95-112">$2,50</span><span class="sxs-lookup"><span data-stu-id="ccd95-112">$2.50</span></span><br /><br /> <span data-ttu-id="ccd95-113">($2,50)</span><span class="sxs-lookup"><span data-stu-id="ccd95-113">($2.50)</span></span>|  
|<span data-ttu-id="ccd95-114">D lub d</span><span class="sxs-lookup"><span data-stu-id="ccd95-114">D or d</span></span>|<span data-ttu-id="ccd95-115">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="ccd95-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="ccd95-116">00025</span><span class="sxs-lookup"><span data-stu-id="ccd95-116">00025</span></span>|  
|<span data-ttu-id="ccd95-117">E lub e</span><span class="sxs-lookup"><span data-stu-id="ccd95-117">E or e</span></span>|<span data-ttu-id="ccd95-118">Wykładniczego</span><span class="sxs-lookup"><span data-stu-id="ccd95-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="ccd95-119">2.50 e + 005</span><span class="sxs-lookup"><span data-stu-id="ccd95-119">2.50E+005</span></span>|  
|<span data-ttu-id="ccd95-120">F lub f</span><span class="sxs-lookup"><span data-stu-id="ccd95-120">F or f</span></span>|<span data-ttu-id="ccd95-121">Wartość stałoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="ccd95-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="ccd95-122">2,50</span><span class="sxs-lookup"><span data-stu-id="ccd95-122">2.50</span></span><br /><br /> <span data-ttu-id="ccd95-123">3</span><span class="sxs-lookup"><span data-stu-id="ccd95-123">3</span></span>|  
|<span data-ttu-id="ccd95-124">G lub g</span><span class="sxs-lookup"><span data-stu-id="ccd95-124">G or g</span></span>|<span data-ttu-id="ccd95-125">Ogólne</span><span class="sxs-lookup"><span data-stu-id="ccd95-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="ccd95-126">2,5</span><span class="sxs-lookup"><span data-stu-id="ccd95-126">2.5</span></span>|  
|<span data-ttu-id="ccd95-127">N lub n</span><span class="sxs-lookup"><span data-stu-id="ccd95-127">N or n</span></span>|<span data-ttu-id="ccd95-128">przypada</span><span class="sxs-lookup"><span data-stu-id="ccd95-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="ccd95-129">2 500 000,00</span><span class="sxs-lookup"><span data-stu-id="ccd95-129">2,500,000.00</span></span>|  
|<span data-ttu-id="ccd95-130">P lub p</span><span class="sxs-lookup"><span data-stu-id="ccd95-130">P or p</span></span>|<span data-ttu-id="ccd95-131">Wartość procentowa</span><span class="sxs-lookup"><span data-stu-id="ccd95-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="ccd95-132">25,00%</span><span class="sxs-lookup"><span data-stu-id="ccd95-132">25.00%</span></span>|  
|<span data-ttu-id="ccd95-133">R lub r</span><span class="sxs-lookup"><span data-stu-id="ccd95-133">R or r</span></span>|<span data-ttu-id="ccd95-134">Wartość dwustronna</span><span class="sxs-lookup"><span data-stu-id="ccd95-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="ccd95-135">2,5</span><span class="sxs-lookup"><span data-stu-id="ccd95-135">2.5</span></span>|  
|<span data-ttu-id="ccd95-136">X lub x</span><span class="sxs-lookup"><span data-stu-id="ccd95-136">X or x</span></span>|<span data-ttu-id="ccd95-137">Wartość szesnastkowa</span><span class="sxs-lookup"><span data-stu-id="ccd95-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="ccd95-138">FA</span><span class="sxs-lookup"><span data-stu-id="ccd95-138">FA</span></span><br /><br /> <span data-ttu-id="ccd95-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="ccd95-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ccd95-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccd95-140">Remarks</span></span>

<span data-ttu-id="ccd95-141">Użyj specyfikatora formatu, aby utworzyć ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="ccd95-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="ccd95-142">Ciąg formatu ma następującą postać: `Axx`, gdzie</span><span class="sxs-lookup"><span data-stu-id="ccd95-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="ccd95-143">`A` jest specyfikatorem formatu, który kontroluje typ formatowania zastosowanego do wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="ccd95-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="ccd95-144">`xx` jest specyfikatorem dokładności, który ma wpływ na liczbę cyfr w sformatowanym danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ccd95-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="ccd95-145">Wartość specyfikatora dokładności mieści się w zakresie od 0 do 99.</span><span class="sxs-lookup"><span data-stu-id="ccd95-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="ccd95-146">Specyfikatory formatu dziesiętnego ("D" lub "d") i szesnastkowego ("X" lub "x") są obsługiwane tylko dla typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ccd95-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="ccd95-147">Specyfikator formatu rundy ("R" lub "r") jest obsługiwany tylko w przypadku typów <xref:System.Single>, <xref:System.Double>i <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="ccd95-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="ccd95-148">Ciągi standardowego formatu liczbowego są obsługiwane przez:</span><span class="sxs-lookup"><span data-stu-id="ccd95-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="ccd95-149">Niektóre przeciążenia metody `ToString` wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="ccd95-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="ccd95-150">Na przykład można podać ciąg formatu liczbowego dla metod <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccd95-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="ccd95-151">[Funkcja formatowania złożonego](../../../standard/base-types/composite-formatting.md)platformy .NET, obsługiwana przez metodę <xref:System.String.Format%2A?displayProperty=nameWithType>, na przykład.</span><span class="sxs-lookup"><span data-stu-id="ccd95-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="ccd95-152">[Ciągi interpolowane](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="ccd95-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="ccd95-153">Aby uzyskać więcej informacji, zobacz [Standardowe ciągi formatujące](../../../standard/base-types/standard-numeric-format-strings.md)liczby.</span><span class="sxs-lookup"><span data-stu-id="ccd95-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccd95-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccd95-154">See also</span></span>

- [<span data-ttu-id="ccd95-155">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="ccd95-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ccd95-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ccd95-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ccd95-157">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="ccd95-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="ccd95-158">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="ccd95-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="ccd95-159">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="ccd95-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="ccd95-160">string</span><span class="sxs-lookup"><span data-stu-id="ccd95-160">string</span></span>](../builtin-types/reference-types.md)
