---
title: Testowanie ASP.NET podstawowych aplikacji MVC
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Testowanie ASP.NET podstawowych aplikacji MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2b347442c4a9b7b6cf912ec461248f901dc45417
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147494"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="9e10e-103">Testowanie ASP.NET podstawowych aplikacji MVC</span><span class="sxs-lookup"><span data-stu-id="9e10e-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="9e10e-104">*"Jeśli nie lubisz testować jednostkowych produktów, najprawdopodobniej twoi klienci nie będą chcieli go przetestować."*</span><span class="sxs-lookup"><span data-stu-id="9e10e-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="9e10e-105">\_- Anonimowe-</span><span class="sxs-lookup"><span data-stu-id="9e10e-105">\_- Anonymous-</span></span>

<span data-ttu-id="9e10e-106">Oprogramowanie o dowolnej złożoności może zakończyć się niespodziewanym powodzeniem w odpowiedzi na zmiany.</span><span class="sxs-lookup"><span data-stu-id="9e10e-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="9e10e-107">W związku z tym testowanie po dokonaniu zmian jest wymagane dla wszystkich, ale najbardziej trywialne (lub najmniej krytyczne) aplikacje.</span><span class="sxs-lookup"><span data-stu-id="9e10e-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="9e10e-108">Ręczne testowanie jest najwolniejszym, najmniej niezawodnym i najdroższym sposobem testowania oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="9e10e-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="9e10e-109">Niestety, jeśli aplikacje nie są przeznaczone do testowania, może to być jedyny dostępny środek.</span><span class="sxs-lookup"><span data-stu-id="9e10e-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="9e10e-110">Wnioski napisane zgodnie z zasadami architektury określonymi w [rozdziale 4](architectural-principles.md) powinny być sprawdzalne jednostkami.</span><span class="sxs-lookup"><span data-stu-id="9e10e-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="9e10e-111">ASP.NET Podstawowe aplikacje obsługują automatyczną integrację i testowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9e10e-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="9e10e-112">Rodzaje testów automatycznych</span><span class="sxs-lookup"><span data-stu-id="9e10e-112">Kinds of automated tests</span></span>

<span data-ttu-id="9e10e-113">Istnieje wiele rodzajów zautomatyzowanych testów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="9e10e-114">Najprostszym testem na najniższym poziomie jest test jednostkowy.</span><span class="sxs-lookup"><span data-stu-id="9e10e-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="9e10e-115">Na nieco wyższym poziomie istnieją testy integracyjne i testy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9e10e-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="9e10e-116">Inne rodzaje testów, takich jak testy interfejsu i uwyżenia, testy obciążenia, testy warunków skrajnych i testy dymu, wykraczają poza zakres tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="9e10e-117">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="9e10e-117">Unit tests</span></span>

<span data-ttu-id="9e10e-118">Test jednostkowy testuje pojedynczą część logiki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="9e10e-119">Można to dalej opisać, wymieniając niektóre rzeczy, które nie są.</span><span class="sxs-lookup"><span data-stu-id="9e10e-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="9e10e-120">Test jednostkowy nie testuje, jak kod działa z zależnościami lub infrastruktury — to, co testy integracji są dla.</span><span class="sxs-lookup"><span data-stu-id="9e10e-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="9e10e-121">Test jednostkowy nie testuje struktury, na której jest napisane kod — należy założyć, że działa lub, jeśli okaże się, że nie, zgłać błąd i kod obejść.</span><span class="sxs-lookup"><span data-stu-id="9e10e-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="9e10e-122">Test jednostkowy jest uruchamiany całkowicie w pamięci i w trakcie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="9e10e-123">Nie komunikuje się z systemem plików, siecią ani bazą danych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="9e10e-124">Testy jednostkowe należy przetestować tylko kod.</span><span class="sxs-lookup"><span data-stu-id="9e10e-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="9e10e-125">Testy jednostkowe, ze względu na fakt, że testują tylko jedną jednostkę kodu, bez zależności zewnętrznych, należy wykonać bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="9e10e-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="9e10e-126">W związku z tym powinno być możliwe uruchomienie zestawów testów setek testów jednostkowych w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="9e10e-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="9e10e-127">Uruchamiaj je często, najlepiej przed każdym wypychaniem do repozytorium kontroli źródła udostępnionego, a na pewno z każdą zautomatyzowaną kompilacją na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="9e10e-128">Testy integracji</span><span class="sxs-lookup"><span data-stu-id="9e10e-128">Integration tests</span></span>

