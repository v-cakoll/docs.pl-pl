---
title: Ciągi interpolowane (Visual Basic)
ms.date: 10/31/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9501c052f387a522226e957193a8866083aa4233
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="6ce53-102">Ciągi interpolowane (odwołanie w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ce53-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="6ce53-103">Użyta do skonstruowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="6ce53-103">Used to construct strings.</span></span>  <span data-ttu-id="6ce53-104">Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="6ce53-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="6ce53-105">Ciągu interpolowanym zwraca ciąg, który zastępuje interpolowanego wyrażenia, które zawiera ich reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="6ce53-106">Ta funkcja jest dostępna w języku Visual Basic 14 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="6ce53-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="6ce53-107">Argumenty ciągu interpolowanym są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="6ce53-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="6ce53-108">Na przykład ciągu interpolowanym</span><span class="sxs-lookup"><span data-stu-id="6ce53-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="6ce53-109">zawiera dwa interpolowanego wyrażenia, "{name}" i "{godziny: hh}".</span><span class="sxs-lookup"><span data-stu-id="6ce53-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="6ce53-110">Ciąg formatu złożonego równoważne jest:</span><span class="sxs-lookup"><span data-stu-id="6ce53-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="6ce53-111">Struktura ciągu interpolowanym jest:</span><span class="sxs-lookup"><span data-stu-id="6ce53-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="6ce53-112">gdzie:</span><span class="sxs-lookup"><span data-stu-id="6ce53-112">where:</span></span> 

- <span data-ttu-id="6ce53-113">*szerokość pola* jest całkowita wskazującą liczbę znaków w tym polu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="6ce53-114">Jeśli jest dodatnia, pole jest wyrównany do prawej; Jeśli jest ujemna, wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="6ce53-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="6ce53-115">*Ciąg formatu* jest odpowiednia dla typu obiektu jest sformatowana ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="6ce53-116">Na przykład w przypadku <xref:System.DateTime> wartości, może to być [standardowa Data i godzina ciąg formatu](~/docs/standard/base-types/standard-date-and-time-format-strings.md) takich jak "D" lub "d".</span><span class="sxs-lookup"><span data-stu-id="6ce53-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ce53-117">Nie może zawierać żadnych spacji między `$` i `"` zaczynającym się ciąg.</span><span class="sxs-lookup"><span data-stu-id="6ce53-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="6ce53-118">To powoduje wystąpienie błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6ce53-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="6ce53-119">Można użyć ciągu interpolowanym dowolnym można użyć literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="6ce53-120">W ciągu interpolowanym jest następuje za każdym razem, który wykonuje kod w ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6ce53-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="6ce53-121">Dzięki temu można rozdzielić definicji i oceny ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6ce53-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="6ce53-122">Aby uwzględnić nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwa nawiasy klamrowe, "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="6ce53-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="6ce53-123">Zobacz sekcję niejawne konwersje więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="6ce53-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="6ce53-124">Jeśli w ciągu interpolowanym zawiera znaki o specjalnym znaczeniu w ciągu interpolowanym, takie jak znak cudzysłowu ("), dwukropek (:) lub przecinkami (,), należy wpisywany je Jeśli występują one w tekście literału lub powinny one zostać włączone w wyrażeniu rozdzielone nawiasy, jeśli są one uwzględnione w wyrażeniu interpolowane elementy języka.</span><span class="sxs-lookup"><span data-stu-id="6ce53-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="6ce53-125">Poniższy przykład specjalne znaki cudzysłowu, aby je uwzględnić w ciągu wynik i używa nawiasów do rozdzielenia wyrażenie `(age == 1 ? "" : "s")` , aby dwukropkiem nie jest interpretowany jako rozpoczynający się ciągiem formatu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="6ce53-126">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="6ce53-126">Implicit Conversions</span></span>  

<span data-ttu-id="6ce53-127">Istnieją trzy niejawne konwersje typów w ciągu interpolowanym:</span><span class="sxs-lookup"><span data-stu-id="6ce53-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="6ce53-128">Konwersja ciągu interpolowanym do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6ce53-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="6ce53-129">Poniższy przykład zwraca ciąg, którego wyrażenia ciągu interpolowanym zostały zastąpione ich reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="6ce53-130">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6ce53-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="6ce53-131">To końcowy wynik interpretacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="6ce53-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="6ce53-132">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") są konwertowane na jednym nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="6ce53-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="6ce53-133">Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi zmiennej, która umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6ce53-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="6ce53-134">Jest to przydatne w przypadku łącznie z czynności, takich jak poprawne formaty liczb i dat dla poszczególnych kultur.</span><span class="sxs-lookup"><span data-stu-id="6ce53-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="6ce53-135">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostać jako podwójne nawiasy klamrowe do formatu ciągu wywołując jawnie lub niejawnie <xref:System.Object.ToString> metody.</span><span class="sxs-lookup"><span data-stu-id="6ce53-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="6ce53-136">Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6ce53-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="6ce53-137">W poniższym przykładzie użyto odbicia, aby wyświetlić elementy członkowskie, a także wartości pola i właściwości <xref:System.IFormattable> zmiennej, która jest tworzona na podstawie ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="6ce53-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="6ce53-138">Przekazuje również <xref:System.IFormattable> zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6ce53-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="6ce53-139">Należy pamiętać, że ciągu interpolowanym mogą być kontrolowane tylko przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="6ce53-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="6ce53-140">Jeśli jest przekazywana do ciągu formatowania metody, takie jak <xref:System.Console.WriteLine(System.String)>, jego format elementy zostaną rozwiązane i został zwrócony ciąg wyniku.</span><span class="sxs-lookup"><span data-stu-id="6ce53-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="6ce53-141">Konwersja ciągu interpolowanym do <xref:System.FormattableString> zmienna, która reprezentuje ciąg formatu złożonego.</span><span class="sxs-lookup"><span data-stu-id="6ce53-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="6ce53-142">Zapoznanie się ciąg formatu złożone i sposób renderowania w związku z tym ciąg może na przykład pomóc w ochronie przed atakami iniekcji zostały kompilowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="6ce53-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="6ce53-143">A <xref:System.FormattableString> obejmuje również:</span><span class="sxs-lookup"><span data-stu-id="6ce53-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="6ce53-144">A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="6ce53-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="6ce53-145">A <xref:System.FormattableString.Invariant%2A> metodę, która tworzy ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="6ce53-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="6ce53-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="6ce53-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="6ce53-147">Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe, dopóki nie zostanie sformatowany.</span><span class="sxs-lookup"><span data-stu-id="6ce53-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="6ce53-148">Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6ce53-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="6ce53-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ce53-149">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="6ce53-150">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ce53-150">Visual Basic Language Reference</span></span>](index.md)  
 