---
title: Zdarzenia domeny. projektowanie i wdrażanie
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Uzyskaj szczegółowy widok zdarzeń domeny, kluczową koncepcję do ustanowienia komunikacji między agregatami.
ms.date: 10/08/2018
ms.openlocfilehash: e03abba66945a6434f6a81eaa9f50d53998f346c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988720"
---
# <a name="domain-events-design-and-implementation"></a>Zdarzenia w domenie: projektowanie i implementacja

Użyj zdarzeń domeny, aby jawnie zaimplementować skutki uboczne zmian w domenie. Innymi słowy i przy użyciu terminologii DDD, użyj zdarzeń domeny jawnie implementować skutki uboczne w wielu agregatów. Opcjonalnie dla lepszej skalowalności i mniejszego wpływu w blokady bazy danych, należy użyć spójności ostatecznej między agregatami w tej samej domenie.

## <a name="what-is-a-domain-event"></a>Co to jest zdarzenie domeny?

Wydarzenie to coś, co wydarzyło się w przeszłości. Zdarzenie domeny jest coś, co się stało w domenie, które chcesz innych części tej samej domeny (w procesie) być świadomi. Zgłoszone części zwykle reagują w jakiś sposób na wydarzenia.

Ważną zaletą zdarzeń domeny jest to, że skutki uboczne mogą być wyraźnie wyrażone.

Na przykład jeśli po prostu używasz Entity Framework i musi być reakcja na niektóre zdarzenia, prawdopodobnie kod, co trzeba blisko tego, co wyzwala zdarzenie. Tak więc reguła jest połączona, niejawnie, z kodem i musisz zajrzeć do kodu, aby, miejmy nadzieję, zrealizować regułę zaimplementowano tam.

Z drugiej strony przy użyciu zdarzeń domeny sprawia, `DomainEvent` że pojęcie `DomainEventHandler` jawne, ponieważ istnieje i co najmniej jeden zaangażowany.

Na przykład w aplikacji eShopOnContainers, gdy zamówienie jest tworzone, użytkownik `OrderStartedDomainEvent` staje się kupującym, `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`więc jest wywoływana i obsługiwana w , więc podstawowa koncepcja jest oczywista.

Krótko mówiąc, zdarzenia domeny pomagają wyraźnie wyrazić reguły domeny, oparte na wszechobecnym języku dostarczonym przez ekspertów domeny. Zdarzenia domeny umożliwiają również lepsze oddzielenie problemów między klasami w tej samej domenie.

Ważne jest, aby upewnić się, że podobnie jak transakcji bazy danych, wszystkie operacje związane ze zdarzeniem domeny zakończyć się pomyślnie lub żaden z nich nie.

Zdarzenia domeny są podobne do zdarzeń w stylu obsługi wiadomości, z jedną istotną różnicą. W przypadku obsługi wiadomości, kolejkowania wiadomości, brokerów wiadomości lub magistrali usług przy użyciu usługi AMQP wiadomość jest zawsze wysyłana asynchronicznie i komunikowana między procesami i komputerami. Jest to przydatne do integrowania wielu ograniczonych kontekstów, mikrousług lub nawet różnych aplikacji. Jednak w przypadku zdarzeń domeny chcesz wywołać zdarzenie z aktualnie uruchomionej operacji domeny, ale chcesz, aby wszelkie skutki uboczne wystąpiły w tej samej domenie.

Zdarzenia domeny i ich skutki uboczne (akcje wyzwalane później, które są zarządzane przez programy obsługi zdarzeń) powinny wystąpić niemal natychmiast, zwykle w toku i w tej samej domenie. W związku z tym zdarzenia domeny może być synchroniczne lub asynchroniczne. Zdarzenia integracji, jednak zawsze powinny być asynchroniczne.

## <a name="domain-events-versus-integration-events"></a>Zdarzenia domeny a zdarzenia integracji

