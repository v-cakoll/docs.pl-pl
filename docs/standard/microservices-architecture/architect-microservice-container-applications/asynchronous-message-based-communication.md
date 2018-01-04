---
title: Oparta na komunikatach komunikacji asynchronicznej
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Oparta na komunikatach komunikacji asynchronicznej"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ed0f12c5eca1ed45dabe94661f84216e07476ebd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-message-based-communication"></a>Oparta na komunikatach komunikacji asynchronicznej

Asynchroniczne obsługi wiadomości i sterowane zdarzeniami komunikacji są krytyczne, gdy propagowanie zmian w wielu mikrousług oraz ich modeli domeny powiązane. Jak wspomniano wcześniej w mikrousług dyskusji i konteksty ograniczone (usług łączności biznesowej), różne na różnych mikrousług lub usług łączności biznesowej oznacza modeli (użytkownika, klienta, produktu, konto, itp.). Oznacza to, że podczas wprowadzania zmian, należy w celu uzgodnienia zmian w różnych modelach. Rozwiązanie jest spójność ostateczna i komunikacji sterowane zdarzeniami oparte na asynchroniczną obsługę wiadomości.

Korzystając z komunikatów, procesy komunikują się przez wymianę wiadomości asynchronicznie. Klient wysyła polecenie lub żądanie do usługi wysyłając wiadomość. Jeśli usługa musi odpowiedzieć, wysyła inną wiadomość do klienta. Ponieważ jest oparta na komunikatach komunikatu, klient przyjmie założenie, że odpowiedź nie otrzyma natychmiast, i że może być brak odpowiedzi na wszystkich.

Komunikat składa się nagłówka (metadane, takie jak informacje identyfikacyjne lub zabezpieczeń) i treść. Komunikaty są zwykle przesyłane za pośrednictwem protokołów asynchroniczne jak protokołu AMQP.

Preferowany infrastruktury dla tego typu komunikacji w społeczności mikrousług jest brokera komunikatów lekkie, który jest inny niż brokerzy dużych i orchestrators używane w SOA. W brokerze lekkie wiadomości infrastruktury jest zazwyczaj "bez," działa tylko jako brokera komunikatów, z prostych implementacji, takie jak RabbitMQ lub magistralą skalowalna usługa w chmurze, takich jak usługi Azure Service Bus. W tym scenariuszu większość "inteligentne" planowania nadal znajduje się w punkty końcowe, które tworzenie i korzystanie z komunikatów — to znaczy w mikrousług.

Inną regułę, które należy wykonać, jak to możliwe, jest do użycia tylko asynchroniczne wysyłanie komunikatów między wewnętrznych usług, a także używają synchroniczne komunikacji (takich jak HTTP) tylko z aplikacji klienta do usługi frontonu (bram interfejsu API oraz pierwszy poziom z mikrousług).

Istnieją dwa rodzaje komunikacji asynchronicznej obsługi komunikatów: komunikacji jednego odbiorcę komunikatów i wiele odbiorników komunikacji na podstawie komunikatu. W poniższych sekcjach udostępniamy szczegółowe informacje o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikacja oparta na komunikatach jednego odbiornika 

Komunikat asynchroniczne komunikacji z jednego odbiornika oznacza, że występuje komunikacja punkt-punkt, który zapewnia komunikat dokładnie jeden z użytkowników, która odczytuje z kanału i komunikat jest przetwarzany tylko raz. Istnieją jednak sytuacji specjalnych. Na przykład w systemie chmury, która podejmuje próbę usuwania skutków błędów, ten sam komunikat mógł zostać wysłany wiele razy. Z powodu sieci lub inne błędy klient musi być w stanie ponowić próbę wysyłanie wiadomości, a serwer ma do wykonania operacji być idempotentności, aby przetworzyć komunikatu o określonym tylko raz.

Komunikacja oparta na komunikatach jednego odbiornika najlepiej nadaje się do wysyłania poleceń asynchroniczne z jednego mikrousługi do innego, jak pokazano w rysunek 4-18 ilustrujący takie podejście.

Po uruchomieniu wysyłania wiadomości-komunikacji (albo z poleceń i zdarzeń), należy unikać mieszanie komunikacji wiadomości z synchronicznego komunikacji HTTP.

![](./media/image18.PNG)

**Rysunek 4-18**. Pojedynczy mikrousługi, otrzymywanie komunikatów asynchronicznych

