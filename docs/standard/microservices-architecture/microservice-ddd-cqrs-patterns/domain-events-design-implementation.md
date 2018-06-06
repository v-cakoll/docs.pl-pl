---
title: Zdarzenia domeny. Projektowanie i wdrażanie
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Zdarzenia domeny, projektowanie i wdrażanie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: e6af18b1154759677c7749632eace30bad752591
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697199"
---
# <a name="domain-events-design-and-implementation"></a>Zdarzenia domeny: projektowanie i wdrażanie

Zdarzenia domeny umożliwia jawne Implementowanie skutków ubocznych zmiany w swojej domenie. W innych wyrazów i za pomocą terminologii DDD umożliwia jawne Implementowanie skutków ubocznych między Agreguje wiele zdarzeń domeny. Opcjonalnie lepszą skalowalność i mniej wpływ zablokowanie bazy danych, należy użyć spójność ostateczna między zagregowanych zakresu umieszczonych w tej samej domenie.

## <a name="what-is-a-domain-event"></a>Co to jest zdarzenie domeny?

Zdarzenie jest coś, co ma przypada w przeszłości. Zdarzenie w domenie jest, logicznie, czegoś, co się stało w określonej domenie i coś ma inne części tej samej domeny (w trakcie), należy pamiętać o i potencjalnie reagowania na.

Ważne korzyści zdarzeń domeny jest, że efekty uboczne po coś się stało w domenie może zostać wyrażona jawnie zamiast niejawnie. Te strony efekty muszą być zgodne, tak się zdarzyć, albo wszystkie operacje związane z zadań biznesowych lub żadna z nich. Ponadto zdarzenia domeny umożliwiają lepsze separacji między klas w ramach tej samej domenie.

Na przykład jeśli tylko korzystania z programu Entity Framework i jednostek lub nawet agregacje, jeśli ma być efekty uboczne znacznej w przypadku użycia, te będą realizowane jako niejawne koncepcji w kodzie sprzężonego po coś się stało. Jednak jeśli właśnie widzisz ten kod może być niemożliwe kodu (ubocznym) jest częścią operacji głównego lub naprawdę jest efektem. Z drugiej strony w przypadku używania zdarzeń domeny sprawia, że pojęcie jawne i część powszechny języka. Na przykład w aplikacji eShopOnContainers tworzenie kolejność nie jest chodzi o kolejność; jego aktualizuje lub tworzy nabywców agregacji, na podstawie oryginalnego użytkownika, ponieważ użytkownik nie jest kupujący, dopóki jest zamówienia. Jeśli używasz zdarzenia domeny, można jawnie express tej zasady domeny, na podstawie języka powszechny zapewniana przez ekspertów domeny.

Zdarzenia domeny są nieco podobne do stylu komunikatów zdarzeń, z jedną istotną różnicą. Z rzeczywistych komunikatów usługi kolejkowania komunikatów, brokerzy komunikat albo usługi service bus przy użyciu AMPQ wiadomość jest zawsze wysyłane asynchronicznie i przekazywane między procesami i maszyny. Jest to przydatne w przypadku integrowania wielu kontekstów ograniczone, mikrousług lub nawet różnych aplikacji. Jednak ze zdarzeniami domeny, aby wywołać zdarzenie z operacji domeny, które są aktualnie uruchomione, ale ma wszystkie efekty uboczne w tej samej domenie.

Zdarzenia domeny i ich efekty uboczne (akcje po wyzwoleniu zarządzanych przez programy obsługi zdarzeń) powinien wystąpić niemal natychmiast, zwykle w procesie, a w tej samej domenie. W związku z tym zdarzenia domeny może być synchroniczna lub asynchroniczna. Zdarzenia integracji, zawsze należy jednak asynchronicznego.

## <a name="domain-events-versus-integration-events"></a>Zdarzenia domeny i zdarzeń integracji

Semantycznie, domeny i integracja z zdarzenia to samo: powiadomienia dotyczące coś, które wystąpiły po prostu. Jednak ich realizacji muszą się różnić. Zdarzenia domeny są tylko komunikatów wypchniętych do dyspozytora zdarzeń domeny, która może być zaimplementowany jako mediatora w pamięci na podstawie kontenera IoC lub innej metody.

