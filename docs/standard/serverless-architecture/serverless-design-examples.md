---
title: Przykłady projektu bez użycia serwera — aplikacje niekorzystające z serwera
description: Poznaj różne scenariusze obsługiwane przez architektury bezserwerowe, od planowania i przetwarzania wyzwalacze plików i przetwarzania strumienia opartego na zdarzeniach.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: d165746ff2f03b0edc59a9284052323a0c1fd05b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784440"
---
# <a name="serverless-design-examples"></a>Przykłady projektów bezserwerowych

Istnieje wiele wzorców projektowych, które istnieją dla bez użycia serwera. Ta sekcja zawiera kilka typowych scenariuszy korzystających z bez użycia serwera. Co to wszystkie przykłady mają wspólną podstawowe połączenie zdarzenie wyzwalacza i logiki biznesowej.

## <a name="scheduling"></a>Planowanie

Planowanie zadań jest funkcją wspólnej. Na poniższym diagramie przedstawiono starszej wersji bazy danych, która nie ma sprawdzania integralności odpowiednie. Baza danych musi być okresowo wyczyszczona. Funkcję niewymagającą użycia serwera znajduje nieprawidłowych danych i czyści ją. Wyzwalacz jest czasomierz, który uruchamia kod zgodnie z harmonogramem.

