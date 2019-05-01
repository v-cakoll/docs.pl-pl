---
title: Implementowanie odczytów i zapytań w mikrousłudze CQRS
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, wykonania zapytania boku CQRS na szeregowania mikrousługi w ramach aplikacji eShopOnContainers przy użyciu programem Dapper.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 104c7564b7dd29209b48d99b1dea7524c07d7e69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020078"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementowanie odczytów i zapytań w mikrousłudze CQRS

Dla odczytów i zapytań szeregowania mikrousług z aplikacji referencyjnej w ramach aplikacji eShopOnContainers implementuje zapytania niezależnie od modelu DDD i obszar transakcyjnych. Stało się przede wszystkim, ponieważ żądania dla zapytania i transakcje są znacząco różne. Zapisy wykonywania transakcji, które muszą być zgodne z logiką domeny. Zapytania, z drugiej strony, są idempotentne i być rozdzielone od zasad domeny.

Podejście to proste, jak pokazano w rysunek 7-3. Interfejs API jest implementowany przez kontrolerów internetowych interfejsów API przy użyciu dowolnej infrastruktury, takich jak micro relacyjnego mapowania ORM (Object) np. programem Dapper i zwracanie modele dynamicznych widoków w zależności od potrzeb aplikacji interfejsu użytkownika.

![Najprostsza metoda stronie zapytań w uproszczone podejście CQRS może być implementowany przez tylko zapytanie do bazy danych za pomocą Micro-ORM np. programem Dapper, zwracając modele dynamicznych widoków.](./media/image3.png)

**Rysunek 7-3**. Najprostszą metodą dla zapytań w mikrousłudze CQRS

Jest to najprostsza metoda możliwe dla zapytań. Definicje zapytania w bazie danych i zwracają ViewModel dynamiczne, oparta na bieżąco dla każdego zapytania. Ponieważ zapytania są idempotentne, nie zmienią danych niezależnie od tego, ile razy można uruchomić zapytanie. W związku z tym nie trzeba być ograniczana przez wszelkie wzorzec DDD używane w transakcji po stronie, takich jak zagregowanych danych i inne wzorce i dlatego zapytania są oddzielone od obszaru transakcyjnych. Po prostu danych, która wymaga interfejsu użytkownika w bazie danych i zwracać ViewModel dynamicznych, które nie muszą zostać statycznie zdefiniowanych dowolnego miejsca (nie klasy dla modele widoków) z wyjątkiem w instrukcji SQL, samodzielnie.

