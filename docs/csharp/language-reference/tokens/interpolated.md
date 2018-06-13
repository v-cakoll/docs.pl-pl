---
title: $ - ciąg interpolacji (odwołanie w C#)
description: Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni do formatowania danych wyjściowych ciąg niż tradycyjne ciąg złożone formatowanie.
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
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058839"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="e9b72-103">$ - ciąg interpolacji (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e9b72-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="e9b72-104">`$` Znak specjalny identyfikuje ciąg literału jako *interpolowane ciąg*.</span><span class="sxs-lookup"><span data-stu-id="e9b72-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="e9b72-105">Ciągu interpolowanym jest ciągiem literału, który może zawierać *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="e9b72-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="e9b72-106">Po usunięciu ciągu interpolowanym ciąg wyniku, elementów z wyrażenia interpolowane zastępuje reprezentacji ciągu wyników wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="e9b72-107">Ta funkcja jest dostępna w C# 6 i nowsze wersje języka.</span><span class="sxs-lookup"><span data-stu-id="e9b72-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="e9b72-108">Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni utworzyć ciągi sformatowane niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9b72-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="e9b72-109">W poniższym przykładzie użyto obie funkcje do tworzenia tych samych danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="e9b72-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="e9b72-110">Struktura ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="e9b72-110">Structure of an interpolated string</span></span>

<span data-ttu-id="e9b72-111">Aby zidentyfikować ciąg literału jako ciągu interpolowanym, dołączenie wartości za pomocą `$` symbolu.</span><span class="sxs-lookup"><span data-stu-id="e9b72-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="e9b72-112">Nie może zawierać żadnego odstępu między `$` i `"` zaczynającym się literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="e9b72-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="e9b72-113">To powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9b72-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="e9b72-114">Struktura element o interpolowanego wyrażenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e9b72-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="e9b72-115">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e9b72-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="e9b72-116">W poniższej tabeli opisano każdy element:</span><span class="sxs-lookup"><span data-stu-id="e9b72-116">The following table describes each element:</span></span>

|<span data-ttu-id="e9b72-117">Element</span><span class="sxs-lookup"><span data-stu-id="e9b72-117">Element</span></span>|<span data-ttu-id="e9b72-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e9b72-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="e9b72-119">Wyrażenie, które daje wynik formatowania.</span><span class="sxs-lookup"><span data-stu-id="e9b72-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="e9b72-120">Reprezentacja ciągu `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9b72-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="e9b72-121">Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w reprezentację ciągu wynik interpolowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="e9b72-122">Jeśli jest dodatnia, reprezentacja tekstowa jest wyrównany do prawej; Jeśli ujemną, jest wyrównany.</span><span class="sxs-lookup"><span data-stu-id="e9b72-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="e9b72-123">Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="e9b72-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="e9b72-124">Ciąg formatu, który jest obsługiwany przez ten typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="e9b72-125">Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="e9b72-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="e9b72-126">W poniższym przykładzie użyto opcjonalnych składników formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="e9b72-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="e9b72-127">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="e9b72-127">Special characters</span></span>

<span data-ttu-id="e9b72-128">Uwzględnienie nawias klamrowy "{" lub "}", w tekście utworzonego przez ciągu interpolowanym, użyj dwóch nawiasów klamrowych, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="e9b72-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="e9b72-129">Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="e9b72-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="e9b72-130">Jako dwukropkiem (":") ma specjalne znaczenie w elemencie interpolowanego wyrażenia, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażeniu interpolowane ujmij tego wyrażenia w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e9b72-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="e9b72-131">W poniższym przykładzie pokazano, jak dołączyć nawiasu klamrowego ciągu wynik i sposobu użycia operator warunkowy w wyrażeniu interpolowane:</span><span class="sxs-lookup"><span data-stu-id="e9b72-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="e9b72-132">Rozpoczyna się od ciągu dosłownego wyrażenia interpolowane `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="e9b72-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="e9b72-133">Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) i [dosłownego wyrażenia identyfikator](verbatim.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="e9b72-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="e9b72-134">`$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="e9b72-135">Niejawne konwersje i określając `IFormatProvider` implementacji</span><span class="sxs-lookup"><span data-stu-id="e9b72-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="e9b72-136">Istnieją trzy niejawną konwersję z ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="e9b72-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="e9b72-137">Konwersja ciągu interpolowanym do <xref:System.String> wystąpienie, które jest wynikiem rozdzielczość ciągu interpolowanym interpolowanego wyrażenia elementów zastępowane z reprezentacji ciągu prawidłowo sformatowane ich wyników.</span><span class="sxs-lookup"><span data-stu-id="e9b72-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="e9b72-138">Ta konwersja używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="e9b72-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="e9b72-139">Konwersja ciągu interpolowanym do <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikiem wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="e9b72-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="e9b72-140">Który umożliwia tworzenie wielu ciągów wyników z specyficzne dla kultury zawartości z jednej <xref:System.FormattableString> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="e9b72-141">Robić, które wywołują jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="e9b72-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="e9b72-142">A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="e9b72-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="e9b72-143"><xref:System.FormattableString.Invariant%2A> Metodę, która tworzy ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="e9b72-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="e9b72-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="e9b72-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="e9b72-145">Można też użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby udostępnić implementację użytkownika <xref:System.IFormatProvider> interfejsu, który obsługuje niestandardowe formatowanie.</span><span class="sxs-lookup"><span data-stu-id="e9b72-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="e9b72-146">Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="e9b72-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="e9b72-147">Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi wystąpienie, które umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9b72-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="e9b72-148">W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> można utworzyć ciągów wynikowych specyficzne dla kultury:</span><span class="sxs-lookup"><span data-stu-id="e9b72-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="e9b72-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e9b72-149">Additional resources</span></span>

<span data-ttu-id="e9b72-150">Jeśli jesteś nowym użytkownikiem interpolacji ciągu, zobacz [ciągu interpolacji w języku C#](../../quick-starts/interpolated-strings.yml) Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="e9b72-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="e9b72-151">Aby uzyskać więcej przykładów, zobacz [ciągu interpolacji w języku C#](../../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="e9b72-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9b72-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9b72-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="e9b72-153">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="e9b72-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="e9b72-154">Ciągi</span><span class="sxs-lookup"><span data-stu-id="e9b72-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="e9b72-155">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e9b72-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="e9b72-156">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="e9b72-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="e9b72-157">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e9b72-157">C# Reference</span></span>](../index.md)  