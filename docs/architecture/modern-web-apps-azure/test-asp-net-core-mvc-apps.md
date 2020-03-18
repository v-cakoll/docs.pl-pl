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
# <a name="test-aspnet-core-mvc-apps"></a>Testowanie ASP.NET podstawowych aplikacji MVC

> *"Jeśli nie lubisz testować jednostkowych produktów, najprawdopodobniej twoi klienci nie będą chcieli go przetestować."*
 > \_- Anonimowe-

Oprogramowanie o dowolnej złożoności może zakończyć się niespodziewanym powodzeniem w odpowiedzi na zmiany. W związku z tym testowanie po dokonaniu zmian jest wymagane dla wszystkich, ale najbardziej trywialne (lub najmniej krytyczne) aplikacje. Ręczne testowanie jest najwolniejszym, najmniej niezawodnym i najdroższym sposobem testowania oprogramowania. Niestety, jeśli aplikacje nie są przeznaczone do testowania, może to być jedyny dostępny środek. Wnioski napisane zgodnie z zasadami architektury określonymi w [rozdziale 4](architectural-principles.md) powinny być sprawdzalne jednostkami. ASP.NET Podstawowe aplikacje obsługują automatyczną integrację i testowanie funkcjonalne.

## <a name="kinds-of-automated-tests"></a>Rodzaje testów automatycznych

Istnieje wiele rodzajów zautomatyzowanych testów dla aplikacji. Najprostszym testem na najniższym poziomie jest test jednostkowy. Na nieco wyższym poziomie istnieją testy integracyjne i testy funkcjonalne. Inne rodzaje testów, takich jak testy interfejsu i uwyżenia, testy obciążenia, testy warunków skrajnych i testy dymu, wykraczają poza zakres tego dokumentu.

### <a name="unit-tests"></a>Testy jednostkowe

Test jednostkowy testuje pojedynczą część logiki aplikacji. Można to dalej opisać, wymieniając niektóre rzeczy, które nie są. Test jednostkowy nie testuje, jak kod działa z zależnościami lub infrastruktury — to, co testy integracji są dla. Test jednostkowy nie testuje struktury, na której jest napisane kod — należy założyć, że działa lub, jeśli okaże się, że nie, zgłać błąd i kod obejść. Test jednostkowy jest uruchamiany całkowicie w pamięci i w trakcie. Nie komunikuje się z systemem plików, siecią ani bazą danych. Testy jednostkowe należy przetestować tylko kod.

Testy jednostkowe, ze względu na fakt, że testują tylko jedną jednostkę kodu, bez zależności zewnętrznych, należy wykonać bardzo szybko. W związku z tym powinno być możliwe uruchomienie zestawów testów setek testów jednostkowych w ciągu kilku sekund. Uruchamiaj je często, najlepiej przed każdym wypychaniem do repozytorium kontroli źródła udostępnionego, a na pewno z każdą zautomatyzowaną kompilacją na serwerze kompilacji.

### <a name="integration-tests"></a>Testy integracji

Chociaż jest to dobry pomysł, aby hermetyzować kod, który współdziała z infrastrukturą, takich jak bazy danych i systemy plików, nadal będziesz miał niektóre z tego kodu i prawdopodobnie będziesz chciał go przetestować. Ponadto należy sprawdzić, czy warstwy kodu współdziałają zgodnie z oczekiwaniami, gdy zależności aplikacji są w pełni rozwiązane. Jest to odpowiedzialność testów integracji. Testy integracji są zwykle wolniejsze i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ często zależą od zależności zewnętrznych i infrastruktury. W związku z tym należy unikać testowania rzeczy, które mogą być testowane z testów jednostkowych w testach integracji. Jeśli można przetestować dany scenariusz z testu jednostkowego, należy przetestować go z testu jednostkowego. Jeśli nie możesz, rozważ użycie testu integracji.

Testy integracji często mają bardziej złożone procedury konfiguracji i rozdarcia niż testy jednostkowe. Na przykład test integracji, który jest sprzeczny z rzeczywistą bazą danych będzie potrzebny sposób, aby przywrócić bazę danych do znanego stanu przed każdym uruchomieniu testu. Po dodaniu nowych testów i rozwoju schematu produkcyjnej bazy danych te skrypty testowe będą rosły w rozmiarze i złożoności. W wielu dużych systemach jest niepraktyczne, aby uruchomić pełne pakiety testów integracji na stacjach roboczych deweloperów przed zaewidencjonowaniem zmian do współużytkowanej kontroli źródła. W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.

