---
title: Implementowanie warstwy aplikacji mikrousług za pomocą internetowego interfejsu API
description: Zrozumienie iniekcji zależności i wzorców mediatora i ich szczegóły implementacji w warstwie aplikacji interfejsu API sieci Web.
ms.date: 01/30/2020
ms.openlocfilehash: a88f3bfd11ea06df085ca82ed7265cb37006fc31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502447"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Użyj funkcji Iniekcji zależności, aby wstrzyknąć obiekty infrastruktury do warstwy aplikacji

Jak wspomniano wcześniej, warstwa aplikacji może być zaimplementowana jako część artefaktu (zestawu), który budujesz, na przykład w ramach projektu interfejsu API sieci Web lub projektu aplikacji sieci Web MVC. W przypadku mikrousługi zbudowanej z ASP.NET Core warstwa aplikacji będzie zwykle biblioteką interfejsu API sieci Web. Jeśli chcesz oddzielić to, co pochodzi z ASP.NET Core (jego infrastruktury oraz kontrolerów) od niestandardowego kodu warstwy aplikacji, można również umieścić warstwę aplikacji w oddzielnej bibliotece klas, ale jest to opcjonalne.

Na przykład kod warstwy aplikacji mikrousługi zamawiania jest bezpośrednio implementowany jako część projektu **Ordering.API** (ASP.NET core web api projektu), jak pokazano na rysunku 7-23.

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Zrzut ekranu przedstawiający mikrousługę Ordering.API w Eksploratorze rozwiązań.":::
Widok Eksploratora rozwiązań mikrousługi Ordering.API, przedstawiający podfoldery w folderze Aplikacji: Zachowania, Polecenia, DomainEventHandlers, IntegrationEvents, Models, Queries i Validations.
:::image-end:::

**Rysunek 7-23**. Warstwa aplikacji w projekcie interfejsu API interfejsu API ASP.NET Core Web API

ASP.NET Core zawiera prosty [wbudowany kontener IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowany przez interfejs IServiceProvider), który domyślnie obsługuje iniekcji konstruktora i ASP.NET udostępnia niektóre usługi za pośrednictwem DI. ASP.NET Core używa *terminu usługa* dla każdego z typów, które rejestrują, które zostaną wstrzyknięte za pośrednictwem DI. Skonfigurować wbudowane usługi kontenera w ConfigureServices metody w klasie startowej aplikacji. Zależności są implementowane w usługach, które wymaga typu i że można zarejestrować się w kontenerze IoC.

Zazwyczaj chcesz wstrzyknąć zależności, które implementują obiekty infrastruktury. Bardzo typowa zależność do wstrzykiwania jest repozytorium. Ale można wstrzyknąć wszelkie inne zależności infrastruktury, które mogą mieć. Dla prostszych implementacji można bezpośrednio wstrzyknąć jednostki pracy obiektu wzorca (EF DbContext obiektu), ponieważ DBContext jest również implementacja obiektów trwałości infrastruktury.

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

