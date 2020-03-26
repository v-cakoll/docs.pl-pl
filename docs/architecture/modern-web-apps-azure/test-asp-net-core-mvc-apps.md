---
title: Testowanie aplikacji Core MVC ASP.NET
description: Architekt nowoczesnych aplikacji sieci Web z ASP.NET Core i Azure | Testowanie ASP.NET podstawowych aplikacji MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: fa87fdba830398786cce8951d353e86bc4ff7491
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111052"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="bb4fe-103">Testowanie aplikacji Core MVC ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bb4fe-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="bb4fe-104">*"Jeśli nie lubisz testować produktu w jednostce, najprawdopodobniej twoi klienci również nie będą chcieli go przetestować".*</span><span class="sxs-lookup"><span data-stu-id="bb4fe-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="bb4fe-105">\_- Anonimowy-</span><span class="sxs-lookup"><span data-stu-id="bb4fe-105">\_- Anonymous-</span></span>

<span data-ttu-id="bb4fe-106">Oprogramowanie o dowolnej złożoności może zakończyć się niepowodzeniem w nieoczekiwany sposób w odpowiedzi na zmiany.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="bb4fe-107">W związku z tym testowanie po wszczęciem zmian jest wymagane dla wszystkich, ale najbardziej trywialne (lub najmniej krytyczne) aplikacje.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="bb4fe-108">Ręczne testowanie jest najwolniejszym, najmniej niezawodnym i najdroższym sposobem testowania oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="bb4fe-109">Niestety, jeśli aplikacje nie są zaprojektowane do testowania, może to być jedyny dostępny środek.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="bb4fe-110">Wnioski napisane zgodnie z zasadami architektonicznymi określonymi w [rozdziale 4](architectural-principles.md) powinny być sprawdzalne w jednostkach.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="bb4fe-111">ASP.NET Aplikacje Core obsługują zautomatyzowaną integrację i testowanie funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="bb4fe-112">Rodzaje zautomatyzowanych testów</span><span class="sxs-lookup"><span data-stu-id="bb4fe-112">Kinds of automated tests</span></span>

<span data-ttu-id="bb4fe-113">Istnieje wiele rodzajów zautomatyzowanych testów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="bb4fe-114">Najprostszym testem najniższego poziomu jest test jednostkowy.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="bb4fe-115">Na nieco wyższym poziomie, istnieją testy integracji i testy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="bb4fe-116">Inne rodzaje testów, takich jak testy interfejsu użytkownika, testy obciążenia, testy warunków skrajnych i testy dymu, wykraczają poza zakres tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="bb4fe-117">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="bb4fe-117">Unit tests</span></span>

<span data-ttu-id="bb4fe-118">Test jednostkowy testuje pojedynczą część logiki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="bb4fe-119">Można go dalej opisać, wymieniając niektóre rzeczy, które nie są.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="bb4fe-120">Test jednostkowy nie testuje, jak kod działa z zależnościami lub infrastrukturą — do czego służą testy integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="bb4fe-121">Test jednostkowy nie testuje struktury, na której jest napisany kod — należy założyć, że działa lub, jeśli okaże się, że nie, złóż błąd i kod obejście problemu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="bb4fe-122">Test jednostkowy jest uruchamiany całkowicie w pamięci i w trakcie procesu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="bb4fe-123">Nie komunikuje się z systemem plików, siecią ani bazą danych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="bb4fe-124">Testy jednostkowe należy tylko przetestować kod.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="bb4fe-125">Testy jednostkowe, ze względu na fakt, że testują tylko jedną jednostkę kodu, bez zależności zewnętrznych, należy wykonać bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="bb4fe-126">W związku z tym powinieneś być w stanie uruchomić zestawy testów setek testów jednostkowych w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="bb4fe-127">Uruchamiaj je często, najlepiej przed każdym wypychaniem do repozytorium kontroli źródła udostępnionego, a na pewno przy każdej zautomatyzowanej kompilacji na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="bb4fe-128">Testy integracji</span><span class="sxs-lookup"><span data-stu-id="bb4fe-128">Integration tests</span></span>

