---
title: Testowanie platformy ASP.NET Core MVC aplikacji
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Testowanie aplikacji ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: b6c881a445f5848829ab5ccc6ce8547a390d89f3
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404622"
---
# <a name="test-aspnet-core-mvc-apps"></a>Testowanie platformy ASP.NET Core MVC aplikacji

> *"Jeśli nie potrzebujesz produktu testy jednostkowe, najprawdopodobniej klienci nie będą, takich jak do testowania, albo."*
 > \_-Anonimowe-

Oprogramowanie o dowolnej złożoności może zakończyć się niepowodzeniem w nieoczekiwany sposób w odpowiedzi na zmiany. W związku z tym testowanie po wprowadzeniu zmian jest wymagana dla wszystkich pól poza najbardziej proste (lub najmniej krytyczne) aplikacji. Testowanie ręczne jest najwolniejsze, zawodnych, najbardziej kosztowne sposób testowania oprogramowania. Niestety Jeśli aplikacje nie mogą być sprawdzalnego działa zgodnie, może być tylko dostępnych środków. Aplikacje napisane następujące zasady dotyczące architektury rozmieszczony w rozdziale X powinna być jednostki sprawdzalnego działa zgodnie i aplikacje platformy ASP.NET Core obsługują automatyczne integracji i testowania funkcjonalnego także.

## <a name="kinds-of-automated-tests"></a>Rodzaje testów automatycznych

Istnieje wiele rodzajów testów automatycznych z aplikacjami. Najprostszy, najniższego poziomu testu jest test jednostkowy. Nieco wyższym poziomie istnieją testy integracji i testów funkcjonalnych. Inne rodzaje testów, takich jak testy interfejsu użytkownika, testy obciążeniowe, testy obciążeniowe i testów dymu wykraczają poza zakres tego dokumentu.

### <a name="unit-tests"></a>Testy jednostkowe

Test jednostkowy testy pojedynczą częścią Twojej aplikacji logiki. Jeden można dodatkowo opisać, wyświetlając listę kilka rzeczy, które nie jest. Test jednostkowy nie sprawdza, jak Twoje kod działa z zależności lub infrastruktury — integracja testy dotyczą. Test jednostkowy nie test framework, którą Twój kod jest zapisywany na — należy założyć, że jego działania lub, jeśli możesz znaleźć nie, Zgłoś usterkę i kodu obejścia tego problemu. Test jednostkowy jest wykonywany w całości w pamięci i w procesie. Nie będzie komunikować się z systemu plików, sieci lub bazy danych. Testy jednostkowe należy przetestować tylko Twój kod.

Testy jednostkowe, ze względu na fakt, przetestować pojedynczą jednostkę kodu, bez zewnętrznych zależności mają być wykonywane bardzo szybko. W związku z tym można uruchomić zestawy testów z setek testów jednostkowych w ciągu kilku sekund. Uruchom je często, najlepiej przed każdym wypychania do repozytorium kontroli źródła udostępnionego, a także bez obaw z każdą kompilacją automatycznych na serwerze kompilacji.

### <a name="integration-tests"></a>Testy integracji

Chociaż jest to dobry pomysł, aby hermetyzować swój kod, który współdziała z infrastrukturą, takich jak bazy danych i systemy plików, będą nadal mieć część kodu, i prawdopodobnie warto go przetestować. Ponadto należy sprawdzić, czy warstwy kodu wchodzić w interakcje w oczekiwany sposób w przypadku w pełni rozpoznać zależności aplikacji. Jest to odpowiedzialność testów integracji. Testy integracji zwykle być wolniejszy i trudniejsze do skonfigurowania niż testy jednostkowe, ponieważ są one często są zależne od zależności zewnętrzne i infrastruktury. W związku z tym należy unikać różne rzeczy, które mogłyby zostać testów przy użyciu testów jednostkowych w testów integracji. Jeśli danego scenariusza można przetestować za pomocą testu jednostkowego, należy go przetestować, za pomocą testu jednostkowego. Jeśli nie jest możliwe, rozważ użycie wiąże się test integracji.

