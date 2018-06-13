---
title: Ciąg interpolacji w języku C#
description: Dowiedz się, jak dołączyć wyniki sformatowany wyrażenia ciągu wynik w języku C# z interpolacji ciągu.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 447e87cd4aae49896f0efbb8ece6097181079266
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058942"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="bd404-103">Ciąg interpolacji w języku C#</span><span class="sxs-lookup"><span data-stu-id="bd404-103">String interpolation in C#</span></span> #

<span data-ttu-id="bd404-104">Ten samouczek przedstawia sposób użycia [ciągu interpolacji](../language-reference/tokens/interpolated.md) sformatowanie i dołączyć wyniki wyrażenia ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="bd404-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="bd404-105">Przykładów założono, że czytelnik zna podstawowe pojęcia języka C# i formatowanie typu .NET.</span><span class="sxs-lookup"><span data-stu-id="bd404-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="bd404-106">Jeśli jesteś nowym użytkownikiem interpolacji ciąg lub formatowania typu .NET, zapoznaj się [szybkiego startu interpolacji interakcyjne ciąg](../quick-starts/interpolated-strings.yml) pierwszy.</span><span class="sxs-lookup"><span data-stu-id="bd404-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation quickstart](../quick-starts/interpolated-strings.yml) first.</span></span> <span data-ttu-id="bd404-107">Aby uzyskać więcej informacji na temat typy formatowania w .NET, zobacz [typy formatowania w .NET](../../standard/base-types/formatting-types.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bd404-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="bd404-108">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="bd404-108">Introduction</span></span>

