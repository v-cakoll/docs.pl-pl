---
title: Najważniejsze wskazówki dotyczące pisania testów jednostkowych
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi pisania testów jednostkowych, które mają jakość kodu napędowego i odporność projektów .NET Core i .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240964"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="99ecc-103">Najlepsze rozwiązania dotyczące testowania jednostkowego z .NET Core i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="99ecc-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="99ecc-104">Istnieje wiele korzyści z pisania testów jednostkowych; pomagają w regresji, dostarczają dokumentację i ułatwiają dobry projekt.</span><span class="sxs-lookup"><span data-stu-id="99ecc-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="99ecc-105">Jednak trudne do odczytania i kruche testy jednostkowe mogą siać spustoszenie w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="99ecc-106">W tym artykule opisano niektóre najlepsze rozwiązania dotyczące projektowania testów jednostkowych dla projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="99ecc-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="99ecc-107">W tym przewodniku dowiesz się o najlepszych praktykach podczas pisania testów jednostkowych, aby testy były odporne i łatwe do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="99ecc-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="99ecc-108">[John Reese](https://reese.dev) ze specjalnymi podziękowaniami dla [Roya Osherove'a](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="99ecc-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="99ecc-109">Dlaczego test jednostkowy?</span><span class="sxs-lookup"><span data-stu-id="99ecc-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="99ecc-110">Krótszy czas wykonywania testów funkcjonalnych</span><span class="sxs-lookup"><span data-stu-id="99ecc-110">Less time performing functional tests</span></span>
<span data-ttu-id="99ecc-111">Testy funkcjonalne są drogie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-111">Functional tests are expensive.</span></span> <span data-ttu-id="99ecc-112">Zazwyczaj obejmują one otwarcie aplikacji i wykonanie serii kroków, które ty (lub ktoś inny), należy wykonać w celu zweryfikowania oczekiwanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="99ecc-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="99ecc-113">Kroki te mogą nie zawsze być znane testerowi, co oznacza, że będą musieli dotrzeć do kogoś bardziej kompetentnego w okolicy w celu przeprowadzenia testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="99ecc-114">Samo testowanie może potrwać kilka sekund dla trywialnych zmian lub minut dla większych zmian.</span><span class="sxs-lookup"><span data-stu-id="99ecc-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="99ecc-115">Wreszcie, proces ten musi być powtórzony dla każdej zmiany, które można wprowadzić w systemie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="99ecc-116">Testy jednostkowe, z drugiej strony, wziąć milisekund, mogą być uruchamiane po naciśnięciu przycisku i nie koniecznie wymagają żadnej wiedzy na temat systemu w ogóle.</span><span class="sxs-lookup"><span data-stu-id="99ecc-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="99ecc-117">To, czy test zda lub nie, zależy od biegacza testowego, a nie jednostki.</span><span class="sxs-lookup"><span data-stu-id="99ecc-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="99ecc-118">Ochrona przed regresją</span><span class="sxs-lookup"><span data-stu-id="99ecc-118">Protection against regression</span></span>
<span data-ttu-id="99ecc-119">Wady regresji są wady, które są wprowadzane po wprowadzeniu zmiany do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="99ecc-120">Testerzy często testują nie tylko swoją nową funkcję, ale także funkcje, które istniały wcześniej, aby sprawdzić, czy wcześniej zaimplementowane funkcje nadal działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="99ecc-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="99ecc-121">W przypadku testowania jednostkowego można ponownie uruchomić cały zestaw testów po każdej kompilacji lub nawet po zmianie wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="99ecc-122">Daje pewność, że nowy kod nie może złamać istniejące funkcje.</span><span class="sxs-lookup"><span data-stu-id="99ecc-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="99ecc-123">Dokumentacja wykonywalna</span><span class="sxs-lookup"><span data-stu-id="99ecc-123">Executable documentation</span></span>
<span data-ttu-id="99ecc-124">Nie zawsze może być oczywiste, co dana metoda robi lub jak zachowuje się biorąc pod uwagę pewne dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="99ecc-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="99ecc-125">Możesz zadać sobie pytanie: Jak zachowuje się ta metoda, jeśli przekażę jej pusty ciąg?</span><span class="sxs-lookup"><span data-stu-id="99ecc-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="99ecc-126">Null?</span><span class="sxs-lookup"><span data-stu-id="99ecc-126">Null?</span></span>

