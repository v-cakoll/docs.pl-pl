---
title: Zdarzenia domeny. projektowanie i wdrażanie
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Uzyskaj szczegółowy widok zdarzeń domeny, kluczową koncepcję ustanowienia komunikacji między agregatami.
ms.date: 10/08/2018
ms.openlocfilehash: 3bba18d4a77b47abee55c16bae8a64ed27ac9aba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74884231"
---
# <a name="domain-events-design-and-implementation"></a>Zdarzenia w domenie: projektowanie i implementacja

Zdarzenia w domenie można używać do jawnego zaimplementowania skutków ubocznych zmian w domenie. Innymi słowy i przy użyciu terminologii DDD, użyj zdarzenia domeny jawnie implementować skutki uboczne w wielu agregatów. Opcjonalnie dla lepszej skalowalności i mniejszy wpływ na blokady bazy danych, należy użyć spójności ostatecznej między agregacji w tej samej domenie.

## <a name="what-is-a-domain-event"></a>Co to jest zdarzenie domeny?

Zdarzenie to coś, co wydarzyło się w przeszłości. Zdarzenie domeny to coś, co wydarzyło się w domenie, o którym mają wiedzieć inne części tej samej domeny (w trakcie procesu). Zgłoszone części zwykle reagują jakoś na wydarzenia.

Ważną zaletą zdarzeń domeny jest to, że skutki uboczne mogą być jawnie wyrażone.

Na przykład jeśli używasz tylko entity framework i nie musi być reakcja na niektóre zdarzenia, prawdopodobnie kod, co trzeba w pobliżu, co wyzwala zdarzenie. Tak więc reguła jest sprzężona, niejawnie, z kodem i musisz zajrzeć do kodu, aby, miejmy nadzieję, uświadomić sobie, że reguła jest tam zaimplementowana.

Z drugiej strony przy użyciu zdarzenia domeny sprawia, `DomainEvent` że pojęcie `DomainEventHandler` jawne, ponieważ istnieje i co najmniej jeden zaangażowanych.

Na przykład w aplikacji eShopOnContainers, gdy zamówienie jest tworzony, użytkownik staje `OrderStartedDomainEvent` się nabywcą, więc `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`jest wywoływane i obsługiwane w , więc podstawowa koncepcja jest oczywiste.

Krótko mówiąc, zdarzenia domeny pomagają wyraźnie wyrazić reguły domeny oparte na wszechobecnym języku dostarczonym przez ekspertów domeny. Zdarzenia domeny umożliwiają również lepsze rozdzielenie problemów między klasami w tej samej domenie.

Ważne jest, aby upewnić się, że podobnie jak transakcja bazy danych, wszystkie operacje związane ze zdarzeniem domeny zakończyć pomyślnie lub żaden z nich nie.

Zdarzenia w domenie są podobne do zdarzeń w stylu wiadomości, z jedną ważną różnicą. W przypadku rzeczywistych wiadomości, kolejkowania wiadomości, brokerów komunikatów lub magistrali usług korzystających z usługi AMQP wiadomość jest zawsze wysyłana asynchronicznie i przekazywana między procesami i komputerami. Jest to przydatne do integracji wielu ograniczonych kontekstów, mikrousług lub nawet różnych aplikacji. Jednak w przypadku zdarzeń domeny chcesz wywołać zdarzenie z operacji domeny, która jest aktualnie uruchomiona, ale chcesz, aby wszelkie skutki uboczne wystąpiły w tej samej domenie.

Zdarzenia domeny i ich skutki uboczne (akcje wyzwalane później, które są zarządzane przez programy obsługi zdarzeń) powinny wystąpić niemal natychmiast, zwykle w procesie i w tej samej domenie. W związku z tym zdarzenia domeny mogą być synchroniczne lub asynchroniczne. Zdarzenia integracji, jednak zawsze powinny być asynchroniczne.

## <a name="domain-events-versus-integration-events"></a>Zdarzenia domeny a zdarzenia integracji

