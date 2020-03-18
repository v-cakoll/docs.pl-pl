---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumieć implementację po stronie zapytań CQRS na mikrousługi zamawiania w eShopOnContainers przy użyciu Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 235b0e471a17e2a37a883a111cf499b7837f3ea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972087"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementowanie odczytów/zapytań w mikrousługach CQRS

W przypadku odczytów/zapytań mikrousługi porządkowania z aplikacji referencyjnej eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszaru transakcyjnego. Zostało to zrobione głównie dlatego, że wymagania dotyczące zapytań i transakcji są drastycznie różne. Zapisuje transakcje wykonywania, które muszą być zgodne z logiką domeny. Zapytania, z drugiej strony, są idempotentności i mogą być oddzielone od reguł domeny.

Podejście jest proste, jak pokazano na rysunku 7-3. Interfejs interfejsu API jest implementowany przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury, takiej jak mikroobiektowy maper relacyjny (ORM), taki jak Dapper, i zwracadynamiczny viewmodels w zależności od potrzeb aplikacji interfejsu użytkownika.

![Diagram przedstawiający zapytania wysokiego poziomu po stronie uproszczonego CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Rysunek 7-3**. Najprostsze podejście do zapytań w mikrousłudze CQRS

Najprostsze podejście do zapytań po stronie uproszczonego podejścia CQRS można zaimplementować, po prostu zapytań do bazy danych z Micro-ORM jak Dapper, zwracając dynamiczne ViewModels. Definicje kwerend kwerendy kwerendy bazy danych i zwrócić dynamiczny ViewModel zbudowany na bieżąco dla każdej kwerendy. Ponieważ zapytania są idempotentności, nie zmieni danych bez względu na to, ile razy uruchomić kwerendę. W związku z tym nie trzeba być ograniczone przez wzorzec DDD używane po stronie transakcyjnej, takich jak agregaty i inne wzorce i dlatego zapytania są oddzielone od obszaru transakcyjnego. Wystarczy zbadać bazę danych dla danych, które interfejsu dostępu do interfejsu dostępu potrzebne i zwrócić dynamiczny ViewModel, który nie musi być statycznie zdefiniowane w dowolnym miejscu (bez klas dla ViewModels), z wyjątkiem samych instrukcji SQL.

Ponieważ jest to proste podejście, kod wymagany dla strony zapytań (takich jak kod przy użyciu mikro ORM jak [Dapper)](https://github.com/StackExchange/Dapper)mogą być realizowane [w ramach tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Rysunek 7-4 to pokazuje. Zapytania są zdefiniowane w projekcie mikrousługi **Ordering.API** w ramach rozwiązania eShopOnContainers.

![Zrzut ekranu przedstawiający folder Zapytania projektu Usługi.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Rysunek 7-4**. Zapytania w mikrousługi zamawiania w eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Korzystanie z ViewModels specjalnie dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może być specjalnie dla klientów, na podstawie danych zwracanych przez zapytania. Te modele lub obiekty transferu danych (DTO) są nazywane ViewModels.

Zwrócone dane (ViewModel) może być wynikiem łączenia danych z wielu jednostek lub tabel w bazie danych, a nawet w wielu agregatów zdefiniowanych w modelu domeny dla obszaru transakcyjnego. W takim przypadku, ponieważ tworzysz kwerendy niezależne od modelu domeny, agregowane granice i ograniczenia są całkowicie ignorowane i możesz swobodnie wysyłać zapytania do dowolnej tabeli i kolumny, której możesz potrzebować. Takie podejście zapewnia dużą elastyczność i produktywność dla deweloperów tworzenia lub aktualizowania zapytań.

ViewModels mogą być typy statyczne zdefiniowane w klasach. Lub mogą być tworzone dynamicznie na podstawie zapytań wykonywanych (jak jest zaimplementowana w mikrousługi zamawiania), który jest bardzo zwinny dla deweloperów.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Użyj Dapper jako mikro ORM do wykonywania zapytań

Do wykonywania zapytań można użyć dowolnego mikro ORM, entity framework core, a nawet zwykłego ADO.NET. W przykładowej aplikacji Dapper został wybrany dla mikrousługi zamawiania w eShopOnContainers jako dobry przykład popularnego mikro ORM. Można uruchomić proste zapytania SQL z dużą wydajnością, ponieważ jest to bardzo lekka struktura. Za pomocą Dapper, można napisać kwerendę SQL, które mogą uzyskać dostęp do wielu tabel i dołączyć do nich.

Dapper jest projektem open source (oryginalny stworzony przez Sama Szafrana) i jest częścią bloków konstrukcyjnych używanych w [Stack Overflow](https://stackoverflow.com/). Aby korzystać z Dapper, wystarczy zainstalować go za pośrednictwem [pakietu NuGet Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższym rysunku:

![Zrzut ekranu przedstawiający pakiet Dapper w widoku pakietów NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Należy również dodać using instrukcji, więc kod ma dostęp do metod rozszerzenia Dapper.

Korzystając z dapper w kodzie, <xref:System.Data.SqlClient.SqlConnection> bezpośrednio użyć <xref:System.Data.SqlClient> klasy dostępne w przestrzeni nazw. Za pomocą metody QueryAsync i innych <xref:System.Data.SqlClient.SqlConnection> metod rozszerzenia, które rozszerzają klasę, można po prostu uruchomić zapytania w prosty i performans.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczne a statyczne modele widoków

Podczas zwracania ViewModels od strony serwera do aplikacji klienckich, można myśleć o tych ViewModels jako Obiektów transferu danych , które mogą się różnić od wewnętrznych jednostek domeny modelu jednostki, ponieważ ViewModels przechowywać dane sposób aplikacji klienta Potrzeb. W związku z tym w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i komponować ViewModels dokładnie zgodnie z tym, jak aplikacja kliencki potrzebuje tych danych.

Te ViewModels lub DTO można zdefiniować jawnie (jako klasy `OrderSummary` posiadacza danych), takich jak klasa pokazana w późniejszym fragmencie kodu lub po prostu można zwrócić dynamiczne ViewModels lub dynamiczne DTO po prostu na podstawie atrybutów zwracanych przez zapytania, jako typ dynamiczny.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typ dynamiczny

Jak pokazano w poniższym kodzie, a `ViewModel` mogą być bezpośrednio zwracane przez zapytania, po prostu zwracając typ *dynamiczny,* który wewnętrznie jest oparty na atrybutach zwracanych przez kwerendę. Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samej kwerendzie. W związku z tym jeśli dodasz nową kolumnę do kwerendy lub `ViewModel`sprzężenia, dane te są dynamicznie dodawane do zwróconych .

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

Ważną kwestią jest to, że przy użyciu typu dynamicznego zwracanej kolekcji danych jest dynamicznie montowane jako ViewModel.

**Plusy:** Takie podejście zmniejsza potrzebę modyfikowania statycznych klas ViewModel przy każdym aktualizowaniu zdania SQL kwerendy, dzięki czemu to podejście projektowe jest dość elastyczne podczas kodowania, proste i szybkie rozwijanie w odniesieniu do przyszłych zmian.

**Minusy:** W dłuższej perspektywie typy dynamiczne mogą negatywnie wpłynąć na przejrzystość i zgodność usługi z aplikacjami klienckimi. Ponadto oprogramowanie oprogramowania pośredniczego, takie jak Swashbuckle, nie może zapewnić tego samego poziomu dokumentacji dotyczącej zwracanych typów, jeśli używasz typów dynamicznych.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowane klasy DTO

**Zalety:** Mając statyczne wstępnie zdefiniowane viewmodel klas, takich jak "kontrakty" na podstawie jawnych klas DTO, jest zdecydowanie lepiej dla publicznych interfejsów API, ale także dla mikrousług długoterminowych, nawet jeśli są one używane tylko przez tę samą aplikację.

Jeśli chcesz określić typy odpowiedzi dla Swagger, należy użyć jawnych klas DTO jako typ zwracany. W związku z tym wstępnie zdefiniowane klasy DTO umożliwiają oferowanie bogatszych informacji od swaggera. To poprawia dokumentację interfejsu API i zgodności podczas korzystania z interfejsu API.

**Minusy**: Jak wspomniano wcześniej, podczas aktualizowania kodu, trwa kilka kroków, aby zaktualizować klasy DTO.

*Wskazówka na podstawie naszego doświadczenia*: W zapytaniach zaimplementowanych w mikrousługach zamawiania w eShopOnContainers rozpoczęliśmy prace nad dynamicznym ViewModels, ponieważ było to bardzo proste i elastyczne na wczesnych etapach rozwoju. Jednak po ustabilizowaniu rozwoju zdecydowaliśmy się refaktoryzacji interfejsów API i użyć statycznych lub wstępnie zdefiniowanych dco dla ViewModels, ponieważ jest bardziej jasne dla konsumentów mikrousługi znać jawne typy DTO, używane jako "kontrakty".

W poniższym przykładzie można zobaczyć, jak kwerenda zwraca dane przy użyciu jawnej ViewModel DTO klasy: OrderSummary klasy.

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

#### <a name="describe-response-types-of-web-apis"></a>Opis typów odpowiedzi interfejsów API sieci Web

Deweloperzy korzystający z internetowych interfejsów API i mikrousług są najbardziej zainteresowani tym, co jest zwracane — w szczególności typy odpowiedzi i kody błędów (jeśli nie standardowe). Są one obsługiwane w komentarzach XML i adnotacjach danych.

Bez odpowiedniej dokumentacji w interfejsie Swagger, konsument nie ma wiedzy na temat typów są zwracane lub jakie kody HTTP mogą być zwracane. Ten problem został rozwiązany <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>przez dodanie , więc Swashbuckle może generować bogatsze informacje o modelu zwracanym interfejsu API i wartości, jak pokazano w poniższym kodzie:

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

Jednak `ProducesResponseType` atrybut nie można użyć dynamicznego jako typu, ale `OrderSummary` wymaga użycia jawnych typów, takich jak ViewModel DTO, pokazano w poniższym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dlaczego jawne zwracane typy są lepsze niż typy dynamiczne, w dłuższej perspektywie. Korzystając z `ProducesResponseType` atrybutu, można również określić, jaki jest oczekiwany wynik w odniesieniu do możliwych błędów/kodów HTTP, takich jak 200, 400 itp.

Na poniższej ilustracji można zobaczyć, jak swagger interfejsu pokazuje informacje ResponseType.

![Zrzut ekranu przedstawiający stronę interfejsu interfejsu firmy Swagger dla interfejsu api zamawiania.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Rysunek 7-5**. Interfejs swagger z typami odpowiedzi i możliwymi kodami stanu HTTP z internetowego interfejsu API

Na powyższym obrazie można zobaczyć niektóre przykładowe wartości oparte na typach ViewModel oraz możliwych kodów stanu HTTP, które mogą zostać zwrócone.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacje hybrydowe (artykuł magazynu MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **ASP.NET podstawowych stron pomocy interfejsu API sieci Web przy użyciu swaggera**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Poprzedni](eshoponcontainers-cqrs-ddd-microservice.md)
>[następny](ddd-oriented-microservice.md)
