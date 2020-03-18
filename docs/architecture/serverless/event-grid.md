---
title: Usługa Azure Event Grid — aplikacje bezserwerowe
description: Usługa Azure Event Grid to rozwiązanie bezserwerowe do niezawodnego dostarczania zdarzeń i routingu na masową skalę w modelu płatności za zdarzenie.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522716"
---
# <a name="event-grid"></a>Event Grid

[Usługa Azure Event Grid](/azure/event-grid/overview) udostępnia infrastrukturę bezserwerową dla aplikacji opartych na zdarzeniach. Można publikować w usiule zdarzeń z dowolnego źródła i używać wiadomości z dowolnej platformy. Usługa Event Grid ma również wbudowaną obsługę zdarzeń z zasobów platformy Azure, aby usprawnić integrację z aplikacjami. Na przykład można subskrybować zdarzenia magazynu obiektów blob, aby powiadomić aplikację o przekazaniu pliku. Aplikacja może następnie opublikować komunikat niestandardowej siatki zdarzeń, który jest używany przez inne aplikacje w chmurze lub lokalne. Event Grid został stworzony tak, aby niezawodnie obsługiwać dużą skalę. Możesz uzyskać korzyści z publikowania i subskrybowania wiadomości bez konieczności konfigurowania niezbędnej infrastruktury.

![Logo siatki zdarzeń](./media/event-grid-logo.png)

Główne cechy siatki zdarzeń obejmują:

- W pełni zarządzana routing zdarzeń.
- Niemal w czasie rzeczywistym dostarczanie zdarzeń na dużą skalę.
- Szeroki zasięg zarówno wewnątrz, jak i na zewnątrz platformy Azure.

## <a name="scenarios"></a>Scenariusze

Usługa Event Grid rozwiązuje kilka różnych scenariuszy. Ta sekcja obejmuje trzy z najczęstszych.

### <a name="ops-automation"></a>Automatyzacja operacji

![Automatyzacja operacji](./media/ops-automation.png)

