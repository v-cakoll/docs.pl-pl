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
# <a name="network-protocols"></a><span data-ttu-id="39609-103">Protokoły sieciowe</span><span class="sxs-lookup"><span data-stu-id="39609-103">Network protocols</span></span>

<span data-ttu-id="39609-104">W przeciwieństwie do Windows Communication Foundation (WCF), gRPC używa protokołu HTTP/2 jako podstawy dla sieci.</span><span class="sxs-lookup"><span data-stu-id="39609-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="39609-105">Zapewnia to znaczne zalety usług WCF i SOAP, które działają tylko w przypadku protokołu HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="39609-105">This offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="39609-106">Deweloperzy chcą korzystać z gRPC, ponieważ nie istnieje alternatywa dla protokołu HTTP/2. wydaje się to idealne rozwiązanie, aby poznać protokół HTTP/2 bardziej szczegółowo i zidentyfikować dodatkowe korzyści wynikające z używania gRPC.</span><span class="sxs-lookup"><span data-stu-id="39609-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="39609-107">Protokół HTTP/2 wydawany przez dział Internet Engineering Task Force w 2015 został utworzony na podstawie eksperymentalnego protokołu SPDY, który jest już używany przez firmę Google.</span><span class="sxs-lookup"><span data-stu-id="39609-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="39609-108">Został specjalnie zaprojektowany tak, aby był bardziej wydajny, szybszy i bezpieczniejszy niż protokół HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="39609-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="39609-109">Najważniejsze funkcje protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="39609-109">Key features of HTTP/2</span></span>

<span data-ttu-id="39609-110">Ta lista zawiera najważniejsze funkcje i zalety protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="39609-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="39609-111">Protokół binarny</span><span class="sxs-lookup"><span data-stu-id="39609-111">Binary protocol</span></span>

<span data-ttu-id="39609-112">Cykle żądania/odpowiedzi nie potrzebują już poleceń tekstowych.</span><span class="sxs-lookup"><span data-stu-id="39609-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="39609-113">Upraszcza to i przyspiesza implementację poleceń.</span><span class="sxs-lookup"><span data-stu-id="39609-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="39609-114">W związku z tym dane analizy są szybsze i zużywają mniej pamięci, opóźnienie sieci jest skracane z oczywistymi powiązanymi ulepszeniami w zakresie szybkości i istnieje ogólne lepsze wykorzystanie zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="39609-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="39609-115">Strumienie</span><span class="sxs-lookup"><span data-stu-id="39609-115">Streams</span></span>

<span data-ttu-id="39609-116">Strumienie umożliwiają tworzenie długotrwałych połączeń między nadawcą i odbiornikiem, przez co wiele komunikatów lub ramek można wysyłać asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="39609-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="39609-117">Wiele strumieni może działać niezależnie w ramach pojedynczego połączenia HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="39609-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="39609-118">Żądanie multipleksowania przez pojedyncze połączenie TCP</span><span class="sxs-lookup"><span data-stu-id="39609-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="39609-119">Ta funkcja jest jednym z najważniejszych innowacji protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="39609-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="39609-120">Ponieważ umożliwia wiele żądań danych, można teraz pobierać pliki internetowe jednocześnie z jednego serwera.</span><span class="sxs-lookup"><span data-stu-id="39609-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="39609-121">Szybsze ładowanie witryn sieci Web i konieczność optymalizacji jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="39609-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="39609-122">Blokowanie linii telefonicznej (HOL), w których odpowiedzi są gotowe do wysłania do momentu ukończenia wcześniejszego żądania, również zostały skorygowane (mimo że blokowanie w programie HOL nadal może wystąpić na poziomie transportu TCP).</span><span class="sxs-lookup"><span data-stu-id="39609-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="39609-123">Wydajność w sieci net. TCP, na wielu platformach</span><span class="sxs-lookup"><span data-stu-id="39609-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="39609-124">Zasadniczo, kombinacja gRPC i HTTP/2 oferuje deweloperom co najmniej równoważną szybkość i efektywność powiązań net. TCP dla programu WCF, a w niektórych przypadkach jeszcze większą szybkość i wydajność.</span><span class="sxs-lookup"><span data-stu-id="39609-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="39609-125">Jednak, w przeciwieństwie do net. TCP, gRPC za pośrednictwem protokołu HTTP/2 nie jest ograniczony do aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="39609-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="39609-126">[Poprzednie](interface-definition-language.md)
>[dalej](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="39609-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
