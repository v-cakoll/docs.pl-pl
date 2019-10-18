---
title: Przykłady projektu bezserwerowego — aplikacje bezserwerowe
description: Zapoznaj się z różnymi scenariuszami obsługiwanymi przez architektury bezserwerowe, od planowania i przetwarzania opartego na zdarzeniach w wyzwalaczach plików i procesach przesyłania strumieniowego.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: f7d3ec50608848b725d813ae2a9ee59ae9532ef3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522351"
---
# <a name="serverless-design-examples"></a>Przykłady projektów bezserwerowych

Istnieje wiele wzorców projektowych, które istnieją dla bezserwerowego. W tej sekcji przedstawiono niektóre typowe scenariusze, w których są używane bezserwerowe. Wszystkie przykłady, które są wspólne, są podstawową kombinacją wyzwalacza zdarzeń i logiki biznesowej.

## <a name="scheduling"></a>Harmonogram

Planowanie zadań jest wspólną funkcją. Na poniższym diagramie przedstawiono starszą bazę danych, która nie ma odpowiednich kontroli integralności. Baza danych musi być okresowo szybka. Funkcja bezserwerowego znajduje nieprawidłowe dane i czyści ją. Wyzwalacz jest czasomierzem, który uruchamia kod zgodnie z harmonogramem.

