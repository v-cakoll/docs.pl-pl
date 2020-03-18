---
title: Asynchroniczna komunikacja oparta na komunikatach
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Asynchroniczne komunikaty oparte na komunikatach jest podstawową koncepcją w architekturze mikrousług, ponieważ jest to najlepszy sposób, aby zachować mikrousług niezależnych od siebie, a także są synchronizowane w końcu.
ms.date: 09/20/2018
ms.openlocfilehash: 84eaf70178cce91a86dae8a55badb0b4ddd6a7c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73454231"
---
# <a name="asynchronous-message-based-communication"></a>Asynchroniczna komunikacja oparta na komunikatach

Asynchroniczne wiadomości i komunikacji opartej na zdarzeniach mają kluczowe znaczenie podczas propagowania zmian w wielu mikrousług i powiązanych modeli domeny. Jak wspomniano wcześniej w dyskusji mikrousług i ograniczone konteksty (BC), modele (użytkownik, klient, produkt, konto, itp.) może oznaczać różne rzeczy do różnych mikrousług lub kontrolerów bcs. Oznacza to, że w przypadku wystąpienia zmian, trzeba jakiś sposób, aby uzgadniać zmiany w różnych modelach. Rozwiązaniem jest spójność ostateczna i komunikacja oparta na zdarzeniach oparta na komunikatach asynchronicznych.

Podczas korzystania z obsługi wiadomości procesy komunikują się, wymieniając wiadomości asynchronicznie. Klient wydaje polecenie lub żądanie do usługi, wysyłając mu wiadomość. Jeśli usługa musi odpowiedzieć, wysyła inną wiadomość z powrotem do klienta. Ponieważ jest to komunikacja oparta na wiadomościach, klient zakłada, że odpowiedź nie zostanie odebrana natychmiast i że może nie być żadnej odpowiedzi.

Wiadomość składa się z nagłówka (metadanych, takich jak informacje identyfikacyjne lub informacje zabezpieczające) i treści. Wiadomości są zwykle wysyłane za pośrednictwem protokołów asynchronicznych, takich jak AMQP.

Preferowana infrastruktura dla tego typu komunikacji w społeczności mikrousług jest brokerem komunikatów uproszczonych, który różni się od dużych brokerów i koordynatorów używanych w SOA. W brokera wiadomości uproszczone infrastruktury jest zazwyczaj "głupi", działając tylko jako broker komunikatów, z prostych implementacji, takich jak RabbitMQ lub skalowalnej magistrali usług w chmurze, takich jak usługa Azure Service Bus. W tym scenariuszu większość "inteligentnego" myślenia nadal żyje w punktach końcowych, które produkują i zużywają komunikaty, czyli w mikrousługach.

Inną regułą, którą należy spróbować wykonać, w miarę możliwości, jest używanie tylko asynchronicznych komunikatów między usługami wewnętrznymi i używanie komunikacji synchronicznej (takiej jak HTTP) tylko z aplikacji klienckich do usług frontonu (bramy interfejsu API plus pierwszy poziom mikrousług).

Istnieją dwa rodzaje komunikacji asynchronicznej wiadomości: komunikacja oparta na komunikatach pojedynczego odbiornika i komunikacja oparta na komunikatach wielu odbiorników. W poniższych sekcjach podano szczegółowe informacje na ich temat.

## <a name="single-receiver-message-based-communication"></a>Komunikacja oparta na komunikatach z jednym odbiornikiem

Komunikacja asynchroniczna oparta na komunikatach z jednym odbiornikiem oznacza, że komunikacja typu punkt-punkt dostarcza komunikat dokładnie do jednego z konsumentów, który odczytuje z kanału i że wiadomość jest przetwarzana tylko raz. Istnieją jednak szczególne sytuacje. Na przykład w systemie chmury, który próbuje automatycznie odzyskać z powodu awarii, ten sam komunikat może być wysyłany wiele razy. Ze względu na awarie sieci lub inne błędy klient musi mieć możliwość ponowienia próby wysłania wiadomości, a serwer musi zaimplementować operację, aby być idempotentnością, aby przetworzyć określony komunikat tylko raz.

Komunikacja oparta na komunikatach pojedynczego odbiorcy jest szczególnie dobrze nadaje się do wysyłania poleceń asynchronicznych z jednej mikrousługi do innej, jak pokazano na rysunku 4-18, który ilustruje to podejście.

Po rozpoczęciu wysyłania komunikacji opartej na wiadomościach (z poleceniami lub zdarzeniami) należy unikać mieszania komunikacji opartej na wiadomościach z synchroniczną komunikacją HTTP.

