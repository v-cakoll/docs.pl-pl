---
title: Testowanie platformy ASP.NET Core MVC aplikacji
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Testowanie aplikacji ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: e93c33ae29268c3968ccb59739e899966ae4339d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628264"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="eace1-103">Testowanie platformy ASP.NET Core MVC aplikacji</span><span class="sxs-lookup"><span data-stu-id="eace1-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="eace1-104">*"Jeśli nie potrzebujesz produktu testy jednostkowe, najprawdopodobniej klienci nie będą, takich jak do testowania, albo."*</span><span class="sxs-lookup"><span data-stu-id="eace1-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="eace1-105">\_-Anonimowe-</span><span class="sxs-lookup"><span data-stu-id="eace1-105">\_- Anonymous-</span></span>

<span data-ttu-id="eace1-106">Oprogramowanie o dowolnej złożoności może zakończyć się niepowodzeniem w nieoczekiwany sposób w odpowiedzi na zmiany.</span><span class="sxs-lookup"><span data-stu-id="eace1-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="eace1-107">W związku z tym testowanie po wprowadzeniu zmian jest wymagana dla wszystkich pól poza najbardziej proste (lub najmniej krytyczne) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="eace1-108">Testowanie ręczne jest najwolniejsze, zawodnych, najbardziej kosztowne sposób testowania oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="eace1-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="eace1-109">Niestety Jeśli aplikacje nie są projektowane jako sprawdzalnego działa zgodnie, może być tylko dostępnych środków.</span><span class="sxs-lookup"><span data-stu-id="eace1-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="eace1-110">Aplikacje napisane w następujące zasady dotyczące architektury, w sekcji [rozdział 4](architectural-principles.md) jednostka powinna być sprawdzalnego działa zgodnie i aplikacje platformy ASP.NET Core obsługuje automatyczne integracji i testowania funkcjonalnego także.</span><span class="sxs-lookup"><span data-stu-id="eace1-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="eace1-111">Rodzaje testów automatycznych</span><span class="sxs-lookup"><span data-stu-id="eace1-111">Kinds of automated tests</span></span>

<span data-ttu-id="eace1-112">Istnieje wiele rodzajów testów automatycznych z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="eace1-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="eace1-113">Najprostszy, najniższego poziomu testu jest test jednostkowy.</span><span class="sxs-lookup"><span data-stu-id="eace1-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="eace1-114">Nieco wyższym poziomie istnieją testy integracji i testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="eace1-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="eace1-115">Inne rodzaje testów, takich jak testy interfejsu użytkownika, testy obciążeniowe, testy obciążeniowe i testów dymu wykraczają poza zakres tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eace1-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="eace1-116">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="eace1-116">Unit tests</span></span>

<span data-ttu-id="eace1-117">Test jednostkowy testy pojedynczą częścią Twojej aplikacji logiki.</span><span class="sxs-lookup"><span data-stu-id="eace1-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="eace1-118">Jeden można dodatkowo opisać, wyświetlając listę kilka rzeczy, które nie jest.</span><span class="sxs-lookup"><span data-stu-id="eace1-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="eace1-119">Test jednostkowy nie sprawdza, jak Twoje kod działa z zależności lub infrastruktury — integracja testy dotyczą.</span><span class="sxs-lookup"><span data-stu-id="eace1-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="eace1-120">Test jednostkowy nie test framework, którą Twój kod jest zapisywany na — należy założyć, że jego działania lub, jeśli możesz znaleźć nie, Zgłoś usterkę i kodu obejścia tego problemu.</span><span class="sxs-lookup"><span data-stu-id="eace1-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="eace1-121">Test jednostkowy jest wykonywany w całości w pamięci i w procesie.</span><span class="sxs-lookup"><span data-stu-id="eace1-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="eace1-122">Nie będzie komunikować się z systemu plików, sieci lub bazy danych.</span><span class="sxs-lookup"><span data-stu-id="eace1-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="eace1-123">Testy jednostkowe należy przetestować tylko Twój kod.</span><span class="sxs-lookup"><span data-stu-id="eace1-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="eace1-124">Testy jednostkowe, ze względu na fakt, przetestować pojedynczą jednostkę kodu, bez zewnętrznych zależności mają być wykonywane bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="eace1-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="eace1-125">W związku z tym można uruchomić zestawy testów z setek testów jednostkowych w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="eace1-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="eace1-126">Uruchom je często, najlepiej przed każdym wypychania do repozytorium kontroli źródła udostępnionego, a także bez obaw z każdą kompilacją automatycznych na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="eace1-127">Testy integracyjne</span><span class="sxs-lookup"><span data-stu-id="eace1-127">Integration tests</span></span>

