---
title: Nowości w języku C# 6 - przewodnik C#
description: Dowiedz się nowych funkcji w języku C# w wersji 6
keywords: .NET, .NET Core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: ea54e9a05120134eea8e1bc9d82302a7513b43e7
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="122e7-104">Nowości w języku C# 6</span><span class="sxs-lookup"><span data-stu-id="122e7-104">What's New in C# 6</span></span>

<span data-ttu-id="122e7-105">6.0 wersji języka C# zawiera wiele funkcji, które zwiększają wydajność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="122e7-105">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="122e7-106">Funkcje w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="122e7-106">Features in this release include:</span></span>

* <span data-ttu-id="122e7-107">[Tylko do odczytu właściwości Auto](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="122e7-107">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="122e7-108">Można tworzyć tylko do odczytu auto właściwości, które można ustawić tylko w przypadku konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="122e7-108">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="122e7-109">[Inicjatory Auto właściwością](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="122e7-109">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="122e7-110">Można pisać wyrażenia inicjowania, aby ustawić początkowej wartości auto właściwością.</span><span class="sxs-lookup"><span data-stu-id="122e7-110">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="122e7-111">[Elementy członkowskie zabudowanych wyrażenia funkcji](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="122e7-111">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="122e7-112">Można tworzyć za pomocą wyrażenia lambda metody jednego wiersza.</span><span class="sxs-lookup"><span data-stu-id="122e7-112">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="122e7-113">[przy użyciu statycznego](#using-static):</span><span class="sxs-lookup"><span data-stu-id="122e7-113">[using static](#using-static):</span></span>
    - <span data-ttu-id="122e7-114">Wszystkie metody jednej klasy można zaimportować do bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="122e7-114">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="122e7-115">[Null — operatory warunkowe](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="122e7-115">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="122e7-116">Zwięźle i bezpiecznie dostępnych elementów członkowskich obiektu podczas nadal sprawdzania wartości null z operatora warunkowego wartości null.</span><span class="sxs-lookup"><span data-stu-id="122e7-116">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="122e7-117">[Ciąg interpolacji](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="122e7-117">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="122e7-118">Ciąg formatowania wyrażenia za pomocą wbudowanego wyrażeń zamiast argumenty pozycyjne może zapisywać.</span><span class="sxs-lookup"><span data-stu-id="122e7-118">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="122e7-119">[Filtry wyjątków](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="122e7-119">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="122e7-120">Można przechwycić wyrażenia na podstawie właściwości wyjątek lub inny stan programu.</span><span class="sxs-lookup"><span data-stu-id="122e7-120">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="122e7-121">[nameof wyrażenia](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="122e7-121">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="122e7-122">Możesz pozwolić, aby wygenerować reprezentacji ciągu symbole kompilatora.</span><span class="sxs-lookup"><span data-stu-id="122e7-122">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="122e7-123">[await w catch i finally blokuje](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="122e7-123">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="122e7-124">Można użyć `await` wyrażenia w lokalizacjach, które je wcześniej niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="122e7-124">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="122e7-125">[Indeks inicjatory](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="122e7-125">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="122e7-126">Można tworzyć wyrażenia inicjowania asocjacyjnej kontenerów, a także kontenery sekwencji.</span><span class="sxs-lookup"><span data-stu-id="122e7-126">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="122e7-127">[Metody rozszerzenia dla inicjatory kolekcji](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="122e7-127">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="122e7-128">Inicjatory kolekcji można oparte na metodach dostępne rozszerzenia, oprócz metod elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="122e7-128">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="122e7-129">[Rozpoznanie przeciążenia ulepszone](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="122e7-129">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="122e7-130">Niektóre konstrukcje wygenerowanych wcześniej wywołania metody niejednoznaczne teraz rozpoznawane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="122e7-130">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="122e7-131">Ogólny efekt tych funkcji jest który zapisu bardziej zwięzły kod, który jest również bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="122e7-131">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="122e7-132">Składnia zawiera mniej procedury dla wielu typowych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="122e7-132">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="122e7-133">Możliwe jest łatwiejsze Zobacz celem projektu z mniej procedury.</span><span class="sxs-lookup"><span data-stu-id="122e7-133">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="122e7-134">Informacje te funkcje także i będzie bardziej wydajnej pracy, pisania czytelność kodu i bardziej skoncentrować się na Twoje podstawowe funkcje niż w konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="122e7-134">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="122e7-135">W pozostałej części tego tematu zawiera szczegółowe informacje na każdym z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="122e7-135">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="122e7-136">Ulepszenia Auto-właściwością</span><span class="sxs-lookup"><span data-stu-id="122e7-136">Auto-Property enhancements</span></span> 

<span data-ttu-id="122e7-137">Składnia automatycznie implementowanych właściwości (zwykle nazywane "właściwości auto") wprowadzone łatwość tworzenia właściwości, które ma prosty get i set metod dostępu:</span><span class="sxs-lookup"><span data-stu-id="122e7-137">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="122e7-138">Jednak ta składnia proste ograniczony rodzaje projektów, które można obsługiwać przy użyciu właściwości auto.</span><span class="sxs-lookup"><span data-stu-id="122e7-138">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="122e7-139">C# 6 zwiększa możliwości właściwości auto, dzięki czemu można ich używać w scenariuszach więcej.</span><span class="sxs-lookup"><span data-stu-id="122e7-139">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="122e7-140">Nie musisz przełączyć na pełniejsze składnia deklarowanie i operowanie nimi pole zapasowe ręcznie często.</span><span class="sxs-lookup"><span data-stu-id="122e7-140">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="122e7-141">Nowej składni adresów scenariusze dla właściwości tylko do odczytu i Inicjowanie zmiennej magazynu za auto właściwością.</span><span class="sxs-lookup"><span data-stu-id="122e7-141">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="122e7-142">Auto właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="122e7-142">Read-only auto-properties</span></span>

<span data-ttu-id="122e7-143">*Tylko do odczytu właściwości auto* zapewniają bardziej zwięzły składni do tworzenia typów niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="122e7-143">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="122e7-144">Najbardziej Ci można modyfikować typów we wcześniejszych wersjach języka C# to zadeklarować ustawiające prywatnych:</span><span class="sxs-lookup"><span data-stu-id="122e7-144">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="122e7-145">Przy użyciu tej składni, kompilator nie upewnij się, że typ naprawdę nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="122e7-145">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="122e7-146">Wymusza tylko który `FirstName` i `LastName` z kodu poza klasy nie są modyfikowane właściwości.</span><span class="sxs-lookup"><span data-stu-id="122e7-146">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="122e7-147">Tylko do odczytu właściwości automatycznie włączyć true zachowania tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="122e7-147">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="122e7-148">Auto właściwością został zadeklarowany za pomocą dostępu get:</span><span class="sxs-lookup"><span data-stu-id="122e7-148">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="122e7-149">`FirstName` i `LastName` właściwości można ustawić tylko w treści konstruktora:</span><span class="sxs-lookup"><span data-stu-id="122e7-149">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="122e7-150">Ustawiany `LastName` w innej metody generuje `CS0200` błąd kompilacji:</span><span class="sxs-lookup"><span data-stu-id="122e7-150">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

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

<span data-ttu-id="122e7-151">Ta funkcja umożliwia obsługę języka wartość true, tworzenie typów niezmienne i przy użyciu składni auto właściwością zwięzły i bardziej wygodne.</span><span class="sxs-lookup"><span data-stu-id="122e7-151">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="122e7-152">Inicjatory Auto właściwością</span><span class="sxs-lookup"><span data-stu-id="122e7-152">Auto-Property Initializers</span></span>

<span data-ttu-id="122e7-153">*Inicjatory Auto-właściwością* można zadeklarować jako część deklaracji właściwości początkowej wartości dla właściwości auto.</span><span class="sxs-lookup"><span data-stu-id="122e7-153">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="122e7-154">We wcześniejszych wersjach te właściwości musi mieć metody ustawiające i należy użyć tej metody ustawiającej można zainicjować magazynu danych używana przez pole zapasowe.</span><span class="sxs-lookup"><span data-stu-id="122e7-154">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="122e7-155">Należy wziąć pod uwagę tej klasy dla użytkowników domowych, zawierający nazwę i listę klas studenta:</span><span class="sxs-lookup"><span data-stu-id="122e7-155">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="122e7-156">Wraz z rozwojem tej klasy, może zawierać inne konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="122e7-156">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="122e7-157">Każdy Konstruktor musi zainicjować tego pola lub będą powodować błędy.</span><span class="sxs-lookup"><span data-stu-id="122e7-157">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="122e7-158">C# 6 umożliwia przypisanie wartości początkowej dla miejsca używanego przez auto właściwością w deklaracji właściwości automatycznej:</span><span class="sxs-lookup"><span data-stu-id="122e7-158">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="122e7-159">`Grades` Element członkowski został zainicjowany, którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="122e7-159">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="122e7-160">Który ułatwia zainicjować dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="122e7-160">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="122e7-161">Inicjowanie jest częścią deklaracja właściwości, co ułatwia są równoważne Alokacja magazynu z interfejs publiczny dla `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="122e7-161">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="122e7-162">Inicjatory właściwości można użyć właściwości odczytu/zapisu, jak również właściwości tylko do odczytu, jak pokazano tutaj.</span><span class="sxs-lookup"><span data-stu-id="122e7-162">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="122e7-163">Elementy członkowskie zabudowanych wyrażenie — funkcja</span><span class="sxs-lookup"><span data-stu-id="122e7-163">Expression-bodied function members</span></span>

<span data-ttu-id="122e7-164">Treść wiele elementów członkowskich, które możemy zapisać składają się z tylko jedną instrukcję, który może być reprezentowany jako wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-164">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="122e7-165">Można zmniejszyć tego składni pisząc zamiast tego elementu członkowskiego zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-165">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="122e7-166">Działa metody i właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="122e7-166">It works for methods and read-only properties.</span></span> <span data-ttu-id="122e7-167">Na przykład zastępująca `ToString()` często jest doskonałym kandydatem:</span><span class="sxs-lookup"><span data-stu-id="122e7-167">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="122e7-168">Można także użyć zabudowanych wyrażenia elementów członkowskich właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="122e7-168">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="122e7-169">przy użyciu statycznego</span><span class="sxs-lookup"><span data-stu-id="122e7-169">using static</span></span>

<span data-ttu-id="122e7-170">*Przy użyciu statycznego* ulepszenie umożliwia importowanie metod statycznych tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="122e7-170">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="122e7-171">Wcześniej `using` instrukcji zaimportowane wszystkie typy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="122e7-171">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="122e7-172">Często używamy metody statyczne klasy w całym naszego kodu.</span><span class="sxs-lookup"><span data-stu-id="122e7-172">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="122e7-173">Wielokrotnie wpisanie nazwy klasy mogą przesłaniać znaczenie kodu.</span><span class="sxs-lookup"><span data-stu-id="122e7-173">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="122e7-174">Typowym przykładem jest podczas zapisywania klasy, które wielu obliczeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="122e7-174">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="122e7-175">Kod będzie wyściełana <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> i inne wywołania do różnych metod w <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="122e7-175">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="122e7-176">Nowe `using static` składni ułatwia tych klas znacznie czyszczący do odczytu.</span><span class="sxs-lookup"><span data-stu-id="122e7-176">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="122e7-177">Należy określić klasę, którego używasz:</span><span class="sxs-lookup"><span data-stu-id="122e7-177">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="122e7-178">Teraz, można użyć dowolnej metody statycznej w <xref:System.Math> klasy bez kwalifikowanie <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="122e7-178">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="122e7-179"><xref:System.Math> Klasa jest przypadek użycia doskonały dla tej funkcji, ponieważ nie zawiera żadnych metod wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="122e7-179">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="122e7-180">Można również użyć `using static` klasy statycznej metody klasy, która ma obu statyczna importu do metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="122e7-180">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="122e7-181">Jednym z najbardziej przydatne przykłady jest <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="122e7-181">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="122e7-182">Należy użyć nazwy FQDN klasy `System.String` w statycznego za pomocą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="122e7-182">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="122e7-183">Nie można użyć `string` słowa kluczowego zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="122e7-183">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="122e7-184">Można teraz wywołać metody statyczne zdefiniowane w <xref:System.String> klasy bez kwalifikowanie tych metod jako elementy członkowskie tej klasy:</span><span class="sxs-lookup"><span data-stu-id="122e7-184">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="122e7-185">`static using` Funkcji i rozszerzenie metody interakcji w sposób i niektórych reguł, które w szczególności adresu tych interakcji zawarte w projekcie języka.</span><span class="sxs-lookup"><span data-stu-id="122e7-185">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="122e7-186">Celem jest, aby zminimalizować ryzyko wszelkie istotne zmiany w istniejących codebases, tym należy do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="122e7-186">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="122e7-187">Metody rozszerzenia są tylko w zakresie wywołanego przy użyciu składni wywołanie metody rozszerzenia nie wywołanego jako metoda statyczna.</span><span class="sxs-lookup"><span data-stu-id="122e7-187">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="122e7-188">Często pojawi się to w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="122e7-188">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="122e7-189">Można importować wzorzec LINQ, importując <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="122e7-189">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="122e7-190">Zostaną zaimportowane wszystkie metody w <xref:System.Linq.Enumerable> klasy.</span><span class="sxs-lookup"><span data-stu-id="122e7-190">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="122e7-191">Metody rozszerzenia są jednak tylko w zakresie wywołanego jako metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-191">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="122e7-192">Nie są w zakresie, jeśli są one nazywane przy użyciu składni metody statycznej:</span><span class="sxs-lookup"><span data-stu-id="122e7-192">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="122e7-193">Ta decyzja jest ponieważ metody rozszerzenia są zwykle nazywane przy użyciu wyrażenia wywołania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-193">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="122e7-194">W rzadkich przypadkach, gdy są wywoływane przy użyciu metody statycznej wywołania składni jest, aby usunąć niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="122e7-194">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="122e7-195">Wymaganie nazwę klasy w ramach wywołania prawdopodobnie rozsądnego.</span><span class="sxs-lookup"><span data-stu-id="122e7-195">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="122e7-196">Istnieje jedna funkcja ostatniego `static using`.</span><span class="sxs-lookup"><span data-stu-id="122e7-196">There's one last feature of `static using`.</span></span> <span data-ttu-id="122e7-197">`static using` Dyrektywy również importuje wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="122e7-197">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="122e7-198">Który umożliwia wskazanie żadnych zagnieżdżonych typów bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="122e7-198">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="122e7-199">Operatory warunkowe null</span><span class="sxs-lookup"><span data-stu-id="122e7-199">Null-conditional operators</span></span>

<span data-ttu-id="122e7-200">Wartości zerowe skomplikować kodu.</span><span class="sxs-lookup"><span data-stu-id="122e7-200">Null values complicate code.</span></span> <span data-ttu-id="122e7-201">Należy sprawdzić co dostępu do zmiennych, aby upewnić się, nie są usunięcia odwołania `null`.</span><span class="sxs-lookup"><span data-stu-id="122e7-201">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="122e7-202">*Null operator warunkowy* sprawia, że te testy znacznie łatwiejsze i płynnych.</span><span class="sxs-lookup"><span data-stu-id="122e7-202">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="122e7-203">Po prostu zastąpić dostęp do elementu członkowskiego `.` z `?.`:</span><span class="sxs-lookup"><span data-stu-id="122e7-203">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="122e7-204">W powyższym przykładzie zmienna `first` przypisano `null` Jeśli obiekt osoby jest `null`.</span><span class="sxs-lookup"><span data-stu-id="122e7-204">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="122e7-205">W przeciwnym razie zostanie przypisana wartość `FirstName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="122e7-205">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="122e7-206">Przede wszystkim `?.` oznacza, że ten wiersz kodu nie generuje `NullReferenceException` podczas `person` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="122e7-206">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="122e7-207">Zamiast tego short-circuits i tworzy `null`.</span><span class="sxs-lookup"><span data-stu-id="122e7-207">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="122e7-208">Ponadto pamiętać, że wyrażenie zwraca `string`, niezależnie od wartości `person`.</span><span class="sxs-lookup"><span data-stu-id="122e7-208">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="122e7-209">W przypadku krótkich circuiting `null` wartość zwracana jest wpisana do dopasowania pełnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-209">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="122e7-210">Często służą ta konstrukcja z *null łączenie* operator można przypisać wartości domyślne, jeśli jedna z właściwości są `null`:</span><span class="sxs-lookup"><span data-stu-id="122e7-210">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="122e7-211">Argument operacji po stronie prawej z `?.` operator nie jest ograniczona do właściwości lub pól.</span><span class="sxs-lookup"><span data-stu-id="122e7-211">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="122e7-212">Można również użyć do warunkowo wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="122e7-212">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="122e7-213">Najczęściej używane funkcje elementów członkowskich o wartości null operator warunkowy jest można bezpiecznie wywołać delegatów (lub procedury obsługi zdarzeń) może to być `null`.</span><span class="sxs-lookup"><span data-stu-id="122e7-213">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="122e7-214">Można to zrobić przez wywołanie metody delegata `Invoke` przy użyciu metody `?.` operator może uzyskać dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="122e7-214">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="122e7-215">Widać w przykładzie</span><span class="sxs-lookup"><span data-stu-id="122e7-215">You can see an example in the</span></span>  
<span data-ttu-id="122e7-216">[Delegowanie wzorce](../delegates-patterns.md#handling-null-delegates) tematu.</span><span class="sxs-lookup"><span data-stu-id="122e7-216">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="122e7-217">Zasady `?.` operator upewnij się, że po lewej stronie operatora jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="122e7-217">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="122e7-218">Ważne jest i umożliwia wielu idioms, w tym przykładzie przy użyciu programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="122e7-218">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="122e7-219">Zacznijmy od użycia programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="122e7-219">Let's start with the event handler usage.</span></span> <span data-ttu-id="122e7-220">W poprzednich wersjach języka C# zostałby zachęca do pisania kodu, jak to:</span><span class="sxs-lookup"><span data-stu-id="122e7-220">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="122e7-221">To preferowany nad prostsze składni:</span><span class="sxs-lookup"><span data-stu-id="122e7-221">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="122e7-222">Powyższy przykład wprowadza wyścigu.</span><span class="sxs-lookup"><span data-stu-id="122e7-222">The preceding example introduces a race condition.</span></span> <span data-ttu-id="122e7-223">`SomethingHappened` Zdarzenia może mieć subskrybentów po zaznaczeniu tej opcji przed `null`, i tych subskrybentów mógł zostać usunięty przed zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="122e7-223">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="122e7-224">Spowodowałoby <xref:System.NullReferenceException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="122e7-224">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="122e7-225">W tej drugiej wersji `SomethingHappened` obsługi zdarzeń może mieć wartości null podczas testowania, ale jeśli inny kod usuwa obsługi, nadal możliwe wartości null podczas wywoływania obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="122e7-225">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="122e7-226">Kompilator generuje kod dla `?.` operator, który zapewnia po lewej stronie (`this.SomethingHappened`) z `?.` wyrażenie jest obliczane raz, a wynik jest buforowany:</span><span class="sxs-lookup"><span data-stu-id="122e7-226">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="122e7-227">Zapewnienie, że po lewej stronie jest oceniane tylko raz umożliwia również użyć dowolnego wyrażenia, w tym wywołania metody, po lewej stronie `?.` nawet jeśli te efekty uboczne, są one oceniane raz, więc efekty uboczne wystąpić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="122e7-227">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="122e7-228">Można wyświetlić na przykład w naszej zawartości [zdarzenia](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="122e7-228">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="122e7-229">Ciąg interpolacji</span><span class="sxs-lookup"><span data-stu-id="122e7-229">String Interpolation</span></span>

<span data-ttu-id="122e7-230">C# 6 zawiera nowej składni do tworzenia ciągów z ciągu formatu i wyrażeń, które są obliczane, aby utworzyć inne wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="122e7-230">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="122e7-231">Zazwyczaj potrzebne do użycia parametrów pozycyjnych w metodzie, takie jak `string.Format`:</span><span class="sxs-lookup"><span data-stu-id="122e7-231">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="122e7-232">C# 6 nowe [ciągu interpolacji](../language-reference/tokens/interpolated.md) funkcja umożliwia osadzanie wyrażeń w ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="122e7-232">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="122e7-233">Po prostu poprzedzony ciąg z `$`:</span><span class="sxs-lookup"><span data-stu-id="122e7-233">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="122e7-234">W tym przykładzie początkowej użyto wyrażenia właściwości podstawione wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="122e7-234">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="122e7-235">Można rozwinąć w tej składni, aby użyć dowolnego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-235">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="122e7-236">Na przykład można obliczyć Średnia ocen studenta jako część interpolacji:</span><span class="sxs-lookup"><span data-stu-id="122e7-236">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="122e7-237">Uruchomione w poprzednim przykładzie, czy stwierdzisz, że w danych wyjściowych `Grades.Average()` może mieć więcej miejsc dziesiętnych, niż chcesz.</span><span class="sxs-lookup"><span data-stu-id="122e7-237">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="122e7-238">Składnia ciągu interpolacji obsługuje wszystkie w formacie ciągów dostępne przy użyciu metod formatowania wcześniej.</span><span class="sxs-lookup"><span data-stu-id="122e7-238">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="122e7-239">Możesz dodać ciągów formatu w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="122e7-239">You add the format strings inside the braces.</span></span> <span data-ttu-id="122e7-240">Dodaj `:` po wyrażeniu formatowania:</span><span class="sxs-lookup"><span data-stu-id="122e7-240">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="122e7-241">Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.</span><span class="sxs-lookup"><span data-stu-id="122e7-241">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="122e7-242">`:` Zawsze jest interpretowany jako separator wyrażeniu formatowania ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="122e7-242">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="122e7-243">Może to powodować problemy, gdy używa wyrażenia `:` w inny sposób, na przykład operator warunkowy:</span><span class="sxs-lookup"><span data-stu-id="122e7-243">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="122e7-244">W powyższym przykładzie `:` jest analizowana jako początku ciąg formatu nie jest częścią operator warunkowy.</span><span class="sxs-lookup"><span data-stu-id="122e7-244">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="122e7-245">We wszystkich przypadkach, gdy tak się stanie należy ująć wyrażenia w nawiasach, aby wymusić kompilatora, aby zinterpretować wyrażenia, jak zamierzasz:</span><span class="sxs-lookup"><span data-stu-id="122e7-245">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="122e7-246">Nie ma ograniczenia wyrażeń, które można umieścić w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="122e7-246">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="122e7-247">Można wykonywać złożonych zapytań LINQ w ciągu interpolowanym można przeprowadzić obliczenia i wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="122e7-247">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="122e7-248">W tym przykładzie widać, czy można zagnieżdżać interpolacji wyrażeniem wewnątrz innego interpolacji wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="122e7-248">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="122e7-249">W tym przykładzie jest bardzo prawdopodobne, bardziej złożone niż byłaby wskazana w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="122e7-249">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="122e7-250">Zamiast jest opisowy szerokości funkcji.</span><span class="sxs-lookup"><span data-stu-id="122e7-250">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="122e7-251">Dowolne wyrażenie C# można umieścić między nawiasami klamrowymi ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="122e7-251">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="122e7-252">Ciąg interpolacji i określone kultury</span><span class="sxs-lookup"><span data-stu-id="122e7-252">String interpolation and specific cultures</span></span>

<span data-ttu-id="122e7-253">Wszystkie przykłady w poprzedniej sekcji formatu ciągi, przy użyciu bieżącej kultury i języka na komputerze gdzie kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="122e7-253">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="122e7-254">Często konieczne może być ciąg utworzony, używając określonej kultury formatu.</span><span class="sxs-lookup"><span data-stu-id="122e7-254">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="122e7-255">Robić, które używają fakt, że obiekt utworzony przez interpolacji ciągu można niejawnie przekonwertować <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="122e7-255">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="122e7-256"><xref:System.FormattableString> Wystąpienie zawiera ciąg formatu oraz wynikiem obliczenia wyrażenia przed ich konwertowanie na ciągi.</span><span class="sxs-lookup"><span data-stu-id="122e7-256">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="122e7-257">Można użyć metod publicznych klasy <xref:System.FormattableString> do określenia kultury podczas formatowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="122e7-257">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="122e7-258">Na przykład poniższy przykład tworzy ciąg przy użyciu kultury niemieckim.</span><span class="sxs-lookup"><span data-stu-id="122e7-258">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="122e7-259">(Separator dziesiętny używa znaku ',' i '.' znak jako separatora.)</span><span class="sxs-lookup"><span data-stu-id="122e7-259">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="122e7-260">Aby uzyskać więcej informacji, zobacz [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="122e7-260">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="122e7-261">Filtry wyjątków</span><span class="sxs-lookup"><span data-stu-id="122e7-261">Exception Filters</span></span>

<span data-ttu-id="122e7-262">Kolejną nową funkcją w C# 6 jest *filtry wyjątków*.</span><span class="sxs-lookup"><span data-stu-id="122e7-262">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="122e7-263">Filtry wyjątków są klauzule określające stosowania klauzuli catch danego.</span><span class="sxs-lookup"><span data-stu-id="122e7-263">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="122e7-264">Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, w klauzuli catch wykonuje jego normalnego przetwarzania z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="122e7-264">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="122e7-265">Jeśli wyrażenie ma `false`, a następnie `catch` klauzuli zostanie pominięta.</span><span class="sxs-lookup"><span data-stu-id="122e7-265">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="122e7-266">Zapoznaj się z informacjami o wyjątku, aby ustalić, czy jest jedno użycie `catch` klauzuli może przetwarzać wyjątek:</span><span class="sxs-lookup"><span data-stu-id="122e7-266">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="122e7-267">Kod wygenerowany przez filtry wyjątków zapewnia lepsze informacje o wyjątek zgłoszony i nie jest przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="122e7-267">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="122e7-268">Przed dodaniem filtry wyjątków dla języka, należy utworzyć kod podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="122e7-268">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="122e7-269">Punkt, w którym wyjątku zmiany między te dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="122e7-269">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="122e7-270">W poprzednim kodzie, gdzie `throw` jest używana klauzula, analiza śledzenia stosu ani badania zrzuty awaryjne wyświetli, czy wyjątek został zgłoszony z `throw` instrukcji w klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="122e7-270">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="122e7-271">Obiekt wyjątku rzeczywiste będzie zawierać oryginalnego stos wywołań, ale wszystkie inne informacje o zmiennych w stosie wywołań między tym punkcie throw i lokalizację punktu początkowego throw zostało utracone.</span><span class="sxs-lookup"><span data-stu-id="122e7-271">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="122e7-272">Natomiast który o przetwarzaniu kod przy użyciu filtru wyjątków: daje w wyniku wyrażenia filtru wyjątków `false`.</span><span class="sxs-lookup"><span data-stu-id="122e7-272">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="122e7-273">W związku z tym wykonywania nigdy nie przechodzi `catch` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="122e7-273">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="122e7-274">Ponieważ `catch` klauzuli nie wykonuj, odwijanie stosu nie ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="122e7-274">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="122e7-275">Czy oznacza, że oryginalne throw lokalizacji są zachowywane na potrzeby debugowania działań, które nastąpi później.</span><span class="sxs-lookup"><span data-stu-id="122e7-275">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="122e7-276">Zawsze, gdy należy ocenić pola lub właściwości wyjątek, zdejmując to zadanie wyłącznie typ wyjątku, użyj filtru wyjątków, aby zachować więcej informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="122e7-276">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="122e7-277">Inny, zalecane wzorca zawierającego filtry wyjątków jest używane do rejestrowania procedury.</span><span class="sxs-lookup"><span data-stu-id="122e7-277">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="122e7-278">To użycie korzysta również sposób, w której punkt Zgłoś wyjątek jest zachowywane podczas daje w wyniku filtra wyjątku `false`.</span><span class="sxs-lookup"><span data-stu-id="122e7-278">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="122e7-279">Metoda rejestrowania będą metody, którego argument jest wyjątek, który bezwarunkowo zwraca `false`:</span><span class="sxs-lookup"><span data-stu-id="122e7-279">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="122e7-280">Zawsze, gdy chcesz rejestrować wyjątek, możesz dodać klauzuli catch i tej metody można użyć jako filtru wyjątków:</span><span class="sxs-lookup"><span data-stu-id="122e7-280">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="122e7-281">Wyjątki są przechwytywane nigdy, ponieważ `LogException` metoda zawsze zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="122e7-281">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="122e7-282">Tego filtru wyjątków zawsze wartość FAŁSZ oznacza, że umieszczenie tej obsługi rejestrowania przed wszystkie inne programy obsługi wyjątków:</span><span class="sxs-lookup"><span data-stu-id="122e7-282">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="122e7-283">Powyższy przykład prezentuje ważne aspektu filtrów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="122e7-283">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="122e7-284">Filtry wyjątków umożliwić scenariuszy, w których bardziej ogólne klauzuli catch wyjątku może pojawić się przed co bardziej szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="122e7-284">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="122e7-285">Istnieje również możliwość mają ten sam typ wyjątku, są wyświetlane w wielu klauzule catch:</span><span class="sxs-lookup"><span data-stu-id="122e7-285">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="122e7-286">Inny wzorzec zalecane zapobiega klauzule catch przetwarzania wyjątki, gdy jest dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="122e7-286">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="122e7-287">Ta technika pozwala na uruchamianie aplikacji z debugera i zatrzymuje wykonywanie, gdy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="122e7-287">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="122e7-288">W kodzie należy dodać filtra wyjątku, aby każdy kod odzyskiwania wykonuje tylko wtedy, gdy nie jest dołączony debuger:</span><span class="sxs-lookup"><span data-stu-id="122e7-288">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="122e7-289">Po dodaniu to w kodzie, należy ustawić debuger można przerwać w przypadku wszystkich nieobsługiwanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="122e7-289">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="122e7-290">Uruchom program w debugerze i debuger dzieli się po każdej zmianie `PerformFailingOperation()` zgłasza `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="122e7-290">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="122e7-291">Debuger dzieli programu, ponieważ w klauzuli catch nie będzie można wykonać z powodu filtru wyjątków zwracającego wartość false.</span><span class="sxs-lookup"><span data-stu-id="122e7-291">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="122e7-292">`nameof` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="122e7-292">`nameof` Expressions</span></span>

<span data-ttu-id="122e7-293">`nameof` Wyrażenie ma nazwę symbolu.</span><span class="sxs-lookup"><span data-stu-id="122e7-293">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="122e7-294">Jest to dobry sposób na Pobierz narzędzia Praca zawsze, gdy potrzebna jest nazwa zmienną, właściwością lub polem członka.</span><span class="sxs-lookup"><span data-stu-id="122e7-294">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="122e7-295">Jedną z najbardziej typowych używa `nameof` jest zapewnienie nazwa symbolu, który spowodował wyjątek:</span><span class="sxs-lookup"><span data-stu-id="122e7-295">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="122e7-296">Użyj innego jest z aplikacjami na podstawie języka XAML, które implementuje `INotifyPropertyChanged` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="122e7-296">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="122e7-297">Zaletą używania `nameof` operator przez ciąg stałej jest dokładnie symbolu, narzędzia.</span><span class="sxs-lookup"><span data-stu-id="122e7-297">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="122e7-298">Jeśli używasz narzędzia do refaktoryzacji Aby zmienić nazwę symbolu, go spowoduje zmianę nazwy w `nameof` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-298">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="122e7-299">Ciągi o stałej nie ma tego korzyści.</span><span class="sxs-lookup"><span data-stu-id="122e7-299">Constant strings don't have that advantage.</span></span> <span data-ttu-id="122e7-300">Wypróbuj ją samodzielnie w edytorze Ulubione: Zmień nazwę zmiennej, a także wszystkie `nameof` również zaktualizuje wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-300">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="122e7-301">`nameof` Wyrażenie zwraca niekwalifikowana nazwa argumentu (`LastName` w poprzednich przykładach) nawet wtedy, gdy używasz w pełni kwalifikowana nazwa argumentu:</span><span class="sxs-lookup"><span data-stu-id="122e7-301">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="122e7-302">To `nameof` wyrażenie daje `FirstName`, a nie `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="122e7-302">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="122e7-303">Await w Catch i Finally blokuje</span><span class="sxs-lookup"><span data-stu-id="122e7-303">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="122e7-304">C# 5 ma kilka ograniczeń wokół lokalizację można `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-304">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="122e7-305">Jednym z tych została usunięta w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="122e7-305">One of those has been removed in C# 6.</span></span> <span data-ttu-id="122e7-306">Można teraz używać `await` w `catch` lub `finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="122e7-306">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="122e7-307">Dodanie await wyrażenia w catch i finally bloki może wydawać się skomplikować, jak te są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="122e7-307">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="122e7-308">Dodajmy przykład omówimy sposobu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="122e7-308">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="122e7-309">W dowolnej metody asynchronicznej, można użyć wyrażenia await w klauzuli finally.</span><span class="sxs-lookup"><span data-stu-id="122e7-309">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="122e7-310">C# 6 można również zdefiniować oczekiwania w wyrażeniach catch.</span><span class="sxs-lookup"><span data-stu-id="122e7-310">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="122e7-311">To jest najczęściej używana w scenariuszach rejestrowania:</span><span class="sxs-lookup"><span data-stu-id="122e7-311">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="122e7-312">Szczegóły implementacji dodawania `await` obsługuje wewnątrz `catch` i `finally` klauzule zapewnia, że zachowanie jest zgodne z zachowaniem synchroniczne kodu.</span><span class="sxs-lookup"><span data-stu-id="122e7-312">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="122e7-313">Jeśli kod wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego.</span><span class="sxs-lookup"><span data-stu-id="122e7-313">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="122e7-314">Wystąpił wyjątek bieżący, ten wyjątek zostanie utracone.</span><span class="sxs-lookup"><span data-stu-id="122e7-314">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="122e7-315">W tym celu z Oczekiwano wyrażenia w `catch` i `finally` klauzule: odpowiedniej `catch` jest wyszukiwany i bieżący wyjątek, jeśli istnieje, zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="122e7-315">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="122e7-316">To zachowanie jest powód, zaleca się zapisu `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="122e7-316">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="122e7-317">Inicjatory indeksu</span><span class="sxs-lookup"><span data-stu-id="122e7-317">Index Initializers</span></span>

<span data-ttu-id="122e7-318">*Inicjatory indeksu* jest jednym z dwóch funkcje inicjatory kolekcji bardziej spójny.</span><span class="sxs-lookup"><span data-stu-id="122e7-318">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="122e7-319">We wcześniejszych wersjach języka C#, można użyć *inicjatory kolekcji* tylko z kolekcjami styl sekwencji:</span><span class="sxs-lookup"><span data-stu-id="122e7-319">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="122e7-320">Teraz, można również używać ich z <xref:System.Collections.Generic.Dictionary%602> kolekcje i podobnych typów:</span><span class="sxs-lookup"><span data-stu-id="122e7-320">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="122e7-321">Ta funkcja oznacza, że asocjacyjnej kontenery mogą być inicjowane przy użyciu składni podobnej do została co w przypadku sekwencji kontenery różne wersje.</span><span class="sxs-lookup"><span data-stu-id="122e7-321">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

### <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="122e7-322">Rozszerzenie `Add` metod w inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="122e7-322">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="122e7-323">Inny funkcja, która ułatwia inicjowania kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="122e7-323">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="122e7-324">Ta funkcja została dodana do parzystości za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="122e7-324">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="122e7-325">Funkcja jest najbardziej przydatna w przypadku klasy niestandardowej kolekcji, która ma metodę o innej nazwie do semantycznie dodawania nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="122e7-325">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="122e7-326">Rozważmy na przykład kolekcja studentów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="122e7-326">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="122e7-327">`Enroll` Metoda dodaje studenta.</span><span class="sxs-lookup"><span data-stu-id="122e7-327">The `Enroll` method adds a student.</span></span> <span data-ttu-id="122e7-328">Ale nie będzie zgodna z `Add` wzorca.</span><span class="sxs-lookup"><span data-stu-id="122e7-328">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="122e7-329">W poprzednich wersjach języka C#, nie można użyć inicjatory kolekcji z `Enrollment` obiektu:</span><span class="sxs-lookup"><span data-stu-id="122e7-329">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="122e7-330">Teraz możesz, ale tylko wtedy, gdy tworzenie metodę rozszerzenia, która mapuje `Add` do `Enroll`:</span><span class="sxs-lookup"><span data-stu-id="122e7-330">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="122e7-331">Czynności przy użyciu tej funkcji ma mapowania dowolnej metody dodaje elementy kolekcji do metody o nazwie `Add` tworząc metody rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="122e7-331">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method:</span></span> 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a><span data-ttu-id="122e7-332">Rozpoznanie przeciążenia ulepszone</span><span class="sxs-lookup"><span data-stu-id="122e7-332">Improved overload resolution</span></span>

<span data-ttu-id="122e7-333">Ta funkcja ostatniego jest jeden, który prawdopodobnie nie będzie zauważyć.</span><span class="sxs-lookup"><span data-stu-id="122e7-333">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="122e7-334">Znaleziono konstrukcje poprzedniej wersji kompilatora C# mogą mieć wykryto niektóre wywołania metody obejmujące wyrażenia lambda jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="122e7-334">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="122e7-335">Tej metody należy wziąć pod uwagę:</span><span class="sxs-lookup"><span data-stu-id="122e7-335">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="122e7-336">We wcześniejszych wersjach języka C# wywołanie tej metody, przy użyciu składni grupy — metoda nie powiedzie się:</span><span class="sxs-lookup"><span data-stu-id="122e7-336">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="122e7-337">Wcześniej kompilatora nie można prawidłowo między rozróżnienia `Task.Run(Action)` i `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="122e7-337">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="122e7-338">W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="122e7-338">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="122e7-339">Kompilator języka C# 6 poprawnie określi, że `Task.Run(Func<Task>())` jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="122e7-339">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
