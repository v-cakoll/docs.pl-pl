---
title: Protokoły sieciowe — gRPC dla deweloperów WCF
description: Omówienie protokołów sieciowych gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a176d3e84f5f454f746273c9cc7e7afe7c7f9d8a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184289"
---
# <a name="network-protocols"></a>Protokoły sieciowe

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W przeciwieństwie do WCF, gRPC używa protokołu HTTP/2 jako podstawy dla sieci. Zapewnia to znaczne zalety usług WCF i SOAP, które działają tylko w przypadku protokołu HTTP/1.1. Deweloperzy chcą korzystać z gRPC, ponieważ nie istnieje alternatywa dla protokołu HTTP/2. wydaje się to idealnym momentem do eksplorowania protokołu HTTP/2 i zidentyfikowania dodatkowych korzyści związanych z korzystaniem z gRPC.

Protokół HTTP/2 wydawany przez dział Internet Engineering Task Force w 2015 został utworzony na podstawie eksperymentalnego protokołu SPDY, który jest już używany przez firmę Google. Został specjalnie zaprojektowany tak, aby był bardziej wydajny, szybszy i bezpieczniejszy niż protokół HTTP/1.1.

## <a name="key-features-of-http2"></a>Najważniejsze funkcje protokołu HTTP/2

Na poniższej liście przedstawiono niektóre najważniejsze funkcje i zalety protokołu HTTP/2:

### <a name="binary-protocol"></a>Protokół binarny

Cykle żądania/odpowiedzi nie potrzebują już poleceń tekstowych. Upraszcza to i przyspiesza implementację poleceń. W związku z tym dane analizy są szybsze i zużywają mniej pamięci, opóźnienie sieci jest skracane z oczywistymi powiązanymi ulepszeniami w zakresie szybkości i istnieje ogólne lepsze wykorzystanie zasobów sieciowych.

### <a name="streams"></a>Strumienie

Strumienie umożliwiają tworzenie długotrwałych połączeń między nadawcą i odbiornikiem, przez co wiele komunikatów lub ramek można wysyłać asynchronicznie. Wiele strumieni może działać niezależnie w ramach pojedynczego połączenia HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Żądanie multipleksowania przez pojedyncze połączenie TCP

Ta funkcja jest jednym z najważniejszych innowacji protokołu HTTP/2. Dzięki umożliwieniu wielu równoległych żądań danych można teraz pobierać pliki internetowe jednocześnie z jednego serwera. Szybsze ładowanie witryn sieci Web i wymaganie optymalizacji jest ograniczone. Blokowanie głowy (dzień HOL), w którym odpowiedzi są gotowe do wysłania do momentu ukończenia wcześniejszego żądania, również zostały skorygowane (mimo że blokowanie w programie HOL nadal może wystąpić na poziomie transportu TCP).

### <a name="nettcp-like-performance-cross-platform"></a>NetTCP wydajność na wielu platformach

Zasadniczo, kombinacja gRPC i HTTP/2 oferuje deweloperom co najmniej równoważną szybkość i wydajność powiązań NetTCP dla usług WCF, a w niektórych przypadkach jeszcze większą szybkość i wydajność. Jednak w przeciwieństwie do NetTCP, gRPC za pośrednictwem protokołu HTTP/2 nie są ograniczone do aplikacji .NET.

>[!div class="step-by-step"]
>[Poprzedni](interface-definition-language.md)
>[Następny](why-grpc.md)
