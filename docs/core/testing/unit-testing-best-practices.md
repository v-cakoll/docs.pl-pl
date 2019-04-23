---
title: Najlepsze rozwiązania dotyczące pisania testów jednostkowych
description: Poznaj najlepsze rozwiązania dotyczące pisania testów jednostkowych, które Dbaj o jakość kodu i odporności dla projektów .NET Core i .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 7f4699b5277c5feeac4d9116ac85e096247aa748
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427451"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="51380-103">Najlepsze rozwiązania przy użyciu platformy .NET Core i .NET Standard testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="51380-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="51380-104">Istnieje wiele korzyści, do pisania testów jednostkowych; pomagają przy użyciu regresji, zapewniają dostęp do dokumentacji i ułatwienia dobrego projektowania.</span><span class="sxs-lookup"><span data-stu-id="51380-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="51380-105">Jednak testy jednostkowe trudne do odczytu i kruchy można spustoszyć bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="51380-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="51380-106">W tym artykule opisano najlepsze rozwiązania dotyczące projektowania testów jednostkowych dla projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="51380-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="51380-107">W tym przewodniku dowiesz się najważniejsze wskazówki podczas pisania testów jednostkowych, aby zachować testów, odporne i łatwe do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="51380-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="51380-108">Przez [John Reese](https://reese.dev) ze specjalnymi dzięki [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="51380-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="51380-109">Dlaczego test jednostkowy?</span><span class="sxs-lookup"><span data-stu-id="51380-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="51380-110">Mniej czasu na wykonywanie testów funkcjonalnych</span><span class="sxs-lookup"><span data-stu-id="51380-110">Less time performing functional tests</span></span>
<span data-ttu-id="51380-111">Testy funkcjonalne są kosztowne.</span><span class="sxs-lookup"><span data-stu-id="51380-111">Functional tests are expensive.</span></span> <span data-ttu-id="51380-112">Są na ogół podczas otwierania aplikacji, a następnie wykonanie serii czynności, które użytkownik (lub kogoś innego), należy wykonać, aby można było zweryfikować oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="51380-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="51380-113">Te kroki nie zawsze być znane do testera, co oznacza, że konieczne będzie skontaktowanie się z ktoś większą wiedzę w obszarze w celu przeprowadzenia badania.</span><span class="sxs-lookup"><span data-stu-id="51380-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="51380-114">Testowanie sam może potrwać sekund proste zmiany lub minut w celu większe zmiany.</span><span class="sxs-lookup"><span data-stu-id="51380-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="51380-115">Ponadto ten proces należy powtórzyć dla każdej zmiany wprowadzone w systemie.</span><span class="sxs-lookup"><span data-stu-id="51380-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="51380-116">Testy jednostkowe, z drugiej strony ręcznie, zająć milisekund, mogą być uruchamiane naciśnięciem przycisku i nie muszą mieć żadnej wiedzy w dużych systemu.</span><span class="sxs-lookup"><span data-stu-id="51380-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="51380-117">Określa, czy test kończy się pomyślnie lub nie powiedzie się, zależy od narzędzia test runner nie osoby.</span><span class="sxs-lookup"><span data-stu-id="51380-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="51380-118">Ochrona przed regresji</span><span class="sxs-lookup"><span data-stu-id="51380-118">Protection against regression</span></span>
<span data-ttu-id="51380-119">Regresja wady są wady, które są wprowadzone podczas wprowadzania zmian do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51380-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="51380-120">Powszechne jest wprowadzanie dla testerów, nie tylko testowania ich nowych funkcji, ale także funkcje, które istniało wcześniej w celu sprawdzenia, które było wcześniej zaimplementowane funkcje nadal działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="51380-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="51380-121">Za pomocą testów jednostkowych jest możliwe ponowne uruchamianie usługi cały zestaw testów po każdej kompilacji, lub nawet w przypadku, po zmianie wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="51380-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="51380-122">Co daje pewność, że nowy kod nie mogą przerwać działania istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="51380-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="51380-123">Dokumentacja pliku wykonywalnego</span><span class="sxs-lookup"><span data-stu-id="51380-123">Executable documentation</span></span>
<span data-ttu-id="51380-124">Go może nie zawsze jest oczywiste działanie konkretną metodę lub jego zachowania podany niektórych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="51380-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="51380-125">Może zadać sobie: Jak zachowują się ta metoda jeśli mogę przekazać pusty ciąg?</span><span class="sxs-lookup"><span data-stu-id="51380-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="51380-126">Wartość null?</span><span class="sxs-lookup"><span data-stu-id="51380-126">Null?</span></span>

<span data-ttu-id="51380-127">W przypadku zestawu testów jednostkowych dobrze nazwane każdy test powinien móc wyjaśniają oczekiwanych danych wyjściowych dla danego składnika.</span><span class="sxs-lookup"><span data-stu-id="51380-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="51380-128">Ponadto powinno być możliwe sprawdzić, czy rzeczywiście działa.</span><span class="sxs-lookup"><span data-stu-id="51380-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="51380-129">Mniej sprzężonych kodu</span><span class="sxs-lookup"><span data-stu-id="51380-129">Less coupled code</span></span>
<span data-ttu-id="51380-130">Gdy kod jest ściśle powiązane, może być trudne do testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="51380-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="51380-131">Bez tworzenia testów jednostkowych dla kodu, który właśnie piszesz, sprzężenia mogą być mniej jasne.</span><span class="sxs-lookup"><span data-stu-id="51380-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="51380-132">Pisanie testów dla kodu naturalnie będzie rozdzielenie kodu, ponieważ może być trudniejsze do testowania, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="51380-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="51380-133">Charakterystyki testu jednostkowego dobre</span><span class="sxs-lookup"><span data-stu-id="51380-133">Characteristics of a good unit test</span></span>
- <span data-ttu-id="51380-134">**Szybkie**.</span><span class="sxs-lookup"><span data-stu-id="51380-134">**Fast**.</span></span> <span data-ttu-id="51380-135">Nie jest niczym niezwykłym dojrzała projektów, które mają kilka tysięcy testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="51380-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="51380-136">Testy jednostkowe powinno zająć bardzo mało czasu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="51380-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="51380-137">Liczba milisekund.</span><span class="sxs-lookup"><span data-stu-id="51380-137">Milliseconds.</span></span>
- <span data-ttu-id="51380-138">**Izolowane**.</span><span class="sxs-lookup"><span data-stu-id="51380-138">**Isolated**.</span></span> <span data-ttu-id="51380-139">Testy jednostkowe są autonomiczne, mogą być uruchamiane w izolacji i mieć żadnych zależności na wszelkich zewnętrznych czynników, takich jak system plików lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="51380-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="51380-140">**Powtarzalne**.</span><span class="sxs-lookup"><span data-stu-id="51380-140">**Repeatable**.</span></span> <span data-ttu-id="51380-141">Uruchamianie testów jednostkowych powinny być zgodne z jego wyniki, oznacza to, zawsze zwraca ten sam wynik, jeśli nie należy zmieniać niczego Between przebiegów.</span><span class="sxs-lookup"><span data-stu-id="51380-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="51380-142">**Sprawdzanie własnym**.</span><span class="sxs-lookup"><span data-stu-id="51380-142">**Self-Checking**.</span></span> <span data-ttu-id="51380-143">Test powinien móc automatycznie wykryć, czy przekazywany ani nie powiodła się bez interwencji człowieka.</span><span class="sxs-lookup"><span data-stu-id="51380-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="51380-144">**Czas**.</span><span class="sxs-lookup"><span data-stu-id="51380-144">**Timely**.</span></span> <span data-ttu-id="51380-145">Test jednostkowy nie powinna przyjmować zapisu w porównaniu do testowany kod jest nieproporcjonalnie dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="51380-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="51380-146">Jeśli okaże się, testowanie kodu, biorąc dużą ilość czasu w porównaniu do pisania kodu, należy wziąć pod uwagę projekt, który jest bardziej sprawdzalnego działa zgodnie.</span><span class="sxs-lookup"><span data-stu-id="51380-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="51380-147">Teraz używać tego samego języka</span><span class="sxs-lookup"><span data-stu-id="51380-147">Let's speak the same language</span></span>
<span data-ttu-id="51380-148">Termin *testowanie* jest Niestety bardzo użyte w przypadku testowania.</span><span class="sxs-lookup"><span data-stu-id="51380-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="51380-149">Następujące definiuje najbardziej powszechne typy *elementów sztucznych* podczas pisania testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="51380-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="51380-150">*Sztuczne* -sfałszowana to ogólny termin określający, który może służyć do opisu odcinek lub makiety obiektu.</span><span class="sxs-lookup"><span data-stu-id="51380-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="51380-151">Czy jest on odcinek czy pozorny zależy od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="51380-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="51380-152">Dlatego oznacza to, sfałszowana można odcinek lub pozorny.</span><span class="sxs-lookup"><span data-stu-id="51380-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="51380-153">*Testowanie* -makiety obiektu jest obiektem sztuczne w systemie, który decyduje, czy test jednostkowy został zakończony powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="51380-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="51380-154">Pozorny rozpoczyna się jako sfałszowana do momentu jej przeciwko.</span><span class="sxs-lookup"><span data-stu-id="51380-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="51380-155">*Klasy zastępczej* — odcinek jest musi zastąpić istniejące zależności (lub współpracownika) w systemie.</span><span class="sxs-lookup"><span data-stu-id="51380-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="51380-156">Za pomocą odcinek, można testować kod bez konieczności wnikania zależnością bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="51380-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="51380-157">Domyślnie sfałszowana rozpoczyna się jako wejściowy.</span><span class="sxs-lookup"><span data-stu-id="51380-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="51380-158">Rozważmy następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="51380-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="51380-159">Jest to przykład wycinka są określane jako pozorny.</span><span class="sxs-lookup"><span data-stu-id="51380-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="51380-160">W tym przypadku jest to wycinka.</span><span class="sxs-lookup"><span data-stu-id="51380-160">In this case, it is a stub.</span></span> <span data-ttu-id="51380-161">Po prostu przechodząc w kolejności, co oznacza, że aby można było utworzyć wystąpienia `Purchase` (system w trakcie testu).</span><span class="sxs-lookup"><span data-stu-id="51380-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="51380-162">Nazwa `MockOrder` jest również bardzo mylące, ponieważ ponownie, kolejność nie jest pozorny.</span><span class="sxs-lookup"><span data-stu-id="51380-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="51380-163">Lepszym rozwiązaniem byłoby</span><span class="sxs-lookup"><span data-stu-id="51380-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="51380-164">Zmieniając nazwę klasy, która ma `FakeOrder`, wprowadzono klasy o wiele bardziej ogólnym, klasa może służyć jako pozorny ani klas zastępczych.</span><span class="sxs-lookup"><span data-stu-id="51380-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="51380-165">Obowiązuje lepszym miejscem dla przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="51380-165">Whichever is better for the test case.</span></span> <span data-ttu-id="51380-166">W powyższym przykładzie `FakeOrder` służy jako wejściowy.</span><span class="sxs-lookup"><span data-stu-id="51380-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="51380-167">Nie używasz `FakeOrder` w dowolnej formie podczas assert.</span><span class="sxs-lookup"><span data-stu-id="51380-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="51380-168">`FakeOrder` po prostu została przekazana do `Purchase` klasy w celu spełnienia wymagań konstruktora.</span><span class="sxs-lookup"><span data-stu-id="51380-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="51380-169">Aby użyć go jako pozorny, możesz to zrobić coś takiego</span><span class="sxs-lookup"><span data-stu-id="51380-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="51380-170">W takim przypadku podczas sprawdzania właściwość sfałszowana (potwierdzające przed nim), więc w powyższym fragmencie kodu `mockOrder` jest pozorny.</span><span class="sxs-lookup"><span data-stu-id="51380-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51380-171">Należy uzyskać prawidłowy terminologię.</span><span class="sxs-lookup"><span data-stu-id="51380-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="51380-172">Wywołanie usługi wycinków "mocks" inni deweloperzy mają wartość false zakładają zgodne z zamiarami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51380-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="51380-173">Główny jest, aby pamiętać mocks i wycinków jest mocks przypominają wycinków, że asercja względem makiety obiektu, natomiast nie wystąpiło zapewnienie względem wycinka.</span><span class="sxs-lookup"><span data-stu-id="51380-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="51380-174">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="51380-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="51380-175">Nadawanie nazw testów</span><span class="sxs-lookup"><span data-stu-id="51380-175">Naming your tests</span></span>
<span data-ttu-id="51380-176">Nazwa testu powinien składać się z trzech części:</span><span class="sxs-lookup"><span data-stu-id="51380-176">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="51380-177">Nazwa metody poddawana testom.</span><span class="sxs-lookup"><span data-stu-id="51380-177">The name of the method being tested.</span></span>
- <span data-ttu-id="51380-178">Scenariusz, w którym jest testowana.</span><span class="sxs-lookup"><span data-stu-id="51380-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="51380-179">Oczekiwane zachowanie po wywołaniu tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="51380-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-180">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-180">Why?</span></span>
- <span data-ttu-id="51380-181">Standardy nazewnictwa są ważne, ponieważ one jawnie express celem testu.</span><span class="sxs-lookup"><span data-stu-id="51380-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="51380-182">Testy są więcej niż tylko upewniając się, Twój kod działa, ale oferują też dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="51380-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="51380-183">Po prostu patrząc pakietów testów jednostkowych, można rozpoznać zachowania kodu bez nawet spojrzenie na sam kod.</span><span class="sxs-lookup"><span data-stu-id="51380-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="51380-184">Ponadto gdy testy nie powiodą się, możesz zobaczyć dokładnie scenariuszy, do których nie spełniają Twoich oczekiwań.</span><span class="sxs-lookup"><span data-stu-id="51380-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-185">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="51380-186">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="51380-187">Rozmieszczanie testów</span><span class="sxs-lookup"><span data-stu-id="51380-187">Arranging your tests</span></span>
<span data-ttu-id="51380-188">**Rozmieść, działania, Asercja** pojawia się często wzorca, gdy testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="51380-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="51380-189">Jak wskazuje nazwa, składa się z trzech głównych czynności:</span><span class="sxs-lookup"><span data-stu-id="51380-189">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="51380-190">*Rozmieść* obiektów, tworzenia i konfigurowania zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="51380-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="51380-191">*ACT* na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="51380-191">*Act* on an object.</span></span>
- <span data-ttu-id="51380-192">*Asercja* , coś, co jest zgodne z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="51380-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-193">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-193">Why?</span></span>
- <span data-ttu-id="51380-194">Wyraźnie oddziela jest poddawana testom z *Rozmieść* i *asercja* kroki.</span><span class="sxs-lookup"><span data-stu-id="51380-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="51380-195">Mniej szansę intermix potwierdzenia z kodem "Act".</span><span class="sxs-lookup"><span data-stu-id="51380-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="51380-196">Czytelność jest jednym z najważniejszych aspektów, podczas zapisywania testu.</span><span class="sxs-lookup"><span data-stu-id="51380-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="51380-197">Oddzielając każdy z tych akcji w ramach testu wyraźnie wyróżnić zależności wymagane do wywołania w kodzie, jak kod jest wywoływana i próbujesz potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="51380-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="51380-198">Może być możliwe, aby połączyć kilka kroków i zmniejszyć rozmiar testu, podstawowym celem jest zapewnienie testu jako do odczytu, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="51380-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-199">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="51380-200">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="51380-201">Pisanie minimalny zestaw testów przekazywanie</span><span class="sxs-lookup"><span data-stu-id="51380-201">Write minimally passing tests</span></span>
<span data-ttu-id="51380-202">Dane wejściowe do użycia w test jednostkowy powinna być najprostsza możliwa, aby sprawdzić zachowanie, które obecnie testujesz.</span><span class="sxs-lookup"><span data-stu-id="51380-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-203">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-203">Why?</span></span>
- <span data-ttu-id="51380-204">Testy stają się bardziej odporne na przyszłe zmiany w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="51380-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="51380-205">Im bliżej testowania implementacji zachowania.</span><span class="sxs-lookup"><span data-stu-id="51380-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="51380-206">Testy, które zawierają więcej informacji, niż jest to wymagane do przekazania testu wyższe prawdopodobieństwo wprowadzenie błędów do testu i może być celem mniej wyczyść test.</span><span class="sxs-lookup"><span data-stu-id="51380-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="51380-207">Podczas pisania testów chcesz skupić się na zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="51380-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="51380-208">Ustawianie właściwości dodatkowych modeli lub przy użyciu wartości różna od zera, gdy nie jest wymagany, źle wpływa tylko na próbujesz potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="51380-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-209">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="51380-210">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="51380-211">Należy unikać magic ciągów</span><span class="sxs-lookup"><span data-stu-id="51380-211">Avoid magic strings</span></span>
<span data-ttu-id="51380-212">Nazwy zmiennych w jednostce testów to jako ważne, jeśli nie ważniejsza, nazw zmiennych w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="51380-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="51380-213">Testy jednostkowe nie powinna zawierać ciągi magic.</span><span class="sxs-lookup"><span data-stu-id="51380-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-214">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-214">Why?</span></span>
- <span data-ttu-id="51380-215">Eliminuje konieczność Sprawdzanie kodu produkcyjnego, aby ustalić, co sprawia, że wartość specjalne dla czytnika testu.</span><span class="sxs-lookup"><span data-stu-id="51380-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="51380-216">Wyraźnie pokazuje, co ma być realizowany *udowodnić, że* zamiast próbowania *osiągnąć*.</span><span class="sxs-lookup"><span data-stu-id="51380-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="51380-217">Ciągi Magic może nie być jasne do czytnika testów.</span><span class="sxs-lookup"><span data-stu-id="51380-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="51380-218">Jeśli ciąg wygląda niezwykłe, mogą dowiedzieć się, dlaczego określoną wartość został wybrany dla parametru lub zwróć wartość.</span><span class="sxs-lookup"><span data-stu-id="51380-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="51380-219">Może to prowadzić do Przyjrzyj się bliżej szczegóły implementacji, a nie skoncentrować się na testowej.</span><span class="sxs-lookup"><span data-stu-id="51380-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="51380-220">Podczas pisania testów, należy dążyć do express tyle przeznaczenie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="51380-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="51380-221">W przypadku ciągów magic dobra metoda jest można przypisać te wartości na stałe.</span><span class="sxs-lookup"><span data-stu-id="51380-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-222">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="51380-223">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="51380-224">Należy unikać logiki w testach</span><span class="sxs-lookup"><span data-stu-id="51380-224">Avoid logic in tests</span></span>
<span data-ttu-id="51380-225">Podczas zapisywania jednostkowe, testy Unikaj łączenia ciągów ręczne i logiczne warunków, takich jak `if`, `while`, `for`, `switch`itp.</span><span class="sxs-lookup"><span data-stu-id="51380-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-226">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-226">Why?</span></span>
- <span data-ttu-id="51380-227">Mniej masz szansę, aby wprowadzić usterkę w testach.</span><span class="sxs-lookup"><span data-stu-id="51380-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="51380-228">Skup się na wynik końcowy, a nie szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="51380-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="51380-229">Po wprowadzeniu logiki w pakiecie testowym znacznie zwiększa ryzyko wprowadzenia usterkę do niego.</span><span class="sxs-lookup"><span data-stu-id="51380-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="51380-230">Ostatnie miejsce, które chcesz znaleźć usterkę znajduje się w pakiecie testowym.</span><span class="sxs-lookup"><span data-stu-id="51380-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="51380-231">Powinny mieć pewność, że testy pracy wysokiego poziomu, w przeciwnym razie zostanie ufasz je.</span><span class="sxs-lookup"><span data-stu-id="51380-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="51380-232">Testy, które nie ufasz, nie oferuje żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="51380-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="51380-233">Gdy test zakończy się niepowodzeniem, chcesz mieć sens, czy jest coś, co faktycznie problem z kodem i że nie może być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="51380-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="51380-234">Jeśli logika w teście nieuniknione, należy rozważyć rozdzielenie test na co najmniej dwóch różnych badań.</span><span class="sxs-lookup"><span data-stu-id="51380-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-235">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="51380-236">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="51380-237">Preferuj metody pomocnika do instalacji i usuwania</span><span class="sxs-lookup"><span data-stu-id="51380-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="51380-238">Podobne obiektu lub stanu są wymagane dla testów, najpierw metody pomocnika niż korzystanie z atrybutów instalacji i usuwania, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="51380-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-239">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-239">Why?</span></span>
- <span data-ttu-id="51380-240">Mniej błąd podczas odczytywania testów, ponieważ cały kod nie jest widoczny w ramach każdego testu.</span><span class="sxs-lookup"><span data-stu-id="51380-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="51380-241">Mniejsze ryzyko Definiowanie zbyt dużej lub zbyt mały dla danego testu.</span><span class="sxs-lookup"><span data-stu-id="51380-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="51380-242">Mniejsze ryzyko udostępnianie stanu między testami, które tworzy niechcianych zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="51380-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="51380-243">W jednostce testowanie struktur, `Setup` jest wywoływana przed test każdej jednostki w pakiecie testowym.</span><span class="sxs-lookup"><span data-stu-id="51380-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="51380-244">Podczas gdy niektóre może zobaczyć jako przydatne narzędzie, zazwyczaj kończy się prowadzące do przeglądarek i trudne do odczytania testów.</span><span class="sxs-lookup"><span data-stu-id="51380-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="51380-245">Zwykle obejmuje różne wymagania, aby uruchomić test działanie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="51380-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="51380-246">Niestety `Setup` wymusza przy użyciu dokładnie te same wymagania dla każdego testu.</span><span class="sxs-lookup"><span data-stu-id="51380-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="51380-247">xUnit usunęła instalacji i usuwania, począwszy od wersji 2.x</span><span class="sxs-lookup"><span data-stu-id="51380-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-248">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="51380-249">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="51380-250">Należy unikać wiele asercji</span><span class="sxs-lookup"><span data-stu-id="51380-250">Avoid multiple asserts</span></span>
<span data-ttu-id="51380-251">Podczas pisania testów, spróbuj obejmujący tylko jednego potwierdzenia dla testu.</span><span class="sxs-lookup"><span data-stu-id="51380-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="51380-252">Typowe sposoby użycia tylko jednej assert, obejmują:</span><span class="sxs-lookup"><span data-stu-id="51380-252">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="51380-253">Utwórz oddzielne testu dla każdego potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="51380-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="51380-254">Użyć sparametryzowanych testów.</span><span class="sxs-lookup"><span data-stu-id="51380-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="51380-255">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="51380-255">Why?</span></span>
- <span data-ttu-id="51380-256">Jeśli jeden Asercja nie powiedzie się, nie zostanie ono ocenione kolejnych potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="51380-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="51380-257">Gwarantuje, że nie są potwierdzające wiele przypadków, w testach.</span><span class="sxs-lookup"><span data-stu-id="51380-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="51380-258">Zawiera cały obraz tego, dlaczego testy kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="51380-258">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="51380-259">W przypadku wprowadzenia wielu potwierdza do przypadku testowego, go nie masz gwarancję, że wszystkie z deklaracji rozkazujących będzie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="51380-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="51380-260">W większości struktur testowania jednostek po potwierdzenie nie powiedzie się podczas testów jednostkowych, testów postępowania są automatycznie uznawane za zakończonych niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="51380-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="51380-261">Może to być mylące, ponieważ funkcje, które rzeczywiście działa, będą wyświetlane jako niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="51380-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="51380-262">Typowe wyjątkiem od tej reguły jest potwierdzające względem obiektu.</span><span class="sxs-lookup"><span data-stu-id="51380-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="51380-263">W tym przypadku jest ogół dopuszczalne mieć wielu deklaracji rozkazujących dla każdej właściwości, aby upewnić się, obiekt jest w stanie się on w oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="51380-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="51380-264">Zły:</span><span class="sxs-lookup"><span data-stu-id="51380-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="51380-265">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="51380-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="51380-266">Sprawdzanie poprawności metody prywatne przez metody publiczne testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="51380-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="51380-267">W większości przypadków nie należy, aby przetestować metody prywatnej.</span><span class="sxs-lookup"><span data-stu-id="51380-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="51380-268">Metody prywatne są szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="51380-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="51380-269">Można traktować je w ten sposób: metody prywatne nigdy nie istnieje w izolacji.</span><span class="sxs-lookup"><span data-stu-id="51380-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="51380-270">W pewnym momencie będzie to mieć publiczną metodę umożliwiający dostęp do Internetu, który wywołuje metody prywatnej jako część jego implementacja.</span><span class="sxs-lookup"><span data-stu-id="51380-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="51380-271">Co zadbać o to wynik końcowy metodę publiczną, która wywołuje jeden prywatny.</span><span class="sxs-lookup"><span data-stu-id="51380-271">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="51380-272">Należy wziąć pod uwagę następujący przypadek</span><span class="sxs-lookup"><span data-stu-id="51380-272">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="51380-273">Pierwszy reakcję może być do rozpoczęcia pisania test `TrimInput` ponieważ chcesz upewnić się, że metoda działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="51380-273">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="51380-274">Jednak jest całkowicie możliwe, `ParseLogLine` manipuluje `sanitizedInput` w taki sposób, który nie będzie, renderowanie Testuj pod względem `TrimInput` bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="51380-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span> 

<span data-ttu-id="51380-275">Test rzeczywisty ma być przeprowadzane względem publicznej metody mające połączenie z Internetem `ParseLogLine` ponieważ jest to, co powinno ostatecznie interesujące Cię.</span><span class="sxs-lookup"><span data-stu-id="51380-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="51380-276">Z tego punktu widzenia Jeśli widzisz metody prywatnej, Znajdź publicznej metody i pisania testów względem tej metody.</span><span class="sxs-lookup"><span data-stu-id="51380-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="51380-277">Po prostu, ponieważ jest to metoda prywatna zwraca oczekiwany wynik, nie znaczy, że system, który wywołuje na końcu metody prywatnej używa wynik poprawnie.</span><span class="sxs-lookup"><span data-stu-id="51380-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="51380-278">Klasy zastępczej odwołań statycznych</span><span class="sxs-lookup"><span data-stu-id="51380-278">Stub static references</span></span>
<span data-ttu-id="51380-279">Jest jedną z zasad testu jednostkowego, musi mieć pełną kontrolę nad systemie poddawanym testowi.</span><span class="sxs-lookup"><span data-stu-id="51380-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="51380-280">Może to być problematyczne, gdy w kodzie produkcyjnym obejmuje wywołania do odwołań statycznych (np. `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="51380-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="51380-281">Rozważmy poniższy kod</span><span class="sxs-lookup"><span data-stu-id="51380-281">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="51380-282">Jak ten kod prawdopodobnie można jednostki testowane?</span><span class="sxs-lookup"><span data-stu-id="51380-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="51380-283">Możesz spróbować podejście takich jak</span><span class="sxs-lookup"><span data-stu-id="51380-283">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="51380-284">Niestety będzie szybkie tworzenie, istnieje kilka problemów dotyczących testów.</span><span class="sxs-lookup"><span data-stu-id="51380-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="51380-285">Jeśli zestaw testów jest uruchamiana we wtorek, drugi test zostanie przekazany, ale pierwszy test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="51380-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="51380-286">Jeżeli zestaw testów jest wykonywany w innych dniu, pierwszy test zostanie przekazany, ale drugi test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="51380-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="51380-287">Aby rozwiązać te problemy, konieczne będzie wprowadzenie *szwu* w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="51380-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="51380-288">Jest jednym z podejść do zawijania kodu, które należy kontrolować w interfejsie i kodzie produkcyjnym, zależą od tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="51380-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="51380-289">Stanie się w pakiecie testowym</span><span class="sxs-lookup"><span data-stu-id="51380-289">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="51380-290">Teraz zestaw testów ma pełną kontrolę nad `DateTime.Now` i można zastąpić klasą zastępczą dowolnej wartości podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="51380-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
