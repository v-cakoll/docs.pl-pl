---
title: Implementowanie modelu domeny mikrousługi za pomocą platformy .NET Core
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze szczegółami implementacji modelu domeny zorientowanego na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 0b42ecc2440faf5870b2d99e31d03cda00b21ce0
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306915"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implementowanie modelu domeny mikrousługi przy użyciu platformy .NET Core

W poprzedniej sekcji zostały wyjaśnione podstawowe zasady projektowania i wzorce projektowania modelu domeny. Teraz można poznać możliwe sposoby implementacji modelu domeny za pomocą platformy .NET Core (zwykłego \# kodu C) i EF Core. Model domeny będzie złożony po prostu z Twojego kodu. Będzie on miał tylko wymagania dotyczące modelu EF Core, ale nie rzeczywiste zależności w EF. Nie należy mieć sztywnych zależności ani odwołań do EF Core ani żadnych innych ORM w modelu domeny.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domeny w niestandardowej bibliotece .NET Standard

Organizacja folderu używana dla aplikacji referencyjnej eShopOnContainers pokazuje model DDD dla aplikacji. Może się okazać, że inna organizacja folderu bardziej jasno komunikuje się z opcjami projektu dla aplikacji. Jak widać na rysunku 7-10, w modelu domeny porządkowania są dwie wartości zagregowane, zagregowana kolejność i agregacja kupująca. Każda agregacja jest grupą obiektów domeny i obiekty wartości, chociaż może istnieć agregacja złożona z pojedynczej jednostki domeny (jednostki zagregowanej lub głównej).

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Zrzut ekranu przedstawiający projekt porządkowanie. domena w Eksplorator rozwiązań.":::
Widok Eksplorator rozwiązań dla projektu porządkowania. domeny, przedstawiający folder AggregatesModel zawierający foldery BuyerAggregate i OrderAggregate, każdy z nich zawierający klasy jednostek, pliki obiektów wartości i tak dalej.
:::image-end:::

**Rysunek 7-10**. Struktura modelu domeny dla mikrousługi porządkowania w eShopOnContainers

Ponadto warstwa modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymaganiami infrastruktury modelu domeny. Innymi słowy, te interfejsy wyrażają, jakie repozytoria i metody muszą być implementowane przez warstwę infrastruktury. Ważne jest, aby implementacja repozytoriów została umieszczona poza warstwą modelu domeny w bibliotece warstw infrastruktury, więc warstwa modelu domeny nie jest "zanieczyszczona" przez interfejsy API lub klasy z technologii infrastruktury, takich jak Entity Framework.

Można również wyświetlić folder [SeedWork](https://martinfowler.com/bliki/Seedwork.html) zawierający niestandardowe klasy bazowe, których można użyć jako podstawy dla jednostek domeny i obiektów wartości, dzięki czemu nie masz nadmiarowego kodu w klasie obiektów każdej domeny.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Agregowanie struktury w niestandardowej bibliotece .NET Standard

Agregacja odnosi się do klastra obiektów domeny zgrupowanych w celu dopasowania spójności transakcyjnej. Te obiekty mogą być wystąpieniami jednostek (z których jednym jest agregacją główną lub główną jednostką) oraz wszelkimi dodatkowymi obiektami wartości.

Spójność transakcyjna oznacza, że agregowanie ma zagwarantować spójność i aktualność na końcu działania biznesowego. Na przykład agregacja kolejności z modelu domeny mikrousługi eShopOnContainers porządkowania składa się, jak pokazano na rysunku 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Zrzut ekranu przedstawiający folder OrderAggregate i jego klasy.":::
Szczegółowy widok folderu OrderAggregate: Address.cs jest obiektem wartości, IOrderRepository jest interfejsem repozytorium, Order.cs jest elementem głównym agregacji, OrderItem.cs jest jednostką podrzędną, a OrderStatus.cs jest klasą wyliczania.
:::image-end:::

**Rysunek 7-11**. Agregacja kolejności w rozwiązaniu Visual Studio

W przypadku otwarcia dowolnego pliku w folderze zagregowanym można zobaczyć, jak jest on oznaczony jako niestandardową klasę bazową lub interfejs, taki jak obiekt jednostki lub wartości, zgodnie z zaimplementowaną w folderze [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) .

## <a name="implement-domain-entities-as-poco-classes"></a>Implementowanie jednostek domeny jako klas POCO

Aby zaimplementować model domeny w programie .NET, należy utworzyć klasy POCO, które implementują jednostki domeny. W poniższym przykładzie Klasa Order jest definiowana jako jednostka, a także jako zagregowany element główny. Ponieważ Klasa Order dziedziczy z klasy podstawowej jednostki, może ponownie użyć wspólnego kodu związanego z jednostkami. Należy pamiętać, że te klasy bazowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc jest to kod, a nie kod infrastruktury z ORM, np. EF.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

Należy pamiętać, że jest to jednostka domeny zaimplementowana jako Klasa POCO. Nie ma żadnej bezpośredniej zależności od Entity Framework Core ani żadnych innych struktur infrastruktury. Ta implementacja ma charakter w DDD, po prostu kod C# implementujący model domeny.

Ponadto Klasa ma interfejs o nazwie IAggregateRoot. Ten interfejs jest pustym interfejsem, czasami nazywany *interfejsem znacznika*, który jest używany tylko do wskazania, że ta klasa jednostki jest również zagregowanym elementem głównym.

Interfejs znacznika jest czasami traktowany jako Antywzorzec; Jednak jest to również czysty sposób oznaczania klasy, szczególnie w przypadku, gdy ten interfejs może się pojawić. Atrybut może być innym wyborem dla znacznika, ale jest szybszym sposobem wyświetlania klasy bazowej (jednostki) obok interfejsu IAggregate zamiast umieszczania znacznika atrybutu agregacji powyżej klasy. W każdym przypadku jest to sprawa z preferencjami.

Posiadanie zagregowanego elementu głównego oznacza, że większość kodu związanego z spójnością i regułami biznesowymi jednostek agregacji powinna być implementowana jako metody w klasie głównej agregacji Order (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji). Nie należy tworzyć ani aktualizować obiektów OrderItems niezależnie lub bezpośrednio; Klasa AggregateRoot musi utrzymywać kontrolę i spójność każdej operacji aktualizacji z jej jednostkami podrzędnymi.

## <a name="encapsulate-data-in-the-domain-entities"></a>Hermetyzuj dane w jednostkach domeny

Typowy problem związany z modelami jednostek polega na udostępnieniu właściwości nawigacji kolekcji jako typów list dostępnych publicznie. Pozwala to deweloperom współpracownikom na manipulowanie zawartością tych typów kolekcji, co może spowodować obejście ważnych reguł firmy związanych z kolekcją, prawdopodobnie pozostawiając obiekt w nieprawidłowym stanie. Rozwiązaniem tego problemu jest udostępnienie dostępu tylko do odczytu do powiązanych kolekcji i jawne dostarczenie metod, które definiują sposoby manipulowania nimi przez klientów.

W poprzednim kodzie należy zauważyć, że wiele atrybutów jest tylko do odczytu lub jako prywatne i można je aktualizować tylko przy użyciu metod klasy, więc każda aktualizacja traktuje nieodmiany i logikę domeny biznesowej określone w metodach klasy.

Na przykład, poniższe wzorce DDD, ** *nie* należy wykonywać następujących czynności** z żadnej metody obsługi poleceń lub klasy aplikacji (w rzeczywistości powinna to być niemożliwe):

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

W tym przypadku metoda Add jest czysto operacją dodawania danych, z bezpośrednim dostępem do kolekcji OrderItems. W związku z tym większość logiki domeny, reguł lub walidacji związanych z tą operacją z jednostkami podrzędnymi zostanie rozłożona między warstwą aplikacji (programy obsługi poleceń i kontrolery API sieci Web).

Jeśli przejdziesz do zagregowanego elementu głównego, zagregowany element główny nie może zagwarantować jego nieważności, jego poprawności lub jego spójności. Ostatecznie będziesz mieć kod spaghetti lub transakcyjny kod skryptu.

Aby obserwować wzorce DDD, jednostki nie mogą mieć publicznych metod ustawiających we właściwościach Entity. Zmiany w jednostce powinny być oparte na jawnych metodach z jawnym, powszechnie używanym językiem o zmianach wykonywanych w jednostce.

Ponadto kolekcje w jednostce (takie jak Order Items) powinny być właściwościami tylko do odczytu (Metoda AsReadOnly omówiona później). Należy ją zaktualizować tylko z poziomu metod klasy głównej agregacji lub metod jednostki podrzędnej.

Jak widać w kodzie dla głównego elementu agregacji zamówienia, wszystkie metody ustawiające powinny być prywatne lub tylko do odczytu na zewnątrz, tak aby każda operacja na danych jednostki lub jej jednostkach podrzędnych była wykonywana za pomocą metod klasy Entity. Zapewnia to spójność kontrolowanych i zorientowanych obiektowo, a nie implementowanie kodu skryptu transakcyjnego.

Poniższy fragment kodu przedstawia właściwy sposób kodowania zadania dodawania obiektu OrderItem do agregacji zamówienia.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object's business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

W tym fragmencie kodu większość walidacji lub logiki związanych z tworzeniem obiektu OrderItem będzie podlegać kontroli nad elementem głównym agregacji zamówienia — w metodzie AddOrderItem — szczególnie walidacji i logika związanych z innymi elementami w agregacji. Na przykład można uzyskać ten sam element produktu, co w wyniku wielu wywołań AddOrderItem. W tej metodzie można przeanalizować elementy produktu i skonsolidować te same elementy produktu w pojedynczy obiekt OrderItem o kilku jednostkach. Ponadto jeśli istnieją różne kwoty rabatu, ale identyfikator produktu jest taki sam, prawdopodobnie obowiązuje wyższy rabat. Ta zasada ma zastosowanie do każdej innej logiki domeny dla obiektu OrderItem.

Ponadto nowa operacja OrderItem (params) również będzie kontrolowana i wykonywana przez metodę AddOrderItem z poziomu głównego agregacji Order. W związku z tym większość logiki lub walidacji związanych z tą operacją (szczególnie każdy ma wpływ na spójność między innymi jednostkami podrzędnymi) będzie w jednym miejscu w ramach zagregowanego elementu głównego. Jest to ostateczny cel zagregowanego wzorca głównego.

W przypadku korzystania z Entity Framework Core 1,1 lub nowszej jednostka DDD może być lepiej wyrażona, ponieważ umożliwia ona [Mapowanie do pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości. Jest to przydatne w przypadku ochrony kolekcji jednostek podrzędnych lub obiektów wartości. Dzięki temu ulepszeniu można używać prostych prywatnych pól zamiast właściwości i można zaimplementować dowolną aktualizację do kolekcji pól w metodach publicznych i zapewnić dostęp tylko do odczytu za pomocą metody AsReadOnly.

W DDD należy zaktualizować jednostkę tylko za pomocą metod w jednostce (lub w konstruktorze) w celu kontrolowania wszelkich niezmiennej i spójności danych, dlatego właściwości są definiowane tylko przy użyciu metody dostępu get. Właściwości są obsługiwane przez pola prywatne. Dostęp do prywatnych elementów członkowskich można uzyskać tylko z poziomu klasy. Istnieje jednak jeden wyjątek: EF Core muszą także ustawiać te pola (aby można było zwrócić obiekt z prawidłowymi wartościami).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Właściwości mapy z dostępem tylko do pól w tabeli bazy danych

Mapowanie właściwości do kolumn tabeli bazy danych nie jest odpowiedzialnością w domenie, ale częścią infrastruktury i warstwy trwałości. Tutaj wspominamy o nowych możliwościach EF Core 1,1 lub nowszych związanych z tym, jak można modelować jednostki. Dodatkowe szczegóły dotyczące tego tematu zostały omówione w sekcji infrastruktura i trwałość.

W przypadku korzystania z EF Core 1,0 lub nowszego w kontekście DbContext należy zmapować właściwości, które są zdefiniowane tylko przez metody pobierające do rzeczywistych pól w tabeli bazy danych. Jest to realizowane za pomocą metody HasField klasy PropertyBuilder.

### <a name="map-fields-without-properties"></a>Mapuj pola bez właściwości

Przy użyciu funkcji w EF Core 1,1 lub nowszej, aby zamapować kolumny na pola, można również nie używać właściwości. Zamiast tego można po prostu zmapować kolumny z tabeli do pól. Typowym przypadkiem użycia jest to pole prywatne dla stanu wewnętrznego, do którego nie trzeba uzyskiwać dostępu poza jednostką.

Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pól prywatnych, takich jak `_paymentMethodId` pole, które nie ma powiązanej właściwości dla metody ustawiającej lub pobierającej. To pole może być również obliczane w ramach logiki biznesowej i stosowane z metod zamówienia, ale muszą być również utrwalane w bazie danych. Tak więc w EF Core (od wersji 1.1) istnieje możliwość mapowania pola bez powiązanej właściwości do kolumny w bazie danych. Jest to również wyjaśnione w sekcji [warstwa infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) tego przewodnika.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Vaughn Vernon. Modelowanie agregacji z DDD i Entity Framework.** Należy zauważyć, że *nie* jest to Entity Framework Core. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Punkty danych — kodowanie dla projektowania opartego na domenie: porady dotyczące Deweloperzyów danych** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **UDI Dahan. Jak utworzyć w pełni hermetyzowane modele domen** \
  <https://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Poprzedni](microservice-domain-model.md) 
>  [Dalej](seedwork-domain-model-base-classes-interfaces.md)