<span data-ttu-id="9e10e-129">Chociaż jest to dobry pomysł, aby hermetyzować kod, który współdziała z infrastrukturą, takich jak bazy danych i systemy plików, nadal będziesz miał niektóre z tego kodu i prawdopodobnie będziesz chciał go przetestować.</span><span class="sxs-lookup"><span data-stu-id="9e10e-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="9e10e-130">Ponadto należy sprawdzić, czy warstwy kodu współdziałają zgodnie z oczekiwaniami, gdy zależności aplikacji są w pełni rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="9e10e-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="9e10e-131">Jest to odpowiedzialność testów integracji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="9e10e-132">Testy integracji są zwykle wolniejsze i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ często zależą od zależności zewnętrznych i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9e10e-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="9e10e-133">W związku z tym należy unikać testowania rzeczy, które mogą być testowane z testów jednostkowych w testach integracji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="9e10e-134">Jeśli można przetestować dany scenariusz z testu jednostkowego, należy przetestować go z testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="9e10e-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="9e10e-135">Jeśli nie możesz, rozważ użycie testu integracji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="9e10e-136">Testy integracji często mają bardziej złożone procedury konfiguracji i rozdarcia niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="9e10e-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="9e10e-137">Na przykład test integracji, który jest sprzeczny z rzeczywistą bazą danych będzie potrzebny sposób, aby przywrócić bazę danych do znanego stanu przed każdym uruchomieniu testu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="9e10e-138">Po dodaniu nowych testów i rozwoju schematu produkcyjnej bazy danych te skrypty testowe będą rosły w rozmiarze i złożoności.</span><span class="sxs-lookup"><span data-stu-id="9e10e-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="9e10e-139">W wielu dużych systemach jest niepraktyczne, aby uruchomić pełne pakiety testów integracji na stacjach roboczych deweloperów przed zaewidencjonowaniem zmian do współużytkowanej kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="9e10e-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="9e10e-140">W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="9e10e-141">Testy funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="9e10e-141">Functional tests</span></span>

<span data-ttu-id="9e10e-142">Testy integracji są zapisywane z perspektywy dewelopera, aby sprawdzić, czy niektóre składniki systemu działają poprawnie razem.</span><span class="sxs-lookup"><span data-stu-id="9e10e-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="9e10e-143">Testy funkcjonalne są zapisywane z perspektywy użytkownika i sprawdzić poprawność systemu w oparciu o jego wymagania.</span><span class="sxs-lookup"><span data-stu-id="9e10e-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="9e10e-144">Poniższy fragment oferuje użyteczną analogię do myślenia o testach funkcjonalnych, w porównaniu do testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="9e10e-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="9e10e-145">"Wiele razy rozwój systemu jest porównywany do budowy domu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="9e10e-146">Chociaż ta analogia nie jest całkiem poprawna, możemy ją rozszerzyć w celu zrozumienia różnicy między testami jednostkowymi i funkcjonalnymi.</span><span class="sxs-lookup"><span data-stu-id="9e10e-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="9e10e-147">Testowanie jednostkowe jest analogiczne do inspektora budowlanego odwiedzającego plac budowy domu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="9e10e-148">Koncentruje się na różnych systemach wewnętrznych domu, fundacji, kadrowania, instalacji elektrycznej, kanalizacji i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9e10e-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="9e10e-149">Zapewnia (testy), że części domu będą działać poprawnie i bezpiecznie, czyli spełniają kodeks budowlany.</span><span class="sxs-lookup"><span data-stu-id="9e10e-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="9e10e-150">Testy funkcjonalne w tym scenariuszu są analogiczne do właściciela domu odwiedzającego ten sam plac budowy.</span><span class="sxs-lookup"><span data-stu-id="9e10e-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="9e10e-151">Zakłada on, że systemy wewnętrzne będą zachowywać się odpowiednio, że inspektor budowlany wykonuje swoje zadanie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="9e10e-152">Właściciel domu koncentruje się na tym, jak to będzie mieszkać w tym domu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="9e10e-153">Jest zaniepokojony tym, jak wygląda dom, czy różne pokoje są wygodne, czy dom pasuje do potrzeb rodziny, są okna mieszczanami w dobrym miejscu, aby złapać poranne słońce.</span><span class="sxs-lookup"><span data-stu-id="9e10e-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="9e10e-154">Właściciel domu wykonuje testy funkcjonalne w domu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="9e10e-155">Ma perspektywę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e10e-155">He has the user's perspective.</span></span> <span data-ttu-id="9e10e-156">Inspektor budowlany przeprowadza testy jednostkowe w domu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="9e10e-157">Ma perspektywę budowniczego."</span><span class="sxs-lookup"><span data-stu-id="9e10e-157">He has the builder's perspective."</span></span>

