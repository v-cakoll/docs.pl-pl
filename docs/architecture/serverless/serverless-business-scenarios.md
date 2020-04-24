---
title: Przykładowe scenariusze biznesowe i przypadki użycia dla aplikacji bezserwerowych
description: Dowiedz się bezserwerowo, korzystając z praktycznego podejścia, uzyskując dostęp do próbek, które przedziały od przetwarzania obrazów do obsługi urządzeń przenośnych i potoków ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135662"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scenariusze biznesowe i przypadki użycia bez korzystania z serwera

Istnieje wiele przypadków użycia i scenariuszy dotyczących aplikacji bezserwerowych. Ten rozdział zawiera przykłady ilustrujące różne scenariusze. Scenariusze obejmują linki do powiązanej dokumentacji i repozytoriów kodu publicznego. Przykłady w tym rozdziale umożliwiają rozpoczęcie pracy nad tworzeniem i implementowaniem rozwiązań bezserwerowych.

## <a name="big-data-processing"></a>Przetwarzanie danych Big Data

![Mapa/Zmniejsz diagram](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

Ten przykład używa bezserwerowego, aby wykonać operację mapowania/zmniejszania dla zestawu danych Big Data. Określa średnią prędkość w przypadku żółtej podróży w Nowym Jorku na dzień w 2017.

[Przetwarzanie danych Big Data: bezserwerowe MapReduce na platformie Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a>Tworzenie aplikacji bezserwerowych: ćwiczenia praktyczne

Dowiedz się, jak używać funkcji do wykonywania logiki po stronie serwera i tworzenia architektur bezserwerowych.

- Wybór najlepszej usługi platformy Azure dla Twojej firmy
- Tworzenie Azure Functions
- Korzystanie z wyzwalaczy
- Funkcje łańcucha
- Długotrwałe przepływy pracy
- Monitorowanie
- Programowanie, testowanie i wdrażanie

[Tworzenie aplikacji bezserwerowych](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a>Przeglądy klientów

Ten przykład przedstawia nowe narzędzia Azure Functions dla bibliotek klas C# w programie Visual Studio. Utwórz witrynę sieci Web, w której klienci przesyłają przeglądy produktów, które są przechowywane w obiektach Blob usługi Azure Storage i CosmosDB. Dodaj funkcję platformy Azure, aby przeprowadzać automatyczne moderowanie przeglądów klientów przy użyciu usługi Azure Cognitive Services. Użyj kolejki usługi Azure Storage, aby oddzielić witrynę internetową od funkcji.

[Aplikacja przegląda klienta z Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a>Obsługa obrazów platformy Docker Linux

Ten przykład pokazuje, jak utworzyć `Dockerfile` i uruchomić Azure Functions w kontenerze Docker systemu Linux.

[Azure Functions w systemie Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a>Przetwarzanie i sprawdzanie poprawności plików

Ten przykład analizuje zestaw plików CSV od hipotetycznych klientów. Gwarantuje to, że wszystkie pliki wymagane przez klienta "Batch" są gotowe, a następnie sprawdza poprawność struktury każdego pliku. Różne rozwiązania są prezentowane przy użyciu Azure Functions, Logic Apps i Durable Functions.

[Przetwarzanie i sprawdzanie poprawności plików przy użyciu Azure Functions, Logic Apps i Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a>Wizualizacja danych gry

![Telemetria gier](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

Przykład sposobu, w jaki deweloper może zaimplementować rozwiązanie wizualizacji danych w edytorze dla swojej gry. W rzeczywistości wtyczka aparatu Unreal 4 i wtyczka aparatu Unity zostały opracowane przy użyciu tego przykładu jako zaplecza. Składnik usługi to niezależny od aparatu gry.

[Wizualizacja telemetrii gier w edytorze](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a>GraphQL

Utwórz bezserwerową funkcję, która uwidacznia interfejs API GraphQL.

[Funkcje bezserwerowe dla GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a>Niezawodny przekaźnik graniczny Internet rzeczy (IoT)

![Architektura IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

Ten przykład implementuje nowy protokół komunikacyjny, aby umożliwić niezawodne komunikacji nadrzędnej z urządzeń IoT. Automatyzuje wykrywanie przerw w danych i wypełnianie.

[Niezawodny przekaźnik IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a>Architektura referencyjna mikrousług

![Architektura referencyjna](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

Architektura referencyjna, która przeprowadzi Cię przez proces podejmowania decyzji związanych z projektowaniem, tworzeniem i dostarczaniem RideShare przez aplikację Relecloud (fikcyjnej firmy). Zawiera instrukcje praktyczne dotyczące konfigurowania i wdrażania wszystkich składników architektury.

[Architektura referencyjna mikrousług bezserwerowych](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a>Migrowanie aplikacji konsolowych do bezserwerowego

Ten przykład to funkcja generyczna (`.csx` plik), która może służyć do konwersji dowolnej aplikacji konsolowej do usługi sieci Web HTTP w Azure Functions. Wystarczy edytować plik konfiguracji i określić, jakie parametry wejściowe będą przekazane jako argumenty do `.exe`.

[Uruchom aplikacje konsolowe na Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a>Bezserwerowy dla urządzeń przenośnych

Azure Functions można łatwo zaimplementować i zachować i uzyskać dostęp za pośrednictwem protokołu HTTP. Są one doskonałym sposobem implementacji interfejsu API dla aplikacji mobilnej. Firma Microsoft oferuje wspaniałe narzędzia dla wielu platform dla systemów iOS, Android i Windows za pomocą platformy Xamarin. W związku z tym platformy Xamarin i Azure Functions działają doskonale. W tym artykule pokazano, jak wdrożyć funkcję platformy Azure w portalu internetowym platformy Azure lub w programie Visual Studio w pierwszej kolejności oraz utworzyć klienta międzyplatformowego za pomocą interfejsu Xamarin. Forms działającego w systemach Android, iOS i Windows.

[Implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a>Obsługa komunikatów bezserwerowych

Ten przykład pokazuje, jak użyć wzorca wentylatorów Durable Functions "do załadowania dowolnej liczby komunikatów na dowolną liczbę sesji/partycji. Jest ona przeznaczona dla kolejek Service Bus, Event Hubs lub magazynu. Przykład dodaje również możliwość korzystania z tych komunikatów z inną funkcją platformy Azure i ładowania powstających danych o chronometrażu w innym centrum zdarzeń. Dane są następnie pozyskiwane na usługi analizy, takie jak Azure Eksplorator danych.

[Tworzenie i używanie komunikatów za pomocą kolejek Service Bus, Event Hubs i magazynu przy użyciu Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a>Zalecane zasoby

- [Azure Functions w systemie Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [Przetwarzanie danych Big Data: bezserwerowe MapReduce na platformie Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [Tworzenie aplikacji bezserwerowych](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [Aplikacja przegląda klienta z Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [Przetwarzanie i sprawdzanie poprawności plików przy użyciu Azure Functions, Logic Apps i Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [Implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Wizualizacja telemetrii gier w edytorze](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [Niezawodny przekaźnik IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [Tworzenie i używanie komunikatów za pomocą kolejek Service Bus, Event Hubs i magazynu przy użyciu Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [Uruchom aplikacje konsolowe na Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [Funkcje bezserwerowe dla GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [Architektura referencyjna mikrousług bezserwerowych](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
>[Poprzedni](orchestration-patterns.md)
>[Następny](serverless-conclusion.md)
