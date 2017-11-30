---
title: "Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Przy użyciu iniekcji zależności na iniekcję obiektów infrastruktury do warstwy aplikacji

Jak wspomniano wcześniej, można zaimplementować jako część artefaktu tworzysz, takie jak w projekcie interfejsu API sieci Web lub projektu aplikacji sieci web MVC warstwy aplikacji. W przypadku mikrousługi skompilowanej za pomocą platformy ASP.NET Core warstwy aplikacji będzie zazwyczaj biblioteki interfejsu API sieci Web. Aby oddzielić wkrótce z platformy ASP.NET Core (swoją infrastrukturę oraz kontrolerach) w kodzie warstwy aplikacji niestandardowych, można również umieścić warstwy aplikacji w bibliotece klas oddzielnych, ale jest to opcjonalne.

Na przykład kod warstwy aplikacji porządkowania mikrousługi bezpośrednio jest zaimplementowany jako część **Ordering.API** projekt (projekt interfejsu API platformy ASP.NET Core sieci Web), rysunek jako pokazano 9-19.

![](./media/image20.png)

**Rysunek 9-19**. Warstwa aplikacji w projekcie interfejsu API programu Ordering.API platformy ASP.NET Core sieci Web

Platformy ASP.NET Core obejmuje prostą [wbudowanych kontenera IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowane przez interfejsu IServiceProvider) obsługującej iniekcji konstruktora domyślnie i program ASP.NET udostępnia pewnych usług za pośrednictwem Podpisane. Termin korzysta z platformy ASP.NET Core *usługi* dla każdego z typów rejestrowania, które będą wstrzyknięte przez Podpisane. Należy skonfigurować usługi wbudowanych kontenerów w ConfigureServices metody w klasie uruchomienia aplikacji. Zależności są implementowane w usługach, które wymaga typu.

Zazwyczaj mają wstrzyknięcia zależności, które implementują obiektów infrastruktury. Zależność bardzo typowy iniekcję to repozytorium. Jednak można wstrzyknąć innych zależności infrastruktury, który może być. W przypadku prostszych implementacji może bezpośrednio uruchomić obiektu wzorzec jednostki pracy (obiektu EF DbContext), ponieważ DBContext jest również implementacji obiektów trwałości infrastruktury.

W poniższym przykładzie widać, jak oprogramowanie .NET Core wprowadza obiekty wymagane repozytorium za pośrednictwem konstruktora. Klasa jest programem obsługi, które omówimy w następnej sekcji.

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