Semantycznie, domeny i integracji wydarzenia są takie same: powiadomienia o czymś, co właśnie się stało. Ich realizacja musi być jednak inna. Zdarzenia domeny to tylko wiadomości wypychane do dyspozytora zdarzeń domeny, które mogą być implementowane jako mediator w pamięci na podstawie kontenera IoC lub innej metody.

Z drugiej strony celem zdarzeń integracji jest propagowanie zatwierdzonych transakcji i aktualizacji do dodatkowych podsystemów, niezależnie od tego, czy są to inne mikrousługi, ograniczone konteksty, a nawet aplikacje zewnętrzne. W związku z tym powinny one wystąpić tylko wtedy, gdy jednostka jest pomyślnie utrwalone, w przeciwnym razie jest tak, jakby cała operacja nigdy się nie stało.

Jak wspomniano wcześniej, zdarzenia integracji muszą być oparte na komunikacji asynchronicznej między wieloma mikrousługami (inne konteksty ograniczone) lub nawet zewnętrznych systemów/aplikacji.

W związku z tym interfejs magistrali zdarzeń wymaga pewnej infrastruktury, która umożliwia komunikację między procesami i rozproszonymi między potencjalnie usług zdalnych. Może być oparty na komercyjnej magistrali usług, kolejkach, udostępnionej bazie danych używanej jako skrzynka pocztowa lub innym rozproszonym i idealnie wypychanym systemie obsługi wiadomości.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Zdarzenia domeny jako preferowany sposób wyzwalania skutków ubocznych w wielu skupiskach w tej samej domenie

Jeśli wykonanie polecenia związanego z jednym wystąpieniem agregacji wymaga dodatkowych reguł domeny, które mają być uruchamiane na co najmniej jednym dodatkowym agregacji, należy zaprojektować i zaimplementować te skutki uboczne, które mają być wyzwalane przez zdarzenia domeny. Jak pokazano na rysunku 7-14 i jako jeden z najważniejszych przypadków użycia, zdarzenie domeny powinny być używane do propagowania zmian stanu w wielu agregatach w ramach tego samego modelu domeny.