Testy integracji mają często bardziej złożone ustawienia i procedury usuwania niż testy jednostkowe. Na przykład test integracji, który przechodzi z istniejącej bazy danych należy sposób, aby przywrócić bazę danych do znanego stanu przed każdym przebiegu testu. Jak są dodawane nowe testy i schemat bazy danych w środowisku produkcyjnym rozwoju, testów, te skrypty będą przeważnie zwiększanie się rozmiaru i złożoności. W wielu dużych systemach jest niepraktyczne uruchomić pełne zestawy testów integracyjnych na stanowisko pracy dewelopera przed zaewidencjonowaniem zmiany do kontroli źródła udostępnionych. W takich przypadkach testy integracji mogą być uruchamiane na serwerze kompilacji.

Klasa implementacji LocalFileImageService implementuje logikę pobierania i zwracania bajtów w pliku obrazu z określonego folderu podany identyfikator:

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

### <a name="functional-tests"></a>Testy funkcjonalne

Testy integracji są zapisywane z perspektywy deweloperów, aby sprawdzić, czy niektóre składniki systemu poprawnie współpracują ze sobą. Testy funkcjonalne są zapisywane z punktu widzenia użytkownika i sprawdź poprawność systemu zależy od jego potrzeb. Poniższy fragment oferuje przydatne w sposób analogiczny, jak wziąć pod uwagę testów funkcjonalnych w porównaniu do testów jednostkowych:

> "Wiele razy rozwój systemu przyrównać do budowania domu. Chociaż w ten sposób analogiczny, nie jest jeszcze prawidłowy, firma Microsoft można rozszerzyć na potrzeby rozróżnienie między jednostkowych i testów funkcjonalnych. Testy jednostkowe jest analogiczne do Inspektora budynku, odwiedzając witrynę konstrukcji domu. Koncentruje się na różnych systemów wewnętrznych domu podstawę formułowanie, elektryczny, wodociągów i tak dalej. Zapewnia on (testy), czy części domu będą działać poprawnie i bezpiecznie, oznacza to, że spełniają kod tworzenia. Testy funkcjonalne w tym scenariuszu są analogiczne do właściciel tej samej witrynie konstrukcji. Zakłada on, systemami wewnętrznymi działają prawidłowo, czy inspektor budynku działa jego zadań. Właściciel koncentruje się na co będzie podobnie jak w tym dom na żywo. On dotyczy wygląd domu, różnych pomieszczeniach komfortowo, jednocześnie rozmiar, jest domu potrzeb rodziny, są okna w dobre miejsce, gdzie możesz przechwytywać sun rano. Właściciel wykonuje testy funkcjonalne w domu. Ma on perspektywy użytkownika. Inspektor budynku wykonuje testy jednostkowe w domu. Ma on konstruktora perspektywy."

