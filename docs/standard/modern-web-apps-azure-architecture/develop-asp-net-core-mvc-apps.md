---
title: Tworzenie platformy ASP.NET Core MVC aplikacji
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Tworzenie aplikacji programu ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 1d58f6ef590e798e52730d79e56b8c16830c1712
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128391"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Tworzenie platformy ASP.NET Core MVC aplikacji

> "Należy nie można pobrać jej prawej po raz pierwszy. To wszechobecne uzyskać odpowiednie ostatniego".  
> _— Andrew Hunt i Davida Thomas_

Platforma ASP.NET Core to dla wielu platform, typu open source umożliwiająca tworzenie aplikacji nowoczesne rozwiązania sieci web, które są zoptymalizowane pod kątem chmury. Aplikacje platformy ASP.NET Core to uproszczone, modułowe, z wbudowaną obsługę wstrzykiwania zależności, umożliwiając większe możliwości testowania i łatwość konserwacji. W połączeniu z MVC, który obsługuje tworzenie nowoczesnych internetowych interfejsów API oprócz aplikacji opartych na widok, platforma ASP.NET Core to Rozbudowana platforma umożliwiające tworzenie aplikacji sieci web enterprise.

## <a name="mvc-and-razor-pages"></a>MVC i stron Razor

Platforma ASP.NET Core MVC udostępnia wiele funkcji, które są przydatne do tworzenia interfejsów API i aplikacje sieci web. Termin MVC oznacza "Model-View-Controller", wzorzec interfejsu użytkownika, który powoduje podział obowiązków odpowiadania na żądania użytkowników na kilka fragmentów. Oprócz tego wzorca, możesz również wdrożyć funkcje w aplikacjach ASP.NET Core jako stron Razor. Strony razor są wbudowane w platformy ASP.NET Core MVC i te same funkcje na użytek routingu powiązanie modelu, itp. Jednak zamiast mające oddzielnych folderów i plików dla kontrolerów, widoki, itp., a przy użyciu opartych na atrybutach routingu, stron Razor są umieszczane w jednym folderze ("/ strony"), trasę na podstawie względnej lokalizacji w tym folderze, a uchwyt żądania obsługi zamiast akcji kontrolera.

Podczas tworzenia nowej aplikacji platformy ASP.NET Core, powinien mieć planu, należy pamiętać o rodzaju aplikacji, którą chcesz skompilować. W programie Visual Studio możesz wybrać kilka szablonów. Trzy Najpopularniejsze szablony projektów są interfejsu API sieci Web, aplikacji sieci Web i aplikacji sieci Web (Model-View-Controller). Ta decyzja można wprowadzać tylko w przypadku, gdy należy najpierw utworzyć projekt, ale nie jest on nieodwołalną decyzją. Projekt interfejsu API sieci Web używa standardowych kontrolerów Model-View-Controller — po prostu nie ma widoków domyślnie. Podobnie domyślnego szablonu aplikacji sieci Web używa stron Razor i dlatego też brakuje folderu widoków. W tych projektach później w celu obsługi zachowanie na podstawie widoku można dodać folder widoków. Domyślnie projekty składnika Web API i Model-View-Controller nie zawierają folder stron, ale możesz je dodać później w celu obsługi zachowanie oparte na stron Razor. Można potraktować te trzy szablony jako obsługuje trzy różne rodzaje interakcji z użytkownikiem domyślne: danych (interfejs API sieci web), na stronie i na podstawie widoku. Można jednak mieszać i dopasowywać wybranych lub wszystkich z nich w ramach pojedynczego projektu, w razie potrzeby.

### <a name="why-razor-pages"></a>Dlaczego stron Razor?

Strony razor jest podejście domyślne dla nowych aplikacji sieci web w programie Visual Studio. Strony razor zapewnia prostszy sposób tworzenia funkcji oparty na stronie aplikacji, takich jak formularze bez SPA. Przy użyciu widoków i kontrolerów, były wspólne dla aplikacji do bardzo dużych kontrolery, które działały z wielu różnych składników zależnych, a widok modeli i zwrócony z wielu różnych widoków. To spowodowało wiele złożoności i często spowodowało kontrolery, które nie zastosowano zasady pojedynczej odpowiedzialności lub zasadami otwarty/zamknięty skutecznie. Strony razor rozwiązuje ten problem poprzez hermetyzację logiki po stronie serwera dla danego logiczne "strony" w aplikacji sieci web za pomocą jego znaczników Razor. Strona Razor nie logiki po stronie serwera może po prostu składają się z pliku Razor (na przykład "Index.cshtml"). Większość nietrywialnymi stron Razor będzie jednak skojarzona strona klasy modelu, który zwyczajowo ma nazwę taki sam jak plik Razor z rozszerzeniem "CS" (na przykład "Index.cshtml.cs").

Strona Razor strony modelu łączy obowiązków kontroler MVC i viewmodel. Zamiast obsługę żądania za pomocą metody akcji kontrolera, obsługi modelu strony, takich jak "OnGet()" są wykonywane, renderowanie ich skojarzona strona domyślnie. Strony razor upraszcza proces tworzenia poszczególnych stron w aplikacji ASP.NET Core, przy jednoczesnym dalszym zapewnianiu funkcji architektury platformy ASP.NET Core MVC. Są one to wybór dobre domyślne dla nowych funkcji opartych na stronie.

### <a name="when-to-use-mvc"></a>Kiedy należy używać MVC

Jeśli tworzysz interfejsów API sieci web wzorzec MVC pozwala także lepszym rozwiązaniem niż podjęcie próby korzystania ze stron Razor. Jeśli projekt będzie tylko udostępnić punkty końcowe interfejsu API sieci web, najlepiej należy zacząć od szablonu projektu interfejsu API sieci Web, ale w przeciwnym razie jest łatwe do dodania do dowolnej aplikacji platformy ASP.NET Core kontrolery i skojarzone punkty końcowe interfejsu API. Jeśli w przypadku migrowania istniejącej aplikacji platformy ASP.NET MVC 5 lub jego starszej wersji platformy ASP.NET Core MVC i chcesz to zrobić z najmniejszą ilością nakład pracy, należy użyć podejście oparte na widoku MVC. Po utworzeniu początkowej migracji, będziesz w stanie ocenić, czy warto przyjąć stron Razor na temat nowych funkcji, lub nawet całościowego migracji.

