---
title: Interpolacja $-String- C# odwołanie
ms.custom: seodec18
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię formatu ciągu wyjściowego niż tradycyjne formatowanie złożone ciągu.
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
ms.openlocfilehash: 1f0d63a549daa9fecd0cce3a7e5a6496929c37d2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202961"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="47be0-103">Interpolacja $-String (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="47be0-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="47be0-104">Znak specjalny identyfikuje literał ciągu jako *ciąg interpolowany.* `$`</span><span class="sxs-lookup"><span data-stu-id="47be0-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="47be0-105">Ciąg interpolowany jest literałem ciągu, która może zawierać *wyrażenia interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="47be0-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="47be0-106">Gdy ciąg interpolowany jest rozpoznawany jako ciąg wynikowy, elementy z wyrażeniami interpolacji są zastępowane ciągami reprezentującymi wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="47be0-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="47be0-107">Ta funkcja jest dostępna w C# 6 i nowszych wersjach języka.</span><span class="sxs-lookup"><span data-stu-id="47be0-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="47be0-108">Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia ciągów sformatowanych niż funkcja [formatowania złożonego w postaci ciągu](../../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="47be0-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="47be0-109">Poniższy przykład używa obu funkcji do wygenerowania tych samych danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="47be0-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="47be0-110">Struktura ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="47be0-110">Structure of an interpolated string</span></span>

<span data-ttu-id="47be0-111">Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go `$` symbolem.</span><span class="sxs-lookup"><span data-stu-id="47be0-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="47be0-112">`$` Między`"` i, które zaczyna się literałem ciągu znaków, nie może zawierać żadnego odstępu.</span><span class="sxs-lookup"><span data-stu-id="47be0-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="47be0-113">Powoduje to błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="47be0-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="47be0-114">Struktura elementu z wyrażeniem interpolacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="47be0-114">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="47be0-115">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="47be0-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="47be0-116">W poniższej tabeli opisano każdy element:</span><span class="sxs-lookup"><span data-stu-id="47be0-116">The following table describes each element:</span></span>

|<span data-ttu-id="47be0-117">Element</span><span class="sxs-lookup"><span data-stu-id="47be0-117">Element</span></span>|<span data-ttu-id="47be0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="47be0-118">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="47be0-119">Wyrażenie, które generuje wynik do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="47be0-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="47be0-120">Ciąg reprezentujący `null` wynik to <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47be0-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="47be0-121">Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w ciągu reprezentującym wynik wyrażenia interpolacji.</span><span class="sxs-lookup"><span data-stu-id="47be0-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolation expression.</span></span> <span data-ttu-id="47be0-122">W przypadku wartości pozytywnej Reprezentacja ciągu jest wyrównana do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej.</span><span class="sxs-lookup"><span data-stu-id="47be0-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="47be0-123">Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="47be0-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="47be0-124">Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="47be0-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="47be0-125">Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="47be0-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="47be0-126">W poniższym przykładzie zastosowano opcjonalne składniki formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="47be0-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="47be0-127">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="47be0-127">Special characters</span></span>

<span data-ttu-id="47be0-128">Aby dołączyć nawias klamrowy "{" lub "}" w tekście wytworzonym przez ciąg interpolowany, użyj dwóch nawiasów klamrowych "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="47be0-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="47be0-129">Aby uzyskać więcej informacji, [](../../../standard/base-types/composite-formatting.md#escaping-braces)Zobacz nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="47be0-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="47be0-130">Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie wyrażenia interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, należy ująć to wyrażenie w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="47be0-130">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="47be0-131">Poniższy przykład pokazuje, jak uwzględnić nawias klamrowy w ciągu wynikowym oraz jak używać operatora warunkowego w wyrażeniu interpolacji:</span><span class="sxs-lookup"><span data-stu-id="47be0-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="47be0-132">Ciąg interpolowany Verbatim rozpoczyna się od znaku `$` , po którym następuje `@` znak.</span><span class="sxs-lookup"><span data-stu-id="47be0-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="47be0-133">Aby uzyskać więcej informacji na temat ciągów Verbatim, zobacz temat [identyfikatory](verbatim.md) [ciągów](../keywords/string.md) i Verbatim.</span><span class="sxs-lookup"><span data-stu-id="47be0-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="47be0-134">Token musi występować `@` przed tokenem w ciągu interpolowanym Verbatim. `$`</span><span class="sxs-lookup"><span data-stu-id="47be0-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="47be0-135">Konwersje niejawne `IFormatProvider` i określanie implementacji</span><span class="sxs-lookup"><span data-stu-id="47be0-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="47be0-136">Istnieją trzy niejawne konwersje z ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="47be0-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="47be0-137">Konwersja ciągu interpolowanego na <xref:System.String> wystąpienie, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji, które są zastępowane poprawnie sformatowanymi reprezentacjami ciągu wyników.</span><span class="sxs-lookup"><span data-stu-id="47be0-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="47be0-138">Ta konwersja używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="47be0-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="47be0-139">Konwersja ciągu interpolowanego na <xref:System.FormattableString> wystąpienie, które reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="47be0-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="47be0-140">Pozwala to na tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego <xref:System.FormattableString> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="47be0-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="47be0-141">Aby to wywołać, należy wykonać jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="47be0-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="47be0-142">Przeciążenie generujące ciąg wynikowy <xref:System.Globalization.CultureInfo.CurrentCulture>dla. <xref:System.FormattableString.ToString></span><span class="sxs-lookup"><span data-stu-id="47be0-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="47be0-143">Metoda, która generuje ciąg wynikowy <xref:System.Globalization.CultureInfo.InvariantCulture>dla. <xref:System.FormattableString.Invariant%2A></span><span class="sxs-lookup"><span data-stu-id="47be0-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="47be0-144"><xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, która tworzy ciąg wynikowy dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="47be0-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="47be0-145">Można również użyć <xref:System.FormattableString.ToString(System.IFormatProvider)> metody, aby zapewnić zdefiniowaną przez użytkownika implementację <xref:System.IFormatProvider> interfejsu, która obsługuje niestandardowe formatowanie.</span><span class="sxs-lookup"><span data-stu-id="47be0-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="47be0-146">Aby uzyskać więcej informacji, zobacz [niestandardowe formatowanie za pomocą ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="47be0-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="47be0-147">Konwersja ciągu interpolowanego na <xref:System.IFormattable> wystąpienie, które również umożliwia tworzenie wielu ciągów wynikowych przy użyciu zawartości specyficznej dla kultury z jednego <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="47be0-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="47be0-148">W poniższym przykładzie zastosowano niejawną konwersję do <xref:System.FormattableString> , aby utworzyć charakterystyczne dla kultury ciągi wynikowe:</span><span class="sxs-lookup"><span data-stu-id="47be0-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="47be0-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="47be0-149">Additional resources</span></span>

<span data-ttu-id="47be0-150">Jeśli dopiero zaczynasz interpolację ciągów, zobacz Interpolacja [ciągów w C# ](../../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="47be0-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="47be0-151">Możesz również sprawdzić inne [interpolacje ciągów w C# ](../../tutorials/string-interpolation.md) samouczku, w którym pokazano, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="47be0-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="47be0-152">Kompilacja ciągów interpolowanych</span><span class="sxs-lookup"><span data-stu-id="47be0-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="47be0-153">Jeśli ciąg interpolowany ma typ `string`, zazwyczaj jest przekształcany <xref:System.String.Format%2A?displayProperty=nameWithType> do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="47be0-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="47be0-154">Kompilator może zastępować <xref:System.String.Format%2A?displayProperty=nameWithType> w <xref:System.String.Concat%2A?displayProperty=nameWithType> przypadku, gdy przeanalizowane zachowanie byłoby równoważne konkatenacji.</span><span class="sxs-lookup"><span data-stu-id="47be0-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="47be0-155">Jeśli ciąg interpolowany ma typ <xref:System.IFormattable> lub <xref:System.FormattableString>, kompilator <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> generuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="47be0-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="47be0-156">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="47be0-156">C# language specification</span></span>

<span data-ttu-id="47be0-157">Aby uzyskać więcej informacji, zobacz sekcję [interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="47be0-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47be0-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47be0-158">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="47be0-159">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="47be0-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="47be0-160">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="47be0-160">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="47be0-161">Ciągi</span><span class="sxs-lookup"><span data-stu-id="47be0-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="47be0-162">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="47be0-162">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47be0-163">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="47be0-163">C# Special Characters</span></span>](index.md)
- [<span data-ttu-id="47be0-164">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="47be0-164">C# Reference</span></span>](../index.md)
