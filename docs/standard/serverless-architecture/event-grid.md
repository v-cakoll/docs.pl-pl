---
title: Usługa Azure Event Grid — aplikacje niekorzystające z serwera
description: Usługa Azure Event Grid to rozwiązanie bez użycia serwera do niezawodnego dostarczania zdarzeń i routingu na ogromną skalę w modelu płatności na zdarzenie.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: a10fc6a47322de5db40870b1b727edc5559a27f6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145894"
---
# <a name="event-grid"></a>Event Grid

[Usługa Azure Event Grid](/azure/event-grid/overview) zapewnia infrastrukturę bez użycia serwera dla aplikacji opartych na zdarzeniach. Możesz publikować do usługi Event Grid z dowolnego źródła i używać komunikatów z dowolnej platformy. Usługa Event Grid również ma wbudowaną obsługę zdarzeń z zasobów platformy Azure, aby usprawnić integracji z aplikacjami. Na przykład możesz subskrybować zdarzenia usługi blob storage do powiadamiania aplikacji, gdy plik zostanie przekazany. Aplikację można następnie publikować komunikat siatki zdarzeń niestandardowych, który jest używany przez inne chmurę lub lokalne aplikacje. Usługa Event Grid została stworzona z myślą niezawodny sposób będą obsługiwać bardzo dużą skalę. Korzyści publikowania i subskrybowania komunikatów bez konieczności konfigurowania infrastruktury wymaganej.

![Logo siatki zdarzeń](./media/event-grid-logo.png)

Główne funkcje usługi event Grid:

* W pełni zarządzanym routingiem zdarzeń.
* W pobliżu dostarczania zdarzeń w czasie rzeczywistym na dużą skalę.
* Szeroka pokrycia i spoza platformy Azure.

## <a name="scenarios"></a>Scenariusze

Usługa Event Grid adresów różnych scenariuszy. W tej sekcji opisano trzy najbardziej typowe.

### <a name="ops-automation"></a>Automatyzacja operacji

![Automatyzacja operacji](./media/ops-automation.png)

