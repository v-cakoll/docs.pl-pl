---
title: Komunikacja w ramach architektury mikrousługi
description: Poznaj różne sposoby komunikacji między mikrousługami, zrozumienia konsekwencji synchroniczne i asynchroniczne metody.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 364bd4eb82907fcf0fbcc850eca839f676a2dbf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909510"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikacja w ramach architektury mikrousługi

W aplikacji monolitycznej, uruchomiony w ramach jednego procesu składniki wywołać za pomocą metody poziomu języka lub wywołania funkcji. Te mogą zostać zdecydowanie dołączone Jeśli tworzysz obiektów przy użyciu kodu (na przykład `new ClassName()`), lub może być wywoływany w sposób odłączony, jeśli używasz wstrzykiwanie zależności, odwołując się do abstrakcje zamiast konkretnych obiektów. W obu przypadkach obiekty są uruchamiane w ramach tego samego procesu. Największe wyzwanie w przypadku zmiany z poziomu aplikacji monolitycznych aplikacji opartych na mikrousługach znajduje się podczas zmieniania mechanizm komunikacji. Bezpośrednia konwersji z wywołania metody w trakcie do wywołań RPC usługi spowoduje, że duża liczba i nie sprawną komunikację, która nie wykonuje również w rozproszonych środowisk. Wyzwania związane z prawidłowo projektowania Rozproszony system wystarczająco dobrze wiadomo, czy jest parzysta canon, znane jako [błędne przekonania dotyczące przetwarzania rozproszonego](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) , zawiera listę założeń, które deweloperzy mogą stosować często podczas przenoszenia z monolitycznego projekty do rozproszonego.

Nie ma jednego rozwiązania, ale kilka. Jedno rozwiązanie polega na izolowanie możliwie mikrousług biznesowych. Następnie użyj komunikacji asynchronicznej między mikrousługami wewnętrzny i Zastąp szczegółowych komunikacji, który jest typowy wewnątrzprocesową komunikacji między obiektami za pomocą gruboziarnisty szczegółowej komunikacji. Można to zrobić przez grupowanie połączeń i zwracanie danych, która agreguje wyniki wielu wywołań wewnętrznego, do klienta.

Aplikacją opartą na mikrousługach to Rozproszony system działających w wielu procesów lub usług, zwykle nawet między wieloma serwerami lub hostów. Każde wystąpienie usługi jest zwykle procesem. W związku z tym usług muszą wchodzić w interakcje za pomocą protokołu komunikacji między procesami, takich jak HTTP, AMQP lub binarny protokołu takich jak TCP, w zależności od charakteru każdej usługi.

Społeczność mikrousług promuje ideę "[inteligentne punkty końcowe i potoków bez](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" to slogan zachęca do projektu, który jest całkowicie niezależny możliwie między mikrousługami i jak spójnego, jak to możliwe w jednej mikrousługi. Jak wyjaśniono wcześniej, każda mikrousługa jest właścicielem własnych danych i własnej logiki domeny. Ale mikrousług, aplikacja end-to-end redagowania są zazwyczaj po prostu choreographed przy użyciu komunikacji REST, a nie złożoną protokołów, takich jak usługi WS -\* i elastyczne komunikacji oparte na zdarzeniach, zamiast scentralizowane Business — proces koordynatorów.

Dwa najczęściej używane protokoły są żądania/odpowiedzi HTTP przy użyciu interfejsów API (podczas wykonywania zapytania większość wszystkich) zasobów i uproszczone asynchronicznej obsługi komunikatów podczas komunikowania się aktualizuje przez wiele mikrousług. Omówiona bardziej szczegółowo w poniższych sekcjach.

## <a name="communication-types"></a>Typy komunikacji

Klienta i usługi mogą komunikować się za pośrednictwem wiele różnych typów komunikacji, każdy z nich przeznaczone dla różnych scenariuszy i cele. Początkowo tych typów komunikacji mogą być klasyfikowane w dwóch osi.

Pierwsza oś Określa, czy protokół jest synchroniczna lub asynchroniczna:

- Protokół synchroniczne. Protokół HTTP jest protokół synchroniczne. Klient wysyła żądanie i czeka na odpowiedź z usługi. Który jest niezależny od wykonania kodu klienta, który może być synchroniczna (wątek jest zablokowany) lub asynchroniczną (wątek nie jest zablokowany, i odpowiedź osiągną wywołanie zwrotne po pewnym czasie). Należy koniecznie zwrócić uwagę, jest protokół (HTTP/HTTPS) jest synchroniczne i kod klienta można kontynuować tylko jej zadania, po otrzymaniu odpowiedzi serwera HTTP.

