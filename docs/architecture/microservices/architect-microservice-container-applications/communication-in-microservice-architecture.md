---
title: Komunikacja w ramach architektury mikrousługi
description: Poznaj różne sposoby komunikacji między mikrousługami, opisując implikacje synchronicznych i asynchronicznych metod.
ms.date: 09/20/2018
ms.openlocfilehash: add1ff74bee456e0fa7f2fb54d2cf4e536402db4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738039"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikacja w ramach architektury mikrousługi

W aplikacji monolitycznej uruchomionej w pojedynczym procesie składniki są wywoływane nawzajem przy użyciu metody lub wywołania funkcji na poziomie języka. Te elementy mogą być silnie powiązane, jeśli tworzysz obiekty z kodem (na przykład `new ClassName()`) lub można je wywołać w oddzielnym sposób, jeśli używasz iniekcji zależności przez odwołanie do abstrakcyjnych, a nie wystąpień konkretnych obiektów. W obu przypadkach obiekty są uruchomione w ramach tego samego procesu. Największe wyzwanie w przypadku zmiany z aplikacji monolitycznej na aplikację opartą na mikrousługach polega na zmianie mechanizmu komunikacji. Bezpośrednia konwersja z metod wywołujących wywołania wywołań RPC do usług spowoduje rozmowę i nie wydajną komunikację, która nie będzie działać w środowiskach rozproszonych. Problemy związane z projektowaniem rozproszonego systemu są dostatecznie znane, że istnieje nawet znana jako [fallacies rozproszonego przetwarzania](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) danych, która zawiera listę założeń, które deweloperzy często tworzą podczas przechodzenia z monolitycznych do projektów rozproszonych .

Nie ma jednego rozwiązania, ale kilka. Jedno rozwiązanie wymaga odizolowania mikrousług, jak to możliwe. Następnie należy użyć asynchronicznej komunikacji między mikrousługami wewnętrznymi i zamienić szczegółową komunikację, która jest typowa w komunikacji wewnątrz procesów między obiektami z grubszą komunikacją. Można to zrobić przez grupowanie wywołań i zwrócenie danych, które agregują wyniki wielu wywołań wewnętrznych do klienta.

Aplikacja oparta na mikrousługach jest systemem rozproszonym uruchomionym w wielu procesach lub usługach, zwykle nawet na wielu serwerach lub hostach. Każde wystąpienie usługi jest zazwyczaj procesem. W związku z tym usługi muszą korzystać z protokołu komunikacji między procesami, takiego jak HTTP, AMQP lub protokołu binarnego, takiego jak TCP, w zależności od rodzaju każdej usługi.

Społeczność mikrousług promuje się do "[inteligentnych punktów końcowych i potoków Dumb](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" to slogan zachęca do zaprojektowania, jak to możliwe, między mikrousługami i możliwie jak najbardziej spójny w ramach jednej mikrousługi. Jak wyjaśniono wcześniej, każda mikrousługa posiada własne dane i własną logikę domeny. Jednak mikrousługi składające się na kompleksową aplikację zwykle choreographed przy użyciu komunikacji REST, a nie złożonych protokołów, takich jak WS-\* i elastyczna komunikacja oparta na zdarzeniach, a nie scentralizowana Proces biznesowy — koordynatorzy.

Dwa najczęściej używane protokoły to żądania HTTP/odpowiedzi z interfejsami API zasobów (w przypadku wykonywania zapytań w większości) oraz lekkie komunikaty asynchroniczne podczas komunikacji między wieloma mikrousługami. Wyjaśniono je szczegółowo w poniższych sekcjach.

## <a name="communication-types"></a>Typy komunikacji

Klient i usługi mogą komunikować się za pomocą wielu różnych rodzajów komunikacji, a każdy z nich ma inny scenariusz i cele. Początkowo typy komunikacji mogą być klasyfikowane na dwie osie.

Pierwsza oś definiuje, czy protokół jest synchroniczny, czy asynchroniczny:

- Protokół synchroniczny. HTTP jest protokołem synchronicznym. Klient wysyła żądanie i czeka na odpowiedź z usługi. Jest to niezależne od wykonania kodu klienta, które może być synchroniczne (wątek jest zablokowany) lub asynchronicznie (wątek nie jest zablokowany, a odpowiedź w końcu dociera do wywołania zwrotnego). Ważną kwestią jest to, że protokół (HTTP/HTTPS) jest synchroniczny, a kod klienta może kontynuować jego zadanie tylko wtedy, gdy odbierze odpowiedź serwera HTTP.

