---
title: 'Porady: uzupełnianie liczby zerami prowadzącymi'
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
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131973"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="b7268-102">Porady: uzupełnianie liczby zerami prowadzącymi</span><span class="sxs-lookup"><span data-stu-id="b7268-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="b7268-103">Zera wiodące można dodawać do liczby całkowitej za pomocą [standardowego ciągu formatu numerycznego](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" z precyzyjnym specyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="b7268-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="b7268-104">Można dodać zera wiodące zarówno do liczb całkowitych, jak i zmiennoprzecinkowych, używając [niestandardowego ciągu formatu liczbowego](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="b7268-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="b7268-105">W tym artykule pokazano, jak używać obu metod do pad liczba z zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="b7268-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="b7268-106">Aby podkładki liczby całkowitej z zerami wiodącymi do określonej długości</span><span class="sxs-lookup"><span data-stu-id="b7268-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="b7268-107">Określ minimalną liczbę cyfr, która ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="b7268-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="b7268-108">W tym numerze uwzględnij wszystkie cyfry wiodące.</span><span class="sxs-lookup"><span data-stu-id="b7268-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="b7268-109">Określ, czy liczba całkowita ma być wyświetlana jako wartość dziesiętna, czy szesnastkowa.</span><span class="sxs-lookup"><span data-stu-id="b7268-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="b7268-110">Aby wyświetlić liczbę całkowitą jako wartość dziesiętną, należy wywołać `ToString(String)` jej metodę i przekazać ciąg "D*n"* jako wartość `format` parametru, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="b7268-111">Aby wyświetlić liczbę całkowitą jako wartość szesnastkowa, należy wywołać jej `ToString(String)` metodę i przekazać ciąg "X*n"* jako wartość parametru formatu, gdzie *n* reprezentuje minimalną długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="b7268-112">Można również użyć ciągu formatu w interpolowanym ciągu w [językach C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) <xref:System.String.Format%2A?displayProperty=nameWithType> Basic <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>lub można wywołać metodę, taką jak lub , która używa [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="b7268-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="b7268-113">Poniższy przykład formatuje kilka wartości całkowitych z zerami wiodącymi, dzięki czemu całkowita długość sformatowanej liczby wynosi co najmniej osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="b7268-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="b7268-114">Aby podkładki liczby całkowitej z określoną liczbę zer wiodących</span><span class="sxs-lookup"><span data-stu-id="b7268-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="b7268-115">Określ, ile zer wiodących ma być wyświetlana wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="b7268-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="b7268-116">Określ, czy liczba całkowita ma być wyświetlana jako wartość dziesiętna, czy szesnastkowa.</span><span class="sxs-lookup"><span data-stu-id="b7268-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="b7268-117">Formatowanie go jako wartości dziesiętnej wymaga użycia specyfikatora formatu standardowego "D".</span><span class="sxs-lookup"><span data-stu-id="b7268-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="b7268-118">Formatowanie go jako wartości szesnastkowej wymaga użycia specyfikatora formatu standardowego "X".</span><span class="sxs-lookup"><span data-stu-id="b7268-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="b7268-119">Określ długość niezalanego ciągu liczbowego, wywołując wartość `ToString("D").Length` lub `ToString("X").Length` metodę liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="b7268-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="b7268-120">Dodaj liczbę zer wiodących, które mają zostać uwzględnione w sformatowanym ciągu, do długości niezawiązanego ciągu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="b7268-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="b7268-121">Dodanie liczby zer wiodących definiuje całkowitą długość wyściełanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="b7268-122">Wywołaj `ToString(String)` metodę wartości całkowitej i przekaż ciąg "D*n"* dla ciągów dziesiętnych i "X*n"* dla ciągów szesnastkowych, gdzie *n* reprezentuje całkowitą długość wyściełanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="b7268-123">Można również użyć ciągu formatu "D*n"* lub "X*n"* w metodzie obsługującej formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="b7268-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="b7268-124">Poniższy przykład klocki wartość całkowitą z pięcioma zerami wiodącymi.</span><span class="sxs-lookup"><span data-stu-id="b7268-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="b7268-125">Aby poddać wartość liczbową zerom wiodącym do określonej długości</span><span class="sxs-lookup"><span data-stu-id="b7268-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="b7268-126">Określ, ile cyfr po lewej stronie dziesiętnego ma być reprezentacja ciągu liczby.</span><span class="sxs-lookup"><span data-stu-id="b7268-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="b7268-127">Uwzględnij wszystkie zera wiodące w tej całkowitej liczbie cyfr.</span><span class="sxs-lookup"><span data-stu-id="b7268-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="b7268-128">Zdefiniuj niestandardowy ciąg formatu liczbowego, który używa zero zastępczego symbolu "0" do reprezentowania minimalnej liczby zer.</span><span class="sxs-lookup"><span data-stu-id="b7268-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="b7268-129">Wywołaj `ToString(String)` metodę numeru i przekaż jej ciąg formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b7268-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="b7268-130">Można również użyć niestandardowego ciągu formatu z interpolacją ciągów lub z metodą obsługującym formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="b7268-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="b7268-131">Poniższy przykład formatuje kilka wartości liczbowych z zerami wiodącymi.</span><span class="sxs-lookup"><span data-stu-id="b7268-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="b7268-132">W rezultacie całkowita długość sformatowanej liczby wynosi co najmniej osiem cyfr po lewej stronie miejsca po przecinku.</span><span class="sxs-lookup"><span data-stu-id="b7268-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="b7268-133">Aby poddać wartość liczbową określoną liczbą zer wiodących</span><span class="sxs-lookup"><span data-stu-id="b7268-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="b7268-134">Określ, ile zer wiodących ma mieć wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="b7268-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="b7268-135">Określ liczbę cyfr po lewej stronie dziesiętnego w niezaopatrzonym ciągu liczbowym:</span><span class="sxs-lookup"><span data-stu-id="b7268-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="b7268-136">Określ, czy reprezentacja ciągu liczby zawiera symbol przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="b7268-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="b7268-137">Jeśli zawiera symbol przecinka dziesiętnego, należy określić liczbę znaków po lewej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="b7268-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="b7268-138">— lub —</span><span class="sxs-lookup"><span data-stu-id="b7268-138">-or-</span></span>

         <span data-ttu-id="b7268-139">Jeśli nie zawiera symbolu przecinka dziesiętnego, należy określić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="b7268-140">Utwórz ciąg formatu niestandardowego, który używa:</span><span class="sxs-lookup"><span data-stu-id="b7268-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="b7268-141">Zero symbol zastępczy "0" dla każdego z wiodących zer, które mają być wyświetlane w ciągu.</span><span class="sxs-lookup"><span data-stu-id="b7268-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="b7268-142">Zero symbol zastępczy lub symbol zastępczy cyfry "#" do reprezentowania każdej cyfry w ciągu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b7268-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="b7268-143">Podaj ciąg formatu niestandardowego jako `ToString(String)` parametr do metody liczby lub do metody obsługującej formatowanie złożone.</span><span class="sxs-lookup"><span data-stu-id="b7268-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="b7268-144">Poniższy przykład klocki dwie <xref:System.Double> wartości z pięciu zer wiodących.</span><span class="sxs-lookup"><span data-stu-id="b7268-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="b7268-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7268-145">See also</span></span>

- [<span data-ttu-id="b7268-146">Niestandardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="b7268-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="b7268-147">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="b7268-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="b7268-148">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="b7268-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
