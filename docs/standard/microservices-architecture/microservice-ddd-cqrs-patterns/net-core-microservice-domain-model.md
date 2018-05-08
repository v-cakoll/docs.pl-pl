---
title: Implementowanie modelu domeny mikrousługi z platformą .NET Core
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie modelu domeny mikrousługi z platformą .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: e0c931405b8b7e3b52bdcbd511737b449dc74273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implementowanie modelu domeny mikrousługi z platformą .NET Core 

W poprzedniej sekcji zostały wyjaśnione zasady projektowania podstawowych i wzorce projektowania modelu domeny. Teraz nadszedł czas, aby poznać możliwości, aby wdrożyć model domeny przy użyciu platformy .NET Core (zwykły C\# kodu) i EF podstawowe. Należy pamiętać, że model domeny będzie składać się z kodu. Na EF będzie mieć tylko podstawowe EF wymagania modelu, ale nie rzeczywistych zależności. Nie powinna mieć twarde zależności lub odwołania do podstawowych funkcji EF lub innych ORM modelu domeny.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domeny niestandardowe biblioteki .NET Standard

Organizacja folderu używane dla aplikacji odwołanie eShopOnContainers pokazuje DDD modelu dla aplikacji. Może się okazać, że organizacja inny folder dokładniej komunikuje się decyzji projektowych dotyczących aplikacji. Jak widać w rysunek 9 – 10 w porządkowania modelu domeny istnieją agregatów, zagregowany kolejności i nabywców agregacji. Każdego agregacji jest grupą domeny jednostek i obiektów wartość, mimo że agregacji składa się z jednostek jednej domenie, (łączny głównego lub podmiot główny) również może mieć.

![](./media/image11.png)

**Rysunek 9 – 10**. Struktura modelu domeny dla porządkowania mikrousługi w eShopOnContainers

Ponadto warstwy modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymagania dotyczące infrastruktury modelu domeny. Innymi słowy, te interfejsy express repozytoriów, jakie musi implementować warstwę infrastruktury i w jaki sposób. Jest krytyczny, że implementacja repozytoriów można umieścić poza warstwy modelu domeny, w bibliotece warstwę infrastruktury tak warstwy modelu domeny jest nie "zanieczyszczone" interfejsu API lub klas z technologii infrastruktury, takich jak Entity Framework.

Możesz również sprawdzić [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder zawierający niestandardowe klasy bazowej, która służy jako podstawa dla jednostek domeny i wartość obiekty, dlatego nie masz nadmiarowy kod w klasie obiektów w każdej domenie.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Struktury wartości zagregowanych w niestandardowa biblioteka .NET Standard

Wartość zagregowana odwołuje się do klastra obiektów domeny zgrupowane w celu dopasowania spójności transakcyjnej. Te obiekty można wystąpienia jednostek (z których jeden jest łączny głównego lub podmiot główny) oraz wszystkie obiekty dodatkowe wartości.

Spójności transakcyjnej oznacza, że agregacji gwarantuje to spójność i na bieżąco na koniec działania biznesowe. Na przykład agregacji kolejności z eShopOnContainers kolejność modelu domeny mikrousługi składa się jak pokazano w rysunek 9-11.

![](./media/image12.png)

**Rysunek 9-11**. Kolejność agregacji w rozwiązaniu Visual Studio

Po otwarciu plików w folderze agregacji widać jak jest oznaczony jako niestandardowej klasy podstawowej lub interfejsu, takich jak jednostka lub wartość obiektu, zgodnie z implementacją w [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folderu.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implementowanie jednostek domeny jako klasy POCO

Model domeny można zaimplementować w .NET przez utworzenie klas POCO, które implementują obiekty domeny. W poniższym przykładzie klasa kolejności jest zdefiniowana jako jednostki, a także jako główny agregacji. Ponieważ klasa kolejności pochodzi od klasy podstawowej jednostki, można użyć ponownie typowy Kod powiązane z jednostkami. Przy tym pamiętać, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc Twojej kod, nie infrastrukturze kod z ORM, takich jak EF.

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

Należy zauważyć, że jest jednostką domeny, zaimplementowane jako klasa POCO. Nie ma żadnych bezpośrednich zależność od Entity Framework Core lub inne struktury infrastruktury. Ta implementacja jest powinny być w DDD, po prostu C\# kod implementacji modelu domeny.

Ponadto klasa zostanie nadany interfejsu o nazwie IAggregateRoot. Ten interfejs jest interfejsem pusta, nazywane również *interfejsu znacznika*, która jest używana tylko w celu oznaczać, że ta klasa jednostki jest również głównego agregacji.

Interfejs znacznika czasami jest uznawany za wzorca oprogramowania; jednak również to czysta sposób Oznacz klasę, szczególnie w przypadku, gdy ten interfejs może rozwijającymi. Atrybut może być inne wybór dla znacznika, ale jest szybsze wyświetlić klasy podstawowej (jednostka) obok interfejsu IAggregate zamiast umieszczanie znacznika atrybutu agregacji powyżej klasy. Metter preferencji, jest w każdym przypadku.

O oznacza głównego agregacji, że większość kod powiązany spójności i reguły biznesowe jednostek wartości zagregowanej powinny zostać wdrożone jako metod klasy głównym agregacji kolejności (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji) . Nie należy utworzyć ani zaktualizować obiektów OrderItems niezależnie lub bezpośrednio; Klasa AggregateRoot musi przechowywać i kontroli spójności żadnej operacji aktualizacji, przed jego obiektów podrzędnych.

## <a name="encapsulating-data-in-the-domain-entities"></a>Zawieranie dane w jednostkach domeny

To powszechny problem w modelach jednostki jest czy udostępniają właściwości nawigacji kolekcji jako typów list publicznie. Dzięki temu każdy Deweloper współpracownika do manipulowania zawartość te typy kolekcji, których może pominąć ważnymi reguł związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie. To rozwiązanie jest ujawnia dostęp tylko do odczytu do kolekcji powiązanych i jawnie Podaj metod, które definiują sposób, w którym klienci można przekształcać je.

W poprzednim kodzie należy zauważyć, że wiele atrybutów są tylko do odczytu lub prywatnych i tylko są tak Każda aktualizacja uwzględnia invariants domeny business konta i logikę określoną w ramach metod klasy nadaje się do aktualizacji za pomocą metod klasy.

Na przykład następujące wzorce DDD należy *nie* wykonaj następujące czynności z dowolnej polecenie obsługi metody lub aplikacji warstwy klasy:

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

W tym przypadku metoda Add jest wyłącznie operacji dodawania danych, za pomocą bezpośredniego dostępu do kolekcji OrderItems. W związku z tym większość logika domeny, reguł lub Sprawdzanie poprawności dotyczące czy operację, podając obiektów podrzędnych będą rozkładane warstwy aplikacji (programy obsługi poleceń i kontrolery interfejsu API sieci Web).

Przejście wokół agregacji głównego agregacji głównego nie może zagwarantować jego invariants, ważności lub jego spójności. Po pewnym czasie będzie mieć postaci spaghetti kod lub skrypt kod.

Wykonać wzorce DDD, jednostki nie może mieć publicznych ustawiające w dowolnej właściwości jednostki. Zmian w jednostce powinny być regulowane przez jawnych metod jawne języka powszechna o zmianie, które działają one w jednostce.

Ponadto, kolekcje w ramach jednostki (np. kolejność elementów) powinny być właściwości tylko do odczytu (metoda AsReadOnly wyjaśniono później). Można zaktualizować tylko z metod klasy głównym agregacji lub metody jednostek podrzędnych.

Jak widać w kodzie dla elementu głównego agregacji w kolejności, wszystkie metody ustawiające powinny być prywatne lub co najmniej tylko do odczytu zewnętrznie, dzięki czemu ma być wykonywane za pomocą metod w klasie jednostki żadnej operacji względem danych jednostki lub jego obiektów podrzędnych. Zapewnia to dostępność spójności w sposób kontrolowanych i zorientowanym obiektowo zamiast wdrażania kodu skrypt.

Poniższy fragment kodu przedstawia prawidłowego sposobem kodu zadania dodawania obiektu OrderItem do zagregowania kolejności.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

W tym fragmencie, większość operacji sprawdzania poprawności lub logiki powiązane do utworzenia obiektu OrderItem będą kontroli głównego agregacji kolejności — w metodzie AddOrderItem — szczególnie operacji sprawdzania poprawności i logiki powiązane z innymi elementami w całkowitym. Na przykład można uzyskać ten sam element produktu w wyniku wielu wywołań AddOrderItem. W tej metodzie można zbadać elementów produktu i konsolidować te same elementy produktu w pojedynczy obiekt OrderItem z kilku jednostek. Ponadto jeśli istnieją różne stawki kwoty, ale identyfikator produktu jest taki sam, będzie prawdopodobnie Zastosuj wyższy rabat. Ta zasada ma zastosowanie do innych logika domeny dla obiekt OrderItem.

Ponadto nowej operacji OrderItem(params) utworzy również być kontrolowane i wykonywane przez metodę AddOrderItem od elementu głównego agregacji kolejności. W związku z tym większość logiki lub Sprawdzanie poprawności związane z konieczności operacji (szczególnie wszystko, co ma wpływ na spójności między innymi jednostek podrzędnych) w jednym miejscu w katalogu głównym agregacji. To jest ostatecznym celem wzorzec głównego agregacji.

Jeśli używasz Entity Framework Core 1.1 lub później, jednostki DDD można lepiej wyrazić ponieważ zezwala ona na [mapowania pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości. Jest to przydatne podczas ochrony kolekcji jednostek podrzędnych lub obiekty wartości. To rozszerzenie zamiast właściwości można korzystać z prostego pól prywatnych i można zaimplementować żadnych aktualizacji do kolekcji pola w metodach publicznego i zapewnić dostęp tylko do odczytu za pomocą metody AsReadOnly.

W DDD do zaktualizowania jednostki tylko za pośrednictwem metod w obiekcie (lub konstruktora) w celu sterowania wszystkie niezmiennej i spójność danych więc właściwości są zdefiniowane tylko za pomocą metody dostępu get. Właściwości bazują na pól prywatnych. Prywatne elementy członkowskie są dostępne tylko z należące do klasy. Jednak istnieje jeden wyjątek: EF Core musi ustawić także tych pól.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapowania właściwości z tylko Pobierz metod dostępu do pola w tabeli bazy danych

Mapowanie właściwości do kolumny tabeli bazy danych nie jest odpowiedzialność domeny, ale część warstwy infrastruktury i trwałości. Firma Microsoft informacje o tym tutaj wystarczy, aby poznać nowe funkcje w wersji 1.1 Core EF lub później związanych z jak modelu jednostki. Dodatkowe szczegóły dotyczące tego tematu opisano w sekcji infrastruktury i trwałości.

Jeśli używasz EF Core 1.0, w ramach DbContext należy zamapować właściwości, które są zdefiniowane tylko za pomocą metody pobierające, do rzeczywistych pola w tabeli bazy danych. Można to zrobić za pomocą metody HasField klasy PropertyBuilder.

### <a name="mapping-fields-without-properties"></a>Mapowanie pól bez właściwości

Dzięki funkcji w programie EF Core 1.1 lub nowszej do mapowania kolumn do pól jest również możliwe nie używać właściwości. Zamiast tego można mapować tylko kolumny tabeli do pól. Przypadek użycia wspólnych dla tego jest prywatny pól dla stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.

Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pól prywatnych, jak `_paymentMethodId` pole, które ma nie powiązanych właściwości metody ustawiającej lub metody pobierającej. Można również tego pola obliczane w kolejności logiki biznesowej i użycia w kolejności metody, ale zachodzi potrzeba jego utrwalenia w bazie danych oraz. Dlatego w EF Core (od momentu w wersji 1.1) mapują pole bez właściwości powiązanych z kolumną w bazie danych. Jest to również szczegółowo [warstwę infrastruktury](#the-infrastructure-layer) tego przewodnika.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Vaughn Vernon. Modelowanie wartości zagregowanych z DDD i strukturą Entity Framework.** Należy pamiętać, że jest to *nie* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Kodowanie oparte na domenie projektu: porady dotyczące Devs danych**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan. Jak utworzyć pełni hermetyzowany modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Poprzednie] (mikrousługi domeny model.md) [dalej] (seedwork-domain-model-base-classes-interfaces.md)