- Protokół asynchroniczny. Inne protokoły, takie jak AMQP (protokół obsługiwany przez wiele systemów operacyjnych i środowisk w chmurze), używają komunikatów asynchronicznych. Kod klienta lub nadawca wiadomości zwykle nie czeka na odpowiedź. Po prostu wysyła komunikat jako wysyłany do kolejki RabbitMQ lub dowolnego innego brokera komunikatów.

Druga oś definiuje, czy komunikacja ma jednego odbiorcę, czy wielu odbiorników:

- Pojedynczy odbiornik. Każde żądanie musi być przetwarzane przez dokładnie jednego odbiorcę lub usługę. Przykładem tej komunikacji jest [wzorzec poleceń](https://en.wikipedia.org/wiki/Command_pattern).

- Wielu odbiorników. Każde żądanie może być przetwarzane przez zero do wielu odbiorców. Ten typ komunikacji musi być asynchroniczny. Przykładem jest mechanizm [publikowania/subskrybowania](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) używany w wzorcach, takich jak [Architektura sterowana zdarzeniami](https://microservices.io/patterns/data/event-driven-architecture.html). Jest to oparte na interfejsie usługi Event Bus lub brokerze komunikatów podczas propagowania aktualizacji danych między wieloma mikrousługami za pośrednictwem zdarzeń; zwykle jest to implementowane za pośrednictwem usługi Service Bus lub podobnego artefaktu, takiego jak [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) , za pomocą [tematów i subskrypcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikacja oparta na mikrousługach często używa kombinacji tych stylów komunikacji. Najczęściej spotykanym typem jest komunikacja pojedynczego odbiornika z protokołem synchronicznym, na przykład HTTP/HTTPS podczas wywoływania zwykłej usługi HTTP interfejsu API sieci Web. Mikrousługi zazwyczaj używają protokołów obsługi komunikatów do komunikacji asynchronicznej między mikrousługami.

Te osie są dobre, aby mieć pewność, że masz świadomość możliwości komunikacji, ale nie są to istotne kwestie podczas tworzenia mikrousług. W przypadku integrowania mikrousług nie jest ani asynchroniczny charakter wykonywania wątku klienta, ani asynchroniczny charakter wybranego protokołu. Ważne *jest* , aby umożliwić integrację mikrousług asynchronicznie, jednocześnie zapewniając niezależność mikrousług, jak wyjaśniono w poniższej sekcji.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Asynchroniczna integracja mikrousług wymusza autonomię mikrousług

Jak wspomniano, ważnym punktem podczas kompilowania aplikacji opartych na mikrousługach jest sposób integrowania mikrousług. W idealnym przypadku należy podjąć próbę zminimalizowania komunikacji między mikrousługami wewnętrznymi. Im mniej komunikacji między mikrousługami, tym lepiej. Jednak w wielu przypadkach trzeba będzie w jakiś sposób zintegrować mikrousługi. Jeśli trzeba to zrobić, reguła krytyczna polega na tym, że komunikacja między mikrousługami powinna być asynchroniczna. Nie oznacza to, że należy używać określonego protokołu (na przykład asynchronicznych komunikatów i synchronicznego protokołu HTTP). Oznacza to, że komunikacja między mikrousługami powinna odbywać się tylko przez propagowanie danych asynchronicznie, ale nie zależy od innych mikrousług wewnętrznych jako części operacji żądania HTTP/odpowiedzi usługi początkowej.

Jeśli to możliwe, nigdy nie zależą od komunikacji synchronicznej (żądanie/odpowiedź) między wieloma mikrousługami, nawet w przypadku zapytań. Celem każdej mikrousługi jest autonomiczna i dostępna dla konsumenta klienta, nawet jeśli inne usługi, które są częścią kompleksowej aplikacji, są wyłączone lub w złej kondycji. Jeśli uważasz, że musisz wykonać wywołanie z jednej mikrousługi do innych mikrousług (takich jak wykonywanie żądania HTTP dla zapytania dotyczącego danych), aby zapewnić odpowiedź do aplikacji klienckiej, masz architekturę, która nie będzie odporna na awarie niektórych mikrousług.

Ponadto, jeśli istnieją zależności HTTP między mikrousługami, takie jak podczas tworzenia cykli długotrwałych żądań/odpowiedzi z łańcuchami żądań HTTP, jak pokazano w pierwszej części rysunku 4-15, nie tylko mikrousługi są NIEAUTONOMICZNE, ale również ich wydajność jest wpływ na to, jak tylko jedna z usług w tym łańcuchu nie działa prawidłowo.

Im większa jest liczba synchronicznych zależności między mikrousługami, takimi jak żądania zapytań, tym gorszy jest całkowity czas odpowiedzi dla aplikacji klienckich.

![Diagram przedstawiający trzy typy komunikacji między mikrousługami.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Rysunek 4-15**. Antywzorce i wzorce komunikacji między mikrousługami

Jak pokazano na powyższym diagramie, w przypadku komunikacji synchronicznej "łańcuch" żądań jest tworzony między mikrousługami przy zachowaniu żądania klienta. Jest to antywzorców. W przypadku mikrousług komunikacji asynchronicznej używa komunikatów asynchronicznych lub sondowania protokołu HTTP do komunikacji z innymi mikrousługami, ale żądanie klienta jest od razu obsługiwane.

Jeśli mikrousługa musi podnieść dodatkową akcję w innej mikrousłudze, jeśli to możliwe, nie należy wykonywać tej akcji synchronicznie i w ramach oryginalnego żądania mikrousługi i operacji odpowiedzi. Zamiast tego należy to zrobić asynchronicznie (przy użyciu komunikatów asynchronicznych lub zdarzeń integracji, kolejek itp.). Jednak tak dużo jak to możliwe, nie wywołuj akcji synchronicznie w ramach oryginalnej operacji synchronicznego żądania i odpowiedzi.

A wreszcie (w przypadku, gdy większość problemów występuje podczas tworzenia mikrousług), jeśli początkowa mikrousługa wymaga danych, które są pierwotnie własnością innych mikrousług, nie należy polegać na przesyłaniu żądań synchronicznych dla tych danych. Zamiast tego należy replikować lub propagować te dane (tylko potrzebne atrybuty) do bazy danych usługi początkowej przy użyciu spójności ostatecznej (zazwyczaj przy użyciu zdarzeń integracji, jak wyjaśniono w kolejnych sekcjach).

Jak wspomniano wcześniej w sekcji [Identyfikowanie granic modelu domeny dla każdej mikrousługi](identify-microservice-domain-model-boundaries.md), duplikowanie niektórych danych z kilku mikrousług nie jest niewłaściwym projektem — w przeciwieństwie do tego, że można przetłumaczyć dane na konkretną język lub warunki tej dodatkowej domeny lub kontekstu ograniczonego. Na przykład w [aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) masz mikrousługę o nazwie Identity. API, która jest odpowiedzialna za większość danych użytkownika z jednostką o nazwie user. Jednak w przypadku konieczności przechowywania danych o użytkowniku w ramach mikrousługi porządkowania należy przechowywać ją jako inną jednostkę o nazwie kupc. Jednostka kupca udostępnia taką samą tożsamość z oryginalną jednostką użytkownika, ale może mieć tylko kilka atrybutów wymaganych przez domenę kolejności, a nie cały profil użytkownika.

Można użyć dowolnego protokołu do komunikacji i propagowania danych asynchronicznie w mikrousługach w celu zapewnienia spójności ostatecznej. Jak wspomniano, można użyć zdarzeń integracji przy użyciu magistrali zdarzeń lub brokera komunikatów lub można nawet użyć protokołu HTTP przez sondowanie innych usług. Nie ma znaczenia. Ważna zasada polega na tym, że nie można utworzyć synchronicznych zależności między mikrousługami.

W poniższych sekcjach opisano wiele stylów komunikacji, których można użyć w aplikacji opartej na mikrousługach.

## <a name="communication-styles"></a>Style komunikacji

Istnieje wiele protokołów i opcji, których można użyć do komunikacji, w zależności od typu komunikacji, który ma być używany. Jeśli używasz mechanizmu komunikacji synchronicznej na żądanie/odpowiedź, protokoły takie jak HTTP i REST są najbardziej typowe, szczególnie w przypadku publikowania usług poza hostem platformy Docker lub klastrem mikrousług. Jeśli komunikujesz się między usługami wewnętrznie (w ramach klastra platformy Docker lub w klastrze mikrousług), możesz również użyć mechanizmów komunikacji formatu binarnego (takich jak WCF przy użyciu protokołu TCP i formatu binarnego). Alternatywnie można używać asynchronicznych mechanizmów komunikacji opartych na komunikatach, takich jak AMQP.

Istnieje również wiele formatów komunikatów, takich jak JSON lub XML, a nawet formatów binarnych, które mogą być bardziej wydajne. Jeśli wybrany format binarny nie jest standardem, prawdopodobnie nie jest dobrym pomysłem na publiczne publikowanie Twoich usług przy użyciu tego formatu. Do komunikacji wewnętrznej między mikrousługami można używać niestandardowego formatu. Można to zrobić podczas komunikacji między mikrousługami w ramach hosta platformy Docker lub klastra mikrousług (na przykład programu Docker Orchestrator) lub dla zastrzeżonych aplikacji klienckich, które komunikują się z mikrousługami.

### <a name="requestresponse-communication-with-http-and-rest"></a>Komunikacja żądania/odpowiedzi z użyciem protokołu HTTP i REST

Gdy klient używa komunikacji żądania/odpowiedzi, wysyła żądanie do usługi, a następnie usługa przetwarza żądanie i wysyła odpowiedź. Komunikacja żądania/odpowiedzi jest szczególnie przydatna w przypadku wykonywania zapytań dotyczących danych dla interfejsu użytkownika w czasie rzeczywistym (interfejsu użytkownika na żywo) z aplikacji klienckich. W związku z tym w architekturze mikrousług prawdopodobnie użyjesz tego mechanizmu komunikacji dla większości zapytań, jak pokazano na rysunku 4-16.

![Diagram przedstawiający formy komunikacji żądania/odpowiedzi dla zapytań i aktualizacji na żywo.](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Rysunek 4-16**. Używanie komunikacji żądania/odpowiedzi HTTP (synchroniczna lub asynchroniczna)

Gdy klient korzysta z komunikacji żądania/odpowiedzi, zakłada, że odpowiedź zostanie w krótkim czasie, zazwyczaj krótsza niż sekunda lub kilka sekund. W przypadku opóźnionych odpowiedzi należy zaimplementować asynchroniczną komunikację opartą na [wzorcach obsługi komunikatów](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) i [technologiach obsługi komunikatów](https://en.wikipedia.org/wiki/Message-oriented_middleware), która jest innym podejściem, które wyjaśnimy w następnej sekcji.

Popularnym stylem architektury dla komunikacji żądania/odpowiedzi jest [rest](https://en.wikipedia.org/wiki/Representational_state_transfer). To podejście jest oparte na, i ściśle sprzężone z, protokołem [http](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) , obejmujące zlecenia http, takie jak GET, post i Put. REST to najczęściej używane podejście do komunikacji architektonicznej podczas tworzenia usług. Usługi REST można zaimplementować podczas tworzenia ASP.NET Core usług interfejsu API sieci Web.

W przypadku korzystania z usług REST protokołu HTTP jako języka definicji interfejsu nie ma dodatkowej wartości. Na przykład w przypadku użycia [metadanych struktury Swagger](https://swagger.io/) do OPISYWANIA interfejsu API usługi można użyć narzędzi generujących replikę klienta, które mogą bezpośrednio wykrywać i korzystać z usług.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Fowlera Martin. Model dojrzałości Richardson** opis modelu Rest. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- Struktura **Swagger** Oficjalna lokacja. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Komunikacja wypychana i w czasie rzeczywistym oparta na protokole HTTP

Kolejną możliwością (zwykle w różnych celach niż REST) jest komunikacja w czasie rzeczywistym i jeden-do-wielu z platformami wyższego poziomu, takimi jak [ASP.NET sygnalizujący](https://www.asp.net/signalr) i protokoły, takie jak [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Jak pokazano na rysunku 4-17, komunikacja HTTP w czasie rzeczywistym oznacza, że można mieć kod serwerowy wypychania zawartości do podłączonych klientów, ponieważ dane staną się dostępne, zamiast czekać, aż klient zażąda nowych danych.

![Diagram przedstawiający wypychanie i formy komunikacji w czasie rzeczywistym na podstawie sygnału.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Rysunek 4-17**. Komunikacja asynchroniczna między wiadomościami w czasie rzeczywistym

Sygnalizujący to dobry sposób na osiągnięcie komunikacji w czasie rzeczywistym na potrzeby wypychania zawartości do klientów z serwera zaplecza. Ze względu na to, że komunikacja jest w czasie rzeczywistym, aplikacje klienckie pokazują zmiany niemal natychmiast. Jest to zwykle obsługiwane przez protokół, taki jak WebSockets, przy użyciu wielu połączeń usługi WebSockets (jeden na klienta). Typowym przykładem jest to, że usługa komunikuje się ze zmianą w wyniku gry sportowe z wieloma aplikacjami sieci Web klienta jednocześnie.

>[!div class="step-by-step"]
>[Poprzedni](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[dalej](asynchronous-message-based-communication.md)
