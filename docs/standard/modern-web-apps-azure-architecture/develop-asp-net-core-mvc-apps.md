---
title: Tworzenie aplikacji MVC ASP.NET Core
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Tworzenie aplikacji programu ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 59f0d46dadb736ad55e53f6715b7ca1b62e9cec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592408"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Tworzenie aplikacji MVC ASP.NET Core

> "Nie jest ważna uzyskać prawo po raz pierwszy. Jest zasadnicze znaczenie uzyskać prawo ostatniego."  
> _-Andrew Hunt i blogu Thomasa Dominik_

## <a name="summary"></a>Podsumowanie

Platformy ASP.NET Core to platforma i platform, open source do tworzenia nowoczesnych zoptymalizowanych pod kątem chmury aplikacji sieci web. Aplikacje platformy ASP.NET Core to lekkie i moduły z wbudowaną obsługą iniekcji zależności, włączanie w większej kontroli i łatwości konserwacji. Połączone z MVC, który obsługuje tworzenie nowoczesnych interfejsów API sieci web oprócz aplikacji opartych na widoku, platformy ASP.NET Core to platforma Zaawansowane umożliwiające tworzenie aplikacji sieci web organizacji.

## <a name="mapping-requests-to-responses"></a>Mapowania żądania do odpowiedzi

Centrum w aplikacji platformy ASP.NET Core żądania przychodzące są mapowane na wychodzące odpowiedzi. Na niskim poziomie jest to zrobić za pomocą oprogramowania pośredniczącego i proste aplikacje platformy ASP.NET Core i mikrousług może składać się wyłącznie z niestandardowych oprogramowania pośredniczącego. Podczas korzystania z platformy ASP.NET Core MVC, można pracować nieco wyższego poziomu, myśląc pod względem *tras*, *kontrolerów*, i *akcje*. Każde żądanie przychodzące jest porównywana z tabeli routingu aplikacji, a jeśli znaleziono pasującej trasy do żądania obsługi ma zostać wywołana metoda skojarzone z akcją (należących do kontrolera). Jeśli nie pasującej trasy zostanie znaleziony, program obsługi błędów (w tym przypadku zwracanie wyniku NotFound) jest wywoływana.

Trasy z konwencjonalnej i tras atrybutów, można użyć aplikacji MVC ASP.NET Core. Trasy z konwencjonalnej są zdefiniowane w kodzie, określając routingu *konwencje* przy użyciu składni, podobnie jak w poniższym przykładzie:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

W tym przykładzie dodano trasę o nazwie "domyślne" do tabeli routingu. Definiuje szablon trasy z symbole zastępcze *kontrolera*, *akcji*, i *identyfikator*. Symbole zastępcze kontroler i akcja ma określony domyślny ("Home" i "Index", odpowiednio), i identyfikator symbol zastępczy jest opcjonalne (na mocy niniejszej "?" zastosowane do niego). Konwencji zdefiniowane w tym miejscu stanów odpowiadających pierwsza część żądanie do nazwy kontrolera, a druga część do akcji, a następnie w razie potrzeby trzeciej części reprezentuje parametr id. Trasy z konwencjonalnej są zazwyczaj definiowane w jednym miejscu aplikacji, takich jak w metodzie Konfiguruj w klasie uruchamiania.

Tras atrybutów są stosowane bezpośrednio do kontrolerów i akcji, a nie określono globalnie. To ustawienie zaleta ich mogą znacznie szybciej odnajdywać rozważasz usługę konkretnej metody, ale oznacza, że informacje routingu nie są przechowywane w jednym miejscu w aplikacji. Atrybut trasy możesz można łatwo określić wiele tras dla danego działania, a także łączenia tras między kontrolerów i akcji. Na przykład:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

Można określić trasy [HttpGet] i oddziel podobne atrybutów, dzięki czemu nie trzeba dodać [trasy\] atrybutów. Tras atrybutów można także użyć tokenów, aby zmniejszyć trzeba powtórzyć nazwy kontrolera lub akcji, jak pokazano poniżej:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

