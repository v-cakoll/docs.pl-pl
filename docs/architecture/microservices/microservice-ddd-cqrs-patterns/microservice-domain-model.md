---
title: Projektowanie modelu domeny mikrousługi
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Opis kluczowych pojęć podczas projektowania modelu domeny zorientowanego na DDD.
ms.date: 01/30/2020
ms.openlocfilehash: 628fb5c76362ec8f48367b3d69d16ea6ebd24f09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502333"
---
# <a name="design-a-microservice-domain-model"></a>Projektowanie modelu domeny mikrousług

*Zdefiniuj jeden model domeny sformatowany dla każdej mikrousługi biznesowej lub ograniczonego kontekstu.*

Twoim celem jest utworzenie jednego modelu domeny spójności dla każdej mikrousługi biznesowej lub ograniczonego kontekstu (BC). Należy jednak pamiętać, że mikrousługi bc lub biznesowe czasami może składać się z kilku usług fizycznych, które współużytkują model jednej domeny. Model domeny musi przechwytywać reguły, zachowanie, język biznesowy i ograniczenia pojedynczego ograniczonego kontekstu lub mikrousługi biznesowej, które reprezentuje.

## <a name="the-domain-entity-pattern"></a>Wzorzec encji domeny

Jednostki reprezentują obiekty domeny i są definiowane głównie przez ich tożsamość, ciągłość i trwałość w czasie, a nie tylko przez atrybuty, które je tworzą. Jak mówi Eric Evans, "obiekt definiowany głównie przez jego tożsamość jest nazywany jednostką". Jednostki są bardzo ważne w modelu domeny, ponieważ są one podstawą dla modelu. Dlatego należy je dokładnie zidentyfikować i zaprojektować.

*Tożsamości jednostki można przekreślić wiele mikrousług lub ograniczone konteksty.*

Ta sama tożsamość (czyli `Id` ta sama wartość, chociaż być może nie ta sama jednostka domeny) może być modelowana w wielu kontekstach ograniczonych lub mikrousługach. Jednak nie oznacza to, że ta sama jednostka, z tych samych atrybutów i logiki będą implementowane w wielu kontekstach ograniczone. Zamiast tego jednostki w każdym ograniczonym kontekście ograniczają swoje atrybuty i zachowania do tych wymaganych w domenie tego ograniczonego kontekstu.

Na przykład jednostka kupującego może mieć większość atrybutów osoby, które są zdefiniowane w jednostce użytkownika w mikrousłudze profilu lub tożsamości, w tym tożsamości. Ale jednostka kupującego w mikrousługi zamawiania może mieć mniej atrybutów, ponieważ tylko niektóre dane kupującego jest związany z procesem zamówienia. Kontekst każdej mikrousługi lub ograniczonego kontekstu wpływa na jego model domeny.

*Jednostki domeny muszą implementować zachowanie oprócz implementacji atrybutów danych.*

Jednostka domeny w DDD musi implementować logikę domeny lub zachowanie związane z danymi jednostki (obiekt emitowany w pamięci). Na przykład jako część klasy jednostki zamówienia musi mieć logikę biznesową i operacje zaimplementowane jako metody dla zadań, takich jak dodawanie elementu zamówienia, sprawdzanie poprawności danych i obliczenia sumy. Metody jednostki dbać o invariants i reguły jednostki, a nie o te reguły rozłożone na warstwie aplikacji.

Rysunek 7-8 przedstawia jednostkę domeny, która implementuje nie tylko atrybuty danych, ale operacje lub metody z logiką domeny pokrewnej.

![Diagram przedstawiający wzorzec jednostki domeny.](./media/microservice-domain-model/domain-entity-pattern.png)

**Rysunek 7-8**. Przykład projektu jednostki domeny implementującej dane plus zachowanie

Jednostka modelu domeny implementuje zachowania za pomocą metod, oznacza to, że nie jest to model "anemiczny". Oczywiście czasami można mieć jednostki, które nie implementują żadnej logiki jako część klasy jednostki. Może się to zdarzyć w jednostkach podrzędnych w agregacji, jeśli jednostka podrzędna nie ma żadnej specjalnej logiki, ponieważ większość logiki jest zdefiniowana w katalogu głównym agregacji. Jeśli masz złożonych mikrousług, który ma wiele logiki zaimplementowane w klasach usług, a nie w jednostkach domeny, może być wchodzących w modelu domeny anemicznej, wyjaśnione w poniższej sekcji.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Model domeny sformatycznej a model domeny anemicznej

