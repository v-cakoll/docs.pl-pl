---
title: Wydarzenia związane z domeny. Projektowanie i implementacja
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Uzyskaj szczegółowy widok zdarzeń domeny kluczową koncepcją do nawiązania komunikacji między agregacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: fc71e661a5fd2de2a69da36df0fc60616b149802
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127852"
---
# <a name="domain-events-design-and-implementation"></a>Zdarzenia w domenie: projektowanie i implementacja

Jawne Implementowanie efekty uboczne zmian w swojej domenie za pomocą zdarzeń domeny Innymi słowy i używania terminologii DDD za jawne Implementowanie efekty uboczne w wielu agregacji za pomocą zdarzeń domeny. Opcjonalnie lepszą skalowalność i mniej wpływ na blokady bazy danych, należy użyć spójności ostatecznej między agregacje w ramach tej samej domenie.

## <a name="what-is-a-domain-event"></a>Co to jest zdarzenie domeny?

Zdarzenie jest coś, co zostało przeprowadzone w przeszłości. Jest to zdarzenie domeny, coś, co wydarzyło się w domenie mają inne części do tej samej domeny (w procesie), których trzeba pamiętać. Części powiadomienia zwykle reagować jakiś sposób na.

Ważną zaletą zdarzeń domeny jest jawnie wyrażone efekty uboczne.

Na przykład jeśli one po prostu używający narzędzia Entity Framework i musi istnieć w reakcji na zdarzenie, prawdopodobnie będzie kodu czegokolwiek potrzebujesz blisko co wyzwala zdarzenie. Reguła pobiera ściśle niejawnie do kodu, i masz możliwość przejrzenia kodu, weź pod uwagę reguły, mamy nadzieję, że zaimplementowano istnieje.

Z drugiej strony, za pomocą zdarzeń domeny sprawia, że pojęcie jawnej, ponieważ istnieje `DomainEvent` i co najmniej jeden `DomainEventHandler` zaangażowane.

Na przykład w ramach aplikacji eShopOnContainers aplikacji, gdy zamówienie zostanie utworzony, użytkownik staje się nabywców, więc `OrderStartedDomainEvent` jest wyświetlany i obsługiwane w `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`, więc podstawowych koncepcji jest oczywiste.

Krótko mówiąc zdarzenia domeny pomóc, jawnie, te reguły można wyrazić domeny, na podstawie języka wszechobecne udostępniane przez ekspertów z konkretnych dziedzin. Zdarzenia domeny umożliwia także lepsze separacji między klasami w ramach tej samej domenie.

Należy upewnić się, że tylko takie jak transakcji bazy danych, albo wszystkie operacje związane z zdarzenie domeny zakończy się pomyślnie lub żadna z nich.

Zdarzenia domeny są podobne do zdarzeń stylu komunikatów, z jedną istotną różnicą. Za pomocą rzeczywistych obsługi komunikatów, usługi kolejkowania komunikatów, brokerami lub usługi Service bus przy użyciu AMPQ komunikat jest zawsze wysyłane asynchronicznie i przekazywane między procesami i maszyny. Jest to przydatne do integrowania wielu ograniczone konteksty mikrousług lub nawet różnych aplikacji. Jednak za pomocą zdarzeń domeny, aby wywołać zdarzenie z operacji domeny, które są aktualnie uruchomione, ale chcesz, aby wszelkie efekty uboczne zostać przeprowadzone w tej samej domenie.

Zdarzenia domeny i ich skutki uboczne (akcje wyzwalane po tym dniu, które są zarządzane przez programy obsługi zdarzeń) powinny być wykonywane niemal natychmiast, zwykle w procesie, a w ramach tej samej domenie. W związku z tym zdarzenia domeny może być synchroniczna lub asynchroniczna. Zdarzenia integracji, jednak powinny zawsze być asynchroniczne.

## <a name="domain-events-versus-integration-events"></a>Zdarzenia domeny, a zdarzenia integracji

