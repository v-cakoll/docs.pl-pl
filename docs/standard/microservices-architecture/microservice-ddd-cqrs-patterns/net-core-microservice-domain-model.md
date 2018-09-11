---
title: Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272283"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core 

W poprzedniej sekcji zostały wyjaśnione podstawowych projektowania i wzorce projektowania modelu domeny. Teraz nadszedł czas, aby poznać sposoby, aby wdrożyć model domeny przy użyciu platformy .NET Core (C zwykły\# kodu) i programem EF Core. Należy pamiętać, że modelu domeny będzie składać się z kodu. Tylko wymagania modelu platformy EF Core, ale w zależności nie rzeczywistych będzie miał na EF. W modelu domeny nie powinna mieć twarde zależności lub odwołania do programu EF Core lub innych ORM.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domeny niestandardowej biblioteki .NET Standard

Organizacja folderu używane w ramach aplikacji eShopOnContainers aplikacji referencyjnej pokazuje modelu DDD dla aplikacji. Może się okazać, że organizacja inny folder wyraźniej komunikuje się uzasadnienie wyboru tych elementów, dla aplikacji. Jak widać na rysunku 9-10 w szeregowania modelu domeny istnieją dwie wartości zagregowane, aggregate kolejności i agregacji kupujący. Każdej agregacji jest grupą domeny jednostek i obiektów wartości, mimo że może mieć również składa się z jednostką jednej domenie (głównego agregacji lub jednostki głównej) wartość zagregowana.

![](./media/image11.png)

**Rysunek 9 – 10**. Struktura modelu domeny mikrousługi sortowania, w ramach aplikacji eShopOnContainers

Ponadto w warstwie modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymagania dotyczące infrastruktury modelu domeny. Innymi słowy, te interfejsy express repozytoriów, jakie musi implementować warstwy infrastruktury i w jaki sposób. Koniecznie, implementacja repozytoriów można umieścić poza warstwie modelu domeny w bibliotece warstwę infrastruktury, więc warstwie modelu domeny nie jest "zanieczyszczona" interfejsu API lub klasy z technologii infrastruktury, takich jak Entity Framework.

Można również wyświetlić [SeedWork](https://martinfowler.com/bliki/Seedwork.html) obiektów folder zawierający niestandardowe klasy bazowej, która służy jako podstawa dla domeny, jednostki i wartości, więc nie trzeba nadmiarowy kod w klasie obiektów w każdej domenie.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Tworzenie struktury wartości zagregowanych umieszczonych w niestandardowej biblioteki .NET Standard

Wartość zagregowana odnosi się do klastra, w przypadku obiektów domeny zgrupowane razem, aby dopasować poziom spójności transakcyjnej. Te obiekty można wystąpień jednostki (z których jeden jest głównego agregacji lub jednostki głównej) oraz wszystkie obiekty dodatkową wartość.

Poziom spójności transakcyjnej oznacza, że wartość zagregowana jest gwarantowane były spójne i na bieżąco na końcu działań biznesowych. Na przykład składa się agregacji kolejność, w ramach aplikacji eShopOnContainers kolejność modelu domeny mikrousługi, jak pokazano w rysunek 9 – 11.

![](./media/image12.png)

**Rysunek 9 – 11**. Kolejność agregacji w rozwiązaniu Visual Studio

Jeśli możesz otworzyć dowolny z plików w folderze agregacji, możesz zobaczyć jak jest oznaczony jako niestandardowej klasy bazowej lub interfejsu, takich jak jednostka lub wartość obiektu, zaimplementowanego w [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folderu.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implementowanie jednostki domeny jako klasy POCO

Model domeny na platformie .NET implementuje są przez utworzenie klas POCO, które implementują jednostki domeny. W poniższym przykładzie klasa kolejność jest zdefiniowana jako jednostki, a także jako główny agregacji. Ponieważ klasa kolejności pochodzi z klasy podstawowej jednostki, można ponownie użyć wspólny kod powiązane z jednostkami. Mieć na uwadze, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc Twoja kod, a nie kod infrastruktury z ORM, takie jak EF.

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

Należy pamiętać, że to jest jednostka domeny implementowany jako klasa POCO. Nie ma żadnych zależności bezpośrednich platformy Entity Framework Core lub dowolnej architektury infrastruktury. Ta implementacja jest należycie w DDD, po prostu C\# kodu Implementowanie modelu domeny.

Ponadto klasa zostanie nadany interfejs o nazwie IAggregateRoot. Ten interfejs jest pusty interfejs, czasami nazywane *interfejs znacznika*, która jest używana tylko w celu wskazania, że ta klasa jednostki jest również głównego agregacji.

To interfejs znacznika czasami jest traktowany jako wzorzec ochrony; jednak go jest również eleganckie rozwiązanie, aby oznaczyć klasę, szczególnie w przypadku, gdy ten interfejs może zmieniających się. Atrybut może być inne rozwiązanie dla znacznika, ale jest szybsze wyświetlić klasę bazową (jednostka) obok interfejsu IAggregate zamiast umieszczać znacznika atrybutu dotyczącego agregacji powyżej klasy. Niezależnie od lokalizacji tych preferencji, jest w każdym przypadku.

Posiadanie oznacza głównego agregacji, że większość kodu związane z spójności i reguł biznesowych, jednostek agregacji powinny zostać wdrożone jako metody w klasie głównego agregacji zamówienia (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji) . Użytkownik powinien nie utworzyć lub zaktualizować OrderItems obiekty niezależnie lub bezpośrednio; Klasa AggregateRoot musi przechowywać kontroli i spójności żadnych operacji aktualizacji, przed jego obiektów podrzędnych.

## <a name="encapsulating-data-in-the-domain-entities"></a>Zawieranie danymi w obiektach domeny

Typowy problem w modelach jednostki jest eksponowanie właściwości nawigacji kolekcji jako typy list dostępny publicznie. Dzięki temu każdy Deweloper współpracownika do manipulowania zawartość tych kolekcji typów, które może pominąć reguł biznesowych ważne związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie. Rozwiązaniem tego problemu do prezentowania dostęp tylko do odczytu do powiązanej kolekcji i jawnie określić metody, które definiują sposób, w którym klienci nimi manipulować.

W poprzednim kodzie należy pamiętać, że wiele atrybutów są tylko do odczytu "lub" prywatnych są one tylko nadaje się do aktualizacji za pomocą metod klasy tak Każda aktualizacja wymaga invariants domeny biznesowej konta i logikę określoną w ramach metod klasy.

Na przykład, następujące wzorców DDD, wykonaj następujące czynności *nie* wykonaj następujące czynności z dowolnego polecenia obsługi metody lub aplikacji warstwy klasy:

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

W tym przypadku metoda Add jest wyłącznie operacji dodawania danych bezpośredni dostęp do kolekcji OrderItems. W związku z tym większość logika domeny, zasady lub walidacji dotyczące czy operację, używając obiektów podrzędnych będą rozkłada warstwy aplikacji (programy obsługi poleceń i kontrolerów internetowych interfejsów API).

Po przejściu wokół głównego agregacji głównego agregacji nie gwarantuje jego invariants, jego ważności lub jego zgodności. Po pewnym czasie będziesz mieć postaci spaghetti kod lub kod skryptu transakcji.

Aby skorzystać z wzorców DDD, jednostki nie może mieć publiczne metody ustawiające w dowolnej właściwości jednostki. Zmiany w jednostce powinien opierać się za pomocą jawnych metod za pomocą jawnego wszechobecne języka o zmiany, które wykonują w jednostce.

Ponadto, kolekcjami w obrębie jednostki (takie jak elementy zamówienia) powinny być właściwości tylko do odczytu (metoda AsReadOnly opisana później). Można zaktualizować go tylko w obrębie głównego agregacji metod klasy lub metody jednostki podrzędne.

Jak widać w kodzie dla głównego agregacji w kolejności, wszystkie metody ustawiające powinny być prywatne lub co najmniej tylko do odczytu zewnętrznie, tak aby każdej operacji względem danych jednostki lub jego obiektów podrzędnych musi być wykonywane za pomocą metody w klasie jednostki. Zapewnia to spójność w sposób kontrolowany i zorientowane obiektowo, a nie Implementowanie kod skryptu transakcji.

Poniższy fragment kodu przedstawia prawidłowego sposobu kod: zadanie dodawania obiektu OrderItem do zagregowania zamówienia.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

W tym fragmencie kodu, większość operacji sprawdzania poprawności lub logiki powiązane z tworzenia obiektu OrderItem będą kontroli głównego agregacji zamówienia — w metodzie AddOrderItem — szczególnie logiki i walidacji powiązanych do innych elementów w agregacji. Na przykład możesz otrzymać ten sam element produktu w wyniku AddOrderItem wielu wywołań. W tej metodzie można zbadać elementów produktu i konsolidować tych samych towarów produktu w pojedynczy obiekt OrderItem z kilku jednostek. Ponadto jeśli istnieją kwoty różnych rabatów, ale identyfikator produktu jest taki sam, będzie prawdopodobnie stosować ten rabat wyższy. Ta zasada ma zastosowanie do innych logiki domeny dla obiektu OrderItem.

Ponadto nową operację OrderItem(params) będzie również być kontrolowany i wykonywane przez metodę AddOrderItem z katalogu głównego agregacji zamówienia. W związku z tym większość logiki i walidacji związane z konieczności operacji (szczególnie wszystko, co ma wpływ na spójność między innymi jednostkami podrzędnych) w jednym miejscu w obrębie głównego agregacji. To jest ostatecznym celem wzorzec głównego agregacji.

Gdy korzystasz z programu Entity Framework Core 1.1 lub później, jednostki DDD można lepiej wyrazić ponieważ zezwala ona na [zamapowane na pola](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości. Jest to przydatne w przypadku ochrony kolekcji jednostki podrzędne lub obiekty wartości. Za pomocą tego rozszerzenia można użyć prostego pola prywatne, zamiast właściwości i można zaimplementować wszelkich aktualizacji kolekcji pól za pomocą metod publicznych i zapewnić dostęp tylko do odczytu za pośrednictwem metody AsReadOnly.

W DDD, które chcesz zaktualizować jednostki, tylko za pośrednictwem metody w jednostki (lub konstruktora) w celu kontrolowania wszelkie niezmiennej i spójność danych więc właściwości są zdefiniowane tylko za pomocą metody dostępu get. Właściwości są wspierane przez pola prywatne. Prywatne elementy Członkowskie może zostać oceniony jedynie z w klasie. Jednak miejsca jeden wyjątek: programu EF Core musi ustawić również tych pól.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapowanie właściwości z tylko pobieranie metod dostępu do pól w tabeli bazy danych

Mapowanie właściwości do kolumny tabeli bazy danych nie jest odpowiedzialność domeny, ale część warstwy infrastruktury i trwałości. Firma Microsoft wspomnieć o tego w tym miejscu po prostu, dzięki czemu masz świadomość nowe możliwości w wersji EF Core 1.1 lub później powiązany sposób można modelować jednostek. Dodatkowe szczegóły dotyczące tego tematu opisano w sekcji infrastruktury i trwałości.

Gdy używasz programu EF Core 1.0, w ramach kontekstu DbContext należy zamapować właściwości, które są zdefiniowane tylko w przypadku metod pobierających do rzeczywistego pól w tabeli bazy danych. Można to zrobić za pomocą metody HasField klasy PropertyBuilder.

### <a name="mapping-fields-without-properties"></a>Mapowanie pól bez właściwości

Dzięki funkcji w programie EF Core 1.1 lub nowszej mapowania kolumn na pola użytkownik może również nie korzystać z właściwości. Zamiast tego po prostu można mapować kolumny z tabeli pola. Typowy przypadek użycia tego jest pola prywatne, wewnętrzne stanu, które nie muszą być dostępne spoza jednostki.

Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pola prywatne, takie jak `_paymentMethodId` pola, mających nie powiązane właściwości metody ustawiającej lub metody pobierającej. Również być obliczane w kolejności logiki biznesowej i użycia w kolejności metod tego pola, ale w celu jego utrwalenia w bazie danych również musi. Dlatego w programie EF Core (od wersji 1.1) istnieje sposób mapowania pól bez właściwości powiązanych z kolumną w bazie danych. To także szczegółowo [warstwy infrastruktury](#the-infrastructure-layer) części tego przewodnika.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Vaughn Vernon. Modelowanie agregacji za pomocą zastosowania projektowania DDD i Entity Framework.** Należy zauważyć, że jest to *nie* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Kodowanie dla projektowania opartego na domenie: wskazówki dla deweloperów skoncentrowane na danych**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan. Jak utworzyć w pełni hermetyzowane modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Poprzednie](microservice-domain-model.md)
[dalej](seedwork-domain-model-base-classes-interfaces.md)
