---
title: Równoważenie obciążenia gRPC-gRPC dla deweloperów WCF
description: Wybieranie modułu równoważenia obciążenia do pracy z usługami gRPC Services.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5d4a9be9b8f4e511a72af6b68d8a005604fd984d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184394"
---
# <a name="load-balancing-grpc"></a>Równoważenie obciążenia gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Typowe wdrożenie aplikacji gRPC obejmuje wiele identycznych wystąpień usługi, zapewniając odporność i skalowalność w poziomie. Równoważenie obciążenia rozproszone żądania przychodzące w tych wystąpieniach w celu zapewnienia pełnego użycia wszystkich dostępnych zasobów. Aby ta funkcja równoważenia obciążenia była niewidoczna dla klienta, często używany jest serwer usługi równoważenia obciążenia proxy do obsługi żądań od klientów i kierowania ich do wystąpień zaplecza.

Usługi równoważenia obciążenia są klasyfikowane zgodnie z *warstwą* , w której działają. Moduły równoważenia obciążenia warstwy 4 pracują na poziomie *transportu* , na przykład z gniazdami TCP, połączeniami i pakietami. Moduły równoważenia obciążenia warstwy 7 działają na poziomie *aplikacji* , w tym obsługa żądań HTTP/2 dla aplikacji gRPC.

## <a name="l4-load-balancers"></a>Moduły równoważenia obciążenia P4

Moduł równoważenia obciążenia P4 akceptuje żądanie połączenia TCP od klienta, otwiera inne połączenie z jednym z wystąpień zaplecza i kopiuje dane między dwoma połączeniami bez rzeczywistego przetwarzania. P4 oferuje doskonałą wydajność i małe opóźnienia, ale bardzo małą kontrolę i analizę. Dopóki klient utrzymuje otwarte połączenie, wszystkie żądania będą kierowane do tego samego wystąpienia zaplecza.

Przykładem modułu równoważenia obciążenia P4 jest [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).

## <a name="l7-load-balancers"></a>Moduły równoważenia obciążenia P7

Moduł równoważenia obciążenia P7 analizuje przychodzące żądania HTTP/2 i przekazuje je do wystąpień zaplecza na podstawie żądania na żądanie, niezależnie od tego, jak długo połączenie jest przechowywane przez klienta.

Przykłady modułów równoważenia obciążenia P7:

- [Nginx](https://www.nginx.com/)
- [HAproxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Zgodnie z zasadą dla elementu kciuka, moduły równoważenia obciążenia P7 są najlepszym wyborem dla gRPC i innych aplikacji HTTP/2 (a także dla aplikacji HTTP ogólnie w rzeczywistości). Usługi równoważenia obciążenia P4 będą *współpracować* z aplikacjami gRPC, ale są szczególnie przydatne w przypadku małych opóźnień i niskiego obciążenia.

> [!IMPORTANT]
> W czasie tego pisania nie wszystkie moduły równoważenia obciążenia P7 obsługują wszystkie części specyfikacji protokołu HTTP/2 wymagane przez usługi gRPC, takie jak nagłówki końcowe.

W przypadku korzystania z szyfrowania TLS usługi równoważenia obciążenia mogą przerwać połączenie TLS i przekazać nieszyfrowane żądania do aplikacji zaplecza lub przekazać zaszyfrowane żądanie razem. W obu przypadkach moduł równoważenia obciążenia musi być skonfigurowany z kluczem publicznym i prywatnym serwera, dzięki czemu może odszyfrować żądania przetwarzania.

Zapoznaj się z dokumentacją preferowanego modułu równoważenia obciążenia, aby dowiedzieć się, jak skonfigurować go do obsługi żądań HTTP/2 w ramach usług zaplecza.

## <a name="load-balancing-within-kubernetes"></a>Równoważenie obciążenia w Kubernetes

Zapoznaj [się z sekcją dotyczącą siatek usług](service-mesh.md) , aby zapoznać się z omówieniem równoważenia obciążenia w ramach usług wewnętrznych w systemie Kubernetes.

>[!div class="step-by-step"]
>[Poprzedni](service-mesh.md)
>[Następny](application-performance-management.md)