Klasa używa wprowadzony repozytoria do wykonania transakcji i utrwalić zmiany stanu. Nie ma znaczenia, czy w tej klasy jest programem obsługi, metoda kontrolera interfejsu API platformy ASP.NET Core sieci Web, czy [usługi aplikacji DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Ostatecznie jest prostą klasę, który używa repozytoriów, jednostek domeny i innych koordynacji aplikacji w sposób podobny do obsługi polecenia. Taki sam sposób dla wszystkich wymienionych klas, jak pokazano w przykładzie przy użyciu Podpisane oparte na konstruktorze działa iniekcji zależności.

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Rejestrowanie typów wdrożenia zależności i interfejsów lub obiektów abstrakcyjnych

Przed użyciem obiekty dodane za pomocą konstruktorów, musisz wiedzieć, gdzie można zarejestrować interfejsów i klasy, które powodują powstanie obiektów do klasy Twojej aplikacji za pośrednictwem Podpisane. (Takich jak Podpisane na podstawie konstruktora, jak pokazano wcześniej.)

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>Za pomocą wbudowanych kontenera IoC pochodzącymi z platformy ASP.NET Core

Korzystając z wbudowanego kontenera IoC pochodzącymi z platformy ASP.NET Core, zarejestruj się typów, który chcesz wstawić w metodzie ConfigureServices w pliku Startup.cs, zgodnie z poniższym kodem:

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Najbardziej typowe wzorzec po rejestrowanie typów w kontenerze Inwersja kontroli można zarejestrować dwa typy — interfejs i jego klasa implementacji pokrewne. W przypadku żądania obiektu z kontenera IoC za pomocą dowolnego konstruktora, następnie zażądać obiektu określonego typu interfejsu. Na przykład w poprzednim przykładzie, ostatni wiersz stwierdza, że gdy dowolne z konstruktorów zależy od IMyCustomRepository (interfejsu lub abstrakcji), kontenera IoC będzie wstrzyknąć wystąpienie implementacji MyCustomSQLServerRepository Klasa.

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>Za pomocą biblioteki Scrutor typy automatycznej rejestracji

Używając Podpisane w .NET Core, możesz mieć możliwość skanowania zestawu i automatyczne rejestrowanie jego typów przez Konwencję. Ta funkcja nie jest obecnie dostępna w ASP.NET Core. Można jednak użyć [Scrutor](https://github.com/khellang/Scrutor) biblioteki w tym. Takie podejście jest wygodny w przypadku wielu typów, które muszą być zarejestrowane w Twojej kontenera IoC.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Matthew króla. Usługi w zarejestrowani Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang. Scrutor.** Repozytorium GitHub.
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>Przy użyciu Autofac jako kontenera IoC

Można również użyć dodatkowe kontenery Inwersja kontroli i podłącz je do potoku platformy ASP.NET Core, tak jak porządkowania mikrousługi w eShopOnContainers, który używa [Autofac](https://autofac.org/). Korzystając z Autofac zwykle należy zarejestrować typy za pośrednictwem modułów, dzięki której można podzielić typów rejestracji między wiele plików, w zależności od lokalizacji użytkownika typy, tak samo, jak można używać typów aplikacji rozproszone na wielu bibliotek klas.

Na przykład poniżej przedstawiono [modułu aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu z typami można wstrzyknąć.

```csharp
public class ApplicationModule
    :Autofac.Module
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

Proces rejestracji i pojęcia są bardzo podobne do sposób z wbudowanych kontenerem platformy ASP.NET Core dla systemu iOS można zarejestrować typy, ale składni, korzystając z Autofac różni się nieco.

W przykładowym kodzie abstrakcji IOrderRepository został zarejestrowany oraz klasa implementacji OrderRepository. Oznacza to, że zawsze, gdy Konstruktor jest deklarowanie zależności za pomocą abstrakcji IOrderRepository lub interfejsu, kontenera IoC będzie wstrzyknąć wystąpienia klasy OrderRepository.

Typ zakresu wystąpienia określa, jak wystąpienia są współużytkowane przez żądania dla tej samej usługi lub zależności. Po wysłaniu żądania jest zależność, kontenera IoC może zwrócić następujące czynności:

-   Jednego wystąpienia na okres istnienia zakresu (określone w kontenerze platformy ASP.NET Core IoC jako *zakres*).

-   Nowe wystąpienie na zależność (określone w kontenerze platformy ASP.NET Core IoC jako *przejściowa*).

-   Pojedyncze wystąpienie współużytkowana przez wszystkie obiekty przy użyciu kontenera IoC (określone w kontenerze platformy ASP.NET Core IoC jako *pojedyncze*).

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wprowadzenie do iniekcji zależności w platformy ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac.** Oficjalna dokumentacja.
    [*http://docs.autofac.org/en/Latest/*](http://docs.autofac.org/en/latest/)

-   **Torre de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>Implementowanie wzorce polecenia i program obsługi poleceń

W przykładzie Podpisane za pomocą konstruktora przedstawionym w poprzedniej sekcji kontenera IoC został wstrzyknięcie repozytoria za pośrednictwem Konstruktor w klasie. Ale dokładnie gdzie zostały one dodane? W przypadku prostego interfejsu API sieci Web (na przykład mikrousługi katalogu w eShopOnContainers) można wstrzyknąć na poziomie kontrolerów MVC, w Konstruktorze kontrolera. Jednak w początkowej kodu w tej sekcji ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy z usługi Ordering.API w eShopOnContainers), iniekcja zależności odbywa się za pośrednictwem konstruktora konkretnego polecenia Program obsługi. Daj nam wyjaśnić programu obsługi poleceń jest i dlaczego warto jej używać.

Wzorzec polecenia leżą jest powiązany z wzorca CQRS, który został wprowadzony wcześniej w tym przewodniku. CQRS ma dwie strony. Pierwszy obszar jest zapytania za pomocą uproszczonego zapytań z [Dapper](https://github.com/StackExchange/dapper-dot-net) ORM micro wyjaśniono wcześniej. Drugi ma poleceń, które są punkt początkowy dla transakcji i kanał wejściowy z poza usługi.

Jak pokazano w rysunku 9-20, wzorzec jest oparta na akceptowanie poleceń z po stronie klienta, przetwarzania je zgodnie z regułami modelu domeny, a na koniec utrwalanie stanów transakcji.

![](./media/image21.png)

**Rysunek 9-20**. Widok wysokiego poziomu poleceń lub "transakcyjne po stronie" we wzorcu CQRS

### <a name="the-command-class"></a>Klasy poleceń

Polecenie jest żądaniem systemu do wykonywania akcji zmieniającej stan systemu. Polecenia są konieczne i powinny być przetwarzane tylko raz.

Ponieważ polecenia priorytetów, są zwykle nazywane ze zleceniem w trybie stylu (na przykład "Utwórz" lub "Aktualizuj"), i może zawierać typu agregacji, na przykład CreateOrderCommand. W przeciwieństwie do zdarzenia polecenie nie jest faktów z przeszłości; jest tylko żądania, a w związku z tym można odmówić.

Polecenia można pochodzi z interfejsu użytkownika w wyniku inicjowanie żądanie użytkownika lub Menedżera procesu podczas Menedżera procesu jest kierowanie agregacji do wykonania akcji.

Istotne cechy polecenia jest, że powinien on tylko raz przetworzony przez jednego odbiorcę. Jest tak, ponieważ polecenie jest jednej akcji lub transakcji, które należy wykonać w aplikacji. Na przykład tego samego polecenia tworzenia kolejności nie powinny być przetwarzane więcej niż raz. Jest to ważna różnica między poleceń i zdarzeń. Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług mogą być zainteresowani zdarzenia.

Ponadto jest ważne, że polecenie przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentności. Polecenie jest idempotentności, jeśli jego mogą być wykonywane wiele razy bez zmiany wyników, z powodu charakteru polecenia lub ze względu na sposób system obsługi polecenia.

Jest dobrym rozwiązaniem, aby Twoje polecenia i aktualizuje idempotentności, gdy sens w ramach reguł biznesowych użytkownika domeny i invariants. Na przykład do użycia w tym samym przykładzie, jeśli jakiegokolwiek powodu (logika ponowień, przejęcie itp.) tego samego polecenia CreateOrder osiągnie system wielokrotnie, można zidentyfikować je i upewnij się, nie należy tworzyć wielu zamówień. Aby to zrobić, należy dołączyć określonego rodzaju tożsamości w operacjach i ustalić, czy polecenie lub aktualizacji został już przetworzony.

Wyślij polecenie do jednego odbiorcę; polecenie nie jest opublikować. Publikowanie jest dla zdarzeń integracji, które stanu fakt — coś się nie stało i mogą być interesujące dla odbiorcy zdarzeń. W przypadku zdarzeń wydawcy ma nie problemów, o których odbiorcy uzyskać zdarzenia lub co robią go. Ale zdarzeń integracji inny wątek już wprowadzone w poprzednich sekcjach.

Polecenie jest realizowana za pomocą klasy, która zawiera pola danych lub kolekcji wszystkie informacje, które są potrzebne w celu wykonania tego polecenia. Polecenie jest specjalnym rodzajem z danych Transfer obiektu (DTO), które jest używane wyłącznie do żądania zmiany lub transakcji. Samo polecenie opiera się na dokładnie informacje potrzebne do przetwarzania polecenia i nic więcej.

W poniższym przykładzie pokazano uproszczony klasy CreateOrderCommand. To jest niezmienialny polecenia, który jest używany w porządkowania mikrousługi w eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
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

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
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

Zasadniczo klasy poleceń zawiera wszystkie dane potrzebne do przeprowadzania transakcji firm za pomocą obiektów modelu domeny. W związku z tym polecenia są po prostu struktur danych, które zawierają dane tylko do odczytu i nie zachowanie. Nazwa polecenia wskazuje jej celem. W wielu językach takich jak C\#, polecenia są reprezentowane jako klasy, ale nie są one true klas w tym sensie, rzeczywista obiektowo.

Jako dodatkowe właściwości polecenia są niezmienne, ponieważ jest oczekiwane wykorzystanie są przetwarzane bezpośrednio przez modelu domeny. Potrzebują oni zmieniać podczas ich przewidywanego okresu istnienia. W języku C\# klasy immutability można osiągnąć, ponieważ nie ma żadnych ustawiające lub innych metod, które spowodują zmianę stanu wewnętrznego.

Na przykład klasa polecenia do tworzenia kolejności jest prawdopodobnie podobne pod względem danych kolejność, według której ma zostać utworzona, ale prawdopodobnie nie ma potrzeby takie same atrybuty. Na przykład CreateOrderCommand nie ma identyfikator zamówienia, ponieważ kolejność nie został jeszcze utworzony.

Wiele klas polecenie może być prosty, wymagania dotyczące niektórych stanu, który musi zostać zmienione tylko kilka pól. Wyniesie przypadku tylko w przypadku zmiany stanu zlecenia od "w toku" do "płatnej" lub "wysłane" przy użyciu polecenia podobny do następującego:

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

Niektóre deweloperzy tworzą żądania interfejsu użytkownika w nich obiekty niezależnie od ich DTOs polecenia, ale jest to wystarczy preferencji. Jest niewygodny separacji nie wiele wartości dodanej, a obiekty są prawie dokładnie tego samego kształtu. Na przykład w eShopOnContainers, polecenia pochodzi bezpośrednio z po stronie klienta.

### <a name="the-command-handler-class"></a>Klasa obsługi polecenia

Należy zaimplementować klasę programu obsługi określonego polecenia dla każdego polecenia. To działanie wzorzec i jest którym będziesz używać obiektów repozytorium infrastruktury, obiektów domeny i obiektu polecenia. Program obsługi poleceń w rzeczywistości jest centralnym warstwy aplikacji pod względem CQRS i DDD. Jednak całą logikę domeny powinny być zawarte w klasach domeny — w ramach korzenie agregacji (jednostek głównego), jednostek podrzędnych lub [usług domenowych w usłudze](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale nie w ciągu programu obsługi poleceń, który jest klasy z aplikacji warstwy.

Program obsługi poleceń odebrało polecenie i uzyskuje wynik z zagregowaną, która jest używana. Wynik powinien być pomyślnego wykonania polecenia lub wystąpił wyjątek. W przypadku wyjątku stanu systemu należy bez zmian.

Program obsługi poleceń zazwyczaj wykonuje następujące czynności:

-   Odbiera obiekt polecenia, takich jak DTO (z [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub innego obiektu infrastruktury).

-   Jest sprawdzane, czy to polecenie jest nieprawidłowa (Jeśli nie jest zweryfikowany przez mediatora).

-   Metoda tworzy wystąpienia głównego agregacji, który jest miejscem docelowym bieżącego polecenia.

-   Metoda jest wykonywana w wystąpieniu głównego agregacji, pobieranie danych wymagane polecenia.

-   Istnieje nowy stan agregacji do jego bazie danych. Ta ostatnia operacja jest rzeczywista transakcji.

Zazwyczaj obsługi polecenia obsługuje pojedynczy agregacji, wynikają z głównym agregacji (jednostka głównego). Jeśli Agreguje wiele powinny mieć wpływ na odebranie jednego polecenia, można za pomocą zdarzeń domeny propagowanie Agreguje wiele stanów lub akcji

Należy koniecznie zwrócić uwagę to, że podczas przetwarzania polecenia całą logikę domeny powinien znajdować się w modelu domeny (agregacji) pełni hermetyzowany i gotowa do przeprowadzania testów jednostkowych. Program obsługi poleceń po prostu działa jako sposób uzyskać modelu domeny z bazy danych i ostatni krok mówić warstwę infrastruktury (repozytoria), aby utrwalić zmiany po zmianie modelu. Zaletą tej metody jest, że można Refaktoryzuj logika domeny w modelu domeny izolowanym, pełni hermetyzowany, rozbudowane, behawioralnej bez zmiany kodu w aplikacji lub infrastruktury warstw, które są poziom żmudne procesy (programy obsługi poleceń, interfejsu API sieci Web, repozytoria itp.).

Podczas obsługi polecenia uzyskać złożonych z logiką zbyt dużo, który może być zapachu kodu. Przejrzyj je, a Jeśli znajdziesz logika domeny zrefaktoryzuj kod, aby przenieść tego zachowania domeny do metod obiektów domeny (łączny główna i podrzędna jednostka).

Na przykład klasa obsługi polecenia poniższy kod przedstawia tej samej klasy CreateOrderCommandHandler, który był wyświetlany na początku tego działu. W takim przypadku firma Microsoft ma wyróżnione dojścia metody i operacje z obiektami modelu domeny/agregacji.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

Program obsługi poleceń należy wykonać dodatkowe kroki, są to:

-   Użyj polecenia danych z metody i zachowanie elementu głównego agregacji.

-   Wewnętrznie w obiektach domeny wywołania domeny zdarzeń, gdy transakcja jest wykonywana, ale jest przezroczysty z punktu widzenia obsługi polecenia.

-   Jeśli wynik działania wartości zagregowanej zakończy się pomyślnie, a po zakończeniu transakcji, Wywołaj program obsługi poleceń zdarzeń integracji. (Te mogą również być zgłaszany przez klas infrastruktury, takich jak repozytoriów.)

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Seemann znaku. Na granicach, aplikacje są zorientowane obiektowo nie**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, zorientowane na ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **Poleceń i zdarzeń**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **Do czego służy program obsługi polecenia? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard. Wzorce poleceń domeny — programy obsługi**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard. Wzorce poleceń domeny — Weryfikacja**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Polecenie potoku proces: sposób włączania obsługi polecenia

Następne pytanie jest o wywoływaniu programem obsługi. Można ręcznie wywołać ją z każdym pokrewne kontrolera ASP.NET Core. Jednak metoda byłaby zbyt połączeniu i nie jest idealnym rozwiązaniem.

Inne dwa główne, które są zalecane opcje, są następujące opcje:

-   Za pomocą wzorca artefaktu mediatora w pamięci.

-   Z kolejki komunikatów asynchronicznych, Between kontrolerów i obsługi.

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>W potoku polecenia przy użyciu wzorca mediatora (w pamięci)

Jak pokazano w rysunek 9-21, w podejściu CQRS służy inteligentnego mediatora, podobnie jak magistrala w pamięci, czyli inteligentne przekierowywanie do obsługi polecenie right na podstawie typu polecenia lub DTO odbierane. Pojedynczy czarne strzałki między składnikami reprezentują zależności między obiekty (w wielu przypadkach wprowadzonym za pośrednictwem Podpisane) z ich powiązane interakcje.

![](./media/image22.png)

**Rysunek 9-21**. Przy użyciu wzorca mediatora w procesie w jednym mikrousługi CQRS

Pasującą przy użyciu wzorca mediatora dzieje się tak że w aplikacjach dla przedsiębiorstw, przetwarzania żądań można uzyskać skomplikowane. Chcesz mieć możliwość dodawania Otwórz liczba kompleksowymi problemy, takie jak rejestrowanie, sprawdzanie poprawności, inspekcji i zabezpieczeń. W takich przypadkach polega na potoku mediatora (zobacz [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern)) do wymuszenia dla tych dodatkowych zachowania lub kompleksowymi problemy.

Obiekt hermetyzujący "jak" tego procesu jest mediatora: go koordynuje wykonywania na podstawie stanu, sposób obsługi polecenia jest wywoływana lub ładunku Podaj do programu obsługi. Ze składnikiem mediatora można zastosować kompleksowymi problemy w sposób scentralizowany i przejrzysty, stosując elementów decorator (lub [potoku zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) od mediatora v3). (Aby uzyskać więcej informacji, zobacz [wzorzec Dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).)

Elementy decorator i zachowania są podobne do [aspekt ukierunkowane programowania (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)tylko zastosowane do zarządzanych przez składnik mediatora potoku określonego procesu. Aspektów AOP implementujących dotyczy kompleksowymi są stosowane na podstawie *weavers aspekt* wprowadzonym w czasie kompilacji lub w oparciu o przechwytywaniu wywołania obiektu. Obu podejść typowe AOP czasami są określane jako działania "magic", ponieważ nie jest łatwo sprawdzić, jak AOP działa jej. Podczas pracy nad poważnych problemów i zgłaszanie usterek, AOP może być trudne do debugowania. Z drugiej strony te elementy decorator/zachowania są jawne i stosowane tylko w kontekście mediatora, więc debugowanie jest bardziej przewidywalna i łatwe.

Na przykład w eShopOnContainers kolejności mikrousługi, wprowadziliśmy dwa dekoratory próbki, [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) klasy i [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) klasy. Implementacja dekoratora znajduje się w następnej sekcji. Należy pamiętać, że w przyszłych wersjach eShopOnContainers spowoduje zmigrowanie [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) i przejdź do [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) zamiast elementów decorator.

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>W potoku do polecenia, używając kolejek wiadomości (poza procesem)

Wybór innego polega na użyciu asynchronicznej wiadomości na podstawie brokerzy lub kolejki komunikatów, jak pokazano w rysunek 9-22. Ta opcja również można łączyć ze składnikiem mediatora bezpośrednio poprzedzający program obsługi poleceń.

![](./media/image23.png)

**Rysunek 9-22**. Za pomocą polecenia CQRS, używając kolejek wiadomości (poza procesem i komunikacji między procesami)

Za pomocą wiadomości kolejki, aby zaakceptować polecenia można bardziej szczegółowo skomplikować potoku dla polecenia, ponieważ prawdopodobnie będzie konieczne podzielić potok dwa procesy połączone za pośrednictwem kolejki wiadomości zewnętrznych. Nadal należy używać, gdy trzeba mieć zwiększona skalowalność i wydajność w oparciu asynchroniczną obsługę wiadomości. Należy wziąć pod uwagę, że w przypadku rysunek 9-22 kontroler tylko zapisuje komunikat polecenia do kolejki i zwraca. Następnie programy obsługi poleceń przetwarzanie wiadomości we własnym tempie. Oznacza to doskonały korzyści kolejek — kolejki wiadomości może działać jako buforu w przypadkach gdy skalowalność funkcji hyper jest wymagane, takie jak w przypadku zasobów lub innych scenariuszy z dużą liczbę danych wejściowych.

Jednak ze względu na asynchroniczne charakter kolejki komunikatów, należy dowiedzieć się, jak do komunikacji z aplikacją klient o powodzeniu lub niepowodzeniu polecenia procesu. Zgodnie z zasadą nigdy nie należy używać poleceń "wyzwalać i zapomnij". Każda aplikacja biznesowa musi wiedzieć, jeśli polecenie zostało przetworzone pomyślnie, co najmniej zweryfikowane i zaakceptowane.

W związku z tym możliwość odpowiedzi do klienta po weryfikacji komunikatem polecenia, który został przesłany do asynchronicznego kolejki dodaje złożoność do systemu, w porównaniu do polecenia w trakcie procesu, który zwraca wynik operacji po uruchomieniu transakcji. Korzystanie z kolejek, konieczne może być zwrócić wyników polecenia procesu za pomocą innych wiadomości wynik operacji, które będzie wymagać dodatkowych składników i niestandardowych komunikacji w systemie.

Ponadto polecenia asynchroniczne są jednokierunkowe poleceń, które w wielu przypadkach mogą nie być wymagane, opisane w poniższych interesujące wymiany między Burtsev Alexey i małych Gregowi w [online konwersacji](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\] znaleźć się części kodu, których użytkownicy korzystają Obsługa polecenia async lub jednokierunkowej polecenia wiadomości bez jakiegokolwiek powodu, aby to zrobić (nie robią niektórych długotrwałej operacji, nie są one wykonywanie kodu async zewnętrznych, ich nie nawet przechodzą aplikacji granic z magistrali komunikatów). Dlaczego ich wprowadzenie tego niepotrzebnych złożoności? I w rzeczywistości I nie zostało to jeszcze widoczne CQRS przykładowego kodu z blokuje programy obsługi poleceń wykonanej do tej pory, że będzie ona działać tak dobrze w większości przypadków.

\[Gregowi małych\] \[... \] asynchronicznej polecenie nie istnieje; jest faktycznie inne zdarzenie. Jeśli musi zaakceptować, co możesz wysyłać mi i wywołaj zdarzenie, jeśli nie zgadzam się, nie jest już możesz informacją coś zrobić. Jest możesz informujący, który coś zostało wykonane. Prawdopodobnie to niewielka różnica na początku, ale ma wpływ na wiele.

Asynchroniczne polecenia znaczne zwiększenie złożoność systemu, ponieważ nie istnieje prosty sposób wskazująca błędów. W związku z tym polecenia asynchroniczne nie są zalecane inne niż skalowania wymagania są potrzebne, lub w szczególnych przypadkach podczas komunikacji wewnętrznej mikrousług przy użyciu wiadomości. W takich przypadkach należy projektować oddzielnego systemu raportowania i odzyskiwania na wypadek awarii.

W pierwotnej wersji eShopOnContainers zdecydowaliśmy się użyć polecenia synchronicznego przetwarzania, rozpoczynający się od żądań HTTP i regulowane przez wzorzec mediatora. Które łatwo można zwrócić powodzenie lub niepowodzenie procesu, podobnie jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.

W każdym przypadku powinien to być decyzji na podstawie wymagań biznesowych w aplikacji lub w mikrousługi.

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementowanie potoku polecenie procesu z wzorcem mediatora (MediatR)

Jako przykładowe zastosowanie ten przewodnik przedstawia za pomocą potoku w procesie oparte na wzorcu mediatora na wprowadzanie polecenia dysku i routing, w pamięci, do obsługi polecenie right. Przewodnik proponuje, stosowanie elementów decorator lub [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) aby oddzielić kompleksowymi problemy.

Implementacja .NET Core są dostępne wielu bibliotekach open source, które implementują wzorzec mediatora. Biblioteka używanych w tym przewodniku jest [MediatR](https://github.com/jbogard/MediatR) biblioteki open source (utworzony przez Jimmy Bogard), ale można użyć innej metody. MediatR jest niewielki i prosty biblioteki, która służy do przetwarzania komunikatów w pamięci, takich jak polecenia, podczas stosowania elementów decorator lub zachowania.

Przy użyciu wzorca mediatora pomaga ograniczyć sprzężenia i do izolowania problemów żądanej pracy, podczas łączenia automatycznie do programu obsługi, który wykonuje pracy — w takim przypadku na programy obsługi poleceń.

Kolejny powód dobra do użycia z wzorcem mediatora wyjaśniono przez Jimmy Bogard podczas przeglądania w tym przewodniku:

Myślę, może być warto zauważyć testowania w tym miejscu — zapewnia nieuprzywilejowany zgodne okno do zachowania systemu. W żądaniu, poza odpowiedzi. Znaleziono element bardzo przydatna w budynku spójnie zachowuje testy.

Najpierw Daj nam zapoznaj się z kodem kontroler faktycznie użycia obiektu mediatora. Obiekt mediatora nie były używane, należy wprowadzić wszystkie zależności dla tego kontrolera, np. obiekt rejestratora i inne. W związku z tym Konstruktor jest dość złożone. Z drugiej strony Jeśli używasz obiektu mediatora konstruktora kontroler może być znacznie prostsze, kilka zależności, zamiast wiele zależności, które byłyby gdyby jeden na operację kompleksowymi, jak w poniższym przykładzie:

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

Widać, że mediatora zapewnia czyste i gotowa konstruktora kontrolera interfejsu API sieci Web. Ponadto w ramach metod kontrolera kod, aby wysyłać polecenia do obiektu mediatora jest prawie jeden wiersz:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

MediatR pod uwagę klasy obsługi polecenia, należy zarejestrować klasy mediatora i klasy programu obsługi poleceń w Twojej kontenera IoC. Domyślnie MediatR używa Autofac jako kontenera IoC, ale można również użyć wbudowanych kontenera ASP.NET Core IoC lub innych kontenera obsługiwane przez MediatR.

Poniższy kod przedstawia sposób rejestrowania poleceń i typów w mediatora przy użyciu modułów Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

Ponieważ każdy program obsługi poleceń implementuje interfejs z ogólnym IAsyncRequestHandler&lt;T&gt; , a następnie sprawdza RegisteredAssemblyTypes obiektu, program obsługi jest w stanie powiązać każde polecenie z programem obsługi, ponieważ który określona relacja commandhandler — obiekt klasy, jak w poniższym przykładzie:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

To jest kod odpowiadająca poleceń z programy obsługi poleceń. Program obsługi ma prostą klasę, ale dziedziczy on z RequestHandler&lt;T&gt;, i MediatR zapewnia on wywołany z poprawną ładunku.

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>Stosowanie kompleksowymi problemy podczas przetwarzania polecenia wzorami mediatora i Dekoratora

Istnieje więcej rzecz: możliwość dotyczą problemów kompleksowymi mediatora potoku. Możesz również sprawdzić w końcu kod modułu rejestracji Autofac jak jest rejestrowanie dekoratora typ, w szczególności niestandardowej klasy LogDecorator.

Ponownie, należy pamiętać, że przyszłej wersji eShopOnContainers go spowoduje zmigrowanie [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) i przejdź do [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) zamiast elementów decorator.

Czy [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) jako następujący kod, który rejestruje informacje na temat program obsługi poleceń, które było wykonywane, i czy było pomyślne lub nie można zaimplementować klasy.

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

Wystarczy implementowania tej klasy dekoratora i przez potok wraz z jego dekoracji wszystkich poleceń, które są przetwarzane przez MediatR będzie rejestrowanie informacji na temat wykonywania.

EShopOnContainers porządkowanie mikrousługi ma zastosowanie również w drugim dekoratora dla podstawowych operacji sprawdzania poprawności, [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) klasy, która zależy od [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w następujący kod:

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

Następnie, na podstawie [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, utworzyliśmy sprawdzanie poprawności danych przekazanych z CreateOrderCommand, zgodnie z poniższym kodem:

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
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

Można utworzyć dodatkowe operacje sprawdzania poprawności. Jest to bardzo czyste i elegancki sposób implementacji Twojego polecenia operacji sprawdzania poprawności.

W podobny sposób można zaimplementować innych elementów decorator dodatkowe aspekty lub kompleksowymi problemy, które mają być stosowane do poleceń podczas ich obsługę.

#### <a name="additional-resources"></a>Dodatkowe zasoby

##### <a name="the-mediator-pattern"></a>Wzorzec mediatora

-   **Wzorzec mediatora**
    [*https://en.wikipedia.org/wiki/Mediator\_wzorca*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Wzorzec dekoratora

-   **Wzorzec dekoratora**
    [*https://en.wikipedia.org/wiki/Decorator\_wzorca*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR.** Repozytorium GitHub.
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **CQRS MediatR i AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **Umieść kontrolerów tradycyjną: ogłoszeń i poleceń. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **Poruszając kompleksowymi problemy z potokiem mediatora**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS i REST: czego szukasz**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **Przykłady potoku MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **Wycinek pionowy testów osprzętu MediatR i ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **Rozszerzenia MediatR iniekcji zależności Microsoft wydała**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Sprawdzanie poprawności Fluent

-   **Jeremy Skinner. FluentValidation.** Repozytorium GitHub.
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[Poprzednie] (microservice-application-layer-web-api-design.md) [dalej] (.. /Implement-resilient-Applications/index.MD)