Źródło: [Unit Testing i testy funkcjonalne](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Jestem fond z informacją o tym "jako programiści, firma Microsoft nie na dwa sposoby: wbudowana niewłaściwej kolejności lub wbudowana nic złego." Testy jednostkowe upewnij się, że tworzysz rzecz po prawej stronie; testy funkcjonalne upewnij się, że tworzysz właściwe.

Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewien stopień automatyzacji interfejsu użytkownika. Takie jak testy integracji zazwyczaj pracują z pewnego rodzaju także infrastrukturę testowania. Z tego powodu wolniejszy i bardziej kruchy niż testy jednostkowe i integracji. Użytkownik powinien mieć tylko tyle testy funkcjonalne, ponieważ muszą mieć pewność, system zachowuje się zgodnie z oczekiwaniami użytkowników.

### <a name="testing-pyramid"></a>Testowanie ostrosłupowy

Zapisano Martina Fowlera o ostrosłupowy testowania, przykład jest wyświetlany w rysunek 9-1.

![](./media/image9-1.png)

Rysunek 9-1 testowania ostrosłupowy

Różne warstwy ostrosłupa i ich względne rozmiary reprezentują różne rodzaje testów i ile należy wpisać dla swojej aplikacji. Jak widać, zaleca się mieć duży podstawą testów jednostkowych, obsługiwany przez warstwę mniejszych testy integracji z mniejszych warstwą testy funkcjonalne. Każda warstwa najlepiej mają tylko testy, których nie można wykonać operacji odpowiednio w niższej warstwie. Gdy próbujesz określić, jakiego rodzaju badań potrzebne dla danego scenariusza, należy pamiętać o testowania ostrosłupa.

### <a name="what-to-test"></a>Co należy przetestować

Typowy problem dla deweloperów, którzy są niedoświadczonej pisanie zautomatyzowanych testów jest pojawi się z tym, co do testowania. To dobry punkt wyjścia do testowania logikę warunkową. Dowolnym masz metody z zachowaniem, które zmiany oparte na instrukcji warunkowej (if-else, Przełącz itp.), powinno być możliwe, co pozwoli uzyskać co najmniej kilka testów potwierdzających poprawnego zachowania w pewnych warunkach. Jeśli kod zawiera błędy, dobrze jest zapisać co najmniej jeden test do "pożądaną ścieżkę" przez kod (z bez błędów) i co najmniej jeden test "sad ścieżki" (z błędów lub nietypowych wyników) upewnij się, że Twoja aplikacja działa zgodnie z oczekiwaniami w przypadku błędów. Ponadto spróbuj skupić się na różne rzeczy, które może zakończyć się niepowodzeniem, zamiast koncentrowania się na metryki, takie jak pokrycie kodu. Ogólnie jest lepsze niż, mniejsze więcej pokrycia kodu. Pisanie kilka więcej testów metody bardzo złożone i krytyczne dla prowadzonej działalności jest jednak zazwyczaj lepszego wykorzystania czasu niż pisania testów dla właściwości auto tylko w celu poprawy metryki pokrycie kodu testu.

## <a name="organizing-test-projects"></a>Organizowanie projektów testowych

Projekty testowe można organizować, jednak działa najlepiej dla Ciebie. To dobry pomysł, aby rozdzielić testy według typów (test jednostkowy, test integracji) i jakie poddawanego testom (według projektu, obszaru nazw). Czy ta separacja składa się z folderów w ramach projektu testowego jednego lub wielu projektów testów jest decyzję projektową. Najprościej jest jednym projektem, ale dla dużych projektów za pomocą wielu testów lub aby można było łatwiej uruchomić różne zestawy testów, możesz chcieć mieć kilka projektów testowych różnych. Wiele zespołów organizowanie projektów testów opartych na projekt, który poddawanego testom, którym dla aplikacji przy użyciu więcej niż kilku projektów może skutkować dużą liczbę projektów testowych, zwłaszcza wtedy, gdy użytkownik nadal podziału je według rodzaju testy są w każdym projekcie. To podejście naruszenia zabezpieczeń jest jednym projektem na rodzaj testu w każdej aplikacji, za pomocą folderów w folderze projektów testowych, aby wskazać testowanego projektu (i klasy).

Typowym podejściem jest do organizowania projektów aplikacji w obszarze folderu "src" i projekty testowe aplikacji w ramach równoległego folderu "testów". W programie Visual Studio, można utworzyć pasujących folderów rozwiązania, jeśli okaże się tej organizacji przydatne.

![](./media/image9-2.png)

Rysunek 9-2 Test organizacji w rozwiązaniu

Możesz użyć różnych platform testowych, które użytkownik sobie tego życzy. XUnit framework działa dobrze i to wszystkie testy w ASP.NET Core i programem EF Core są zapisywane. W programie Visual Studio przy użyciu szablonu, pokazane w rysunek 9-3 lub z interfejsu wiersza polecenia przy użyciu nowego xunit dotnet, możesz dodać projekt testu xUnit.

![](./media/image9-3.png)

Rysunek 9-3. Dodaj projekt testu xUnit w programie Visual Studio

### <a name="test-naming"></a>Nazwy testu

Testy w sposób spójny, należy nadać nazwę przy użyciu nazwy na wskazujące na to, co oznacza każdy test. Jest jednym z podejść miałem doskonałe zakończone sukcesem nazwy klas testowych zgodnie z klasy i metody, które poddawanego testom. Powoduje to wiele klas mały test, ale zapewnia bardzo jasne, co to jest odpowiedzialny za każdego testu. Przy użyciu nazwy klasy testu, ustawić, aby zidentyfikować klasę i metodę ma zostać przetestowana Nazwa metody testu może służyć do określania zachowania poddawana testom. Powinno to obejmować oczekiwane zachowanie i dane wejściowe lub założenia, które powinny to zachowanie. Niektóre przykładowe nazwy testu:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Odmiana tej metody kończy każda nazwa klasy testu za pomocą "Powinien" i modyfikuje nieco czasu teraźniejszego:

- `CatalogControllerGetImage`**Należy**`.`**wywołania**`ImageServiceWithId`

- `CatalogControllerGetImage`**Należy**`.`**dziennika**`WarningGivenImageMissingException`

Niektóre zespoły znaleźć drugiego podejścia nazewnictwa bardziej zrozumiały, jednak nieco bardziej szczegółowy. W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w zachowanie testów, tak, że gdy co najmniej jeden test nie powiedzie się, jest oczywiste, z ich nazw, w jakich sytuacjach nie powiodło się. Unikaj nazewnictwa możesz testy vaguely, takich jak ControllerTests.Test1, ponieważ oferują one żadnej wartości, gdy zostanie wyświetlony w wynikach testu.

Jeśli zgodne z konwencją nazewnictwa, takie jak ten powyżej, tworzy wiele klas mały test, jest dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i obszarów nazw. Jedno z podejść do organizowania testów według folderów w ramach kilku projektów testowych pokazano na rysunku 9-4.

![](./media/image9-4.png)

**Rysunek 9 – 4.** Organizowanie klas testowych według folderów na podstawie klasy poddawana testom.

Oczywiście jeśli klasy określonej aplikacji ma wiele metod poddawana testom (a zatem klas wiele testów) rozsądne może okazać się umieścić je w folderze odpowiadający klasy aplikacji. Ta organizacja nie różni się od sposobu może organizowania plików w folderach w innym miejscu. Jeśli masz więcej niż trzy lub cztery powiązane pliki w folderze zawierających wiele plików, często jest przydatne przenieść je do ich własnych podfolderu.

## <a name="unit-testing-aspnet-core-apps"></a>Jednostki testowania aplikacji platformy ASP.NET Core

W dobrze zaprojektowana aplikacja platformy ASP.NET Core większość złożoności i logikę biznesową, będzie można hermetyzować w podmioty gospodarcze i różnych usług. Aplikacji ASP.NET Core MVC, za pomocą kontrolerów, filtry, modele widoków i widoki, wymagać bardzo mało testów jednostkowych. Wiele funkcji danej akcji znajduje się poza sama metoda akcji. Sprawdzenie, czy routing działa prawidłowo lub obsługi błędu globalnego nie można wykonać skutecznie z testu jednostkowego. Podobnie wszelkie filtry, takimi jak sprawdzanie poprawności modelu i uwierzytelnianie i filtry autoryzacji nie może być testowane jednostki. Bez tych źródeł zachowanie większość metod akcji powinna być w przypadku małych delegowanie duża część swojej pracy z usługami, które mogą być testowane niezależne od kontrolera, który używa tych.

Czasami musisz Refaktoryzacja kodu w kolejności do testów jednostkowych. Często obejmuje to identyfikowanie abstrakcje i otwieranie abstrakcji w kodzie, który chcesz przetestować za pomocą iniekcji zależności, a nie kodu bezpośrednio w odniesieniu do infrastruktury. Rozważmy na przykład tej metody prostej akcji do wyświetlania obrazów:

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

Ta metoda testowania jednostek składa się trudne bezpośrednie zależne od System.IO.File, która jest używana do odczytu z systemu plików. Można przetestować tego zachowania, aby upewnić się, działa zgodnie z oczekiwaniami, ale wiąże się test integracji to działanie za pomocą rzeczywistych plików. Warto zauważyć, nie można przetestować tę metodę trasy — pokazano, jak można to zrobić za pomocą testu funkcjonalnego wkrótce.

Jeśli test jednostkowy zachowanie systemu plików nie można bezpośrednio, a nie Testuj trasę, co jest do testowania? Również po refaktoryzacji, aby umożliwić testy jednostkowe, użytkownik może stwierdzić, niektóre przypadki testowe i Brak zachowania, na przykład obsługa błędów. Do czego służy metoda? Jeśli nie odnaleziono pliku Co ona zrobić? W tym przykładzie metoda wycofanej wygląda następująco:

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

\_Rejestratora i \_imageService są zarówno wprowadzane jako zależności. Teraz możesz sprawdzić, czy ten sam identyfikator, który jest przekazywany do metody akcji jest przekazywany do \_imageService, oraz że wynikowy bajtów są zwracane jako część FileResult. Możesz także testować wykonywane rejestrowanie błędów zgodnie z oczekiwaniami i że wynik NotFound jest zwracany, jeśli obraz jest nieobecne, przy założeniu, że jest to ważna aplikacja zachowanie (oznacza to, nie tylko tymczasowe kod dewelopera dodane do zdiagnozowania problemu). Logika rzeczywisty plik został przeniesiony do oddzielnych implementacji usługi i został uzupełniony do zwrócenia wyjątku specyficzne dla aplikacji w przypadku brakujących plików. Możesz przetestować tę implementację niezależnie, za pomocą wiąże się test integracji.

## <a name="integration-testing-aspnet-core-apps"></a>Testowanie aplikacji platformy ASP.NET Core integracji

Aby sprawdzić, czy LocalFileImageService działa poprawnie za pomocą testu integraiton, należy utworzyć plik obrazu znanych testu i sprawdź, czy usługa zwraca ona określone dane wejściowe podane. Należy zadbać nie należy używać makiety obiektów na zachowanie, które faktycznie chcesz przetestować (w tym przypadku odczytu z systemu plików). Jednak obiekty makiety nadal może być przydatne do skonfigurowania testów integracji. W takim przypadku można testowanie IHostingEnvironment tak, aby jego ContentRootPath wskazuje folder, który zamierzasz na użytek obraz testu. Pełne klasy testowej integracji pracy jest następujący:

```csharp
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";

    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }

    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
        var location = System.Reflection.Assembly.GetEntryAssembly().Location;
        return Path.GetDirectoryName(location);
    }

    [Fact]
    public void ReturnsFileContentResultGivenValidId()
    {
        var fileService = new LocalFileImageService(_mockEnvironment.Object);
        var result = fileService.GetImageBytesById(_testImageId);
        Assert.Equal(_testBytes, result);
    }
}
```

> [!NOTE]
> Badanie jest bardzo proste — duża część kodu jest niezbędne do konfiguracji systemu oraz tworzenie infrastruktury testów (w tym przypadku rzeczywistego pliku do odczytu z dysku). To jest typowe dla testów integracji, które często wymagają bardziej złożonych czynności niż testy jednostkowe.

## <a name="functional-testing-aspnet-core-apps"></a>Funkcjonalności testowanie aplikacji platformy ASP.NET Core

W przypadku aplikacji platformy ASP.NET Core klasy elementu TestServer sprawia, że testy funkcjonalne stosunkowo łatwa do zapisania. Konfigurowanie elementu TestServer bezpośrednio za pomocą WebHostBuilder (tak jak zwykle dla aplikacji), lub z typem WebApplicationFactory (dostępne w 2.1). Należy starać jako najdokładniej dopasować hosta testów do hosta produkcji, aby testy wykonują zachowanie podobne do aplikacji wykona w środowisku produkcyjnym. Klasa WebApplicationFactory jest przydatne w przypadku konfigurowania elementu TestServer ContentRoot, który jest używany przez platformy ASP.NET Core można zlokalizować statycznych zasobów, takich jak widoki.

Można utworzyć proste testy funkcjonalne, tworząc klasy testowej, który implementuje IClassFixture < WebApplicationFactory<TEntry>> gdzie TEntry jest klasa uruchamiania aplikacji sieci web. Dzięki temu w miejscu Twoje warunki początkowe testu można utworzyć klienta przy użyciu metody CreateClient fabryka jest:

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

Często, należy wykonać pewne dodatkowe czynności konfiguracyjne witryny, przed uruchomieniem każdego testu, takie jak konfigurowanie aplikacji do korzystania z pamięci magazynu danych, a następnie rozmieszczania aplikacji z danymi. Aby to zrobić, należy utworzyć własną podklasę klasy WebApplicationFactory<TEntry> i jej metoda ConfigureWebHost musi zostać zastąpiona. W poniższym przykładzie pochodzi z projektu FunctionalTests eShopOnWeb i jest używana jako część testów aplikacji sieci web głównego.

```cs
using Infrastructure.Data;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.eShopWeb;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;
using Microsoft.EntityFrameworkCore;
using Infrastructure.Identity;

namespace FunctionalTests.WebRazorPages
{
    public class CustomWebRazorPagesApplicationFactory<TStartup>
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
                        .GetRequiredService<ILogger<CustomWebRazorPagesApplicationFactory<TStartup>>>();

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

Testy można skorzystać z tego niestandardowego WebApplicationFactory przez użyciem jej do utworzenia klienta i następnie zgłasza żądania do aplikacji przy użyciu tego wystąpienia klienta. Aplikacja będzie miała zasilany danych, który może służyć jako część testu potwierdzenia. Ten test sprawdza, czy strony głównej eShopOnWeb stron Razor aplikacji poprawnie ładowana i zawiera listę produktów, który został dodany do aplikacji jako część danych inicjatora.

```cs
using Microsoft.eShopWeb.RazorPages;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebRazorPagesApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebRazorPagesApplicationFactory<Startup> factory)
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
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse); // from seed data
        }
    }
}
```

Ten test funkcjonalny wykonuje pełne ASP.NET Core MVC / stosu aplikacji stron Razor, w tym wszystkie oprogramowania pośredniczącego, filtry, wiążących, itp., które mogą być w miejscu. Sprawdza, czy daną trasą ("/") zwraca Powodzenie oczekiwany kod stanu i danych wyjściowych HTML. Odbywa się to bez konfigurowania serwera sieci web rzeczywiste, a więc eliminuje większość kruchości, który za pomocą rzeczywistych sieci web serwera do testowania mogą występować (na przykład problemy z ustawieniami zapory). Testy funkcjonalne, które są uruchamiane względem elementu TestServer są zwykle wolniejsze niż integracji i testów jednostkowych, ale jest znacznie szybsze niż testy, które może działać przez sieć do serwera sieci web test. Aby upewnić się, że stos fronton aplikacji działa zgodnie z oczekiwaniami, należy użyć testów funkcjonalnych. Te testy są szczególnie przydatne podczas duplikowania możesz znaleźć w kontrolerach lub strony i adresów powielania, dodając filtry. W idealnym przypadku tej refaktoryzacji nie spowoduje zmiany zachowania aplikacji, a zestaw testów funkcjonalnych sprawdzi, czy jest to możliwe.

>[!div class="step-by-step"]
[Poprzednie](work-with-data-in-asp-net-core-apps.md)
[dalej](development-process-for-azure.md)
