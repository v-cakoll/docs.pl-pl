---
title: Co nowego w języku C# 6 — Przewodnik po języku C#
description: Dowiedz się, nowych funkcji w języku C# w wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: 478fd512f6b6facfce6d7f70f9691ce15e418d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706185"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="49ed0-103">Co nowego w języku C# 6</span><span class="sxs-lookup"><span data-stu-id="49ed0-103">What's New in C# 6</span></span>

<span data-ttu-id="49ed0-104">Wersja 6.0 C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="49ed0-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="49ed0-105">Ogólny efekt tych funkcji jest pisania bardziej zwięzły widok kodu, który jest również bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="49ed0-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="49ed0-106">Składnia zawiera mniej procedury dla wielu typowych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="49ed0-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="49ed0-107">Jest łatwiej zobaczyć założenia projektowe z mniej procedury.</span><span class="sxs-lookup"><span data-stu-id="49ed0-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="49ed0-108">Dowiedz się również, te funkcje i zostanie mu bardziej wydajnej pracy i napisać bardziej czytelny kod.</span><span class="sxs-lookup"><span data-stu-id="49ed0-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="49ed0-109">Możesz skoncentrować się więcej na temat Twojej funkcji niż w konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="49ed0-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="49ed0-110">W pozostałej części tego artykułu zawiera omówienie każdego z tych funkcji, za pomocą łącza, aby zapoznać się z każdej funkcji.</span><span class="sxs-lookup"><span data-stu-id="49ed0-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="49ed0-111">Możesz też zapoznać się z funkcjami w [możliwość interaktywnego eksplorowania na C# 6](../tutorials/exploration/csharp-6.yml) w sekcji samouczków.</span><span class="sxs-lookup"><span data-stu-id="49ed0-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="49ed0-112">Auto właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49ed0-112">Read-only auto-properties</span></span>

