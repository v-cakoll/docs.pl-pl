---
title: Implementowanie modelu domeny mikrousługi za pomocą platformy .NET Core
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami implementacji modelu domeny zorientowanego na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 24f700b371d998cf99cbcf260a5278d797cb39d4
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988430"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implementowanie modelu domeny mikrousług za pomocą platformy .NET Core

W poprzedniej sekcji wyjaśniono podstawowe zasady projektowania i wzorce projektowania modelu domeny. Teraz nadszedł czas, aby zbadać możliwe sposoby zaimplementowania\# modelu domeny przy użyciu .NET Core (zwykły kod C) i EF Core. Należy pamiętać, że model domeny będzie składać się po prostu z kodu. Będzie miał tylko ef podstawowe wymagania modelu, ale nie rzeczywiste zależności od EF. Nie powinny mieć twardych zależności lub odwołania do EF Core lub innych ORM w modelu domeny.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domeny w niestandardowej bibliotece standardowej platformy .NET

Organizacja folderów używana dla aplikacji referencyjnej eShopOnContainers demonstruje model DDD dla aplikacji. Może się okazać, że inna organizacja folderów wyraźniej komunikuje wybory projektowe dokonane dla aplikacji. Jak widać na rysunku 7-10, w modelu domeny zamawiania znajdują się dwa agregaty, agregacja zamówienia i agregacja kupującego. Każda agregacja jest grupą jednostek domeny i obiektów wartości, chociaż można mieć agregację składającą się z pojedynczej jednostki domeny (agregującej jednostki głównej lub głównej).

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Zrzut ekranu przedstawiający projekt Ordering.Domain w Eksploratorze rozwiązań.":::
W widoku Eksploratora rozwiązań dla projektu Ordering.Domain, pokazano folder AggregatesModel zawierający foldery BuyerAggregate i OrderAggregate, z których każdy zawiera klasy jednostek, pliki obiektów wartości i tak dalej.
:::image-end:::

**Rysunek 7-10**. Struktura modelu domeny dla mikrousługi zamawiania w eShopOnContainers

Ponadto warstwa modelu domeny zawiera kontrakty repozytorium (interfejsy), które są wymaganiami infrastruktury modelu domeny. Innymi słowy te interfejsy wyrażają, jakie repozytoria i metody warstwy infrastruktury musi zaimplementować. Bardzo ważne jest, aby implementacja repozytoriów była umieszczana poza warstwą modelu domeny w bibliotece warstw infrastruktury, więc warstwa modelu domeny nie jest "zanieczyszczona" przez interfejs API lub klasy z technologii infrastruktury, takich jak Entity Framework.