<span data-ttu-id="9e10e-158">Źródło: [Testowanie jednostkowe a testy funkcjonalne](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="9e10e-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="9e10e-159">Lubię mówić: "Jako deweloperzy zawodzimy na dwa sposoby: budujemy coś złego, albo budujemy coś złego".</span><span class="sxs-lookup"><span data-stu-id="9e10e-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="9e10e-160">Testy jednostkowe zapewniają, że budujesz to, co właściwe; testy funkcjonalne zapewniają, że budujesz to, co właściwe.</span><span class="sxs-lookup"><span data-stu-id="9e10e-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="9e10e-161">Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewnego stopnia automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e10e-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="9e10e-162">Podobnie jak testy integracji, zwykle działają one z jakąś infrastrukturą testową.</span><span class="sxs-lookup"><span data-stu-id="9e10e-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="9e10e-163">To sprawia, że są wolniejsze i bardziej kruche niż testy jednostkowe i integracyjne.</span><span class="sxs-lookup"><span data-stu-id="9e10e-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="9e10e-164">Należy mieć tylko tyle testów funkcjonalnych, ile trzeba mieć pewność, że system zachowuje się tak, jak oczekują użytkownicy.</span><span class="sxs-lookup"><span data-stu-id="9e10e-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="9e10e-165">Piramida testowania</span><span class="sxs-lookup"><span data-stu-id="9e10e-165">Testing Pyramid</span></span>

<span data-ttu-id="9e10e-166">Martin Fowler napisał o piramidzie testowej, której przykład przedstawiono na rysunku 9-1.</span><span class="sxs-lookup"><span data-stu-id="9e10e-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Piramida testowania](./media/image9-1.png)

<span data-ttu-id="9e10e-168">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="9e10e-168">**Figure 9-1**.</span></span> <span data-ttu-id="9e10e-169">Piramida testowania</span><span class="sxs-lookup"><span data-stu-id="9e10e-169">Testing Pyramid</span></span>

<span data-ttu-id="9e10e-170">Różne warstwy piramidy i ich względne rozmiary reprezentują różne rodzaje testów i liczbę pisanych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="9e10e-171">Jak widać, zaleca się mieć dużą bazę testów jednostkowych, wspieranych przez mniejszą warstwę testów integracyjnych, z jeszcze mniejszą warstwą testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="9e10e-172">Każda warstwa powinna mieć tylko testy, których nie można wykonać odpowiednio w niższej warstwie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="9e10e-173">Pamiętaj o piramidzie testowej, gdy próbujesz zdecydować, jakiego rodzaju testu potrzebujesz dla określonego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9e10e-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="9e10e-174">Co przetestować</span><span class="sxs-lookup"><span data-stu-id="9e10e-174">What to test</span></span>

<span data-ttu-id="9e10e-175">Częstym problemem dla deweloperów, którzy są niedoświadczeni w pisaniu zautomatyzowanych testów jest wymyślanie, co do testowania.</span><span class="sxs-lookup"><span data-stu-id="9e10e-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="9e10e-176">Dobrym punktem wyjścia jest przetestowanie logiki warunkowej.</span><span class="sxs-lookup"><span data-stu-id="9e10e-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="9e10e-177">Wszędzie tam, gdzie masz metodę z zachowaniem, które zmienia się na podstawie instrukcji warunkowej (if-else, switch itd.), powinieneś być w stanie wymyślić co najmniej kilka testów, które potwierdzają prawidłowe zachowanie dla niektórych warunków.</span><span class="sxs-lookup"><span data-stu-id="9e10e-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="9e10e-178">Jeśli kod ma warunki błędu, dobrze jest napisać co najmniej jeden test dla "szczęśliwej ścieżki" za pomocą kodu (bez błędów) i co najmniej jeden test dla "smutnej ścieżki" (z błędami lub nietypowymi wynikami), aby potwierdzić, że aplikacja zachowuje się zgodnie z oczekiwaniami w obliczu błędów.</span><span class="sxs-lookup"><span data-stu-id="9e10e-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="9e10e-179">Na koniec spróbuj skupić się na testowaniu rzeczy, które mogą się nie powieść, zamiast skupiać się na metrykach, takich jak pokrycie kodu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="9e10e-180">Więcej pokrycia kodu jest lepszy niż mniej, ogólnie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="9e10e-181">Jednak pisanie kilku testów złożonych i biznesowych metody krytyczne jest zwykle lepsze wykorzystanie czasu niż pisanie testów dla właściwości automatycznych tylko w celu poprawy metryki pokrycia kodu testu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="9e10e-182">Organizowanie projektów testowych</span><span class="sxs-lookup"><span data-stu-id="9e10e-182">Organizing test projects</span></span>

<span data-ttu-id="9e10e-183">Projekty testowe mogą być zorganizowane, jednak najlepiej dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="9e10e-184">Dobrym pomysłem jest oddzielenie testów według typu (test jednostkowy, test integracji) i według tego, co testują (według projektu, według przestrzeni nazw).</span><span class="sxs-lookup"><span data-stu-id="9e10e-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="9e10e-185">Czy to rozdzielenie składa się z folderów w ramach jednego projektu testowego lub wielu projektów testowych, jest decyzja projektowa.</span><span class="sxs-lookup"><span data-stu-id="9e10e-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="9e10e-186">Jeden projekt jest najprostszy, ale dla dużych projektów z wieloma testami lub w celu łatwiejszego uruchamiania różnych zestawów testów, możesz chcieć mieć kilka różnych projektów testowych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="9e10e-187">Wiele zespołów organizuje projekty testowe na podstawie projektu, który testują, co dla aplikacji z więcej niż kilkoma projektami może spowodować dużą liczbę projektów testowych, zwłaszcza jeśli nadal je rozbić zgodnie z rodzajem testów w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="9e10e-188">Podejście kompromisowe jest mieć jeden projekt na rodzaj testu, na aplikację, z folderów wewnątrz projektów testowych, aby wskazać projektu (i klasy) testowane.</span><span class="sxs-lookup"><span data-stu-id="9e10e-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="9e10e-189">Typowym podejściem jest organizowanie projektów aplikacji w folderze "src" i projektów testowych aplikacji w równoległym folderze "testy".</span><span class="sxs-lookup"><span data-stu-id="9e10e-189">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="9e10e-190">W programie Visual Studio można utworzyć pasujące foldery rozwiązań, jeśli ta organizacja okaże się przydatna.</span><span class="sxs-lookup"><span data-stu-id="9e10e-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Testowanie organizacji w rozwiązaniu](./media/image9-2.png)