<span data-ttu-id="eace1-128">Chociaż jest to dobry pomysł, aby hermetyzować swój kod, który współdziała z infrastrukturą, takich jak bazy danych i systemy plików, będą nadal mieć część kodu, i prawdopodobnie warto go przetestować.</span><span class="sxs-lookup"><span data-stu-id="eace1-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="eace1-129">Ponadto należy sprawdzić, czy warstwy kodu wchodzić w interakcje w oczekiwany sposób w przypadku w pełni rozpoznać zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="eace1-130">Jest to odpowiedzialność testów integracji.</span><span class="sxs-lookup"><span data-stu-id="eace1-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="eace1-131">Testy integracji zwykle być wolniejszy i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ są one często są zależne od zależności zewnętrzne i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="eace1-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="eace1-132">W związku z tym należy unikać różne rzeczy, które mogłyby zostać testów przy użyciu testów jednostkowych w testów integracji.</span><span class="sxs-lookup"><span data-stu-id="eace1-132">Thus, you should avoid testing things that could be tests with unit tests in integration tests.</span></span> <span data-ttu-id="eace1-133">Jeśli danego scenariusza można przetestować za pomocą testu jednostkowego, należy go przetestować, za pomocą testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="eace1-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="eace1-134">Jeśli nie jest możliwe, rozważ użycie wiąże się test integracji.</span><span class="sxs-lookup"><span data-stu-id="eace1-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="eace1-135">Testy integracji mają często bardziej złożone ustawienia i procedury usuwania niż testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="eace1-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="eace1-136">Na przykład test integracji, który przechodzi z istniejącej bazy danych należy sposób, aby przywrócić bazę danych do znanego stanu przed każdym przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="eace1-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="eace1-137">Jak są dodawane nowe testy i schemat bazy danych w środowisku produkcyjnym rozwoju, testów, te skrypty będą przeważnie zwiększanie się rozmiaru i złożoności.</span><span class="sxs-lookup"><span data-stu-id="eace1-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="eace1-138">W wielu dużych systemach jest niepraktyczne uruchomić pełne zestawy testów integracyjnych na stanowisko pracy dewelopera przed zaewidencjonowaniem zmiany do kontroli źródła udostępnionych.</span><span class="sxs-lookup"><span data-stu-id="eace1-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="eace1-139">W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="eace1-140">Klasa implementacji LocalFileImageService implementuje logikę pobierania i zwracania bajtów w pliku obrazu z określonego folderu podany identyfikator:</span><span class="sxs-lookup"><span data-stu-id="eace1-140">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a><span data-ttu-id="eace1-141">Testy funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="eace1-141">Functional tests</span></span>

