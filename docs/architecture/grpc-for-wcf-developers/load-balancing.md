---
title: Równoważenie obciążenia gRPC-gRPC dla deweloperów WCF
description: Wybieranie modułu równoważenia obciążenia do pracy z usługami gRPC Services.
ms.date: 09/02/2019
ms.openlocfilehash: 070fc7fda73988302d15c8cec12b1ac359641317
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967452"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="88bc8-103">Równoważenie obciążenia gRPC</span><span class="sxs-lookup"><span data-stu-id="88bc8-103">Load balancing gRPC</span></span>

<span data-ttu-id="88bc8-104">Typowe wdrożenie aplikacji gRPC obejmuje wiele identycznych wystąpień usługi, zapewniając odporność i skalowalność w poziomie.</span><span class="sxs-lookup"><span data-stu-id="88bc8-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="88bc8-105">Równoważenie obciążenia rozproszone żądania przychodzące w tych wystąpieniach w celu zapewnienia pełnego użycia wszystkich dostępnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="88bc8-105">Load balancing distributed incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="88bc8-106">Aby ta funkcja równoważenia obciążenia była niewidoczna dla klienta, często używany jest serwer usługi równoważenia obciążenia proxy do obsługi żądań od klientów i kierowania ich do wystąpień zaplecza.</span><span class="sxs-lookup"><span data-stu-id="88bc8-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="88bc8-107">Usługi równoważenia obciążenia są klasyfikowane zgodnie z *warstwą* , w której działają.</span><span class="sxs-lookup"><span data-stu-id="88bc8-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="88bc8-108">Moduły równoważenia obciążenia warstwy 4 pracują na poziomie *transportu* , na przykład z gniazdami TCP, połączeniami i pakietami.</span><span class="sxs-lookup"><span data-stu-id="88bc8-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections and packets.</span></span> <span data-ttu-id="88bc8-109">Moduły równoważenia obciążenia warstwy 7 działają na poziomie *aplikacji* , w tym obsługa żądań HTTP/2 dla aplikacji gRPC.</span><span class="sxs-lookup"><span data-stu-id="88bc8-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="88bc8-110">Moduły równoważenia obciążenia P4</span><span class="sxs-lookup"><span data-stu-id="88bc8-110">L4 load balancers</span></span>

<span data-ttu-id="88bc8-111">Moduł równoważenia obciążenia P4 akceptuje żądanie połączenia TCP od klienta, otwiera inne połączenie z jednym z wystąpień zaplecza i kopiuje dane między dwoma połączeniami bez rzeczywistego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="88bc8-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="88bc8-112">P4 oferuje doskonałą wydajność i małe opóźnienia, ale bardzo małą kontrolę i analizę.</span><span class="sxs-lookup"><span data-stu-id="88bc8-112">L4 offers excellent performance and low latency, but very little control or intelligence.</span></span> <span data-ttu-id="88bc8-113">Dopóki klient utrzymuje otwarte połączenie, wszystkie żądania będą kierowane do tego samego wystąpienia zaplecza.</span><span class="sxs-lookup"><span data-stu-id="88bc8-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

<span data-ttu-id="88bc8-114">Przykładem modułu równoważenia obciążenia P4 jest [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span><span class="sxs-lookup"><span data-stu-id="88bc8-114">An example of an L4 load balancer is the [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/).</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="88bc8-115">Moduły równoważenia obciążenia P7</span><span class="sxs-lookup"><span data-stu-id="88bc8-115">L7 load balancers</span></span>

<span data-ttu-id="88bc8-116">Moduł równoważenia obciążenia P7 analizuje przychodzące żądania HTTP/2 i przekazuje je do wystąpień zaplecza na podstawie żądania na żądanie, niezależnie od tego, jak długo połączenie jest przechowywane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="88bc8-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="88bc8-117">Przykłady modułów równoważenia obciążenia P7:</span><span class="sxs-lookup"><span data-stu-id="88bc8-117">Examples of L7 load balancers include:</span></span>

- [<span data-ttu-id="88bc8-118">Nginx</span><span class="sxs-lookup"><span data-stu-id="88bc8-118">Nginx</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="88bc8-119">HAproxy</span><span class="sxs-lookup"><span data-stu-id="88bc8-119">HAproxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="88bc8-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="88bc8-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="88bc8-121">Zgodnie z zasadą dla elementu kciuka, moduły równoważenia obciążenia P7 są najlepszym wyborem dla gRPC i innych aplikacji HTTP/2 (a także dla aplikacji HTTP ogólnie w rzeczywistości).</span><span class="sxs-lookup"><span data-stu-id="88bc8-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="88bc8-122">Usługi równoważenia obciążenia P4 będą *współpracować* z aplikacjami gRPC, ale są szczególnie przydatne w przypadku małych opóźnień i niskiego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="88bc8-122">L4 load balancers will *work* with gRPC applications, but are primarily useful when low latency and low overhead are of paramount importance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88bc8-123">W czasie tego pisania nie wszystkie moduły równoważenia obciążenia P7 obsługują wszystkie części specyfikacji protokołu HTTP/2 wymagane przez usługi gRPC, takie jak nagłówki końcowe.</span><span class="sxs-lookup"><span data-stu-id="88bc8-123">At the time of this writing, not all L7 load balancers support all parts of the HTTP/2 specification required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="88bc8-124">W przypadku korzystania z szyfrowania TLS usługi równoważenia obciążenia mogą przerwać połączenie TLS i przekazać nieszyfrowane żądania do aplikacji zaplecza lub przekazać zaszyfrowane żądanie razem.</span><span class="sxs-lookup"><span data-stu-id="88bc8-124">When using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or pass the encrypted request along.</span></span> <span data-ttu-id="88bc8-125">W obu przypadkach moduł równoważenia obciążenia musi być skonfigurowany z kluczem publicznym i prywatnym serwera, dzięki czemu może odszyfrować żądania przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="88bc8-125">Either way, the load balancer will need to be configured with the server's public and private key, so that it can decrypt requests for processing.</span></span>

<span data-ttu-id="88bc8-126">Zapoznaj się z dokumentacją preferowanego modułu równoważenia obciążenia, aby dowiedzieć się, jak skonfigurować go do obsługi żądań HTTP/2 w ramach usług zaplecza.</span><span class="sxs-lookup"><span data-stu-id="88bc8-126">Refer to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="88bc8-127">Równoważenie obciążenia w Kubernetes</span><span class="sxs-lookup"><span data-stu-id="88bc8-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="88bc8-128">Zapoznaj [się z sekcją dotyczącą siatek usług](service-mesh.md) , aby zapoznać się z omówieniem równoważenia obciążenia w ramach usług wewnętrznych w systemie Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="88bc8-128">See [the section on Service Meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88bc8-129">[Poprzedni](service-mesh.md)
>[Następny](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="88bc8-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>
