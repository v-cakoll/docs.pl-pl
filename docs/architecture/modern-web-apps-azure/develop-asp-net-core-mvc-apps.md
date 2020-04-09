---
title: Opracowywanie aplikacji ASP.NET Core MVC
description: Architekt nowoczesnych aplikacji sieci Web z ASP.NET Core i Azure | opracowywanie ASP.NET Core MVC Apps
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 3de70af23206b0ae0525541b3d2cb480dc5bb882
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987910"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Opracowywanie aplikacji core ASP.NET MVC

> "Nie jest ważne, aby za pierwszym razem to naprawić. To niezwykle ważne, aby to naprawić po raz ostatni."  
> _- Andrew Hunt i David Thomas_

ASP.NET Core to wieloplatformowa, otwarta struktura do tworzenia nowoczesnych aplikacji internetowych zoptymalizowanych pod kątem chmury. ASP.NET aplikacje Core są lekkie i modułowe, z wbudowaną obsługą iniekcji zależności, co zapewnia większą sprawdzalność i łatwość konserwacji. W połączeniu z MVC, który obsługuje tworzenie nowoczesnych interfejsów API sieci web oprócz aplikacji opartych na widoku, ASP.NET Core jest zaawansowana struktura, z której można tworzyć aplikacje sieci web dla przedsiębiorstw.

## <a name="mvc-and-razor-pages"></a>Strony MVC i Razor

ASP.NET Core MVC oferuje wiele funkcji, które są przydatne do tworzenia interfejsów API i aplikacji opartych na sieci Web. Termin MVC oznacza "Model-View-Controller", wzorzec interfejsu użytkownika, który dzieli obowiązki odpowiadania na żądania użytkownika na kilka części. Oprócz podążania za tym wzorcem można również zaimplementować funkcje w aplikacjach ASP.NET Core jako strony Razor Pages. Strony brzytwy są wbudowane w ASP.NET Core MVC i używają tych samych funkcji do routingu, wiązania modelu itp. Jednak zamiast oddzielnych folderów i plików dla kontrolerów, widoków itp.

Podczas tworzenia nowej aplikacji core ASP.NET, powinieneś mieć na uwadze plan dla rodzaju aplikacji, którą chcesz utworzyć. W programie Visual Studio wybierz jedną z kilku szablonów. Trzy najpopularniejsze szablony projektów to interfejs API sieci Web, aplikacja sieci Web i aplikacja sieci Web (administrator widoku modelu). Chociaż tę decyzję można podjąć tylko przy pierwszym utworzeniu projektu, nie jest to nieodwołalna decyzja. Projekt interfejsu API sieci Web używa standardowych kontrolerów widoku modelu — domyślnie brakuje widoków. Podobnie domyślny szablon aplikacji sieci Web używa stron Razor Pages, a więc również nie ma folderu Widoki. Można dodać widok folderu do tych projektów później do obsługi zachowania opartego na widoku. Projekty interfejsu API sieci Web i kontrolera widoku modelu domyślnie nie zawierają folderu Pages, ale można go dodać później, aby obsługiwać zachowanie oparte na stronach Razor. Te trzy szablony można potraktować jako obsługę trzech różnych rodzajów domyślnej interakcji użytkownika: danych (interfejsu API sieci Web), opartych na stronie i opartych na widoku. Jednak można mieszać i dopasować dowolne lub wszystkie z nich w ramach jednego projektu, jeśli chcesz.

### <a name="why-razor-pages"></a>Dlaczego Razor Pages?

Razor Pages jest domyślnym podejściem dla nowych aplikacji sieci web w programie Visual Studio. Razor Pages oferuje prostszy sposób tworzenia funkcji aplikacji opartych na stronach, takich jak formularze inne niż SPA. Za pomocą kontrolerów i widoków, było wspólne dla aplikacji mają bardzo duże kontrolery, które pracowały z wielu różnych zależności i modeli widoku i zwrócił wiele różnych widoków. Spowodowało to większą złożoność i często powodowało, że kontrolerzy nie przestrzegali zasady jednolitej odpowiedzialności ani zasad otwartych/zamkniętych. Razor Pages rozwiązuje ten problem, hermetyzując logikę po stronie serwera dla danej logicznej "strony" w aplikacji sieci web z jego znaczników Razor. Strona Razor, która nie ma logiki po stronie serwera, może po prostu składać się z pliku Razor (na przykład "Index.cshtml"). Jednak większość nietrywialnych stron Razor będzie miała skojarzoną klasę modelu strony, która zgodnie z konwencją nosi nazwę pliku Razor z rozszerzeniem ".cs" (na przykład "Index.cshtml.cs").

Model strony Razor Page łączy w sobie obowiązki kontrolera MVC i modelu viewmodel. Zamiast obsługi żądań z metod akcji kontrolera, programy obsługi modelu strony, takie jak "OnGet()" są wykonywane, renderowania ich skojarzonej strony domyślnie. Razor Pages upraszcza proces tworzenia poszczególnych stron w aplikacji ASP.NET Core, jednocześnie zapewniając wszystkie funkcje architektoniczne ASP.NET Core MVC. Są one dobrym wyborem domyślnym dla nowych funkcji opartych na stronie.

### <a name="when-to-use-mvc"></a>Kiedy stosować MVC

Jeśli tworzysz interfejsy API sieci Web, wzorzec MVC ma większy sens niż próba użycia stron Razor. Jeśli projekt będzie udostępniać tylko punkty końcowe interfejsu API sieci web, najlepiej rozpocząć od szablonu projektu interfejsu API sieci Web. W przeciwnym razie można łatwo dodać kontrolery i skojarzone punkty końcowe interfejsu API do dowolnej aplikacji ASP.NET Core. Użyj podejścia MVC opartego na widoku, jeśli przeprowadzasz migrację istniejącej aplikacji z ASP.NET MVC 5 lub starszej, aby ASP.NET Core MVC i chcesz to zrobić przy jak najmniejszym wysiłku. Po dokonaniu wstępnej migracji możesz ocenić, czy warto przyjąć strony Razor pages do nowych funkcji, czy nawet jako migrację hurtową.

