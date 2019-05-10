---
title: Interpolacja ciągów w języku C#
description: Dowiedz się, jak obejmują wyrażenie sformatowane wyniki w ciągu wynikowym w języku C# przy użyciu interpolacji ciągu.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 068a30bdcb96140787a38e9ae52f9c62d8a57c96
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063230"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="f5550-103">Interpolacja ciągów w języku C\#</span><span class="sxs-lookup"><span data-stu-id="f5550-103">String interpolation in C\#</span></span>

<span data-ttu-id="f5550-104">W tym samouczku dowiesz się, jak używać [Interpolacja ciągów](../language-reference/tokens/interpolated.md) do formatu i Dołącz wyniki wyrażenia w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="f5550-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="f5550-105">W przykładach założono, że znasz podstawowe pojęcia języka C# i .NET typu formatowania.</span><span class="sxs-lookup"><span data-stu-id="f5550-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="f5550-106">Jeśli jesteś nowym użytkownikiem Interpolacja ciągów lub formatowanie typu .NET, zapoznaj się z [samouczek interpolacji ciągu interaktywne](exploration/interpolated-strings.yml) pierwszy.</span><span class="sxs-lookup"><span data-stu-id="f5550-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="f5550-107">Aby uzyskać więcej informacji na temat typy formatowania w programie .NET, zobacz [typy formatowania na platformie .NET](../../standard/base-types/formatting-types.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f5550-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="f5550-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f5550-108">Introduction</span></span>

