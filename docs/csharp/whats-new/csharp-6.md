---
title: Co nowego w języku C# 6 - Przewodnik po językach C#
description: Poznaj nowe funkcje w języku C# w wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399393"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="464b0-103">Co nowego w C# 6</span><span class="sxs-lookup"><span data-stu-id="464b0-103">What's New in C# 6</span></span>

<span data-ttu-id="464b0-104">Wersja 6.0 języka C# zawierała wiele funkcji, które zwiększają produktywność deweloperów.</span><span class="sxs-lookup"><span data-stu-id="464b0-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="464b0-105">Ogólny efekt tych funkcji jest, że piszesz bardziej zwięzły kod, który jest również bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="464b0-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="464b0-106">Składnia zawiera mniej ceremonii dla wielu typowych praktyk.</span><span class="sxs-lookup"><span data-stu-id="464b0-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="464b0-107">Łatwiej jest zobaczyć intencję projektu z mniejszą ceremonią.</span><span class="sxs-lookup"><span data-stu-id="464b0-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="464b0-108">Dobrze się poznaj te funkcje, a będziesz bardziej produktywny i napisz bardziej czytelny kod.</span><span class="sxs-lookup"><span data-stu-id="464b0-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="464b0-109">Możesz skoncentrować się bardziej na swoich funkcjach niż na konstrukcjach języka.</span><span class="sxs-lookup"><span data-stu-id="464b0-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="464b0-110">W dalszej części tego artykułu zawiera omówienie każdej z tych funkcji, z linkiem do eksplorowania każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="464b0-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="464b0-111">Można również eksplorować funkcje w [interaktywnej eksploracji w języku C# 6](../tutorials/exploration/csharp-6.yml) w sekcji samouczków.</span><span class="sxs-lookup"><span data-stu-id="464b0-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="464b0-112">Właściwości automatyczne tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="464b0-112">Read-only auto-properties</span></span>

<span data-ttu-id="464b0-113">*Właściwości automatyczne tylko do odczytu* zapewniają bardziej zwięzłą składnię do tworzenia typów niezmiennych.</span><span class="sxs-lookup"><span data-stu-id="464b0-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="464b0-114">Deklarujesz auto-właściwość tylko z get akcesor:</span><span class="sxs-lookup"><span data-stu-id="464b0-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="464b0-115">I `FirstName` `LastName` właściwości można ustawić tylko w treści konstruktora tej samej klasy:</span><span class="sxs-lookup"><span data-stu-id="464b0-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="464b0-116">Próba ustawienia `LastName` w innej metodzie generuje błąd `CS0200` kompilacji:</span><span class="sxs-lookup"><span data-stu-id="464b0-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="464b0-117">Ta funkcja umożliwia obsługę języka true do tworzenia typów niezmienne i używa bardziej zwięzłe i wygodne składni auto-właściwości.</span><span class="sxs-lookup"><span data-stu-id="464b0-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="464b0-118">Jeśli dodanie tej składni nie powoduje usunięcia dostępnej metody, jest to [zmiana zgodna z binarną](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="464b0-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="464b0-119">Inicjatory właściwości automatycznych</span><span class="sxs-lookup"><span data-stu-id="464b0-119">Auto-property initializers</span></span>

<span data-ttu-id="464b0-120">*Inicjatory właściwości* auto umożliwiają zadeklarowanie wartości początkowej właściwości auto jako części deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="464b0-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="464b0-121">Element `Grades` członkowski jest inicjowany, gdzie jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="464b0-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="464b0-122">To sprawia, że łatwiej wykonać inicjowanie dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="464b0-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="464b0-123">Inicjowanie jest częścią deklaracji właściwości, co ułatwia zrównanie alokacji `Student` magazynu z interfejsem publicznym dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="464b0-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="464b0-124">Elementy członkowskie funkcji zabudowane wyrażeniem</span><span class="sxs-lookup"><span data-stu-id="464b0-124">Expression-bodied function members</span></span>