Niezależnie od tego, czy zdecydujesz się na tworzenie aplikacji sieci web przy użyciu stron Razor lub widoków MVC, aplikacja będzie miała podobną wydajność i będzie obejmować obsługę iniekcji zależności, filtrów, powiązania modelu, sprawdzania poprawności i tak dalej.

## <a name="mapping-requests-to-responses"></a>Mapowanie żądań do odpowiedzi

W swej istocie aplikacje ASP.NET Core mapują przychodzące żądania na odpowiedzi wychodzące. Na niskim poziomie odbywa się to za pomocą oprogramowania pośredniczącego i proste ASP.NET podstawowe aplikacje i mikrousług mogą składać się wyłącznie z niestandardowego oprogramowania pośredniczącego. Korzystając z ASP.NET Core MVC, można pracować na nieco wyższym poziomie, myśląc w kategoriach _tras,_ _kontrolerów_i _działań._ Każde żądanie przychodzące jest porównywane z tabelą routingu aplikacji, a jeśli zostanie znaleziona pasująca trasa, wywoływana jest skojarzona metoda akcji (należąca do kontrolera) do obsługi żądania. Jeśli nie zostanie znaleziona pasująca trasa, wywoływany jest program obsługi błędów (w tym przypadku zwracany wynik NotFound).

ASP.NET aplikacje Core MVC mogą używać konwencjonalnych tras, tras atrybutów lub obu tych podstawowych tras. Konwencjonalne trasy są definiowane w kodzie, określając _konwencje_ routingu przy użyciu składni, jak w poniższym przykładzie:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

W tym przykładzie do tabeli routingu dodano trasę o nazwie "default". Definiuje szablon trasy z symbolami zastępczymi dla _kontrolera,_ _akcji_i _identyfikatora_. Symbole zastępcze kontrolera i akcji mają domyślnie określone ("Strona główna" i "Indeks", odpowiednio), a symbol zastępczy identyfikatora jest opcjonalny (na podstawie "?" zastosowanego do niego). Konwencja zdefiniowana w tym miejscu stanowi, że pierwsza część żądania powinna odpowiadać nazwie kontrolera, druga część akcji, a następnie w razie potrzeby trzecia część będzie reprezentować parametr id. Konwencjonalne trasy są zazwyczaj definiowane w jednym miejscu dla aplikacji, na przykład w Configure metody w Startup klasy.

Trasy atrybutów są stosowane do kontrolerów i akcji bezpośrednio, a nie określone globalnie. Ma to tę zaletę, że znacznie bardziej wykrywalne, gdy patrzysz na określonej metody, ale oznacza, że informacje o routingu nie jest przechowywany w jednym miejscu w aplikacji. Za pomocą tras atrybutów można łatwo określić wiele tras dla danej akcji, a także połączyć trasy między kontrolerami i akcjami. Przykład:

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

Trasy można określić na [HttpGet] i podobne atrybuty, unikając konieczności dodawania atrybutów [Route] . Trasy atrybutów mogą również używać tokenów, aby zmniejszyć potrzebę powtarzania nazw kontrolerów lub akcji, jak pokazano poniżej:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages nie używa routingu atrybutów. W ramach dyrektywy `@page` można określić dodatkowe informacje o szablonie trasy dla strony Razor:

```csharp
@page "{id:int}"
```

W poprzednim przykładzie strona, o którą mowa, będzie `id` pasować do trasy z parametrem liczby całkowitej. Na przykład *strona Products.cshtml* znajdująca `/Pages` się w katalogu głównym miałaby tę trasę:

```csharp
"/Products/123"
```

Gdy dane żądanie zostało dopasowane do trasy, ale przed wywołaniem metody akcji, ASP.NET Core MVC wykona [powiązanie modelu](/aspnet/core/mvc/models/model-binding) i [sprawdzanie poprawności modelu](/aspnet/core/mvc/models/validation) na żądanie. Powiązanie modelu jest odpowiedzialne za konwertowanie przychodzących danych HTTP na typy .NET określone jako parametry metody akcji, która ma zostać wywołana. Na przykład jeśli metoda akcji oczekuje parametru int id, powiązanie modelu spróbuje podać ten parametr z wartości podanej w ramach żądania. W tym celu powiązanie modelu wyszukuje wartości w zaksięgowanych formularzach, wartości w samej marszruty i wartości ciągu zapytania. Zakładając, że wartość identyfikatora zostanie znaleziona, zostanie przekonwertowana na liczę całkowitą przed przekazaniem do metody akcji.

Po powiązaniu modelu, ale przed wywołaniem metody akcji, występuje sprawdzanie poprawności modelu. Sprawdzanie poprawności modelu używa atrybutów opcjonalnych na typ modelu i może pomóc w zapewnieniu, że podany obiekt modelu jest zgodny z określonymi wymaganiami dotyczącymi danych. Niektóre wartości mogą być określone w razie potrzeby lub ograniczone do określonej długości lub zakresu liczbowego itp. Jeśli atrybuty sprawdzania poprawności są określone, ale model nie spełnia ich wymagań, właściwość ModelState.IsValid będzie false, a zestaw reguł sprawdzania poprawności nie zakończy się niepowodzeniem będą dostępne do wysłania do klienta wysyłającego żądanie.

Jeśli używasz sprawdzania poprawności modelu, należy zawsze sprawdzić, czy model jest prawidłowy przed wykonaniem jakichkolwiek poleceń zmiany stanu, aby upewnić się, że aplikacja nie jest uszkodzony przez nieprawidłowe dane. Można użyć [filtru,](/aspnet/core/mvc/controllers/filters) aby uniknąć konieczności dodawania kodu do tego w każdej akcji. ASP.NET Filtry Core MVC oferują sposób przechwytywania grup żądań, dzięki czemu wspólne zasady i przekrojowe problemy mogą być stosowane na podstawie ukierunkowanej. Filtry mogą być stosowane do poszczególnych akcji, całych kontrolerów lub globalnie dla aplikacji.

