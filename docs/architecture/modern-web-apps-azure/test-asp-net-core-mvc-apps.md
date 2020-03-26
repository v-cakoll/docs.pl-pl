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
# <a name="test-aspnet-core-mvc-apps"></a>Testowanie aplikacji Core MVC ASP.NET

> *"Jeśli nie lubisz testować produktu w jednostce, najprawdopodobniej twoi klienci również nie będą chcieli go przetestować".*
 > \_- Anonimowy-

Oprogramowanie o dowolnej złożoności może zakończyć się niepowodzeniem w nieoczekiwany sposób w odpowiedzi na zmiany. W związku z tym testowanie po wszczęciem zmian jest wymagane dla wszystkich, ale najbardziej trywialne (lub najmniej krytyczne) aplikacje. Ręczne testowanie jest najwolniejszym, najmniej niezawodnym i najdroższym sposobem testowania oprogramowania. Niestety, jeśli aplikacje nie są zaprojektowane do testowania, może to być jedyny dostępny środek. Wnioski napisane zgodnie z zasadami architektonicznymi określonymi w [rozdziale 4](architectural-principles.md) powinny być sprawdzalne w jednostkach. ASP.NET Aplikacje Core obsługują zautomatyzowaną integrację i testowanie funkcjonalne.

## <a name="kinds-of-automated-tests"></a>Rodzaje zautomatyzowanych testów

Istnieje wiele rodzajów zautomatyzowanych testów dla aplikacji. Najprostszym testem najniższego poziomu jest test jednostkowy. Na nieco wyższym poziomie, istnieją testy integracji i testy funkcjonalne. Inne rodzaje testów, takich jak testy interfejsu użytkownika, testy obciążenia, testy warunków skrajnych i testy dymu, wykraczają poza zakres tego dokumentu.

### <a name="unit-tests"></a>Testy jednostkowe

Test jednostkowy testuje pojedynczą część logiki aplikacji. Można go dalej opisać, wymieniając niektóre rzeczy, które nie są. Test jednostkowy nie testuje, jak kod działa z zależnościami lub infrastrukturą — do czego służą testy integracji. Test jednostkowy nie testuje struktury, na której jest napisany kod — należy założyć, że działa lub, jeśli okaże się, że nie, złóż błąd i kod obejście problemu. Test jednostkowy jest uruchamiany całkowicie w pamięci i w trakcie procesu. Nie komunikuje się z systemem plików, siecią ani bazą danych. Testy jednostkowe należy tylko przetestować kod.

Testy jednostkowe, ze względu na fakt, że testują tylko jedną jednostkę kodu, bez zależności zewnętrznych, należy wykonać bardzo szybko. W związku z tym powinieneś być w stanie uruchomić zestawy testów setek testów jednostkowych w ciągu kilku sekund. Uruchamiaj je często, najlepiej przed każdym wypychaniem do repozytorium kontroli źródła udostępnionego, a na pewno przy każdej zautomatyzowanej kompilacji na serwerze kompilacji.

### <a name="integration-tests"></a>Testy integracji

Chociaż jest to dobry pomysł, aby hermetyzować kod, który współdziała z infrastruktury, takich jak bazy danych i systemy plików, nadal będzie mieć niektóre z tego kodu i prawdopodobnie będzie chcesz go przetestować. Ponadto należy sprawdzić, czy warstwy kodu współdziałają zgodnie z oczekiwaniami, gdy zależności aplikacji zostaną w pełni rozwiązane. Jest to odpowiedzialność za testy integracji. Testy integracji wydają się być wolniejsze i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ często zależą od zależności zewnętrznych i infrastruktury. W związku z tym należy unikać testowania rzeczy, które mogą być testowane za pomocą testów jednostkowych w testach integracji. Jeśli można przetestować dany scenariusz z testu jednostkowego, należy przetestować go za pomocą testu jednostkowego. Jeśli nie możesz, rozważ użycie testu integracji.

Testy integracji często mają bardziej złożone procedury konfiguracji i usuwania niż testy jednostkowe. Na przykład test integracji, który jest sprzeczny z rzeczywistą bazą danych, będzie potrzebował sposobu zwrócenia bazy danych do znanego stanu przed każdym uruchomieniem testu. W miarę dodawania nowych testów i ewoluuje schemat produkcyjnej bazy danych, te skrypty testowe będą miały tendencję do zwiększania rozmiaru i złożoności. W wielu dużych systemach jest niepraktyczne, aby uruchomić pełne zestawy testów integracji na stacjach roboczych deweloperów przed sprawdzeniem zmian w kontroli źródła udostępnionego. W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.

