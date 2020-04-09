---
title: Projektowanie modelu domeny mikrousługi
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Poznaj kluczowe pojęcia podczas projektowania modelu domeny zorientowanego na DDD.
ms.date: 01/30/2020
ms.openlocfilehash: 64860d75dca645904e973a4b8927a716a1603394
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988417"
---
# <a name="design-a-microservice-domain-model"></a>Projektowanie modelu domeny mikrousług

*Zdefiniuj jeden model domeny rozszerzonej dla każdej mikrousługi biznesowej lub ograniczonego kontekstu.*

Twoim celem jest utworzenie jednego spójnego modelu domeny dla każdej mikrousługi biznesowej lub ograniczonego kontekstu (BC). Należy jednak pamiętać, że mikrousługa BC lub biznesowa może czasami składać się z kilku usług fizycznych, które współużytkuje jeden model domeny. Model domeny musi przechwytywać reguły, zachowanie, język biznesowy i ograniczenia pojedynczego ograniczonego kontekstu lub mikrousług biznesowych, które reprezentuje.

## <a name="the-domain-entity-pattern"></a>Wzorzec jednostki domeny

Jednostki reprezentują obiekty domeny i są definiowane przede wszystkim przez ich tożsamości, ciągłości i trwałości w czasie, a nie tylko przez atrybuty, które je tworzą. Jak mówi Eric Evans, "obiekt zdefiniowany przede wszystkim przez jego tożsamość jest nazywany jednostką". Jednostki są bardzo ważne w modelu domeny, ponieważ są one podstawą dla modelu. Dlatego należy je dokładnie zidentyfikować i zaprojektować.

*Tożsamość jednostki może przejść przez wiele mikrousług lub ograniczonych kontekstów.*

Ta sama tożsamość (czyli `Id` ta sama wartość, chociaż być może nie ta sama jednostka domeny) może być modelowana w wielu kontekstach ograniczonych lub mikrousługach. Jednak to nie oznacza, że ta sama jednostka, z tych samych atrybutów i logiki zostaną zaimplementowane w wielu kontekstach ograniczonych. Zamiast tego jednostki w każdym kontekście ograniczonym ograniczają swoje atrybuty i zachowania do tych wymaganych w domenie ograniczonego kontekstu.

Na przykład jednostka kupującego może mieć większość atrybutów osoby, które są zdefiniowane w jednostce użytkownika w profilu lub mikrousługi tożsamości, w tym tożsamości. Ale jednostka kupującego w mikrousługi zamawiania może mieć mniej atrybutów, ponieważ tylko niektóre dane kupującego jest związane z procesem zamówienia. Kontekst każdej mikrousługi lub ograniczonego kontekstu wpływa na jego model domeny.

*Jednostki domeny należy zaimplementować zachowanie oprócz implementowania atrybutów danych.*

Jednostka domeny w DDD musi implementować logikę domeny lub zachowanie związane z danymi jednostki (obiektem dostępnym w pamięci). Na przykład jako część klasy jednostki zamówienia musi mieć logikę biznesową i operacje zaimplementowane jako metody dla zadań, takich jak dodawanie elementu zamówienia, sprawdzanie poprawności danych i obliczania sumy. Metody jednostki dbają o niezmienne i reguły jednostki zamiast tych reguł rozłożonych w warstwie aplikacji.

Rysunek 7-8 przedstawia jednostkę domeny, która implementuje nie tylko atrybuty danych, ale operacje lub metody z logiką domeny pokrewnych.

![Diagram przedstawiający wzorzec jednostki domeny.](./media/microservice-domain-model/domain-entity-pattern.png)

**Rysunek 7-8**. Przykład projektu jednostki domeny implementującej dane plus zachowanie

Jednostka modelu domeny implementuje zachowania za pomocą metod, czyli nie jest modelem "anemicznym". Oczywiście czasami można mieć jednostki, które nie implementują żadnej logiki jako część klasy jednostki. Może się to zdarzyć w jednostkach podrzędnych w ramach agregacji, jeśli jednostka podrzędna nie ma żadnej specjalnej logiki, ponieważ większość logiki jest zdefiniowana w katalogu głównym agregacji. Jeśli masz złożonych mikrousługi, która ma wiele logiki zaimplementowane w klasach usług, a nie w jednostkach domeny, może być wpadnięcie do modelu domeny anemicznej, wyjaśnione w poniższej sekcji.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Model domeny rozszerzonej a anemiczny model domeny