![Pojedyncza mikrousługa odbierająca komunikat asynchroniczny](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Rysunek 4-18**. Pojedyncza mikrousługa odbierająca komunikat asynchroniczny

Należy zauważyć, że gdy polecenia pochodzą z aplikacji klienckich, mogą być implementowane jako polecenia synchroniczne HTTP. Polecenia oparte na komunikatach należy używać, gdy potrzebujesz większej skalowalności lub gdy jesteś już w procesie biznesowym opartym na wiadomościach.

## <a name="multiple-receivers-message-based-communication"></a>Komunikacja oparta na komunikatach wielu odbiorników

Jako bardziej elastyczne podejście, można również użyć mechanizmu publikowania/subskrybowania, dzięki czemu komunikacja z nadawcą będzie dostępna dla dodatkowych mikrousług subskrybenta lub aplikacji zewnętrznych. W ten sposób pomaga przestrzegać [zasady otwartej /zamkniętej](https://en.wikipedia.org/wiki/Open/closed_principle) w usłudze wysyłania. W ten sposób można dodać dodatkowych subskrybentów w przyszłości bez konieczności modyfikowania usługi nadawcy.

Korzystając z komunikacji publikowania/subskrybowania, może być używany interfejs magistrali zdarzeń do publikowania zdarzeń do dowolnego subskrybenta.

## <a name="asynchronous-event-driven-communication"></a>Asynchroniczna komunikacja oparta na zdarzeniach

Korzystając z komunikacji asynchronicznej opartej na zdarzeniach, mikrousługa publikuje zdarzenie integracji, gdy coś dzieje się w jego domenie, a inna mikrousługa musi być tego świadoma, jak zmiana ceny w mikrousłudze katalogu produktów. Dodatkowe mikrousługi subskrybują zdarzenia, dzięki czemu mogą odbierać je asynchronicznie. W takim przypadku odbiorcy mogą aktualizować własne jednostki domeny, co może spowodować więcej zdarzeń integracji, które mają zostać opublikowane. Ten system publikowania/subskrybowania jest zwykle wykonywane przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń może być zaprojektowana jako abstrakcja lub interfejs za pomocą interfejsu API, który jest potrzebny do subskrybowania lub anulowania subskrypcji zdarzeń i publikowania zdarzeń. Magistrala zdarzeń może mieć co najmniej jedną implementacje na podstawie dowolnego brokera międzyprocesowego i obsługi wiadomości, takiego jak kolejka obsługi wiadomości lub magistrala usług, która obsługuje komunikację asynchroniczną i model publikowania/subskrybowania.

Jeśli system używa spójności ostatecznej napędzane przez zdarzenia integracji, zaleca się, że takie podejście jest całkowicie jasne dla użytkownika końcowego. System nie powinien używać podejścia, które naśladuje zdarzenia integracji, takie jak SignalR lub sondowania systemów z klienta. Użytkownik końcowy i właściciel firmy muszą jawnie objąć spójność ostateczną w systemie i zdać sobie sprawę, że w wielu przypadkach firma nie ma żadnego problemu z tym podejściem, o ile jest jawne. Jest to ważne, ponieważ użytkownicy mogą spodziewać się niektórych wyników natychmiast i może to nie zdarzyć się z spójności ą ostateczną.

Jak wspomniano wcześniej w [wyzwania i rozwiązania dla zarządzania danymi rozproszonymi](distributed-data-management.md) sekcji, można użyć zdarzeń integracji do zaimplementowania zadań biznesowych, które obejmują wiele mikrousług. W związku z tym będziesz mieć spójność ostateczną między tymi usługami. Ostatecznie spójna transakcja składa się z kolekcji akcji rozproszonych. Przy każdej akcji powiązanej mikrousługi aktualizuje jednostkę domeny i publikuje inne zdarzenie integracji, które wywołuje następną akcję w ramach tego samego zadania biznesowego end-to-end.

Ważnym punktem jest, że można komunikować się z wieloma mikrousług, które są subskrybowane do tego samego zdarzenia. W tym celu można użyć publikowania/subskrybowania wiadomości na podstawie komunikacji opartej na zdarzeniach, jak pokazano na rysunku 4-19. Ten mechanizm publikowania/subskrybowania nie jest wyłącznie dla architektury mikrousług. Jest on podobny do sposobu [ograniczone konteksty](https://martinfowler.com/bliki/BoundedContext.html) w DDD powinny komunikować się lub sposób propagowania aktualizacji z bazy danych zapisu do odczytu bazy danych w [command and query responsibility segregacji (CQRS)](https://martinfowler.com/bliki/CQRS.html) wzorzec architektury. Celem jest, aby mieć spójność ostateczną między wieloma źródłami danych w systemie rozproszonym.

![Diagram przedstawiający komunikację asynchroniczną opartą na zdarzeniach.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Rysunek 4-19**. Asynchroniczna komunikacja komunikatów sterana zdarzeniami

W komunikacji asynchronicznej opartej na zdarzeniach jedna mikrousługa publikuje zdarzenia do magistrali zdarzeń, a wiele mikrousług może subskrybować ją, aby otrzymywać powiadomienia i działać na jej podstawie. Implementacja określi, jakiego protokołu użyć do komunikacji opartej na zdarzeniach, opartej na komunikatach. [Funkcja AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) może pomóc w osiągnięciu niezawodnej komunikacji w kolejce.

Korzystając z magistrali zdarzeń, można użyć poziomu abstrakcji (jak interfejs magistrali zdarzeń) na podstawie powiązanej implementacji w klasach z kodem przy użyciu interfejsu API z brokera komunikatów, takiego jak [RabbitMQ](https://www.rabbitmq.com/) lub magistrali usług, takich jak [usługa Azure Service Bus z tematami](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatywnie można użyć magistrali usług wyższego poziomu, takich jak NServiceBus, MassTransit lub Brighter, aby wyartykułować magistrali ę zdarzeń i opublikować /subskrybować system.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Uwaga dotycząca technologii przesyłania wiadomości dla systemów produkcyjnych

Technologie obsługi wiadomości dostępne do implementowania abstrakcyjnej magistrali zdarzeń są na różnych poziomach. Na przykład produkty takie jak RabbitMQ (transport brokera obsługi wiadomości) i usługa Azure Service Bus są na niższym poziomie niż inne produkty, takie jak NServiceBus, MassTransit lub Brighter, które mogą działać na wierzchu RabbitMQ i Usługi Azure Service Bus. Wybór zależy od liczby funkcji bogatych na poziomie aplikacji i skalowalności out-of-the-box potrzebnej do aplikacji. Do implementowania tylko magistrali zdarzeń proof-of-concept dla środowiska programistycznego, jak to miało miejsce w eShopOnContainers próbki, prosta implementacja na górze RabbitMQ uruchomiony w kontenerze platformy Docker może wystarczyć.

Jednak w przypadku systemów o znaczeniu krytycznym i produkcyjnych, które wymagają hiperskalowalności, można ocenić usługę Azure Service Bus. W przypadku abstrakcji i funkcji wysokiego poziomu, które ułatwiają tworzenie rozproszonych aplikacji, zaleca się ocenę innych komercyjnych i open source magistrali usług, takich jak NServiceBus, MassTransit i Brighter. Oczywiście, można zbudować własne funkcje magistrali usług na szczycie technologii niższego poziomu, takich jak RabbitMQ i Docker. Ale ta praca hydraulika może kosztować zbyt wiele dla niestandardowej aplikacji przedsiębiorstwa.

## <a name="resiliently-publishing-to-the-event-bus"></a>Elastyczne publikowanie w magistrali zdarzeń

Wyzwaniem podczas implementowania architektury stertej zdarzenia w wielu mikrousług jest sposób niepodzielnie zaktualizować stan w oryginalnej mikrousługi podczas odpornego publikowania powiązanych zdarzeń integracji do magistrali zdarzeń, jakoś na podstawie Transakcji. Oto kilka sposobów, aby to osiągnąć, chociaż mogą być również dodatkowe podejścia.

- Korzystanie z kolejki transakcyjnej (opartej na usułku), takiej jak usługa MSMQ. (Jest to jednak podejście starsze).

- Korzystanie z [eksploracji dziennika transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Korzystanie z pełnego [wzorca pozyskiwania zdarzeń.](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- Przy użyciu [wzorca skrzynki nadawczej:](https://www.kamilgrzybek.com/design/the-outbox-pattern/)transakcyjnej tabeli bazy danych jako kolejki komunikatów, która będzie podstawą składnika twórcy zdarzenia, który utworzy zdarzenie i opublikuje go.

Dodatkowe tematy, które należy wziąć pod uwagę podczas korzystania z komunikacji asynchronicznej są idempotencja wiadomości i deduplikacji wiadomości. Te tematy są omówione w sekcji [Implementowanie komunikacji opartej na zdarzeniach między mikrousług (zdarzenia integracji)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) w dalszej części tego przewodnika.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wiadomości oparte na zdarzeniach** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Kanał publikowania/subskrybowania** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Udi Dahan. Wyjaśnione CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

- **Segregacja odpowiedzialności za polecenia i kwerendy (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Komunikowanie się między kontekstami ograniczonymi** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Spójność ostateczna** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard. Refaktoryzacja w kierunku odporności: ocena sprzężenia** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Poprzedni](communication-in-microservice-architecture.md)
> [następny](maintain-microservice-apis.md)