<span data-ttu-id="eace1-142">Testy integracji są zapisywane z perspektywy deweloperów, aby sprawdzić, czy niektóre składniki systemu poprawnie współpracują ze sobą.</span><span class="sxs-lookup"><span data-stu-id="eace1-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="eace1-143">Testy funkcjonalne są zapisywane z punktu widzenia użytkownika i sprawdź poprawność systemu zależy od jego potrzeb.</span><span class="sxs-lookup"><span data-stu-id="eace1-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="eace1-144">Poniższy fragment oferuje przydatne w sposób analogiczny, jak wziąć pod uwagę testów funkcjonalnych w porównaniu do testów jednostkowych:</span><span class="sxs-lookup"><span data-stu-id="eace1-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="eace1-145">"Wiele razy rozwój systemu przyrównać do budowania domu.</span><span class="sxs-lookup"><span data-stu-id="eace1-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="eace1-146">Chociaż w ten sposób analogiczny, nie jest jeszcze prawidłowy, firma Microsoft można rozszerzyć na potrzeby rozróżnienie między jednostkowych i testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="eace1-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="eace1-147">Testy jednostkowe jest analogiczne do Inspektora budynku, odwiedzając witrynę konstrukcji domu.</span><span class="sxs-lookup"><span data-stu-id="eace1-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="eace1-148">Koncentruje się na różnych systemów wewnętrznych domu podstawę formułowanie, elektryczny, wodociągów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="eace1-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="eace1-149">Zapewnia on (testy), czy części domu będą działać poprawnie i bezpiecznie, oznacza to, że spełniają kod tworzenia.</span><span class="sxs-lookup"><span data-stu-id="eace1-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="eace1-150">Testy funkcjonalne w tym scenariuszu są analogiczne do właściciel tej samej witrynie konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="eace1-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="eace1-151">Zakłada on, systemami wewnętrznymi działają prawidłowo, czy inspektor budynku działa jego zadań.</span><span class="sxs-lookup"><span data-stu-id="eace1-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="eace1-152">Właściciel koncentruje się na co będzie podobnie jak w tym dom na żywo.</span><span class="sxs-lookup"><span data-stu-id="eace1-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="eace1-153">On dotyczy wygląd domu, różnych pomieszczeniach komfortowo, jednocześnie rozmiar, jest domu potrzeb rodziny, są okna w dobre miejsce, gdzie możesz przechwytywać sun rano.</span><span class="sxs-lookup"><span data-stu-id="eace1-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="eace1-154">Właściciel wykonuje testy funkcjonalne w domu.</span><span class="sxs-lookup"><span data-stu-id="eace1-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="eace1-155">Ma on perspektywy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="eace1-155">He has the user's perspective.</span></span> <span data-ttu-id="eace1-156">Inspektor budynku wykonuje testy jednostkowe w domu.</span><span class="sxs-lookup"><span data-stu-id="eace1-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="eace1-157">Ma on konstruktora perspektywy."</span><span class="sxs-lookup"><span data-stu-id="eace1-157">He has the builder's perspective."</span></span>

