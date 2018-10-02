---
title: Formatowanie tabeli wyników liczbowych (odwołanie w C#)
description: Dowiedz się więcej o języku C# standardowe ciągi formatujące liczby
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 6f1cb5b49139cf9661e678cfc0ecc884a2749622
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863705"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="40481-103">Formatowanie tabeli wyników liczbowych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="40481-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="40481-104">W poniższej tabeli przedstawiono specyfikatory formatu obsługiwanych formatowania wyników liczbowych.</span><span class="sxs-lookup"><span data-stu-id="40481-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="40481-105">Sformatowany wynik w ostatniej kolumnie odnosi się do "en US" <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="40481-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="40481-106">Specyfikator formatu</span><span class="sxs-lookup"><span data-stu-id="40481-106">Format specifier</span></span>|<span data-ttu-id="40481-107">Opis</span><span class="sxs-lookup"><span data-stu-id="40481-107">Description</span></span>|<span data-ttu-id="40481-108">Przykłady</span><span class="sxs-lookup"><span data-stu-id="40481-108">Examples</span></span>|<span data-ttu-id="40481-109">Wynik</span><span class="sxs-lookup"><span data-stu-id="40481-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="40481-110">C lub c</span><span class="sxs-lookup"><span data-stu-id="40481-110">C or c</span></span>|<span data-ttu-id="40481-111">Waluta</span><span class="sxs-lookup"><span data-stu-id="40481-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="40481-112">$2.50</span><span class="sxs-lookup"><span data-stu-id="40481-112">$2.50</span></span><br /><br /> <span data-ttu-id="40481-113">($2.50)</span><span class="sxs-lookup"><span data-stu-id="40481-113">($2.50)</span></span>|  
|<span data-ttu-id="40481-114">D lub d</span><span class="sxs-lookup"><span data-stu-id="40481-114">D or d</span></span>|<span data-ttu-id="40481-115">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="40481-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="40481-116">00025</span><span class="sxs-lookup"><span data-stu-id="40481-116">00025</span></span>|  
|<span data-ttu-id="40481-117">E lub e</span><span class="sxs-lookup"><span data-stu-id="40481-117">E or e</span></span>|<span data-ttu-id="40481-118">Wykładnicza</span><span class="sxs-lookup"><span data-stu-id="40481-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="40481-119">2.50E + 005</span><span class="sxs-lookup"><span data-stu-id="40481-119">2.50E+005</span></span>|  
|<span data-ttu-id="40481-120">F lub f</span><span class="sxs-lookup"><span data-stu-id="40481-120">F or f</span></span>|<span data-ttu-id="40481-121">Wartość stałoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="40481-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="40481-122">2.50</span><span class="sxs-lookup"><span data-stu-id="40481-122">2.50</span></span><br /><br /> <span data-ttu-id="40481-123">3</span><span class="sxs-lookup"><span data-stu-id="40481-123">3</span></span>|  
|<span data-ttu-id="40481-124">G lub g</span><span class="sxs-lookup"><span data-stu-id="40481-124">G or g</span></span>|<span data-ttu-id="40481-125">Ogólne</span><span class="sxs-lookup"><span data-stu-id="40481-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="40481-126">2.5</span><span class="sxs-lookup"><span data-stu-id="40481-126">2.5</span></span>|  
|<span data-ttu-id="40481-127">N lub n</span><span class="sxs-lookup"><span data-stu-id="40481-127">N or n</span></span>|<span data-ttu-id="40481-128">Numeryczne</span><span class="sxs-lookup"><span data-stu-id="40481-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="40481-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="40481-129">2,500,000.00</span></span>|  
|<span data-ttu-id="40481-130">P lub p</span><span class="sxs-lookup"><span data-stu-id="40481-130">P or p</span></span>|<span data-ttu-id="40481-131">Wartość procentowa</span><span class="sxs-lookup"><span data-stu-id="40481-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="40481-132">% 25,00</span><span class="sxs-lookup"><span data-stu-id="40481-132">25.00%</span></span>|  
|<span data-ttu-id="40481-133">R lub r</span><span class="sxs-lookup"><span data-stu-id="40481-133">R or r</span></span>|<span data-ttu-id="40481-134">Wartość dwustronna</span><span class="sxs-lookup"><span data-stu-id="40481-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="40481-135">2.5</span><span class="sxs-lookup"><span data-stu-id="40481-135">2.5</span></span>|  
|<span data-ttu-id="40481-136">X lub x</span><span class="sxs-lookup"><span data-stu-id="40481-136">X or x</span></span>|<span data-ttu-id="40481-137">Wartość szesnastkowa</span><span class="sxs-lookup"><span data-stu-id="40481-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="40481-138">FA</span><span class="sxs-lookup"><span data-stu-id="40481-138">FA</span></span><br /><br /> <span data-ttu-id="40481-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="40481-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="40481-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40481-140">Remarks</span></span>

<span data-ttu-id="40481-141">Specyfikator formatu umożliwia tworzenie ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="40481-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="40481-142">Ciąg formatu ma następującą postać: `Axx`, gdzie</span><span class="sxs-lookup"><span data-stu-id="40481-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="40481-143">`A` to specyfikator formatu, który określa typ sformatowane na wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="40481-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="40481-144">`xx` jest Specyfikator dokładności, który wpływa na liczbę cyfr w sformatowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="40481-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="40481-145">Wartość zakresu Specyfikator dokładności, od 0 do 99.</span><span class="sxs-lookup"><span data-stu-id="40481-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="40481-146">Dziesiętnego ("D" lub "d") i formatu szesnastkowego ("X" lub "x") specyfikatory są obsługiwane tylko w przypadku typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="40481-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="40481-147">Obustronne specyfikator formatu ("R" lub "r") jest obsługiwana tylko w przypadku <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger> typów.</span><span class="sxs-lookup"><span data-stu-id="40481-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="40481-148">Ciągi standardowego formatu liczb są obsługiwane przez:</span><span class="sxs-lookup"><span data-stu-id="40481-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="40481-149">Niektóre przeciążenia `ToString` metoda wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="40481-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="40481-150">Na przykład można podać ciąg w formacie liczbowym do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="40481-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="40481-151">.NET [funkcję formatowania złożonego](../../../standard/base-types/composite-formatting.md), które są obsługiwane przez <xref:System.String.Format%2A?displayProperty=nameWithType> metody, na przykład.</span><span class="sxs-lookup"><span data-stu-id="40481-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="40481-152">[Ciągi interpolowane](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="40481-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="40481-153">Aby uzyskać więcej informacji, zobacz [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="40481-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40481-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40481-154">See also</span></span>

- [<span data-ttu-id="40481-155">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="40481-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40481-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="40481-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40481-157">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="40481-157">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="40481-158">Formatowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="40481-158">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="40481-159">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="40481-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="40481-160">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="40481-160">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="40481-161">string</span><span class="sxs-lookup"><span data-stu-id="40481-161">string</span></span>](string.md)
