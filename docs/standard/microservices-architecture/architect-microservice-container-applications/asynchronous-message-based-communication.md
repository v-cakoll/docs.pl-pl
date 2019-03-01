---
title: Oparta na komunikatach komunikacji asynchronicznej
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Oparta na komunikatach komunikacji asynchronicznej jest podstawowe pojęcie w architekturze mikrousług, ponieważ jest najlepszym sposobem pozostaw mikrousług niezależne od siebie nawzajem podczas również został beeing zsynchronizowany, po pewnym czasie.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 10e2a05e8fa33ecbf2aec2432c0cf51204fc35c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969365"
---
# <a name="asynchronous-message-based-communication"></a>Oparta na komunikatach komunikacji asynchronicznej

Asynchroniczna Obsługa komunikatów i komunikacji oparte na zdarzeniach mają kluczowe znaczenie, gdy propagowanie zmian przez wiele mikrousług i ich modeli powiązanych domeny. Jak wspomniano wcześniej w dyskusji mikrousług i ograniczone konteksty (usług łączności biznesowej), modele (użytkownika, klient, produkt, konta itp.) może mieć różne znaczenie w różnych mikrousług lub usług łączności biznesowej. Oznacza to, że zmianach, należy jakiś sposób, aby uzgadniać zmiany w różnych modelach. To rozwiązanie jest spójność i oparte na zdarzeniach komunikacji asynchronicznej obsługi komunikatów w oparciu.

Korzystając z komunikatów, procesy komunikują się przez wymianę wiadomości asynchronicznie. Klient wysyła polecenie lub żądanie do usługi wysyłając wiadomość. Jeśli usługa musi odpowiedzieć, wysyła inny komunikat do klienta. Ponieważ jest oparta na komunikatach komunikacji, klient przyjmie założenie, że odpowiedzi nie będzie natychmiast odebrane i że może być brak odpowiedzi na wszystkich.

Komunikat składa się nagłówka (metadane, takie jak informacje identyfikacyjne lub zabezpieczeń) i treść. Komunikaty są zwykle wysyłane za pośrednictwem protokołów asynchronicznych, takich jak AMQP.

Preferowany infrastrukturę dla tego typu komunikacji w społeczności mikrousług jest broker uproszczone komunikatów, który jest inny niż brokerów duże i koordynatorów używane w SOA. Broker komunikatów uproszczone infrastruktura jest zazwyczaj "bez," działają wyłącznie jako broker komunikatów, za pomocą prostych implementacji, takich jak RabbitMQ lub skalowalne usługi Service bus w chmurze, taka jak Azure Service Bus. W tym scenariuszu większość "eleganckie" myśleć nadal znajduje się punkty końcowe, które tworzenie i korzystanie z komunikatów — czyli w mikrousług.

Inną regułę, które należy wykonać, jak to możliwe, jest używanie tylko asynchronicznej obsługi komunikatów między usługami wewnętrznej i do użycia synchronicznego komunikacji (na przykład HTTP) tylko z poziomu aplikacji klienta do usługi frontonu (bramy interfejsu API oraz pierwszy poziom mikrousługi).

Istnieją dwa rodzaje komunikacji asynchronicznej obsługi komunikatów: komunikacja oparta na komunikatach jednego odbiornika i wiele odbiorników komunikacji oparta na komunikatach. Poniższe sekcje zawierają szczegółowe informacje o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikacja oparta na komunikatach jednego odbiornika

Oparta na komunikatach komunikacji asynchronicznej za pomocą jednego odbiornika oznacza, że ma bezpośredniej komunikacji, który zapewnia komunikat z dokładnie jednym konsumentów, która odczytuje z kanału, a komunikat jest przetwarzany tylko raz. Istnieją jednak szczególnych sytuacjach. Na przykład w system w chmurze, która próbuje automatycznie odzyskać sprawność po awarii, ten sam komunikat można było wysłać wiele razy. Z powodu sieci lub inne błędy klient musi umożliwiać ponowne wysyłanie wiadomości, a serwer musi przeprowadzić wdrażanie operacji być idempotentne, aby przetworzyć określonego komunikatu o tylko raz.

Komunikacja oparta na komunikatach jednego odbiornika szczególnie dobrze nadaje się do wysyłania poleceń asynchronicznego z jednego mikrousług innemu pokazany w rysunek 4-18, to podejście pokazano.

Po rozpoczęciu wysyłania oparta na komunikatach komunikacji (albo za pomocą poleceń lub zdarzenia), należy unikać mieszania oparta na komunikatach komunikacji przy użyciu synchronicznej komunikacji HTTP.

![Odbieranie komunikatów asynchronicznych pojedynczych mikrousług](./media/image18.png)

**Rysunek 4-18**. Odbieranie komunikatów asynchronicznych pojedynczych mikrousług

