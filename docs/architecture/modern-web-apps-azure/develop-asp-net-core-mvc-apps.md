---
title: Tworzenie ASP.NET podstawowych aplikacji MVC
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | tworzenie ASP.NET Core MVC Apps
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: a18b4dfc60c7d3971136f73f333b7225735710b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503945"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Tworzenie ASP.NET podstawowych aplikacji MVC

> "To nie jest ważne, aby to dobrze za pierwszym razem. To bardzo ważne, aby to naprawić po raz ostatni."  
> _- Andrew Hunt i David Thomas_

ASP.NET Core to wieloplatformowa struktura typu open source do tworzenia nowoczesnych aplikacji internetowych zoptymalizowanych pod kątem chmury. ASP.NET Aplikacje Core są lekkie i modułowe, z wbudowaną obsługą wstrzykiwania zależności, co pozwala na większą możliwość testowania i łatwość konserwacji. W połączeniu z MVC, który obsługuje tworzenie nowoczesnych interfejsów API internetowych oprócz aplikacji opartych na widoku, ASP.NET Core to zaawansowana struktura, za pomocą której można tworzyć aplikacje internetowe dla przedsiębiorstw.

## <a name="mvc-and-razor-pages"></a>Strony MVC i Razor

ASP.NET Core MVC oferuje wiele funkcji, które są przydatne do tworzenia internetowych interfejsów API i aplikacji. Termin MVC oznacza "Model-View-Controller", wzorzec interfejsu użytkownika, który dzieli obowiązki odpowiadania na żądania użytkowników na kilka części. Oprócz podążania za tym wzorcem można również zaimplementować funkcje w aplikacjach ASP.NET Core jako Strony Razor. Strony razor są wbudowane w ASP.NET Core MVC i używają tych samych funkcji do routingu, wiązania modelu itp. Jednak zamiast oddzielnych folderów i plików dla kontrolerów, widoków itp.

Podczas tworzenia nowej ASP.NET Core App, należy mieć na uwadze plan dla rodzaju aplikacji, którą chcesz utworzyć. W programie Visual Studio do wyboru będzie kilka szablonów. Trzy najpopularniejsze szablony projektów to interfejs Web API, aplikacja sieci Web i aplikacja sieci Web (Model-View-Controller). Chociaż tę decyzję można podjąć tylko podczas tworzenia projektu, nie jest to nieodwołalna decyzja. Projekt interfejsu API sieci Web używa standardowych kontrolerów Model-View-Controller — domyślnie brakuje tylko widoków. Podobnie domyślny szablon aplikacji sieci Web używa stron Razor, a więc również brakuje folderu Widoki. Folder Widoki można później dodać do tych projektów, aby obsługiwać zachowanie oparte na widoku. Web API i Model-View-Controller projekty nie zawierają folder strony domyślnie, ale można dodać jeden później do obsługi razor strony oparte zachowanie. Te trzy szablony można pomyśleć jako obsługę trzech różnych rodzajów domyślnej interakcji użytkownika: danych (internetowy interfejs API), opartych na stronach i opartych na widokach. Można jednak mieszać i dopasowywać dowolne lub wszystkie z nich w ramach jednego projektu, jeśli chcesz.

### <a name="why-razor-pages"></a>Dlaczego Strony Razor?

Strona Razor jest domyślnym podejściem dla nowych aplikacji sieci web w programie Visual Studio. Razor Pages oferuje prostszy sposób tworzenia funkcji aplikacji opartych na stronach, takich jak formularze bez SPA. Przy użyciu kontrolerów i widoków, to było wspólne dla aplikacji mają bardzo duże kontrolery, które pracowały z wielu różnych zależności i modeli widoku i zwrócił wiele różnych widoków. Spowodowało to większą złożoność i często skutkowało tym, że kontrolerzy nie przestrzegali zasady jednolitej odpowiedzialności ani zasad otwartych/zamkniętych. Razor Pages rozwiązuje ten problem, hermetyzując logikę po stronie serwera dla danej logicznej "strony" w aplikacji internetowej z znacznikami Razor. Strona Razor, która nie ma logiki po stronie serwera, może po prostu składać się z pliku Razor (na przykład "Index.cshtml"). Jednak większość nietrywialnych stron Razor strony będą miały skojarzoną klasę modelu strony, która zgodnie z konwencją nosi nazwę taką samą jak plik Razor z rozszerzeniem ".cs" (na przykład "Index.cshtml.cs").

Model strony razor page łączy obowiązki kontrolera MVC i viewmodel. Zamiast obsługi żądań za pomocą metod akcji kontrolera, programy obsługi modelu strony, takie jak "OnGet()", są domyślnie wykonywane renderowania ich skojarzonej strony. Strona Razor upraszcza proces tworzenia poszczególnych stron w aplikacji ASP.NET Core, zapewniając jednocześnie wszystkie funkcje architektoniczne ASP.NET Core MVC. Są one dobrym domyślnym wyborem dla nowych funkcji opartych na stronie.

### <a name="when-to-use-mvc"></a>Kiedy używać MVC

Jeśli tworzysz internetowe interfejsy API, wzorzec MVC ma większy sens niż próba użycia stron razor. Jeśli projekt będzie tylko uwidaczniać web API punktów końcowych, najlepiej rozpocząć od szablonu projektu interfejsu API sieci Web. W przeciwnym razie można łatwo dodać kontrolery i skojarzone punkty końcowe interfejsu API do dowolnej aplikacji ASP.NET Core. Użyj opartego na widoku metody MVC, jeśli migrujesz istniejącą aplikację z ASP.NET MVC 5 lub wcześniejszych do ASP.NET Core MVC i chcesz to zrobić przy jak najmniejszym wysiłku. Po dojściu do pierwszej migracji możesz ocenić, czy warto przyjąć strony Razor dla nowych funkcji, czy nawet jako migrację hurtową.

Niezależnie od tego, czy zdecydujesz się utworzyć aplikację sieci web przy użyciu widoków Razor Pages lub MVC, aplikacja będzie miała podobną wydajność i będzie obsługiwać iniekcja zależności, filtry, powiązanie modelu, sprawdzanie poprawności i tak dalej.