<span data-ttu-id="bb4fe-129">Chociaż jest to dobry pomysł, aby hermetyzować kod, który współdziała z infrastruktury, takich jak bazy danych i systemy plików, nadal będzie mieć niektóre z tego kodu i prawdopodobnie będzie chcesz go przetestować.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="bb4fe-130">Ponadto należy sprawdzić, czy warstwy kodu współdziałają zgodnie z oczekiwaniami, gdy zależności aplikacji zostaną w pełni rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="bb4fe-131">Jest to odpowiedzialność za testy integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="bb4fe-132">Testy integracji wydają się być wolniejsze i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ często zależą od zależności zewnętrznych i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="bb4fe-133">W związku z tym należy unikać testowania rzeczy, które mogą być testowane za pomocą testów jednostkowych w testach integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="bb4fe-134">Jeśli można przetestować dany scenariusz z testu jednostkowego, należy przetestować go za pomocą testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="bb4fe-135">Jeśli nie możesz, rozważ użycie testu integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="bb4fe-136">Testy integracji często mają bardziej złożone procedury konfiguracji i usuwania niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="bb4fe-137">Na przykład test integracji, który jest sprzeczny z rzeczywistą bazą danych, będzie potrzebował sposobu zwrócenia bazy danych do znanego stanu przed każdym uruchomieniem testu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="bb4fe-138">W miarę dodawania nowych testów i ewoluuje schemat produkcyjnej bazy danych, te skrypty testowe będą miały tendencję do zwiększania rozmiaru i złożoności.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="bb4fe-139">W wielu dużych systemach jest niepraktyczne, aby uruchomić pełne zestawy testów integracji na stacjach roboczych deweloperów przed sprawdzeniem zmian w kontroli źródła udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="bb4fe-140">W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="bb4fe-141">Testy funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="bb4fe-141">Functional tests</span></span>

<span data-ttu-id="bb4fe-142">Testy integracji są zapisywane z punktu widzenia dewelopera, aby sprawdzić, czy niektóre składniki systemu działają poprawnie razem.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="bb4fe-143">Testy funkcjonalne są zapisywane z perspektywy użytkownika i weryfikują poprawność systemu na podstawie jego wymagań.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="bb4fe-144">Poniższy fragment zawiera użyteczną analogię do myślenia o testach funkcjonalnych w porównaniu z testami jednostkowymi:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="bb4fe-145">"Wiele razy rozwój systemu jest porównywany do budowy domu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="bb4fe-146">Chociaż ta analogia nie jest całkiem poprawna, możemy rozszerzyć ją w celu zrozumienia różnicy między testami jednostkowymi a funkcjonalnymi.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="bb4fe-147">Testy jednostkowe są analogiczne do wizyty inspektora budowlanego na placu budowy domu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="bb4fe-148">Koncentruje się na różnych wewnętrznych systemach domu, fundament, kadrowanie, elektryczne, instalacyjne i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="bb4fe-149">Zapewnia (testy), że części domu będą działać poprawnie i bezpiecznie, czyli spełniają kodeks budowlany.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="bb4fe-150">Testy funkcjonalne w tym scenariuszu są analogiczne do właściciela domu odwiedzającego ten sam plac budowy.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="bb4fe-151">Zakłada on, że systemy wewnętrzne będą zachowywać się odpowiednio, że inspektor budowlany wykonuje swoje zadanie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="bb4fe-152">Właściciel domu koncentruje się na tym, jak to będzie żyć w tym domu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="bb4fe-153">Jest zaniepokojony tym, jak wygląda dom, są różne pokoje wygodny rozmiar, czy dom pasuje do potrzeb rodziny, są okna w dobrym miejscu, aby złapać poranne słońce.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="bb4fe-154">Właściciel domu przeprowadza testy funkcjonalne w domu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="bb4fe-155">Ma perspektywę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-155">He has the user's perspective.</span></span> <span data-ttu-id="bb4fe-156">Inspektor budowlany przeprowadza testy jednostkowe w domu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="bb4fe-157">Ma perspektywę budowniczego."</span><span class="sxs-lookup"><span data-stu-id="bb4fe-157">He has the builder's perspective."</span></span>