Semantycznie, domeny i integracji zdarzeń są tak samo: powiadomienia dotyczące coś, które wystąpiły po prostu. Jednak ich implementacji, musi być inna. Zdarzenia domeny są po prostu wiadomości wypychane do dyspozytora zdarzeń domeny, które można zaimplementować jako mediatora w pamięci, w oparciu o kontenera IoC lub innej metody.

Z drugiej strony celem zdarzenia integracji jest propagacja przekazane transakcje i aktualizacje podsystemów dodatkowe, czy są one innych mikrousług, ograniczone konteksty lub nawet zewnętrznych aplikacji. Dlatego powinien wystąpić tylko jeśli jednostka pomyślnie jest trwały, w przeciwnym razie jest tak, jakby cała operacja nigdy się stało.

Jak wspomniano wcześniej, zdarzenia integracji musi być oparta na komunikacji asynchronicznej między wielu mikrousługach (inne ograniczone konteksty) lub nawet zewnętrznych systemów/aplikacji.

W efekcie interfejsu magistrali zdarzenia musi niektóre infrastrukturę, która umożliwia między procesu i rozproszonych komunikację między usługami potencjalnie zdalnego. Ona może bazować na komercyjnej usługi Service bus, kolejki, udostępnionej bazy danych, używane jako skrzynki pocztowej lub inne rozproszone i najlepiej wypychane oparte na system obsługi komunikatów.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Zdarzenia domeny jako preferowany sposób, aby wyzwolić efekty uboczne w wielu wartości zagregowanych w ramach tej samej domenie

W przypadku wykonywania polecenia związane z jednego wystąpienia agregacji wymaga reguły dodatkowe domeny do uruchamiania na co najmniej jeden dodatkowy agregacji powinny projektowania i wdrażania efektów ubocznych przez zdarzenia domeny. Jak pokazano w rysunek 7-14, a także jako jedna z najważniejszych przypadków użycia, zdarzenie domeny powinny być używane do propagowanie zmian stanu wielu wartości zagregowanych w ramach tego samego modelu domeny.

![Spójność między agregacje odbywa się przez zdarzenia domeny, agregacji kolejności wysyła zdarzenie domeny OrderStarted, które odbywa się zaktualizować kupujący agregacji. ](./media/image15.png)

**Rysunek 7-14**. Zdarzenia domeny, aby wymusić spójność między wiele wartości zagregowanych w ramach tej samej domenie

Na rysunku gdy użytkownik zainicjuje zamówienie, zdarzenie domeny OrderStarted wyzwala utworzenia obiektu kupujący w mikrousługach szeregowania, oparty na oryginalne informacje o użytkowniku z mikrousług identity (informacji podanych w poleceniu CreateOrder). Zdarzenie domeny jest generowany przez agregacji zamówienia, gdy zostanie utworzony w pierwszej kolejności.

Alternatywnie możesz mieć głównego agregacji subskrybuje zdarzenia wygenerowane przez członków jego wartości zagregowanych (jednostki podrzędne). Na przykład każdy obiekt podrzędny OrderItem może wywołać zdarzenie, kiedy cena elementu jest wyższy niż określoną ilością lub w przypadku, gdy kwota pozycji produktu jest zbyt wysoka. Głównego agregacji można otrzymywać te zdarzenia i wykonywać obliczenia globalne lub agregacji.

Jest ważne zrozumieć, tę komunikację opartego na zdarzeniach — nie jest zaimplementowana bezpośrednio z poziomu agregacje; musisz zaimplementować obsługę zdarzeń domeny.

Obsługa zdarzeń domeny jest kwestią aplikacji. Warstwie modelu domeny należy skoncentrować się tylko na logice domeny — rzeczy, które może zrozumieć eksperta domeny, nie na infrastrukturze aplikacji takich jak programy obsługi i działania trwałości efekt uboczny przy użyciu repozytoriów. W związku z tym na poziomie warstwy aplikacji jest, gdzie powinien mieć wyzwalają akcje w przypadku, gdy zostanie wywołane zdarzenie domeny procedury obsługi zdarzeń domeny.

