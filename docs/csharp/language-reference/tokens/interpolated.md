---
title: $ — Interpolacja ciągów - C# odwołania
ms.custom: seodec18
description: Interpolacja ciągów pozwala bardziej czytelne i wygodne składni do formatowania danych wyjściowych ciąg znaków, niż tradycyjne ciągu formatowania złożonego.
ms.date: 04/29/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: bc27eedcf1957a109a9bcb80cf9a49e9606921fd
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251000"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="d0c25-103">$ — Interpolacja ciągów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d0c25-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="d0c25-104">`$` Znak specjalny identyfikuje literał ciągu zgodny z *ciągiem interpolowanym*.</span><span class="sxs-lookup"><span data-stu-id="d0c25-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="d0c25-105">Ciągu interpolowanego jest ciągiem literału, który może zawierać *wyrażeń interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="d0c25-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="d0c25-106">Po usunięciu ciągu interpolowanego do ciągu wynikowego, elementy przy użyciu interpolacji wyrażenia są zastępowane przez ciągów reprezentujących wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d0c25-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="d0c25-107">Ta funkcja jest dostępna w języku C# 6 i nowsze wersje języka.</span><span class="sxs-lookup"><span data-stu-id="d0c25-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="d0c25-108">Interpolacja ciągów pozwala bardziej czytelne i wygodne składni utworzyć sformatowane ciągi niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="d0c25-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="d0c25-109">W poniższym przykładzie użyto obu funkcji, aby utworzyć ten sam wynik:</span><span class="sxs-lookup"><span data-stu-id="d0c25-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="d0c25-110">Struktura ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="d0c25-110">Structure of an interpolated string</span></span>

<span data-ttu-id="d0c25-111">Aby zidentyfikować literał ciągu zgodny z ciągu interpolowanego, dodaj ją za pomocą `$` symboli.</span><span class="sxs-lookup"><span data-stu-id="d0c25-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="d0c25-112">Nie może mieć dowolny biały obszar między `$` i `"` którego początkowe literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="d0c25-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="d0c25-113">Ten sposób powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d0c25-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="d0c25-114">Struktura elementu za pomocą wyrażenia interpolacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d0c25-114">The structure of an item with an interpolation expression is as follows:</span></span>

```
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="d0c25-115">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d0c25-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="d0c25-116">W poniższej tabeli opisano każdy element:</span><span class="sxs-lookup"><span data-stu-id="d0c25-116">The following table describes each element:</span></span>

