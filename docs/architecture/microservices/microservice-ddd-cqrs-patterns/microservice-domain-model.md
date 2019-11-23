---
title: Projektowanie modelu domeny mikrousługi
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z najważniejszymi pojęciami dotyczącymi projektowania zorientowanej na siebie modelu domeny.
ms.date: 10/08/2018
ms.openlocfilehash: 3a02059064305ca148b7909923e2f51e60ee54d5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737386"
---
# <a name="design-a-microservice-domain-model"></a>Projektowanie modelu domeny mikrousługi

*Zdefiniuj jeden bogaty model domeny dla każdego mikrousługi biznesowej lub ograniczonego kontekstu.*

Celem jest utworzenie jednego spójnego modelu domeny dla każdego mikrousług biznesowej lub ograniczonego kontekstu (BC). Należy jednak pamiętać, że mikrousługa BC lub biznesowa może czasami składać się z kilku usług fizycznych, które współużytkują jeden model domeny. Model domeny musi przechwycić reguły, zachowanie, język biznesowy i ograniczenia dotyczące pojedynczego powiązanego kontekstu lub mikrousługi biznesowej, które reprezentuje.

## <a name="the-domain-entity-pattern"></a>Wzorzec jednostki domeny

Jednostki reprezentują obiekty domeny i są głównie definiowane przez ich tożsamość, ciągłość i trwałość w czasie, a nie tylko te, które zawierają te atrybuty. Jak Eric Evans mówi, "obiekt, głównie zdefiniowany przez jego tożsamość, nosi nazwę jednostki". Jednostki są bardzo ważne w modelu domeny, ponieważ są one podstawą dla modelu. W związku z tym należy uważnie identyfikować i projektować.

*Tożsamość jednostki może przekroczyć wiele mikrousług lub ograniczonych kontekstów.*

Taka sama tożsamość (to samo `Id` wartość, chociaż prawdopodobnie nie jest to taka sama jednostka domeny) można modelować w wielu ograniczonych kontekstach lub mikrousługach. Nie oznacza to jednak, że ta sama jednostka z tymi samymi atrybutami i logiką zostałaby wdrożona w wielu powiązanych kontekstach. Zamiast tego obiekty w każdym ograniczonym kontekście ograniczają ich atrybuty i zachowania do tych, które są wymagane w domenie powiązanego kontekstu.

Na przykład jednostka kupca może mieć większość atrybutów osób, które są zdefiniowane w jednostce użytkownika w ramach profilu lub mikrousługi tożsamości, w tym tożsamość. Jednak jednostka kupca w mikrousłudze porządkowania może mieć mniej atrybutów, ponieważ tylko niektóre dane dotyczące kupujących są powiązane z procesem zamówienia. Kontekst każdego mikrousługi lub ograniczonego kontekstu ma wpływ na model domeny.

*Jednostki domeny muszą implementować zachowanie oprócz implementowania atrybutów danych.*

Jednostka domeny w DDD musi implementować logikę domeny lub zachowanie związane z danymi jednostki (obiektem dostępnym w pamięci). Na przykład w ramach klasy jednostki zamówienia należy mieć logikę biznesową i operacje zaimplementowane jako metody dla zadań, takich jak dodawanie elementu zamówienia, sprawdzanie poprawności danych i obliczanie całkowite. Metody jednostki zapoznają się z niektórymi różnymi i niektórymi regułami jednostki, zamiast korzystać z tych reguł w warstwie aplikacji.

Rysunek 7-8 pokazuje jednostkę domeny, która implementuje nie tylko atrybuty danych, ale operacje lub metody z powiązaną logiką domeny.

![Diagram przedstawiający wzorzec jednostki domeny.](./media/microservice-domain-model/domain-entity-pattern.png)

**Rysunek 7-8**. Przykład projektu jednostki domeny implementującego dane oraz zachowanie

Jednostka modelu domeny implementuje zachowania za pomocą metod, czyli nie jest to model "Anemic". Oczywiście czasami może istnieć jednostka, która nie implementuje żadnej logiki jako części klasy Entity. Może się to zdarzyć w jednostkach podrzędnych w ramach agregacji, jeśli jednostka podrzędna nie ma żadnej specjalnej logiki, ponieważ większość logiki jest zdefiniowana w zagregowanym elemencie głównym. Jeśli istnieje złożona mikrousługa, która ma wiele implementacji logiki w klasach usług, a nie w jednostkach domeny, można uwzględnić model domeny Anemic, wyjaśniony w poniższej sekcji.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Bogaty model domeny a model domeny Anemic

W swoim [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)post Fowlera opisuje model domeny Anemic w ten sposób:

Podstawowym objawem modelu domeny Anemic jest to, że pierwszy rumianolawendowy wygląda jak w rzeczywistości. Istnieją obiekty, wiele nazwanych po rzeczownikach w przestrzeni domeny, a te obiekty są połączone z rozbudowanymi relacjami i strukturą, które mają prawdziwe modele domeny. Catch pojawia się, gdy zobaczysz zachowanie i zobaczysz, że na tych obiektach istnieje trudne jakiekolwiek zachowanie, dzięki czemu są one nieco większe niż zbiory metod pobierających i ustawiających.

