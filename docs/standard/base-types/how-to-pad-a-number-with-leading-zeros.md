---
title: 'Instrukcje: Uzupełnianie liczby zerami wiodącymi'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd016bcb1484f7f94e509e79dbb6b9bb982dd96a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972560"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="12ac5-102">Instrukcje: Uzupełnianie liczby zerami wiodącymi</span><span class="sxs-lookup"><span data-stu-id="12ac5-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="12ac5-103">Można dodać zer wiodących na liczbę całkowitą, za pomocą "D" [standardowy Ciąg formatujący](../../../docs/standard/base-types/standard-numeric-format-strings.md) przy użyciu specyfikatora dokładności.</span><span class="sxs-lookup"><span data-stu-id="12ac5-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="12ac5-104">Można dodać zer wiodących zarówno liczba całkowita, jak i liczb zmiennoprzecinkowych za pomocą [ciąg niestandardowego formatu liczb](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="12ac5-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="12ac5-105">W tym artykule pokazano, jak uzupełnianie liczby zerami wiodącymi za pomocą obu metod.</span><span class="sxs-lookup"><span data-stu-id="12ac5-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>
  
## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="12ac5-106">Aby uzupełnić liczbą całkowitą z wiodącymi zerami w celu określonej długości</span><span class="sxs-lookup"><span data-stu-id="12ac5-106">To pad an integer with leading zeros to a specific length</span></span>
  
1. <span data-ttu-id="12ac5-107">Określ minimalną liczbę cyfr, ma wartość całkowitą, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="12ac5-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="12ac5-108">Uwzględnij wszystkie wiodące cyfry w tej liczby.</span><span class="sxs-lookup"><span data-stu-id="12ac5-108">Include any leading digits in this number.</span></span>  
  
1. <span data-ttu-id="12ac5-109">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="12ac5-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    - <span data-ttu-id="12ac5-110">Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, należy wywołać jej `ToString(String)` metody i przekazać ciągu "D*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalna długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ac5-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    - <span data-ttu-id="12ac5-111">Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, należy wywołać jej `ToString(String)` metody i przekazać ciągu "X*n*" jako wartości parametru formatu, gdzie *n* reprezentuje minimalna długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ac5-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>
  
