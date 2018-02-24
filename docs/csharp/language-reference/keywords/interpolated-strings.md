---
title: "Ciągi interpolowane (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="6507b-102">Ciągi interpolowane (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6507b-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="6507b-103">Użyta do skonstruowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="6507b-103">Used to construct strings.</span></span>  <span data-ttu-id="6507b-104">Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="6507b-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="6507b-105">Ciągu interpolowanym zwraca ciąg, który zastępuje interpolowanego wyrażenia, które zawiera ich reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6507b-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="6507b-106">Ta funkcja jest dostępna w C# 6 i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="6507b-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="6507b-107">Argumenty ciągu interpolowanym są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="6507b-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="6507b-108">Na przykład ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="6507b-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="6507b-109">zawiera dwa interpolowanego wyrażenia, "{name}" i "{godziny: hh}".</span><span class="sxs-lookup"><span data-stu-id="6507b-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="6507b-110">Ciąg formatu złożonego równoważne jest:</span><span class="sxs-lookup"><span data-stu-id="6507b-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="6507b-111">Struktura ciągu interpolowanym jest:</span><span class="sxs-lookup"><span data-stu-id="6507b-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="6507b-112">gdzie:</span><span class="sxs-lookup"><span data-stu-id="6507b-112">where:</span></span> 

- <span data-ttu-id="6507b-113">*szerokość pola* jest całkowita wskazującą liczbę znaków w tym polu.</span><span class="sxs-lookup"><span data-stu-id="6507b-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="6507b-114">Jeśli jest dodatnia, pole jest wyrównany do prawej; Jeśli jest ujemna, wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="6507b-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="6507b-115">*Ciąg formatu* jest odpowiednia dla typu obiektu jest sformatowana ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="6507b-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="6507b-116">Na przykład w przypadku <xref:System.DateTime> wartości, może to być standardowa Data i godzina ciąg formatu, takie jak "D" lub "d".</span><span class="sxs-lookup"><span data-stu-id="6507b-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6507b-117">Nie może zawierać żadnych spacji między `$` i `"` zaczynającym się ciąg.</span><span class="sxs-lookup"><span data-stu-id="6507b-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="6507b-118">To powoduje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6507b-118">Doing so causes a compile time error.</span></span>

 <span data-ttu-id="6507b-119">Można użyć ciągu interpolowanym dowolnym można użyć literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="6507b-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="6507b-120">W ciągu interpolowanym jest następuje za każdym razem, który wykonuje kod w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6507b-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="6507b-121">Dzięki temu można rozdzielić definicji i oceny ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6507b-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="6507b-122">Aby uwzględnić nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwa nawiasy klamrowe, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="6507b-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="6507b-123">Zobacz sekcję niejawne konwersje więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="6507b-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="6507b-124">Jeśli w ciągu interpolowanym zawiera znaki o specjalnym znaczeniu w ciągu interpolowanym, takie jak znak cudzysłowu ("), dwukropek (:) lub przecinkami (,), należy wpisywany je Jeśli występują one w tekście literału lub powinny one zostać włączone w wyrażeniu rozdzielone nawiasy, jeśli są one uwzględnione w wyrażeniu interpolowane elementy języka.</span><span class="sxs-lookup"><span data-stu-id="6507b-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="6507b-125">Poniższy przykład specjalne znaki cudzysłowu, aby je uwzględnić w ciągu wynik i używa nawiasów do rozdzielenia wyrażenie `(age == 1 ? "" : "s")` , aby dwukropkiem nie jest interpretowany jako rozpoczynający się ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="6507b-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="6507b-126">Użyj ciągi interpolowane z Verbatim `$` następuje znak `@` znaków.</span><span class="sxs-lookup"><span data-stu-id="6507b-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="6507b-127">Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](string.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6507b-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="6507b-128">Następujący kod to zmodyfikowana wersja poprzedniego fragmentu przy użyciu ciągu dosłownego wyrażenia interpolowane:</span><span class="sxs-lookup"><span data-stu-id="6507b-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="6507b-129">Zmiany formatowania są niezbędne, ponieważ ciągi verbatim podlega `\` sekwencje specjalne.</span><span class="sxs-lookup"><span data-stu-id="6507b-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6507b-130">`$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6507b-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="6507b-131">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="6507b-131">Implicit Conversions</span></span>  

<span data-ttu-id="6507b-132">Istnieją trzy niejawne konwersje typów w ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="6507b-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="6507b-133">Konwersja ciągu interpolowanym do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6507b-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="6507b-134">Poniższy przykład zwraca ciąg, którego wyrażenia ciągu interpolowanym zostały zastąpione ich reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6507b-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="6507b-135">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6507b-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="6507b-136">To końcowy wynik interpretacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6507b-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="6507b-137">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") są konwertowane na jednym nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="6507b-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="6507b-138">Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi zmiennej, która umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6507b-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="6507b-139">Jest to przydatne w przypadku łącznie z czynności, takich jak poprawne formaty liczb i dat dla poszczególnych kultur.</span><span class="sxs-lookup"><span data-stu-id="6507b-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="6507b-140">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostać jako podwójne nawiasy klamrowe do formatu ciągu wywołując jawnie lub niejawnie <xref:System.Object.ToString> metody.</span><span class="sxs-lookup"><span data-stu-id="6507b-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="6507b-141">Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6507b-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="6507b-142">W poniższym przykładzie użyto odbicia, aby wyświetlić elementy członkowskie, a także wartości pola i właściwości <xref:System.IFormattable> zmiennej, która jest tworzona na podstawie ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6507b-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="6507b-143">Przekazuje również <xref:System.IFormattable> zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6507b-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="6507b-144">Należy pamiętać, że ciągu interpolowanym mogą być kontrolowane tylko przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="6507b-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="6507b-145">Jeśli jest przekazywana do ciągu formatowania metody, takie jak <xref:System.Console.WriteLine(System.String)>, jego format elementy zostaną rozwiązane i został zwrócony ciąg wyniku.</span><span class="sxs-lookup"><span data-stu-id="6507b-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="6507b-146">Konwersja ciągu interpolowanym do <xref:System.FormattableString> zmienna, która reprezentuje ciąg formatu złożonego.</span><span class="sxs-lookup"><span data-stu-id="6507b-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="6507b-147">Zapoznanie się ciąg formatu złożone i sposób renderowania w związku z tym ciąg może na przykład pomóc w ochronie przed atakami iniekcji zostały kompilowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="6507b-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="6507b-148"><xref:System.FormattableString> zawiera również <xref:System.FormattableString.ToString> przeciążenia, które pozwalają tworzyć ciągów wynikowych dla <xref:System.Globalization.CultureInfo.InvariantCulture> i <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="6507b-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="6507b-149">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają podwójne nawiasy klamrowe, dopóki nie zostanie sformatowany.</span><span class="sxs-lookup"><span data-stu-id="6507b-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="6507b-150">Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6507b-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="6507b-151">Specyfikacja języka</span><span class="sxs-lookup"><span data-stu-id="6507b-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6507b-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6507b-152">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="6507b-153">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6507b-153">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6507b-154">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6507b-154">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