<span data-ttu-id="99ecc-127">Jeśli masz zestaw dobrze nazwanych testów jednostkowych, każdy test powinien być w stanie jasno wyjaśnić oczekiwane dane wyjściowe dla danego wejścia.</span><span class="sxs-lookup"><span data-stu-id="99ecc-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="99ecc-128">Ponadto powinien być w stanie sprawdzić, czy rzeczywiście działa.</span><span class="sxs-lookup"><span data-stu-id="99ecc-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="99ecc-129">Mniej sprzężeny kod</span><span class="sxs-lookup"><span data-stu-id="99ecc-129">Less coupled code</span></span>
<span data-ttu-id="99ecc-130">Gdy kod jest ściśle sprzężeny, może być trudne do testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="99ecc-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="99ecc-131">Bez tworzenia testów jednostkowych dla kodu, który piszesz, sprzężenia mogą być mniej widoczne.</span><span class="sxs-lookup"><span data-stu-id="99ecc-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="99ecc-132">Pisanie testów dla kodu będzie naturalnie oddzielić kod, ponieważ byłoby trudniejsze do przetestowania w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="99ecc-133">Charakterystyka dobrego testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="99ecc-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="99ecc-134">**Szybko**.</span><span class="sxs-lookup"><span data-stu-id="99ecc-134">**Fast**.</span></span> <span data-ttu-id="99ecc-135">Nie rzadko zdarza się, że dojrzałe projekty mają tysiące testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="99ecc-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="99ecc-136">Testy jednostkowe powinny zająć bardzo mało czasu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="99ecc-137">Milisekund.</span><span class="sxs-lookup"><span data-stu-id="99ecc-137">Milliseconds.</span></span>
- <span data-ttu-id="99ecc-138">**Izolowane**.</span><span class="sxs-lookup"><span data-stu-id="99ecc-138">**Isolated**.</span></span> <span data-ttu-id="99ecc-139">Testy jednostkowe są autonomiczne, można uruchomić w izolacji i nie mają zależności od czynników zewnętrznych, takich jak system plików lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="99ecc-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="99ecc-140">**Powtarzalne**.</span><span class="sxs-lookup"><span data-stu-id="99ecc-140">**Repeatable**.</span></span> <span data-ttu-id="99ecc-141">Uruchomienie testu jednostkowego powinno być zgodne z jego wynikami, oznacza to, że zawsze zwraca ten sam wynik, jeśli nie zmienisz niczego między przebiegami.</span><span class="sxs-lookup"><span data-stu-id="99ecc-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="99ecc-142">**Samokontrolowanie**.</span><span class="sxs-lookup"><span data-stu-id="99ecc-142">**Self-Checking**.</span></span> <span data-ttu-id="99ecc-143">Test powinien być w stanie automatycznie wykryć, czy przeszedł lub nie powiodło się bez interakcji człowieka.</span><span class="sxs-lookup"><span data-stu-id="99ecc-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="99ecc-144">**Terminowo**.</span><span class="sxs-lookup"><span data-stu-id="99ecc-144">**Timely**.</span></span> <span data-ttu-id="99ecc-145">Test jednostkowy nie powinien trwać nieproporcjonalnie długo, aby napisać w porównaniu do testowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="99ecc-146">Jeśli znajdziesz testowania kodu przy dużej ilości czasu w porównaniu do pisania kodu, należy wziąć pod uwagę projekt, który jest bardziej sprawdzalne.</span><span class="sxs-lookup"><span data-stu-id="99ecc-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="99ecc-147">Mówmy tym samym językiem</span><span class="sxs-lookup"><span data-stu-id="99ecc-147">Let's speak the same language</span></span>
<span data-ttu-id="99ecc-148">Termin *mock* jest niestety bardzo nadużywane, gdy mówimy o testach.</span><span class="sxs-lookup"><span data-stu-id="99ecc-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="99ecc-149">Następujące definiuje najczęstsze typy *podróbek* podczas pisania testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="99ecc-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="99ecc-150">*Fałszywe* — podróbka to ogólny termin, który może służyć do opisywania wycinka lub makiety obiektu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="99ecc-151">Czy jest to skrót lub makiety zależy od kontekstu, w którym jest używany.</span><span class="sxs-lookup"><span data-stu-id="99ecc-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="99ecc-152">Innymi słowy, fałszywy może być zalążek lub makiety.</span><span class="sxs-lookup"><span data-stu-id="99ecc-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="99ecc-153">*Makieta* — makieta obiektu jest fałszywy obiekt w systemie, który decyduje, czy test jednostkowy przeszedł lub nie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="99ecc-154">Makieta zaczyna się jako fake, dopóki nie zostanie dotwierdzona przeciwko.</span><span class="sxs-lookup"><span data-stu-id="99ecc-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="99ecc-155">*Stub* — skrótowy jest kontrolowanym zamiennikiem istniejącej zależności (lub współpracownika) w systemie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="99ecc-156">Za pomocą skrótu, można przetestować kod bez zajmowania się zależności bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="99ecc-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="99ecc-157">Domyślnie fałszywy zaczyna się jako skrót.</span><span class="sxs-lookup"><span data-stu-id="99ecc-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="99ecc-158">Należy wziąć pod uwagę następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="99ecc-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="99ecc-159">Byłby to przykład wycinka jest określany jako makieta.</span><span class="sxs-lookup"><span data-stu-id="99ecc-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="99ecc-160">W tym przypadku jest to wycinek.</span><span class="sxs-lookup"><span data-stu-id="99ecc-160">In this case, it is a stub.</span></span> <span data-ttu-id="99ecc-161">Właśnie przechodzisz w Zakonie jako środek, aby `Purchase` móc tworzyć wystąpienia (system w teście).</span><span class="sxs-lookup"><span data-stu-id="99ecc-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="99ecc-162">Nazwa `MockOrder` jest również bardzo mylące, ponieważ znowu, kolejność nie jest makieta.</span><span class="sxs-lookup"><span data-stu-id="99ecc-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="99ecc-163">Lepszym podejściem byłoby</span><span class="sxs-lookup"><span data-stu-id="99ecc-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="99ecc-164">Zmieniając nazwę klasy na `FakeOrder`, zrobiłeś klasy o wiele bardziej ogólne, klasa może służyć jako makiety lub wycinka.</span><span class="sxs-lookup"><span data-stu-id="99ecc-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="99ecc-165">W zależności od tego, co jest lepsze dla przypadku testowego.</span><span class="sxs-lookup"><span data-stu-id="99ecc-165">Whichever is better for the test case.</span></span> <span data-ttu-id="99ecc-166">W powyższym `FakeOrder` przykładzie jest używany jako wycinek.</span><span class="sxs-lookup"><span data-stu-id="99ecc-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="99ecc-167">Nie używasz `FakeOrder` w żadnym kształcie lub formie podczas asertywny.</span><span class="sxs-lookup"><span data-stu-id="99ecc-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="99ecc-168">`FakeOrder`właśnie został przekazany `Purchase` do klasy, aby spełnić wymagania konstruktora.</span><span class="sxs-lookup"><span data-stu-id="99ecc-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="99ecc-169">Aby użyć go jako makiety, można zrobić coś takiego</span><span class="sxs-lookup"><span data-stu-id="99ecc-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="99ecc-170">W takim przypadku sprawdzasz właściwość na Fake (twierdząc przeciwko niemu), więc w `mockOrder` powyższym fragmencie kodu, jest mock.</span><span class="sxs-lookup"><span data-stu-id="99ecc-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99ecc-171">Ważne jest, aby ta terminologia była poprawna.</span><span class="sxs-lookup"><span data-stu-id="99ecc-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="99ecc-172">Jeśli wywołasz wycinki "makiety", inni deweloperzy będą wprowadzać fałszywe założenia dotyczące intencji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="99ecc-173">Najważniejszą rzeczą do zapamiętania o makiety kontra wycinki jest to, że makiety są jak wycinki, ale twierdzą, przeciwko makiety obiektu, podczas gdy nie twierdzą przeciwko wycinka.</span><span class="sxs-lookup"><span data-stu-id="99ecc-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="99ecc-174">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="99ecc-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="99ecc-175">Nadawanie nazw testom</span><span class="sxs-lookup"><span data-stu-id="99ecc-175">Naming your tests</span></span>
<span data-ttu-id="99ecc-176">Nazwa testu powinna składać się z trzech części:</span><span class="sxs-lookup"><span data-stu-id="99ecc-176">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="99ecc-177">Nazwa testowanej metody.</span><span class="sxs-lookup"><span data-stu-id="99ecc-177">The name of the method being tested.</span></span>
- <span data-ttu-id="99ecc-178">Scenariusz, w którym jest testowany.</span><span class="sxs-lookup"><span data-stu-id="99ecc-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="99ecc-179">Oczekiwane zachowanie, gdy scenariusz jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="99ecc-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-180">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-180">Why?</span></span>