<span data-ttu-id="9e10e-192">**Rysunek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="9e10e-192">**Figure 9-2**.</span></span> <span data-ttu-id="9e10e-193">Testowanie organizacji w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="9e10e-193">Test organization in your solution</span></span>

<span data-ttu-id="9e10e-194">Można użyć struktury testowej, która wolisz.</span><span class="sxs-lookup"><span data-stu-id="9e10e-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="9e10e-195">Struktura xUnit działa dobrze i jest to, co wszystkie testy ASP.NET Core i EF Core są zapisywane w.</span><span class="sxs-lookup"><span data-stu-id="9e10e-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="9e10e-196">Projekt testu xUnit można dodać w programie Visual Studio przy użyciu szablonu pokazanego na rysunku 9-3 lub z identyfikatora cli przy użyciu . `dotnet new xunit`</span><span class="sxs-lookup"><span data-stu-id="9e10e-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Dodawanie projektu testu xUnit w programie Visual Studio](./media/image9-3.png)

<span data-ttu-id="9e10e-198">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="9e10e-198">**Figure 9-3**.</span></span> <span data-ttu-id="9e10e-199">Dodawanie projektu testu xUnit w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e10e-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="9e10e-200">Testowanie nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="9e10e-200">Test naming</span></span>

<span data-ttu-id="9e10e-201">Nazwij testy w spójny sposób, z nazwami, które wskazują, co robi każdy test.</span><span class="sxs-lookup"><span data-stu-id="9e10e-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="9e10e-202">Jednym z podejść miałem wielki sukces z jest nazwa klas testowych zgodnie z klasą i metodą, którą testują.</span><span class="sxs-lookup"><span data-stu-id="9e10e-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="9e10e-203">Powoduje to wiele małych klas testowych, ale to sprawia, że bardzo jasne, co każdy test jest odpowiedzialny za.</span><span class="sxs-lookup"><span data-stu-id="9e10e-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="9e10e-204">Z nazwą klasy testowej skonfigurowanej do identyfikowania klasy i metody, które mają być testowane, nazwa metody testowej może służyć do określenia badanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="9e10e-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="9e10e-205">Powinno to obejmować oczekiwane zachowanie i wszelkie dane wejściowe lub założenia, które powinny przynieść to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9e10e-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="9e10e-206">Niektóre przykładowe nazwy testów:</span><span class="sxs-lookup"><span data-stu-id="9e10e-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="9e10e-207">Odmiana tego podejścia kończy każdą nazwę klasy testowej na "Powinien" i nieznacznie modyfikuje czas:</span><span class="sxs-lookup"><span data-stu-id="9e10e-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="9e10e-208">`CatalogControllerGetImage`**Należy**`.`**zadzwonić**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="9e10e-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="9e10e-209">`CatalogControllerGetImage`**Czy**`.`**zaloguj się**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="9e10e-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="9e10e-210">Niektóre zespoły uważają, że drugie podejście do nazewnictwa jest jaśniejsze, choć nieco bardziej szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="9e10e-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="9e10e-211">W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testu, tak aby po niepowodzeniu jednego lub więcej testów, jest oczywiste, z ich nazw, jakie przypadki nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="9e10e-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="9e10e-212">Należy unikać nazewnictwa testów niejasno, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy widzisz je w wynikach testów.</span><span class="sxs-lookup"><span data-stu-id="9e10e-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="9e10e-213">Jeśli postępuj zgodnie z konwencją nazewnictwa, taką jak powyższa, która tworzy wiele małych klas testowych, dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9e10e-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="9e10e-214">Rysunek 9-4 przedstawia jedno podejście do organizowania testów według folderu w ramach kilku projektów testowych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Organizowanie klas testowych według folderu na podstawie testowanej klasy](./media/image9-4.png)