Po danego żądania ma dopasowane do trasy, ale przed akcją metoda jest wywoływana, ASP.NET Core MVC będzie wykonywać [modelu powiązania](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) i [modelu weryfikacji](https://docs.microsoft.com/aspnet/core/mvc/models/validation) na żądanie. Wiązanie modelu jest odpowiedzialny za konwersji przychodzących danych protokołu HTTP do typów .NET określony jako parametry metody akcji do wywołania. Na przykład jeśli metoda akcji oczekuje parametru identyfikatora int, ten parametr z wartości w ramach żądania będzie podejmować wiązania modelu. Aby to zrobić, tworzenia powiązania modelu szuka wartości przesłanego formularza, wartości trasy, sama i wartości ciągu zapytania. Zakładając, że wartość identyfikatora zostanie znaleziony, zostanie przekonwertowany na liczbę całkowitą przed przekazaniem do metody akcji.

Po powiązaniu modelu, ale przed wywołaniem metody akcji występuje weryfikacji modelu. Weryfikacja modelu używa opcjonalnych atrybutów w typie modelu i pozwala zagwarantować, że obiekt modelu podana spełnia wymogi niektórych danych. Niektóre wartości mogą być określone jako wymagane lub ograniczone do niektórych długości lub zakresu numerycznego, itp. Jeśli zostaną określone atrybuty weryfikacji, ale modelu nie jest zgodna z ich wymaganiami, właściwość ModelState.IsValid będzie mieć wartość false, a zestaw reguł sprawdzania poprawności, które uległy awarii będzie dostępna do wysłania do klienta zgłoszenia żądania.

Jeśli korzystasz z weryfikacją modelu, należy zawsze Sprawdź, czy model jest prawidłowy, przed wykonaniem wszelkie zmiany stanu polecenia, aby upewnić się, że aplikacja nie jest uszkodzony przez nieprawidłowe dane. Można użyć [filtru](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) Aby uniknąć konieczności dodawania kodu to każda akcja. Filtry MVC ASP.NET Core umożliwiają o przechwytywaniu grup żądania, tak, aby wspólne zasady i kompleksowymi problemy, które mogą być stosowane na podstawie docelowego. Filtry można zastosować do poszczególnych działań, całe kontrolerów lub globalnie dla aplikacji.

Dla interfejsów API sieci web platformy ASP.NET MVC Core obsługuje [ *negocjowanie zawartości*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), dzięki czemu żądania określić, jak powinien być sformatowany odpowiedzi. W oparciu o nagłówki udostępnione w żądaniu, akcje zwracający dane sformatuje odpowiedzi w XML, JSON lub innego obsługiwanego formatu. Ta funkcja umożliwia tego samego interfejsu API do użycia przez wielu klientów z wymagań formatu danych.

> ### <a name="references--mapping-requests-to-responses"></a>Odwołania — mapowania żądania do odpowiedzi
> - **Routing do akcji kontrolera**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Wiązanie modelu** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **Weryfikacja modelu**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **filtry** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>Praca z zależnościami

Platformy ASP.NET Core ma wbudowaną obsługę i wewnętrznie sprawia, że użycie techniką [iniekcji zależności](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection). Iniekcji zależności to technika, który umożliwia luźne powiązanie między poszczególnymi częściami aplikacji. Im sprzężenia jest pożądane, ponieważ ułatwi do izolowania poszczególnych części aplikacji, co do testowania lub wymiany. Również powoduje mniej prawdopodobne, że zmiany w jednej części aplikacji będą miały wpływ nieoczekiwany gdzieś w aplikacji. Iniekcji zależności opiera się na zasadzie odwracanie zależności i często ma kluczowe znaczenie dla osiągnięcia zasady otwarty/zamknięty. Podczas obliczania działanie aplikacji z zależnościami, należy wziąć pod [statycznych przylepna](http://deviq.com/static-cling/) kodu zapachu i zapamiętać aphorism "[nowe jest sklejki](https://ardalis.com/new-is-glue)."

Statyczne przylepna występuje podczas wykonywania wywołań do metod statycznych klas lub dostępu do właściwości statycznych, które ma efekty uboczne ani zależności w infrastrukturze. Na przykład jeśli masz metodę, która wywołuje metody statycznej, który z kolei zapisuje do bazy danych, metodę jest ściśle powiązane z bazą danych. Wszystko, co dzieli tego wywołania bazy danych spowoduje przerwanie metodę. Testowanie tych metod jest bardzo trudne, ponieważ testy te wymagają komercyjnych mocking bibliotek mock statyczne wywołania, lub należy badać tylko z bazy danych testu w miejscu. Statyczne wywołania, które nie ma żadnych zależności od infrastruktury, zwłaszcza tych, które są całkowicie bezstanowych jest poprawna wywołań i nie mają wpływu na sprzężenia lub pola (poza sprzężenia kodu statyczne wywołania, sam).

Wielu deweloperów zrozumieć ryzyka przylepna statyczne i stan globalny, ale będzie nadal ściśle połączenie ich kod do implementacji określonego przez bezpośrednie wystąpienia. "Nowe jest sklejki" ma być przypomnieniem tego sprzężenia, a nie ogólne potępianiu stosowania słowo kluczowe new. Tak jak w przypadku wywołania metody statycznej nowych wystąpień typów, które zwykle mają bez zewnętrznych zależności nie ściśle sprzęgania kodu szczegóły implementacji lub utrudnić testowania. Jednak zawsze, gdy klasa zostanie uruchomiony, po prostu krótki chwilę potrwać należy wziąć pod uwagę, czy warto być zakodowane tego konkretnego wystąpienia w określonej lokalizacji, jeśli jest lepsze projekt, aby zażądać tego wystąpienia jako zależność.

### <a name="declare-your-dependencies"></a>Deklarowanie zależności

Platformy ASP.NET Core opiera się o metod i ich zależności, żądając jako argumenty zadeklarować klasy. Aplikacje ASP.NET są zwykle tworzone w klasie uruchomienia, które jest skonfigurowany do obsługi iniekcji zależności w kilku miejscach. Jeśli klasa uruchamiania konstruktora, mogą żądać zależności za pomocą konstruktora, w następujący sposób:

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

Klasa początkowa jest interesujące, że nie ma żadnych wymagań jawnego typu dla niego. Nie dziedziczy po klasie podstawowej specjalne uruchamiania, ani implementuje żadnych konkretnego interfejsu. Można określić konstruktora, lub nie, a następnie można określić dowolną liczbę parametrów w Konstruktorze można dowolnie. Po uruchomieniu hosta sieci web skonfigurowana dla aplikacji wywoła Klasa początkowa zostały informację, aby użyć i użyje do wypełnienia wszelkie zależności, wymaga Klasa początkowa iniekcji zależności. Oczywiście jeśli żądania parametrów, które nie są skonfigurowane w kontenerze usługi używane przez program ASP.NET Core otrzymasz wyjątek, ale tak długo, jak trzymać zależności kontenera zna, możesz poprosić o dowolnych znaków.

Iniekcji zależności jest wbudowana w aplikacji platformy ASP.NET Core prawo od początku, po utworzeniu wystąpienia uruchamiania. Nie zatrzymał istnieje dla klasy uruchamiania. Możesz również poprosić o zależności w metodzie konfiguracji:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices jest wyjątkiem to zachowanie; tylko jeden parametr typu IServiceCollection musi wykonać. Naprawdę nie musi obsługiwać iniekcji zależności, ponieważ z jednej strony jest odpowiedzialny za dodawanie obiektów w kontenerze usługi, a w drugim ma dostęp do wszystkich aktualnie skonfigurowanych usług za pomocą parametru IServiceCollection. W związku z tym można pracować z zależnościami zdefiniowana w kolekcji usług platformy ASP.NET Core w każdej części Klasa początkowa, żądając wymagane usługi, jako parametr lub z IServiceCollection w ConfigureServices.

> [!NOTE]
> Jeśli należy się upewnić, niektóre usługi są dostępne do własnej klasy uruchamiania, można je skonfigurować przy użyciu WebHostBuilder oraz sposób jej ConfigureServices.

Klasa początkowa jest model powinien strukturą innych części aplikacji platformy ASP.NET Core, kontrolerów z oprogramowaniem pośredniczącym filtrów do własnych usług. W każdym przypadku należy wykonać [jawne zależności zasady](http://deviq.com/explicit-dependencies-principle/)żąda zależności, a nie bezpośrednio ich tworzenia i wykorzystaniu iniekcji zależności w całej aplikacji. Należy zwrócić szczególną uwagę na jak i gdzie bezpośrednio wystąpienia implementacji, szczególnie usług i obiekty, które działają z infrastrukturą lub mieć skutki uboczne. Preferowane jest praca z obiektów abstrakcyjnych zdefiniowanych w aplikacji podstawowych i przekazane jako argumenty do hardcoding odwołania do typów konkretnej implementacji.

## <a name="structuring-the-application"></a>Struktura aplikacji

Aplikacje wbudowanymi zwykle mają jeden punkt wejścia. W przypadku aplikacji sieci web platformy ASP.NET Core punkt wejścia będą projektu sieci web platformy ASP.NET Core. Jednakże, który nie oznacza rozwiązania powinien składać się z jednego projektu. Warto podzielić aplikację do różnych warstw, aby wykonać separacji. Po podzielić się do warstwy, warto wykracza poza folderów do osobnych projektów, które mogą pomóc osiągnąć lepszą hermetyzacji. Najlepsze sposób na osiągnięcie tych celów z aplikacji platformy ASP.NET Core jest odmianą czystej architektury omówionych w rozdziale 5. Po tej metody rozwiązanie aplikacji będzie składać się z oddzielnych biblioteki interfejsu użytkownika, infrastruktury i ApplicationCore.

Oprócz tych projektów projekty testowe oddzielne uwzględniono również (testowanie opisanej w rozdziale 9).

Model obiektów i interfejsów aplikacji powinna zostać umieszczona w projekcie ApplicationCore. Ten projekt zostanie jako kilka zależności jak to możliwe, i innych projektów w rozwiązaniu będzie odwoływać się on. Jednostki biznesowe, które muszą zostać utrwalony są definiowane w projekcie ApplicationCore są usług, które nie zależą bezpośrednio infrastruktury.

Szczegóły implementacji, takie jak realizację trwałości lub jak powiadomienia zostaną wysłane do użytkownika, są przechowywane w projekcie infrastruktury. Ten projekt będzie odwoływać się do konkretnej implementacji pakiety, takie jak Entity Framework Core, ale nie powinny ujawniać szczegółowe informacje o tych implementacji poza projektem. Usługi infrastruktury oraz repozytoria powinien implementować interfejsów, które są zdefiniowane w projekcie ApplicationCore i ich implementacji trwałości są odpowiedzialne za odczytywanie i zapisywanie jednostek zdefiniowanych w ApplicationCore.

Projekt interfejsu użytkownika programu ASP.NET Core jest odpowiedzialny za wszelkie problemy dotyczące do poziomu interfejsu użytkownika, ale nie może zawierać szczegóły infrastruktury i logiki biznesowej. W rzeczywistości w idealnym przypadku nie powinny nawet ona zależności w projekcie infrastruktury, co pomoże upewnij się, że przypadkowo wprowadzono nie zależności między dwa projekty. Można to osiągnąć przy użyciu kontenera Podpisane innych firm, takich jak StructureMap, dzięki czemu można zdefiniować reguły Podpisane w klasach rejestru w każdym projekcie.

Innym sposobem oddzielenia aplikacji od szczegóły implementacji jest mikrousług wywołania aplikacji, możliwe, że wdrożone w poszczególnych kontenerach Docker. Rozdzielenie lepsze problemy i oddzielenie niż wykorzystaniu Podpisane między dwa projekty, ale ma stopnia złożoności.

### <a name="feature-organization"></a>Funkcja organizacji

Domyślnie aplikacje platformy ASP.NET Core organizowanie struktury ich folderów kontrolery i widoki i często ViewModels. Kod po stronie klienta do obsługi tych struktur po stronie serwera jest zwykle przechowywane oddzielnie w folderze wwwroot. Jednak dużych aplikacji mogą wystąpić problemy z daną organizacją, ponieważ pracy z dowolnej funkcji danego często wymaga przechodzenie między folderami te. Pobiera to bardziej trudne, wraz z rozwojem liczbę plików i podfolderów znajdujących się w każdym folderze, co zapewnia w dużym stopniem przewijanie w Eksploratorze rozwiązań. Jedno rozwiązanie tego problemu jest zorganizowanie kodu aplikacji przez *funkcji* zamiast według typu pliku. Ten styl organizacji jest zazwyczaj zwane foldery funkcji lub funkcja wycinków (Zobacz też: [pionowy wycinków](http://deviq.com/vertical-slices/)).

ASP.NET Core MVC obsługuje obszary, w tym celu. Obszary można utworzyć oddzielne zestawy kontrolery i widoki folderów (a także żadnych modeli skojarzone) w każdym folderze obszaru. Przykład struktury folderów, za pomocą obszarów przedstawiono na rysunku 7-1.

![](./media/image7-1.png)

Rysunek 7-1 próbka obszaru organizacji

Korzystając z obszarów, należy użyć do dekoracji kontrolerów z nazwę obszaru, do którego należą te atrybuty:

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

Oprócz wbudowanych wsparcia dla obszarów umożliwia także własne struktury folderów i konwencje zamiast atrybutów i trasy niestandardowe. Umożliwi to foldery funkcji, które nie obejmują osobne foldery widoki, kontrolery, itp., pamiętając płaska hierarchii i ułatwiając zobaczyć wszystkie powiązane pliki w jednym miejscu dla każdej funkcji.

Platformy ASP.NET Core używa konwencji wbudowanych typów kontrolowanie swojego zachowania. Można zmodyfikować lub Zastąp te Konwencji. Na przykład można utworzyć Konwencji, który będzie automatycznie pobrać nazwy funkcji dla danego kontrolera oparte na przestrzeń nazw (która zazwyczaj są powiązane z folderu, w którym znajduje się kontroler):

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

Następnie możesz określić tę Konwencję jako opcja po dodaniu obsługi MVC dla aplikacji w ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

Platformy ASP.NET Core MVC również używa konwencji zlokalizować widoki. Można zastąpić go z Konwencją niestandardowe, aby widoki będą znajdować się w folderach funkcji (przy użyciu nazwy funkcji podanego przez FeatureConvention powyżej). Można dowiedzieć się więcej na temat tej metody i pobrać przykładowy pracy z artykuł w witrynie MSDN [wycinków funkcji dla platformy ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Dotyczy kompleksowymi

Wzrostem aplikacji staje się coraz bardziej ważne składników wychodzących kompleksowymi problemy, aby wyeliminować dublowania i zachowanie spójności. Przykłady kompleksowymi problemy w aplikacji platformy ASP.NET Core to uwierzytelnianie, reguł sprawdzania poprawności modelu, buforowanie danych wyjściowych i obsługi błędu, jeśli istnieje wiele innych. Platformy ASP.NET Core MVC [filtry](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) zezwalają na uruchamianie kodu przed lub po pewne czynności w potoku przetwarzania żądań. Na przykład filtr można uruchomić przed i po wiązania modelu, przed i po akcji lub przed i po wyniku akcji. Umożliwia także filtr autoryzacji do kontrolowania dostępu do pozostałego potoku. Pokazuje rysunki 7-2 jak żądanie wykonania przepływów filtry, skonfigurowanie.

![Żądanie jest przetwarzane za pośrednictwem filtry autoryzacji, filtrów zasobów powiązania modelu, filtry akcji, wykonywanie akcji i konwersji wynik akcji, filtry wyjątków, filtry wyników i wykonania wyniku. W drodze limit żądania jest przetwarzany tylko przez filtry wyników i filtry zasobów aby stać się odpowiedzi wysyłane do klienta.](./media/image7-2.png)

Rysunek 7-2 wykonywania żądania za pomocą filtrów i żądania potoku.

Filtry zwykle są zaimplementowane jako atrybuty, aby można było zastosować je kontrolerów i akcji. Po dodaniu w taki sposób, filtry określone na zastąpienie poziomie akcji lub kompilacji na filtrów z określonego na poziomie kontrolera, które same zastąpić filtry globalne. Na przykład \[trasy\] atrybut może służyć do zbudowania tras między kontrolerów i akcji. Podobnie autoryzacji można konfigurować na poziomie kontrolera i następnie zastąpione przez poszczególne działania, jak w poniższym przykładzie pokazano:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

Pierwsza metoda logowania, używa filtra AllowAnonymous (atrybut) do przesłonięcia filtr autoryzacji, należy ustawić na poziomie kontrolera. Akcja ForgotPassword (i innych działań w klasie, która nie ma atrybutu AllowAnonymous) wymaga uwierzytelnionego żądania.

Filtry można wyeliminować dublowanie w postaci typowych obsługę błędów zasady dla interfejsów API. Na przykład typowa zasad interfejsu API jest do zwrócenia NotFound odpowiedzi na żądania PRZYWOŁUJĄCE klucze, które nie istnieją, a element BadRequest odpowiedzi w przypadku niepowodzenia weryfikacji modelu. W poniższym przykładzie pokazano tych dwóch zasad, w akcji:

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

Nie zezwalaj z metody akcji zapełnić warunkowego kodu następująco. Zamiast tego należy pobierać zasady do filtrów, które mogą być stosowane w zgodnie z potrzebami. W tym przykładzie sprawdzenie poprawności modelu, który powinna wystąpić zawsze, gdy polecenie są wysyłane do interfejsu API, może być zastąpiony następującego atrybutu:

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

Podobnie filtr może służyć do sprawdzenia, czy rekord istnieje i zwróć 404, przed wykonaniem akcji, eliminując konieczność wykonania tych testów w akcji. Po pobierane limit typowych konwersji i zorganizowane rozwiązanie, aby oddzielić infrastruktury kodu i logiki biznesowej w Interfejsie użytkownika, MVC metody akcji powinny być bardzo elastycznej:

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Więcej o implementacji filtry i pobrać przykładowy pracy z artykuł w witrynie MSDN [rzeczywistych World platformy ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Odwołania — struktury aplikacji
> - **Obszary**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN — wycinków funkcji podstawowych programu ASP.NET MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN — rzeczywistych platformy ASP.NET Core MVC filtry**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpieczenia

Zabezpieczanie aplikacji sieci web jest duża tematu, z wiele kwestii. Na najbardziej podstawowym poziomie zabezpieczeń obejmuje zapewnienie, że wiesz, kto pochodzące z danego żądania i zapewnienie, że żądanie ma dostęp tylko do zasobów, które powinno. Uwierzytelnianie to proces porównanie poświadczenia dostarczone z żądaniem w zaufanym magazynie danych, aby zobaczyć, czy żądanie powinny być traktowane jako pochodzący od znanych jednostek. Autoryzacja jest przez proces ograniczania dostępu do niektórych zasobów na podstawie tożsamości użytkownika. Trzeci problem dotyczący zabezpieczeń chroni żądań podsłuchiwaniu przez osoby trzecie, dla których należy co najmniej [upewnij się, że protokół SSL jest używany przez aplikację](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Uwierzytelnianie

Tożsamość platformy ASP.NET Core to system członkostwa, używanych do obsługi funkcji logowania dla aplikacji. Ma ona Obsługa kont użytkowników lokalnych, a także Obsługa dostawcy logowania zewnętrznego od dostawców, takich jak Microsoft Account, Twitter, Facebook i Google. Oprócz ASP.NET Core Identity, aplikacja może używać uwierzytelniania systemu windows lub dostawca tożsamości innych firm, takich jak [tożsamości serwera](https://github.com/IdentityServer/IdentityServer4).

Tożsamość platformy ASP.NET Core znajduje się w nowych szablonów projektu, jeśli wybrano opcję indywidualnych kont użytkowników. Ten szablon obejmuje obsługę rejestracji i logowania, logowań zewnętrznych, zapomniane hasła oraz dodatkowe funkcje.

![](./media/image7-3.png)

Rysunek 7-3 Wybierz indywidualne konta użytkowników do ma tożsamość wstępnie.

Obsługa tożsamości jest konfigurowana w uruchamiania, zarówno w ConfigureServices i konfiguracji:

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

Jest ważne, czy UseIdentity są wyświetlane przed UseMvc w metodzie Konfigurowanie. W przypadku konfigurowania tożsamości w ConfigureServices, można zauważyć wywołania AddDefaultTokenProviders. To nie ma nic wspólnego z tokenów, które mogą służyć do zabezpieczenia komunikacji w sieci web, ale zamiast tego odwołuje się do dostawcy, które utworzyć monity, które mogą być wysyłane do użytkowników za pośrednictwem programu SMS lub wiadomości e-mail w kolejności ich, aby potwierdzić swoją tożsamość.

Możesz dowiedzieć się więcej [konfigurowania uwierzytelniania dwuskładnikowego](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) i [włączania dostawcy logowania zewnętrznego](https://docs.microsoft.com/aspnet/core/security/authentication/social/) z oficjalna dokumentacja platformy ASP.NET Core.

### <a name="authorization"></a>Autoryzacja

Najprostsza forma autoryzacji obejmuje ograniczania dostępu do użytkowników anonimowych. Można to osiągnąć poprzez zastosowanie po prostu \[autoryzacji\] atrybutu niektórych kontrolerach ani akcji. Role są używane, ten atrybut może dodatkowo rozszerzona ograniczyć dostęp do użytkowników, którzy należą do określonych ról, jak pokazano:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

W takim przypadku użytkowników należących do ról HRManager lub not (lub obie) będzie mieć dostęp do SalaryController. Aby wymagać, że użytkownik należy do wielu ról (nie tylko jeden z kilku), można zastosować atrybutu wielokrotnie, określenie wymaganej roli zawsze.

Określanie niektóre zestawy role jako ciągi w wielu różnych kontrolerów i akcji może prowadzić do niepożądanych powtarzania. Można skonfigurować zasady autoryzacji, które hermetyzują reguł autoryzacji, a następnie określ zasady zamiast poszczególnych ról, podczas stosowania \[autoryzacji\] atrybutu:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

W ten sposób za pomocą zasad, można oddzielić rodzaje działań jest ograniczony z określonych ról lub reguły, które mają zastosowanie do niej. Później, jeśli tworzysz nową rolę, która musi mieć dostęp do niektórych zasobów można tylko aktualizować zasady, a nie aktualizacji co lista ról na każdym \[autoryzacji\] atrybutu.

#### <a name="claims"></a>Oświadczenia

Oświadczenia są par wartości nazw, które reprezentują właściwości uwierzytelnionego użytkownika. Na przykład może przechowywać numer pracownika użytkowników jako oświadczenia. Następnie można oświadczeń jako część zasad autoryzacji. Można utworzyć zasadę o nazwie "EmployeeOnly" wymaga istnienia oświadczenie o nazwie "NumerPracownika", jak pokazano w poniższym przykładzie:

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

Ta zasada może być użyta z \[autoryzacji\] atrybut, aby chronić kontrolera i/lub akcji, jak opisano powyżej.

#### <a name="securing-web-apis"></a>Zabezpieczanie interfejsów API sieci Web

Większość interfejsów API sieci web należy zaimplementować uwierzytelnianie oparte na token systemu. Token uwierzytelniania jest bezstanowe i skalowalne zaprojektowane. W systemie uwierzytelniania opartego na tokenie klient muszą najpierw uwierzytelnić się z dostawcą uwierzytelniania. Jeśli to się powiedzie, klient wystawił token, to po prostu kryptograficznie znaczący ciąg znaków. Gdy klient następnie musi wysłać żądania do interfejsu API, dodaje ten token jako nagłówka w żądaniu. Następnie serwer weryfikuje token w nagłówku żądania znaleziono przed wykonaniem żądania. Rysunek 7-4 przedstawiono ten proces.

![TokenAuth](./media/image7-4.png)

**Rysunek 7-4.** Token uwierzytelniania dla interfejsów API sieci Web.

> ### <a name="references--security"></a>Odwołania — zabezpieczeń
> - **Omówienie dokumentów dotyczących zabezpieczeń**  
> https://docs.microsoft.com/aspnet/core/security/
> - **Wymuszanie protokołu SSL w aplikacji platformy ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Wprowadzenie do tożsamości**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Wprowadzenie do autoryzacji**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Uwierzytelnianie i autoryzacja aplikacji interfejsu API w usłudze aplikacji Azure**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>Komunikacja klienta

Oprócz obsługująca stron i odpowiada na żądania danych za pośrednictwem interfejsów API sieci web, aplikacje platformy ASP.NET Core może komunikować się bezpośrednio z połączonych klientów. Tej komunikacji wychodzącej można użyć różnych technologii transportu jest najbardziej typowych Websocket. SignalR platformy ASP.NET Core to biblioteki, która ułatwia dodawanie w czasie rzeczywistym komunikacji klient serwera funkcji do aplikacji. SignalR obsługuje wiele technologii transportu, w tym Websocket i abstracts wielu zadań szczegóły implementacji od dewelopera.

SignalR platformy ASP.NET Core jest obecnie opracowywane i będą dostępne w następnej wersji platformy ASP.NET Core. Jednak inne [otworzyć źródła Websocket biblioteki](https://github.com/radu-matei/websocket-manager) są obecnie dostępne.

Komunikacja z klientem w czasie rzeczywistym, czy przy użyciu protokołu WebSockets bezpośrednio lub innych technik są przydatne w różnych scenariuszach. Oto kilka przykładów:

-   Aplikacje na żywo pokoju rozmów

-   Monitorowanie aplikacji

-   Aktualizacje postępu zadania

-   Powiadomienia

-   Interaktywne formularze aplikacji

Podczas kompilowania komunikacji z klientem w aplikacji, są zazwyczaj dwa składniki:

-   Menedżer połączeń po stronie serwera (koncentratora SignalR, WebSocketManager WebSocketHandler)

-   Biblioteka klienta

Klienci nie są ograniczone do przeglądarek — aplikacje mobilne, aplikacje konsoli i inne aplikacje natywne mogą również komunikować się za pomocą SignalR/Websocket. Następujący program proste echa całą zawartość wysyłane do aplikacji rozmów w konsoli jako część WebSocketManager przykładową aplikację:

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
```

Należy rozważyć wystąpić sposoby, w których aplikacji komunikują się bezpośrednio z aplikacji klienckich i należy wziąć pod uwagę, czy w czasie rzeczywistym komunikacji poprawiające użytkownika aplikacji.

> ### <a name="references--client-communication"></a>Odwołania — komunikacji z klientem
> - **SignalR platformy ASP.NET Core**  
> <https://github.com/aspnet/SignalR>
> - **Menedżer protokołu WebSocket**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Domeny oparte na projektowanie — powinien zastosowaniu?

Projektowanie oparte na domenie (DDD) jest elastyczne podejście do tworzenia oprogramowania, które jest kładzie nacisk koncentrujących się na *domeny business*. Umieszcza duże nacisk położono na komunikację i interakcji z expert(s) domeny biznesowe, które można powiązać z deweloperów, jak działa system rzeczywistych. Na przykład jeśli tworzysz systemu, który obsługuje standardowych transakcji ekspert Twojej domeny może być doświadczonym brokera standardowych. DDD zaprojektowano w celu rozwiązania problemów biznesowych dużych, złożonych i często nie jest odpowiedni dla aplikacji mniejszych, prostszy, inwestycji w opis i modelowanie domeny nie jest warto go.

Podczas tworzenia oprogramowania następujące podejście DDD, zespołu (w tym nietechnicznych uczestnikom projektu i współautorzy) należy opracować *powszechny języka* miejsce problem. Oznacza to należy używać tej samej terminologii koncepcji rzeczywistych modelowanego, odpowiednik oprogramowania i wszelkich struktur, które może istnieć, aby utrwalić koncepcji (na przykład tabel bazy danych). W związku z tym pojęcia opisane w języku powszechny powinny być podstawą dla Twojego *modelu domeny*.

Model domeny obejmuje obiekty, które współdziałają ze sobą do reprezentowania zachowanie systemu. Te obiekty mogą można podzielić na następujące kategorie:

-   [Jednostki](http://deviq.com/entity/), które reprezentują obiektów z wątkiem tożsamości. Jednostki są zwykle przechowywany w trwałości za pomocą klucza za pomocą którego mogą później zostać pobrane.

-   [Agreguje](http://deviq.com/aggregate-pattern/), które reprezentują grupy obiektów, które powinny zostać utrwalony jako jednostka.

-   [Wartość obiektów](http://deviq.com/value-object/), które reprezentują pojęcia, które można porównać na podstawie sumy wartości właściwości. Na przykład DateRange składające się z datę początkową i końcową.

-   [Zdarzenia domeny](https://martinfowler.com/eaaDev/DomainEvent.html), które reprezentują czynności wykonywane w ramach systemu, które mogą być przydatne do innych części systemu.

Należy pamiętać, że model domeny DDD zalecaną zachowanie złożonego w modelu. Jednostki, w szczególności, nie tylko należy kolekcji właściwości. Gdy model domeny nie ma zachowania, a jedynie reprezentuje stan systemu, jest określany jako [anemic modelu](http://deviq.com/anemic-model/), która jest niepożądanych w DDD.

Oprócz tych typów wzór DDD zwykle wdraża różnych wzorców:

-   [Repozytorium](http://deviq.com/repository-pattern/), dla abstrakcyjność szczegółów trwałości.

-   [Fabryka](https://en.wikipedia.org/wiki/Factory_method_pattern), dla hermetyzując Tworzenie obiektów złożonych.

-   Zdarzenia domeny dla oddzielenie zachowanie zależne od wyzwalania zachowanie.

-   [Usługi](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)dla hermetyzowany zachowanie złożone i/lub szczegóły implementacji infrastruktury.

-   [Polecenie](https://en.wikipedia.org/wiki/Command_pattern)dla oddzielenie wydawania polecenia i wykonywania samo polecenie.

-   [Specyfikacja](http://deviq.com/specification-pattern/), dla zawierający szczegóły zapytania.

DDD również zalecane jest stosowanie czystej architektury omówionych wcześniej, co pozwala na luźne powiązanie, hermetyzacji i kod, który łatwo można sprawdzić za pomocą testów jednostkowych.

### <a name="when-should-you-apply-ddd"></a>Kiedy należy zastosować DDD

DDD jest dobrze nadaje się do dużych aplikacji z złożoności firma (nie tylko technicznych). Aplikacja powinna wymagać wiedzy ekspertów domeny. Model domeny, reprezentujący reguł biznesowych i interakcje poza po prostu przechowywanie i pobieranie bieżącego stanu różnych rekordów z magazynów danych powinna mieć znaczący zachowanie.

### <a name="when-shouldnt-you-apply-ddd"></a>Kiedy nie należy zastosować DDD

DDD obejmuje inwestycje w modelowania, architektura i komunikacji, który nie może być uzasadnione dla mniejszych aplikacji lub aplikacji, które są po prostu CRUD (Tworzenie/odczytu/aktualizowania/usuwania). Jeśli użytkownik chce podejścia aplikacji po DDD, ale okazać, że domena ma anemic modelu i nie może być konieczne przemyślenia swoje podejście. Aplikacja nie może być konieczne DDD albo może być potrzebna pomoc refaktoryzacji hermetyzowania logiki biznesowej w modelu domeny, a nie z bazy danych lub interfejsu użytkownika aplikacji.

Rozwiązanie hybrydowe byłoby do użycia tylko DDD obszarów transakcyjnej lub bardziej złożonych aplikacji, ale nie prostsze CRUD lub tylko do odczytu części aplikacji. Na przykład nie musi mieć ograniczenia agregacji, jeśli jest kwerendy danych, aby wyświetlić raport lub do wizualizacji danych dla pulpitu nawigacyjnego. Jest całkowicie dopuszczalne mają oddzielne, prostszy model odczytu dla tych wymagań.

> ### <a name="references--domain-driven-design"></a>Odwołania — projektowanie oparte na domenie
> - **DDD w zwykły język angielski (StackOverflow odpowiedzi)**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>wdrażania

Obejmuje kilka czynności w procesie wdrożenia aplikacji platformy ASP.NET Core, niezależnie od tego, w którym będzie hostowana. Pierwszym krokiem jest, aby opublikować aplikację, można to zrobić przy użyciu dotnet publikowania polecenia interfejsu wiersza polecenia. Spowoduje to skompilować aplikację i umieść wszystkie pliki potrzebne do uruchomienia aplikacji do wskazanego folderu. Podczas wdrażania w programie Visual Studio, wykonanie tego kroku można automatycznie. Folder publikowania zawiera pliki .exe i dll dla aplikacji i jej zależności. Aplikację autonomiczną zawiera również wersję środowiska uruchomieniowego .NET. Aplikacje platformy ASP.NET Core będą także obejmować widoków MVC, zasoby statyczne klienta i pliki konfiguracji.

Aplikacje platformy ASP.NET Core są aplikacji konsoli, które musi zostać uruchomiony, gdy serwer jest uruchamiany oraz ponownego uruchomienia, jeśli wystąpiła awaria aplikacji (lub serwera). Menedżer procesu może służyć do automatyzacji tego procesu. Najbardziej typowe menedżerów procesu ASP.NET Core to Nginx i Apache na systemie Linux oraz usług IIS lub usługi systemu Windows w systemie Windows.

Oprócz menedżerem procesu aplikacji platformy ASP.NET Core znajdującej się na serwerze sieci web Kestrel należy użyć serwera zwrotnego serwera proxy. Zwrotnego serwera proxy odbiera żądania HTTP z Internetem i przekazuje je do Kestrel po niektórych wstępne obsługi. Serwery zwrotny serwer proxy zapewniają warstwę zabezpieczeń dla aplikacji i są wymagane dla wdrożeń krawędzi (ujawniony na ruch z Internetu). Kestrel jest względnie nowe i jeszcze nie zapewnia ochronę przed atakami niektórych. Kestrel nie obsługuje również obsługi wielu aplikacji na tym samym porcie, więc technik, takich jak nagłówki hosta nie można jej używać z nią do włączenia obsługi wielu aplikacji na tym samym port i adres IP.

![Kestrel do Internetu](./media/image7-5.png)

Rysunek 7-5 ASP.NET hostowane w Kestrel za serwerem proxy wstecznego

Inny scenariusz, w którym mogą być pomocne zwrotny serwer proxy jest zapewnienie wiele aplikacji przy użyciu protokołu SSL i HTTPS. W takim przypadku tylko zwrotny serwer proxy należy skonfigurować protokół SSL. Komunikacja między zwrotnego serwera proxy i Kestrel może odbywać się za pośrednictwem protokołu HTTP, jak pokazano w rysunek 7-6.

![](./media/image7-6.png)

Rysunek 7-6 ASP.NET hostowanej za zabezpieczone HTTPS zwrotnego serwera proxy

Jest coraz bardziej popularne podejście do hostowania aplikacji platformy ASP.NET Core w kontenerze Docker, który następnie może być przechowywana lokalnie lub wdrożeniu na platformie Azure opartej na chmurze hostingu. Kontener Docker mogą zawierać kod aplikacji uruchomionych na Kestrel i czy można wdrożyć za serwerem proxy odwrotnej zgodnie z powyższym.

Jeśli przechowujesz aplikacji na platformie Azure, można bramę aplikacji usługi Microsoft Azure jako dedykowane urządzenie wirtualne udostępniają kilka usług. Oprócz działający jako zwrotny serwer proxy dla poszczególnych aplikacji, bramy aplikacji może również oferują następujące funkcje:

-   Równoważenie obciążenia HTTP

-   Odciążanie protokołu SSL (SSL tylko do Internetu)

-   Kompleksowe SSL

-   Routing w wielu lokacjach (maksymalnie 20 Lokacje w jednej bramie aplikacji konsolidacji)

-   Zapora aplikacji sieci Web

-   Obsługa protokołu Websocket

-   Zaawansowane diagnostyki

*Dowiedz się więcej na temat opcji wdrożenia usługi Azure w rozdziale 10.*

> ### <a name="references--deployment"></a>Odwołania — wdrożenia
> - **Omówienie wdrożenia i obsługi**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kiedy należy używać Kestrel z zwrotny serwer proxy**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Host aplikacji platformy ASP.NET Core w Docker**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Wprowadzenie do bramy aplikacji Azure**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[Poprzednie] (typowe klienta-po stronie web-technologies.md) [dalej] (work-with-data-in-asp-net-core-apps.md)
