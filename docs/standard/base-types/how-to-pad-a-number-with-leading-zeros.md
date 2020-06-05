---
title: 'Instrukcje: Uzupełnianie liczby zerami wiodącymi'
description: Dowiedz się, jak dowiedzieć się, jak uzupełniać liczbę wiodącymi zerami. Dodaj Wiodące zera do liczb całkowitych lub wartości liczbowych, aby uzyskać określoną całkowitą długość lub określoną liczbę zer wiodących.
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
ms.openlocfilehash: 6ef0ddb37f1bc73254aa639d7c018ec6a01abd9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447189"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="49e7e-104">Instrukcje: Uzupełnianie liczby zerami wiodącymi</span><span class="sxs-lookup"><span data-stu-id="49e7e-104">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="49e7e-105">Można dodać Wiodące zera do liczby całkowitej przy użyciu [standardowego ciągu formatu liczbowego](standard-numeric-format-strings.md) "D" ze specyfikatorem dokładności.</span><span class="sxs-lookup"><span data-stu-id="49e7e-105">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="49e7e-106">Można dodać Wiodące zera do liczb całkowitych i zmiennoprzecinkowych przy użyciu [niestandardowego ciągu formatu liczbowego](custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="49e7e-106">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="49e7e-107">W tym artykule pokazano, jak używać obu metod do uzupełniania liczby wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="49e7e-107">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="49e7e-108">Aby uzupełnić liczbę całkowitą wiodącymi zerami do określonej długości</span><span class="sxs-lookup"><span data-stu-id="49e7e-108">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="49e7e-109">Określ minimalną liczbę cyfr, jaka ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="49e7e-109">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="49e7e-110">Dołącz wszystkie znaki wiodące w tej liczbie.</span><span class="sxs-lookup"><span data-stu-id="49e7e-110">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="49e7e-111">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="49e7e-111">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="49e7e-112">Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, wywołaj `ToString(String)` metodę i przekaż ciąg "D*n*" jako wartość `format` parametru, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-112">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="49e7e-113">Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, wywołaj `ToString(String)` metodę i przekaż ciąg "X*n*" jako wartość parametru formatu, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-113">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="49e7e-114">Możesz również użyć ciągu w formacie interpolowanym w [języku C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)lub wywołać metodę, taką jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , która używa [formatowania złożonego](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="49e7e-114">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="49e7e-115">Poniższy przykład formatuje kilka wartości całkowitych wiodących zer, tak aby łączna długość sformatowanej liczby była co najmniej 8 znaków.</span><span class="sxs-lookup"><span data-stu-id="49e7e-115">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="49e7e-116">Aby uzupełnić liczbę całkowitą z określoną liczbą zer wiodących</span><span class="sxs-lookup"><span data-stu-id="49e7e-116">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="49e7e-117">Określ, ile wiodących zer ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="49e7e-117">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="49e7e-118">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="49e7e-118">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="49e7e-119">Formatowanie go jako wartości dziesiętnej wymaga użycia specyfikatora formatu standardowego "D".</span><span class="sxs-lookup"><span data-stu-id="49e7e-119">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="49e7e-120">Formatowanie go jako wartości szesnastkowej wymaga użycia specyfikatora formatu standardowego "X".</span><span class="sxs-lookup"><span data-stu-id="49e7e-120">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="49e7e-121">Ustal długość nieuzupełnionego ciągu liczbowego, wywołując wartość typu Integer `ToString("D").Length` lub `ToString("X").Length` metodę.</span><span class="sxs-lookup"><span data-stu-id="49e7e-121">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="49e7e-122">Dodaj liczbę zer wiodących, które mają być uwzględnione w ciągu sformatowanym do długości nieuzupełnionego ciągu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="49e7e-122">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="49e7e-123">Dodanie liczby zer wiodących określa łączną długość uzupełnionego ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-123">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="49e7e-124">Wywołaj metodę wartości całkowitej `ToString(String)` i przekaż ciąg "D*n*" dla ciągów dziesiętnych i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje łączną długość uzupełnionego ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-124">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="49e7e-125">Można również użyć ciągu formatu "D*n*" lub "X*n*" w metodzie, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="49e7e-125">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="49e7e-126">Poniższy przykład ilustruje liczbę całkowitą z pięciu wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="49e7e-126">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="49e7e-127">Aby uzupełnić wartość liczbową wiodącymi zerami do określonej długości</span><span class="sxs-lookup"><span data-stu-id="49e7e-127">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="49e7e-128">Określ liczbę cyfr po lewej stronie przecinka dziesiętnego, w ciągu którego ma zostać wystawiona liczba.</span><span class="sxs-lookup"><span data-stu-id="49e7e-128">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="49e7e-129">Dołącz wszystkie zera wiodące w tej łącznej liczbie cyfr.</span><span class="sxs-lookup"><span data-stu-id="49e7e-129">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="49e7e-130">Zdefiniuj niestandardowy ciąg formatu liczbowego, który używa symbolu zastępczego zero "0" do reprezentowania minimalnej liczby zer.</span><span class="sxs-lookup"><span data-stu-id="49e7e-130">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="49e7e-131">Wywołaj metodę Number `ToString(String)` i przekaż ją do niestandardowym ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-131">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="49e7e-132">Można również użyć niestandardowego ciągu formatu z interpolacją ciągu lub metodą, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="49e7e-132">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="49e7e-133">Poniższy przykład formatuje kilka wartości liczbowych z zerami wiodącymi.</span><span class="sxs-lookup"><span data-stu-id="49e7e-133">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="49e7e-134">W związku z tym łączna długość sformatowanej liczby ma co najmniej osiem cyfr z lewej strony dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="49e7e-134">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="49e7e-135">Aby uzupełnić wartość numeryczną określoną liczbą zer wiodących</span><span class="sxs-lookup"><span data-stu-id="49e7e-135">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="49e7e-136">Określ, ile wiodących zer ma mieć wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="49e7e-136">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="49e7e-137">Określ liczbę cyfr po lewej stronie przecinka dziesiętnego w nieuzupełnionym ciągu liczbowym:</span><span class="sxs-lookup"><span data-stu-id="49e7e-137">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="49e7e-138">Ustal, czy ciąg reprezentujący liczbę zawiera symbol separatora dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="49e7e-138">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="49e7e-139">Jeśli zawiera symbol separatora dziesiętnego, należy określić liczbę znaków po lewej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="49e7e-139">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="49e7e-140">-lub-</span><span class="sxs-lookup"><span data-stu-id="49e7e-140">-or-</span></span>

         <span data-ttu-id="49e7e-141">Jeśli nie zawiera symbolu punktu dziesiętnego, ustal długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-141">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="49e7e-142">Utwórz niestandardowy ciąg formatujący, który używa:</span><span class="sxs-lookup"><span data-stu-id="49e7e-142">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="49e7e-143">Symbol zastępczy zero "0" dla każdego wiodącego zera, który ma być wyświetlany w ciągu.</span><span class="sxs-lookup"><span data-stu-id="49e7e-143">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="49e7e-144">Symbol zastępczy zero lub symbol zastępczy cyfry "#" reprezentujący każdą cyfrę w postaci ciągu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="49e7e-144">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="49e7e-145">Podaj ciąg formatu niestandardowego jako parametr do `ToString(String)` metody Number lub do metody, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="49e7e-145">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="49e7e-146">W poniższym przykładzie są umieszczane dwie <xref:System.Double> wartości z pięciu wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="49e7e-146">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="49e7e-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49e7e-147">See also</span></span>

- [<span data-ttu-id="49e7e-148">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="49e7e-148">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="49e7e-149">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="49e7e-149">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="49e7e-150">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="49e7e-150">Composite Formatting</span></span>](composite-formatting.md)
