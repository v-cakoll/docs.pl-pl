---
title: Zdarzenia domeny. Projektowanie i implementacja
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Uzyskaj szczegółowy widok zdarzeń domeny, kluczową koncepcję do ustanowienia komunikacji między agregacjami.
ms.date: 10/08/2018
ms.openlocfilehash: 4fe0c1fa04bbecb64783e070838ab796de4f90d6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031841"
---
# <a name="domain-events-design-and-implementation"></a>Zdarzenia w domenie: projektowanie i implementacja

Za pomocą zdarzeń domeny można jawnie zaimplementować efekty uboczne zmian w domenie. Innymi słowy i przy użyciu terminologii DDD należy używać zdarzeń domeny w celu jawnego implementowania efektów ubocznych w wielu agregacjach. Opcjonalnie, aby zapewnić lepszą skalowalność i mniej wpływ na blokady baz danych, należy użyć spójności ostatecznej między agregacjami w tej samej domenie.

## <a name="what-is-a-domain-event"></a>Co to jest zdarzenie domeny?

Zdarzenie to coś, co się stało w przeszłości. Zdarzenie domeny to, coś, co nastąpiło w domenie, aby inne części tej samej domeny (w procesie) były świadome. Przekazane części zazwyczaj reagują na zdarzenia.

Ważną zaletą zdarzeń domeny jest to, że efekty uboczne mogą być wyrażone jawnie.

Na przykład jeśli korzystasz tylko z Entity Framework, a musisz być odpowiedzią na niektóre zdarzenie, prawdopodobnie kod, którego potrzebujesz blisko, co spowoduje Wyzwalanie zdarzenia. W związku z tym reguła jest połączona, niejawnie do kodu i trzeba będzie przyjrzeć się do kodu, miejmy nadzieję, aby zrealizować regułę.

Z drugiej strony, korzystanie z zdarzeń domeny czyni koncepcję jawną, ponieważ występuje `DomainEvent` i co najmniej jeden `DomainEventHandler`.

Na przykład w aplikacji eShopOnContainers, gdy zamówienie zostanie utworzone, użytkownik zostaje kupujący, więc `OrderStartedDomainEvent` jest zgłaszane i obsługiwane w `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`, więc koncepcja bazowa jest oczywista.

W skrócie zdarzenia domeny pomagają w jawnym wykorzystaniu zasad domeny, w oparciu o język powszechny udostępniony przez ekspertów domeny. Zdarzenia domeny umożliwiają również lepsze rozdzielenie problemów między klasami w tej samej domenie.

Ważne jest, aby upewnić się, że podobnie jak transakcja bazy danych, wszystkie operacje związane ze zdarzeniem domeny zakończą się pomyślnie lub żadna z nich nie działa.

Zdarzenia domeny są podobne do zdarzeń w stylu obsługi komunikatów, z jedną istotną różnicą. W przypadku rzeczywistej obsługi komunikatów, usługi kolejkowania komunikatów, brokerów komunikatów lub usługi Service Bus przy użyciu AMQP komunikat jest zawsze wysyłany asynchronicznie i przekazywany przez procesy i maszyny. Jest to przydatne w przypadku integrowania wielu ograniczonych kontekstów, mikrousług lub nawet różnych aplikacji. Jednak ze zdarzeniami domeny, chcesz zgłosić zdarzenie z aktualnie działającej operacji domeny, ale chcesz, aby wszystkie efekty uboczne miały miejsce w tej samej domenie.

Zdarzenia domeny i ich skutki uboczne (akcje wyzwalane w późniejszym czasie, które są zarządzane przez programy obsługi zdarzeń) powinny wystąpić niemal natychmiast, zwykle w procesie i w tej samej domenie. W rezultacie zdarzenia domeny mogą być synchroniczne lub asynchroniczne. Zdarzenia integracji powinny jednak zawsze być asynchroniczne.

## <a name="domain-events-versus-integration-events"></a>Zdarzenia dotyczące domeny a zdarzenia integracji