Czy istnieje możliwość tworzenia aplikacji sieci web przy użyciu stron Razor lub widoków MVC, aplikacja będzie mieć podobną wydajność i będzie zawierać obsługę wstrzykiwania zależności filtry, wiązania modelu i sprawdzania poprawności, itp.

## <a name="mapping-requests-to-responses"></a>Mapowania żądania do odpowiedzi

Centrum w aplikacji platformy ASP.NET Core żądania przychodzące są mapowane na wychodzące odpowiedzi serwera. Na niskim poziomie odbywa się za pomocą oprogramowania pośredniczącego i proste aplikacje platformy ASP.NET Core i mikrousług może składać się wyłącznie z niestandardowego oprogramowania pośredniczącego. Korzystając z platformy ASP.NET Core MVC, można pracować na nieco wyższy poziom, myśl pod względem _trasy_, _kontrolerów_, i _akcje_. Każdego żądania przychodzącego jest porównywana z tabeli routingu aplikacji, a jeśli znajduje się trasy zgodne, skojarzona metoda akcji (należące do kontrolera) jest wywoływana, aby obsłużyć żądanie. Jeśli żadna trasa dopasowania zostanie znaleziony, jest wywoływana procedura obsługi błędów (w tym przypadku zwracając wynik NotFound).

Konwencjonalne tras i/lub tras atrybutów, można użyć aplikacji ASP.NET Core MVC. Konwencjonalne trasy są definiowane w kodzie, określając routing _konwencje_ przy użyciu składni podobnie jak w poniższym przykładzie:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

W tym przykładzie dodano trasę o nazwie "domyślna" do tabeli routingu. Definiuje szablon trasy z symbolami zastępczymi _kontrolera_, _akcji_, i _identyfikator_. Symbole zastępcze kontrolerów i akcji ma określony domyślny ("Home" i "Index", odpowiednio), a symbol zastępczy identyfikator jest opcjonalny (na mocy niniejszej "?" zastosowano). Konwencji zdefiniowane w tym miejscu stany odpowiadające pierwszej części żądania do nazwy kontrolera, a druga sekcja do akcji, a następnie w razie potrzeby trzeciej części będzie reprezentować parametru identyfikatora. Konwencjonalne trasy są zazwyczaj definiowane w jednym miejscu aplikacji, takich jak w metodzie Konfiguruj w klasie uruchamiania.

Tras atrybutów są stosowane do kontrolerów i akcji bezpośrednio, a nie określono globalnie. To ma tę zaletę, dzięki czemu mogą znacznie szybciej odnajdywać podczas poszukujesz w konkretnej metody, ale oznacza, że informacje routingu nie są przechowywane w jednym miejscu w aplikacji. Za pomocą tras atrybutów można można łatwo określić wiele tras dla danej akcji, a także połączyć tras między kontrolerów i akcji. Na przykład:

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

Można określić trasy w [HttpGet] i podobne atrybuty, unikając konieczności dodawania oddziel atrybuty [trasy]. Tras atrybutów można także użyć tokenów, aby zmniejszyć liczbę powtórzeń nazwy kontrolera lub akcji, jak pokazano poniżej:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Strony razor nie korzysta z trasami atrybutów. Informacje o szablonie dodatkowe trasy dla strony Razor można określić jako część jej `@page` dyrektywy:

```csharp
@page "{id:int}"
```

W poprzednim przykładzie, ta strona będzie pasował trasy z liczbą całkowitą `id` parametru. Na przykład *Products.cshtml* strony znajduje się w folderze głównym `/Pages` miałby tej trasy:

```csharp
"/Products/123"
```

Gdy danego żądania został dopasowany do trasy, ale przed akcją, metoda jest wywoływana, ASP.NET Core MVC wykona [wiązanie modelu](/aspnet/core/mvc/models/model-binding) i [Walidacja modelu](/aspnet/core/mvc/models/validation) na żądanie. Wiązanie modelu jest odpowiedzialny za konwersji danych przychodzących HTTP do typów .NET określane jako parametry metody akcji, które ma zostać wywołana. Na przykład jeśli metoda akcji oczekuje parametru id int, wiązania modelu będzie podejmowana próba udostępnienia tego parametru z wartością podana jako część żądania. Aby to zrobić, wiązanie modelu szuka wartości przesłanego formularza, wartości trasy, sama i wartości ciągu zapytania. Przy założeniu, że wartość zostanie znaleziony, zostanie przekonwertowany na liczbę całkowitą przed przekazaniem do metody akcji.

Po powiązaniu modelu, ale przed wywołaniem metody akcji występuje weryfikacji modelu. Sprawdzanie poprawności modelu korzysta z opcjonalnych atrybutów na typ modelu, a może pomóc upewnić się, że obiekt podany model spełnia określone wymagania danych. Niektóre wartości mogą być określone jako wymagane lub ograniczone do niektórych długości lub zakresu liczbowego, itp. Jeśli podano atrybutów sprawdzania poprawności, ale modelu nie jest zgodny z ich wymaganiami, właściwość ModelState.IsValid będzie mieć wartość false, a zestaw reguł sprawdzania poprawności, które uległy awarii, będzie można wysłać do klienta wysyłającego żądanie.

Jeśli używasz weryfikacji modelu, należy się, że zawsze sprawdzić, czy model jest prawidłowy, przed wykonaniem dowolnego polecenia zmiany stanu, aby upewnić się, że aplikacja nie jest uszkodzony, przez nieprawidłowe dane. Możesz użyć [filtru](/aspnet/core/mvc/controllers/filters) Aby uniknąć konieczności dodawania kodu w tym w każdym działaniu. Platforma ASP.NET Core MVC filtry oferują sposób przechwycenia grup żądań, tak, aby wspólnych zasad i odciąż przekrojowe zagadnienia, które mogą być stosowane na podstawie docelowej. Filtry można stosować do poszczególnych czynności w całej kontrolerów, lub globalnie dla aplikacji.