<span data-ttu-id="bd404-109">[Ciągu interpolacji](../language-reference/tokens/interpolated.md) funkcji jest oparty na [złożone formatowanie](../../standard/base-types/composite-formatting.md) funkcji i zapewnia bardziej czytelny i wygodne składni zawiera wyrażenie sformatowane wyniki w ciągu wynik.</span><span class="sxs-lookup"><span data-stu-id="bd404-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="bd404-110">Aby zidentyfikować ciąg literału jako ciągu interpolowanym, dołączenie wartości za pomocą `$` symbolu.</span><span class="sxs-lookup"><span data-stu-id="bd404-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="bd404-111">Można osadzić dowolne prawidłowe C# wyrażenie zwracające wartość w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="bd404-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="bd404-112">W poniższym przykładzie, jak Obliczanie wyrażenia jego wynik jest konwertowana na ciąg i uwzględniona w parametrach wyników:</span><span class="sxs-lookup"><span data-stu-id="bd404-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="bd404-113">Jak w przykładzie pokazano, można użyć wyrażenia w ciągu interpolowanym, należy ująć w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="bd404-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="bd404-114">W czasie kompilacji ciągu interpolowanym zwykle jest przekształcana na <xref:System.String.Format%2A?displayProperty=nameWithType> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="bd404-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="bd404-115">Dzięki temu wszystkie możliwości [ciągu formatowania złożonego](../../standard/base-types/composite-formatting.md) dostępne do użycia z również ciągi interpolowane funkcji.</span><span class="sxs-lookup"><span data-stu-id="bd404-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="bd404-116">Jak określać ciągu formatu dla interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="bd404-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="bd404-117">Określ ciąg formatu, który jest obsługiwany przez typ wyniku wyrażenia wykonując interpolowanego wyrażenia dwukropka (":"), a ciąg formatu:</span><span class="sxs-lookup"><span data-stu-id="bd404-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="bd404-118">Poniższy przykład przedstawia sposób określić format standardowe i niestandardowe ciągi dla wyrażeń, które powodują powstanie daty i godziny lub wyników liczbowych:</span><span class="sxs-lookup"><span data-stu-id="bd404-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="bd404-119">Aby uzyskać więcej informacji, zobacz [składnika ciąg formatu](../../standard/base-types/composite-formatting.md#format-string-component) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bd404-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="bd404-120">Tej sekcji zamieszczono linki do tematów opisujących ciągi formatujące standardowe i niestandardowe obsługiwane przez typy podstawowe .NET.</span><span class="sxs-lookup"><span data-stu-id="bd404-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="bd404-121">Sterowanie pola szerokości i wyrównania sformatowany interpolowanego wyrażenia</span><span class="sxs-lookup"><span data-stu-id="bd404-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="bd404-122">Określ szerokość pola minimalna i wyrównanie do wyniku wyrażenia sformatowany wykonując interpolowanego wyrażenia za pomocą przecinka (",") i wyrażenie stałe:</span><span class="sxs-lookup"><span data-stu-id="bd404-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="bd404-123">Jeśli *wyrównanie* wartość jest dodatnia, wyniku wyrażenia sformatowany jest wyrównany do prawej; Jeśli ujemną, jest wyrównany.</span><span class="sxs-lookup"><span data-stu-id="bd404-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="bd404-124">Jeśli trzeba określić wyrównanie i ciąg formatu, uruchom za pomocą składnika wyrównania:</span><span class="sxs-lookup"><span data-stu-id="bd404-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="bd404-125">Poniższy przykład przedstawia sposób Określanie wyrównania i używa potoku znaków ("|") do rozdzielenia pól tekstowych:</span><span class="sxs-lookup"><span data-stu-id="bd404-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="bd404-126">Jako przykład przedstawiono dane wyjściowe, jeśli długość wyniku wyrażenia sformatowany przekracza określony szerokość pola *wyrównanie* wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="bd404-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="bd404-127">Aby uzyskać więcej informacji, zobacz [składnika wyrównanie](../../standard/base-types/composite-formatting.md#alignment-component) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bd404-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="bd404-128">Jak używać sekwencji unikowych w ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="bd404-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="bd404-129">Ciągi interpolowane obsługuje wszystkie sekwencje specjalne, które mogą być używane w literałach ciągu zwykłego.</span><span class="sxs-lookup"><span data-stu-id="bd404-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="bd404-130">Aby uzyskać więcej informacji, zobacz [sekwencji unikowych ciąg](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="bd404-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="bd404-131">Aby zinterpretować sekwencji unikowych jako literału, należy użyć [dosłownego wyrażenia](../language-reference/tokens/verbatim.md) literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="bd404-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="bd404-132">Rozpoczyna się od ciągu dosłownego wyrażenia interpolowane `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="bd404-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="bd404-133">Uwzględnienie nawias klamrowy "{" lub "}", w wyniku ciągu, użyj dwa nawiasy klamrowe, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="bd404-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="bd404-134">Aby uzyskać więcej informacji, zobacz [anulowanie nawiasów klamrowych](../../standard/base-types/composite-formatting.md#escaping-braces) sekcji [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bd404-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="bd404-135">Poniższy przykład pokazuje, jak dołączyć nawiasy klamrowe w ciągu wynik i utworzyć dosłownego wyrażenia ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="bd404-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="bd404-136">Jak używać trójargumentowy operator warunkowy `?:` w wyrażeniu interpolowane</span><span class="sxs-lookup"><span data-stu-id="bd404-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="bd404-137">Jako dwukropkiem (":") ma specjalne znaczenie w elemencie z interpolowanego wyrażenia, aby można było używać [operator warunkowy](../language-reference/operators/conditional-operator.md) w wyrażeniu, należy ująć go w nawiasy, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bd404-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="bd404-138">Jak utworzyć ciąg specyficzne dla kultury wynik z interpolacji ciągu</span><span class="sxs-lookup"><span data-stu-id="bd404-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="bd404-139">Domyślnie ciągu interpolowanym używa bieżącej kultury, zdefiniowane przez <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> właściwości dla wszystkich operacji formatowania.</span><span class="sxs-lookup"><span data-stu-id="bd404-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="bd404-140">Użyj niejawna konwersja ciągu interpolowanym do <xref:System.FormattableString?displayProperty=nameWithType> wystąpienia i wywołanie jego <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby utworzyć parametry specyficzne dla kultury wynik.</span><span class="sxs-lookup"><span data-stu-id="bd404-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="bd404-141">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="bd404-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="bd404-142">Jak pokazano na przykładzie, można użyć jednego <xref:System.FormattableString> wystąpienie do generowania wielu ciągów wynik dla różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="bd404-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="bd404-143">Jak utworzyć ciąg wynik użyta Niezmienna kultura</span><span class="sxs-lookup"><span data-stu-id="bd404-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="bd404-144">Wraz z programem <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, można użyć statycznych <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metodę, aby rozpoznać ciągu interpolowanym ciąg wynik <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="bd404-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="bd404-145">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="bd404-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="bd404-146">Wniosek</span><span class="sxs-lookup"><span data-stu-id="bd404-146">Conclusion</span></span>

<span data-ttu-id="bd404-147">W tym samouczku opisano typowe scenariusze użycia interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="bd404-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="bd404-148">Aby uzyskać więcej informacji na temat interpolacji ciągu, zobacz [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bd404-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="bd404-149">Aby uzyskać więcej informacji na temat typy formatowania w .NET, zobacz [typy formatowania w .NET](../../standard/base-types/formatting-types.md) i [złożone formatowanie](../../standard/base-types/composite-formatting.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="bd404-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd404-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd404-150">See also</span></span>

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[<span data-ttu-id="bd404-151">Ciągi</span><span class="sxs-lookup"><span data-stu-id="bd404-151">Strings</span></span>](../programming-guide/strings/index.md)  
