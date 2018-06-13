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
ms.openlocfilehash: 8ce3b59db027ffebf616a035b018629cb7aed30c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569775"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="dfaec-102">Porady: uzupełnianie liczby zerami prowadzącymi</span><span class="sxs-lookup"><span data-stu-id="dfaec-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="dfaec-103">Można dodać zera wiodące na liczbę całkowitą za pomocą "D" [ciągu standardowego formatu liczbowego](../../../docs/standard/base-types/standard-numeric-format-strings.md) z Specyfikator dokładności.</span><span class="sxs-lookup"><span data-stu-id="dfaec-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="dfaec-104">Można dodać zera wiodące do liczby całkowitej i liczby zmiennoprzecinkowe przy użyciu [ciąg niestandardowego formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="dfaec-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="dfaec-105">W tym temacie pokazano, jak uzupełnianie liczby zerami prowadzącymi przy użyciu obu metod.</span><span class="sxs-lookup"><span data-stu-id="dfaec-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="dfaec-106">Liczba całkowita z zerami określoną długość służących do</span><span class="sxs-lookup"><span data-stu-id="dfaec-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="dfaec-107">Określ minimalną liczbę cyfr ma wartość całkowita do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="dfaec-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="dfaec-108">Dołącz wszystkie wiodące cyfry ten numer.</span><span class="sxs-lookup"><span data-stu-id="dfaec-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="dfaec-109">Określ, czy mają być wyświetlane liczb całkowitych jako wartość dziesiętną lub szesnastkową wartość.</span><span class="sxs-lookup"><span data-stu-id="dfaec-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="dfaec-110">Aby wyświetlić liczb całkowitych jako wartości dziesiętnej, należy wywołać jej `ToString(String)` — metoda i przekazać ciąg "D*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalna długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="dfaec-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="dfaec-111">Aby wyświetlić liczb całkowitych jako wartości szesnastkowej, należy wywołać jej `ToString(String)` — metoda i przekazać ciąg "X*n*" jako wartości `format` parametru, gdzie *n* reprezentuje minimalną długość ciąg.</span><span class="sxs-lookup"><span data-stu-id="dfaec-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="dfaec-112">Umożliwia także ciąg formatu w metodzie, takie jak <xref:System.String.Format%2A> lub <xref:System.Console.WriteLine%2A>, która używa [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dfaec-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="dfaec-113">Poniższy przykład formatuje kilka wartości całkowitych z zerami, dzięki czemu sformatowana liczba całkowita długość co najmniej osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="dfaec-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="dfaec-114">Aby uzupełnić liczbą całkowitą o określonej liczby zer</span><span class="sxs-lookup"><span data-stu-id="dfaec-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="dfaec-115">Określ, ile zera wiodące całkowitą do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="dfaec-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="dfaec-116">Określ, czy mają być wyświetlane liczb całkowitych jako wartość dziesiętną lub szesnastkową wartość.</span><span class="sxs-lookup"><span data-stu-id="dfaec-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="dfaec-117">Formatowanie jej jako wartości dziesiętnej wymaga użycia specyfikator formatu standardowych "D"; Formatowanie go jako wartość szesnastkowa wymaga użycia specyfikator formatu standardowych "X".</span><span class="sxs-lookup"><span data-stu-id="dfaec-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="dfaec-118">Ustalić długość ciągu numerycznego unpadded wywołując wartość całkowita `ToString("D").Length` lub `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="dfaec-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="dfaec-119">Dodanie liczby zer, które chcesz uwzględnić w ciągu sformatowany, długość unpadded ciągu numerycznego.</span><span class="sxs-lookup"><span data-stu-id="dfaec-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="dfaec-120">Definiuje całkowita długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="dfaec-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="dfaec-121">Wywołaj wartość całkowita `ToString(String)` — metoda i przekazać ciąg "D*n*" decimal ciągów i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje sumę długość ciągu wypełniony.</span><span class="sxs-lookup"><span data-stu-id="dfaec-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="dfaec-122">Można również użyć "D*n*" lub "X*n*" ciąg w metodzie, która obsługuje złożone formatowanie formatu.</span><span class="sxs-lookup"><span data-stu-id="dfaec-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="dfaec-123">Poniższy przykład dopełnia całkowitą pięć zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="dfaec-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="dfaec-124">Aby uzupełnić wartość liczbową z zerami określoną długość</span><span class="sxs-lookup"><span data-stu-id="dfaec-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="dfaec-125">Określ liczbę miejsc po przecinku numer ma reprezentację ciągu.</span><span class="sxs-lookup"><span data-stu-id="dfaec-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="dfaec-126">Obejmują wszystkie zera wiodące w tym łączna liczba cyfr.</span><span class="sxs-lookup"><span data-stu-id="dfaec-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="dfaec-127">Zdefiniuj ciąg niestandardowego formatu liczbowego, który używa zero symbolu zastępczego ("0") do reprezentowania minimalnej liczby zer.</span><span class="sxs-lookup"><span data-stu-id="dfaec-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="dfaec-128">Liczba wywołań `ToString(String)` — metoda i przekaż go niestandardowy ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="dfaec-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="dfaec-129">Umożliwia także niestandardowy ciąg formatu za pomocą metody, która obsługuje złożone formatowanie.</span><span class="sxs-lookup"><span data-stu-id="dfaec-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="dfaec-130">Poniższy przykład formatuje kilka wartości liczbowych zerami prowadzącymi tak, aby sformatowana liczba całkowita długość co najmniej osiem miejsc po przecinku.</span><span class="sxs-lookup"><span data-stu-id="dfaec-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="dfaec-131">Aby uzupełnić wartość liczbową z określonej liczby zer</span><span class="sxs-lookup"><span data-stu-id="dfaec-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="dfaec-132">Określ, ile zera wiodące ma wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="dfaec-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="dfaec-133">Określić liczbę miejsc po przecinku w unpadded ciągów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="dfaec-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="dfaec-134">W tym celu:</span><span class="sxs-lookup"><span data-stu-id="dfaec-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="dfaec-135">Ustal, czy reprezentacja ciągu z liczbą zawiera symbol punktu dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="dfaec-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="dfaec-136">Jeśli posiada symbol punktu dziesiętnego, określ liczbę znaków z lewej strony punktu dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="dfaec-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="dfaec-137">—lub—</span><span class="sxs-lookup"><span data-stu-id="dfaec-137">-or-</span></span>  
  
         <span data-ttu-id="dfaec-138">Jeśli nie ma symbolu dziesiętnym, określ długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="dfaec-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="dfaec-139">Utwórz niestandardowy ciąg formatu używającą zero symbolu zastępczego ("0") dla każdego zera wiodące pojawią się w ciągu i używającą do reprezentowania każdej cyfry w domyślny ciąg zastępczy zero lub symbol zastępczy cyfry ("#").</span><span class="sxs-lookup"><span data-stu-id="dfaec-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="dfaec-140">Dostarcza niestandardowy ciąg formatu jako parametr do liczby `ToString(String)` metodę lub metody, która obsługuje złożone formatowanie.</span><span class="sxs-lookup"><span data-stu-id="dfaec-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="dfaec-141">Poniższy przykład dopełnia dwa <xref:System.Double> wartości z pięciu zera wiodące.</span><span class="sxs-lookup"><span data-stu-id="dfaec-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="dfaec-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfaec-142">See Also</span></span>  
 [<span data-ttu-id="dfaec-143">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="dfaec-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="dfaec-144">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="dfaec-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="dfaec-145">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="dfaec-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