- <span data-ttu-id="99ecc-181">Standardy nazewnictwa są ważne, ponieważ jawnie wyrażają intencję testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="99ecc-182">Testy są czymś więcej niż tylko upewnienie się, że kod działa, ale również zawierają dokumentację.</span><span class="sxs-lookup"><span data-stu-id="99ecc-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="99ecc-183">Wystarczy spojrzeć na zestaw testów jednostkowych, powinieneś być w stanie wywnioskować zachowanie kodu, nawet nie patrząc na sam kod.</span><span class="sxs-lookup"><span data-stu-id="99ecc-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="99ecc-184">Ponadto po niepowodzeniu testów można zobaczyć dokładnie, które scenariusze nie spełniają twoich oczekiwań.</span><span class="sxs-lookup"><span data-stu-id="99ecc-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-185">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="99ecc-186">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="99ecc-187">Organizowanie testów</span><span class="sxs-lookup"><span data-stu-id="99ecc-187">Arranging your tests</span></span>
<span data-ttu-id="99ecc-188">**Rozmieść, Działaj, Potwierdzaj** jest typowym wzorcem podczas testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="99ecc-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="99ecc-189">Jak sama nazwa wskazuje, składa się z trzech głównych działań:</span><span class="sxs-lookup"><span data-stu-id="99ecc-189">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="99ecc-190">*Rozmieść* obiekty, tworząc je i konfigurując w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="99ecc-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="99ecc-191">*Działaj* na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-191">*Act* on an object.</span></span>
- <span data-ttu-id="99ecc-192">*Twierdzą,* że coś jest zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="99ecc-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-193">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-193">Why?</span></span>

