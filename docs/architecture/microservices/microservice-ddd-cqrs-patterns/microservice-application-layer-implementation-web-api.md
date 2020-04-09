---
title: Implementowanie warstwy aplikacji mikrousług za pomocą internetowego interfejsu API
description: Zrozumienie iniekcji zależności i wzorców mediatora i ich szczegóły ich implementacji w warstwie aplikacji interfejsu API sieci Web.
ms.date: 01/30/2020
ms.openlocfilehash: 76562d87b09a18e4a4ecb7625a2e823bc1ccff78
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988469"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Iniekcja zależności służy do wstrzykiwania obiektów infrastruktury do warstwy aplikacji

Jak wspomniano wcześniej, warstwy aplikacji mogą być implementowane jako część artefaktu (zestawu) są budowane, takich jak w projekcie interfejsu API sieci Web lub projektu aplikacji sieci web MVC. W przypadku mikrousługi utworzonej za pomocą ASP.NET Core warstwa aplikacji będzie zwykle biblioteką interfejsu API sieci Web. Jeśli chcesz oddzielić to, co pochodzi od ASP.NET Core (jego infrastruktury i kontrolerów) od kodu warstwy aplikacji niestandardowej, można również umieścić warstwę aplikacji w oddzielnej bibliotece klas, ale jest to opcjonalne.

Na przykład kod warstwy aplikacji mikrousługi zamawiania jest bezpośrednio implementowany jako część projektu **Ordering.API** (ASP.NET core web API projektu), jak pokazano na rysunku 7-23.

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Zrzut ekranu przedstawiający mikrousługę Ordering.API w Eksploratorze rozwiązań.":::
Widok Eksploratora rozwiązań mikrousługi Ordering.API, przedstawiający podfoldery w folderze aplikacji: Zachowania, polecenia, DomainEventHandlers, IntegrationEvents, Models, Queries i Validations.
:::image-end:::

**Rysunek 7-23**. Warstwa aplikacji w projekcie uszekw.API ASP.NET Core Web API

ASP.NET Core zawiera prosty [wbudowany kontener IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowany przez interfejs IServiceProvider), który domyślnie obsługuje iniekcję konstruktora, a ASP.NET udostępnia niektóre usługi za pośrednictwem DI. ASP.NET Core używa terminu *usługi* dla dowolnego typu, który zostanie zarejestrowany, który zostanie wstrzyknięty za pośrednictwem DI. Konfigurowanie wbudowanych usług kontenera w ConfigureServices metody w aplikacji Startup klasy. Zależności są implementowane w usługach, które typ potrzebuje i które można zarejestrować w kontenerze IoC.

Zazwyczaj chcesz wstrzyknąć zależności, które implementują obiekty infrastruktury. Bardzo typową zależnością do wstrzyknięcia jest repozytorium. Ale można wstrzyknąć inne zależności infrastruktury, które mogą mieć. W przypadku prostszych implementacji można bezpośrednio wstrzyknąć obiekt wzorca unit of work (obiekt EF DbContext), ponieważ DBContext jest również implementacją obiektów trwałości infrastruktury.

W poniższym przykładzie można zobaczyć, jak .NET Core jest wstrzykiwanie wymaganych obiektów repozytorium za pośrednictwem konstruktora. Klasa jest program obsługi poleceń, które omówimy w następnej sekcji.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Klasa używa wstrzykniętych repozytoriów do wykonania transakcji i utrwalenia zmian stanu. Nie ma znaczenia, czy ta klasa jest programem obsługi poleceń, ASP.NET podstawowych metod kontrolera interfejsu API sieci Web, czy [usługą aplikacji DDD.](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/) Jest to ostatecznie prosta klasa, która używa repozytoriów, jednostek domeny i innej koordynacji aplikacji w sposób podobny do obsługi poleceń. Iniekcja zależności działa w taki sam sposób dla wszystkich wymienionych klas, jak w przykładzie przy użyciu DI na podstawie konstruktora.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Rejestrowanie typów implementacji zależności oraz interfejsów lub abstrakcji