W przypadku interfejsów API sieci web ASP.NET Core MVC obsługuje [_negocjacje zawartości,_](/aspnet/core/mvc/models/formatting)umożliwiając żądania określania sposobu formatowania odpowiedzi. Na podstawie nagłówków podanych w żądaniu akcje zwracające dane sformatować odpowiedź w formacie XML, JSON lub innym obsługiwanym formacie. Ta funkcja umożliwia ten sam interfejs API, który ma być używany przez wielu klientów z różnymi wymaganiami dotyczącymi formatu danych.

Projekty interfejsu API sieci `[ApiController]` Web należy rozważyć użycie atrybutu, który może być stosowany do poszczególnych kontrolerów, do klasy kontrolera podstawowego lub do całego zestawu. Ten atrybut dodaje automatyczne sprawdzanie poprawności modelu i wszelkie działania z nieprawidłowym modelu zwróci BadRequest ze szczegółami błędów sprawdzania poprawności. Atrybut wymaga również wszystkie akcje mają trasę atrybutu, a nie przy użyciu konwencjonalnej trasy i zwraca bardziej szczegółowe informacje ProblemDetails w odpowiedzi na błędy.

> ### <a name="references--mapping-requests-to-responses"></a>Odwołania — mapowanie żądań odpowiedzi
>
> - **Akcje routingu do kontrolera**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Wiązanie modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Sprawdzanie poprawności modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Atrybut ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Praca z zależnościami