<span data-ttu-id="464b0-125">Wiele członków, które piszesz są pojedyncze instrukcje, które mogą być pojedyncze wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="464b0-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="464b0-126">Zamiast tego napisz element członkowski zabudowany wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="464b0-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="464b0-127">Działa dla metod i właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="464b0-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="464b0-128">Na przykład zastąpienie `ToString()` jest często świetnym kandydatem:</span><span class="sxs-lookup"><span data-stu-id="464b0-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="464b0-129">Tej składni można również użyć dla właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="464b0-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="464b0-130">Zmiana istniejącego elementu członkowskiego na element członkowski wyrażenia jest [zmianą zgodną z binarną.](version-update-considerations.md#binary-compatible-changes)</span><span class="sxs-lookup"><span data-stu-id="464b0-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="464b0-131">za pomocą statycznego</span><span class="sxs-lookup"><span data-stu-id="464b0-131">using static</span></span>

<span data-ttu-id="464b0-132">*Za pomocą statycznego* rozszerzenia umożliwia importowanie metod statycznych pojedynczej klasy.</span><span class="sxs-lookup"><span data-stu-id="464b0-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="464b0-133">Określasz klasę, której używasz:</span><span class="sxs-lookup"><span data-stu-id="464b0-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="464b0-134">Nie <xref:System.Math> zawiera żadnych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="464b0-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="464b0-135">Można również `using static` użyć do zaimportowania klasy metod statycznych dla klasy, która ma zarówno metody statyczne i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="464b0-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="464b0-136">Jednym z najbardziej przydatnych <xref:System.String>przykładów jest:</span><span class="sxs-lookup"><span data-stu-id="464b0-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="464b0-137">Należy użyć w pełni kwalifikowanej `System.String` nazwy klasy, w instrukcji statycznego using.</span><span class="sxs-lookup"><span data-stu-id="464b0-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="464b0-138">Zamiast tego `string` nie można użyć słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="464b0-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="464b0-139">Podczas importowania `static using` z instrukcji metody rozszerzenia są tylko w zakresie, gdy wywoływane przy użyciu składni wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="464b0-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="464b0-140">Nie są one w zakresie, gdy wywoływana jako metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="464b0-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="464b0-141">Często zobaczysz to w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="464b0-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="464b0-142">Wzór LINQ można zaimportować, <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable>importując lub .</span><span class="sxs-lookup"><span data-stu-id="464b0-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="464b0-143">Zazwyczaj należy wywołać metody rozszerzenia przy użyciu wyrażeń wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="464b0-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="464b0-144">Dodanie nazwy klasy w rzadkich przypadkach, w których nazywasz je przy użyciu składni wywołania metody statycznej rozwiązuje niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="464b0-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="464b0-145">Dyrektywa `static using` importuje również wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="464b0-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="464b0-146">Można odwoływać się do wszystkich typów zagnieżdżonych bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="464b0-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="464b0-147">Operatory warunkowe zerowe</span><span class="sxs-lookup"><span data-stu-id="464b0-147">Null-conditional operators</span></span>