## <a name="mapping-requests-to-responses"></a>Mapowanie żądań do odpowiedzi

W jego sercu ASP.NET aplikacje Core mapują przychodzące żądania odpowiedzi wychodzących. Na niskim poziomie odbywa się to za pomocą pośredniczania i proste ASP.NET podstawowych aplikacji i mikrousług może składać się wyłącznie z niestandardowego pośredniczania. Korzystając z ASP.NET Core MVC, można pracować na nieco wyższym poziomie, myśląc w kategoriach _tras,_ _kontrolerów_i _akcji._ Każde żądanie przychodzące jest porównywane z tabelą routingu aplikacji, a jeśli zostanie znaleziona pasująca trasa, skojarzona metoda akcji (należąca do kontrolera) jest wywoływana w celu obsługi żądania. Jeśli nie zostanie znaleziona zgodna trasa, wywoływany jest program obsługi błędów (w tym przypadku zwracany wynik NotFound).

ASP.NET Aplikacje Core MVC mogą używać konwencjonalnych tras, tras atrybutów lub obu tych dróg. Konwencjonalne trasy są zdefiniowane w kodzie, określając _konwencje_ routingu przy użyciu składni, jak w poniższym przykładzie:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

W tym przykładzie do tabeli routingu dodano trasę o nazwie "default". Definiuje szablon trasy z symbolami zastępczymi dla _kontrolera,_ _akcji_i _identyfikatora_. Kontroler i symbole zastępcze akcji mają domyślnie określone ("Home" i "Index", odpowiednio), a symbol zastępczy identyfikatora jest opcjonalny (ze względu na "?" stosowane do niego). Konwencja zdefiniowana w tym miejscu stanowi, że pierwsza część żądania powinna odpowiadać nazwie kontrolera, drugiej części akcji, a następnie w razie potrzeby trzecia część będzie reprezentować parametr id. Konwencjonalne trasy są zazwyczaj zdefiniowane w jednym miejscu dla aplikacji, na przykład w Configure metody w Startup klasy.

Trasy atrybutów są stosowane do kontrolerów i akcji bezpośrednio, a nie określone globalnie. Ma to tę zaletę, że są znacznie bardziej wykrywalne, gdy patrzysz na określoną metodę, ale oznacza, że informacje o routingu nie są przechowywane w jednym miejscu w aplikacji. Za pomocą tras atrybutów można łatwo określić wiele tras dla danej akcji, a także połączyć trasy między kontrolerami i akcjami. Przykład:

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

Trasy można określić na [HttpGet] i podobne atrybuty, unikając konieczności dodawania oddzielnych [Route] atrybutów. Trasy atrybutów można również użyć tokenów, aby zmniejszyć potrzebę powtarzania nazwy kontrolera lub akcji, jak pokazano poniżej:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Strona Razor nie używa routingu atrybutów. Dodatkowe informacje o szablonie trasy dla strony razor można określić w ramach jej dyrektywy: `@page`

```csharp
@page "{id:int}"
```

W poprzednim przykładzie strona, o którą mowa, będzie `id` pasować do trasy z parametrem liczby całkowitej. Na przykład strona *Products.cshtml* znajdująca `/Pages` się w katalogu głównym będzie miała tę trasę:

```csharp
"/Products/123"
```

Po dopasowaniu danego żądania do trasy, ale przed wywołaniem metody akcji, ASP.NET Core MVC wykona [powiązanie modelu](/aspnet/core/mvc/models/model-binding) i [sprawdzania poprawności modelu](/aspnet/core/mvc/models/validation) na żądanie. Powiązanie modelu jest odpowiedzialny za konwersję przychodzących danych HTTP do typów .NET określonych jako parametry metody akcji, która ma być wywoływana. Na przykład jeśli metoda akcji oczekuje int id parametru, powiązanie modelu podejmie próbę dostarczenia tego parametru z wartości podanej jako część żądania. W tym celu powiązanie modelu wyszcone jest wysznanie wartości w zaksięgowanym formularzu, wartości w samej marszrucie i wartości ciągów kwerend. Przy założeniu, że zostanie znaleziony wartość identyfikatora, zostanie ona przekonwertowana na całkowitą, zanim zostanie przekazana do metody akcji.

Po powiązaniu modelu, ale przed wywołaniem metody akcji, sprawdzanie poprawności modelu występuje. Sprawdzanie poprawności modelu używa atrybutów opcjonalnych na typ modelu i może pomóc upewnić się, że obiekt modelu jest zgodny z określonymi wymaganiami dotyczącymi danych. Niektóre wartości mogą być określone w razie potrzeby lub ograniczone do określonej długości lub zakresu liczbowego itp. Jeśli atrybuty sprawdzania poprawności są określone, ale model nie jest zgodny z ich wymaganiami, właściwość ModelState.IsValid będzie false, a zestaw reguł sprawdzania poprawności nie będzie dostępny do wysłania do klienta, który wykonuje żądanie.

Jeśli używasz sprawdzania poprawności modelu, należy zawsze sprawdzać, czy model jest prawidłowy przed wykonaniem jakichkolwiek poleceń zmieniających stan, aby upewnić się, że aplikacja nie jest uszkodzona przez nieprawidłowe dane. Można użyć [filtru,](/aspnet/core/mvc/controllers/filters) aby uniknąć konieczności dodawania kodu do tego w każdej akcji. ASP.NET Filtry Core MVC oferują sposób przechwytywania grup żądań, dzięki czemu wspólne zasady i problemy przekrojowe mogą być stosowane w sposób ukierunkowany. Filtry mogą być stosowane do poszczególnych akcji, całych kontrolerów lub globalnie dla aplikacji.

