---
title: Formatowanie tabeli wyników liczbowych C# — odwołanie
description: Więcej informacji C# na temat standardowych ciągów formatu liczbowego
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: eb93f0a4f3c66e9f7b295366a77b9fb099fc3a1e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713513"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="55a8b-103">Formatowanie tabeli wyników liczbowychC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="55a8b-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="55a8b-104">W poniższej tabeli przedstawiono obsługiwane specyfikatory formatu do formatowania wyników liczbowych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="55a8b-105">Sformatowany wynik w ostatniej kolumnie odpowiada <xref:System.Globalization.CultureInfo>"pl-US".</span><span class="sxs-lookup"><span data-stu-id="55a8b-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="55a8b-106">Specyfikator formatu</span><span class="sxs-lookup"><span data-stu-id="55a8b-106">Format specifier</span></span>|<span data-ttu-id="55a8b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="55a8b-107">Description</span></span>|<span data-ttu-id="55a8b-108">Przykłady</span><span class="sxs-lookup"><span data-stu-id="55a8b-108">Examples</span></span>|<span data-ttu-id="55a8b-109">Wynik</span><span class="sxs-lookup"><span data-stu-id="55a8b-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="55a8b-110">C lub c</span><span class="sxs-lookup"><span data-stu-id="55a8b-110">C or c</span></span>|<span data-ttu-id="55a8b-111">Waluta</span><span class="sxs-lookup"><span data-stu-id="55a8b-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="55a8b-112">\\$2,50</span><span class="sxs-lookup"><span data-stu-id="55a8b-112">\\$2.50</span></span><br /><br /> <span data-ttu-id="55a8b-113">(\\$2,50)</span><span class="sxs-lookup"><span data-stu-id="55a8b-113">(\\$2.50)</span></span>|  
|<span data-ttu-id="55a8b-114">D lub d</span><span class="sxs-lookup"><span data-stu-id="55a8b-114">D or d</span></span>|<span data-ttu-id="55a8b-115">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="55a8b-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="55a8b-116">00025</span><span class="sxs-lookup"><span data-stu-id="55a8b-116">00025</span></span>|  
|<span data-ttu-id="55a8b-117">E lub e</span><span class="sxs-lookup"><span data-stu-id="55a8b-117">E or e</span></span>|<span data-ttu-id="55a8b-118">Wykładniczy</span><span class="sxs-lookup"><span data-stu-id="55a8b-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="55a8b-119">2.50 e + 005</span><span class="sxs-lookup"><span data-stu-id="55a8b-119">2.50E+005</span></span>|  
|<span data-ttu-id="55a8b-120">F lub f</span><span class="sxs-lookup"><span data-stu-id="55a8b-120">F or f</span></span>|<span data-ttu-id="55a8b-121">Wartość stałoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="55a8b-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="55a8b-122">2.50</span><span class="sxs-lookup"><span data-stu-id="55a8b-122">2.50</span></span><br /><br /> <span data-ttu-id="55a8b-123">3</span><span class="sxs-lookup"><span data-stu-id="55a8b-123">3</span></span>|  
|<span data-ttu-id="55a8b-124">G lub g</span><span class="sxs-lookup"><span data-stu-id="55a8b-124">G or g</span></span>|<span data-ttu-id="55a8b-125">Ogólne</span><span class="sxs-lookup"><span data-stu-id="55a8b-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="55a8b-126">2.5</span><span class="sxs-lookup"><span data-stu-id="55a8b-126">2.5</span></span>|  
|<span data-ttu-id="55a8b-127">N lub n</span><span class="sxs-lookup"><span data-stu-id="55a8b-127">N or n</span></span>|<span data-ttu-id="55a8b-128">Numeryczne</span><span class="sxs-lookup"><span data-stu-id="55a8b-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="55a8b-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="55a8b-129">2,500,000.00</span></span>|  
|<span data-ttu-id="55a8b-130">P lub p</span><span class="sxs-lookup"><span data-stu-id="55a8b-130">P or p</span></span>|<span data-ttu-id="55a8b-131">Wartość procentowa</span><span class="sxs-lookup"><span data-stu-id="55a8b-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="55a8b-132">25,00%</span><span class="sxs-lookup"><span data-stu-id="55a8b-132">25.00%</span></span>|  
|<span data-ttu-id="55a8b-133">R lub r</span><span class="sxs-lookup"><span data-stu-id="55a8b-133">R or r</span></span>|<span data-ttu-id="55a8b-134">Wartość dwustronna</span><span class="sxs-lookup"><span data-stu-id="55a8b-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="55a8b-135">2.5</span><span class="sxs-lookup"><span data-stu-id="55a8b-135">2.5</span></span>|  
|<span data-ttu-id="55a8b-136">X lub x</span><span class="sxs-lookup"><span data-stu-id="55a8b-136">X or x</span></span>|<span data-ttu-id="55a8b-137">Wartość szesnastkowa</span><span class="sxs-lookup"><span data-stu-id="55a8b-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="55a8b-138">FA</span><span class="sxs-lookup"><span data-stu-id="55a8b-138">FA</span></span><br /><br /> <span data-ttu-id="55a8b-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="55a8b-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="55a8b-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55a8b-140">Remarks</span></span>

