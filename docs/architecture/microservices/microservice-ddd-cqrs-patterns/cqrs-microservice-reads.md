---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z implementacją zapytania CQRS na mikrousłudze porządkowania w eShopOnContainers przy użyciu Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 6541a0cb7ce8ac3946e119483308d91158bdb522
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094064"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementowanie operacji odczytu/zapytań w CQRS mikrousługi

W przypadku operacji odczytu/zapytań, mikrousługa porządkowania z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego. Zostało to zrobione przede wszystkim dlatego, że wymagania dotyczące zapytań i transakcji są znacząco inne. Zapisuje transakcje wykonania, które muszą być zgodne z logiką domeny. Zapytania, z drugiej strony, są idempotentne i mogą być segregowane z reguł domeny.

Podejście jest proste, jak pokazano na rysunku 7-3. Interfejs API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak relacyjne mapowanie mikroobiektu (ORM), takie jak Dapper, i zwracanie dynamicznego modele widoków w zależności od potrzeb aplikacji interfejsu użytkownika.

![Najprostszym podejściem do wykonywania zapytań w uproszczonym podejściu CQRS może być implementacja przez samo wykonanie zapytania dotyczącego bazy danych przy użyciu mikroorm, na przykład Dapper, zwrócenie dynamicznego modele widoków.](./media/image3.png)

**Rysunek 7-3**. Najprostszym podejściem do wykonywania zapytań w mikrousłudze CQRS

Jest to najprostsza możliwa Metoda dla zapytań. Definicje zapytania zapytania do bazy danych i zwracają dynamiczny ViewModel zbudowany na bieżąco dla każdego zapytania. Ponieważ zapytania są idempotentne, nie zmieniają danych niezależnie od tego, ile razy zostało uruchomione zapytanie. W związku z tym nie trzeba ograniczać się przez żaden wzorzec DDD używany w stronie transakcyjnej, taki jak agregacje i inne wzorce, a także to, dlaczego zapytania są oddzielone od obszaru transakcyjnego. Po prostu wysyłasz zapytanie do bazy danych o dane wymagane przez interfejs użytkownika i zwracają dynamiczny ViewModel, który nie musi być statycznie zdefiniowany w dowolnym miejscu (brak klas dla modele widoków), z wyjątkiem samych instrukcji SQL.