- <span data-ttu-id="99ecc-194">Wyraźnie oddziela to, co jest testowane od *kroków aranżacji* *i potwierdzenia.*</span><span class="sxs-lookup"><span data-stu-id="99ecc-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="99ecc-195">Mniejsza szansa na połączenie twierdzeń z kodem "Act".</span><span class="sxs-lookup"><span data-stu-id="99ecc-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="99ecc-196">Czytelność jest jednym z najważniejszych aspektów podczas pisania testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="99ecc-197">Oddzielenie każdej z tych akcji w ramach testu wyraźnie wyróżnić zależności wymagane do wywołania kodu, jak kod jest wywoływany i co próbujesz potwierdzić.</span><span class="sxs-lookup"><span data-stu-id="99ecc-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="99ecc-198">Chociaż może być możliwe, aby połączyć niektóre kroki i zmniejszyć rozmiar testu, głównym celem jest, aby test tak czytelny, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="99ecc-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-199">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="99ecc-200">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="99ecc-201">Napisz minimalnie przechodzące testy</span><span class="sxs-lookup"><span data-stu-id="99ecc-201">Write minimally passing tests</span></span>
<span data-ttu-id="99ecc-202">Dane wejściowe, które mają być używane w teście jednostkowym powinny być najprostsze z możliwych w celu sprawdzenia zachowania, które są obecnie testujące.</span><span class="sxs-lookup"><span data-stu-id="99ecc-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-203">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-203">Why?</span></span>

