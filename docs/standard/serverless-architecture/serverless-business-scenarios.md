---
title: Przykładowe scenariusze biznesowe i przypadki użycia aplikacji bez użycia serwera
description: Dowiedz się bez użycia serwera, praktyczne podejście przez uzyskanie dostępu do przykładów z zakresu przetwarzania obrazu mobilnych zaplecza i dostępne potoki przetwarzania ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 177fb1d7f79a0067ab185e520778b593d4b8eaf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017271"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scenariusze biznesowe i przypadki użycia bez korzystania z serwera

Istnieje wiele przypadków użycia i scenariuszy dla aplikacji bez użycia serwera. Ten rozdział zawiera przykłady ilustrujące różnych scenariuszy. Scenariusze obejmują linki do powiązanej dokumentacji i publicznych repozytoriach kodów źródłowych. Przykłady w tym rozdziale umożliwiają rozpoczęcie pracy własne kompilowanie i wdrażanie rozwiązań nieużywających serwera.

## <a name="analyze-and-archive-images"></a>Analizuj i archiwizowanie obrazów

Niniejszy przykład pokazuje zdarzeń bez użycia serwera (usługa Event Grid), przepływy pracy (aplikacji logiki) i kod (usługi Azure Functions). Pokazano również, jak zintegrować z innego zasobu w tej wielkości liter, Cognitive Services do analizy obrazu.

Aplikację konsolową w języku umożliwia przekazywanie łącze do adresu URL w sieci web. Aplikacja publikuje adresu URL jako wiadomość siatki zdarzeń. Równolegle to aplikacja funkcję niewymagającą użycia serwera, a aplikacja logiki subskrybować wiadomości. Bezserwerowa aplikacja funkcji serializuje obrazu do usługi blob storage. Przechowuje także informacji w usłudze Azure Table Storage. Metadane są przechowywane, oryginalny adres URL obrazu i nazwę obrazu, obiektów blob. Aplikacja logiki współdziała z niestandardowego interfejsu API przetwarzania do analizowania obrazu i utworzyć podpis generowany sprzętowo. Podpis jest przechowywane w tabeli metadanych.

![Analizuj i archiwizowanie architektury obrazów](./media/image-processing-example.png)

Aplikacji oddzielne jednostronicowej (SPA) wywołuje funkcję niewymagającą użycia serwera, aby uzyskać listę obrazów i metadanych. Dla każdego obrazu wywołuje inną funkcję, która dostarcza dane obrazu z archiwum. Wynik końcowy jest Galeria o transkrypcji automatycznych.

![Galeria obrazów automatycznych](./media/automated-image-gallery.png)