Semantycznie zdarzenia dotyczące domeny i integracji są takie same: powiadomienia dotyczące coś, co się stało. Jednak ich implementacja musi się różnić. Zdarzenia domeny są po prostu przekazywane do dyspozytora zdarzeń domeny, który można zaimplementować jako mediator w pamięci na podstawie kontenera IoC lub innej metody.

Z drugiej strony, celem zdarzeń integracji jest propagowanie zatwierdzonych transakcji i aktualizacji do dodatkowych podsystemów, bez względu na to, czy są to inne mikrousługi, ograniczone konteksty, czy nawet aplikacje zewnętrzne. W związku z tym powinny wystąpić tylko wtedy, gdy jednostka została pomyślna utrwalana, w przeciwnym razie jest tak, jakby cała operacja nigdy nie zakończyła się.

Jak wspomniano wcześniej, zdarzenia integracji muszą opierać się na asynchronicznej komunikacji między wieloma mikrousługami (innymi kontekstami ograniczonymi) lub nawet z zewnętrznymi systemami/aplikacjami.

Z tego względu Interfejs magistrali zdarzeń musi mieć pewną infrastrukturę, która umożliwia międzyprocesową i rozproszoną komunikację między potencjalnie zdalnymi usługami. Może ona być oparta na komercyjnej magistrali usług, kolejkach, udostępnionej bazie danych używanej jako Skrzynka pocztowa lub w dowolnym innym rozproszonym i idealnym systemie dostarczania komunikatów opartych na wypychaniu.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Zdarzenia domeny jako preferowany sposób wyzwalania efektów ubocznych przez wiele agregacji w tej samej domenie

Jeśli wykonanie polecenia związanego z jednym wystąpieniem zagregowanym wymaga uruchomienia dodatkowych reguł domeny w jednej lub większej liczbie dodatkowych agregacji, należy zaprojektować i zaimplementować te efekty uboczne, aby były wyzwalane przez zdarzenia domeny. Jak pokazano na rysunku 7-14 i jako jeden z najważniejszych przypadków użycia, zdarzenie domeny powinno być używane do propagowania zmian stanu w wielu agregacjach w ramach tego samego modelu domeny.

![Spójność między agregacjami jest osiągana przez zdarzenia domeny, zagregowana kolejność wysyła zdarzenie domeny OrderStarted, które jest obsługiwane w celu zaktualizowania agregacji nabywcy. ](./media/image15.png)

**Rysunek 7-14**. Zdarzenia domeny w celu wymuszenia spójności między wieloma agregacjami w tej samej domenie

Na rysunku, gdy użytkownik inicjuje zamówienie, zdarzenie domeny OrderStarted wyzwala Tworzenie obiektu kupca w mikrousłudze porządkowania, na podstawie oryginalnych informacji o użytkowniku z mikrousługi tożsamości (z informacjami podanymi w poleceniu "Utwórz zamówienie"). Zdarzenie domeny jest generowane przez agregację zamówienia, gdy jest tworzona w pierwszym miejscu.

Alternatywnie można mieć zagregowany katalog główny subskrybowany dla zdarzeń wywoływanych przez elementy członkowskie jego agregacji (jednostki podrzędne). Na przykład każda jednostka podrzędna OrderItem może zgłosić zdarzenie, gdy cena elementu jest wyższa niż określona kwota lub gdy ilość elementu produktu jest zbyt wysoka. Zagregowany element główny może następnie odbierać te zdarzenia i wykonywać globalne obliczenia lub agregację.

Ważne jest, aby zrozumieć, że ta komunikacja oparta na zdarzeniach nie została zaimplementowana bezpośrednio w ramach agregacji; należy zaimplementować obsługę zdarzeń domeny.

