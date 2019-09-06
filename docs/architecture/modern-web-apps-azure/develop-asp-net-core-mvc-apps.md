---
title: Opracowywanie aplikacji ASP.NET Core MVC
description: Tworzenie architektury nowoczesnych aplikacji sieci Web przy użyciu ASP.NET Core i platformy Azure | opracowywanie aplikacji ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 51feb770e84af170bf31a6ba363a1d9e72616284
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373777"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Opracowywanie aplikacji ASP.NET Core MVC

> "Nie jest ważne, aby pobrać go po raz pierwszy. Bardzo ważne jest, aby uzyskać je po raz ostatni. "  
> _— Andrew polowa i David Thomas_

ASP.NET Core to międzyplatformowa platforma typu "open source" służąca do tworzenia nowoczesnych aplikacji sieci Web zoptymalizowanych pod kątem chmury. Aplikacje ASP.NET Core są lekkie i modularne, dzięki wbudowanej obsłudze iniekcji zależności, co pozwala zwiększyć możliwości testowania i utrzymania. W połączeniu z platformą MVC, która obsługuje tworzenie nowoczesnych interfejsów API sieci Web oprócz aplikacji opartych na widoku, ASP.NET Core to zaawansowana platforma, w której można tworzyć aplikacje sieci Web dla przedsiębiorstw.

## <a name="mvc-and-razor-pages"></a>MVC i Razor Pages

ASP.NET Core MVC oferuje wiele funkcji, które są przydatne do tworzenia interfejsów API i aplikacji opartych na sieci Web. Termin MVC oznacza "Model-View-Controller", wzorzec interfejsu użytkownika, który dzieli obowiązki odpowiedzi na żądania użytkowników do kilku części. Oprócz tego wzorca można także zaimplementować funkcje w ASP.NET Core aplikacji jako Razor Pages. Razor Pages są wbudowane w ASP.NET Core MVC i używają tych samych funkcji routingu, powiązania modeli itp. Jednak zamiast oddzielnych folderów i plików dla kontrolerów, widoków itp. i przy użyciu routingu opartego na atrybutach Razor Pages są umieszczane w pojedynczym folderze ("/Pages"), trasie na podstawie ich lokalizacji względnej w tym folderze i obsługi żądań z obsługą zamiast akcji kontrolerów.

Podczas tworzenia nowej aplikacji ASP.NET Core należy mieć plan na uwadze dla rodzaju aplikacji, którą chcesz skompilować. W programie Visual Studio będziesz wybierać spośród kilku szablonów. Trzy najpopularniejsze szablony projektów to Web API, aplikacja sieci Web i aplikacja sieci Web (Model-View-Controller). Chociaż tę decyzję można podjąć tylko podczas pierwszego tworzenia projektu, nie jest to nieodwołalna decyzja. Projekt interfejsu API sieci Web używa standardowych kontrolerów kontrolera widoku modelu — tylko domyślnie nie ma widoków. Podobnie szablon domyślnej aplikacji sieci Web używa Razor Pages, a zatem nie ma folderu widoki. Możesz później dodać folder widoki do tych projektów, aby obsługiwać zachowanie oparte na widoku. Projekty Web API i Model-View-Controller nie zawierają domyślnie folderu Pages, ale można je później dodać do obsługi zachowania opartego na Razor Pages. Te trzy szablony można traktować jako obsługujące trzy różne rodzaje domyślnej interakcji użytkownika: dane (internetowy interfejs API), oparte na stronach i widoku. Można jednak mieszać i dopasować dowolne lub wszystkie z nich w ramach pojedynczego projektu, jeśli chcesz.

### <a name="why-razor-pages"></a>Dlaczego Razor Pages?

Razor Pages to domyślne podejście do nowych aplikacji sieci Web w programie Visual Studio. Razor Pages oferuje prostszy sposób tworzenia funkcji aplikacji opartych na stronach, takich jak formularze niespa. Korzystanie z kontrolerów i widoków było powszechne dla aplikacji, które mają bardzo duże kontrolery, które pracowały z wieloma różnymi zależnościami, i wyświetlają wiele różnych widoków. Spowodowało to wiele złożoności i często wynika z kontrolerów, które nie były zgodne z pojedynczą zasadą odpowiedzialności lub zasad otwartych/zamkniętych. Razor Pages rozwiązuje ten problem przez hermetyzację logiki po stronie serwera dla danej logicznej "strony" w aplikacji sieci Web z oznaczeniem Razor. Strona Razor, która nie ma logiki po stronie serwera, może po prostu składać się z pliku Razor (na przykład "index. cshtml"). Jednak większość nieuproszczonych Razor Pages będzie miała skojarzoną klasę modelu strony, która jest taka sama jak nazwa pliku Razor z rozszerzeniem ". cs" (na przykład "Index.cshtml.cs").

Model strony strony Razor łączy obowiązki kontrolera MVC i ViewModel. Zamiast obsługi żądań z metodami akcji kontrolera, programy obsługi modelu strony, takie jak "OnGet ()", są wykonywane, domyślnie renderuje ich skojarzone strony. Razor Pages upraszcza proces kompilowania poszczególnych stron w aplikacji ASP.NET Core, zapewniając jednocześnie wszystkie funkcje architektury ASP.NET Core MVC. Są to dobry wybór domyślny dla nowych funkcji opartych na stronach.

### <a name="when-to-use-mvc"></a>Kiedy używać MVC

Jeśli tworzysz interfejsy API sieci Web, wzorzec MVC staje się bardziej zrozumiały niż próba użycia Razor Pages. Jeśli projekt będzie uwidaczniał wyłącznie punkty końcowe interfejsu API sieci Web, należy najlepiej zacząć od szablonu projektu interfejsu API sieci Web, ale w przeciwnym razie można łatwo dodać kontrolery i skojarzone punkty końcowe interfejsu API do dowolnej aplikacji ASP.NET Core. Należy również użyć podejścia MVC opartego na widoku, Jeśli migrujesz istniejącą aplikację z ASP.NET MVC 5 lub starszego do ASP.NET Core MVC i chcesz to zrobić z mniejszą ilością nakładu pracy. Po przeprowadzeniu migracji wstępnej można sprawdzić, czy ma to na celu przyjęcie Razor Pages nowych funkcji, a nawet w przypadku migracji hurtowej.