Przed użyciem obiektów wstrzykuje się za pośrednictwem konstruktorów, należy wiedzieć, gdzie zarejestrować interfejsy i klasy, które produkują obiekty wstrzykuje się do klas aplikacji za pośrednictwem DI. (Podobnie jak DI na podstawie konstruktora, jak pokazano wcześniej.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Użyj wbudowanego kontenera IoC dostarczonego przez ASP.NET Core

Korzystając z wbudowanego kontenera IoC dostarczonego przez ASP.NET Core, można zarejestrować typy, które mają być wstrzykiwane w configureservices metody w pliku Startup.cs, jak w następującym kodzie:

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Najczęstszym wzorcem podczas rejestrowania typów w kontenerze IoC jest zarejestrowanie pary typów — interfejsu i powiązanej z nim klasy implementacji. Następnie, gdy zażądasz obiektu z kontenera IoC za pośrednictwem dowolnego konstruktora, żądasz obiektu określonego typu interfejsu. Na przykład w poprzednim przykładzie ostatni wiersz stwierdza, że gdy którykolwiek z konstruktorów mają zależność od IMyCustomRepository (interfejs lub abstrakcja), kontener IoC wstrzyknie wystąpienie myCustomSQLServerRepository klasy implementacji.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Użyj biblioteki Scrutor do automatycznej rejestracji typów

Podczas korzystania z DI w .NET Core, można chcieć być w stanie skanować zestaw i automatycznie zarejestrować jego typy według konwencji. Ta funkcja nie jest obecnie dostępna w ASP.NET Core. Można jednak użyć biblioteki [Scrutor](https://github.com/khellang/Scrutor) do tego. Takie podejście jest wygodne, gdy masz dziesiątki typów, które muszą być zarejestrowane w kontenerze IoC.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Mateusz Król. Rejestracja usług w Scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Skrutor.** Repozytorium GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Używanie autofac jako kontenera IoC

Można również użyć dodatkowych kontenerów IoC i podłączyć je do potoku ASP.NET Core, jak w mikrousługach zamawiania w eShopOnContainers, która używa [autofac](https://autofac.org/). Podczas korzystania z Autofac zazwyczaj zarejestrować typy za pośrednictwem modułów, które umożliwiają dzielenie typów rejestracji między wiele plików w zależności od tego, gdzie są typy, tak jak można mieć typy aplikacji rozproszone w wielu bibliotekach klas.

Na przykład poniżej przedstawiono [moduł aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla projektu [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) z typami, które chcesz wstrzyknąć.

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

Autofac posiada również funkcję [skanowania zestawów i rejestrowania typów według konwencji nazw](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Proces rejestracji i pojęcia są bardzo podobne do sposobu, w jaki można zarejestrować typy za pomocą wbudowanego kontenera ASP.NET Core IoC, ale składnia podczas korzystania z autofac jest nieco inna.

W przykładowym kodzie abstrakcja IOrderRepository jest zarejestrowana wraz z klasą implementacji OrderRepository. Oznacza to, że za każdym razem, gdy konstruktor deklaruje zależność za pośrednictwem abstrakcji lub interfejsu IOrderRepository, kontener IoC wstrzyknie wystąpienie klasy OrderRepository.

Typ zakresu wystąpienia określa sposób współużytkowania wystąpienia między żądaniami dla tej samej usługi lub zależności. Gdy zostanie wykonane żądanie zależności, kontener IoC może zwrócić następujące elementy:

- Pojedyncze wystąpienie na okres istnienia (o którym mowa w ASP.NET core IoC kontenera jako *zakres).*

- Nowe wystąpienie na zależności (określane w ASP.NET Core IoC kontenera jako *przejściowe).*

- Pojedyncze wystąpienie współużytkowane przez wszystkie obiekty przy użyciu kontenera IoC (określanego w ASP.NET Core IoC kontenera jako *singleton).*

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do iniekcji zależności w ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficjalna dokumentacja. \
  <https://docs.autofac.org/en/latest/>

- **Porównanie okresów istnienia usługi kontenera core ASP.NET z zakresami wystąpienia kontenera Autofac IoC — Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementowanie wzorców obsługi poleceń i poleceń

W przykładzie DI-through-constructor pokazano w poprzedniej sekcji kontener IoC wstrzykiwał repozytoria za pośrednictwem konstruktora w klasie. Ale dokładnie gdzie zostały one wstrzyknięte? W prostym interfejsie API sieci Web (na przykład mikrousługi katalogu w eShopOnContainers), można wstrzyknąć je na poziomie kontrolerów MVC, w konstruktorze kontrolera, jako część potoku żądań ASP.NET Core. Jednak w kodzie początkowym tej sekcji [(CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy z ordering.API usługi w eShopOnContainers), iniekcji zależności odbywa się za pośrednictwem konstruktora określonego programu obsługi poleceń. Wyjaśnijmy, czym jest program obsługi poleceń i dlaczego chcesz go używać.

Wzorzec polecenia jest nierozerwalnie związany ze wzorcem CQRS, który został wprowadzony wcześniej w tym przewodniku. CQRS ma dwie strony. Pierwszym obszarem są zapytania, przy użyciu uproszczonych zapytań z [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, co zostało wyjaśnione wcześniej. Drugi obszar to polecenia, które są punktem wyjścia dla transakcji i kanał wejściowy spoza usługi.

Jak pokazano na rysunku 7-24, wzorzec opiera się na akceptowaniu poleceń od strony klienta, przetwarzaniu ich na podstawie reguł modelu domeny i wreszcie utrwalaniu stanów z transakcjami.

![Diagram przedstawiający przepływ danych wysokiego poziomu z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

**Rysunek 7-24**. Widok wysokiego poziomu poleceń lub "strony transakcyjnej" w wzorcu CQRS

Rysunek 7-24 pokazuje, że aplikacja interfejsu użytkownika wysyła `CommandHandler`polecenie za pośrednictwem interfejsu API, który dostaje się do , który zależy od modelu domeny i infrastruktury, aby zaktualizować bazę danych.

### <a name="the-command-class"></a>Klasa polecenia

Polecenie jest żądaniem dla systemu do wykonania akcji, która zmienia stan systemu. Polecenia są konieczne i powinny być przetwarzane tylko raz.

Ponieważ polecenia są imperatywami, są one zazwyczaj nazwane z zleceniem w imperatywnym nastroju (na przykład "create" lub "update") i mogą zawierać typ agregacji, taki jak CreateOrderCommand. W przeciwieństwie do zdarzenia, polecenie nie jest faktem z przeszłości; jest to tylko wniosek, a zatem można go odmówić.

Polecenia mogą pochodzić z interfejsu użytkownika w wyniku inicjowania żądania przez użytkownika lub od menedżera procesów, gdy menedżer procesów kieruje agregację do wykonania akcji.

Ważną cechą polecenia jest to, że powinno być przetwarzane tylko raz przez jeden odbiornik. Dzieje się tak, ponieważ polecenie jest pojedynczą akcją lub transakcją, którą chcesz wykonać w aplikacji. Na przykład tego samego polecenia tworzenia zamówienia nie powinny być przetwarzane więcej niż jeden raz. Jest to istotna różnica między poleceniami i zdarzeniami. Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług może być zainteresowany zdarzenia.

Ponadto ważne jest, aby polecenie było przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentne. Polecenie jest idempotentne, jeśli może być wykonywane wiele razy bez zmiany wyniku, ze względu na charakter polecenia lub ze względu na sposób, w jaki system obsługuje polecenie.

Jest dobrą praktyką, aby polecenia i aktualizacje idempotentne, gdy ma to sens w ramach reguł biznesowych domeny i invariants. Na przykład, aby użyć tego samego przykładu, jeśli z jakiegokolwiek powodu (logika ponawiania próby, hacking, itp.) to samo polecenie CreateOrder dociera do systemu wiele razy, powinieneś być w stanie go zidentyfikować i upewnić się, że nie tworzysz wielu zamówień. Aby to zrobić, należy dołączyć pewnego rodzaju tożsamości w operacjach i określić, czy polecenie lub aktualizacja została już przetworzona.

Polecenie jest wysyłane do jednego odbiornika; nie publikujesz polecenia. Publikowanie jest dla zdarzeń, które stwierdzają fakt, że coś się stało i może być interesujące dla odbiorców zdarzeń. W przypadku zdarzeń wydawca nie ma obaw, którzy odbiorcy otrzymują zdarzenie ani co robią. Ale zdarzenia domeny lub integracji to inna historia już wprowadzona w poprzednich sekcjach.

Polecenie jest implementowane z klasą, która zawiera pola danych lub kolekcje ze wszystkimi informacjami, które są potrzebne do wykonania tego polecenia. Polecenie jest specjalnym rodzajem obiektu transferu danych (DTO), który jest specjalnie używany do żądania zmian lub transakcji. Samo polecenie jest oparte na dokładnie tych informacjach, które są potrzebne do przetworzenia polecenia i nic więcej.

Poniższy przykład przedstawia `CreateOrderCommand` klasę uproszczoną. Jest to niezmienne polecenie, które jest używane w mikrousługi zamawiania w eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

Zasadniczo klasa polecenia zawiera wszystkie dane potrzebne do wykonywania transakcji biznesowej przy użyciu obiektów modelu domeny. W związku z tym polecenia są po prostu struktur danych, które zawierają dane tylko do odczytu i nie zachowanie. Nazwa polecenia wskazuje jego przeznaczenie. W wielu językach, takich jak C#, polecenia są reprezentowane jako klasy, ale nie są prawdziwe klasy w sensie rzeczywistym obiektowe.

Jako dodatkową cechę polecenia są niezmienne, ponieważ oczekiwane użycie jest, że są one przetwarzane bezpośrednio przez model domeny. Nie muszą się zmieniać w trakcie przewidywanego okresu istnienia. W klasie C# niezmienność można osiągnąć, nie mając żadnych ustawiających lub innych metod, które zmieniają stan wewnętrzny.

Należy pamiętać, że jeśli zamierzasz lub oczekujesz, że polecenia przejść przez proces serializacji/deserializacji, `[DataMember]` właściwości `[JsonProperty]`muszą mieć prywatny seter i (lub) atrybut. W przeciwnym razie deserializer nie będzie można zrekonstruować obiektu w miejscu docelowym z wymaganymi wartościami. Można również użyć prawdziwie tylko do odczytu właściwości, jeśli klasa ma konstruktora z parametrami dla wszystkich właściwości, ze `[JsonConstructor]`zwykłą konwencją nazewnictwa camelCase i adnotacje konstruktora jako . Jednak ta opcja wymaga więcej kodu.

Na przykład klasa polecenia do tworzenia zamówienia jest prawdopodobnie podobny pod względem danych do kolejności, którą chcesz utworzyć, ale prawdopodobnie nie są potrzebne te same atrybuty. Na przykład `CreateOrderCommand` nie ma identyfikatora zamówienia, ponieważ zamówienie nie zostało jeszcze utworzone.

Wiele klas poleceń może być proste, wymagając tylko kilka pól o niektórych stanu, który wymaga zmiany. Tak będzie w przypadku, gdy po prostu zmieniasz status zamówienia z "w toku" na "płatne" lub "wysłane" za pomocą polecenia podobnego do następującego:

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

Niektórzy deweloperzy, aby ich obiekty żądania interfejsu użytkownika oddzielnie od ich polecenia DTO, ale to tylko kwestia preferencji. Jest to żmudna separacja z nie dużą wartością dodaną, a obiekty mają prawie dokładnie ten sam kształt. Na przykład w eShopOnContainers niektóre polecenia pochodzą bezpośrednio od strony klienta.

### <a name="the-command-handler-class"></a>Klasa obsługi polecenia

Należy zaimplementować określoną klasę obsługi polecenia dla każdego polecenia. Tak działa wzorzec i w tym miejscu użyjesz obiektu polecenia, obiektów domeny i obiektów repozytorium infrastruktury. Program obsługi poleceń jest w rzeczywistości sercem warstwy aplikacji pod względem CQRS i DDD. Jednak wszystkie logiki domeny powinny być zawarte w klasach domeny — w obrębie agregujących katalogów głównych (jednostek głównych), jednostek podrzędnych lub [usług domeny](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale nie w ramach programu obsługi poleceń, który jest klasą z warstwy aplikacji.

Klasa obsługi poleceń oferuje silny odskocznię w drodze do osiągnięcia zasady pojedynczej odpowiedzialności (SRP) wymienionej w poprzedniej sekcji.

Program obsługi polecenia odbiera polecenie i uzyskuje wynik z agregacji, który jest używany. Wynikiem powinno być pomyślne wykonanie polecenia lub wyjątek. W przypadku wyjątku stan systemu powinien być niezmieniony.

Program obsługi poleceń zwykle wykonuje następujące kroki:

- Odbiera obiekt polecenia, jak DTO (od [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub innego obiektu infrastruktury).

- Sprawdza, czy polecenie jest prawidłowe (jeśli nie jest zatwierdzone przez mediatora).

- Wystąpienia agregacji wystąpienia głównego, który jest celem bieżącego polecenia.

- Wykonuje metodę w zagregowanym wystąpieniu głównym, uzyskując wymagane dane z polecenia.

- Utrzymuje się nowy stan agregacji do powiązanej bazy danych. Ta ostatnia operacja jest rzeczywistą transakcją.

Zazwyczaj program obsługi poleceń zajmuje się pojedynczym agregacji napędzany przez jego agregacji głównego (jednostki głównej). Jeśli na odbiór pojedynczego polecenia powinno mieć wpływ wiele agregatów, można użyć zdarzeń domeny do propagowania stanów lub akcji w wielu agregatach.

Ważnym punktem w tym miejscu jest to, że podczas przetwarzania polecenia, wszystkie logiki domeny powinny znajdować się wewnątrz modelu domeny (agregaty), w pełni hermetyzowany i gotowy do testowania jednostkowego. Program obsługi poleceń działa tylko jako sposób, aby uzyskać model domeny z bazy danych i jako ostatni krok, aby poinformować warstwy infrastruktury (repozytoria) do utrwalenia zmian po zmianie modelu. Zaletą tego podejścia jest to, że można refaktoryzować logiki domeny w izolowanym, w pełni hermetyzowany, bogaty, behawioralny model domeny bez zmiany kodu w warstwach aplikacji lub infrastruktury, które są poziom instalacji wodno-kanalizacyjnych (programy obsługi poleceń, web API, repozytoria, itp.).

Gdy programy obsługi poleceń stają się złożone, ze zbyt dużą logiką, która może być zapachem kodu. Przejrzyj je, a jeśli znajdziesz logikę domeny, refaktoryzuj kod, aby przenieść to zachowanie domeny do metod obiektów domeny (agregującej jednostki głównej i podrzędnej).

Jako przykład klasy obsługi poleceń, poniższy `CreateOrderCommandHandler` kod pokazuje tę samą klasę, która została wyświetlena na początku tego rozdziału. W takim przypadku chcemy wyróżnić Handle metody i operacji z obiektów modelu domeny/agreguje.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Oto dodatkowe kroki, które powinien wykonać program obsługi poleceń:

- Użyj danych polecenia do pracy z metodami i zachowaniem głównego agregacji.

- Wewnętrznie w obiektach domeny, podnieść zdarzenia domeny podczas wykonywania transakcji, ale jest to niewidoczny z punktu widzenia obsługi poleceń.

- Jeśli wynik operacji agregacji zakończy się pomyślnie i po zakończeniu transakcji, podnieś zdarzenia integracji. (Mogą one również być wywoływane przez klasy infrastruktury, takie jak repozytoria).

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Marek Seemann. Na granicach aplikacje nie są zorientowane obiektowo** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Polecenia i zdarzenia** \
  <https://cqrs.nu/Faq/commands-and-events>

- **Do czego działa program obsługi poleceń?** \
  <https://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Wzorce poleceń domeny — programy obsługi** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Wzorce poleceń domeny — sprawdzanie poprawności** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Potok procesu polecenia: jak wyzwolić program obsługi poleceń

Następne pytanie jest jak wywołać program obsługi poleceń. Można ręcznie wywołać go z każdego powiązanego kontrolera core ASP.NET. Jednak takie podejście byłoby zbyt powiązane i nie jest idealne.

Pozostałe dwie główne opcje, które są zalecanymi opcjami, to:

- Za pośrednictwem artefaktu wzorca mediatora w pamięci.

- Z kolejki komunikatów asynchronicznych, między kontrolerami i programami obsługi.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Użyj wzorca mediatora (w pamięci) w potoku poleceń

Jak pokazano na rysunku 7-25, w podejściu CQRS używasz inteligentnego mediatora, podobnego do magistrali w pamięci, która jest wystarczająco inteligentna, aby przekierować do odpowiedniego programu obsługi poleceń na podstawie typu odebranego polecenia lub DTO. Pojedyncze czarne strzałki między składnikami reprezentują zależności między obiektami (w wielu przypadkach wstrzykuje się za pośrednictwem DI) z ich powiązanych interakcji.

![Diagram przedstawiający bardziej szczegółowy przepływ danych z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

**Rysunek 7-25**. Korzystanie ze wzorca mediatora w procesie w jednej mikrousługach CQRS

Powyższy diagram pokazuje powiększenie z obrazu 7-24: kontroler ASP.NET Core wysyła polecenie do potoku poleceń MediatR, aby dostać się do odpowiedniego programu obsługi.

Powodem, dla którego przy użyciu wzorca mediatora ma sens jest to, że w aplikacjach przedsiębiorstwa żądania przetwarzania mogą się skomplikować. Chcesz mieć możliwość dodania otwartej liczby przekrojowych problemów, takich jak rejestrowanie, sprawdzanie poprawności, inspekcja i bezpieczeństwo. W takich przypadkach można polegać na potoku mediatora (zobacz [wzorzec mediatora),](https://en.wikipedia.org/wiki/Mediator_pattern)aby zapewnić środki dla tych dodatkowych zachowań lub problemów przekrojowych.

Mediator jest obiektem, który hermetyzuje "jak" tego procesu: koordynuje wykonanie na podstawie stanu, sposobu wywoływania programu obsługi poleceń lub ładunku, który udostępnia program obsługi. Za pomocą komponentu mediatora można zastosować kwestie przekrojowe w sposób scentralizowany i przejrzysty, stosując dekoratory (lub [zachowania rurociągów](https://github.com/jbogard/MediatR/wiki/Behaviors) od [MediatR 3).](https://www.nuget.org/packages/MediatR/3.0.0) Aby uzyskać więcej informacji, zobacz [wzór dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratory i zachowania są podobne do [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), tylko stosowane do określonego potoku procesu zarządzanego przez składnik mediatora. Aspekty w AOP, które implementują problemy przekrojowe są stosowane w oparciu o *tkaczy aspektów wstrzykuje* się w czasie kompilacji lub na podstawie przechwytywania wywołania obiektu. Oba typowe podejścia AOP są czasami mówi się, że działa "jak magia", ponieważ nie jest łatwo zobaczyć, jak AOP wykonuje swoją pracę. W przypadku poważnych problemów lub błędów AOP może być trudne do debugowania. Z drugiej strony te dekoratory/zachowania są jawne i stosowane tylko w kontekście mediatora, więc debugowanie jest znacznie bardziej przewidywalne i łatwe.

Na przykład w eShopOnContainers zamawiania mikrousługi zaimplementowaliśmy dwa przykładowe zachowania, [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy i [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy. Implementacja zachowań jest wyjaśniona w następnej sekcji, pokazując, jak eShopOnContainers wykorzystuje [mediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [zachowań](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Używanie kolejek komunikatów (out-of-proc) w potoku polecenia

Innym wyborem jest użycie wiadomości asynchronicznych na podstawie brokerów lub kolejek wiadomości, jak pokazano na rysunku 7-26. Ta opcja może być również łączona ze składnikiem mediatora tuż przed programem obsługi poleceń.

![Diagram przedstawiający przepływ danych przy użyciu kolejki komunikatów wysokiej źródła.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

**Rysunek 7-26**. Korzystanie z kolejek komunikatów (komunikacja poza procesem i między procesem) za pomocą poleceń CQRS

Potok polecenia może być również obsługiwany przez kolejkę komunikatów o wysokiej dostępności, aby dostarczyć polecenia do odpowiedniego programu obsługi. Za pomocą kolejek komunikatów, aby zaakceptować polecenia może dodatkowo skomplikować potok polecenia, ponieważ prawdopodobnie trzeba będzie podzielić potoku na dwa procesy połączone za pośrednictwem kolejki komunikatów zewnętrznych. Mimo to należy go używać, jeśli trzeba mieć lepszą skalowalność i wydajność na podstawie asynchronii wiadomości. Należy wziąć pod uwagę, że w przypadku rysunek 7-26, kontroler po prostu księguje komunikat polecenia do kolejki i zwraca. Następnie programy obsługi poleceń przetwarzają wiadomości we własnym tempie. Jest to duża zaleta kolejek: kolejka komunikatów może działać jako bufor w przypadkach, gdy wymagana jest nadmierna skalowalność, na przykład dla zapasów lub innego scenariusza z dużą ilością danych transferu danych przychodzących.

Jednak ze względu na asynchroniczne charakter kolejek komunikatów, należy dowiedzieć się, jak komunikować się z aplikacją kliencką o powodzenie lub niepowodzenie procesu polecenia. Z reguły nigdy nie należy używać poleceń "ogień i zapomnij". Każda aplikacja biznesowa musi wiedzieć, czy polecenie zostało pomyślnie przetworzone, czy przynajmniej zweryfikowane i zaakceptowane.

W związku z tym możliwość odpowiedzi na klienta po sprawdzeniu poprawności komunikat polecenia, który został przesłany do kolejki asynchroniiowej zwiększa złożoność systemu, w porównaniu do procesu polecenia w trakcie, który zwraca wynik operacji po uruchomieniu transakcji. Za pomocą kolejek może być konieczne zwrócenie wyniku procesu polecenia za pośrednictwem innych komunikatów wynik operacji, które będą wymagać dodatkowych składników i komunikacji niestandardowej w systemie.

Dodatkowo polecenia asynchronizowe są poleceniami jednokierunkowymi, które w wielu przypadkach mogą nie być potrzebne, jak wyjaśniono w następującej interesującej wymianie między Burtsev Aleksiejem a Gregiem Youngiem w [rozmowie online:](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)

> \[Burtsev Alexey\] znajduję wiele kodu, gdzie ludzie używają obsługi poleceń asynchronicznego lub jednokierunkowej obsługi poleceń bez żadnego powodu (nie robią długiej operacji, nie wykonują zewnętrznego kodu asynchronicznego, nawet nie przekraczają granic aplikacji, aby korzystać z magistrali wiadomości). Dlaczego wprowadzają tę niepotrzebną złożoność? I rzeczywiście, JA do końca' widział pewien CQRS kod przykład rezygnować blokowanie polecenia rachowania dłoń jak dotąd, chociaż ono wola praca dobrze w najliczniejszy cases.
>
> \[Greg\] \[Młody ... \] polecenie asynchroniczne nie istnieje; to właściwie kolejne wydarzenie. Jeśli muszę zaakceptować to, co mnie wysłać i podnieść zdarzenie, jeśli \[się nie zgadzam, to\]już nie mówisz mi zrobić coś, co jest, to nie jest polecenie . To ty mówisz mi, że coś zostało zrobione. Na początku wydaje się to niewielką różnicą, ale ma wiele konsekwencji.

Polecenia asynchroniczne znacznie zwiększają złożoność systemu, ponieważ nie ma prostego sposobu na wskazanie błędów. W związku z tym polecenia asynchroniczne nie są zalecane inne niż wtedy, gdy wymagania dotyczące skalowania są potrzebne lub w szczególnych przypadkach podczas komunikowania się mikrousług wewnętrznych za pośrednictwem wiadomości. W takich przypadkach należy zaprojektować oddzielny system raportowania i odzyskiwania dla awarii.

W początkowej wersji eShopOnContainers zdecydowaliśmy się użyć synchroniczowego przetwarzania poleceń, rozpoczętego od żądań HTTP i napędzanego przez wzorzec mediatora. To łatwo pozwala na powrót sukcesu lub niepowodzenia procesu, jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.

W każdym przypadku powinna to być decyzja na podstawie wymagań biznesowych aplikacji lub mikrousług.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementowanie potoku procesu polecenia za pomocą wzorca mediatora (MediatR)

W ramach przykładowej implementacji w tym przewodniku proponuje się użycie potoku w toku opartego na wzorzec mediatora do kierowania poleceniami pozyskiwania i trasowania w pamięci do odpowiednich programów obsługi poleceń. W przewodniku proponuje się również stosowanie [zachowań](https://github.com/jbogard/MediatR/wiki/Behaviors) w celu oddzielenia obaw przekrojowych.

Do implementacji w programie .NET Core dostępnych jest wiele bibliotek typu open source, które implementują wzorzec mediatora. Biblioteka używana w tym przewodniku jest biblioteka open source [MediatR](https://github.com/jbogard/MediatR) (stworzona przez Jimmy'ego Bogarda), ale można użyć innego podejścia. MediatR to mała i prosta biblioteka, która umożliwia przetwarzanie komunikatów w pamięci, takich jak polecenie, podczas stosowania dekoratorów lub zachowań.

Za pomocą wzorca mediatora pomaga zmniejszyć sprzężenia i wyizolować obawy żądanej pracy, podczas automatycznego łączenia się z programem obsługi, który wykonuje tę pracę — w tym przypadku do obsługi poleceń.

Innym dobrym powodem, aby użyć wzorca Mediator został wyjaśniony przez Jimmy Bogard podczas przeglądu tego przewodnika:

> Myślę, że warto wspomnieć o testowaniu tutaj - zapewnia ładne spójne okno na zachowanie systemu. Żądanie, odpowiedź-out. Odkryliśmy, że ten aspekt jest bardzo cenny w budowaniu konsekwentnie zachowujących się testów.

Najpierw przyjrzyjmy się przykładowego kontrolera WebAPI, w którym faktycznie można użyć obiektu mediatora. Jeśli nie używasz obiektu mediatora, należy wstrzyknąć wszystkie zależności dla tego kontrolera, takie rzeczy jak obiekt rejestratora i inne. W związku z tym konstruktora byłoby dość skomplikowane. Z drugiej strony, jeśli używasz obiektu mediatora, konstruktor kontrolera może być o wiele prostszy, z zaledwie kilkoma zależnościami zamiast wielu zależności, jeśli masz jeden na operację przekrojową, jak w poniższym przykładzie:

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

Widać, że mediator zapewnia czysty i chudy konstruktor kontrolera interfejsu API sieci Web. Ponadto w ramach metod kontrolera kod do wysłania polecenia do obiektu mediatora jest prawie jeden wiersz:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a>Implementowanie poleceń idempotentnych

W **eShopOnContainers**bardziej zaawansowanym przykładem niż powyższe jest przesyłanie CreateOrderCommand obiektu z mikrousługi zamawiania. Ale ponieważ proces zamawiania biznesowych jest nieco bardziej złożony i w naszym przypadku faktycznie uruchamia się w mikrousługi koszyka, ta akcja przesyłania CreateOrderCommand obiektu jest wykonywana z obsługi zdarzeń integracji o nazwie [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) zamiast prostego kontrolera WebAPI wywołanego z aplikacji klienta, jak w poprzednim prostym przykładzie.

Niemniej jednak działanie przesyłania polecenia do MediatR jest dość podobne, jak pokazano w poniższym kodzie.

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

Jednak ten przypadek jest również nieco bardziej zaawansowany, ponieważ implementujemy również polecenia idempotentne. CreateOrderCommand proces powinien być idempotentny, więc jeśli ten sam komunikat jest duplikowany za pośrednictwem sieci, z jakiegokolwiek powodu, jak ponownych prób, to samo zamówienie biznesowe będą przetwarzane tylko raz.

Jest to realizowane przez zawijania polecenia biznesowego (w tym przypadku CreateOrderCommand) i osadzanie go w ogólnym IdentifiedCommand, który jest śledzony przez identyfikator każdej wiadomości przechodzącej przez sieć, która musi być idempotentny.

W poniższym kodzie widać, że IdentifiedCommand jest niczym więcej niż DTO z i ID oraz opakowanym obiektem polecenia biznesowego.

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

Następnie CommandHandler dla IdentifiedCommand nazwie [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) będzie w zasadzie sprawdzić, czy identyfikator pochodzących jako część wiadomości już istnieje w tabeli. Jeśli już istnieje, to polecenie nie zostanie ponownie przetworzone, więc zachowuje się jako polecenie idempotent. Ten kod infrastruktury jest `_requestManager.ExistAsync` wykonywany przez wywołanie metody poniżej.

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

Ponieważ IdentifiedCommand działa jak koperta polecenia biznesowego, gdy polecenie biznesowe musi być przetworzone, ponieważ nie jest powtarzającym się identyfikatorem, to przyjmuje to wewnętrzne polecenie biznesowe i `_mediator.Send(message.Command)`ponownie przesyła je do mediatora, jak w ostatniej części kodu pokazanej powyżej podczas uruchamiania , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

W ten sposób połączy się i uruchomi program obsługi poleceń biznesowych, w tym przypadku [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) który jest uruchomiony transakcje względem bazy danych Zamawianie, jak pokazano w poniższym kodzie.

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a>Rejestrowanie typów używanych przez MediatR

Aby MediatR być świadomi klas obsługi poleceń, należy zarejestrować klasy mediatora i klas obsługi poleceń w kontenerze IoC. Domyślnie MediatR używa Autofac jako kontenera IoC, ale można również użyć wbudowanego kontenera ASP.NET Core IoC lub innego kontenera obsługiwanego przez MediatR.

Poniższy kod pokazuje, jak zarejestrować typy i polecenia Mediatora podczas korzystania z modułów Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

To jest, gdy "magia się dzieje" z MediatR.

Ponieważ każdy program obsługi `IAsyncRequestHandler<T>` poleceń implementuje interfejs ogólny, podczas rejestrowania `RegisteredAssemblyTypes` zestawów, `IAsyncRequestHandler` kod rejestruje `CommandHandlers` wszystkie `Commands`typy oznaczone jako `CommandHandler` odnoszące się do ich , dzięki relacji podanej w klasie, jak w poniższym przykładzie:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Jest to kod, który koreluje polecenia z programami obsługi poleceń. Program obsługi jest tylko prostą klasą, ale dziedziczy z `RequestHandler<T>`, gdzie T jest typem polecenia, a MediatR upewnia się, że jest wywoływany z poprawnym ładunkiem (poleceniem).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Stosowanie problemów przekrojowych podczas przetwarzania poleceń za pomocą zachowań w mediatR

Jest jeszcze jedna rzecz: możliwość zastosowania przekrojowych obaw do rurociągu mediatora. Można również zobaczyć na końcu kodu modułu rejestracji Autofac, jak rejestruje typ zachowania, w szczególności niestandardowe LoggingBehavior klasy i ValidatorBehavior klasy. Ale można dodać inne zachowania niestandardowe, zbyt.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

Że [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy można zaimplementować jako następujący kod, który rejestruje informacje o program obsługi polecenia wykonywane i czy zakończyło się pomyślnie, czy nie.

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

Tylko przez implementowanie tej klasy zachowania i rejestrując go w potoku (w MediatorModule powyżej), wszystkie polecenia przetwarzane za pośrednictwem MediatR będzie rejestrowanie informacji o wykonaniu.

EShopOnContainers zamawiania mikrousługi stosuje również drugie zachowanie dla podstawowych sprawdzania poprawności, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy, która opiera się na biblioteki [FluentValidation,](https://github.com/JeremySkinner/FluentValidation) jak pokazano w poniższym kodzie:

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

Zachowanie w tym miejscu jest wywoływanie wyjątku, jeśli sprawdzanie poprawności nie powiedzie się, ale można również zwrócić wynik obiektu, zawierający wynik polecenia, jeśli się powiedzie lub komunikatów sprawdzania poprawności w przypadku, gdy nie. Prawdopodobnie ułatwiłoby to wyświetlanie wyników sprawdzania poprawności dla użytkownika.

Następnie, na podstawie biblioteki [FluentValidation,](https://github.com/JeremySkinner/FluentValidation) utworzyliśmy sprawdzanie poprawności danych przekazanych za pomocą CreateOrderCommand, jak w poniższym kodzie:

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

Można utworzyć dodatkowe weryfikacje. Jest to bardzo czysty i elegancki sposób implementacji sprawdzania poprawności poleceń.

W podobny sposób można zaimplementować inne zachowania dla dodatkowych aspektów lub przekrojowe obawy, które mają być stosowane do poleceń podczas ich obsługi.

#### <a name="additional-resources"></a>Zasoby dodatkowe

##### <a name="the-mediator-pattern"></a>Wzór mediatora

- **Wzór mediatora** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Wzór dekoratora

- **Wzór dekoratora** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** Repozytorium GitHub. \
  <https://github.com/jbogard/MediatR>

- **CQRS z MediatR i AutoMapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Umieść kontrolery na diecie: POSTs i polecenia.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Rozwiązywanie problemów przekrojowych za pomocą rurociągu mediatora** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS i REST: idealne dopasowanie** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Przykłady potoku MediatR** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Pionowe uchwyty testowe do MediatR i ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Rozszerzenia MediatR dla iniekcji zależności firmy Microsoft wydane** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Płynna walidacja

- **Jeremy Skinner. FluentValidation.** Repozytorium GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Poprzedni](microservice-application-layer-web-api-design.md)
> [następny](../implement-resilient-applications/index.md)