W przypadku interfejsów API sieci Web ASP.NET Core MVC obsługuje [_negocjowanie zawartości,_](/aspnet/core/mvc/models/formatting)umożliwiając żądaniom określenie sposobu formatowania odpowiedzi. Na podstawie nagłówków podanych w żądaniu akcje zwracające dane sformatują odpowiedź w formacie XML, JSON lub innym obsługiwanym formacie. Ta funkcja umożliwia ten sam interfejs API do użycia przez wielu klientów z różnych wymagań formatu danych.

Projekty interfejsu API sieci `[ApiController]` Web należy rozważyć przy użyciu atrybutu, który może być stosowany do poszczególnych kontrolerów, do klasy kontrolera podstawowego lub do całego zestawu. Ten atrybut dodaje sprawdzanie poprawności modelu automatycznego i każda akcja z nieprawidłowym modelem zwróci BadRequest ze szczegółami błędów sprawdzania poprawności. Atrybut wymaga również wszystkie akcje mają trasę atrybutu, a nie przy użyciu konwencjonalnej trasy i zwraca bardziej szczegółowe informacje ProblemDetails w odpowiedzi na błędy.

> ### <a name="references--mapping-requests-to-responses"></a>Odwołania — mapowanie żądań do odpowiedzi
>
> - **Routing do akcji kontrolera**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Powiązanie modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Sprawdzanie poprawności modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Atrybut ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Praca z zależnościami

