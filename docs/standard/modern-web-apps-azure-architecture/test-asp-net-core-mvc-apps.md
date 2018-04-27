---
title: Test platformy ASP.NET Core aplikacji MVC
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Test platformy ASP.NET Core aplikacji MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c9e71e7aeffbdb0721dae8487fe027b937b5b28a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="test-aspnet-core-mvc-apps"></a>Test platformy ASP.NET Core aplikacji MVC

> _"Jeśli nie podoba Ci się produkt testy jednostkowe, najprawdopodobniej klientów nie będą takie jak do testowania, albo."_
> _ - Anonimowe -

## <a name="summary"></a>Podsumowanie

Oprogramowanie żadnych złożoności może zakończyć się niepowodzeniem w nieoczekiwany sposób w odpowiedzi na zmiany. W związku z tym testowanie po wprowadzeniu zmian jest wymagana dla wszystkich aplikacji najbardziej trivial (lub najmniej krytyczne). Testów ręcznych do testowania oprogramowania jest niższa, zawodnych, najdroższych sposób. Niestety Jeśli aplikacje nie są zaprojektowane do można testować, może być jedynym sposobem dostępne. Aplikacje napisane następujące zasady architektury, którego układ określa się w rozdziale X należy testować jednostki i aplikacje platformy ASP.NET Core obsługują automatyczne integracji i funkcjonalności oraz testowania.

## <a name="kinds-of-automated-tests"></a>Rodzaje testów automatycznych

Istnieje wiele rodzajów zautomatyzowanych testów dla aplikacji. Najprostsza, najniższego poziomu testu jest test jednostkowy. Nieco wyższym poziomie istnieje testów integracji i funkcjonalności. Inne rodzaje testy, takie jak testy interfejsu użytkownika, testów obciążenia, testy obciążenia i dymu testy wykraczają poza zakres tego dokumentu.

### <a name="unit-tests"></a>Testy jednostkowe

Test jednostkowy testy pojedynczego część logiki aplikacji. Jeden można dodatkowo opisać poprzez wyszczególnienie niektóre czynności, które nie jest. Testu jednostkowego nie sprawdza, jak działa z kodu z zależności lub infrastruktury — jakie integracji testów są dla. Testu jednostkowego nie sprawdza szkielet kodu są zapisywane na — powinien założyć go działa lub, jeśli uważasz, że nie, o usterce i kod obejścia. Testu jednostkowego jest wykonywany w całości w pamięci i w procesie. Go nie komunikują się z systemu plików, sieci lub bazy danych. Testy jednostkowe należy przetestować tylko kodu.

Testy jednostkowe, ze względu na fakt, że sprawdzają one tylko pojedynczą jednostkę kodu, bez zewnętrznych zależności mają być wykonywane bardzo szybko. W związku z tym można uruchomić testów setek testów jednostkowych w ciągu kilku sekund. Uruchom je często, najlepiej przed co wypychania do repozytorium kontroli źródła udostępnionego i pewnością z każdej kompilacji automatycznych na serwerze kompilacji.

### <a name="integration-tests"></a>Testy integracji

Dobrym pomysłem jest Hermetyzowanie swój kod, który współdziała z infrastrukturą, takie jak bazy danych i systemy plików, ale będzie nadal masz niektórych z kodu i prawdopodobnie warto przetestować go. Ponadto należy sprawdzić, czy warstwy swój kod interakcji zgodnie z oczekiwaniami, gdy są całkowicie rozwiązany zależności aplikacji. To jest odpowiedzialny za testy integracji. Testy integracji zazwyczaj będzie wolniejsze i utrudnia Konfiguracja niż testy jednostkowe, ponieważ zależą one od często zależności zewnętrzne i infrastruktury. W związku z tym należy unikać testowania czynności, które mogą być testów przy użyciu testów jednostkowych w testach integracji. W przypadku testowania danego scenariusza z testu jednostkowego, należy przetestować go z testu jednostkowego. Jeśli nie, należy rozważyć przy użyciu testów integracji.

