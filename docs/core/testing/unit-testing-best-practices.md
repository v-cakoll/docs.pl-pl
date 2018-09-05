---
title: Najlepsze rozwiązania dotyczące pisania testów jednostkowych
description: Poznaj najlepsze rozwiązania dotyczące pisania testów jednostkowych, które Dbaj o jakość kodu i odporności na błędy
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 69fe0cae141d1ed1e1281eecd78bf03e6e8be961
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530601"
---
# <a name="unit-testing-best-practices"></a><span data-ttu-id="f1a08-103">Najlepsze rozwiązania testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="f1a08-103">Unit testing best practices</span></span>

<span data-ttu-id="f1a08-104">Przez [John Reese](http://reesespieces.io) ze specjalnymi dzięki [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="f1a08-104">By [John Reese](http://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

<span data-ttu-id="f1a08-105">Istnieje wiele korzyści, do pisania testów jednostkowych; pomagają przy użyciu regresji, zapewniają dostęp do dokumentacji i ułatwienia dobrego projektowania.</span><span class="sxs-lookup"><span data-stu-id="f1a08-105">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="f1a08-106">Jednak testy jednostkowe trudne do odczytu i kruchy można spustoszyć bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-106">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span>

<span data-ttu-id="f1a08-107">W tym przewodniku dowiesz się najważniejsze wskazówki podczas pisania testów jednostkowych, aby zachować testów, odporne i łatwe do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="f1a08-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="f1a08-108">Dlaczego test jednostkowy?</span><span class="sxs-lookup"><span data-stu-id="f1a08-108">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="f1a08-109">Mniej czasu na wykonywanie testów funkcjonalnych</span><span class="sxs-lookup"><span data-stu-id="f1a08-109">Less time performing functional tests</span></span>
<span data-ttu-id="f1a08-110">Testy funkcjonalne są kosztowne.</span><span class="sxs-lookup"><span data-stu-id="f1a08-110">Functional tests are expensive.</span></span> <span data-ttu-id="f1a08-111">Są na ogół podczas otwierania aplikacji, a następnie wykonanie serii czynności, które użytkownik (lub kogoś innego), należy wykonać, aby można było zweryfikować oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-111">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="f1a08-112">Te kroki nie zawsze być znane do testera, co oznacza, że konieczne będzie skontaktowanie się z ktoś większą wiedzę w obszarze w celu przeprowadzenia badania.</span><span class="sxs-lookup"><span data-stu-id="f1a08-112">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="f1a08-113">Testowanie sam może potrwać sekund proste zmiany lub minut w celu większe zmiany.</span><span class="sxs-lookup"><span data-stu-id="f1a08-113">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="f1a08-114">Ponadto ten proces należy powtórzyć dla każdej zmiany wprowadzone w systemie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-114">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="f1a08-115">Testy jednostkowe, z drugiej strony ręcznie, zająć milisekund, mogą być uruchamiane naciśnięciem przycisku i nie muszą mieć żadnej wiedzy w dużych systemu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-115">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="f1a08-116">Określa, czy test kończy się pomyślnie lub nie powiedzie się, zależy od narzędzia test runner nie osoby.</span><span class="sxs-lookup"><span data-stu-id="f1a08-116">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="f1a08-117">Ochrona przed regresji</span><span class="sxs-lookup"><span data-stu-id="f1a08-117">Protection against regression</span></span>
<span data-ttu-id="f1a08-118">Regresja wady są wady, które są wprowadzone podczas wprowadzania zmian do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1a08-118">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="f1a08-119">Powszechne jest wprowadzanie dla testerów, nie tylko testowania ich nowych funkcji, ale także funkcje, które istniało wcześniej w celu sprawdzenia, które było wcześniej zaimplementowane funkcje nadal działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f1a08-119">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="f1a08-120">Za pomocą testów jednostkowych jest możliwe ponowne uruchamianie usługi cały zestaw testów po każdej kompilacji, lub nawet w przypadku, po zmianie wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-120">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="f1a08-121">Co daje pewność, że nowy kod nie mogą przerwać działania istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="f1a08-121">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="f1a08-122">Dokumentacja pliku wykonywalnego</span><span class="sxs-lookup"><span data-stu-id="f1a08-122">Executable documentation</span></span>
<span data-ttu-id="f1a08-123">Go może nie zawsze jest oczywiste działanie konkretną metodę lub jego zachowania podany niektórych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f1a08-123">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="f1a08-124">Możesz poprosić samodzielnie: to metoda zachowaniem jeśli mogę przekazać pusty ciąg?</span><span class="sxs-lookup"><span data-stu-id="f1a08-124">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="f1a08-125">Wartość null?</span><span class="sxs-lookup"><span data-stu-id="f1a08-125">Null?</span></span>

<span data-ttu-id="f1a08-126">W przypadku zestawu testów jednostkowych dobrze nazwane każdy test powinien móc wyjaśniają oczekiwanych danych wyjściowych dla danego składnika.</span><span class="sxs-lookup"><span data-stu-id="f1a08-126">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="f1a08-127">Ponadto powinno być możliwe sprawdzić, czy rzeczywiście działa.</span><span class="sxs-lookup"><span data-stu-id="f1a08-127">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="f1a08-128">Mniej sprzężonych kodu</span><span class="sxs-lookup"><span data-stu-id="f1a08-128">Less coupled code</span></span>
<span data-ttu-id="f1a08-129">Gdy kod jest ściśle powiązane, może być trudne do testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="f1a08-129">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="f1a08-130">Bez tworzenia testów jednostkowych dla kodu, który właśnie piszesz, sprzężenia mogą być mniej jasne.</span><span class="sxs-lookup"><span data-stu-id="f1a08-130">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="f1a08-131">Pisanie testów dla kodu naturalnie będzie rozdzielenie kodu, ponieważ może być trudniejsze do testowania, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-131">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="f1a08-132">Charakterystyki testu jednostkowego dobre</span><span class="sxs-lookup"><span data-stu-id="f1a08-132">Characteristics of a good unit test</span></span>
- <span data-ttu-id="f1a08-133">**Szybkie**.</span><span class="sxs-lookup"><span data-stu-id="f1a08-133">**Fast**.</span></span> <span data-ttu-id="f1a08-134">Nie jest niczym niezwykłym dojrzała projektów, które mają kilka tysięcy testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="f1a08-134">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="f1a08-135">Testy jednostkowe powinno zająć bardzo mało czasu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="f1a08-135">Unit tests should take very little time to run.</span></span> <span data-ttu-id="f1a08-136">Liczba milisekund.</span><span class="sxs-lookup"><span data-stu-id="f1a08-136">Milliseconds.</span></span>
- <span data-ttu-id="f1a08-137">**Izolowane**.</span><span class="sxs-lookup"><span data-stu-id="f1a08-137">**Isolated**.</span></span> <span data-ttu-id="f1a08-138">Testy jednostkowe są autonomiczne, mogą być uruchamiane w izolacji i mieć żadnych zależności na wszelkich zewnętrznych czynników, takich jak system plików lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f1a08-138">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="f1a08-139">**Powtarzalne**.</span><span class="sxs-lookup"><span data-stu-id="f1a08-139">**Repeatable**.</span></span> <span data-ttu-id="f1a08-140">Uruchamianie testów jednostkowych powinny być zgodne z jego wyniki, oznacza to, zawsze zwraca ten sam wynik, jeśli nie należy zmieniać niczego Between przebiegów.</span><span class="sxs-lookup"><span data-stu-id="f1a08-140">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="f1a08-141">**Sprawdzanie własnym**.</span><span class="sxs-lookup"><span data-stu-id="f1a08-141">**Self-Checking**.</span></span> <span data-ttu-id="f1a08-142">Test powinien móc automatycznie wykryć, czy przekazywany ani nie powiodła się bez interwencji człowieka.</span><span class="sxs-lookup"><span data-stu-id="f1a08-142">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="f1a08-143">**Czas**.</span><span class="sxs-lookup"><span data-stu-id="f1a08-143">**Timely**.</span></span> <span data-ttu-id="f1a08-144">Test jednostkowy nie powinna przyjmować zapisu w porównaniu do testowany kod jest nieproporcjonalnie dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-144">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="f1a08-145">Jeśli okaże się, testowanie kodu, biorąc dużą ilość czasu w porównaniu do pisania kodu, należy wziąć pod uwagę projekt, który jest bardziej sprawdzalnego działa zgodnie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-145">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="f1a08-146">Teraz używać tego samego języka</span><span class="sxs-lookup"><span data-stu-id="f1a08-146">Let's speak the same language</span></span>
<span data-ttu-id="f1a08-147">Termin *testowanie* jest Niestety bardzo użyte w przypadku testowania.</span><span class="sxs-lookup"><span data-stu-id="f1a08-147">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="f1a08-148">Następujące definiuje najbardziej powszechne typy *elementów sztucznych* podczas pisania testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="f1a08-148">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="f1a08-149">*Sztuczne* -sfałszowana to ogólny termin określający, który może służyć do opisu odcinek lub makiety obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-149">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="f1a08-150">Czy jest on odcinek czy pozorny zależy od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="f1a08-150">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="f1a08-151">Dlatego oznacza to, sfałszowana można odcinek lub pozorny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-151">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="f1a08-152">*Testowanie* -makiety obiektu jest obiektem sztuczne w systemie, który decyduje, czy test jednostkowy został zakończony powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f1a08-152">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="f1a08-153">Pozorny rozpoczyna się jako sfałszowana do momentu jej przeciwko.</span><span class="sxs-lookup"><span data-stu-id="f1a08-153">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="f1a08-154">*Klasy zastępczej* — odcinek jest musi zastąpić istniejące zależności (lub współpracownika) w systemie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-154">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="f1a08-155">Za pomocą odcinek, można testować kod bez konieczności wnikania zależnością bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f1a08-155">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="f1a08-156">Domyślnie sfałszowana rozpoczyna się jako wejściowy.</span><span class="sxs-lookup"><span data-stu-id="f1a08-156">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="f1a08-157">Rozważmy następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="f1a08-157">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="f1a08-158">Jest to przykład wycinka są określane jako pozorny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-158">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="f1a08-159">W tym przypadku jest to wycinka.</span><span class="sxs-lookup"><span data-stu-id="f1a08-159">In this case, it is a stub.</span></span> <span data-ttu-id="f1a08-160">Po prostu przechodząc w kolejności, co oznacza, że aby można było utworzyć wystąpienia `Purchase` (system w trakcie testu).</span><span class="sxs-lookup"><span data-stu-id="f1a08-160">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="f1a08-161">Nazwa `MockOrder` jest również bardzo mylące, ponieważ ponownie, kolejność nie jest pozorny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-161">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="f1a08-162">Lepszym rozwiązaniem byłoby</span><span class="sxs-lookup"><span data-stu-id="f1a08-162">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="f1a08-163">Zmieniając nazwę klasy, która ma `FakeOrder`, wprowadzono klasy o wiele bardziej ogólnym, klasa może służyć jako pozorny ani klas zastępczych.</span><span class="sxs-lookup"><span data-stu-id="f1a08-163">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="f1a08-164">Obowiązuje lepszym miejscem dla przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="f1a08-164">Whichever is better for the test case.</span></span> <span data-ttu-id="f1a08-165">W powyższym przykładzie `FakeOrder` służy jako wejściowy.</span><span class="sxs-lookup"><span data-stu-id="f1a08-165">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="f1a08-166">Nie używasz `FakeOrder` w dowolnej formie podczas assert.</span><span class="sxs-lookup"><span data-stu-id="f1a08-166">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="f1a08-167">`FakeOrder` po prostu została przekazana do `Purchase` klasy w celu spełnienia wymagań konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f1a08-167">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="f1a08-168">Aby użyć go jako pozorny, możesz to zrobić coś takiego</span><span class="sxs-lookup"><span data-stu-id="f1a08-168">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="f1a08-169">W takim przypadku podczas sprawdzania właściwość sfałszowana (potwierdzające przed nim), więc w powyższym fragmencie kodu `mockOrder` jest pozorny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-169">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1a08-170">Należy uzyskać prawidłowy terminologię.</span><span class="sxs-lookup"><span data-stu-id="f1a08-170">It's important to get this terminology correct.</span></span> <span data-ttu-id="f1a08-171">Wywołanie usługi wycinków "mocks" inni deweloperzy mają wartość false zakładają zgodne z zamiarami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1a08-171">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="f1a08-172">Główny jest, aby pamiętać mocks i wycinków jest mocks przypominają wycinków, że asercja względem makiety obiektu, natomiast nie wystąpiło zapewnienie względem wycinka.</span><span class="sxs-lookup"><span data-stu-id="f1a08-172">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f1a08-173">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f1a08-173">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="f1a08-174">Nadawanie nazw testów</span><span class="sxs-lookup"><span data-stu-id="f1a08-174">Naming your tests</span></span>
<span data-ttu-id="f1a08-175">Nazwa testu powinien składać się z trzech części:</span><span class="sxs-lookup"><span data-stu-id="f1a08-175">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="f1a08-176">Nazwa metody poddawana testom.</span><span class="sxs-lookup"><span data-stu-id="f1a08-176">The name of the method being tested.</span></span>
- <span data-ttu-id="f1a08-177">Scenariusz, w którym jest testowana.</span><span class="sxs-lookup"><span data-stu-id="f1a08-177">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="f1a08-178">Oczekiwane zachowanie po wywołaniu tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f1a08-178">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-179">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-179">Why?</span></span>
- <span data-ttu-id="f1a08-180">Standardy nazewnictwa są ważne, ponieważ one jawnie express celem testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-180">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="f1a08-181">Testy są więcej niż tylko upewniając się, Twój kod działa, ale oferują też dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f1a08-181">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="f1a08-182">Po prostu patrząc pakietów testów jednostkowych, można rozpoznać zachowania kodu bez nawet spojrzenie na sam kod.</span><span class="sxs-lookup"><span data-stu-id="f1a08-182">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="f1a08-183">Ponadto gdy testy nie powiodą się, możesz zobaczyć dokładnie scenariuszy, do których nie spełniają Twoich oczekiwań.</span><span class="sxs-lookup"><span data-stu-id="f1a08-183">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-184">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-184">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="f1a08-185">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-185">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="f1a08-186">Rozmieszczanie testów</span><span class="sxs-lookup"><span data-stu-id="f1a08-186">Arranging your tests</span></span>
<span data-ttu-id="f1a08-187">**Rozmieść, działania, Asercja** pojawia się często wzorca, gdy testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="f1a08-187">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="f1a08-188">Jak wskazuje nazwa, składa się z trzech głównych czynności:</span><span class="sxs-lookup"><span data-stu-id="f1a08-188">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="f1a08-189">*Rozmieść* obiektów, tworzenia i konfigurowania zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="f1a08-189">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="f1a08-190">*ACT* na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-190">*Act* on an object.</span></span>
- <span data-ttu-id="f1a08-191">*Asercja* , coś, co jest zgodne z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f1a08-191">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-192">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-192">Why?</span></span>
- <span data-ttu-id="f1a08-193">Wyraźnie oddziela jest poddawana testom z *Rozmieść* i *asercja* kroki.</span><span class="sxs-lookup"><span data-stu-id="f1a08-193">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="f1a08-194">Mniej szansę intermix potwierdzenia z kodem "Act".</span><span class="sxs-lookup"><span data-stu-id="f1a08-194">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="f1a08-195">Czytelność jest jednym z najważniejszych aspektów, podczas zapisywania testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-195">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="f1a08-196">Oddzielając każdy z tych akcji w ramach testu wyraźnie wyróżnić zależności wymagane do wywołania w kodzie, jak kod jest wywoływana i próbujesz potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f1a08-196">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="f1a08-197">Może być możliwe, aby połączyć kilka kroków i zmniejszyć rozmiar testu, podstawowym celem jest zapewnienie testu jako do odczytu, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f1a08-197">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-198">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-198">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="f1a08-199">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-199">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="f1a08-200">Pisanie minimalny zestaw testów przekazywanie</span><span class="sxs-lookup"><span data-stu-id="f1a08-200">Write minimally passing tests</span></span>
<span data-ttu-id="f1a08-201">Dane wejściowe do użycia w test jednostkowy powinna być najprostsza możliwa, aby sprawdzić zachowanie, które obecnie testujesz.</span><span class="sxs-lookup"><span data-stu-id="f1a08-201">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-202">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-202">Why?</span></span>
- <span data-ttu-id="f1a08-203">Testy stają się bardziej odporne na przyszłe zmiany w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-203">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="f1a08-204">Im bliżej testowania implementacji zachowania.</span><span class="sxs-lookup"><span data-stu-id="f1a08-204">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="f1a08-205">Testy, które zawierają więcej informacji, niż jest to wymagane do przekazania testu wyższe prawdopodobieństwo wprowadzenie błędów do testu i może być celem mniej wyczyść test.</span><span class="sxs-lookup"><span data-stu-id="f1a08-205">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="f1a08-206">Podczas pisania testów chcesz skupić się na zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-206">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="f1a08-207">Ustawianie właściwości dodatkowych modeli lub przy użyciu wartości różna od zera, gdy nie jest wymagany, źle wpływa tylko na próbujesz potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="f1a08-207">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-208">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-208">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="f1a08-209">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-209">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="f1a08-210">Należy unikać magic ciągów</span><span class="sxs-lookup"><span data-stu-id="f1a08-210">Avoid magic strings</span></span>
<span data-ttu-id="f1a08-211">Nazwy zmiennych w jednostce testów to jako ważne, jeśli nie ważniejsza, nazw zmiennych w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f1a08-211">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="f1a08-212">Testy jednostkowe nie powinna zawierać ciągi magic.</span><span class="sxs-lookup"><span data-stu-id="f1a08-212">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-213">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-213">Why?</span></span>
- <span data-ttu-id="f1a08-214">Eliminuje konieczność Sprawdzanie kodu produkcyjnego, aby ustalić, co sprawia, że wartość specjalne dla czytnika testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-214">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="f1a08-215">Wyraźnie pokazuje, co ma być realizowany *udowodnić, że* zamiast próbowania *osiągnąć*.</span><span class="sxs-lookup"><span data-stu-id="f1a08-215">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="f1a08-216">Ciągi Magic może nie być jasne do czytnika testów.</span><span class="sxs-lookup"><span data-stu-id="f1a08-216">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="f1a08-217">Jeśli ciąg wygląda niezwykłe, mogą dowiedzieć się, dlaczego określoną wartość został wybrany dla parametru lub zwróć wartość.</span><span class="sxs-lookup"><span data-stu-id="f1a08-217">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="f1a08-218">Może to prowadzić do Przyjrzyj się bliżej szczegóły implementacji, a nie skoncentrować się na testowej.</span><span class="sxs-lookup"><span data-stu-id="f1a08-218">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="f1a08-219">Podczas pisania testów, należy dążyć do express tyle przeznaczenie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f1a08-219">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="f1a08-220">W przypadku ciągów magic dobra metoda jest można przypisać te wartości na stałe.</span><span class="sxs-lookup"><span data-stu-id="f1a08-220">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-221">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-221">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="f1a08-222">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-222">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="f1a08-223">Należy unikać logiki w testach</span><span class="sxs-lookup"><span data-stu-id="f1a08-223">Avoid logic in tests</span></span>
<span data-ttu-id="f1a08-224">Podczas zapisywania jednostkowe, testy Unikaj łączenia ciągów ręczne i logiczne warunków, takich jak `if`, `while`, `for`, `switch`itp.</span><span class="sxs-lookup"><span data-stu-id="f1a08-224">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-225">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-225">Why?</span></span>
- <span data-ttu-id="f1a08-226">Mniej masz szansę, aby wprowadzić usterkę w testach.</span><span class="sxs-lookup"><span data-stu-id="f1a08-226">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="f1a08-227">Skup się na wynik końcowy, a nie szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="f1a08-227">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="f1a08-228">Po wprowadzeniu logiki w pakiecie testowym znacznie zwiększa ryzyko wprowadzenia usterkę do niego.</span><span class="sxs-lookup"><span data-stu-id="f1a08-228">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="f1a08-229">Ostatnie miejsce, które chcesz znaleźć usterkę znajduje się w pakiecie testowym.</span><span class="sxs-lookup"><span data-stu-id="f1a08-229">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="f1a08-230">Powinny mieć pewność, że testy pracy wysokiego poziomu, w przeciwnym razie zostanie ufasz je.</span><span class="sxs-lookup"><span data-stu-id="f1a08-230">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="f1a08-231">Testy, które nie ufasz, nie oferuje żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="f1a08-231">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="f1a08-232">Gdy test zakończy się niepowodzeniem, chcesz mieć sens, czy jest coś, co faktycznie problem z kodem i że nie może być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f1a08-232">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="f1a08-233">Jeśli logika w teście nieuniknione, należy rozważyć rozdzielenie test na co najmniej dwóch różnych badań.</span><span class="sxs-lookup"><span data-stu-id="f1a08-233">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-234">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-234">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="f1a08-235">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-235">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="f1a08-236">Preferuj metody pomocnika do instalacji i usuwania</span><span class="sxs-lookup"><span data-stu-id="f1a08-236">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="f1a08-237">Podobne obiektu lub stanu są wymagane dla testów, najpierw metody pomocnika niż korzystanie z atrybutów instalacji i usuwania, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="f1a08-237">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-238">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-238">Why?</span></span>
- <span data-ttu-id="f1a08-239">Mniej błąd podczas odczytywania testów, ponieważ cały kod nie jest widoczny w ramach każdego testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-239">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="f1a08-240">Mniejsze ryzyko Definiowanie zbyt dużej lub zbyt mały dla danego testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-240">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="f1a08-241">Mniejsze ryzyko udostępnianie stanu między testami, które tworzy niechcianych zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="f1a08-241">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="f1a08-242">W jednostce testowanie struktur, `Setup` jest wywoływana przed test każdej jednostki w pakiecie testowym.</span><span class="sxs-lookup"><span data-stu-id="f1a08-242">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="f1a08-243">Podczas gdy niektóre może zobaczyć jako przydatne narzędzie, zazwyczaj kończy się prowadzące do przeglądarek i trudne do odczytania testów.</span><span class="sxs-lookup"><span data-stu-id="f1a08-243">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="f1a08-244">Zwykle obejmuje różne wymagania, aby uruchomić test działanie każdego testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-244">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="f1a08-245">Niestety `Setup` wymusza przy użyciu dokładnie te same wymagania dla każdego testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-245">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="f1a08-246">xUnit usunęła instalacji i usuwania, począwszy od wersji 2.x</span><span class="sxs-lookup"><span data-stu-id="f1a08-246">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-247">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-247">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="f1a08-248">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-248">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="f1a08-249">Należy unikać wiele asercji</span><span class="sxs-lookup"><span data-stu-id="f1a08-249">Avoid multiple asserts</span></span>
<span data-ttu-id="f1a08-250">Podczas pisania testów, spróbuj obejmujący tylko jednego potwierdzenia dla testu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-250">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="f1a08-251">Typowe sposoby użycia tylko jednej assert, obejmują:</span><span class="sxs-lookup"><span data-stu-id="f1a08-251">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="f1a08-252">Utwórz oddzielne testu dla każdego potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f1a08-252">Create a separate test for each assert.</span></span>
- <span data-ttu-id="f1a08-253">Użyć sparametryzowanych testów.</span><span class="sxs-lookup"><span data-stu-id="f1a08-253">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="f1a08-254">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="f1a08-254">Why?</span></span>
- <span data-ttu-id="f1a08-255">Jeśli jeden Asercja nie powiedzie się, nie zostanie ono ocenione kolejnych potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f1a08-255">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="f1a08-256">Gwarantuje, że nie są potwierdzające wiele przypadków, w testach.</span><span class="sxs-lookup"><span data-stu-id="f1a08-256">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="f1a08-257">Zawiera cały obraz tego, dlaczego testy kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f1a08-257">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="f1a08-258">W przypadku wprowadzenia wielu potwierdza do przypadku testowego, go nie masz gwarancję, że wszystkie z deklaracji rozkazujących będzie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="f1a08-258">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="f1a08-259">W większości struktur testowania jednostek po potwierdzenie nie powiedzie się podczas testów jednostkowych, testów postępowania są automatycznie uznawane za zakończonych niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f1a08-259">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="f1a08-260">Może to być mylące, ponieważ funkcje, które rzeczywiście działa, będą wyświetlane jako niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-260">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="f1a08-261">Typowe wyjątkiem od tej reguły jest potwierdzające względem obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-261">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="f1a08-262">W tym przypadku jest ogół dopuszczalne mieć wielu deklaracji rozkazujących dla każdej właściwości, aby upewnić się, obiekt jest w stanie się on w oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="f1a08-262">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="f1a08-263">Zły:</span><span class="sxs-lookup"><span data-stu-id="f1a08-263">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="f1a08-264">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="f1a08-264">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="f1a08-265">Sprawdzanie poprawności metody prywatne przez metody publiczne testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="f1a08-265">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="f1a08-266">W większości przypadków nie należy, aby przetestować metody prywatnej.</span><span class="sxs-lookup"><span data-stu-id="f1a08-266">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="f1a08-267">Metody prywatne są szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="f1a08-267">Private methods are an implementation detail.</span></span> <span data-ttu-id="f1a08-268">Można traktować je w ten sposób: metody prywatne nigdy nie istnieje w izolacji.</span><span class="sxs-lookup"><span data-stu-id="f1a08-268">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="f1a08-269">W pewnym momencie będzie to mieć publiczną metodę umożliwiający dostęp do Internetu, który wywołuje metody prywatnej jako część jego implementacja.</span><span class="sxs-lookup"><span data-stu-id="f1a08-269">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="f1a08-270">Co zadbać o to wynik końcowy metodę publiczną, która wywołuje jeden prywatny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-270">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="f1a08-271">Należy wziąć pod uwagę następujący przypadek</span><span class="sxs-lookup"><span data-stu-id="f1a08-271">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="f1a08-272">Pierwszy reakcję może być do rozpoczęcia pisania test `trimInput` ponieważ chcesz upewnić się, że metoda działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f1a08-272">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="f1a08-273">Jednak jest całkowicie możliwe, `ParseLogLine` manipuluje `sanitizedInput` w taki sposób, który nie będzie, renderowanie Testuj pod względem `trimInput` bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="f1a08-273">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="f1a08-274">Test rzeczywisty ma być przeprowadzane względem publicznej metody mające połączenie z Internetem `ParseLogLine` ponieważ jest to, co powinno ostatecznie interesujące Cię.</span><span class="sxs-lookup"><span data-stu-id="f1a08-274">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="f1a08-275">Z tego punktu widzenia Jeśli widzisz metody prywatnej, Znajdź publicznej metody i pisania testów względem tej metody.</span><span class="sxs-lookup"><span data-stu-id="f1a08-275">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="f1a08-276">Po prostu, ponieważ jest to metoda prywatna zwraca oczekiwany wynik, nie znaczy, że system, który wywołuje na końcu metody prywatnej używa wynik poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f1a08-276">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="f1a08-277">Klasy zastępczej odwołań statycznych</span><span class="sxs-lookup"><span data-stu-id="f1a08-277">Stub static references</span></span>
<span data-ttu-id="f1a08-278">Jest jedną z zasad testu jednostkowego, musi mieć pełną kontrolę nad systemie poddawanym testowi.</span><span class="sxs-lookup"><span data-stu-id="f1a08-278">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="f1a08-279">Może to być problematyczne, gdy w kodzie produkcyjnym obejmuje wywołania do odwołań statycznych (np. `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="f1a08-279">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="f1a08-280">Rozważmy poniższy kod</span><span class="sxs-lookup"><span data-stu-id="f1a08-280">Consider the following code</span></span>

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

<span data-ttu-id="f1a08-281">Jak ten kod prawdopodobnie można jednostki testowane?</span><span class="sxs-lookup"><span data-stu-id="f1a08-281">How can this code possibly be unit tested?</span></span> <span data-ttu-id="f1a08-282">Możesz spróbować podejście takich jak</span><span class="sxs-lookup"><span data-stu-id="f1a08-282">You may try an approach such as</span></span>

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

<span data-ttu-id="f1a08-283">Niestety będzie szybkie tworzenie, istnieje kilka problemów dotyczących testów.</span><span class="sxs-lookup"><span data-stu-id="f1a08-283">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="f1a08-284">Jeśli zestaw testów jest uruchamiana we wtorek, drugi test zostanie przekazany, ale pierwszy test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f1a08-284">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="f1a08-285">Jeżeli zestaw testów jest wykonywany w innych dniu, pierwszy test zostanie przekazany, ale drugi test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f1a08-285">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="f1a08-286">Aby rozwiązać te problemy, konieczne będzie wprowadzenie *szwu* w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f1a08-286">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="f1a08-287">Jest jednym z podejść do zawijania kodu, które należy kontrolować w interfejsie i kodzie produkcyjnym, zależą od tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f1a08-287">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public bool GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
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

<span data-ttu-id="f1a08-288">Stanie się w pakiecie testowym</span><span class="sxs-lookup"><span data-stu-id="f1a08-288">Your test suite now becomes</span></span>

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

<span data-ttu-id="f1a08-289">Teraz zestaw testów ma pełną kontrolę nad `DateTime.Now` i można zastąpić klasą zastępczą dowolnej wartości podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="f1a08-289">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