ASP.NET Core ma wbudowaną obsługę i wewnętrznie korzysta z techniki znanej jako [iniekcja zależności.](/aspnet/core/fundamentals/dependency-injection) Iniekcja zależności jest techniką, która umożliwia luźne sprzężenie między różnymi częściami aplikacji. Luźniejsze sprzęgło jest pożądane, ponieważ ułatwia izolowanie części aplikacji, co pozwala na testowanie lub wymianę. To również sprawia, że mniej prawdopodobne, że zmiana w jednej części aplikacji będzie mieć nieoczekiwany wpływ gdzie indziej w aplikacji. Wstrzykiwanie zależności opiera się na zasadzie inwersji zależności i często jest kluczem do osiągnięcia zasady otwartej/zamkniętej. Oceniając, jak aplikacja działa z jego zależności, uważaj na [statyczny](https://deviq.com/static-cling/) zapach kodu przylegania i pamiętaj, że aforyzm "[nowy to klej."](https://ardalis.com/new-is-glue)

Statyczne przyleganie występuje, gdy klasy wywołać metody statyczne lub dostęp do właściwości statycznych, które mają skutki uboczne lub zależności na infrastrukturze. Na przykład jeśli masz metodę, która wywołuje metodę statyczną, która z kolei zapisuje do bazy danych, metoda jest ściśle powiązane z bazą danych. Wszystko, co przerywa to wywołanie bazy danych spowoduje przerwanie metody. Testowanie takich metod jest notorycznie trudne, ponieważ takie testy wymagają komercyjnych szyderczych bibliotek do makiety wywołań statycznych lub mogą być testowane tylko z testową bazą danych w miejscu. Wywołania statyczne, które nie mają żadnej zależności od infrastruktury, zwłaszcza tych, które są całkowicie bezstanowe, są w porządku do wywołania i nie mają wpływu na sprzężenie lub testowalność (poza kodem sprzężenia do samego wywołania statycznego).

Wielu deweloperów zrozumieć ryzyko statyczne przyleganie i stan globalny, ale nadal ściśle połączą swój kod z określonymi implementacjami za pomocą bezpośredniego wystąpienia. "Nowy jest klej" ma być przypomnieniem tego sprzężenia, a nie ogólnym `new` potępieniem użycia słowa kluczowego. Podobnie jak w przypadku wywołań metod statycznych, nowe wystąpienia typów, które nie mają zależności zewnętrznych, zazwyczaj nie ściśle powiązują kod ze szczegółami implementacji lub utrudniają testowanie. Ale za każdym razem, gdy klasa jest tworzone, poświęć tylko krótką chwilę, aby zastanowić się, czy ma sens do hard-code tego konkretnego wystąpienia w tej konkretnej lokalizacji lub jeśli byłoby lepszym projektem do żądania tego wystąpienia jako zależności.

### <a name="declare-your-dependencies"></a>Deklaruj swoje zależności

ASP.NET Core jest zbudowany wokół o metody i klasy deklarują swoje zależności, żądając ich jako argumenty. ASP.NET aplikacje są zazwyczaj konfigurowane w Startup klasy, która sama jest skonfigurowana do obsługi iniekcji zależności w kilku punktach. Jeśli Startup klasy ma konstruktora, można żądać zależności za pośrednictwem konstruktora, tak:

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

Startup Klasa jest interesująca, ponieważ nie ma żadnych wymagań typu jawnego dla niego. Nie dziedziczy ze specjalnej klasy podstawowej uruchamiania, ani nie implementuje żadnego określonego interfejsu. Można nadać mu konstruktora, czy nie, i można określić dowolną liczbę parametrów na konstruktorze, jak chcesz. Po uruchomieniu hosta sieci web skonfigurowanego dla aplikacji wywoła on klasę Startup, której użytkownik ma użyć, i użyje iniekcji zależności do wypełnienia wszelkich zależności wymaganych przez startup. Oczywiście jeśli zażądasz parametrów, które nie są skonfigurowane w kontenerze usług używanych przez ASP.NET Core, otrzymasz wyjątek, ale tak długo, jak trzymać się zależności kontener wie o, można zażądać wszystko, co chcesz.

Iniekcji zależności jest wbudowany w ASP.NET podstawowych aplikacji od samego początku, podczas tworzenia wystąpienia uruchamiania. Nie kończy się tam dla Startup klasy. Zależności można również żądać w metodzie Configure:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices jest wyjątkiem od tego zachowania; musi przyjmować tylko jeden parametr typu IServiceCollection. Tak naprawdę nie trzeba obsługiwać iniekcji zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów do kontenera usług, a z drugiej strony ma dostęp do wszystkich aktualnie skonfigurowanych usług za pośrednictwem iServiceCollection parametru. W związku z tym można pracować z zależnościami zdefiniowanymi w kolekcji usług ASP.NET Core w każdej części Klasy Startup, żądając żądanej usługi jako parametru lub pracy z iServiceCollection w ConfigureServices.

> [!NOTE]
> Jeśli musisz upewnić się, że niektóre usługi są dostępne dla klasy Start, możesz skonfigurować je przy użyciu iWebHostBuilder i jego Metody ConfigureServices wewnątrz wywołania CreateDefaultBuilder.

Startup Klasa jest modelem, jak należy struktury innych części aplikacji ASP.NET Core, od kontrolerów do oprogramowania pośredniczego do filtrów do własnych usług. W każdym przypadku należy postępować zgodnie z [jawne zależności zasady](https://deviq.com/explicit-dependencies-principle/), żądając zależności, a nie bezpośrednio ich tworzenia i wykorzystując iniekcji zależności w całej aplikacji. Należy zachować ostrożność, gdzie i jak bezpośrednio wystąpienia implementacji, zwłaszcza usług i obiektów, które współpracują z infrastrukturą lub mają skutki uboczne. Preferuj pracę z abstrakcjami zdefiniowanymi w rdzeniu aplikacji i przekazywaną jako argumenty do hardcoding odwołań do określonych typów implementacji.

## <a name="structuring-the-application"></a>Strukturyzacja aplikacji

Aplikacje monolityczne zazwyczaj mają jeden punkt wejścia. W przypadku ASP.NET core aplikacji sieci web, punkt wejścia będzie ASP.NET core projektu sieci web. Nie oznacza to jednak, że rozwiązanie powinno składać się tylko z jednego projektu. Warto podzielić aplikację na różne warstwy, aby śledzić separację problemów. Po podziale na warstwy, warto wyjść poza foldery do oddzielnych projektów, co może pomóc w osiągnięciu lepszej hermetyzacji. Najlepszym rozwiązaniem do osiągnięcia tych celów za pomocą aplikacji ASP.NET Core jest odmiana czystej architektury omówione w rozdziale 5. Zgodnie z tym podejściem rozwiązanie aplikacji będzie składać się z oddzielnych bibliotek dla interfejsu, infrastruktury i ApplicationCore.

Oprócz tych projektów uwzględniono również oddzielne projekty testowe (testy zostały omówione w rozdziale 9).

Model obiektów aplikacji i interfejsy powinny być umieszczone w projekcie ApplicationCore. Ten projekt będzie miał jak najmniej zależności, a inne projekty w rozwiązaniu będą się do niego odwoływać. Jednostki biznesowe, które muszą być utrwaliłe są zdefiniowane w projekcie ApplicationCore, podobnie jak usługi, które nie są bezpośrednio zależne od infrastruktury.

Szczegóły implementacji, takie jak sposób trwałości jest wykonywana lub jak powiadomienia mogą być wysyłane do użytkownika, są przechowywane w projekcie infrastruktury. Ten projekt będzie odwoływać się do pakietów specyficznych dla implementacji, takich jak Entity Framework Core, ale nie powinien ujawniać szczegółów dotyczących tych implementacji poza projektem. Usługi infrastruktury i repozytoria należy zaimplementować interfejsy, które są zdefiniowane w projekcie ApplicationCore, a jego implementacje trwałości są odpowiedzialne za pobieranie i przechowywanie jednostek zdefiniowanych w ApplicationCore.

Projekt ASP.NET Core UI jest odpowiedzialny za wszelkie problemy na poziomie interfejsu i usług, ale nie powinien zawierać logiki biznesowej ani szczegółów infrastruktury. W rzeczywistości najlepiej, jeśli nie powinien nawet mieć zależność od projektu infrastruktury, co pomoże zapewnić, że nie zależność między tymi dwoma projektami zostanie wprowadzona przypadkowo. Można to osiągnąć przy użyciu kontenera DI innych firm, takiego jak Autofac, który umożliwia definiowanie reguł DI w klasach module w każdym projekcie.

Innym podejściem do oddzielenia aplikacji od szczegółów implementacji jest mieć mikrousług wywołań aplikacji, być może wdrożone w poszczególnych kontenerach platformy Docker. Zapewnia to jeszcze większe oddzielenie obaw i oddzielenie od produkcji niż wykorzystanie DI między dwoma projektami, ale ma dodatkową złożoność.

### <a name="feature-organization"></a>Organizacja funkcji

Domyślnie ASP.NET aplikacje podstawowe organizują swoją strukturę folderów w celu uwzględnienia kontrolerów i widoków oraz często ViewModels. Kod po stronie klienta do obsługi tych struktur po stronie serwera jest zwykle przechowywany oddzielnie w folderze wwwroot. Jednak duże aplikacje mogą napotkać problemy z tą organizacją, ponieważ praca nad daną funkcją często wymaga przeskakiwania między tymi folderami. Staje się to coraz trudniejsze wraz ze wzrostem liczby plików i podfolderów w każdym folderze, co powoduje duże przewijanie Eksploratora rozwiązań. Jednym z rozwiązań tego problemu jest organizowanie kodu aplikacji według _funkcji,_ a nie według typu pliku. Ten styl organizacyjny jest zwykle określany jako foldery funkcji lub [wycinki funkcji](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) (zobacz też: [Pionowe plasterki).](https://deviq.com/vertical-slices/)

ASP.NET Core MVC obsługuje obszary w tym celu. Za pomocą obszarów można tworzyć oddzielne zestawy folderów Kontrolery i Widoki (a także wszystkie skojarzone modele) w każdym folderze Obszar. Rysunek 7-1 przedstawia przykładową strukturę folderów przy użyciu obszarów.

![Organizacja obszaru próbkowania](./media/image7-1.png)

**Rysunek 7-1**. Organizacja obszaru próbkowania

Korzystając z funkcji Obszary, należy użyć atrybutów do ozdabiania kontrolerów nazwą obszaru, do którego należą:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Należy również dodać obsługę obszaru do tras:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Oprócz wbudowanej obsługi obszarów można również użyć własnej struktury folderów i konwencji w miejsce atrybutów i tras niestandardowych. Pozwoliłoby to mieć foldery funkcji, które nie zawierały oddzielnych folderów dla widoków, kontrolerów itp., zachowując hierarchię bardziej płaską i ułatwiając wyświetlanie wszystkich powiązanych plików w jednym miejscu dla każdej funkcji.

ASP.NET Core używa wbudowanych typów konwencji do kontrolowania jego zachowania. Można zmodyfikować lub zastąpić te konwencje. Na przykład można utworzyć konwencję, która automatycznie uzyska nazwę funkcji dla danego kontrolera na podstawie jego przestrzeni nazw (która zazwyczaj koreluje z folderem, w którym znajduje się kontroler):

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

Następnie należy określić tę konwencję jako opcję podczas dodawania obsługi MVC do aplikacji w ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC używa również konwencji do lokalizowania widoków. Można zastąpić go konwencją niestandardową, tak aby widoki znajdowały się w folderach funkcji (przy użyciu nazwy funkcji podanego przez Konwencję FeatureConvention powyżej). Możesz dowiedzieć się więcej o tym podejściu i pobrać próbkę roboczą z artykułu MSDN [Magazine, Plasterki funkcji dla ASP.NET Core MVC](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).

### <a name="cross-cutting-concerns"></a>Zagadnienia ogólne

Wraz ze wzrostem zastosowań coraz ważniejsze staje się uwzględnienie problemów przekrojowych w celu wyeliminowania powielania i zachowania spójności. Niektóre przykłady problemów przekrojowych w ASP.NET podstawowych aplikacji są uwierzytelniania, reguły sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługi błędów, chociaż istnieje wiele innych. ASP.NET podstawowe [filtry](/aspnet/core/mvc/controllers/filters) MVC umożliwiają uruchamianie kodu przed lub po pewnych krokach w potoku przetwarzania żądań. Na przykład filtr można uruchomić przed i po powiązaniu modelu, przed i po akcji lub przed i po wyniku akcji. Można również użyć filtru autoryzacji do kontrolowania dostępu do pozostałej części potoku. Rysunki 7-2 pokazuje, jak wykonanie żądania przepływa przez filtry, jeśli jest skonfigurowany.

![Żądanie jest przetwarzane za pomocą filtrów autoryzacji, filtrów zasobów, wiązania modelu, filtrów akcji, wykonania akcji i konwersji wyników akcji, filtrów wyjątków, filtrów wyników i wykonania wyników. W drodze, żądanie jest przetwarzane tylko przez filtry wyników i filtry zasobów, zanim stanie się odpowiedzią wysłaną do klienta.](./media/image7-2.png)

**Rysunek 7-2**. Żądanie wykonania za pomocą filtrów i potoku żądania.

Filtry są zwykle implementowane jako atrybuty, dzięki czemu można je zastosować do kontrolerów lub akcji (lub nawet globalnie). Po dodaniu w ten sposób filtry określone na poziomie akcji zastępują lub opierają się na filtrach określonych na poziomie kontrolera, które same zastępują filtry globalne. Na przykład \[Route\] atrybut może służyć do tworzenia tras między kontrolerami i akcji. Podobnie autoryzacji można skonfigurować na poziomie kontrolera, a następnie zastąpić przez poszczególne akcje, jak pokazano w poniższym przykładzie:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

Pierwsza metoda, Login, używa AllowAnonymous filtr (atrybut), aby zastąpić authorize filtr ustawiony na poziomie kontrolera. Akcja ForgotPassword (i wszelkie inne akcje w klasie, które nie mają AllowAnonymous atrybut) będzie wymagać uwierzytelnione go żądania.

Filtry mogą służyć do wyeliminowania powielania w postaci typowych zasad obsługi błędów dla interfejsów API. Na przykład typowe zasady interfejsu API jest zwrócenie NotFound odpowiedzi na żądania odwołujące się do kluczy, które nie istnieją i badrequest odpowiedzi, jeśli sprawdzanie poprawności modelu nie powiedzie się. W poniższym przykładzie przedstawiono te dwie zasady w działaniu:

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

Nie zezwalaj na zaśmiecanie metod akcji kodem warunkowym w ten sposób. Zamiast tego pociągnąć zasady do filtrów, które mogą być stosowane w razie potrzeby. W tym przykładzie sprawdzanie poprawności modelu, które powinno wystąpić w dowolnym momencie wysłania polecenia do interfejsu API, można zastąpić następującym atrybutem:

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

Można dodać `ValidateModelAttribute` do projektu jako zależność NuGet, dołączając [pakiet Ardalis.ValidateModel.](https://www.nuget.org/packages/Ardalis.ValidateModel) W przypadku interfejsów API można użyć atrybutu `ApiController` do `ValidateModel` wymuszenia tego zachowania bez konieczności stosowania oddzielnego filtru.

Podobnie filtr może służyć do sprawdzania, czy istnieje rekord i zwrócić 404 przed wykonaniem akcji, eliminując konieczność wykonywania tych kontroli w akcji. Po wyciągnięciu typowych konwencji i zorganizowaniu rozwiązania w celu oddzielenia kodu infrastruktury i logiki biznesowej od interfejsu użytkownika metody akcji MVC powinny być bardzo cienkie:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Możesz przeczytać więcej na temat wdrażania filtrów i pobrać próbkę roboczą z artykułu MSDN Magazine, [Real-World ASP.NET Core MVC Filters](https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters).

> ### <a name="references--structuring-applications"></a>Referencje – aplikacje strukturyzujące
>
> - **Obszary**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine - Plasterki funkcji dla ASP.NET Core MVC**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Msdn Magazine - Real World ASP.NET Core Filtry MVC**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Zabezpieczenia

Zabezpieczanie aplikacji sieci web jest dużym tematem, z wieloma zagadnieniami. Na najbardziej podstawowym poziomie zabezpieczeń polega na upewnieniu się, że wiesz, kto dane żądanie pochodzi z, a następnie zapewnienie, że żądanie ma dostęp tylko do zasobów powinien. Uwierzytelnianie to proces porównywania poświadczeń dostarczonych z żądaniem z danymi w zaufanym magazynie danych, aby sprawdzić, czy żądanie powinno być traktowane jako pochodzące ze znanej jednostki. Autoryzacja to proces ograniczania dostępu do niektórych zasobów na podstawie tożsamości użytkownika. Trzecią kwestią bezpieczeństwa jest ochrona żądań przed podsłuchiwaniem przez osoby trzecie, dla których należy przynajmniej [upewnić się, że ssl jest używany przez aplikację.](/aspnet/core/security/enforcing-ssl)

### <a name="authentication"></a>Authentication

ASP.NET Core Identity to system członkostwa, którego można używać do obsługi funkcji logowania dla aplikacji. Obsługuje lokalne konta użytkowników, a także wsparcie zewnętrznego dostawcy logowania od dostawców takich jak Microsoft Account, Twitter, Facebook, Google i inne. Oprócz ASP.NET Core Identity aplikacja może używać uwierzytelniania systemu Windows lub dostawcy tożsamości innej firmy, takiego jak [Identity Server](https://github.com/IdentityServer/IdentityServer4).

ASP.NET Tożsamość podstawowa jest uwzględniona w nowych szablonach projektów, jeśli wybrana jest opcja Indywidualne konta użytkowników. Ten szablon zawiera obsługę rejestracji, logowania, logowania zewnętrznego, zapomnianych haseł i dodatkowych funkcji.

![Wybierz indywidualne konta użytkowników, aby mieć wstępnie skonfigurowaną tożsamość](./media/image7-3.png)

**Rysunek 7-3**. Wybierz poszczególne konta użytkowników, aby mieć wstępnie skonfigurowaną tożsamość.

Obsługa tożsamości jest skonfigurowana w startupie, zarówno w configureservices, jak i Configure:

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
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Ważne jest, aby UseIdentity pojawił się przed UseMvc w Configure metody. Podczas konfigurowania tożsamości w ConfigureServices, można zauważyć wywołanie AddDefaultTokenProviders. Nie ma to nic wspólnego z tokenami, które mogą być używane do zabezpieczania komunikacji internetowej, ale zamiast tego odnosi się do dostawców, którzy tworzą monity, które mogą być wysyłane do użytkowników za pośrednictwem wiadomości SMS lub e-mail w celu potwierdzenia ich tożsamości.

Więcej informacji na temat [konfigurowania uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa) i [włączania zewnętrznych dostawców logowania](/aspnet/core/security/authentication/social/) z oficjalnych dokumentów ASP.NET Core.

### <a name="authorization"></a>Autoryzacja

Najprostsza forma autoryzacji polega na ograniczeniu dostępu do anonimowych użytkowników. Można to osiągnąć, po \[prostu\] stosując authorize atrybut do niektórych kontrolerów lub akcji. Jeśli używane są role, atrybut może zostać dodatkowo rozszerzony, aby ograniczyć dostęp do użytkowników należących do określonych ról, jak pokazano:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

W takim przypadku użytkownicy należący do ról HRManager lub Finanse (lub obu) będą mieli dostęp do kontrolera Wynagrodzeń. Aby wymagać, aby użytkownik należał do wielu ról (nie tylko jednej z kilku), można zastosować atrybut wiele razy, określając za każdym razem wymaganą rolę.

Określanie niektórych zestawów ról jako ciągów w wielu różnych kontrolerach i akcjach może prowadzić do niepożądanego powtarzania. Można skonfigurować zasady autoryzacji, które hermetyzują reguły autoryzacji, a następnie \[określić\] zasady zamiast poszczególnych ról podczas stosowania atrybutu Authorize:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Korzystając z zasad w ten sposób, można oddzielić rodzaje akcji są ograniczone od określonych ról lub reguł, które mają do niego zastosowanie. Później, jeśli utworzysz nową rolę, która musi mieć dostęp do niektórych zasobów, możesz po \[prostu\] zaktualizować zasady, zamiast aktualizować każdą listę ról w każdym atrybucie Authorize.

#### <a name="claims"></a>Oświadczenia

Oświadczenia to pary wartości nazw, które reprezentują właściwości uwierzytelnionego użytkownika. Na przykład można przechowywać numer pracownika użytkowników jako oświadczenie. Oświadczenia mogą być następnie używane jako część zasad autoryzacji. Można utworzyć zasadę o nazwie "Tylko pracownika", która wymaga istnienia oświadczenia o nazwie "EmployeeNumber", jak pokazano w tym przykładzie:

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

Te zasady mogą być \[następnie\] używane z Authorize atrybut do ochrony dowolnego kontrolera i/lub działania, jak opisano powyżej.

#### <a name="securing-web-apis"></a>Zabezpieczanie internetowych interfejsów API

Większość internetowych interfejsów API powinna zaimplementować system uwierzytelniania oparty na tokenie. Uwierzytelnianie tokenu jest bezstanowe i jest przeznaczone do skalowalnych. W systemie uwierzytelniania opartym na tokenie klient musi najpierw uwierzytelnić się u dostawcy uwierzytelniania. Jeśli się powiedzie, klient jest wystawiany token, który jest po prostu kryptograficznie znaczący ciąg znaków. Gdy klient następnie musi wydać żądanie do interfejsu API, dodaje ten token jako nagłówek na żądanie. Następnie serwer sprawdza poprawność tokenu znalezionego w nagłówku żądania przed zakończeniem żądania. Rysunek 7-4 pokazuje ten proces.

![TokenAuth (TokenAuth)](./media/image7-4.png)

**Rysunek 7-4.** Uwierzytelnianie oparte na tokenie dla interfejsów API sieci Web.

Można utworzyć własną usługę uwierzytelniania, zintegrować z usługą Azure AD i OAuth lub zaimplementować usługę przy użyciu narzędzia typu open source, takiego jak [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Zabezpieczenia niestandardowe

Należy zachować szczególną ostrożność przy "rolowaniu własnej" implementacji kryptografii, członkostwa użytkowników lub systemu generowania tokenów. Dostępnych jest wiele komercyjnych i otwartych alternatyw, które prawie na pewno będą miały lepsze zabezpieczenia niż implementacja niestandardowa.

> ### <a name="references--security"></a>Referencje – bezpieczeństwo
>
> - **Omówienie dokumentów zabezpieczeń**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Wymuszanie ssl w ASP.NET core app**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Wprowadzenie do tożsamości**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Wprowadzenie do autoryzacji**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Uwierzytelnianie i autoryzacja dla usługi API Apps w usłudze Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Serwer tożsamości**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikacja z klientem

Oprócz wyświetlania stron i odpowiadania na żądania danych za pośrednictwem internetowych interfejsów API ASP.NET aplikacje Core mogą komunikować się bezpośrednio z połączonymi klientami. Ta komunikacja wychodząca może korzystać z różnych technologii transportu, z których najczęściej są WebSockets. ASP.NET Core SignalR to biblioteka, która ułatwia dodawanie funkcji komunikacji między serwerem a klientem w czasie rzeczywistym do aplikacji. SignalR obsługuje różne technologie transportu, w tym WebSockets i abstrakcje od wielu szczegółów implementacji od dewelopera.

Komunikacja klienta w czasie rzeczywistym, czy przy użyciu WebSockets bezpośrednio lub innych technik, są przydatne w różnych scenariuszach aplikacji. Oto niektóre przykłady:

- Aplikacje do rozmów na żywo

- Monitorowanie aplikacji

- Aktualizacje postępu zadań

- Powiadomienia

- Interaktywne aplikacje formularzy

Podczas tworzenia komunikacji z klientem do aplikacji, zazwyczaj istnieją dwa składniki:

- Menedżer połączeń po stronie serwera (SignalR Hub, WebSocketManager WebSocketHandler)

- Biblioteka po stronie klienta

Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się za pomocą SignalR/WebSockets. Poniższy prosty program powtarza całą zawartość wysłaną do aplikacji czatu do konsoli, jako część przykładowej aplikacji WebSocketManager:

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

Zastanów się, w jaki sposób aplikacje komunikują się bezpośrednio z aplikacjami klienckimi i zastanów się, czy komunikacja w czasie rzeczywistym poprawiłaby środowisko użytkownika aplikacji.

> ### <a name="references--client-communication"></a>Referencje – Komunikacja z klientem
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/dotnet/aspnetcore/tree/master/src/SignalR>
> - **Menedżer gniazd websocket**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Projekt oparty na domenie — należy go zastosować?

Domain-Driven Design (DDD) to elastyczne podejście do tworzenia oprogramowania, które kładzie nacisk na skupienie się na _domenie biznesowej._ Kładzie duży nacisk na komunikację i interakcję z ekspertami domeny biznesowej, którzy mogą odnosić się do programistów, jak działa system rzeczywisty. Na przykład, jeśli budujesz system, który obsługuje transakcje giełdowe, twój ekspert domeny może być doświadczonym brokerem giełdowym. DDD ma na celu rozwiązanie dużych, złożonych problemów biznesowych i często nie jest odpowiedni dla mniejszych, prostszych aplikacji, ponieważ inwestycja w zrozumienie i modelowanie domeny nie jest tego warta.

Podczas tworzenia oprogramowania zgodnie z podejściem DDD, twój zespół (w tym nietechniczne zainteresowane strony i współautorzy) powinien opracować _wszechobecny język_ dla przestrzeni problemowej. Oznacza to, że ta sama terminologia powinna być używana dla koncepcji rzeczywistych są modelowane, odpowiednik oprogramowania i wszelkie struktury, które mogą istnieć, aby utrwalić pojęcie (na przykład tabele bazy danych). W związku z tym pojęcia opisane w wszechobecnym języku powinny stanowić podstawę _dla modelu domeny._

Model domeny składa się z obiektów, które współdziałają ze sobą do reprezentowania zachowanie systemu. Obiekty te mogą być podzielone na następujące kategorie:

- [Jednostki](https://deviq.com/entity/), które reprezentują obiekty z wątkiem tożsamości. Jednostki są zazwyczaj przechowywane w trwałości z kluczem, za pomocą którego można później pobrać.

- [Agreguje](https://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny być utrwaliłe jako jednostki.

- [Value obiektów](https://deviq.com/value-object/), które reprezentują pojęcia, które mogą być porównywane na podstawie sumy ich wartości właściwości. Na przykład DateRange składający się z daty rozpoczęcia i zakończenia.

- [Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują rzeczy dzieje się w systemie, które są interesujące dla innych części systemu.

Model domeny DDD powinien hermetyzować złożone zachowanie w modelu. Jednostki, w szczególności, nie powinny być jedynie kolekcje właściwości. Gdy model domeny nie zachowuje się i reprezentuje jedynie stan systemu, mówi się, że jest [to model anemiczny](https://deviq.com/anemic-model/), który jest niepożądany w DDD.

Oprócz tych typów modeli, DDD zazwyczaj wykorzystuje różne wzorce:

- [Repozytorium](https://deviq.com/repository-pattern/), dla abstrakcji szczegóły trwałości.

- [Fabryczne](https://en.wikipedia.org/wiki/Factory_method_pattern), do hermetyzacji tworzenia złożonych obiektów.

- Zdarzenia domeny, do oddzielenia zachowania zależnego od wyzwalania zachowania.

- [Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), do hermetyzacji złożonych szczegółów implementacji zachowań i/lub infrastruktury.

- [Command](https://en.wikipedia.org/wiki/Command_pattern), do oddzielenia od poleceń i wykonania samego polecenia.

- [Specyfikacja](https://deviq.com/specification-pattern/), dla hermetyzacji szczegółów kwerendy.

DDD zaleca również użycie czystej architektury omówione wcześniej, co pozwala na luźne sprzężenia, hermetyzacji i kodu, które można łatwo zweryfikować przy użyciu testów jednostkowych.

### <a name="when-should-you-apply-ddd"></a>Kiedy należy zastosować DDD

DDD doskonale nadaje się do dużych zastosowań o znacznej złożoności biznesowej (nie tylko technicznej). Aplikacja powinna wymagać wiedzy ekspertów domeny. W samym modelu domeny powinno istnieć istotne zachowanie, reprezentujące reguły biznesowe i interakcje wykraczające poza zwykłe przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych.

### <a name="when-shouldnt-you-apply-ddd"></a>Kiedy nie należy stosować DDD

DDD obejmuje inwestycje w modelowanie, architekturę i komunikację, które mogą nie być uzasadnione dla mniejszych aplikacji lub aplikacji, które są zasadniczo tylko CRUD (tworzenie/odczyt/aktualizacja/usuwanie). Jeśli zdecydujesz się zbliżyć do aplikacji po DDD, ale okaże się, że domena ma model anemiczny bez zachowania, może być konieczne przemyślenie podejścia. Aplikacja może nie potrzebować DDD lub może być potrzebna pomoc refaktoryzacji aplikacji w celu hermetyzacji logiki biznesowej w modelu domeny, a nie w bazie danych lub interfejsie użytkownika.

Podejście hybrydowe byłoby używać tylko DDD dla transakcyjnych lub bardziej złożonych obszarów aplikacji, ale nie dla prostszych CRUD lub tylko do odczytu części aplikacji. Na przykład nie trzeba mieć ograniczenia agregacji, jeśli jesteś wykonywania kwerendy danych, aby wyświetlić raport lub wizualizacji danych dla pulpitu nawigacyjnego. Jest to całkowicie dopuszczalne, aby mieć oddzielny, prostszy model odczytu dla takich wymagań.

> ### <a name="references--domain-driven-design"></a>Referencje — projekt oparty na domenie
>
> - **DDD w prostym języku angielskim (odpowiedź stackoverflow)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Wdrożenie

Istnieje kilka kroków zaangażowanych w proces wdrażania aplikacji ASP.NET Core, niezależnie od tego, gdzie będzie hostowana. Pierwszym krokiem jest opublikowanie aplikacji, co `dotnet publish` można zrobić za pomocą polecenia CLI. Spowoduje to skompilowanie aplikacji i umieszczenie wszystkich plików potrzebnych do uruchomienia aplikacji w wyznaczonym folderze. Podczas wdrażania z programu Visual Studio ten krok jest wykonywany automatycznie. Folder publikowania zawiera pliki exe i dll dla aplikacji i jej zależności. Niezależna aplikacja będzie również zawierać wersję programu runtime .NET. ASP.NET Podstawowe aplikacje będą również zawierać pliki konfiguracyjne, statyczne zasoby klienta i widoki MVC.

ASP.NET Aplikacje podstawowe to aplikacje konsolowe, które należy uruchomić po uruchomieniu serwera i ponownym uruchomieniu w przypadku awarii aplikacji (lub serwera). Menedżer procesów może służyć do automatyzacji tego procesu. Najczęstszymi menedżerami procesów dla ASP.NET Core są Nginx i Apache w systemie Linux oraz Usługi IIS lub Windows w systemie Windows.

Oprócz menedżera procesów ASP.NET aplikacje podstawowe mogą używać odwrotnego serwera proxy. Odwrotny serwer proxy odbiera żądania HTTP z Internetu i przekazuje je do Kestrel po wstępnej obsługi. Odwrócone serwery proxy zapewniają warstwę zabezpieczeń dla aplikacji. Kestrel nie obsługuje również obsługi wielu aplikacji na tym samym porcie, więc technik, takich jak nagłówki hostów, nie można używać z nim do włączania hostowania wielu aplikacji na tym samym porcie i adresie IP.

![Kestrel do Internetu](./media/image7-5.png)

**Rysunek 7-5**. ASP.NET hostowane w Kestrel za odwrotnym serwerem proxy

Innym scenariuszem, w którym odwrotny serwer proxy może być pomocny, jest zabezpieczenie wielu aplikacji przy użyciu protokołu SSL/HTTPS. W takim przypadku tylko zwrotny serwer proxy musiałby mieć skonfigurowany protokół SSL. Komunikacja między odwróconym serwerem proxy a kestrelem może odbywać się za pośrednictwem protokołu HTTP, jak pokazano na rysunku 7-6.

![ASP.NET hostowany za serwerem zwrotnym serwera proxy zabezpieczonym protokołem HTTPS](./media/image7-6.png)

**Rysunek 7-6**. ASP.NET hostowany za serwerem zwrotnym serwera proxy zabezpieczonym protokołem HTTPS

Coraz bardziej popularnym podejściem jest hostowanie aplikacji ASP.NET Core w kontenerze platformy Docker, które następnie mogą być hostowane lokalnie lub wdrażane na platformie Azure w celu hostingu opartego na chmurze. Kontener platformy Docker może zawierać kod aplikacji, uruchomiony na Kestrel i zostanie wdrożony za serwerem zwrotnym serwera proxy, jak pokazano powyżej.

Jeśli hostujesz aplikację na platformie Azure, możesz użyć bramy aplikacji platformy Microsoft Azure jako dedykowanego urządzenia wirtualnego, aby zapewnić kilka usług. Oprócz działania jako zwrotny serwer proxy dla poszczególnych aplikacji, brama aplikacji może również oferować następujące funkcje:

- Równoważenie obciążenia HTTP

- Odciążenie SSL (SSL tylko do Internetu)

- SSL koniec-koniec

- Routing wielooddziałowy (konsolidacja do 20 lokacji na jednej bramie aplikacji)

- Zapora aplikacji internetowej

- Obsługa gniazd internetowych

- Zaawansowana diagnostyka

_Dowiedz się więcej o opcjach wdrażania platformy Azure w [rozdziale 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odwołania — wdrażanie
>
> - **Omówienie hostingu i wdrażania**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kiedy używać kestrelu z zwrotnym serwerem proxy**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostuj ASP.NET aplikacje Core w platformie Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Przedstawiamy bramę aplikacji platformy Azure**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Poprzedni](common-client-side-web-technologies.md)
>[następny](work-with-data-in-asp-net-core-apps.md)