- <span data-ttu-id="99ecc-204">Testy stają się bardziej odporne na przyszłe zmiany w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="99ecc-205">Bliżej do testowania zachowania nad implementacją.</span><span class="sxs-lookup"><span data-stu-id="99ecc-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="99ecc-206">Testy, które zawierają więcej informacji niż wymagane do zdaniu testu mają większe szanse na wprowadzenie błędów do testu i może sprawić, że intencja testu mniej jasne.</span><span class="sxs-lookup"><span data-stu-id="99ecc-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="99ecc-207">Podczas pisania testów chcesz skupić się na zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="99ecc-208">Ustawianie dodatkowych właściwości w modelach lub używanie wartości niezerowych, gdy nie jest to wymagane, tylko umniejsza to, co próbujesz udowodnić.</span><span class="sxs-lookup"><span data-stu-id="99ecc-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-209">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="99ecc-210">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="99ecc-211">Unikaj magicznych strun</span><span class="sxs-lookup"><span data-stu-id="99ecc-211">Avoid magic strings</span></span>
<span data-ttu-id="99ecc-212">Nazewnictwo zmiennych w testach jednostkowych jest równie ważne, jeśli nie ważniejsze, niż nazewnictwo zmiennych w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="99ecc-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="99ecc-213">Testy jednostkowe nie powinny zawierać magicznych ciągów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-214">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-214">Why?</span></span>

- <span data-ttu-id="99ecc-215">Zapobiega konieczności czytelnika testu do sprawdzenia kodu produkcji, aby dowiedzieć się, co sprawia, że wartość jest wyjątkowa.</span><span class="sxs-lookup"><span data-stu-id="99ecc-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="99ecc-216">Wyraźnie pokazuje, co próbujesz *udowodnić,* a nie *próbujesz osiągnąć*.</span><span class="sxs-lookup"><span data-stu-id="99ecc-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="99ecc-217">Magiczne struny mogą powodować zamieszanie dla czytelnika testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="99ecc-218">Jeśli ciąg wygląda nietypowe, mogą się zastanawiać, dlaczego pewna wartość została wybrana dla parametru lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="99ecc-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="99ecc-219">Może to prowadzić ich do bliższego przyjrzenia się szczegółom implementacji, a nie skupić się na teście.</span><span class="sxs-lookup"><span data-stu-id="99ecc-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="99ecc-220">Podczas pisania testów, należy dążyć do wyrażenia jak najwięcej intencji, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="99ecc-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="99ecc-221">W przypadku magicznych ciągów dobrym podejściem jest przypisywanie tych wartości do stałych.</span><span class="sxs-lookup"><span data-stu-id="99ecc-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-222">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="99ecc-223">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="99ecc-224">Unikaj logiki w testach</span><span class="sxs-lookup"><span data-stu-id="99ecc-224">Avoid logic in tests</span></span>
<span data-ttu-id="99ecc-225">Podczas pisania testów jednostkowych należy unikać ręcznego `if` `while`łączenia `for` `switch`ciągów i warunków logicznych, takich jak , , , , itp.</span><span class="sxs-lookup"><span data-stu-id="99ecc-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-226">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-226">Why?</span></span>

- <span data-ttu-id="99ecc-227">Mniejsza szansa na wprowadzenie błędu wewnątrz testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="99ecc-228">Skoncentruj się na wyniku końcowym, a nie na szczegółach implementacji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="99ecc-229">Po wprowadzeniu logiki do zestawu testów, szansa wprowadzenia błędu do niego znacznie wzrasta.</span><span class="sxs-lookup"><span data-stu-id="99ecc-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="99ecc-230">Ostatnie miejsce, w którym chcesz znaleźć błąd, znajduje się w pakiecie testowym.</span><span class="sxs-lookup"><span data-stu-id="99ecc-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="99ecc-231">Powinieneś mieć wysoki poziom pewności, że twoje testy działają, w przeciwnym razie nie będziesz im ufać.</span><span class="sxs-lookup"><span data-stu-id="99ecc-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="99ecc-232">Testy, którym nie ufasz, nie zapewniają żadnej wartości.</span><span class="sxs-lookup"><span data-stu-id="99ecc-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="99ecc-233">Gdy test nie powiedzie się, chcesz mieć poczucie, że coś jest rzeczywiście nie tak z kodem i że nie można go zignorować.</span><span class="sxs-lookup"><span data-stu-id="99ecc-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="99ecc-234">Jeśli logika w teście wydaje się nieunikniona, należy rozważyć podzielenie testu na dwa lub więcej różnych testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-235">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="99ecc-236">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="99ecc-237">Preferuj metody pomocnika do konfiguracji i rozdarcia</span><span class="sxs-lookup"><span data-stu-id="99ecc-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="99ecc-238">Jeśli potrzebujesz podobnego obiektu lub stanu dla testów, wolisz metodę pomocnika niż wykorzystanie atrybutów Setup i Teardown, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="99ecc-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-239">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-239">Why?</span></span>