### <a name="functional-tests"></a>Testy funkcjonalne

Testy integracji są zapisywane z perspektywy dewelopera, aby sprawdzić, czy niektóre składniki systemu działają poprawnie razem. Testy funkcjonalne są zapisywane z perspektywy użytkownika i sprawdzić poprawność systemu w oparciu o jego wymagania. Poniższy fragment oferuje użyteczną analogię do myślenia o testach funkcjonalnych, w porównaniu do testów jednostkowych:

> "Wiele razy rozwój systemu jest porównywany do budowy domu. Chociaż ta analogia nie jest całkiem poprawna, możemy ją rozszerzyć w celu zrozumienia różnicy między testami jednostkowymi i funkcjonalnymi. Testowanie jednostkowe jest analogiczne do inspektora budowlanego odwiedzającego plac budowy domu. Koncentruje się na różnych systemach wewnętrznych domu, fundacji, kadrowania, instalacji elektrycznej, kanalizacji i tak dalej. Zapewnia (testy), że części domu będą działać poprawnie i bezpiecznie, czyli spełniają kodeks budowlany. Testy funkcjonalne w tym scenariuszu są analogiczne do właściciela domu odwiedzającego ten sam plac budowy. Zakłada on, że systemy wewnętrzne będą zachowywać się odpowiednio, że inspektor budowlany wykonuje swoje zadanie. Właściciel domu koncentruje się na tym, jak to będzie mieszkać w tym domu. Jest zaniepokojony tym, jak wygląda dom, czy różne pokoje są wygodne, czy dom pasuje do potrzeb rodziny, są okna mieszczanami w dobrym miejscu, aby złapać poranne słońce. Właściciel domu wykonuje testy funkcjonalne w domu. Ma perspektywę użytkownika. Inspektor budowlany przeprowadza testy jednostkowe w domu. Ma perspektywę budowniczego."

