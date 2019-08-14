---
title: Co nowego w C# 6- C# przewodniku
description: Poznaj nowe funkcje w C# wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971382"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="537e0-103">Co nowego w C# 6</span><span class="sxs-lookup"><span data-stu-id="537e0-103">What's New in C# 6</span></span>

<span data-ttu-id="537e0-104">Wersja 6,0 systemu C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="537e0-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="537e0-105">Ogólnym efektem tych funkcji jest pisanie bardziej zwięzłego kodu, który jest również bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="537e0-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="537e0-106">Składnia zawiera mniej procedury dla wielu typowych praktyk.</span><span class="sxs-lookup"><span data-stu-id="537e0-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="537e0-107">Łatwiej jest zobaczyć cel projektowania z mniejszą procedury.</span><span class="sxs-lookup"><span data-stu-id="537e0-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="537e0-108">Poznaj te funkcje również, aby zwiększyć produktywność i napisać bardziej czytelny kod.</span><span class="sxs-lookup"><span data-stu-id="537e0-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="537e0-109">Możesz skoncentrować się na swoich funkcjach, niż w konstrukcjach języka.</span><span class="sxs-lookup"><span data-stu-id="537e0-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="537e0-110">Pozostała część tego artykułu zawiera omówienie każdej z tych funkcji z linkiem do eksplorowania każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="537e0-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="537e0-111">Możesz również zapoznać się z funkcjami w [interaktywnej eksplorowaniu C# ](../tutorials/exploration/csharp-6.yml) w sekcji samouczki.</span><span class="sxs-lookup"><span data-stu-id="537e0-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="537e0-112">Autowłaściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="537e0-112">Read-only auto-properties</span></span>