- <span data-ttu-id="99ecc-240">Mniej zamieszania podczas czytania testów, ponieważ cały kod jest widoczny z poziomu każdego testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="99ecc-241">Mniejsze szanse na ustawienie zbyt dużo lub zbyt mało dla danego testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="99ecc-242">Mniejsza szansa na udostępnianie stanu między testami, który tworzy niepożądane zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="99ecc-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="99ecc-243">W ramach testowania `Setup` jednostkowego jest wywoływana przed każdym testem jednostkowym w pakiecie testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="99ecc-244">Podczas gdy niektórzy mogą zobaczyć to jako przydatne narzędzie, to zazwyczaj kończy się prowadzi do nadęty i trudne do odczytania testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="99ecc-245">Każdy test będzie zazwyczaj mieć różne wymagania w celu uruchomienia testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="99ecc-246">Niestety, `Setup` zmusza do korzystania z dokładnie tych samych wymagań dla każdego testu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="99ecc-247">xUnit usunął zarówno SetUp i TearDown w wersji 2.x</span><span class="sxs-lookup"><span data-stu-id="99ecc-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-248">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="99ecc-249">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="99ecc-250">Unikaj wielu twierdzeń</span><span class="sxs-lookup"><span data-stu-id="99ecc-250">Avoid multiple asserts</span></span>
<span data-ttu-id="99ecc-251">Podczas pisania testów, spróbuj dołączyć tylko jeden Assert na test.</span><span class="sxs-lookup"><span data-stu-id="99ecc-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="99ecc-252">Typowe podejścia do używania tylko jednego potwierdzenia obejmują:</span><span class="sxs-lookup"><span data-stu-id="99ecc-252">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="99ecc-253">Utwórz oddzielny test dla każdego potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="99ecc-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="99ecc-254">Użyj sparametryzowanych testów.</span><span class="sxs-lookup"><span data-stu-id="99ecc-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="99ecc-255">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="99ecc-255">Why?</span></span>

- <span data-ttu-id="99ecc-256">Jeśli jeden Assert nie powiedzie się, kolejne Asserts nie będą oceniane.</span><span class="sxs-lookup"><span data-stu-id="99ecc-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="99ecc-257">Zapewnia, że nie są potwierdzające wiele przypadków w testach.</span><span class="sxs-lookup"><span data-stu-id="99ecc-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="99ecc-258">Daje cały obraz, dlaczego testy nie powiodą się.</span><span class="sxs-lookup"><span data-stu-id="99ecc-258">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="99ecc-259">Podczas wprowadzania wielu potwierdza w przypadku testowym, nie jest gwarantowane, że wszystkie potwierdzenia zostaną wykonane.</span><span class="sxs-lookup"><span data-stu-id="99ecc-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="99ecc-260">W większości platform testowania jednostek, gdy potwierdzenie nie powiedzie się w teście jednostkowym, testy postępowania są automatycznie uważane za niepowiedzę.</span><span class="sxs-lookup"><span data-stu-id="99ecc-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="99ecc-261">Może to być mylące, ponieważ funkcja, która faktycznie działa, będzie wyświetlana jako nieudana.</span><span class="sxs-lookup"><span data-stu-id="99ecc-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="99ecc-262">Typowym wyjątkiem od tej reguły jest podczas powoływania się na obiekt.</span><span class="sxs-lookup"><span data-stu-id="99ecc-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="99ecc-263">W takim przypadku jest ogólnie dopuszczalne mieć wiele dotuje względem każdej właściwości, aby upewnić się, że obiekt jest w stanie, który oczekujesz, że w.</span><span class="sxs-lookup"><span data-stu-id="99ecc-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="99ecc-264">Źle:</span><span class="sxs-lookup"><span data-stu-id="99ecc-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="99ecc-265">Lepsze:</span><span class="sxs-lookup"><span data-stu-id="99ecc-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="99ecc-266">Sprawdzanie poprawności metod prywatnych według metod publicznych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="99ecc-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="99ecc-267">W większości przypadków nie powinno być potrzeby testowania metody prywatnej.</span><span class="sxs-lookup"><span data-stu-id="99ecc-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="99ecc-268">Metody prywatne są szczegółem implementacji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="99ecc-269">Można myśleć o tym w ten sposób: metody prywatne nigdy nie istnieją w izolacji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="99ecc-270">W pewnym momencie będzie metoda publiczna, która wywołuje metodę prywatną w ramach jej implementacji.</span><span class="sxs-lookup"><span data-stu-id="99ecc-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="99ecc-271">To, na czym należy dbać, to efekt końcowy metody publicznej, która wywołuje ją w sposób prywatny.</span><span class="sxs-lookup"><span data-stu-id="99ecc-271">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="99ecc-272">Rozważmy następujący przypadek</span><span class="sxs-lookup"><span data-stu-id="99ecc-272">Consider the following case</span></span>

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