<span data-ttu-id="464b0-148">*Operator warunkowy null* sprawia, że kontrole null znacznie łatwiejsze i płynne.</span><span class="sxs-lookup"><span data-stu-id="464b0-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="464b0-149">Zastąp `.` `?.`dostęp do elementu członkowskiego na:</span><span class="sxs-lookup"><span data-stu-id="464b0-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="464b0-150">W poprzednim przykładzie zmienna `first` jest `null` przypisywana, jeśli `null`obiekt person jest .</span><span class="sxs-lookup"><span data-stu-id="464b0-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="464b0-151">W przeciwnym razie jest przypisywana `FirstName` wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="464b0-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="464b0-152">Co najważniejsze, `?.` oznacza, że ten wiersz kodu `NullReferenceException` nie `person` generuje `null`jeśli zmienna jest .</span><span class="sxs-lookup"><span data-stu-id="464b0-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="464b0-153">Zamiast tego, to zwarcia i zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="464b0-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="464b0-154">Można również użyć null operator warunkowy dla dostępu do tablicy lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="464b0-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="464b0-155">Zamień `[]` w `?[]` wyrażeniu indeksu.</span><span class="sxs-lookup"><span data-stu-id="464b0-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="464b0-156">Następujące wyrażenie zwraca `string`wartość , niezależnie `person`od wartości .</span><span class="sxs-lookup"><span data-stu-id="464b0-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="464b0-157">Często używasz tej konstrukcji z operatorem *łączenia zerowego,* aby przypisać wartości domyślne, gdy jedną z właściwości jest `null`.</span><span class="sxs-lookup"><span data-stu-id="464b0-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="464b0-158">Gdy wyrażenie zwarcia, `null` zwracana wartość jest wpisany, aby dopasować pełne wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="464b0-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="464b0-159">Można również `?.` użyć do warunkowego wywołania metod.</span><span class="sxs-lookup"><span data-stu-id="464b0-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="464b0-160">Najczęstszym zastosowaniem funkcji elementów członkowskich z operatorem warunkowym null jest `null`bezpiecznie wywołać delegatów (lub obsługi zdarzeń), które mogą być .</span><span class="sxs-lookup"><span data-stu-id="464b0-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="464b0-161">Zostanie wywołana metoda pełnomocnika `Invoke` przy `?.` użyciu operatora, aby uzyskać dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="464b0-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="464b0-162">Możesz zobaczyć przykład w artykule [wzorców delegata.](../delegates-patterns.md#handling-null-delegates)</span><span class="sxs-lookup"><span data-stu-id="464b0-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="464b0-163">Zasady `?.` operatora zapewniają, że lewa strona operatora jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="464b0-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="464b0-164">Umożliwia wiele idiomów, w tym w poniższym przykładzie przy użyciu programów obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="464b0-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="464b0-165">Zapewnienie, że lewa strona jest oceniana tylko raz, umożliwia również użycie dowolnego wyrażenia, w tym wywołania metody, po lewej stronie`?.`</span><span class="sxs-lookup"><span data-stu-id="464b0-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="464b0-166">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="464b0-166">String interpolation</span></span>

<span data-ttu-id="464b0-167">W przypadku języka C# 6 nowa funkcja [interpolacji ciągów](../language-reference/tokens/interpolated.md) umożliwia osadzanie wyrażeń w ciągu.</span><span class="sxs-lookup"><span data-stu-id="464b0-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="464b0-168">Po prostu poprzedzaj ciąg z `$`i użyj wyrażeń między `{` i `}` zamiast ordinals:</span><span class="sxs-lookup"><span data-stu-id="464b0-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="464b0-169">W tym przykładzie użyto właściwości wyrażenia podstawione.</span><span class="sxs-lookup"><span data-stu-id="464b0-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="464b0-170">Można użyć dowolnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="464b0-170">You can use any expression.</span></span> <span data-ttu-id="464b0-171">Na przykład można obliczyć średnią punktową ucznia jako część interpolacji:</span><span class="sxs-lookup"><span data-stu-id="464b0-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="464b0-172">Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczbę zmiennoprzecinkową z dwoma miejscami dziesiętnym.</span><span class="sxs-lookup"><span data-stu-id="464b0-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="464b0-173">Często może być konieczne sformatowanie ciągu produkowane przy użyciu określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="464b0-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="464b0-174">Należy użyć faktu, że obiekt wytwarzany przez interpolację <xref:System.FormattableString?displayProperty=nameWithType>ciągu może być niejawnie konwertowany na .</span><span class="sxs-lookup"><span data-stu-id="464b0-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="464b0-175">Wystąpienie <xref:System.FormattableString> zawiera ciąg formatu złożonego i wyniki oceny wyrażeń przed konwersją ich na ciągi.</span><span class="sxs-lookup"><span data-stu-id="464b0-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="464b0-176">Użyj <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, aby określić kulturę podczas formatowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="464b0-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="464b0-177">Poniższy przykład tworzy ciąg przy użyciu kultury niemiecki (de-DE).</span><span class="sxs-lookup"><span data-stu-id="464b0-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="464b0-178">(Domyślnie kultura niemiecka używa znaku ',' dla separatora dziesiętnego i znaku '.' jako separatora tysięcy).</span><span class="sxs-lookup"><span data-stu-id="464b0-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="464b0-179">Aby rozpocząć z interpolacji ciągów, zobacz [Interpolacji ciąg ów w języku c#](../tutorials/exploration/interpolated-strings.yml) interaktywny samouczek, [String interpolacji](../language-reference/tokens/interpolated.md) artykułu i [interpolacji ciąg w języku C#tutorial.](../tutorials/string-interpolation.md)</span><span class="sxs-lookup"><span data-stu-id="464b0-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="464b0-180">Filtry wyjątków</span><span class="sxs-lookup"><span data-stu-id="464b0-180">Exception filters</span></span>

<span data-ttu-id="464b0-181">*Filtry wyjątków* są klauzule, które określają, kiedy należy zastosować danego catch klauzuli.</span><span class="sxs-lookup"><span data-stu-id="464b0-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="464b0-182">Jeśli wyrażenie używane dla filtru `true`wyjątków jest oceniane , catch klauzula wykonuje swoje normalne przetwarzanie na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="464b0-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="464b0-183">Jeśli wyrażenie ocenia `false`, a `catch` następnie klauzula jest pomijana.</span><span class="sxs-lookup"><span data-stu-id="464b0-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="464b0-184">Jednym z nich jest badanie informacji o `catch` wyjątku, aby ustalić, czy klauzula może przetworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="464b0-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="464b0-185">Wyrażenie `nameof`</span><span class="sxs-lookup"><span data-stu-id="464b0-185">The `nameof` expression</span></span>

<span data-ttu-id="464b0-186">[Nameof](../language-reference/operators/nameof.md) wyrażenie oblicza nazwę symbolu.</span><span class="sxs-lookup"><span data-stu-id="464b0-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="464b0-187">Jest to świetny sposób, aby narzędzia działały zawsze, gdy potrzebujesz nazwy zmiennej, właściwości lub pola członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="464b0-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="464b0-188">Jednym z najczęstszych `nameof` zastosowań jest podanie nazwy symbolu, który spowodował wyjątek:</span><span class="sxs-lookup"><span data-stu-id="464b0-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="464b0-189">Inne zastosowanie dotyczy aplikacji opartych na `INotifyPropertyChanged` języku XAML, które implementują interfejs:</span><span class="sxs-lookup"><span data-stu-id="464b0-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="464b0-190">Czekaj w blokach Catch i Finally</span><span class="sxs-lookup"><span data-stu-id="464b0-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="464b0-191">C# 5 miał kilka ograniczeń `await` wokół, gdzie można umieścić wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="464b0-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="464b0-192">Z C# 6, można `await` `catch` teraz `finally` używać w lub wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="464b0-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="464b0-193">Jest to najczęściej używane w scenariuszach rejestrowania:</span><span class="sxs-lookup"><span data-stu-id="464b0-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="464b0-194">Szczegóły implementacji `await` do `catch` dodawania obsługi wewnątrz i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem kodu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="464b0-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="464b0-195">Gdy kod wykonywany w lub `catch` `finally` zgłasza klauzuli, wykonanie szuka odpowiedniej `catch` klauzuli w następnym otaczającym bloku.</span><span class="sxs-lookup"><span data-stu-id="464b0-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="464b0-196">Jeśli istnieje bieżący wyjątek, ten wyjątek zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="464b0-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="464b0-197">To samo dzieje się z `catch` `finally` oczekiwanych wyrażeń i klauzule: odpowiedni `catch` jest wyszukiwany, a bieżący wyjątek, jeśli istnieje, zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="464b0-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="464b0-198">To zachowanie jest powodem, dla `catch` którego `finally` zaleca się dokładne pisanie i klauzule, aby uniknąć wprowadzania nowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="464b0-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="464b0-199">Inicjuj kolekcje asocjacyjne przy użyciu indeksatorów</span><span class="sxs-lookup"><span data-stu-id="464b0-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="464b0-200">*Inicjatory indeksu* jest jedną z dwóch funkcji, które sprawiają, że inicjatory kolekcji bardziej spójne z użycia indeksu.</span><span class="sxs-lookup"><span data-stu-id="464b0-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="464b0-201">We wcześniejszych wersjach języka C#, można użyć *inicjatorów kolekcji kolekcji* sekwencji styl, w tym <xref:System.Collections.Generic.Dictionary%602>, dodając nawiasy klamrowe wokół par kluczy i wartości:</span><span class="sxs-lookup"><span data-stu-id="464b0-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="464b0-202">Można ich używać <xref:System.Collections.Generic.Dictionary%602> z kolekcjami i `Add` innymi typami, w których metoda dostępna akceptuje więcej niż jeden argument.</span><span class="sxs-lookup"><span data-stu-id="464b0-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="464b0-203">Nowa składnia obsługuje przypisanie przy użyciu indeksu do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="464b0-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="464b0-204">Ta funkcja oznacza, że kontenery zestojowego mogą być inicjowane przy użyciu składni podobne ja w miejscu dla kontenerów sekwencji dla kilku wersji.</span><span class="sxs-lookup"><span data-stu-id="464b0-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="464b0-205">Metody `Add` rozszerzenia w inicjatorach kolekcji</span><span class="sxs-lookup"><span data-stu-id="464b0-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="464b0-206">Inną funkcją, która ułatwia inicjowanie kolekcji jest możliwość `Add` użycia metody *rozszerzenia* dla metody.</span><span class="sxs-lookup"><span data-stu-id="464b0-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="464b0-207">Ta funkcja została dodana dla parzystości z języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="464b0-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="464b0-208">Ta funkcja jest najbardziej przydatna, gdy masz niestandardową klasę kolekcji, która ma metodę o innej nazwie niż semantycznie dodawać nowe elementy.</span><span class="sxs-lookup"><span data-stu-id="464b0-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="464b0-209">Ulepszona rozdzielczość przeciążenia</span><span class="sxs-lookup"><span data-stu-id="464b0-209">Improved overload resolution</span></span>

<span data-ttu-id="464b0-210">Ta ostatnia funkcja to ta, której prawdopodobnie nie zauważysz.</span><span class="sxs-lookup"><span data-stu-id="464b0-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="464b0-211">Istnieją konstrukcje, gdzie poprzednia wersja kompilatora C# może znaleźć niektóre wywołania metody obejmujące wyrażenia lambda niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="464b0-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="464b0-212">Należy wziąć pod uwagę tę metodę:</span><span class="sxs-lookup"><span data-stu-id="464b0-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="464b0-213">We wcześniejszych wersjach języka C#wywołanie tej metody przy użyciu składni grupy metod zakończy się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="464b0-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="464b0-214">Wcześniejszy kompilator nie mógł poprawnie `Task.Run(Action)` `Task.Run(Func<Task>())`rozróżnić między i .</span><span class="sxs-lookup"><span data-stu-id="464b0-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="464b0-215">W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="464b0-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="464b0-216">Kompilator C# 6 poprawnie `Task.Run(Func<Task>())` określa, że jest lepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="464b0-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="464b0-217">Deterministyczne dane wyjściowe kompilatora</span><span class="sxs-lookup"><span data-stu-id="464b0-217">Deterministic compiler output</span></span>

<span data-ttu-id="464b0-218">Opcja `-deterministic` instruuje kompilator do tworzenia bajtów dla bajtów identyczny zestaw wyjściowy dla kolejnych kompilacji tych samych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="464b0-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="464b0-219">Domyślnie każda kompilacja tworzy unikatowe dane wyjściowe na każdej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="464b0-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="464b0-220">Kompilator dodaje sygnaturę czasową i identyfikator GUID wygenerowany na podstawie liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="464b0-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="464b0-221">Ta opcja jest używana, jeśli chcesz porównać dane wyjściowe bajtów dla bajtów, aby zapewnić spójność między kompilacjami.</span><span class="sxs-lookup"><span data-stu-id="464b0-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="464b0-222">Aby uzyskać więcej informacji, zobacz [-deterministic kompilator a opcja](../language-reference/compiler-options/deterministic-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="464b0-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
