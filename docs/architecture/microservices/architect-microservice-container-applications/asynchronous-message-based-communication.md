---
title: Asynchroniczna komunikacja oparta na komunikatach
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Asynchroniczna komunikacja oparta na komunikatach to podstawowe koncepcje w architekturze mikrousług, ponieważ jest to najlepszy sposób, aby mikrousługi były niezależne od siebie, a także ostatecznie zsynchronizowane.
ms.date: 09/20/2018
ms.openlocfilehash: a8af94540a7906c474b9b784c28aa60ebae0a6e3
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306971"
---
# <a name="asynchronous-message-based-communication"></a>Asynchroniczna komunikacja oparta na komunikatach

Asynchroniczne komunikaty i komunikacja sterowane zdarzeniami są kluczowe, gdy propagowanie zmian w wielu mikrousługach i związanych z nimi modelach domen. Jak wspomniano wcześniej w przypadku mikrousług dyskusji i ograniczonych kontekstów (BCs), modele (użytkownik, klient, produkt, konto itp.) mogą oznaczać różne rzeczy dla różnych mikrousług lub usług łączności biznesowej. Oznacza to, że gdy wystąpią zmiany, potrzebny jest jakiś sposób uzgadniania zmian w różnych modelach. Rozwiązanie to spójność ostateczna i komunikacja oparta na zdarzeniach na podstawie asynchronicznych komunikatów.

W przypadku korzystania z komunikatów procesy komunikują się przez wymianę komunikatów asynchronicznie. Klient wykonuje polecenie lub żądanie do usługi, wysyłając do niego wiadomość. Jeśli usługa musi odpowiedzieć, wysyła do klienta inny komunikat z powrotem. Ponieważ jest to komunikacja oparta na komunikatach, klient zakłada, że odpowiedź nie zostanie natychmiast odebrana, a w ogóle może nie mieć odpowiedzi.

Komunikat składa się z nagłówka (metadane, takie jak identyfikacja lub informacje o zabezpieczeniach) i treść. Komunikaty są zwykle wysyłane za poorednictwem protokołów asynchronicznych, takich jak AMQP.

Preferowaną infrastrukturą dla tego typu komunikacji w społeczności mikrousług jest lekki Broker komunikatów, który jest inny niż w przypadku dużych brokerów i koordynatorów używanych w ramach SOA. W lekkim brokerze komunikatów infrastruktura jest zazwyczaj "Dumb", działającą tylko jako Broker komunikatów, z prostymi implementacjami, takimi jak RabbitMQ, lub skalowalną magistralą usług w chmurze, taką jak Azure Service Bus. W tym scenariuszu większość "inteligentnych" myśli nadal przebywa w punktach końcowych, które produkują i zużywają komunikaty, czyli w mikrousługach.

Kolejną regułą, jaką należy wykonać, tak jak to możliwe, jest użycie tylko asynchronicznych komunikatów między usługami wewnętrznymi i użycie synchronicznej komunikacji (na przykład HTTP) tylko z aplikacji klienckich do usług frontonu (bramy interfejsu API i pierwszy poziom mikrousług).

Istnieją dwa rodzaje asynchronicznej komunikacji komunikatów: komunikacja oparta na komunikatach o pojedynczym odbiorniku i komunikacja oparta na komunikatach. W poniższych sekcjach znajdują się szczegółowe informacje o nich.

## <a name="single-receiver-message-based-communication"></a>Komunikacja oparta na komunikatach pojedynczego odbiorcy

Komunikacja asynchroniczna oparta na komunikatach z pojedynczym odbiornikiem oznacza komunikację typu punkt-punkt, która dostarcza komunikat do dokładnie jednego z odbiorców, który odczytuje z kanału, i że komunikat jest przetwarzany tylko raz. Istnieją jednak specjalne sytuacje. Na przykład w systemie w chmurze, który próbuje automatycznie odzyskać sprawność po awarii, ten sam komunikat może być wysyłany wiele razy. Ze względu na sieć lub inne błędy, klient musi być w stanie ponowić próbę wysłania wiadomości, a serwer musi zaimplementować operację do idempotentne w celu przetworzenia konkretnego komunikatu tylko raz.

Komunikacja oparta na komunikatach pojedynczego odbiorcy jest szczególnie przydatna w przypadku wysyłania poleceń asynchronicznych z jednej mikrousługi do innej, jak pokazano na rysunku 4-18, który ilustruje to podejście.

Po rozpoczęciu wysyłania komunikacji opartej na komunikatach (z poleceniami lub zdarzeniami) należy unikać mieszania komunikacji opartej na komunikatach z synchroniczną komunikacją protokołu HTTP.

![Jedna mikrousługa otrzymująca komunikat asynchroniczny](./media/asynchronous-message-based-communication/single-receiver-message-based-communication.png)

**Rysunek 4-18**. Jedna mikrousługa otrzymująca komunikat asynchroniczny

