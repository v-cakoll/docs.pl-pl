---
title: Przykładowe scenariusze biznesowe i przypadki użycia aplikacji bezserwerowych
description: Ucz się bezserwerowe z praktycznepodejście, uzyskując dostęp do próbek, które wahają się od przetwarzania obrazu do mobilnych zaplecza i potoków ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787894"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scenariusze biznesowe i przypadki użycia bez korzystania z serwera

Istnieje wiele przypadków użycia i scenariuszy dla aplikacji bezserwerowych. Ten rozdział zawiera przykłady, które ilustrują różne scenariusze. Scenariusze obejmują łącza do powiązanej dokumentacji i repozytoriów publicznego kodu źródłowego. Przykłady w tym rozdziale umożliwiają rozpoczęcie pracy nad własnym i wdrażającym rozwiązania bezserwerowe.

## <a name="analyze-and-archive-images"></a>Analizowanie i archiwizowanie obrazów

W tym przykładzie przedstawiono zdarzenia bezużycia serwera (siatka zdarzeń), przepływy pracy (aplikacja logiki) i kod (Usługi Azure Functions). Pokazuje również, jak zintegrować z innym zasobem, w tym przypadku usług Cognitive Services do analizy obrazu.

Aplikacja konsolowa umożliwia przekazanie łącza do adresu URL w sieci Web. Aplikacja publikuje adres URL jako komunikat siatki zdarzeń. Równolegle aplikacja funkcji bezserwerowych i aplikacja logiki subskrybują komunikat. Aplikacja funkcji bez serwerów serializuje obraz do magazynu obiektów blob. Przechowuje również informacje w usłudze Azure Table Storage. Metadane przechowuje oryginalny adres URL obrazu i nazwę obrazu obiektu blob. Aplikacja logiki współdziała z interfejsem API niestandardowych wizji, aby analizować obraz i utworzyć podpis wygenerowany maszynowo. Podpis jest przechowywany w tabeli metadanych.

![Analizowanie i archiwizowanie architektury obrazów](./media/image-processing-example.png)

Oddzielna aplikacja jednostronicowa (SPA) wywołuje funkcję bezserwerową, aby uzyskać listę obrazów i metadanych. Dla każdego obrazu wywołuje inną funkcję, która dostarcza dane obrazu z archiwum. Efektem końcowym jest galeria z automatycznymi podpisami.

![Zautomatyzowana galeria obrazów](./media/automated-image-gallery.png)