Ponieważ jest to proste podejście, kod wymagany po stronie zapytania (np. kodu za pomocą micro, takich jak ORM [programem Dapper](https://github.com/StackExchange/Dapper)) można zaimplementować [w obrębie tego samego projektu interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). 7 — pokazano na rysunku 4 to. Zapytania są definiowane w **Ordering.API** mikrousług projektu w ramach rozwiązania w ramach aplikacji eShopOnContainers.

![Widok Eksploratora rozwiązania, projektu Ordering.API, przedstawiający aplikację > folderu zapytania.](./media/image4.png)

**Rysunek 7-4**. Zapytania w mikrousługach porządkowanie w ramach aplikacji eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Użyj modele widoków celowo dla aplikacji klienckich, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane w celu uzyskania danych wymaganych przez aplikacje klienckie, zwracany typ może specjalnie się dla klientów, w oparciu o dane zwrócone przez zapytania. Te modele lub obiektów transferu danych (dto), są nazywane modele widoków.

Zwrócone dane (ViewModel) może być wynikiem łączenie danych z wielu obiektów lub tabel w bazie danych lub nawet przez wiele agregacje zdefiniowane w modelu domeny dla obszaru transakcyjnych. W tym przypadku ponieważ tworzysz zapytania niezależnie od modelu domeny, agregacje granice i ograniczenia całkowicie są ignorowane i możesz zbadać żadnych tabel i kolumn, który może być konieczne. To podejście zapewnia dużą elastyczność i produktywność dla deweloperów, tworzenie lub aktualizowanie zapytań.

Modele widoków mogą być statyczne typy zdefiniowane w klasach. Lub można opracować dynamicznie w oparciu zapytania wykonywane (ponieważ jest zaimplementowana w mikrousługach szeregowania), który jest bardzo agile dla deweloperów.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Pełnić do wykonywania zapytań wczesnych ORM programem Dapper 

Można użyć dowolnego wczesnych ORM, platformy Entity Framework Core lub nawet zwykły ADO.NET podczas wykonywania zapytań. W przykładowej aplikacji programem Dapper został wybrany do szeregowania mikrousługi w ramach aplikacji eShopOnContainers jako dobrym przykładem popularnych ORM micro. Zwykły zapytania SQL może działać o bardzo dużej wydajności, ponieważ jest on bardzo małe framework. Korzystając z programem Dapper, można napisać zapytanie SQL, które mogą uzyskać dostęp i Dołącz do wielu tabel.

Programem Dapper to projekt typu open source (oryginalnie utworzone przez Sam szafran) i jest częścią bloki konstrukcyjne, używane w [Stack Overflow](https://stackoverflow.com/). Aby korzystać z programem Dapper, wystarczy zainstalować go za pośrednictwem [pakietu NuGet z programem Dapper](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji:

![Programem Dapper pakiet jako wyświetlane w widoku pakiety zarządzania NuGet w programie VS.](./media/image4.1.png)

Należy także dodać przy użyciu instrukcji, dzięki czemu kod ma dostęp do metod rozszerzenia programem Dapper.

Korzystając z programem Dapper w kodzie, możesz bezpośrednio użyć <xref:System.Data.SqlClient.SqlConnection> dostępna w klasie <xref:System.Data.SqlClient> przestrzeni nazw. Za pomocą metody QueryAsync i innych metod rozszerzających, które rozszerzają <xref:System.Data.SqlClient.SqlConnection> klasy, można po prostu uruchomić zapytania w sposób prosty i wydajny.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamiczne i modele widoków statyczne

Przy powrocie modele widoków po stronie serwera do aplikacji klienckich, można to porównać te modele widoków jako dto (obiektów transferu danych), które mogą być różnych jednostek domeny wewnętrznej modelu jednostki, ponieważ modele widoków przechowywania danych sposób aplikację kliencką wymagania związane z. W związku z tym w wielu przypadkach można agregować dane pochodzące z wielu jednostek domeny i narzędzia compose modele widoków dokładnie według jak aplikacja kliencka potrzebuje tych danych.

Te modele widoków lub dto może być jawnie zdefiniowane w (jako klasy symbol zastępczy danych) takich jak `OrderSummary` klasy wyświetlane w późniejszym fragment kodu, lub po prostu może zwrócić modele dynamicznych widoków lub dynamicznej dto, po prostu na podstawie atrybutów zwracane przez Twojego zapytania jako dynamiczny Typ.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako typu dynamicznego

Jak pokazano w poniższym kodzie `ViewModel` może bezpośrednio zostać zwrócony przez zapytania, zwracając tylko *dynamiczne* typ, który wewnętrznie opiera się na atrybutach zwróconych przez zapytanie. Oznacza to, że podzbiór atrybutów, które mają zostać zwrócone opiera się na samą kwerendę. W związku z tym, jeśli dodasz nową kolumnę do zapytania lub łączenia tych danych jest dynamicznie dodawane do zwracanego `ViewModel`.

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

Istotną kwestią jest to, że za pomocą dynamicznego typu zwracanego zbierania danych jest dynamicznie składany jako ViewModel.

**Zalety:** To podejście ogranicza potrzebę zmodyfikować statycznych klas ViewModel po zaktualizowaniu zdania SQL kwerendy, dość agile, podczas kodowania, prosty i szybki rozwój rozumieniu przyszłe zmiany, dzięki czemu takie podejście do projektowania.

**Wady:** W dłuższej perspektywie typów dynamicznych może niekorzystnie wpłynąć na przejrzystości i zgodności usługi przy użyciu aplikacji klienckich. Ponadto oprogramowania oprogramowania pośredniczącego, takiego jak pakiet Swashbuckle nie może dostarczyć taki sam poziom dokumentacji na typy zwracane, jeśli przy użyciu typów dynamicznych.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako wstępnie zdefiniowany obiekt DTO klasy

**Specjaliści**: Wstępnie zdefiniowane ViewModel klas statycznych, takich jak "Umowy" oparte na jawne klas DTO, jest zdecydowanie lepszym miejscem dla publicznych interfejsów API, ale także na mikrousługi w długim okresie, nawet jeśli są używane tylko przez samą aplikację.

Jeśli chcesz określić typy odpowiedzi dla struktury Swagger, należy użyć jawnej klasy DTO jako typ zwracany. W związku z tym wstępnie zdefiniowanych klas DTO umożliwiają oferowanie bogatsze informacje z programu Swagger. Dokumentacja interfejsu API i zgodności, poprawiający podczas korzystania z interfejsu API.

**Cons**: Jak wspomniano wcześniej, podczas aktualizowania kodu, może potrwać kilka więcej kroki, aby zaktualizować obiekt DTO klasy.

*Porada oparte na naszych doświadczeniach*: W zapytaniach wdrożone na mikrousługach porządkowanie w ramach aplikacji eShopOnContainers Rozpoczęliśmy tworzenia za pomocą dynamicznego modele widoków, jak bardzo proste i zwinne na wczesnym etapie projektowania. Jednak po rozwoju była charakteryzują się rozległymi, wybraliśmy Refaktoryzuj interfejsów API i używanie dto statyczne lub wstępnie zdefiniowane modele widoków, ponieważ jest bardziej zrozumiały dla konsumentów mikrousług wiedzieć jawnych typów DTO, używane jako "Umowy".

W poniższym przykładzie można zobaczyć, jak zapytanie zwraca dane za pomocą jawnego klasy ViewModel DTO: klasa OrderSummary.

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
            var result = await connection.QueryAsync<OrderSummary>(
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

Deweloperom korzystanie z internetowych interfejsów API i mikrousług są najbardziej interesujących co to jest zwracany — w szczególności typy odpowiedzi i kody błędów usługi (Jeśli to nie standard). Są one obsługiwane w adnotacjach komentarze i dane XML.

Bez prawidłowego dokumentacji w Interfejsie użytkownika programu Swagger, użytkownik nie ma wiedzy zwracane są typy lub HTTP, które mogą być zwracane kodów. Ten problem został rozwiązany przez dodanie <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, więc pakiet Swashbuckle może generować bogatsze informacje o modelu zwracany interfejsu API i wartości, jak pokazano w poniższym kodzie:

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

Jednak `ProducesResponseType` atrybutu nie można użyć dynamicznego, zgodnie z typem, ale wymaga przeprowadzenia używać jawnych typów, takie jak `OrderSummary` ViewModel DTO, pokazano w poniższym przykładzie:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Jest to kolejny powód, dlaczego jawne typy zwracane są lepsze niż typy dynamiczne w perspektywie długoterminowej. Korzystając z `ProducesResponseType` atrybut, można również określić, jak co to jest oczekiwany wynik w zakresie możliwe błędy HTTP/kodów, 200, 400, itp.

Na poniższej ilustracji widać, jak interfejs użytkownika struktury Swagger z informacjami wartość ResponseType.

![Widok przeglądarki strony interfejs użytkownika struktury Swagger dla interfejsu API kolejności.](./media/image5.png)

**Rysunek 7-5**. Wyświetlanie typów odpowiedzi i możliwe kody stanu HTTP z internetowego interfejsu API interfejs użytkownika struktury swagger

Widać na ilustracji powyżej niektóre przykładowe wartości, na podstawie typów ViewModel oraz możliwe kody stanu HTTP, które mogą być zwracane.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Dapper** \
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Punkty danych — programem Dapper, platformy Entity Framework oraz hybrydowych aplikacji (artykuł MSDN mag)** \
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- **ASP.NET Core stron sieci Web interfejsu API pomocy korzystające z programu Swagger** \
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Poprzednie](eshoponcontainers-cqrs-ddd-microservice.md)
>[dalej](ddd-oriented-microservice.md)
