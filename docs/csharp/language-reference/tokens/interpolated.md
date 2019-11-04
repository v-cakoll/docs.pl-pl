---
title: Interpolacja $-String- C# odwołanie
ms.custom: seodec18
description: Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię formatu ciągu wyjściowego niż tradycyjne formatowanie złożone ciągu.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: cda8582da9ca8262ec2ce6bcfbb76e2e2f5f6006
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421856"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="86c77-103">Interpolacja $-String (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="86c77-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="86c77-104">`$` znak specjalny identyfikuje literał ciągu jako *ciąg interpolowany*.</span><span class="sxs-lookup"><span data-stu-id="86c77-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="86c77-105">Ciąg interpolowany jest literałem ciągu, która może zawierać *wyrażenia interpolacji*.</span><span class="sxs-lookup"><span data-stu-id="86c77-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="86c77-106">Gdy ciąg interpolowany jest rozpoznawany jako ciąg wynikowy, elementy z wyrażeniami interpolacji są zastępowane ciągami reprezentującymi wyniki wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="86c77-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="86c77-107">Ta funkcja jest dostępna od C# 6.</span><span class="sxs-lookup"><span data-stu-id="86c77-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="86c77-108">Interpolacja ciągów zapewnia bardziej czytelną i wygodną składnię do tworzenia ciągów sformatowanych niż funkcja [formatowania złożonego w postaci ciągu](../../../standard/base-types/composite-formatting.md) .</span><span class="sxs-lookup"><span data-stu-id="86c77-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="86c77-109">Poniższy przykład używa obu funkcji do wygenerowania tych samych danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="86c77-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="86c77-110">Struktura ciągu interpolowanego</span><span class="sxs-lookup"><span data-stu-id="86c77-110">Structure of an interpolated string</span></span>