Testy integracji ma często bardziej złożonych konfiguracji i usuwania procedur niż testy jednostkowe. Na przykład testu integracji, który jest przesyłany z istniejącej bazy danych należy sposób, aby przywrócić bazę danych do znanego stanu przed każdym uruchomieniu testu. Jak są dodawane nowe testy i schemat bazy danych produkcyjnej rozwoju środowisko testu, te skrypty będą zwykle zwiększa się rozmiar i złożoność. W wielu systemach dużych jest niemożliwe do uruchamiania pełnego zestawy testów integracji na stacjach roboczych deweloperów przed zaewidencjonowaniem zmian do kontroli źródła udostępnionego. W takich przypadkach testy integracji może zostać uruchomione na serwerze kompilacji.

Klasa implementacji LocalFileImageService implementuje logikę pobierania i zwracania bajtów pliku obrazu z określonego folderu podany identyfikator:

```cs
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
```

### <a name="functional-tests"></a>Testy funkcjonalne

Integracja testy są zapisywane z punktu widzenia developer, aby sprawdzić, czy niektóre składniki systemu poprawnie działają razem. Testy funkcjonalne są zapisywane z punktu widzenia użytkownika, a następnie sprawdź poprawność systemu na podstawie jego wymagań. Poniższy fragment udostępnia przydatne sposób analogiczny, jak można traktować testy funkcjonalne, w porównaniu do testów jednostkowych:

> "Wielokrotnie rozwój systemu przyrównać do budowania domu. Gdy to odpowiednio nie jest jeszcze prawidłowy, firma Microsoft można rozszerzyć na potrzeby rozróżnianie między jednostki i testy funkcjonalne. Testy jednostkowe jest odpowiednikiem inspektora budynku, odwiedzając witrynę konstrukcji domu. Koncentruje się na różnych systemów wewnętrzny domu foundation, formułowanie, elektrycznego wodociągów i tak dalej. Zapewnia on (testy), aby części domu będą działać poprawnie i bezpiecznie, oznacza to, spełniały kompilowanie kodu. Testy funkcjonalne, w tym scenariuszu są podobne do właściciela domu, w tej samej witrynie konstrukcji. Zakłada on wewnętrznych systemach działają prawidłowo, czy inspektor budynku działa zadań. Właściciela domu koncentruje się na co będzie podobnie jak w domu tego. On dotyczy wyglądu domu, są różne pomieszczenia doświadczenia rozmiar, jest domu potrzeb rodziny, są w dobrym miejscem do catch sun rano systemu windows. Właściciela domu wykonuje testy funkcjonalne w domu. Ma on perspektywy użytkownika. Kompilowanie inspektora wykonuje testy jednostkowe w domu. Ma on konstruktora perspektywy."

