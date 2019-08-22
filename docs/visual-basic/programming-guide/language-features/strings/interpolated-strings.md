---
title: Ciągi interpolowane (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: b9dd055154c86da370a984a465ed412f1fd9908c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666950"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="57ae2-102">Ciągi interpolowane (odwołanie Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57ae2-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="57ae2-103">Używane do konstruowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="57ae2-103">Used to construct strings.</span></span>  <span data-ttu-id="57ae2-104">Ciąg interpolowany wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="57ae2-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="57ae2-105">Ciąg interpolowany zwraca ciąg, który zastępuje interpolowane wyrażenia, które zawiera z ich reprezentacją ciągu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="57ae2-106">Ta funkcja jest dostępna w wersji Visual Basic 14 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="57ae2-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="57ae2-107">Argumenty interpolowanego ciągu są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="57ae2-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="57ae2-108">Na przykład ciąg interpolowany</span><span class="sxs-lookup"><span data-stu-id="57ae2-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="57ae2-109">zawiera dwa wyrażenia interpolowane "{name}" i "{hours: gg}".</span><span class="sxs-lookup"><span data-stu-id="57ae2-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="57ae2-110">Równoważny ciąg formatu złożonego to:</span><span class="sxs-lookup"><span data-stu-id="57ae2-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

<span data-ttu-id="57ae2-111">Struktura ciągu interpolowanego jest:</span><span class="sxs-lookup"><span data-stu-id="57ae2-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="57ae2-112">gdzie:</span><span class="sxs-lookup"><span data-stu-id="57ae2-112">where:</span></span>

- <span data-ttu-id="57ae2-113">*pole-Width* jest ze znakiem liczby całkowitej, która wskazuje liczbę znaków w polu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="57ae2-114">Jeśli wartość jest dodatnia, pole jest wyrównane do prawej; w przypadku wartości ujemnych wyrównanych do lewej.</span><span class="sxs-lookup"><span data-stu-id="57ae2-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="57ae2-115">*ciąg formatu* jest ciągiem formatu odpowiednim dla typu formatowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="57ae2-116">Na przykład dla <xref:System.DateTime> wartości może to być [standardowy ciąg formatu daty i godziny](../../../../standard/base-types/standard-date-and-time-format-strings.md) , taki jak "d" lub "d".</span><span class="sxs-lookup"><span data-stu-id="57ae2-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57ae2-117">Nie można mieć żadnego odstępu między `$` `"` i, który uruchamia ciąg.</span><span class="sxs-lookup"><span data-stu-id="57ae2-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="57ae2-118">Powoduje to błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="57ae2-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="57ae2-119">Możesz użyć ciągu interpolowanego wszędzie tam, gdzie można użyć literału ciągu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="57ae2-120">Ciąg interpolowany jest oceniany za każdym razem, gdy wykonywany jest kod z ciągiem interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="57ae2-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="57ae2-121">Pozwala to na oddzielenie definicji i oceny ciągu interpolowanego.</span><span class="sxs-lookup"><span data-stu-id="57ae2-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="57ae2-122">Aby dołączyć nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwóch nawiasów klamrowych "{{" lub "}}".</span><span class="sxs-lookup"><span data-stu-id="57ae2-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="57ae2-123">Aby uzyskać więcej informacji, zobacz sekcję konwersje niejawne.</span><span class="sxs-lookup"><span data-stu-id="57ae2-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="57ae2-124">Jeśli ciąg interpolowany zawiera inne znaki o specjalnym znaczeniu w ciągu interpolowanym, takim jak cudzysłów ("), dwukropek (:) lub przecinek (,), powinny być wyprowadzane w przypadku wystąpienia tekstu w postaci literału lub powinny być zawarte w wyrażeniu ograniczonym przez nawiasy, jeśli są elementami języka zawartymi w wyrażeniu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="57ae2-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="57ae2-125">Poniższy przykład wyprowadza znaki cudzysłowu, aby uwzględnić je w ciągu wynikowym, i używa nawiasów, aby rozdzielić wyrażenie `(age == 1 ? "" : "s")` tak, aby dwukropek nie był interpretowany jako początkowy ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="57ae2-126">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="57ae2-126">Implicit Conversions</span></span>

<span data-ttu-id="57ae2-127">Istnieją trzy niejawne konwersje typów z ciągu interpolowanego:</span><span class="sxs-lookup"><span data-stu-id="57ae2-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="57ae2-128">Konwersja ciągu interpolowanego na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="57ae2-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="57ae2-129">Poniższy przykład zwraca ciąg, którego interpolowane wyrażenia ciągu zostały zastąpione ich reprezentacją ciągu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="57ae2-130">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="57ae2-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="57ae2-131">Jest to ostateczny wynik interpretacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="57ae2-132">Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") są konwertowane na pojedynczy nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="57ae2-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="57ae2-133">Konwersja ciągu interpolowanego na <xref:System.IFormattable> zmienną, która umożliwia tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego <xref:System.IFormattable> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="57ae2-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="57ae2-134">Jest to przydatne do uwzględniania takich elementów jak poprawne formaty liczbowe i daty dla poszczególnych kultur.</span><span class="sxs-lookup"><span data-stu-id="57ae2-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="57ae2-135">Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe do momentu formatowania ciągu przez jawne lub niejawne wywołanie <xref:System.Object.ToString> metody.</span><span class="sxs-lookup"><span data-stu-id="57ae2-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="57ae2-136">Wszystkie zawarte wyrażenia interpolacji są konwertowane na {0}, {1}, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="57ae2-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="57ae2-137">Poniższy przykład używa odbicia, aby wyświetlić elementy członkowskie, a także wartości <xref:System.IFormattable> pól i właściwości zmiennej, która jest tworzona na podstawie interpolowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="57ae2-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="57ae2-138">Przekazuje <xref:System.IFormattable> również zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> do metody.</span><span class="sxs-lookup"><span data-stu-id="57ae2-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="57ae2-139">Należy zauważyć, że ciąg interpolowany może być sprawdzany tylko przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="57ae2-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="57ae2-140">Jeśli zostanie przekazana do metody formatowania ciągu, na przykład <xref:System.Console.WriteLine(System.String)>, jego elementy formatu są rozwiązane i zwracany jest ciąg wynikowy.</span><span class="sxs-lookup"><span data-stu-id="57ae2-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="57ae2-141">Konwersja ciągu interpolowanego na <xref:System.FormattableString> zmienną, która reprezentuje ciąg formatu złożonego.</span><span class="sxs-lookup"><span data-stu-id="57ae2-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="57ae2-142">Sprawdzanie ciągu formatu złożonego i sposób renderowania jako ciąg wynikowy może na przykład ułatwić ochronę przed atakami polegającymi na iniekcji w przypadku tworzenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="57ae2-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="57ae2-143">Obejmuje <xref:System.FormattableString> również:</span><span class="sxs-lookup"><span data-stu-id="57ae2-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="57ae2-144">Przeciążenie generujące ciąg wynikowy <xref:System.Globalization.CultureInfo.CurrentCulture>dla. <xref:System.FormattableString.ToString></span><span class="sxs-lookup"><span data-stu-id="57ae2-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="57ae2-145">Metoda, która tworzy ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>dla elementu. <xref:System.FormattableString.Invariant%2A></span><span class="sxs-lookup"><span data-stu-id="57ae2-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="57ae2-146"><xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, która tworzy ciąg wynikowy dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="57ae2-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="57ae2-147">Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe, dopóki nie sformatujesz.</span><span class="sxs-lookup"><span data-stu-id="57ae2-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="57ae2-148">Wszystkie zawarte wyrażenia interpolacji są konwertowane na {0}, {1}, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="57ae2-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="57ae2-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57ae2-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="57ae2-150">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57ae2-150">Visual Basic Language Reference</span></span>](index.md)
