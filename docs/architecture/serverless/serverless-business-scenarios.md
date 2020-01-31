---
title: Przykładowe scenariusze biznesowe i przypadki użycia dla aplikacji bezserwerowych
description: Dowiedz się bezserwerowo Dzięki praktycznemu podejściu, uzyskując dostęp do przykładów, które przechodzący od przetwarzania obrazów do zaplecza mobilnego i potoków ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787894"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scenariusze biznesowe i przypadki użycia bez korzystania z serwera

Istnieje wiele przypadków użycia i scenariuszy dotyczących aplikacji bezserwerowych. Ten rozdział zawiera przykłady ilustrujące różne scenariusze. Scenariusze obejmują linki do powiązanej dokumentacji i repozytoriów kodu publicznego. Przykłady w tym rozdziale umożliwiają rozpoczęcie pracy nad tworzeniem i implementowaniem rozwiązań bezserwerowych.

## <a name="analyze-and-archive-images"></a>Analizowanie i archiwizowanie obrazów

Ten przykład demonstruje zdarzenia bezserwerowe (Event Grid), przepływy pracy (aplikacja logiki) i kod (Azure Functions). Pokazano również, jak przeprowadzić integrację z innym zasobem, w tym przypadku Cognitive Services na potrzeby analizy obrazów.

Aplikacja konsolowa umożliwia przekazywanie linku do adresu URL w sieci Web. Aplikacja publikuje adres URL jako komunikat w usłudze Event Grid. Równolegle aplikacja funkcji bezserwerowych i aplikacja logiki subskrybują wiadomość. Aplikacja funkcji bezserwerowego serializować obraz do magazynu obiektów BLOB. Przechowuje również informacje w usłudze Azure Table Storage. Metadane są przechowywane przy użyciu adresu URL oryginalnego obrazu i nazwy obrazu obiektu BLOB. Aplikacja logiki współdziała z interfejsem API Custom Vision, aby przeanalizować obraz i utworzyć podpis wygenerowany przez maszynę. Podpis jest przechowywany w tabeli metadanych.

![Analizowanie i archiwizowanie architektury obrazów](./media/image-processing-example.png)

Oddzielna aplikacja jednostronicowa (SPA) wywołuje funkcję bezserwerową, aby uzyskać listę obrazów i metadanych. Dla każdego obrazu wywołuje kolejną funkcję, która dostarcza dane obrazu z archiwum. Końcowym wynikiem jest Galeria z automatycznymi napisami.

![Galeria obrazów automatycznych](./media/automated-image-gallery.png)