Ponieważ jest to proste podejście, kod wymagany dla strony zapytania (na przykład kod korzystający z mikroorm like [Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w ramach tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Przedstawiono to na rysunku 7-4. Zapytania są definiowane w projekcie **porządkowania. API** mikrousług w ramach rozwiązania eShopOnContainers.

![Widok Eksplorator rozwiązań projektu porządkowania. API, pokazujący folder > zapytań aplikacji.](./media/image4.png)

**Rysunek 7-4**. Zapytania w mikrousłudze porządkowania w eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Używaj modele widoków określonych dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być przeznaczony dla klientów na podstawie danych zwróconych przez zapytania. Te modele lub Transfer danych obiekty (DTO) są nazywane modele widoków.

Zwrócone dane (ViewModel) mogą wynikać z dołączania danych z wielu jednostek lub tabel w bazie danych, a nawet wielu agregacji zdefiniowanych w modelu domeny dla obszaru transakcyjnego. W tym przypadku, ponieważ tworzysz zapytania niezależnie od modelu domeny, zagregowane granice i ograniczenia są całkowicie ignorowane i można wysyłać zapytania do dowolnej tabeli i kolumny, które mogą być potrzebne. Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzących lub aktualizujących zapytania.

Modele widoków mogą być typami statycznymi zdefiniowanymi w klasach. Lub mogą być tworzone dynamicznie na podstawie zapytań wykonanych (zgodnie z implementacją mikrousługi porządkowania), które są bardzo elastyczne dla deweloperów.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Używanie Dapper jako mikroorm do wykonywania zapytań

Do wykonywania zapytań można użyć dowolnego mikroorm, Entity Framework Core lub nawet zwykłego ADO.NET. W przykładowej aplikacji Dapper został wybrany dla mikrousługi porządkowania w eShopOnContainers jako dobry przykład popularnego mikroorm. Może uruchamiać zwykłe zapytania SQL o doskonałej wydajności, ponieważ jest to bardzo lekka struktura. Za pomocą Dapper można napisać zapytanie SQL, które może uzyskać dostęp do wielu tabel i dołączyć do nich.

Dapper to projekt typu "open source" (oryginalny utworzony przez sam Saffron) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/). Aby korzystać z Dapper, wystarczy zainstalować go za pomocą [pakietu NuGet Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:

![Pakiet Dapper wyświetlany w widoku Zarządzanie pakietami NuGet w programie VS.](./media/image4.1.png)

Należy również dodać instrukcję using, aby kod miał dostęp do metod rozszerzenia Dapper.

W przypadku używania Dapper w kodzie należy bezpośrednio użyć klasy <xref:System.Data.SqlClient.SqlConnection> dostępnej w przestrzeni nazw <xref:System.Data.SqlClient>. Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerzają klasę <xref:System.Data.SqlClient.SqlConnection>, można po prostu uruchamiać zapytania w sposób prosty i wydajny.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczny a statyczny modele widoków

Po powrocie modele widoków z serwera do aplikacji klienckich można myśleć o tych modele widoków jako DTO (Transfer danych obiektów), które mogą być różne dla wewnętrznych jednostek domeny modelu jednostki, ponieważ modele widoków przechowuje dane w sposób, w jaki aplikacja kliencka konieczne. Z tego względu w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i precyzyjnie redagować modele widoków według sposobu, w jaki aplikacja kliencka wymaga tych danych.

Te modele widoków lub DTO mogą być zdefiniowane jawnie (jako klasy posiadaczy danych), takie jak Klasa `OrderSummary` pokazana w późniejszym fragmencie kodu lub po prostu zwracają dynamiczne modele widoków lub dynamiczne DTO na podstawie atrybutów zwracanych przez zapytania jako typ dynamiczny.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typ dynamiczny

Jak pokazano w poniższym kodzie, wartość `ViewModel` może być zwracana bezpośrednio przez zapytania przez zwrócenie samego typu *dynamicznego* , który wewnętrznie opiera się na atrybutach zwracanych przez zapytanie. Oznacza to, że podzbiór atrybutów do zwrócenia jest oparty na zapytaniu. W związku z tym, jeśli dodasz nową kolumnę do zapytania lub sprzężenia, dane te są dynamicznie dodawane do zwróconego `ViewModel`.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

Ważnym punktem jest to, że za pomocą typu dynamicznego, zwrócona kolekcja danych jest dynamicznie zmontowany jako ViewModel.

**Specjaliści:** Takie podejście zmniejsza konieczność modyfikacji statycznych klas ViewModel za każdym razem, gdy aktualizujesz zdanie SQL zapytania, dzięki czemu ten projekt podejścia jest dość Agile podczas kodowania, bezpośrednie i szybkiej ewolucji w odniesieniu do przyszłych zmian.

**Wady:** W długim okresie typy dynamiczne mogą mieć negatywny wpływ na przejrzystość i zgodność usługi z aplikacjami klienckimi. Ponadto oprogramowanie pośredniczące, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji dla zwracanych typów, jeśli są używane typy dynamiczne.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowane klasy DTO

**Specjaliści**: posiadanie statycznych wstępnie zdefiniowanych klas ViewModel, na przykład "umów" opartych na jawnych klasach DTO, jest w znacznym zakresie lepsze dla publicznych interfejsów API, ale również dla mikrousług długoterminowych, nawet jeśli są one używane tylko przez tę samą aplikację.

Jeśli chcesz określić typy odpowiedzi dla struktury Swagger, musisz użyć jawnych klas DTO jako typu zwracanego. W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bardziej szczegółowych informacji z struktury Swagger. Poprawia to dokumentację interfejsu API i zgodność przy korzystaniu z interfejsu API.

**Wady**: jak wspomniano wcześniej, podczas aktualizowania kodu należy wykonać kilka kroków, aby zaktualizować klasy DTO.

*Porada oparta na naszym doświadczeniu*: w zapytaniach zaimplementowanych w mikrousłudze porządkowania w eShopOnContainers rozpoczynamy Programowanie przy użyciu dynamicznych modele widoków, ponieważ było to bardzo proste i elastyczne na wczesnych etapach tworzenia oprogramowania. Jednak po ustabilizowaniu rozwoju wybieramy do refaktoryzacji interfejsy API i używają statycznego lub wstępnie zdefiniowanego DTO dla modele widoków, ponieważ jest to wyraźniejsze dla konsumentów mikrousług, aby znać jawne typy DTO, używane jako "kontrakty".

W poniższym przykładzie można zobaczyć, jak zapytanie zwraca dane przy użyciu jawnej klasy ViewModel DTO: klasy OrderSummary.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a>Opisywanie typów odpowiedzi interfejsów API sieci Web

Deweloperzy korzystający z interfejsów API sieci Web i mikrousług są najbardziej zainteresowani tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie są standardem). Są one obsługiwane w komentarzach XML i adnotacjach danych.

Bez odpowiedniej dokumentacji w interfejsie użytkownika programu Swagger klient nie ma wiedzy na temat typów zwracanych lub kodów HTTP, które mogą być zwracane. Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc Swashbuckle może generować bogatsze informacje o modelu i wartościach zwracanych przez interfejs API, jak pokazano w poniższym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

Jednak atrybut `ProducesResponseType` nie może używać wartości dynamicznej jako typu, ale wymaga użycia jawnych typów, takich jak `OrderSummary` ViewModel DTO, jak pokazano w następującym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dla którego jawne zwracane typy są lepsze niż typy dynamiczne w długim okresie. Korzystając z atrybutu `ProducesResponseType`, można również określić, jaki jest oczekiwany wynik w odniesieniu do możliwych błędów/kodów HTTP, takich jak 200, 400 itd.

Na poniższej ilustracji widać, jak interfejs użytkownika struktury Swagger wyświetla informacje o odpowiedzi.

![Widok przeglądarki na stronie interfejsu użytkownika struktury Swagger dla interfejsu API porządkowania.](./media/image5.png)

**Rysunek 7-5**. Interfejs użytkownika struktury Swagger pokazujący typy odpowiedzi i możliwe kody stanu HTTP z internetowego interfejsu API

Na obrazie można zobaczyć więcej przykładowych wartości na podstawie typów ViewModel oraz możliwych kodów stanu HTTP, które mogą być zwracane.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Punkty danych — Dapper, Entity Framework i aplikacje hybrydowe (artykuł z magazynu MSDN)**  
  <https://msdn.microsoft.com/magazine/mt703432>

- **Strony pomocy dla interfejsu Web API platformy ASP.NET Core korzystające z programu Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md)
>[Następny](ddd-oriented-microservice.md)
