---
title: Komunikacja w ramach architektury mikrousługi
description: Poznaj różne sposoby komunikacji między mikrousługami, zrozumienie implikacji synchronicznych i asynchronicznych sposobów.
ms.date: 01/30/2020
ms.openlocfilehash: f2d6e78966bb7d5f481de6db0ab1dcfe2812a1b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401656"
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikacja w ramach architektury mikrousługi

W aplikacji monolityczne uruchomionej w jednym procesie składniki wywołać siebie za pomocą metody na poziomie języka lub wywołania funkcji. Mogą one być silnie sprzężona, jeśli tworzysz `new ClassName()`obiekty z kodem (na przykład), lub mogą być wywoływane w sposób niepowiązanych, jeśli używasz iniekcji zależności, odwołując się abstrakcje, a nie wystąpienia konkretnych obiektów. Tak czy inaczej, obiekty są uruchomione w ramach tego samego procesu. Największym wyzwaniem podczas zmiany z aplikacji monolityczne do aplikacji opartej na mikrousługach polega na zmianie mechanizmu komunikacji. Bezpośrednia konwersja z wywołań metody w procesie do wywołań RPC do usług spowoduje chatty i nie efektywnej komunikacji, która nie będzie działać dobrze w środowiskach rozproszonych. Wyzwania związane z projektowaniem rozproszonego systemu są na tyle dobrze znane, że istnieje nawet kanon znany jako [Błędy rozproszonego przetwarzania,](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) który wymienia założenia, które deweloperzy często przyjmują podczas przechodzenia z monolitycznych do rozproszonych projektów.

Nie ma jednego rozwiązania, ale kilka. Jedno rozwiązanie polega na izolowaniu mikrousług biznesowych, jak to możliwe. Następnie należy użyć komunikacji asynchronicznej między mikrousług wewnętrznych i zastąpić komunikację drobnoziarnistą, która jest typowa w komunikacji wewnątrz procesu między obiektami z grubsze ziarnistej komunikacji. Można to zrobić przez grupowanie wywołań i zwracanie danych, które agreguje wyniki wielu wywołań wewnętrznych, do klienta.

Aplikacja oparta na mikrousługach jest systemem rozproszonym działana na wielu procesach lub usługach, zwykle nawet na wielu serwerach lub hostach. Każde wystąpienie usługi jest zazwyczaj procesem. W związku z tym usługi muszą współdziałać przy użyciu protokołu komunikacji między procesami, takich jak HTTP, AMQP lub protokołu binarnego, takich jak TCP, w zależności od charakteru każdej usługi.

Społeczność mikrousług promuje filozofię "[inteligentnych punktów końcowych i niepomyte potoki](https://simplicable.com/new/smart-endpoints-and-dumb-pipes)" To hasło zachęca projekt, który jest tak oddzielone, jak to możliwe między mikrousług i jak bardziej zgodne, jak to możliwe w ramach jednej mikrousługi. Jak wyjaśniono wcześniej, każda mikrousługa jest właścicielem własnych danych i własnej logiki domeny. Jednak mikrousługi tworzące aplikację end-to-end są zwykle po prostu choreografia przy użyciu\* komunikacji REST, a nie złożonych protokołów, takich jak WS- i elastyczne zdarzenia oparte na komunikacji zamiast scentralizowanych procesów biznesowych-orchestrators.

Dwa często używane protokoły są żądanie HTTP/odpowiedź z interfejsami API zasobów (podczas wykonywania zapytań przede wszystkim) i lekkich komunikatów asynchronicznych podczas przekazywania aktualizacji w wielu mikrousług. Są one wyjaśnione bardziej szczegółowo w poniższych sekcjach.

## <a name="communication-types"></a>Typy komunikacji

Klient i usługi mogą komunikować się za pośrednictwem wielu różnych typów komunikacji, z których każdy jest przeznaczony dla innego scenariusza i celów. Początkowo tego typu komunikaty można sklasyfikować na dwóch osiach.

Pierwsza oś określa, czy protokół jest synchroniczny lub asynchroniczny:

- protokół synchroniczny. HTTP jest protokołem synchronicznym. Klient wysyła żądanie i czeka na odpowiedź z usługi. To jest niezależne od wykonania kodu klienta, które mogą być synchroniczne (wątek jest zablokowany) lub asynchroniczne (wątek nie jest zablokowany, a odpowiedź zostanie ostatecznie dotrzeć do wywołania wywołania. Ważną kwestią jest to, że protokół (HTTP/HTTPS) jest synchroniczny, a kod klienta może kontynuować swoje zadanie tylko po odebraniu odpowiedzi serwera HTTP.

- Protokół asynchroniczny. Inne protokoły, takie jak AMQP (protokół obsługiwany przez wiele systemów operacyjnych i środowisk w chmurze) używają komunikatów asynchronicznych. Kod klienta lub nadawca wiadomości zwykle nie czeka na odpowiedź. Po prostu wysyła wiadomość, jak podczas wysyłania wiadomości do kolejki RabbitMQ lub innego brokera wiadomości.

Druga oś określa, czy komunikacja ma jeden odbiornik lub wiele odbiorników:

- Pojedynczy odbiornik. Każde żądanie musi być przetworzone przez dokładnie jeden odbiornik lub usługę. Przykładem tej komunikacji jest [wzorzec polecenia](https://en.wikipedia.org/wiki/Command_pattern).

- Wiele odbiorników. Każde żądanie może być przetwarzane przez zero do wielu odbiorników. Ten typ komunikacji musi być asynchroniczny. Przykładem jest mechanizm [publikowania/subskrybowania](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) używany w wzorcach, takich jak [architektura sterna zdarzeniami.](https://microservices.io/patterns/data/event-driven-architecture.html) Jest to oparte na interfejsie magistrali zdarzeń lub brokera komunikatów podczas propagowania aktualizacji danych między wieloma mikrousługami za pośrednictwem zdarzeń; jest zwykle implementowane za pośrednictwem magistrali usług lub podobnego artefaktu, takiego jak [usługa Azure Service Bus](https://azure.microsoft.com/services/service-bus/) przy użyciu [tematów i subskrypcji.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)

Aplikacja oparta na mikrousługach często używa kombinacji tych stylów komunikacji. Najczęstszym typem jest komunikacja z jednym odbiorcą z protokołem synchronicznym, takim jak HTTP/HTTPS podczas wywoływania zwykłej usługi HTTP interfejsu API sieci Web. Mikrousługi zazwyczaj używają protokołów obsługi wiadomości do komunikacji asynchronicznej między mikrousługami.

Te osie są dobre wiedzieć, więc masz jasność co do możliwych mechanizmów komunikacji, ale nie są one ważne problemy podczas tworzenia mikrousług. Ani asynchroniczny charakter wykonywania wątku klienta, ani asynchroniczny charakter wybranego protokołu nie są ważnymi punktami podczas integracji mikrousług. Co *jest* ważne jest możliwość integracji mikrousług asynchronicznie przy zachowaniu niezależności mikrousług, jak wyjaśniono w poniższej sekcji.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Integracja mikrousług asynchronicznych wymusza autonomię mikrousługi

Jak wspomniano, ważnym punktem podczas tworzenia aplikacji opartej na mikrousługach jest sposób integracji mikrousług. W idealnym przypadku należy spróbować zminimalizować komunikację między mikrousług wewnętrznych. Im mniej komunikacji między mikrousługami, tym lepiej. Ale w wielu przypadkach trzeba będzie jakoś zintegrować mikrousług. Gdy trzeba to zrobić, krytyczną regułą w tym miejscu jest, że komunikacja między mikrousług ami powinny być asynchroniczne. Nie oznacza to, że trzeba użyć określonego protokołu (na przykład asynchronicznego przesyłania wiadomości w porównaniu z synchronicznym protokołem HTTP). Oznacza to po prostu, że komunikacja między mikrousługami powinna odbywać się tylko przez propagowanie danych asynchronicznie, ale staraj się nie polegać na innych mikrousług wewnętrznych jako część operacji żądania/odpowiedzi HTTP usługi początkowej.

Jeśli to możliwe, nigdy nie zależą od komunikacji synchronicznej (żądanie/odpowiedź) między wieloma mikrousługami, nawet dla zapytań. Celem każdej mikrousługi ma być autonomiczne i dostępne dla konsumenta klienta, nawet jeśli inne usługi, które są częścią aplikacji end-to-end są w dół lub w złej kondycji. Jeśli uważasz, że trzeba nawiązać wywołanie z jednej mikrousługi do innych mikrousług (takich jak wykonywanie żądania HTTP dla zapytania danych), aby móc zapewnić odpowiedź na aplikację kliencką, masz architekturę, która nie będzie odporna, gdy niektóre mikrousługi nie powiedzie się.

Ponadto o zależności HTTP między mikrousługami, jak podczas tworzenia długich żądań/odpowiedzi cykli z łańcuchami żądań HTTP, jak pokazano w pierwszej części rysunku 4-15, nie tylko sprawia, że mikrousługi nie autonomiczne, ale także ich wydajność ma wpływ, jak tylko jedna z usług w tym łańcuchu nie działa dobrze.

Im więcej można dodać synchroniczne zależności między mikrousługami, takich jak żądania zapytań, tym gorszy ogólny czas odpowiedzi pobiera dla aplikacji klienckich.

![Diagram przedstawiający trzy typy komunikacji między mikrousługami.](./media/communication-in-microservice-architecture/sync-vs-async-patterns-across-microservices.png)

**Rysunek 4-15**. Anti-wzorce i wzorce w komunikacji między mikrousługami

Jak pokazano na powyższym diagramie, w komunikacji synchronicznej "łańcuch" żądań jest tworzony między mikrousług podczas obsługi żądania klienta. Jest to anty-wzór. W mikrousługach komunikacji asynchronicznej użyj komunikatów asynchronicznych lub sondowania http do komunikowania się z innymi mikrousługami, ale żądanie klienta jest obsługiwane od razu.

Jeśli mikrousługi musi podnieść dodatkową akcję w innej mikrousługi, jeśli to możliwe, nie należy wykonywać tej akcji synchronicznie i jako część oryginalnego żądania mikrousługi i operacji odpowiedzi. Zamiast tego zrób to asynchronicznie (przy użyciu asynchronicznych komunikatów lub zdarzeń integracji, kolejek itp.). Jednak w miarę możliwości nie należy wywoływać akcji synchronicznie jako część oryginalnego synchronicznego żądania i operacji odpowiedzi.

I na koniec (i to jest, gdy większość problemów pojawiają się podczas tworzenia mikrousług), jeśli początkowemikrousługi wymaga danych, które są pierwotnie własnością innych mikrousług, nie polegać na dokonywanie synchroniczne żądania dla tych danych. Zamiast tego replikuj lub propagować te dane (tylko potrzebne atrybuty) do bazy danych usługi początkowej przy użyciu spójności ostatecznej (zazwyczaj przy użyciu zdarzeń integracji, jak wyjaśniono w nadchodzących sekcjach).

Jak wspomniano wcześniej w identyfikacji granic modelu domeny dla każdej sekcji [mikrousługi,](identify-microservice-domain-model-boundaries.md) powielanie niektórych danych w kilku mikrousług nie jest niepoprawny projekt — wręcz przeciwnie, podczas wykonywania, że można przetłumaczyć dane na określony język lub warunki tej dodatkowej domeny lub ograniczony kontekst. Na przykład w [aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) masz mikrousługę o nazwie, `identity-api` która jest odpowiedzialna za większość `User`danych użytkownika z jednostką o nazwie . Jednak gdy trzeba przechowywać dane o `Ordering` użytkowniku w mikrousługi, należy `Buyer`przechowywać go jako inną jednostkę o nazwie . Jednostka `Buyer` udostępnia tę samą `User` tożsamość oryginalnej jednostce, ale może mieć `Ordering` tylko kilka atrybutów wymaganych przez domenę, a nie cały profil użytkownika.

Można użyć dowolnego protokołu do komunikowania się i propagacji danych asynchronicznie przez mikrousług w celu uzyskania spójności ostatecznej. Jak wspomniano, można użyć zdarzeń integracji przy użyciu magistrali zdarzeń lub brokera komunikatów lub można nawet użyć protokołu HTTP, sondując inne usługi zamiast tego. To nie ma znaczenia. Ważną zasadą jest, aby nie tworzyć synchroniczne zależności między mikrousług.

W poniższych sekcjach wyjaśniono wiele stylów komunikacji, które można rozważyć przy użyciu w aplikacji opartej na mikrousługach.

## <a name="communication-styles"></a>Style komunikacji

Istnieje wiele protokołów i opcji, których można używać do komunikacji, w zależności od typu komunikacji, którego chcesz użyć. Jeśli używasz synchronicznego mechanizmu komunikacji opartego na żądaniu/odpowiedzi, protokoły, takie jak podejścia HTTP i REST, są najczęściej, szczególnie jeśli publikujesz swoje usługi poza hostem platformy Docker lub klastrem mikrousług. Jeśli komunikujesz się między usługami wewnętrznie (w obrębie hosta platformy Docker lub klastra mikrousług), można również użyć mechanizmów komunikacji w formacie binarnym (takich jak WCF przy użyciu protokołu TCP i formatu binarnego). Alternatywnie można użyć asynchronicznych, opartych na komunikatach mechanizmów komunikacji, takich jak AMQP.

Istnieje również wiele formatów wiadomości, takich jak JSON lub XML, a nawet formatów binarnych, które mogą być bardziej wydajne. Jeśli wybrany format binarny nie jest standardem, prawdopodobnie nie jest dobrym pomysłem publiczne publikowanie usług w tym formacie. Można użyć niestandardowego formatu do wewnętrznej komunikacji między mikrousługami. Można to zrobić podczas komunikowania się między mikrousług w obrębie hosta platformy Docker lub klastra mikrousług (na przykład koordynatorów platformy Docker) lub dla zastrzeżonych aplikacji klienckich, które komunikują się z mikrousług.

### <a name="requestresponse-communication-with-http-and-rest"></a>Komunikacja żądania/odpowiedzi z HTTP i REST

Gdy klient używa komunikacji żądania/odpowiedzi, wysyła żądanie do usługi, a następnie usługa przetwarza żądanie i odsyła odpowiedź. Komunikacja żądania/odpowiedzi jest szczególnie dobrze nadaje się do wykonywania zapytań danych dla interfejsu użytkownika w czasie rzeczywistym (interfejs użytkownika na żywo) z aplikacji klienckich. W związku z tym w architekturze mikrousług prawdopodobnie użyjesz tego mechanizmu komunikacji dla większości zapytań, jak pokazano na rysunku 4-16.

![Diagram przedstawiający komunikaty żądania/odpowiedzi dla zapytań i aktualizacji na żywo.](./media/communication-in-microservice-architecture/request-response-comms-live-queries-updates.png)

**Rysunek 4-16**. Korzystanie z komunikacji żądania/odpowiedzi HTTP (synchroniczne lub asynchroniczne)

Gdy klient używa komunikacji żądania/odpowiedzi, zakłada, że odpowiedź zostanie nadejdzie w krótkim czasie, zazwyczaj mniej niż sekundę lub co najwyżej kilka sekund. W przypadku opóźnionych odpowiedzi należy zaimplementować komunikację asynchroniczną na podstawie [wzorców obsługi wiadomości](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) i [technologii obsługi wiadomości](https://en.wikipedia.org/wiki/Message-oriented_middleware), co jest innym podejściem, które wyjaśniamy w następnej sekcji.

Popularnym stylem architektonicznym komunikacji żądania/odpowiedzi jest [REST.](https://en.wikipedia.org/wiki/Representational_state_transfer) Takie podejście jest oparte na i ściśle powiązane z protokołem [HTTP,](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) obejmując zlecenia HTTP, takie jak GET, POST i PUT. REST jest najczęściej używanym podejściem komunikacji architektonicznej podczas tworzenia usług. Usługi REST można zaimplementować podczas opracowywania ASP.NET podstawowych usług interfejsu API sieci Web.

Istnieje dodatkowa wartość podczas korzystania z usług HTTP REST jako języka definicji interfejsu. Na przykład jeśli używasz [metadanych Swagger](https://swagger.io/) do opisania interfejsu API usługi, można użyć narzędzi, które generują wycinki klienta, które mogą bezpośrednio odnajdowania i korzystania z usług.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. Richardson Maturity Model** Opis modelu REST. \
  <https://martinfowler.com/articles/richardsonMaturityModel.html>

- **Puszyć** Oficjalna strona. \
  <https://swagger.io/>

### <a name="push-and-real-time-communication-based-on-http"></a>Komunikacja push i w czasie rzeczywistym oparta na http

Inną możliwością (zwykle do innych celów niż REST) jest komunikacja w czasie rzeczywistym i jeden do wielu z ramami wyższego poziomu, takimi jak [ASP.NET SignalR](https://www.asp.net/signalr) i protokołami, takimi jak [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Jak pokazuje rysunek 4-17, komunikacja HTTP w czasie rzeczywistym oznacza, że kod serwera może wypychać zawartość do połączonych klientów w miarę udostępniania danych, zamiast czekać na klienta, aby zażądać nowych danych.

![Diagram przedstawiający komunikatory wypychania i rzeczywistym oparte na SignalR.](./media/communication-in-microservice-architecture/one-to-many-communication.png)

**Rysunek 4-17**. Asynchroniczny komunikat w czasie rzeczywistym

SignalR to dobry sposób na uzyskanie komunikacji w czasie rzeczywistym w celu wypychania treści do klientów z serwera zaplecza. Ponieważ komunikacja jest w czasie rzeczywistym, aplikacje klienckie pokazują zmiany niemal natychmiast. Jest to zwykle obsługiwane przez protokół, taki jak WebSockets, przy użyciu wielu połączeń WebSockets (jeden na klienta). Typowym przykładem jest, gdy usługa komunikuje zmiany wyniku gry sportowej do wielu aplikacji sieci Web klienta jednocześnie.

>[!div class="step-by-step"]
>[Poprzedni](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
>[następny](asynchronous-message-based-communication.md)