Usługi Event Grid może pomóc szybkość automatyzacji i uproszczenie wymuszania zasad przez powiadomienie [usługi Azure Automation](https://docs.microsoft.com/azure/automation) po zaaprowizowaniu infrastruktury.

### <a name="application-integration"></a>Integracja aplikacji

![Integracja aplikacji](./media/app-integration.png)

Usługa Event Grid umożliwia łączenie aplikacji z innymi usługami. Za pomocą standardowych protokołów HTTP, nawet starsze aplikacje można łatwo modyfikować do publikacji komunikatów usługi Event Grid. Elementy webhook są dostępne dla innych usług i platformy, które będą używać komunikatów z usługi Event Grid.

### <a name="serverless-apps"></a>Aplikacje niewymagające użycia serwera

![Aplikacje niewymagające użycia serwera](./media/serverless-apps.png)

Usługa Event Grid można uruchomić usługi Azure Functions, Logic Apps lub własny kod niestandardowy. Główną zaletą używania usługi Event Grid to, że używa on *wypychania* mechanizm do wysyłania wiadomości po wystąpieniu zdarzenia. Architektura wypychania zużywa mniej zasobów i skaluje się lepiej niż *sondowania* mechanizmów. Sondowania należy sprawdzić dostępność aktualizacji w regularnych odstępach czasu.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Usługa Event Grid w porównaniu z innymi usługami platformy Azure dla obsługi wiadomości

Platforma Azure udostępnia kilka usług obsługi wiadomości, w tym [usługi Event Hubs](https://docs.microsoft.com/azure/event-hubs) i [usługi Service Bus](https://docs.microsoft.com/azure/service-bus-messaging). Każdy jest przeznaczony do adresów określony zestaw przypadków użycia. Na poniższym diagramie przedstawiono ogólne omówienie różnic między usługami.

![Azure messaging porównania](./media/azure-messaging-services.png)

Aby uzyskać bardziej szczegółowe porównanie, zobacz [Porównanie usług obsługi wiadomości](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Elementy docelowe wydajności

Za pomocą usługi Event Grid, możesz korzystać z zalet wydajności następujące gwarantuje:

* Subsecond end-to-end opóźnienie w 99. percentylu.
* dostępność na poziomie 99,99%.
* 10 milionów zdarzeń na sekundę na region.
* 100 milionów subskrypcji na region.
* Opóźnienie wydawcy 50 ms.
* 24-godzinny ponawiania wykładniczego wycofywania gwarantowane dostarczanie w oknie 1 dzień.
* Przezroczyste rozwiązania regionalnej pracy awaryjnej.

## <a name="event-grid-schema"></a>Schemat siatki zdarzeń

Usługi Event Grid używa standardowego schematu do opakowania zdarzeń niestandardowych. Schemat jest jak kopercie, która otacza nazwę elementu danych niestandardowych. Oto przykładowy komunikat usługi Event Grid:

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

Wszystkie informacje o wiadomości jest standardowa z wyjątkiem `data` właściwości. Możesz sprawdzić wiadomość i użyć `eventType` i `dataVersion` można zdeserializować niestandardowe części ładunku.

## <a name="azure-resources"></a>Zasoby platformy Azure

Główną zaletą używania usługi Event Grid jest automatyczne komunikaty generowane przez platformę Azure. Na platformie Azure, zasoby automatycznie opublikować *tematu* pozwala zasubskrybować dla różnych zdarzeń. W poniższej tabeli wymieniono typy zasobów, typy komunikatów i zdarzenia, które są automatycznie dostępne.

| Zasób platformy Azure | Typ zdarzenia | Opis |
| -------------- | ---------- | ----------- |
| Subskrypcja platformy Azure | Microsoft.Resources.ResourceWriteSuccess | Wywoływane, gdy zasób utworzyć lub zaktualizować operacji powiedzie się. |
| | Microsoft.Resources.ResourceWriteFailure | Wywoływane, gdy tworzenie zasobu lub operacja aktualizacji nie powiedzie się. |
| | Microsoft.Resources.ResourceWriteCancel | Wywoływane, gdy zasób utworzyć lub zaktualizować operacji zostało anulowane. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Wywoływane, gdy operacja usuwania zasobu zakończy się pomyślnie. |
|  | Microsoft.Resources.ResourceDeleteFailure | Wywoływane, gdy operacja usuwania zasobu nie powiodło się. |
| | Microsoft.Resources.ResourceDeleteCancel | Wywoływane, gdy operacja usuwania zasobu zostało anulowane. To zdarzenie występuje, gdy wdrożenie szablonu zostanie anulowane. |
| Blob Storage | Microsoft.Storage.BlobCreated | Wywoływane, gdy zostanie utworzony obiekt blob. |
| | Microsoft.Storage.BlobDeleted | Wywoływane, gdy obiekt blob zostanie usunięty. |
| Usługa Event Hubs | Microsoft.EventHub.CaptureFileCreated | Wywoływane, gdy tworzony jest plik przechwytywania.
| Usługa IoT Hub | Microsoft.Devices.DeviceCreated | Opublikowane po zarejestrowaniu urządzenia do usługi IoT hub. |
| | Microsoft.Devices.DeviceDeleted | Opublikowana, gdy urządzenie zostanie usunięty z usługi IoT hub. |
| Grupy zasobów | Microsoft.Resources.ResourceWriteSuccess | Wywoływane, gdy zasób utworzyć lub zaktualizować operacji powiedzie się. |
| | Microsoft.Resources.ResourceWriteFailure | Wywoływane, gdy tworzenie zasobu lub operacja aktualizacji nie powiedzie się. |
| | Microsoft.Resources.ResourceWriteCancel | Wywoływane, gdy zasób utworzyć lub zaktualizować operacji zostało anulowane. |
| | Microsoft.Resources.ResourceDeleteSuccess | Wywoływane, gdy operacja usuwania zasobu zakończy się pomyślnie. |
| | Microsoft.Resources.ResourceDeleteFailure | Wywoływane, gdy operacja usuwania zasobu nie powiodło się. |
| | Microsoft.Resources.ResourceDeleteCancel | Wywoływane, gdy operacja usuwania zasobu zostało anulowane. To zdarzenie występuje, gdy wdrożenie szablonu zostanie anulowane. |

Aby uzyskać więcej informacji, zobacz [schematu zdarzeń usługi Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

Usługa Event Grid dostęp z dowolnego typu aplikacji, nawet jeśli jest on uruchamianego w środowisku lokalnym.

## <a name="conclusion"></a>Wniosek

W tym rozdziale opisano bezserwerowej platformy Azure, które składa się z usługi Azure Functions, Logic Apps i Event Grid. Dzięki tym zasobom można tworzyć architekturę aplikacji bezserwerowej w całości lub Utwórz hybrydowe rozwiązanie, które wchodzi w interakcję z innych zasobów w chmurze i lokalnych serwerów. Połączone z platformą bez użycia serwera danych, takich jak [Azure SQL](https://docs.microsoft.com/azure/sql-database) lub [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), w pełni zarządzana usługa w chmurze mogą tworzyć aplikacje natywne.

## <a name="recommended-resources"></a>Zalecane zasoby

* [Plany usługi App service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Analiza usługi Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure: Udostępnij swoją aplikację w chmurze przy użyciu bezserwerowej usługi Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure Event Grid](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [Schemat zdarzeń w usłudze Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
* [Dokumentacja usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions)
* [Pojęcia powiązania i Wyzwalacze usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Usługi Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [Porównanie funkcji wersji 1.x i 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [Nawiązywanie połączenia z lokalnymi źródłami danych za pomocą bramy danych lokalnych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [Tworzenie pierwszej funkcji w witrynie Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [Tworzenie pierwszej funkcji przy użyciu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [Funkcje obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [Monitorowanie usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [Praca z serwerów proxy usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Poprzednie](logic-apps.md)
>[dalej](durable-azure-functions.md)