Z drugiej strony celem zdarzeń integracji jest propagację zatwierdzone transakcje i aktualizacje podsystemów dodatkowe, czy są one innych mikrousług, ograniczone kontekstów lub nawet zewnętrznych aplikacji. W związku z tym powinien wystąpić tylko jeśli jednostka pomyślnie jest trwały, od momentu w wielu scenariuszach w przypadku niepowodzenia całą operację skutecznie nigdy nie wystąpiły.

Ponadto i jak już wspomniano, integracja zdarzenia musi być oparta na komunikacji asynchronicznej między wieloma mikrousług (innych ograniczonych kontekstach) lub nawet zewnętrznych systemów/aplikacji. W związku z tym interfejs magistrali zdarzenia musi niektórych infrastrukturę, która umożliwia między procesu i rozproszonych komunikacji między usługami potencjalnie zdalnego. Może opierać się na magistrali usługi komercyjnych, kolejek, udostępnionej bazy danych używane jako skrzynki pocztowej lub inne rozproszonych, a w idealnym przypadku push oparte na system obsługi wiadomości.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Zdarzenia domeny jako preferowany sposób, aby wyzwolić efekty uboczne w wielu wartości zagregowanych w tej samej domenie

Jeśli wykonywania polecenia związane z jednego wystąpienia agregacji wymaga dodatkową domenę reguł do uruchomienia na jeden lub więcej dodatkowych wartości zagregowanych powinien projektowania i wdrażania tych efekty uboczne, które będą wyzwalane przez zdarzenia domeny. Jak pokazano w rysunek 9-14 i jako jedną z najważniejszych zastosowań, zdarzenie domeny powinny być używane do zmiany stanu są propagowane na wiele wartości zagregowanych w ramach tego samego modelu domeny.

![](./media/image15.png)

**Rysunek 9-14**. Zdarzenia domeny, aby wymusić spójność wielu wartości zagregowanych w tej samej domenie

Na ilustracji, gdy użytkownik inicjuje kolejności OrderStarted domeny zdarzenie jest wyzwalane utworzenia obiektu nabywców w porządkowania mikrousługi, oparte na oryginalne informacje o użytkowniku z mikrousługi tożsamość (z informacji podanych w poleceniu CreateOrder). Zdarzenie w domenie jest generowany przez agregacji kolejności podczas jego tworzenia w pierwszej kolejności.

Alternatywnie można mieć głównego agregacji subskrybuje zdarzenia generowane przez członków jego agregacji (jednostek podrzędnych). Każdy obiekt podrzędny OrderItem można na przykład wywołaj zdarzenie, kiedy cenę jest wyższy niż określoną kwotę lub jest zbyt duża wartość elementu produktu. Łączny głównego można otrzymywać te zdarzenia i wykonywanie obliczeń globalnych lub agregacji.

Ważne jest, aby zrozumieć, oparty na zdarzeniach komunikacji nie jest zaimplementowana bezpośrednio z poziomu agregacji; należy wdrożyć procedury obsługi zdarzeń domeny. Obsługa zdarzeń domeny jest kwestią aplikacji. Warstwa modelu domeny tylko skoncentrować się logika domeny — nie aplikacji infrastruktury, takich jak programy obsługi i trwałości efekt uboczny akcji przy użyciu repozytoriów, rzeczy, które ekspert domeny czy zrozumieć. W związku z tym na poziomie warstwy aplikacji jest, gdzie powinien mieć obsługi zdarzeń domeny wyzwalają akcje w przypadku zdarzenia domeny.

Zdarzenia domeny można także służyć do wyzwolenia dowolną liczbę akcji aplikacji, a co to jest ważniejsze, musi być otwarty, aby zwiększyć w przyszłości tego numeru w sposób rozdzielonymi. Na przykład po uruchomieniu kolejności, można opublikować zdarzenie w domenie Propaguj tej informacji do innych wartości zagregowanych, a nawet podnieść akcji aplikacji, takich jak powiadomienia.

