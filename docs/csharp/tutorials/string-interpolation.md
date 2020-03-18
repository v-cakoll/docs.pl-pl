---
title: 'Interpolacja ciągów w C #'
description: Dowiedz się, jak dołączyć sformatowane wyniki wyrażenia w ciągu wyników w języku C# z interpolacją ciągów.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039212"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="b21bb-103">Interpolacja ciągów w C\#</span><span class="sxs-lookup"><span data-stu-id="b21bb-103">String interpolation in C\#</span></span>

<span data-ttu-id="b21bb-104">W tym samouczku pokazano, jak używać [interpolacji ciągów](../language-reference/tokens/interpolated.md) do formatowania i uwzględniania wyników wyrażeń w ciągu wyników.</span><span class="sxs-lookup"><span data-stu-id="b21bb-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="b21bb-105">W przykładach przyjęto założenie, że znasz podstawowe pojęcia języka C# i formatowanie typu .NET.</span><span class="sxs-lookup"><span data-stu-id="b21bb-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="b21bb-106">Jeśli dopiero powszawisz się interpolacją ciągów lub formatowaniem typu .NET, najpierw zapoznaj się z [interaktywnym samouczkiem interpolacji ciągów.](exploration/interpolated-strings.yml)</span><span class="sxs-lookup"><span data-stu-id="b21bb-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="b21bb-107">Aby uzyskać więcej informacji na temat typów formatowania w .NET, zobacz [temat Typy formatowania w .NET.](../../standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="b21bb-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b21bb-108">Introduction</span></span>