Oczywiście w przypadku używania modelu domeny Anemic te modele danych będą używane z zestawu obiektów usługi (tradycyjnie nazywana *warstwą biznesową*), które przechwytują całą domenę lub logikę biznesową. Warstwa biznesowa znajduje się na szczycie modelu danych i używa modelu danych tak samo jak dane.

Model domeny Anemic jest tylko projektem w stylu proceduralnym. Obiekty jednostek Anemic nie są obiektami rzeczywistymi, ponieważ nie są one zachowaniem (Metoda). Przechowują one tylko właściwości danych, dlatego nie jest to projektowanie zorientowane obiektowo. Umieszczenie wszystkich zachowań w obiektach usługi (warstwa biznesowa) zasadniczo kończy się [spaghetti kodu](https://en.wikipedia.org/wiki/Spaghetti_code) lub [skryptów transakcji](https://martinfowler.com/eaaCatalog/transactionScript.html), w związku z czym utracisz korzyści, jakie zapewnia model domeny.

Bez względu na to, że usługa mikrousług lub ograniczone konteksty są bardzo proste (usługi CRUD), model domeny Anemic w formie obiektów Entity ze wszystkimi właściwościami danych może być wystarczająco dobry i nie będzie warto wdrażać bardziej złożonych wzorców DDD. W takim przypadku jest to po prostu model trwałości, ponieważ celowo utworzono jednostkę z tylko danymi do celów CRUD.

Dlatego architektury mikrousług doskonale nadaje się do podejścia wieloarchitekturowego, w zależności od każdego powiązanego kontekstu. Na przykład w eShopOnContainers, porządkowanie mikrousługi implementuje wzorce DDD, ale nie jest to prosta usługa CRUD.

Niektórzy użytkownicy mówią, że model domeny Anemic jest antywzorców. Jest to naprawdę zależne od implementacji. Jeśli mikrousługa, którą tworzysz, jest wystarczająco prosta (na przykład usługa CRUD), zgodnie z modelem domeny Anemic nie jest to Antywzorzec. Jeśli jednak chcesz zaradzić sobie z złożonością domeny mikrousługi, która ma wiele niezmienionych reguł firmy, model domeny Anemic może być Antywzorzec dla tego mikrousługi lub ograniczonego kontekstu. W takim przypadku projektowanie go jako bogaty model z obiektami zawierającymi dane oraz zachowaniem, a także wdrożenie dodatkowych wzorców DDD (agregatów, obiektów wartości itp.) może mieć ogromny zakres korzyści w przypadku długotrwałego sukcesu takich mikrousług.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **DevIQ. \ jednostki domeny**
  <https://deviq.com/entity/>

- **Fowlera Martin. Model domeny** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Fowlera Martin. Model domeny Anemic** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Wzorzec obiektu wartości

Ponieważ zanotowano Eric Evans, "wiele obiektów nie ma tożsamości koncepcyjnej. Te obiekty opisują pewne charakterystyki elementu ".

Jednostka wymaga tożsamości, ale istnieje wiele obiektów w systemie, które nie są takie jak wzorzec obiektu wartości. Obiekt wartości jest obiektem bez tożsamości koncepcyjnej opisującym aspekt domeny. Są to obiekty, które są przeznaczone do reprezentowania elementów projektu, które dotyczą tylko chwilowo. Pamiętaj o tym, *czego* zajmują. Przykłady zawierają liczby i ciągi, ale mogą być również pojęcia wyższego poziomu, takie jak grupy atrybutów.

Coś, co jest jednostką w mikrousłudze, może nie być jednostką w innej mikrousług, ponieważ w drugim przypadku ograniczony kontekst może mieć inne znaczenie. Na przykład adres w aplikacji handlu elektronicznego może nie mieć tożsamości, ponieważ może reprezentować tylko grupę atrybutów profilu klienta dla osoby lub firmy. W takim przypadku adres powinien być sklasyfikowany jako obiekt wartości. Jednak w aplikacji dla elektrycznego narzędzia do zarządzania energię adres klienta może być istotny dla domeny biznesowej. W związku z tym adres musi mieć tożsamość, aby system rozliczeń mógł być bezpośrednio połączony z adresem. W takim przypadku adres powinien być sklasyfikowany jako jednostka domeny.

Osoba o nazwisku i nazwisku jest zazwyczaj jednostką, ponieważ osoba ma tożsamość, nawet jeśli nazwa i nazwisko pokrywają się z innym zestawem wartości, takich jak te nazwy również odnoszą się do innej osoby.

Obiekty wartości są trudne do zarządzania w relacyjnych bazach danych i ORMs takich jak EF, natomiast w przypadku baz danych zorientowanych na dokumenty, które są łatwiejsze do wdrożenia i użycia.

EF Core 2,0 zawiera funkcję [jednostek będących własnością](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) , która ułatwia obsługę obiektów wartości, co opisano w dalszej części artykułu.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Fowlera Martin. \ wzorca obiektu wartości**
  <https://martinfowler.com/bliki/ValueObject.html>

-  \ **obiektu wartości**
  <https://deviq.com/value-object/>

- **Obiekty wartości w programowaniu opartym na testach** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Projektowanie oparte na domenie: zapełnianie złożoności w oprogramowaniu.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Wzorzec agregacji

Model domeny zawiera klastry różnych jednostek danych i procesów, które mogą kontrolować znaczący obszar funkcjonalności, taki jak realizacja lub spis kolejności. Bardziej szczegółowym przydziałem jest agregacja, która opisuje klaster lub grupę jednostek i zachowań, które mogą być traktowane jako spójna jednostka.

Zwykle definiuje się wartość zagregowaną na podstawie wymaganych transakcji. Klasycznym przykładem jest kolejność, która zawiera również listę elementów zamówienia. Element Order zazwyczaj będzie jednostką. Ale będzie ona jednostką podrzędną w ramach agregacji Order, która również będzie zawierać jednostkę Order jako jednostkę główną, zazwyczaj nazywaną zagregowanym elementem głównym.

Identyfikowanie zagregowane może być trudne. Agregacja to grupa obiektów, która musi być spójna ze sobą, ale nie można tylko wybrać grupy obiektów i oznaczyć je agregacją. Należy zacząć od koncepcji domeny i myśleć o jednostkach, które są używane w najpopularniejszych transakcjach związanych z tą koncepcją. Te jednostki, które muszą mieć spójną transakcję, tworzą agregację. Zastanawiamy się, że operacje transakcji są prawdopodobnie najlepszym sposobem na identyfikację agregacji.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Wzorzec zagregowanych lub głównych jednostek głównych

Agregacja składa się z co najmniej jednej jednostki: zagregowanego elementu głównego, nazywanego również jednostką główną lub jednostką podstawową. Ponadto może mieć wiele jednostek podrzędnych i obiektów wartości, ze wszystkimi jednostkami i obiektami, które współpracują w celu zaimplementowania wymaganego zachowania i transakcji.

Celem zagregowanego elementu głównego jest zapewnienie spójności agregacji; powinien być jedynym punktem wejścia dla aktualizacji zagregowanych za pomocą metod lub operacji w klasie głównej agregacji. Zmiany jednostek w ramach agregacji należy wprowadzać tylko za pośrednictwem zagregowanego elementu głównego. Jest to zagregowany opiekun spójności, biorąc pod uwagę wszystkie niewarianty i reguły spójności, które mogą być potrzebne w ramach agregacji. Jeśli zmienisz jednostkę podrzędną lub obiekt wartości niezależnie, zagregowany element główny nie może zagwarantować, że agregacja jest w prawidłowym stanie. Byłoby tak jak tabela z luźną gałęzią. Zachowanie spójności jest głównym celem zagregowanego elementu głównego.

Na rysunku 7-9 można zobaczyć przykładowe zagregowane wartości, takie jak agregacja kupującego, która zawiera pojedynczą jednostkę (zagregowany główny kupujący). Zagregowana kolejność zawiera wiele jednostek i obiekt wartości.

![Diagram porównujący zagregowaną sumę i agregację zamówienia.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Rysunek 7-9**. Przykład zagregowanych elementów z wieloma jednostkami lub pojedynczymi

Model domeny DDD składa się z agregacji, agregacja może mieć tylko jedną jednostkę lub wiele obiektów i może zawierać również obiekty wartości. Należy pamiętać, że agregowanie kupującego może mieć dodatkowe jednostki podrzędne, w zależności od domeny, tak jak w przypadku mikrousługi porządkowania w aplikacji eShopOnContainers Reference. Rysunek 7-9 po prostu ilustruje przypadek, w którym kupujący ma pojedynczą jednostkę, jako przykład agregacji, która zawiera tylko zagregowany element główny.

Aby zachować rozdzielenie agregacji i zachować jasne granice między nimi, dobrym sposobem w modelu domeny DDD jest uniemożliwienie bezpośredniej nawigacji między agregacjami i tylko posiadanie pola klucza obcego (FK), zgodnie z implementacją w [modelu domeny mikrousługi](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) w eShopOnContainers. Jednostka Order ma tylko pole klucza obcego dla kupującego, ale nie EF Core właściwość nawigacji, jak pokazano w poniższym kodzie:

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

Identyfikowanie i praca z agregacjami wymaga badań i środowiska. Aby uzyskać więcej informacji, zobacz poniższą listę zasobów dodatkowych.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Vaughn Vernon. Efektywny model agregacji — część I: Modelowanie pojedynczej agregacji** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Efektywny projekt zagregowany — część II: wykonywanie zagregowanych współdziałań** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Efektywny projekt zagregowany — część III: uzyskiwanie wglądu w dane poprzez odnajdywanie** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergey Grybniak. Wzorce projektowe DDD taktyczne** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Krzysztof Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregacji** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. \ wzorca agregacji**
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Poprzedni](ddd-oriented-microservice.md)
>[Następny](net-core-microservice-domain-model.md)
