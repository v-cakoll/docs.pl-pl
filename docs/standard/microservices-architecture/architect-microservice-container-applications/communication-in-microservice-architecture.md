---
title: "Komunikacja w ramach architektury mikrousługi"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Komunikacja w architektury architektury mikrousługi"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f373119f4d221745063688a9a5211d5ae11598b7
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="communication-in-a-microservice-architecture"></a>Komunikacja w ramach architektury mikrousługi

W aplikacji wbudowanymi uruchomiony w ramach jednego procesu składniki wywołać za pomocą metody poziom języka lub wywołania funkcji. Te mogą być silnie sprzężona w przypadku tworzenia obiektów z kodem (na przykład `new ClassName()`), lub może być wywoływany w sposób rozdzielonymi, jeśli używasz iniekcji zależności odwołując abstrakcje zamiast konkretnych obiektów. W obu przypadkach obiekty są uruchomione w ramach tego samego procesu. Wyzwanie największych podczas zmiany z wbudowanymi aplikacji do aplikacji opartych na mikrousług znajduje się w zmiana mechanizm komunikacji. Konwersja bezpośrednie wywołania metody w trakcie do wywołań RPC usługi spowoduje, że chatty i nie sprawną komunikację, który nie będzie wykonywać również w rozproszonych środowiskach. Wyzwania prawidłowo projektowania Rozproszony system wystarczająco również wiadomo, czy jest parzysta canon, znany jako [Fallacies rozproszonego przetwarzania danych](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) która wyświetla założenia, które deweloperzy tworzą często podczas przenoszenia z wbudowanymi projekty do rozproszonej.

Brak nie jedno rozwiązanie, ale niektóre. Jedno rozwiązanie obejmuje izolowanie możliwie mikrousług biznesowych. Następnie użyj komunikacji asynchronicznej między wewnętrzny mikrousług i Zastąp szczegółowych komunikacji, typowy wewnątrz procesu komunikacji między obiektami z dopasowanymi gruboziarnisty komunikacji. Można to zrobić przez grupowanie połączeń i przez zwrócenie danych, który agreguje wyniki wielu wywołań wewnętrznego, do klienta.

Aplikacja mikrousług jest rozproszonej systemami na wiele procesów lub usług, zwykle nawet między wieloma serwerami lub hostów. Każde wystąpienie usługi jest zwykle procesu. W związku z tym usługi musi współdziałać przy użyciu protokołu komunikacji między procesami, takich jak HTTP, protokołu AMQP lub binarne protokołu podobnie jak protokół TCP, w zależności od charakteru każdej usługi.

Społeczność mikrousługi wspiera założeń "[inteligentne punkty końcowe i potoków bez](http://simplicable.com/new/smart-endpoints-and-dumb-pipes)." To hasło reklamowe zachęca projekt, który się całkowicie niezależna, jak to możliwe, między mikrousług i jak spójne w obrębie jednego mikrousługi. Zgodnie z opisem, własnych danych i jego własnej logiki domeny jest właścicielem poszczególnych mikrousługi. Ale mikrousług tworzenie aplikacji na trasie są zwykle po prostu choreographed przy użyciu komunikacji REST zamiast złożonych protokołów, takich jak usługi WS -\* i elastyczne komunikacji sterowane zdarzeniami zamiast scentralizowane orchestrators-Business procesu.

Dwa najczęściej używane protokoły są żądania/odpowiedzi HTTP z zasobu interfejsów API (podczas wykonywania zapytania większość wszystkich) i aktualizuje lekkie asynchroniczną obsługę wiadomości podczas komunikacji między wieloma mikrousług. Te są co omówiono bardziej szczegółowo w poniższych sekcjach.

## <a name="communication-types"></a>Typy komunikacji

Usługi i klienta może komunikować się za pomocą wielu różnych typów komunikacji w każdej z nich przeznaczonych dla różnych scenariuszy i cele. Początkowo tych typów komunikacyjnych mogą być klasyfikowane w dwóch osiach.

Pierwsza oś jest zdefiniowanie, jeśli protokół jest synchroniczna lub asynchroniczna:

