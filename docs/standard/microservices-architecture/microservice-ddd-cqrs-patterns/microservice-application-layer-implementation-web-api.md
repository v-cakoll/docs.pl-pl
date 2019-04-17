---
title: Implementowanie warstwy aplikacji mikrousług za pomocą internetowego interfejsu API
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, wstrzykiwanie zależności i wzorce mediatora oraz ich szczegóły implementacji w warstwie aplikacji interfejsu API sieci Web.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 376b4eca99ed60a54831aa37099108692d8bac6d
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612163"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementowanie warstwy aplikacji mikrousług przy użyciu interfejsu API sieci Web

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Użyj iniekcji zależności iniekcję obiektów infrastruktury do usługi warstwy aplikacji

Jak wspomniano wcześniej, można zaimplementować jako część artefaktu (assembly), którą tworzysz, takich jak w ramach projektu interfejsu API sieci Web lub projektu aplikacji sieci web MVC warstwy aplikacji. W przypadku mikrousług, utworzonych za pomocą platformy ASP.NET Core warstwy aplikacji będzie zazwyczaj biblioteki interfejsu API sieci Web. Jeśli chcesz oddzielić wkrótce się z platformą ASP.NET Core (swoją infrastrukturę oraz kontrolerach) od kodu warstwy aplikacji niestandardowych warstwie aplikacji można także umieścić w bibliotece osobnej klasy, ale jest opcjonalny.

Na przykład kod warstwy aplikacji mikrousług szeregowania bezpośrednio jest wdrażany jako część **Ordering.API** projektu (projekt internetowego interfejsu API platformy ASP.NET Core), rysunek jak pokazano na 7-23.

![Widok Eksploratora rozwiązań mikrousług Ordering.API, przedstawiający podfolderów w folderze aplikacji: Zachowania, poleceń, DomainEventHandlers, IntegrationEvents, modele, zapytań i operacji sprawdzania poprawności.](./media/image20.png)

**Rysunek 7-23**. Warstwa aplikacji w projekcie Ordering.API ASP.NET Core Web API

Platforma ASP.NET Core obejmuje prostą [wbudowanych kontenera IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowany przez interfejsu IServiceProvider), która obsługuje iniekcji Konstruktor domyślny i ASP.NET sprawia, że niektóre usługi są dostępne za pośrednictwem DI. Platforma ASP.NET Core używa termin *usługi* dla każdego z typów rejestrowania, które będą wstrzyknięte przez DI. Możesz skonfigurować usług w kontenerze wbudowane w metodzie ConfigureServices w klasie uruchamiania aplikacji. Zależności są implementowane w usługach wymaga typu i Zarejestruj w kontenerze IoC.

Zazwyczaj mają zależności, które implementują obiektów infrastruktury. Bardzo typowy zależności do dodania to repozytorium. Jednak można wstawić wszelkich innych zależności infrastruktury, które mogą mieć. Prostsze implementacji może bezpośrednio uruchomić obiektu wzorzec jednostki pracy (obiektu EF DbContext), ponieważ kontekstu DBContext jest również implementację obiektów trwałości infrastruktury.

W poniższym przykładzie można zobaczyć, jak .NET Core wprowadza obiekty wymagane repozytorium za pomocą konstruktora. Klasa jest program obsługi poleceń, co zostanie omówione w następnej sekcji.

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