<span data-ttu-id="f5550-109">[Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja jest wbudowana w górnej części [formatowania złożonego](../../standard/base-types/composite-formatting.md) funkcji i zapewnia bardziej czytelne i wygodne składni obejmujący wyrażenie sformatowane wyniki w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="f5550-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="f5550-110">Aby zidentyfikować literał ciągu zgodny z ciągu interpolowanego, dodaj ją za pomocą `$` symboli.</span><span class="sxs-lookup"><span data-stu-id="f5550-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="f5550-111">Możesz osadzić dowolne prawidłowe C# wyrażenie zwracające wartość w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="f5550-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="f5550-112">W poniższym przykładzie tak szybko, jak wyrażenie jest obliczane, wynik jest konwertowana na ciąg i zawarte w ciągu wynikowym:</span><span class="sxs-lookup"><span data-stu-id="f5550-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="f5550-113">Jak pokazano w przykładzie, dołączysz wyrażenia w ciągu interpolowanym umieszczając go w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="f5550-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="f5550-114">Ciągi interpolowane obsługują wszystkie funkcje [ciągu formatowania złożonego](../../standard/base-types/composite-formatting.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f5550-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="f5550-115">Dzięki temu ich czytelność alternatywą do korzystania z <xref:System.String.Format%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f5550-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="f5550-116">Jak określić ciąg formatu dla wyrażenia interpolowanego</span><span class="sxs-lookup"><span data-stu-id="f5550-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="f5550-117">Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, postępując zgodnie z wyrażenia interpolowanego z dwukropkiem (":") i ciąg formatu:</span><span class="sxs-lookup"><span data-stu-id="f5550-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="f5550-118">Poniższy przykład pokazuje, jak określić ciągi formatów standardowych i niestandardowych wyrażeń, które tworzą daty i godziny lub wyników liczbowych:</span><span class="sxs-lookup"><span data-stu-id="f5550-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="f5550-119">Aby uzyskać więcej informacji, zobacz [element ciągu formatującego](../../standard/base-types/composite-formatting.md#format-string-component) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f5550-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="f5550-120">Tę sekcję zawiera łącza do tematów opisujących ciągów formatu standardowego i niestandardowego obsługiwanych przez typów podstawowych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="f5550-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="f5550-121">Jak kontrolować szerokość pola i wyrównanie sformatowanego wyrażenia interpolowanego</span><span class="sxs-lookup"><span data-stu-id="f5550-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="f5550-122">Określ szerokość minimalna pola i wyrównanie wyniku wyrażenia sformatowane postępując zgodnie z wyrażenia interpolowanego za pomocą przecinka (",") i wyrażenie stałe:</span><span class="sxs-lookup"><span data-stu-id="f5550-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="f5550-123">Jeśli *wyrównanie* wartość jest dodatnia, wynik wyrażenia sformatowane jest wyrównany do prawej; Jeśli jest negatywny, jest wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="f5550-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="f5550-124">Jeśli musisz określić wyrównania i ciąg formatu, rozpoczynać składnik wyrównania:</span><span class="sxs-lookup"><span data-stu-id="f5550-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="f5550-125">Poniższy przykład pokazuje, jak określić wyrównania i używa potoku znaków ("|") do rozdzielenia pól tekstowych:</span><span class="sxs-lookup"><span data-stu-id="f5550-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="f5550-126">Jako przykład przedstawiono dane wyjściowe, jeśli długość wyniku wyrażenia sformatowane przekracza określony szerokość pola *wyrównanie* wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="f5550-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="f5550-127">Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../standard/base-types/composite-formatting.md#alignment-component) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f5550-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="f5550-128">Jak używać sekwencje ucieczki w ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="f5550-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="f5550-129">Ciągi interpolowane obsługuje wszystkie sekwencje unikowe, które mogą być używane w literałach ciągu zwykłego.</span><span class="sxs-lookup"><span data-stu-id="f5550-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="f5550-130">Aby uzyskać więcej informacji, zobacz [sekwencje ucieczki w ciągu](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="f5550-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="f5550-131">Aby interpretowany dosłownie sekwencje ucieczki, należy użyć [verbatim](../language-reference/tokens/verbatim.md) literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="f5550-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="f5550-132">Ciąg verbatim interpolowane zaczyna się od `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="f5550-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="f5550-133">Aby uwzględnić nawiasu klamrowego, "{" lub "}", w ciągu wynikowym, użyj dwóch nawiasów klamrowych, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="f5550-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="f5550-134">Aby uzyskać więcej informacji, zobacz [anulowania zapewnianego element nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) części [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f5550-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="f5550-135">Poniższy przykład pokazuje, jak dołączyć nawiasy klamrowe w ciągu wynikowym i konstruowania verbatim ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="f5550-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="f5550-136">Jak używać trójargumentowy operator warunkowy `?:` w wyrażenie interpolowane</span><span class="sxs-lookup"><span data-stu-id="f5550-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="f5550-137">Jako dwukropkiem (":") ma specjalne znaczenie w elemencie z wyrażenia interpolowanego, aby można było używać [operator warunkowy](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ją ująć w nawiasy, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="f5550-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="f5550-138">Jak utworzyć ciąg wynikowy specyficzne dla kultury za pomocą Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="f5550-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="f5550-139">Domyślnie ciągu interpolowanego używa bieżącej kultury, które są definiowane przez <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> właściwości dla wszystkich operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="f5550-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="f5550-140">Użyj niejawnej konwersji ciągu interpolowanego do <xref:System.FormattableString?displayProperty=nameWithType> wystąpienie i wywołania jego <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby utworzyć ciąg wynikowy specyficzne dla kultury.</span><span class="sxs-lookup"><span data-stu-id="f5550-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="f5550-141">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="f5550-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="f5550-142">Jak pokazano w przykładzie, możesz użyć jednego <xref:System.FormattableString> wystąpienia do generowania wielu ciągi wyników dla różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="f5550-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="f5550-143">Jak utworzyć ciąg wynikowy, przy użyciu niezmiennej kultury</span><span class="sxs-lookup"><span data-stu-id="f5550-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="f5550-144">Wraz z <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, można użyć statycznej <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metodą rozwiązania ciągu interpolowanego na ciąg wyniku do <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="f5550-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="f5550-145">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="f5550-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="f5550-146">Wniosek</span><span class="sxs-lookup"><span data-stu-id="f5550-146">Conclusion</span></span>

<span data-ttu-id="f5550-147">W tym samouczku opisano typowe scenariusze użycia interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="f5550-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="f5550-148">Aby uzyskać więcej informacji na temat Interpolacja ciągów, zobacz [Interpolacja ciągów](../language-reference/tokens/interpolated.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f5550-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="f5550-149">Aby uzyskać więcej informacji na temat typy formatowania w programie .NET, zobacz [typy formatowania na platformie .NET](../../standard/base-types/formatting-types.md) i [formatowania złożonego](../../standard/base-types/composite-formatting.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="f5550-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5550-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5550-150">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="f5550-151">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f5550-151">Strings</span></span>](../programming-guide/strings/index.md)
