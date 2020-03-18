---
title: Przykłady projektowania bez serwerów — aplikacje bezserwerowe
description: Zapoznaj się z różnymi scenariuszami obsługiwanymi przez architektury bezserwerowe, od planowania i przetwarzania opartego na zdarzeniach po wyzwalacze plików i proces strumienia.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093552"
---
# <a name="serverless-design-examples"></a>Przykłady projektów bezserwerowych

Istnieje wiele wzorców projektowych, które istnieją dla bezserwerowych. W tej sekcji przechwytuje niektóre typowe scenariusze, które używają bezserwerowych. To, co mają wspólnego wszystkie przykłady, to podstawowa kombinacja wyzwalacza zdarzenia i logiki biznesowej.

## <a name="scheduling"></a>Planowanie

Planowanie zadań jest wspólną funkcją. Na poniższym diagramie przedstawiono starszą bazę danych, która nie ma odpowiednich kontroli integralności. Baza danych musi być okresowo wyszorowywana. Funkcja bezserwerowa znajduje nieprawidłowe dane i czyści je. Wyzwalacz jest czasotorem, który uruchamia kod zgodnie z harmonogramem.

![Planowanie bezużycia serwera](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Podział odpowiedzialności polecenia i zapytania (CQRS)

Command and Query Responsibility Segregation (CQRS) to wzorzec, który udostępnia różne interfejsy do odczytywania (lub wykonywania zapytań) danych i operacji modyfikujących dane. Odnosi się do kilku typowych problemów. W tradycyjnych systemach opartych na create read update delete (CRUD) konflikty mogą wynikać z dużej liczby odczytów i zapisów w tym samym magazynie danych. Blokowanie może często wystąpić i znacznie spowolnić odczyty. Często dane są prezentowane jako złożone z kilku obiektów domeny i operacji odczytu musi łączyć dane z różnych jednostek.

Przy użyciu CQRS odczytu może obejmować specjalne "spłaszczone" jednostki, która modeluje dane sposób, w jaki jest zużywane. Odczyt jest obsługiwany inaczej niż sposób jego przechowywania. Na przykład chociaż baza danych może przechowywać kontakt jako rekord nagłówka z rekordem adresu podrzędnego, odczyt może obejmować jednostkę z właściwościami nagłówka i adresu. Istnieje wiele podejść do tworzenia modelu odczytu. Może być zmaterializowany z widoków. Operacje aktualizacji mogą być hermetyzowane jako izolowane zdarzenia, które następnie wyzwalają aktualizacje do dwóch różnych modeli. Istnieją oddzielne modele do czytania i pisania.

![Przykład CQRS](./media/cqrs-example.png)

Bezserwerowy może pomieścić wzorzec CQRS, zapewniając segregowane punkty końcowe. Jedna funkcja bezserwerowa obsługuje kwerendy lub odczyty, a inna funkcja bezserwerowa lub zestaw funkcji obsługuje operacje aktualizacji. Funkcja bezserwerowa może być również odpowiedzialna za aktualizowanie modelu odczytu i może być wyzwalana przez [kanał informacyjny zmian](https://docs.microsoft.com/azure/cosmos-db/change-feed)bazy danych . Tworzenie frontonu jest uproszczone do łączenia się z niezbędnymi punktami końcowymi. Przetwarzanie zdarzeń jest obsługiwane na zapleczu. Ten model również skaluje się również dla dużych projektów, ponieważ różne zespoły mogą pracować nad różnymi operacjami.

## <a name="event-based-processing"></a>Przetwarzanie oparte na zdarzeniach

W systemach opartych na wiadomościach zdarzenia są często zbierane w kolejkach lub tematach wydawcy/subskrybenta, na które należy podjąć działania. Zdarzenia te mogą wyzwalać funkcje bezużycia serwera, aby wykonać logikę biznesową. Przykładem przetwarzania opartego na zdarzeniach są systemy pochodzące od zdarzeń. "Zdarzenie" jest wywoływane, aby oznaczyć zadanie jako ukończone. Funkcja bezserwerowa wyzwolona przez zdarzenie aktualizuje odpowiedni dokument bazy danych. Druga funkcja bezserwerowa może używać zdarzenia do aktualizowania modelu odczytu dla systemu. [Usługa Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) umożliwia integrację zdarzeń z funkcjami jako subskrybentami.

> Zdarzenia są komunikatami informacyjnymi. Aby uzyskać więcej informacji, zobacz [Wzorzec pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Wyzwalacze i przekształcenia plików

Wyodrębnianie, przekształcanie i ładowanie (ETL) jest wspólną funkcją biznesową. Serverless jest doskonałym rozwiązaniem dla ETL, ponieważ umożliwia kod być wyzwalane jako część potoku. Poszczególne składniki kodu mogą dotyczyć różnych aspektów. Jedna funkcja bez serwerów może pobrać plik, inna stosuje transformację, a inna ładuje dane. Kod można przetestować i wdrożyć niezależnie, co ułatwia konserwację i skalowanie w razie potrzeby.

![Wyzwalacze i przekształcenia plików bez serwerów](./media/serverless-file-triggers.png)

Na diagramie "chłodny magazyn" zawiera dane analizowane w [usłudze Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Wszelkie problemy napotkane w strumieniu danych wyzwolić funkcję platformy Azure w celu rozwiązania anomalii.

## <a name="asynchronous-background-processing-and-messaging"></a>Asynchroniczne przetwarzanie w tle i przesyłanie wiadomości

Asynchroniczne obsługi wiadomości i przetwarzania w tle umożliwiają aplikacjom uruchamianie procesów bez konieczności oczekiwania. Przykładem przetwarzania asynchronicznego jest aplikacja OCR. Obraz jest przesyłany i umieszczany w kolejce do przetworzenia. Skanowanie obrazu w celu wyodrębnienia tekstu może zająć trochę czasu, a po jego zakończeniu zostanie wysłane powiadomienie. Bezserwerowy może obsłużyć wywołania i wynik w tym scenariuszu.

## <a name="web-apps-and-apis"></a>Aplikacje internetowe i interfejsy API

Popularnym scenariuszem dla aplikacji bezserwerowych jest aplikacje n-warstwowe, najczęściej te, w których warstwa interfejsu i usług jest aplikacją sieci web. Popularność aplikacji jednostronicowych (SPA) wzrosła w ostatnim czasie. Aplikacje SPA renderują pojedynczą stronę, a następnie polegają na wywołaniach interfejsu API i zwróconych danych, aby dynamicznie renderować nowy interfejs bez ponownego ładowania pełnej strony. Renderowanie po stronie klienta zapewnia znacznie szybszą i bardziej responsywną aplikację dla użytkownika końcowego.

Bezserwerowe punkty końcowe wyzwalane przez wywołania HTTP mogą służyć do obsługi żądań interfejsu API. Na przykład firma świadcząca usługi reklamowe może wywołać funkcję bezserwerową z informacjami o profilu użytkownika w celu żądania reklam niestandardowych. Funkcja bezserwerowa zwraca reklamę niestandardową, a strona internetowa ją renderuje.

![Interfejs API sieci Web bez serwerów](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Potok danych

Funkcje bezserwerowe mogą służyć do ułatwienia potoku danych. W tym przykładzie plik wyzwala funkcję tłumaczenia danych w pliku CSV na wiersze danych w tabeli. Uporządkowana tabela umożliwia pulpitowi nawigacyjnemu usługi Power BI prezentowanie analiz użytkownikowi końcowemu.

![Potok danych bezserwerowych](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Przetwarzanie strumienia

Urządzenia i czujniki często generują strumienie danych, które muszą być przetwarzane w czasie rzeczywistym. Istnieje wiele technologii, które mogą przechwytywać wiadomości i strumienie z [usługi Event Hub s](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) i Centrum [IoT](https://docs.microsoft.com/azure/iot-hub) do [usługi Service Bus](https://docs.microsoft.com/azure/service-bus). Niezależnie od transportu, bezserwerowy jest idealnym mechanizmem do przetwarzania wiadomości i strumieni danych, ponieważ są one w ich dochodzi. Bezserwerowy można szybko skalować, aby zaspokoić zapotrzebowanie na duże ilości danych. Kod bezserwerowy można zastosować logikę biznesową do analizowania danych i danych wyjściowych w ustrukturyzowanym formacie dla akcji i analiz.

![Przetwarzanie strumienibez serwerów](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brama interfejsu API

Brama interfejsu API zapewnia pojedynczy punkt wejścia dla klientów, a następnie inteligentnie kieruje żądania do usług zaplecza. Jest to przydatne do zarządzania dużymi zestawami usług. Może również obsługiwać przechowywanie wersji i uprościć programowanie, łatwo łącząc klientów z różnymi środowiskami. Bezserwerowy może obsługiwać skalowanie zaplecza poszczególnych mikrousług podczas prezentacji pojedynczego frontonu za pośrednictwem bramy interfejsu API.

![Brama interfejsu API bezserwerowego](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Zalecane zasoby

- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Projektowanie mikrousług: identyfikowanie granic mikrousług](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Centra zdarzeń](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Wzorzec pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Implementowanie wzorca wyłącznika](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [Iot](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Praca z obsługą kanału danych o zmianach w usłudze Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Poprzedni](serverless-architecture-considerations.md)
>[następny](azure-serverless-platform.md)