Punkt klucza jest otwarte liczbę akcji do wykonania po wystąpieniu zdarzenia domeny. Po pewnym czasie działania i zasad w domenie i aplikacja będzie rosnąć. Złożoność lub liczbę akcji efekt uboczny, gdy wydarzy się coś wzrośnie, ale jeśli kodu zostały połączone z "sklejki" (oznacza to po prostu Tworzenie wystąpień obiektów z słowo kluczowe "new" w języku C\#), a następnie za każdym razem, gdy trzeba było dodać nową akcję należy Zmień oryginalnego kodu. Może to spowodować nowych usterek, ponieważ z każdym nowe wymaganie trzeba zmienić oryginalnego przepływu kodu. Taka strategia przed [zasady Open/zamknięty](https://en.wikipedia.org/wiki/Open/closed_principle) z [stałe](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). Nie tylko że, oryginalnej klasy, która została organizowanie operacje czy wzrostu i rozwoju, który znajduje się przed [jednej zasady odpowiedzialność (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Z drugiej strony użycie zdarzeń domeny, można utworzyć szczegółowych i rozdzielonymi wdrożenia przez umieszczenie odpowiedzialności za pomocą tej metody:

1.  Wyślij polecenie (na przykład CreateOrder).
2.  Odbierać polecenia programu obsługi poleceń.
    -   Wykonaj transakcję pojedynczego agregacji.
    -   (Opcjonalnie) Wywoływanie zdarzeń domeny dla efekty uboczne (na przykład OrderStartedDomainEvent).
1.  Obsługi zdarzeń domeny (w ramach bieżącego procesu) wykona Otwórz liczba efekty uboczne w wielu wartości zagregowanych lub działania aplikacji. Na przykład:
    -   Sprawdź lub utwórz metody nabywców i płatności.
    -   Tworzenie i wysyłanie zdarzeń powiązanych integracji magistrali zdarzeń do stanów są propagowane na mikrousług lub wyzwalacza zewnętrznego akcji, takich jak wysyłanie wiadomości e-mail kupującemu.
    -   Obsługa inne efekty uboczne.

Jak pokazano w rysunek 9-15, począwszy od tego samego zdarzenia domeny można obsługiwać wielu akcji związanych z innych wartości zagregowanych w domenie lub aplikacji dodatkowe czynności, które należy wykonać w mikrousług nawiązywania połączenia z zdarzeń integracji i bus zdarzeń.

![](./media/image16.png)

**Rysunek 9 – 15**. Obsługa wielu akcji dla domeny

Programy obsługi zdarzeń są zwykle w warstwie aplikacji, ponieważ korzystasz z obiektów infrastruktury, takich jak repozytoria lub aplikacji interfejsu API dla zachowania mikrousługi. W tym sensie procedury obsługi zdarzeń są podobne do programy obsługi poleceń, więc obie należą do warstwy aplikacji. Istotną różnicą jest to, że polecenie powinny być przetwarzane tylko raz. Zdarzenie domeny mogą być przetwarzane zero lub *n* razy, ponieważ może zostać odebrany przez wiele odbiorników lub programów obsługi zdarzeń z różnych cel każdy program obsługi.

Możliwość Otwórz liczby programów obsługi na zdarzenie domeny umożliwia dodanie dużo więcej reguł domeny bez wpływu na bieżącego kodu. Na przykład Implementowanie następujące reguły biznesowej, który ma mieć miejsce prawo po zdarzeniu może być tak proste, jak dodać kilka programów obsługi zdarzeń (lub nawet co najmniej jeden):

Suma zakupione w sklepie na dowolną liczbę zamówień, przekroczenia $6000 dotyczą 10% od rabat co nową kolejność i powiadomić klienta o wiadomość e-mail o tym rabatów dla przyszłych zleceń.

## <a name="implementing-domain-events"></a>Implementowanie zdarzeń domeny

W języku C# zdarzenie w domenie jest po prostu używane do przechowywania danych struktury lub klasy, jak DTO, wszystkie informacje związane z naturę tylko w domenie, jak pokazano w poniższym przykładzie:

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

Jest to zasadniczo klasę, która przechowuje wszystkie dane dotyczące zdarzeń OrderStarted.

W języku powszechny domeny ponieważ zdarzenie jest to przypada w przeszłości, nazwa klasy zdarzenia powinny być reprezentowane jako przeszłego zlecenia, takie jak OrderStartedDomainEvent lub OrderShippedDomainEvent. To zdarzenie w domenie jest implementowania porządkowania mikrousługi w eShopOnContainers.

Jak wspomniano wcześniej, ważną cechą zdarzenia jest to, że zdarzenie jest coś, które wystąpiły w przeszłości, nie należy zmieniać. W związku z tym musi być klasą niezmienialny. Widać w poprzednim kodzie, którego właściwości są tylko do odczytu z poza obiekt. Za pomocą konstruktora jest jedynym sposobem, aby zaktualizować obiekt, podczas tworzenia obiektu zdarzenia.

### <a name="raising-domain-events"></a>Wywoływanie zdarzeń domeny

Następne pytanie jest jak wywoływanie zdarzeń domeny dzięki osiągnie jego programy obsługi zdarzeń powiązanych. Można użyć kilku metod.

Proponowana pierwotnie Udi Dahan (na przykład w kilku związanych z wpisów, takich jak [zdarzenia domeny — potrwać 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) do zarządzania i wywoływanie zdarzeń przy użyciu klasy statycznej. Może to być klasy statycznej o nazwie DomainEvents, który może wywoływać zdarzeń domeny natychmiast, gdy jest wywoływana, przy użyciu składni, takich jak DomainEvents.Raise (Event myEvent). Jimmy Bogard zapisano w blogu ([wzmocnienia domenę: zdarzenia domeny](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) zaleca się podejście podobne.

Jednak w przypadku statycznej klasy zdarzenia domeny również wywołuje do obsługi natychmiast. To utrudnia testowania i debugowania, ponieważ programy obsługi zdarzeń z logiką efekty uboczne są wykonywane bezpośrednio po wywołaniu zdarzenia. Podczas testowania i debugowania, chcesz skupić się na i po prostu co dzieje się w bieżącej klasy agregacji; Czy chcesz nagle przekierowanie do innych programów obsługi zdarzeń dla efektów ubocznych dotyczących innych wartości zagregowanych lub logiki aplikacji. Dlatego właśnie usprawnionych inne podejścia, zgodnie z objaśnieniem w następnej sekcji.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>Odroczone podejście do podnoszenia i wywoływanie zdarzeń

Zamiast wysyłania do obsługi zdarzeń domeny natychmiast, lepszym rozwiązaniem jest dodanie zdarzenia domeny do kolekcji, a następnie wysłać te zdarzenia domeny *bezpośrednio poprzedzający* lub *prawo*  *Po* zatwierdzania transakcji (podobnie jak w przypadku metody SaveChanges w EF). (To rozwiązanie zostało opisanego przez Jimmy Bogard w tym wpisie [lepsze wzorzec zdarzenia domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Po wysłaniu zdarzenia domeny prawo przed lub po prawej stronie po zatwierdzania transakcji jest zazwyczaj ważne, ponieważ określa, czy będzie zawierać efekty uboczne w ramach tej samej transakcji lub w innej transakcji. W drugim przypadku należy uwzględniać spójność ostateczna między wiele wartości zagregowanych. W tym temacie omówiono w następnej sekcji.

Odroczone podejście jest, jakie eShopOnContainers używa. Najpierw należy dodać zdarzenia wykonywane w jednostki w kolekcji lub listę zdarzeń na jednostkę. Tę listę powinny być obiektu jednostki, nawet lepiej części lub klasy podstawowej jednostki, jak pokazano w poniższym przykładzie klasa podstawowa jednostka:

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
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

Jeśli chcesz zgłosić zdarzenie, możesz po prostu dodaj go do zbierania zdarzeń z kodu w dowolnej metody jednostki głównego agregacji.

Poniższy kod, część [kolejność głównego agregacji w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), przedstawiono przykład:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Zwróć uwagę, że jedynym elementem, który wykonuje metodę AddDomainEvent jest dodawanie zdarzenia do listy. Zdarzenie nie jest jeszcze wysłane i bez obsługi zdarzeń jest wywoływany jeszcze.

Konieczne jest wysłanie zdarzenia później podczas zatwierdzania transakcji do bazy danych. Jeśli korzystasz z programu Entity Framework Core, oznacza to metody SaveChanges Twojej DbContext EF, zgodnie z poniższym kodem:

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
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

O tym kodzie są wysyłania zdarzeń jednostki do ich odpowiednich procedur obsługi.

Wynik ogólny jest, że użytkownik ma całkowicie niezależna wywoływanie zdarzenia domeny (prosty, Dodaj do listy w pamięci) od wysyła go do programu obsługi zdarzeń. Ponadto w zależności od tego, jakiego rodzaju dyspozytora używasz, możesz można wysyłania zdarzeń synchronicznie lub asynchronicznie.

Należy pamiętać, tutaj odtwarzania transakcyjne granice wchodzą w znaczący. Jeśli urządzenia w pracy i transakcja może obejmować więcej niż jeden agregacji (jak w przypadku EF Core i relacyjnej bazy danych), to również działać. Jednak jeśli transakcja nie może obejmować agregacje, takie jak w przypadku używania bazą danych NoSQL, takie jak usługi Azure DocumentDB, musisz zaimplementować dodatkowe kroki w celu osiągnięcia spójności. Jest to kolejny powód, dlaczego nieznajomości trwałości nie jest uniwersalny; To zależy od używanego systemu magazynowania.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Pojedynczej transakcji przez wartości zagregowanych i spójność ostateczna między agregacji

Pytanie, czy ma być przeprowadzane pojedynczej transakcji przez wartości zagregowanych i zależne spójność ostateczna w tych agregacji jest kontrowersyjna. Wielu autorów DDD jak Evans marek i Vaughn Vernon wspierają reguły tego jedna transakcja = co agregacji i w związku z tym argumentowało za spójność ostateczna między agregacji. Na przykład w jego książce *projekt Domain-Driven*, marek Evans mówi, że:

Reguły obejmującej agreguje zostanie nie powinny być aktualne przez cały czas. Za pomocą przetwarzania zdarzeń, przetwarzanie wsadowe lub innych mechanizmów aktualizacji innych zależności można rozpoznawać w niektórych określony czas. (strona 128)

Vaughn Vernon mówi następujące opcje w [efektywnym projektowaniu agregacji. Część II: Tworzenie agreguje pracy ze sobą](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

W związku z tym, jeśli na jednym agregacji wystąpienia wymaga, że dodatkowe reguły biznesowe są wykonywane na jeden lub więcej wartości zagregowanych wykonywania polecenia użyj spójność ostateczna \[...\] Brak praktycznym sposobem obsługi spójność ostateczna DDD modelu. Metoda agregacji publikuje zdarzenie domeny, które jest w określonym momencie dostarczone do co najmniej jeden subskrybentów asynchronicznego.

Ta decyzja została oparta na obejmującego szczegółowe transakcji zamiast transakcjach obejmujących wiele wartości zagregowanych lub jednostek. Pomysł jest, że w drugim przypadku liczbę blokad bazy danych zostaną istotne w aplikacji na dużą skalę o potrzebach wysoką skalowalność. Korzystają z faktu, że wysokiej skalowalne aplikacje wymagają ma błyskawicznych spójności transakcyjnej między Agreguje wiele ułatwia akceptowanie pojęcie spójność ostateczna. Zmiany Atomic często nie są wymagane przez firmę, a w każdym przypadku jest odpowiedzialny za ekspertów domeny znaczy czy określonych operacji wymagają atomic transakcji. Jeśli operacja zawsze musi atomic transakcji między wiele wartości zagregowanych, może poprosić o czy Twoje agregacji powinna być większa lub nie została poprawnie zaprojektowana.

Jednak inne deweloperzy i architektów, takich jak Jimmy Bogard są zgadzasz się na spanning pojedynczej transakcji między kilka wartości zagregowanych —, ale tylko, gdy te dodatkowe wartości zagregowane są związane z efekty uboczne dla tego samego polecenia oryginalnego. Na przykład w [lepsze wzorzec zdarzenia domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard mówi, że:

Zwykle ma efekty uboczne zdarzenia domeny występuje w ramach tej samej logicznej transakcji, ale niekoniecznie w tym samym zakresie wywołaniem zdarzenia domeny \[...\] Tuż przed możemy zatwierdzić naszych transakcji, możemy wysyłania naszych zdarzenia do ich odpowiednich programów obsługi.

Jeśli wysyłania prawo zdarzenia domeny *przed* zatwierdzania oryginalnej transakcji, oznacza to, że ma efekty uboczne tych zdarzeń, które mają zostać uwzględnione w tej samej transakcji. Na przykład w przypadku niepowodzenia metody EF DbContext SaveChanges transakcji cofnie wszystkie zmiany, w tym wynik żadnych operacji ubocznym implementowane przez programy obsługi zdarzeń powiązanych domeny. To jest ponieważ zakres życia DbContext jest domyślnie zdefiniowany jako "zakresu." W związku z tym obiektu DbContext jest współużytkowany przez wiele obiektów repozytorium uruchamianiu w tym samym zakresie lub wykres obiektu. Pokrywa się to z zakresem HttpRequest podczas opracowywania aplikacji interfejsu API sieci Web lub MVC.

W rzeczywistości obu podejść (pojedynczej Atomowej transakcji i spójność ostateczna) może być prawo. To naprawdę zależy wymagań domeny lub biznesowych i co ekspertów domeny informujące. Także od tego, jak skalowalne potrzebna usługa można (bardziej szczegółowego transakcje wpływają mniej względem blokady bazy danych). I zależy on ile inwestycji podejmowanie dokonanie w kodzie, ponieważ spójność ostateczna wymaga bardziej złożonego kodu w celu wykrycia możliwych niespójności między wartości zagregowanych i trzeba zaimplementować wyrównawczych akcje. Wziąć pod uwagę, że jeśli można przekazać zmian do oryginalnego agregacji i później, gdy są wysyłane zdarzenia istnieje problem i obsługi zdarzeń nie może zatwierdzić ich efekty uboczne, trzeba będzie niespójności między wartości zagregowanych.

Sposób wyrównawczych akcji zezwalania byłoby przechowywania zdarzeń domeny w tabelach z dodatkowej bazy danych, tak aby były częścią oryginalnej transakcji. Później można mieć przetwarzania wsadowego, która wykrywa niespójności i wyrównawczych akcje uruchamiane przez porównanie listę zdarzeń z bieżącym stanem agregacji. Wyrównawczych akcje są częścią złożonych temat, który będzie wymagać szczegółowa analiza z Twojej strony, w tym dyskutować go z biznesowych użytkownika i domena ekspertów.

W każdym przypadku można podejście, które są potrzebne. Ale początkowej odroczone podejście — wywoływanie zdarzeń przed zatwierdzeniem, więc należy używaj jednej transakcji — jest najprostsza metoda, korzystając z EF Core i relacyjnej bazy danych. Jest łatwiejsze do wdrożenia i prawidłowy w wielu przypadkach biznesowych. Jest również używane w porządkowania mikrousługi w eShopOnContainers podejście.

Jednak jak zostanie faktycznie wysyłania tych zdarzeń do ich odpowiednich procedur obsługi? Co to jest \_mediatora obiekt, który zostanie wyświetlony w poprzednim przykładzie? Musi wykonać za pomocą techniki i artefakty, który służy do mapowania zdarzeń i ich obsługi zdarzeń.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dyspozytor zdarzeń domeny: mapowanie ze zdarzeń do obsługi zdarzeń

Po będziesz mieć możliwość wysyłania lub opublikować zdarzenia, należy niektórych rodzaj artefaktu, która będzie publikować zdarzenia, dzięki czemu co obsługi pokrewne można pobrać go i przetwarzanie efekty uboczne, na podstawie tego zdarzenia.

Jednym z podejść jest rzeczywistym komunikatów systemu lub nawet zdarzeń magistrali, najlepiej jest oparta na magistrali usług, w przeciwieństwie do zdarzeń w pamięci. Jednakże w pierwszym przypadku rzeczywistych wiadomości może być zbyt obszerne w przypadku przetwarzania zdarzeń domeny, ponieważ wystarczy do przetwarzania tych zdarzeń w ramach tego samego procesu (to znaczy w ramach tej samej warstwie domeny i aplikacji).

Innym sposobem mapowania zdarzeń na wielu obsług zdarzeń jest za pomocą rejestracji typów w kontenerze Inwersja kontroli, dzięki czemu można dynamicznie wnioskować where do wysyłania zdarzeń. Innymi słowy musisz wiedzieć, co potrzebne do pobrania określonego zdarzenia procedury obsługi zdarzeń. Rysunek 9 – 16 zawiera uproszczone podejście do tego.

![](./media/image17.png)

**Rysunek 9 – 16**. Dyspozytor zdarzeń domeny przy użyciu Inwersja kontroli

Można tworzyć wszystkie żmudne procesy i artefakty do wdrożenia tego podejścia samodzielnie. Jednak można także używać dostępnych bibliotek, takich jak [MediatR](https://github.com/jbogard/MediatR), który poniżej obejmuje korzysta z kontenera IoC. W związku z tym bezpośrednio można wstępnie zdefiniowanych interfejsów i metod publikowania wysyłania obiektu mediatora.

W kodzie, najpierw należy zarejestrować typy programów obsługi zdarzeń w Twojej kontenera IoC, jak pokazano w poniższym przykładzie w [eShopOnContainers mikrousługi porządkowanie](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kod najpierw identyfikuje zestaw zawierający obsługi zdarzeń domeny dzięki umieszczeniu zestawu, który zawiera wszelkie obsługi (przy użyciu typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale może wybrano inne obsługi zdarzeń, które można zlokalizować zestawu). Ponieważ obsługi zdarzeń implementować interfejs IAsyncNotificationHandler, kod, a następnie wyszukiwanie tylko dla tych typów i rejestruje obsługi zdarzeń.

### <a name="how-to-subscribe-to-domain-events"></a>Subskrybowanie zdarzeń domeny

W przypadku użycia MediatR, każdy program obsługi zdarzeń musi użyć typ zdarzenia, który znajduje się na parametrze ogólnym interfejsu INotificationHandler, jak widać w poniższym kodzie:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na podstawie relacji między zdarzeń i program obsługi zdarzeń, które mogą zostać uwzględnione subskrypcji, artefaktu MediatR mogą odnaleźć obsługi zdarzeń dla każdego zdarzenia i wyzwolić każdego z tych programów obsługi zdarzeń.

### <a name="how-to-handle-domain-events"></a>Sposób obsługi zdarzeń domeny

Na koniec programu obsługi zdarzeń zwykle implementuje kod warstwy aplikacji, który używa repozytoria infrastruktury, aby uzyskać wymagane dodatkowe wartości zagregowanych i wykonywanie logiki efekt uboczny domeny. Następujące [kod obsługi zdarzenia domeny na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), przedstawiono przykład implementacji.

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

Poprzedni kod obsługi zdarzenia domeny jest uznawany za kod warstwy aplikacji, ponieważ używa repozytoria infrastruktury zgodnie z opisem w następnej sekcji na warstwie infrastrukturze trwałości. Programy obsługi zdarzeń można również użyć innych składników infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Zdarzenia domeny może wygenerować zdarzeń integracji publikowane poza granice mikrousługi

Na koniec należy podać, że czasami warto zdarzenia są propagowane na wiele mikrousług. Która jest traktowana jako zdarzenie integracji i mogą być publikowane za pośrednictwem magistrali zdarzeń z obsługi zdarzeń dowolnej określonej domeny.

## <a name="conclusions-on-domain-events"></a>Wnioski dotyczące zdarzeń domeny

Jak już wspomniano, należy użyć domeny zdarzeń w celu jawne Implementowanie skutków ubocznych zmiany w swojej domenie. Aby użyć terminologii DDD, za pomocą zdarzeń domeny jawne Implementowanie skutków ubocznych przez jednego lub wielu wartości zagregowanych. Ponadto i lepszą skalowalność i mniej wpływ na blokady bazy danych użyj spójność ostateczna między zagregowanych zakresu umieszczonych w tej samej domenie.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Małych Gregowi. Co to jest zdarzenie domeny?**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Zdarzenia domeny i spójność ostateczna**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Lepsze wzorzec zdarzenia domeny**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Efektywnym projektowaniu agregacji część II: Tworzenie wartości zagregowanych współpracują**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Wzmocnienie domenę: zdarzenia domeny**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *

-   **Tony Truong. Przykład wzorca zdarzenia domeny**
    [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan. Jak utworzyć pełni hermetyzowany modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan. Zdarzenia domeny — potrwać 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan. Zdarzenia domeny — Salvation**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Nie Publikuj zdarzenia domeny, zwraca je!**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Torre de la Cesarowi. Vs zdarzenia domeny. Integracja zdarzeń w DDD i mikrousług architektury**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Previous] (client-side-validation.md) [Next] (infrastructure-persistence-layer-design.md)