Należy pamiętać, że przypadku polecenia pochodzących z aplikacji klienckich, ich można zaimplementować jako synchroniczna poleceń protokołu HTTP. Należy użyć poleceń oparta na komunikatach, gdy będziesz potrzebować skalowalności, lub gdy użytkownik jest już w procesie biznesowym oparta na komunikatach.

## <a name="multiple-receivers-message-based-communication"></a>Komunikacja oparta na komunikatach wielu odbiorców

Co jest bardziej elastyczne podejście można również używany był mechanizm publikowania/subskrybowania, tak, aby komunikacja od nadawcy, dostępna dla mikrousług dodatkowe subskrybenta lub do aplikacji zewnętrznych. W związku z tym, pomaga postępuj zgodnie z [otwarty/zamknięty zasady](https://en.wikipedia.org/wiki/Open/closed_principle) wysyłania usługi. W ten sposób dodatkowe subskrybentów można dodawać w przyszłości, bez konieczności modyfikowania usługi nadawcy.

Użycie opcji publikowania/subskrybowania komunikacji, być może używasz interfejs magistrali zdarzeń do publikowania zdarzeń w celu każdy subskrybent.

## <a name="asynchronous-event-driven-communication"></a>Komunikacji asynchronicznej oparte na zdarzeniach

Korzystając z komunikacji asynchronicznej oparte na zdarzeniach, mikrousługi publikuje zdarzenie integracji, gdy coś, co się dzieje w jego domenie i innym mikrousług musi wiedzieć, jak zmiany ceny w mikrousługach katalogu produktów. Dodatkowe mikrousług subskrybują zdarzenia, dzięki czemu mogą one odbierać je asynchronicznie. Jeśli tak się stanie, odbiorców może aktualizować własne jednostki domeny, co może powodować więcej zdarzeń integracji do opublikowania. Ten system publikowania/subskrybowania zwykle odbywa się przy użyciu implementacji magistrali zdarzeń. Magistrali zdarzeń mogą służyć jako abstrakcji lub interfejs, za pomocą interfejsu API, który ma potrzebne chcesz subskrybować zdarzenia i publikowania zdarzeń. Magistrali zdarzeń może również zawierać jeden lub więcej implementacje oparte na każdego brokera między procesami i obsługi komunikatów, takich jak kolejki komunikatów lub usługi service bus, który obsługuje komunikacji asynchronicznej i modelu publikowania/subskrybowania.

Jeśli system używa prowadzona przez zdarzenia integracji spójność ostateczną, zaleca się, że to podejście jest jasno całkowicie użytkownikowi końcowemu. System nie należy użyć metody, która naśladuje zdarzenia integracji, takich jak SignalR lub systemy sondowania z klienta. Użytkownik końcowy i właściciel firmy trzeba jawnie Uwzględniaj spójność ostateczną w systemie i należy pamiętać w wielu przypadkach firma nie ma żadnych problem tego podejścia, tak długo, jak jest jawne. Jest to ważne, ponieważ użytkownicy mogą wyniki powinny być widoczne niektóre natychmiast i nie może to się zdarzyć spójności ostatecznej.

Jak wspomniano wcześniej w [problemy i rozwiązania dotyczące rozproszonego zarządzania danymi](distributed-data-management.md) sekcji, można użyć zdarzenia integracji do zaimplementowania zadań biznesowych, obejmujących wiele mikrousług. W związku z tym będziesz mieć spójności ostatecznej między tymi usługami. Transakcja ostatecznie spójną składa się z kolekcją rozproszonych działań. W każdej akcji powiązanych mikrousług zaktualizuje jednostkę domeny i publikuje inne zdarzenie integracji, która wywołuje następnej akcji w obrębie tego samego zadania biznesowe end-to-end.

To ważny punkt jest, możesz zechcieć do komunikacji z wielu mikrousług, które mają subskrypcję do tego samego zdarzenia. Aby to zrobić, można użyć publikowania/subskrybowania komunikatów na podstawie oparte na zdarzeniach komunikacji, jak pokazano w rysunek 4-19. Ten mechanizm publikowania/subskrybowania jest wyłącznie w architekturze mikrousług. Jest on podobny do sposobu [ograniczone konteksty](https://martinfowler.com/bliki/BoundedContext.html) w DDD skontaktować się lub sposób Propagacja aktualizacje z bazy danych zapisu do bazy danych do odczytu w [odpowiedzialności polecenia i zapytania podziału (CQRS)](https://martinfowler.com/bliki/CQRS.html)wzorzec architektury. Celem jest zapewnienie spójności ostatecznej między wieloma źródłami danych w rozproszonym systemie.

![W przypadku komunikacji asynchronicznej oparte na zdarzeniach jeden mikrousług publikuje zdarzenia magistrali zdarzeń i wielu mikrousług, co może być subskrybowana przez, Otrzymuj powiadomienia i działają na niej.](./media/image19.png)

**Rysunek 4-19**. Komunikacja komunikatów oparte na zdarzeniach asynchronicznych

Twoja implementacja określi, co protokołu na potrzeby komunikacji oparte na zdarzeniach, oparta na komunikatach. [Protokół AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) może pomóc w osiągnięciu niezawodnej komunikacji umieszczonych w kolejce.

Korzystając z magistrali zdarzeń, warto użyć poziom abstrakcji (np. interfejsu magistrali zdarzenia) oparty na powiązane implementacji klas z kodu za pomocą interfejsu API z brokera komunikatów, takie jak [RabbitMQ](https://www.rabbitmq.com/) lub service bus, podobnie jak [Usługi azure Service Bus z obsługą tematów](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatywnie można umożliwiają wyższego poziomu magistrali usług, takich jak NServiceBus, MassTransit lub Brighter sformułowania usługi Service bus event i publikowania/subskrybowania systemu.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Uwaga dotycząca komunikatów technologii dla systemów produkcyjnych.

Technologii obsługi komunikatów, która jest dostępna dla implementacji usługi Service bus zdarzenie abstrakcyjne są na różnych poziomach. Na przykład produktów, takich jak RabbitMQ (komunikatów transportu brokera) i usługi Azure Service Bus znajdują się na niższym poziomie niż innych produktów, takich jak NServiceBus, MassTransit lub Brighter, która może działać na podstawie RabbitMQ i usługi Azure Service Bus. Wybór zależy od liczby rozbudowanych funkcji na poziomie aplikacji i skalowalności out-of--box, czego potrzebujesz do aplikacji. Do wykonania po prostu magistrali zdarzeń weryfikacji koncepcji dla swojego środowiska programowania, jak zostało to zrobione, w tym przykładzie w ramach aplikacji eShopOnContainers proste wdrażanie na podstawie RabbitMQ uruchomione w kontenerze platformy Docker może wystarczyć.

Jednak w przypadku o kluczowym znaczeniu oraz systemów produkcyjnych, wymagających hyper skalowalność, warto do oceny usługi Azure Service Bus. Dla abstrakcji wysokiego poziomu i funkcje, które ułatwić opracowywanie zawartości aplikacji rozproszonych firma Microsoft zaleca oceny innych magistrali usługi komercyjnych i typu open source, takich jak NServiceBus MassTransit i Brighter. Oczywiście można tworzyć własne funkcje usługi service bus na podstawie technologii niższego poziomu, takie jak RabbitMQ i platformy Docker. Ale działające nadmiar kosztów za dużo aplikacji niestandardowych przedsiębiorstwa.

## <a name="resiliently-publishing-to-the-event-bus"></a>Publikowanie odpornych magistrali zdarzeń

Wyzwanie w przypadku implementowania architektury oparte na zdarzeniach między wiele mikrousług jest sposób niepodzielne aktualizacji stanu w oryginalnym mikrousług podczas odpornych publikowania jej zdarzenia powiązane integracji do magistrali zdarzeń, w jakiś sposób na podstawie transakcje. Poniżej przedstawiono kilka sposobów, aby to osiągnąć, chociaż może to być także dodatkowe metody.

- Za pomocą transakcyjne kolejki (w oparciu o usługi DTC) takich jak usługi MSMQ. (Jednak to podejście starszej wersji.)

- Za pomocą [wyszukiwania dziennik transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Przy użyciu pełnej [określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) wzorca.

- Za pomocą [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/): Tabela transakcji bazy danych jako kolejki komunikatów, który ma być base, aby składnik Twórca zdarzenia, który może utworzyć zdarzenia i opublikujesz je.

Tematy dodatkowe, które należy wziąć pod uwagę podczas korzystania z komunikacji asynchronicznej są idempotentność wiadomości i deduplikacji wiadomości. Te tematy zostały omówione w sekcji [Implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) później w tym przewodniku.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Aktivita typu EventDriven komunikatów** \
  [*http://soapatterns.org/design_patterns/event_driven_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

- **Publikowania/subskrybowania kanału** \
  [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

- **Udi Dahan. Sklarowanego CQRS** \
  [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

- **Polecenie and Query Responsibility Segregation (CQRS)** \
  [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- **Komunikacja między ograniczone konteksty** \
  [*https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)*](https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10))

- **Spójność ostateczna** \
  [*https://en.wikipedia.org/wiki/Eventual_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Jimmy Bogard. Refaktoryzacja kierunku odporności na błędy: Ocena sprzężenia** \
  [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

>[!div class="step-by-step"]
>[Poprzednie](communication-in-microservice-architecture.md)
>[dalej](maintain-microservice-apis.md)