![Planowanie bezserwerowe](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Command and Query Responsibility Segregation (CQRS)

Command and Query Responsibility Segregation (CQRS) to wzorzec, który oferuje różne interfejsy służące do odczytywania (lub wykonywania zapytań) danych i operacji, które modyfikują dane. Rozwiązuje kilka typowych problemów. W tradycyjnych operacjach Create Read Update Delete (CRUD) systemy na podstawie konfliktów mogą wynikać z dużej ilości operacji odczytu i zapisu w tym samym magazynie danych. Zablokowanie może często występować i znacznie spowalnia odczyt. Często dane są prezentowane jako złożone z kilku obiektów domeny, a operacje odczytu muszą łączyć dane z różnych jednostek.

Za pomocą CQRS, odczyt może dotyczyć specjalnej, spłaszczonej jednostki, która modeluje dane w sposób, w jaki są używane. Odczyt jest obsługiwany inaczej niż w sposobie ich przechowywania. Na przykład mimo że baza danych może przechowywać kontakt jako rekord nagłówka z rekordem adresu podrzędnego, odczyt może dotyczyć jednostki z właściwościami nagłówka i adresu. Istnieją wyposażono podejścia do tworzenia modelu odczytu. Może być materiałem z widoków. Operacje aktualizacji mogą być hermetyzowane jako zdarzenia izolowane, które następnie wyzwalają aktualizacje do dwóch różnych modeli. Istnieją oddzielne modele do odczytu i zapisu.

![Przykład CQRS](./media/cqrs-example.png)

Bezserwerowy może obsłużyć wzorzec CQRS, dostarczając oddzielone punkty końcowe. Jedna funkcja bezserwerowa obsługuje zapytania lub odczyty, a inna funkcja bezserwerowa lub zestaw funkcji obsługuje operacje aktualizacji. Funkcja bezserwerowa może być również odpowiedzialna za utrzymywanie Aktualności modelu odczytu i może być wyzwalana przez [Źródło zmian](https://docs.microsoft.com/azure/cosmos-db/change-feed)bazy danych. Opracowywanie frontonu jest uproszczone w celu nawiązania połączenia z wymaganymi punktami końcowymi. Przetwarzanie zdarzeń jest obsługiwane na zapleczu. Ten model również skaluje się dobrze w przypadku dużych projektów, ponieważ różne zespoły mogą korzystać z różnych operacji.

## <a name="event-based-processing"></a>Przetwarzanie oparte na zdarzeniach

W systemach opartych na komunikatach zdarzenia są często zbierane w kolejkach lub w tematach wydawcy/subskrybentów, które mają zostać podjęte. Zdarzenia te mogą wyzwalać funkcje bezserwerowe w celu wykonania części logiki biznesowej. Przykład przetwarzania opartego na zdarzeniach to systemy źródła zdarzeń. "Zdarzenie" jest wywoływane, aby oznaczyć zadanie jako ukończone. Funkcja bezserwerowa wyzwalana przez zdarzenie aktualizuje odpowiedni dokument bazy danych. Druga funkcja bezserwerowa może użyć zdarzenia do zaktualizowania modelu odczytywania dla systemu. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) zapewnia sposób integrowania zdarzeń z funkcjami jako subskrybentami.

> Zdarzenia są komunikatami informacyjnymi. Aby uzyskać więcej informacji, zobacz [wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Wyzwalacze i przekształcenia plików

Wyodrębnianie, przekształcanie i ładowanie (ETL) jest wspólną funkcją biznesową. Bezserwerowy jest doskonałym rozwiązaniem dla ETL, ponieważ umożliwia wyzwalanie kodu w ramach potoku. Poszczególne składniki kodu mogą zająć się różnymi aspektami. Jedna funkcja bezserwerowa może pobrać plik, drugi stosuje transformację i inne ładuje dane. Kod może być testowany i wdrażany niezależnie, co ułatwia obsługę i skalowanie w razie potrzeby.

![Wyzwalacze i przekształcenia plików bezserwerowych](./media/serverless-file-triggers.png)

Na diagramie "chłodna pamięć masowa" zawiera dane, które są analizowane w [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Wszelkie problemy napotkane w strumieniu danych wyzwalają funkcję platformy Azure w celu rozwiązania problemu.

## <a name="asynchronous-background-processing-and-messaging"></a>Asynchroniczne przetwarzanie w tle i obsługa komunikatów

Asynchroniczne przetwarzanie komunikatów i w tle pozwala aplikacjom uruchamiać procesy bez konieczności oczekiwania. Przykładem przetwarzania asynchronicznego jest aplikacja OCR. Obraz zostanie przesłany i umieszczony w kolejce do przetworzenia. Skanowanie obrazu w celu wyodrębnienia tekstu może zająć trochę czasu, a po zakończeniu zostanie wysłane powiadomienie. Bezserwerowy może obsługiwać zarówno wywołanie, jak i wynik w tym scenariuszu.

## <a name="web-apps-and-apis"></a>Aplikacje sieci Web i interfejsy API

Popularnym scenariuszem dla bezserwerowych aplikacji jest N-warstwowa aplikacja, najczęściej w przypadku, gdy warstwa interfejsu użytkownika jest aplikacją internetową. Niedawno przepięcia popularności aplikacji jednostronicowych (SPA). Aplikacje SPA renderują pojedynczą stronę, a następnie polegają na wywołaniach interfejsu API i zwracanych danych do dynamicznego renderowania nowego interfejsu użytkownika bez ponownego ładowania pełnej strony. Renderowanie po stronie klienta zapewnia znacznie szybszą, wydajniejszą aplikację dla użytkownika końcowego.

Bezserwerowe punkty końcowe wyzwalane przez wywołania HTTP mogą służyć do obsługi żądań interfejsu API. Na przykład firma usług AD może wywoływać funkcję bezserwerową z informacjami o profilu użytkownika, aby zażądać reklamy niestandardowej. Funkcja bezserwerowa zwraca niestandardową reklamę i renderuje ją na stronie sieci Web.

![Bezserwerowy interfejs API sieci Web](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Potok danych

Funkcje bezserwerowe mogą służyć do ułatwienia potoku danych. W tym przykładzie plik wyzwala funkcję do translacji danych w pliku CSV do wierszy danych w tabeli. Zorganizowana tabela umożliwia pulpitowi nawigacyjnemu Power BI prezentowanie analiz dla użytkownika końcowego.

![Potok danych bezserwerowych](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Przetwarzanie strumienia

Urządzenia i czujniki często generują strumienie danych, które muszą być przetwarzane w czasie rzeczywistym. Istnieje wiele technologii, które mogą przechwytywać komunikaty i strumienie z [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) i [IoT Hub](https://docs.microsoft.com/azure/iot-hub) do [Service Bus](https://docs.microsoft.com/azure/service-bus). Bez względu na transport bezserwerowy jest idealnym mechanizmem przetwarzania komunikatów i strumieni danych w miarę ich działania. Bezserwerowo można szybko skalować w celu spełnienia wymagań dotyczących dużych ilości danych. Kod bezserwerowy może zastosować logikę biznesową w celu przeanalizowania danych i danych wyjściowych w formacie strukturalnym dla akcji i analizy.

![Przetwarzanie strumienia bezserwerowego](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brama interfejsu API

Brama interfejsu API zapewnia pojedynczy punkt wejścia dla klientów, a następnie inteligentnie kieruje żądania do usług zaplecza. Warto zarządzać dużymi zestawami usług. Może również obsługiwać przechowywanie wersji i uprościć programowanie przez łatwe łączenie klientów z różnymi środowiskami. Bezserwerowe może obsłużyć skalowanie zaplecza poszczególnych mikrousług podczas prezentowania pojedynczego frontonu za pośrednictwem bramy interfejsu API.

![Bezserwerowa Brama interfejsu API](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Zalecane zasoby

- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [IoT Hub platformy Azure](https://docs.microsoft.com/azure/iot-hub)
- [Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Projektowanie mikrousług: Identyfikowanie granic mikrousług](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Implementowanie wzorca wyłącznika](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Praca z obsługą kanału informacyjnego zmian w Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Poprzedni](serverless-architecture-considerations.md)
>[Następny](azure-serverless-platform.md)