Klasa używa wstrzykuje repozytoriów do wykonania transakcji i utrwalić zmiany stanu. Nie ma znaczenia, czy ta klasa jest programobsługi poleceń, ASP.NET core web api metody kontrolera lub [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Ostatecznie jest to prosta klasa, która używa repozytoriów, jednostek domeny i innych koordynacji aplikacji w sposób podobny do programu obsługi poleceń. Iniekcji zależności działa w ten sam sposób dla wszystkich wymienionych klas, jak w przykładzie przy użyciu DI na podstawie konstruktora.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Rejestrowanie typów implementacji zależności i interfejsów lub abstrakcji

Przed użyciem obiektów wstrzykuje za pomocą konstruktorów, musisz wiedzieć, gdzie zarejestrować interfejsy i klasy, które produkują obiekty wstrzykiwane do klas aplikacji za pośrednictwem DI. (Podobnie jak DI na podstawie konstruktora, jak pokazano wcześniej.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Użyj wbudowanego kontenera IoC dostarczonego przez ASP.NET Core

Korzystając z wbudowanego kontenera IoC dostarczonego przez ASP.NET Core, należy zarejestrować typy, które mają zostać wstrzyknięte w metodzie ConfigureServices w pliku Startup.cs, tak jak w poniższym kodzie:

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

Najczęstszym wzorcem podczas rejestrowania typów w kontenerze IoC jest zarejestrowanie pary typów — interfejsu i powiązanej z nim klasy implementacji. Następnie podczas żądania obiektu z kontenera IoC za pośrednictwem dowolnego konstruktora, należy zażądać obiektu określonego typu interfejsu. Na przykład w poprzednim przykładzie ostatni wiersz stwierdza, że gdy którykolwiek z konstruktorów mają zależność od IMyCustomRepository (interfejs lub abstrakcji), kontener IoC wstrzyknie wystąpienie implementacji MyCustomSQLServerRepository Klasa.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Używanie biblioteki Scrutor do automatycznej rejestracji typów

Korzystając z DI w .NET Core, można mieć możliwość skanowania zestawu i automatycznie zarejestrować jego typy zgodnie z konwencją. Ta funkcja nie jest obecnie dostępna w ASP.NET Core. Można jednak użyć biblioteki [Scrutor](https://github.com/khellang/Scrutor) do tego celu. Takie podejście jest wygodne, gdy masz dziesiątki typów, które muszą być zarejestrowane w kontenerze IoC.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Mateusz Król. Rejestracja usług w Scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** Repozytorium GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Użyj Autofac jako pojemnika IoC

Można również użyć dodatkowych kontenerów IoC i podłączyć je do potoku ASP.NET Core, jak w mikrousługi zamawiania w eShopOnContainers, który używa [Autofac](https://autofac.org/). Korzystając z Autofac zazwyczaj zarejestrować typy za pomocą modułów, które umożliwiają dzielenie typów rejestracji między wiele plików w zależności od tego, gdzie są typy, tak jak można mieć typy aplikacji rozproszone w wielu bibliotekach klas.

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

Autofac posiada również funkcję [skanowania złożeń i rejestrowania typów według konwencji nazw.](https://autofac.readthedocs.io/en/latest/register/scanning.html)

Proces rejestracji i pojęcia są bardzo podobne do sposobu rejestrowania typów za pomocą wbudowanego kontenera ASP.NET Core IoC, ale składnia podczas korzystania z Autofac jest nieco inna.

W przykładowym kodzie abstrakcji IOrderRepository jest rejestrowany wraz z klasy implementacji OrderRepository. Oznacza to, że za każdym razem, gdy konstruktor deklaruje zależność za pośrednictwem abstrakcji iOrderRepository lub interfejsu, kontener IoC wstrzyknie wystąpienie OrderRepository klasy.

Typ zakresu wystąpienia określa sposób, w jaki wystąpienie jest współużytkowane między żądaniami dla tej samej usługi lub zależności. Po nałożeniu żądania zależności kontener IoC może zwrócić następujące elementy:

- Pojedyncze wystąpienie na zakres istnienia (określone w ASP.NET kontenerze Core IoC jako *zakres).*

- Nowe wystąpienie na zależność (określane w ASP.NET kontenerze Core IoC jako *przejściowe).*

- Pojedyncze wystąpienie współużytkowane przez wszystkie obiekty przy użyciu kontenera IoC (określane go w kontenerze ASP.NET Core IoC jako *singleton).*

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do wstrzykiwań zależności w ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficjalna dokumentacja. \
  <https://docs.autofac.org/en/latest/>

- **Porównanie ASP.NET okresy istnienia kontenera Core IoC z zakresami wystąpienia kontenera Autofac IoC — Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementowanie wzorców obsługi poleceń i poleceń

W przykładzie Konstruktora DI-through pokazano w poprzedniej sekcji kontener IoC wstrzykiwania repozytoriów za pośrednictwem konstruktora w klasie. Ale dokładnie, gdzie były wstrzykiwane? W prostym interfejsie API sieci Web (na przykład mikrousługi katalogu w eShopOnContainers) wstrzyknąć je na poziomie kontrolerów MVC, w konstruktorze kontrolera, jako część potoku żądania ASP.NET Core. Jednak w początkowym kodzie tej sekcji [(CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy z Usługi Ordering.API w eShopOnContainers), wstrzyknięcie zależności odbywa się za pośrednictwem konstruktora określonego programu obsługi poleceń. Wyjaśnijmy, czym jest program obsługi poleceń i dlaczego chcesz go używać.

Wzorzec polecenia jest nierozerwalnie związane z wzorcem CQRS, który został wprowadzony wcześniej w tym przewodniku. CQRS ma dwie strony. Pierwszym obszarem są zapytania, za pomocą uproszczonych zapytań z [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, co zostało wyjaśnione wcześniej. Drugi obszar to polecenia, które są punktem wyjścia dla transakcji, a kanał wejściowy spoza usługi.

Jak pokazano na rysunku 7-24, wzorzec jest oparty na akceptowaniu poleceń od strony klienta, przetwarzaniu ich na podstawie reguł modelu domeny i wreszcie utrwalania stanów z transakcjami.

![Diagram przedstawiający przepływ danych wysokiego poziomu z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

**Rysunek 7-24**. Widok wysokiego poziomu poleceń lub "po stronie transakcyjnej" we wzorcu CQRS

Rysunek 7-24 pokazuje, że aplikacja interfejsu ze strony interfejsu `CommandHandler`i zesłania za pośrednictwem interfejsu API, który pobiera do , który zależy od modelu domeny i infrastruktury, aby zaktualizować bazę danych.

### <a name="the-command-class"></a>Klasa polecenia

Polecenie jest żądaniem dla systemu do wykonania akcji, która zmienia stan systemu. Polecenia są konieczne i powinny być przetwarzane tylko raz.

Ponieważ polecenia są imperatywami, są one zazwyczaj nazwane z czasownikiem w nastroju imperatywu (na przykład "create" lub "update" i mogą zawierać typ agregacji, takich jak CreateOrderCommand. W przeciwieństwie do zdarzenia, polecenie nie jest faktem z przeszłości; jest to tylko wniosek, a zatem można go odmów odpowiedzieć.

Polecenia mogą pochodzić z interfejsu użytkownika w wyniku zainicjowania żądania przez użytkownika lub od menedżera procesów, gdy menedżer procesów kieruje agregat do wykonania akcji.

Ważną cechą polecenia jest to, że powinno być przetwarzane tylko raz przez jednego odbiornika. Dzieje się tak, ponieważ polecenie jest pojedynczą akcją lub transakcją, którą chcesz wykonać w aplikacji. Na przykład to samo polecenie tworzenia zamówienia nie powinny być przetwarzane więcej niż jeden raz. Jest to istotna różnica między poleceniami i zdarzeniami. Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług może być zainteresowanych zdarzeniem.

Ponadto ważne jest, aby polecenie było przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentnością. Polecenie jest idempotentności, jeśli można go wykonać wiele razy bez zmiany wyniku, ze względu na charakter polecenia lub ze względu na sposób, w jaki system obsługuje polecenie.

Dobrą praktyką jest wykonywanie poleceń i aktualizacji idempotentności, gdy ma to sens zgodnie z regułami biznesowymi i niezmiennymi regułami domeny. Na przykład, aby użyć tego samego przykładu, jeśli z jakiegokolwiek powodu (logika ponawiania prób, hacking, itp.) to samo polecenie CreateOrder dociera do systemu wiele razy, powinieneś być w stanie go zidentyfikować i upewnić się, że nie tworzysz wielu zamówień. Aby to zrobić, należy dołączyć pewnego rodzaju tożsamości w operacjach i określić, czy polecenie lub aktualizacja została już przetworzona.

Polecenie wysyłasz do jednego odbiornika; nie publikujesz polecenia. Publikowanie jest dla zdarzeń, które stwierdzają fakt, że coś się stało i może być interesujące dla odbiorców zdarzeń. W przypadku zdarzeń wydawca nie ma wątpliwości co do tego, które odbiorniki otrzymują zdarzenie lub co robią. Ale zdarzenia domeny lub integracji to inna historia już wprowadzona w poprzednich sekcjach.

Polecenie jest implementowane z klasą, która zawiera pola danych lub kolekcje ze wszystkimi informacjami, które są potrzebne do wykonania tego polecenia. Polecenie jest specjalnym rodzajem obiektu transferu danych (DTO), który jest specjalnie używany do żądania zmian lub transakcji. Samo polecenie jest oparte na dokładnie tych informacjach, które są potrzebne do przetwarzania polecenia i nic więcej.

W poniższym przykładzie `CreateOrderCommand` przedstawiono klasę uproszczoną. Jest to niezmienne polecenie, które jest używane w mikrousługi porządkowania w eShopOnContainers.

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

Zasadniczo klasa polecenia zawiera wszystkie dane potrzebne do wykonywania transakcji biznesowych przy użyciu obiektów modelu domeny. W związku z tym polecenia są po prostu struktury danych, które zawierają dane tylko do odczytu i nie zachowanie. Nazwa polecenia wskazuje jego przeznaczenie. W wielu językach, takich jak C#, polecenia są reprezentowane jako klasy, ale nie są prawdziwe klasy w sensie rzeczywistym obiektowych.

Jako dodatkową cechę polecenia są niezmienne, ponieważ oczekiwane użycie polega na tym, że są one przetwarzane bezpośrednio przez model domeny. Nie muszą się zmieniać w przewidywanym okresie życia. W klasie C# niezmienność można osiągnąć, nie mając żadnych ustawiających lub innych metod, które zmieniają stan wewnętrzny.

Należy pamiętać, że jeśli zamierzasz lub oczekujesz poleceń, aby przejść przez proces serializacji/deserializacji, właściwości muszą mieć private setter i `[DataMember]` (lub `[JsonProperty]`) atrybut. W przeciwnym razie deserializator nie będzie mógł zrekonstruować obiektu w miejscu docelowym z wymaganymi wartościami. Można również użyć prawdziwie tylko do odczytu właściwości, jeśli klasa ma konstruktora z parametrami dla wszystkich właściwości, ze `[JsonConstructor]`zwykłą konwencją nazewnictwa wielbłądacase i adnotować konstruktora jako . Jednak ta opcja wymaga więcej kodu.

Na przykład klasa polecenia do tworzenia zamówienia jest prawdopodobnie podobna pod względem danych do kolejności, którą chcesz utworzyć, ale prawdopodobnie nie potrzebujesz tych samych atrybutów. Na przykład `CreateOrderCommand` nie ma identyfikatora zamówienia, ponieważ zamówienie nie zostało jeszcze utworzone.

Wiele klas poleceń może być proste, wymaga tylko kilka pól o niektórych stan, który musi zostać zmieniony. Miałoby to miejsce, gdyby tylko zmieniłeś status zamówienia z "w toku" na "płatny" lub "wysłany", używając polecenia podobnego do następującego:

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

Niektórzy deweloperzy sprawiają, że ich obiekty żądania interfejsu i systemu ui oddzielnie od ich polecenia DTOs, ale to tylko kwestia preferencji. Jest to żmudna separacja z niedużą wartością dodaną, a obiekty mają prawie dokładnie ten sam kształt. Na przykład w eShopOnContainers niektóre polecenia pochodzą bezpośrednio od strony klienta.

### <a name="the-command-handler-class"></a>Klasa obsługi polecenia

Należy zaimplementować klasę obsługi określonego polecenia dla każdego polecenia. Tak działa wzorzec i w tym miejscu użyjesz obiektu polecenia, obiektów domeny i obiektów repozytorium infrastruktury. Program obsługi poleceń jest w rzeczywistości sercem warstwy aplikacji pod względem CQRS i DDD. Jednak cała logika domeny powinna być zawarta w klasach domeny — w obrębie zagregowanych katalogów głównych (jednostek głównych), jednostek podrzędnych lub [usług domeny,](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)ale nie w programie obsługi poleceń, który jest klasą z warstwy aplikacji.

Klasa obsługi poleceń oferuje silny krok w drodze do osiągnięcia zasady pojedynczej odpowiedzialności (SRP) wymienione w poprzedniej sekcji.

Program obsługi poleceń odbiera polecenie i uzyskuje wynik z agregacji, która jest używana. Wynik powinien być pomyślne wykonanie polecenia lub wyjątek. W przypadku wyjątku stan systemu powinien być niezmieniony.

Program obsługi poleceń zwykle wykonuje następujące kroki:

- Odbiera obiekt polecenia, jak DTO (od [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub innego obiektu infrastruktury).

- Sprawdza, czy polecenie jest prawidłowe (jeśli nie zostanie zweryfikowane przez mediatora).

- Tworzy wystąpienia agregacji głównej, która jest celem bieżącego polecenia.

- Wykonuje metodę w wystąpieniu głównego agregacji, uzyskując wymagane dane z polecenia.

- Utrzymuje nowy stan agregacji do powiązanej bazy danych. Ta ostatnia operacja jest rzeczywistą transakcją.

Zazwyczaj program obsługi poleceń dotyczy pojedynczej agregacji napędzanej przez jego zagregowanego roota (jednostki głównej). Jeśli odbiór pojedynczego polecenia ma wpływ na wiele agregatów, można użyć zdarzeń domeny do propagowania stanów lub akcji w wielu agregatach.

Ważną kwestią jest to, że podczas przetwarzania polecenia, wszystkie logiki domeny powinny być wewnątrz modelu domeny (agregaty), w pełni hermetyzowane i gotowe do testowania jednostkowego. Program obsługi poleceń działa tylko jako sposób na uzyskanie modelu domeny z bazy danych i jako ostatni krok, aby poinformować warstwę infrastruktury (repozytoria), aby utrwalić zmiany po zmianie modelu. Zaletą tego podejścia jest to, że można refaktoryzacji logiki domeny w izolowanym, w pełni hermetyzowane, bogate, behawioralne modelu domeny bez zmiany kodu w warstwach aplikacji lub infrastruktury, które są poziom instalacji wodno-kanalizacyjnej (programy obsługi poleceń, Interfejs API sieci Web, repozytoriów itp.).

Gdy programy obsługi poleceń stają się złożone, z zbyt dużą logiką, która może być zapachem kodu. Przejrzyj je, a jeśli znajdziesz logikę domeny, refaktoryzuj kod, aby przenieść to zachowanie domeny do metod obiektów domeny (jednostki głównej agregacji i podrzędnej).

Jako przykład klasy obsługi poleceń, poniższy kod `CreateOrderCommandHandler` pokazuje tę samą klasę, która została wyświetlona na początku tego rozdziału. W takim przypadku chcemy wyróżnić Handle metody i operacje z obiektów modelu domeny/agregacji.

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

Są to dodatkowe kroki, które powinien wykonać program obsługi poleceń:

- Użyj danych polecenia do pracy z zagregowanych metod i zachowania roota.

- Wewnętrznie w obrębie obiektów domeny, podnieść zdarzenia domeny podczas wykonywania transakcji, ale jest przezroczysty z punktu widzenia obsługi poleceń.

- Jeśli wynik operacji agregacji zakończy się pomyślnie i po zakończeniu transakcji, podnieść zdarzenia integracji. (Mogą one również być wywoływane przez klasy infrastruktury, takie jak repozytoria).

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Mark Seemann. Na granicach aplikacje nie są zorientowane obiektowe** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Polecenia i zdarzenia** \
  <https://cqrs.nu/Faq/commands-and-events>

- **Co robi program obsługi poleceń?** \
  <https://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Wzorce poleceń domeny — programy obsługi** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Wzorce poleceń domeny — sprawdzanie poprawności** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Potok procesu polecenia: jak wyzwolić program obsługi poleceń

Następne pytanie brzmi, jak wywołać program obsługi poleceń. Można ręcznie wywołać go z każdego powiązanego kontrolera ASP.NET Core. Jednak takie podejście byłoby zbyt powiązane i nie jest idealne.

Pozostałe dwie główne opcje, które są zalecanymi opcjami, to:

- Za pośrednictwem artefaktu wzorca mediatora w pamięci.

- Z kolejki komunikatów asynchronicznych, pomiędzy kontrolerów i programów obsługi.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Użyj wzorca mediatora (w pamięci) w potoku poleceń

Jak pokazano na rysunku 7-25, w podejściu CQRS używasz inteligentnego mediatora, podobnego do magistrali w pamięci, która jest wystarczająco inteligentna, aby przekierować do prawego programu obsługi poleceń na podstawie typu odbieranego polecenia lub DTO. Pojedyncze czarne strzałki między składnikami reprezentują zależności między obiektami (w wielu przypadkach wstrzykuje się przez DI) z ich powiązanych interakcji.

![Diagram przedstawiający bardziej szczegółowy przepływ danych z klienta do bazy danych.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

**Rysunek 7-25**. Używanie wzorca mediatora w procesie w jednej mikrousłudze CQRS

Powyższy diagram przedstawia powiększenie z obrazu 7-24: kontroler ASP.NET Core wysyła polecenie do potoku poleceń MediatR, dzięki czemu udają się do odpowiedniego programu obsługi.

Powodem, dla którego użycie wzorca mediatora ma sens, jest to, że w aplikacjach przedsiębiorstwa żądania przetwarzania mogą się komplikować. Chcesz mieć możliwość dodania otwartej liczby problemów przekrojowych, takich jak rejestrowanie, sprawdzanie poprawności, inspekcje i zabezpieczenia. W takich przypadkach można polegać na potoku mediatora (patrz [wzorzec mediatora),](https://en.wikipedia.org/wiki/Mediator_pattern)aby zapewnić środki dla tych dodatkowych zachowań lub problemów przekrojowych.

Mediator jest obiektem, który hermetyzuje "jak" tego procesu: koordynuje wykonywanie na podstawie stanu, sposób obsługi poleceń jest wywoływany lub ładunku, który podajesz do obsługi. Za pomocą składnika mediatora można stosować problemy przekrojowe w sposób scentralizowany i przejrzysty, stosując dekoratory (lub [zachowania potoku](https://github.com/jbogard/MediatR/wiki/Behaviors) od [MediatR 3).](https://www.nuget.org/packages/MediatR/3.0.0) Aby uzyskać więcej informacji, zobacz [wzorzec dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratory i zachowania są podobne do [programowania zorientowanego na aspekty (AOP),](https://en.wikipedia.org/wiki/Aspect-oriented_programming)stosowane tylko do określonego potoku procesu zarządzanego przez składnik mediatora. Aspekty w aop, które implementują przekrojowe problemy są stosowane na podstawie *aspektu tkaczy* wstrzykiwanych w czasie kompilacji lub na podstawie przechwytywania wywołania obiektu. Oba typowe podejścia AOP są czasami mówi się, że działa "jak magia", ponieważ nie jest łatwo zobaczyć, jak AOP wykonuje swoją pracę. Podczas radzenia sobie z poważnymi problemami lub błędami, AOP może być trudne do debugowania. Z drugiej strony te dekoratory/zachowania są jawne i stosowane tylko w kontekście mediatora, więc debugowanie jest znacznie bardziej przewidywalne i łatwe.

Na przykład w eShopOnContainers zamawiania mikrousługi, zaimplementowaliśmy dwa przykładowe zachowania, [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy i [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy. Implementacja zachowań jest wyjaśnione w następnej sekcji, pokazując, jak eShopOnContainers używa [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Używanie kolejek komunikatów (poza proc) w potoku polecenia

Innym wyborem jest użycie komunikatów asynchronicznych opartych na brokerach lub kolejkach komunikatów, jak pokazano na rysunku 7-26. Ta opcja może być również połączona ze składnikiem mediatora tuż przed programem obsługi poleceń.

![Diagram przedstawiający przepływ danych przy użyciu kolejki komunikatów ha.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

**Rysunek 7-26**. Korzystanie z kolejek komunikatów (poza procesem i komunikacji międzyprocesowej) z poleceniami CQRS

Potok polecenia może być również obsługiwany przez kolejkę komunikatów o wysokiej dostępności, aby dostarczyć polecenia do odpowiedniego programu obsługi. Za pomocą kolejek komunikatów do akceptowania poleceń może dodatkowo skomplikować potoku polecenia, ponieważ prawdopodobnie trzeba będzie podzielić potoku na dwa procesy połączone za pośrednictwem kolejki komunikatów zewnętrznych. Mimo to należy go używać, jeśli trzeba mieć lepszą skalowalność i wydajność na podstawie asynchronicznych wiadomości. Należy wziąć pod uwagę, że w przypadku rysunku 7-26 kontroler po prostu księguje komunikat polecenia w kolejce i zwraca. Następnie programy obsługi poleceń przetwarzają wiadomości we własnym tempie. Jest to bardzo korzystne dla kolejek: kolejka komunikatów może działać jako bufor w przypadkach, gdy potrzebna jest hiperskalowalność, na przykład dla zapasów lub innego scenariusza z dużą ilością danych przychodzących.

Jednak ze względu na asynchroniczny charakter kolejek komunikatów, należy dowiedzieć się, jak komunikować się z aplikacją kliencką o powodzeniu lub niepowodzeniu procesu polecenia. Z reguły nigdy nie należy używać poleceń "ogień i zapomnij". Każda aplikacja biznesowa musi wiedzieć, czy polecenie zostało przetworzone pomyślnie, a przynajmniej zatwierdzone i zaakceptowane.

W związku z tym jest w stanie odpowiedzieć na klienta po poważaniu komunikatu polecenia, który został przesłany do kolejki asynchronicznej zwiększa złożoność systemu, w porównaniu do procesu polecenia w procesie, który zwraca wynik operacji po uruchomieniu transakcji. Przy użyciu kolejek może być konieczne zwrócenie wyniku procesu polecenia za pomocą innych komunikatów wyników operacji, które będą wymagały dodatkowych składników i komunikacji niestandardowej w systemie.

Dodatkowo, async polecenia są jednokierunkowe polecenia, które w wielu przypadkach mogą nie być potrzebne, jak wyjaśniono w następujących ciekawych wymiany między Burtsev Alexey i Greg Young w [rozmowie online:](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)

> \[Burtsev Alexey\] znajduję wiele kodu, w którym ludzie używają obsługi poleceń asynchronicznej lub jednokierunkowych komunikatów poleceń bez żadnego powodu ( nie wykonują długiej operacji, nie wykonują zewnętrznego kodu asynchronicznego, nawet nie przekraczają granicy aplikacji, aby używać magistrali komunikatów). Dlaczego wprowadzają tę niepotrzebną złożoność? I rzeczywiście, nie widziałem przykład kodu CQRS z blokowania obsługi poleceń do tej pory, choć będzie działać dobrze w większości przypadków.
>
> \[Greg\] \[Young ... \] asynchroniczne polecenie nie istnieje; to kolejne wydarzenie. Jeśli muszę zaakceptować to, co mi wysłać i podnieść zdarzenie, jeśli się nie \[zgadzam, to już nie\]mówisz mi zrobić coś, co jest, to nie jest polecenie . Mówisz mi, że coś zostało zrobione. Na początku wydaje się to niewielką różnicą, ale ma wiele implikacji.

Polecenia asynchroniczne znacznie zwiększają złożoność systemu, ponieważ nie ma prostego sposobu wskazywania błędów. W związku z tym asynchroniczne polecenia nie są zalecane inne niż wtedy, gdy wymagania skalowania są potrzebne lub w szczególnych przypadkach podczas komunikowania mikrousług wewnętrznych za pośrednictwem wiadomości. W takich przypadkach należy zaprojektować oddzielny system raportowania i odzyskiwania dla awarii.

W początkowej wersji eShopOnContainers zdecydowaliśmy się użyć synchronicznego przetwarzania poleceń, rozpoczęte z żądań HTTP i napędzane przez wzorzec mediatora. To łatwo pozwala na zwrócenie sukcesu lub niepowodzenia procesu, jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.

W każdym przypadku powinna to być decyzja oparta na wymaganiach biznesowych aplikacji lub mikrousługi.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementowanie potoku procesu poleceń za pomocą wzorca mediatora (MediatR)

Jako przykładową implementację, ten przewodnik proponuje przy użyciu potoku w procesie na podstawie wzorca mediatora do kierowania poleceń polecenia i polecenia trasy, w pamięci, do obsługi poleceń po prawej stronie. W przewodniku zaproponowano również stosowanie [zachowań](https://github.com/jbogard/MediatR/wiki/Behaviors) w celu oddzielenia problemów przekrojowych.

Do implementacji w .NET Core dostępnych jest wiele bibliotek open source, które implementują wzorzec mediatora. Biblioteka używana w tym przewodniku jest biblioteką open source [MediatR](https://github.com/jbogard/MediatR) (utworzoną przez Jimmy'ego Bogarda), ale można użyć innego podejścia. MediatR to mała i prosta biblioteka, która umożliwia przetwarzanie wiadomości w pamięci, takich jak polecenie, podczas stosowania dekoratorów lub zachowań.

Za pomocą wzorca mediatora pomaga zmniejszyć sprzężenia i izolować obawy żądanej pracy, podczas automatycznego łączenia się z obsługi, która wykonuje tę pracę — w tym przypadku do obsługi poleceń.

Innym dobrym powodem, aby korzystać z wzoru Mediator został wyjaśniony przez Jimmy Bogard podczas przeglądu tego przewodnika:

> Myślę, że warto wspomnieć o testach tutaj - zapewnia ładne spójne okno na zachowanie systemu. Żądanie w, odpowiedź-out. Odkryliśmy, że ten aspekt jest dość cenny w budowaniu konsekwentnie zachowujących się testów.

Najpierw przyjrzyjmy się przykładowemu kontrolerowi WebAPI, w którym faktycznie użyjesz obiektu mediatora. Jeśli nie używasz obiektu mediatora, należy wstrzyknąć wszystkie zależności dla tego kontrolera, takie rzeczy jak obiekt rejestratora i inne. W związku z tym konstruktor będzie dość skomplikowane. Z drugiej strony, jeśli używasz obiektu mediatora, konstruktor kontrolera może być o wiele prostsze, z zaledwie kilku zależności zamiast wielu zależności, jeśli miał jeden na operację przekrojową, jak w poniższym przykładzie:

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

Widać, że mediator zapewnia czysty i chudego konstruktora kontrolera interfejsu API sieci Web. Ponadto w ramach metod kontrolera kod wysyłania polecenia do obiektu mediatora jest prawie jeden wiersz:

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

### <a name="implement-idempotent-commands"></a>Implementowanie poleceń idempotentności

W **eShopOnContainers**, bardziej zaawansowany przykład niż powyżej jest przesyłanie CreateOrderCommand obiektu z mikrousługi zamawiania. Ale ponieważ proces biznesowy zamawiania jest nieco bardziej skomplikowane i, w naszym przypadku, faktycznie rozpoczyna się w mikrousługi koszyka, ta akcja przesyłania CreateOrderCommand obiekt jest wykonywany z integration-event handler o nazwie [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) zamiast prostego kontrolera WebAPI wywoływane z aplikacji klienta, jak w poprzednim przykładzie prostsze.

Niemniej jednak akcja przesyłania polecenia do MediatR jest bardzo podobna, jak pokazano w poniższym kodzie.

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

Jednak ten przypadek jest również nieco bardziej zaawansowany, ponieważ implementujemy również polecenia idempotentności. Proces CreateOrderCommand powinien być idempotentny, więc jeśli ten sam komunikat zostanie zduplikowany za pośrednictwem sieci, z jakiegokolwiek powodu, takiego jak ponownych prób, to samo zlecenie biznesowe zostanie przetworzone tylko raz.

Jest to realizowane przez zawijanie polecenia biznesowego (w tym przypadku CreateOrderCommand) i osadzanie go w ogólnym IdentifiedCommand, który jest śledzony przez identyfikator każdej wiadomości przychodzącej przez sieć, która musi być idempotentna.

W poniższym kodzie widać, że IdentifiedCommand jest niczym więcej niż DTO z i identyfikatorplus opakowany obiekt polecenia biznesowego.

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

Następnie CommandHandler dla IdentifiedCommand o nazwie [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) będzie w zasadzie sprawdzić, czy identyfikator najbliższych jako część wiadomości już istnieje w tabeli. Jeśli już istnieje, to polecenie nie zostanie ponownie przetworzone, więc zachowuje się jako polecenie idempotentności. Ten kod infrastruktury jest `_requestManager.ExistAsync` wykonywany przez wywołanie metody poniżej.

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

Ponieważ IdentifiedCommand działa jak koperta polecenia biznesowego, gdy polecenie biznesowe musi zostać przetworzone, ponieważ nie jest to identyfikator wielokrotny, to przyjmuje to wewnętrzne polecenie biznesowe i `_mediator.Send(message.Command)`ponownie przesyła je do mediatora, jak w ostatniej części kodu pokazanego powyżej podczas uruchamiania , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

W ten sposób będzie łączyć i uruchamiać program obsługi poleceń biznesowych, w tym przypadku [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) który jest uruchomiony transakcji względem bazy danych zamawiania, jak pokazano w poniższym kodzie.

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

Aby MediatR zdawać sobie sprawę z klas obsługi poleceń, należy zarejestrować klas mediatora i klasy obsługi poleceń w kontenerze IoC. Domyślnie MediatR używa Autofac jako kontenerii IoC, ale można również użyć wbudowanego kontenera ASP.NET Core IoC lub dowolnego innego kontenera obsługiwanego przez MediatR.

Poniższy kod pokazuje, jak zarejestrować typy i polecenia mediatora podczas korzystania z modułów Autofac.

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

To jest, gdy "magia dzieje się" z MediatR.

Ponieważ każdy program obsługi `IAsyncRequestHandler<T>` poleceń implementuje ogólny interfejs, podczas rejestrowania zestawów, `IAsyncRequestHandler` kod rejestruje `CommandHandlers` się `Commands`ze `CommandHandler` `RegisteredAssemblyTypes` wszystkimi typami oznaczonymi jako podczas ich, dzięki relacji podanej w klasie, jak w poniższym przykładzie:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Jest to kod, który koreluje polecenia z programami obsługi poleceń. Program obsługi jest tylko prostą klasą, `RequestHandler<T>`ale dziedziczy z , gdzie T jest typem polecenia, a MediatR upewnia się, że jest wywoływany przy poprawnym ładunku (polecenie).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Stosowanie problemów przekrojowych podczas przetwarzania poleceń za pomocą zachowań w MediatR

Jest jeszcze jedna rzecz: możliwość zastosowania przekrojowych problemów do rurociągu mediatora. Można również zobaczyć na końcu kodu modułu rejestracji Autofac, jak rejestruje typ zachowania, w szczególności niestandardowe loggingbehavior klasy i ValidatorBehavior klasy. Ale można dodać inne zachowania niestandardowe, zbyt.

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

Że [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy można zaimplementować jako następujący kod, który rejestruje informacje o programie obsługi poleceń są wykonywane i czy zakończyło się pomyślnie, czy nie.

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

Wystarczy implementując tę klasę zachowania i rejestrując ją w potoku (w mediatormodule powyżej), wszystkie polecenia przetwarzane za pośrednictwem MediatR będą rejestrowania informacji o wykonaniu.

EShopOnContainers zamawiania mikrousługi stosuje również drugie zachowanie dla podstawowych sprawdzania poprawności, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy, która opiera się na [fluentvalidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w następującym kodzie:

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

Zachowanie w tym miejscu jest zgłaszanie wyjątku, jeśli sprawdzanie poprawności nie powiedzie się, ale można również zwrócić obiekt wynik, zawierający wynik polecenia, jeśli się powiedzie lub komunikaty sprawdzania poprawności w przypadku, gdy nie. Prawdopodobnie ułatwiłoby to użytkownikowi wyświetlanie wyników sprawdzania poprawności.

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

Można utworzyć dodatkowe sprawdzania poprawności. Jest to bardzo czysty i elegancki sposób implementacji sprawdzania poprawności poleceń.

W podobny sposób można zaimplementować inne zachowania dla dodatkowych aspektów lub problemów przekrojowych, które mają być stosowane do poleceń podczas ich obsługi.

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

- **Umieść kontrolery na diecie: POSTs i poleceń.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Rozwiązywanie problemów przekrojowych za pomocą rurociągu mediatora** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS i REST: idealne dopasowanie** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Przykłady potoku MediatR** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Pionowe oprawy testowe plasterków dla MediatR i ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Rozszerzeń MediatR dla iniekcji zależności firmy Microsoft zwolniony** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Sprawna walidacja

- **Jeremy Skinner. FluentValidation.** Repozytorium GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Poprzedni](microservice-application-layer-web-api-design.md)
> [następny](../implement-resilient-applications/index.md)