Źródło: [testowania i testy funkcjonalne jednostki](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Jestem fond z informacją o tym "jako deweloperów Failover na dwa sposoby: budujemy operacją nieprawidłową lub budujemy nic złego." Testy jednostkowe upewnij się, że tworzysz prawa operacją; testy funkcjonalne upewnij się, że tworzysz co.

Ponieważ testy funkcjonalne działają na poziomie systemu, mogą wymagać pewien stopień automatyzacji interfejsu użytkownika. Jak testy integracji zazwyczaj działają one z określonego rodzaju również infrastruktury testu. Z tego powodu wolniejszy i bardziej łamliwa niż testy jednostkowe i integracji. Użytkownik powinien mieć tylko tyle testy funkcjonalne, jak muszą mieć pewność, system zachowuje się jak Użytkownicy oczekują.

### <a name="testing-pyramid"></a>Testowanie ostrosłupowy

Zapisano Fowler pole o ostrosłupa testowania, którego przykład jest wyświetlany w rysunek 9-1.

![](./media/image9-1.png)

Rysunek 9-1 testowania ostrosłupowy

Różnych warstw ostrosłupa i ich względne rozmiary reprezentuje różne rodzaje testy i ile należy zapisać dla aplikacji. Jak widać, zaleca się ma duże base testów jednostkowych, obsługiwane przez warstwę mniejsze testów integracji z warstwą mniejszy testy funkcjonalne. Każda warstwa najlepiej ma tylko testy w nim, że nie można wykonać odpowiednio w dolnej warstwie. Podczas próby zdecydować, jakiego rodzaju testu potrzebne dla danego scenariusza, należy pamiętać o testowania ostrosłupa.

### <a name="what-to-test"></a>Co do testowania

To powszechny problem dla deweloperów, którzy są niedoświadczonych pisanie zautomatyzowanych testów jest powtarzający się z tym, co do testowania. Jest dobry punkt wyjścia do testowania logikę warunkową. Dowolnym ma metodę o zachowanie zmiany oparte na instrukcji warunkowej (if-else, przełącznika, itp.), powinno być możliwe znaleziona co najmniej kilku testów potwierdzających poprawne zachowanie w pewnych warunkach. Jeśli kod ma błędów, warto zapisać co najmniej jeden test "ścieżki wszystkiego" za pomocą kodu (z bez błędów) i co najmniej jeden test "sad ścieżki" (z błędami lub nietypowe wyniki) upewnij się, że aplikacja działa zgodnie z oczekiwaniami w wypadku błędów. Na koniec spróbuj skupić się na testowania czynności, które może zakończyć się niepowodzeniem, a nie koncentrujących się na metryk, takich jak pokrycie kodu. Ogólnie jest lepszym rozwiązaniem niż mniej, więcej pokrycia kodu. Jednak zapisywania kilka większej liczby testów metody bardzo złożonych i biznesowych o znaczeniu krytycznym jest zwykle lepsze wykorzystanie czasu niż pisania testów dla właściwości auto tylko w celu poprawy metryki pokrycia kodu testu.

## <a name="organizing-test-projects"></a>Organizowanie projekty testowe

Projekty testowe można organizować, jednak działa najważniejsze dla Ciebie. Jest dobrym rozwiązaniem do oddzielania testy według typów (testu jednostkowego, testowanie integracji) i co testujesz (według projektu, przestrzeni nazw). Czy ta separacja składa się z folderami projekt testowy jednego lub wielu projekty testowe, jest decyzji projektowych. Najprościej jest jeden projekt, ale dla dużych projektów z wiele testów lub uruchomienie łatwiej różne zestawy testów, warto mieć kilka projekty testowe inny. Wiele zespołów organizować projekty testowe oparte na projekt, który ich testowania, którym dla aplikacji z więcej niż kilka projektów może skutkować dużą liczbę projekty testowe, zwłaszcza, jeśli użytkownik nadal rozbić te według rodzaju testy są w każdym projekcie. To podejście naruszenia jest jeden projekt na rodzaj testu na aplikację z folderami wewnątrz projekty testowe, aby wskazać testowane projektu (i klasy).

Typowym podejściem jest do organizowania projektów aplikacji w folderze 'src' i projekty testowe aplikacji równoległych folderze "testów". Foldery rozwiązania zgodnego można utworzyć w programie Visual Studio, jeśli użyteczna tej organizacji.

![](./media/image9-2.png)

Rysunek 9-2 Test organizacji w rozwiązaniu

Można użyć niezależnie od struktury testowej preferowane. Struktura xUnit dobrze działa i jest co wszystkie testy platformy ASP.NET Core i EF Core są zapisywane. W programie Visual Studio przy użyciu szablonu pokazano na rysunku 9-3 lub interfejsu wiersza polecenia przy użyciu nowego xunit dotnet można dodać xUnit projektu testowego.

![](./media/image9-3.png)

Rysunek 9-3 Dodaj xUnit projektu testu w programie Visual Studio

### <a name="test-naming"></a>Nazewnictwo testu

Należy nazwę testów w sposób zgodny z nazwy na wskazujące, działania każdego z testów. Jest jednym z podejść I właśnie dużą Powodzenie z nazwy klasy testu zgodnie z klasy i metody ich testowania. Powoduje to wiele klas teście małych, ale ułatwia bardzo wyczyść co to jest odpowiedzialny za każdego z testów. Ustawić tak, aby zidentyfikować klasy i metody do sprawdzenia nazwy klasy testu o nazwę metody testu może służyć do określania zachowania testowana. Obejmuje to oczekiwane zachowanie oraz dane wejściowe lub założenia, które należy użyć instrukcji yield to zachowanie. Niektóre przykładowe nazwy testu:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Zmiany tego podejścia kończy nazwy klasy testu z "Powinien" i modyfikuje nieco czas:

-   CatalogControllerGetImage**powinien**. **Wywołanie**ImageServiceWithId

-   CatalogControllerGetImage**powinien**. **Dziennik**WarningGivenImageMissingException

Niektóre zespoły znaleźć drugiej metody nazewnictwa jaśniejszy, jednak wymaga nieco więcej pełne. W każdym przypadku spróbuj użyć konwencji nazewnictwa, która zapewnia wgląd w działanie testu tak, aby w przypadku awarii jednego lub więcej testów, wynika z ich nazw, w jakich przypadkach nie powiodło się. Unikaj nadawania nazw można testy vaguely, takich jak ControllerTests.Test1, jak kiedy zostanie wyświetlony w wynikach testów oferuje żadnej wartości.

Jeśli wykonujesz konwencji nazewnictwa jak w poprzednim, który tworzy wiele klas teście małych, jest dobrym pomysłem jest dalsze organizowanie testów przy użyciu folderów i przestrzenie nazw. Na rysunku 9-4 przedstawiono jeden ze sposobów organizowanie testów przez folder w kilku projekty testowe.

![](./media/image9-4.png)

**Rysunek 9-4.** Organizowanie klasy testowe według folderów na podstawie klasy testowana.

Oczywiście jeśli klasa określona aplikacja ma wiele metod testowane (i w związku z tym wiele testów klasy), rozsądne może okazać można umieścić w folderze odpowiadającym udziałowi klasy aplikacji. Ta organizacja nie różni się od sposobu zorganizowania plików do folderów w innym miejscu. Jeśli masz więcej niż trzy lub cztery powiązane pliki w folderze zawierający wiele plików, często jest przydatne przenieść je do ich własnych podfolderu.

## <a name="unit-testing-aspnet-core-apps"></a>Aplikacje platformy ASP.NET Core testów jednostkowych

W dobrze zaprojektowanej aplikacji platformy ASP.NET Core większość złożoność i logiki biznesowej będzie można hermetyzowane w jednostek biznesowych i wielu usług. Aplikacji platformy ASP.NET Core MVC, kontrolerów, filtry, viewmodels i widoki, należy wymagać bardzo mało testów jednostkowych. Wiele funkcji danej akcji znajduje się poza metody akcji. Sprawdzenie, czy routing działa prawidłowo lub obsługi błędów globalnych nie można wykonać skutecznie z testu jednostkowego. Podobnie wszystkie filtry, w tym uwierzytelniania i walidacji modelu i filtry autoryzacji nie może być testowane jednostki. Bez tych źródeł zachowanie powinna być trivially mały, delegowanie zbiorczego działanie usługi, które można przetestować niezależnie od kontrolera, który używa tych większości metod akcji.

Czasami musisz refaktoryzacji kodu w kolejności do testu jednostkowego. Obejmuje to często identyfikowania obiektów abstrakcyjnych i otwieranie abstrakcji w kodzie, którą chcesz przetestować za pomocą iniekcji zależności, zamiast kodowania bezpośrednio przed infrastruktury. Rozważmy na przykład tej metody akcji proste do wyświetlania obrazów:

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Ta metoda testy jednostkowe następuje trudne bezpośrednio zależne od System.IO.File, która jest używana do odczytu z systemu plików. Można przetestować tego zachowania, aby upewnić się, działa on zgodnie z oczekiwaniami, ale z plikami rzeczywistych jest test integracji. Warto zauważyć trasy tej metody nie można sprawdzić — zobaczysz jak to zrobić z funkcjonalnej wkrótce.

Jeśli test jednostkowy zachowaniem systemu plików nie można bezpośrednio i nie można przetestować trasy, co to jest do testowania? Również po refaktoryzacji, aby umożliwić testowanie jednostkowe, użytkownik może stwierdzić niektórych przypadków testowych i brak zachowanie, takich jak obsługa błędów. Metoda czego po znalezieniu nie jest plikiem? Do czego należy go? W tym przykładzie metoda refactored wygląda następująco:

```cs
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

\_Rejestratora i \_imageService są oba dodane jako zależności. Teraz możesz przetestować, że ten sam identyfikator, który jest przekazywany do metody akcji jest przekazywany do \_imageService, oraz że bajtów wynikowe są zwracane jako część FileResult. Można również sprawdzić wykonywane rejestrowania błędów zgodnie z oczekiwaniami oraz że wynik NotFound jest zwracany, jeśli brakuje obrazu, przy założeniu, że jest to zachowanie ważnych aplikacji (oznacza to, nie tylko tymczasowy kod developer dodane w celu zdiagnozowania problemu). Logika rzeczywisty plik został przeniesiony do oddzielnych implementacji usługi i zostały rozszerzone do zwrócenia wyjątku specyficzne dla aplikacji w przypadku brakujących plików. Można przetestować tę implementację niezależnie, za pomocą testu integracji.

## <a name="integration-testing-aspnet-core-apps"></a>Aplikacje platformy ASP.NET Core Testowanie integracji

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

Ta usługa używa IHostingEnvironment, podobnie jak CatalogController kod jak przed jego został zrefaktoryzowany do oddzielnych usługi. Ponieważ to jest tylko kod na kontrolerze, który używany IHostingEnvironment, tej zależności został usunięty z CatalogController tego konstruktora.

Aby sprawdzić, czy ta usługa działa prawidłowo, należy utworzyć plik obrazu znane testu i sprawdź, usługa zwraca go podane określone dane wejściowe. Należy zadbać nie należy używać zasymulować obiektów na zachowanie, które faktycznie chcesz przetestować (w tym przypadku odczytywania z systemu plików). Jednak obiekty zasymulować nadal mogą być przydatne do skonfigurowania integracji testy. W takim przypadku można mock IHostingEnvironment, dzięki czemu jego ContentRootPath wskazuje folder, którego zamierzasz użyć dla obrazu testu. Zakończenie klasy testowej integracji pracy jest następujący:

```cs
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
> czy badanie jest bardzo prosty — zbiorczego kod jest niezbędne do skonfigurowania systemu i utworzyć testowania infrastruktury (w tym przypadku rzeczywistego pliku do odczytu z dysku). To jest typowe dla testów integracji, które często wymagają bardziej złożonych czynności niż testy jednostkowe.

## <a name="functional-testing-aspnet-core-apps"></a>Funkcjonalności testowanie aplikacji platformy ASP.NET Core

W przypadku aplikacji platformy ASP.NET Core klasy elementu TestServer sprawia, że testy funkcjonalne stosunkowo łatwa do zapisu. Element TestServer przy użyciu WebHostBuilder, należy skonfigurować tak samo, jak zwykle dla aplikacji. To WebHostBuilder powinny być skonfigurowane tak samo jak aplikacji rzeczywistych hosta, ale można zmodyfikować wszystkie aspekty, które ułatwić testowanie. W większości przypadków będzie ponowne użycie tego samego elementu TestServer dla wielu przypadków testowych, więc może ona Hermetyzowanie w wielokrotnego użytku — metoda (np. w klasie podstawowej):

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath — metoda po prostu zwraca ścieżkę fizyczną do projektu sieci web (Pobierz przykładowe rozwiązanie). WebHostBuilder w takim przypadku po prostu Określa, gdzie jest zawartość katalogu głównego aplikacji sieci web, a odwołuje się do tej samej klasy uruchomienia, która korzysta z aplikacji sieci web rzeczywistych. Aby pracować z elementu TestServer, standardowy typ System.Net.HttpClient służy do żądania do niego. Element TestServer opisuje metodę CreateClient pomocne, która udostępnia wstępnie skonfigurowany klienta, który jest gotowy na wysyłanie żądań do aplikacji uruchomionych na element TestServer. Użyj tego klienta (Ustaw do chronionej \_Członkowskie klienta na podstawowy test powyżej) podczas pisania testów funkcjonalności aplikacji platformy ASP.NET Core:

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Ten test funkcjonalności wykonuje pełne stosu aplikacji ASP.NET Core MVC włącznie ze wszystkimi oprogramowanie pośredniczące, filtry, integratorów, itp., które mogą być stosowane. Sprawdza, czy podany trasy ("/ 1-katalogu/pic") zwraca tablicę bajtów oczekiwanego pliku w znanej lokalizacji. Wykonuje bez konfigurowania serwera sieci web prawdziwe, a więc pozwala uniknąć znacznie kruchości, który przy użyciu rzeczywistego sieci web serwera do testowania może wystąpić (na przykład problemy z ustawieniami zapory). Testy funkcjonalne, systemem względem elementu TestServer są zazwyczaj wolniej niż integracji i testów jednostkowych, ale jest znacznie szybsze niż testy, które może działać przez sieć do serwera sieci web testu.

>[!div class="step-by-step"]
[Poprzednie] (work-with-data-in-asp-net-core-apps.md) [dalej] (Programowanie — proces do azure.md)