Można również zobaczyć [folder SeedWork,](https://martinfowler.com/bliki/Seedwork.html) który zawiera niestandardowe klasy podstawowe, które można użyć jako podstawy dla jednostek domeny i obiektów wartości, więc nie masz nadmiarowego kodu w klasie obiektów każdej domeny.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Strukturyj agregacje w niestandardowej bibliotece standardu .NET

Agregacja odwołuje się do klastra obiektów domeny zgrupowanych razem, aby dopasować spójność transakcyjną. Obiekty te mogą być wystąpienia jednostek (z których jeden jest agregująca jednostka główna lub główna) plus wszelkie dodatkowe obiekty wartości.

Spójność transakcyjna oznacza, że agregacja jest gwarantowana jako spójna i aktualna na końcu działania biznesowego. Na przykład agregacja zamówień z eShopOnContainers zamawiania modelu domeny mikrousług jest skomponowany, jak pokazano na rysunku 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Zrzut ekranu folderu OrderAggregate i jego klas.":::
Szczegółowy widok folderu OrderAggregate: Address.cs jest obiektem wartości, IOrderRepository jest interfejsem repozytorium, Order.cs jest źródłem agregacji, OrderItem.cs jest jednostką podrzędną, a OrderStatus.cs jest klasą wyliczenia.
:::image-end:::

**Rysunek 7-11**. Agregacja zamówień w programie Visual Studio

Jeśli otworzysz dowolny plik w folderze agregacji, można zobaczyć, jak jest oznaczony jako niestandardowa klasa podstawowa lub interfejs, taki jak encja lub obiekt wartości, zgodnie z implementacjami w folderze [SeedWork.](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork)

## <a name="implement-domain-entities-as-poco-classes"></a>Implementowanie jednostek domeny jako klas POCO

Zaimplementuj model domeny w .NET, tworząc klasy POCO, które implementują jednostki domeny. W poniższym przykładzie Order Klasa jest zdefiniowana jako jednostka, a także jako główny agregacji. Ponieważ Klasa Order pochodzi od klasy podstawowej jednostki, może ponownie użyć wspólnego kodu związanego z jednostkami. Należy pamiętać, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc jest to kod, a nie kod infrastruktury z ORM jak EF.

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

Należy pamiętać, że jest to jednostka domeny zaimplementowana jako klasa POCO. Nie ma żadnej bezpośredniej zależności od entity framework core lub innych struktur infrastruktury. Ta implementacja jest tak, jak powinno\# być w DDD, tylko kod C implementacji modelu domeny.

Ponadto klasa jest ozdobiona interfejsem o nazwie IAggregateRoot. Ten interfejs jest pusty interfejs, czasami nazywany *interfejs znacznika*, który jest używany tylko do wskazania, że ta klasa jednostki jest również głównym agregacji.

Interfejs znacznika jest czasami uważany za anty-wzór; jednak jest to również czysty sposób, aby oznaczyć klasę, zwłaszcza, gdy interfejs może ewoluować. Atrybut może być inny wybór dla znacznika, ale jest szybsze, aby zobaczyć klasy podstawowej (Entity) obok interfejsu IAggregate zamiast umieszczania znacznik agregacji atrybutu powyżej klasy. W każdym razie jest to kwestia preferencji.

Posiadanie zagregowanego katalogu głównego oznacza, że większość kodu związanego z spójnością i regułami biznesowymi jednostek agregujących powinny być implementowane jako metody w klasie głównej zbiorczej order (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji). Nie należy tworzyć ani aktualizować obiektów OrderItems niezależnie lub bezpośrednio; AggregateRoot klasa musi zachować kontrolę i spójność każdej operacji aktualizacji względem jego jednostek podrzędnych.

## <a name="encapsulate-data-in-the-domain-entities"></a>Hermetyzowanie danych w jednostkach domeny

Typowym problemem w modelach jednostek jest to, że uwidaczniają właściwości nawigacji kolekcji jako publicznie dostępne typy list. Dzięki temu każdy wykonawca współpracownika manipulować zawartością tych typów kolekcji, które mogą pominąć ważne reguły biznesowe związane z kolekcji, ewentualnie pozostawiając obiekt w nieprawidłowym stanie. Rozwiązaniem tego problemu jest udostępnić dostęp tylko do odczytu do powiązanych kolekcji i jawnie zapewnić metody, które definiują sposoby, w których klienci mogą manipulować nimi.

W poprzednim kodzie należy zauważyć, że wiele atrybutów są tylko do odczytu lub prywatne i są aktualizowane tylko przez metody klasy, więc każda aktualizacja uwzględnia invariants domeny biznesowej i logiki określone w ramach metod klasy.

Na przykład następujące wzorce DDD, ** *nie* należy wykonywać następujące czynności** z dowolnej metody obsługi poleceń lub klasy warstwy aplikacji (w rzeczywistości powinno być niemożliwe, aby to zrobić):

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

W takim przypadku Add metoda jest wyłącznie operacją, aby dodać dane, z bezpośrednim dostępem do OrderItems kolekcji. W związku z tym większość logiki domeny, reguł lub sprawdzania poprawności związanych z tej operacji z jednostkami podrzędnymi będą rozłożone na warstwę aplikacji (programy obsługi poleceń i kontrolery interfejsu API sieci Web).

Jeśli obejść głównego agregacji, agregacji katalogu głównego nie może zagwarantować jego invariants, jego ważności lub jego spójności. Po pewnym czasie będziesz miał kod spaghetti lub kod skryptu transakcyjnego.

Aby śledzić wzorce DDD, jednostki nie mogą mieć publicznych ustawiaczy w żadnej właściwości jednostki. Zmiany w jednostce powinny być oparte na jawnych metodach z jawnym wszechobecnym językiem na temat zmiany, którą wykonują w jednostce.

Ponadto kolekcje w obrębie jednostki (takie jak elementy zamówienia) powinny być właściwości tylko do odczytu (AsReadOnly metoda wyjaśnione później). Powinna być w stanie zaktualizować go tylko z poziomu metody klasy głównej agregacji lub metody jednostki podrzędnej.

Jak widać w kodzie dla order agregacji głównego, wszystkie setters powinny być prywatne lub przynajmniej tylko do odczytu zewnętrznie, tak, że wszelkie działania względem danych jednostki lub jej jednostek podrzędnych musi być wykonywane za pomocą metod w klasie jednostki. Utrzymuje to spójność w sposób kontrolowany i zorientowany obiektowo zamiast implementowania kodu skryptu transakcyjnego.

Poniższy fragment kodu pokazuje prawidłowy sposób kodowania zadania dodawania obiektu OrderItem do agregacji Order.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object's business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

W tym urywek większość sprawdzania poprawności lub logiki związane z tworzeniem OrderItem obiektu będzie pod kontrolą order agregacji głównego — w AddOrderItem metody, zwłaszcza sprawdzania poprawności i logiki związane z innymi elementami w agregacji. Na przykład może pojawić się ten sam element produktu w wyniku wielu wywołań AddOrderItem. W tej metodzie można sprawdzić towary produktu i skonsolidować te same elementy produktu w jeden obiekt OrderItem z kilkoma jednostkami. Ponadto jeśli istnieją różne kwoty rabatu, ale identyfikator produktu jest taki sam, prawdopodobnie zastosujesz wyższy rabat. Zasada ta ma zastosowanie do każdej innej logiki domeny dla OrderItem obiektu.

Ponadto nowa operacja OrderItem(params) będzie również kontrolowana i wykonywana przez metodę AddOrderItem z katalogu głównego agregacji Order. W związku z tym większość logiki lub sprawdzania poprawności związanych z tej operacji (zwłaszcza wszystko, co wpływa na spójność między innymi jednostkami podrzędnymi) będzie w jednym miejscu w katalogu głównym agregacji. To jest ostateczny cel agregacji wzorca głównego.

Korzystając z entity framework core 1.1 lub nowszego, jednostka DDD może być lepiej wyrażona, ponieważ umożliwia [mapowanie pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości. Jest to przydatne podczas ochrony kolekcji jednostek podrzędnych lub obiektów wartości. Dzięki temu ulepszeniu można używać prostych pól prywatnych zamiast właściwości i można zaimplementować dowolną aktualizację kolekcji pól w metodach publicznych i zapewnić dostęp tylko do odczytu za pośrednictwem metody AsReadOnly.

W DDD chcesz zaktualizować jednostkę tylko za pomocą metod w jednostce (lub konstruktora) w celu kontrolowania wszelkich niezmienne i spójność danych, więc właściwości są definiowane tylko za pomocą get akcesor. Właściwości są wspierane przez pola prywatne. Prywatnych członków można uzyskać tylko z wewnątrz klasy. Jednak istnieje jeden wyjątek: EF Core musi ustawić te pola, jak również (dzięki czemu można zwrócić obiekt z odpowiednimi wartościami).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Właściwości mapowania z dostępem tylko do pól w tabeli bazy danych

Właściwości mapowania do kolumn tabel bazy danych nie jest obowiązkiem domeny, ale częścią warstwy infrastruktury i trwałości. Wspominamy o tym tutaj tylko po to, aby być świadomi nowych możliwości w EF Core 1.1 lub później związane z jak można modelować jednostki. Dodatkowe szczegóły na ten temat są wyjaśnione w sekcji infrastruktury i trwałości.

Podczas korzystania z EF Core 1.0 lub nowszego, w DbContext należy mapować właściwości, które są zdefiniowane tylko za pomocą getters do rzeczywistych pól w tabeli bazy danych. Odbywa się to za pomocą HasField metody PropertyBuilder klasy.

### <a name="map-fields-without-properties"></a>Mapowanie pól bez właściwości

Dzięki funkcji w EF Core 1.1 lub nowszej do mapowania kolumn do pól, istnieje również możliwość nie używać właściwości. Zamiast tego można po prostu mapować kolumny z tabeli na pola. Typowym przypadkiem użycia jest to pola prywatne dla stanu wewnętrznego, do którego nie trzeba uzyskiwać dostępu spoza jednostki.

Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka `_paymentMethodId` pól prywatnych, takich jak pole, które nie mają właściwości pokrewnych dla ustawiacza lub gettera. To pole może być również obliczane w ramach logiki biznesowej zamówienia i używane z metod zamówienia, ale musi być również utrwalone w bazie danych. Tak więc w EF Core (od wersji 1.1) istnieje sposób mapowania pola bez powiązanej właściwości do kolumny w bazie danych. Jest to również wyjaśnione w sekcji [warstwy infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) w tym przewodniku.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Vaughn Vernon. Modelowanie agregatów za pomocą DDD i entity Framework.** Należy zauważyć, że *nie* jest to entity framework core. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Punkty danych — kodowanie do projektowania opartego na domenie: porady dotyczące deweloperów skoncentrowanych na danych** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **Udi Dahan. Jak utworzyć w pełni hermetyzowane modele domen** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Poprzedni](microservice-domain-model.md)
> [następny](seedwork-domain-model-base-classes-interfaces.md)