<span data-ttu-id="bb4fe-158">Źródło: [Testy jednostkowe a testy funkcjonalne](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="bb4fe-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="bb4fe-159">Lubię mówić: "Jako deweloperzy zawodzimy na dwa sposoby: budujemy coś złego, albo budujemy coś złego".</span><span class="sxs-lookup"><span data-stu-id="bb4fe-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="bb4fe-160">Testy jednostkowe zapewniają, że budujesz rzecz dobrze; testy funkcjonalne zapewniają, że budujesz właściwą rzecz.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="bb4fe-161">Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewnego stopnia automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="bb4fe-162">Podobnie jak testy integracji, zwykle działają z pewnego rodzaju infrastruktury testowej, jak również.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="bb4fe-163">To sprawia, że są wolniejsze i bardziej kruche niż testy jednostki i integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="bb4fe-164">Powinieneś mieć tylko tyle testów funkcjonalnych, ile trzeba mieć pewność, że system zachowuje się zgodnie z oczekiwaniami użytkowników.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="bb4fe-165">Piramida badań</span><span class="sxs-lookup"><span data-stu-id="bb4fe-165">Testing Pyramid</span></span>

<span data-ttu-id="bb4fe-166">Martin Fowler napisał o piramidzie testowej, której przykład pokazano na rysunku 9-1.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Piramida badań](./media/image9-1.png)

<span data-ttu-id="bb4fe-168">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-168">**Figure 9-1**.</span></span> <span data-ttu-id="bb4fe-169">Piramida badań</span><span class="sxs-lookup"><span data-stu-id="bb4fe-169">Testing Pyramid</span></span>

<span data-ttu-id="bb4fe-170">Różne warstwy ostrosłupa i ich względne rozmiary reprezentują różne rodzaje testów i ile należy napisać dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="bb4fe-171">Jak widać, zalecenie jest mieć dużą bazę testów jednostkowych, obsługiwane przez mniejszą warstwę testów integracji, z jeszcze mniejszą warstwą testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="bb4fe-172">Każda warstwa powinna być w idealnym miejscu tylko testy, które nie mogą być wykonywane odpowiednio w dolnej warstwie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="bb4fe-173">Należy pamiętać o piramidzie testowania, gdy próbujesz zdecydować, jakiego rodzaju testu potrzebujesz dla określonego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="bb4fe-174">Co przetestować</span><span class="sxs-lookup"><span data-stu-id="bb4fe-174">What to test</span></span>

<span data-ttu-id="bb4fe-175">Częstym problemem dla deweloperów, którzy są niedoświadczeni z pisania zautomatyzowanych testów jest wymyślanie, co do testowania.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="bb4fe-176">Dobrym punktem wyjścia jest przetestowanie logiki warunkowej.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="bb4fe-177">Gdziekolwiek masz metodę z zachowaniem, które zmienia się na podstawie instrukcji warunkowej (if-else, switch, itd.), powinieneś być w stanie wymyślić co najmniej kilka testów, które potwierdzają poprawne zachowanie dla niektórych warunków.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="bb4fe-178">Jeśli kod ma warunki błędu, dobrze jest napisać co najmniej jeden test dla "ścieżki happy" za pośrednictwem kodu (bez błędów) i co najmniej jeden test dla "smutnej ścieżki" (z błędami lub nietypowymi wynikami), aby potwierdzić, że aplikacja zachowuje się zgodnie z oczekiwaniami w obliczu błędów.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="bb4fe-179">Na koniec spróbuj skupić się na testowaniu rzeczy, które mogą zakończyć się niepowodzeniem, zamiast skupiać się na metryki, takie jak pokrycie kodu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="bb4fe-180">Większy zasięg kodu jest lepszy niż mniej, ogólnie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="bb4fe-181">Jednak pisanie kilku testów złożonej i krytycznej dla firmy metody jest zwykle lepsze wykorzystanie czasu niż pisanie testów dla właściwości auto tylko w celu poprawy metryki pokrycia kodu testu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="bb4fe-182">Organizowanie projektów testowych</span><span class="sxs-lookup"><span data-stu-id="bb4fe-182">Organizing test projects</span></span>