W przypadku internetowych interfejsów API obsługuje platformy ASP.NET Core MVC [ _negocjacji zawartości_](/aspnet/core/mvc/models/formatting), zezwolenie na żądania określić, jak powinny być sformatowane odpowiedzi. Oparte na nagłówki podany w żądaniu, akcje zwracający dane sformatuje odpowiedzi XML, JSON lub innego obsługiwanego formatu. Ta funkcja umożliwia tego samego interfejsu API, który będzie używany przez wielu klientów z różnymi danymi format wymaganiami.

Projekty sieci Web interfejsu API należy wziąć pod uwagę przy użyciu `[ApiController]` atrybut, który można zastosować do poszczególnych kontrolerów, klasę kontrolera podstawowego lub cały zespół. Ten atrybut dodaje sprawdzania poprawności modelu automatyczne i działania z modelem nieprawidłowy zwróci element BadRequest ze szczegółami błędów sprawdzania poprawności. Ten atrybut wymaga również wszystkie akcje mają trasę atrybutu, a nie za pomocą konwencjonalnych trasy i zwraca szczegółowe informacje o ProblemDetails w odpowiedzi na błędy.

> ### <a name="references--mapping-requests-to-responses"></a>Odwołania — mapowania żądania do odpowiedzi
>
> - **Routing do akcji kontrolera**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Wiązanie modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Walidacja modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Atrybut klasy ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/?view=aspnetcore-2.2>

## <a name="working-with-dependencies"></a>Praca z zależnościami