### <a name="functional-tests"></a>Testy funkcjonalne

Testy integracji są zapisywane z punktu widzenia dewelopera, aby sprawdzić, czy niektóre składniki systemu działają poprawnie razem. Testy funkcjonalne są zapisywane z perspektywy użytkownika i weryfikują poprawność systemu na podstawie jego wymagań. Poniższy fragment zawiera użyteczną analogię do myślenia o testach funkcjonalnych w porównaniu z testami jednostkowymi:

> "Wiele razy rozwój systemu jest porównywany do budowy domu. Chociaż ta analogia nie jest całkiem poprawna, możemy rozszerzyć ją w celu zrozumienia różnicy między testami jednostkowymi a funkcjonalnymi. Testy jednostkowe są analogiczne do wizyty inspektora budowlanego na placu budowy domu. Koncentruje się na różnych wewnętrznych systemach domu, fundament, kadrowanie, elektryczne, instalacyjne i tak dalej. Zapewnia (testy), że części domu będą działać poprawnie i bezpiecznie, czyli spełniają kodeks budowlany. Testy funkcjonalne w tym scenariuszu są analogiczne do właściciela domu odwiedzającego ten sam plac budowy. Zakłada on, że systemy wewnętrzne będą zachowywać się odpowiednio, że inspektor budowlany wykonuje swoje zadanie. Właściciel domu koncentruje się na tym, jak to będzie żyć w tym domu. Jest zaniepokojony tym, jak wygląda dom, są różne pokoje wygodny rozmiar, czy dom pasuje do potrzeb rodziny, są okna w dobrym miejscu, aby złapać poranne słońce. Właściciel domu przeprowadza testy funkcjonalne w domu. Ma perspektywę użytkownika. Inspektor budowlany przeprowadza testy jednostkowe w domu. Ma perspektywę budowniczego."

