---
title: Interpolacja ciągów wC#
description: Dowiedz się, jak dołączać sformatowane wyniki wyrażenia w C# ciągu wynikowym przy użyciu interpolacji ciągów.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039212"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="16592-103">Interpolacja ciągów w języku C\#</span><span class="sxs-lookup"><span data-stu-id="16592-103">String interpolation in C\#</span></span>

<span data-ttu-id="16592-104">W tym samouczku pokazano, jak używać [interpolacji ciągów](../language-reference/tokens/interpolated.md) do formatowania i dołączania wyników wyrażenia w ciągu wynikowym.</span><span class="sxs-lookup"><span data-stu-id="16592-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="16592-105">W przykładach założono, że znasz podstawowe C# pojęcia i formatowanie typów .NET.</span><span class="sxs-lookup"><span data-stu-id="16592-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="16592-106">Jeśli jesteś nowym programem do interpolacji ciągów lub formatowania typu .NET, najpierw zapoznaj się z [samouczkiem Interpolacja ciągów interaktywnych](exploration/interpolated-strings.yml) .</span><span class="sxs-lookup"><span data-stu-id="16592-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="16592-107">Aby uzyskać więcej informacji na temat formatowania typów w programie .NET, zobacz [Typy formatowania w temacie .NET](../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="16592-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="16592-108">Introduction</span></span>