Pełne repozytorium i instrukcje tworzenia aplikacji logiki są dostępne tutaj: [Klej siatki zdarzeń](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Wieloplatformowy klient mobilny korzystający z platformy Xamarin.Forms i funkcji

Zobacz, jak zaimplementować prostą bezserwerową funkcję platformy Azure w witrynie Azure Web Portal lub w programie Visual Studio. Zbuduj klienta za pomocą platformy Xamarin.Forms działającej w systemach Android, iOS i Windows. Aplikacja jest następnie udoskonalana, aby używać JavaScript Object Notation (JSON) jako nośnika komunikacji między serwerem a klientami mobilnymi z bezserwerowym zapleczem.

Aby uzyskać więcej informacji, zobacz [Implementowanie prostej funkcji platformy Azure za pomocą klienta Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generowanie mozaiki zdjęć z rozpoznawaniem obrazu bez serwerów

Przykład używa funkcji Azure Functions i microsoft Cognitive Services Custom Vision Service do generowania mozaiki zdjęć z obrazu wejściowego. Model jest przeszkolony do rozpoznawania obrazów. Po przesłaniu obrazu rozpoznaje obraz i wyszukiwania za pomocą usługi Bing. Oryginalny obraz jest ponownie skomponowany przy użyciu wyników wyszukiwania.

![Orlando zdjęcie oczu i mozaiki](./media/orlando-eye-both.png)

Na przykład można trenować model z orlando punktów orientacyjnych, takich jak Orlando Eye. Custom Vision rozpozna obraz Orlando Eye, a funkcja stworzy mozaikę zdjęć składającą się z wyników wyszukiwania obrazów Bing dla "Orlando Eye".

Aby uzyskać więcej informacji, zobacz [Generator mozaiki fotograficznej usługi Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrowanie istniejącej aplikacji do chmury

Jak omówiono w poprzednich rozdziałach, często obejmuje architektury n-warstwy do hosta aplikacji w środowisku lokalnym. Chociaż migracja zasobów "tak jak jest" przy użyciu maszyn wirtualnych jest najmniej ryzykowna ścieżka do chmury, wiele firm decyduje się na możliwość refaktoryzacji swoich aplikacji. Na szczęście refaktoryzacja nie musi być "wszystko albo nic" wysiłku. W rzeczywistości jest możliwe do migracji aplikacji, a następnie fragmentaryczne zastąpić składniki z odpowiednikami macierzystych chmury.

Aplikacja korzysta z funkcji serwerów proxy funkcji azure funkcji, aby umożliwić refaktoryzacji punktu końcowego ze starszego kodu lokalnego do punktu końcowego bez użycia serwera.

![Architektura migracji](./media/migration-architecture.png)

Serwer proxy udostępnia pojedynczy punkt końcowy interfejsu API, który jest aktualizowany w celu zmiany trasy poszczególnych żądań, ponieważ są one przenoszone do funkcji bezserwerowych.

Możesz wyświetlić klip wideo, który przechodzi przez całą migrację: [Podnoszenie i przesuwanie za pomocą funkcji platformy Azure bez serwerów](https://channel9.msdn.com/Events/Connect/2017/E102). Dostęp do przykładowego kodu: [Przynieś własną aplikację](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analizuj plik CSV i wstawiaj do bazy danych

Wyodrębnianie, przekształcanie i ładowanie (ETL) jest wspólną funkcją biznesową, która integruje różne systemy. Tradycyjne podejścia często obejmują konfigurowanie dedykowanych serwerów FTP, a następnie wdrażanie zaplanowanych zadań w celu analizowania plików i tłumaczenia ich do użytku biznesowego. Architektura bezserwerowa ułatwia zadanie, ponieważ wyzwalacz może być uruchamiany po przesłaniu pliku. Usługa Azure Functions rozwiązuje zadania, takie jak ETL, za pośrednictwem idealnego składu małych fragmentów kodu, które koncentrują się na określonym problemie.

![Zrzut ekranu przedstawiający proces analizowania csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Aby uzyskać kod źródłowy i praktyczne laboratorium, zobacz [Laboratorium importu CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Skracanie linków i śledzenie danych

Narzędzia skracające łącza pierwotnie pomogły zakodować adresy URL w krótkich postach na Twitterze, aby dostosować się do limitu 140 znaków. Stały się one obejmujące kilka zastosowań, najczęściej do śledzenia klikania dla analityki. Scenariusz skracacza łączy jest całkowicie bezserwerową aplikacją, która zarządza łączami i raportami metryki.

Usługa Azure Functions służy do obsługi aplikacji jednostronicowej (SPA), która umożliwia wklejanie długiego adresu URL i generowanie krótkich adresów URL. Adresy URL są oznaczane w celu śledzenia takich rzeczy, jak kampanie (tematy) i media (takie jak sieci społecznościowe, do których są publikowane linki). Krótki kod jest przechowywany w usłudze Azure Table Storage jako klucz, z długim adresem URL jako wartości. Po kliknięciu krótkiego łącza inna funkcja wyszbędzie długi adres URL, wyśle przekierowanie i umiejscje informacje o zdarzeniu w kolejce. Inna funkcja platformy Azure przetwarza kolejkę i umieszcza informacje w usłudze Azure Cosmos DB.

![Architektura skracacza łączy](./media/link-shortener-architecture.png)

Następnie można utworzyć pulpit nawigacyjny usługi Power BI, aby zebrać szczegółowe informacje o zebranych danych. Na zapleczu usługa Application Insights udostępnia ważne metryki. Telemetria zawiera, jak długo trwa dla przeciętnego użytkownika do przekierowania i jak długo trwa dostęp do usługi Azure Table Storage.

![Przykład usługi Power BI](./media/power-bi-example.png)

Pełny link shortener repozytorium z instrukcjami jest dostępny tutaj: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener). Możesz przeczytać o uproszczonej wersji tutaj: [Usługa Azure Storage dla aplikacji .NET bezserwerowych w ciągu kilku minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Weryfikowanie łączności urządzenia przy użyciu funkcji ping

Przykład składa się z usługi Azure IoT Hub i funkcji platformy Azure. Nowy komunikat w Centrum IoT wyzwala funkcję platformy Azure. Kod bezserwerowy wysyła tę samą zawartość wiadomości z powrotem do urządzenia, które go wysłało. Projekt ma wszystkie kodu i konfiguracji wdrożenia potrzebne do rozwiązania.

Aby uzyskać więcej informacji, zobacz [polecenie ping usługi Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Zalecane zasoby

- [Generator mozaiki fotograficznej Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Ping usługi Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Usługa Azure Storage dla aplikacji platformy .net bezserwerowej w ciągu kilku minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Przynieś własną aplikację](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratorium importu CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Klej siatki zdarzeń](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implementowanie prostej funkcji platformy Azure za pomocą klienta Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Podnoszenie i przenoszenie dzięki funkcjom platformy Azure bez serwerów](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Bezserwerowy shortener adresu URL](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Poprzedni](orchestration-patterns.md)
>[następny](serverless-conclusion.md)