Platforma ASP.NET Core ma wbudowaną obsługę i wewnętrznie sprawia, że użycie to technika, znana jako [wstrzykiwanie zależności](/aspnet/core/fundamentals/dependency-injection). Wstrzykiwanie zależności jest techniką, która umożliwia luźne powiązanie między różne części aplikacji. Im sprzężenia jest pożądane, ponieważ ułatwia Izolowanie części aplikacji, co umożliwia testowanie lub wymiany. Również powoduje mniej prawdopodobne, że zmiany w jednej części aplikacji będą miały wpływ nieoczekiwany gdzieś w aplikacji. Wstrzykiwanie zależności opiera się na zasadzie odwrócenie zależności i często ma kluczowe znaczenie dla osiągnięcia zasady otwarty/zamknięty. Podczas obliczania, jak aplikacja współpracuje z jego zależności, należy [statyczne przylepna](https://deviq.com/static-cling/) kodu zapachu i pamiętać aphorism "[nowe jest pośredniczącego](https://ardalis.com/new-is-glue)."

Statyczne przylepna występuje, gdy Twoich zajęciach wykonywać wywołania do metod statycznych lub dostępu do właściwości statycznej, które ma efekty uboczne ani zależności w infrastrukturze. Na przykład w przypadku metody, która wywołuje statyczną metodę, która z kolei zapis w bazie danych, metoda jest ściśle powiązany z bazą danych. Wszystko, co powoduje przerwanie wywołania bazy danych spowoduje przerwanie metodę. Testowanie takich metod jest bardzo trudne, ponieważ takie testy wymagają komercyjnych pozorowania bibliotek testowanie wywołania statycznych, lub należy badać tylko z bazą danych testów w miejscu. Wywołania statycznych, które nie mają żadnych zależności w infrastrukturze, zwłaszcza tych, które są całkowicie bezstanowe są w dobrym stanie wywołać i nie ma wpływu na sprzężenie lub testowania (poza sprzężenia kodu na wywołanie statyczne, sam).

Wielu programistów zrozumieć ryzyko przylepna statycznych i stan globalny, ale będzie nadal ściśle Połącz swój kod do implementacji określonego poprzez bezpośrednie utworzenie wystąpienia. "Nowe jest pośredniczącego" ma być przypomnieniem o tym sprzężenia, a nie ogólne potępianiu użytkowania `new` — słowo kluczowe. Podobnie jak za pomocą wywołania metody statycznej nowych wystąpień typów, które zwykle mają bez zewnętrznych zależności nie ściśle sprzęgnięcie kodu do szczegółów implementacji lub utrudniają testowania. Ale każdorazowo, gdy jest tworzone wystąpienie klasy przyjrzeć tylko krótkie należy wziąć pod uwagę, czy warto się kodować sprzętowo tego konkretnego wystąpienia w tej konkretnej lokalizacji, czy byłoby lepsze projektu, aby zażądać tego wystąpienia jako zależność.

### <a name="declare-your-dependencies"></a>Zadeklaruj zależności

Platforma ASP.NET Core powstał z myślą o metod i klas zadeklarować ich zależności, żądając jako argumenty. Aplikacje ASP.NET są zazwyczaj ustawiane w klasie uruchamiania, który sam jest skonfigurowany do obsługi iniekcji zależności w kilku miejscach. Jeśli klasa uruchamiania ma konstruktora, może zażądać jej zależności za pomocą konstruktora, w następujący sposób:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Klasa początkowa jest interesujące, że nie ma żadnych wymagań jawnego typu dla niego. Nie dziedziczy z klasy bazowej specjalne uruchamiania nie zawiera implementacji dowolnego określonego interfejsu. Możesz nadać mu konstruktora, czy nie. Ponadto można określić dowolną liczbę parametrów w Konstruktorze dowolną. Podczas uruchamiania hosta sieci web skonfigurowanych dla danej aplikacji będzie wywoływać klasę uruchamiania, którą Informujesz, aby użyć i użyje wstrzykiwanie zależności w celu wypełnienia żadnych zależności, o których klasa startowa. wymaga. Oczywiście jeśli użytkownik zażąda parametry, które nie są skonfigurowane w kontenerze usługi używane przez program ASP.NET Core, otrzymasz wyjątek, ale tak długo, jak trzymaj zależności kontenera obsługującemu, możesz poprosić o coś, czego chcesz.

Wstrzykiwanie zależności jest wbudowana w aplikacji platformy ASP.NET Core bezpośrednio od samego początku, po utworzeniu wystąpienia uruchomienia. Nie zatrzymał istnieje dla klasy uruchamiania. Możesz również poprosić o zależności w metodzie skonfiguruj:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices jest wyjątek do zachowania; należy ją wykonać tylko jeden parametr typu IServiceCollection. Tak naprawdę nie musi obsługiwać wstrzykiwanie zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów do kontenera usług, a na drugim ma dostęp do wszystkich usług aktualnie skonfigurowane za pomocą parametru IServiceCollection. W związku z tym można pracować z zdefiniowanych w kolekcji usługi ASP.NET Core w każdej części klasy uruchamiania, żądając wymagane usługi, jako parametr lub poprzez współdziałanie z IServiceCollection w ConfigureServices zależności.

> [!NOTE]
> Jeśli musisz upewnić się, niektóre usługi są dostępne do klasy uruchamiania, można je skonfigurować przy użyciu WebHostBuilder oraz sposób jej ConfigureServices.

Klasa początkowa to model umożliwiający powinien strukturą innych części aplikacji platformy ASP.NET Core z kontrolerów, aby oprogramowanie pośredniczące do filtrów do swoich własnych usług. W obu przypadkach należy przestrzegać [jawne zależności zasady](https://deviq.com/explicit-dependencies-principle/)żądania z zależności, a nie bezpośrednio są one tworzone i wykorzystując wstrzykiwanie zależności w całej aplikacji. Należy zachować ostrożność, z którym i w jaki sposób bezpośrednio wystąpienia implementacji, szczególnie usług i obiektów, które współdziałać z infrastrukturą lub mieć skutki uboczne. Preferuje pracę z abstrakcje zdefiniowane w podstawowych aplikacji i przekazany jako argumenty do hardcoding odwołania do typów konkretnej implementacji.

## <a name="structuring-the-application"></a>Tworzenie struktury aplikacji

Aplikacje monolityczne zwykle mają jeden punkt wejścia. W przypadku aplikacji sieci web platformy ASP.NET Core punkt wejścia będą projektu sieci web platformy ASP.NET Core. Jednakże, nie oznacza, że rozwiązanie powinna składać się z pojedynczego projektu. Warto podzielić aplikację w różnych warstwach, aby wykonać separacji zagadnień. Gdy podzielone na warstwy, warto wykracza poza folderów do osobnych projektów, które może pomóc w osiągnięciu lepszej hermetyzacji. Najlepszym rozwiązaniem, aby osiągnąć te cele za pomocą aplikacji platformy ASP.NET Core jest odmianą czystej architektury omówionych w rozdziale 5. Następujące tego podejścia rozwiązania aplikacji będzie składać się z oddzielnych bibliotek interfejsu użytkownika, infrastruktury i ApplicationCore.

Oprócz tych projektów projekty testowe w oddzielnych uwzględniono również (testowanie opisanej w rozdziale 9).

Model obiektu i interfejsy aplikacji będzie umieszczona w projekcie ApplicationCore. Ten projekt będzie miał tak małą zależności jak to możliwe, a inne projekty w rozwiązaniu zostaną do niego odwołują. Jednostki biznesowe, które muszą zostać utrwalona, są zdefiniowane w projekcie ApplicationCore, zgodnie z usług, które nie są bezpośrednio zależne od infrastruktury.

Szczegóły implementacji, takich jak jak odbywa się trwałości lub jak mogą być wysyłane powiadomienia do użytkownika, są przechowywane w projekcie infrastruktury. Ten projekt będzie odwoływać się do pakietów specyficzne dla implementacji, takich jak Entity Framework Core, ale nie powinny uwidaczniać szczegółowe informacje o tych implementacji, poza projektem. Usługi infrastruktury i repozytoriów powinny implementować interfejsy, które są zdefiniowane w projekcie ApplicationCore i ich implementacji trwałości jest odpowiedzialny za pobieranie i przechowywanie podmioty zdefiniowane w ApplicationCore.

Projekt interfejsu użytkownika programu ASP.NET Core jest odpowiedzialny za jakiekolwiek wątpliwości poziomu interfejsu użytkownika, ale nie może zawierać szczegóły logikę lub infrastruktury firmy. W rzeczywistości najlepiej go nie należy jeszcze mają zależności w projekcie infrastruktury, co poprawi, upewnij się, że przypadkowo wprowadzone nie zależności między dwa projekty. Można to osiągnąć za pomocą konteneru DI innych firm, takich jak Autofac, dzięki czemu można zdefiniować reguły DI w klasach modułu w każdym projekcie.

Oddzielenie aplikacji, od szczegółów implementacji na innym sposobem jest mikrousługi wywołanie aplikacji, może być wdrażane w poszczególnych kontenerach platformy Docker. Jeszcze większe rozdzielenie problemów i oddzielenie niż wykorzystaniu DI między dwa projekty, ale ma dodatkową złożoność.

### <a name="feature-organization"></a>Funkcja organizacji

Domyślnie aplikacje platformy ASP.NET Core organizowanie ich strukturę folderów w celu uwzględnienia kontrolery i widoki i często modele widoków. Kod po stronie klienta do obsługi tych struktur po stronie serwera są zwykle przechowywane osobno w folderze wwwroot. Jednak duże aplikacje mogą wystąpić problemy z tej organizacji, ponieważ często nad dowolnym dana funkcja wymaga przechodzenie między te foldery. Pobiera to bardziej trudne, wraz z rozwojem liczbę plików i podfolderów w folderze każdego skutkuje dużym stopniem przewijanie w Eksploratorze rozwiązań. Jedno rozwiązanie tego problemu jest zorganizowanie kod aplikacji przez _funkcji_ zamiast według typu pliku. Ten styl organizacji jest zwykle określane jako funkcja foldery lub [funkcji wycinki](https://msdn.microsoft.com/magazine/mt763233.aspx) (Zobacz również: [Wycinki pionowy](https://deviq.com/vertical-slices/)).

Platforma ASP.NET Core MVC obsługuje obszary, w tym celu. Obszary można utworzyć oddzielne zestawy kontrolery i widoki folderów (a także żadnych modeli skojarzone) w każdym folderze obszaru. Rysunek 7-1 przedstawiono przykład struktury folderów, korzystać z obszarów.

![](./media/image7-1.png)

Rysunek 7-1 próbka obszaru organizacji

Korzystając z obszarów, należy użyć atrybutów do dekorowania kontrolerach nazwą obszaru, do której należą:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Należy również dodać obsługę obszaru do trasy:

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

Oprócz wbudowanych funkcji dla obszarów umożliwia także własne strukturę folderów i konwencje zamiast atrybutów i tras niestandardowych. Umożliwi to funkcja foldery, które nie zawierają oddzielnych folderów widoki, kontrolery, itp., utrzymywanie płaski hierarchii i ułatwiając widać wszystkie powiązane pliki w jednym miejscu dla każdej funkcji.

ASP.NET Core używa konwencji wbudowanych typów kontrolowanie swojego zachowania. Można zmodyfikować lub zastąpienie tych konwencji. Na przykład można utworzyć z Konwencją, która zostanie automatycznie pobrana nazwa funkcji dla danego kontrolera, w oparciu o jego przestrzeń nazw (korelującą zwykle do folderu, w którym znajduje się kontroler):

```csharp
FeatureConvention : IControllerModelConvention
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

Następnie możesz określić tę Konwencję jako opcja po dodaniu pomocy technicznej dla platformy MVC dla aplikacji w ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

Platforma ASP.NET Core MVC również używa konwencji zlokalizować widoki. Można zastąpić go z Konwencją niestandardowe, aby widoki będą znajdować się w folderach funkcji (przy użyciu nazwy funkcji podana przez FeatureConvention powyżej). Możesz dowiedzieć się więcej na temat tego podejścia i pobrać próbkę pracy z artykuł w witrynie MSDN [wycinki funkcji dla platformy ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Odciąż przekrojowe zagadnienia

Miarę wzrostu aplikacji, staje się coraz ważniejsze wyodrębnić odciąż przekrojowe zagadnienia, aby nie zawierała dublowania i zachowania spójności. Kilka przykładów odciąż przekrojowe zagadnienia w aplikacjach ASP.NET Core to uwierzytelnianie, reguł sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługę błędów, chociaż istnieje wiele innych. Platforma ASP.NET Core MVC [filtry](/aspnet/core/mvc/controllers/filters) pozwala na uruchamianie kodu przed lub po pewne czynności w potoku przetwarzania żądań. Na przykład filtr, można uruchomić przed i po nim powiązanie modelu, przed i po wykonaniu akcji lub przed i po wyniku akcji. Filtr autoryzacji można również użyć do kontrolowania dostępu do pozostałego potoku. Jeśli skonfigurowano rysunki 7-2 pokazuje jak żądanie jest przesyłane wykonywania filtry przekazywania.

![Żądanie jest przetwarzane przez filtry autoryzacji, filtrów zasobów, powiązanie modelu, filtry akcji, wykonywanie akcji i konwersji wynik akcji, filtry wyjątków, filtry wyników i wynik wykonywania. Na jej poziomie żądania jest przetwarzany tylko przez filtry wyników i filtrów zasobów przed staje się odpowiedzi wysyłane do klienta.](./media/image7-2.png)

Wykonanie żądania na rysunku 7-2 przy użyciu filtrów i potok żądań.

Filtry zwykle są implementowane jako atrybuty, dzięki czemu można je zastosować do kontrolerów i akcji (lub nawet globalnie). Po dodaniu w taki sposób, filtry określone zastąpienia poziomie akcji lub bazują filtry określone na poziomie kontrolera znacznej zastąpić filtrów globalnych. Na przykład \[trasy\] atrybut może służyć do zbudowania tras między kontrolerów i akcji. Podobnie autoryzacji można konfigurować na poziomie kontrolera i następnie zastępowane przez poszczególne akcje, tak jak pokazano w następującym przykładzie:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

Pierwszej metody logowania, używa filtra AllowAnonymous (atrybut), aby zastąpić filtr autoryzacji, należy ustawić na poziomie kontrolera. Akcja ForgotPassword (i innych działań w klasie, która nie ma atrybutu AllowAnonymous) będzie wymagać uwierzytelnionego żądania.

Filtry można wyeliminować dublowanie w postaci wspólnego obsługi błędów zasady dla interfejsów API. Na przykład typowych zasad interfejsu API jest zwracana NotFound odpowiedzi na żądania PRZYWOŁUJĄCE klucze, które nie istnieją, a element BadRequest odpowiedź, gdy sprawdzanie poprawności modelu nie powiedzie się. W poniższym przykładzie pokazano te dwie zasady w akcji:

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

Nie zezwalaj na swoje metody akcji, aby zapełnić kod warunkowy następująco. Zamiast tego należy ściągnąć zasady do filtrów, które mogą być stosowane w zgodnie z potrzebami. W tym przykładzie można zastąpić sprawdzenie poprawności modelu, który powinno nastąpić każdym razem, gdy polecenie jest wysyłany do interfejsu API, według następującego atrybutu:

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

Możesz dodać `ValidateModelAttribute` do projektu jako zależności NuGet, umieszczając [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) pakietu. W przypadku interfejsów API, można użyć `ApiController` atrybutu, aby wymusić to zachowanie, bez konieczności oddzielnego `ValidateModel` filtru.

Podobnie filtr może służyć do sprawdzania, czy rekord istnieje i zwrócić kod 404, przed wykonaniem akcji, eliminując konieczność wykonywania tych sprawdzeń w akcji. Po ściągane się typowych Konwencji i zorganizowane rozwiązania, aby oddzielić infrastruktury kodu i logiki biznesowej od interfejsu użytkownika, MVC metody akcji powinny być bardzo cienka:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Możesz dowiedzieć się więcej o implementacji filtry i pobrać przykładowy pracy z artykuł w witrynie MSDN [rzeczywistych platformy ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Odwołania — struktury aplikacji
>
> - **Obszary**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine — wycinki funkcji dla platformy ASP.NET Core MVC**  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN — rzeczywistych platformy ASP.NET Core MVC filtry**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpieczenia

Zabezpieczanie aplikacji sieci web jest duże tematu, z wiele uwagi. Na najbardziej podstawowym poziomie zabezpieczeń obejmuje zapewnienie, że wiesz, kto pochodzące z danego żądania i zapewnienie, że żądanie musi jedynie dostęp do zasobów, które powinno. Uwierzytelnianie to proces porównanie poświadczenia dostarczone z żądaniem w zaufanym magazynie danych, aby zobaczyć, czy żądanie powinny być traktowane jako pochodzący od znanych jednostki. Autoryzacja to proces ograniczanie dostępu do niektórych zasobów na podstawie tożsamości użytkownika. Trzeci kwestią zabezpieczeń chroni żądań podsłuchiwaniu przez osoby trzecie, dla których należy co najmniej [upewnij się, że protokół SSL jest używany przez aplikację](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Uwierzytelnianie

Tożsamość platformy ASP.NET Core jest systemu członkostwa, służących do obsługi funkcji logowania dla swojej aplikacji. Ma ona obsługi dla kont użytkowników lokalnych, a także informacje o obsłudze dostawców zewnętrznych danych logowania od dostawców, takich jak Account Microsoft, Twitter, Facebook i Google. Oprócz tożsamości platformy ASP.NET Core, aplikacja może używać uwierzytelniania systemu windows lub z dostawcy tożsamości innych firm, takich jak [serwera tożsamości](https://github.com/IdentityServer/IdentityServer4).

Tożsamości platformy ASP.NET Core znajduje się w nowe szablony projektów, jeśli wybrano opcję indywidualnych kont użytkowników. Ten szablon obejmuje obsługę rejestracji, logowania, logowania zewnętrzne, zapomniane hasła i dodatkowe funkcje.

![](./media/image7-3.png)

Rysunek 7-3. Wybierz pojedyncze konta użytkowników mają tożsamości we wstępnie skonfigurowanym.

Obsługa tożsamości jest skonfigurowany w uruchamiania, zarówno w ConfigureServices i skonfiguruj:

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

Jest ważne, czy UseIdentity są wyświetlane przed UseMvc w metodzie Konfiguruj. Podczas konfigurowania tożsamości w ConfigureServices, zauważysz AddDefaultTokenProviders po wywołaniu. To nie ma nic wspólnego z tokenów, które mogą służyć do zabezpieczenia komunikacji w sieci web, ale zamiast tego odwołuje się do dostawców tworzące monity, które mogą być wysyłane do użytkowników za pośrednictwem wiadomości SMS lub wiadomości e-mail, aby je, aby potwierdzić swoją tożsamość.

Możesz dowiedzieć się więcej [Konfigurowanie uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa) i [Włączanie dostawcy logowania zewnętrznego](/aspnet/core/security/authentication/social/) oficjalnych dokumentach platformy ASP.NET Core.

### <a name="authorization"></a>Autoryzacja

Najprostsza forma autoryzacji polega na ograniczenie dostępu dla użytkowników anonimowych. Można to osiągnąć, po prostu stosując \[Autoryzuj\] atrybutu do niektórych kontrolerów i akcji. Role są używane, ten atrybut może dodatkowo rozszerzona do ograniczania dostępu do użytkowników, którzy należą do określonych ról, jak pokazano:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

W takim przypadku użytkownicy należący do ról HRManager lub Finance (lub obie) będzie mieć dostęp do SalaryController. Aby wymagać, że użytkownik należy do wielu ról (nie tylko jeden z kilku), można zastosować atrybutu wiele razy, określając wymaganej roli każdorazowo.

Określanie określone zestawy ról, zgodnie z ciągów w wielu różnych kontrolerów i akcji może doprowadzić do powtarzania niepożądane. Możesz skonfigurować zasady autoryzacji, które hermetyzują reguł autoryzacji, a następnie określ zasady, a nie poszczególnych ról podczas stosowania \[Autoryzuj\] atrybutu:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

W ten sposób, korzystając z zasad, można oddzielić rodzaje działań jest ograniczony z określonych ról lub reguły, które go dotyczą. Później, jeśli tworzysz nową rolę, która musi mieć dostęp do niektórych zasobów, można po prostu aktualizować zasady, a nie aktualizacji co listy ról na każdym \[Autoryzuj\] atrybutu.

#### <a name="claims"></a>oświadczenia

Oświadczenia są pary nazwa / wartość, które reprezentują właściwości uwierzytelnionego użytkownika. Na przykład może przechowywać numer pracownika użytkowników jako oświadczenia. Następnie można oświadczeń jako część zasad autoryzacji. Można utworzyć zasady o nazwie "EmployeeOnly" wymaga istnienia oświadczenie o nazwie "EmployeeNumber", jak pokazano w poniższym przykładzie:

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

Ta zasada może być użyta z \[Autoryzuj\] atrybutu, aby chronić kontroler i/lub akcji, jak opisano powyżej.

#### <a name="securing-web-apis"></a>Zabezpieczanie interfejsów API sieci web

Większość interfejsów API sieci web należy zaimplementować uwierzytelnianie oparte na token systemu. Uwierzytelnianie przy użyciu tokenów jest przeznaczona do skalowalne i bezstanowych. W systemie uwierzytelniania opartego na tokenach klienta muszą najpierw zostać uwierzytelnione za pomocą dostawcy uwierzytelniania. Jeśli to się powiedzie, klient wystawił token, który jest po prostu kryptograficznie istotnych ciąg znaków. Gdy klient musi wysłać żądanie do interfejsu API, dodaje ten token jako nagłówka w żądaniu. Serwer następnie weryfikuje token w nagłówku żądania znaleziono przed wykonaniem żądania. Rysunek 7-4 przedstawiono ten proces.

![TokenAuth](./media/image7-4.png)

**Rysunek 7-4.** Uwierzytelnianie oparte na tokenach dla interfejsów API sieci Web.

Można utworzyć usługi uwierzytelniania, integracja z usługą Azure AD i OAuth lub implementacji usługi przy użyciu narzędzia typu open source, takich jak [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Custom Security

Ostrożnie szczególnie "Uaktualnianie własnych" implementację kryptografii, członkostwa użytkownika lub generowania tokenów systemu. Istnieje wiele komercyjnych i open-source alternatywy dostępne, które prawie na pewno lepsze zabezpieczenia niż implementację niestandardową.

> ### <a name="references--security"></a>Odwołania — zabezpieczenia
>
> - **Omówienie zabezpieczeń usługi Docs**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Wymuszanie protokołu SSL w aplikacji ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Wprowadzenie do tożsamości**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Wprowadzenie do autoryzacji**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Uwierzytelnianie i autoryzacja dla usługi API Apps w usłudze Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Tożsamość serwera**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikacja z klientem

Oprócz obsługi stron i odpowiadanie na żądania dotyczące danych za pośrednictwem interfejsów API sieci web, aplikacje platformy ASP.NET Core mogą komunikować się bezpośrednio z połączonych klientów. Ta komunikacja wychodząca można użyć wielu różnych technologii transportu jest najbardziej typowych funkcji WebSockets. SignalR platformy ASP.NET Core to bibliotekę, która ułatwia dodawanie funkcji komunikacji serwera do klienta w czasie rzeczywistym do aplikacji. SignalR obsługuje szereg technologii transportu, w tym funkcji WebSockets i streszcza away wiele szczegółów implementacji od dewelopera.

SignalR platformy ASP.NET Core jest udostępniana z platformą ASP.NET Core od wersji 2.1.

Komunikacja z klientem w czasie rzeczywistym, czy przy użyciu funkcji WebSockets bezpośrednio lub innych technik przydają się w różnych zastosowaniach. Oto niektóre przykłady:

- Aplikacje na żywo pokoju rozmów

- Monitorowanie aplikacji

- Aktualizacje postępu zadania

- Powiadomienia

- Formularze interaktywne aplikacje

Podczas tworzenia komunikacji z klientem w swoich aplikacjach, istnieją zazwyczaj dwa składniki:

- Menedżer połączeń po stronie serwera (Centrum SignalR, WebSocketManager WebSocketHandler)

- Biblioteka klienta

Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się przy użyciu SignalR/Websocket. Następujący program prostą funkcją cała zawartość wysłana do aplikacji rozmów w konsoli jako część WebSocketManager przykładowej aplikacji:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
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

Należy rozważyć sposobów w których Twoje aplikacje komunikują się bezpośrednio z aplikacji klienckich i należy wziąć pod uwagę, czy komunikację w czasie rzeczywistym mogłyby poprawić użytkownika aplikacji środowiska.

> ### <a name="references--client-communication"></a>Odwołania — komunikacja z klientem
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/aspnet/SignalR>
> - **WebSocket Manager**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Projektowanie oparte na domenie — powinien zastosowania?

Projektowania opartego na domenach (DDD) jest podejście agile do tworzenia oprogramowania, która kładzie nacisk koncentrujących się na _domeny biznesowej_. Umieszcza mocno nacisk na komunikację i interakcję z expert(s) domeny biznesowej, który może odnosić się do deweloperów działania systemu rzeczywistych. Na przykład jeśli tworzysz system, który obsługuje kursów akcji usługi eksperta domeny może być brokera podstawowe doświadczenie. DDD zaprojektowano w celu rozwiązania problemów w firmie dużymi, złożonymi i często nie jest odpowiednie w przypadku aplikacji mniejszy, prostszy, ponieważ inwestycji w zrozumienie i modelowanie domeny nie są one warte.

Podczas tworzenia oprogramowania, korzystając z podejścia DDD, Twój zespół (w tym Nietechniczne uczestnikom projektu i współautorzy) należy opracować _wszechobecne języka_ miejsca problem. Oznacza to należy używać terminologii tego samego pojęcia rzeczywistych są modelowane, odpowiednik oprogramowania i wszelkimi strukturami, które mogą istnieć do utrwalenia pojęcie (na przykład tabele bazy danych). W efekcie pojęcia opisane w tym języku wszechobecne powinny być podstawą dla sieci _modelu domeny_.

Model domeny składa się z obiektów, które współdziałają ze sobą do reprezentowania zachowanie systemu. Te obiekty może można podzielić na następujące kategorie:

- [Jednostki](https://deviq.com/entity/), zawierające obiekty z wątkiem tożsamości. Jednostki są zazwyczaj przechowywane w trwałości za pomocą klucza za pomocą którego mogą później zostać pobrane.

- [Agregacje](https://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny zostać utrwalone jako jednostka.

- [Wartość obiekty](https://deviq.com/value-object/), które reprezentują pojęcia, które można porównać na podstawie sumy wartości ich właściwości. Na przykład DateRange składający się z datę początkową i końcową.

- [Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują czynności wykonywane w ramach systemu, które mają znaczenie w odniesieniu do innych części systemu.

Należy pamiętać, że model domeny DDD powinna hermetyzować złożonych zachowania w ramach modelu. Jednostki, w szczególności, nie tylko należy kolekcji właściwości. Jeśli model domeny nie ma zachowanie, jedynie reprezentuje stan systemu jest określany jako [anemic modelu](https://deviq.com/anemic-model/), czyli niepożądanych w DDD.

Oprócz tych typów modelu DDD zwykle stosuje różnych wzorców:

- [Repozytorium](https://deviq.com/repository-pattern/), dla abstrakcyjność szczegółów stanu trwałego.

- [Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern), do enkapsulacji tworzenia obiektu złożonego.

- Zdarzenia domeny dla oddzielenie zachowanie zależnych wraz z zachowaniem.

- [Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)dla hermetyzowany zachowanie złożone i/lub szczegółów implementacji infrastruktury.

- [Polecenie](https://en.wikipedia.org/wiki/Command_pattern)dla oddzielenie wydawanie polecenia i wykonywania w niej samo polecenie.

- [Specyfikacja](https://deviq.com/specification-pattern/), do enkapsulacji szczegółów zapytania.

DDD zaleca również używanie czystej architektury omówionych wcześniej, pozwalając na tym luźne powiązanie, hermetyzacji i kod, który można łatwo zweryfikować za pomocą testów jednostkowych.

### <a name="when-should-you-apply-ddd"></a>Kiedy należy zastosować DDD

DDD dobrze nadaje się do dużej aplikacji przy użyciu złożoności firma (nie tylko weryfikacji technicznej). Aplikacja powinna wymagają znajomości ekspertów z konkretnych dziedzin. Powinna istnieć znaczące zachowanie w modelu domeny, reprezentujący reguł biznesowych i interakcje ponad po prostu przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych.

### <a name="when-shouldnt-you-apply-ddd"></a>Kiedy nie należy zastosować DDD

DDD wymaga inwestycji w modelowania, architektury i komunikacji, który nie może być uzasadnione dla mniejszych aplikacji lub aplikacji, które zasadniczo są po prostu CRUD (Tworzenie/odczyt/aktualizowanie/usuwanie). Jeśli użytkownik chce podejście do aplikacji następujące DDD, ale okazać, że domeny ma anemic modelu, z zachowaniem programu nie może być konieczne zmusza danej metody. Aplikacja nie może być konieczne DDD albo możesz potrzebować pomocy refaktoryzacji hermetyzowania logiki biznesowej w modelu domeny, a nie w swojej bazie danych lub interfejsu użytkownika aplikacji.

Podejście hybrydowe byłoby tylko DDD obszarów transakcyjnej lub bardziej złożonych aplikacji, ale nie CRUD prostsze lub tylko do odczytu części aplikacji. Na przykład musi mieć ograniczenia agregacji, jeśli zadajesz zapytanie do danych do wyświetlania raportu lub wizualizacji danych dla pulpitu nawigacyjnego. Jest idealnie dopuszczalne mają oddzielny, prostsze modelu odczytu dla tych wymagań.

> ### <a name="references--domain-driven-design"></a>Odwołania — projektowania opartego na domenie
>
> - **DDD w prostych słowach (StackOverflow odpowiedzi)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>wdrażania

Zaangażowanych kilka czynności w procesie wdrażania aplikacji platformy ASP.NET Core, niezależnie od tego, w którym będzie hostowana. Pierwszym krokiem jest opublikowanie aplikacji, co można zrobić za pomocą polecenia dotnet publikowanie interfejsu wiersza polecenia. Spowoduje to skompilować aplikację i umieścić wszystkie pliki potrzebne do uruchomienia aplikacji w wyznaczonym folderze. Podczas wdrażania w programie Visual Studio, w tym kroku jest realizowane automatycznie dla Ciebie. Folder publikowania zawiera pliki .exe i .dll dla aplikacji i jego zależności. Samodzielna aplikacja będzie również udostępniać wersję środowiska uruchomieniowego .NET. Aplikacje platformy ASP.NET Core będzie również udostępniać pliki konfiguracyjne, elementy zawartości statycznej klienta i widoków MVC.

Aplikacje platformy ASP.NET Core to aplikacji konsoli, które musi zostać uruchomiona, gdy serwer uruchamia się i ponownego uruchomienia, jeśli wystąpiła awaria aplikacji (lub serwera). Menedżera procesów można zautomatyzować ten proces. Najbardziej typowe menedżerów procesu dla platformy ASP.NET Core są serwera Nginx i Apache w systemie Linux oraz usług IIS lub usługa Windows na Windows.

Oprócz menedżera procesów aplikacje platformy ASP.NET Core hostowanych na serwerze sieci web Kestrel należy użyć zwrotnego serwera proxy. Zwrotnego serwera proxy odbiera żądania HTTP z Internetu i przekazuje je do Kestrel po niektórych wstępnego obsługi. Serwery zwrotny serwer proxy zapewnia warstwę zabezpieczeń dla aplikacji i są wymagane w przypadku wdrożeń usługi edge (ujawniony na ruch z Internetu). Kestrel jest względnie nowe i jeszcze nie oferuje zabezpieczenia przed atakami niektórych. Kestrel nie obsługuje również hostowania wielu aplikacji, w tym samym porcie, więc technik, takich jak nagłówki hosta nie można używać z nią hostowania wielu aplikacji na ten sam port i adres IP.

![Usługi kestrel do Internetu](./media/image7-5.png)

Rysunek 7-5 ASP.NET hostowane w Kestrel za serwerem proxy odwrotnej

Inny scenariusz, w którym zwrotny serwer proxy mogą być pomocne jest zapewnienie wielu aplikacji przy użyciu protokołu SSL i HTTPS. W takim przypadku tylko zwrotny serwer proxy będzie konieczne skonfigurowano protokół SSL. Komunikacja między zwrotnego serwera proxy i Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano w rysunek 7-6.

![](./media/image7-6.png)

Rysunek 7 – 6 ASP.NET hostowanych za zabezpieczone przez protokół HTTPS zwrotnego serwera proxy

Jest coraz bardziej popularne podejście do hostowania aplikacji platformy ASP.NET Core w kontenerze platformy Docker, które następnie mogą być hostowane lokalnie lub wdrożona na platformie Azure do hostowania opartej na chmurze. Kontener platformy Docker może zawierać kod aplikacji uruchomionych na Kestrel i będzie można wdrożyć za serwerem proxy odwrotnej, jak pokazano powyżej.

Jeśli hostujesz aplikację na platformie Azure umożliwia Microsoft Azure Application Gateway jako dedykowane urządzenie wirtualne zapewniają kilka usług. Oprócz działający jako zwrotny serwer proxy dla poszczególnych aplikacji, usługa Application Gateway może oferują również następujące funkcje:

- Równoważenie obciążenia HTTP

- Odciążanie protokołu SSL (SSL tylko z Internetu)

- Kompleksowej usługi SSL

- Routing obejmujący wiele lokacji (skonsolidować maksymalnie 20 witryn na pojedynczą usługą Application Gateway)

- Zapora aplikacji sieci Web

- Obsługa protokołu Websocket

- Zaawansowana Diagnostyka

_Dowiedz się więcej o opcjach wdrażania platformy Azure w programie [rozdział 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odwołania — wdrożenia
>
> - **Omówienie wdrożenia i hosting**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kiedy należy używać Kestrel przy użyciu zwrotnego serwera proxy**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostowanie aplikacji platformy ASP.NET Core na platformie Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Wprowadzenie do usługi Azure Application Gateway**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Poprzednie](common-client-side-web-technologies.md)
>[dalej](work-with-data-in-asp-net-core-apps.md)