Zdarzenia domeny może także służyć do wyzwolenia dowolną liczbę akcji aplikacji i co to jest niezwykle ważne, musi być otwarty, aby zwiększyć tę liczbę w przyszłości w sposób odłączony. Na przykład uruchamianiu kolejność można opublikować zdarzenie domeny, Propagacja tej informacji do innych wartości zagregowanych, a nawet podnieść akcji aplikacji, takich jak powiadomienia.

Kluczowym punktem jest otwarty liczba akcji do wykonania, gdy wystąpi zdarzenie domeny. Po pewnym czasie będzie rosnąć działań i reguł w domenie i aplikacji. Złożoność lub liczba akcji efekt uboczny, gdy coś, co się stanie, będzie się zwiększać, ale jeśli kodu zostały połączone z "skleić" (czyli tworzenia określonych obiektów z `new`), a następnie za każdym razem, gdy trzeba było dodać nową akcję będzie trzeba będzie również zmienić pracy i przetestowane kod.

Ta zmiana może spowodować nowych usterek i takie podejście również przechodzi względem [zasady otwarty/zamknięty](https://en.wikipedia.org/wiki/Open/closed_principle) z [SOLID](https://en.wikipedia.org/wiki/SOLID). Nie wszystko: oryginalnej klasy, która została organizowanie działań może rosnąć i rozwijanie działalności, który znajduje się przed [pojedynczej odpowiedzialności zasady (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Z drugiej strony możesz za pomocą zdarzeń domeny, można utworzyć szczegółowe i rozdzielonego wdrożenia przez umieszczenie odpowiedzialności za pomocą tej metody:

1. Wysłać polecenie (na przykład CreateOrder).
2. Odbierać polecenia programu obsługi poleceń.
   - Wykonywanie transakcji pojedynczego agregacji.
   - (Opcjonalnie) Wywoływanie zdarzeń domeny dla efekty uboczne (na przykład OrderStartedDomainEvent).
3. Obsługa zdarzeń domeny (w ramach bieżący proces), wykonujących Otwórz liczba efekty uboczne w wielu agregacje lub akcje aplikacji. Na przykład:
   - Sprawdź lub Utwórz metodę nabywców i płatności.
   - Utwórz i wysyłać zdarzenia powiązane integracji bus zdarzeń i propagowanie stany mikrousług lub wyzwalacza zewnętrznego akcje, takie jak wysyłanie wiadomości e-mail do kupującego.
   - Obsługa innych efektów ubocznych.

Jak pokazano w rysunek 7-15, począwszy od tego samego zdarzenia domeny można obsługiwać wielu akcji związanych z innych wartości zagregowanych w domenie lub akcje dodatkowych aplikacji, które należy wykonać na mikrousługi łączenie ze zdarzeniami integracji i magistrali zdarzeń.

![Może istnieć kilka programów obsługi dla tego samego zdarzenia domeny w warstwie aplikacji, co program obsługi może rozwiązać spójności między agregacje i innego programu obsługi zdarzenie można opublikować integracji, dzięki czemu inne mikrousługi można zrobić z nim coś.](./media/image16.png)

**Rysunek 7 – 15**. Obsługa wielu akcji dla domeny

Programy obsługi zdarzeń są zazwyczaj w warstwie aplikacji, ponieważ obiektów infrastruktury, takich jak repozytoria lub interfejsu API aplikacji będą używane na potrzeby zachowania mikrousług. W tym sensie programy obsługi zdarzeń są podobne do obsługi polecenia, więc obie są częścią warstwy aplikacji. Istotną różnicą jest to, czy polecenie powinny być przetwarzane tylko raz. Zdarzenie domeny mogą być przetwarzane zero lub *n* razy, ponieważ może zostać odebrany przez wielu odbiorców lub programów obsługi zdarzeń z różnych przeznaczenia dla każdego programu obsługi.

Masz otwarte liczby programów obsługi na zdarzenie domeny umożliwia dodawanie tyle reguły domen bez zgodnie z potrzebami, bez wywierania wpływu na bieżący numer kierunkowy. Na przykład implementacja następujące reguły biznesowej mogą być bardzo proste — wystarczy dodanie kilku procedur obsługi zdarzeń (lub nawet tylko jednego):

> Łączna kwota zakupione w sklepie w dowolnej liczbie zamówienia, przekroczenia $6000 się o 10% rabat w wysokości do każdego nowego zamówienia i powiadomić klienta o wiadomość e-mail dotyczącą tego rabat na przyszłe zamówienia.

## <a name="implement-domain-events"></a>Implementowanie zdarzeń domeny

W języku C# zdarzenie domeny jest po prostu przechowywania danych struktury lub klasy, takie jak obiekt DTO, wszystkie informacje związane z co właśnie wydarzyło się w domenie, jak pokazano w poniższym przykładzie:

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

To jest zasadniczo klasą, która przechowuje wszystkie dane związane ze zdarzeniem OrderStarted.

Pod względem języka wszechobecne domeny ponieważ zdarzenie jest coś, co wydarzyło się w przeszłości, nazwa klasy zdarzenia powinna być reprezentowana jako czasownik przeszłym, takich jak OrderStartedDomainEvent lub OrderShippedDomainEvent. To zdarzenie domeny jest implementacji w szeregowania mikrousługi w ramach aplikacji eShopOnContainers.

Jak wspomniano wcześniej, ważną cechą zdarzeń jest to, że ponieważ zdarzenie jest coś, co wydarzyło się w przeszłości, nie należy zmieniać. W związku z tym musi być klasą niezmienne. W poprzednim kodzie widać, że właściwości są tylko do odczytu. Nie ma możliwości można zaktualizować obiektu, wartości można ustawić tylko podczas jego tworzenia.

Jest ważne wyróżnić w tym miejscu, że gdyby domeny zdarzeń do obsłużenia asynchronicznie, przy użyciu kolejki wymagające serializacji i deserializacji obiektów zdarzeń, właściwości konieczne będzie "Zestaw prywatny" zamiast tylko do odczytu, więc będzie Deserializator można przypisać wartości podczas usuwania z kolejki. Ta wartość jest problem w mikrousługach porządkowanie, ponieważ domeny zdarzeń publikowania/subskrybowania jest implementowany synchronicznie przy użyciu MediatR.

### <a name="raise-domain-events"></a>Wywoływanie zdarzeń domeny

Następne pytanie jest sposób wywołać zdarzenie w domenie, osiągnie swoich programów obsługi zdarzeń powiązanych. Można użyć wielu metod.

Udi Dahan została pierwotnie zaproponowana (na przykład w kilku powiązane wpisy, takich jak [zdarzeń domeny — potrwać 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) do zarządzania i wywoływanie zdarzeń przy użyciu klasy statycznej. Może to obejmować statyczne klasę o nazwie DomainEvents, która będzie wywoływać zdarzenia, domeny, natychmiast, gdy jest wywoływana, przy użyciu składni `DomainEvents.Raise(Event myEvent)`. Jimmy Bogard napisałem wpis w blogu ([wzmocnienia domeny: Zdarzenia domeny](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)), zaleca się podejście podobne.

Jednak w przypadku statycznej klasy zdarzeń domeny również wywołuje programy obsługi natychmiast. To sprawia, że testowanie i debugowanie trudniejsze, ponieważ programy obsługi zdarzeń z logiką efekty uboczne są wykonywane natychmiast, po wywołaniu zdarzenia. Podczas testowania i debugowania, chcesz skupić się na i po prostu co się dzieje w bieżącej klasy agregacji; Czy chcesz nagle nastąpi przekierowanie do inne procedury obsługi zdarzeń dla efektów ubocznych dotyczących innych wartości zagregowanych lub logiki aplikacji. Dlatego właśnie usprawniły innych metod, zgodnie z opisem w następnej sekcji.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odroczone podejście do Zgłoś i wysyłania zdarzeń

Zamiast wysyłania do obsługi zdarzeń domeny natychmiast, lepszym rozwiązaniem jest dodanie zdarzenia domeny do kolekcji i do wysyłania tych zdarzeń domeny *bezpośrednio poprzedzający* lub *prawo*  *Po* Zatwierdzanie transakcji (podobnie jak w przypadku SaveChanges w programie EF). (To podejście został opisany przez Jimmy Bogard w tym wpisie [lepsze wzorzec zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Przy wyborze rozwiązania, jeśli wysyłanie zdarzeń domeny po prawej stronie przed lub w prawo po zatwierdzeniu transakcji ważne jest, ponieważ określa, czy będzie zawierać efekty uboczne w ramach tej samej transakcji lub w innej transakcji. W tym drugim przypadku musisz obsługi spójności ostatecznej między wiele agregacji. W tym temacie omówiono w następnej sekcji.

Odroczone podejście to, jakie ramach aplikacji eShopOnContainers używa. Najpierw dodaj się zdarzenia, dzieje się w jednostkach w kolekcji lub Podaj listę zdarzeń na jednostkę. Tej listy powinny być częścią obiektu jednostki lub jeszcze lepiej część swojej klasy podstawowej jednostki, jak pokazano w poniższym przykładzie klasa bazowa jednostki:

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

Jeśli chcesz wywołać zdarzenie, możesz po prostu dodaj go do zbierania zdarzeń z kodu w dowolnej metody jednostkę główną agregacji.

Poniższy kod, część [kolejność elementu głównego agregacji w ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), przedstawiono przykład:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Należy zauważyć, że jedynym elementem, który wykonuje metodę AddDomainEvent polega na dodaniu zdarzenia do listy. Nie zdarzenie jest wywoływane jeszcze i żadna procedura obsługi zdarzeń jest wywoływany jeszcze.

Faktycznie chcesz później na wysłanie zdarzenia podczas zatwierdzania transakcji w bazie danych. Jeśli używasz platformy Entity Framework Core, oznacza to, w ramach metody SaveChanges swoje DbContext EF, zgodnie z poniższym kodem:

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

Przy użyciu tego kodu możesz wysyłania zdarzeń jednostki do ich odpowiednich procedur obsługi.

Ogólny wynik jest, czy można mieć rozdzielenie wywoływanie zdarzenie w domenie (proste dodawanie do listy w pamięci) wysyła go do programu obsługi zdarzeń. Ponadto w zależności od tego, jakiego rodzaju dyspozytora używasz, możesz można wysyłać zdarzenia synchronicznie lub asynchronicznie.

Należy pamiętać, w tym miejscu odtwarzania transakcyjnych granice wchodzą w znaczący. Jeśli Twoja jednostka pracy i transakcji może obejmować więcej niż jedną wartość zagregowaną (tak jak w przypadku korzystania z programu EF Core i relacyjnej bazy danych), to będzie działać prawidłowo. Ale jeśli transakcja nie mogą rozciągać się agregacje, takie jak w przypadku korzystania z bazy danych NoSQL, takie jak Azure cosmos DB, musisz zaimplementować dodatkowe kroki w celu osiągnięcia spójności. Jest to kolejny powód, dlaczego nie jest uniwersalny; nieznajomości trwałości To zależy od używanego systemu magazynu. 

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Pojedyncza transakcja różnych wartości zagregowanych i spójności ostatecznej między agregacji

Pytanie, czy ma być przeprowadzane pojedynczej transakcji między agregacje, a opieranie się na spójność między tych agregacji jest kontrowersyjny. Wiele autorzy DDD, takie jak Eric Evans i Vaughn Vernon Ambasador regułę, że jedna transakcja = co agregacji i w związku z tym dokumentu uważają w celu zachowania spójności ostatecznej między agregacji. Na przykład w książce *projektowania driven*, Eric Evans mówi, że:

> Reguły obejmującej agregacji spowoduje nie powinny mieć aktualne przez cały czas. Przez przetwarzanie zdarzeń, przetwarzanie wsadowe lub innych mechanizmów aktualizacji innych zależności mogą być wyszukiwane w niektórych określony czas. (strona 128)

Vaughn Vernon mówi następujące [efektywnym projektowaniu agregacji. Część II: Podejmowanie agreguje pracy ze sobą](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> W związku z tym, jeśli wykonywania polecenia na jednym wystąpieniu agregacji wymaga, że dodatkowe reguły biznesowe są wykonywane na jeden lub więcej wartości zagregowanych, użyj spójności ostatecznej \[...\] Istnieje praktyczny sposób obsługiwać spójność ostateczną w modelu DDD. Metoda agregacji publikuje zdarzenie domeny, które jest w momencie dostarczane do co najmniej jeden subskrybentów asynchronicznego.

Takiego rozumowania mogą być jest oparty na założeń szczegółowych transakcji zamiast transakcje obejmujące wiele agregacji lub jednostki. Chodzi o to, że w drugim przypadku liczbę blokad bazy danych będzie istotne w wielkoskalowych aplikacji potrzebom wysokiej skalowalności. Fakt wysoce skalowalne aplikacje nie wymagają natychmiastowej spójności transakcyjnej między Agreguje wiele założeń pomaga przyjmuje koncepcję spójności ostatecznej. Atomowej zmiany często nie są wymagane przez firmę i w każdym przypadku jest odpowiedzialny za eksperci domeny powiedzieć, czy jakieś operacje muszą transakcje niepodzielne. Jeśli operacja zawsze musi transakcji niepodzielnej między wiele wartości zagregowane, może poprosić czy agregacji usługi powinien być większy lub nie został niepoprawnie zaprojektowany.

Jednak przeszkadza obejmujące pojedynczą transakcję kilka wartości zagregowane są innych deweloperów i architektów, takich jak Jimmy Bogard —, ale tylko, gdy te dodatkowe wartości zagregowanych są powiązane z efekty uboczne dla tego samego polecenia oryginalnego. Na przykład w [lepsze wzorzec zdarzeń domeny](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard mówi, że:

> Zazwyczaj ma efekty uboczne domeny zdarzenia w obrębie tej samej transakcji logiczne, ale nie musi w tym samym zakresie liczby zdarzeń domeny \[...\] Przed jesteśmy zaangażowani w naszym transakcji, firma Microsoft wysyłania naszych zdarzenia do ich odpowiednich programów obsługi.

Jeśli na wysłanie zdarzenia domeny po prawej stronie *przed* Zatwierdzanie transakcji oryginalnej, oznacza to, że ma efekty uboczne tych zdarzeń, które mają zostać uwzględnione w tej samej transakcji. Na przykład jeśli metodę EF DbContext SaveChanges zakończy się niepowodzeniem, transakcja zostanie wycofać wszystkie wprowadzone zmiany, w tym także wynik operacji efekt uboczny, implementowany przez programy obsługi zdarzeń pokrewne domeny. To jest ponieważ zakres życia DbContext jest domyślnie zdefiniowany jako "o określonym zakresie." W związku z tym obiektu DbContext jest udostępniony dla wielu obiektów repozytorium, które są tworzone w tym samym zakresie lub wykres obiektu. Pokrywa się z zakresem HttpRequest podczas tworzenia aplikacji interfejsu API sieci Web lub MVC.

W rzeczywistości oba podejścia (jednej transakcji niepodzielnej i spójności ostatecznej) może być odpowiednie. Tak naprawdę zależy wymagań domeny lub business i co eksperci domeny informujące. Zależy on również skalowalność należy usługa będzie (bardziej szczegółowe transakcje mają mniejsze znaczenie w odniesieniu do blokady bazy danych). A od tego, ile inwestycji gdy zgadzasz się się w kodzie, ponieważ spójności ostatecznej wymaga bardziej skomplikowanym kodzie w celu wykrycia możliwych niespójności między agregacje i trzeba implementować akcje kompensacyjne. Należy wziąć pod uwagę, że jeśli zdecydujesz się zmiany oryginalnego agregacji, a później, gdy zdarzenia są wysyłane, jeśli występuje problem, a także procedury obsługi zdarzeń nie można zatwierdzić ich skutki uboczne, użytkownik będzie miał niespójności między agregacji.

Sposób kompensacyjne akcji zezwalania będzie do przechowywania zdarzeń domeny w tabelach dodatkowe bazy danych, dzięki czemu mogą być częścią oryginalnej transakcji. Później może mieć procesu wsadowego, który wykrywa niespójności i uruchamia akcje kompensacyjne, porównując listę zdarzeń z bieżącym stanem agregacji. Akcje kompensacyjne są częścią złożoną kwestią, które wymagają dokładnej analizy ze strony użytkownika zawiera Omawiając go za pomocą użytkowników biznesowych i ekspertów z konkretnych dziedzin.

W każdym przypadku można wybrać metody, których potrzebujesz. Ale początkowego odroczone podejście — wywoływanie zdarzeń przed zatwierdzeniem, dzięki czemu możesz użyć jednej transakcji — jest najprostszym podejściem podczas korzystania z programu EF Core i relacyjnej bazy danych. Jest to łatwiejsze do wdrożenia i prawidłowy w wielu przypadkach biznesowych. Jest również podejście użyte w szeregowania mikrousługi w ramach aplikacji eShopOnContainers.

Ale jak zostanie faktycznie wysyłania tych zdarzeń do ich odpowiednich procedur obsługi? Co to jest `_mediator` obiektów, zostanie wyświetlony w poprzednim przykładzie? Musi to zrobić za pomocą techniki i artefaktów, używane do mapowania miedzy zdarzenia do swoich programów obsługi zdarzeń.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dyspozytora zdarzeń domeny: mapowanie ze zdarzeń z programami obsługi zdarzeń

Gdy jesteś w stanie wysyłać lub opublikować zdarzenia, należy pewnego rodzaju artefaktu, która będzie publikować zdarzenia, dzięki czemu co powiązane obsługi mogą go i przetworzyć efekty uboczne bazujących na tym zdarzeniu.

Jednym z podejść jest rzeczywistym komunikatów system lub nawet magistrali zdarzeń, prawdopodobnie oparte na usługi Service bus, w przeciwieństwie do zdarzenia w pamięci. Jednak w przypadku pierwszego rzeczywiste komunikatów będzie obszerne do przetwarzania zdarzeń domeny, ponieważ potrzebne do przetwarzania tych zdarzeń w ramach tego samego procesu (czyli w ramach tej samej warstwie domeny i aplikacji).

Innym sposobem mapowania zdarzeń na wiele procedur obsługi zdarzeń jest przy użyciu typów rejestracji w pojemniku IoC, co może dynamicznie wywnioskować gdzie wysyłać zdarzenia. Innymi słowy musisz wiedzieć, co procedury obsługi zdarzeń koniecznych do uzyskania określonego zdarzenia. Rysunek 7-16 pokazuje uproszczone podejście, w tym podejściu.

![Wstrzykiwanie zależności umożliwia kojarzenie zdarzeń z programami obsługi zdarzeń, czyli metody używane przez MediatR](./media/image17.png)

**Rysunek 7-16**. Dyspozytora zdarzeń domeny przy użyciu IoC

Można tworzyć wszystkie aspekty techniczne i artefaktów do implementowania tego podejścia samodzielnie. Jednak można również użyć dostępnych bibliotek, takich jak [MediatR](https://github.com/jbogard/MediatR) kontenera IoC dzieje się w tle, który używa. W związku z tym bezpośrednio można wstępnie zdefiniowane interfejsy i metody publikowania wysyłania obiektu mediatora.

W kodzie, najpierw musisz zarejestrować typy programów obsługi zdarzeń w Twoim kontenerze IoC, jak pokazano w poniższym przykładzie w [ramach aplikacji eShopOnContainers mikrousług porządkowanie](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kod najpierw identyfikuje zestaw zawierający programy obsługi zdarzeń domeny, znajdując zestawu, który zawiera dowolny z elementów obsługi (przy użyciu typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale może wybrano inne obsługi zdarzeń, które można zlokalizować zestawu). Ponieważ wszystkich procedur obsługi zdarzeń implementować interfejs IAsyncNotificationHandler, kod, a następnie po prostu wyszukiwania dla tych typów i rejestruje wszystkie procedury obsługi zdarzeń.

### <a name="how-to-subscribe-to-domain-events"></a>Subskrybowanie zdarzeń domeny

W przypadku użycia MediatR, każdy program obsługi zdarzeń musi użyć typu zdarzenia, który znajduje się na parametry generyczne interfejsu INotificationHandler, jak pokazano w poniższym kodzie:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na podstawie relacji między zdarzeń i obsługi zdarzeń, który jest uznawana za subskrypcję, artefaktu MediatR może odnajdywać całej obsługi zdarzeń dla każdego zdarzenia i wyzwolić każdej z nich te programy obsługi zdarzeń.

### <a name="how-to-handle-domain-events"></a>Sposób obsługi zdarzeń domeny

Ponadto program obsługi zdarzeń zwykle implementuje kod warstwy aplikacji, który używa repozytoria infrastruktury w celu uzyskania wymaganych dodatkowych wartości zagregowanych i do wykonywania logiki domeny efekt uboczny. Następujące [kod procedury obsługi zdarzeń domeny w ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), przedstawiono przykład implementacji.

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

Poprzedni kod procedury obsługi zdarzeń domeny jest uznawany za kod warstwy aplikacji, ponieważ używa ona repozytoria infrastruktury zgodnie z opisem w następnej sekcji warstwy trwałości infrastruktury. Programy obsługi zdarzeń można także stosować inne składniki infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Zdarzenia domeny może generować zdarzenia integracji do opublikowania poza granic mikrousługi

Na koniec warto wspomnieć, że czasami warto propagowanie zdarzenia z wielu mikrousług. Propagacja tej to zdarzenie integracji i mogą być publikowane za pośrednictwem magistrali zdarzeń z dowolnego programu obsługi zdarzeń określonej domeny.

## <a name="conclusions-on-domain-events"></a>Wnioski dotyczące zdarzeń domeny

Jak wspomniano, za pomocą zdarzeń domeny, aby jawnie implementować efekty uboczne zmian w swojej domenie. Aby użyć terminologii DDD, za pomocą zdarzeń domeny na jawne Implementowanie efekty uboczne w jednej lub wielu wartości zagregowanych. Ponadto i lepszą skalowalność i mniej wpływ na blokady bazy danych należy użyć spójności ostatecznej między agregacje w ramach tej samej domenie.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Grega Younga. Co to jest zdarzenie domeny?** \
  [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

- **Stenberg stycznia. Zdarzenia domeny i spójności ostatecznej** \
  [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

- **Jimmy Bogard. Lepsze wzorzec zdarzeń domeny** \
  [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

- **Vaughn Vernon. Efektywnym projektowaniu agregacji część II: Tworzenie wartości zagregowanych pracują razem** \
  [*https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Wzmocnienie domeny: Zdarzeń domeny** \
  [*https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/*](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)

- **Tony Truong. Przykład wzorca zdarzeń domeny** \
  [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)

- **Udi Dahan. Jak utworzyć w pełni hermetyzowane modeli domeny** \
  [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

- **Udi Dahan. Zdarzenia domeny — próba 2** \
  [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

- **Udi Dahan. Zdarzenia domeny — Salvation** \
  [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

- **Kronquist stycznia. Nie Publikuj zdarzenia domeny, przywrócić je!** \
  [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

- **Torre'a de la Cesarowi. Vs zdarzeń domeny. Zdarzenia integracji w architektur mikrousług i DDD** \
  [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)

>[!div class="step-by-step"]
>[Poprzednie](client-side-validation.md)
>[dalej](infrastructure-persistence-layer-design.md)