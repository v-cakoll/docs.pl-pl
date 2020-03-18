---
title: Implementowanie modelu domeny mikrousługi za pomocą platformy .NET Core
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami implementacji modelu domeny zorientowanej na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: bff9cbda08e519038056268151a1721427f0ac01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972044"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implementowanie modelu domeny mikrousług za pomocą programu .NET Core

W poprzedniej sekcji wyjaśniono podstawowe zasady projektowania i wzorce projektowania modelu domeny. Teraz nadszedł czas, aby zbadać możliwe sposoby zaimplementowania\# modelu domeny przy użyciu .NET Core (zwykły kod C) i EF Core. Należy pamiętać, że model domeny będzie składać się po prostu z kodu. Będzie miał tylko wymagania modelu EF Core, ale nie rzeczywiste zależności od EF. Nie powinny mieć twarde zależności lub odwołania do EF Core lub innych ORM w modelu domeny.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domeny w niestandardowej standardowej bibliotece .NET

Organizacja folderów używana dla aplikacji referencyjnej eShopOnContainers demonstruje model DDD dla aplikacji. Może się okazać, że inna organizacja folderów wyraźniej komunikuje wybory projektowe dokonane dla aplikacji. Jak widać na rysunku 7-10, w modelu domeny zamawiania istnieją dwa agregaty, agregacja zamówień i agregacja kupującego. Każda agregacja jest grupą jednostek domeny i obiektów wartości, chociaż może mieć agregację składającą się z pojedynczej jednostki domeny (jednostki głównej lub głównej).

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Zrzut ekranu przedstawiający projekt Ordering.Domain w Eksploratorze rozwiązań.":::
Widok Eksploratorrozwiązania dla projektu Ordering.Domain, zawierający folder AggregatesModel zawierający foldery BuyerAggregate i OrderAggregate, z których każdy zawiera klasy jednostek, pliki obiektów wartości itd.
:::image-end:::

**Rysunek 7-10**. Struktura modelu domeny dla mikrousługi porządkowania w eShopOnContainers

Ponadto warstwa modelu domeny zawiera kontrakty repozytorium (interfejsy), które są wymagania infrastrukturalne modelu domeny. Innymi słowy te interfejsy wyrazić, jakie repozytoria i metody warstwy infrastruktury musi implementować. Bardzo ważne jest, aby implementacja repozytoriów została umieszczona poza warstwą modelu domeny w bibliotece warstwy infrastruktury, dzięki czemu warstwa modelu domeny nie jest "zanieczyszczona" interfejsem API lub klasami z technologii infrastruktury, takich jak Entity Framework.