Klasa używa wprowadzonego repozytoria do wykonywania transakcji i zachować zmiany stanu. Nie ma znaczenia, czy ta klasa procedurę obsługi poleceń, metodą kontroler internetowego interfejsu API platformy ASP.NET Core, czy [usługi aplikacji DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Ostatecznie to klient jest prostą klasę, która korzysta z repozytoriów, jednostki domeny i koordynacji innych aplikacji w sposób podobny do obsługi polecenia. Taki sam sposób dla wszystkich wymienionych klas, tak jak w przykładzie, za pomocą DI oparte na konstruktora działa iniekcji zależności.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Rejestrowanie typów implementacji zależności i interfejsy lub abstrakcje

Przed użyciem obiektów wprowadzonym za pomocą konstruktorów, musisz wiedzieć, gdzie można zarejestrować interfejsów i klas, które tworzą obiekty, które są wstrzykiwane do swojej klasy aplikacji za pośrednictwem DI. (Takich jak DI na podstawie konstruktora, jak pokazano wcześniej.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Użyj wbudowanych kontenera IoC dostarczone przez platformy ASP.NET Core

Korzystając z wbudowanych kontenera IoC, dostarczonego przez platformy ASP.NET Core, zarejestruj się typy, które chcesz wstawić w metodzie ConfigureServices w pliku Startup.cs, zgodnie z poniższym kodem:

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

Najczęstszym wzorcem po rejestrowanie typów w pojemniku IoC można zarejestrować dwa typy — interfejs i jej klasy pokrewne implementacji. W przypadku żądania obiektu z kontenera IoC przez dowolny Konstruktor, następnie zażądać obiektu określonego typu interfejsu. Na przykład w poprzednim przykładzie, ostatni wiersz stany, gdy dowolne z konstruktorów mają zależności IMyCustomRepository (interfejs lub abstrakcji), kontenera IoC doda wystąpienia wykonania MyCustomSQLServerRepository Klasa.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Korzystanie z biblioteki Scrutor dla typów automatycznej rejestracji

Korzystając z DI platformie .NET Core, możesz chcieć można przeskanować zestawu i automatycznie zarejestrować jego typów zgodnie z Konwencją. Ta funkcja nie jest obecnie dostępna w programie ASP.NET Core. Można jednak użyć [Scrutor](https://github.com/khellang/Scrutor) biblioteki, w tym. To podejście jest wygodne w przypadku wielu typów, które muszą być zarejestrowani w kontenerze IoC.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Matthew King. Rejestrowanie usługi przy użyciu Scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** Repozytorium GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Użyj Autofac jako kontenera IoC

Możesz również dodatkowe kontenery IoC i podłącz je do potoku platformy ASP.NET Core, tak jak szeregowania mikrousługi w ramach aplikacji eShopOnContainers, który używa [Autofac](https://autofac.org/). Korzystając z Autofac zwykle należy zarejestrować typy za pośrednictwem modułów, dzięki czemu można będzie podzielić typów rejestracji między wiele plików, w zależności od tego, gdzie są Twoje typy, tak samo, jak masz typy aplikacji rozproszonych w wielu bibliotek klas.

Na przykład poniżej przedstawiono [modułu aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu z typami, należy wstawić.

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

Autofac ma również funkcję [skanowanie zestawów i zarejestrować typy według Konwencji nazwy](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Proces rejestracji i pojęcia są bardzo podobne do sposób typów można zarejestrować za pomocą wbudowanych kontenera ASP.NET Core IoC, ale składni, korzystając z Autofac jest nieco inna.

W przykładowym kodzie abstrakcji IOrderRepository jest zarejestrowany wraz z implementacji klasy OrderRepository. Oznacza to, że zawsze wtedy, gdy Konstruktor jest zadeklarowanie zależności za pomocą abstrakcji IOrderRepository lub interfejsu, kontenera IoC doda wystąpienia klasy OrderRepository.

Typ zakresu wystąpienia określa, jak wystąpienie jest współużytkowana przez żądania dla tej samej usługi lub zależności. Po wysłaniu żądania dla zależności, kontenera IoC może zwracać następujące czynności:

- Jedno wystąpienie na okres istnienia, zakres (określone w kontenerze platformy ASP.NET Core IoC jako *zakresie*).

- Nowe wystąpienie na zależności (określone w kontenerze platformy ASP.NET Core IoC jako *przejściowy*).

- Pojedyncze wystąpienie udostępnione dla wszystkich obiektów za pomocą kontenera IoC (określone w kontenerze platformy ASP.NET Core IoC jako *pojedyncze*).

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do iniekcji zależności w programie ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficjalna dokumentacja. \
  <https://docs.autofac.org/en/latest/>

- **Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC - Torre'a de la Cesarowi.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementowanie wzorców polecenia i program obsługi poleceń

W przykładzie DI za pośrednictwem konstruktora pokazano w poprzedniej sekcji kontenera IoC został wprowadza repozytoriów za pośrednictwem konstruktora w klasie. Ale dokładnie których zostały one dodane? Proste internetowego interfejsu API (na przykład mikrousług katalogu w ramach aplikacji eShopOnContainers) należy wstrzyknąć je na poziomie kontrolerów MVC w Konstruktorze kontrolera, jako część potoku żądania programu ASP.NET Core. Jednak w kod początkowy przedstawione w tej sekcji ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy usługi Ordering.API w ramach aplikacji eShopOnContainers), iniekcja zależności odbywa się za pośrednictwem konstruktora określonego polecenia Program obsługi. Daj nam wyjaśniono, jakie procedurę obsługi poleceń jest i dlaczego chcesz używać go.

Wzorzec polecenia wewnętrznie jest powiązana z wzorcem CQRS, która została wprowadzona wcześniej w tym przewodniku. Podejście CQRS ma dwie strony. Pierwszy obszar jest zapytań przy użyciu uproszczone zapytań przy użyciu [programem Dapper](https://github.com/StackExchange/dapper-dot-net) ORM wczesnych wyjaśniono wcześniej. Drugi ma polecenia, które są punkt początkowy dla transakcji i kanału wejściowego z poza usługi.

Jak pokazano w rysunek 7-24, wzorzec jest oparty na akceptowanie poleceń po stronie klienta przetwarzanie je zgodnie z regułami modelu domeny, a na koniec utrwalania stanów z transakcji.

![Widok wysokiego poziomu stronie zapisu we wzorcu CQRS: Aplikacja interfejsu użytkownika wysyła polecenie za pomocą interfejsu API, który pobiera commandhandler — obiekt, który zależy od modelu domeny i infrastruktury w celu aktualizacji bazy danych.](./media/image21.png)

**Rysunek 7-24**. Ogólny widok poleceń lub "transakcji po stronie" we wzorcu CQRS

### <a name="the-command-class"></a>Klasy poleceń

Polecenie to żądanie systemu do wykonania akcji, który zmienia stan systemu. Polecenia są konieczne i mają być przetwarzane tylko raz.

Ponieważ polecenia są priorytetów, są zwykle nazywane ze zleceniem ochotę imperatywnego (na przykład "Utwórz" lub "Aktualizuj"), i mogą one obejmować odpowiedni typ agregacji, takich jak CreateOrderCommand. W przeciwieństwie do zdarzenia polecenie nie jest faktów z przeszłości; jest tylko żądania, a więc można odmówić.

Polecenia mogą pochodzić z interfejsu użytkownika, w wyniku użytkownik inicjuje żądanie lub menedżera procesów, gdy Menedżer procesu jest kierowanie agregacji do wykonania akcji.

Ważną cechą polecenie jest, że powinien on tylko raz przetwarzany przez jednego odbiorcę. Jest to, ponieważ polecenie jest jedna akcja lub transakcji, które mają być wykonywane w aplikacji. Na przykład polecenia do tworzenia tej samej kolejności nie powinny być przetwarzane więcej niż jeden raz. Jest to ważna różnica między poleceń i zdarzeń. Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług może być zainteresowany zdarzenia.

Ponadto jest ważne, że polecenie być przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentna. Polecenie jest idempotentna, jeśli go mogą być wykonywane wiele razy bez wprowadzania zmian w wyniku ze względu na rodzaj polecenie lub ze względu na sposób system obsługuje polecenie.

Jest dobrą praktyką, aby poleceń i aktualizuje idempotentne, gdy największy sens w ramach reguł biznesowych domeny i invariants. Na przykład aby użyć w tym samym przykładzie, jeśli jakiegokolwiek powodu (logika ponowień, stosowanie metod hakerskich itp.) to samo polecenie CreateOrder osiągnie system wielokrotnie, można identyfikację i upewnij się, że nie należy tworzyć wiele zamówień. Aby to zrobić, należy dołączyć pewnego rodzaju tożsamości w operacjach i ustalić, czy polecenie lub aktualizacji został już przetworzony.

Wysłać polecenie do jednego odbiornika; nie opublikowano polecenia. Publikowanie jest dla zdarzeń, które podają fakt — coś się stało i mogą być interesujące dla odbiorcy zdarzeń. W przypadku zdarzeń wydawca ma nie obaw, o których odbiorcy pobrać zdarzenia lub ich działania go. Ale zdarzeń domeny lub Integracja z innego wątku już wprowadzone w poprzednich sekcjach.

Polecenie jest implementowane za pomocą klasy, która nie zawiera pola danych i kolekcji wszystkie informacje, które są potrzebne w celu wykonania tego polecenia. Polecenie jest specjalnym rodzajem elementu danych transferu obiektu (DTO), taki, który jest używane wyłącznie do żądania zmiany lub transakcji. Samo polecenie opiera się na dokładnie te informacje, które są potrzebne do przetwarzania polecenia i nic więcej.

Poniższy przykład przedstawia klasę CreateOrderCommand uproszczone. Jest to niezmienne polecenia, który jest używany podczas szeregowania mikrousługi w ramach aplikacji eShopOnContainers.

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
// https://msdn.microsoft.com/library/bb383979.aspx
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

Po prostu klasy poleceń zawiera wszystkie dane, których potrzebują do przeprowadzania transakcji biznesowych za pomocą obiektów modelu domeny. W efekcie polecenia są po prostu struktur danych, które zawierają dane tylko do odczytu i nie zachowanie. Nazwa polecenia wskazuje jej przeznaczenie. W wielu językach, takich jak C#, polecenia są reprezentowane jako klasy, ale nie mają wartość true, klasy, w tym sensie, rzeczywiste zorientowane obiektowo.

Jako dodatkowe właściwości polecenia są niezmienne, ponieważ oczekiwane użycie jest, że są przetwarzane bezpośrednio przez model domeny. Nie ma potrzeby zmiany w okresie ich istnienia przewidywany. W C# klasy, niezmienność można osiągnąć, nie ma żadnych metod ustawiających lub innych metod, które zmieniają stan wewnętrzny.

Należy pamiętać, że jeśli planowane lub oczekiwać poleceń będzie przechodzić przez proces serializacji deserializing właściwości muszą mieć prywatnej metody ustawiającej, należy sobie zdawać sprawę i `[DataMember]` (lub `[JsonProperty]`) atrybutów, w przeciwnym razie Deserializator nie będzie można odtworzenie obiektu w lokalizacji docelowej z wymaganymi wartościami.

Na przykład klasy poleceń do tworzenia zamówienie przypomina prawdopodobnie pod względem danych kolejności, w której ma zostać utworzona, ale prawdopodobnie nie potrzebujesz tych atrybutów. Na przykład CreateOrderCommand ma identyfikator zamówienia, ponieważ kolejność nie został jeszcze utworzony.

Wiele klas polecenia mogą być proste, wymagania dotyczące pewnego stanu, który musi zostać zmienione tylko kilka pól. Byłoby w przypadku tylko w przypadku zmiany stanu zamówienia z "w toku" do "płatnych" lub "dostarczane" przy użyciu polecenia podobnego do następującego:

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

Niektórzy deweloperzy wprowadzić w nich obiekty interfejsu użytkownika żądania niezależnie od ich dto polecenia, ale jest to kwestia preferencji. Jest niewygodna separacji nie dużo wartością dodaną i obiekty są prawie dokładnie tak sam kształt. Na przykład w ramach aplikacji eShopOnContainers, niektóre polecenia pochodzą bezpośrednio po stronie klienta.

### <a name="the-command-handler-class"></a>Klasy obsługi poleceń

Należy zaimplementować klasę programu obsługi określone polecenie dla każdego polecenia. To, jak wzorzec działa i jest to, gdzie będzie używać obiekt polecenia, obiektów domeny i obiektów repozytorium infrastruktury. Program obsługi poleceń w rzeczywistości to serce warstwy aplikacji w kontekście CQRS i DDD. Jednak logika domeny powinny być zawarte w obrębie klasy domeny — w ramach korzenie agregacji (głównych jednostek), jednostki podrzędne lub [usługi domenowe](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale nie w ramach programu obsługi poleceń jest klasa z aplikacji warstwy.

Klasa procedury obsługi polecenia oferuje silnej kamień przechodzenia krok po kroku w taki sposób, aby osiągnąć pojedynczej odpowiedzialności zasady (SRP) opisane w poprzedniej sekcji.

Program obsługi poleceń otrzymuje polecenie i uzyskuje wynik agregacji, która jest używana. Wynik powinien być pomyślne wykonanie polecenia lub wyjątek. W przypadku wyjątku stan systemu należy bez zmian.

Program obsługi poleceń zwykle wykonuje następujące czynności:

- Odbiera obiekt polecenia, takie jak obiekt DTO (z [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub inny obiekt infrastruktury).

- Weryfikuje on, że polecenie jest nieprawidłowy (Jeśli nie jest zweryfikowany przez mediatora).

- Metoda tworzy wystąpienie głównego agregacji, które jest elementem docelowym bieżącego polecenia.

- Metoda wykonuje na wystąpieniu głównego agregacji, pobierania wymaganych danych z polecenia.

- Utrzymuje nowy stan agregacji do powiązanej bazie danych. Ta ostatnia operacja jest rzeczywistych transakcji.

Zazwyczaj obsługi polecenia obsługuje jednej wartości zagregowanej wynika z jego głównego agregacji (jednostki głównej). Jeśli wiele agregacji powinny mieć wpływ na odbiór jednego polecenia, można użyć zdarzeń domeny do propagowanie Agreguje wiele stanów lub akcji.

Istotną kwestią jest, że podczas przetwarzania polecenia logika domeny powinny być wewnątrz modelu domeny (agregacje), w pełni hermetyzowany i gotowe do testowania jednostki. Procedura obsługi polecenia działa tylko jako sposób uzyskać modelu domeny z bazy danych i ostatni krok, aby poinformować warstwy infrastruktury (repozytoriów), aby utrwalić zmiany po zmianie modelu. Zaletą tego podejścia jest refaktoryzować logika domeny w modelu domeny izolowane pełni zhermetyzowany, rozbudowane, zachowań bez konieczności zmiany kodu w aplikacji lub warstwy infrastruktury, które działają na poziomie nadmiar (programy obsługi poleceń, w przypadku interfejsu API sieci Web repozytoria itp.).

Podczas obsługi polecenia okazać się skomplikowane, za pomocą zbyt dużo logiki, które mogą być zapachu kodu. Zapoznaj się z nimi, a jeśli okaże się logika domeny zrefaktoryzuj kod, aby przenieść to zachowanie domeny do metod obiektów domeny (agregacji główna i podrzędna jednostki).

Jako przykład klasę programu obsługi poleceń poniższy kod przedstawia tej samej klasie CreateOrderCommandHandler, który był wyświetlany na początku w tym rozdziale. W tym przypadku chcemy podkreślić, metoda dojścia i operacji za pomocą obiektów modelu domeny/agregacji.

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

Poniżej przedstawiono dodatkowe kroki, które należy wykonać procedurę obsługi poleceń:

- Działanie przy użyciu metody agregacji głównego i zachowanie, należy użyć polecenia danych.

- Wewnętrznie w obiektach domeny zgłosić zdarzenia domeny podczas transakcji jest wykonywane, ale która jest przezroczysta z punktu widzenia obsługi polecenia.

- Jeśli wynik operacji agregacji zakończy się pomyślnie, a po zakończeniu transakcji, należy zgłosić zdarzenia integracji. (Te mogą również zostać wywołane przez klasy infrastruktury, takie jak repozytoriami.)

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Seemann znacznika. Na granicach aplikacje są nie zorientowane obiektowo** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Poleceń i zdarzeń** \
  <http://cqrs.nu/Faq/commands-and-events>

- **Do czego służy program obsługi poleceń?** \
  <http://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Wzorce poleceń domeny — programy obsługi** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Wzorce poleceń domeny — sprawdzanie poprawności** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Potok przetwarzania polecenia: jak wyzwolić procedurę obsługi poleceń

Następne pytanie jest jak wywołać procedurę obsługi poleceń. Można ręcznie wywołać go z każdego powiązane kontrolera platformy ASP.NET Core. Jednak podejście byłaby zbyt powiązane i nie jest idealnym rozwiązaniem.

Pozostałe dwie główne opcje, które są zalecane opcje, są:

- Za pomocą wzorca artefakt mediatora w pamięci.

- Za pomocą kolejki wiadomości asynchronicznych, Between kontrolery i obsługi.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Użyj wzorca mediatora (w pamięci) w potoku do polecenia

Jak pokazano w rysunek 7-25, w podejście CQRS za pomocą inteligentnego mediatora, podobne do magistrali danych w pamięci, czyli inteligentnego przekierować do obsługi odpowiednie polecenia, na podstawie typu polecenia lub obiekt DTO odbierane. Pojedynczy czarne strzałki powodują przechodzenie między składnikami reprezentują zależności między obiektami (w wielu przypadkach wprowadzony przez DI) przy użyciu ich powiązane interakcje.

![Powiększanie z poprzedniej ilustracji: kontrolera platformy ASP.NET Core wysyła polecenie do potoku polecenie MediatR firmy, dzięki czemu staną się odpowiedni program obsługi.](./media/image22.png)

**Rysunek 7-25**. Przy użyciu wzorca mediatora w procesie w mikrousłudze CQRS w jednym

Przyczyna, pasującą przy użyciu wzorca mediatora jest w aplikacjach dla przedsiębiorstw, przetwarzania żądań może skomplikowane. Chcesz mieć możliwość dodawania open numerem odciąż przekrojowe zagadnienia, takie jak rejestrowanie, sprawdzanie poprawności, inspekcji i zabezpieczeń. W takich przypadkach możesz polegać na potok mediatora (zobacz [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern)) do zapewnienia oznacza, że te dodatkowe zachowania lub odciąż przekrojowe zagadnienia.

Mediatora jest obiektem, który hermetyzuje "jak" tego procesu: koordynuje jej wykonanie w oparciu o stan, wywoływaną sposób obsługi polecenia lub ładunku zapewniają do programu obsługi. Za pomocą składnika mediatora można zastosować odciąż przekrojowe zagadnienia w sposób scentralizowany i przejrzystości, stosując dekoratory (lub [potoku zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) ponieważ [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Aby uzyskać więcej informacji, zobacz [wzorzec Dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratory i zachowania są podobne do [aspekt zorientowanej na programowania (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)tylko zastosowane do zarządzanych przez składnik mediatora potoku określonego procesu. AOP aspektów, które implementują odciąż przekrojowe zagadnienia są stosowane na podstawie *weavers aspekt* wprowadzonym w czasie kompilacji lub w oparciu o przejęciu wywołanie obiektu. Oba typowe podejścia AOP czasami mówi się, że działania ""Magia, ponieważ nie jest łatwo sprawdzić, jak AOP wykonuje swoją pracę. Podczas pracy z poważnymi problemami i zgłaszanie usterek, AOP może być trudne do debugowania. Z drugiej strony, te dekoratory/zachowania są jawne i stosowane tylko w kontekście mediatora, dlatego debugowanie jest znacznie bardziej przewidywalna i łatwe.

Na przykład w ramach aplikacji eShopOnContainers porządkowanie mikrousług, wprowadziliśmy dwa przykładowe zachowania, [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy i [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy. Implementacja zachowania zostało wyjaśnione w następnej sekcji, pokazując, jak korzysta z ramach aplikacji eShopOnContainers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Użyj komunikat kolejki (poza poza procesem) w potoku do polecenia

Inną możliwością polega na użyciu wiadomości asynchronicznych, na podstawie brokerów lub kolejki komunikatów, jak pokazano w rysunek 7-26. Tej opcji można również łączyć za pomocą składnika mediatora bezpośrednio poprzedzający program obsługi poleceń.

![Potok polecenia również może być obsługiwany przez kolejki komunikatów o wysokiej dostępności umożliwia umieszczanie w odpowiedni program obsługi poleceń.](./media/image23.png)

**Rysunek 7-26**. Za pomocą poleceń CQRS przy użyciu kolejek komunikatów (poza procesem i komunikacji między procesami)

Za pomocą komunikatu kolejki, aby zaakceptować dodatkowo polecenia skomplikować potoku dla polecenia, ponieważ prawdopodobnie konieczne będzie rozdzielenie potoku na dwa procesy połączone za pośrednictwem kolejki komunikatów zewnętrznych. Nadal należy używać, jeśli chcesz mieć zwiększona skalowalność i wydajność w oparciu asynchronicznej obsługi komunikatów. Należy wziąć pod uwagę, że w przypadku rysunek 7-26 kontrolera po prostu publikuje komunikat polecenia w kolejce i zwraca. Następnie programy obsługi poleceń przetwarzania komunikatów w swoim własnym tempie. Oznacza to ogromne korzyści kolejek: kolejki komunikatów może pełnić rolę bufora w przypadkach, gdy skalowalność funkcji hyper jest wymagane, tak samo jak w przypadku zasobów lub innego scenariusza, z dużej ilości danych przychodzących.

Jednak ze względu na charakter asynchronicznego kolejek komunikatów, musisz opracować sposób komunikowania się z aplikacją klienta o powodzeniu lub niepowodzeniu polecenia procesu. Zgodnie z zasadą nigdy nie należy użyć polecenia "fire and forget". Aplikacja biznesowa, co musi wiedzieć, jeśli polecenie zostało przetworzone pomyślnie, lub były co najmniej zweryfikowane i zaakceptowane.

Dlatego możliwość odpowiedzi do klienta po upewnieniu się, komunikat polecenia, który został przesłany do asynchronicznego kolejki zwiększa złożoność do systemu, w porównaniu do procesu poleceń w procesie, który zwraca wynik operacji po uruchomieniu transakcji. Korzystanie z kolejek, konieczne może być zwracanie wyniku procesu polecenia za pomocą innych wiadomości wynik operacji, które będzie wymagać dodatkowych składników i komunikacja z niestandardowych w systemie.

Ponadto polecenia asynchroniczne są jednokierunkowe poleceń, które w wielu przypadkach może być niepotrzebne, opisane w poniższej interesujące wymiany między Burtsev Alexey i Grega Younga w [rozmowę online](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

> \[Burtsev Alexey\] znaleźć się części kodu, których użytkownicy korzystają z obsługi polecenia async lub jednym ze sposobów polecenia wiadomości bez jakiegokolwiek powodu, aby to zrobić (nie robią pewne długotrwałej operacji, nie są one wykonywane kod asynchroniczny zewnętrznych, ich nie nawet przechodzą aplikacji granica korzystać z magistrali komunikatów). Dlaczego wprowadzają tę złożoność niepotrzebne? I w rzeczywistości mogę nie jeszcze widoczne przykładowy kod CQRS z blokowaniem programy obsługi poleceń do tej pory, chociaż będzie działać prawidłowo w większości przypadków.
>
> \[Grega Younga\] \[... \] polecenia asynchronicznego nie istnieje; jest faktycznie inne zdarzenie. Jeśli musisz zaakceptować, co możesz Wyślij do mnie i wywołać zdarzenie, jeśli nie zgadzam się, nie jest już możesz informuje mnie coś zrobić \[oznacza to, że nie jest poleceniem\]. Chodzi o Ciebie informuje mnie, które coś, co zostało zrobione. To niewielka różnica na początku, ale ma wpływ wiele.

Asynchroniczne poleceń znaczne zwiększenie złożoności systemu, ponieważ nie ma prostego sposobu wskazują błędy. W związku z tym polecenia asynchronicznego nie są zalecane innych niż razie wymagania dotyczące skalowania lub w szczególnych przypadkach podczas komunikacji wewnętrznej mikrousług za pomocą komunikatów. W takich przypadkach należy projektować oddzielnego systemu raportowania i odzyskiwania na wypadek awarii.

W pierwszej wersji w ramach aplikacji eShopOnContainers zdecydowaliśmy się użyć polecenia synchronicznego przetwarzania, pracy z żądań HTTP i opartych na podstawie wzorca mediatora. Łatwo pozwala to zwracać powodzenie lub niepowodzenie procesu, podobnie jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.

W każdym przypadku powinna to być decyzji na podstawie swojej aplikacji lub w mikrousługach wymagań biznesowych.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementowanie potok przetwarzania polecenia z wzorcem mediatora (MediatR)

Jako przykład implementacji ten przewodnik przedstawia, przy użyciu potoku w trakcie oparta na wzorcu mediatora do wprowadzania polecenia dysku i polecenia route w pamięci do obsługi polecenie right. Przewodnik proponuje, stosując [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) w celu oddzielenia odciąż przekrojowe zagadnienia.

Do wykonania w programie .NET Core są dostępne wiele bibliotek typu open source, które implementują wzorzec mediatora. Biblioteka używanych w tym przewodniku jest [MediatR](https://github.com/jbogard/MediatR) biblioteki typu open source (utworzonego przez Jimmy Bogard), ale można użyć innego podejścia. MediatR jest niewielki i prosty biblioteki, która umożliwia przetwarzanie komunikatów w pamięci, takich jak polecenia, stosując dekoratory lub zachowania.

Przy użyciu wzorca mediatora pomaga zmniejszyć sprzężenia i aby wyizolować problemy żądanej pracy, automatycznie łącząc program obsługi, który wykonuje pracę — w tym przypadku do obsługi polecenia.

Kolejny powód dobre, aby użyć wzorca mediatora zostało wyjaśnione przy użyciu Jimmy Bogard podczas przeglądania tego przewodnika:

> Myślę, może być warte wymienienie testowania w tym miejscu — zapewnia dobre rozwiązanie zgodne okno w zachowanie systemu. Żądania w poziomie w odpowiedzi. Odkryliśmy, że aspekt bardzo przydatne w budynku spójnie zachowuje się testy.

Najpierw Przyjrzyjmy się kontrolkę webapi przykładowe faktycznie użycia obiektu mediatora. Obiekt mediatora nie była używana, należy wstrzyknąć wszystkie zależności dla tego kontrolera, np. obiekt rejestratora i innym osobom. W związku z tym Konstruktor będzie dość skomplikowane. Z drugiej strony Jeśli używasz obiektu mediatora, Konstruktor kontrolera może być znacznie prostsze, za pomocą tylko kilku zależności zamiast wiele zależności, jeśli masz jeden na przekrojowe operacji, jak w poniższym przykładzie:

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

Aby zobaczyć, że mediatora zapewnia czyste i zwarte Konstruktor kontrolera interfejsu API sieci Web. Ponadto w ramach metody kontrolera kod, aby wysłać polecenie do obiektu mediatora jest prawie jeden wiersz:

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

### <a name="implement-idempotent-commands"></a>Implementowanie polecenia idempotentne

W **ramach aplikacji eShopOnContainers**, stanowi przykład bardziej zaawansowane niż powyższe przesyła obiekt CreateOrderCommand z mikrousług porządkowanie. Ale ponieważ proces biznesowy zamówienia jest nieco bardziej skomplikowane, a w naszym przypadku faktycznie zacznie w mikrousługach koszyka, ta akcja przesyłania obiektu CreateOrderCommand jest przeprowadzane z poziomu programu obsługi zdarzeń integracji o nazwie > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) zamiast kontrolkę webapi proste wywoływane z klienta aplikacji, tak jak w poprzednim przykładzie prostsze.

Niemniej jednak akcji przesyłania polecenie, aby MediatR jest bardzo podobne, jak pokazano w poniższym kodzie.

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

Jednak ten przypadek jest również nieco bardziej zaawansowane, ponieważ również wdrażamy polecenia idempotentne. Proces CreateOrderCommand powinny być idempotentne, więc jeśli ten sam komunikat pochodzi zduplikowane za pośrednictwem sieci, w związku z jakiegokolwiek powodu, takie jak ponownych prób, takiej samej kolejności firm będzie przetwarzany tylko raz.

To jest implementowany przez opakowanie polecenia firmy (w tym przypadku CreateOrderCommand) i osadzenie jej w IdentifiedCommand ogólnych, które są śledzone przez identyfikator każdej wiadomości przesyłanych w sieci, która ma być idempotentne.

W poniższym kodzie widać, IdentifiedCommand to nic więcej niż obiekt DTO z i identyfikator oraz obiektu polecenia opakowana biznesowego.

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

Następnie commandhandler — obiekt dla IdentifiedCommand o nazwie [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) zasadniczo sprawdzi, czy identyfikator dostępne jako część komunikatu już istnieje w tabeli. Jeśli już istnieje, że polecenie nie będzie on przetworzony ponownie, więc działa jako polecenia idempotentne. Czy infrastruktury kodu odbywa się przez `_requestManager.ExistAsync` poniżej wywołania metody.

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

Ponieważ IdentifiedCommand zachowuje się jak koperty polecenie biznesowych, gdy polecenie firmy musi zostać przetworzona, ponieważ nie jest powtarzane identyfikator, następnie go zajmuje to polecenie wewnętrzne firmy i ponownie przesyła do mediatora, tak jak w ostatniej części kodu, gdy powyżej uruchamianie `_mediator.Send(message.Command)`, z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Podczas tych czynności spowoduje link i uruchom program obsługi poleceń firm, w tym przypadku, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) której działa transakcje w bazie danych porządkowanie, jak pokazano w poniższym kodzie.

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

### <a name="register-the-types-used-by-mediatr"></a>Zarejestruj typy używane przez MediatR

MediatR znać swojej klasy programu obsługi poleceń, należy zarejestrować klasy mediatora i klasy programu obsługi poleceń w kontenerze IoC. Domyślnie MediatR używa Autofac jako kontenera IoC, ale można również użyć wbudowanych kontenerów platformy ASP.NET Core IoC lub innego kontenera obsługiwane przez MediatR.

Poniższy kod pokazuje, jak zarejestrować poleceń i typy mediatora firmy, korzystając z modułów Autofac.

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

Jest to miejsce "Magia" miejsce w przypadku stron MediatR.

Ponieważ każdy program obsługi poleceń implementuje ogólnego `IAsyncRequestHandler<T>` interfejsu, podczas rejestrowania zestawów, ten kod rejestruje `RegisteredAssemblyTypes` oznaczenie wszystkich typów `IAsyncRequestHandler` podczas odnoszących się `CommandHandlers` z ich `Commands`, dziękuję do relacji, o których wspomniano w `CommandHandler` klasy, jak w poniższym przykładzie:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

To kod, który jest odwrotnie skorelowana poleceń z programy obsługi poleceń. Program obsługi jest prostą klasę, ale dziedziczy `RequestHandler<T>`, gdzie T jest typem polecenia i MediatR upewnia się, zostanie wywołana z ładunkiem poprawne (polecenie).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Zastosuj odciąż przekrojowe zagadnienia podczas przetwarzania polecenia za pomocą zachowań w MediatR

Ma jedną rzecz: możliwość zastosowania odciąż przekrojowe zagadnienia do potoku mediatora. Widać również na końcu kod modułu rejestracji Autofac jak rejestruje typ zachowania, w szczególności klasę niestandardową LoggingBehavior i klasa ValidatorBehavior. Ale można dodać inne niestandardowe zachowania zbyt.

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

Czy [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) klasy można zaimplementować jako następujący kod, który rejestruje informacje na temat obsługi polecenia wykonywane i tego, czy zakończyło się pomyślnie lub nie.

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

Po prostu zaimplementowanie tej klasy zachowanie i rejestrując ją w potoku (w powyższym MediatorModule) wszystkie polecenia, które są przetwarzane przez MediatR będziesz rejestrować informacje dotyczące wykonywania.

Ramach aplikacji eShopOnContainers porządkowanie mikrousług ma zastosowanie również w drugim zachowanie dla podstawowe sprawdzanie poprawności, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) klasy, która opiera się na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w Poniższy kod:

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

Zachowanie w tym miejscu jest wywoływanie wyjątek, jeśli weryfikacja zakończy się niepowodzeniem, ale mogą także zwracać obiekt wyniku, zawierający wynik polecenia w przypadku powodzenia lub Sprawdzanie poprawności wiadomości w przypadku, gdy nie. To będzie prawdopodobnie ułatwiają wyświetlić wyniki sprawdzania poprawności dla użytkownika.

Następnie, na podstawie [FluentValidation](https://github.com/JeremySkinner/FluentValidation) , możemy utworzyć bibliotekę sprawdzania poprawności dla danych przekazanych z CreateOrderCommand, tak jak w poniższym kodzie:

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

Można utworzyć dodatkowe sprawdzanie poprawności. Jest to bardzo prosty i przejrzysty sposób wdrożyć swoje polecenie walidacji.

W podobny sposób można zaimplementować innych zachowań dodatkowe aspekty lub odciąż przekrojowe zagadnienia, które mają być stosowane do poleceń, gdy ich obsługę.

#### <a name="additional-resources"></a>Dodatkowe zasoby

##### <a name="the-mediator-pattern"></a>Wzorzec mediatora

- **Wzorzec mediatora** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Wzorzec dekoratora

- **Wzorzec dekoratora** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** Repozytorium GitHub. \
  <https://github.com/jbogard/MediatR>

- **Podejście CQRS z MediatR i AutoMapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Umieść swoje kontrolery na diecie: Wpisy i poleceń.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Realizowanie odciąż przekrojowe zagadnienia z potokiem mediatora** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **Podejście CQRS i REST: doskonałe dopasowanie** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Przykłady MediatR potoku** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Wycinek pionowy testu świetlnymi MediatR i platformy ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Rozszerzenia MediatR do wstrzykiwania zależności firmy Microsoft, wydania** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Sprawdzanie poprawności Fluent

- **Jeremy Skinner. FluentValidation.** Repozytorium GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Poprzednie](microservice-application-layer-web-api-design.md)
> [dalej](../implement-resilient-applications/index.md)