<span data-ttu-id="99ecc-273">Pierwszą reakcją może być rozpoczęcie `TrimInput` pisania testu, ponieważ chcesz upewnić się, że metoda działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="99ecc-273">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="99ecc-274">Jednak jest całkowicie możliwe, `ParseLogLine` że `sanitizedInput` manipuluje w taki sposób, że `TrimInput` nie można oczekiwać, renderowania test przed bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="99ecc-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="99ecc-275">Prawdziwy test powinien być przeprowadzony przeciwko `ParseLogLine` metodzie publicznej, ponieważ to jest to, na czym ostatecznie powinieneś dbać.</span><span class="sxs-lookup"><span data-stu-id="99ecc-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="99ecc-276">Z tego punktu widzenia, jeśli widzisz metodę prywatną, znajdź metodę publiczną i napisz testy przeciwko tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="99ecc-277">Tylko dlatego, że metoda prywatna zwraca oczekiwany wynik, nie oznacza, że system, który ostatecznie wywołuje metodę prywatną używa wynik poprawnie.</span><span class="sxs-lookup"><span data-stu-id="99ecc-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="99ecc-278">Stub odniesienia statyczne</span><span class="sxs-lookup"><span data-stu-id="99ecc-278">Stub static references</span></span>
<span data-ttu-id="99ecc-279">Jedną z zasad badania jednostkowego jest to, że musi on mieć pełną kontrolę nad badanym systemem.</span><span class="sxs-lookup"><span data-stu-id="99ecc-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="99ecc-280">Może to być problematyczne, gdy kod produkcyjny zawiera `DateTime.Now`wywołania odwołań statycznych (np. ).</span><span class="sxs-lookup"><span data-stu-id="99ecc-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="99ecc-281">Należy wziąć pod uwagę następujący kod</span><span class="sxs-lookup"><span data-stu-id="99ecc-281">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="99ecc-282">Jak ten kod może być ewentualnie testowane jednostki?</span><span class="sxs-lookup"><span data-stu-id="99ecc-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="99ecc-283">Możesz spróbować takiego podejścia, jak</span><span class="sxs-lookup"><span data-stu-id="99ecc-283">You may try an approach such as</span></span>

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

<span data-ttu-id="99ecc-284">Niestety, szybko zdasz sobie sprawę, że istnieje kilka problemów z testami.</span><span class="sxs-lookup"><span data-stu-id="99ecc-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="99ecc-285">Jeśli zestaw testów zostanie uruchomiony we wtorek, drugi test zakończy się powodzeniem, ale pierwszy test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="99ecc-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="99ecc-286">Jeśli zestaw testów jest uruchamiany w dowolnym innym dniu, pierwszy test zakończy się powodzeniem, ale drugi test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="99ecc-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="99ecc-287">Aby rozwiązać te problemy, musisz wprowadzić *szew* do kodu produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="99ecc-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="99ecc-288">Jednym z podejść jest zawijanie kodu, który należy kontrolować w interfejsie i mieć kod produkcyjny zależy od tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="99ecc-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="99ecc-289">Twój zestaw testów stanie się teraz</span><span class="sxs-lookup"><span data-stu-id="99ecc-289">Your test suite now becomes</span></span>

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

<span data-ttu-id="99ecc-290">Teraz zestaw testów ma `DateTime.Now` pełną kontrolę nad i może wycinek dowolnej wartości podczas wywoływania do metody.</span><span class="sxs-lookup"><span data-stu-id="99ecc-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