Obsługa zdarzeń domeny jest problemem aplikacji. Warstwa modelu domeny powinna skupiać się tylko na logice domeny, co jest zrozumiałe dla eksperta domeny, a nie infrastruktury aplikacji, takiej jak programy obsługi i akcje trwałości ubocznej przy użyciu repozytoriów. W związku z tym poziom warstwy aplikacji to miejsce, w którym należy wykonać procedury obsługi zdarzeń domeny wyzwalające akcje po podniesieniu zdarzenia domeny.

Zdarzenia domeny mogą również służyć do wyzwalania dowolnej liczby akcji aplikacji i co ważniejsze, muszą być otwarte, aby zwiększyć tę liczbę w przyszłości w niezależny sposób. Na przykład po rozpoczęciu zamówienia można opublikować zdarzenie domeny, aby propagować te informacje do innych agregacji, a nawet wywołać akcje aplikacji, takie jak powiadomienia.

Punkt klucza to otwarta liczba akcji do wykonania w przypadku wystąpienia zdarzenia domeny. Ostatecznie akcje i reguły w domenie i aplikacji zostaną rozrastane. Złożoność lub liczba akcji związanych z efektem ubocznym, gdy wystąpi coś, ale jeśli kod został połączony z "klejem" (czyli tworzeniem określonych obiektów z `new`), a następnie za każdym razem, gdy trzeba dodać nową akcję, należy również zmienić pracę i kod przetestowany.

