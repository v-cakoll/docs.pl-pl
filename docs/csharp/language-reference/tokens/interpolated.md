---
title: $ — Interpolacja ciągów - C# odwołania
ms.custom: seodec18
description: Interpolacja ciągów pozwala bardziej czytelne i wygodne składni do formatowania danych wyjściowych ciąg znaków, niż tradycyjne ciągu formatowania złożonego.
ms.date: 03/26/2018
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
ms.openlocfilehash: 64728182fe0b758f8da668d19761305e2001f1a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659920"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="a48ea-103">$ — Interpolacja ciągów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a48ea-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="a48ea-104">`$` Znak specjalny identyfikuje literał ciągu zgodny z *ciągiem interpolowanym*.</span><span class="sxs-lookup"><span data-stu-id="a48ea-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="a48ea-105">Ciągu interpolowanego jest ciągiem literału, który może zawierać *wyrażeń interpolowanych*.</span><span class="sxs-lookup"><span data-stu-id="a48ea-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="a48ea-106">Po usunięciu ciągu interpolowanego do ciągu wynikowego, elementy z wyrażeń interpolowanych są zastępowane przez ciągów reprezentujących wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a48ea-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="a48ea-107">Ta funkcja jest dostępna w języku C# 6 i nowsze wersje języka.</span><span class="sxs-lookup"><span data-stu-id="a48ea-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="a48ea-108">Interpolacja ciągów pozwala bardziej czytelne i wygodne składni utworzyć sformatowane ciągi niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="a48ea-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="a48ea-109">W poniższym przykładzie użyto obu funkcji, aby utworzyć ten sam wynik:</span><span class="sxs-lookup"><span data-stu-id="a48ea-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="a48ea-110">Struktura ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="a48ea-110">Structure of an interpolated string</span></span>

<span data-ttu-id="a48ea-111">Aby zidentyfikować literał ciągu zgodny z ciągu interpolowanego, dodaj ją za pomocą `$` symboli.</span><span class="sxs-lookup"><span data-stu-id="a48ea-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="a48ea-112">Nie może mieć dowolny biały obszar między `$` i `"` którego początkowe literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="a48ea-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="a48ea-113">Ten sposób powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a48ea-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="a48ea-114">Struktura element na wyrażenie interpolowane jest następująca:</span><span class="sxs-lookup"><span data-stu-id="a48ea-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="a48ea-115">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a48ea-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="a48ea-116">W poniższej tabeli opisano każdy element:</span><span class="sxs-lookup"><span data-stu-id="a48ea-116">The following table describes each element:</span></span>

|<span data-ttu-id="a48ea-117">Element</span><span class="sxs-lookup"><span data-stu-id="a48ea-117">Element</span></span>|<span data-ttu-id="a48ea-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a48ea-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="a48ea-119">Wyrażenie, które daje wynik do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="a48ea-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="a48ea-120">Ciąg reprezentujący `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a48ea-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="a48ea-121">Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w ciągu reprezentującego wynik wyrażenia interpolowane.</span><span class="sxs-lookup"><span data-stu-id="a48ea-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="a48ea-122">Jeśli jest to dodatnia, reprezentacji w postaci ciągu jest wyrównany do prawej; Jeśli jest negatywny, jest wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="a48ea-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="a48ea-123">Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="a48ea-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="a48ea-124">Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a48ea-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="a48ea-125">Aby uzyskać więcej informacji, zobacz [element ciągu formatującego](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="a48ea-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="a48ea-126">W poniższym przykładzie użyto opcjonalne składniki formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="a48ea-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="a48ea-127">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="a48ea-127">Special characters</span></span>

<span data-ttu-id="a48ea-128">Aby uwzględnić nawiasu klamrowego, "{" lub "}", w tekście, generowane przez ciągu interpolowanego, użyj dwóch nawiasów klamrowych, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="a48ea-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="a48ea-129">Aby uzyskać więcej informacji, zobacz [anulowania zapewnianego element nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="a48ea-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="a48ea-130">Jako dwukropkiem (":") ma specjalne znaczenie w elemencie wyrażenie interpolowane, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażenie interpolowane ująć to wyrażenie w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="a48ea-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="a48ea-131">Poniższy przykład pokazuje, jak dołączyć nawiasu klamrowego w ciągu wynikowym i sposobu użycia operatora warunkowego w wyrażenie interpolowane:</span><span class="sxs-lookup"><span data-stu-id="a48ea-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="a48ea-132">Ciąg verbatim interpolowane zaczyna się od `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="a48ea-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="a48ea-133">Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) i [identyfikator dosłownego wyrażenia](verbatim.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="a48ea-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="a48ea-134">`$` Tokenu musi występować przed `@` tokenu w verbatim ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="a48ea-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="a48ea-135">Niejawne konwersje i określając `IFormatProvider` implementacji</span><span class="sxs-lookup"><span data-stu-id="a48ea-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="a48ea-136">Istnieją trzy niejawną konwersję z ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="a48ea-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="a48ea-137">Konwersja ciągu interpolowanego do <xref:System.String> wystąpienia, która jest wynikiem rozdzielczość ciąg interpolowany z wyrażenia interpolowanego elementy zastępowane poprawnie sformatowanych ciągów reprezentujących ich wyniki.</span><span class="sxs-lookup"><span data-stu-id="a48ea-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="a48ea-138">Ta konwersja skorzysta z bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="a48ea-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="a48ea-139">Konwersja ciągu interpolowanego do <xref:System.FormattableString> wystąpienia, która reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="a48ea-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="a48ea-140">Pozwala to do utworzenia wielu ciągów wynik z specyficzne dla kultury zawartości z jednego <xref:System.FormattableString> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a48ea-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="a48ea-141">Który wywołać jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="a48ea-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="a48ea-142">A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="a48ea-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="a48ea-143"><xref:System.FormattableString.Invariant%2A> Metodę, która tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="a48ea-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="a48ea-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która daje ciąg wynikowy dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="a48ea-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="a48ea-145">Możesz również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby udostępnić implementację zdefiniowanych przez użytkownika z <xref:System.IFormatProvider> interfejsu, który obsługuje formatowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="a48ea-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="a48ea-146">Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie z ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="a48ea-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="a48ea-147">Konwersja ciągu interpolowanego do <xref:System.IFormattable> ciągi specyficzne dla kultury zawartości z jednego wystąpienia, które umożliwia również tworzenie wielu wyników <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a48ea-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="a48ea-148">W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> utworzyć ciągi wynikowe charakterystyczne dla kultury:</span><span class="sxs-lookup"><span data-stu-id="a48ea-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="a48ea-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a48ea-149">Additional resources</span></span>

<span data-ttu-id="a48ea-150">Jeśli jesteś nowym użytkownikiem Interpolacja ciągów, zobacz [Interpolacja w ciągów C# ](../../tutorials/exploration/interpolated-strings.yml) interaktywnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="a48ea-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="a48ea-151">Lub możesz spróbować [Interpolacja w ciągów C# ](../../tutorials/string-interpolation.md) samouczek lokalnie na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a48ea-151">Or you can try the  [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial locally on your machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="a48ea-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a48ea-152">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="a48ea-153">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="a48ea-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="a48ea-154">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="a48ea-154">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="a48ea-155">Ciągi</span><span class="sxs-lookup"><span data-stu-id="a48ea-155">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="a48ea-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a48ea-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a48ea-157">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="a48ea-157">C# Special Characters</span></span>](index.md)
- [<span data-ttu-id="a48ea-158">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a48ea-158">C# Reference</span></span>](../index.md)