Pełne repozytorium i instrukcje dotyczące tworzenia aplikacji logiki są tutaj dostępne: [Event grid pośredniczącego](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Dla wielu platform klienta mobilnego za pomocą platformy Xamarin.Forms i funkcje

Zobacz, jak wdrożyć prostą bezserwerowej funkcji platformy Azure w portalu sieci Web platformy Azure lub w programie Visual Studio. Tworzenie klienta przy użyciu zestawu narzędzi Xamarin.Forms, który jest uruchamiany w systemach Android, iOS i Windows. Aplikacja jest następnie Elegancja służące JavaScript Object Notation (JSON) jako średniej lub komunikacji między serwerem a klientów mobilnych za pomocą bez użycia serwera zaplecza.

Aby uzyskać więcej informacji, zobacz [implementacji prostej funkcji platformy Azure przy użyciu klienta interfejsu Xamarin.Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generowanie mozaiki zdjęcia przy użyciu rozpoznawania obrazów bez użycia serwera

W przykładzie użyto usługi Azure Functions i Microsoft Cognitive Services usługi Custom Vision Service do generowania mozaiki zdjęć z obrazu wejściowego. Model jest uczony do rozpoznawania obrazów. Po przekazaniu obrazu rozpoznaje obrazu i wyszukiwania przy użyciu usługi Bing. Oryginalny obraz jest przeskładanie za pomocą wyników wyszukiwania.

![Orlando oka zdjęć i mozaiki](./media/orlando-eye-both.png)

Na przykład możesz uczyć modelu za pomocą Orlando punkty orientacyjne, takie jak oka Orlando. Custom Vision rozpozna obrazu oka Orlando, a funkcja spowoduje utworzenie mozaiki zdjęcie składa się z wyników wyszukiwania obrazów Bing "Orlando oka".

Aby uzyskać więcej informacji, zobacz [generator mozaiki zdjęć usługi Azure Functions](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Zmigrowanie istniejącej aplikacji w chmurze

Zgodnie z opisem w poprzednich akapitach, jest często przyjęcie architektury N-warstwowej do hostowania swojej aplikacji w środowisku lokalnym. Mimo że migracja zasobów "w jakim jest" przy użyciu maszyn wirtualnych jest najmniej ryzykowne drogą do chmury, wiele firm wybierz Refaktoryzuj swoich aplikacji za pomocą szansy sprzedaży. Na szczęście refaktoryzacji nie musi być "sztywnego" nakładu pracy. W rzeczywistości jest możliwe do migracji aplikacji, a następnie przyjąć Zastąp składników z odpowiednikami natywnych w chmurze.

Aplikacja korzysta z funkcji serwery proxy usługi Azure functions, Włącz refaktoryzację punktu końcowego z kodu w starszej wersji środowiska lokalnego do endpoint bez użycia serwera.

![Architekturę migracji](./media/migration-architecture.png)

Serwer proxy zapewnia jeden punkt końcowy interfejsu API, która jest aktualizowana w celu przekierowywania poszczególnych żądań, ponieważ są one przenoszone do funkcje niewymagające użycia serwera.

Możesz wyświetlić film wideo, który przeprowadzi migrację całej: [Lift- and -shift przy użyciu bezserwerowej usługi Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102). Dostęp do przykładowego kodu: [Przenieś swoją własną aplikację](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analizowanie pliku CSV i wstawić do bazy danych

Wyodrębnianie, przekształcanie, i ładowania (ETL) jest typowych funkcji biznesowych, która integruje różne systemy. Tradycyjne podejścia często oznaczać między innymi konfigurowaniu dedykowanych serwerów FTP, a następnie wdrażania zaplanowanych zadań, aby przeanalizować pliki i tłumaczyć je do użytku służbowego. Architektura bezserwerowa ułatwia zadania, ponieważ wyzwalacz może wyzwalać po przekazaniu pliku. Zadania Associates usługi Azure Functions, takich jak ETL za pomocą jego idealne skład małych fragmentów kodu, które koncentrują się na konkretnego problemu.

![Zrzut ekranu pokazujący analizy procesu csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Kod źródłowy i praktycznym laboratorium, zobacz [CSV zaimportować laboratorium](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Skróć łącza i śledzenie metryk

Narzędzia skracanie łącze pierwotnie brały udział w skrócie kodowania adresów URL w usłudze twitter wpisów, aby pomieścić limit 140 znaków. One doceniają obejmują kilka zastosowań, najczęściej śledzenie kliknięć dla analizy. Scenariusz skracania adresów łącze jest całkowicie bez użycia serwera aplikacji, która zarządza łącza i raporty metryk.

Usługa Azure Functions jest używany do obsługi jednej strony aplikacji (SPA) umożliwiający Wklej długiego adresu URL i wygenerować krótkimi adresami URL. Adresy URL są oznaczone do śledzenia elementów, takich jak kampanii (tematy) i nośników (np. sieci społecznościowych, zaksięgowanych łącza). Krótki kod znajduje się w usłudze Azure Table Storage jako klucz, za pomocą długiego adresu URL jako wartość. Po kliknięciu krótki link innej funkcji wyszukuje długiego adresu URL, wysyła przekierowania i umieszcza informacje o zdarzeniu w kolejce. Inna funkcja platformy Azure przetwarza kolejki i umieszcza je w usłudze Azure Cosmos DB.

![Architektura usług skracania adresów łącza](./media/link-shortener-architecture.png)

Następnie możesz utworzyć pulpit nawigacyjny usługi Power BI w celu zbierania szczegółowych informacji o zebranych danych. Na zapleczu Application Insights udostępnia ważne metryki. Dane telemetryczne obejmuje, ile trwa średni użytkownikowi przekierowania i jak długo trwa dostęp do usługi Azure Table Storage.

![Usługa Power BI przykład](./media/power-bi-example.png)

Repozytorium skracania adresów pełna konsolidacja, korzystając z instrukcji jest dostępna tutaj: [Skracanie adresów URL bez użycia serwera](https://github.com/jeremylikness/serverless-url-shortener). Możesz przeczytać o uproszczonej wersji: [Usługa Azure Storage dla aplikacji .NET bez użycia serwera w ciągu kilku minut](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Sprawdź łączność urządzeń za pomocą polecenia ping

Przykład składa się z usługi Azure IoT Hub i funkcji platformy Azure. Nowa wiadomość w usłudze IoT Hub wywołuje funkcję platformy Azure. Kod bez użycia serwera wysyła tę samą wiadomość w zawartości do urządzeń, która przesłała ten. Projekt ma całą konfigurację kodu i wdrażania służące do rozwiązania.

Aby uzyskać więcej informacji, zobacz [ping usługi Azure IoT Hub](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Zalecane zasoby

* [Generator mozaiki zdjęć w usłudze platformy Azure funkcji](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Usługa Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Usługa Azure Storage dla aplikacji .NET bez użycia serwera w ciągu kilku minut](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [Przenieś swoją własną aplikację](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [Woluminów CSV import laboratorium](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Przyklej siatki zdarzeń](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Implementowanie prostego funkcji platformy Azure za pomocą klienta interfejsu Xamarin.Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Lift- and -shift przy użyciu bezserwerowej usługi Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Skracanie adresów URL bez użycia serwera](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Poprzednie](orchestration-patterns.md)
>[dalej](serverless-conclusion.md)