Gdy polecenia pochodzą z aplikacji klienckich, można je zaimplementować jako polecenia synchroniczne HTTP. Użyj poleceń opartych na komunikatach, gdy potrzebujesz wyższej skalowalności lub gdy jesteś już w procesie biznesowym opartym na komunikatach.

## <a name="multiple-receivers-message-based-communication"></a>Komunikacja oparta na komunikatach wielu odbiorników

Bardziej elastyczne podejście może również wymagać użycia mechanizmu publikowania/subskrybowania, aby komunikacja od nadawcy była dostępna dla dodatkowych mikrousług subskrybentów lub aplikacji zewnętrznych. Z tego względu pomaga to postępować zgodnie z [zasadą otwierania/zamykania](https://en.wikipedia.org/wiki/Open/closed_principle) w usłudze wysyłającej. Dzięki temu dodatkowi Subskrybenci mogą zostać dodani w przyszłości bez konieczności modyfikowania usługi nadawcy.

W przypadku korzystania z komunikacji publikowania/subskrybowania można używać interfejsu usługi Event bus do publikowania zdarzeń na dowolnym subskrybencie.

## <a name="asynchronous-event-driven-communication"></a>Asynchroniczna komunikacja oparta na zdarzeniach

W przypadku korzystania z asynchronicznej komunikacji opartej na zdarzeniach mikrousługa publikuje zdarzenie integracji, gdy coś się dzieje w swojej domenie, a inna mikrousługa musi mieć do niej świadomość, na przykład zmianę cen w mikrousłudze katalogu produktów. Dodatkowe mikrousługi subskrybują zdarzenia, aby mogli je odbierać asynchronicznie. W takim przypadku odbiorcy mogą zaktualizować swoje jednostki domeny, co może spowodować opublikowanie większej liczby zdarzeń integracji. Ten system publikowania/subskrybowania jest zwykle wykonywany przy użyciu implementacji magistrali zdarzeń. Magistrala zdarzeń może być zaprojektowana jako Abstrakcja lub interfejs, z interfejsem API, który jest wymagany do subskrybowania lub anulowania subskrypcji zdarzeń oraz do publikowania zdarzeń. Magistrala zdarzeń może również mieć co najmniej jedną implementację opartą na dowolnym procesie i brokerze obsługi komunikatów, takim jak kolejka komunikatów lub Usługa Service Bus, która obsługuje komunikację asynchroniczną i model publikowania/subskrybowania.

Jeśli system używa spójności ostatecznej opartej na zdarzeniach integracji, zaleca się, aby to podejście było całkowicie jasne dla użytkownika końcowego. System nie powinien używać podejścia, które śladuje zdarzenia integracji, takie jak sygnalizujące lub systemy sondowania od klienta. Użytkownik końcowy i właściciel biznesowy muszą jawnie wdrożyć w systemie spójność ostateczną i pamiętać, że w wielu przypadkach firma nie ma żadnego problemu z tym podejściem, o ile jest to jawne. Jest to ważne, ponieważ użytkownicy mogą od razu zobaczyć niektóre wyniki, co może nie być spowodowane spójnością ostateczną.

Jak wspomniano wcześniej w sekcji [wyzwania i rozwiązania dotyczące zarządzania danymi rozproszonymi](distributed-data-management.md) , można użyć zdarzeń integracji w celu zaimplementowania zadań firmowych obejmujących wiele mikrousług. W ten sposób będziesz mieć ostateczną spójność między tymi usługami. Ostatecznie spójna transakcja składa się z kolekcji rozproszonych akcji. W każdej akcji powiązana mikrousługa aktualizuje jednostkę domeny i publikuje inne zdarzenie integracji, które wywołuje następną akcję w ramach tego samego zadania biznesowego.

Ważnym punktem jest to, że możesz chcieć komunikować się z wieloma mikrousługami subskrybowanymi na tym samym zdarzeniu. W tym celu można użyć komunikatów publikowania/subskrybowania na podstawie komunikacji sterowanej zdarzeniami, jak pokazano na rysunku 4-19. Ten mechanizm publikowania/subskrybowania nie jest wyłączny dla architektury mikrousług. Jest to podobne do sposobu, w jaki [ograniczone konteksty](https://martinfowler.com/bliki/BoundedContext.html) w DDD powinny komunikować się, lub w sposób propagowania aktualizacji z bazy danych zapisu do bazy danych odczytu w wzorcu architektury [Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) . Celem jest zachowanie spójności ostatecznej między wieloma źródłami danych w systemie rozproszonym.

![Diagram przedstawiający asynchroniczne komunikację sterowaną zdarzeniami.](./media/asynchronous-message-based-communication/asynchronous-event-driven-communication.png)

**Rysunek 4-19**. Asynchroniczna komunikacja komunikatów oparta na zdarzeniach

W przypadku asynchronicznej komunikacji opartej na zdarzeniach jedna mikrousługa publikuje zdarzenia do magistrali zdarzeń, a wiele mikrousług może subskrybować ten element, aby otrzymywać powiadomienia i działać na nim. Twoja implementacja określi, który protokół ma być używany na potrzeby komunikacji opartej na zdarzeniach. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) może pomóc w osiągnięciu niezawodnej komunikacji kolejkowanej.

Korzystając z magistrali zdarzeń, można użyć poziomu abstrakcji (na przykład interfejsu magistrali zdarzeń) na podstawie powiązanej implementacji w klasach z kodem przy użyciu interfejsu API z brokera komunikatów, takiego jak [RabbitMQ](https://www.rabbitmq.com/) , lub usługi Service Bus, takiej jak [Azure Service Bus z tematami](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Alternatywnie możesz chcieć użyć magistrali usług wyższego poziomu, takiej jak NServiceBus, MassTransit lub jaśniejszy, aby ideach swoją magistralę zdarzeń i system publikowania/subskrybowania.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Uwaga dotycząca technologii obsługi komunikatów w systemach produkcyjnych

Technologie obsługi wiadomości dostępne do wdrożenia abstrakcyjnej magistrali zdarzeń są na różnych poziomach. Na przykład produkty takie jak RabbitMQ (transport brokera komunikatów) i Azure Service Bus znajdują się na niższym poziomie niż inne produkty, takie jak NServiceBus, MassTransit lub jaśniejszy, które mogą współpracować nad RabbitMQ i Azure Service Bus. Wybór zależy od liczby bogatych funkcji na poziomie aplikacji oraz wbudowanej skalowalności potrzebnej dla aplikacji. W celu zaimplementowania tylko testowej magistrali zdarzeń dla środowiska deweloperskiego, tak jak zostało to zrobione w przykładzie eShopOnContainers, prosta implementacja na platformie RabbitMQ działającej w kontenerze platformy Docker może być wystarczająca.

Jednak w przypadku systemów o znaczeniu krytycznym i produkcyjnym, które wymagają skalowalności, możesz chcieć oszacować Azure Service Bus. W przypadku abstrakcji i funkcji wysokiego poziomu, które ułatwiają tworzenie aplikacji rozproszonych, zalecamy ocenę innych komercyjnych i typu open-source magistrali usług, takich jak NServiceBus, MassTransit i jaśniejszy. Oczywiście możesz tworzyć własne funkcje magistrali usług na podstawie technologii niższego poziomu, takich jak RabbitMQ i Docker. Jednak w przypadku niestandardowej aplikacji korporacyjnej prace wodociągowe mogą być zbyt duże.

## <a name="resiliently-publishing-to-the-event-bus"></a>Odporne na przepublikowanie do magistrali zdarzeń

Wyzwanie w przypadku implementowania architektury opartej na zdarzeniach w wielu mikrousługach polega na niepodzielnej aktualizacji stanu w ramach oryginalnej mikrousługi przy jednoczesnym opublikowaniu powiązanego zdarzenia integracji w usłudze Event Bus w sposób w zależności od transakcji. Poniżej przedstawiono kilka sposobów osiągnięcia tego celu, chociaż mogą wystąpić również dodatkowe podejścia.

- Korzystanie z kolejki transakcyjnej (opartej na usłudze DTC), takiej jak MSMQ. (Jest to jednak starsze podejście).

- Korzystanie z [wyszukiwania w dzienniku transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Używanie wzorca [pozyskiwania pełnego zdarzenia](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing) .

- Używanie [wzorca skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/): transakcyjna tabela bazy danych jako kolejka komunikatów, która będzie podstawą dla składnika Event-Creator, który utworzy zdarzenie i opublikuje je.

Dodatkowe tematy, które należy wziąć pod uwagę podczas korzystania z komunikacji asynchronicznej, to idempotentność komunikatów i Deduplikacja komunikatów. Te tematy zostały omówione w sekcji [implementowanie komunikacji opartej na zdarzeniach między mikrousługami (zdarzenia integracji)](../multi-container-microservice-net-applications/integration-event-based-microservice-communications.md) w dalszej części tego przewodnika.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Obsługa komunikatów opartych na zdarzeniach** \
  <https://soapatterns.org/design_patterns/event_driven_messaging>

- **Kanał publikowania/subskrybowania** \
  <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **UDI Dahan. Wyjaśniono CQRS** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

- **Command and Query Responsibility Segregation (CQRS)** \
  <https://docs.microsoft.com/azure/architecture/patterns/cqrs>

- **Komunikacja między kontekstami ograniczonymi** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Spójność ostateczna** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Jimmy Bogard. Refaktoryzacja do odporności: ocenianie sprzęgu** \
  <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

> [!div class="step-by-step"]
> [Poprzedni](communication-in-microservice-architecture.md) 
>  [Dalej](maintain-microservice-apis.md)