|<span data-ttu-id="d0c25-117">Element</span><span class="sxs-lookup"><span data-stu-id="d0c25-117">Element</span></span>|<span data-ttu-id="d0c25-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d0c25-118">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="d0c25-119">Wyrażenie, które daje wynik do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="d0c25-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="d0c25-120">Ciąg reprezentujący `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0c25-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="d0c25-121">Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w ciągu reprezentującego wynik wyrażenia interpolacji.</span><span class="sxs-lookup"><span data-stu-id="d0c25-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolation expression.</span></span> <span data-ttu-id="d0c25-122">Jeśli jest to dodatnia, reprezentacji w postaci ciągu jest wyrównany do prawej; Jeśli jest negatywny, jest wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="d0c25-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="d0c25-123">Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="d0c25-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="d0c25-124">Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d0c25-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="d0c25-125">Aby uzyskać więcej informacji, zobacz [element ciągu formatującego](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="d0c25-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="d0c25-126">W poniższym przykładzie użyto opcjonalne składniki formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="d0c25-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="d0c25-127">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="d0c25-127">Special characters</span></span>

<span data-ttu-id="d0c25-128">Aby uwzględnić nawiasu klamrowego, "{" lub "}", w tekście, generowane przez ciągu interpolowanego, użyj dwóch nawiasów klamrowych, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="d0c25-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="d0c25-129">Aby uzyskać więcej informacji, zobacz [anulowania zapewnianego element nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="d0c25-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="d0c25-130">Jako dwukropkiem (":") ma specjalne znaczenie w elemencie wyrażenie interpolacji, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażeniu interpolacji ująć to wyrażenie w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d0c25-130">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="d0c25-131">Poniższy przykład pokazuje, jak dołączyć nawiasu klamrowego w ciągu wynikowym i sposobu użycia operatora warunkowego w wyrażeniu interpolacji:</span><span class="sxs-lookup"><span data-stu-id="d0c25-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="d0c25-132">Ciąg verbatim interpolowane zaczyna się od `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="d0c25-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="d0c25-133">Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) i [identyfikator dosłownego wyrażenia](verbatim.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="d0c25-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="d0c25-134">`$` Tokenu musi występować przed `@` tokenu w verbatim ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="d0c25-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="d0c25-135">Niejawne konwersje i określając `IFormatProvider` implementacji</span><span class="sxs-lookup"><span data-stu-id="d0c25-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="d0c25-136">Istnieją trzy niejawną konwersję z ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="d0c25-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="d0c25-137">Konwersja ciągu interpolowanego do <xref:System.String> wystąpienie, które jest wynikiem rozdzielczości ciągu interpolowanego z wyrażeniem interpolacji elementy zastępowane poprawnie sformatowanych ciągów reprezentujących ich wyniki.</span><span class="sxs-lookup"><span data-stu-id="d0c25-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="d0c25-138">Ta konwersja skorzysta z bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="d0c25-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="d0c25-139">Konwersja ciągu interpolowanego do <xref:System.FormattableString> wystąpienia, która reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="d0c25-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="d0c25-140">Pozwala to do utworzenia wielu ciągów wynik z specyficzne dla kultury zawartości z jednego <xref:System.FormattableString> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0c25-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="d0c25-141">Który wywołać jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="d0c25-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="d0c25-142">A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="d0c25-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="d0c25-143"><xref:System.FormattableString.Invariant%2A> Metodę, która tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="d0c25-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="d0c25-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która daje ciąg wynikowy dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="d0c25-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="d0c25-145">Możesz również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby udostępnić implementację zdefiniowanych przez użytkownika z <xref:System.IFormatProvider> interfejsu, który obsługuje formatowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="d0c25-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="d0c25-146">Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie z ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="d0c25-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="d0c25-147">Konwersja ciągu interpolowanego do <xref:System.IFormattable> ciągi specyficzne dla kultury zawartości z jednego wystąpienia, które umożliwia również tworzenie wielu wyników <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0c25-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="d0c25-148">W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> utworzyć ciągi wynikowe charakterystyczne dla kultury:</span><span class="sxs-lookup"><span data-stu-id="d0c25-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="d0c25-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d0c25-149">Additional resources</span></span>

<span data-ttu-id="d0c25-150">Jeśli jesteś nowym użytkownikiem Interpolacja ciągów, zobacz [Interpolacja w ciągów C# ](../../tutorials/exploration/interpolated-strings.yml) interaktywnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="d0c25-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="d0c25-151">Możesz również sprawdzić innego [Interpolacja w ciągów C# ](../../tutorials/string-interpolation.md) samouczek, który demonstruje sposób użycia ciągów interpolowanych w celu wygenerowania sformatowane ciągi.</span><span class="sxs-lookup"><span data-stu-id="d0c25-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="d0c25-152">Kompilacja ciągi interpolowane</span><span class="sxs-lookup"><span data-stu-id="d0c25-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="d0c25-153">Jeśli w ciągu interpolowanym ma typ `string`, zwykle jest przekształcana na <xref:System.String.Format%2A?displayProperty=nameWithType> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d0c25-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="d0c25-154">Kompilator może zastąpić <xref:System.String.Format%2A?displayProperty=nameWithType> z <xref:System.String.Concat%2A?displayProperty=nameWithType> Jeśli analizowany zachowanie byłaby równoważna łączenia.</span><span class="sxs-lookup"><span data-stu-id="d0c25-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="d0c25-155">Jeśli w ciągu interpolowanym ma typ <xref:System.IFormattable> lub <xref:System.FormattableString>, kompilator generuje wywołanie <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d0c25-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d0c25-156">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d0c25-156">C# language specification</span></span>

<span data-ttu-id="d0c25-157">Aby uzyskać więcej informacji, zobacz [ciągi interpolowane](~/_csharplang/spec/expressions.md#interpolated-strings) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d0c25-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0c25-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0c25-158">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="d0c25-159">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="d0c25-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="d0c25-160">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="d0c25-160">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="d0c25-161">Ciągi</span><span class="sxs-lookup"><span data-stu-id="d0c25-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="d0c25-162">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d0c25-162">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0c25-163">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="d0c25-163">C# Special Characters</span></span>](index.md)
- [<span data-ttu-id="d0c25-164">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d0c25-164">C# Reference</span></span>](../index.md)
