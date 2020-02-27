---
title: Protokoły sieciowe — gRPC dla deweloperów WCF
description: Omówienie protokołów sieciowych gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ceb140f7b7ac7e796a87612ebb9d21e28d33968
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628491"
---
# <a name="network-protocols"></a>Protokoły sieciowe

W przeciwieństwie do Windows Communication Foundation (WCF), gRPC używa protokołu HTTP/2 jako podstawy dla sieci. Zapewnia to znaczne zalety usług WCF i SOAP, które działają tylko w przypadku protokołu HTTP/1.1. Deweloperzy chcą korzystać z gRPC, ponieważ nie istnieje alternatywa dla protokołu HTTP/2. wydaje się to idealne rozwiązanie, aby poznać protokół HTTP/2 bardziej szczegółowo i zidentyfikować dodatkowe korzyści wynikające z używania gRPC.

Protokół HTTP/2 wydawany przez dział Internet Engineering Task Force w 2015 został utworzony na podstawie eksperymentalnego protokołu SPDY, który jest już używany przez firmę Google. Został specjalnie zaprojektowany tak, aby był bardziej wydajny, szybszy i bezpieczniejszy niż protokół HTTP/1.1.

## <a name="key-features-of-http2"></a>Najważniejsze funkcje protokołu HTTP/2

Ta lista zawiera najważniejsze funkcje i zalety protokołu HTTP/2:

### <a name="binary-protocol"></a>Protokół binarny

Cykle żądania/odpowiedzi nie potrzebują już poleceń tekstowych. Upraszcza to i przyspiesza implementację poleceń. W związku z tym dane analizy są szybsze i zużywają mniej pamięci, opóźnienie sieci jest skracane z oczywistymi powiązanymi ulepszeniami w zakresie szybkości i istnieje ogólne lepsze wykorzystanie zasobów sieciowych.

### <a name="streams"></a>Strumienie

Strumienie umożliwiają tworzenie długotrwałych połączeń między nadawcą i odbiornikiem, przez co wiele komunikatów lub ramek można wysyłać asynchronicznie. Wiele strumieni może działać niezależnie w ramach pojedynczego połączenia HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Żądanie multipleksowania przez pojedyncze połączenie TCP

Ta funkcja jest jednym z najważniejszych innowacji protokołu HTTP/2. Ponieważ umożliwia wiele żądań danych, można teraz pobierać pliki internetowe jednocześnie z jednego serwera. Szybsze ładowanie witryn sieci Web i konieczność optymalizacji jest ograniczona. Blokowanie linii telefonicznej (HOL), w których odpowiedzi są gotowe do wysłania do momentu ukończenia wcześniejszego żądania, również zostały skorygowane (mimo że blokowanie w programie HOL nadal może wystąpić na poziomie transportu TCP).

### <a name="nettcp-like-performance-cross-platform"></a>Wydajność w sieci net. TCP, na wielu platformach

Zasadniczo, kombinacja gRPC i HTTP/2 oferuje deweloperom co najmniej równoważną szybkość i efektywność powiązań net. TCP dla programu WCF, a w niektórych przypadkach jeszcze większą szybkość i wydajność. Jednak, w przeciwieństwie do net. TCP, gRPC za pośrednictwem protokołu HTTP/2 nie jest ograniczony do aplikacji .NET.

>[!div class="step-by-step"]
>[Poprzednie](interface-definition-language.md)
>[dalej](why-grpc.md)