<span data-ttu-id="b21bb-109">Funkcja [interpolacji ciągów](../language-reference/tokens/interpolated.md) jest zbudowana na złożonej funkcji [formatowania](../../standard/base-types/composite-formatting.md) i zapewnia bardziej czytelną i wygodną składnię w celu uwzględnienia sformatowanych wyników wyrażeń w ciągu wyników.</span><span class="sxs-lookup"><span data-stu-id="b21bb-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="b21bb-110">Aby zidentyfikować literał ciągu jako interpolowany ciąg, `$` należy go potoczyć symbolem.</span><span class="sxs-lookup"><span data-stu-id="b21bb-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="b21bb-111">Można osadzić dowolne prawidłowe wyrażenie C#, które zwraca wartość w interpolowanym ciągu.</span><span class="sxs-lookup"><span data-stu-id="b21bb-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="b21bb-112">W poniższym przykładzie, jak tylko wyrażenie jest oceniane, jego wynik jest konwertowany na ciąg i zawarte w ciągu wyników:</span><span class="sxs-lookup"><span data-stu-id="b21bb-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="b21bb-113">Jak pokazano w przykładzie, należy dołączyć wyrażenie do interpolowanego ciągu, załączając je nawiasami klamrowym:</span><span class="sxs-lookup"><span data-stu-id="b21bb-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="b21bb-114">Interpolowane ciągi obsługują wszystkie możliwości funkcji [formatowania złożonego ciągu.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="b21bb-115">To czyni je bardziej czytelną alternatywą <xref:System.String.Format%2A?displayProperty=nameWithType> dla stosowania metody.</span><span class="sxs-lookup"><span data-stu-id="b21bb-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="b21bb-116">Jak określić ciąg formatu dla wyrażenia interpolacji</span><span class="sxs-lookup"><span data-stu-id="b21bb-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="b21bb-117">Należy określić ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia, wykonując wyrażenie interpolacji z dwukropkiem (":") i ciągformatu:</span><span class="sxs-lookup"><span data-stu-id="b21bb-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="b21bb-118">W poniższym przykładzie pokazano, jak określić standardowe i niestandardowe ciągi formatu dla wyrażeń, które generują datę i godzinę lub wyniki liczbowe:</span><span class="sxs-lookup"><span data-stu-id="b21bb-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="b21bb-119">Aby uzyskać więcej informacji, zobacz sekcję [Formatowanie składników ciągów](../../standard/base-types/composite-formatting.md#format-string-component) w temacie [Formatowanie kompozytowe.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="b21bb-120">Ta sekcja zawiera łącza do tematów, które opisują standardowe i niestandardowe ciągi formatu obsługiwane przez typy podstawowe .NET.</span><span class="sxs-lookup"><span data-stu-id="b21bb-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="b21bb-121">Jak kontrolować szerokość pola i wyrównanie sformatowanego wyrażenia interpolacji</span><span class="sxs-lookup"><span data-stu-id="b21bb-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="b21bb-122">Minimalną szerokość pola i wyrównanie sformatowanego wyniku wyrażenia należy określić, wykonując wyrażenie interpolacji przecinkiem (""),) i wyrażeniem stałym:</span><span class="sxs-lookup"><span data-stu-id="b21bb-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="b21bb-123">Jeśli wartość *wyrównania* jest dodatnia, wynik sformatowanego wyrażenia jest wyrównany do prawej; jeśli jest ujemna, jest wyrównana do lewej.</span><span class="sxs-lookup"><span data-stu-id="b21bb-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="b21bb-124">Jeśli konieczne jest określenie zarówno linii trasowania, jak i ciągu formatu, zacznij od komponentu wyrównania:</span><span class="sxs-lookup"><span data-stu-id="b21bb-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="b21bb-125">W poniższym przykładzie pokazano, jak określić wyrównanie i używa znaków potoku ("|") do rozgraniczania pól tekstowych:</span><span class="sxs-lookup"><span data-stu-id="b21bb-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="b21bb-126">Jak pokazuje przykładowe dane wyjściowe, jeśli długość sformatowanego wyniku wyrażenia przekracza określoną szerokość pola, wartość *wyrównania* jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="b21bb-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="b21bb-127">Aby uzyskać więcej informacji, zobacz sekcję [Komponent wyrównanie](../../standard/base-types/composite-formatting.md#alignment-component) w temacie [Formatowanie kompozytowe.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="b21bb-128">Jak używać sekwencji ucieczki w interpolowanym ciągu</span><span class="sxs-lookup"><span data-stu-id="b21bb-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="b21bb-129">Interpolowane ciągi obsługują wszystkie sekwencje ucieczki, które mogą być używane w zwykłych literałach ciągów.</span><span class="sxs-lookup"><span data-stu-id="b21bb-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="b21bb-130">Aby uzyskać więcej informacji, zobacz [Sekwencje ucieczki ciągów](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="b21bb-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="b21bb-131">Aby interpretować sekwencje ucieczki dosłownie, należy użyć [dosłownego ciągu literał.](../language-reference/tokens/verbatim.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="b21bb-132">Interpolowany ciąg dosłowny zaczyna `$` się od `@` znaku, po którym następuje znak.</span><span class="sxs-lookup"><span data-stu-id="b21bb-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="b21bb-133">Począwszy od Języka C# 8.0, można użyć `$` i `$@"..."` `@$"..."` `@` tokeny w dowolnej kolejności: oba i są prawidłowe interpolowane ciągi dosłowne.</span><span class="sxs-lookup"><span data-stu-id="b21bb-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="b21bb-134">Aby dołączyć nawias klamrowy"{" lub "}", w ciągu wynikowym, należy użyć dwóch nawiasów klamrowych: "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="b21bb-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="b21bb-135">Aby uzyskać więcej informacji, zobacz [sekcję Uciekanie nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) w temacie [Formatowanie złożone.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="b21bb-136">W poniższym przykładzie pokazano, jak uwzględnić nawiasy klamrowe w ciągu wyników i skonstruować dosłowny interpolowany ciąg:</span><span class="sxs-lookup"><span data-stu-id="b21bb-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="b21bb-137">Jak używać operatora `?:` warunkowego ternary w wyrażeniu interpolacji</span><span class="sxs-lookup"><span data-stu-id="b21bb-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="b21bb-138">Jak dwukropek (":") ma szczególne znaczenie w elemencie z wyrażeniem interpolacji, w celu użycia [operatora warunkowego](../language-reference/operators/conditional-operator.md) w wyrażeniu, ujmować go w nawiasy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b21bb-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="b21bb-139">Jak utworzyć ciąg wyniku specyficzny dla kultury z interpolacją ciągu</span><span class="sxs-lookup"><span data-stu-id="b21bb-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="b21bb-140">Domyślnie interpolowany ciąg używa bieżącej kultury zdefiniowanej <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> przez właściwość dla wszystkich operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="b21bb-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="b21bb-141">Użyj niejawnej konwersji interpolowany <xref:System.FormattableString?displayProperty=nameWithType> ciąg do <xref:System.FormattableString.ToString(System.IFormatProvider)> wystąpienia i wywołać jego metodę, aby utworzyć ciąg wynik specyficzny dla kultury.</span><span class="sxs-lookup"><span data-stu-id="b21bb-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="b21bb-142">W poniższym przykładzie pokazano, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="b21bb-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="b21bb-143">Jak pokazano w przykładzie, <xref:System.FormattableString> można użyć jednego wystąpienia do generowania wielu ciągów wyników dla różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="b21bb-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="b21bb-144">Jak utworzyć ciąg wynikowy przy użyciu kultury niezmiennej</span><span class="sxs-lookup"><span data-stu-id="b21bb-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="b21bb-145">Wraz z <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodą można użyć <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metody statycznej, aby rozpoznać interpolowany ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>do ciągu wynikowego dla .</span><span class="sxs-lookup"><span data-stu-id="b21bb-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="b21bb-146">W poniższym przykładzie pokazano, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="b21bb-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="b21bb-147">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="b21bb-147">Conclusion</span></span>

<span data-ttu-id="b21bb-148">W tym samouczku opisano typowe scenariusze użycia interpolacji ciągów.</span><span class="sxs-lookup"><span data-stu-id="b21bb-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="b21bb-149">Aby uzyskać więcej informacji na temat interpolacji ciągów, zobacz [temat Interpolacji ciągów.](../language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="b21bb-150">Aby uzyskać więcej informacji na temat typów formatowania w .NET, zobacz [Tematy formatowania formatowania w .NET](../../standard/base-types/formatting-types.md) i composite tematów [formatowania.](../../standard/base-types/composite-formatting.md)</span><span class="sxs-lookup"><span data-stu-id="b21bb-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="b21bb-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b21bb-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="b21bb-152">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b21bb-152">Strings</span></span>](../programming-guide/strings/index.md)