Usługa Event Grid może pomóc w przyspieszeniu automatyzacji i uprościć wymuszanie zasad, powiadamiając o usłudze [Azure Automation,](https://docs.microsoft.com/azure/automation) gdy infrastruktura jest aprowiowana.

### <a name="application-integration"></a>Integracja aplikacji

![Integracja aplikacji](./media/app-integration.png)

Za pomocą usługi Event Grid można połączyć aplikację z innymi usługami. Przy użyciu standardowych protokołów HTTP można łatwo modyfikować nawet starsze aplikacje w celu publikowania komunikatów siatki zdarzeń. Haki sieci Web są dostępne dla innych usług i platform do używania komunikatów siatki zdarzeń.

### <a name="serverless-apps"></a>Aplikacje bezserwerowe

![Aplikacje bezserwerowe](./media/serverless-apps.png)

Usługa Event Grid może wyzwolić funkcje platformy Azure, aplikacje logiki lub własny kod niestandardowy. Główną zaletą korzystania z usługi Event Grid jest użycie mechanizmu *wypychania* do wysyłania wiadomości, gdy wystąpią zdarzenia. Architektura wypychania zużywa mniej zasobów i skaluje się lepiej niż mechanizmy *sondowania.* Sondowanie musi sprawdzać dostępność aktualizacji w regularnych odstępach czasu.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Siatka zdarzeń a inne usługi obsługi wiadomości platformy Azure

Platforma Azure udostępnia kilka usług obsługi wiadomości, w tym [centra zdarzeń](https://docs.microsoft.com/azure/event-hubs) i [magistralę usług .](https://docs.microsoft.com/azure/service-bus-messaging) Każdy z nich jest przeznaczony do rozwiązania określonego zestawu przypadków użycia. Na poniższym diagramie przedstawiono ogólny przegląd różnic między usługami.

![Porównanie wiadomości platformy Azure](./media/azure-messaging-services.png)

Aby uzyskać bardziej szczegółowe porównanie, zobacz [Porównywanie usług obsługi wiadomości](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Cele dotyczące wydajności

Korzystając z siatki zdarzeń, można skorzystać z następujących gwarancji wydajności:

- Opóźnienie podsekundowe end-to-end w 99 percentylu.
- Dostępność na poziomie 99,99%.
- 10 milionów zdarzeń na sekundę na region.
- 100 milionów subskrypcji na region.
- Opóźnienie wydawcy 50 ms.
- 24-godzinna próba ponowienia z wykładniczym wycofaniem w celu zapewnienia gwarantowanej dostawy w oknie 1-dniowym.
- Przejrzysta regionalna praca awaryjna.

## <a name="event-grid-schema"></a>Schemat usługi Event Grid

Siatka zdarzeń używa standardowego schematu do zawijania zdarzeń niestandardowych. Schemat jest jak koperta, która zawija element danych niestandardowych. Oto przykładowy komunikat siatki zdarzeń:

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

Wszystko o wiadomości jest `data` standardem, z wyjątkiem właściwości. Można sprawdzić komunikat i `eventType` użyć `dataVersion` i de-serializacji niestandardowej części ładunku.

## <a name="azure-resources"></a>Zasoby platformy Azure

Główną zaletą korzystania z usługi Event Grid jest automatyczne komunikaty tworzone przez platformę Azure. Na platformie Azure zasoby automatycznie publikują w *temacie,* który umożliwia subskrypcję różnych zdarzeń. W poniższej tabeli wymieniono typy zasobów, typy komunikatów i zdarzenia, które są dostępne automatycznie.

| Zasób platformy Azure | Typ zdarzenia | Opis |
| -------------- | ---------- | ----------- |
| Subskrypcja platformy Azure | Microsoft.Resources.ResourceWrite Sukces | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu powiedzie się. |
| | Niepowodzenie zapisu zasobów firmy Microsoft.Resources.Resource | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu nie powiedzie się. |
| | Program Microsoft.Resources.ResourceWriteCancel | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu jest anulowana. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Wywoływane, gdy operacja usuwania zasobu zakończy się pomyślnie. |
|  | Awaria usuwania zasobów firmy Microsoft.Resources.Resourcedelete | Wywoływane, gdy operacja usuwania zasobu nie powiedzie się. |
| | Microsoft.Resources.ResourceDeleteCancel | Wywoływane po anulowaniu operacji usuwania zasobu. To zdarzenie ma miejsce, gdy wdrożenie szablonu zostanie anulowane. |
| Blob Storage | Obiekt Microsoft.Storage.BlobUtworzony | Wywoływane podczas tworzenia obiektu blob. |
| | Plik Microsoft.Storage.BlobDeleted | Wywoływane po usunięciu obiektu blob. |
| Usługa Event Hubs | Microsoft.EventHub.CapturePlikutworzony | Wywoływane podczas tworzenia pliku przechwytywania.
| Usługa IoT Hub | Microsoft.Devices.DeviceUtworzone | Opublikowane, gdy urządzenie jest zarejestrowane w centrum IoT hub. |
| | Usunięty plik Microsoft.Devices.Device | Opublikowano po usunięciu urządzenia z centrum IoT Hub. |
| Grupy zasobów | Microsoft.Resources.ResourceWrite Sukces | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu powiedzie się. |
| | Niepowodzenie zapisu zasobów firmy Microsoft.Resources.Resource | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu nie powiedzie się. |
| | Program Microsoft.Resources.ResourceWriteCancel | Wywoływane, gdy operacja tworzenia lub aktualizacji zasobu jest anulowana. |
| | Microsoft.Resources.ResourceDeleteSuccess | Wywoływane, gdy operacja usuwania zasobu zakończy się pomyślnie. |
| | Awaria usuwania zasobów firmy Microsoft.Resources.Resourcedelete | Wywoływane, gdy operacja usuwania zasobu nie powiedzie się. |
| | Microsoft.Resources.ResourceDeleteCancel | Wywoływane po anulowaniu operacji usuwania zasobu. To zdarzenie ma miejsce, gdy wdrożenie szablonu zostanie anulowane. |

Aby uzyskać więcej informacji, zobacz [Schemat zdarzeń usługi Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

Dostęp do usługi Event Grid można uzyskać z dowolnego typu aplikacji, nawet z tej, która jest uruchamiana lokalnie.

## <a name="conclusion"></a>Podsumowanie

W tym rozdziale przedstawiono informacje o platformie bezserwerowej platformy Azure, która składa się z funkcji azure, aplikacji logiki i siatki zdarzeń. Za pomocą tych zasobów można utworzyć całkowicie bezserwerową architekturę aplikacji lub utworzyć rozwiązanie hybrydowe, które współdziała z innymi zasobami w chmurze i serwerami lokalnymi. W połączeniu z bezserwerową platformą danych, taką jak [Azure SQL](https://docs.microsoft.com/azure/sql-database) lub [CosmosDB,](https://docs.microsoft.com/azure/cosmos-db/introduction)można tworzyć w pełni zarządzane aplikacje natywne w chmurze.

## <a name="recommended-resources"></a>Zalecane zasoby

- [Plany usług aplikacji](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Analiza analizy analizy analizy aplikacji](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Platforma Azure: przenieś swoją aplikację do chmury dzięki bezserwerowym funkcjom platformy Azure](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Schemat zdarzeń usługi Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs)
- [Dokumentacja usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions)
- [Pojęcia powiązań i wyzwalaczy usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)
- [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Porównanie funkcji 1.x i 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Łączenie z lokalnymi źródłami danych za pomocą bramy danych lokalnych platformy Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Tworzenie pierwszej funkcji w witrynie Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Tworzenie pierwszej funkcji z poziomu interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Funkcje obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Monitorowanie usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Praca z serwerami Proxy usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Poprzedni](logic-apps.md)
>[następny](durable-azure-functions.md)