<span data-ttu-id="bb4fe-183">Projekty testowe mogą być organizowane jednak najlepiej dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="bb4fe-184">Dobrym pomysłem jest oddzielenie testów według typu (test jednostkowy, test integracji) i przez co są one testujące (według projektu, według przestrzeni nazw).</span><span class="sxs-lookup"><span data-stu-id="bb4fe-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="bb4fe-185">Czy ta separacja składa się z folderów w ramach jednego projektu testowego lub wielu projektów testowych, jest decyzja projektowa.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="bb4fe-186">Jeden projekt jest najprostszy, ale dla dużych projektów z wieloma testami lub w celu łatwiejszego uruchamiania różnych zestawów testów, można mieć kilka różnych projektów testowych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="bb4fe-187">Wiele zespołów organizuje projekty testowe na podstawie projektu, który testuje, co dla aplikacji z więcej niż kilkoma projektami może spowodować dużą liczbę projektów testowych, zwłaszcza jeśli nadal je rozbijesz zgodnie z rodzajem testów w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="bb4fe-188">Podejście kompromisowe jest mieć jeden projekt na rodzaj testu, dla aplikacji, z folderów wewnątrz projektów testowych, aby wskazać projekt (i klasy) testowane.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="bb4fe-189">Wspólne podejście polega na organizowaniu projektów aplikacji w folderze "src", a projekty testowe aplikacji w równoległym folderze "testowym".</span><span class="sxs-lookup"><span data-stu-id="bb4fe-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="bb4fe-190">W programie Visual Studio można utworzyć pasujące foldery rozwiązań, jeśli ta organizacja jest przydatna.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Testowanie organizacji w rozwiązaniu](./media/image9-2.png)

<span data-ttu-id="bb4fe-192">**Rysunek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-192">**Figure 9-2**.</span></span> <span data-ttu-id="bb4fe-193">Testowanie organizacji w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="bb4fe-193">Test organization in your solution</span></span>

<span data-ttu-id="bb4fe-194">Możesz użyć dowolnej struktury testowej, którą wolisz.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="bb4fe-195">Struktura xUnit działa dobrze i jest to, co wszystkie ASP.NET Core i EF Core testy są zapisywane w.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="bb4fe-196">Projekt testu xUnit można dodać w programie Visual Studio przy użyciu szablonu przedstawionego `dotnet new xunit`na rysunku 9-3 lub z interfejsu wiersza polecenia przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="bb4fe-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Dodawanie projektu testowego xUnit w programie Visual Studio](./media/image9-3.png)

<span data-ttu-id="bb4fe-198">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-198">**Figure 9-3**.</span></span> <span data-ttu-id="bb4fe-199">Dodawanie projektu testowego xUnit w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb4fe-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="bb4fe-200">Nazewnictwo testowe</span><span class="sxs-lookup"><span data-stu-id="bb4fe-200">Test naming</span></span>