<span data-ttu-id="537e0-113">*Właściwości autotylko do odczytu* zapewniają bardziej zwięzłą składnię do tworzenia niezmiennych typów.</span><span class="sxs-lookup"><span data-stu-id="537e0-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="537e0-114">Właściwość autoproperty deklaruje się tylko przy użyciu metody dostępu get:</span><span class="sxs-lookup"><span data-stu-id="537e0-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="537e0-115">Właściwości `FirstName` i`LastName` można ustawić tylko w treści konstruktora tej samej klasy:</span><span class="sxs-lookup"><span data-stu-id="537e0-115">The `FirstName` and `LastName` properties can be set only in the body of the constructor of the same class:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="537e0-116">Próba ustawienia `LastName` w innej metodzie spowoduje `CS0200` wygenerowanie błędu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="537e0-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="537e0-117">Ta funkcja umożliwia obsługę języków w przypadku tworzenia niezmiennych typów i używa bardziej zwięzłej i wygodnej składni autowłaściwości.</span><span class="sxs-lookup"><span data-stu-id="537e0-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="537e0-118">Jeśli dodanie tej składni nie spowoduje usunięcia dostępnej metody, jest to [zgodna](version-update-considerations.md#binary-compatible-changes)z binarną zmianą.</span><span class="sxs-lookup"><span data-stu-id="537e0-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="537e0-119">Inicjatory właściwości automatycznej</span><span class="sxs-lookup"><span data-stu-id="537e0-119">Auto-property initializers</span></span>

<span data-ttu-id="537e0-120">*Inicjatory właściwości automatycznie* umożliwiają deklarowanie wartości początkowej właściwości autoproperty jako części deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="537e0-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="537e0-121">Element `Grades` członkowski jest inicjowany w miejscu, w którym został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="537e0-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="537e0-122">Dzięki temu można łatwiej wykonać inicjalizację dokładnie jeden raz.</span><span class="sxs-lookup"><span data-stu-id="537e0-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="537e0-123">Inicjalizacja jest częścią deklaracji właściwości, dzięki czemu łatwiej jest zrównać alokację magazynu z interfejsem publicznym dla `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="537e0-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="537e0-124">Składowe funkcji w postaci wyrażeń</span><span class="sxs-lookup"><span data-stu-id="537e0-124">Expression-bodied function members</span></span>

<span data-ttu-id="537e0-125">Wiele składowych, które piszesz, to pojedyncze instrukcje, które mogą być pojedynczymi wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="537e0-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="537e0-126">Zamiast tego Napisz element członkowski z wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="537e0-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="537e0-127">Działa w przypadku metod i właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="537e0-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="537e0-128">Na przykład przesłonięcie `ToString()` jest często doskonałym kandydatem:</span><span class="sxs-lookup"><span data-stu-id="537e0-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="537e0-129">Tej składni można także użyć do właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="537e0-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="537e0-130">Zmiana istniejącego elementu członkowskiego na wyrażenie składowane składowe jest [zgodną](version-update-considerations.md#binary-compatible-changes)z binarną zmianą.</span><span class="sxs-lookup"><span data-stu-id="537e0-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="537e0-131">Używanie static</span><span class="sxs-lookup"><span data-stu-id="537e0-131">using static</span></span>

<span data-ttu-id="537e0-132">*Użycie statycznego* rozszerzenia umożliwia importowanie metod statycznych pojedynczej klasy.</span><span class="sxs-lookup"><span data-stu-id="537e0-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="537e0-133">Należy określić klasę, z której korzystasz:</span><span class="sxs-lookup"><span data-stu-id="537e0-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="537e0-134"><xref:System.Math> Nie zawiera żadnych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="537e0-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="537e0-135">Można również użyć `using static` do zaimportowania metod statycznych klasy dla klasy, która ma zarówno metody statyczne, jak i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="537e0-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="537e0-136">Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="537e0-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="537e0-137">Należy użyć `System.String` w pełni kwalifikowanej nazwy klasy w statycznej instrukcji using.</span><span class="sxs-lookup"><span data-stu-id="537e0-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="537e0-138">Nie można użyć `string` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="537e0-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="537e0-139">W przypadku zaimportowania z `static using` instrukcji metody rozszerzające są tylko w zakresie, gdy są wywoływane przy użyciu składni wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="537e0-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="537e0-140">Nie są one w zakresie, gdy jest wywoływana jako metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="537e0-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="537e0-141">Często są one widoczne w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="537e0-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="537e0-142">Wzorzec LINQ można zaimportować przez <xref:System.Linq.Enumerable>zaimportowanie lub. <xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="537e0-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="537e0-143">Metody rozszerzające są zwykle wywoływane przy użyciu wyrażeń wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="537e0-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="537e0-144">Dodanie nazwy klasy w rzadkim przypadku, gdy są one wywoływane przy użyciu składni wywołania metody statycznej, rozwiązuje niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="537e0-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="537e0-145">`static using` Dyrektywa importuje również wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="537e0-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="537e0-146">Można odwoływać się do wszelkich zagnieżdżonych typów bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="537e0-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="537e0-147">Operatory warunkowe o wartości null</span><span class="sxs-lookup"><span data-stu-id="537e0-147">Null-conditional operators</span></span>

<span data-ttu-id="537e0-148">*Operator warunkowy o wartości null* sprawia, że sprawdzanie wartości null jest znacznie łatwiejsze i płynne.</span><span class="sxs-lookup"><span data-stu-id="537e0-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="537e0-149">Zastąp element członkowski `.` dostępem `?.`:</span><span class="sxs-lookup"><span data-stu-id="537e0-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="537e0-150">W poprzednim przykładzie zmienna `first` jest przypisywana `null` , jeśli obiektem jest `null`.</span><span class="sxs-lookup"><span data-stu-id="537e0-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="537e0-151">W przeciwnym razie jest przypisana wartość `FirstName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="537e0-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="537e0-152">Co ważniejsze, `?.` oznacza, że ten wiersz kodu nie generuje elementu `NullReferenceException` , jeśli `person` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="537e0-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="537e0-153">Zamiast tego, krótkie obwody i zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="537e0-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="537e0-154">Można również użyć operatora warunkowego null dla dostępu do tablicy lub indeksatora.</span><span class="sxs-lookup"><span data-stu-id="537e0-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="537e0-155">Zamień `[]`nawwyrażeniuindeksu `?[]` .</span><span class="sxs-lookup"><span data-stu-id="537e0-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="537e0-156">Poniższe wyrażenie zwraca `string`, niezależnie od `person`wartości.</span><span class="sxs-lookup"><span data-stu-id="537e0-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="537e0-157">Ta konstrukcja jest często używana z operatorem *łączenia wartości null* do przypisywania wartości domyślnych, gdy jedna `null`z właściwości jest.</span><span class="sxs-lookup"><span data-stu-id="537e0-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="537e0-158">W przypadku krótkich obwodów `null` wyrażenia zwracana wartość jest wpisana w celu dopasowania pełnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="537e0-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="537e0-159">Można również użyć `?.` do warunkowego wywoływania metod.</span><span class="sxs-lookup"><span data-stu-id="537e0-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="537e0-160">Najbardziej typowym zastosowaniem funkcji Członkowskich z operatorem warunkowym null jest bezpieczne wywoływanie delegatów (lub obsługi zdarzeń), które `null`mogą być.</span><span class="sxs-lookup"><span data-stu-id="537e0-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="537e0-161">Wywołamy `Invoke` metodę delegata przy użyciu operatora, `?.` Aby uzyskać dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="537e0-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="537e0-162">W artykule dotyczącego [wzorców delegatów](../delegates-patterns.md#handling-null-delegates) można zobaczyć przykład.</span><span class="sxs-lookup"><span data-stu-id="537e0-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="537e0-163">Reguły `?.` operatora zapewniają, że lewa strona operatora jest szacowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="537e0-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="537e0-164">Umożliwia ona wiele idiomy, w tym Poniższy przykład, przy użyciu obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="537e0-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="537e0-165">Upewnienie się, że lewa strona jest szacowana tylko raz, również umożliwia użycie dowolnego wyrażenia, w tym wywołań metod, po lewej stronie`?.`</span><span class="sxs-lookup"><span data-stu-id="537e0-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="537e0-166">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="537e0-166">String interpolation</span></span>

<span data-ttu-id="537e0-167">W C# przypadku opcji 6 Nowa funkcja [interpolacji ciągu](../language-reference/tokens/interpolated.md) umożliwia osadzanie wyrażeń w ciągu.</span><span class="sxs-lookup"><span data-stu-id="537e0-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="537e0-168">Wystarczy wpisać ciąg z `$`wyrażeniami i używać wyrażeń między `{` i `}` zamiast liczb porządkowych:</span><span class="sxs-lookup"><span data-stu-id="537e0-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="537e0-169">W tym przykładzie zastosowano właściwości przedstawionych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="537e0-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="537e0-170">Możesz użyć dowolnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="537e0-170">You can use any expression.</span></span> <span data-ttu-id="537e0-171">Na przykład można obliczyć średnią punktu oceny studenta w ramach interpolacji:</span><span class="sxs-lookup"><span data-stu-id="537e0-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="537e0-172">Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczbę zmiennoprzecinkową z dwoma miejscami dziesiętnymi.</span><span class="sxs-lookup"><span data-stu-id="537e0-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="537e0-173">Często może zajść potrzeba sformatowania ciągu utworzonego przy użyciu określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="537e0-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="537e0-174">Możesz użyć faktu, że obiekt tworzony przez interpolację ciągu może być niejawnie konwertowany na <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="537e0-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="537e0-175"><xref:System.FormattableString> Wystąpienie zawiera ciąg formatu złożonego i wyniki oceny wyrażeń przed przekonwertowaniem ich na ciągi.</span><span class="sxs-lookup"><span data-stu-id="537e0-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="537e0-176"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Użyj metody, aby określić kulturę podczas formatowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="537e0-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="537e0-177">Poniższy przykład generuje ciąg przy użyciu kultury niemieckiej (de-DE).</span><span class="sxs-lookup"><span data-stu-id="537e0-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="537e0-178">(Domyślnie Kultura niemiecki używa znaku "," dla separatora dziesiętnego i znaku "." jako separatora tysięcy).</span><span class="sxs-lookup"><span data-stu-id="537e0-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="537e0-179">Aby rozpocząć pracę z interpolacją ciągów, zobacz [Interpolacja ciągów C# w](../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym, artykuł [interpolacji ciągów](../language-reference/tokens/interpolated.md) i [Interpolacja ciągów w C# ](../tutorials/string-interpolation.md) samouczku.</span><span class="sxs-lookup"><span data-stu-id="537e0-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="537e0-180">Filtry wyjątków</span><span class="sxs-lookup"><span data-stu-id="537e0-180">Exception filters</span></span>

<span data-ttu-id="537e0-181">*Filtry wyjątków* są klauzulami, które określają, kiedy należy zastosować daną klauzulę catch.</span><span class="sxs-lookup"><span data-stu-id="537e0-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="537e0-182">Jeśli wyrażenie używane dla filtru wyjątków jest szacowane do `true`, klauzula catch wykonuje normalne przetwarzanie na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="537e0-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="537e0-183">Jeśli wyrażenie zwróci `false`wartość, `catch` klauzula jest pomijana.</span><span class="sxs-lookup"><span data-stu-id="537e0-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="537e0-184">Jednym z nich jest badanie informacji o wyjątku, aby określić, czy `catch` klauzula może przetworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="537e0-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="537e0-185">`nameof` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="537e0-185">The `nameof` expression</span></span>

<span data-ttu-id="537e0-186">Wyrażenie [nameof](../language-reference/operators/nameof.md) oblicza nazwę symbolu.</span><span class="sxs-lookup"><span data-stu-id="537e0-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="537e0-187">Jest to świetny sposób, aby uzyskać dostęp do narzędzi, gdy potrzebna jest nazwa zmiennej, właściwości lub pola elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="537e0-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="537e0-188">Jednym z najpopularniejszych użycia programu `nameof` jest podanie nazwy symbolu, który spowodował wyjątek:</span><span class="sxs-lookup"><span data-stu-id="537e0-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="537e0-189">Innym zastosowaniem jest używanie aplikacji opartych na języku XAML `INotifyPropertyChanged` , które implementują interfejs:</span><span class="sxs-lookup"><span data-stu-id="537e0-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="537e0-190">Await w blokach catch i finally</span><span class="sxs-lookup"><span data-stu-id="537e0-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="537e0-191">C#5 miało kilka ograniczeń, w których można `await` umieścić wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="537e0-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="537e0-192">Za C# pomocą 6 można teraz używać `await` wyrażeń in `catch` i. `finally`</span><span class="sxs-lookup"><span data-stu-id="537e0-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="537e0-193">Jest to najczęściej używane w scenariuszach rejestrowania:</span><span class="sxs-lookup"><span data-stu-id="537e0-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="537e0-194">Szczegóły implementacji umożliwiające dodanie `await` obsługi wewnątrz `catch` i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem kodu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="537e0-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="537e0-195">Gdy kod wykonywany w `catch` klauzuli or `finally` zgłasza, wykonanie szuka odpowiedniej `catch` klauzuli w następnym otaczającym bloku.</span><span class="sxs-lookup"><span data-stu-id="537e0-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="537e0-196">Jeśli wystąpił bieżący wyjątek, ten wyjątek zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="537e0-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="537e0-197">Dzieje się tak samo w przypadku wyrażeń oczekujących `finally` w `catch` klauzulach i `catch` : odpowiednia wartość jest wyszukiwana, a obecny wyjątek, jeśli istnieje, zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="537e0-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="537e0-198">To zachowanie jest przyczyną, że zaleca się pisanie `catch` i `finally` klauzule uważnie, aby uniknąć wprowadzania nowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="537e0-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="537e0-199">Inicjuj kolekcje asocjacyjne przy użyciu indeksatorów</span><span class="sxs-lookup"><span data-stu-id="537e0-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="537e0-200">*Inicjatory indeksów* to jedna z dwóch funkcji, które sprawiają, że Inicjatory kolekcji są bardziej spójne z użyciem indeksu.</span><span class="sxs-lookup"><span data-stu-id="537e0-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="537e0-201">We wcześniejszych wersjach programu C#można było użyć *inicjatorów kolekcji* z kolekcjami stylów sekwencji, w <xref:System.Collections.Generic.Dictionary%602>tym, dodając nawiasy klamrowe wokół par klucz-wartość:</span><span class="sxs-lookup"><span data-stu-id="537e0-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="537e0-202">Można ich używać z <xref:System.Collections.Generic.Dictionary%602> kolekcjami i innymi typami, w których dostępna `Add` Metoda akceptuje więcej niż jeden argument.</span><span class="sxs-lookup"><span data-stu-id="537e0-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="537e0-203">Nowa składnia obsługuje przypisanie przy użyciu indeksu do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="537e0-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="537e0-204">Ta funkcja oznacza, że Kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do lokalizacji kontenerów sekwencji dla kilku wersji.</span><span class="sxs-lookup"><span data-stu-id="537e0-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="537e0-205">Metody `Add` rozszerzające w inicjatorach kolekcji</span><span class="sxs-lookup"><span data-stu-id="537e0-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="537e0-206">Kolejną funkcją, która ułatwia inicjowanie kolekcji, jest możliwość użycia *metody rozszerzenia* dla `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="537e0-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="537e0-207">Ta funkcja została dodana do parzystości z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="537e0-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="537e0-208">Ta funkcja jest najbardziej przydatna, gdy istnieje Klasa kolekcji niestandardowej, która ma metodę o innej nazwie do semantycznie Dodaj nowe elementy.</span><span class="sxs-lookup"><span data-stu-id="537e0-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="537e0-209">Ulepszone rozwiązanie przeciążania</span><span class="sxs-lookup"><span data-stu-id="537e0-209">Improved overload resolution</span></span>

<span data-ttu-id="537e0-210">Ta Ostatnia funkcja jest prawdopodobnie niezauważalna.</span><span class="sxs-lookup"><span data-stu-id="537e0-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="537e0-211">Istnieją konstrukcje, w których Poprzednia wersja C# kompilatora mogła znaleźć pewne wywołania metody, które zawierają niejednoznaczne wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="537e0-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="537e0-212">Rozważmy tę metodę:</span><span class="sxs-lookup"><span data-stu-id="537e0-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="537e0-213">We wcześniejszych wersjach programu C#wywołanie tej metody przy użyciu składni grupy metod nie powiedzie się:</span><span class="sxs-lookup"><span data-stu-id="537e0-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="537e0-214">Wcześniejszy kompilator nie może rozróżnić `Task.Run(Action)` prawidłowo `Task.Run(Func<Task>())`między i.</span><span class="sxs-lookup"><span data-stu-id="537e0-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="537e0-215">W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="537e0-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="537e0-216">C# 6 kompilator prawidłowo określa, że `Task.Run(Func<Task>())` jest to lepszy wybór.</span><span class="sxs-lookup"><span data-stu-id="537e0-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="537e0-217">Deterministyczne dane wyjściowe kompilatora</span><span class="sxs-lookup"><span data-stu-id="537e0-217">Deterministic compiler output</span></span>

<span data-ttu-id="537e0-218">`-deterministic` Opcja instruuje kompilator, aby wytwarzał zestaw danych wyjściowych o identycznym bajcie dla kolejnych kompilacji tych samych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="537e0-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="537e0-219">Domyślnie każda kompilacja generuje unikatowe dane wyjściowe dla każdej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="537e0-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="537e0-220">Kompilator dodaje sygnaturę czasową i identyfikator GUID generowany na podstawie liczb losowych.</span><span class="sxs-lookup"><span data-stu-id="537e0-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="537e0-221">Użyj tej opcji, jeśli chcesz porównać dane wyjściowe bajty dla bajtów w celu zapewnienia spójności między kompilacjami.</span><span class="sxs-lookup"><span data-stu-id="537e0-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="537e0-222">Aby uzyskać więcej informacji, zobacz artykuł [Opcja kompilatora-deterministyczna](../language-reference/compiler-options/deterministic-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="537e0-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