![Diagram przedstawiający zdarzenie domeny kontrolujące dane agregacji kupującego.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Rysunek 7-14**. Zdarzenia domeny wymuszaj spójność między wieloma agregacjami w tej samej domenie

Rysunek 7-14 pokazuje, jak spójność między agregatami jest osiągana przez zdarzenia domeny. Gdy użytkownik inicjuje zamówienie, agregowanie zamówień wysyła zdarzenie `OrderStarted` domeny. Zdarzenie Domeny OrderStarted jest obsługiwane przez agregację kupującego w celu utworzenia obiektu Nabywca w mikrousługach zamawiania, na podstawie oryginalnych informacji o użytkowniku z mikrousługi tożsamości (z informacjami podanymi w poleceniu CreateOrder).

Alternatywnie można mieć agregacji głównego subskrybowane dla zdarzeń wywoływanych przez członków jego agregacji (jednostek podrzędnych). Na przykład każda jednostka podrzędna OrderItem może podnieść zdarzenie, gdy cena towaru jest wyższa niż określona kwota lub gdy kwota towaru produktu jest zbyt wysoka. Główny zagregowany może następnie odbierać te zdarzenia i wykonywać obliczenia globalne lub agregację.

Ważne jest, aby zrozumieć, że ta komunikacja oparta na zdarzeniach nie jest implementowana bezpośrednio w ramach agregatów; należy zaimplementować programy obsługi zdarzeń domeny.

Obsługa zdarzeń domeny jest problemem aplikacji. Warstwa modelu domeny powinna koncentrować się tylko na logice domeny — na rzeczach, które zrozumiałby ekspert domeny, a nie na infrastrukturze aplikacji, takich jak programy obsługi i akcje trwałości efektów ubocznych przy użyciu repozytoriów. W związku z tym poziom warstwy aplikacji jest, gdzie powinien mieć programy obsługi zdarzeń domeny wyzwalania akcji, gdy zdarzenie domeny jest wywoływana.

Zdarzenia domeny mogą być również używane do wyzwalania dowolnej liczby akcji aplikacji, a co ważniejsze, musi być otwarty, aby zwiększyć tę liczbę w przyszłości w sposób oddzielony. Na przykład po uruchomieniu zamówienia można opublikować zdarzenie domeny, aby propagować te informacje do innych agregatów, a nawet do podnoszenia akcji aplikacji, takich jak powiadomienia.

Punktem kluczowym jest otwarta liczba akcji, które mają być wykonywane w przypadku wystąpienia zdarzenia domeny. Ostatecznie akcje i reguły w domenie i aplikacji będą rosnąć. Złożoność lub liczba akcji efekt uboczny, gdy coś się stanie wzrośnie, ale jeśli kod zostały połączone `new`z "kleju" (czyli tworzenie określonych obiektów z ), a następnie za każdym razem, gdy trzeba dodać nową akcję trzeba również zmienić pracy i przetestowane kodu.

Ta zmiana może spowodować nowe błędy i takie podejście jest również sprzeczne z [zasadą Otwarte / Zamknięte](https://en.wikipedia.org/wiki/Open/closed_principle) z [SOLID](https://en.wikipedia.org/wiki/SOLID). Nie tylko to, oryginalna klasa, która była organizowanie operacji będzie rosnąć i rosnąć, co jest sprzeczne z [zasadą jednolitej odpowiedzialności (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Z drugiej strony, jeśli używasz zdarzeń domeny, można utworzyć implementacji szczegółowe i oddzielone przez oddzielenie obowiązków przy użyciu tego podejścia:

1. Wyślij polecenie (na przykład Utwórz polecenie).
2. Odbierz polecenie w programie obsługi poleceń.
   - Wykonywanie transakcji pojedynczej agregacji.
   - (Opcjonalnie) Podnieść zdarzenia domeny dla skutków ubocznych (na przykład OrderStartedDomainEvent).
3. Obsługa zdarzeń domeny (w ramach bieżącego procesu), które będą wykonywać otwartą liczbę efektów ubocznych w wielu agregatach lub akcjach aplikacji. Przykład:
   - Zweryfikuj lub utwórz metodę płatności kupującego i płatności.
   - Tworzenie i wysyłanie powiązanego zdarzenia integracji do magistrali zdarzeń do propagacji stanów w mikrousługach lub wyzwalania akcji zewnętrznych, takich jak wysyłanie wiadomości e-mail do kupującego.
   - Obsługiwać inne działania niepożądane.

Jak pokazano na rysunku 7-15, począwszy od tego samego zdarzenia domeny, można obsługiwać wiele akcji związanych z innymi agregatami w domenie lub dodatkowych akcji aplikacji, które należy wykonać w mikrousługach łączących się ze zdarzeniami integracji i magistrali zdarzeń.

![Diagram przedstawiający zdarzenie domeny przekazywania danych do kilku programów obsługi zdarzeń.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Rysunek 7-15**. Obsługa wielu akcji w domenie

Może istnieć kilka programów obsługi dla tego samego zdarzenia domeny w warstwie aplikacji, jeden program obsługi może rozwiązać spójność między agregatami, a inny program obsługi może opublikować zdarzenie integracji, więc inne mikrousługi mogą coś z nim zrobić. Programy obsługi zdarzeń są zazwyczaj w warstwie aplikacji, ponieważ będzie używać obiektów infrastruktury, takich jak repozytoria lub interfejs API aplikacji dla zachowania mikrousług. W tym sensie programy obsługi zdarzeń są podobne do programów obsługi poleceń, więc oba są częścią warstwy aplikacji. Ważną różnicą jest to, że polecenie powinno być przetwarzane tylko raz. Zdarzenie domeny może być przetwarzane zero lub *n* razy, ponieważ mogą być odbierane przez wielu odbiorników lub programów obsługi zdarzeń z innym celem dla każdego programu obsługi.

Mając otwartą liczbę programów obsługi na zdarzenie domeny pozwala dodać tyle reguł domeny, ile potrzeba, bez wpływu na bieżący kod. Na przykład wdrożenie następującej reguły biznesowej może być tak proste, jak dodanie kilku programów obsługi zdarzeń (lub nawet tylko jednego):

> Gdy łączna kwota zakupiona przez klienta w sklepie, w dowolnej liczbie zamówień, przekracza 6000 USD, zastosuj 10% zniżki na każde nowe zamówienie i powiadom klienta e-mailem o tym rabatze dla przyszłych zamówień.

## <a name="implement-domain-events"></a>Implementowanie zdarzeń domeny

W języku C#zdarzenie domeny jest po prostu strukturą lub klasą przechowywania danych, taką jak DTO, ze wszystkimi informacjami związanymi z tym, co właśnie wydarzyło się w domenie, jak pokazano w poniższym przykładzie:

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

Jest to zasadniczo klasa, która przechowuje wszystkie dane związane ze zdarzeniem OrderStarted.

Jeśli chodzi o wszechobecny język domeny, ponieważ zdarzenie jest czymś, co wydarzyło się w przeszłości, nazwa klasy zdarzenia powinna być reprezentowana jako czasownik przeszłościowy, taki jak OrderStartedDomainEvent lub OrderShippedDomainEvent. W ten sposób zdarzenie domeny jest implementowane w mikrousługi zamawiania w eShopOnContainers.

Jak wspomniano wcześniej, ważną cechą wydarzeń jest to, że ponieważ wydarzenie jest czymś, co wydarzyło się w przeszłości, nie powinno się zmieniać. W związku z tym musi być niezmienne klasy. W poprzednim kodzie widać, że właściwości są tylko do odczytu. Nie ma sposobu, aby zaktualizować obiekt, można ustawić tylko wartości podczas jego tworzenia.

W tym miejscu należy podkreślić, że jeśli zdarzenia domeny mają być obsługiwane asynchronicznie, przy użyciu kolejki, która wymaga serializacji i deserializacji obiektów zdarzeń, właściwości musiałyby być "zestaw prywatny" zamiast tylko do odczytu, więc deserializer będzie mógł przypisać wartości po usunięciu z kolejki. Nie jest to problem w mikrousługi zamawiania, jak pub/sub zdarzenia domeny jest implementowany synchronicznie przy użyciu MediatR.

### <a name="raise-domain-events"></a>Zwiększanie zdarzeń domeny

Następne pytanie jest jak podnieść zdarzenie domeny, aby osiągnąć jego powiązanych programów obsługi zdarzeń. Można użyć wielu metod.

Udi Dahan pierwotnie proponowane (na przykład w kilku powiązanych wpisów, takich jak [zdarzenia domeny - Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) przy użyciu klasy statycznej do zarządzania i podnoszenia zdarzeń. Może to obejmować klasę statyczną o nazwie DomainEvents, która natychmiast wywołuje zdarzenia `DomainEvents.Raise(Event myEvent)`domeny, używając składni, takiej jak . Jimmy Bogard napisał wpis na blogu[(Wzmocnienie domeny: Domain Events),](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)który zaleca podobne podejście.

Jednak gdy klasa zdarzeń domeny jest statyczna, wysyła również do programów obsługi natychmiast. To sprawia, że testowanie i debugowanie trudniejsze, ponieważ programy obsługi zdarzeń z logiką efektów ubocznych są wykonywane natychmiast po zdarzenia jest wywoływana. Podczas testowania i debugowania, chcesz skupić się na i tylko to, co dzieje się w bieżących klas agregacji; nie chcesz nagle zostać przekierowany do innych programów obsługi zdarzeń dla skutków ubocznych związanych z innymi agregatami lub logiką aplikacji. Dlatego inne podejścia ewoluowały, jak wyjaśniono w następnej sekcji.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odroczone podejście do podnoszenia i wysyłania zdarzeń

Zamiast natychmiast wysyłać do programu obsługi zdarzeń domeny, lepszym rozwiązaniem jest dodanie zdarzeń domeny do kolekcji, a następnie wysłanie tych zdarzeń domeny *tuż przed* lub *zaraz* *po* zapisaniu transakcji (tak jak w przypadku savechanges w EF). (To podejście zostało opisane przez Jimmy Bogard w tym poście [lepszy wzorzec zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Decyzja o wysłaniu zdarzeń domeny bezpośrednio przed lub zaraz po zatwierdzeniu transakcji jest ważna, ponieważ określa, czy zostaną uwzględnione skutki uboczne jako część tej samej transakcji lub w różnych transakcjach. W tym ostatnim przypadku należy radzić sobie z spójność ostateczną w wielu agregatów. Ten temat został omówiony w następnej sekcji.

Odroczone podejście jest to, co eShopOnContainers używa. Najpierw należy dodać zdarzenia dzieje się w jednostkach do kolekcji lub listy zdarzeń na jednostkę. Ta lista powinna być częścią obiektu jednostki lub nawet lepszą częścią podstawowej klasy encji, jak pokazano w poniższym przykładzie klasy podstawowej jednostki:

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

Jeśli chcesz podnieść zdarzenie, wystarczy dodać go do kolekcji zdarzeń z kodu w dowolnej metodzie jednostki agregacji głównej.

Poniższy kod, część [zamówienia agregacji root w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), pokazuje przykład:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Należy zauważyć, że jedyną rzeczą, którą robi AddDomainEvent metoda jest dodanie zdarzenia do listy. Żadne zdarzenie nie jest jeszcze wywoływane, a nie jest jeszcze wywoływany żaden program obsługi zdarzeń.

Faktycznie chcesz wysłać zdarzenia później, podczas zatwierdzania transakcji do bazy danych. Jeśli używasz Entity Framework Core, oznacza to, że w SaveChanges metody EF DbContext, jak w poniższym kodzie:

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

Za pomocą tego kodu można wysłać zdarzenia jednostki do ich odpowiednich programów obsługi zdarzeń.

Ogólny wynik jest, że zostały oddzielone wywoływania zdarzenia domeny (proste dodać do listy w pamięci) z wysyłania go do obsługi zdarzeń. Ponadto, w zależności od rodzaju dyspozytora, którego używasz, można wysyłać zdarzenia synchronicznie lub asynchronicznie.

Należy pamiętać, że granice transakcyjne wchodzą w istotną grę tutaj. Jeśli jednostka pracy i transakcji może obejmować więcej niż jeden agregacji (jak przy użyciu EF Core i relacyjnej bazy danych), może to działać dobrze. Ale jeśli transakcja nie może obejmować agregatów, takich jak podczas korzystania z bazy danych NoSQL, takich jak Usługa Azure CosmosDB, należy zaimplementować dodatkowe kroki w celu osiągnięcia spójności. Jest to kolejny powód, dla którego ignorancja trwałości nie jest uniwersalna; zależy to od używanego systemu pamięci masowej.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Pojedyncza transakcja w ramach agregacji a spójność ostateczna w agregatach

Pytanie, czy wykonać pojedynczą transakcję w agregatach w porównaniu z poleganiem na spójności ostatecznej między tymi agregacjami, jest kontrowersyjne. Wielu autorów DDD, takich jak Eric Evans i Vaughn Vernon, opowiada się za zasadą, że jedna transakcja = jedna agregacja i dlatego opowiada się za ostateczną spójnością między agregatami. Na przykład, w swojej książce *Domain-Driven Design*, Eric Evans mówi to:

> Nie oczekuje się, że żadna reguła obejmująca agregacje będzie zawsze aktualna. Za pomocą przetwarzania zdarzeń, przetwarzania wsadowego lub innych mechanizmów aktualizacji inne zależności można rozwiązać w określonym czasie. (strona 128)

Vaughn Vernon mówi, co następuje w [efektywnym projektowaniu kruszywa. Część II: Tworzenie współpracy agregatów:](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

> W związku z tym jeśli wykonywanie polecenia w jednym zagregowanym wystąpieniu wymaga \[wykonania dodatkowych reguł biznesowych na co najmniej jednym agregacie, należy użyć spójności ostatecznej ... \] Istnieje praktyczny sposób obsługi spójności ostatecznej w modelu DDD. Metoda agregująca publikuje zdarzenie domeny, które jest w czasie dostarczane do jednego lub więcej subskrybentów asynchronicznych.

To uzasadnienie opiera się na obejmujące transakcji drobnoziarnistych zamiast transakcji obejmujących wiele agregatów lub jednostek. Chodzi o to, że w drugim przypadku liczba blokad bazy danych będzie znaczna w aplikacjach na dużą skalę o wysokich potrzebach skalowalności. Obejmując fakt, że wysoce skalowalne aplikacje nie muszą mieć natychmiastowej spójności transakcyjnej między wieloma agregatami, pomaga w zaakceptowaniu koncepcji spójności ostatecznej. Zmiany atomowe często nie są potrzebne przez firmę, a w każdym razie obowiązkiem ekspertów domeny jest stwierdzenie, czy konkretne operacje wymagają transakcji atomowych, czy nie. Jeśli operacja zawsze wymaga transakcji niepodzielnej między wieloma agregatami, można zapytać, czy agregacja powinna być większa lub nie została poprawnie zaprojektowana.

Jednak inni deweloperzy i architekci, tacy jak Jimmy Bogard, są w porządku z obejmującą pojedynczą transakcję w kilku agregatach , ale tylko wtedy, gdy te dodatkowe agregaty są związane z efektami ubocznymi dla tego samego oryginalnego polecenia. Na przykład, w [lepszym wzorzec zdarzeń domeny,](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard mówi tak:

> Zazwyczaj chcę, aby skutki uboczne zdarzenia domeny występowały w ramach tej samej transakcji logicznej, ale niekoniecznie w tym samym zakresie wywoływania zdarzenia \[domeny ... \] Tuż przed zatwierdzeniem naszej transakcji wysyłamy nasze zdarzenia do odpowiednich programów obsługi.

Jeśli wyślesz zdarzenia domeny tuż *przed* zatwierdzeniem oryginalnej transakcji, to dlatego, że chcesz, aby skutki uboczne tych zdarzeń zostały uwzględnione w tej samej transakcji. Na przykład jeśli EF DbContext SaveChanges metoda nie powiedzie się, transakcja będzie wycofać wszystkie zmiany, w tym wynik wszelkich operacji efekt uboczny zaimplementowane przez programy obsługi zdarzeń domeny powiązanych. Dzieje się tak, ponieważ zakres życia DbContext jest domyślnie zdefiniowany jako "zakres". W związku z tym DbContext obiekt jest współużytkowany przez wiele obiektów repozytorium tworzone w tym samym zakresie lub wykres obiektu. Zbiega się to z zakresem HttpRequest podczas tworzenia aplikacji interfejsu API sieci Web lub MVC.

W rzeczywistości oba podejścia (pojedyncza transakcja niepodzielna i spójność ostateczna) mogą mieć rację. To naprawdę zależy od domeny lub wymagań biznesowych i tego, co mówią ci eksperci od domeny. Zależy to również od tego, jak skalowalny trzeba usługi,aby być (bardziej szczegółowe transakcje mają mniejszy wpływ w odniesieniu do blokad bazy danych). I to zależy od tego, ile inwestycji jesteś gotów dokonać w kodzie, ponieważ spójność ostateczna wymaga bardziej złożonego kodu w celu wykrycia możliwych niespójności w agregatach i konieczności zaimplementowania akcji kompensacyjnych. Należy wziąć pod uwagę, że jeśli zatwierdzisz zmiany w oryginalnym agregacji, a następnie, gdy zdarzenia są wywoływane, jeśli występuje problem i programy obsługi zdarzeń nie może zatwierdzić ich skutki uboczne, będziesz miał niespójności między agregatami.

Sposobem na umożliwienie akcji kompensacyjnych byłoby przechowywanie zdarzeń domeny w dodatkowych tabelach bazy danych, aby mogły być częścią oryginalnej transakcji. Następnie może mieć proces wsadowy, który wykrywa niespójności i uruchamia akcje kompensacyjne, porównując listę zdarzeń z bieżącym stanem agregatów. Akcje kompensacyjne są częścią złożonego tematu, który będzie wymagał dogłębnej analizy z Twojej strony, która obejmuje omówienie go z użytkownikami biznesowymi i ekspertami domeny.

W każdym razie możesz wybrać podejście, którego potrzebujesz. Jednak początkowe podejście odroczone — podnoszenie zdarzeń przed zatwierdzeniem, dlatego używasz pojedynczej transakcji — jest najprostszym podejściem podczas korzystania z EF Core i relacyjnej bazy danych. Jest to łatwiejsze do wdrożenia i ważne w wielu przypadkach biznesowych. Jest to również podejście używane w mikrousługi zamawiania w eShopOnContainers.

Ale jak faktycznie wysyłać te zdarzenia do ich odpowiednich programów obsługi zdarzeń? Jaki jest `_mediator` obiekt widoczny w poprzednim przykładzie? Ma to do czynienia z technik i artefaktów, które można użyć do mapowania między zdarzeniami i ich obsługi zdarzeń.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dyspozytor zdarzeń domeny: mapowanie zdarzeń do obsługi zdarzeń

Gdy będziesz w stanie wysyłać lub publikować zdarzenia, potrzebujesz jakiegoś artefaktu, który opublikuje zdarzenie, aby każdy powiązany program obsługi mógł je uzyskać i przetworzyć skutki uboczne na podstawie tego zdarzenia.

Jednym z podejść jest prawdziwy system obsługi wiadomości lub nawet magistrala zdarzeń, prawdopodobnie na podstawie magistrali usług, w przeciwieństwie do zdarzeń w pamięci. Jednak w pierwszym przypadku prawdziwe wiadomości byłoby przesadą w przetwarzaniu zdarzeń domeny, ponieważ wystarczy przetworzyć te zdarzenia w ramach tego samego procesu (czyli w tej samej domenie i warstwie aplikacji).

Innym sposobem mapowania zdarzeń do wielu programów obsługi zdarzeń jest przy użyciu rejestracji typów w kontenerze IoC, dzięki czemu można dynamicznie wywnioskować, gdzie można wysłać zdarzenia. Innymi słowy należy wiedzieć, jakie programy obsługi zdarzeń muszą uzyskać określone zdarzenie. Rysunek 7-16 przedstawia uproszczone podejście do tego podejścia.

![Diagram przedstawiający dyspozytora zdarzeń domeny wysyłającego zdarzenia do odpowiednich programów obsługi.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Rysunek 7-16**. Dyspozytor zdarzeń domeny przy użyciu usługi IoC

Można zbudować wszystkie instalacje wodno-kanalizacyjne i artefakty, aby samodzielnie wdrożyć to podejście. Można jednak również użyć dostępnych bibliotek, takich jak [MediatR,](https://github.com/jbogard/MediatR) która używa kontenera IoC pod osłonami. W związku z tym można bezpośrednio użyć wstępnie zdefiniowanych interfejsów i metody publikowania/wysyłania obiektu mediatora.

W kodzie najpierw musisz zarejestrować typy obsługi zdarzeń w kontenerze IoC, jak pokazano w poniższym przykładzie w [eShopOnContainers Zamawianie mikrousług:](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)

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

Kod najpierw identyfikuje zestaw, który zawiera programy obsługi zdarzeń domeny przez zlokalizowanie zestawu, który zawiera dowolny z programów obsługi (przy użyciu typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale można było wybrać inny program obsługi zdarzeń, aby zlokalizować zestaw). Ponieważ wszystkie programy obsługi zdarzeń implementują interfejs IAsyncNotificationHandler, kod następnie po prostu wyszukuje te typy i rejestruje wszystkie programy obsługi zdarzeń.

### <a name="how-to-subscribe-to-domain-events"></a>Jak subskrybować wydarzenia domeny

Korzystając z funkcji MediatR, każdy program obsługi zdarzeń musi używać typu zdarzenia, który znajduje się w ogólnym parametrze interfejsu INotificationHandler, jak widać w następującym kodzie:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na podstawie relacji między zdarzeniami i obsługi zdarzeń, które można uznać za subskrypcję, Artefakt MediatR można odnajdywać wszystkie programy obsługi zdarzeń dla każdego zdarzenia i wyzwolić każdy z tych programów obsługi zdarzeń.

### <a name="how-to-handle-domain-events"></a>Jak obsługiwać zdarzenia domeny

Na koniec program obsługi zdarzeń zwykle implementuje kod warstwy aplikacji, który używa repozytoriów infrastruktury w celu uzyskania wymaganych dodatkowych agregatów i wykonania logiki domeny efektu ubocznego. Następujący [kod obsługi zdarzeń domeny w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), pokazuje przykład implementacji.

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

Poprzedni kod obsługi zdarzeń domeny jest uważany za kod warstwy aplikacji, ponieważ używa repozytoriów infrastruktury, jak wyjaśniono w następnej sekcji na warstwie trwałości infrastruktury. Programy obsługi zdarzeń mogą również używać innych składników infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Zdarzenia domeny mogą generować zdarzenia integracji, które mają być publikowane poza granicami mikrousług

Na koniec należy wspomnieć, że czasami warto propagować zdarzenia w wielu mikrousługach. Propagacja jest zdarzeniem integracji i może zostać opublikowana za pośrednictwem magistrali zdarzeń z dowolnego programu obsługi zdarzeń określonej domeny.

## <a name="conclusions-on-domain-events"></a>Wnioski dotyczące zdarzeń domeny

Zgodnie z opisem użyj zdarzeń domeny, aby jawnie zaimplementować skutki uboczne zmian w domenie. Aby użyć terminologii DDD, użyj zdarzeń domeny, aby jawnie zaimplementować skutki uboczne w jednym lub wielu agregatach. Ponadto i dla lepszej skalowalności i mniejszy wpływ na blokady bazy danych, należy użyć spójności ostatecznej między agregatami w tej samej domenie.

Aplikacja referencyjna używa [MediatR](https://github.com/jbogard/MediatR) do propagowania zdarzeń domeny synchronicznie w ramach agregacji w ramach jednej transakcji. Jednak można również użyć niektórych implementacji AMQP, takich jak [RabbitMQ](https://www.rabbitmq.com/) lub [usługi Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) do propagowania zdarzeń domeny asynchronicznie, przy użyciu spójności ostatecznej, ale, jak wspomniano powyżej, należy wziąć pod uwagę potrzebę akcji kompensacyjnych w przypadku awarii.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Greg Young. Co to jest zdarzenie domeny?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Zdarzenia domeny i spójność ostateczna** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Lepszy wzorzec zdarzeń domeny** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon. Efektywny projekt agregatu Część II: Tworzenie współpracy agregatów** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Wzmocnienie domeny: Zdarzenia domeny** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Tony Truong. Przykład wzorca zdarzeń domeny** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan. Jak utworzyć w pełni hermetyzowane modele domen** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan. Wydarzenia w domenie — Weź 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan. Wydarzenia domeny – Zbawienie** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Nie publikuj zdarzeń domeny, zwróć je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre. Zdarzenia domeny a zdarzenia integracji w architekturach DDD i mikrousług** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Poprzedni](client-side-validation.md)
>[następny](infrastructure-persistence-layer-design.md)