<span data-ttu-id="bb4fe-201">Nazwij testy w spójny sposób, z nazwami wskazującymi, co robi każdy test.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="bb4fe-202">Jednym z podejść miałem wielki sukces jest nazwać klasy testowe zgodnie z klasą i metodą, które testują.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="bb4fe-203">Powoduje to wiele małych klas testowych, ale to sprawia, że bardzo jasne, co każdy test jest odpowiedzialny za.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="bb4fe-204">Z nazwą klasy testowej skonfigurowaną w celu zidentyfikowania klasy i metody, która ma być testowana, można użyć nazwy metody testowej do określenia testowanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="bb4fe-205">Powinno to obejmować oczekiwane zachowanie i wszelkie dane wejściowe lub założenia, które powinny przynieść to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="bb4fe-206">Przykładowe nazwy testów:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="bb4fe-207">Odmiana tego podejścia kończy każdą nazwę klasy testu z "Powinien" i nieznacznie modyfikuje czas:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="bb4fe-208">`CatalogControllerGetImage`**Należy**`.`**zadzwonić**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="bb4fe-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="bb4fe-209">`CatalogControllerGetImage`**Należy**`.`**dziennik**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="bb4fe-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="bb4fe-210">Niektóre zespoły uważają drugie podejście do nazewnictwa za jaśniejsze, choć nieco bardziej pełne.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="bb4fe-211">W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testu, tak aby gdy jeden lub więcej testów zakończy się niepowodzeniem, jest oczywiste z ich nazw, jakie przypadki nie powiodły się.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="bb4fe-212">Należy unikać nazywania testów niejasno, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy widzisz je w wynikach testów.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="bb4fe-213">Jeśli zastosujesz się do konwencji nazewnictwa, takiej jak ta powyżej, która tworzy wiele małych klas testowych, dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="bb4fe-214">Rysunek 9-4 przedstawia jedno podejście do organizowania testów według folderów w ramach kilku projektów testowych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Organizowanie klas testowych według folderów na podstawie testowanych klas](./media/image9-4.png)