<span data-ttu-id="16592-109">Funkcja [interpolacji ciągu](../language-reference/tokens/interpolated.md) jest tworzona na podstawie funkcji [formatowania złożonego](../../standard/base-types/composite-formatting.md) i zapewnia bardziej czytelną i wygodną składnię, aby dołączać sformatowane wyniki wyrażeń do ciągu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="16592-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="16592-110">Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go symbolem `$`.</span><span class="sxs-lookup"><span data-stu-id="16592-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="16592-111">Można osadzić dowolne prawidłowe C# Wyrażenie zwracające wartość w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="16592-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="16592-112">W poniższym przykładzie, zaraz po obliczeniu wyrażenia, jego wynik jest konwertowany na ciąg i uwzględniony w ciągu wynikowym:</span><span class="sxs-lookup"><span data-stu-id="16592-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="16592-113">Jak pokazano w przykładzie, można uwzględnić wyrażenie w ciągu interpolowanym, umieszczając je w nawiasach klamrowych:</span><span class="sxs-lookup"><span data-stu-id="16592-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="16592-114">Ciągi interpolowane obsługują wszystkie możliwości funkcji [formatowania złożonego w ciągu](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="16592-115">Sprawia, że są one bardziej czytelną alternatywą dla użycia metody <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16592-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="16592-116">Jak określić ciąg formatu dla wyrażenia interpolacji</span><span class="sxs-lookup"><span data-stu-id="16592-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="16592-117">Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągiem formatu:</span><span class="sxs-lookup"><span data-stu-id="16592-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="16592-118">Poniższy przykład ilustruje sposób określania standardowych i niestandardowych ciągów formatu dla wyrażeń, które tworzą datę i godzinę lub wyniki liczbowe:</span><span class="sxs-lookup"><span data-stu-id="16592-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="16592-119">Aby uzyskać więcej informacji, zobacz sekcję [Format składnika ciągu](../../standard/base-types/composite-formatting.md#format-string-component) w temacie [formatowanie złożone](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="16592-120">Ta sekcja zawiera linki do tematów, które opisują standardowe i niestandardowe ciągi formatujące obsługiwane przez typy podstawowe programu .NET.</span><span class="sxs-lookup"><span data-stu-id="16592-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="16592-121">Kontrolowanie szerokości pola i wyrównania sformatowanego wyrażenia interpolacji</span><span class="sxs-lookup"><span data-stu-id="16592-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="16592-122">Należy określić minimalną szerokość pola i wyrównanie sformatowanego wyniku wyrażenia, wykonując wyrażenie interpolacji z przecinkiem (",") i wyrażeniem stałym:</span><span class="sxs-lookup"><span data-stu-id="16592-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="16592-123">Jeśli wartość *wyrównania* jest dodatnia, wynik sformatowanego wyrażenia jest wyrównany do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej.</span><span class="sxs-lookup"><span data-stu-id="16592-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="16592-124">Jeśli musisz określić zarówno wyrównanie, jak i ciąg formatu, Rozpocznij od składnika wyrównania:</span><span class="sxs-lookup"><span data-stu-id="16592-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="16592-125">Poniższy przykład pokazuje, jak określić wyrównanie i używa znaków potoku ("|") do rozgraniczania pól tekstowych:</span><span class="sxs-lookup"><span data-stu-id="16592-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="16592-126">Jak przykładowe dane wyjściowe są wyświetlane, jeśli długość sformatowanego wyniku wyrażenia przekroczy określoną szerokość pola, wartość *wyrównania* jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="16592-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="16592-127">Aby uzyskać więcej informacji, zobacz sekcję [wyrównania składnika](../../standard/base-types/composite-formatting.md#alignment-component) w temacie [formatowanie złożone](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="16592-128">Jak używać sekwencji unikowych w ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="16592-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="16592-129">Ciągi interpolowane obsługują wszystkie sekwencje unikowe, które mogą być używane w zwykłych literałach ciągu.</span><span class="sxs-lookup"><span data-stu-id="16592-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="16592-130">Aby uzyskać więcej informacji, zobacz [Sekwencje ucieczki ciągów](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="16592-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="16592-131">Aby interpretować sekwencje ucieczki dosłownie, użyj literału ciągu [Verbatim](../language-reference/tokens/verbatim.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="16592-132">Interpolacja Verbatim ciąg rozpoczyna się od znaku `$`, po którym następuje znak `@`.</span><span class="sxs-lookup"><span data-stu-id="16592-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="16592-133">Począwszy od C# 8,0, można użyć tokenów`$`i`@`w dowolnej kolejności: zarówno `$@"..."`, jak i`@$"..."`są prawidłowymi interpolowanymi ciągami Verbatim.</span><span class="sxs-lookup"><span data-stu-id="16592-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="16592-134">Aby dołączyć nawias klamrowy "{" lub "}" w ciągu wynikowym, użyj dwóch nawiasów klamrowych "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="16592-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="16592-135">Aby uzyskać więcej informacji, zobacz sekcję [ucieczki nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) tematu [formatowanie złożone](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="16592-136">Poniższy przykład pokazuje, jak uwzględnić nawiasy klamrowe w ciągu wynikowym i utworzyć ciąg interpolowany Verbatim:</span><span class="sxs-lookup"><span data-stu-id="16592-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="16592-137">Jak używać operatora warunkowego Trzyelementowy `?:` w wyrażeniu interpolacji</span><span class="sxs-lookup"><span data-stu-id="16592-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="16592-138">Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie z wyrażeniem interpolacji, aby użyć [operatora warunkowego](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ująć go w nawiasy, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="16592-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="16592-139">Jak utworzyć ciąg wyniku specyficzny dla kultury przy użyciu interpolacji ciągów</span><span class="sxs-lookup"><span data-stu-id="16592-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="16592-140">Domyślnie ciąg interpolowany używa bieżącej kultury zdefiniowanej przez właściwość <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> dla wszystkich operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="16592-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="16592-141">Użyj niejawnej konwersji ciągu interpolowanego na wystąpienie <xref:System.FormattableString?displayProperty=nameWithType> i Wywołaj metodę <xref:System.FormattableString.ToString(System.IFormatProvider)>, aby utworzyć ciąg wyniku specyficzny dla kultury.</span><span class="sxs-lookup"><span data-stu-id="16592-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="16592-142">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="16592-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="16592-143">Jak pokazano w przykładzie, można użyć jednego wystąpienia <xref:System.FormattableString>, aby wygenerować wiele ciągów wynikowych dla różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="16592-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="16592-144">Jak utworzyć ciąg wynikowy przy użyciu niezmiennej kultury</span><span class="sxs-lookup"><span data-stu-id="16592-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="16592-145">Podobnie jak w przypadku metody <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> można użyć statycznej metody <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType>, aby rozpoznać ciąg interpolowany do ciągu wynikowego dla <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="16592-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="16592-146">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="16592-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="16592-147">Wniosek</span><span class="sxs-lookup"><span data-stu-id="16592-147">Conclusion</span></span>

<span data-ttu-id="16592-148">W tym samouczku opisano typowe scenariusze użycia interpolacji ciągów.</span><span class="sxs-lookup"><span data-stu-id="16592-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="16592-149">Aby uzyskać więcej informacji na temat interpolacji ciągów, zobacz temat [Interpolacja ciągów](../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="16592-150">Aby uzyskać więcej informacji na temat formatowania typów w programie .NET, zobacz [Typy formatowania w temacie .NET](../../standard/base-types/formatting-types.md) i [formatowanie złożone](../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="16592-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="16592-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16592-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="16592-152">Ciągi</span><span class="sxs-lookup"><span data-stu-id="16592-152">Strings</span></span>](../programming-guide/strings/index.md)