Należy pamiętać, że gdy polecenia pochodzą z aplikacji klienckich, ich można zaimplementować jako synchroniczne polecenia HTTP. Należy używać poleceń oparta na komunikatach, gdy będziesz potrzebować skalowalności lub, gdy już proces biznesowy oparta na komunikatach.

## <a name="multiple-receivers-message-based-communication"></a>Wiele odbiorników komunikacji wiadomości 

Jako bardziej elastyczne podejście można również używać mechanizmu publikowania/subskrypcji, tak aby komunikacji od nadawcy będzie mikrousług dodatkowe subskrybenta lub aplikacjami zewnętrznymi. W związku z tym pomaga wykonaj [otwarty/zamknięty zasady](https://en.wikipedia.org/wiki/Open/closed_principle) wysyłania usługi. Można dodać w ten sposób dodatkowe subskrybentów w przyszłości, bez konieczności modyfikowania usługi nadawcy.

Korzystając z komunikatu publikowania/subskrypcji, być może używasz interfejsu magistrali zdarzenia do publikowania zdarzeń do dowolnego subskrybenta.

## <a name="asynchronous-event-driven-communication"></a>Komunikacji asynchronicznej sterowane zdarzeniami

Podczas korzystania z komunikacji asynchronicznej sterowane zdarzeniami, mikrousługi publikuje integracji zdarzenie, gdy wydarzy się coś w jego domenie i innym mikrousługi musi wiedzieć, jak zmiany ceny mikrousługi katalogu produktów. Mikrousług dodatkowe subskrybować zdarzenia, aby mogły one odbierać je asynchronicznie. W takim przypadku odbiorców może aktualizować jednostek własnej domeny, co może powodować więcej zdarzeń integracji do opublikowania. Ten system publikowania/subskrypcji zwykle odbywa się przy użyciu implementacji magistrali zdarzeń. Magistrali zdarzeń mogą służyć jako abstrakcji lub interfejsu z interfejsu API, który chcesz subskrybować zdarzeń oraz do publikowania zdarzeń. Magistrali zdarzeń również może zawierać jeden lub więcej implementacje oparte na wszystkie brokera między procesami i obsługi wiadomości, jak kolejki wiadomości lub obsługującego komunikacji asynchronicznej i modelu publikowania/subskrypcji usługi service bus.

Jeśli system używa spójność ostateczna regulowane przez zdarzeń integracji, zaleca się czy tego podejścia być jasno całkowicie dla użytkownika końcowego. System nie należy używać metody, która symuluje zdarzeń integracji, takich jak SignalR lub systemów sondowania z klienta. Użytkownik końcowy i właściciel firmy muszą jawnie obejmować spójność ostateczna w systemie i pamiętaj, że w wielu przypadkach firmy nie ma problem z tej metody, tak długo, jak jest jawne.

Jak wspomniano wcześniej w [problemy i rozwiązania rozproszone Zarządzanie danych](#challenges-and-solutions-for-distributed-data-management) sekcji zdarzeń integracji można użyć do wykonania zadań biznesowych, które obejmują wiele mikrousług. W związku z tym konieczne będzie spójność ostateczna między tymi usługami. Po pewnym czasie spójne transakcji składa się z kolekcji rozproszonej akcji. W każdej akcji powiązanych mikrousługi aktualizuje jednostką domeny i publikuje inne zdarzenie integracji, który wywołuje akcję dalej w ramach tego samego zadania biznesowe na trasie.

Punkt ważne jest, czy może chcesz komunikują się z wielu mikrousług, który subskrybują tego samego zdarzenia. Aby to zrobić, można użyć publikowania/subskrypcji wiadomości na podstawie sterowane zdarzeniami komunikacji, jak pokazano w rysunek 4-19. Ten mechanizm publikowania/subskrypcji nie jest zarezerwowana architektury mikrousługi. Jest on podobny do sposobu [ograniczone kontekstów](http://martinfowler.com/bliki/BoundedContext.html) w skontaktować się DDD lub sposób propagacji aktualizacji z bazy danych zapisu do bazy danych do odczytu w [poleceń i zapytań podział odpowiedzialności (CQRS)](http://martinfowler.com/bliki/CQRS.html)wzorzec architektury. Celem jest spójność ostateczna między wiele źródeł danych w rozproszonym systemie.

![](./media/image19.png)

**Rysunek 4-19**. Komunikacja komunikatów asynchronicznych sterowane zdarzeniami

Implementacji zależy, który protokół do użycia na potrzeby komunikacji sterowane zdarzeniami, na podstawie komunikatu. [Protokół AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) mogą pomóc osiągnąć niezawodny umieszczonych w kolejce.

Korzystając z magistrali zdarzeń, warto użyć poziom abstrakcji (np. interfejsu magistrali zdarzenia) oparty na powiązanych implementacja klas z kodem przy użyciu interfejsu API z brokera komunikatów, takie jak [RabbitMQ](https://www.rabbitmq.com/) lub service bus, podobnie jak [Usługi azure Service Bus z tematów](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatywnie można użyć wyższego poziomu magistrali usług, takich jak NServiceBus, MassTransit lub Brighter zwrócone z magistrali zdarzeń i publikowania/subskrypcji systemu.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Uwagi dotyczące obsługi wiadomości technologii dla systemów produkcyjnych.

Są dostępne dla implementacji magistrali sieci zdarzenia abstrakcyjnego technologie obsługi wiadomości na różnych poziomach. Na przykład produktów, takich jak RabbitMQ (wiadomości transportu brokera) i usługi Azure Service Bus znajdują się na niższym poziomie niż innych produktów, takich jak NServiceBus, MassTransit albo Brighter, który może pracować na górze RabbitMQ i usługi Azure Service Bus. Wybór zależy od liczby różnorodnych funkcji na poziomie aplikacji i poza pole skalowalność, potrzebnych aplikacji. Do wykonania po prostu magistrali Weryfikacja koncepcji zdarzeń środowiska deweloperskiego, jak możemy to zostało zrobione w przykładowym eShopOnContainers proste wdrożenia na uruchomione w kontenerze Docker RabbitMQ może być wystarczającej ilości.

Niemniej jednak w przypadku krytycznym i systemów produkcyjnych, które wymagają skalowalność funkcji hyper może chcesz ocenić Azure Service Bus. Wysokiego poziomu obiektów abstrakcyjnych i funkcje, które ułatwia projektowanie aplikacji rozproszonych zaleca się dokonanie oceny innych magistrali usługi handlowych i open source, takie jak NServiceBus, MassTransit i Brighter. Oczywiście można tworzyć własne funkcje usługi service bus na niższym poziomie technologii, takich jak RabbitMQ i Docker. Ale pracy żmudne procesy może koszt za dużo aplikacji niestandardowych przedsiębiorstwa.

## <a name="resiliently-publishing-to-the-event-bus"></a>Publikowanie resiliently magistrali zdarzeń

Żądanie w przypadku implementowania architekturę sterowane zdarzeniami między wieloma mikrousług jest automatycznie aktualizacji stanu w oryginalnym mikrousługi podczas resiliently publikowania do magistrali zdarzeń, w jakiś sposób na podstawie jej zdarzenia pokrewne integracji transakcje. Poniżej przedstawiono na kilka sposobów, aby to osiągnąć, chociaż może to być również dodatkowych metod.

-   Przy użyciu transakcyjne kolejki (w oparciu o usługi DTC) takie jak usługi MSMQ. (Jednak jest podejście starszej wersji).

-   Przy użyciu [wyszukiwania dziennik transakcji](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   Przy użyciu pełnego [źródłem zdarzeń](https://msdn.microsoft.com/en-us/library/dn589792.aspx) wzorca.

-   Przy użyciu [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/): Tabela transakcyjne bazy danych jako kolejki komunikatów, który ma być base składnika tworzenia zdarzeń, który może utworzyć zdarzenia i opublikuj go.

Tematy dodatkowe, które należy wziąć pod uwagę podczas komunikacji asynchronicznej są projektu wiadomości i deduplikacji wiadomości. Te tematy w sekcji [wdrożenie oparte na zdarzeniu komunikacji między mikrousług (zdarzeń integracji)](#implementing_event_based_comms_microserv) dalszej części tego przewodnika.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Zdarzenia zmiennych wiadomości**
    [*http://soapatterns.org/design\_wzorce lub zdarzenia\_zmiennych\_obsługi wiadomości*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Kanał publikowania/subskrypcji**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Udi Dahan. Zawiera wyjaśnienie CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Poleceń i zapytań podział odpowiedzialności (CQRS)**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Komunikacja pomiędzy ograniczone kontekstów**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Spójność ostateczna**
    [*https://en.wikipedia.org/wiki/Eventual\_spójności*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Refaktoryzacja kierunku odporności: Ocena sprzężenia**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Poprzednie] (komunikacji w — mikrousługi architecture.md) [dalej] (Obsługa mikrousługi apis.md)