<span data-ttu-id="bb4fe-216">**Rysunek 9-4.**</span><span class="sxs-lookup"><span data-stu-id="bb4fe-216">**Figure 9-4.**</span></span> <span data-ttu-id="bb4fe-217">Organizowanie klas testowych według folderów na podstawie testowanych klas.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="bb4fe-218">Jeśli klasa określonej aplikacji ma wiele metod testowanych (a tym samym wiele klas testowych), może mieć sens, aby umieścić je w folderze odpowiadającym klasie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="bb4fe-219">Ta organizacja nie różni się od sposobu organizowania plików w folderach w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="bb4fe-220">Jeśli w folderze zawierającym wiele innych plików znajdują się więcej niż trzy lub cztery powiązane pliki, często warto przenieść je do własnego podfolderu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="bb4fe-221">Testowanie jednostek ASP.NET aplikacje Core</span><span class="sxs-lookup"><span data-stu-id="bb4fe-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="bb4fe-222">W dobrze zaprojektowanej aplikacji ASP.NET Core większość złożoności i logiki biznesowej będzie hermetyzowana w jednostkach biznesowych i różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="bb4fe-223">Sama aplikacja Core MVC ASP.NET z kontrolerami, filtrami, modułami widokowymi i widokami powinna wymagać bardzo niewielu testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="bb4fe-224">Wiele funkcji danej akcji leży poza samą metodą działania.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="bb4fe-225">Testowanie, czy routing działa poprawnie lub globalnej obsługi błędów, nie można wykonać skutecznie za pomocą testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-225">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="bb4fe-226">Podobnie wszystkie filtry, w tym sprawdzanie poprawności modelu i filtry uwierzytelniania i autoryzacji, nie mogą być testowane jednostkowo za pomocą testu docelowego metody akcji kontrolera.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="bb4fe-227">Bez tych źródeł zachowania większość metod akcji powinny być trywialnie małe, delegowanie większość ich pracy do usług, które mogą być testowane niezależnie od kontrolera, który ich używa.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="bb4fe-228">Czasami trzeba refaktoryzuje kod w celu przetestowania jednostki.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="bb4fe-229">Często wiąże się to z identyfikowaniem abstrakcji i przy użyciu iniekcji zależności, aby uzyskać dostęp do abstrakcji w kodzie, który chcesz przetestować, a nie kodowania bezpośrednio względem infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="bb4fe-230">Rozważmy na przykład tę prostą metodę działania do wyświetlania obrazów:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-230">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="bb4fe-231">Testowanie jednostkowe tej metody jest utrudnione przez jej bezpośrednią zależność od `System.IO.File`, który używa do odczytu z systemu plików.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="bb4fe-232">Można przetestować to zachowanie, aby upewnić się, że działa zgodnie z oczekiwaniami, ale w ten sposób z rzeczywistymi plikami jest test integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="bb4fe-233">Warto zauważyć, że nie można jednostki przetestować trasę tej metody - zobaczysz, jak to zrobić z testu funkcjonalnego wkrótce.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-233">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="bb4fe-234">Jeśli nie można jednostki przetestować zachowanie systemu plików bezpośrednio, a nie można przetestować trasę, co jest tam, aby przetestować?</span><span class="sxs-lookup"><span data-stu-id="bb4fe-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="bb4fe-235">Cóż, po refaktoryzacji, aby umożliwić testowanie jednostkowe, można odkryć niektóre przypadki testowe i brakujące zachowanie, takie jak obsługa błędów.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="bb4fe-236">Do czego polega ta metoda, gdy plik nie zostanie znaleziony?</span><span class="sxs-lookup"><span data-stu-id="bb4fe-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="bb4fe-237">Co powinien zrobić?</span><span class="sxs-lookup"><span data-stu-id="bb4fe-237">What should it do?</span></span> <span data-ttu-id="bb4fe-238">W tym przykładzie metoda refaktoryzowana wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-238">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="bb4fe-239">`_logger`i `_imageService` są wstrzykiwane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="bb4fe-240">Teraz można przetestować, że ten sam identyfikator, który `_imageService`jest przekazywany do metody akcji jest przekazywana do , i że wynikowe bajty są zwracane jako część FileResult.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="bb4fe-241">Można również przetestować, że rejestrowanie błędów `NotFound` odbywa się zgodnie z oczekiwaniami i że wynik jest zwracany, jeśli brakuje obrazu, przy założeniu, że jest to ważne zachowanie aplikacji (oznacza to, że nie tylko kod tymczasowy dodany przez dewelopera w celu zdiagnozowania problemu).</span><span class="sxs-lookup"><span data-stu-id="bb4fe-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="bb4fe-242">Logika rzeczywistego pliku została przeniesiona do oddzielnej usługi implementacji i została rozszerzona, aby zwrócić wyjątek specyficzny dla aplikacji w przypadku brakującego pliku.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="bb4fe-243">Tę implementację można przetestować niezależnie, przy użyciu testu integracji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="bb4fe-244">W większości przypadków należy użyć globalnych programów obsługi wyjątków w kontrolerach, więc ilość logiki w nich powinna być minimalna i prawdopodobnie nie warto testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="bb4fe-245">Wykonaj większość akcji testowania kontrolera przy `TestServer` użyciu testów funkcjonalnych i klasy opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="bb4fe-246">Testowanie integracji ASP.NET aplikacjami Core</span><span class="sxs-lookup"><span data-stu-id="bb4fe-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="bb4fe-247">Większość testów integracji w aplikacjach ASP.NET Core powinny być testowanie usług i innych typów implementacji zdefiniowanych w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="bb4fe-248">Na przykład można [przetestować, że EF Core został pomyślnie aktualizowanie i pobieranie danych, których oczekujesz](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od klas dostępu do danych zamieszkałych w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="bb4fe-249">Najlepszym sposobem, aby sprawdzić, czy ASP.NET core projektu MVC zachowuje się poprawnie jest z testów funkcjonalnych, które są uruchamiane przeciwko aplikacji uruchomionej na hoście testowym.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="bb4fe-250">Testowanie funkcjonalne ASP.NET aplikacje Core</span><span class="sxs-lookup"><span data-stu-id="bb4fe-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="bb4fe-251">W przypadku aplikacji ASP.NET Core `TestServer` klasa sprawia, że testy funkcjonalne są dość łatwe do zapisania.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="bb4fe-252">Można skonfigurować `TestServer` przy `WebHostBuilder` użyciu `HostBuilder`(lub) bezpośrednio (jak zwykle w przypadku `WebApplicationFactory` aplikacji) lub z typem (dostępne od wersji 2.1).</span><span class="sxs-lookup"><span data-stu-id="bb4fe-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="bb4fe-253">Spróbuj dopasować hosta testowego do hosta produkcyjnego tak ściśle, jak to możliwe, więc testy zachowania ćwiczeń podobne do tego, co aplikacja zrobi w produkcji.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="bb4fe-254">Klasa `WebApplicationFactory` jest przydatna do konfigurowania ContentRoot Serwera TestServer, który jest używany przez ASP.NET Core do lokalizowania statycznych zasobów, takich jak widoki.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="bb4fe-255">Można utworzyć proste testy funkcjonalne, tworząc klasę testową, która implementuje IClassFixture\<WebApplicationFactory\<TEntry>> gdzie TEntry jest klasy uruchamiania aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-255">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="bb4fe-256">Dzięki temu urządzenie testowe może utworzyć klienta przy użyciu fabrycznej metody CreateClient:</span><span class="sxs-lookup"><span data-stu-id="bb4fe-256">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="bb4fe-257">Często należy wykonać dodatkową konfigurację witryny przed każdym przebiegiem testu, na przykład konfigurowanie aplikacji do używania magazynu danych w pamięci, a następnie wysiewanie aplikacji danymi testowymi.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="bb4fe-258">Aby to zrobić, należy utworzyć własną podklasę\<WebApplicationFactory TEntry> i zastąpić jego ConfigureWebHost metody.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-258">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="bb4fe-259">Poniższy przykład pochodzi z projektu eShopOnWeb FunctionalTests i jest używany jako część testów w głównej aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

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

