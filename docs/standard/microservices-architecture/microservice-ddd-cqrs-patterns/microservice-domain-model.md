---
title: Projektowanie modelu domeny mikrousługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie modelu domeny mikrousługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: 2776412b96d4ed141f48814d19d2deaa1a71520d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579460"
---
# <a name="designing-a-microservice-domain-model"></a>Projektowanie modelu domeny mikrousługi

*Zdefiniuj jeden model domeny sformatowanego dla każdego mikrousługi biznesowych lub ograniczonych kontekstu*

Celem użytkownika jest utworzyć model pojedynczej domeny spójności dla każdej mikrousługi biznesowych lub ograniczonych kontekstu (BC). Należy pamiętać, mimo że BC lub business mikrousługi czasami może składają się z kilka fizycznych usług mających modelu pojedynczej domeny. Model domeny konieczne jest przechwycenie reguł, zachowanie, języka biznesowych i ograniczenia w pojedynczym kontekście ograniczony lub mikrousługi biznesowych, który reprezentuje.

## <a name="the-domain-entity-pattern"></a>Wzorzec jednostką domeny

Jednostki reprezentują obiektów domeny i są zdefiniowane głównie przez ich tożsamość, ciągłość działania i trwałości wraz z upływem czasu i nie tylko atrybuty, które obejmują je. Jak Evans marek jest wyświetlany komunikat "obiekt zdefiniowane głównie przez jego tożsamość jest nazywany jednostką." Jednostki są bardzo ważne w modelu domeny, ponieważ są one base dla modelu. W związku z tym należy zidentyfikować i zaprojektować je dokładnie.

*Tożsamość jednostki mogą przechodzić wielu mikrousług lub kontekstów ograniczone.*

Tej samej tożsamości (choć nie tego samego obiektu) należy modelować wielu kontekstów ograniczony lub mikrousług. Która nie oznacza, że tej samej jednostki o tej samej logiki i atrybuty są realizowane w wielu sytuacjach ograniczone. Zamiast tego jednostek w kontekście każdego ograniczone ograniczyć ich atrybuty i zachowania do wymaganych w tym ograniczone kontekście domeny.

Na przykład jednostki nabywcy może być najbardziej atrybutów osoby, które są zdefiniowane w jednostce użytkownika w profilu lub tożsamości mikrousługi, włącznie z tożsamością. Jednak obiektu nabywców porządkowania mikrousługi może być mniej atrybutów, ponieważ niektóre dane nabywców jest związane z procesem kolejności. Kontekst każdego mikrousługi lub ograniczonych kontekstu ma wpływ na jego modelu domeny.

*Domeny jednostek musi implementować zachowanie oprócz atrybuty danych wykonawczych*

Jednostka w domenie w DDD musi implementować logika domeny lub zachowanie związane z danymi jednostki (obiekt dostęp do pamięci). Na przykład w ramach klasy jednostki kolejności musi mieć logiki biznesowej i operacje zaimplementowane jako metody dla zadań, takich jak dodawanie elementu kolejności, sprawdzanie poprawności danych i obliczenie razem. Metody jednostki zajmie się invariants i reguł jednostki zamiast te reguły rozłożyć na warstwie aplikacji.

Rysunek 9-8 zawiera jednostki domeny, która implementuje nie tylko atrybuty danych, ale metod lub operacji z logiką pokrewne domeny.

![](./media/image9.png)

**Rysunek 9 — 8**. Przykład projektu jednostki domeny Implementowanie danych oraz zachowanie

Oczywiście czasami może być jednostek, które nie implementują wszelka logika jako część klasy jednostka. Może to nastąpić w obiektów podrzędnych w agregacji, jeśli obiekt podrzędny nie ma żadnych specjalnych logiki, ponieważ większość logiki jest zdefiniowana w katalogu głównym łączny. Jeśli masz mikrousługi złożonych, ma dużo logiki zaimplementowana w klasach usługi zamiast w jednostkach domeny może być należących do modelu domeny anemic wyjaśniono w poniższej sekcji.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Model domeny sformatowany i model domeny anemic