<span data-ttu-id="55a8b-141">Użyj specyfikatora formatu, aby utworzyć ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="55a8b-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="55a8b-142">Ciąg formatu ma następującą postać: `Axx`, gdzie</span><span class="sxs-lookup"><span data-stu-id="55a8b-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="55a8b-143">`A` jest specyfikatorem formatu, który kontroluje typ formatowania zastosowanego do wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="55a8b-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="55a8b-144">`xx` jest specyfikatorem dokładności, który ma wpływ na liczbę cyfr w sformatowanym danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="55a8b-145">Wartość specyfikatora dokładności mieści się w zakresie od 0 do 99.</span><span class="sxs-lookup"><span data-stu-id="55a8b-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="55a8b-146">Specyfikatory formatu dziesiętnego ("D" lub "d") i szesnastkowego ("X" lub "x") są obsługiwane tylko dla typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="55a8b-147">Specyfikator formatu rundy ("R" lub "r") jest obsługiwany tylko w przypadku typów <xref:System.Single>, <xref:System.Double>i <xref:System.Numerics.BigInteger>.</span><span class="sxs-lookup"><span data-stu-id="55a8b-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="55a8b-148">Ciągi standardowego formatu liczbowego są obsługiwane przez:</span><span class="sxs-lookup"><span data-stu-id="55a8b-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="55a8b-149">Niektóre przeciążenia metody `ToString` wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="55a8b-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="55a8b-150">Na przykład można podać ciąg formatu liczbowego dla metod <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55a8b-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="55a8b-151">[Funkcja formatowania złożonego](../../../standard/base-types/composite-formatting.md)platformy .NET, obsługiwana przez metodę <xref:System.String.Format%2A?displayProperty=nameWithType>, na przykład.</span><span class="sxs-lookup"><span data-stu-id="55a8b-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="55a8b-152">[Ciągi interpolowane](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="55a8b-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="55a8b-153">Aby uzyskać więcej informacji, zobacz [Standardowe ciągi formatujące](../../../standard/base-types/standard-numeric-format-strings.md)liczby.</span><span class="sxs-lookup"><span data-stu-id="55a8b-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55a8b-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55a8b-154">See also</span></span>

- [<span data-ttu-id="55a8b-155">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="55a8b-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="55a8b-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="55a8b-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="55a8b-157">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="55a8b-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="55a8b-158">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="55a8b-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="55a8b-159">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="55a8b-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="55a8b-160">string</span><span class="sxs-lookup"><span data-stu-id="55a8b-160">string</span></span>](../builtin-types/reference-types.md)