Niezależnie od tego, czy wybierzesz kompilację aplikacji sieci Web przy użyciu widoków Razor Pages lub MVC, aplikacja będzie miała podobną wydajność i obejmuje obsługę iniekcji zależności, filtrów, powiązań modelu i walidacji itp.

## <a name="mapping-requests-to-responses"></a>Mapowanie żądań na odpowiedzi

W swoich serca ASP.NET Core aplikacje mapują przychodzące żądania na odpowiedzi wychodzące. Na niskim poziomie jest to realizowane za pomocą oprogramowania pośredniczącego, a proste aplikacje i mikrousługi ASP.NET Core mogą obejmować wyłącznie niestandardowe oprogramowanie pośredniczące. W przypadku korzystania z ASP.NET Core MVC można korzystać na nieco wyższym poziomie, zastanawiając się pod względem _tras_, _kontrolerów_i _akcji_. Każde żądanie przychodzące jest porównywane z tabelą routingu aplikacji. w przypadku znalezienia zgodnej trasy zostanie wywołana skojarzona Metoda akcji (należącej do kontrolera) do obsługi żądania. Jeśli nie zostanie znaleziona zgodna trasa, zostanie wywołana procedura obsługi błędów (w tym przypadku zwracająca wynik NotFound).

Aplikacje ASP.NET Core MVC mogą używać tras konwencjonalnych, tras atrybutów lub obu. Trasy konwencjonalne są zdefiniowane w kodzie, określając _konwencje_ routingu przy użyciu składni podobnej do poniższego przykładu:

```csharp
app.UseMvc(routes =>
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

W tym przykładzie trasa o nazwie "default" została dodana do tabeli routingu. Definiuje szablon trasy z symbolami zastępczymi dla _kontrolera_, _akcji_i _identyfikatora_. Symbole zastępcze kontrolera i akcji mają domyślnie określony ("Dom" i "index"), a symbol zastępczy ID jest opcjonalny (na przykład "?"). W ramach Konwencji zdefiniowanej tutaj należy określić, że pierwsza część żądania powinna odpowiadać nazwie kontrolera, drugiej części akcji, a następnie, jeśli to konieczne, trzecia część będzie reprezentować parametr ID. Trasy konwencjonalne są zwykle zdefiniowane w jednym miejscu dla aplikacji, na przykład w metodzie Configure w klasie Startup.

Trasy atrybutów są stosowane bezpośrednio do kontrolerów i akcji, a nie do określonych globalnie. Zaletą tego jest znacznie bardziej wykrywalność, gdy przeglądasz określoną metodę, ale oznacza to, że informacje o routingu nie są przechowywane w jednym miejscu w aplikacji. Korzystając z tras atrybutów, można łatwo określić wiele tras dla danej akcji, a także połączyć trasy między kontrolerami i akcjami. Na przykład:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

Trasy można określić w [narzędzia HttpGet] i podobnych atrybutach, unikając konieczności dodawania oddzielnych atrybutów [Route]. Trasy atrybutu mogą również używać tokenów, aby ograniczyć potrzebę powtarzania nazw kontrolerów lub akcji, jak pokazano poniżej:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages nie używa routingu atrybutów. Jako część swojej `@page` dyrektywy można określić dodatkowe informacje o szablonie trasy dla strony Razor:

```csharp
@page "{id:int}"
```

W poprzednim przykładzie dana strona będzie pasowała do trasy z parametrem Integer `id` . Na przykład strona *Products. cshtml* znajdująca się w folderze głównym `/Pages` ma następującą trasę:

```csharp
"/Products/123"
```

Po dopasowaniu danego żądania do trasy, ale przed wywołaniem metody akcji, ASP.NET Core MVC będzie wykonywał [powiązania modelu](/aspnet/core/mvc/models/model-binding) i [Sprawdzanie poprawności modelu](/aspnet/core/mvc/models/validation) na żądanie. Powiązanie modelu jest odpowiedzialne za konwertowanie przychodzących danych HTTP na typy .NET określone jako parametry metody akcji, która ma zostać wywołana. Na przykład jeśli metoda akcja oczekuje parametru identyfikatora int, powiązanie modelu podejmie próbę dostarczenia tego parametru z wartości dostarczonej jako część żądania. W tym celu powiązanie modelu wyszukuje wartości w opublikowanym formularzu, wartości w samej trasie i wartości ciągu zapytania. Przy założeniu, że wartość identyfikatora zostanie znaleziona, zostanie przekonwertowana na liczbę całkowitą przed przekazaniem do metody akcji.

Po powiązaniu modelu, ale przed wywołaniem metody akcji, następuje Walidacja modelu. Walidacja modelu używa opcjonalnych atrybutów dla typu modelu i może pomóc zapewnić, że udostępniony obiekt modelu spełnia określone wymagania dotyczące danych. Niektóre wartości mogą być określone jako wymagane lub ograniczone do określonej długości lub zakresu liczbowego itd. Jeśli określono atrybuty walidacji, ale model nie spełnia wymagań, właściwość ModelState. IsValid ma wartość false, a zestaw reguł walidacji z błędami będzie dostępny do wysłania do klienta wysyłającego żądanie.

W przypadku korzystania z walidacji modelu należy zawsze sprawdzić, czy model jest prawidłowy przed wykonaniem jakichkolwiek poleceń zmiany stanu, aby upewnić się, że aplikacja nie jest uszkodzona przez nieprawidłowe dane. Możesz użyć [filtru](/aspnet/core/mvc/controllers/filters) , aby uniknąć konieczności dodawania kodu dla każdej akcji. ASP.NET Core filtry MVC oferują sposób przechwytywania grup żądań, dzięki czemu można zastosować typowe zasady i zagadnienia dotyczące krzyżowego rozliczania. Filtry mogą być stosowane do poszczególnych akcji, całych kontrolerów lub globalnie dla aplikacji.

W przypadku interfejsów API sieci Web ASP.NET Core MVC obsługuje [_negocjowanie zawartości_](/aspnet/core/mvc/models/formatting), umożliwiając żądanie określenia sposobu formatowania odpowiedzi. W oparciu o nagłówki podane w żądaniu akcje zwracające dane spowodują sformatowanie odpowiedzi w formacie XML, JSON lub innym obsługiwanym formacie. Ta funkcja umożliwia korzystanie z tego samego interfejsu API przez wielu klientów z różnymi wymaganiami dotyczącymi formatu danych.

Projekty interfejsu API sieci Web należy rozważyć `[ApiController]` przy użyciu atrybutu, który można zastosować do poszczególnych kontrolerów, do podstawowej klasy kontrolera lub do całego zestawu. Ten atrybut dodaje Automatyczne sprawdzanie poprawności modelu, a każda akcja z nieprawidłowym modelem zwróci nieprawidłowego żądania z informacjami o błędach walidacji. Ten atrybut wymaga również, aby wszystkie akcje miały atrybut trasy, zamiast używać trasy konwencjonalnej i zwracają bardziej szczegółowe informacje ProblemDetails w odpowiedzi na błędy.

> ### <a name="references--mapping-requests-to-responses"></a>References — mapowanie żądań na odpowiedzi
>
> - **Routing do akcji kontrolera**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Powiązanie modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Walidacja modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **ApiController — atrybut**
 > <https://docs.microsoft.com/aspnet/core/web-api/?view=aspnetcore-2.2>

## <a name="working-with-dependencies"></a>Praca z zależnościami

ASP.NET Core ma wbudowaną obsługę i wewnętrznie wykorzystuje technikę znaną jako [iniekcja zależności](/aspnet/core/fundamentals/dependency-injection). Wstrzykiwanie zależności to technika, która umożliwia swobodne sprzęganie różnych części aplikacji. Sprzężenie luźne jest pożądane, ponieważ ułatwia izolowanie części aplikacji, co pozwala na testowanie lub zastępowanie. Sprawia również, że zmiana w jednej części aplikacji będzie miała nieoczekiwany wpływ w innym miejscu aplikacji. Iniekcja zależności jest oparta na zasadzie niewersji zależności i jest często kluczem do osiągnięcia zasady otwarte/zamknięte. Podczas oceniania, jak działa Twoja aplikacja wraz z jej zależnościami, należy pamiętać o kodzie [static cling](https://deviq.com/static-cling/) zapachu i pamiętaj, że aphorism "[New to Glue](https://ardalis.com/new-is-glue)".

Statyczne cling występuje, gdy klasy umożliwiają wywoływanie metod statycznych lub dostęp do właściwości statycznych, które mają efekty uboczne lub zależności dotyczące infrastruktury. Na przykład jeśli masz metodę, która wywołuje metodę statyczną, która z kolei zapisuje dane w bazie danych, metoda jest ściśle sprzężona z bazą danych. Wszystkie elementy, które dzielą się tym wywołaniem bazy danych, spowodują uszkodzenie metody. Testowanie takich metod jest trudne, ponieważ takie testy wymagają, aby komercyjne biblioteki do zasymulować wywołania statyczne lub mogły być testowane tylko z testową bazą danych. Wywołania statyczne, które nie są zależne od infrastruktury, szczególnie te, które są całkowicie bezstanowe, są bardzo ważne do wywołania i nie mają wpływu na sprzęganie ani testowanie (poza kodem sprzęgania do samego wywołania statycznego).

Wielu programistów zna ryzyko związane ze statycznym clingm i globalnym stanem, ale nadal ściśle połączy swój kod z określonymi implementacjami za pośrednictwem bezpośredniego tworzenia wystąpienia. "New to Glue" to przypomnienie dotyczące sprzęgu, a nie ogólne Condemnation użycia `new` słowa kluczowego. Podobnie jak w przypadku wywołań metod statycznych, nowe wystąpienia typów, które nie mają zależności zewnętrznych, zazwyczaj nie umożliwiają ścisłego podzielenia kodu na szczegóły implementacji lub sprawiają, że testowanie jest trudniejsze. Ale za każdym razem, gdy Klasa jest tworzona, Poświęć nieco chwilę, aby rozważyć, czy ma to sens, że ma to na celu wyznaczenie, że ma to miejsce w konkretnym miejscu w danej lokalizacji, czy też będzie lepszym rozwiązaniem do żądania tego wystąpienia jako zależności.

### <a name="declare-your-dependencies"></a>Deklarowanie zależności

ASP.NET Core jest oparty na tym, że metody i klasy deklarują swoje zależności, żądając ich jako argumentów. Aplikacje ASP.NET są zwykle konfigurowane w klasie startowej, która jest konfigurowana do obsługi iniekcji zależności w kilku punktach. Jeśli Klasa startowa ma Konstruktor, może zażądać zależności za pomocą konstruktora, tak więc:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Klasa uruchomieniowa jest interesująca, że nie ma żadnych jawnych wymagań dla tego typu. Nie dziedziczy po specjalnej początkowej klasie bazowej ani nie implementuje żadnego konkretnego interfejsu. Możesz nadać mu konstruktora, a nie, i można określić dowolną liczbę parametrów w konstruktorze. Po uruchomieniu hosta sieci Web, który został skonfigurowany dla aplikacji, zostanie wywołana Klasa startowa, której użyto, i użyje iniekcji zależności do wypełnienia wszelkich zależności wymaganych przez klasę uruchomieniową. Oczywiście, jeśli poprosisz o parametry, które nie są skonfigurowane w kontenerze usług używanym przez ASP.NET Core, otrzymasz wyjątek, ale o ile przejdziesz do zależności, których dotyczy ten kontener, możesz poprosić o dowolne elementy.

Iniekcja zależności jest wbudowana w aplikacje ASP.NET Core bezpośrednio od początku, podczas tworzenia wystąpienia uruchamiania. Nie powoduje zatrzymania klasy startowej. Możesz również zażądać zależności w metodzie konfigurowania:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices to wyjątek dla tego zachowania; musi on mieć tylko jeden parametr typu IServiceCollection. Nie ma potrzeby obsługi iniekcji zależności, ponieważ z jednej strony jest odpowiedzialny za Dodawanie obiektów do kontenera usługi, a w drugiej, ma dostęp do wszystkich aktualnie skonfigurowanych usług za pośrednictwem parametru IServiceCollection. Z tego względu można pracować z zależnościami zdefiniowanymi w kolekcji usług ASP.NET Core Services w każdej części klasy uruchomieniowej, żądając wymaganej usługi jako parametru lub przez pracę z IServiceCollection w ConfigureServices.

> [!NOTE]
> Jeśli musisz upewnić się, że niektóre usługi są dostępne dla klasy startowej, możesz je skonfigurować przy użyciu WebHostBuilder i jego metody ConfigureServices.

Klasa startowa to model służący do tworzenia struktury innych części aplikacji ASP.NET Core, od kontrolerów do oprogramowania pośredniczącego, do filtrów do własnych usług. W każdym przypadku należy postępować zgodnie z [zasadami jawnych zależności](https://deviq.com/explicit-dependencies-principle/), żądając zależności, a nie ich bezpośrednio tworzyć i wykorzystując iniekcję zależności w całej aplikacji. Należy zachować ostrożność, gdzie i w jaki sposób bezpośrednio utworzyć wystąpienia implementacji, szczególnie usług i obiektów, które pracują z infrastrukturą, lub mieć skutki uboczne. Preferuj pracę z abstrakcyjnymi definicjami w rdzeńu aplikacji i przekazane jako argumenty do zakodowana odwołań do określonych typów implementacji.

## <a name="structuring-the-application"></a>Tworzenie struktury aplikacji

Aplikacje monolityczne zwykle mają jeden punkt wejścia. W przypadku ASP.NET Core aplikacji sieci Web punkt wejścia będzie ASP.NET Core projekcie sieci Web. Nie oznacza to jednak, że rozwiązanie powinno zawierać tylko jeden projekt. Warto podzielić aplikację na różne warstwy, aby obserwować rozdzielenie problemów. Po podpisaniu na warstwach warto przekroczyć foldery do oddzielnych projektów, co może pomóc w osiągnięciu lepszego hermetyzacji. Najlepszym podejściem do osiągnięcia tych celów za pomocą aplikacji ASP.NET Core jest odmiana czystego architektury omówionego w rozdziale 5. Po tym podejściu rozwiązanie aplikacji będzie składać się z oddzielnych bibliotek dla interfejsu użytkownika, infrastruktury i ApplicationCore.

Poza tymi projektami są również dołączone oddzielne projekty testowe (testowanie jest omówione w rozdziale 9).

Model obiektów i interfejsy aplikacji należy umieścić w projekcie ApplicationCore. Ten projekt będzie miał możliwie najmniejszej liczby zależności, a inne projekty w rozwiązaniu będą odwoływać się do niego. Jednostki biznesowe, które muszą być utrwalane, są zdefiniowane w projekcie ApplicationCore, podobnie jak usługi, które nie zależą bezpośrednio od infrastruktury.

Szczegóły implementacji, takie jak trwałość lub sposób wysyłania powiadomień do użytkownika, są przechowywane w projekcie infrastruktury. Ten projekt będzie odwoływać się do pakietów specyficznych dla implementacji, takich jak Entity Framework Core, ale nie powinien ujawniać szczegółowych informacji o tych implementacjach poza projektem. Usługi infrastruktury i repozytoria powinny implementować interfejsy, które są zdefiniowane w projekcie ApplicationCore, a jego implementacje trwałości są odpowiedzialne za pobieranie i przechowywanie jednostek zdefiniowanych w ApplicationCore.

Projekt interfejsu użytkownika ASP.NET Core jest odpowiedzialny za wszelkie wątpliwości dotyczące poziomu interfejsu użytkownika, ale nie powinien obejmować logiki biznesowej ani szczegółów infrastruktury. W rzeczywistości najlepiej nie powinien on mieć zależności od projektu infrastruktury, co pomaga zapewnić, że żadna zależność między tymi dwoma projektami nie zostanie wprowadzona przypadkowo. Można to osiągnąć za pomocą innych kontenerów DI innych firm, takich jak Autofac, co pozwala na definiowanie reguł DI w klasach modułów w każdym projekcie.

Inne podejście do oddzielenia aplikacji od szczegółów implementacji ma na celu wywołanie mikrousług, które mogą być wdrożone w poszczególnych kontenerach platformy Docker. Zapewnia to jeszcze większe rozdzielenie problemów i rozróżnienie niż wykorzystanie dwóch projektów, ale ma dodatkową złożoność.

### <a name="feature-organization"></a>Organizacja funkcji

Domyślnie aplikacje ASP.NET Core organizują strukturę folderów w taki sposób, aby obejmowały kontrolery i widoki oraz często modele widoków. Kod po stronie klienta do obsługi tych struktur po stronie serwera jest zazwyczaj przechowywany osobno w folderze wwwroot. Jednak duże aplikacje mogą napotkać problemy z tą organizacją, ponieważ praca nad daną funkcją często wymaga przechodzenia między tymi folderami. Jest to bardziej trudne i trudniejsze w miarę zwiększania się liczby plików i podfolderów w każdym folderze, dzięki czemu można przewijać Eksplorator rozwiązań. Jednym z rozwiązań tego problemu jest organizowanie kodu aplikacji według _funkcji_ zamiast według typu plików. Ten styl organizacyjny jest zwykle określany jako foldery funkcji lub [wycinki funkcji](https://msdn.microsoft.com/magazine/mt763233.aspx) (Zobacz również: [Wycinków pionowych](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC obsługuje obszary do tego celu. Korzystając z obszarów, można utworzyć osobne zestawy kontrolerów i folderów widoków (oraz wszelkich skojarzonych modeli) w każdym folderze obszaru. Rysunek 7-1 pokazuje przykładową strukturę folderów przy użyciu obszarów.

![Przykładowa organizacja obszaru](./media/image7-1.png)

**Rysunek 7-1**. Przykładowa organizacja obszaru

W przypadku korzystania z obszarów należy użyć atrybutów do dekorować kontrolerów z nazwą obszaru, do którego należą:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Musisz również dodać obsługę obszaru do swoich tras:

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

Oprócz wbudowanej obsługi obszarów, można również użyć własnej struktury folderów oraz Konwencji zamiast atrybutów i tras niestandardowych. Dzięki temu można mieć foldery funkcji, które nie zawierały oddzielnych folderów dla widoków, kontrolerów itp., utrzymując hierarchię Flatter i ułatwiając wyświetlanie wszystkich powiązanych plików w jednym miejscu dla każdej funkcji.

ASP.NET Core używa wbudowanych typów Konwencji do sterowania jego zachowaniem. Możesz zmodyfikować lub zastąpić te konwencje. Na przykład można utworzyć Konwencję, która będzie automatycznie pobierać nazwę funkcji dla danego kontrolera na podstawie jego przestrzeni nazw (co zazwyczaj jest skorelowane z folderem, w którym znajduje się kontroler):

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Następnie należy określić tę Konwencję jako opcję po dodaniu obsługi MVC do aplikacji w ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC używa również Konwencji do lokalizowania widoków. Można zastąpić go Konwencją niestandardową, aby widoki znajdowały się w folderach funkcji (przy użyciu nazwy funkcji dostarczonej przez FeatureConvention). Aby dowiedzieć się więcej na temat tego podejścia i pobrać przykład roboczy z artykułu MSDN, [wycinki funkcji dla ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Zagadnienia dotyczące wycinania

Po rozbudowywaniu aplikacji coraz bardziej ważne jest, aby wyeliminować problemy związane z wycinaniem i zachować spójność. Niektóre przykłady zagadnień związanych z obcinaniem w aplikacjach ASP.NET Core to uwierzytelnianie, reguły walidacji modelu, buforowanie danych wyjściowych i obsługa błędów, chociaż istnieje wiele innych. ASP.NET Core [filtry](/aspnet/core/mvc/controllers/filters) MVC umożliwiają uruchamianie kodu przed określonymi krokami w potoku przetwarzania żądań lub po nich. Na przykład filtr może zostać uruchomiony przed i po powiązaniu modelu, przed i po akcji lub przed i po wyniku akcji. Można również użyć filtru autoryzacji, aby kontrolować dostęp do reszty potoku. Ilustracje 7-2 pokazuje, w jaki sposób przepływają żądania wykonania przez filtry, jeśli są skonfigurowane.

![Żądanie jest przetwarzane przez filtry autoryzacji, filtry zasobów, powiązania modelu, filtry akcji, wykonywanie akcji i konwersję wyników akcji, filtry wyjątków, filtry wynikowe i wykonywanie wyniku. W ten sposób żądanie jest przetwarzane tylko przez filtry wyników i filtry zasobów przed wysłaniem odpowiedzi do klienta.](./media/image7-2.png)

**Rysunek 7-2**. Zażądaj wykonania przez filtry i potok żądań.

Filtry są zwykle zaimplementowane jako atrybuty, więc można je stosować do kontrolerów lub akcji (lub nawet globalnie). Po dodaniu w ten sposób filtry określone na poziomie akcji przesłaniają lub kompilują przy użyciu filtrów określonych na poziomie kontrolera, które same przesłaniają filtry globalne. Na przykład \[atrybut trasy\] może służyć do tworzenia tras między kontrolerami i akcjami. Podobnie można skonfigurować autoryzację na poziomie kontrolera, a następnie przesłonić poszczególne akcje, jak pokazano w poniższym przykładzie:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

Pierwsza metoda, login, używa filtru AllowAnonymous (atrybut), aby zastąpić filtr autoryzacji ustawiony na poziomie kontrolera. Akcja ForgotPassword (i jakakolwiek inna akcja w klasie, która nie ma atrybutu AllowAnonymous) będzie wymagała uwierzytelnionego żądania.

Filtry mogą służyć do eliminacji duplikatów w postaci typowych zasad obsługi błędów dla interfejsów API. Na przykład typowe zasady interfejsu API to zwrócenie odpowiedzi NotFound do żądań odwołujących się do kluczy, które nie istnieją, i odpowiedzi nieprawidłowego żądania, jeśli Walidacja modelu kończy się niepowodzeniem. Poniższy przykład ilustruje te dwie zasady w działaniu:

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Nie należy zezwalać na bałaganie metod akcji przy użyciu kodu warunkowego, takiego jak ten. Zamiast tego należy ściągnąć zasady do filtrów, które mogą być stosowane w zależności od tego, co jest potrzebne. W tym przykładzie sprawdzanie poprawności modelu, który powinien wystąpić za każdym razem, gdy polecenie jest wysyłane do interfejsu API, może być zastąpione przez następujący atrybut:

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

Można dodać `ValidateModelAttribute` do projektu jako zależność NuGet, dołączając pakiet [Ardalis. ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) . W przypadku interfejsów API można użyć `ApiController` atrybutu, aby wymusić to zachowanie bez potrzeby osobnego `ValidateModel` filtru.

Analogicznie, filtr może służyć do sprawdzenia, czy rekord istnieje i zwrócić 404 przed wykonaniem akcji, eliminując konieczność wykonywania tych testów w akcji. Po pobraniu wspólnych Konwencji i zorganizowaniu rozwiązania w celu oddzielenia kodu infrastruktury i logiki biznesowej od interfejsu użytkownika, metody akcji MVC powinny być niezwykle cienkie:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Aby dowiedzieć się więcej na temat implementowania filtrów i pobrać przykład roboczy z artykułu MSDN, [rzeczywistych filtrów ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>References — Tworzenie struktury aplikacji
>
> - **Obszary**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **Magazyn MSDN — wycinki funkcji dla ASP.NET Core MVC**  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN — Real World ASP.NET Core Filters**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpieczenia

Zabezpieczanie aplikacji sieci Web to duży temat z wieloma kwestiami. Na najbardziej podstawowym poziomie zabezpieczenia polegają na tym, że wiesz, z kogo pochodzi żądanie, a następnie upewniając się, że żądanie ma tylko dostęp do zasobów, które powinny. Uwierzytelnianie to proces porównujący poświadczenia dostarczone z żądaniem do tych w zaufanym magazynie danych, aby sprawdzić, czy żądanie powinno być traktowane jako pochodzące ze znanej jednostki. Autoryzacja to proces ograniczania dostępu do określonych zasobów na podstawie tożsamości użytkownika. Trzeci problem dotyczący zabezpieczeń chroni żądania przed podsłuchiwaniem przez inne osoby, dla którego należy [upewnić się, że protokół SSL jest używany przez aplikację](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Uwierzytelnianie

ASP.NET Core tożsamością jest system członkostwa, którego można użyć do obsługi funkcji logowania dla aplikacji. Obsługuje ona konta użytkowników lokalnych, a także dostawcę logowania zewnętrznego od dostawców, takich jak konto Microsoft, Twitter, Facebook, Google i inne. Oprócz tożsamości ASP.NET Core aplikacja może korzystać z uwierzytelniania systemu Windows lub innego dostawcy tożsamości, takiego jak [serwer tożsamości](https://github.com/IdentityServer/IdentityServer4).

ASP.NET Core tożsamość jest dołączana do nowych szablonów projektu, jeśli wybrano opcję konta poszczególnych użytkowników. Ten szablon obejmuje obsługę rejestracji, logowania, logowania zewnętrznego, zapomnianych haseł i dodatkowych funkcji.

![Wybieranie kont poszczególnych użytkowników w celu skonfigurowania tożsamości](./media/image7-3.png)

**Rysunek 7-3**. Wybierz opcję konta poszczególnych użytkowników, aby mieć wstępnie skonfigurowaną tożsamość.

Obsługa tożsamości jest konfigurowana podczas uruchamiania, zarówno w ConfigureServices, jak i w konfiguracji:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Ważne jest, aby UseIdentity pojawił się przed UseMvc w metodzie Configure. Podczas konfigurowania tożsamości w programie ConfigureServices należy zauważyć wywołanie AddDefaultTokenProviders. Nie ma nic do wykonania w przypadku tokenów, które mogą być używane do zabezpieczania komunikacji w sieci Web, ale zamiast tego odnoszą się do dostawców, którzy tworzą monity, które mogą być wysyłane do użytkowników za pośrednictwem wiadomości SMS lub poczty e-mail w celu potwierdzenia tożsamości.

Więcej informacji na temat [konfigurowania uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa) i [włączania zewnętrznych dostawców logowania](/aspnet/core/security/authentication/social/) można znaleźć w oficjalnym ASP.NET Core dokumentach.

### <a name="authorization"></a>Autoryzacja

Najprostsza forma autoryzacji obejmuje ograniczenie dostępu do użytkowników anonimowych. Można to osiągnąć przez zastosowanie \[\] atrybutu Autoryzuj do określonych kontrolerów lub akcji. Jeśli role są używane, atrybut można rozszerzyć, aby ograniczyć dostęp do użytkowników, którzy należą do określonych ról, jak pokazano poniżej:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

W takim przypadku użytkownicy należący do roli HRManager lub finanse (lub obie) będą mieli dostęp do SalaryController. Aby wymagać, aby użytkownik należał do wielu ról (nie tylko jeden z kilku), można zastosować atrybut wielokrotnie, określając wymaganą rolę za każdym razem.

Określanie niektórych zestawów ról jako ciągów w wielu różnych kontrolerach i akcjach może prowadzić do niepożądanego powtórzenia. Istnieje możliwość skonfigurowania zasad autoryzacji, które hermetyzują reguły autoryzacji, a następnie określania zasad zamiast poszczególnych ról przy zastosowaniu \[\] atrybutu Autoryzuj:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Korzystając z zasad w ten sposób, można oddzielić rodzaje akcji, które są ograniczone z określonych ról lub reguł, które mają zastosowanie. Później, jeśli utworzysz nową rolę, która musi mieć dostęp do określonych zasobów, można po prostu zaktualizować zasady, zamiast aktualizować każdą listę ról przy każdym \[\] autoryzowanym atrybucie.

#### <a name="claims"></a>Oświadczeń

Oświadczenia są parami wartości nazw, które reprezentują właściwości uwierzytelnionego użytkownika. Na przykład użytkownik może przechowywać numer pracownika jako roszczeń. Oświadczenia mogą być następnie używane jako część zasad autoryzacji. Można utworzyć zasady o nazwie "EmployeeOnly", które wymagają istnienia żądania o nazwie "EmployeeNumber", jak pokazano w poniższym przykładzie:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Te zasady mogą być następnie używane z \[\] atrybutem Autoryzuj do ochrony dowolnego kontrolera i/lub akcji, zgodnie z powyższym opisem.

#### <a name="securing-web-apis"></a>Zabezpieczanie interfejsów API sieci Web

Większość interfejsów API sieci Web powinna implementować system uwierzytelniania oparty na tokenach. Uwierzytelnianie tokenu jest bezstanowe i zaprojektowane do skalowalności. W systemie uwierzytelniania opartego na tokenach klient musi najpierw przeprowadzić uwierzytelnienie u dostawcy uwierzytelniania. Jeśli to się powiedzie, klient wystawia token, który jest po prostu zrozumiałą w sposób kryptograficznie ciągiem znaków. Gdy klient musi wydać żądanie do interfejsu API, dodaje ten token jako nagłówek w żądaniu. Następnie serwer sprawdza poprawność tokenu znalezionego w nagłówku żądania przed ukończeniem żądania. Rysunek 7-4 ilustruje ten proces.

![TokenAuth](./media/image7-4.png)

**Rysunek 7-4.** Uwierzytelnianie oparte na tokenach dla interfejsów API sieci Web.

Można utworzyć własną usługę uwierzytelniania, zintegrować ją z usługą Azure AD i uwierzytelnianiem OAuth lub wdrożyć usługę przy użyciu narzędzia typu open source, takiego jak [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Zabezpieczenia niestandardowe

Należy zwrócić szczególną uwagę na "wycofywanie własnych" implementacji kryptografii, członkostwa użytkowników lub systemu generacji tokenów. Istnieje wiele dostępnych alternatyw komercyjnych i typu "open source", które niemal wykorzystają lepsze zabezpieczenia niż implementacja niestandardowa.

> ### <a name="references--security"></a>Odwołania — zabezpieczenia
>
> - **Przegląd dokumentów dotyczących zabezpieczeń**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Wymuszanie protokołu SSL w aplikacji ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Wprowadzenie do tożsamości**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Wprowadzenie do autoryzacji**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Uwierzytelnianie i autoryzacja API Apps w Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Serwer tożsamości**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikacja z klientem

Oprócz obsługi stron i reagowania na żądania danych za pośrednictwem interfejsów API sieci Web aplikacje ASP.NET Core mogą komunikować się bezpośrednio z połączonymi klientami. Ta komunikacja wychodząca może korzystać z różnych technologii transportu, najczęściej używanych przez obiekty WebSockets. ASP.NET Core sygnalizujący to biblioteka, która ułatwia dodawanie funkcji komunikacji między klientami w czasie rzeczywistym do aplikacji. Program sygnalizujący obsługuje różne technologie transportowe, w tym elementy WebSockets, i dzieli wiele szczegółów implementacji od dewelopera.

Program ASP.NET Core sygnalizujący jest dostępny z ASP.NET Core od wersji 2,1.

Komunikacja klientów w czasie rzeczywistym, bez względu na to, czy używanie funkcji WebSockets bezpośrednio czy z innymi technikami jest przydatne w różnych scenariuszach aplikacji. Oto niektóre przykłady:

- Aplikacje do pokoju rozmów na żywo

- Monitorowanie aplikacji

- Aktualizacje postępu zadania

- Powiadomienia

- Interaktywne aplikacje formularzy

Podczas tworzenia komunikacji z klientem w aplikacjach są zwykle dwa składniki:

- Menedżer połączeń po stronie serwera (centrum sygnałów, websocketmanager WebSocketHandler)

- Biblioteka po stronie klienta

Klienci nie są ograniczeni do przeglądarek — aplikacje mobilne, aplikacje konsolowe i inne aplikacje natywne mogą również komunikować się przy użyciu sygnałów/obiektów WebSockets. Następujący prosty program umożliwia echo całej zawartości wysyłanej do aplikacji czatu do konsoli programu w ramach przykładowej aplikacji websocketmanager:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

Rozważ sposoby, w których aplikacje komunikują się bezpośrednio z aplikacjami klienckimi i należy rozważyć, czy komunikacja w czasie rzeczywistym poprawi środowisko użytkownika aplikacji.

> ### <a name="references--client-communication"></a>Odwołania — komunikacja z klientem
>
> - **ASP.NET Core sygnalizujący**  
>   <https://github.com/aspnet/SignalR>
> - **Menedżer obiektów WebSocket**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Projektowanie oparte na domenie — czy należy je zastosować?

Projektowanie oparte na domenie (DDD) to Agile podejście do tworzenia oprogramowania, które kładzie nacisk na _domenę biznesową_. W dużym stopniu naciska na komunikację i interakcję z ekspertami domeny biznesowej, którzy mogą odnosić się do deweloperów, w jaki działa system w świecie rzeczywistym. Jeśli na przykład tworzysz system, który obsługuje handel giełdowy, ekspertem domeny może być doświadczony Broker ds. it. DDD jest przeznaczony do rozwiązywania dużych i złożonych problemów związanych z biznesem. często nie jest to konieczne w przypadku mniejszych, prostszych aplikacji, ponieważ inwestycje w zrozumieniu i modelowania domeny nie są w tej samej postaci.

Podczas kompilowania oprogramowania po drodze, zespół (w tym udziałowcy nietechniczne i współautorzy) powinien opracować powszechny _Język_ dla obszaru problemu. Oznacza to, że ta sama terminologia powinna zostać użyta w przypadku modelowania rzeczywistego pojęcia, odpowiedniki oprogramowania i wszelkich struktur, które mogą istnieć, aby zachować koncepcję (na przykład tabele bazy danych). W związku z tym koncepcje opisane w języku powszechnym powinny stanowić podstawę dla _modelu domeny_.

Model domeny składa się z obiektów, które współdziałają ze sobą, aby reprezentować zachowanie systemu. Te obiekty mogą należeć do następujących kategorii:

- [Jednostki](https://deviq.com/entity/)reprezentujące obiekty z wątkiem tożsamości. Jednostki są zwykle przechowywane w stanie trwałości przy użyciu klucza, za pomocą którego mogą być później pobierane.

- [Agregaty](https://deviq.com/aggregate-pattern/)reprezentujące grupy obiektów, które powinny być utrwalane jako jednostka.

- [Obiekty wartości](https://deviq.com/value-object/), które reprezentują koncepcje, które mogą być porównane na podstawie sumy wartości ich właściwości. Na przykład DateRange składa się z daty rozpoczęcia i zakończenia.

- [Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują rzeczy wykonywane w systemie, które są istotne dla innych części systemu.

Należy zauważyć, że model domeny DDD powinien hermetyzować złożone zachowanie w modelu. Jednostki, w szczególności nie powinny być kolekcjami właściwości. Gdy model domeny nie ma zachowania i jedynie reprezentuje stan systemu, jest on uznawany za [model Anemic](https://deviq.com/anemic-model/), który jest NIEPOŻĄDANY w DDD.

Oprócz tych typów modeli DDD zazwyczaj wykorzystuje różne wzorce:

- [Repozytorium](https://deviq.com/repository-pattern/), aby uzyskać szczegółowe informacje o trwałości.

- [Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern)dla hermetyzowania złożonego tworzenia obiektów.

- Zdarzenia domeny w celu oddzielenia zachowań zależnych od zachowań wyzwalających.

- [Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)dla hermetyzowania złożonych zachowań i/lub szczegółów implementacji infrastruktury.

- [Polecenia](https://en.wikipedia.org/wiki/Command_pattern), do oddzielania poleceń i wykonywania polecenia.

- [Specyfikacja](https://deviq.com/specification-pattern/)dla hermetyzowania szczegółów zapytania.

DDD również zaleca użycie czystej architektury omówionej wcześniej, co pozwala na swobodne sprzęganie, hermetyzację i kod, który można łatwo zweryfikować przy użyciu testów jednostkowych.

### <a name="when-should-you-apply-ddd"></a>Kiedy należy zastosować DDD

DDD jest dobrze dostosowany do dużych aplikacji z znaczącą złożonością biznesową (nie tylko techniczną). Aplikacja powinna wymagać znajomości ekspertów domeny. Istnieje duże zachowanie w modelu domeny, reprezentujące reguły biznesowe i interakcje wykraczające poza zwykłe przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych.

### <a name="when-shouldnt-you-apply-ddd"></a>Kiedy nie należy stosować DDD

DDD obejmuje inwestycje w modelowanie, architekturę i komunikację, które mogą nie być uzasadnione w przypadku mniejszych aplikacji lub aplikacji, które zasadniczo CRUD (Tworzenie/odczytywanie/aktualizowanie/usuwanie). W przypadku wybrania podejścia do Twojej aplikacji po DDD, ale dowiesz się, że domena ma model Anemic bez zachowań, może być konieczne ponowne zawieszanie się z podejściem. Twoja aplikacja może nie potrzebować DDD lub może być potrzebna pomoc w refaktoryzacji aplikacji w celu hermetyzacji logiki biznesowej w modelu domeny, a nie w bazie danych lub interfejsie użytkownika.

Podejście hybrydowe będzie używać DDD tylko dla transakcyjnych lub bardziej złożonych obszarów aplikacji, ale nie dla prostszej CRUD lub tylko do odczytu części aplikacji. Na przykład nie musi mają ograniczenia agregacji, jeśli wykonujesz zapytanie o dane w celu wyświetlenia raportu lub wizualizacji danych dla pulpitu nawigacyjnego. Doskonale akceptowalne jest oddzielny, prostszy model odczytu dla takich wymagań.

> ### <a name="references--domain-driven-design"></a>Odwołania — Projektowanie oparte na domenie
>
> - **DDD w zwykłym języku angielskim (odpowiedź StackOverflow)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>wdrażania

W procesie wdrażania aplikacji ASP.NET Core należy wykonać kilka kroków, bez względu na to, gdzie będzie ona hostowana. Pierwszym krokiem jest opublikowanie aplikacji, którą można wykonać przy użyciu dotnet publish interfejsu wiersza polecenia. Spowoduje to skompilowanie aplikacji i umieszczenie wszystkich plików wymaganych do uruchomienia aplikacji w wydzielonym folderze. W przypadku wdrażania z programu Visual Studio ten krok jest wykonywany automatycznie. Folder publikowania zawiera pliki. exe i. dll dla aplikacji i jej zależności. Aplikacja samodzielna zawiera również wersję środowiska uruchomieniowego .NET. Aplikacje ASP.NET Core zawierają również pliki konfiguracji, statyczne zasoby klienta i widoki MVC.

Aplikacje ASP.NET Core są aplikacjami konsolowymi, które należy uruchomić, gdy serwer jest uruchamiany i uruchamiany ponownie, jeśli wystąpi awaria aplikacji (lub serwera). Za pomocą Menedżera procesów można zautomatyzować ten proces. Najbardziej typowymi menedżerami procesów dla ASP.NET Core są Nginx i Apache w systemach Linux i IIS lub Windows Service w systemie Windows.

Oprócz Menedżera procesów ASP.NET Core aplikacje hostowane na serwerze sieci Web Kestrel muszą używać serwera zwrotnego serwera proxy. Odwrotny serwer proxy odbiera żądania HTTP z Internetu i przekazuje je do Kestrel po pewnej wstępnej obsłudze. Odwrotne serwery proxy zapewniają warstwę zabezpieczeń dla aplikacji i są wymagane dla wdrożeń brzegowych (narażonych na ruch z Internetu). Kestrel jest stosunkowo nowy i nie oferuje jeszcze obrony przed niektórymi atakami. Kestrel również nie obsługuje hostowania wielu aplikacji na tym samym porcie, dlatego nie można używać technik takich jak nagłówki hosta, aby umożliwić hostowanie wielu aplikacji na tym samym porcie i adresie IP.

![Kestrel z Internetem](./media/image7-5.png)

**Rysunek 7-5**. ASP.NET hostowane w Kestrel za odwrotnym serwerze proxy

Innym scenariuszem, w którym może być przydatny zwrotny serwer proxy, jest zabezpieczanie wielu aplikacji przy użyciu protokołu SSL/HTTPS. W takim przypadku tylko zwrotny serwer proxy musi mieć skonfigurowany protokół SSL. Komunikacja między odwrotnym serwerem proxy a Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano na rysunku 7-6.

![ASP.NET hostowane za pośrednictwem protokołu HTTPS zwrotnego serwera proxy](./media/image7-6.png)

**Rysunek 7-6**. ASP.NET hostowane za pośrednictwem protokołu HTTPS zwrotnego serwera proxy

Coraz bardziej popularne podejście polega na hostowaniu ASP.NET Core aplikacji w kontenerze platformy Docker, który można hostować lokalnie lub wdrożyć na platformie Azure na potrzeby hostingu opartego na chmurze. Kontener platformy Docker może zawierać kod aplikacji działający w Kestrel i zostałby wdrożony za odwrotnym serwerem proxy, jak pokazano powyżej.

Jeśli aplikacja jest obsługiwana na platformie Azure, można użyć Application Gateway Microsoft Azure jako dedykowanego urządzenia wirtualnego, aby zapewnić kilka usług. Oprócz działania jako zwrotny serwer proxy dla poszczególnych aplikacji, Application Gateway może również oferować następujące funkcje:

- Równoważenie obciążenia HTTP

- Odciążanie protokołu SSL (tylko protokół SSL do Internetu)

- Kompleksowa próba SSL

- Routing między lokacjami (konsolidowanie do 20 lokacji na jednym Application Gateway)

- Zapora aplikacji sieci Web

- Obsługa protokołu WebSocket

- Zaawansowana diagnostyka

_Dowiedz się więcej o opcjach wdrażania platformy Azure w [rozdziale 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odwołania — wdrażanie
>
> - **Omówienie hostingu i wdrażania**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kiedy używać Kestrel z zwrotnym serwerem proxy**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostowanie aplikacji ASP.NET Core w platformie Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Wprowadzenie do usługi Azure Application Gateway**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Poprzedni](common-client-side-web-technologies.md)Następny
>[](work-with-data-in-asp-net-core-apps.md)