W jego post [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Fowler pole w tym artykule opisano model domeny anemic w ten sposób:

Podstawowe objawem Anemic Model domeny jest najpierw co blush wygląda czegoś. Istnieją obiekty o nazwie wiele po rzeczowniki w obszarze domeny i te obiekty są połączone z zaawansowanych relacje i struktura, która ma modeli domeny wartość true. Catch zaczyna się po wyświetleniu zachowania i okazuje się, że tych obiektów, jest bardzo trudno żadnych zachowanie nadawania nieco więcej niż torebki o metodach ustawiających i pobierających.

Oczywiście, gdy używasz modelu domeny anemic tych modeli danych będą używane w z zestawu obiektów usługi (tradycyjnie nazwane *warstwie business*) który Przechwyć wszystkie domeny lub logikę biznesową. Warstwa biznesowa znajduje się w modelu danych i używa modelu danych tylko jako dane.

Model domeny anemic to po prostu projekt styl procedurach. Obiekty anemic obiektów nie są prawdziwe obiektów, ponieważ mają zachowanie (metody). Posiadają tylko właściwości danych i dlatego nie jest zorientowany obiektowo projektu. Ustawiając limit to zachowanie na obiekty usługi (warstwie business) zasadniczo na końcu [kod postaci spaghetti](https://en.wikipedia.org/wiki/Spaghetti_code) lub [skryptów transakcji](https://martinfowler.com/eaaCatalog/transactionScript.html), i w związku z tym utracić zalety modelu domeny udostępnia.

Niezależnie od tego, jeśli mikrousługi lub ograniczonych kontekstu jest bardzo proste (CRUD usługa), modelu domeny anemic w formie obiektów jednostek z tylko właściwości danych może być wystarczająca i nie może być warto Implementowanie bardziej złożonych wzorców DDD. W takim przypadku będzie po prostu modelu trwałości, ponieważ utworzono celowo jednostki z danych tylko do celów CRUD.

Właśnie dlatego architektury mikrousług są idealne w przypadku wielu architektura w zależności od kontekstu każdego ograniczone. Na przykład w eShopOnContainers, porządkowania mikrousługi implementuje wzorce DDD, ale mikrousługi katalogu, co jest proste usługi CRUD, nie ma.

Niektórzy użytkownicy powiedzieć, że model anemic domeny jest uruchomiony wzorca. Naprawdę zależy to implementacja. Jeśli mikrousługi tworzona jest prosty wystarczająco (na przykład usługa CRUD), po modelu anemic domeny nie jest uruchomiony wzorca. Jednak jeśli zachodzi potrzeba rozwiązania złożoność mikrousługi domeny, która ma wiele kiedykolwiek zmiana reguł biznesowych, model anemic domeny może być układ wzorca dla tego mikrousługi lub ograniczonych kontekstu. W takim przypadku projektowania jako wzbogaconej modelu za pomocą jednostek zawierających dane plus zachowanie, a także wykonania dodatkowych wzorce DDD (agregacje, obiekty wartości itp.) może być ogromnych korzyści długoterminowe Powodzenie takich mikrousługi.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **DevIQ. Domain Entity**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Pole Fowler. Model domeny**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Pole Fowler. Model domeny Anemic**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Wzorzec obiektu wartości

Wspomnianego Evans marek ma "wiele obiektów nie miały koncepcyjnej tożsamości. Te obiekty opisują niektórych parametrów przedmiotu".

Jednostka wymaga tożsamości, ale w systemie, która nie istnieje wiele obiektów, takich jak wzorzec obiektu wartości. Obiekt wartości jest obiektem przy nie koncepcyjnej tożsamości, która opisuje aspekt domeny. Są to obiekty, które można utworzyć wystąpienia do reprezentowania elementów projektu, które tylko dotyczą możesz tymczasowo. Najważniejsze informacje dotyczące *co* , nie są *kto* są. Przykłady obejmują liczb i ciągów, ale można też pojęcia wyższego poziomu, takich jak grupy atrybutów.

Coś, co jest jednostką w mikrousługi może nie być jednostki w innym mikrousługi, ponieważ w drugim przypadku kontekstu ograniczone może mieć inne znaczenie. Na przykład adres w aplikacji handlu elektronicznego może nie mieć tożsamości, ponieważ może stanowić jedynie grupy atrybutów profilu klienta dla osoby lub firmy. W takim przypadku adres powinny być klasyfikowane jako obiekt wartości. Jednak w aplikacji firmy narzędzie energii elektrycznej adres odbiorcy może być ważne dla domeny biznesowych. Adres musi mieć tożsamość, więc systemów rozliczeniowych może być bezpośrednio połączony adres. W takim przypadku adres powinny być klasyfikowane jako jednostką domeny.

Osoba mająca imię i nazwisko jest zwykle jednostki osoba ma tożsamość, nawet jeśli imię i nazwisko pokrywa się z innego zestawu wartości, np. Jeśli te nazwy odnosi się także do innej osoby.

Obiekty wartości są trudne do zarządzania relacyjnymi bazami danych i ORMs, takie jak EF, natomiast w dokumencie ukierunkowane bazy danych, które są łatwiejsze do zaimplementowania i użycia.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Pole Fowler. Value — wzorzec obiektu**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Wartość obiektu**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **Wartości obiektów w rozwoju Test-Driven**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto wartość — obiekty*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.** (Książki; zawiera omówienie obiekty wartości) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>Wzorzec agregacji

Model domeny zawiera klaster jednostek inne dane i procesy, które można kontrolować istotny obszar funkcje, takie jak realizacji order lub magazynu. Do bardziej szczegółowych DDD jest agregacji, opisujący klastra lub grupy jednostek i zachowania, które mogą być traktowane jako jednostka spójności.

Zazwyczaj Definiowanie agregacji na podstawie transakcji, które są potrzebne. Klasycznym przykładem jest zamówienie zawiera także listę kolejności elementów. Element kolejności zwykle jest jednostką. Ale będzie ona jednostce podrzędnej w wartości zagregowanej kolejności, będzie również zawierać jednostki zamówienia jego obiektu głównego, zwykle nazywane głównego agregacji.

Identyfikowanie agregacji może być trudne. Wartość zagregowana jest grupy obiektów, które muszą być zgodne ze sobą, ale nie można po prostu wybierz grupy obiektów i etykietowanie agregacji. Musi rozpoczynać się od domeny koncepcji i zastanowić, jednostek, które są używane w najbardziej typowych transakcje powiązane z tą koncepcją. Tych jednostek, które muszą być spójna transakcyjnie są, co stanowi agregacji. Analiza operacji transakcji jest prawdopodobnie najlepszy sposób, aby zidentyfikować agregacji.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Wzorzec główny agregacji lub głównego jednostki

Wartość zagregowana składa się z co najmniej jedną jednostkę: głównego agregacji, nazywany również jednostki głównej lub podstawowej jednostki. Ponadto może mieć wiele jednostek podrzędnych i obiekty wartości ze wszystkimi jednostek i obiektów, które współpracują, aby zaimplementować wymagane zachowanie i transakcji.

Główny agregacji ma na celu zapewnienia spójności agregacji; należy go tylko punkt wejścia dla aktualizacji do zagregowania za pośrednictwem metody lub operacji w całkowitym Klasa główna. Należy wprowadzić zmiany do podmiotów w obrębie agregacji tylko przy użyciu głównego agregacji. Jest ochrona spójności wartości zagregowanej, biorąc pod uwagę wszystkie invariants i reguły spójności, potrzebne do wykonania w Twojej agregacji. W przypadku zmiany obiektu podrzędnego jednostka lub wartość niezależnie głównego agregacji nie powiodło się, że agregacji jest w prawidłowym stanie. Byłoby jak tabelę z utracić etap. Obsługa spójności jest głównym celem głównego agregacji.

9 rysunek-9, widać agreguje próbki jak kupujący agregacji, zawierający pojedynczy element (łączny głównego nabywców). Agregacja kolejności zawiera wiele jednostek i obiektu wartości.

![](./media/image10.png)

**Rysunek 9 — 9**. Przykład agregacji w wielu lub pojedynczego jednostek

Należy zauważyć, że Agregacja nabywców można kolejne podrzędne jednostki, w zależności od domeny, co w porządkowania mikrousługi w aplikacji odwołanie eShopOnContainers. Rysunek 9 — 9 przedstawiono tylko przypadek, w którym kupujący ma pojedynczej jednostki, na przykład wartość zagregowaną, która zawiera tylko głównego agregacji.

Aby zachowanie separacji agregacji i zapewnić wyraźne granice między nimi, jest dobrym rozwiązaniem w modelu domeny DDD, aby uniemożliwić bezpośrednie nawigacji między wartości zagregowanych i tylko posiadające pole klucza obcego (klucz OBCY) zgodnie z implementacją w [ Kolejność modelu domeny mikrousługi](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) w eShopOnContainers. Jednostki kolejności ma tylko pola klucza Obcego dla kupującemu, ale nie EF Core właściwość nawigacji, jak pokazano w poniższym kodzie:

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

Identyfikowanie i Praca z wartości zagregowanych wymaga badań i obsługi. Aby uzyskać więcej informacji zobacz następujące listę dodatkowych zasobów.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Vaughn Vernon. Efektywnym projektowaniu agregacji — część I: modelowania pojedynczego agregacji**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_SPOŁECZNOŚCI\_OPISOWYCH\_AGREGUJE\_części \_pdf 1.*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Skuteczne agregacji projektu — część II: Tworzenie wartości zagregowanych współpracują**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *

-   **Vaughn Vernon. Skuteczne agregacji projektu — część III: Uzyskanie wglądu za pomocą odnajdywania**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *

-   **Sergey Grybniak. Wzorce projektowe taktyczne DDD**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Krzysztof Richardson. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowanych**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. Wzorzec agregacji**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[Previous] (ddd-oriented-microservice.md) [Next] (net-core-microservice-domain-model.md)