Można również wyświetlić [seedwork](https://martinfowler.com/bliki/Seedwork.html) folder, który zawiera niestandardowe klasy podstawowe, które można użyć jako podstawa dla jednostek domeny i obiektów wartości, więc nie masz nadmiarowego kodu w klasie obiektów każdej domeny.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Agregacja struktury w niestandardowej bibliotece standardu .NET

Agregat odnosi się do klastra obiektów domeny zgrupowanych w celu dopasowania spójności transakcyjnej. Obiekty te mogą być wystąpienia jednostek (z których jeden jest agregacji jednostki głównej lub głównej) plus wszelkie dodatkowe obiekty wartości.

Spójność transakcyjna oznacza, że wartość zagregowana jest spójna i aktualna na koniec akcji biznesowej. Na przykład agregacji zamówienia z eShopOnContainers zamawiania modelu domeny mikrousługi składa się, jak pokazano na rysunku 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Zrzut ekranu przedstawiający folder OrderAggregate i jego klasy.":::
Szczegółowy widok orderuzagregacji folderu: Address.cs jest obiektem wartości, IOrderRepository jest interfejsem repozytorium, Order.cs jest zagregowanym katalogiem głównym, OrderItem.cs jest jednostką podrzędną, a OrderStatus.cs jest klasą wyliczenia.
:::image-end:::

**Rysunek 7-11**. Agregacja zamówień w rozwiązaniu programu Visual Studio

Jeśli otworzysz dowolny z plików w folderze agregacji, można zobaczyć, jak jest oznaczony jako niestandardowej klasy podstawowej lub interfejsu, takich jak jednostki lub obiektu wartości, jak zaimplementowane w folderze [SeedWork.](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork)

## <a name="implement-domain-entities-as-poco-classes"></a>Implementowanie jednostek domeny jako klas POCO

Model domeny można zaimplementować w .NET, tworząc klasy POCO, które implementują jednostki domeny. W poniższym przykładzie Order klasy jest zdefiniowany jako jednostki, a także jako zagregowanego katalogu głównego. Ponieważ Order Klasa pochodzi od jednostki klasy podstawowej, można ponownie użyć wspólnego kodu związane z jednostek. Należy pamiętać, że te klasy podstawowe i interfejsy są definiowane przez użytkownika w projekcie modelu domeny, więc jest to kod, a nie kod infrastruktury z ORM jak EF.

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

Należy pamiętać, że jest to jednostka domeny zaimplementowana jako klasa POCO. Nie ma żadnej bezpośredniej zależności od core framework jednostki lub innych ramach infrastruktury. Ta implementacja jest tak, jak powinna\# być w DDD, tylko kod C implementacji modelu domeny.

Ponadto klasa jest ozdobiona interfejsem o nazwie IAggregateRoot. Ten interfejs jest pusty interfejs, czasami nazywany *interfejs znacznika*, który jest używany tylko do wskazania, że ta klasa jednostki jest również zagregowanego katalogu głównego.

Interfejs znacznika jest czasami uważany za anty-wzór; jednak jest to również czysty sposób, aby oznaczyć klasę, zwłaszcza gdy ten interfejs może ewoluować. Atrybut może być innym wyborem dla znacznika, ale szybciej jest zobaczyć klasy podstawowej (jednostki) obok interfejsu IAggregate zamiast umieszczania zagregowanego znacznika atrybutu nad klasą. W każdym razie jest to kwestia preferencji.

Posiadanie katalogu głównego agregacji oznacza, że większość kodu związanego z regułami spójności i działalności jednostek agregacji powinna być zaimplementowana jako metody w klasie głównej agregacji zamówienia (na przykład AddOrderItem podczas dodawania OrderItem obiektu do agregacji) . Nie należy tworzyć ani aktualizować OrderItems obiektów niezależnie lub bezpośrednio; AggregateRoot klasa musi zachować kontrolę i spójność każdej operacji aktualizacji względem jego jednostek podrzędnych.

## <a name="encapsulate-data-in-the-domain-entities"></a>Hermetyzować dane w jednostkach domeny

Typowym problemem w modelach jednostek jest, że uwidaczniają właściwości nawigacji kolekcji jako publicznie dostępne typy list. Dzięki temu każdy deweloper współpracownika do manipulowania zawartością tych typów kolekcji, które mogą ominąć ważne reguły biznesowe związane z kolekcji, ewentualnie pozostawiając obiekt w nieprawidłowym stanie. Rozwiązaniem tego problemu jest udostępnienie dostępu tylko do odczytu do powiązanych kolekcji i jawnie podać metody, które definiują sposoby, w których klienci mogą manipulować nimi.

W poprzednim kodzie należy pamiętać, że wiele atrybutów są tylko do odczytu lub prywatnych i są dostępne tylko przez metody klasy, więc każda aktualizacja uważa, że domeny biznesowej invariants i logiki określonych w ramach metod klasy.

Na przykład po wzorce DDD, ** *nie* należy wykonywać następujące z** dowolnej metody obsługi poleceń lub klasy warstwy aplikacji (w rzeczywistości powinno być niemożliwe, aby to zrobić):

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

W takim przypadku Add metoda jest czysto operacji, aby dodać dane, z bezpośrednim dostępem do OrderItems kolekcji. W związku z tym większość logiki domeny, reguł lub weryfikacji związanych z tą operacją z jednostkami podrzędnych będzie rozłożona na warstwę aplikacji (programy obsługi poleceń i kontrolery interfejsu API sieci Web).

Jeśli obejść katalogu głównego agregacji, agregacji katalogu głównego nie może zagwarantować jego invariants, jego ważności lub jego spójności. Po pewnym czasie będziesz miał kod spaghetti lub kod skryptu transakcyjnego.

Aby wykonać wzorce DDD, jednostki nie mogą mieć ustawiaczy publicznych w żadnej właściwości jednostki. Zmiany w jednostce powinny być napędzane przez jawne metody z jawnym wszechobecnym językiem o zmianie, którą wykonują w jednostce.

Ponadto kolekcje w jednostce (jak elementy zamówienia) powinny być właściwościtylko do odczytu (AsReadOnly metoda wyjaśnione później). Powinno być możliwe zaktualizowanie go tylko z poziomu zagregowanych metod klasy głównej lub metod encji podrzędnej.

Jak widać w kodzie zagregowanego katalogu głównego zagregowanego zamówienia, wszystkie metody ustawiania powinny być prywatne lub przynajmniej tylko do odczytu zewnętrznie, tak aby każda operacja względem danych jednostki lub jej jednostek podrzędnych musi być wykonywana za pomocą metod w klasie jednostki. Pozwala to zachować spójność w sposób kontrolowany i obiektowy zamiast implementowania kodu skryptu transakcyjnego.

Poniższy fragment kodu pokazuje właściwy sposób kodowania zadania dodawania OrderItem obiektu do Zaagregacji Zamówienia.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

W tym fragmencie kodu większość sprawdzania poprawności lub logiki związanych z tworzeniem OrderItem obiektu będzie pod kontrolą katalogu głównego agregacji zamówienia — w AddOrderItem metody — szczególnie sprawdzania poprawności i logiki związane z innymi elementami w agregacji. Na przykład może pojawić się ten sam element produktu w wyniku wielu wywołań AddOrderItem. W tej metodzie można zbadać towary produktu i skonsolidować te same elementy produktu w jednym OrderItem obiektu z kilku jednostek. Ponadto, jeśli istnieją różne kwoty rabatu, ale identyfikator produktu jest taki sam, prawdopodobnie zastosujesz wyższy rabat. Zasada ta ma zastosowanie do każdej innej logiki domeny dla OrderItem obiektu.

Ponadto nowa operacja OrderItem(params) będzie również kontrolowana i wykonywana przez metodę AddOrderItem z katalogu głównego agregacji zamówienia. W związku z tym większość logiki lub sprawdzania poprawności związanych z tą operacją (zwłaszcza wszystko, co wpływa na spójność między innymi jednostkami podrzędnych) będzie w jednym miejscu w katalogu głównym agregacji. To jest ostateczny cel wzorca głównego agregacji.

Korzystając z jednostki Framework Core 1.1 lub nowsze, jednostka DDD może być lepiej wyrażone, ponieważ umożliwia [mapowanie do pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości. Jest to przydatne podczas ochrony kolekcji jednostek podrzędnych lub obiektów wartości. Za pomocą tego rozszerzenia można użyć prostych pól prywatnych zamiast właściwości i można zaimplementować dowolną aktualizację do kolekcji pól w metodach publicznych i zapewnić dostęp tylko do odczytu za pośrednictwem AsReadOnly metody.

W DDD chcesz zaktualizować jednostkę tylko za pomocą metod w jednostce (lub konstruktora) w celu kontrolowania wszelkich niezmiennych i spójności danych, więc właściwości są definiowane tylko za pomocą get akcesora. Właściwości są wspierane przez pola prywatne. Członkowie prywatni są dostępowi tylko z poziomu klasy. Jednak istnieje jeden wyjątek: EF Core musi ustawić te pola, jak również (dzięki czemu można zwrócić obiekt z odpowiednimi wartościami).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Właściwości mapy z tylko uzyskać akcesory do pól w tabeli bazy danych

Mapowanie właściwości do kolumn tabeli bazy danych nie jest odpowiedzialnością domeny, ale częścią warstwy infrastruktury i trwałości. Wspominamy o tym tutaj tylko dlatego, że są świadomi nowych możliwości w EF Core 1.1 lub nowszych związane z jak można modelować jednostki. Dodatkowe szczegóły na ten temat są wyjaśnione w sekcji infrastruktury i trwałości.

Korzystając z EF Core 1.0 lub nowszego, w ramach DbContext należy mapować właściwości, które są zdefiniowane tylko z metodami rozejrzające do rzeczywistych pól w tabeli bazy danych. Odbywa się to za pomocą HasField metody PropertyBuilder klasy.

### <a name="map-fields-without-properties"></a>Mapowanie pól bez właściwości

Dzięki funkcji w EF Core 1.1 lub nowszej do mapowania kolumn do pól, jest również możliwe, aby nie używać właściwości. Zamiast tego możesz po prostu mapować kolumny z tabeli na pola. Typowy przypadek użycia dla tego jest pola prywatne dla stanu wewnętrznego, który nie musi być dostępny spoza jednostki.

Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pól `_paymentMethodId` prywatnych, takich jak pole, które nie mają właściwości pokrewnej dla podmiotu ustawiającego lub rozdzielającego. To pole może być również obliczane w ramach logiki biznesowej zamówienia i używane z metod zamówienia, ale musi być również utrwalić w bazie danych. Tak więc w EF Core (od 1.1) istnieje sposób mapowania pola bez powiązanej właściwości do kolumny w bazie danych. Jest to również wyjaśnione w sekcji [Warstwa infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) w tym przewodniku.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Vaughn Vernon. Modelowanie agregacji za pomocą DDD i framework jednostek.** Należy zauważyć, że *nie* jest to rdzeń framework jednostki. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Punkty danych — kodowanie dla projektowania opartego na domenie: porady dotyczące deweloperów zorientowanych na dane** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **Udi Dahan. Jak tworzyć w pełni hermetyzowane modele domen** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Poprzedni](microservice-domain-model.md)
> [następny](seedwork-domain-model-base-classes-interfaces.md)