<span data-ttu-id="eace1-158">Źródło: [Testowanie i testów funkcjonalnych jednostek](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="eace1-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="eace1-159">Jestem fond z informacją o tym "jako programiści, firma Microsoft nie na dwa sposoby: wbudowana niewłaściwej kolejności lub wbudowana nic złego."</span><span class="sxs-lookup"><span data-stu-id="eace1-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="eace1-160">Testy jednostkowe upewnij się, że tworzysz rzecz po prawej stronie; testy funkcjonalne upewnij się, że tworzysz właściwe.</span><span class="sxs-lookup"><span data-stu-id="eace1-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="eace1-161">Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewien stopień automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="eace1-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="eace1-162">Takie jak testy integracji zazwyczaj pracują z pewnego rodzaju także infrastrukturę testowania.</span><span class="sxs-lookup"><span data-stu-id="eace1-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="eace1-163">Z tego powodu wolniejszy i bardziej kruchy niż testy jednostkowe i integracji.</span><span class="sxs-lookup"><span data-stu-id="eace1-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="eace1-164">Użytkownik powinien mieć tylko tyle testy funkcjonalne, ponieważ muszą mieć pewność, system zachowuje się zgodnie z oczekiwaniami użytkowników.</span><span class="sxs-lookup"><span data-stu-id="eace1-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="eace1-165">Testowanie ostrosłupowy</span><span class="sxs-lookup"><span data-stu-id="eace1-165">Testing Pyramid</span></span>

<span data-ttu-id="eace1-166">Zapisano Martina Fowlera o ostrosłupowy testowania, przykład jest wyświetlany w rysunek 9-1.</span><span class="sxs-lookup"><span data-stu-id="eace1-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="eace1-167">Rysunek 9-1 testowania ostrosłupowy</span><span class="sxs-lookup"><span data-stu-id="eace1-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="eace1-168">Różne warstwy ostrosłupa i ich względne rozmiary reprezentują różne rodzaje testów i ile należy wpisać dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="eace1-169">Jak widać, zaleca się mieć duży podstawą testów jednostkowych, obsługiwany przez warstwę mniejszych testy integracji z mniejszych warstwą testy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eace1-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="eace1-170">Każda warstwa najlepiej mają tylko testy, których nie można wykonać operacji odpowiednio w niższej warstwie.</span><span class="sxs-lookup"><span data-stu-id="eace1-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="eace1-171">Gdy próbujesz określić, jakiego rodzaju badań potrzebne dla danego scenariusza, należy pamiętać o testowania ostrosłupa.</span><span class="sxs-lookup"><span data-stu-id="eace1-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="eace1-172">Co należy przetestować</span><span class="sxs-lookup"><span data-stu-id="eace1-172">What to test</span></span>

<span data-ttu-id="eace1-173">Typowy problem dla deweloperów, którzy są niedoświadczonej pisanie zautomatyzowanych testów jest pojawi się z tym, co do testowania.</span><span class="sxs-lookup"><span data-stu-id="eace1-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="eace1-174">To dobry punkt wyjścia do testowania logikę warunkową.</span><span class="sxs-lookup"><span data-stu-id="eace1-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="eace1-175">Dowolnym masz metody z zachowaniem, które zmiany oparte na instrukcji warunkowej (if-else, Przełącz itp.), powinno być możliwe, co pozwoli uzyskać co najmniej kilka testów potwierdzających poprawnego zachowania w pewnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="eace1-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="eace1-176">Jeśli kod zawiera błędy, dobrze jest zapisać co najmniej jeden test do "pożądaną ścieżkę" przez kod (z bez błędów) i co najmniej jeden test "sad ścieżki" (z błędów lub nietypowych wyników) upewnij się, że Twoja aplikacja działa zgodnie z oczekiwaniami w przypadku błędów.</span><span class="sxs-lookup"><span data-stu-id="eace1-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="eace1-177">Ponadto spróbuj skupić się na różne rzeczy, które może zakończyć się niepowodzeniem, zamiast koncentrowania się na metryki, takie jak pokrycie kodu.</span><span class="sxs-lookup"><span data-stu-id="eace1-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="eace1-178">Ogólnie jest lepsze niż, mniejsze więcej pokrycia kodu.</span><span class="sxs-lookup"><span data-stu-id="eace1-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="eace1-179">Pisanie kilka więcej testów metody bardzo złożone i krytyczne dla prowadzonej działalności jest jednak zazwyczaj lepszego wykorzystania czasu niż pisania testów dla właściwości auto tylko w celu poprawy metryki pokrycie kodu testu.</span><span class="sxs-lookup"><span data-stu-id="eace1-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="eace1-180">Organizowanie projektów testowych</span><span class="sxs-lookup"><span data-stu-id="eace1-180">Organizing test projects</span></span>

<span data-ttu-id="eace1-181">Projekty testowe można organizować, jednak działa najlepiej dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="eace1-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="eace1-182">To dobry pomysł, aby rozdzielić testy według typów (test jednostkowy, test integracji) i jakie poddawanego testom (według projektu, obszaru nazw).</span><span class="sxs-lookup"><span data-stu-id="eace1-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="eace1-183">Czy ta separacja składa się z folderów w ramach projektu testowego jednego lub wielu projektów testów jest decyzję projektową.</span><span class="sxs-lookup"><span data-stu-id="eace1-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="eace1-184">Najprościej jest jednym projektem, ale dla dużych projektów za pomocą wielu testów lub aby można było łatwiej uruchomić różne zestawy testów, możesz chcieć mieć kilka projektów testowych różnych.</span><span class="sxs-lookup"><span data-stu-id="eace1-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="eace1-185">Wiele zespołów organizowanie projektów testów opartych na projekt, który poddawanego testom, którym dla aplikacji przy użyciu więcej niż kilku projektów może skutkować dużą liczbę projektów testowych, zwłaszcza wtedy, gdy użytkownik nadal podziału je według rodzaju testy są w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="eace1-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="eace1-186">To podejście naruszenia zabezpieczeń jest jednym projektem na rodzaj testu w każdej aplikacji, za pomocą folderów w folderze projektów testowych, aby wskazać testowanego projektu (i klasy).</span><span class="sxs-lookup"><span data-stu-id="eace1-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="eace1-187">Typowym podejściem jest do organizowania projektów aplikacji w obszarze folderu "src" i projekty testowe aplikacji w ramach równoległego folderu "testów".</span><span class="sxs-lookup"><span data-stu-id="eace1-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="eace1-188">W programie Visual Studio, można utworzyć pasujących folderów rozwiązania, jeśli okaże się tej organizacji przydatne.</span><span class="sxs-lookup"><span data-stu-id="eace1-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="eace1-189">Rysunek 9-2 Test organizacji w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="eace1-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="eace1-190">Możesz użyć różnych platform testowych, które użytkownik sobie tego życzy.</span><span class="sxs-lookup"><span data-stu-id="eace1-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="eace1-191">XUnit framework działa dobrze i to wszystkie testy w ASP.NET Core i programem EF Core są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="eace1-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="eace1-192">W programie Visual Studio przy użyciu szablonu, pokazane w rysunek 9-3 lub z interfejsu wiersza polecenia przy użyciu nowego xunit dotnet, możesz dodać projekt testu xUnit.</span><span class="sxs-lookup"><span data-stu-id="eace1-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="eace1-193">Rysunek 9-3. Dodaj projekt testu xUnit w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eace1-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="eace1-194">Nazwy testu</span><span class="sxs-lookup"><span data-stu-id="eace1-194">Test naming</span></span>

<span data-ttu-id="eace1-195">Testy w sposób spójny, należy nadać nazwę przy użyciu nazwy na wskazujące na to, co oznacza każdy test.</span><span class="sxs-lookup"><span data-stu-id="eace1-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="eace1-196">Jest jednym z podejść miałem doskonałe zakończone sukcesem nazwy klas testowych zgodnie z klasy i metody, które poddawanego testom.</span><span class="sxs-lookup"><span data-stu-id="eace1-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="eace1-197">Powoduje to wiele klas mały test, ale zapewnia bardzo jasne, co to jest odpowiedzialny za każdego testu.</span><span class="sxs-lookup"><span data-stu-id="eace1-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="eace1-198">Przy użyciu nazwy klasy testu, ustawić, aby zidentyfikować klasę i metodę ma zostać przetestowana Nazwa metody testu może służyć do określania zachowania poddawana testom.</span><span class="sxs-lookup"><span data-stu-id="eace1-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="eace1-199">Powinno to obejmować oczekiwane zachowanie i dane wejściowe lub założenia, które powinny to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="eace1-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="eace1-200">Niektóre przykładowe nazwy testu:</span><span class="sxs-lookup"><span data-stu-id="eace1-200">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="eace1-201">Odmiana tej metody kończy każda nazwa klasy testu za pomocą "Powinien" i modyfikuje nieco czasu teraźniejszego:</span><span class="sxs-lookup"><span data-stu-id="eace1-201">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="eace1-202">`CatalogControllerGetImage`**Należy**`.`**wywołania**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="eace1-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="eace1-203">`CatalogControllerGetImage`**Należy**`.`**dziennika**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="eace1-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="eace1-204">Niektóre zespoły znaleźć drugiego podejścia nazewnictwa bardziej zrozumiały, jednak nieco bardziej szczegółowy.</span><span class="sxs-lookup"><span data-stu-id="eace1-204">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="eace1-205">W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testów, tak, że gdy co najmniej jeden test nie powiedzie się, jest oczywiste, z ich nazw, w jakich sytuacjach nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="eace1-205">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="eace1-206">Unikaj nazewnictwa możesz testy vaguely, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy zostanie wyświetlony w wynikach testu.</span><span class="sxs-lookup"><span data-stu-id="eace1-206">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="eace1-207">Jeśli zgodne z konwencją nazewnictwa, takie jak ten powyżej, tworzy wiele klas mały test, jest dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="eace1-207">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="eace1-208">Jedno z podejść do organizowania testów według folderów w ramach kilku projektów testowych pokazano na rysunku 9-4.</span><span class="sxs-lookup"><span data-stu-id="eace1-208">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="eace1-209">**Rysunek 9 – 4.**</span><span class="sxs-lookup"><span data-stu-id="eace1-209">**Figure 9-4.**</span></span> <span data-ttu-id="eace1-210">Organizowanie klas testowych według folderów na podstawie klasy poddawana testom.</span><span class="sxs-lookup"><span data-stu-id="eace1-210">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="eace1-211">Oczywiście jeśli klasy określonej aplikacji ma wiele metod poddawana testom (a zatem klas wiele testów) rozsądne może okazać się umieścić je w folderze odpowiadający klasy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eace1-211">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="eace1-212">Ta organizacja nie różni się od sposobu może organizowania plików w folderach w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="eace1-212">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="eace1-213">Jeśli masz więcej niż trzy lub cztery powiązane pliki w folderze zawierających wiele plików, często jest przydatne przenieść je do ich własnych podfolderu.</span><span class="sxs-lookup"><span data-stu-id="eace1-213">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="eace1-214">Jednostki testowania aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eace1-214">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="eace1-215">W dobrze zaprojektowana aplikacja platformy ASP.NET Core większość złożoności i logikę biznesową, będzie można hermetyzować w podmioty gospodarcze i różnych usług.</span><span class="sxs-lookup"><span data-stu-id="eace1-215">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="eace1-216">Aplikacji ASP.NET Core MVC, za pomocą kontrolerów, filtry, modele widoków i widoki, wymagać bardzo mało testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="eace1-216">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="eace1-217">Wiele funkcji danej akcji znajduje się poza sama metoda akcji.</span><span class="sxs-lookup"><span data-stu-id="eace1-217">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="eace1-218">Sprawdzenie, czy routing działa prawidłowo lub obsługi błędu globalnego nie można wykonać skutecznie z testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="eace1-218">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="eace1-219">Podobnie wszelkie filtry, takimi jak sprawdzanie poprawności modelu i uwierzytelnianie i filtry autoryzacji nie może być testowane jednostki.</span><span class="sxs-lookup"><span data-stu-id="eace1-219">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="eace1-220">Bez tych źródeł zachowanie większość metod akcji powinna być w przypadku małych delegowanie duża część swojej pracy z usługami, które mogą być testowane niezależne od kontrolera, który używa tych.</span><span class="sxs-lookup"><span data-stu-id="eace1-220">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="eace1-221">Czasami musisz Refaktoryzacja kodu w kolejności do testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="eace1-221">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="eace1-222">Często obejmuje to identyfikowanie abstrakcje i otwieranie abstrakcji w kodzie, który chcesz przetestować za pomocą iniekcji zależności, a nie kodu bezpośrednio w odniesieniu do infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="eace1-222">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="eace1-223">Rozważmy na przykład tej metody prostej akcji do wyświetlania obrazów:</span><span class="sxs-lookup"><span data-stu-id="eace1-223">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="eace1-224">Ta metoda testowania jednostek składa się trudne bezpośrednie zależne od System.IO.File, która jest używana do odczytu z systemu plików.</span><span class="sxs-lookup"><span data-stu-id="eace1-224">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="eace1-225">Można przetestować tego zachowania, aby upewnić się, działa zgodnie z oczekiwaniami, ale wiąże się test integracji to działanie za pomocą rzeczywistych plików.</span><span class="sxs-lookup"><span data-stu-id="eace1-225">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="eace1-226">Warto zauważyć jednostki nie można przetestować tę metodę trasy — pokazano, jak można to zrobić za pomocą testu funkcjonalnego wkrótce.</span><span class="sxs-lookup"><span data-stu-id="eace1-226">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="eace1-227">Jeśli test jednostkowy zachowanie systemu plików nie można bezpośrednio, a nie Testuj trasę, co jest do testowania?</span><span class="sxs-lookup"><span data-stu-id="eace1-227">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="eace1-228">Również po refaktoryzacji, aby umożliwić testy jednostkowe, użytkownik może stwierdzić, niektóre przypadki testowe i Brak zachowania, na przykład obsługa błędów.</span><span class="sxs-lookup"><span data-stu-id="eace1-228">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="eace1-229">Do czego służy metoda? Jeśli nie odnaleziono pliku</span><span class="sxs-lookup"><span data-stu-id="eace1-229">What does the method do when a file isn't found?</span></span> <span data-ttu-id="eace1-230">Co ona zrobić?</span><span class="sxs-lookup"><span data-stu-id="eace1-230">What should it do?</span></span> <span data-ttu-id="eace1-231">W tym przykładzie metoda wycofanej wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="eace1-231">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")\]
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