W swoim poście [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler opisuje anemiczny model domeny w ten sposób:

Podstawowym objawem Anemic Domain Model jest to, że na początku rumieniec wygląda jak prawdziwe. Istnieją obiekty, wiele nazwanych po rzeczownikach w przestrzeni domeny, a te obiekty są połączone z bogatymi relacjami i strukturą, które mają prawdziwe modele domen. Haczyk przychodzi, gdy patrzysz na zachowanie, i zdajesz sobie sprawę, że nie ma prawie żadnego zachowania na tych obiektach, co czyni je niewiele więcej niż torby getters i setters.

Oczywiście, gdy używasz anemicznego modelu domeny, te modele danych będą używane z zestawu obiektów usługi (tradycyjnie *nazwanych warstwą biznesową),* które przechwytują całą logikę domeny lub biznesowej. Warstwa biznesowa znajduje się na modelu danych i używa modelu danych tak samo jak danych.

Anemiczny model domeny jest tylko projektem stylu proceduralnego. Obiekty encji anemicznej nie są rzeczywistymi obiektami, ponieważ nie mają zachowania (metod). Przechowują tylko właściwości danych, a zatem nie jest to projekt obiektowy. Umieszczając wszystkie zachowanie do obiektów usługi (warstwy biznesowej) zasadniczo kończy się [z kodu spaghetti](https://en.wikipedia.org/wiki/Spaghetti_code) lub [skryptów transakcji,](https://martinfowler.com/eaaCatalog/transactionScript.html)a zatem tracisz zalety, które zapewnia model domeny.

Niezależnie od tego, czy mikrousługi lub ograniczonego kontekstu jest bardzo prosta (usługa CRUD), anemiczny model domeny w postaci obiektów jednostki z właściwości tylko danych może być wystarczająco dobre i może nie warto implementować bardziej złożonych wzorców DDD. W takim przypadku będzie to po prostu model trwałości, ponieważ celowo utworzono jednostkę z tylko danymi do celów CRUD.

Dlatego architektury mikrousług są idealne dla podejścia wielotereologicznego w zależności od każdego ograniczonego kontekstu. Na przykład w eShopOnContainers zamawiania mikrousług implementuje wzorce DDD, ale mikrousługi katalogu, który jest prostą usługą CRUD, nie.

Niektórzy mówią, że anemiczny model domeny jest anty-wzór. To naprawdę zależy od tego, co wdrażasz. Jeśli mikrousługa, którą tworzysz jest dość proste (na przykład usługi CRUD), po anemiczny model domeny nie jest wzorzec anty-wzorzec. Jeśli jednak trzeba rozwiązać złożoność domeny mikrousług, która ma wiele stale zmieniających się reguł biznesowych, anemiczny model domeny może być wzorzec anty-wzorzec dla tej mikrousługi lub ograniczonego kontekstu. W takim przypadku projektowanie go jako modelu zaawansowanego z jednostek zawierających dane plus zachowanie, a także implementowanie dodatkowych wzorców DDD (agregacje, obiekty wartości, itp.) może mieć ogromne korzyści dla długoterminowego sukcesu takich mikrousług.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **deviq. Jednostka domeny** \
  <https://deviq.com/entity/>

- **Martin Fowler. Model domeny** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowler. Anemiczny model domeny** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Wzorzec obiektu wartości

Jak zauważył Eric Evans: "Wiele obiektów nie ma tożsamości koncepcyjnej. Obiekty te opisują pewne cechy rzeczy."

Jednostka wymaga tożsamości, ale istnieje wiele obiektów w systemie, które nie, jak wzorzec obiektu wartości. Obiekt value jest obiektem bez tożsamości koncepcyjnej, który opisuje aspekt domeny. Są to obiekty, które występują w celu przedstawienia elementów projektu, które dotyczą tylko tymczasowo. Dbasz o *to, kim* są, a nie *o to, kim* są. Przykłady obejmują liczby i ciągi, ale mogą być również pojęcia wyższego poziomu, takie jak grupy atrybutów.

Coś, co jest jednostką w mikrousługi może nie być jednostką w innej mikrousługi, ponieważ w drugim przypadku ograniczone kontekstu może mieć inne znaczenie. Na przykład adres w aplikacji e-commerce może nie mieć tożsamości w ogóle, ponieważ może reprezentować tylko grupę atrybutów profilu klienta dla osoby lub firmy. W takim przypadku adres powinien być sklasyfikowany jako obiekt wartości. Jednak we wniosku o przedsiębiorstwo energetyczne adres klienta może być ważny dla domeny biznesowej. W związku z tym adres musi mieć tożsamość, więc system rozliczeniowy może być bezpośrednio połączony z adresem. W takim przypadku adres powinien być sklasyfikowany jako jednostka domeny.

Osoba z imieniem i nazwiskiem jest zwykle podmiotem, ponieważ dana osoba ma tożsamość, nawet jeśli imię i nazwisko pokrywają się z innym zestawem wartości, na przykład jeśli te imiona odnoszą się również do innej osoby.

Obiekty wartości są trudne do zarządzania w relacyjnych baz danych i ORMs jak Entity Framework (EF), podczas gdy w bazach danych zorientowanych na dokumenty są łatwiejsze do zaimplementowania i użycia.

EF Core 2.0 i nowsze wersje zawierają [owned entities](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) funkcji, która ułatwia obsługę obiektów wartości, jak zobaczymy szczegółowo później.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. Wzorzec obiektu wartości** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Obiekt wartości** \
  <https://deviq.com/value-object/>

- **Obiekty wartości w rozwoju opartym na testach** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Wzorzec agregacji

Model domeny zawiera klastry różnych jednostek danych i procesów, które mogą kontrolować znaczący obszar funkcjonalności, takich jak realizacja zamówień lub zapasów. Bardziej szczegółową jednostką DDD jest agregacja, która opisuje klaster lub grupę jednostek i zachowań, które mogą być traktowane jako spójna jednostka.

Zwykle definiujesz agregację na podstawie potrzebnych transakcji. Klasycznym przykładem jest zamówienie, które zawiera również listę elementów zamówienia. Element zamówienia zazwyczaj będzie encją. Ale będzie to jednostka podrzędna w ramach agregacji zamówień, która będzie również zawierać jednostkę zamówienia jako jej jednostkę główną, zwykle nazywaną zagregowanym katalogiem głównym.

Identyfikowanie agregatów może być trudne. Agregacja to grupa obiektów, które muszą być spójne razem, ale nie można po prostu wybrać grupę obiektów i oznaczyć je agregacji. Należy rozpocząć od koncepcji domeny i myśleć o jednostkach, które są używane w najbardziej typowych transakcji związanych z tym pojęciem. Te jednostki, które muszą być spójne transakcyjnie są co tworzy agregacji. Myślenie o operacjach transakcyjnych jest prawdopodobnie najlepszym sposobem identyfikacji agregatów.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Wzorzec agregacji głównej lub jednostki głównej

Agregacja składa się z co najmniej jednej jednostki: agregacji głównej, zwanej również jednostką główną lub jednostką podstawową. Ponadto może mieć wiele jednostek podrzędnych i obiektów wartości, ze wszystkimi jednostkami i obiektami współpracującymi ze sobą w celu zaimplementowania wymaganego zachowania i transakcji.

Celem zagregowanego korzenia jest zapewnienie spójności agregacji; powinien być jedynym punktem wejścia dla aktualizacji agregacji za pomocą metod lub operacji w klasie głównej agregacji. Należy wprowadzić zmiany do jednostek w ramach agregacji tylko za pośrednictwem katalogu głównego agregacji. Jest to strażnik spójności agregacji, biorąc pod uwagę wszystkie invariants i reguły spójności, które mogą być konieczne do wykonania w agregacji. Jeśli zmienisz jednostkę podrzędną lub obiekt wartości niezależnie, katalog główny agregacji nie może zapewnić, że agregacja jest w prawidłowym stanie. Byłoby jak stół z luźną nogą. Zachowanie spójności jest głównym celem głównego agregacji.

Na rysunku 7-9 można zobaczyć próbki agregacji, takich jak agregacja kupującego, która zawiera jedną jednostkę (główny nabywca zbiorczy). Agregacja zamówienia zawiera wiele jednostek i obiekt wartości.

![Diagram porównujący agregację kupującego i agregację zamówień.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Rysunek 7-9**. Przykład agregacji z wieloma lub pojedynczymi encjami

Model domeny DDD składa się z agregatów, agregacja może mieć tylko jedną jednostkę lub więcej i może zawierać obiekty wartości, jak również. Należy zauważyć, że agregacja kupującego może mieć dodatkowe jednostki podrzędne, w zależności od domeny, tak jak to ma w mikrousługi zamawiania w aplikacji referencyjnej eShopOnContainers. Rysunek 7-9 ilustruje tylko przypadek, w którym nabywca ma jedną jednostkę, jako przykład agregacji, która zawiera tylko zagregowany katalog główny.

Aby zachować separacji agregatów i zachować wyraźne granice między nimi, jest dobrą praktyką w modelu domeny DDD, aby nie zezwalać na bezpośrednią nawigację między agregatami i tylko o klucz obcy (FK) pole, zgodnie z implementacji w [modelu domeny mikrousługi zamawiania](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) w eShopOnContainers. Jednostka Zamówienie ma tylko pole FK dla kupującego, ale nie właściwość nawigacji EF Core, jak pokazano w poniższym kodzie:

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

Identyfikacja i praca z skupiskami wymaga badań i doświadczenia. Aby uzyskać więcej informacji, zobacz następującą listę dodatkowych zasobów.

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Vaughn Vernon. Efektywny projekt agregatu - część I: Modelowanie pojedynczego agregatu** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Efektywny projekt agregatu - część II: Tworzenie współpracy agregatów** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Efektywny projekt agregatu - część III: Uzyskiwanie wglądu poprzez odkrycie** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Siergiej Grybniak. DDD Taktyczne wzory projektowania** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregatów** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **deviq. Wzorzec agregacji** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Poprzedni](ddd-oriented-microservice.md)
>[następny](net-core-microservice-domain-model.md)