Semantycznie, domeny i integracji wydarzenia są to samo: powiadomienia o czymś, co właśnie się stało. Ich wdrożenie musi być jednak inne. Zdarzenia domeny są tylko komunikaty wypchnięte do dyspozytora zdarzeń domeny, które mogą być implementowane jako mediator w pamięci na podstawie kontenera IoC lub jakiejkolwiek innej metody.

Z drugiej strony celem zdarzeń integracji jest propagowanie zatwierdzonych transakcji i aktualizacji do dodatkowych podsystemów, niezależnie od tego, czy są to inne mikrousługi, ograniczone konteksty, czy nawet aplikacje zewnętrzne. W związku z tym powinny wystąpić tylko wtedy, gdy jednostka jest pomyślnie utrwalił, w przeciwnym razie jest tak, jakby cała operacja nigdy nie zdarzyło.

Jak wspomniano wcześniej, zdarzenia integracji muszą być oparte na komunikacji asynchronicznej między wieloma mikrousługami (inne ograniczone konteksty) lub nawet systemów zewnętrznych/aplikacji.

W związku z tym interfejs magistrali zdarzeń wymaga pewnej infrastruktury, która umożliwia komunikację między procesami i rozproszoną komunikacją między potencjalnie zdalnymi usługami. Może być oparty na komercyjnej magistrali usług, kolejkach, udostępnionej bazie danych używanej jako skrzynka pocztowa lub innym rozproszonym i najlepiej wypychanym systemie obsługi wiadomości.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Zdarzenia domeny jako preferowany sposób wywoływania skutków ubocznych w wielu agregatach w tej samej domenie

Jeśli wykonywanie polecenia związanego z jednym wystąpieniem agregacji wymaga dodatkowych reguł domeny do uruchomienia na co najmniej jeden dodatkowych agregatów, należy zaprojektować i zaimplementować te skutki uboczne, które mają być wyzwalane przez zdarzenia domeny. Jak pokazano na rysunku 7-14 i jako jeden z najważniejszych przypadków użycia, zdarzenie domeny powinny być używane do propagowania zmian stanu w wielu agregatach w ramach tego samego modelu domeny.