<span data-ttu-id="eace1-232">\_Rejestratora i \_imageService są zarówno wprowadzane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="eace1-232">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="eace1-233">Teraz możesz sprawdzić, czy ten sam identyfikator, który jest przekazywany do metody akcji jest przekazywany do \_imageService, oraz że wynikowy bajtów są zwracane jako część FileResult.</span><span class="sxs-lookup"><span data-stu-id="eace1-233">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="eace1-234">Możesz także testować wykonywane rejestrowanie błędów zgodnie z oczekiwaniami i że wynik NotFound jest zwracany, jeśli obraz jest nieobecne, przy założeniu, że jest to ważna aplikacja zachowanie (oznacza to, nie tylko tymczasowe kod dewelopera dodane do zdiagnozowania problemu).</span><span class="sxs-lookup"><span data-stu-id="eace1-234">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="eace1-235">Logika rzeczywisty plik został przeniesiony do oddzielnych implementacji usługi i został uzupełniony do zwrócenia wyjątku specyficzne dla aplikacji w przypadku brakujących plików.</span><span class="sxs-lookup"><span data-stu-id="eace1-235">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="eace1-236">Możesz przetestować tę implementację niezależnie, za pomocą wiąże się test integracji.</span><span class="sxs-lookup"><span data-stu-id="eace1-236">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="eace1-237">W większości przypadków będziesz chciał użyć obsługi wyjątków globalnego, kontrolerów, dlatego ilość logiki w nich powinny być minimalny i prawdopodobnie nie warte testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="eace1-237">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="eace1-238">Należy wykonać większość testowania akcji kontrolera testów funkcjonalnych i `TestServer` klasy opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="eace1-238">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="eace1-239">Testowanie aplikacji platformy ASP.NET Core integracji</span><span class="sxs-lookup"><span data-stu-id="eace1-239">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="eace1-240">Większość testów integracji w aplikacjach ASP.NET Core powinien testowanie, usługi i inne typy wdrożenia, zdefiniowana w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="eace1-240">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="eace1-241">Testy funkcjonalne, które uruchamiane względem aplikacji uruchomionej w hosta testów jest najlepszym sposobem sprawdzenia, czy projekt platformy ASP.NET Core MVC zachowuje się prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="eace1-241">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span> <span data-ttu-id="eace1-242">W sekcji Testowanie integracji wcześniej w tym rozdziale przedstawiono przykładowy test integracji z klasą dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="eace1-242">An example of an integration test of a data access class is shown in the Integration Testing section earlier in this chapter.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="eace1-243">Funkcjonalności testowanie aplikacji platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eace1-243">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="eace1-244">W przypadku aplikacji platformy ASP.NET Core `TestServer` klasy sprawia, że testy funkcjonalne są stosunkowo łatwa do zapisania.</span><span class="sxs-lookup"><span data-stu-id="eace1-244">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="eace1-245">Możesz skonfigurować `TestServer` przy użyciu `WebHostBuilder` bezpośrednio (jak zwykle dla aplikacji), lub za pomocą `WebApplicationFactory` typu (dostępne od wersji 2.1).</span><span class="sxs-lookup"><span data-stu-id="eace1-245">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="eace1-246">Należy próbować jako najdokładniej dopasować hosta testów do hosta produkcji, aby testy wykonują zachowanie podobne do aplikacji wykona w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="eace1-246">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="eace1-247">`WebApplicationFactory` Klasa jest przydatna do konfigurowania elementu TestServer ContentRoot, który jest używany przez platformy ASP.NET Core można zlokalizować statycznych zasobów, takich jak widoki.</span><span class="sxs-lookup"><span data-stu-id="eace1-247">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="eace1-248">Można utworzyć proste testy funkcjonalne, tworząc klasy testowej, który implementuje IClassFixture\<WebApplicationFactory\<TEntry >> gdzie TEntry jest klasa uruchamiania aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="eace1-248">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="eace1-249">Dzięki temu w miejscu Twoje warunki początkowe testu można utworzyć klienta przy użyciu metody CreateClient fabryka jest:</span><span class="sxs-lookup"><span data-stu-id="eace1-249">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="eace1-250">Często, należy wykonać pewne dodatkowe czynności konfiguracyjne witryny, przed uruchomieniem każdego testu, takie jak konfigurowanie aplikacji do korzystania z pamięci magazynu danych, a następnie rozmieszczania aplikacji z danymi.</span><span class="sxs-lookup"><span data-stu-id="eace1-250">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="eace1-251">Aby to zrobić, należy utworzyć własną podklasę klasy WebApplicationFactory\<TEntry > i jego metoda ConfigureWebHost musi zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="eace1-251">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="eace1-252">W poniższym przykładzie pochodzi z projektu FunctionalTests eShopOnWeb i jest używana jako część testów aplikacji sieci web głównego.</span><span class="sxs-lookup"><span data-stu-id="eace1-252">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory 
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
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
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
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