<span data-ttu-id="9e10e-216">**Rysunek 9-4.**</span><span class="sxs-lookup"><span data-stu-id="9e10e-216">**Figure 9-4.**</span></span> <span data-ttu-id="9e10e-217">Organizowanie klas testowych według folderu na podstawie testowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="9e10e-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="9e10e-218">Jeśli określonej klasy aplikacji ma wiele metod testowanych (a tym samym wiele klas testowych), może mieć sens umieszczenie ich w folderze odpowiadającym klasie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="9e10e-219">Ta organizacja nie różni się od sposobu organizowania plików w folderach w innych miejscach.</span><span class="sxs-lookup"><span data-stu-id="9e10e-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="9e10e-220">Jeśli masz więcej niż trzy lub cztery powiązane pliki w folderze zawierającym wiele innych plików, często warto przenieść je do własnego podfolderu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="9e10e-221">Testowanie jednostek ASP.NET aplikacje Core</span><span class="sxs-lookup"><span data-stu-id="9e10e-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="9e10e-222">W dobrze zaprojektowanej aplikacji ASP.NET Core większość złożoności i logiki biznesowej będzie hermetyzowana w jednostkach biznesowych i różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="9e10e-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="9e10e-223">Sama aplikacja ASP.NET Core MVC, z kontrolerami, filtrami, modelami widoków i widokami, powinna wymagać bardzo niewielu testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="9e10e-224">Duża część funkcjonalności danej akcji znajduje się poza samą metodą akcji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="9e10e-225">Sprawdzanie, czy routing działa poprawnie, czy globalna obsługa błędów, nie może być wykonana skutecznie za pomocą testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="9e10e-225">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="9e10e-226">Podobnie wszystkie filtry, w tym sprawdzanie poprawności modelu i uwierzytelniania i uwierzytelniania i autoryzacji filtrów, nie może być testowany jednostką z testem kierowania na metodę akcji kontrolera.</span><span class="sxs-lookup"><span data-stu-id="9e10e-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="9e10e-227">Bez tych źródeł zachowania większość metod akcji powinna być trywialnie mała, delegując większość ich pracy do usług, które mogą być testowane niezależnie od kontrolera, który ich używa.</span><span class="sxs-lookup"><span data-stu-id="9e10e-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="9e10e-228">Czasami trzeba będzie refaktoryzacji kodu w celu przetestowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="9e10e-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="9e10e-229">Często wiąże się to z identyfikowaniem abstrakcji i przy użyciu iniekcji zależności, aby uzyskać dostęp do abstrakcji w kodzie, który chcesz przetestować, zamiast kodowania bezpośrednio przeciwko infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="9e10e-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="9e10e-230">Rozważmy na przykład tę prostą metodę działania do wyświetlania obrazów:</span><span class="sxs-lookup"><span data-stu-id="9e10e-230">For example, consider this simple action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="9e10e-231">Testowanie jednostkowe tej metody jest utrudnione przez jej bezpośrednią zależność `System.IO.File`od , którego używa do odczytu z systemu plików.</span><span class="sxs-lookup"><span data-stu-id="9e10e-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="9e10e-232">Można przetestować to zachowanie, aby upewnić się, że działa zgodnie z oczekiwaniami, ale robi to z prawdziwymi plikami jest test integracji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="9e10e-233">Warto zauważyć, że nie można przetestować jednostkowo tej metody trasy - zobaczysz, jak to zrobić z testem funkcjonalnym wkrótce.</span><span class="sxs-lookup"><span data-stu-id="9e10e-233">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="9e10e-234">Jeśli nie można przetestować jednostkowe zachowanie systemu plików bezpośrednio i nie można przetestować trasę, co jest do przetestowania?</span><span class="sxs-lookup"><span data-stu-id="9e10e-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="9e10e-235">Cóż, po refaktoryzacji, aby umożliwić testowanie jednostek, może odkryć niektóre przypadki testowe i brakujące zachowanie, takie jak obsługa błędów.</span><span class="sxs-lookup"><span data-stu-id="9e10e-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="9e10e-236">Co robi metoda, gdy plik nie zostanie znaleziony?</span><span class="sxs-lookup"><span data-stu-id="9e10e-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="9e10e-237">Co powinien zrobić?</span><span class="sxs-lookup"><span data-stu-id="9e10e-237">What should it do?</span></span> <span data-ttu-id="9e10e-238">W tym przykładzie metoda refaktoryzowana wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="9e10e-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="9e10e-239">`_logger`i `_imageService` są wstrzykiwane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="9e10e-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="9e10e-240">Teraz można przetestować, że ten sam identyfikator, który `_imageService`jest przekazywany do metody akcji jest przekazywana do , i że wynikowe bajty są zwracane jako część FileResult.</span><span class="sxs-lookup"><span data-stu-id="9e10e-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="9e10e-241">Można również przetestować, że rejestrowanie błędów `NotFound` dzieje się zgodnie z oczekiwaniami i że wynik jest zwracany, jeśli brakuje obrazu, zakładając, że jest to ważne zachowanie aplikacji (to jest nie tylko tymczasowy kod deweloper aplikowany do diagnozowania problemu).</span><span class="sxs-lookup"><span data-stu-id="9e10e-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="9e10e-242">Logika rzeczywistego pliku została przeniesiona do oddzielnej usługi implementacji i została rozszerzona w celu zwrócenia wyjątku specyficznego dla aplikacji w przypadku brakującego pliku.</span><span class="sxs-lookup"><span data-stu-id="9e10e-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="9e10e-243">Można przetestować tę implementację niezależnie, przy użyciu testu integracji.</span><span class="sxs-lookup"><span data-stu-id="9e10e-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="9e10e-244">W większości przypadków należy użyć globalnych programów obsługi wyjątków w kontrolerach, więc ilość logiki w nich powinna być minimalna i prawdopodobnie nie warto testować jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="9e10e-244">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="9e10e-245">Należy wykonać większość testowania akcji kontrolera przy `TestServer` użyciu testów funkcjonalnych i klasy opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="9e10e-245">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="9e10e-246">Testowanie integracji ASP.NET aplikacje Core</span><span class="sxs-lookup"><span data-stu-id="9e10e-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="9e10e-247">Większość testów integracji w ASP.NET podstawowych aplikacji powinny być testowanie usług i innych typów implementacji zdefiniowanych w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9e10e-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="9e10e-248">Na przykład można [przetestować, że EF Core pomyślnie aktualizowanie i pobieranie danych, które można oczekiwać](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od klas dostępu do danych znajdujących się w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9e10e-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="9e10e-249">Najlepszym sposobem, aby sprawdzić, czy ASP.NET Core MVC projektu zachowuje się poprawnie jest z testów funkcjonalnych, które są uruchamiane przeciwko aplikacji uruchomionej na hoście testowym.</span><span class="sxs-lookup"><span data-stu-id="9e10e-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="9e10e-250">Testowanie funkcjonalne ASP.NET aplikacje Core</span><span class="sxs-lookup"><span data-stu-id="9e10e-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="9e10e-251">W przypadku ASP.NET `TestServer` podstawowych aplikacji klasa sprawia, że testy funkcjonalne są dość łatwe do napisania.</span><span class="sxs-lookup"><span data-stu-id="9e10e-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="9e10e-252">Można skonfigurować `TestServer` przy `WebHostBuilder` użyciu `HostBuilder`(lub ) bezpośrednio (jak zwykle w `WebApplicationFactory` przypadku aplikacji) lub z typem (dostępne od wersji 2.1).</span><span class="sxs-lookup"><span data-stu-id="9e10e-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="9e10e-253">Należy spróbować dopasować hosta testowego do hosta produkcyjnego tak ściśle, jak to możliwe, więc testy będą wykonywać zachowanie podobne do tego, co aplikacja zrobi w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="9e10e-253">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="9e10e-254">Klasa `WebApplicationFactory` jest pomocna przy konfigurowaniu contentroot a testservera, który jest używany przez ASP.NET Core do lokalizowania zasobów statycznych, takich jak Widoki.</span><span class="sxs-lookup"><span data-stu-id="9e10e-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="9e10e-255">Proste testy funkcjonalne można utworzyć, tworząc klasę testową, która implementuje IClassFixture\<WebApplicationFactory\<TEntry>> , gdzie TEntry jest klasy startowej aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="9e10e-255">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="9e10e-256">Z tym w miejscu, urządzenie testowe można utworzyć klienta przy użyciu metody CreateClient fabryki:</span><span class="sxs-lookup"><span data-stu-id="9e10e-256">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="9e10e-257">Często należy wykonać dodatkową konfigurację witryny przed każdym uruchomieniu testu, takich jak konfigurowanie aplikacji do korzystania z magazynu danych w pamięci, a następnie rozmieszania aplikacji z danymi testowymi.</span><span class="sxs-lookup"><span data-stu-id="9e10e-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="9e10e-258">Aby to zrobić, należy utworzyć własną podklasę WebApplicationFactory\<TEntry> i zastąpić jego ConfigureWebHost metody.</span><span class="sxs-lookup"><span data-stu-id="9e10e-258">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="9e10e-259">Poniższy przykład pochodzi z projektu eShopOnWeb FunctionalTests i jest używany jako część testów w głównej aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="9e10e-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="9e10e-260">Testy można użyć tego niestandardowego WebApplicationFactory przy użyciu go do tworzenia klienta, a następnie wykonywanie żądań do aplikacji przy użyciu tego wystąpienia klienta.</span><span class="sxs-lookup"><span data-stu-id="9e10e-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="9e10e-261">Aplikacja będzie miała dane seeded, które mogą być używane jako część testu potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="9e10e-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="9e10e-262">Poniższy test sprawdza, czy strona główna aplikacji eShopOnWeb ładuje się poprawnie i zawiera listę produktów, która została dodana do aplikacji jako część danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9e10e-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="9e10e-263">Ten funkcjonalny test wykonuje pełną ASP.NET Stos aplikacji Core MVC / Razor Pages, w tym wszystkie pośredniczenie, filtry, segregatory itp., które mogą być na miejscu.</span><span class="sxs-lookup"><span data-stu-id="9e10e-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="9e10e-264">Sprawdza, czy dana trasa ("/") zwraca oczekiwany kod stanu sukcesu i dane wyjściowe HTML.</span><span class="sxs-lookup"><span data-stu-id="9e10e-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="9e10e-265">Czyni to bez konfigurowania prawdziwego serwera www, a więc pozwala uniknąć wiele kruchości, że przy użyciu prawdziwego serwera www do testowania może wystąpić (na przykład problemy z ustawieniami zapory).</span><span class="sxs-lookup"><span data-stu-id="9e10e-265">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="9e10e-266">Testy funkcjonalne, które są uruchamiane przeciwko TestServer są zwykle wolniejsze niż testy integracyjne i jednostkowe, ale są znacznie szybsze niż testy, które można uruchomić za pośrednictwem sieci do serwera sieci web test.</span><span class="sxs-lookup"><span data-stu-id="9e10e-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="9e10e-267">Należy użyć testów funkcjonalnych, aby upewnić się, że stos frontonu aplikacji działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9e10e-267">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="9e10e-268">Testy te są szczególnie przydatne, gdy znajdziesz duplikacji w kontrolerach lub stron i adres powielania przez dodanie filtrów.</span><span class="sxs-lookup"><span data-stu-id="9e10e-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="9e10e-269">W idealnym przypadku to refaktoryzacji nie zmieni zachowanie aplikacji i zestaw testów funkcjonalnych zweryfikuje to jest przypadek.</span><span class="sxs-lookup"><span data-stu-id="9e10e-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="9e10e-270">Referencje — testowanie ASP.NET aplikacje Core MVC</span><span class="sxs-lookup"><span data-stu-id="9e10e-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="9e10e-271">**Testowanie w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="9e10e-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="9e10e-272">**Konwencja nazewnictwa testu jednostkowego** </span><span class="sxs-lookup"><span data-stu-id="9e10e-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="9e10e-273">**Testowanie rdzenia EF** </span><span class="sxs-lookup"><span data-stu-id="9e10e-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="9e10e-274">**Testy integracji w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="9e10e-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="9e10e-275">[Poprzedni](work-with-data-in-asp-net-core-apps.md)
>[następny](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="9e10e-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