Źródło: [Testowanie jednostkowe a testy funkcjonalne](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Lubię mówić: "Jako deweloperzy zawodzimy na dwa sposoby: budujemy coś złego, albo budujemy coś złego". Testy jednostkowe zapewniają, że budujesz to, co właściwe; testy funkcjonalne zapewniają, że budujesz to, co właściwe.

Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewnego stopnia automatyzacji interfejsu użytkownika. Podobnie jak testy integracji, zwykle działają one z jakąś infrastrukturą testową. To sprawia, że są wolniejsze i bardziej kruche niż testy jednostkowe i integracyjne. Należy mieć tylko tyle testów funkcjonalnych, ile trzeba mieć pewność, że system zachowuje się tak, jak oczekują użytkownicy.

### <a name="testing-pyramid"></a>Piramida testowania

Martin Fowler napisał o piramidzie testowej, której przykład przedstawiono na rysunku 9-1.

![Piramida testowania](./media/image9-1.png)

**Rysunek 9-1**. Piramida testowania

Różne warstwy piramidy i ich względne rozmiary reprezentują różne rodzaje testów i liczbę pisanych dla aplikacji. Jak widać, zaleca się mieć dużą bazę testów jednostkowych, wspieranych przez mniejszą warstwę testów integracyjnych, z jeszcze mniejszą warstwą testów funkcjonalnych. Każda warstwa powinna mieć tylko testy, których nie można wykonać odpowiednio w niższej warstwie. Pamiętaj o piramidzie testowej, gdy próbujesz zdecydować, jakiego rodzaju testu potrzebujesz dla określonego scenariusza.

### <a name="what-to-test"></a>Co przetestować

Częstym problemem dla deweloperów, którzy są niedoświadczeni w pisaniu zautomatyzowanych testów jest wymyślanie, co do testowania. Dobrym punktem wyjścia jest przetestowanie logiki warunkowej. Wszędzie tam, gdzie masz metodę z zachowaniem, które zmienia się na podstawie instrukcji warunkowej (if-else, switch itd.), powinieneś być w stanie wymyślić co najmniej kilka testów, które potwierdzają prawidłowe zachowanie dla niektórych warunków. Jeśli kod ma warunki błędu, dobrze jest napisać co najmniej jeden test dla "szczęśliwej ścieżki" za pomocą kodu (bez błędów) i co najmniej jeden test dla "smutnej ścieżki" (z błędami lub nietypowymi wynikami), aby potwierdzić, że aplikacja zachowuje się zgodnie z oczekiwaniami w obliczu błędów. Na koniec spróbuj skupić się na testowaniu rzeczy, które mogą się nie powieść, zamiast skupiać się na metrykach, takich jak pokrycie kodu. Więcej pokrycia kodu jest lepszy niż mniej, ogólnie. Jednak pisanie kilku testów złożonych i biznesowych metody krytyczne jest zwykle lepsze wykorzystanie czasu niż pisanie testów dla właściwości automatycznych tylko w celu poprawy metryki pokrycia kodu testu.

## <a name="organizing-test-projects"></a>Organizowanie projektów testowych

Projekty testowe mogą być zorganizowane, jednak najlepiej dla Ciebie. Dobrym pomysłem jest oddzielenie testów według typu (test jednostkowy, test integracji) i według tego, co testują (według projektu, według przestrzeni nazw). Czy to rozdzielenie składa się z folderów w ramach jednego projektu testowego lub wielu projektów testowych, jest decyzja projektowa. Jeden projekt jest najprostszy, ale dla dużych projektów z wieloma testami lub w celu łatwiejszego uruchamiania różnych zestawów testów, możesz chcieć mieć kilka różnych projektów testowych. Wiele zespołów organizuje projekty testowe na podstawie projektu, który testują, co dla aplikacji z więcej niż kilkoma projektami może spowodować dużą liczbę projektów testowych, zwłaszcza jeśli nadal je rozbić zgodnie z rodzajem testów w każdym projekcie. Podejście kompromisowe jest mieć jeden projekt na rodzaj testu, na aplikację, z folderów wewnątrz projektów testowych, aby wskazać projektu (i klasy) testowane.

Typowym podejściem jest organizowanie projektów aplikacji w folderze "src" i projektów testowych aplikacji w równoległym folderze "testy". W programie Visual Studio można utworzyć pasujące foldery rozwiązań, jeśli ta organizacja okaże się przydatna.

![Testowanie organizacji w rozwiązaniu](./media/image9-2.png)

**Rysunek 9-2**. Testowanie organizacji w rozwiązaniu

Można użyć struktury testowej, która wolisz. Struktura xUnit działa dobrze i jest to, co wszystkie testy ASP.NET Core i EF Core są zapisywane w. Projekt testu xUnit można dodać w programie Visual Studio przy użyciu szablonu pokazanego na rysunku 9-3 lub z identyfikatora cli przy użyciu . `dotnet new xunit`

![Dodawanie projektu testu xUnit w programie Visual Studio](./media/image9-3.png)

**Rysunek 9-3**. Dodawanie projektu testu xUnit w programie Visual Studio

### <a name="test-naming"></a>Testowanie nazewnictwa

Nazwij testy w spójny sposób, z nazwami, które wskazują, co robi każdy test. Jednym z podejść miałem wielki sukces z jest nazwa klas testowych zgodnie z klasą i metodą, którą testują. Powoduje to wiele małych klas testowych, ale to sprawia, że bardzo jasne, co każdy test jest odpowiedzialny za. Z nazwą klasy testowej skonfigurowanej do identyfikowania klasy i metody, które mają być testowane, nazwa metody testowej może służyć do określenia badanego zachowania. Powinno to obejmować oczekiwane zachowanie i wszelkie dane wejściowe lub założenia, które powinny przynieść to zachowanie. Niektóre przykładowe nazwy testów:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Odmiana tego podejścia kończy każdą nazwę klasy testowej na "Powinien" i nieznacznie modyfikuje czas:

- `CatalogControllerGetImage`**Należy**`.`**zadzwonić**`ImageServiceWithId`

- `CatalogControllerGetImage`**Czy**`.`**zaloguj się**`WarningGivenImageMissingException`

Niektóre zespoły uważają, że drugie podejście do nazewnictwa jest jaśniejsze, choć nieco bardziej szczegółowe. W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testu, tak aby po niepowodzeniu jednego lub więcej testów, jest oczywiste, z ich nazw, jakie przypadki nie powiodło się. Należy unikać nazewnictwa testów niejasno, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy widzisz je w wynikach testów.

Jeśli postępuj zgodnie z konwencją nazewnictwa, taką jak powyższa, która tworzy wiele małych klas testowych, dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i przestrzeni nazw. Rysunek 9-4 przedstawia jedno podejście do organizowania testów według folderu w ramach kilku projektów testowych.

![Organizowanie klas testowych według folderu na podstawie testowanej klasy](./media/image9-4.png)

**Rysunek 9-4.** Organizowanie klas testowych według folderu na podstawie testowanej klasy.

Jeśli określonej klasy aplikacji ma wiele metod testowanych (a tym samym wiele klas testowych), może mieć sens umieszczenie ich w folderze odpowiadającym klasie aplikacji. Ta organizacja nie różni się od sposobu organizowania plików w folderach w innych miejscach. Jeśli masz więcej niż trzy lub cztery powiązane pliki w folderze zawierającym wiele innych plików, często warto przenieść je do własnego podfolderu.

## <a name="unit-testing-aspnet-core-apps"></a>Testowanie jednostek ASP.NET aplikacje Core

W dobrze zaprojektowanej aplikacji ASP.NET Core większość złożoności i logiki biznesowej będzie hermetyzowana w jednostkach biznesowych i różnych usługach. Sama aplikacja ASP.NET Core MVC, z kontrolerami, filtrami, modelami widoków i widokami, powinna wymagać bardzo niewielu testów jednostkowych. Duża część funkcjonalności danej akcji znajduje się poza samą metodą akcji. Sprawdzanie, czy routing działa poprawnie, czy globalna obsługa błędów, nie może być wykonana skutecznie za pomocą testu jednostkowego. Podobnie wszystkie filtry, w tym sprawdzanie poprawności modelu i uwierzytelniania i uwierzytelniania i autoryzacji filtrów, nie może być testowany jednostką z testem kierowania na metodę akcji kontrolera. Bez tych źródeł zachowania większość metod akcji powinna być trywialnie mała, delegując większość ich pracy do usług, które mogą być testowane niezależnie od kontrolera, który ich używa.

Czasami trzeba będzie refaktoryzacji kodu w celu przetestowania jednostkowego. Często wiąże się to z identyfikowaniem abstrakcji i przy użyciu iniekcji zależności, aby uzyskać dostęp do abstrakcji w kodzie, który chcesz przetestować, zamiast kodowania bezpośrednio przeciwko infrastrukturze. Rozważmy na przykład tę prostą metodę działania do wyświetlania obrazów:

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

Testowanie jednostkowe tej metody jest utrudnione przez jej bezpośrednią zależność `System.IO.File`od , którego używa do odczytu z systemu plików. Można przetestować to zachowanie, aby upewnić się, że działa zgodnie z oczekiwaniami, ale robi to z prawdziwymi plikami jest test integracji. Warto zauważyć, że nie można przetestować jednostkowo tej metody trasy - zobaczysz, jak to zrobić z testem funkcjonalnym wkrótce.

Jeśli nie można przetestować jednostkowe zachowanie systemu plików bezpośrednio i nie można przetestować trasę, co jest do przetestowania? Cóż, po refaktoryzacji, aby umożliwić testowanie jednostek, może odkryć niektóre przypadki testowe i brakujące zachowanie, takie jak obsługa błędów. Co robi metoda, gdy plik nie zostanie znaleziony? Co powinien zrobić? W tym przykładzie metoda refaktoryzowana wygląda następująco:

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

`_logger`i `_imageService` są wstrzykiwane jako zależności. Teraz można przetestować, że ten sam identyfikator, który `_imageService`jest przekazywany do metody akcji jest przekazywana do , i że wynikowe bajty są zwracane jako część FileResult. Można również przetestować, że rejestrowanie błędów `NotFound` dzieje się zgodnie z oczekiwaniami i że wynik jest zwracany, jeśli brakuje obrazu, zakładając, że jest to ważne zachowanie aplikacji (to jest nie tylko tymczasowy kod deweloper aplikowany do diagnozowania problemu). Logika rzeczywistego pliku została przeniesiona do oddzielnej usługi implementacji i została rozszerzona w celu zwrócenia wyjątku specyficznego dla aplikacji w przypadku brakującego pliku. Można przetestować tę implementację niezależnie, przy użyciu testu integracji.

W większości przypadków należy użyć globalnych programów obsługi wyjątków w kontrolerach, więc ilość logiki w nich powinna być minimalna i prawdopodobnie nie warto testować jednostkowe. Należy wykonać większość testowania akcji kontrolera przy `TestServer` użyciu testów funkcjonalnych i klasy opisanej poniżej.

## <a name="integration-testing-aspnet-core-apps"></a>Testowanie integracji ASP.NET aplikacje Core

Większość testów integracji w ASP.NET podstawowych aplikacji powinny być testowanie usług i innych typów implementacji zdefiniowanych w projekcie infrastruktury. Na przykład można [przetestować, że EF Core pomyślnie aktualizowanie i pobieranie danych, które można oczekiwać](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od klas dostępu do danych znajdujących się w projekcie infrastruktury. Najlepszym sposobem, aby sprawdzić, czy ASP.NET Core MVC projektu zachowuje się poprawnie jest z testów funkcjonalnych, które są uruchamiane przeciwko aplikacji uruchomionej na hoście testowym.

## <a name="functional-testing-aspnet-core-apps"></a>Testowanie funkcjonalne ASP.NET aplikacje Core

W przypadku ASP.NET `TestServer` podstawowych aplikacji klasa sprawia, że testy funkcjonalne są dość łatwe do napisania. Można skonfigurować `TestServer` przy `WebHostBuilder` użyciu `HostBuilder`(lub ) bezpośrednio (jak zwykle w `WebApplicationFactory` przypadku aplikacji) lub z typem (dostępne od wersji 2.1). Należy spróbować dopasować hosta testowego do hosta produkcyjnego tak ściśle, jak to możliwe, więc testy będą wykonywać zachowanie podobne do tego, co aplikacja zrobi w środowisku produkcyjnym. Klasa `WebApplicationFactory` jest pomocna przy konfigurowaniu contentroot a testservera, który jest używany przez ASP.NET Core do lokalizowania zasobów statycznych, takich jak Widoki.

Proste testy funkcjonalne można utworzyć, tworząc klasę testową, która implementuje IClassFixture\<WebApplicationFactory\<TEntry>> , gdzie TEntry jest klasy startowej aplikacji sieci web. Z tym w miejscu, urządzenie testowe można utworzyć klienta przy użyciu metody CreateClient fabryki:

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

Często należy wykonać dodatkową konfigurację witryny przed każdym uruchomieniu testu, takich jak konfigurowanie aplikacji do korzystania z magazynu danych w pamięci, a następnie rozmieszania aplikacji z danymi testowymi. Aby to zrobić, należy utworzyć własną podklasę WebApplicationFactory\<TEntry> i zastąpić jego ConfigureWebHost metody. Poniższy przykład pochodzi z projektu eShopOnWeb FunctionalTests i jest używany jako część testów w głównej aplikacji sieci web.

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

Testy można użyć tego niestandardowego WebApplicationFactory przy użyciu go do tworzenia klienta, a następnie wykonywanie żądań do aplikacji przy użyciu tego wystąpienia klienta. Aplikacja będzie miała dane seeded, które mogą być używane jako część testu potwierdzeń. Poniższy test sprawdza, czy strona główna aplikacji eShopOnWeb ładuje się poprawnie i zawiera listę produktów, która została dodana do aplikacji jako część danych źródłowych.

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

Ten funkcjonalny test wykonuje pełną ASP.NET Stos aplikacji Core MVC / Razor Pages, w tym wszystkie pośredniczenie, filtry, segregatory itp., które mogą być na miejscu. Sprawdza, czy dana trasa ("/") zwraca oczekiwany kod stanu sukcesu i dane wyjściowe HTML. Czyni to bez konfigurowania prawdziwego serwera www, a więc pozwala uniknąć wiele kruchości, że przy użyciu prawdziwego serwera www do testowania może wystąpić (na przykład problemy z ustawieniami zapory). Testy funkcjonalne, które są uruchamiane przeciwko TestServer są zwykle wolniejsze niż testy integracyjne i jednostkowe, ale są znacznie szybsze niż testy, które można uruchomić za pośrednictwem sieci do serwera sieci web test. Należy użyć testów funkcjonalnych, aby upewnić się, że stos frontonu aplikacji działa zgodnie z oczekiwaniami. Testy te są szczególnie przydatne, gdy znajdziesz duplikacji w kontrolerach lub stron i adres powielania przez dodanie filtrów. W idealnym przypadku to refaktoryzacji nie zmieni zachowanie aplikacji i zestaw testów funkcjonalnych zweryfikuje to jest przypadek.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Referencje — testowanie ASP.NET aplikacje Core MVC
>
> - **Testowanie w ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Konwencja nazewnictwa testu jednostkowego** \
>   <https://ardalis.com/unit-test-naming-convention>
> - **Testowanie rdzenia EF** \
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - **Testy integracji w ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
>[Poprzedni](work-with-data-in-asp-net-core-apps.md)
>[następny](development-process-for-azure.md)