<span data-ttu-id="12ac5-112">Umożliwia również ciąg formatu w ciągu interpolowanym zarówno [ C# ](../../csharp/language-reference/tokens/interpolated.md) i [języka Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), lub można wywołać metodę, takich jak <xref:System.String.Format%2A?displayProperty=nameWithtype> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, używającej [ Formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="12ac5-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithtype> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="12ac5-113">Poniższy przykład formatuje kilka wartości całkowitych zerami wiodącymi, tak aby łączna długość sformatowany numer jest co najmniej osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="12ac5-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="12ac5-114">Aby uzupełnić liczbą całkowitą z określonej liczby zer wiodących</span><span class="sxs-lookup"><span data-stu-id="12ac5-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1. <span data-ttu-id="12ac5-115">Określ, ile zer wiodących wartość całkowitą, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="12ac5-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
1. <span data-ttu-id="12ac5-116">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="12ac5-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="12ac5-117">Formatowanie ją jako wartość dziesiętną wymaga, że używasz specyfikator formatu standardowego "D".</span><span class="sxs-lookup"><span data-stu-id="12ac5-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="12ac5-118">Formatowania w postaci szesnastkowej wymaga, że używasz specyfikator formatu standardowego "X".</span><span class="sxs-lookup"><span data-stu-id="12ac5-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>
  
1. <span data-ttu-id="12ac5-119">Określają długość unpadded ciągu numerycznego, wywołując wartość całkowitą `ToString("D").Length` lub `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="12ac5-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>
  
1. <span data-ttu-id="12ac5-120">Dodaj numer zer wiodących, które chcesz uwzględnić w sformatowanym ciągu do długości unpadded ciągów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="12ac5-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="12ac5-121">Dodanie liczby zer wiodących definiuje całkowita długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="12ac5-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>  
  
1. <span data-ttu-id="12ac5-122">Wywołania na wartość całkowitą `ToString(String)` metody i przekazać ciągu "D*n*" dziesiętnych ciągów i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje sumę długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="12ac5-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="12ac5-123">Można również użyć "D*n*" lub "X*n*" sformatować ciąg w metodzie, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="12ac5-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="12ac5-124">Poniższy przykład dopełnia wartość całkowitą z pięciu zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="12ac5-124">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="12ac5-125">Aby uzupełnić wartość liczbową z wiodącymi zerami w celu określonej długości</span><span class="sxs-lookup"><span data-stu-id="12ac5-125">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1. <span data-ttu-id="12ac5-126">Określ liczbę cyfr na lewo od separatora dziesiętnego ciąg reprezentujący liczbę, aby mieć.</span><span class="sxs-lookup"><span data-stu-id="12ac5-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="12ac5-127">Obejmują wszystkie zera wiodące w tym łącznej liczby cyfr.</span><span class="sxs-lookup"><span data-stu-id="12ac5-127">Include any leading zeros in this total number of digits.</span></span>  
  
1. <span data-ttu-id="12ac5-128">Zdefiniuj ciąg niestandardowego formatu liczb, który używa symbol zastępczy zero "0", który reprezentuje minimalnej liczby zerami.</span><span class="sxs-lookup"><span data-stu-id="12ac5-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>  
  
1. <span data-ttu-id="12ac5-129">Zadzwoń na numer `ToString(String)` metody i przekazać ją w ciągu formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="12ac5-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="12ac5-130">Umożliwia także ciągu formatu niestandardowego Interpolacja ciągów lub z metodą, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="12ac5-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="12ac5-131">W poniższym przykładzie sformatowano kilka wartości liczbowych z zerami.</span><span class="sxs-lookup"><span data-stu-id="12ac5-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="12ac5-132">Dlatego całkowita długość sformatowany numer jest co najmniej ośmiu cyfr na lewo od separatora dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="12ac5-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="12ac5-133">Aby uzupełnić wartość liczbową z określonej liczby zer wiodących</span><span class="sxs-lookup"><span data-stu-id="12ac5-133">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1. <span data-ttu-id="12ac5-134">Określ, ile zer wiodących ma wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="12ac5-134">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
1. <span data-ttu-id="12ac5-135">Określ liczbę cyfr na lewo od separatora dziesiętnego w ciągu numerycznego unpadded:</span><span class="sxs-lookup"><span data-stu-id="12ac5-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>  
  
    1. <span data-ttu-id="12ac5-136">Ustal, czy ciąg reprezentujący liczbę zawiera symbol dziesiętny.</span><span class="sxs-lookup"><span data-stu-id="12ac5-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    1. <span data-ttu-id="12ac5-137">Jeśli posiada symbol punktu dziesiętnego, należy określić liczbę znaków z lewej strony punktu dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="12ac5-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="12ac5-138">—lub—</span><span class="sxs-lookup"><span data-stu-id="12ac5-138">-or-</span></span>  
  
         <span data-ttu-id="12ac5-139">Jeśli nie zawiera symbol punktu dziesiętnego, należy określić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ac5-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>  
  
1. <span data-ttu-id="12ac5-140">Utwórz ciąg formatu niestandardowego, który używa:</span><span class="sxs-lookup"><span data-stu-id="12ac5-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="12ac5-141">Symbol zastępczy zero "0" dla każdego z zer wiodących pojawią się w ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ac5-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="12ac5-142">Symbol zastępczy zero albo symbol zastępczy cyfry "#" do reprezentowania każdej cyfry w domyślnego ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ac5-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>
  
1. <span data-ttu-id="12ac5-143">Dostarczyć ciąg formatu niestandardowego jako parametr, albo numeru `ToString(String)` metodę lub metodę, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="12ac5-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="12ac5-144">Poniższy przykład dopełnia dwa <xref:System.Double> wartości z pięciu zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="12ac5-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="12ac5-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ac5-145">See also</span></span>

- [<span data-ttu-id="12ac5-146">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="12ac5-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="12ac5-147">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="12ac5-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="12ac5-148">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="12ac5-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