![Planowanie bez użycia serwera](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Polecenie and Query Responsibility Segregation (CQRS)

Polecenie i podział odpowiedzialności zapytania (CQRS) to wzorzec, który dostarcza dane różne interfejsy do odczytu (lub zapytań) i operacje, które modyfikują dane. Ona rozwiązuje kilka typowych problemów. W tradycyjnych systemach utworzyć odczytu aktualizacji usuwania (CRUD) na podstawie konflikty mogą powstać w wyniku duża liczba odczytów i zapisów do tego samego magazynu danych. Blokowanie może często występują i znacznie spowolnić odczytów. Często dane są prezentowane, jak połączyć dane z różnymi jednostkami złożonego kilka obiektów domeny i operacji odczytu.

Korzystając z podejścia CQRS, odczyt może obejmować specjalna jednostka "spłaszczonych" modelujący dane, sposobu ich używania. Odczyt przebiega inaczej niż sposób przechowywania. Na przykład mimo że bazy danych mogą przechowywać kontakt jako rekord nagłówka z podrzędnego rekordu adresu, odczytu może obejmować jednostki z nagłówkiem i właściwości adresu. Istnieje wiele metod tworzenia modelu odczytu. Może być zmaterializowany z widoków. Operacje aktualizacji może być zhermetyzowany jako pojedyncze zdarzenia, które następnie wyzwolić aktualizacje na dwa różne modele. Istnieją osobne modele do odczytu i zapisu.

![Przykład CQRS](./media/cqrs-example.png)

Aplikacje niewymagające użycia serwera może obsłużyć wzorca CQRS, zapewniając segregowany punktów końcowych. Jedną funkcję niewymagającą użycia serwera obsługuje zapytania lub operacji odczytu, a inną funkcję niewymagającą użycia serwera lub zbioru funkcji obsługuje operacje aktualizacji. Funkcję niewymagającą użycia serwera, może być również odpowiedzialny za aktualizowanie modelu odczytu i może być uruchamiane w bazie danych [zestawienia zmian](https://docs.microsoft.com/azure/cosmos-db/change-feed). Tworzenie frontonu została uproszczona w celu nawiązywania połączenia z wymaganych punktów końcowych. Przetwarzanie zdarzeń odbywa się na zapleczu. Ten model również skaluje sprawdzają się w przypadku dużych projektów, ponieważ różne zespoły mogą działać na różnych operacji.

## <a name="event-based-processing"></a>Przetwarzanie oparte na zdarzeniach

W komputerach z systemem komunikat zdarzenia często są zbierane w kolejkach lub tematach wydawca/subskrybent, które będą używane. Te zdarzenia możesz wyzwolić funkcje niewymagające użycia serwera, aby wykonać część logiki biznesowej. Przykład oparty na zdarzeniach przetwarzania jest źródłem zdarzeń systemy. "Zdarzenie" jest wykorzystywana, aby oznaczyć zadanie jako zakończone. Funkcję niewymagającą użycia serwera wyzwalane przez zdarzenia aktualizuje dokument odpowiednią bazą danych. Drugi funkcję niewymagającą użycia serwera może użyć zdarzenia, aby zaktualizować model odczytu systemu. [Usługa Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) umożliwia integrowanie zdarzeń za pomocą funkcji jako subskrybentów.

> Zdarzenia są komunikaty informacyjne. Aby uzyskać więcej informacji, zobacz [wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Wyzwalacze plików i przekształcenia

Wyodrębnianie, przekształcanie, i ładowania (ETL) jest wspólne funkcję biznesową. Bez użycia serwera to doskonałe rozwiązanie dla ETL ponieważ zezwala ona na kod, aby być wyzwalane, jako część potoku. Kod poszczególnych składników rozwiązywania przy użyciu różnych aspektów. Jedną funkcję niewymagającą użycia serwera może pobrać plik, inny stosuje transformację i innym służy do ładowania danych. Kod może być przetestowane i wdrażane niezależnie, co ułatwia utrzymanie i skalowania w razie potrzeby.

![Wyzwalacze bez użycia serwera plików i przekształcenia](./media/serverless-file-triggers.png)

Na diagramie, "chłodna magazynu" zawiera dane, który jest analizowany w [usługi Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Wszelkie problemy wystąpił w strumieniu danych wyzwalanie funkcji platformy Azure umożliwiającą anomalii.

## <a name="asynchronous-background-processing-and-messaging"></a>Przetwarzanie w tle asynchronicznych i komunikatów

Asynchroniczna Obsługa komunikatów i przetwarzania w tle umożliwiają aplikacjom uruchamiał procesów, bez konieczności oczekiwania. Przykład asynchronicznego przetwarzania jest aplikacją optyczne rozpoznawanie znaków. Obraz jest przesłane i umieszczane w kolejce do przetworzenia. Skanowanie obrazu, który umożliwia wyodrębnianie tekstu może potrwać, a po zakończeniu powiadomienia są wysyłane. Aplikacje niewymagające użycia serwera może obsłużyć wywołania i wynik, w tym scenariuszu.

## <a name="web-apps-and-apis"></a>Aplikacje sieci Web i interfejsów API

Popularne scenariusza bez użycia serwera jest N-warstwowej aplikacji, najczęściej te warstwy interfejsu użytkownika w przypadku aplikacji sieci web. Popularność z jednej strony aplikacji (SPA) ma lawinowo ostatnio. SPA aplikacji renderowanie jednej strony, a następnie zależą od wywołania interfejsu API i zwrócone dane dynamiczne renderowanie nowy interfejs użytkownika bez ponownego ładowania pełnej stronie. Renderowanie po stronie klienta zapewnia znacznie szybciej i zwiększyć szybkość reakcji aplikacji użytkownika końcowego.

Bez użycia serwera punktów końcowych wyzwolone przez wywołania HTTP może służyć do obsługi żądań interfejsu API. Na przykład firma usług ad może wywołać funkcję niewymagającą użycia serwera za pomocą informacji o profilu użytkownika, aby zażądać niestandardowego reklamy. Funkcję niewymagającą użycia serwera zwraca niestandardowe usługi ad i renderowanie strony sieci web, go.

![Bez użycia serwera internetowego interfejsu API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Potok danych

Funkcje bezserwerowe może służyć do ułatwienia potoku danych. W tym przykładzie plik wyzwolenie funkcji, aby przetłumaczyć dane w pliku CSV do wierszy danych w tabeli. Table zorganizowany umożliwia pulpit nawigacyjny usługi Power BI do przedstawienia analytics dla użytkownika końcowego.

![Potok danych bez użycia serwera](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Przetwarzanie strumienia

Urządzenia i czujniki, często generowania strumieni danych, które muszą zostać przetworzone w czasie rzeczywistym. Istnieje wiele technologii, które można przechwycić komunikaty i strumieni z [usługi Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) i [usługi IoT Hub](https://docs.microsoft.com/azure/iot-hub) do [usługi Service Bus](https://docs.microsoft.com/azure/service-bus). Niezależnie od tego, transport bez użycia serwera jest mechanizm idealne rozwiązanie do przetwarzania komunikatów i strumieni danych, jak pojawiają się w. Aplikacje niewymagające użycia serwera można szybko skalować w celu spełnienia określonych wymagań dużych ilości danych. Kod bez użycia serwera, można zastosować logikę biznesową w celu analizowania danych i danych wyjściowych w formacie ustrukturyzowanym, akcji i analizy.

![Przetwarzanie strumienia bez użycia serwera](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brama interfejsu API

Bramy interfejsu API zapewnia jeden punkt wejścia dla klientów, a następnie inteligentnie kieruje żądania do usługi zaplecza. Jest to przydatne do zarządzania dużymi zestawami usług. Można również obsługiwać przechowywanie wersji i uprościć programowanie, łatwe łączenie klientów z różnych środowisk. Aplikacje niewymagające użycia serwera może obsłużyć serwer zaplecza skalowanie poszczególnych mikrousług, prezentując pojedynczego frontonu za pośrednictwem bramy interfejsu API.

![Brama interfejsu API bez użycia serwera](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Zalecane zasoby

* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md)
* [Projektowanie mikrousług: Identyfikowanie granic mikrousługi](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Usługa Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Implementowanie wzorca wyłącznika](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Service Bus](https://docs.microsoft.com/azure/service-bus)
* [Praca ze zmianą Obsługa kanału informacyjnego w usłudze Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Poprzednie](serverless-architecture-considerations.md)
>[dalej](azure-serverless-platform.md)