W swoim poście [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler opisuje anemiczny model domeny w ten sposób:

Podstawowym objawem anemicznego modelu domeny jest to, że na pierwszy rumieniec wygląda jak prawdziwy. Istnieją obiekty, wiele nazwany chałupnicze w przestrzeni domeny, a te obiekty są połączone z bogatych relacji i struktury, które mają prawdziwe modele domeny. Połów przychodzi, gdy spojrzysz na zachowanie, i zdajesz sobie sprawę, że nie ma prawie żadnego zachowania na tych obiektach, co czyni je niewiele więcej niż torby getters i setters.

Oczywiście w przypadku korzystania z modelu domeny anemicznej te modele danych będą używane z zestawu obiektów usługi (tradycyjnie *nazywanej warstwą biznesową),* które przechwytują całą logikę domeny lub biznesową. Warstwa biznesowa znajduje się na modelu danych i używa modelu danych tak samo jak dane.

Anemiczny model domeny jest tylko proceduralnym stylem. Anemiczne obiekty jednostki nie są rzeczywistymi obiektami, ponieważ brakuje im zachowania (metod). Posiadają one tylko właściwości danych, a tym samym nie jest projektem obiektowym. Umieszczając wszystkie zachowanie w obiektach usługi (warstwie biznesowej), zasadniczo kończy się [kodem spaghetti](https://en.wikipedia.org/wiki/Spaghetti_code) lub [skryptami transakcji,](https://martinfowler.com/eaaCatalog/transactionScript.html)a zatem tracisz zalety, które zapewnia model domeny.

Niezależnie od tego, jeśli mikrousługi lub ograniczony kontekst jest bardzo proste (usługa CRUD), anemiczny model domeny w postaci obiektów jednostki tylko właściwości danych może być wystarczająco dobre i może nie być warte implementacji bardziej złożonych wzorców DDD. W takim przypadku będzie to po prostu model trwałości, ponieważ celowo utworzono jednostkę z tylko danymi do celów CRUD.

Dlatego architektury mikrousług są idealne dla podejścia wieloarchitekturowego w zależności od każdego ograniczonego kontekstu. Na przykład w eShopOnContainers mikrousługi zamawiania implementuje wzorce DDD, ale mikrousługi katalogu, który jest prostą usługą CRUD, nie.

Niektórzy mówią, że anemiczny model domeny jest anty-wzór. To naprawdę zależy od tego, co wdrażasz. Jeśli mikrousługi, które tworzysz jest dość proste (na przykład usługi CRUD), po anemiczny model domeny nie jest anty-wzorca. Jednak jeśli trzeba rozwiązać złożoność domeny mikrousługi, która ma wiele ciągle zmieniających się reguł biznesowych, anemiczny model domeny może być anty-wzorca dla tej mikrousługi lub ograniczony kontekst. W takim przypadku projektowanie go jako model rozbudowany z jednostkami zawierającymi zachowanie danych plus, a także implementowanie dodatkowych wzorców DDD (agregaty, obiekty wartości itp.) może mieć ogromne korzyści dla długoterminowego sukcesu takiej mikrousługi.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **DevIQ. Encja domeny** \
  <https://deviq.com/entity/>

- **Martin Fowler. Model domeny** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowler. Anemiczny model domeny** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Wzorzec obiektu wartości

Jak zauważył Eric Evans: "Wiele obiektów nie ma tożsamości koncepcyjnej. Obiekty te opisują pewne cechy rzeczy."

Jednostka wymaga tożsamości, ale istnieje wiele obiektów w systemie, które nie, jak wzorzec value object. Obiekt wartości jest obiektem bez tożsamości koncepcyjnej, który opisuje aspekt domeny. Są to obiekty, które można utworzyć wystąpienia do reprezentowania elementów projektu, które dotyczą tylko tymczasowo. Zależy Ci na *tym, kim* są, a nie *o to, kim* są. Przykłady obejmują liczby i ciągi, ale może być również pojęcia wyższego poziomu, takie jak grupy atrybutów.

Coś, co jest jednostką w mikrousługi nie może być jednostką w innej mikrousługi, ponieważ w drugim przypadku ograniczone kontekstu może mieć inne znaczenie. Na przykład adres w aplikacji e-commerce może w ogóle nie mieć tożsamości, ponieważ może reprezentować tylko grupę atrybutów profilu klienta dla osoby lub firmy. W takim przypadku adres powinien być sklasyfikowany jako obiekt wartości. Jednak w aplikacji dla firmy energetycznej, adres klienta może być ważne dla domeny biznesowej. W związku z tym adres musi mieć tożsamość, więc system rozliczeniowy mogą być bezpośrednio połączone z adresem. W takim przypadku adres powinien zostać sklasyfikowany jako jednostka domeny.

Osoba z nazwiskiem i nazwiskiem jest zwykle podmiotem, ponieważ dana osoba ma tożsamość, nawet jeśli imię i nazwisko pokrywają się z innym zestawem wartości, na przykład jeśli imiona te odnoszą się również do innej osoby.

Obiekty wartości są trudne do zarządzania w relacyjnych baz danych i ORM, takich jak Entity Framework (EF), podczas gdy w bazach danych zorientowanych na dokumenty są łatwiejsze do zaimplementowania i użycia.

EF Core 2.0 i [nowsze](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) wersje zawierają owned jednostek funkcji, która ułatwia obsługę obiektów wartości, jak zobaczymy szczegółowo później.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. Wzorzec obiektu wartości** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Obiekt wartości** \
  <https://deviq.com/value-object/>

- **Obiekty wartości w programach programistycznych opartych na testach** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Wzorzec agregacji

Model domeny zawiera klastry różnych jednostek danych i procesów, które mogą kontrolować znaczący obszar funkcji, takich jak realizacja zamówień lub spis. Bardziej drobnoziarnistą jednostką DDD jest agregacja, która opisuje klaster lub grupę jednostek i zachowań, które mogą być traktowane jako jednostka spoista.

Zazwyczaj definiuje się agregację na podstawie potrzebnych transakcji. Klasycznym przykładem jest kolejność, która zawiera również listę elementów zamówienia. Element zamówienia będzie zwykle jednostką. Ale będzie to jednostka podrzędna w agregacji zamówienia, która będzie również zawierać jednostkę zamówienia jako jednostkę główną, zwykle nazywaną agregowanym katalogiem głównym.

Identyfikacja agregatów może być trudna. Agregacja jest grupą obiektów, które muszą być spójne ze sobą, ale nie można po prostu wybrać grupę obiektów i oznaczyć je agregacji. Należy rozpocząć od koncepcji domeny i myśleć o jednostkach, które są używane w najbardziej typowych transakcji związanych z tą koncepcją. Te jednostki, które muszą być transakcyjnie spójne są tym, co stanowi agregat. Myślenie o operacjach transakcji jest prawdopodobnie najlepszym sposobem identyfikowania agregatów.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Wzorzec jednostki głównej lub głównej agregacji

Agregat składa się z co najmniej jednej jednostki: agregacji głównej, nazywanej również jednostką główną lub jednostką podstawową. Ponadto może mieć wiele jednostek podrzędnych i obiektów wartości, ze wszystkimi jednostkami i obiektami współpracującymi ze sobą w celu zaimplementowania wymaganego zachowania i transakcji.

Celem zagregowanego katalogu głównego jest zapewnienie spójności agregatu; powinien być jedynym punktem wejścia dla aktualizacji agregacji za pomocą metod lub operacji w klasie głównej agregacji. Należy wprowadzić zmiany do jednostek w agregacji tylko za pośrednictwem katalogu głównego agregacji. Jest to opiekun spójności agregacji, biorąc pod uwagę wszystkie niezmienne i reguły spójności, które mogą być konieczne do przestrzegania w agregacji. Jeśli zmienisz jednostkę podrzędną lub obiekt wartości niezależnie, zagregowany katalog główny nie może zapewnić, że agregacja jest w prawidłowym stanie. To byłoby jak stół z luźną nogą. Zachowanie spójności jest głównym celem agregacji katalogu głównego.

Na rysunku 7-9 możesz zobaczyć przykładowe agregaty, takie jak agregacja kupującego, która zawiera pojedynczą jednostkę (zbiorczy główny nabywca). Agregacja zamówienia zawiera wiele jednostek i obiekt wartości.

![Diagram porównujący agregat nabywcy i agregat zamówień.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Rysunek 7-9**. Przykład agregatów z wieloma lub pojedynczymi jednostkami

Model domeny DDD składa się z agregacji, agregacji może mieć tylko jedną jednostkę lub więcej i może zawierać obiekty wartości, jak również. Należy zauważyć, że agregacja kupujący może mieć dodatkowe jednostki podrzędne, w zależności od domeny, jak to ma w mikrousługi zamawiania w aplikacji referencyjnej eShopOnContainers. Rysunek 7-9 tylko ilustruje przypadek, w którym kupujący ma jedną jednostkę, jako przykład agregacji, która zawiera tylko zagregowany katalog główny.

W celu utrzymania separacji agregatów i zachować wyraźne granice między nimi, jest dobrą praktyką w modelu domeny DDD, aby nie zezwalać na bezpośrednią nawigację między agregatami i tylko o klucz obcy (FK) pole, jak zaimplementowano w [modelu domeny mikrousługi zamawiania](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) w eShopOnContainers. Jednostka Order ma tylko pole FK dla kupującego, ale nie właściwość nawigacji EF Core, jak pokazano w następującym kodzie:

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

Identyfikacja i praca z agregatami wymaga badań i doświadczenia. Aby uzyskać więcej informacji, zobacz następującą listę dodatkowe zasoby.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Vaughn Vernon. Efektywny projekt agregacji - część I: Modelowanie pojedynczego agregatu** (od) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Efektywny projekt agregacji - część II: Tworzenie agregatów współpracujących** (od) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Skuteczny projekt agregacji - część III: Zdobywanie wglądu poprzez odnajdywanie** (od) <http://dddcommunity.org/>\
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Siergiej Grybniak. Wzorce projektowania taktycznego DDD** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregacji** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. Wzorzec agregacji** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Poprzedni](ddd-oriented-microservice.md)
>[następny](net-core-microservice-domain-model.md)
