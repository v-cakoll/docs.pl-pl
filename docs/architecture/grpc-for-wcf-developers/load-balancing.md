---
title: Równoważenie obciążenia gRPC-gRPC dla deweloperów WCF
description: Wybieranie modułu równoważenia obciążenia do pracy z usługami gRPC Services.
ms.date: 09/02/2019
ms.openlocfilehash: 215c0983146bbf9168f01956d64733f80cea6faf
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711172"
---
# <a name="load-balancing-grpc"></a>Równoważenie obciążenia gRPC

Typowe wdrożenie aplikacji gRPC obejmuje wiele identycznych wystąpień usługi, zapewniając odporność i skalowalność w poziomie. Równoważenie obciążenia dystrybuuje żądania przychodzące między tymi wystąpieniami, aby zapewnić pełne użycie wszystkich dostępnych zasobów. Aby ta funkcja równoważenia obciążenia była niewidoczna dla klienta, często używany jest serwer usługi równoważenia obciążenia proxy do obsługi żądań od klientów i kierowania ich do wystąpień zaplecza.

Usługi równoważenia obciążenia są klasyfikowane zgodnie z *warstwą* , w której działają. Moduły równoważenia obciążenia warstwy 4 pracują na poziomie *transportu* , na przykład z gniazdami TCP, połączeniami i pakietami. Moduły równoważenia obciążenia warstwy 7 działają na poziomie *aplikacji* , w tym obsługa żądań HTTP/2 dla aplikacji gRPC.

## <a name="l4-load-balancers"></a>Moduły równoważenia obciążenia P4

Moduł równoważenia obciążenia P4 akceptuje żądanie połączenia TCP od klienta, otwiera inne połączenie z jednym z wystąpień zaplecza i kopiuje dane między dwoma połączeniami bez rzeczywistego przetwarzania. P4 oferuje doskonałą wydajność i małe opóźnienia, ale bardzo małą kontrolę i analizę. Dopóki klient utrzymuje otwarte połączenie, wszystkie żądania będą kierowane do tego samego wystąpienia zaplecza.

 [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) to przykład modułu równoważenia obciążenia P4.

## <a name="l7-load-balancers"></a>Moduły równoważenia obciążenia P7

Moduł równoważenia obciążenia P7 analizuje przychodzące żądania HTTP/2 i przekazuje je do wystąpień zaplecza na podstawie żądania na żądanie, niezależnie od tego, jak długo połączenie jest przechowywane przez klienta.

Przykłady modułów równoważenia obciążenia P7:

- [NGINX](https://www.nginx.com/)
- [HAProxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Zgodnie z zasadą dla elementu kciuka, moduły równoważenia obciążenia P7 są najlepszym wyborem dla gRPC i innych aplikacji HTTP/2 (a także dla aplikacji HTTP ogólnie w rzeczywistości). Usługi równoważenia obciążenia P4 będą *współpracować* z aplikacjami gRPC, ale są one szczególnie przydatne w przypadku małych opóźnień i niskiego obciążenia.

> [!IMPORTANT]
> Podczas tego pisania niektóre moduły równoważenia obciążenia P7 nie obsługują wszystkich części specyfikacji protokołu HTTP/2, które są wymagane przez usługi gRPC, takie jak nagłówki końcowe.

W przypadku korzystania z szyfrowania TLS usługi równoważenia obciążenia mogą przerywać połączenie TLS i przekazywać nieszyfrowane żądania do aplikacji zaplecza lub mogą przekazywać zaszyfrowane żądanie razem. W obu przypadkach moduł równoważenia obciążenia musi być skonfigurowany z publicznym i prywatnym kluczem serwera, aby można było odszyfrować żądania do przetwarzania.

Zapoznaj się z dokumentacją preferowanego modułu równoważenia obciążenia, aby dowiedzieć się, jak skonfigurować go do obsługi żądań HTTP/2 w ramach usług zaplecza.

## <a name="load-balancing-within-kubernetes"></a>Równoważenie obciążenia w Kubernetes

Zapoznaj [się z sekcją dotyczącą siatek usług](service-mesh.md) , aby zapoznać się z omówieniem równoważenia obciążenia w ramach usług wewnętrznych w systemie Kubernetes.

>[!div class="step-by-step"]
>[Poprzednie](service-mesh.md)
>[dalej](application-performance-management.md)