<span data-ttu-id="eace1-253">Testy można skorzystać z tego niestandardowego WebApplicationFactory przez użyciem jej do utworzenia klienta i następnie zgłasza żądania do aplikacji przy użyciu tego wystąpienia klienta.</span><span class="sxs-lookup"><span data-stu-id="eace1-253">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="eace1-254">Aplikacja będzie miała zasilany danych, który może służyć jako część testu potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="eace1-254">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="eace1-255">Kolejny test sprawdza, czy strona główna aplikacji eShopOnWeb poprawnie ładowana i zawiera listę produktów, który został dodany do aplikacji jako część danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="eace1-255">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
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

<span data-ttu-id="eace1-256">Ten test funkcjonalny wykonuje pełne ASP.NET Core MVC / stosu aplikacji stron Razor, w tym wszystkie oprogramowania pośredniczącego, filtry, wiążących, itp., które mogą być w miejscu.</span><span class="sxs-lookup"><span data-stu-id="eace1-256">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="eace1-257">Sprawdza, czy daną trasą ("/") zwraca Powodzenie oczekiwany kod stanu i danych wyjściowych HTML.</span><span class="sxs-lookup"><span data-stu-id="eace1-257">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="eace1-258">Odbywa się to bez konfigurowania serwera sieci web rzeczywiste, a więc eliminuje większość kruchości, który za pomocą rzeczywistych sieci web serwera do testowania mogą występować (na przykład problemy z ustawieniami zapory).</span><span class="sxs-lookup"><span data-stu-id="eace1-258">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="eace1-259">Testy funkcjonalne, które są uruchamiane względem elementu TestServer są zwykle wolniejsze niż integracji i testów jednostkowych, ale jest znacznie szybsze niż testy, które może działać przez sieć do serwera sieci web test.</span><span class="sxs-lookup"><span data-stu-id="eace1-259">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="eace1-260">Aby upewnić się, że stos frontonu aplikacji działa zgodnie z oczekiwaniami, należy użyć testów funkcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="eace1-260">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="eace1-261">Te testy są szczególnie przydatne podczas duplikowania możesz znaleźć w kontrolerach lub strony i adresów powielania, dodając filtry.</span><span class="sxs-lookup"><span data-stu-id="eace1-261">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="eace1-262">W idealnym przypadku tej refaktoryzacji nie zmienią się zachowanie aplikacji, a zestaw testów funkcjonalnych sprawdzi, czy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="eace1-262">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eace1-263">[Poprzednie](work-with-data-in-asp-net-core-apps.md)
>[dalej](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="eace1-263">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