<span data-ttu-id="bb4fe-260">Testy można użyć tego niestandardowego WebApplicationFactory za pomocą go do utworzenia klienta, a następnie żądania do aplikacji przy użyciu tego wystąpienia klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="bb4fe-261">Aplikacja będzie miała rozstawione dane, które mogą być używane jako część potwierdzeń testu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="bb4fe-262">Poniższy test sprawdza, czy strona główna aplikacji eShopOnWeb ładuje się poprawnie i zawiera listę produktów, która została dodana do aplikacji jako część danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

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

<span data-ttu-id="bb4fe-263">Ten test funkcjonalny wykonuje pełną ASP.NET stosu aplikacji Core MVC / Razor Pages, w tym wszystkie oprogramowanie pośredniczące, filtry, segregatory itp., które mogą być na miejscu.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="bb4fe-264">Sprawdza, czy dana trasa ("/") zwraca kod stanu oczekiwanego powodzenia i dane wyjściowe HTML.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="bb4fe-265">Robi to bez konfigurowania prawdziwego serwera www, a więc unika wiele kruchości, że przy użyciu prawdziwego serwera www do testowania może wystąpić (na przykład problemy z ustawieniami zapory).</span><span class="sxs-lookup"><span data-stu-id="bb4fe-265">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="bb4fe-266">Testy funkcjonalne uruchamiane w testserverze są zwykle wolniejsze niż testy integracyjne i jednostkowe, ale są znacznie szybsze niż testy, które byłyby uruchamiane przez sieć na testowym serwerze sieci web.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="bb4fe-267">Użyj testów funkcjonalnych, aby upewnić się, że stos frontonu aplikacji działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="bb4fe-268">Testy te są szczególnie przydatne, gdy znajdziesz powielanie w kontrolerach lub stronach i adres duplikacji przez dodanie filtrów.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="bb4fe-269">W idealnym przypadku to refaktoryzowanie nie zmieni zachowania aplikacji, a zestaw testów funkcjonalnych zweryfikuje, że tak jest.</span><span class="sxs-lookup"><span data-stu-id="bb4fe-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="bb4fe-270">Referencje — test ASP.NET aplikacje Core MVC</span><span class="sxs-lookup"><span data-stu-id="bb4fe-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="bb4fe-271">**Testowanie w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="bb4fe-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="bb4fe-272">**Konwencja nazewnictwa testów jednostek** </span><span class="sxs-lookup"><span data-stu-id="bb4fe-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="bb4fe-273">**Testowanie rdzenia EF** </span><span class="sxs-lookup"><span data-stu-id="bb4fe-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="bb4fe-274">**Testy integracji w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="bb4fe-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="bb4fe-275">[Poprzedni](work-with-data-in-asp-net-core-apps.md)
>[następny](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="bb4fe-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