ASP.NET Core ma wbudowaną obsługę i wewnętrznie korzysta z techniki znanej jako [iniekcja zależności.](/aspnet/core/fundamentals/dependency-injection) Wtrysk zależności jest techniką, która umożliwia luźne sprzężenie między różnymi częściami aplikacji. Luźniejsze sprzęgło jest pożądane, ponieważ ułatwia izolowanie części aplikacji, co pozwala na testowanie lub wymianę. To również sprawia, że mniej prawdopodobne, że zmiana w jednej części aplikacji będzie miał nieoczekiwany wpływ w innym miejscu w aplikacji. Iniekcja zależności opiera się na zasadzie inwersji zależności i często jest kluczem do osiągnięcia zasady otwartej/zamkniętej. Oceniając, jak aplikacja działa z jej zależnościami, uważaj na statyczny zapach kodu [przylegania](https://deviq.com/static-cling/) i pamiętaj o aforyzmie "[nowy to klej".](https://ardalis.com/new-is-glue)

Statyczne przylgnięcie występuje, gdy klasy nawiązują połączenia z metodami statycznymi lub uzyskują dostęp do właściwości statycznych, które mają skutki uboczne lub zależności w infrastrukturze. Na przykład jeśli masz metodę, która wywołuje metodę statyczną, która z kolei zapisuje do bazy danych, metoda jest ściśle sprzężona z bazą danych. Wszystko, co przerywa wywołanie bazy danych spowoduje przerwanie metody. Testowanie takich metod jest notorycznie trudne, ponieważ takie testy wymagają komercyjnych bibliotek szyderczych do szyderstwa z wywołań statycznych lub mogą być testowane tylko z testową bazą danych w miejscu. Statyczne wywołania, które nie mają żadnej zależności od infrastruktury, zwłaszcza te, które są całkowicie bezstanowe, są w porządku do wywołania i nie mają wpływu na sprzężenie lub testability (poza kod sprzężenia do statycznego wywołania.

Wielu deweloperów rozumie ryzyko statycznego przylgnięcia i stanu globalnego, ale nadal będzie ściśle łączyć ich kod z określonymi implementacjami za pośrednictwem bezpośredniego wystąpienia. "Nowy jest klej" ma być przypomnieniem tego sprzężenia, a `new` nie ogólne potępienie stosowania słowa kluczowego. Podobnie jak w przypadku wywołań metod statycznych, nowe wystąpienia typów, które nie mają zależności zewnętrznych zazwyczaj nie ściśle parować kod do szczegółów implementacji lub utrudnić testowanie. Ale za każdym razem, gdy klasa jest tworzone, poświęć tylko krótką chwilę, aby rozważyć, czy ma sens kodowania tego konkretnego wystąpienia w tej konkretnej lokalizacji lub jeśli byłoby lepsze projektowanie, aby zażądać tego wystąpienia jako zależności.

### <a name="declare-your-dependencies"></a>Deklarowanie zależności

ASP.NET Core jest zbudowany wokół posiadania metod i klas deklarują swoje zależności, żądając ich jako argumenty. ASP.NET aplikacje są zazwyczaj skonfigurowane w startup klasy, która sama jest skonfigurowana do obsługi iniekcji zależności w kilku punktach. Jeśli startup klasy ma konstruktora, może zażądać zależności za pośrednictwem konstruktora, tak:

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

Startup Klasy jest interesujące, ponieważ nie ma żadnych jawnych wymagań typu dla niego. Nie dziedziczy ze specjalnej klasy podstawowej uruchamiania ani nie implementuje żadnego określonego interfejsu. Można nadać mu konstruktora, czy nie, i można określić dowolną liczbę parametrów na konstruktorze. Po uruchomieniu hosta sieci web skonfigurowany dla aplikacji wywoła klasę uruchamiania, której chcesz użyć, i użyje iniekcji zależności, aby wypełnić wszystkie zależności, których wymaga klasa Uruchamianie. Oczywiście jeśli zażądasz parametrów, które nie są skonfigurowane w kontenerze usług używanym przez ASP.NET Core, otrzymasz wyjątek, ale tak długo, jak trzymać się zależności kontener wie o, można zażądać, co chcesz.

Iniekcja zależności jest wbudowana w aplikacje ASP.NET Core od samego początku podczas tworzenia wystąpienia uruchamiania. To nie kończy się na startup klasy. Można również zażądać zależności w Configure metody:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices Metoda jest wyjątkiem od tego zachowania; musi zająć tylko jeden parametr typu IServiceCollection. Tak naprawdę nie trzeba obsługiwać iniekcji zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów do kontenera usług, a z drugiej strony ma dostęp do wszystkich aktualnie skonfigurowanych usług za pośrednictwem parametru IServiceCollection. W związku z tym można pracować z zależności zdefiniowane w ASP.NET core kolekcji usług w każdej części Startup klasy, albo żądając potrzebnej usługi jako parametr lub pracy z IServiceCollection w ConfigureServices.

> [!NOTE]
> Jeśli musisz upewnić się, że niektóre usługi są dostępne dla klasy uruchamiania, można skonfigurować je przy użyciu usługi IWebHostBuilder i jego configureservices metody wewnątrz CreateDefaultBuilder wywołania.

Startup Klasy jest modelem, jak należy struktury innych części aplikacji ASP.NET Core, od kontrolerów do oprogramowania pośredniczącego do filtrów do własnych usług. W każdym przypadku należy postępować zgodnie z [zasadą jawne zależności](https://deviq.com/explicit-dependencies-principle/), żądając zależności, a nie bezpośrednio ich tworzenia i wykorzystując iniekcji zależności w całej aplikacji. Należy uważać, gdzie i jak bezpośrednio wystąpienia implementacji, zwłaszcza usług i obiektów, które działają z infrastrukturą lub mają skutki uboczne. Preferuj pracę z abstrakcjami zdefiniowanymi w rdzeniu aplikacji i przekazanymi jako argumenty do hardcoding odwołań do określonych typów implementacji.

## <a name="structuring-the-application"></a>Strukturyzacja aplikacji

Aplikacje monolityczne zazwyczaj mają jeden punkt wejścia. W przypadku aplikacji sieci web ASP.NET Core punktem wejścia będzie projekt sieci web ASP.NET Core. Nie oznacza to jednak, że rozwiązanie powinno składać się tylko z jednego projektu. Warto podzielić aplikację na różne warstwy, aby śledzić oddzielenie obaw. Po podziale na warstwy warto wyjść poza foldery, aby oddzielić projekty, co może pomóc w osiągnięciu lepszej hermetyzacji. Najlepszym podejściem do osiągnięcia tych celów za pomocą aplikacji ASP.NET Core jest odmiana czystej architektury omówiona w rozdziale 5. Zgodnie z tym podejściem rozwiązanie aplikacji będzie składać się z oddzielnych bibliotek dla interfejsu użytkownika, infrastruktury i applicationcore.

Oprócz tych projektów uwzględniono również oddzielne projekty testowe (testy zostały omówione w rozdziale 9).

Model obiektu aplikacji i interfejsy powinny być umieszczone w projekcie ApplicationCore. Ten projekt będzie miał jak najmniej zależności, jak to możliwe, a inne projekty w rozwiązaniu będzie odwoływać się do niego. Jednostki biznesowe, które muszą być utrwalone są zdefiniowane w projekcie ApplicationCore, podobnie jak usługi, które nie są bezpośrednio zależne od infrastruktury.

Szczegóły implementacji, takie jak trwałość jest wykonywana lub jak powiadomienia mogą być wysyłane do użytkownika, są przechowywane w projekcie infrastruktury. W tym projekcie będzie odwoływać się do pakietów specyficznych dla implementacji, takich jak Entity Framework Core, ale nie należy udostępniać szczegółów dotyczących tych implementacji poza projektem. Usługi infrastruktury i repozytoria należy zaimplementować interfejsy, które są zdefiniowane w projekcie ApplicationCore, a jego implementacje trwałości są odpowiedzialne za pobieranie i przechowywanie jednostek zdefiniowanych w ApplicationCore.

Projekt interfejsu użytkownika ASP.NET Core jest odpowiedzialny za wszelkie problemy na poziomie interfejsu użytkownika, ale nie powinien zawierać logiki biznesowej ani szczegółów infrastruktury. W rzeczywistości najlepiej nie powinien mieć nawet zależność od projektu infrastruktury, co pomoże zapewnić, że nie ma zależności między dwoma projektami jest wprowadzany przypadkowo. Można to osiągnąć za pomocą kontenera DI innej firmy, takiego jak Autofac, który umożliwia definiowanie reguł DI w klasach modułu w każdym projekcie.

Innym podejściem do oddzielenia aplikacji od szczegółów implementacji jest mieć mikrousług wywołania aplikacji, być może wdrożony w poszczególnych kontenerach platformy Docker. Zapewnia to jeszcze większe oddzielenie obaw i oddzielenie niż wykorzystanie DI między dwoma projektami, ale ma dodatkową złożoność.

### <a name="feature-organization"></a>Organizacja funkcji

Domyślnie aplikacje ASP.NET Core organizują strukturę folderów w taki sposób, aby zawierały kontrolery i widoki oraz często modele viewmodels. Kod po stronie klienta do obsługi tych struktur po stronie serwera jest zazwyczaj przechowywane oddzielnie w folderze wwwroot. Jednak duże aplikacje mogą napotkać problemy z tą organizacją, ponieważ praca nad daną funkcją często wymaga przeskakiwania między tymi folderami. Staje się to coraz trudniejsze w miarę wzrostu liczby plików i podfolderów w każdym folderze, co powoduje znaczne przewijanie Eksploratora rozwiązań. Jednym z rozwiązań tego problemu jest organizowanie kodu aplikacji według _funkcji,_ a nie według typu pliku. Ten styl organizacyjny jest zazwyczaj określany jako foldery obiektów lub [plasterki operacji](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) (zobacz także: [Plasterki pionowe](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC obsługuje obszary w tym celu. Korzystając z obszarów, można tworzyć oddzielne zestawy folderów Kontrolery i Widoki (a także wszystkie skojarzone modele) w każdym folderze Obszar. Rysunek 7-1 przedstawia przykładową strukturę folderów przy użyciu obszarów.

![Przykładowa organizacja obszaru](./media/image7-1.png)

**Rysunek 7-1**. Przykładowa organizacja obszaru

Podczas korzystania z obszarów, należy użyć atrybutów do dekoracji kontrolerów z nazwą obszaru, do którego należą:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Należy również dodać obsługę obszarów do tras:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Oprócz wbudowanej obsługi obszarów można również użyć własnej struktury folderów i konwencji zamiast atrybutów i tras niestandardowych. Pozwoliłoby to na foldery funkcji, które nie zawierają oddzielnych folderów dla widoków, kontrolerów itp., utrzymując hierarchię bardziej płaski i ułatwiając wyświetlanie wszystkich powiązanych plików w jednym miejscu dla każdej funkcji.

ASP.NET Core używa wbudowanych typów konwencji do kontrolowania jego zachowania. Można zmodyfikować lub zastąpić te konwencje. Na przykład można utworzyć konwencję, która automatycznie otrzyma nazwę funkcji dla danego kontrolera na podstawie jego obszaru nazw (która zazwyczaj koreluje z folderem, w którym znajduje się kontroler):

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

Następnie należy określić tę konwencję jako opcję podczas dodawania obsługi MVC do aplikacji w configureservices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC używa również konwencji do lokalizowania widoków. Można zastąpić go konwencją niestandardową, tak aby widoki znajdowały się w folderach elementów (przy użyciu nazwy funkcji dostarczonej przez FeatureConvention powyżej). Możesz dowiedzieć się więcej na temat tego podejścia i pobrać próbkę roboczą z artykułu MSDN Magazine, [Feature Slices for ASP.NET Core MVC](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).

### <a name="cross-cutting-concerns"></a>Zagadnienia ogólne

Wraz z rozwojem aplikacji coraz ważniejsze staje się uwzględnienie problemów przekrojowych w celu wyeliminowania powielania działań i zachowania spójności. Niektóre przykłady przekrojowych problemów w ASP.NET Podstawowe aplikacje to uwierzytelnianie, reguły sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługa błędów, chociaż istnieje wiele innych. ASP.NET filtry Core MVC umożliwiają [uruchamianie](/aspnet/core/mvc/controllers/filters) kodu przed lub po niektórych krokach w potoku przetwarzania żądań. Na przykład filtr można uruchomić przed i po powiązanie modelu, przed i po akcji lub przed i po wyniku akcji. Można również użyć filtru autoryzacji, aby kontrolować dostęp do pozostałej części potoku. Rysunki 7-2 pokazuje, jak wykonanie żądania przepływa przez filtry, jeśli jest skonfigurowany.

![Żądanie jest przetwarzane za pośrednictwem filtrów autoryzacji, filtrów zasobów, powiązania modelu, filtrów akcji, wykonywania akcji i konwersji wyników akcji, filtrów wyjątków, filtrów wyników i wykonywania wyników. W drodze do wyjścia żądanie jest przetwarzane tylko przez filtry wyników i filtry zasobów, zanim stanie się odpowiedzią wysłaną do klienta.](./media/image7-2.png)

**Rysunek 7-2**. Żądaj wykonania za pośrednictwem filtrów i potoku żądań.

Filtry są zwykle implementowane jako atrybuty, dzięki czemu można je zastosować do kontrolerów lub akcji (lub nawet globalnie). Po dodaniu w ten sposób filtry określone na poziomie akcji zastępują lub opierają się na filtrach określonych na poziomie kontrolera, które same zastępują filtry globalne. Na przykład \[Route\] atrybut może służyć do tworzenia tras między kontrolerami i akcji. Podobnie autoryzacja może być skonfigurowana na poziomie kontrolera, a następnie zastąpiona przez poszczególne akcje, jak pokazuje poniższy przykład:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

Pierwsza metoda, Login, używa AllowAnonymous filtr (atrybut) do zastąpienia autoryzować filtr ustawiony na poziomie kontrolera. Akcja ForgotPassword (i inne działania w klasie, która nie ma atrybutu AllowAnonymous) będą wymagać uwierzytelnionego żądania.

Filtry mogą służyć do wyeliminowania powielania w postaci typowych zasad obsługi błędów dla interfejsów API. Na przykład typowe zasady interfejsu API jest zwracanie NotFound odpowiedzi na żądania odwołujące się do kluczy, które nie istnieją i BadRequest odpowiedzi, jeśli sprawdzanie poprawności modelu nie powiedzie się. Poniższy przykład przedstawia te dwie zasady w działaniu:

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

Nie zezwalaj na to, aby metody działania stały się zaśmiecone kodem warunkowym w ten sposób. Zamiast tego należy przeciągnąć zasady do filtrów, które mogą być stosowane zgodnie z potrzebami. W tym przykładzie sprawdzanie poprawności modelu, które powinno wystąpić w dowolnym momencie, gdy polecenie jest wysyłane do interfejsu API, można zastąpić następującym atrybutem:

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

Można dodać `ValidateModelAttribute` do projektu jako zależność NuGet, dołączając [pakiet Ardalis.ValidateModel.](https://www.nuget.org/packages/Ardalis.ValidateModel) W przypadku interfejsów API `ApiController` można użyć atrybutu, aby wymusić `ValidateModel` to zachowanie bez konieczności stosowania oddzielnego filtru.

Podobnie filtr może służyć do sprawdzania, czy istnieje rekord i zwracać 404 przed wykonaniem akcji, eliminując konieczność wykonywania tych kontroli w akcji. Po wyciągnięciu typowych konwencji i zorganizowaniu rozwiązania w celu oddzielenia kodu infrastruktury i logiki biznesowej od interfejsu użytkownika metody działania MVC powinny być bardzo cienkie:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Możesz przeczytać więcej o implementacji filtrów i pobrać próbkę roboczą z artykułu MSDN Magazine, [Real-World ASP.NET Core MVC Filters](https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters).

> ### <a name="references--structuring-applications"></a>Referencje – aplikacje strukturyzujące
>
> - **Obszary**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine – Wycinki do ASP.NET Core MVC**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN Magazine – Filtry MVC ASP.NET w świecie rzeczywistym**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Zabezpieczenia

Zabezpieczanie aplikacji sieci web jest dużym tematem, z wieloma zagadnieniami. Na najbardziej podstawowym poziomie zabezpieczeń obejmuje zapewnienie, że wiesz, z kogo pochodzi dane żądanie, a następnie zapewnienie, że żądanie ma tylko dostęp do zasobów, które powinien. Uwierzytelnianie to proces porównywania poświadczeń dostarczonych z żądaniem do tych w zaufanym magazynie danych, aby sprawdzić, czy żądanie powinno być traktowane jako pochodzące ze znanej jednostki. Autoryzacja to proces ograniczania dostępu do niektórych zasobów na podstawie tożsamości użytkownika. Trzecią obawą bezpieczeństwa jest ochrona żądań przed podsłuchiwaniem przez osoby trzecie, dla których należy przynajmniej [upewnić się, że SSL jest używany przez aplikację.](/aspnet/core/security/enforcing-ssl)

### <a name="authentication"></a>Authentication

ASP.NET Core Identity to system członkostwa, którego można używać do obsługi funkcji logowania dla aplikacji. Ma wsparcie dla lokalnych kont użytkowników, a także wsparcie zewnętrznego dostawcy logowania od dostawców, takich jak Konto Microsoft, Twitter, Facebook, Google i inne. Oprócz ASP.NET podstawowej tożsamości aplikacja może używać uwierzytelniania systemu Windows lub zewnętrznego dostawcy tożsamości, takiego jak [serwer tożsamości.](https://github.com/IdentityServer/IdentityServer4)

ASP.NET Tożsamość podstawowa jest uwzględniona w nowych szablonach projektu, jeśli wybrano opcję Indywidualne konta użytkowników. Ten szablon obejmuje obsługę rejestracji, logowania, zewnętrznych loginów, zapomnianych haseł i dodatkowych funkcji.

![Wybierz indywidualne konta użytkowników, aby wstępnie skonfigurować tożsamość](./media/image7-3.png)

**Rysunek 7-3**. Wybierz indywidualne konta użytkowników, aby wstępnie skonfigurować tożsamość.

Obsługa tożsamości jest skonfigurowana w obszarze Uruchamianie, zarówno w obszarze Konfigurowanie usług, jak i Konfigurowanie:

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

Ważne jest, aby useidentity pojawiać się przed UseMvc w Configure metody. Podczas konfigurowania tożsamości w ConfigureServices, można zauważyć wywołanie AddDefaultTokenProviders. Nie ma to nic wspólnego z tokenami, które mogą być używane do zabezpieczania komunikacji internetowej, ale zamiast tego odnosi się do dostawców, którzy tworzą monity, które mogą być wysyłane do użytkowników za pośrednictwem wiadomości SMS lub e-mail, aby mogli potwierdzić swoją tożsamość.

Możesz dowiedzieć się więcej o [konfigurowaniu uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa) i [włączaniu zewnętrznych dostawców logowania](/aspnet/core/security/authentication/social/) z oficjalnych dokumentów ASP.NET Core.

### <a name="authorization"></a>Autoryzacja

Najprostsza forma autoryzacji polega na ograniczeniu dostępu do anonimowych użytkowników. Można to osiągnąć po prostu \[stosując\] atrybut Authorize do niektórych administratorów lub działań. Jeśli role są używane, atrybut można dodatkowo rozszerzyć, aby ograniczyć dostęp do użytkowników, którzy należą do niektórych ról, jak pokazano:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

W takim przypadku użytkownicy należący do ról HRManager lub Finance (lub obu) będą mieli dostęp do SalaryController. Aby wymagać, aby użytkownik należał do wielu ról (nie tylko jeden z kilku), można zastosować atrybut wiele razy, określając wymaganą rolę za każdym razem.

Określanie niektórych zestawów ról jako ciągów w wielu różnych kontrolerów i akcje może prowadzić do niepożądanych powtórzeń. Można skonfigurować zasady autoryzacji, które hermetyzują reguły autoryzacji, a następnie \[określić\] zasady zamiast poszczególnych ról podczas stosowania atrybutu Autoryzuj:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Za pomocą zasad w ten sposób, można oddzielić rodzaje akcji są ograniczone od określonych ról lub reguł, które mają zastosowanie do niego. Później, jeśli utworzysz nową rolę, która musi mieć dostęp do niektórych zasobów, można po \[prostu\] zaktualizować zasady, zamiast aktualizować każdą listę ról w każdym atrybutie Authorize.

#### <a name="claims"></a>Oświadczenia

Oświadczenia są parami wartości nazw, które reprezentują właściwości uwierzytelnionego użytkownika. Na przykład można przechowywać numer pracownika użytkowników jako oświadczenie. Oświadczenia mogą być następnie używane jako część zasad autoryzacji. Można utworzyć zasadę o nazwie "EmployeeOnly", która wymaga istnienia oświadczenia o nazwie "EmployeeNumber", jak pokazano w tym przykładzie:

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

Zasady te mogą być \[następnie\] używane z atrybutem Authorize w celu ochrony dowolnego administratora i/lub akcji, jak opisano powyżej.

#### <a name="securing-web-apis"></a>Zabezpieczanie interfejsów API sieci Web

Większość internetowych interfejsów API powinna implementować system uwierzytelniania opartego na tokenach. Uwierzytelnianie tokenu jest bezstanowe i zaprojektowane tak, aby było skalowalne. W systemie uwierzytelniania opartego na tokenie klient musi najpierw uwierzytelnić się u dostawcy uwierzytelniania. Jeśli się powiedzie, klient jest wystawiany token, który jest po prostu kryptograficznie znaczący ciąg znaków. Gdy klient następnie musi wydać żądanie do interfejsu API, dodaje ten token jako nagłówek na żądanie. Serwer następnie sprawdza poprawność tokenu znalezionego w nagłówku żądania przed wykonaniem żądania. Rysunek 7-4 przedstawia ten proces.

![TokenAuth (Właso)](./media/image7-4.png)

**Rysunek 7-4.** Uwierzytelnianie oparte na tokenie dla interfejsów API sieci Web.

Można utworzyć własną usługę uwierzytelniania, zintegrować z usługą Azure AD i OAuth lub zaimplementować usługę przy użyciu narzędzia typu open source, takiego jak [IdentityServer.](https://github.com/IdentityServer)

#### <a name="custom-security"></a>Zabezpieczenia niestandardowe

Szczególnie uważaj na "toczenia własnego" implementacji kryptografii, członkostwa użytkownika lub systemu generowania tokenów. Dostępnych jest wiele komercyjnych i otwartych alternatyw, które prawie na pewno będą miały lepsze zabezpieczenia niż implementacja niestandardowa.

> ### <a name="references--security"></a>Referencje — zabezpieczenia
>
> - **Omówienie dokumentów zabezpieczeń**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Wymuszanie ssl w aplikacji ASP.NET Core**  
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

Oprócz wyświetlania stron i odpowiadania na żądania dotyczące danych za pośrednictwem internetowych interfejsów API, aplikacje ASP.NET Core mogą komunikować się bezpośrednio z połączonymi klientami. Ta komunikacja wychodząca może korzystać z różnych technologii transportu, najczęściej jest WebSockets. ASP.NET Core SignalR to biblioteka, która ułatwia dodawanie funkcji komunikacji serwer-klient w czasie rzeczywistym do aplikacji. SignalR obsługuje różne technologie transportu, w tym WebSockets i abstrakcje od wielu szczegółów implementacji od dewelopera.

Komunikacja z klientem w czasie rzeczywistym, czy przy użyciu WebSockets bezpośrednio lub innych technik, są przydatne w różnych scenariuszach aplikacji. Oto niektóre przykłady:

- Aplikacje do czatu na żywo

- Monitorowanie aplikacji

- Aktualizacje postępu zadań

- Powiadomienia

- Interaktywne aplikacje formularzy

Podczas tworzenia komunikacji klienta do aplikacji, zazwyczaj istnieją dwa składniki:

- Menedżer połączeń po stronie serwera (SignalR Hub, WebSocketManager WebSocketHandler)

- Biblioteka po stronie klienta

Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się za pomocą SignalR / WebSockets. Następujący prosty program odzwierciedla wszystkie treści wysyłane do aplikacji czatu do konsoli, jako część aplikacji przykładowej WebSocketManager:

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

Należy wziąć pod uwagę sposoby, w jaki aplikacje komunikują się bezpośrednio z aplikacjami klienckimi i zastanów się, czy komunikacja w czasie rzeczywistym poprawi środowisko użytkownika aplikacji.

> ### <a name="references--client-communication"></a>Referencje – Komunikacja z klientem
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/dotnet/aspnetcore/tree/master/src/SignalR>
> - **Menedżer WebSocket**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Projektowanie oparte na domenie — czy należy go zastosować?

Domain-Driven Design (DDD) to elastyczne podejście do tworzenia oprogramowania, które kładzie nacisk na _domenę biznesową._ Kładzie duży nacisk na komunikację i interakcję z ekspertami domeny biznesowej, którzy mogą odnosić się do programistów, jak działa system w świecie rzeczywistym. Na przykład, jeśli budujesz system, który obsługuje transakcje giełdowe, Twój ekspert domeny może być doświadczonym brokerem giełdowym. DDD ma na celu rozwiązanie dużych, złożonych problemów biznesowych i często nie jest odpowiedni dla mniejszych, prostszych aplikacji, ponieważ inwestycja w zrozumienie i modelowanie domeny nie jest tego warta.

Podczas tworzenia oprogramowania zgodnie z podejściem DDD, twój zespół (w tym nietechniczne interesariusze i współautorzy) powinien opracować _wszechobecny język_ dla miejsca problemowego. Oznacza to, że ta sama terminologia powinna być używana do modelowania koncepcji świata rzeczywistego, odpowiednika oprogramowania i wszelkich struktur, które mogą istnieć, aby utrwalić koncepcję (na przykład tabele bazy danych). Tak więc pojęcia opisane w wszechobecnym języku powinny stanowić podstawę dla _modelu domeny._

Model domeny składa się z obiektów, które współdziałają ze sobą w celu reprezentowania zachowania systemu. Obiekty te mogą należeć do następujących kategorii:

- [Jednostki](https://deviq.com/entity/), które reprezentują obiekty z wątku tożsamości. Jednostki są zazwyczaj przechowywane w trwałości z kluczem, za pomocą którego można później pobrać.

- [Agreguje](https://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny być utrwalone jako jednostka.

- [Value objects](https://deviq.com/value-object/), które reprezentują pojęcia, które można porównać na podstawie sumy ich wartości właściwości. Na przykład DateRange składający się z daty rozpoczęcia i zakończenia.

- [Zdarzenia domeny,](https://martinfowler.com/eaaDev/DomainEvent.html)które reprezentują rzeczy dzieje się w systemie, które są interesujące dla innych części systemu.

Model domeny DDD powinien hermetyzować złożone zachowanie w modelu. Jednostki, w szczególności, nie powinny być jedynie zbiorami właściwości. Gdy model domeny brakuje zachowania i tylko reprezentuje stan systemu, mówi się, że [model anemiczny](https://deviq.com/anemic-model/), co jest niepożądane w DDD.

Oprócz tych typów modeli DDD zazwyczaj wykorzystuje różne wzorce:

- [Repozytorium](https://deviq.com/repository-pattern/), do abstrakcji szczegółów trwałości.

- [Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern), do hermetyzacji tworzenia obiektów złożonych.

- Zdarzenia domeny, oddzielenie zachowania zależnego od wyzwalania zachowania.

- [Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), do hermetyzacji złożonych zachowań i/lub szczegóły implementacji infrastruktury.

- [Polecenie](https://en.wikipedia.org/wiki/Command_pattern), do oddzielenia wydawania poleceń i wykonywania samego polecenia.

- [Specyfikacja](https://deviq.com/specification-pattern/), do hermetyzacji szczegółów kwerendy.

DDD zaleca również użycie Czystej architektury omówione wcześniej, co pozwala na luźne sprzężenie, hermetyzację i kod, które można łatwo zweryfikować za pomocą testów jednostkowych.

### <a name="when-should-you-apply-ddd"></a>Kiedy należy stosować DDD

DDD doskonale nadaje się do dużych zastosowań o znaczącej złożoności biznesowej (nie tylko technicznej). Aplikacja powinna wymagać wiedzy ekspertów w dziedzinie. Powinno istnieć znaczące zachowanie w samym modelu domeny, reprezentujące reguły biznesowe i interakcje poza po prostu przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych.

### <a name="when-shouldnt-you-apply-ddd"></a>Kiedy nie należy stosować DDD

DDD obejmuje inwestycje w modelowanie, architekturę i komunikację, które mogą nie być uzasadnione dla mniejszych aplikacji lub aplikacji, które są zasadniczo tylko CRUD (tworzenie / odczyt/ aktualizacja / usuwanie). Jeśli zdecydujesz się zbliżyć do aplikacji po DDD, ale okaże się, że domena ma model anemiczny bez zachowania, może być konieczne ponowne przemyślenie podejścia. Aplikacja może nie wymagać DDD lub może być potrzebna pomoc refaktoryzacji aplikacji do hermetyzacji logiki biznesowej w modelu domeny, a nie w bazie danych lub interfejsu użytkownika.

Podejście hybrydowe byłoby używać tylko DDD dla transakcyjnych lub bardziej złożonych obszarów aplikacji, ale nie dla prostszych crud lub tylko do odczytu części aplikacji. Na przykład nie musisz mieć ograniczeń agregacji, jeśli wysyłasz zapytania do danych, aby wyświetlić raport lub wizualizować dane dla pulpitu nawigacyjnego. Jest całkowicie dopuszczalne, aby mieć oddzielny, prostszy model odczytu dla takich wymagań.

> ### <a name="references--domain-driven-design"></a>Odwołania — projektowanie oparte na domenie
>
> - **DDD w prostym języku angielskim (StackOverflow Answer)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Wdrożenie

Istnieje kilka kroków związanych z procesem wdrażania aplikacji ASP.NET Core, niezależnie od tego, gdzie będzie hostowana. Pierwszym krokiem jest opublikowanie aplikacji, co `dotnet publish` można wykonać za pomocą polecenia CLI. Spowoduje to skompilowanie aplikacji i umieszczenie wszystkich plików potrzebnych do uruchomienia aplikacji w wyznaczonym folderze. Po wdrożeniu z programu Visual Studio ten krok jest wykonywany automatycznie. Folder publikowania zawiera pliki .exe i dll dla aplikacji i jej zależności. Samodzielna aplikacja będzie również zawierać wersję środowiska wykonawczego platformy .NET. ASP.NET Aplikacje Core będą również zawierać pliki konfiguracyjne, statyczne zasoby klienta i widoki MVC.

ASP.NET Aplikacje Core to aplikacje konsoli, które należy uruchomić po uruchomieniu serwera i ponownym uruchomieniu, jeśli aplikacja (lub serwer) ulegnie awarii. Menedżer procesów może służyć do automatyzacji tego procesu. Najczęstszymi menedżerami procesów dla ASP.NET Core są Nginx i Apache w systemie Linux i IIS lub Windows Service w systemie Windows.

Oprócz menedżera procesów aplikacje ASP.NET Core mogą używać serwera odwrotnego serwera proxy. Serwer odwrotnego serwera proxy odbiera żądania HTTP z Internetu i przekazuje je do Kestrel po wstępnej obsłudze. Serwery odwrotnego serwera proxy zapewniają warstwę zabezpieczeń aplikacji. Kestrel również nie obsługuje hostowania wielu aplikacji na tym samym porcie, więc techniki takie jak nagłówki hostów nie mogą być używane z nim, aby umożliwić hostowanie wielu aplikacji na tym samym porcie i adresie IP.

![Pustułka do Internetu](./media/image7-5.png)

**Rysunek 7-5**. ASP.NET hostowane w Kestrel za odwrotnym serwerem proxy

Innym scenariuszem, w którym odwrotny serwer proxy może być pomocny, jest zabezpieczenie wielu aplikacji przy użyciu protokołu SSL/HTTPS. W takim przypadku tylko odwrotny serwer proxy musiałby mieć skonfigurowany ssl. Komunikacja między serwerem odwrotnego serwera proxy a Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano na rysunku 7-6.

![ASP.NET hostowane za serwerem odwrotnego serwera proxy zabezpieczonego przez HTTPS](./media/image7-6.png)

**Rysunek 7-6**. ASP.NET hostowane za serwerem odwrotnego serwera proxy zabezpieczonego przez HTTPS

Coraz bardziej popularne podejście jest hostowanie aplikacji ASP.NET Core w kontenerze platformy Docker, które następnie mogą być hostowane lokalnie lub wdrażane na platformie Azure w celu hostingu opartego na chmurze. Kontener platformy Docker może zawierać kod aplikacji, uruchomiony na Kestrel i zostanie wdrożony za serwerem odwrotnego serwera proxy, jak pokazano powyżej.

Jeśli hostujesz aplikację na platformie Azure, możesz użyć bramy aplikacji platformy Microsoft Azure jako dedykowanego urządzenia wirtualnego, aby świadczyć kilka usług. Oprócz działania jako odwrotny serwer proxy dla poszczególnych aplikacji, Brama aplikacji może również oferować następujące funkcje:

- Równoważenie obciążenia HTTP

- Odciążanie SSL (SSL tylko do Internetu)

- SSL od końca do końca

- Routing wielomiejscowy (konsolidacja do 20 lokacji w jednej bramie aplikacji)

- Zapora aplikacji internetowej

- Pomoc techniczna aplikacji Websocket

- Zaawansowana diagnostyka

_Dowiedz się więcej o opcjach wdrażania platformy Azure w [rozdziale 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odwołania — wdrażanie
>
> - **Omówienie hostingu i wdrażania**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kiedy używać Kestrel z odwrotnym serwerem proxy**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostuj aplikacje ASP.NET Core w aplikacji Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Wprowadzenie bramy aplikacji platformy Azure**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Poprzedni](common-client-side-web-technologies.md)
>[następny](work-with-data-in-asp-net-core-apps.md)
