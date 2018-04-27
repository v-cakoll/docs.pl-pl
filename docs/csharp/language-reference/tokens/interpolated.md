---
title: $ - ciąg interpolacji (odwołanie w C#)
description: Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni do formatowania danych wyjściowych ciąg niż tradycyjne ciąg złożone formatowanie.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="f1d02-103">$ - ciąg interpolacji (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f1d02-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="f1d02-104">`$` Znak specjalny identyfikuje ciąg literału jako *interpolowane ciąg*.</span><span class="sxs-lookup"><span data-stu-id="f1d02-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="f1d02-105">Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="f1d02-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="f1d02-106">Po usunięciu ciągu interpolowanym ciąg wyniku, elementów z wyrażenia interpolowane zastępuje reprezentacji ciągu wyników wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-106">When the interpolated string is resolved to the result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="f1d02-107">Ta funkcja jest dostępna w C# 6 i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="f1d02-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="f1d02-108">Ciąg interpolacji zapewnia bardziej czytelny i wygodne składni utworzyć ciągi sformatowane niż [ciągu formatowania złożonego](../../../standard/base-types/composite-formatting.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="f1d02-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="f1d02-109">W poniższym przykładzie użyto obie funkcje do tworzenia tych samych danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="f1d02-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="f1d02-110">Nie może zawierać żadnego odstępu między `$` i `"` zaczynającym się ciąg.</span><span class="sxs-lookup"><span data-stu-id="f1d02-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="f1d02-111">To powoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f1d02-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="f1d02-112">Struktura element o interpolowanego wyrażenia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="f1d02-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="f1d02-113">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f1d02-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="f1d02-114">W tabeli poniżej opisano każdy element.</span><span class="sxs-lookup"><span data-stu-id="f1d02-114">The following table describes each element.</span></span>

|<span data-ttu-id="f1d02-115">Element</span><span class="sxs-lookup"><span data-stu-id="f1d02-115">Element</span></span>|<span data-ttu-id="f1d02-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f1d02-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="f1d02-117">Wyrażenie do oceny, aby uzyskać wynik formatowania.</span><span class="sxs-lookup"><span data-stu-id="f1d02-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="f1d02-118">Reprezentacja ciągu `null` wynik jest <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1d02-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="f1d02-119">Wyrażenie stałe, którego wartość określa minimalną liczbę znaków w reprezentację ciągu wynik interpolowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="f1d02-120">Jeśli jest dodatnia, reprezentacja tekstowa jest wyrównany do prawej; Jeśli ujemną, jest wyrównany.</span><span class="sxs-lookup"><span data-stu-id="f1d02-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="f1d02-121">Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="f1d02-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="f1d02-122">Ciąg formatu standardowych lub niestandardowych, który jest obsługiwany przez ten typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="f1d02-123">Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="f1d02-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="f1d02-124">W poniższym przykładzie użyto opcjonalnych składników formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="f1d02-124">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="f1d02-125">Aby uwzględnić nawiasu klamrowego ("{" lub "}") w tekście utworzonego przez ciągu interpolowanym, użyj dwóch nawiasów klamrowych, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="f1d02-125">To include a brace ("{" or "}") in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="f1d02-126">Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="f1d02-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="f1d02-127">Jako dwukropka (:) ma specjalne znaczenie w elemencie interpolowanego wyrażenia, aby można było używać [operator warunkowy](../operators/conditional-operator.md) w wyrażeniu interpolowane ujmij tego wyrażenia w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="f1d02-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="f1d02-128">W poniższym przykładzie pokazano, jak dołączyć nawiasu klamrowego na ciąg wyniku i sposobu użycia operator warunkowy w wyrażeniu interpolowane:</span><span class="sxs-lookup"><span data-stu-id="f1d02-128">The following example shows how to include a brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="f1d02-129">Użyj ciągi interpolowane z Verbatim `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="f1d02-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="f1d02-130">Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](../keywords/string.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f1d02-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="f1d02-131">`$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

<span data-ttu-id="f1d02-132">Istnieją trzy niejawną konwersję z ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="f1d02-132">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="f1d02-133">Konwersja ciągu interpolowanym do <xref:System.String> wystąpienie, które jest wynikiem rozdzielczość ciągu interpolowanym interpolowanego wyrażenia elementów zastępowane z reprezentacji ciągu prawidłowo sformatowane ich wyników.</span><span class="sxs-lookup"><span data-stu-id="f1d02-133">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="f1d02-134">Ta konwersja używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="f1d02-134">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="f1d02-135">Konwersja ciągu interpolowanym do <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikiem wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="f1d02-135">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="f1d02-136">Który umożliwia tworzenie wielu ciągów wyników z specyficzne dla kultury zawartości z jednej <xref:System.FormattableString> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-136">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="f1d02-137">Robić, które wywołują jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="f1d02-137">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="f1d02-138">A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="f1d02-138">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="f1d02-139">A <xref:System.FormattableString.Invariant%2A> metodę, która tworzy ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="f1d02-139">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="f1d02-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="f1d02-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="f1d02-141">Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi wystąpienie, które umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f1d02-141">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="f1d02-142">W poniższym przykładzie użyto niejawnej konwersji <xref:System.FormattableString> można utworzyć ciągów wynikowych specyficzne dla kultury:</span><span class="sxs-lookup"><span data-stu-id="f1d02-142">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

<span data-ttu-id="f1d02-143">Jeśli jesteś nowym użytkownikiem interpolacji ciągu, sprawdź [ciągu interpolacji w języku C#](../../quick-starts/interpolated-strings.yml) Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="f1d02-143">If you are new to the string interpolation, check the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="f1d02-144">Aby uzyskać więcej przykładów, zobacz [samouczek interpolacji ciąg](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="f1d02-144">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1d02-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1d02-145">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="f1d02-146">Złożone formatowanie</span><span class="sxs-lookup"><span data-stu-id="f1d02-146">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="f1d02-147">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f1d02-147">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="f1d02-148">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="f1d02-148">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="f1d02-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f1d02-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1d02-150">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f1d02-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  