Źródło: [Testy jednostkowe a testy funkcjonalne](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Lubię mówić: "Jako deweloperzy zawodzimy na dwa sposoby: budujemy coś złego, albo budujemy coś złego". Testy jednostkowe zapewniają, że budujesz rzecz dobrze; testy funkcjonalne zapewniają, że budujesz właściwą rzecz.

Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewnego stopnia automatyzacji interfejsu użytkownika. Podobnie jak testy integracji, zwykle działają z pewnego rodzaju infrastruktury testowej, jak również. To sprawia, że są wolniejsze i bardziej kruche niż testy jednostki i integracji. Powinieneś mieć tylko tyle testów funkcjonalnych, ile trzeba mieć pewność, że system zachowuje się zgodnie z oczekiwaniami użytkowników.

### <a name="testing-pyramid"></a>Piramida badań

Martin Fowler napisał o piramidzie testowej, której przykład pokazano na rysunku 9-1.

![Piramida badań](./media/image9-1.png)

**Rysunek 9-1**. Piramida badań

Różne warstwy ostrosłupa i ich względne rozmiary reprezentują różne rodzaje testów i ile należy napisać dla aplikacji. Jak widać, zalecenie jest mieć dużą bazę testów jednostkowych, obsługiwane przez mniejszą warstwę testów integracji, z jeszcze mniejszą warstwą testów funkcjonalnych. Każda warstwa powinna być w idealnym miejscu tylko testy, które nie mogą być wykonywane odpowiednio w dolnej warstwie. Należy pamiętać o piramidzie testowania, gdy próbujesz zdecydować, jakiego rodzaju testu potrzebujesz dla określonego scenariusza.

### <a name="what-to-test"></a>Co przetestować

Częstym problemem dla deweloperów, którzy są niedoświadczeni z pisania zautomatyzowanych testów jest wymyślanie, co do testowania. Dobrym punktem wyjścia jest przetestowanie logiki warunkowej. Gdziekolwiek masz metodę z zachowaniem, które zmienia się na podstawie instrukcji warunkowej (if-else, switch, itd.), powinieneś być w stanie wymyślić co najmniej kilka testów, które potwierdzają poprawne zachowanie dla niektórych warunków. Jeśli kod ma warunki błędu, dobrze jest napisać co najmniej jeden test dla "ścieżki happy" za pośrednictwem kodu (bez błędów) i co najmniej jeden test dla "smutnej ścieżki" (z błędami lub nietypowymi wynikami), aby potwierdzić, że aplikacja zachowuje się zgodnie z oczekiwaniami w obliczu błędów. Na koniec spróbuj skupić się na testowaniu rzeczy, które mogą zakończyć się niepowodzeniem, zamiast skupiać się na metryki, takie jak pokrycie kodu. Większy zasięg kodu jest lepszy niż mniej, ogólnie. Jednak pisanie kilku testów złożonej i krytycznej dla firmy metody jest zwykle lepsze wykorzystanie czasu niż pisanie testów dla właściwości auto tylko w celu poprawy metryki pokrycia kodu testu.

## <a name="organizing-test-projects"></a>Organizowanie projektów testowych

Projekty testowe mogą być organizowane jednak najlepiej dla Ciebie. Dobrym pomysłem jest oddzielenie testów według typu (test jednostkowy, test integracji) i przez co są one testujące (według projektu, według przestrzeni nazw). Czy ta separacja składa się z folderów w ramach jednego projektu testowego lub wielu projektów testowych, jest decyzja projektowa. Jeden projekt jest najprostszy, ale dla dużych projektów z wieloma testami lub w celu łatwiejszego uruchamiania różnych zestawów testów, można mieć kilka różnych projektów testowych. Wiele zespołów organizuje projekty testowe na podstawie projektu, który testuje, co dla aplikacji z więcej niż kilkoma projektami może spowodować dużą liczbę projektów testowych, zwłaszcza jeśli nadal je rozbijesz zgodnie z rodzajem testów w każdym projekcie. Podejście kompromisowe jest mieć jeden projekt na rodzaj testu, dla aplikacji, z folderów wewnątrz projektów testowych, aby wskazać projekt (i klasy) testowane.

Wspólne podejście polega na organizowaniu projektów aplikacji w folderze "src", a projekty testowe aplikacji w równoległym folderze "testowym". W programie Visual Studio można utworzyć pasujące foldery rozwiązań, jeśli ta organizacja jest przydatna.

![Testowanie organizacji w rozwiązaniu](./media/image9-2.png)

**Rysunek 9-2**. Testowanie organizacji w rozwiązaniu

Możesz użyć dowolnej struktury testowej, którą wolisz. Struktura xUnit działa dobrze i jest to, co wszystkie ASP.NET Core i EF Core testy są zapisywane w. Projekt testu xUnit można dodać w programie Visual Studio przy użyciu szablonu przedstawionego `dotnet new xunit`na rysunku 9-3 lub z interfejsu wiersza polecenia przy użyciu pliku .

![Dodawanie projektu testowego xUnit w programie Visual Studio](./media/image9-3.png)

**Rysunek 9-3**. Dodawanie projektu testowego xUnit w programie Visual Studio

### <a name="test-naming"></a>Nazewnictwo testowe

Nazwij testy w spójny sposób, z nazwami wskazującymi, co robi każdy test. Jednym z podejść miałem wielki sukces jest nazwać klasy testowe zgodnie z klasą i metodą, które testują. Powoduje to wiele małych klas testowych, ale to sprawia, że bardzo jasne, co każdy test jest odpowiedzialny za. Z nazwą klasy testowej skonfigurowaną w celu zidentyfikowania klasy i metody, która ma być testowana, można użyć nazwy metody testowej do określenia testowanego zachowania. Powinno to obejmować oczekiwane zachowanie i wszelkie dane wejściowe lub założenia, które powinny przynieść to zachowanie. Przykładowe nazwy testów:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Odmiana tego podejścia kończy każdą nazwę klasy testu z "Powinien" i nieznacznie modyfikuje czas:

- `CatalogControllerGetImage`**Należy**`.`**zadzwonić**`ImageServiceWithId`

- `CatalogControllerGetImage`**Należy**`.`**dziennik**`WarningGivenImageMissingException`

Niektóre zespoły uważają drugie podejście do nazewnictwa za jaśniejsze, choć nieco bardziej pełne. W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testu, tak aby gdy jeden lub więcej testów zakończy się niepowodzeniem, jest oczywiste z ich nazw, jakie przypadki nie powiodły się. Należy unikać nazywania testów niejasno, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy widzisz je w wynikach testów.

Jeśli zastosujesz się do konwencji nazewnictwa, takiej jak ta powyżej, która tworzy wiele małych klas testowych, dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i obszarów nazw. Rysunek 9-4 przedstawia jedno podejście do organizowania testów według folderów w ramach kilku projektów testowych.

![Organizowanie klas testowych według folderów na podstawie testowanych klas](./media/image9-4.png)

**Rysunek 9-4.** Organizowanie klas testowych według folderów na podstawie testowanych klas.

Jeśli klasa określonej aplikacji ma wiele metod testowanych (a tym samym wiele klas testowych), może mieć sens, aby umieścić je w folderze odpowiadającym klasie aplikacji. Ta organizacja nie różni się od sposobu organizowania plików w folderach w innym miejscu. Jeśli w folderze zawierającym wiele innych plików znajdują się więcej niż trzy lub cztery powiązane pliki, często warto przenieść je do własnego podfolderu.

## <a name="unit-testing-aspnet-core-apps"></a>Testowanie jednostek ASP.NET aplikacje Core

W dobrze zaprojektowanej aplikacji ASP.NET Core większość złożoności i logiki biznesowej będzie hermetyzowana w jednostkach biznesowych i różnych usługach. Sama aplikacja Core MVC ASP.NET z kontrolerami, filtrami, modułami widokowymi i widokami powinna wymagać bardzo niewielu testów jednostkowych. Wiele funkcji danej akcji leży poza samą metodą działania. Testowanie, czy routing działa poprawnie lub globalnej obsługi błędów, nie można wykonać skutecznie za pomocą testu jednostkowego. Podobnie wszystkie filtry, w tym sprawdzanie poprawności modelu i filtry uwierzytelniania i autoryzacji, nie mogą być testowane jednostkowo za pomocą testu docelowego metody akcji kontrolera. Bez tych źródeł zachowania większość metod akcji powinny być trywialnie małe, delegowanie większość ich pracy do usług, które mogą być testowane niezależnie od kontrolera, który ich używa.

Czasami trzeba refaktoryzuje kod w celu przetestowania jednostki. Często wiąże się to z identyfikowaniem abstrakcji i przy użyciu iniekcji zależności, aby uzyskać dostęp do abstrakcji w kodzie, który chcesz przetestować, a nie kodowania bezpośrednio względem infrastruktury. Rozważmy na przykład tę prostą metodę działania do wyświetlania obrazów:

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

Testowanie jednostkowe tej metody jest utrudnione przez jej bezpośrednią zależność od `System.IO.File`, który używa do odczytu z systemu plików. Można przetestować to zachowanie, aby upewnić się, że działa zgodnie z oczekiwaniami, ale w ten sposób z rzeczywistymi plikami jest test integracji. Warto zauważyć, że nie można jednostki przetestować trasę tej metody - zobaczysz, jak to zrobić z testu funkcjonalnego wkrótce.

Jeśli nie można jednostki przetestować zachowanie systemu plików bezpośrednio, a nie można przetestować trasę, co jest tam, aby przetestować? Cóż, po refaktoryzacji, aby umożliwić testowanie jednostkowe, można odkryć niektóre przypadki testowe i brakujące zachowanie, takie jak obsługa błędów. Do czego polega ta metoda, gdy plik nie zostanie znaleziony? Co powinien zrobić? W tym przykładzie metoda refaktoryzowana wygląda następująco:

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

`_logger`i `_imageService` są wstrzykiwane jako zależności. Teraz można przetestować, że ten sam identyfikator, który `_imageService`jest przekazywany do metody akcji jest przekazywana do , i że wynikowe bajty są zwracane jako część FileResult. Można również przetestować, że rejestrowanie błędów `NotFound` odbywa się zgodnie z oczekiwaniami i że wynik jest zwracany, jeśli brakuje obrazu, przy założeniu, że jest to ważne zachowanie aplikacji (oznacza to, że nie tylko kod tymczasowy dodany przez dewelopera w celu zdiagnozowania problemu). Logika rzeczywistego pliku została przeniesiona do oddzielnej usługi implementacji i została rozszerzona, aby zwrócić wyjątek specyficzny dla aplikacji w przypadku brakującego pliku. Tę implementację można przetestować niezależnie, przy użyciu testu integracji.

W większości przypadków należy użyć globalnych programów obsługi wyjątków w kontrolerach, więc ilość logiki w nich powinna być minimalna i prawdopodobnie nie warto testowania jednostkowego. Wykonaj większość akcji testowania kontrolera przy `TestServer` użyciu testów funkcjonalnych i klasy opisanej poniżej.

## <a name="integration-testing-aspnet-core-apps"></a>Testowanie integracji ASP.NET aplikacjami Core

Większość testów integracji w aplikacjach ASP.NET Core powinny być testowanie usług i innych typów implementacji zdefiniowanych w projekcie infrastruktury. Na przykład można [przetestować, że EF Core został pomyślnie aktualizowanie i pobieranie danych, których oczekujesz](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od klas dostępu do danych zamieszkałych w projekcie infrastruktury. Najlepszym sposobem, aby sprawdzić, czy ASP.NET core projektu MVC zachowuje się poprawnie jest z testów funkcjonalnych, które są uruchamiane przeciwko aplikacji uruchomionej na hoście testowym.

## <a name="functional-testing-aspnet-core-apps"></a>Testowanie funkcjonalne ASP.NET aplikacje Core

W przypadku aplikacji ASP.NET Core `TestServer` klasa sprawia, że testy funkcjonalne są dość łatwe do zapisania. Można skonfigurować `TestServer` przy `WebHostBuilder` użyciu `HostBuilder`(lub) bezpośrednio (jak zwykle w przypadku `WebApplicationFactory` aplikacji) lub z typem (dostępne od wersji 2.1). Spróbuj dopasować hosta testowego do hosta produkcyjnego tak ściśle, jak to możliwe, więc testy zachowania ćwiczeń podobne do tego, co aplikacja zrobi w produkcji. Klasa `WebApplicationFactory` jest przydatna do konfigurowania ContentRoot Serwera TestServer, który jest używany przez ASP.NET Core do lokalizowania statycznych zasobów, takich jak widoki.

Można utworzyć proste testy funkcjonalne, tworząc klasę testową, która implementuje IClassFixture\<WebApplicationFactory\<TEntry>> gdzie TEntry jest klasy uruchamiania aplikacji sieci web. Dzięki temu urządzenie testowe może utworzyć klienta przy użyciu fabrycznej metody CreateClient:

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

Często należy wykonać dodatkową konfigurację witryny przed każdym przebiegiem testu, na przykład konfigurowanie aplikacji do używania magazynu danych w pamięci, a następnie wysiewanie aplikacji danymi testowymi. Aby to zrobić, należy utworzyć własną podklasę\<WebApplicationFactory TEntry> i zastąpić jego ConfigureWebHost metody. Poniższy przykład pochodzi z projektu eShopOnWeb FunctionalTests i jest używany jako część testów w głównej aplikacji sieci web.

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

Testy można użyć tego niestandardowego WebApplicationFactory za pomocą go do utworzenia klienta, a następnie żądania do aplikacji przy użyciu tego wystąpienia klienta. Aplikacja będzie miała rozstawione dane, które mogą być używane jako część potwierdzeń testu. Poniższy test sprawdza, czy strona główna aplikacji eShopOnWeb ładuje się poprawnie i zawiera listę produktów, która została dodana do aplikacji jako część danych źródłowych.

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

Ten test funkcjonalny wykonuje pełną ASP.NET stosu aplikacji Core MVC / Razor Pages, w tym wszystkie oprogramowanie pośredniczące, filtry, segregatory itp., które mogą być na miejscu. Sprawdza, czy dana trasa ("/") zwraca kod stanu oczekiwanego powodzenia i dane wyjściowe HTML. Robi to bez konfigurowania prawdziwego serwera www, a więc unika wiele kruchości, że przy użyciu prawdziwego serwera www do testowania może wystąpić (na przykład problemy z ustawieniami zapory). Testy funkcjonalne uruchamiane w testserverze są zwykle wolniejsze niż testy integracyjne i jednostkowe, ale są znacznie szybsze niż testy, które byłyby uruchamiane przez sieć na testowym serwerze sieci web. Użyj testów funkcjonalnych, aby upewnić się, że stos frontonu aplikacji działa zgodnie z oczekiwaniami. Testy te są szczególnie przydatne, gdy znajdziesz powielanie w kontrolerach lub stronach i adres duplikacji przez dodanie filtrów. W idealnym przypadku to refaktoryzowanie nie zmieni zachowania aplikacji, a zestaw testów funkcjonalnych zweryfikuje, że tak jest.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Referencje — test ASP.NET aplikacje Core MVC
>
> - **Testowanie w ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Konwencja nazewnictwa testów jednostek** \
>   <https://ardalis.com/unit-test-naming-convention>
> - **Testowanie rdzenia EF** \
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - **Testy integracji w ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
>[Poprzedni](work-with-data-in-asp-net-core-apps.md)
>[następny](development-process-for-azure.md)