<span data-ttu-id="49ed0-113">*Tylko do odczytu właściwości automatyczne* zapewniają bardziej zwięzły widok składnię, aby utworzyć typy niezmienne.</span><span class="sxs-lookup"><span data-stu-id="49ed0-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="49ed0-114">Właściwość automatyczną deklarowana za pomocą tylko akcesor pobierania:</span><span class="sxs-lookup"><span data-stu-id="49ed0-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="49ed0-115">`FirstName` i `LastName` właściwości można ustawić tylko w treści konstruktora:</span><span class="sxs-lookup"><span data-stu-id="49ed0-115">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="49ed0-116">Ustawiany `LastName` w innej metody generuje `CS0200` błąd kompilacji:</span><span class="sxs-lookup"><span data-stu-id="49ed0-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="49ed0-117">Ta funkcja umożliwia obsługę języka true Tworzenie typów niezmienne i używa składni właściwości automatycznej bardziej zwięzłe i wygodne.</span><span class="sxs-lookup"><span data-stu-id="49ed0-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="49ed0-118">Jeśli dodanie tej składni nie powoduje usunięcia dostępnej metody, to [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="49ed0-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="49ed0-119">Inicjatory właściwości automatycznej</span><span class="sxs-lookup"><span data-stu-id="49ed0-119">Auto-property initializers</span></span>

<span data-ttu-id="49ed0-120">*Właściwości automatyczne* umożliwiają deklarowanie początkowa wartość auto właściwością jako część deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="49ed0-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="49ed0-121">`Grades` Elementu członkowskiego jest inicjowany, którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="49ed0-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="49ed0-122">Który sprawia, że łatwiej wykonać inicjowania dokładnie jeden raz.</span><span class="sxs-lookup"><span data-stu-id="49ed0-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="49ed0-123">Inicjowanie jest częścią deklaracji właściwości, dzięki czemu łatwiej jest równoważne Alokacja magazynu za pomocą interfejsu publicznego dla `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="49ed0-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="49ed0-124">Elementy członkowskie z wyrażeniem w treści funkcji</span><span class="sxs-lookup"><span data-stu-id="49ed0-124">Expression-bodied function members</span></span>

<span data-ttu-id="49ed0-125">Wiele elementów członkowskich, które należy zapisać są pojedynczej instrukcji, które mogą być pojedynczego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="49ed0-126">Zamiast niego zapisu elementu członkowskiego z wyrażeniem w treści.</span><span class="sxs-lookup"><span data-stu-id="49ed0-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="49ed0-127">Działa w przypadku metod i właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="49ed0-128">Na przykład zastępowania metody `ToString()` często jest doskonałym kandydatem:</span><span class="sxs-lookup"><span data-stu-id="49ed0-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="49ed0-129">Dla właściwości tylko do odczytu, można również użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="49ed0-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="49ed0-130">Zmienianie istniejącego elementu członkowskiego do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="49ed0-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="49ed0-131">Przy użyciu statycznej</span><span class="sxs-lookup"><span data-stu-id="49ed0-131">using static</span></span>

<span data-ttu-id="49ed0-132">*Przy użyciu statycznej* ulepszenie umożliwia importowanie metod statycznych w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="49ed0-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="49ed0-133">Należy określić klasę, którą używasz:</span><span class="sxs-lookup"><span data-stu-id="49ed0-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="49ed0-134"><xref:System.Math> Nie zawiera żadnych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="49ed0-135">Można również użyć `using static` można zaimportować metody statyczne klasy dla klasy, która ma statycznych i metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="49ed0-136">Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="49ed0-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="49ed0-137">Należy użyć w pełni kwalifikowaną nazwę klasy, `System.String` w statycznych przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="49ed0-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="49ed0-138">Nie można użyć `string` słowa kluczowego zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="49ed0-139">Po zaimportowaniu z `static using` instrukcji, metody rozszerzające są tylko w zakresie, gdy wywoływany przy użyciu składni wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="49ed0-140">Nie są one w zakresie wywołanego jako metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="49ed0-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="49ed0-141">Często zobaczysz następujący w kwerendach LINQ.</span><span class="sxs-lookup"><span data-stu-id="49ed0-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="49ed0-142">Możesz zaimportować wzorzec LINQ, importując <xref:System.Linq.Enumerable>, lub <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="49ed0-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="49ed0-143">Zwykle wywołują metody rozszerzenia za pomocą wyrażenia wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="49ed0-144">Dodawanie nazwy klasy w rzadkich przypadkach, gdzie ich wywoływania przy użyciu wywołania metody statycznej składni usuwa niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="49ed0-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="49ed0-145">`static using` Dyrektywy również importuje wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="49ed0-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="49ed0-146">Wszelkie zagnieżdżone typy bez kwalifikacji można się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="49ed0-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="49ed0-147">Operatory warunkowe null</span><span class="sxs-lookup"><span data-stu-id="49ed0-147">Null-conditional operators</span></span>

<span data-ttu-id="49ed0-148">*Operatora warunkowego wartości null* sprawia, że sprawdzenia wartości null znacznie łatwiejsze i płynny.</span><span class="sxs-lookup"><span data-stu-id="49ed0-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="49ed0-149">Zastąp dostęp do elementu członkowskiego `.` z `?.`:</span><span class="sxs-lookup"><span data-stu-id="49ed0-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="49ed0-150">W poprzednim przykładzie, zmienna `first` przypisano `null` przypadku obiektu osoba `null`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="49ed0-151">W przeciwnym razie jest przypisywana wartość `FirstName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="49ed0-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="49ed0-152">Co najważniejsze `?.` oznacza, że ten wiersz kodu nie generuje `NullReferenceException` Jeśli `person` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="49ed0-153">Zamiast tego należy short-circuits i zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="49ed0-154">Umożliwia także null operatora warunkowego dostępu do tablicy i indeksatora.</span><span class="sxs-lookup"><span data-stu-id="49ed0-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="49ed0-155">Zastąp `[]` z `?[]` w wyrażeniu indeksu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="49ed0-156">Poniższe wyrażenie zwraca `string`, niezależnie od tego, wartości `person`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="49ed0-157">Często używają tej konstrukcji z *łączenie wartości null* operatora, aby przypisać domyślnej wartości, gdy jedna z właściwości jest `null`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="49ed0-158">Gdy wyrażenie short-circuits, `null` wartość zwracana jest wpisany pasuje pełnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="49ed0-159">Można również użyć `?.` do warunkowo wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="49ed0-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="49ed0-160">Najczęściej używane funkcje Członkowskie za pomocą operatora warunkowego wartości null jest bezpiecznie wywoływać delegatów (lub programy obsługi zdarzeń), może być `null`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="49ed0-161">Wywołasz pełnomocnika `Invoke` przy użyciu metody `?.` operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="49ed0-162">Widać w przykładzie [delegować wzorców](../delegates-patterns.md#handling-null-delegates) artykułu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="49ed0-163">Reguły `?.` operatora, upewnij się, że po lewej stronie operatora jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="49ed0-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="49ed0-164">Umożliwia ona wiele idiomy, w tym w poniższym przykładzie przy użyciu programów obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="49ed0-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="49ed0-165">Zapewnienie, że po lewej stronie jest oceniane tylko raz, umożliwi to również użyć dowolnego wyrażenia, w tym wywołania metody, z lewej strony `?.`</span><span class="sxs-lookup"><span data-stu-id="49ed0-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="49ed0-166">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="49ed0-166">String interpolation</span></span>

<span data-ttu-id="49ed0-167">Za pomocą C# 6, nowe [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja umożliwia osadzanie wyrażeń w ciągu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="49ed0-168">Po prostu poprzedzony ciąg z `$`i używać wyrażeń między `{` i `}` zamiast liczby porządkowe:</span><span class="sxs-lookup"><span data-stu-id="49ed0-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="49ed0-169">W tym przykładzie użyto właściwości podstawione wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="49ed0-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="49ed0-170">Można użyć dowolnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-170">You can use any expression.</span></span> <span data-ttu-id="49ed0-171">Na przykład można obliczyć Średnia ocen studenta w ramach interpolacji:</span><span class="sxs-lookup"><span data-stu-id="49ed0-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="49ed0-172">Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.</span><span class="sxs-lookup"><span data-stu-id="49ed0-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="49ed0-173">Często należy sformatować ciąg powstały, używając określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="49ed0-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="49ed0-174">Możesz użyć fakt, że obiekt utworzony przez Interpolacja ciągów, które mogą być niejawnie konwertowane na <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="49ed0-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="49ed0-175"><xref:System.FormattableString> Wystąpienie zawiera ciąg formatu złożonego oraz wynikiem oceny wyrażenia przed rozpoczęciem konwertowania ich na ciągi.</span><span class="sxs-lookup"><span data-stu-id="49ed0-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="49ed0-176">Użyj <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodę, aby określić kulturę, gdy ciąg formatowania.</span><span class="sxs-lookup"><span data-stu-id="49ed0-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="49ed0-177">Poniższy przykład tworzy ciąg przy użyciu kultury niemiecki (de-DE).</span><span class="sxs-lookup"><span data-stu-id="49ed0-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="49ed0-178">(Domyślnie niemieckiego kultura używa znaku ',' jako separatora dziesiętnego i "." znaków jako separatora.)</span><span class="sxs-lookup"><span data-stu-id="49ed0-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="49ed0-179">Aby rozpocząć pracę z Interpolacja ciągów, zobacz [interpolacji w ciągu C# ](../tutorials/exploration/interpolated-strings.yml) interaktywnego samouczka [Interpolacja ciągów](../language-reference/tokens/interpolated.md) artykułu, a [Interpolacja w C# ](../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="49ed0-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="49ed0-180">Filtry wyjątków</span><span class="sxs-lookup"><span data-stu-id="49ed0-180">Exception filters</span></span>

<span data-ttu-id="49ed0-181">*Filtry wyjątków* są klauzule określające stosowania klauzuli catch danego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="49ed0-182">Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, klauzuli "catch" wykonuje jej normalne przetwarzanie po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="49ed0-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="49ed0-183">Jeśli wyrażenie ma `false`, a następnie `catch` klauzula jest pomijany.</span><span class="sxs-lookup"><span data-stu-id="49ed0-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="49ed0-184">Jednym z zastosowań jest zbadanie informacje o wyjątku, aby określić, czy `catch` klauzuli może przetwarzać wyjątek:</span><span class="sxs-lookup"><span data-stu-id="49ed0-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="49ed0-185">`nameof` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="49ed0-185">The `nameof` expression</span></span>

<span data-ttu-id="49ed0-186">`nameof` Wyrażenie ma nazwę symbolu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-186">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="49ed0-187">Jest doskonałym sposobem na narzędzia do pracy w każdym przypadku, gdy potrzebna jest nazwa zmiennej, właściwość lub pole elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="49ed0-188">Jedną z najbardziej typowych używa `nameof` ma na celu dostarczenie nazwa symbolu, który spowodował wyjątek:</span><span class="sxs-lookup"><span data-stu-id="49ed0-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="49ed0-189">Innym zastosowaniem jest z aplikacji opartych na XAML, które implementują `INotifyPropertyChanged` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="49ed0-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="49ed0-190">Await w Catch i Finally blokuje</span><span class="sxs-lookup"><span data-stu-id="49ed0-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="49ed0-191">C# 5 ma również kilka ograniczeń wokół gdzie można umieścić `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="49ed0-192">Za pomocą C# 6, można teraz używać `await` w `catch` lub `finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49ed0-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="49ed0-193">Jest to najczęściej używana w scenariuszach logowania:</span><span class="sxs-lookup"><span data-stu-id="49ed0-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="49ed0-194">Szczegóły implementacji, aby dodać `await` obsługi w `catch` i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem dla kodu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="49ed0-195">Gdy kod jest wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego.</span><span class="sxs-lookup"><span data-stu-id="49ed0-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="49ed0-196">Jeśli było bieżący wyjątek, ten wyjątek zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="49ed0-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="49ed0-197">W tym celu za pomocą wyrażeń oczekiwane w `catch` i `finally` klauzule: odpowiedniej `catch` są wyszukiwane i bieżący wyjątek, jeśli istnieje, zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="49ed0-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="49ed0-198">To zachowanie jest przyczyna, zaleca się zapisać `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="49ed0-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="49ed0-199">Inicjowanie asocjacyjnych kolekcji przy użyciu indeksatorów</span><span class="sxs-lookup"><span data-stu-id="49ed0-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="49ed0-200">*Inicjatory indeksów* to jedna z dwóch funkcji, które inicjatory kolekcji bardziej spójny z użyciem indeksu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="49ed0-201">We wcześniejszych wersjach programu C#, można użyć *inicjatory kolekcji* z kolekcji stylów sekwencji, w tym <xref:System.Collections.Generic.Dictionary%602>, przez dodawanie nawiasów klamrowych otaczających klucz i wartość pary:</span><span class="sxs-lookup"><span data-stu-id="49ed0-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="49ed0-202">Możesz używać ich z <xref:System.Collections.Generic.Dictionary%602> kolekcje i inne typy miejsce dostępne `Add` metoda przyjmuje więcej niż jeden argument.</span><span class="sxs-lookup"><span data-stu-id="49ed0-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="49ed0-203">Nowa składnia obsługuje przypisanie do kolekcji przy użyciu indeksu:</span><span class="sxs-lookup"><span data-stu-id="49ed0-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="49ed0-204">Tej funkcji oznacza, że kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do wprowadzonych w miejscu na potrzeby kontenerów sekwencji dla kilku wersji.</span><span class="sxs-lookup"><span data-stu-id="49ed0-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="49ed0-205">Rozszerzenie `Add` metody inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="49ed0-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="49ed0-206">Kolejną funkcją, który ułatwia inicjowanie kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="49ed0-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="49ed0-207">Ta funkcja została dodana przez parzystość za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="49ed0-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="49ed0-208">Ta funkcja jest najbardziej użyteczna, gdy masz klasę kolekcji niestandardowej, który ma metodę o innej nazwie do semantycznie dodawania nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="49ed0-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="49ed0-209">Rozpoznanie przeciążenia ulepszone</span><span class="sxs-lookup"><span data-stu-id="49ed0-209">Improved overload resolution</span></span>

<span data-ttu-id="49ed0-210">Funkcja ta ostatnia jest jeden, który prawdopodobnie nie będą zauważyć.</span><span class="sxs-lookup"><span data-stu-id="49ed0-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="49ed0-211">Wystąpiły konstrukcje poprzedniej wersji kompilatora języka C# może mieć wykryto niektóre wywołania metody obejmujące wyrażenia lambda jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="49ed0-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="49ed0-212">Należy wziąć pod uwagę tę metodę:</span><span class="sxs-lookup"><span data-stu-id="49ed0-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="49ed0-213">We wcześniejszych wersjach języka C# wywołanie tej metody, przy użyciu składni metody grupy może zakończyć się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="49ed0-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="49ed0-214">Wcześniej kompilator nie można odróżnić prawidłowo między `Task.Run(Action)` i `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="49ed0-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="49ed0-215">W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="49ed0-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="49ed0-216">Kompilator języka C# 6 poprawnie ustali, że `Task.Run(Func<Task>())` jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="49ed0-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="49ed0-217">Dane wyjściowe kompilatora deterministyczna</span><span class="sxs-lookup"><span data-stu-id="49ed0-217">Deterministic compiler output</span></span>

<span data-ttu-id="49ed0-218">`-deterministic` Opcji powoduje, że kompilator generuje zestaw identycznych danych wyjściowych dla bajt dla kolejnych kompilacje tych samych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="49ed0-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="49ed0-219">Domyślnie każdy kompilacji tworzy unikatowe dane wyjściowe w każdej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="49ed0-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="49ed0-220">Kompilator dodaje sygnaturę czasową i identyfikator GUID generowany na podstawie liczby losowe.</span><span class="sxs-lookup"><span data-stu-id="49ed0-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="49ed0-221">Użyj tej opcji, jeśli chcesz porównać dla bajt danych wyjściowych, aby upewnić się, że zostało skompilowane zachowania spójności w.</span><span class="sxs-lookup"><span data-stu-id="49ed0-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="49ed0-222">Aby uzyskać więcej informacji, zobacz [— opcja kompilatora deterministyczne](../language-reference/compiler-options/deterministic-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="49ed0-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