Pełne repozytorium i instrukcje dotyczące kompilowania aplikacji logiki są dostępne tutaj: [przyklej do siatki zdarzeń](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Międzyplatformowy klient mobilny korzystający z narzędzi Xamarin. Forms i Functions

Zobacz, jak zaimplementować prostą bezserwerową funkcję platformy Azure w portalu internetowym platformy Azure lub w programie Visual Studio. Kompiluj klienta przy użyciu interfejsu Xamarin. Forms działającego w systemach Android, iOS i Windows. Następnie aplikacja jest udoskonalana, aby używać JavaScript Object Notation (JSON) jako średniej komunikacji między serwerem a klientami mobilnymi z zapleczem bezserwerowym.

Aby uzyskać więcej informacji, zobacz [implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generowanie mozaiki zdjęć z rozpoznawaniem obrazu bez serwera

Przykład używa Azure Functions i Microsoft Cognitive Services Custom Vision Service do wygenerowania mozaiki zdjęć z obrazu wejściowego. Model jest szkolony do rozpoznawania obrazów. Po przekazaniu obrazu Program rozpoznaje obraz i wyszukuje go przy użyciu usługi Bing. Oryginalny obraz jest tworzony przy użyciu wyników wyszukiwania.

![Fotografia i mozaika Orlando oczu](./media/orlando-eye-both.png)

Na przykład możesz nauczyć model z Orlandoami, takimi jak Orlando. Custom Vision będzie rozpoznawał obraz efektu Orlando, a funkcja utworzy mozaikę zdjęć składającą się z wyników wyszukiwania obrazów Bing dla "oczu Orlando".

Aby uzyskać więcej informacji, zobacz [Azure Functions generatora mozaiki zdjęć](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrowanie istniejącej aplikacji do chmury

Zgodnie z opisem w poprzednich działach, często warto wdrożyć architekturę N-warstwową, aby hostować aplikację lokalnie. Mimo że Migrowanie zasobów "AS IS" przy użyciu maszyn wirtualnych jest najmniej ryzykowną ścieżką do chmury, wiele firm wybiera do użycia możliwość refaktoryzacji aplikacji. Na szczęście Refaktoryzacja nie musi być nakładem "wszystko-ani-Nothing". W rzeczywistości możliwe jest Migrowanie aplikacji, a następnie podmianuje składniki zastępujące elementy z natywnymi odpowiednikami w chmurze.

Aplikacja używa funkcji proxy Azure Functions, aby umożliwić refaktoryzację punktu końcowego ze starszego kodu lokalnego do bezserwerowego punktu końcowego.

![Architektura migracji](./media/migration-architecture.png)

Serwer proxy udostępnia jeden punkt końcowy interfejsu API, który został zaktualizowany do przekierowywania poszczególnych żądań, gdy są one przenoszone do funkcji bezserwerowych.

Możesz wyświetlić film wideo, który przeprowadzi Cię przez całą migrację: [Unieś i Przenieś z usługą Azure Functions bez serwera](https://channel9.msdn.com/Events/Connect/2017/E102). Dostęp do przykładowego kodu: [Przeprowadź własną aplikację](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analizowanie pliku CSV i wstawianie do bazy danych

Wyodrębnianie, przekształcanie i ładowanie (ETL) to typowa funkcja biznesowa, która integruje różne systemy. Tradycyjne podejścia często obejmują skonfigurowanie dedykowanych serwerów FTP, a następnie wdrożenie zaplanowanych zadań do analizy plików i przetłumaczenia ich do użytku biznesowego. Architektura bezserwerowa ułatwia zadanie, ponieważ wyzwalacz może być uruchamiany podczas przekazywania pliku. Azure Functions prowadzi do zadań, takich jak ETL, dzięki idealnemu tworzeniu małych fragmentów kodu, które koncentrują się na konkretnym problemie.

![Zrzut ekranu pokazujący proces analizowania woluminu CSV.](./media/serverless-business-scenarios/csv-parse-database-import.png)

W przypadku kodu źródłowego i laboratorium praktycznego zobacz plik [CSV import Lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Skróć linki i śledź metryki

Narzędzia do skracania rozmiaru ułatwiają kodowanie adresów URL w krótkich wpisach usługi Twitter w celu uwzględnienia limitu znaków 140. Zostały one wyhodowane w taki sposób, aby obejmowały kilka zastosowania, najczęściej do śledzenia klikania w celu analizy. Scenariusz Shortener linku to całkowicie bezserwerowa aplikacja, która zarządza łączami i metrykami raportów.

Azure Functions służy do obsłużenia aplikacji jednostronicowej (SPA), która pozwala na wklejenie długiego adresu URL i wygenerowanie krótkich adresów URL. Adresy URL są oznaczone do śledzenia, takich jak kampanie (tematy) i średnie (takie jak sieci społecznościowe, do których są ogłaszane). Krótki kod jest przechowywany w usłudze Azure Table Storage jako klucz, przy użyciu długiego adresu URL jako wartości. Po kliknięciu krótkiego linku inna funkcja wyszukuje długi adres URL, wysyła przekierowanie i umieszcza informacje o zdarzeniu w kolejce. Inna funkcja platformy Azure przetwarza kolejkę i umieszcza informacje w Azure Cosmos DB.

![Łączenie architektury Shortener](./media/link-shortener-architecture.png)

Następnie możesz utworzyć pulpit nawigacyjny Power BI, aby zebrać szczegółowe informacje o zbieranych danych. Na zapleczu Application Insights zawiera ważne metryki. Dane telemetryczne obejmują czas trwania przekierowania przez średniego użytkownika i czas potrzebny na dostęp do usługi Azure Table Storage.

![Przykład Power BI](./media/power-bi-example.png)

Pełne link Shortener repozytorium z instrukcjami jest dostępny tutaj: [adres URL bezserwerowy Shortener](https://github.com/jeremylikness/serverless-url-shortener). Możesz zapoznać się z wersją uproszczoną tutaj: [usługa Azure Storage dla aplikacji .NET bezserwerowych w ciągu kilku minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Weryfikowanie łączności urządzenia przy użyciu polecenia ping

Przykład składa się z IoT Hub platformy Azure i funkcji platformy Azure. Nowy komunikat na IoT Hub wyzwala funkcję platformy Azure. Kod bezserwerowy wysyła tę samą zawartość wiadomości z powrotem do urządzenia, które je wysłało. Projekt ma cały kod i konfigurację wdrożenia, które są odpowiednie dla rozwiązania.

Aby uzyskać więcej informacji, zobacz [Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Zalecane zasoby

- [Generator mozaiki zdjęć Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Usługa Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Usługa Azure Storage dla aplikacji .NET bezserwerowych w ciągu kilku minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Przenoszenie własnej aplikacji](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratorium importowania woluminów CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Przyklejanie do siatki zdarzeń](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Podnieś i Przenieś za pomocą usługi Azure Functions bez serwera](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Shortener adres URL bezserwerowy](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Poprzedni](orchestration-patterns.md)
>[Następny](serverless-conclusion.md)