<span data-ttu-id="86c77-111">Aby zidentyfikować literał ciągu jako ciąg interpolowany, poprzedź go symbolem `$`.</span><span class="sxs-lookup"><span data-stu-id="86c77-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="86c77-112">Między `$` i `"`, które zaczynają literał ciągu znaków, nie może być odstępy.</span><span class="sxs-lookup"><span data-stu-id="86c77-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="86c77-113">Struktura elementu z wyrażeniem interpolacji jest następująca:</span><span class="sxs-lookup"><span data-stu-id="86c77-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="86c77-114">Elementy w nawiasach kwadratowych są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="86c77-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="86c77-115">W poniższej tabeli opisano każdy element:</span><span class="sxs-lookup"><span data-stu-id="86c77-115">The following table describes each element:</span></span>

|<span data-ttu-id="86c77-116">Element</span><span class="sxs-lookup"><span data-stu-id="86c77-116">Element</span></span>|<span data-ttu-id="86c77-117">Opis</span><span class="sxs-lookup"><span data-stu-id="86c77-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="86c77-118">Wyrażenie, które generuje wynik do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="86c77-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="86c77-119">Reprezentacja ciągu `null` jest <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86c77-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="86c77-120">Wyrażenie stałe, którego wartość definiuje minimalną liczbę znaków w ciągu reprezentującym wynik wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="86c77-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="86c77-121">W przypadku wartości pozytywnej Reprezentacja ciągu jest wyrównana do prawej; Jeśli wartość jest ujemna, jest wyrównana do lewej.</span><span class="sxs-lookup"><span data-stu-id="86c77-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="86c77-122">Aby uzyskać więcej informacji, zobacz [składnik wyrównania](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="86c77-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="86c77-123">Ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="86c77-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="86c77-124">Aby uzyskać więcej informacji, zobacz [Formatowanie składnika ciągu](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="86c77-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="86c77-125">W poniższym przykładzie zastosowano opcjonalne składniki formatowania opisane powyżej:</span><span class="sxs-lookup"><span data-stu-id="86c77-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="86c77-126">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="86c77-126">Special characters</span></span>

<span data-ttu-id="86c77-127">Aby dołączyć nawias klamrowy "{" lub "}" w tekście wytworzonym przez ciąg interpolowany, użyj dwóch nawiasów klamrowych "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="86c77-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="86c77-128">Aby uzyskać więcej informacji, zobacz [nawiasy klamrowe](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="86c77-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="86c77-129">Ponieważ dwukropek (":") ma specjalne znaczenie w elemencie wyrażenia interpolacji, aby użyć [operatora warunkowego](../operators/conditional-operator.md) w wyrażeniu interpolacji, należy ująć to wyrażenie w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="86c77-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="86c77-130">Poniższy przykład pokazuje, jak uwzględnić nawias klamrowy w ciągu wynikowym oraz jak używać operatora warunkowego w wyrażeniu interpolacji:</span><span class="sxs-lookup"><span data-stu-id="86c77-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="86c77-131">Interpolacja Verbatim ciąg rozpoczyna się od znaku `$`, po którym następuje znak `@`.</span><span class="sxs-lookup"><span data-stu-id="86c77-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="86c77-132">Aby uzyskać więcej informacji na temat ciągów Verbatim, zobacz temat [identyfikatory](verbatim.md) [ciągów](../builtin-types/reference-types.md) i Verbatim.</span><span class="sxs-lookup"><span data-stu-id="86c77-132">For more information about verbatim strings, see the [string](../builtin-types/reference-types.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="86c77-133">Począwszy od C# 8,0, można użyć tokenów`$`i`@`w dowolnej kolejności: zarówno `$@"..."`, jak i`@$"..."`są prawidłowymi interpolowanymi ciągami Verbatim.</span><span class="sxs-lookup"><span data-stu-id="86c77-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="86c77-134">We wcześniejszych C# wersjach token `$` musi znajdować się przed tokenem `@`.</span><span class="sxs-lookup"><span data-stu-id="86c77-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="86c77-135">Niejawne konwersje i sposób określania implementacji `IFormatProvider`</span><span class="sxs-lookup"><span data-stu-id="86c77-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="86c77-136">Istnieją trzy niejawne konwersje z ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="86c77-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="86c77-137">Konwersja ciągu interpolowanego na wystąpienie <xref:System.String>, które jest wynikiem interpolowanej rozdzielczości ciągu z elementami wyrażenia interpolacji, które są zastępowane poprawnie sformatowanymi reprezentacjami ciągu wyników.</span><span class="sxs-lookup"><span data-stu-id="86c77-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="86c77-138">Ta konwersja używa <xref:System.Globalization.CultureInfo.CurrentCulture> do formatowania wyników wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="86c77-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="86c77-139">Konwersja ciągu interpolowanego na wystąpienie <xref:System.FormattableString>, które reprezentuje ciąg formatu złożonego wraz z wynikami wyrażenia do sformatowania.</span><span class="sxs-lookup"><span data-stu-id="86c77-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="86c77-140">Pozwala to na tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego wystąpienia <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="86c77-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="86c77-141">W tym celu należy wywołać jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="86c77-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="86c77-142">Przeciążenie <xref:System.FormattableString.ToString>, które tworzy ciąg wynikowy dla <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="86c77-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="86c77-143">Metoda <xref:System.FormattableString.Invariant%2A>, która generuje ciąg wynikowy dla <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="86c77-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="86c77-144">Metoda <xref:System.FormattableString.ToString(System.IFormatProvider)>, która generuje ciąg wynikowy dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="86c77-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="86c77-145">Można również użyć metody <xref:System.FormattableString.ToString(System.IFormatProvider)>, aby zapewnić zdefiniowaną przez użytkownika implementację interfejsu <xref:System.IFormatProvider>, która obsługuje niestandardowe formatowanie.</span><span class="sxs-lookup"><span data-stu-id="86c77-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="86c77-146">Aby uzyskać więcej informacji, zobacz sekcję [formatowanie niestandardowe przy użyciu ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) [typów formatowania w artykule .NET](../../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="86c77-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="86c77-147">Konwersja ciągu interpolowanego na wystąpienie <xref:System.IFormattable>, które również umożliwia tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego wystąpienia <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="86c77-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="86c77-148">W poniższym przykładzie zastosowano niejawną konwersję w celu <xref:System.FormattableString> tworzenia ciągów wynikowych specyficznych dla kultury:</span><span class="sxs-lookup"><span data-stu-id="86c77-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="86c77-149">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="86c77-149">Additional resources</span></span>

<span data-ttu-id="86c77-150">Jeśli dopiero zaczynasz interpolację ciągów, zobacz [Interpolacja ciągów w C# ](../../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="86c77-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="86c77-151">Możesz również sprawdzić inne [interpolacje ciągów w C# ](../../tutorials/string-interpolation.md) samouczku, w którym pokazano, jak używać interpolowanych ciągów do tworzenia sformatowanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="86c77-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="86c77-152">Kompilacja ciągów interpolowanych</span><span class="sxs-lookup"><span data-stu-id="86c77-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="86c77-153">Jeśli ciąg interpolowany ma typ `string`, zazwyczaj jest przekształcany do wywołania metody <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86c77-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="86c77-154">Kompilator może zastąpić <xref:System.String.Format%2A?displayProperty=nameWithType> z <xref:System.String.Concat%2A?displayProperty=nameWithType>, jeśli przeanalizowane zachowanie byłoby równoważne z konkatenacją.</span><span class="sxs-lookup"><span data-stu-id="86c77-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="86c77-155">Jeśli ciąg interpolowany ma typ <xref:System.IFormattable> lub <xref:System.FormattableString>, kompilator generuje wywołanie metody <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86c77-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="86c77-156">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86c77-156">C# language specification</span></span>

<span data-ttu-id="86c77-157">Aby uzyskać więcej informacji, zobacz sekcję [interpolowane ciągi](~/_csharplang/spec/expressions.md#interpolated-strings) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="86c77-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86c77-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86c77-158">See also</span></span>

- [<span data-ttu-id="86c77-159">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="86c77-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="86c77-160">Znaki specjalne języka C#</span><span class="sxs-lookup"><span data-stu-id="86c77-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="86c77-161">Ciągi</span><span class="sxs-lookup"><span data-stu-id="86c77-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="86c77-162">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="86c77-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="86c77-163">Formatowanie złożone</span><span class="sxs-lookup"><span data-stu-id="86c77-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