Ta zmiana może spowodować nowe błędy, a podejście to również odnosi się do [zasady otwarte/zamknięte](https://en.wikipedia.org/wiki/Open/closed_principle) z [pełnych](https://en.wikipedia.org/wiki/SOLID). Nie tylko, Oryginalna klasa, która była w trakcie organizowania operacji, rośnie i rośnie, która jest zgodna z [pojedynczą zasadą odpowiedzialności (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Z drugiej strony, jeśli używasz zdarzeń domeny, możesz utworzyć szczegółową i rozłączoną implementację, segregowając obowiązki przy użyciu tej metody:

1. Wyślij polecenie (na przykład Zamów).
2. Odbierz polecenie w programie obsługi poleceń.
   - Wykonaj pojedynczą transakcję agregacji.
   - Obowiązkowe Podnieś zdarzenia domeny dla efektów ubocznych (na przykład OrderStartedDomainEvent).
3. Obsługa zdarzeń domeny (w ramach bieżącego procesu), które będą wykonywały otwartą liczbę efektów ubocznych w wielu agregacjach lub akcjach aplikacji. Na przykład:
   - Zweryfikuj lub Utwórz kupującego i metodę płatności.
   - Tworzenie i wysyłanie powiązanego zdarzenia integracji do usługi Event Bus w celu propagowania Stanów dla mikrousług lub wyzwalania akcji zewnętrznych, takich jak wysyłanie wiadomości e-mail do kupującego.
   - Obsługuj inne efekty uboczne.

Jak pokazano na rysunku 7-15, rozpoczynając od tego samego zdarzenia domeny, można obsługiwać wiele akcji związanych z innymi agregacjami w domenie lub dodatkowych akcjach aplikacji, które należy wykonać na mikrousługach łączących się ze zdarzeniami integracji i magistralą zdarzeń.

![Może istnieć kilka programów obsługi dla tego samego zdarzenia domeny w warstwie aplikacji, jednak jedna procedura obsługi może rozwiązać spójność między agregacjami, a inna procedura obsługi może opublikować wydarzenie integracji, dzięki czemu inne mikrousługi mogą wykonać coś z nim.](./media/image16.png)

**Rysunek 7-15**. Obsługa wielu akcji na domenę

Programy obsługi zdarzeń zwykle znajdują się w warstwie aplikacji, ponieważ będziesz używać obiektów infrastruktury, takich jak repozytoria lub interfejs API aplikacji dla zachowania mikrousługi. W tym sensie programy obsługi zdarzeń są podobne do programów obsługi poleceń, więc obie są częścią warstwy aplikacji. Istotną różnicą jest to, że polecenie powinno być przetwarzane tylko raz. Zdarzenie domeny może być przetwarzane zero lub *n* razy, ponieważ może zostać odebrane przez wielu odbiorników lub obsługę zdarzeń z innym przeznaczeniem dla każdej procedury obsługi.

Posiadanie otwartej liczby programów obsługi na domenę umożliwia dodanie możliwie największej liczby reguł domeny bez wpływu na bieżący kod. Na przykład wdrożenie następującej reguły biznesowej może być równie proste, jak dodanie kilku programów obsługi zdarzeń (lub nawet jednego z nich):

> Gdy łączna kwota zakupiona przez klienta w sklepie w ramach dowolnej liczby zamówień przekracza $6 000, należy zastosować 10% rabatu na każde nowe zamówienie i powiadomić klienta za pośrednictwem wiadomości e-mail o tym rabatie dla przyszłych zamówień.

## <a name="implement-domain-events"></a>Implementowanie zdarzeń domeny

W C#programie zdarzenie domeny jest po prostu strukturą lub klasą przechowywania danych, taką jak DTO, ze wszystkimi informacjami związanymi z tym, co się stało w domenie, jak pokazano w następującym przykładzie:

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

Jest to zasadniczo Klasa, która zawiera wszystkie dane związane ze zdarzeniem OrderStarted.

W odniesieniu do powszechnie używanego języka domeny, ponieważ zdarzenie to coś, co miało miejsce w przeszłości, nazwa klasy zdarzenia powinna być reprezentowana jako czasownik przeszły, taki jak OrderStartedDomainEvent lub OrderShippedDomainEvent. Jest to sposób implementacji zdarzenia domeny w mikrousłudze porządkowania w eShopOnContainers.

Jak wspomniano wcześniej, ważną cechą zdarzeń jest fakt, że zdarzenie to coś, co miało miejsce w przeszłości, nie powinno się zmieniać. W związku z tym musi być klasą niemodyfikowalną. W poprzednim kodzie można zobaczyć, że właściwości są tylko do odczytu. Nie ma sposobu na zaktualizowanie obiektu, można ustawić tylko wartości podczas jego tworzenia.

Należy tu zaznaczyć, że jeśli zdarzenia domeny mają być obsługiwane asynchronicznie, przy użyciu kolejki, która wymaga serializacji i deserializacji obiektów zdarzeń, właściwości muszą mieć wartość "Prywatny zestaw" zamiast tylko do odczytu, więc Deserializator będzie Możliwość przypisywania wartości podczas usuwania z kolejki. Nie jest to problem występujący w mikrousłudze porządkowania, ponieważ zdarzenie w domenie pub/sub jest zaimplementowane synchronicznie za pomocą MediatR.

### <a name="raise-domain-events"></a>Zgłoś zdarzenia domeny

Następnym pytaniem jest to, jak podnieść zdarzenie domeny, aby docierał do jego powiązanych programów obsługi zdarzeń. Można użyć wielu metod.

UDI Dahan pierwotnie proponowane (na przykład w kilku powiązanych wpisach, takich jak [zdarzenia domeny — Zrób 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) przy użyciu klasy statycznej do zarządzania i wywoływania zdarzeń. Może to obejmować klasę statyczną o nazwie DomainEvents, która mogłaby podnieść zdarzenia domeny natychmiast po wywołaniu, używając składni takiej jak `DomainEvents.Raise(Event myEvent)`. Jimmy Bogard zapisał wpis w blogu ([wzmacnianie domeny: zdarzenia domeny](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)), która zaleca podobne podejście.

Jednak gdy klasa zdarzenia domeny jest statyczna, to również natychmiast wysyła do programów obsługi. Dzięki temu testy i debugowanie są trudniejsze, ponieważ programy obsługi zdarzeń z logiką efektów ubocznych są wykonywane natychmiast po wywołaniu zdarzenia. Podczas testowania i debugowania należy skoncentrować się na tym, co dzieje się w przypadku bieżących klas agregujących; nie chcesz nagle przekierowywać do innych programów obsługi zdarzeń w przypadku efektów ubocznych związanych z innymi agregacjami lub logiką aplikacji. Jest to dlatego, że inne podejścia zostały rozwinięte, jak wyjaśniono w następnej sekcji.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odroczone podejście do wywoływania i wysyłania zdarzeń

Zamiast wysyłać do programu obsługi zdarzeń domeny natychmiast, lepszym rozwiązaniem jest dodanie zdarzeń domeny do kolekcji, a następnie wysłanie tych zdarzeń domeny *bezpośrednio przed* *lub po* *zatwierdzeniu* transakcji (jak w przypadku Metody SaveChanges w EF). (Takie podejście zostało opisane przez Jimmy Bogard w tym wpisie [lepszego wzorca zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)).

Wybór w przypadku wysyłania zdarzeń domeny bezpośrednio przed lub po zatwierdzeniu transakcji jest istotny, ponieważ określa, czy będzie uwzględniać efekty uboczne w ramach tej samej transakcji lub w różnych transakcjach. W tym drugim przypadku należy zaradzić sobie ze spójnością ostateczną w wielu agregacjach. Ten temat został omówiony w następnej sekcji.

Podejście odroczone to eShopOnContainers, z których korzystają. Najpierw Dodaj zdarzenia wykonywane w jednostkach do kolekcji lub listy zdarzeń na jednostkę. Ta lista powinna być częścią obiektu jednostki, a nawet lepiej, częścią klasy jednostki podstawowej, jak pokazano w poniższym przykładzie klasy podstawowej jednostki:

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

Gdy chcesz zgłosić zdarzenie, wystarczy dodać je do kolekcji zdarzeń z kodu w dowolnej metodzie agregacji jednostki głównej.

Poniższy kod, część [agregacji Order-root w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), zawiera przykład:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Należy zauważyć, że jedyną kwestią, że metoda AddDomainEvent jest dodawana do listy zdarzenia. Żadne zdarzenie nie jest jeszcze wysyłane i nie wywołano jeszcze obsługi zdarzeń.

Na pewno chcesz wysłać zdarzenia później, po zatwierdzeniu transakcji do bazy danych. Jeśli używasz Entity Framework Core, oznacza to w metodzie metody SaveChanges w kontekście EF DB, jak w poniższym kodzie:

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

Za pomocą tego kodu wysyłasz zdarzenia jednostki do odpowiednich programów obsługi zdarzeń.

Ogólny wynik polega na tym, że zostało oddzielone podnoszenie poziomu zdarzenia domeny (proste dodanie do listy w pamięci) od wysłania go do programu obsługi zdarzeń. Ponadto, w zależności od używanego rodzaju dyspozytora, można wysyłać zdarzenia synchronicznie lub asynchronicznie.

Należy pamiętać, że granice transakcyjne są znacznie dostępne w tym miejscu. Jeśli jednostka pracy i transakcji może obejmować więcej niż jedną wartość zagregowaną (jak w przypadku używania EF Core i relacyjnej bazy danych), może to być dobre. Ale jeśli transakcja nie może obejmować agregacji, na przykład gdy korzystasz z bazy danych NoSQL, takiej jak Azure CosmosDB, musisz zaimplementować dodatkowe kroki, aby osiągnąć spójność. Jest to kolejny powód, dla którego trwałość ignorujących nie jest uniwersalna; jest to zależne od używanego systemu magazynu. 

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Pojedyncza transakcja w agregacjach i ostateczna spójność w agregacjach

Pytanie, czy wykonać pojedynczą transakcję w ramach agregacji, w przeciwieństwie do spójności ostatecznej dla tych agregacji jest kontrowersyjny. Wiele autorów, takich jak Eric Evans i Vaughn Vernon, ambasadoruje zasadę, że jedna transakcja = jedna wartość zagregowana i w związku z tym podnieśy się do ostatecznej spójności w agregacjach. Na przykład w swoim *projekcie opartym na domenie*, Eric Evans to:

> Wszystkie reguły, które rozciągają się na agregacje, nie będą zawsze aktualne. W przypadku przetwarzania zdarzeń, przetwarzania wsadowego lub innych mechanizmów aktualizacji inne zależności można rozpoznać w określonym czasie. (strona 128)

Vaughn Vernon jest następująca w [skutecznym, zagregowanym projekcie. Część II: wykonywanie zagregowanych zadań jednocześnie](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> W takim przypadku, jeśli wykonanie polecenia w jednym wystąpieniu agregującym wymaga, aby dodatkowe reguły biznesowe były wykonywane na co najmniej jednej agregacji, należy użyć spójności ostatecznej \[... \] istnieje praktyczny sposób zapewnienia spójności ostatecznej w modelu DDD. Metoda agregująca publikuje zdarzenie domeny, które jest w czasie dostarczane do co najmniej jednego subskrybenta asynchronicznego.

To uzasadnienie opiera się na uwzględnieniu szczegółowych transakcji zamiast transakcji obejmujących wiele zagregowanych lub jednostek. Dobrym pomysłem jest to, że w drugim przypadku liczba blokad baz danych będzie znacząca w aplikacjach o dużej skali o wysokiej skalowalności. W przypadku, gdy wysoce skalowalne aplikacje nie muszą mieć natychmiastowej spójności transakcyjnej między wieloma agregacjami, pomaga zaakceptować koncepcję spójności ostatecznej. Zmiany niepodzielne często nie są wymagane przez firmę, a w każdym przypadku odpowiedzialność ekspertów domeny może powiedzieć, czy określone operacje wymagają niepodzielnych transakcji. Jeśli operacja zawsze wymaga niepodzielnej transakcji między wieloma agregacjami, może wystąpić pytanie, czy wartość zagregowana powinna być większa czy nie została prawidłowo zaprojektowana.

Jednak inni deweloperzy i architekty, takie jak Jimmy Bogard, są w trakcie łączenia jednej transakcji z wieloma agregacjami, ale tylko wtedy, gdy te dodatkowe agregaty są powiązane z efektami ubocznymi tego samego oryginalnego polecenia. Przykładowo w przypadku [lepszego wzorca zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard brzmi:

> Zazwyczaj chcę, aby skutki uboczne zdarzenia domeny miały miejsce w ramach tej samej transakcji logicznej, ale niekoniecznie w tym samym zakresie do podniesienia poziomu zdarzenia domeny \[... \] przed zatwierdzeniem naszej transakcji, wysyłamy nasze zdarzenia do odpowiednich programy obsługi.

Jeśli wysyłasz zdarzenia domeny bezpośrednio *przed* zatwierdzeniem oryginalnej transakcji, jest to spowodowane tym, że efekty uboczne tych zdarzeń mają być uwzględnione w tej samej transakcji. Na przykład jeśli metoda EF DbContext metody SaveChanges nie powiedzie się, transakcja wycofa wszystkie zmiany, w tym wynik wszelkich operacji ubocznych wdrożonych przez powiązane procedury obsługi zdarzeń domeny. Wynika to z faktu, że zakres istnienia kontekstu DbContext jest domyślnie zdefiniowany jako "objęty zakresem". W związku z tym obiekt DbContext jest współużytkowany przez wiele obiektów repozytorium, które są tworzone w ramach tego samego zakresu lub grafu obiektów. Ta sama zbieżność z zakresem HttpRequest podczas opracowywania aplikacji sieci Web API lub MVC.

W rzeczywistości obie metody (jedna niepodzielna transakcja i spójność ostateczna) mogą być odpowiednie. Jest to naprawdę zależne od wymagań Twojej domeny lub firmy oraz informacji o tym, co informują eksperci z domeną. Zależy to również od tego, jak skalowalność potrzebuje usługi (bardziej szczegółowe transakcje mają mniejszy wpływ na blokady bazy danych). Jest to zależne od tego, jak dużo inwestycji leży w kodzie, ponieważ w celu wykrywania możliwych niespójności w ramach zagregowanych danych wymagana jest bardziej skomplikowana spójność i konieczna jest implementacja działań wyrównawczych. Należy wziąć pod uwagę, że jeśli zatwierdzisz zmiany w pierwotnej wartości zagregowanej, a następnie, gdy zdarzenia są wysyłane, jeśli wystąpi problem, a programy obsługi zdarzeń nie mogą zatwierdzić ich efektów ubocznych, będziesz mieć niespójności między agregacjami.

Sposobem zezwalania na akcje kompensacyjne będzie przechowywanie zdarzeń domeny w dodatkowych tabelach bazy danych, dzięki czemu mogą one być częścią oryginalnej transakcji. Później może istnieć proces wsadowy, który wykrywa niespójności i uruchamia akcje kompensacyjne, porównując listę zdarzeń z bieżącym stanem agregacji. Działania kompensacyjne są częścią złożonego tematu, który będzie wymagał głębokiej analizy ze strony użytkownika, która obejmuje omawianie jej z ekspertami użytkowników i domen dla firm.

W każdym przypadku można wybrać potrzebną metodę. Ale początkowe podejście odroczone — podnoszenie zdarzeń przed zatwierdzeniem, dlatego należy użyć jednej transakcji — najprostszym podejściem jest użycie EF Core i relacyjnej bazy danych. Jest to łatwiejsze do zaimplementowania i prawidłowego w wielu przypadkach firmy. Jest to również podejście używane w mikrousłudze porządkowania w eShopOnContainers.

Ale jak faktycznie wysyłać te zdarzenia do odpowiednich programów obsługi zdarzeń? Co to jest obiekt `_mediator` widoczny w poprzednim przykładzie? Należy to zrobić przy użyciu technik i artefaktów używanych do mapowania między zdarzeniami a ich programami obsługi zdarzeń.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dyspozytor zdarzeń domeny: mapowanie ze zdarzeń do programów obsługi zdarzeń

Gdy będzie możliwe wysłanie lub opublikowanie zdarzeń, potrzebujesz pewnego rodzaju artefaktu, który będzie publikować zdarzenie, dzięki czemu każda powiązana procedura obsługi może go uzyskać i przetwarzać efekty uboczne na podstawie tego zdarzenia.

Jednym z rozwiązań jest rzeczywisty system obsługi komunikatów, a nawet magistrala zdarzeń, prawdopodobnie oparta na magistrali usług, w przeciwieństwie do zdarzeń w pamięci. Jednak w przypadku pierwszego przypadku prawdziwe wiadomości zbyt obszerne do przetwarzania zdarzeń domeny, ponieważ wystarczy przetwarzać te zdarzenia w ramach tego samego procesu (czyli w obrębie tej samej domeny i warstwy aplikacji).

Innym sposobem mapowania zdarzeń do obsługi wielu zdarzeń jest użycie rejestracji typów w kontenerze IoC, dzięki czemu można dynamicznie wywnioskować, gdzie mają zostać wysłane zdarzenia. Innymi słowy, należy wiedzieć, jakie programy obsługi zdarzeń muszą uzyskać konkretne zdarzenie. Rysunek 7-16 pokazuje uproszczone podejście do tego podejścia.

![Iniekcja zależności może służyć do kojarzenia zdarzeń z obsługą zdarzeń, która jest podejściem używanym przez MediatR](./media/image17.png)

**Rysunek 7-16**. Dyspozytor zdarzeń domeny przy użyciu IoC

Możesz skompilować wszystkie instalacje i artefakty, aby zaimplementować to rozwiązanie samodzielnie. Można jednak również użyć dostępnych bibliotek, takich jak [MediatR](https://github.com/jbogard/MediatR) , które używają kontenera IOC w obszarze okładek. W związku z tym można bezpośrednio używać wstępnie zdefiniowanych interfejsów i metod publikowania/wysyłania obiektów mediator.

W kodzie należy najpierw zarejestrować typy obsługi zdarzeń w kontenerze IoC, jak pokazano w poniższym przykładzie w [EShopOnContainers porządkowanie mikrousługi](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kod najpierw identyfikuje zestaw, który zawiera procedury obsługi zdarzeń domeny przez lokalizowanie zestawu, który zawiera dowolne procedury obsługi (przy użyciu elementu typeof (ValidateOrAddBuyerAggregateWhenXxxx), ale można wybrać dowolną inną procedurę obsługi zdarzeń w celu zlokalizowania zestawu. Ponieważ wszystkie programy obsługi zdarzeń implementują interfejs IAsyncNotificationHandler, kod następnie wyszukuje te typy i rejestruje wszystkie programy obsługi zdarzeń.

### <a name="how-to-subscribe-to-domain-events"></a>Jak subskrybować zdarzenia domeny

W przypadku korzystania z MediatR, każdy program obsługi zdarzeń musi używać typu zdarzenia dostarczonego w parametrze ogólnym interfejsu INotificationHandler, jak widać w poniższym kodzie:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na podstawie relacji między zdarzeniem i obsługą zdarzeń, które mogą być uważane za subskrypcję, artefakt MediatR może odnaleźć wszystkie procedury obsługi zdarzeń dla każdego zdarzenia i wyzwolić każdy z tych programów obsługi zdarzeń.

### <a name="how-to-handle-domain-events"></a>Jak obsługiwać zdarzenia domeny

Na koniec program obsługi zdarzeń zazwyczaj implementuje kod warstwy aplikacji, który korzysta z repozytoriów infrastruktury w celu uzyskania wymaganych dodatkowych agregacji i wykonywania logiki domeny z efektem ubocznym. Następujący [kod procedury obsługi zdarzeń domeny w eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)zawiera przykład implementacji.

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

Poprzedni kod procedury obsługi zdarzeń domeny jest uznawany za kod warstwy aplikacji, ponieważ używa repozytoriów infrastruktury, jak wyjaśniono w następnej sekcji warstwy trwałości infrastruktury. Procedury obsługi zdarzeń mogą również używać innych składników infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Zdarzenia domeny mogą generować zdarzenia integracji do opublikowania poza granicami mikrousług

Na koniec należy zauważyć, że czasami chcesz propagować zdarzenia w wielu mikrousługach. Propagacja jest zdarzeniem integracji i może zostać opublikowana za pośrednictwem magistrali zdarzeń z dowolnego programu obsługi zdarzeń domeny.

## <a name="conclusions-on-domain-events"></a>Wnioski dotyczące zdarzeń domeny

Jak wspomniano, użyj zdarzeń domeny w celu jawnego implementowania efektów ubocznych zmian w domenie. Aby użyć terminologii, użyj zdarzeń domeny w celu jawnego implementowania efektów ubocznych w jednej lub wielu agregacjach. Ponadto, aby zapewnić lepszą skalowalność i mniej wpływ na blokady bazy danych, należy użyć spójności ostatecznej między agregacjami w tej samej domenie.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Greg Young. Co to jest zdarzenie domeny?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Zdarzenia domeny i spójność ostateczna** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Lepszy wzorzec zdarzeń domeny** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon. Efektywna agregowana część II: wykonywanie zagregowanych współdziałania** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Wzmacnianie domeny: zdarzenia domeny** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Której należy Tony Truong. Przykład wzorca zdarzeń domeny** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **UDI Dahan. Jak utworzyć w pełni hermetyzowane modele domen** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **UDI Dahan. Zdarzenia domeny — zajmiemy 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **UDI Dahan. Zdarzenia domeny — Salvation** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Nie Publikuj zdarzeń domeny, zwróć je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de La Torre. Zdarzenia domeny a zdarzenia integracji w architekturze DDD i mikrousług** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Poprzedni](client-side-validation.md)
>[Następny](infrastructure-persistence-layer-design.md)