- Protokół asynchroniczny. Inne protokoły, takie jak protokół AMQP (protokół obsługiwany przez wiele systemów operacyjnych i środowisk w chmurze) używają komunikatów asynchronicznych. Nadawca kodu lub komunikat klienta zazwyczaj nie czeka na odpowiedź. Po prostu wysyła wiadomość jako podczas wysyłania komunikatu do kolejki RabbitMQ lub innych brokera komunikatów.

Drugą oś Określa, czy komunikacja nie ma jednego odbiornika lub wieloma odbiornikami:

- Jednego odbiornika. Każde żądanie muszą zostać przetworzone przez dokładnie jednego odbiornika lub usługi. Na przykład ta komunikacja [wzorzec polecenia](https://en.wikipedia.org/wiki/Command_pattern).

- Wiele odbiorników. Każde żądanie mogą być przetwarzane przez zero do wielu odbiorników. Ten typ komunikacji musi być asynchroniczne. Na przykład [publikowania/subskrybowania](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mechanizm używany w wzorców, takich jak [architektura sterowana zdarzeniami](https://microservices.io/patterns/data/event-driven-architecture.html). Zależy to interfejs lub komunikatów brokera magistrali zdarzeń podczas propagowania aktualizacje danych między wiele mikrousług za pomocą zdarzeń; Zazwyczaj jest implementowany przy użyciu usługi service bus lub podobne artefaktu, takie jak [usługi Azure Service Bus](https://azure.microsoft.com/services/service-bus/) przy użyciu [tematy i subskrypcje](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikacją opartą na mikrousługach często używają kombinacji tych stylów komunikacji. Najczęściej spotykanym typem jest jednego odbiornika protokołu synchroniczne, takich jak HTTP/HTTPS podczas wywoływania regularnej HTTP dla interfejsu API sieci Web. Mikrousługi zwykle także używać protokołów obsługi komunikatów dla komunikacji asynchronicznej między mikrousługami.

Te osi są dobre wiedzieć, dzięki czemu masz w celu uściślenia na mechanizmy komunikacji możliwe, ale nie są istotne problemy podczas tworzenia mikrousług. Rodzaj asynchroniczne wykonywanie wątków klienta ani asynchronicznego charakter wybranego protokołu są ważne punkty podczas integrowania mikrousług. Co *jest* ważna jest możliwość integracji mikrousługi asynchronicznie przy zachowaniu niezależność mikrousług, zgodnie z opisem w poniższej sekcji.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Integracja asynchroniczne mikrousług wymusza autonomię w mikrousługach

Jak wspomniano wcześniej, istotne podczas kompilowania aplikacji mikrousług jest to sposób zintegrować mikrousługi. W idealnym przypadku należy spróbować zminimalizować komunikacji między mikrousługami wewnętrznego. Mniej komunikacji między mikrousługami, tym lepiej. Jednak w wielu przypadkach, będziesz mieć dostęp do jakiś sposób integracji mikrousług. Gdy trzeba to zrobić, w tym miejscu reguła krytycznego jest komunikacji między mikrousług należy asynchronicznego. Nie oznacza, trzeba użyć określonego protokołu, (na przykład asynchronicznej obsługi komunikatów i synchroniczne HTTP). Po prostu oznacza to, że komunikacji między mikrousługami powinno być wykonywane tylko przez propagowanie danych asynchronicznie, ale Staraj się nie są zależne od innych wewnętrznych mikrousługi w ramach operacji żądania/odpowiedzi HTTP początkowej usługi.

Jeśli to możliwe nigdy nie są zależne od synchroniczną komunikację (żądania/odpowiedzi) między wiele mikrousług, nawet w przypadku zapytań. Celem każda mikrousługa jest jako autonomiczne i konsumenta klienta, nawet jeśli są inne usługi, które są częścią aplikacji end-to-end w dół lub w złej kondycji. Jeśli sądzisz, musisz wprowadzić wywołanie jednej mikrousług innych mikrousługi (np. wykonywania żądaniem HTTP kwerendy danych), aby można było podać odpowiedzi do aplikacji klienta, masz architekturę, która nie być odporny, gdy niektóre mikrousług się nie powieść.

Ponadto mających zależności HTTP między mikrousług, takich jak podczas tworzenia długie cykle żądania/odpowiedzi HTTP z żądania łańcuchów, jak pokazano w pierwszej części 4 rysunek-15, nie tylko sprawia, że mikrousługi nie autonomicznego, ale również ich wydajność jest wpływ, jak tylko jednej z usług w tym łańcuchu nie działa poprawnie.

Bardziej Dodaj synchroniczne zależności między mikrousług, takich jak żądania zapytania, niższa pobiera całkowity czas odpowiedzi dla aplikacji klienckich.

![W komunikacie synchroniczne "łańcucha" żądania jest tworzony między mikrousługami przy jednoczesnej obsłudze żądania klienta. Jest to niezalecane wzorca. W przypadku komunikacji asynchronicznej mikrousług wiadomości asynchronicznych lub http sondowania do komunikowania się z innymi mikrousług, ale żądanie klienta jest obsługiwany język.](./media/image15.png)

**Rysunek 4 – 15**. Niezalecane wzorce i wzorców w ramach komunikacji między mikrousługami

Jeśli Twoje mikrousług musi zgłosić dodatkowych akcji w innym mikrousług, jeśli to możliwe, nie wykonuj tę akcję synchronicznie, w ramach mikrousług żądania i odpowiedzi operacji pierwotnej. Zamiast tego asynchronicznie (za pomocą asynchronicznej obsługi komunikatów lub zdarzeń integracji, kolejki, itd.). Jednak w miarę możliwości, nie wywołać akcję synchronicznie w ramach oryginalnego synchronicznych operacji żądania i odpowiedzi.

A na koniec i jest to, gdzie większość problemów wystąpić podczas tworzenia mikrousług, jeśli Twoje początkowe mikrousług wymaga danych, który pierwotnie jest własnością innych mikrousług, nie należy polegać na synchroniczne żądania dla tych danych. Zamiast tego należy replikować lub propagować dane (tylko atrybuty, które są potrzebne) w bazie danych usługi początkowej spójność ostateczną (zazwyczaj przy użyciu zdarzenia integracji, jak wyjaśniono w kolejnych sekcjach).

Jak wspomniano wcześniej w sekcji [identyfikowanie ograniczeń modelu domeny dla poszczególnych mikrousług](identify-microservice-domain-model-boundaries.md), powielanie niektórych danych między kilka mikrousług jest nieprawidłowy projekt — przeciwnie, podczas wykonywania, które można tłumaczyć danych określonego język lub warunki tej dodatkowe domeny lub ograniczone do kontekstu. Na przykład w [aplikacji w ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) masz mikrousługi o nazwie identity.api, który jest odpowiedzialny za większość danych użytkownika za pomocą jednostki o nazwie użytkownika. Jednak jeśli potrzebujesz do przechowywania danych o użytkowniku w mikrousługach porządkowanie, są przechowywane go jako inny element o nazwie kupujący. Jednostki nabywcy udostępni oryginalnej jednostki użytkownika tej samej tożsamości, ale może mieć tylko kilka atrybutów wymaganych przez domenę porządkowanie i nie profilu użytkownika całego.

Do komunikacji i propagowanie danych asynchronicznie mikrousług, aby mogła mieć spójność ostateczną, może korzystać z dowolnego protokołu. Jak wspomniano wcześniej, można użyć zdarzenia integracji przy użyciu magistrali zdarzeń lub broker lub możesz nawet użyć HTTP przez sondowanie innych usług, zamiast tego komunikatu. Nie ma znaczenia. Jest ważne zasada nie chcesz tworzyć synchroniczne zależności między mikrousługi.

W poniższych sekcjach opisano wiele stylów komunikacji, można rozważyć użycie w aplikacji opartych na mikrousługach.

## <a name="communication-styles"></a>Style komunikacji

Istnieje wiele protokołów i opcji, których można użyć do komunikacji, w zależności od typu komunikacji, którego chcesz użyć. Jeśli używasz mechanizm komunikacji/odpowiedzi na podstawie żądań synchronicznych protokoły, takie jak metody HTTP i REST są najbardziej typowy, zwłaszcza, jeśli podczas publikowania usług poza klaster hosta lub mikrousług platformy Docker. Jeśli masz podczas komunikacji między usługami wewnętrznie (w klastrze hosta lub mikrousług platformy Docker), można również użyć mechanizmów komunikacji format binarny (na przykład WCF, za pomocą protokołu TCP i format binarny i komunikacji zdalnej usługi Service Fabric). Alternatywnie można użyć mechanizmów komunikacji asynchronicznej, oparta na komunikatach na przykład protokół AMQP.

Dostępne są także wiele formatów wiadomości, takich jak JSON lub XML lub nawet binarne formatach, które mogą być bardziej wydajne. Jeśli Twoje wybrany format binarny nie jest to standard, prawdopodobnie nie jest dobrym pomysłem jest publicznie publikowania usług z wykorzystaniem tego formatu. Można użyć formatu niestandardowego dla wewnętrznej komunikacji między mikrousługi. Można to zrobić, podczas komunikacji między mikrousługami w ramach platformy Docker lub mikrousług hosta klastra (koordynatorów platformy Docker lub Azure Service Fabric) lub dla aplikacji klienckich własności, komunikujące się z mikrousług.

### <a name="requestresponse-communication-with-http-and-rest"></a>Żądanie/odpowiedź komunikacji przy użyciu tych protokołów REST

Kiedy klient używa komunikacji żądanie/odpowiedź, wysyła żądanie do usługi, a następnie procesów informatycznych żądanie i wysyła odpowiedź z powrotem. Komunikat żądania/odpowiedzi szczególnie dobrze jest odpowiedni dla wykonywanie zapytań o dane w czasie rzeczywistym interfejsu użytkownika (interfejs użytkownika na żywo) z aplikacji klienckich. W związku z tym w ramach architektury mikrousługi prawdopodobnie użyjesz ten mechanizm komunikacji dla większości zapytań, jak pokazano w rysunek 4 – 16.

![Może używać komunikacji żądania/odpowiedzi dla zapytań na żywo, gdy klient wysyła żądanie do bramy interfejsu API, przy założeniu, że odpowiedź z mikrousług zostaną odebrane w bardzo krótkim czasie.](./media/image16.png)

**Rysunek 4 – 16**. Za pomocą komunikacji żądania/odpowiedzi HTTP (synchronicznego lub asynchronicznego)

Kiedy klient używa komunikacji żądanie/odpowiedź, zakłada się, że odpowiedzi zostaną dostarczone w krótkim czasie, zwykle niecałej sekundy lub kilka sekund co najwyżej. Opóźnione odpowiedzi potrzebne do zaimplementowania komunikacji asynchronicznej w oparciu o [wzorców obsługi komunikatów](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) i [komunikatów technologii](https://en.wikipedia.org/wiki/Message-oriented_middleware), który jest różne podejście, które firma Microsoft opisano w następnej sekcji.

Popularnym stylem architektury do komunikacji żądania/odpowiedzi jest [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). To podejście jest oparty na i ściśle sprzężonych, [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokół, stosujących zleceń HTTP, takich jak GET, POST i umieścić. POZOSTAŁE elementy są najczęściej używane podejście architektoniczne komunikacji podczas tworzenia usługi. Podczas tworzenia usługi internetowego interfejsu API platformy ASP.NET Core, można zaimplementować usług REST.

Brak dodatkowych wartości podczas korzystania z usług REST protokołu HTTP jako języka definicji interfejsu. Na przykład jeśli używasz [metadanych Swagger](https://swagger.io/) do opisania interfejsu API usługi, można użyć narzędzia, które generują wycinków klienta, które można bezpośrednio odkrycie i używanie usługi.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Martin Fowler. Model dojrzałości Leonard** opis modelu REST. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Struktury swagger** oficjalna witryna. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Wypychania i komunikację w czasie rzeczywistym, w oparciu o HTTP

Inną możliwością (zwykle dla różnych celów niż REST) jest w czasie rzeczywistym i jeden do wielu komunikacji z platformami wyższego poziomu, takich jak [ASP.NET SignalR](https://www.asp.net/signalr) i protokoły, takie jak [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Jak pokazano na rysunku 4-17, w czasie rzeczywistym komunikacji HTTP oznacza, że można do kodu serwera wypychania zawartości do połączonych klientów, jak dane będą dostępne, zamiast serwera oczekiwania dla klientów dane nowego żądania.

![SignalR to dobry sposób osiągnięcia komunikację w czasie rzeczywistym do wypychania zawartości do klientów z serwerów zaplecza.](./media/image17.png)

**Rysunek 4-17**. Jeden do jednego komunikatów asynchronicznych w czasie rzeczywistym komunikacji

Ponieważ komunikacji w czasie rzeczywistym, aplikacje klienckie niemal natychmiast wyświetlić zmiany. Zazwyczaj jest to obsługiwane przez protokół, takich jak funkcja WebSockets, za pomocą wielu połączeń funkcji WebSockets (po jednej na klienta). Typowym przykładem jest, gdy usługa jednocześnie komunikuje się zmian w wyniku gry sportowe, aby wiele aplikacji sieci web klienta.

>[!div class="step-by-step"]
>[Poprzednie](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[dalej](asynchronous-message-based-communication.md)
