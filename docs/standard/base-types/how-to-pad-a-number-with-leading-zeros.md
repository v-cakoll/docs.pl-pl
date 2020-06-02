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
ms.openlocfilehash: ef18fb1bb7b1592a4e92866028868bf1cf793bbf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290464"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="2a4ad-102">Instrukcje: Uzupełnianie liczby zerami wiodącymi</span><span class="sxs-lookup"><span data-stu-id="2a4ad-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="2a4ad-103">Można dodać Wiodące zera do liczby całkowitej przy użyciu [standardowego ciągu formatu liczbowego](standard-numeric-format-strings.md) "D" ze specyfikatorem dokładności.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="2a4ad-104">Można dodać Wiodące zera do liczb całkowitych i zmiennoprzecinkowych przy użyciu [niestandardowego ciągu formatu liczbowego](custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="2a4ad-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="2a4ad-105">W tym artykule pokazano, jak używać obu metod do uzupełniania liczby wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="2a4ad-106">Aby uzupełnić liczbę całkowitą wiodącymi zerami do określonej długości</span><span class="sxs-lookup"><span data-stu-id="2a4ad-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="2a4ad-107">Określ minimalną liczbę cyfr, jaka ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="2a4ad-108">Dołącz wszystkie znaki wiodące w tej liczbie.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="2a4ad-109">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="2a4ad-110">Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, wywołaj `ToString(String)` metodę i przekaż ciąg "D*n*" jako wartość `format` parametru, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="2a4ad-111">Aby wyświetlić liczbę całkowitą jako wartość szesnastkową, wywołaj `ToString(String)` metodę i przekaż ciąg "X*n*" jako wartość parametru formatu, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="2a4ad-112">Możesz również użyć ciągu w formacie interpolowanym w [języku C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)lub wywołać metodę, taką jak <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , która używa [formatowania złożonego](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="2a4ad-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="2a4ad-113">Poniższy przykład formatuje kilka wartości całkowitych wiodących zer, tak aby łączna długość sformatowanej liczby była co najmniej 8 znaków.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="2a4ad-114">Aby uzupełnić liczbę całkowitą z określoną liczbą zer wiodących</span><span class="sxs-lookup"><span data-stu-id="2a4ad-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="2a4ad-115">Określ, ile wiodących zer ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="2a4ad-116">Określ, czy chcesz wyświetlić liczbę całkowitą jako wartość dziesiętną, czy wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="2a4ad-117">Formatowanie go jako wartości dziesiętnej wymaga użycia specyfikatora formatu standardowego "D".</span><span class="sxs-lookup"><span data-stu-id="2a4ad-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="2a4ad-118">Formatowanie go jako wartości szesnastkowej wymaga użycia specyfikatora formatu standardowego "X".</span><span class="sxs-lookup"><span data-stu-id="2a4ad-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="2a4ad-119">Ustal długość nieuzupełnionego ciągu liczbowego, wywołując wartość typu Integer `ToString("D").Length` lub `ToString("X").Length` metodę.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="2a4ad-120">Dodaj liczbę zer wiodących, które mają być uwzględnione w ciągu sformatowanym do długości nieuzupełnionego ciągu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="2a4ad-121">Dodanie liczby zer wiodących określa łączną długość uzupełnionego ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="2a4ad-122">Wywołaj metodę wartości całkowitej `ToString(String)` i przekaż ciąg "D*n*" dla ciągów dziesiętnych i "X*n*" dla ciągów szesnastkowych, gdzie *n* reprezentuje łączną długość uzupełnionego ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="2a4ad-123">Można również użyć ciągu formatu "D*n*" lub "X*n*" w metodzie, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="2a4ad-124">Poniższy przykład ilustruje liczbę całkowitą z pięciu wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="2a4ad-125">Aby uzupełnić wartość liczbową wiodącymi zerami do określonej długości</span><span class="sxs-lookup"><span data-stu-id="2a4ad-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="2a4ad-126">Określ liczbę cyfr po lewej stronie przecinka dziesiętnego, w ciągu którego ma zostać wystawiona liczba.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="2a4ad-127">Dołącz wszystkie zera wiodące w tej łącznej liczbie cyfr.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="2a4ad-128">Zdefiniuj niestandardowy ciąg formatu liczbowego, który używa symbolu zastępczego zero "0" do reprezentowania minimalnej liczby zer.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="2a4ad-129">Wywołaj metodę Number `ToString(String)` i przekaż ją do niestandardowym ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="2a4ad-130">Można również użyć niestandardowego ciągu formatu z interpolacją ciągu lub metodą, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="2a4ad-131">Poniższy przykład formatuje kilka wartości liczbowych z zerami wiodącymi.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="2a4ad-132">W związku z tym łączna długość sformatowanej liczby ma co najmniej osiem cyfr z lewej strony dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="2a4ad-133">Aby uzupełnić wartość numeryczną określoną liczbą zer wiodących</span><span class="sxs-lookup"><span data-stu-id="2a4ad-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="2a4ad-134">Określ, ile wiodących zer ma mieć wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="2a4ad-135">Określ liczbę cyfr po lewej stronie przecinka dziesiętnego w nieuzupełnionym ciągu liczbowym:</span><span class="sxs-lookup"><span data-stu-id="2a4ad-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="2a4ad-136">Ustal, czy ciąg reprezentujący liczbę zawiera symbol separatora dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="2a4ad-137">Jeśli zawiera symbol separatora dziesiętnego, należy określić liczbę znaków po lewej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="2a4ad-138">-lub-</span><span class="sxs-lookup"><span data-stu-id="2a4ad-138">-or-</span></span>

         <span data-ttu-id="2a4ad-139">Jeśli nie zawiera symbolu punktu dziesiętnego, ustal długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="2a4ad-140">Utwórz niestandardowy ciąg formatujący, który używa:</span><span class="sxs-lookup"><span data-stu-id="2a4ad-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="2a4ad-141">Symbol zastępczy zero "0" dla każdego wiodącego zera, który ma być wyświetlany w ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="2a4ad-142">Symbol zastępczy zero lub symbol zastępczy cyfry "#" reprezentujący każdą cyfrę w postaci ciągu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="2a4ad-143">Podaj ciąg formatu niestandardowego jako parametr do `ToString(String)` metody Number lub do metody, która obsługuje formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="2a4ad-144">W poniższym przykładzie są umieszczane dwie <xref:System.Double> wartości z pięciu wiodących zer.</span><span class="sxs-lookup"><span data-stu-id="2a4ad-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="2a4ad-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a4ad-145">See also</span></span>

- [<span data-ttu-id="2a4ad-146">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="2a4ad-146">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="2a4ad-147">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="2a4ad-147">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="2a4ad-148">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="2a4ad-148">Composite Formatting</span></span>](composite-formatting.md)