![Diagram przedstawiający zdarzenie domeny kontrolujące dane do agregacji kupującego.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Rysunek 7-14**. Zdarzenia domeny w celu wymuszenia spójności między wieloma agregatami w tej samej domenie

Rysunek 7–14 pokazuje, jak spójność między agregacjami jest osiągana przez zdarzenia domeny. Gdy użytkownik inicjuje zamówienie, zagregowanie zamówień wysyła zdarzenie `OrderStarted` domeny. OrderStarted domain zdarzenie jest obsługiwane przez kupującego agregacji, aby utworzyć obiekt Kupującego w mikrousługi zamawiania, na podstawie oryginalnych informacji o użytkowniku z mikrousługi tożsamości (z informacjami podanymi w CreateOrder polecenia).

Alternatywnie można zagregować zagregowany katalog główny subskrybowany dla zdarzeń wywoływanych przez członków jego agregacji (jednostki podrzędne). Na przykład każda jednostka podrzędna OrderItem może podnieść zdarzenie, gdy cena towaru jest wyższa niż określona kwota lub gdy kwota towaru jest zbyt wysoka. Zagregowany katalog główny może następnie odbierać te zdarzenia i wykonywać globalne obliczenia lub agregację.

Ważne jest, aby zrozumieć, że ta komunikacja oparta na zdarzeniach nie jest implementowana bezpośrednio w agregatach; należy zaimplementować programy obsługi zdarzeń domeny.

Obsługa zdarzeń domeny jest problemem aplikacji. Warstwa modelu domeny powinna koncentrować się tylko na logice domeny — rzeczy, które ekspert domeny zrozumie, a nie infrastruktury aplikacji, takich jak programy obsługi i akcje trwałości efektuboczowy przy użyciu repozytoriów. W związku z tym poziom warstwy aplikacji jest, gdzie powinny mieć programy obsługi zdarzeń domeny wyzwalania akcji po wywołaniu zdarzenia domeny.

Zdarzenia domeny mogą być również używane do wyzwalania dowolnej liczby akcji aplikacji, a co ważniejsze, muszą być otwarte, aby zwiększyć tę liczbę w przyszłości w sposób niesparzony. Na przykład po uruchomieniu zamówienia można opublikować zdarzenie domeny, aby propagować te informacje do innych agregatów, a nawet podnieść akcje aplikacji, takie jak powiadomienia.

Kluczowym punktem jest otwarta liczba akcji do wykonania w przypadku wystąpienia zdarzenia domeny. Po pewnym czasie akcje i reguły w domenie i aplikacji będą się zwiększać. Złożoność lub liczba akcji efekt uboczny, gdy coś się dzieje wzrośnie, ale jeśli kod zostały połączone z `new`"klej" (czyli tworzenie określonych obiektów z ), to za każdym razem, gdy trzeba dodać nową akcję trzeba również zmienić pracy i przetestowany kod.

Ta zmiana może spowodować nowe błędy i takie podejście jest również sprzeczne z [zasadą Open / Closed](https://en.wikipedia.org/wiki/Open/closed_principle) z [SOLID](https://en.wikipedia.org/wiki/SOLID). Nie tylko, że oryginalna klasa, która była organizowanie operacji będzie rosnąć i rosnąć, co jest sprzeczne z [zasadą jednolitej odpowiedzialności (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Z drugiej strony, jeśli używasz zdarzeń domeny, można utworzyć implementacji szczegółowe i oddzielone od powiązanych przez segregacji obowiązków przy użyciu tego podejścia:

1. Wyślij polecenie (na przykład CreateOrder).
2. Odbierz polecenie w programie obsługi poleceń.
   - Wykonaj transakcję pojedynczego agregatu.
   - (Opcjonalnie) Wywołanie zdarzeń domeny dla skutków ubocznych (na przykład OrderStartedDomainEvent).
3. Obsługa zdarzeń domeny (w ramach bieżącego procesu), który wykona otwartą liczbę skutków ubocznych w wielu agregacji lub akcji aplikacji. Przykład:
   - Sprawdź lub utwórz kupującego i metodę płatności.
   - Tworzenie i wysyłanie powiązanych zdarzenie integracji do magistrali zdarzeń do propagowania stanów w mikrousługach lub wyzwalania działań zewnętrznych, takich jak wysyłanie wiadomości e-mail do kupującego.
   - Obsłużyć inne skutki uboczne.

Jak pokazano na rysunku 7-15, począwszy od tego samego zdarzenia domeny, można obsługiwać wiele akcji związanych z innymi agregatami w domenie lub dodatkowe akcje aplikacji, które należy wykonać w mikrousługach łączących się ze zdarzeniami integracji i magistrali zdarzeń.

![Diagram przedstawiający zdarzenie domeny przekazywania danych do kilku programów obsługi zdarzeń.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Rysunek 7-15**. Obsługa wielu akcji na domenę

Może istnieć kilka programów obsługi dla tego samego zdarzenia domeny w warstwie aplikacji, jeden program obsługi można rozwiązać spójność między agregacji i innego programu obsługi można opublikować zdarzenie integracji, więc inne mikrousługi można zrobić coś z nim. Programy obsługi zdarzeń są zazwyczaj w warstwie aplikacji, ponieważ będzie używać obiektów infrastruktury, takich jak repozytoria lub interfejsu API aplikacji dla zachowania mikrousługi. W tym sensie programy obsługi zdarzeń są podobne do programów obsługi poleceń, więc oba są częścią warstwy aplikacji. Ważną różnicą jest to, że polecenie powinno być przetwarzane tylko raz. Zdarzenie domeny może być przetwarzane zero lub *n* razy, ponieważ mogą być odbierane przez wielu odbiorców lub programy obsługi zdarzeń w innym celu dla każdego programu obsługi.

Posiadanie otwartej liczby programów obsługi na zdarzenie domeny umożliwia dodanie dowolną liczbę reguł domeny, zgodnie z potrzebami, bez wpływu na bieżący kod. Na przykład implementowanie następującej reguły biznesowej może być tak proste, jak dodanie kilku programów obsługi zdarzeń (lub nawet jednego):

> Gdy całkowita kwota zakupiona przez klienta w sklepie, w dowolnej liczbie zamówień, przekracza 6000 USD, zastosuj rabat 10% rabatu na każde nowe zamówienie i powiadom odbiorcę e-mailem o tym zniżce dla przyszłych zamówień.

## <a name="implement-domain-events"></a>Implementowanie zdarzeń domeny

W języku C#zdarzenie domeny jest po prostu struktury przechowywania danych lub klasy, jak DTO, ze wszystkimi informacjami związanymi z tym, co właśnie się stało w domenie, jak pokazano w poniższym przykładzie:

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

    public OrderStartedDomainEvent(Order order,
                                   int cardTypeId, string cardNumber,
                                   string cardSecurityNumber, string cardHolderName,
                                   DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

Jest to zasadniczo klasa, która przechowuje wszystkie dane związane z OrderStarted zdarzenia.

Jeśli chodzi o wszechobecny język domeny, ponieważ zdarzenie jest coś, co wydarzyło się w przeszłości, nazwa klasy zdarzenia powinny być reprezentowane jako czasownik w czasie przeszłego, jak OrderStartedDomainEvent lub OrderShippedDomainEvent. W ten sposób zdarzenie domeny jest implementowane w mikrousługi zamawiania w eShopOnContainers.

Jak wspomniano wcześniej, ważną cechą wydarzeń jest to, że ponieważ zdarzenie jest czymś, co wydarzyło się w przeszłości, nie powinno się zmieniać. W związku z tym musi być niezmienne klasy. W poprzednim kodzie można zobaczyć, że właściwości są tylko do odczytu. Nie ma możliwości zaktualizowania obiektu, można ustawić wartości tylko podczas jego tworzenia.

W tym miejscu należy podkreślić, że jeśli zdarzenia domeny miałybyć obsługiwane asynchronicznie, przy użyciu kolejki, która wymagała serializacji i deserializacji obiektów zdarzeń, właściwości musiałyby być "zestaw prywatny" zamiast tylko do odczytu, więc deserializator będzie można przypisać wartości po dequeuing. Nie jest to problem w mikrousługi zamawiania, jak pub/sub zdarzenia domeny jest implementowana synchronicznie przy użyciu MediatR.

### <a name="raise-domain-events"></a>Podnoszenie zdarzeń domeny

Następne pytanie brzmi, jak podnieść zdarzenie domeny, dzięki czemu dociera do jego programów obsługi zdarzeń pokrewnych. Można użyć wielu metod.

Udi Dahan pierwotnie proponowane (na przykład w kilku powiązanych wpisów, takich jak [zdarzenia domeny - Take 2)](http://udidahan.com/2008/08/25/domain-events-take-2/)przy użyciu klasy statycznej do zarządzania i podnoszenia zdarzeń. Może to obejmować klasę statyczną o nazwie DomainEvents, która natychmiast `DomainEvents.Raise(Event myEvent)`wywoływałaby zdarzenia domeny przy użyciu składni, takiej jak . Jimmy Bogard napisał wpis na blogu ([Wzmocnienie domeny: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)), który zaleca podobne podejście.

Jednak gdy klasa zdarzenia domeny jest statyczny, również natychmiast wysyła do obsługi. Utrudnia to testowanie i debugowanie, ponieważ programy obsługi zdarzeń z logiką efektów ubocznych są wykonywane natychmiast po wyniesionym zdarzeniu. Podczas testowania i debugowania, chcesz skupić się na i tylko to, co dzieje się w bieżących klas agregacji; nie chcesz nagle zostać przekierowany do innych programów obsługi zdarzeń dla skutków ubocznych związanych z innymi agregatami lub logiki aplikacji. Dlatego inne podejścia ewoluowały, jak wyjaśniono w następnej sekcji.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odroczone podejście do podnoszenia i wysyłania zdarzeń

Zamiast natychmiast wysyłać do programu obsługi zdarzeń domeny, lepszym rozwiązaniem jest dodanie zdarzeń domeny do kolekcji, a następnie wywołanie tych zdarzeń domeny *tuż przed* lub *tuż* *po* zazięciu transakcji (jak w przypadku SaveChanges w EF). (Takie podejście zostało opisane przez Jimmy Bogard w tym poście [lepszy wzór zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Podjęcie decyzji, czy wysłać zdarzenia domeny tuż przed lub tuż po zazięciu transakcji jest ważne, ponieważ określa, czy będą uwzględniane skutki uboczne w ramach tej samej transakcji lub w różnych transakcjach. W tym ostatnim przypadku należy radzić sobie z spójności ą ostateczną w wielu agregatach. Ten temat został omówiony w następnej sekcji.

Odroczone podejście jest to, co eShopOnContainers używa. Najpierw należy dodać zdarzenia dzieje się w jednostkach do kolekcji lub listy zdarzeń na jednostkę. Ta lista powinna być częścią obiektu jednostki, a nawet lepiej, część klasy jednostki podstawowej, jak pokazano w poniższym przykładzie klasy podstawowej jednostki:

```csharp
public abstract class Entity
{
     //...
     private List<INotification> _domainEvents;
     public List<INotification> DomainEvents => _domainEvents;

     public void AddDomainEvent(INotification eventItem)
     {
         _domainEvents = _domainEvents ?? new List<INotification>();
         _domainEvents.Add(eventItem);
     }

     public void RemoveDomainEvent(INotification eventItem)
     {
         _domainEvents?.Remove(eventItem);
     }
     //... Additional code
}
```

Jeśli chcesz podnieść zdarzenie, wystarczy dodać go do kolekcji zdarzeń z kodu w dowolnej metodzie jednostki agregacji-root.

Poniższy kod, część [zagregowanego katalogu głównego zamówienia w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), pokazuje przykład:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Należy zauważyć, że jedyną rzeczą, którą wykonuje AddDomainEvent metoda jest dodanie zdarzenia do listy. Żadne zdarzenie nie jest jeszcze wywoływane i nie wywoływano jeszcze żadnego programu obsługi zdarzeń.

Faktycznie chcesz wywołać zdarzenia później, po zatwierdzeniu transakcji do bazy danych. Jeśli używasz entity framework core, oznacza to, że w SaveChanges metody EF DbContext, jak w następującym kodzie:

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);

        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be committed
        var result = await base.SaveChangesAsync();
    }
}
```

Za pomocą tego kodu można wywołać zdarzenia jednostki do odpowiednich programów obsługi zdarzeń.

Ogólny wynik jest, że zostały oddzielone podnoszenie zdarzenia domeny (proste dodanie do listy w pamięci) z wysyłania go do programu obsługi zdarzeń. Ponadto, w zależności od rodzaju dyspozytora, którego używasz, można wywołać zdarzenia synchronicznie lub asynchronicznie.

Należy pamiętać, że granice transakcyjne wchodzą w znaczącą grę tutaj. Jeśli jednostka pracy i transakcji może zakres więcej niż jeden agregacji (jak w przypadku korzystania z EF Core i relacyjnej bazy danych), to może działać dobrze. Ale jeśli transakcja nie może obejmuje agregacji, takich jak podczas korzystania z bazy danych NoSQL, takich jak Usługa Azure CosmosDB, należy zaimplementować dodatkowe kroki w celu osiągnięcia spójności. Jest to kolejny powód, dla którego niewiedza o trwałości nie jest uniwersalna; zależy to od używanego systemu pamięci masowej.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Pojedyncza transakcja w agregatach a spójność ostateczna w agregatach

Pytanie, czy wykonać jedną transakcję między agregacjami w porównaniu z poleganiem na spójności ostatecznej w tych agregatach jest kontrowersyjne. Wielu autorów DDD, takich jak Eric Evans i Vaughn Vernon, opowiada się za zasadą, że jedna transakcja = jedna agregacja i dlatego opowiada się za ostateczną spójnością w agregatach. Na przykład, w swojej książce *Domain-Driven Design,* Eric Evans mówi tak:

> Wszelkie reguły, które obejmuje agregaty nie będą oczekiwane być aktualne przez cały czas. Poprzez przetwarzanie zdarzeń, przetwarzanie wsadowe lub inne mechanizmy aktualizacji, inne zależności można rozwiązać w określonym czasie. (strona 128)

Vaughn Vernon mówi następujące w [skutecznego projektu kruszywa. Część II: Tworzenie kruszyw razem:](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

> W związku z tym jeśli wykonywanie polecenia w jednym wystąpieniu agregacji wymaga, \[aby dodatkowe reguły biznesowe były wykonywane na jednym lub większej liczbie agregatów, należy użyć spójności ostatecznej ... \] Istnieje praktyczny sposób obsługi spójności ostatecznej w modelu DDD. Metoda agregująca publikuje zdarzenie domeny, które jest w czasie dostarczane do jednego lub więcej subskrybentów asynchronicznych.

Uzasadnienie to opiera się na ogarnięciu transakcji drobnoziarnistych zamiast transakcji obejmujących wiele agregatów lub jednostek. Chodzi o to, że w drugim przypadku liczba blokad bazy danych będzie znaczna w aplikacjach na dużą skalę o wysokich potrzebach skalowalności. Ogarnięcie faktu, że wysoce skalowalne aplikacje nie muszą mieć natychmiastowej spójności transakcyjnej między wieloma agregacjami, pomaga w akceptowaniu pojęcia spójności ostatecznej. Zmiany atomowe często nie są potrzebne przez firmę, a w każdym razie obowiązkiem ekspertów domeny jest stwierdzenie, czy konkretne operacje wymagają transakcji atomowych, czy nie. Jeśli operacja zawsze wymaga transakcji atomowej między wieloma agregatami, można zapytać, czy agregacja powinna być większa, czy nie została poprawnie zaprojektowana.

Jednak inni deweloperzy i architekci, tacy jak Jimmy Bogard, są w porządku z jedną transakcją w kilku agregatach , ale tylko wtedy, gdy te dodatkowe agregaty są związane z efektami ubocznymi dla tego samego oryginalnego polecenia. Na przykład, w [lepszym wzorcu zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard mówi to:

> Zazwyczaj chcę, aby skutki uboczne zdarzenia domeny występują w ramach tej samej transakcji logicznej, \[ale niekoniecznie w tym samym zakresie podnoszenia zdarzenia domeny ... \] Tuż przed zatwierdzeniem naszej transakcji wysyłamy nasze zdarzenia do odpowiednich programów obsługi.

Jeśli wywołasz zdarzenia domeny tuż *przed* zatwierdzeniem oryginalnej transakcji, to dlatego, że chcesz, aby skutki uboczne tych zdarzeń zostały uwzględnione w tej samej transakcji. Na przykład jeśli EF DbContext SaveChanges metoda nie powiedzie się, transakcja wycofa wszystkie zmiany, w tym wynik wszelkich operacji efekt uboczny zaimplementowane przez programy obsługi zdarzeń domeny pokrewne. Dzieje się tak, ponieważ zakres życia DbContext jest domyślnie zdefiniowany jako "zakres". W związku z tym DbContext obiekt jest współużytkowany przez wiele obiektów repozytorium jest tworzone w tym samym zakresie lub wykres obiektu. Jest to zbieżne z zakresem HttpRequest podczas tworzenia aplikacji interfejsu API sieci Web lub MVC.

W rzeczywistości oba podejścia (pojedyncza transakcja niepodzielna i spójność ostateczna) mogą mieć rację. To naprawdę zależy od twojej domeny lub wymagań biznesowych i tego, co mówią ci eksperci domeny. Zależy to również od tego, jak skalowalna jest potrzebna usługa (bardziej szczegółowe transakcje mają mniejszy wpływ w odniesieniu do blokad bazy danych). I to zależy od tego, ile inwestycji są skłonni do wykonania w kodzie, ponieważ spójność ostateczna wymaga bardziej złożony kod w celu wykrycia możliwych niespójności w agregatach i konieczność zaimplementowania akcji kompensacyjnych. Należy wziąć pod uwagę, że jeśli zatwierdzić zmiany do oryginalnego agregacji i później, gdy zdarzenia są wywoływane, jeśli występuje problem i programy obsługi zdarzeń nie może zatwierdzić ich skutki uboczne, będziesz miał niespójności między agregatów.

Sposób, aby umożliwić akcje kompensacyjne byłoby do przechowywania zdarzeń domeny w tabelach dodatkowej bazy danych, dzięki czemu mogą być częścią oryginalnej transakcji. Następnie może mieć proces wsadowy, który wykrywa niespójności i uruchamia akcje kompensacyjne, porównując listę zdarzeń z bieżącym stanem agregatów. Działania kompensacyjne są częścią złożonego tematu, który będzie wymagał głębokiej analizy z Twojej strony, która obejmuje omówienie go z użytkownikami biznesowymi i ekspertami domeny.

W każdym przypadku możesz wybrać potrzebne podejście. Ale początkowe odroczone podejście — podnoszenie zdarzeń przed zatwierdzeniem, więc używasz pojedynczej transakcji — jest najprostszym podejściem podczas korzystania z EF Core i relacyjnej bazy danych. Jest to łatwiejsze do wdrożenia i ważne w wielu przypadkach biznesowych. Jest to również podejście używane w mikrousługi zamawiania w eShopOnContainers.

Ale jak rzeczywiście wysyłać te zdarzenia do odpowiednich programów obsługi zdarzeń? Jaki jest `_mediator` obiekt, który widzisz w poprzednim przykładzie? Ma to do czynienia z technik i artefaktów używanych do mapowania między zdarzeniami i ich programy obsługi zdarzeń.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dyspozytor zdarzeń domeny: mapowanie zdarzeń na programy obsługi zdarzeń

Gdy będzie można wywołać lub opublikować zdarzenia, trzeba jakiś artefakt, który opublikuje zdarzenie, tak aby każdy powiązany program obsługi można uzyskać go i przetwarzać skutki uboczne na podstawie tego zdarzenia.

Jednym z podejść jest prawdziwy system obsługi wiadomości lub nawet magistrali zdarzeń, prawdopodobnie na podstawie magistrali usług, w przeciwieństwie do zdarzeń w pamięci. Jednak w pierwszym przypadku prawdziwe wiadomości byłyby przesadą dla przetwarzania zdarzeń domeny, ponieważ wystarczy przetworzyć te zdarzenia w ramach tego samego procesu (to jest w tej samej warstwie domeny i aplikacji).

Innym sposobem mapowania zdarzeń do wielu programów obsługi zdarzeń jest przy użyciu rejestracji typów w kontenerze IoC, dzięki czemu można dynamicznie wnioskować, gdzie do wywołania zdarzeń. Innymi słowy należy wiedzieć, jakie programy obsługi zdarzeń należy uzyskać określonego zdarzenia. Rysunek 7–16 przedstawia uproszczone podejście do tego podejścia.

![Diagram przedstawiający dyspozytor zdarzeń domeny wysyłający zdarzenia do odpowiednich programów obsługi.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Rysunek 7-16**. Dyspozytor zdarzeń domeny przy użyciu IoC

Można zbudować wszystkie hydraulika i artefakty, aby zaimplementować to podejście samodzielnie. Można jednak również użyć dostępnych bibliotek, takich jak [MediatR,](https://github.com/jbogard/MediatR) który używa kontenera IoC pod osłonami. W związku z tym można bezpośrednio użyć wstępnie zdefiniowanych interfejsów i metody publikowania/wysyłania obiektu mediatora.

W kodzie należy najpierw zarejestrować typy obsługi zdarzeń w kontenerze IoC, jak pokazano w poniższym przykładzie w [mikrousługi zamawiania eShopOnContainers:](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

Kod najpierw identyfikuje zestaw, który zawiera programy obsługi zdarzeń domeny, lokalizując zestaw, który przechowuje dowolny z programów obsługi (przy użyciu typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale można było wybrać inny program obsługi zdarzeń, aby zlokalizować zestaw). Ponieważ wszystkie programy obsługi zdarzeń implementują interfejs IAsyncNotificationHandler, kod po prostu wyszukuje te typy i rejestruje wszystkie programy obsługi zdarzeń.

### <a name="how-to-subscribe-to-domain-events"></a>Jak subskrybować zdarzenia domeny

Korzystając z MediatR, każdy program obsługi zdarzeń musi używać typu zdarzenia, który znajduje się w parametrze ogólnym interfejsu INotificationHandler, jak widać w następującym kodzie:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na podstawie relacji między zdarzeniem i obsługi zdarzeń, które można uznać za subskrypcję, Artefakt MediatR można odnajdywać wszystkie programy obsługi zdarzeń dla każdego zdarzenia i wyzwolić każdy z tych programów obsługi zdarzeń.

### <a name="how-to-handle-domain-events"></a>Jak obsługiwać zdarzenia w domenie

Na koniec program obsługi zdarzeń zwykle implementuje kod warstwy aplikacji, który używa repozytoriów infrastruktury w celu uzyskania wymaganych dodatkowych agregatów i do wykonywania logiki domeny efekt uboczny. Następujący [kod obsługi zdarzeń domeny w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), pokazuje przykład implementacji.

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;

        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }

        buyer.VerifyOrAddPaymentMethod(cardTypeId,
                                       $"Payment Method on {DateTime.UtcNow}",
                                       orderStartedEvent.CardNumber,
                                       orderStartedEvent.CardSecurityNumber,
                                       orderStartedEvent.CardHolderName,
                                       orderStartedEvent.CardExpiration,
                                       orderStartedEvent.Order.Id);

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer)
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

Poprzedni kod obsługi zdarzeń domeny jest uważany za kod warstwy aplikacji, ponieważ używa repozytoriów infrastruktury, jak wyjaśniono w następnej sekcji na warstwie trwałości infrastruktury. Programy obsługi zdarzeń można również użyć innych składników infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Zdarzenia domeny mogą generować zdarzenia integracji, które mają być publikowane poza granicami mikrousług

Na koniec należy wspomnieć, że czasami można propagować zdarzenia w wielu mikrousług. Propagacja jest zdarzeniem integracji i może być opublikowana za pośrednictwem magistrali zdarzeń z dowolnego programu obsługi zdarzeń określonej domeny.

## <a name="conclusions-on-domain-events"></a>Wnioski dotyczące zdarzeń domeny

Jak wspomniano, użyj zdarzeń domeny, aby jawnie zaimplementować skutki uboczne zmian w domenie. Aby użyć terminologii DDD, użyj zdarzeń domeny, aby jawnie implementować skutki uboczne w jednej lub wielu agregatach. Ponadto i dla lepszej skalowalności i mniejszy wpływ na blokady bazy danych, należy użyć spójności ostatecznej między agregacji w tej samej domenie.

Aplikacja referencyjna używa [MediatR](https://github.com/jbogard/MediatR) do propagowania zdarzeń domeny synchronicznie w agregatach w ramach jednej transakcji. Jednak można również użyć niektórych implementacji usługi AMQP, takich jak [RabbitMQ](https://www.rabbitmq.com/) lub [usługi Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) do propagowania zdarzeń domeny asynchronicznie, przy użyciu spójności ostatecznej, ale, jak wspomniano powyżej, należy wziąć pod uwagę potrzebę akcji kompensacyjnych w przypadku awarii.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Grzegorz Young. Co to jest zdarzenie domeny?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Zdarzenia w domenie i spójność ostateczna** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Lepszy wzorzec zdarzeń domeny** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon. Efektywna agregat projektowa część II: Tworzenie kruszyw razem** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Wzmacnianie domeny: Zdarzenia domeny** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Tony Truong. Przykład wzorca zdarzeń domeny** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan. Jak tworzyć w pełni hermetyzowane modele domen** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan. Zdarzenia w domenie – Weź 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan. Wydarzenia w domenie – Zbawienie** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Nie publikuj zdarzeń domeny, zwróć je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre. Zdarzenia domeny a zdarzenia integracji w architekturach DDD i mikrousługach** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Poprzedni](client-side-validation.md)
>[następny](infrastructure-persistence-layer-design.md)
