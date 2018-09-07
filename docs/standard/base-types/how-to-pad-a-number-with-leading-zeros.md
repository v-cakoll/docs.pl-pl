---
title: 'Porady: uzupełnianie liczby zerami prowadzącymi'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3cc6e4d96378cfd8c065a3b04aab865f9b787438
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086725"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="a9e39-102">Porady: uzupełnianie liczby zerami prowadzącymi</span><span class="sxs-lookup"><span data-stu-id="a9e39-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="a9e39-103">Można dodać zer wiodących na liczbę całkowitą, za pomocą "D" [standardowy Ciąg formatujący](../../../docs/standard/base-types/standard-numeric-format-strings.md) przy użyciu specyfikatora dokładności.</span><span class="sxs-lookup"><span data-stu-id="a9e39-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="a9e39-104">Można dodać zer wiodących zarówno liczba całkowita, jak i liczb zmiennoprzecinkowych za pomocą [ciąg niestandardowego formatu liczb](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="a9e39-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="a9e39-105">W tym temacie pokazano, jak uzupełnianie liczby zerami wiodącymi za pomocą obu metod.</span><span class="sxs-lookup"><span data-stu-id="a9e39-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="a9e39-106">Aby uzupełnić liczbą całkowitą z wiodącymi zerami w celu określonej długości</span><span class="sxs-lookup"><span data-stu-id="a9e39-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="a9e39-107">Określ minimalną liczbę cyfr, ma wartość całkowitą, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="a9e39-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="a9e39-108">Uwzględnij wszystkie wiodące cyfry w tej liczby.</span><span class="sxs-lookup"><span data-stu-id="a9e39-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="a9e39-109">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="a9e39-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="a9e39-110">Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, należy wywołać jej `ToString(String)` metody i przekazać ciągu "D*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalna długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="a9e39-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="a9e39-111">Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, należy wywołać jej `ToString(String)` metody i przekazać ciągu "X*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalną długość ciąg.</span><span class="sxs-lookup"><span data-stu-id="a9e39-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="a9e39-112">Umożliwia również ciąg formatu w metodzie, takie jak <xref:System.String.Format%2A> lub <xref:System.Console.WriteLine%2A>, który używa [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="a9e39-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="a9e39-113">Poniższy przykład formatuje kilka wartości całkowitych zerami wiodącymi, tak aby łączna długość sformatowany numer jest co najmniej osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="a9e39-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="a9e39-114">Aby uzupełnić liczbą całkowitą z określonej liczby zer wiodących</span><span class="sxs-lookup"><span data-stu-id="a9e39-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="a9e39-115">Określ, ile zer wiodących wartość całkowitą, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="a9e39-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="a9e39-116">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną lub wartości szesnastkowej.</span><span class="sxs-lookup"><span data-stu-id="a9e39-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="a9e39-117">Formatowanie ją jako wartość dziesiętną wymaga użycia specyfikator formatu standardowego "D"; formatowania w postaci szesnastkowej wymaga, że używasz specyfikator formatu standardowego "X".</span><span class="sxs-lookup"><span data-stu-id="a9e39-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="a9e39-118">Określają długość unpadded ciągu numerycznego, wywołując wartość całkowitą `ToString("D").Length` lub `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="a9e39-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="a9e39-119">Dodaj numer zer wiodących, które chcesz uwzględnić w sformatowanym ciągu do długości unpadded ciągów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a9e39-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="a9e39-120">Definiuje całkowita długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="a9e39-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="a9e39-121">Wywołania na wartość całkowitą `ToString(String)` metody i przekazać ciągu "D*n*" dziesiętnych ciągów i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje sumę długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="a9e39-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="a9e39-122">Można również użyć "D*n*" lub "X*n*" sformatować ciąg w metodzie, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="a9e39-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="a9e39-123">Poniższy przykład dopełnia wartość całkowitą z pięciu zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="a9e39-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="a9e39-124">Aby uzupełnić wartość liczbową z wiodącymi zerami w celu określonej długości</span><span class="sxs-lookup"><span data-stu-id="a9e39-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="a9e39-125">Określ liczbę cyfr na lewo od separatora dziesiętnego ciąg reprezentujący liczbę, aby mieć.</span><span class="sxs-lookup"><span data-stu-id="a9e39-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="a9e39-126">Obejmują wszystkie zera wiodące w tym łącznej liczby cyfr.</span><span class="sxs-lookup"><span data-stu-id="a9e39-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="a9e39-127">Zdefiniuj ciąg niestandardowego formatu liczb, który używa symbol zastępczy zero ("0"), który reprezentuje minimalnej liczby zerami.</span><span class="sxs-lookup"><span data-stu-id="a9e39-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="a9e39-128">Zadzwoń na numer `ToString(String)` metody i przekazać ją w ciągu formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a9e39-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="a9e39-129">Umożliwia także ciągu formatu niestandardowego za pomocą metody, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="a9e39-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="a9e39-130">W poniższym przykładzie sformatowano kilka wartości liczbowych zerami wiodącymi, tak aby łączna długość sformatowany numer jest co najmniej ośmiu cyfr na lewo od separatora dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="a9e39-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="a9e39-131">Aby uzupełnić wartość liczbową z określonej liczby zer wiodących</span><span class="sxs-lookup"><span data-stu-id="a9e39-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="a9e39-132">Określ, ile zer wiodących ma wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="a9e39-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="a9e39-133">Liczba cyfr z lewej strony separatora dziesiętnego w ciągu numerycznego unpadded zależy.</span><span class="sxs-lookup"><span data-stu-id="a9e39-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="a9e39-134">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="a9e39-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="a9e39-135">Ustal, czy ciąg reprezentujący liczbę zawiera symbol dziesiętny.</span><span class="sxs-lookup"><span data-stu-id="a9e39-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="a9e39-136">Jeśli posiada symbol punktu dziesiętnego, należy określić liczbę znaków z lewej strony punktu dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="a9e39-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="a9e39-137">—lub—</span><span class="sxs-lookup"><span data-stu-id="a9e39-137">-or-</span></span>  
  
         <span data-ttu-id="a9e39-138">Jeśli nie ma symbol punktu dziesiętnego, należy określić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="a9e39-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="a9e39-139">Utwórz ciąg formatu niestandardowego, który używa symbol zastępczy zero ("0") dla każdego z zer wiodących pojawią się w ciągu i który używa symbol zastępczy zero lub symbol zastępczy cyfry ("#"), który reprezentuje każdej cyfry w domyślny ciąg.</span><span class="sxs-lookup"><span data-stu-id="a9e39-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="a9e39-140">Dostarczyć ciąg formatu niestandardowego jako parametr, albo numeru `ToString(String)` metodę lub metodę, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="a9e39-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="a9e39-141">Poniższy przykład dopełnia dwa <xref:System.Double> wartości z pięciu zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="a9e39-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e39-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9e39-142">See also</span></span>

- [<span data-ttu-id="a9e39-143">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="a9e39-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
- [<span data-ttu-id="a9e39-144">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="a9e39-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
- [<span data-ttu-id="a9e39-145">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="a9e39-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