-   Protokół synchronicznego. HTTP jest protokołem synchronicznego. Klient wysyła żądanie i czeka na odpowiedź z usługi. Która jest niezależna od wykonanie kodu klienta, który może być synchroniczne (wątek jest zablokowany) lub asynchroniczna (wątek nie jest zablokowany, a odpowiedź ostatecznie osiągną wywołanie zwrotne). Należy koniecznie zwrócić uwagę jest synchroniczne jest protokół (HTTP/HTTPS) oraz kod klienta można kontynuować tylko jego zadań, po odebraniu odpowiedzi serwera HTTP.

-   Protokół asynchroniczny. Innych protokołów, takich jak AMQP (protokół obsługiwany przez wiele systemów operacyjnych i środowisk chmury) używają komunikatów asynchronicznych. Nadawca klienta kodu lub wiadomości zwykle bez oczekiwania na odpowiedź. Po prostu wysyła komunikat jako podczas wysyłania wiadomości do kolejki RabbitMQ lub innych brokera komunikatów.

Jeśli komunikacja ma jeden odbiornik lub wieloma odbiornikami, jest zdefiniowanie drugiej osi:

-   Jeden odbiornik. Każde żądanie muszą zostać przetworzone przez dokładnie jednego odbiornika lub usługi. Przykładem tej komunikacji jest [wzorzec polecenia](https://en.wikipedia.org/wiki/Command_pattern).

-   Wiele odbiorników. Każdego żądania mogą być przetwarzane przez zero, aby wiele odbiorników. Ten typ komunikacji musi być asynchroniczne. Na przykład [publikowania/subskrypcji](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mechanizmu używane we wzorcach, takich jak [sterowane zdarzeniami architektura](http://microservices.io/patterns/data/event-driven-architecture.html). To jest oparta na brokera magistrali zdarzenia interfejsu lub komunikat podczas propagowania aktualizacje danych między wieloma mikrousług za pomocą zdarzeń; Zazwyczaj jest implementowane za pośrednictwem usługi service bus lub podobne artefaktów, takich jak [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) za pomocą [tematy i subskrypcje](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Aplikacja mikrousługi często używają kombinacji tych stylów komunikacji. Najczęściej spotykanym typem jest jeden odbiornik komunikacji przy użyciu protokołu synchroniczne, takich jak HTTP/HTTPS podczas wywoływania regularnej HTTP interfejsu API sieci Web. Mikrousług zwykle także używać protokoły komunikacji asynchronicznej między mikrousług.

Osie te są warto wiedzieć, masz jasności mechanizmów komunikacyjnych, ale nie są ważne problemy podczas kompilowania mikrousług. Asynchroniczne rodzaj wykonywanie wątków klienta nawet asynchroniczne charakter wybranego protokołu są ważne punkty składników podczas integrowania mikrousług. Co *jest* ważna jest możliwość integracji z mikrousług asynchronicznie przy zachowaniu niezależność mikrousług, jak wyjaśniono w poniższej sekcji.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Integracja asynchroniczne mikrousługi wymusza Autonomia mikrousługi firmy

Jak wspomniano, należy koniecznie zwrócić podczas tworzenia aplikacji opartych na mikrousług jest sposób zintegrować z mikrousług. W idealnym przypadku należy zminimalizować komunikację między mikrousług wewnętrznego. Mniej komunikacja między mikrousług, tym lepiej. Jednak, w wielu przypadkach trzeba będzie jakiś sposób integracji mikrousług. Gdy trzeba to zrobić, reguła krytycznego tutaj jest że komunikacji między mikrousług powinny być asynchroniczne. Nie oznacza że, trzeba przypisać protokół (na przykład asynchronicznej obsługi wiadomości i synchroniczne HTTP). Oznacza tylko komunikacji między mikrousług powinno być wykonywane tylko przez asynchronicznie propagowanie danych, ale nie należy w ramach operacji żądania/odpowiedzi HTTP początkowej usługi zależą od innych mikrousług wewnętrznego.

Jeśli to możliwe nigdy nie są zależne od komunikacji synchroniczne (żądania/odpowiedzi) między wieloma mikrousług, nawet dla zapytań. Celem każdego mikrousługi ma być autonomiczne i konsumenta klienta, nawet jeśli są inne usługi, które są częścią aplikacji end-to-end działa lub złej kondycji. Jeśli uważasz, że potrzebne do wywoływania z jednego mikrousługi innych mikrousług (np. wykonywania żądań HTTP kwerendy danych) w, aby mieć możliwość zapewnienia odpowiedzi do aplikacji klienckiej, masz architekturę, której nie będzie odporności, gdy niektóre mikrousług zakończyć się niepowodzeniem.

Ponadto mających zależności HTTP między mikrousług, takich jak tworzenie długo cykle żądań i odpowiedzi protokołu HTTP z żądania łańcuchów, jak pokazano w pierwszej części 4 rysunek-15, nie tylko sprawia, że Twoje mikrousług nie autonomicznego, ale również jest ich wydajności wpływ na jak jedną z usług w tym łańcuchu nie działa prawidłowo. 

Im bardziej dodać synchroniczne zależności między mikrousług, takich jak żądania zapytania, pogarsza się wraz z pobiera całkowity czas odpowiedzi dla aplikacji klienckich.

![](./media/image15.png)

**Rysunek 4 – 15**. Wzorce układ i wzorce komunikacji między mikrousług

Jeśli Twoje mikrousługi musi podnieść dodatkowe działania w innym mikrousługi, jeśli to możliwe, nie należy wykonywać tej akcji synchronicznie i w ramach oryginalnego żądania i odpowiedzi operacji mikrousługi. Zamiast tego, czy asynchronicznie (przy użyciu wiadomości asynchroniczne lub zdarzeń integracji, kolejek, itd.). Ale, jak to możliwe, nie wywołuj akcji synchronicznie jako część oryginalnego synchronicznych operacji żądania i odpowiedzi.

I w końcu (i jest to, gdzie większość problemów wystąpić podczas kompilowania mikrousług), jeśli Twoje początkowej mikrousługi musi dane, które pierwotnie jest własnością innych mikrousług, nie należy polegać na wysyłania żądań synchronicznych dla tych danych. Zamiast tego replikacji lub propagację danych (tylko atrybuty, które są potrzebne) do bazy danych usługi początkowej spójność ostateczna (zazwyczaj przy użyciu zdarzeń integracji, zgodnie z objaśnieniem w kolejnych sekcjach).

Jak wspomniano wcześniej w sekcji [identyfikujące model domeny granice dla każdej mikrousługi](#identifying-domain-model-boundaries-for-each-microservice), duplikowania niektórych danych między kilka mikrousług nie jest niepoprawna projektu — przeciwnie, gdy czynności, które można przetworzyć danych do określonego języka lub warunki dodatkowe domeny lub kontekst ograniczone. Na przykład w [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) aplikacji masz mikrousługi, o nazwie identity.api, który jest odpowiedzialny za większość danych użytkownika z jednostką o nazwie użytkownika. Jednak gdy należy przechowywać dane o użytkowniku w mikrousługi porządkowanie zostaną zapisane jako inny element o nazwie nabywców. Jednostka nabywców współużytkuje tej samej tożsamości z oryginalnej jednostki użytkownika, ale może mieć tylko kilka atrybutów wymagane przez domenę porządkowanie i nie profilu użytkownika całego.

Do komunikacji i propagowanie danych asynchronicznie mikrousług uzyskanie spójność ostateczna może Użyj dowolnego protokołu. Jak wspomniano, można użyć zdarzenia integracji przy użyciu komunikatów brokera lub nawet można użyć protokołu HTTP zamiast Sondując innych usług lub magistrali zdarzeń. Nie ma znaczenia. Reguła ważne jest tworzą synchroniczne zależności między Twojej mikrousług.

W poniższych sekcjach opisano wiele stylów komunikacji, można rozważyć użycie w aplikacji na podstawie mikrousługi.

## <a name="communication-styles"></a>Style komunikacji

Istnieje wiele protokołów i opcje, które można użyć do komunikacji, w zależności od typu komunikacji, który ma być używany. Jeśli używasz mechanizm komunikacji/odpowiedzi na podstawie żądań synchronicznych protokołów, takich jak HTTP i REST podejścia są najbardziej rozpowszechnione, szczególnie w przypadku publikowania usług poza klaster hosta lub mikrousługi Docker. Jeśli są komunikacji między usługami wewnętrznego (w klastrze hosta lub mikrousług Docker) można także użyć mechanizmy komunikacji format binarny (na przykład sieci szkieletowej usług zdalnych lub przy użyciu protokołu TCP i format binarny WCF). Alternatywnie można użyć mechanizmów komunikacji asynchronicznej, oparta na komunikatach, takich jak protokołu AMQP.

Istnieją również wiele formatów wiadomości, takie jak JSON i XML lub nawet binarne formatów, które może być skuteczniejsza. Jeśli wybrany formatu binarnego nie jest standardem, prawdopodobnie nie jest dobrym pomysłem jest publicznie publikowania usług przy użyciu tego formatu. Można użyć formatu niestandardowych do wewnętrznej komunikacji między Twojej mikrousług. Można to zrobić, podczas komunikacji między mikrousług Docker hosta lub mikrousługi klastra (Docker orchestrators lub sieć szkieletowa usług Azure), lub dla aplikacji klienckich zastrzeżonych, którzy komunikują się mikrousług.

### <a name="requestresponse-communication-with-http-and-rest"></a>Żądanie/odpowiedź komunikacji HTTP i REST 

Gdy klient korzysta z komunikacji żądanie/odpowiedź, wysyła żądanie do usługi, a następnie usługa przetwarza żądania i odsyła odpowiedź. Komunikat żądania/odpowiedzi najlepiej nadaje się do wyszukiwanie danych w czasie rzeczywistym interfejsu użytkownika (interfejs użytkownika na żywo) z aplikacji klienta. W związku z tym architektury mikrousługi prawdopodobnie użyjesz ten mechanizm komunikacji dla większości zapytań, jak pokazano w rysunek 4-16.

![](./media/image16.png)

**Rysunek 4 – 16**. Za pomocą komunikacji żądanie i odpowiedź HTTP (synchronicznego lub asynchronicznego)

Gdy klient korzysta z komunikacji żądanie/odpowiedź, zakłada się, że odpowiedzi zostaną dostarczone w krótkim czasie, zazwyczaj mniej niż 1 sekunda lub kilka sekund co najwyżej. Opóźnione odpowiedzi, należy wdrożyć na podstawie komunikacji asynchronicznej [wiadomości wzorce](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) i [wiadomości technologii](https://en.wikipedia.org/wiki/Message-oriented_middleware), który jest inny sposób, który objaśnia, możemy w następnej sekcji.

Popularne styl architektury komunikacji żądanie i odpowiedź jest [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Takie podejście jest oparta na i ściśle połączony, [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) protokołu, obejmującego zleceń HTTP, takich jak GET, POST i PUT. REST jest najczęściej używane podejście architektury komunikacji podczas tworzenia usługi. Podczas opracowywania usługi interfejsu API platformy ASP.NET Core sieci Web, które można zaimplementować usługi REST.

Brak dodatkowych wartości podczas korzystania z usług REST protokołu HTTP jako języka definicji interfejsu. Na przykład jeśli używasz [Swagger metadanych](http://swagger.io/) do opisu interfejsu API usługi, można użyć narzędzia, które Generowanie klas zastępczych klienta, które można bezpośrednio odkrycie i używanie usługi.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Pole Fowler. Lesiak dojrzałości modelu.** Opis modelu REST.
    [*http://martinfowler.com/articles/richardsonMaturityModel.html*](http://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** Oficjalna witryna.
    [*http://swagger.io/*](http://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Wypychania i w czasie rzeczywistym komunikacji HTTP w oparciu

Inną możliwością (zazwyczaj do różnych celów niż REST) jest w czasie rzeczywistym i jeden do wielu komunikacji z wyższego poziomu platform, takich jak [ASP.NET SignalR](https://www.asp.net/signalr) i protokołów, takich jak [Websocket](https://en.wikipedia.org/wiki/WebSocket).

Jak pokazano na rysunku 4-17, w czasie rzeczywistym komunikacji HTTP oznacza, że można do kodu serwera wypychanie zawartość do dołączonych klientów w miarę wprowadzania danych, a nie serwera, poczekaj, aż klientowi żądanie nowych danych.

![](./media/image17.png)

**Rysunek 4-17**. Mapowanie komunikatów asynchronicznych w czasie rzeczywistym komunikacji

Ponieważ komunikacji znajduje się w czasie rzeczywistym, aplikacje klienckie Pokaż zmiany niemal natychmiast. Zazwyczaj jest to obsługiwane przez protokół, takie jak protokół WebSockets, za pomocą wielu połączeń Websocket (po jednym dla każdego klienta). Typowym przykładem jest, gdy usługa jednocześnie komunikuje się zmiany w wyniku gry sportowych, aby wiele aplikacji sieci web klienta.


>[!div class="step-by-step"]
[Previous] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) [Next] (asynchronous-message-based-communication.md)
