---
title: Co nowego w języku C# 6 — Przewodnik po języku C#
description: Dowiedz się, nowych funkcji w języku C# w wersji 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: ad3515e1fc7d70e1377f007276c369d2884780f0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194036"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="1250d-103">Co nowego w języku C# 6</span><span class="sxs-lookup"><span data-stu-id="1250d-103">What's New in C# 6</span></span>

<span data-ttu-id="1250d-104">Wersja 6.0 C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="1250d-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="1250d-105">Funkcje w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="1250d-105">Features in this release include:</span></span>

* <span data-ttu-id="1250d-106">[Tylko do odczytu właściwości automatyczne](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="1250d-106">[Read-only auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="1250d-107">Można tworzyć tylko do odczytu właściwości automatyczne, które można ustawić tylko w konstruktorach.</span><span class="sxs-lookup"><span data-stu-id="1250d-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="1250d-108">[Właściwości automatyczne](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="1250d-108">[Auto-property initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="1250d-109">Można napisać inicjalizacji wyrażenia, aby ustawić wartość początkową auto właściwością.</span><span class="sxs-lookup"><span data-stu-id="1250d-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="1250d-110">[Elementy członkowskie z wyrażeniem w treści funkcji](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="1250d-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="1250d-111">Umożliwia tworzenie metod jednej linii za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="1250d-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="1250d-112">[przy użyciu statycznej](#using-static):</span><span class="sxs-lookup"><span data-stu-id="1250d-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="1250d-113">Wszystkie metody klasy pojedynczej można zaimportować do bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1250d-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="1250d-114">[Operatory warunkowe null](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="1250d-114">[Null-conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="1250d-115">Możesz można zwięźle i bezpiecznie uzyskiwać dostęp do elementów członkowskich obiektu nadal trwa sprawdzanie dostępności o wartości null za pomocą operatora warunkowego wartości null.</span><span class="sxs-lookup"><span data-stu-id="1250d-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="1250d-116">[Interpolacja ciągów](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="1250d-116">[String interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="1250d-117">Możesz zapisać ciąg formatowania wyrażeń za pomocą wbudowanego wyrażeń, zamiast argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="1250d-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="1250d-118">[Filtry wyjątków](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="1250d-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="1250d-119">Możesz przechwytywać wyrażenia na podstawie właściwości wyjątku lub inny stan programu.</span><span class="sxs-lookup"><span data-stu-id="1250d-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="1250d-120">[`nameof` Wyrażenie](#the-nameof-expression):</span><span class="sxs-lookup"><span data-stu-id="1250d-120">[The `nameof` expression](#the-nameof-expression):</span></span>
    - <span data-ttu-id="1250d-121">Można pozwolić kompilatorowi Generowanie ciągów reprezentujących symboli.</span><span class="sxs-lookup"><span data-stu-id="1250d-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="1250d-122">[await w catch i finally blokuje](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="1250d-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="1250d-123">Możesz użyć `await` wyrażeń w lokalizacjach, które wcześniej niedopuszczalne je.</span><span class="sxs-lookup"><span data-stu-id="1250d-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="1250d-124">[Inicjatory indeksów](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="1250d-124">[Index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="1250d-125">Można tworzyć wyrażenia inicjowania dla kontenerów asocjacyjnych, a także kontenery sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1250d-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="1250d-126">[Metody rozszerzenia dla inicjatory kolekcji](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="1250d-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="1250d-127">Inicjatory kolekcji może polegać na metody dostępne rozszerzenia, oprócz metod elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1250d-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="1250d-128">[Ulepszona funkcja rozpoznawania przeciążeń](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="1250d-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="1250d-129">Poprawnie rozpoznać niektórych konstrukcji, które poprzednio wygenerowanym teraz wywołania metody niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="1250d-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>
* <span data-ttu-id="1250d-130">[`deterministic` — Opcja kompilatora](#deterministic-compiler-output):</span><span class="sxs-lookup"><span data-stu-id="1250d-130">[`deterministic` compiler option](#deterministic-compiler-output):</span></span>
    - <span data-ttu-id="1250d-131">Opcja kompilatora deterministyczne gwarantuje, że kolejne kompilacje tego samego źródła generują ten sam wynik w binarnym.</span><span class="sxs-lookup"><span data-stu-id="1250d-131">The deterministic compiler option ensures that subsequent compilations of the same source generate the same binary output.</span></span>

<span data-ttu-id="1250d-132">Ogólny efekt tych funkcji jest pisania bardziej zwięzły widok kodu, który jest również bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="1250d-132">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="1250d-133">Składnia zawiera mniej procedury dla wielu typowych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="1250d-133">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="1250d-134">Jest łatwiej zobaczyć założenia projektowe z mniej procedury.</span><span class="sxs-lookup"><span data-stu-id="1250d-134">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="1250d-135">Dowiedz się również, te funkcje i zostanie mu bardziej wydajnej pracy, pisanie czytelność kodu i bardziej skupić się na swoje podstawowe funkcje niż w konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="1250d-135">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="1250d-136">W pozostałej części tego tematu zawiera szczegółowe informacje dotyczące każdej z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1250d-136">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="1250d-137">Ulepszenia właściwości automatycznej</span><span class="sxs-lookup"><span data-stu-id="1250d-137">Auto-property enhancements</span></span>

<span data-ttu-id="1250d-138">Składnia automatycznie implementowanych właściwości (zwykle określane jako "auto właściwości") wprowadzone bardzo łatwo jest tworzyć właściwości, które było proste get i ustaw metody dostępu:</span><span class="sxs-lookup"><span data-stu-id="1250d-138">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="1250d-139">Jednak to prosta składnia ograniczony rodzaje projektów, które można obsługiwać przy użyciu właściwości auto.</span><span class="sxs-lookup"><span data-stu-id="1250d-139">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="1250d-140">C# 6 zwiększa możliwości właściwości automatyczne, dzięki czemu można ich używać w dalszych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="1250d-140">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="1250d-141">Nie trzeba będzie wrócić na bardziej szczegółowy składni deklarowania i manipulowanie pole zapasowe ręcznie tak często.</span><span class="sxs-lookup"><span data-stu-id="1250d-141">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="1250d-142">Nowa składnia jest przeznaczona dla scenariuszy dla właściwości tylko do odczytu i Inicjowanie zmiennej magazynu za auto właściwością.</span><span class="sxs-lookup"><span data-stu-id="1250d-142">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="1250d-143">Auto właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1250d-143">Read-only auto-properties</span></span>

<span data-ttu-id="1250d-144">*Tylko do odczytu właściwości automatyczne* zapewniają bardziej zwięzły widok składnię, aby utworzyć typy niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1250d-144">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="1250d-145">Najbardziej który można pobrać typów niezmienne we wcześniejszych wersjach języka C# został do deklarowania metod ustawiających prywatnych:</span><span class="sxs-lookup"><span data-stu-id="1250d-145">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="1250d-146">Przy użyciu tej składni, kompilator nie upewnij się, że typ naprawdę niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1250d-146">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="1250d-147">Wymusza tylko który `FirstName` i `LastName` właściwości nie są modyfikowane z dowolnego kodu spoza klasy.</span><span class="sxs-lookup"><span data-stu-id="1250d-147">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="1250d-148">Tylko do odczytu właściwości automatyczne włączanie true zachowanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1250d-148">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="1250d-149">Właściwość automatyczną deklarowana za pomocą tylko akcesor pobierania:</span><span class="sxs-lookup"><span data-stu-id="1250d-149">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="1250d-150">`FirstName` i `LastName` właściwości można ustawić tylko w treści konstruktora:</span><span class="sxs-lookup"><span data-stu-id="1250d-150">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="1250d-151">Ustawiany `LastName` w innej metody generuje `CS0200` błąd kompilacji:</span><span class="sxs-lookup"><span data-stu-id="1250d-151">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="1250d-152">Ta funkcja umożliwia obsługę języka wartość true, aby tworzenie typów niezmienne i za pomocą składni właściwości automatycznej bardziej zwięzłe i wygodne.</span><span class="sxs-lookup"><span data-stu-id="1250d-152">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="1250d-153">Jeśli dodanie tej składni nie powoduje usunięcia dostępnej metody, [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="1250d-153">If adding this syntax does not remove an accessible method, it is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="1250d-154">Inicjatory właściwości automatycznej</span><span class="sxs-lookup"><span data-stu-id="1250d-154">Auto-property initializers</span></span>

<span data-ttu-id="1250d-155">*Właściwości automatyczne* umożliwiają deklarowanie początkowa wartość auto właściwością jako część deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="1250d-155">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="1250d-156">We wcześniejszych wersjach te właściwości musi mieć metody ustawiające i trzeba użyć tej metody ustawiającej można zainicjować magazynu danych, używane przez pola pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="1250d-156">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="1250d-157">Dla uczniów lub studentów, zawierający nazwę i listę ocen studentów, należy wziąć pod uwagę tej klasy:</span><span class="sxs-lookup"><span data-stu-id="1250d-157">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="1250d-158">Wraz z rozwojem tej klasy może zawierać innych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1250d-158">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="1250d-159">Każdy konstruktora musi zainicjować tego pola lub będą powodować błędy.</span><span class="sxs-lookup"><span data-stu-id="1250d-159">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="1250d-160">C# 6, można przypisać wartość początkową dla miejsca używanego przez auto właściwością w deklaracji właściwości automatycznej:</span><span class="sxs-lookup"><span data-stu-id="1250d-160">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="1250d-161">`Grades` Elementu członkowskiego jest inicjowany, którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="1250d-161">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="1250d-162">Który sprawia, że łatwiej wykonać inicjowania dokładnie jeden raz.</span><span class="sxs-lookup"><span data-stu-id="1250d-162">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="1250d-163">Inicjowanie jest częścią deklaracji właściwości, dzięki czemu łatwiej jest równoważne Alokacja magazynu za pomocą interfejsu publicznego dla `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="1250d-163">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="1250d-164">Właściwości można za pomocą właściwości odczytu/zapisu, a także właściwości tylko do odczytu, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="1250d-164">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="1250d-165">Elementy członkowskie z wyrażeniem w treści funkcji</span><span class="sxs-lookup"><span data-stu-id="1250d-165">Expression-bodied function members</span></span>

<span data-ttu-id="1250d-166">Treść wiele elementów członkowskich, które napiszemy składają się z tylko jedną instrukcję, która może być reprezentowany jako wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1250d-166">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="1250d-167">Można zmniejszyć tej składni, pisząc zamiast tego elementu członkowskiego z wyrażeniem w treści.</span><span class="sxs-lookup"><span data-stu-id="1250d-167">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="1250d-168">Działa w przypadku metod i właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1250d-168">It works for methods and read-only properties.</span></span> <span data-ttu-id="1250d-169">Na przykład zastępowania metody `ToString()` często jest doskonałym kandydatem:</span><span class="sxs-lookup"><span data-stu-id="1250d-169">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="1250d-170">Elementy członkowskie z wyrażeniem można również użyć właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="1250d-170">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="1250d-171">Zmienianie istniejącego elementu członkowskiego do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="1250d-171">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>


## <a name="using-static"></a><span data-ttu-id="1250d-172">Przy użyciu statycznej</span><span class="sxs-lookup"><span data-stu-id="1250d-172">using static</span></span>

<span data-ttu-id="1250d-173">*Przy użyciu statycznej* ulepszenie umożliwia importowanie metod statycznych w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="1250d-173">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="1250d-174">Wcześniej `using` zestawienie zaimportowane wszystkie typy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1250d-174">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="1250d-175">Często używamy metody statyczne klasy w naszym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1250d-175">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="1250d-176">Wielokrotnie wpisanie nazwy klasy mogą zasłaniać znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="1250d-176">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="1250d-177">Typowym przykładem jest, kiedy piszesz klas, które wykonują wiele obliczeń numerycznych.</span><span class="sxs-lookup"><span data-stu-id="1250d-177">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="1250d-178">Twój kod będzie wyściełana <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> i innych wywołań do różnych metod w <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="1250d-178">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="1250d-179">Nowy `using static` składni wprowadzać tych klas znacznie bardziej przejrzyste do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1250d-179">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="1250d-180">Należy określić klasę, którą używasz:</span><span class="sxs-lookup"><span data-stu-id="1250d-180">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="1250d-181">Teraz można użyć dowolnej metody statycznej w <xref:System.Math> klasy bez kwalifikowania <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="1250d-181">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="1250d-182"><xref:System.Math> Klasa jest przypadek użycia doskonałe dla tej funkcji, ponieważ nie zawiera żadnych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1250d-182">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="1250d-183">Można również użyć `using static` można zaimportować metody statyczne klasy dla klasy, która ma statycznych i metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1250d-183">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="1250d-184">Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="1250d-184">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="1250d-185">Należy użyć w pełni kwalifikowaną nazwę klasy, `System.String` w statycznych przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1250d-185">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="1250d-186">Nie można użyć `string` słowa kluczowego zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1250d-186">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="1250d-187">Teraz można wywołać metody statyczne zdefiniowane w <xref:System.String> klasy bez kwalifikowania tych metod jako elementy członkowskie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="1250d-187">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="1250d-188">`static using` Funkcji i rozszerzenie metod wchodzić w interakcje w różny sposób, a projekt języka uwzględniane niektórych reguł, które w szczególności rozwiązują tych interakcji.</span><span class="sxs-lookup"><span data-stu-id="1250d-188">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="1250d-189">Celem jest, aby zminimalizować prawdopodobieństwo wszelkie istotne zmiany w istniejących ścieżek bazowych kodów, tym Twoich.</span><span class="sxs-lookup"><span data-stu-id="1250d-189">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="1250d-190">Metody rozszerzenia są tylko w zakresie, gdy wywoływany przy użyciu składni wywołania metody rozszerzenia nie wywołanego jako metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="1250d-190">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="1250d-191">Często zobaczysz następujący w kwerendach LINQ.</span><span class="sxs-lookup"><span data-stu-id="1250d-191">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="1250d-192">Możesz zaimportować wzorzec LINQ, importując <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="1250d-192">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="1250d-193">To importuje wszystkie metody w <xref:System.Linq.Enumerable> klasy.</span><span class="sxs-lookup"><span data-stu-id="1250d-193">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="1250d-194">Metody rozszerzenia są jednak tylko w zakresie wywołanego jako metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-194">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="1250d-195">Nie ma ich w zakresie jeśli są one wezwane przy użyciu składni metody statycznej:</span><span class="sxs-lookup"><span data-stu-id="1250d-195">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="1250d-196">Ta decyzja jest, ponieważ metody rozszerzenia są zwykle nazywane przy użyciu wyrażenia wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-196">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="1250d-197">W rzadkich przypadkach, w których są wywoływane przy użyciu statycznej metody należy wywołać składnia jest rozstrzyganie niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1250d-197">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="1250d-198">Wymaganie nazwę klasy jako część wywołania wygląda poddanie.</span><span class="sxs-lookup"><span data-stu-id="1250d-198">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="1250d-199">Istnieje jedna funkcja ostatnie `static using`.</span><span class="sxs-lookup"><span data-stu-id="1250d-199">There's one last feature of `static using`.</span></span> <span data-ttu-id="1250d-200">`static using` Dyrektywy również importuje wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="1250d-200">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="1250d-201">Która pozwala odwoływać się do żadnych zagnieżdżonych typów bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="1250d-201">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="1250d-202">Operatory warunkowe null</span><span class="sxs-lookup"><span data-stu-id="1250d-202">Null-conditional operators</span></span>

<span data-ttu-id="1250d-203">Wartości null skomplikować kodu.</span><span class="sxs-lookup"><span data-stu-id="1250d-203">Null values complicate code.</span></span> <span data-ttu-id="1250d-204">Należy sprawdzić każdy dostęp do zmiennych, aby upewnić się, nie wyłuskujesz `null`.</span><span class="sxs-lookup"><span data-stu-id="1250d-204">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="1250d-205">*Operatora warunkowego wartości null* sprawia, że tych sprawdzeń znacznie łatwiejsze i płynny.</span><span class="sxs-lookup"><span data-stu-id="1250d-205">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="1250d-206">Zwykłe zamienienie przez dostęp do elementu członkowskiego `.` z `?.`:</span><span class="sxs-lookup"><span data-stu-id="1250d-206">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="1250d-207">W poprzednim przykładzie, zmienna `first` przypisano `null` przypadku obiektu osoba `null`.</span><span class="sxs-lookup"><span data-stu-id="1250d-207">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="1250d-208">W przeciwnym razie, pobiera przypisaną wartość `FirstName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1250d-208">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="1250d-209">Co najważniejsze `?.` oznacza, że nie generuje ten wiersz kodu `NullReferenceException` podczas `person` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="1250d-209">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="1250d-210">Zamiast tego short-circuits i tworzy `null`.</span><span class="sxs-lookup"><span data-stu-id="1250d-210">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="1250d-211">Warto również zauważyć, że to wyrażenie zwraca `string`, niezależnie od tego, wartości `person`.</span><span class="sxs-lookup"><span data-stu-id="1250d-211">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="1250d-212">W przypadku krótkich circuiting `null` wartość zwracana jest wpisany pasuje pełnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-212">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="1250d-213">Często możesz użyć tej konstrukcji z *łączenie wartości null* operator można przypisać wartości domyślne, gdy jedna z właściwości `null`:</span><span class="sxs-lookup"><span data-stu-id="1250d-213">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="1250d-214">Po prawej stronie operandu po stronie `?.` operator nie jest ograniczona do właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="1250d-214">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="1250d-215">Można również użyć do warunkowo wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="1250d-215">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="1250d-216">Najczęściej używane funkcje Członkowskie za pomocą operatora warunkowego wartości null jest bezpiecznie wywoływać delegatów (lub programy obsługi zdarzeń), może być `null`.</span><span class="sxs-lookup"><span data-stu-id="1250d-216">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="1250d-217">Możesz to zrobić przez wywołanie metody delegata `Invoke` przy użyciu metody `?.` operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1250d-217">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="1250d-218">Widać w przykładzie</span><span class="sxs-lookup"><span data-stu-id="1250d-218">You can see an example in the</span></span>  
<span data-ttu-id="1250d-219">[Delegowanie wzorców](../delegates-patterns.md#handling-null-delegates) tematu.</span><span class="sxs-lookup"><span data-stu-id="1250d-219">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="1250d-220">Reguły `?.` operatora, upewnij się, że po lewej stronie operatora jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1250d-220">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="1250d-221">To jest ważne i umożliwia wielu idiomy, w tym przykładzie za pomocą procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1250d-221">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="1250d-222">Zacznijmy od użycia programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1250d-222">Let's start with the event handler usage.</span></span> <span data-ttu-id="1250d-223">W poprzednich wersjach języka C# zostałby zachęca do pisania kodu, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="1250d-223">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="1250d-224">Jest to preferowany nad prostsze składni:</span><span class="sxs-lookup"><span data-stu-id="1250d-224">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="1250d-225">Poprzedni przykład wprowadza sytuacji wyścigu.</span><span class="sxs-lookup"><span data-stu-id="1250d-225">The preceding example introduces a race condition.</span></span> <span data-ttu-id="1250d-226">`SomethingHappened` Zdarzenia może mieć subskrybentów po zaznaczeniu tej opcji przed `null`, i tych subskrybentów mógł zostać usunięty, zanim zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="1250d-226">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="1250d-227">Spowodowałoby <xref:System.NullReferenceException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="1250d-227">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="1250d-228">W tej drugiej wersji `SomethingHappened` programu obsługi zdarzeń może mieć wartości null podczas testowania, ale jeśli inny kod usuwa program obsługi, może nadal być null wywołanego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1250d-228">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="1250d-229">Kompilator generuje kod dla `?.` operatora, które gwarantuje, że po lewej stronie (`this.SomethingHappened`) z `?.` wyrażenie jest wykonywane tylko raz, a wynik jest buforowany:</span><span class="sxs-lookup"><span data-stu-id="1250d-229">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="1250d-230">Zapewnienie, że po lewej stronie jest oceniane tylko raz, umożliwi to również użyć dowolnego wyrażenia, w tym wywołań metod w lewej części `?.` nawet jeśli te efekty uboczne, ocenia się je jeden raz, więc efekty uboczne wystąpić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1250d-230">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="1250d-231">Przykładem w naszej zawartości można wyświetlić na [zdarzenia](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="1250d-231">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="1250d-232">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="1250d-232">String interpolation</span></span>

<span data-ttu-id="1250d-233">C# 6 zawiera nową składnię do redagowania ciągi znaków z ciągu i osadzone wyrażenia, które są obliczane, aby utworzyć inne wartości typu ciąg.</span><span class="sxs-lookup"><span data-stu-id="1250d-233">C# 6 contains new syntax for composing strings from a string and embedded expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="1250d-234">Tradycyjnie, trzeba było używać parametry pozycyjne w metodzie, takie jak <xref:System.String.Format%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="1250d-234">Traditionally, you needed to use positional parameters in a method like <xref:System.String.Format%2A?displayProperty=nameWithType>:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="1250d-235">Za pomocą języka C# 6 nowe [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcji umożliwia osadzanie wyrażeń w ciągu.</span><span class="sxs-lookup"><span data-stu-id="1250d-235">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in a string.</span></span> <span data-ttu-id="1250d-236">Po prostu poprzedzony ciąg z `$`:</span><span class="sxs-lookup"><span data-stu-id="1250d-236">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="1250d-237">W tym przykładzie użyto wyrażenia właściwości podstawione wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1250d-237">This example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="1250d-238">Możesz rozwinąć na tej składni, aby użyć dowolnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-238">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="1250d-239">Na przykład można obliczyć Średnia ocen studenta w ramach interpolacji:</span><span class="sxs-lookup"><span data-stu-id="1250d-239">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="1250d-240">Uruchomione w poprzednim przykładzie, może stwierdzisz, że dane wyjściowe `Grades.Average()` może mieć więcej miejsc dziesiętnych niż chcesz.</span><span class="sxs-lookup"><span data-stu-id="1250d-240">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="1250d-241">Składnia interpolacji ciągu obsługuje format ciągów dostępne za pomocą metod formatowania wcześniej.</span><span class="sxs-lookup"><span data-stu-id="1250d-241">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="1250d-242">Należy określić ciąg formatu w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="1250d-242">You specify the format string inside the braces.</span></span> <span data-ttu-id="1250d-243">Dodaj `:` następujące wyrażenie które ma format:</span><span class="sxs-lookup"><span data-stu-id="1250d-243">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="1250d-244">Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.</span><span class="sxs-lookup"><span data-stu-id="1250d-244">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="1250d-245">`:` Zawsze jest interpretowany jako separator wyrażeń formatowana i ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="1250d-245">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="1250d-246">Gdy używa wyrażenie może prowadzić do problemów `:` w inny sposób, takie jak [operator warunkowy](../language-reference/operators/conditional-operator.md):</span><span class="sxs-lookup"><span data-stu-id="1250d-246">This can introduce problems when your expression uses a `:` in another way, such as a [conditional operator](../language-reference/operators/conditional-operator.md):</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="1250d-247">W powyższym przykładzie `:` jest analizowany jako początek ciągu formatu nie należą do operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="1250d-247">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="1250d-248">We wszystkich przypadkach, w którym dzieje się tak należy ująć wyrażenia z nawiasami, aby wymusić na kompilatorze interpretowanie wyrażenia, ponieważ planowane:</span><span class="sxs-lookup"><span data-stu-id="1250d-248">In all cases where this happens, surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="1250d-249">Nie ma żadnych ograniczeń wyrażenia, które można umieścić między nawiasami klamrowymi.</span><span class="sxs-lookup"><span data-stu-id="1250d-249">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="1250d-250">Można wykonać złożonego zapytania LINQ, wewnątrz ciągu interpolowanego do wykonywania obliczeń i wyświetlić wynik:</span><span class="sxs-lookup"><span data-stu-id="1250d-250">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="1250d-251">W tym przykładzie widać, że można zagnieżdżać wyrażenia interpolacji ciągu wewnątrz innego wyrażenia interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="1250d-251">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="1250d-252">W tym przykładzie jest bardzo prawdopodobne, bardziej złożone niż może pojawić się w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="1250d-252">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="1250d-253">Jest to raczej przedstawiają szeroki zakres funkcji.</span><span class="sxs-lookup"><span data-stu-id="1250d-253">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="1250d-254">Dowolne wyrażenie języka C# mogą być umieszczone między nawiasami klamrowymi ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="1250d-254">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

<span data-ttu-id="1250d-255">Aby rozpocząć pracę z Interpolacja ciągów, zapoznaj się z [Interpolacja w ciągów C# ](../tutorials/intro-to-csharp/interpolated-strings.yml) interaktywnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="1250d-255">To get started with string interpolation, check the [String interpolation in C#](../tutorials/intro-to-csharp/interpolated-strings.yml) interactive tutorial.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="1250d-256">Interpolacja ciągów i określonych kultur</span><span class="sxs-lookup"><span data-stu-id="1250d-256">String interpolation and specific cultures</span></span>

<span data-ttu-id="1250d-257">W przykładach pokazano format sekcji ciągi użyciu bieżącej kultury na komputerze, w której kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1250d-257">All the examples shown in the preceding section format the strings using the current culture on the machine where the code executes.</span></span> <span data-ttu-id="1250d-258">Często potrzebne formatującej ciąg powstały, używając określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="1250d-258">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="1250d-259">Aby zrobić, użyj fakt, że obiekt utworzony przez Interpolacja ciągów, które mogą być niejawnie konwertowane na <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1250d-259">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1250d-260"><xref:System.FormattableString> Wystąpienie zawiera ciąg formatu złożonego oraz wynikiem oceny wyrażenia przed rozpoczęciem konwertowania ich na ciągi.</span><span class="sxs-lookup"><span data-stu-id="1250d-260">The <xref:System.FormattableString> instance contains the composite format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="1250d-261">Użyj <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, aby określić kulturę, gdy ciąg formatowania.</span><span class="sxs-lookup"><span data-stu-id="1250d-261">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="1250d-262">Na przykład poniższy przykład tworzy ciąg przy użyciu kultury niemieckim.</span><span class="sxs-lookup"><span data-stu-id="1250d-262">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="1250d-263">(Używa znaku ',' jako separatora dziesiętnego i "." znaków jako separatora.)</span><span class="sxs-lookup"><span data-stu-id="1250d-263">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="1250d-264">Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../language-reference/tokens/interpolated.md) artykułu i [Interpolacja w języku C# ciągów](../tutorials/string-interpolation.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="1250d-264">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) article and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="1250d-265">Filtry wyjątków</span><span class="sxs-lookup"><span data-stu-id="1250d-265">Exception filters</span></span>

<span data-ttu-id="1250d-266">Kolejną nową funkcją w C# 6 jest *filtry wyjątków*.</span><span class="sxs-lookup"><span data-stu-id="1250d-266">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="1250d-267">Filtry wyjątków są klauzule określające stosowania klauzuli catch danego.</span><span class="sxs-lookup"><span data-stu-id="1250d-267">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="1250d-268">Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, klauzuli "catch" wykonuje jej normalne przetwarzanie po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1250d-268">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="1250d-269">Jeśli wyrażenie ma `false`, a następnie `catch` klauzula jest pomijany.</span><span class="sxs-lookup"><span data-stu-id="1250d-269">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="1250d-270">Jednym z zastosowań jest zbadanie informacje o wyjątku, aby określić, czy `catch` klauzuli może przetwarzać wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1250d-270">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="1250d-271">Kod wygenerowany przez filtry wyjątków zapewnia pełniejsze informacje na temat wyjątek zgłoszony i nie jest przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="1250d-271">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="1250d-272">Zanim filtry wyjątków zostały dodane do języka, będziesz potrzebować do pisania kodu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="1250d-272">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="1250d-273">Punkt, w którym wyjątek jest zgłaszany zmiany między dwa poniższe przykłady.</span><span class="sxs-lookup"><span data-stu-id="1250d-273">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="1250d-274">W poprzednim kodzie, gdzie `throw` jest używana klauzula, analizy śladu stosu ani badania zrzuty awaryjne pokaże, że wyjątek `throw` instrukcji w klauzuli "catch".</span><span class="sxs-lookup"><span data-stu-id="1250d-274">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="1250d-275">Obiekt faktyczny wyjątek będzie zawierać oryginalnego stos wywołań, ale wszystkie inne informacje o żadnych zmiennych w stosie wywołań między tym punktem throw i lokalizacja punktu początkowego throw zostało utracone.</span><span class="sxs-lookup"><span data-stu-id="1250d-275">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="1250d-276">Natomiast, za pomocą przetwarzaniu kod przy użyciu filtra wyjątku: wyrażenie filtru wyjątków, które daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="1250d-276">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="1250d-277">W związku z tym, wykonanie nigdy nie przechodzi `catch` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1250d-277">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="1250d-278">Ponieważ `catch` klauzula nie jest wykonywane, nie wykonywania operacji odwijania stosu odbywa się.</span><span class="sxs-lookup"><span data-stu-id="1250d-278">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="1250d-279">Czy oznacza, że oryginalna throw lokalizacji są zachowywane w debugowania działań, które nastąpi później.</span><span class="sxs-lookup"><span data-stu-id="1250d-279">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="1250d-280">Zawsze, gdy należy ocenić pól lub właściwości wyjątku, zamiast polegania wyłącznie na typ wyjątku, użyj filtru wyjątków, aby zachować więcej informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="1250d-280">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="1250d-281">Inny zalecany wzorzec z filtry wyjątków jest używane do rejestrowania procedury.</span><span class="sxs-lookup"><span data-stu-id="1250d-281">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="1250d-282">Użycie tych korzysta też sposób, w której punkt throw wyjątku jest zachowywane podczas daje w wyniku filtra wyjątku `false`.</span><span class="sxs-lookup"><span data-stu-id="1250d-282">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="1250d-283">Metoda rejestrowania będzie metodą, którego argument jest wyjątek, który bezwarunkowo zwraca `false`:</span><span class="sxs-lookup"><span data-stu-id="1250d-283">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="1250d-284">Zawsze wtedy, gdy chcesz rejestrować wyjątek, można dodać klauzulę catch i użycie tej metody jako filtru wyjątków:</span><span class="sxs-lookup"><span data-stu-id="1250d-284">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="1250d-285">Wyjątki są przechwytywane nigdy, ponieważ `LogException` metoda zawsze zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="1250d-285">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="1250d-286">Z filtrem wyjątku zawsze wartość false oznacza, że można umieszczać w tym obsługi rejestrowania przed wszystkie inne programy obsługi wyjątków:</span><span class="sxs-lookup"><span data-stu-id="1250d-286">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="1250d-287">Poprzedni przykład prezentuje bardzo ważne reguł filtry wyjątków.</span><span class="sxs-lookup"><span data-stu-id="1250d-287">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="1250d-288">Filtry wyjątków włączyć scenariusze, w których bardziej ogólnej klauzuli catch wyjątku może następować przed elementem bardziej konkretny akcelerator.</span><span class="sxs-lookup"><span data-stu-id="1250d-288">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="1250d-289">Użytkownik może również mieć taki sam typ wyjątku, są wyświetlane w wielu klauzule catch:</span><span class="sxs-lookup"><span data-stu-id="1250d-289">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="1250d-290">Inny zalecany wzorzec zapobiega klauzule catch przetwarzania wyjątki, gdy jest dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="1250d-290">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="1250d-291">Ta technika pozwala na uruchamianie aplikacji za pomocą debugera i zatrzymać wykonywanie, gdy wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="1250d-291">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="1250d-292">W kodzie należy dodać filtra wyjątku, aby każdy kod odzyskiwania jest wykonywany tylko wtedy, gdy nie jest dołączony debuger:</span><span class="sxs-lookup"><span data-stu-id="1250d-292">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="1250d-293">Po dodaniu w kodzie, należy ustawić swoje debuger przerywa przy wszystkich wyjątkach nieobsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="1250d-293">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="1250d-294">Uruchom program w debugerze i debuger przerywa zawsze, gdy `PerformFailingOperation()` zgłasza `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="1250d-294">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="1250d-295">Debuger przerywa programu, ponieważ w klauzuli "catch" nie można wykonać z powodu filtru wyjątków zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="1250d-295">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="the-nameof-expression"></a><span data-ttu-id="1250d-296">`nameof` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1250d-296">The `nameof` expression</span></span>

<span data-ttu-id="1250d-297">`nameof` Wyrażenie ma nazwę symbolu.</span><span class="sxs-lookup"><span data-stu-id="1250d-297">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="1250d-298">Jest doskonałym sposobem na narzędzia do pracy w każdym przypadku, gdy potrzebna jest nazwa zmiennej, właściwość lub pole elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1250d-298">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="1250d-299">Jedną z najbardziej typowych używa `nameof` ma na celu dostarczenie nazwa symbolu, który spowodował wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1250d-299">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="1250d-300">Innym zastosowaniem jest przy użyciu XAML na podstawie aplikacji, które implementują `INotifyPropertyChanged` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="1250d-300">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="1250d-301">Zaletą korzystania z `nameof` operator za pośrednictwem stałym ciągiem jest zrozumieć symbol narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1250d-301">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="1250d-302">Jeśli używasz narzędzia do refaktoryzacji można zmienić nazwy symbolu go spowoduje zmianę nazwy w `nameof` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-302">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="1250d-303">Stałe ciągów nie mają tej zalety.</span><span class="sxs-lookup"><span data-stu-id="1250d-303">Constant strings don't have that advantage.</span></span> <span data-ttu-id="1250d-304">Spróbuj napisać kod w ulubionym edytorze: zmiana nazwy zmiennej, a także wszystkie `nameof` wyrażenia zostaną również zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="1250d-304">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="1250d-305">`nameof` Wyrażenie powoduje niekwalifikowana nazwa argumentu (`LastName` w poprzednich przykładach) nawet w przypadku używania w pełni kwalifikowana nazwa argumentu:</span><span class="sxs-lookup"><span data-stu-id="1250d-305">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="1250d-306">To `nameof` tworzy wyrażenie `FirstName`, a nie `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="1250d-306">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="1250d-307">Await w Catch i Finally blokuje</span><span class="sxs-lookup"><span data-stu-id="1250d-307">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="1250d-308">C# 5 ma również kilka ograniczeń wokół gdzie można umieścić `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-308">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="1250d-309">Jeden z nich zostało usunięte w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="1250d-309">One of those has been removed in C# 6.</span></span> <span data-ttu-id="1250d-310">Teraz możesz używać `await` w `catch` lub `finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-310">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="1250d-311">Dodanie wyrażeń await w catch i finally bloków może wydawać się skomplikować, jak te są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="1250d-311">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="1250d-312">Dodajmy przykład w celu omówienia, to wygląd.</span><span class="sxs-lookup"><span data-stu-id="1250d-312">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="1250d-313">W dowolnej metody asynchronicznej, można użyć wyrażenia await w klauzuli finally.</span><span class="sxs-lookup"><span data-stu-id="1250d-313">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="1250d-314">Przy użyciu języka C# 6 można również zdefiniować oczekiwania w wyrażeniach catch.</span><span class="sxs-lookup"><span data-stu-id="1250d-314">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="1250d-315">Jest to najczęściej używana w scenariuszach logowania:</span><span class="sxs-lookup"><span data-stu-id="1250d-315">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="1250d-316">Szczegóły implementacji, aby dodać `await` obsługi w `catch` i `finally` klauzule gwarantuje, że zachowanie jest zgodne z zachowaniem dla kodu synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="1250d-316">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="1250d-317">Gdy kod jest wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego.</span><span class="sxs-lookup"><span data-stu-id="1250d-317">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="1250d-318">Jeśli było bieżący wyjątek, ten wyjątek zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="1250d-318">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="1250d-319">W tym celu za pomocą wyrażeń oczekiwane w `catch` i `finally` klauzule: odpowiedniej `catch` są wyszukiwane i bieżący wyjątek, jeśli istnieje, zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="1250d-319">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="1250d-320">To zachowanie jest przyczyna, zaleca się zapisać `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="1250d-320">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="1250d-321">Inicjatory indeksów</span><span class="sxs-lookup"><span data-stu-id="1250d-321">Index initializers</span></span>

<span data-ttu-id="1250d-322">*Inicjatory indeksów* to jedna z dwóch funkcji, które inicjatory kolekcji bardziej spójny z użyciem indeksu.</span><span class="sxs-lookup"><span data-stu-id="1250d-322">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="1250d-323">We wcześniejszych wersjach języka C#, można użyć *inicjatory kolekcji* tylko z kolekcji stylów sekwencji, w tym <xref:System.Collections.Generic.Dictionary%602> , dodając nawiasów klamrowych otaczających par kluczy i wartości:</span><span class="sxs-lookup"><span data-stu-id="1250d-323">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="1250d-324">Teraz można użyć ich z <xref:System.Collections.Generic.Dictionary%602> kolekcji i podobnych typów.</span><span class="sxs-lookup"><span data-stu-id="1250d-324">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="1250d-325">Nowa składnia obsługuje przypisanie do kolekcji przy użyciu indeksu:</span><span class="sxs-lookup"><span data-stu-id="1250d-325">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="1250d-326">Tej funkcji oznacza, że kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do wprowadzonych w miejscu na potrzeby kontenerów sekwencji dla kilku wersji.</span><span class="sxs-lookup"><span data-stu-id="1250d-326">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="1250d-327">Rozszerzenie `Add` metody inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="1250d-327">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="1250d-328">Kolejną funkcją, który ułatwia inicjowanie kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="1250d-328">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="1250d-329">Ta funkcja została dodana przez parzystość za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1250d-329">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="1250d-330">Ta funkcja jest najbardziej użyteczna, gdy masz klasę kolekcji niestandardowej, który ma metodę o innej nazwie do semantycznie dodawania nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="1250d-330">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="1250d-331">Na przykład należy wziąć pod uwagę kolekcję studentów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1250d-331">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="1250d-332">`Enroll` Metoda dodaje studenta.</span><span class="sxs-lookup"><span data-stu-id="1250d-332">The `Enroll` method adds a student.</span></span> <span data-ttu-id="1250d-333">Ale nie należy wykonać `Add` wzorca.</span><span class="sxs-lookup"><span data-stu-id="1250d-333">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="1250d-334">W poprzednich wersjach języka C#, nie można użyć inicjatory kolekcji za pomocą `Enrollment` obiektu:</span><span class="sxs-lookup"><span data-stu-id="1250d-334">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="1250d-335">Teraz możesz, ale tylko wtedy, gdy tworzysz metodę rozszerzenia, która mapuje `Add` do `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="1250d-335">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="1250d-336">Co robisz za pomocą tej funkcji jest do mapowania dowolnej metody dodaje elementy do kolekcji z metodą o nazwie `Add` , tworząc metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1250d-336">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="1250d-337">Rozpoznanie przeciążenia ulepszone</span><span class="sxs-lookup"><span data-stu-id="1250d-337">Improved overload resolution</span></span>

<span data-ttu-id="1250d-338">Funkcja ta ostatnia jest jeden, który prawdopodobnie nie będą zauważyć.</span><span class="sxs-lookup"><span data-stu-id="1250d-338">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="1250d-339">Wystąpiły konstrukcje poprzedniej wersji kompilatora języka C# może mieć wykryto niektóre wywołania metody obejmujące wyrażenia lambda jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="1250d-339">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="1250d-340">Należy wziąć pod uwagę tę metodę:</span><span class="sxs-lookup"><span data-stu-id="1250d-340">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="1250d-341">We wcześniejszych wersjach języka C# wywołanie tej metody, przy użyciu składni metody grupy może zakończyć się niepowodzeniem:</span><span class="sxs-lookup"><span data-stu-id="1250d-341">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="1250d-342">Wcześniej kompilator nie można odróżnić prawidłowo między `Task.Run(Action)` i `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="1250d-342">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="1250d-343">W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="1250d-343">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="1250d-344">Kompilator języka C# 6 poprawnie ustali, że `Task.Run(Func<Task>())` jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="1250d-344">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="1250d-345">Dane wyjściowe kompilatora deterministyczna</span><span class="sxs-lookup"><span data-stu-id="1250d-345">Deterministic compiler output</span></span>

<span data-ttu-id="1250d-346">`-deterministic` Opcji powoduje, że kompilator generuje zestaw identycznych danych wyjściowych dla bajt dla kolejnych kompilacje tych samych plików źródłowych.</span><span class="sxs-lookup"><span data-stu-id="1250d-346">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="1250d-347">Domyślnie każdy kompilacji tworzy unikatowe dane wyjściowe w każdej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1250d-347">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="1250d-348">Kompilator dodaje sygnaturę czasową i identyfikator GUID generowany na podstawie liczby losowe.</span><span class="sxs-lookup"><span data-stu-id="1250d-348">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="1250d-349">Użyj tej opcji, jeśli chcesz porównać dla bajt danych wyjściowych, aby upewnić się, że zostało skompilowane zachowania spójności w.</span><span class="sxs-lookup"><span data-stu-id="1250d-349">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="1250d-350">Aby uzyskać więcej informacji, zobacz [— opcja kompilatora deterministyczne](../language-reference/compiler-options/deterministic-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="1250d-350">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
