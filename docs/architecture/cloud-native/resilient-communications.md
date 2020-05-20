---
title: Komunikacja odporna
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Komunikacja odporna
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613749"
---
# <a name="resilient-communications"></a><span data-ttu-id="88f81-103">Komunikacja odporna</span><span class="sxs-lookup"><span data-stu-id="88f81-103">Resilient communications</span></span>

<span data-ttu-id="88f81-104">W tej książce zamieszczono podejście architektoniczne oparte na mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="88f81-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="88f81-105">Chociaż taka architektura zapewnia ważne korzyści, wiąże się to z wieloma wyzwaniami:</span><span class="sxs-lookup"><span data-stu-id="88f81-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="88f81-106">*Komunikacja sieciowa poza procesem.*</span><span class="sxs-lookup"><span data-stu-id="88f81-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="88f81-107">Każda mikrousługa komunikuje się za pośrednictwem protokołu sieciowego, który wprowadza Przeciążenie sieci, opóźnienia i błędy przejściowe.</span><span class="sxs-lookup"><span data-stu-id="88f81-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="88f81-108">*Odnajdowanie usług.*</span><span class="sxs-lookup"><span data-stu-id="88f81-108">*Service discovery.*</span></span> <span data-ttu-id="88f81-109">Jak mikrousługi odnajdują i komunikują się ze sobą podczas uruchamiania w klastrze maszyn z własnymi adresami IP i portami?</span><span class="sxs-lookup"><span data-stu-id="88f81-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="88f81-110">*Odporności.*</span><span class="sxs-lookup"><span data-stu-id="88f81-110">*Resiliency.*</span></span> <span data-ttu-id="88f81-111">Jak zarządzać awariami krótko-i zachować stabilność systemu?</span><span class="sxs-lookup"><span data-stu-id="88f81-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="88f81-112">*Równoważenie obciążenia.*</span><span class="sxs-lookup"><span data-stu-id="88f81-112">*Load balancing.*</span></span> <span data-ttu-id="88f81-113">Jak ruch przychodzący jest dystrybuowany między wieloma wystąpieniami mikrousług?</span><span class="sxs-lookup"><span data-stu-id="88f81-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="88f81-114">*Bezpieczeństw.*</span><span class="sxs-lookup"><span data-stu-id="88f81-114">*Security.*</span></span> <span data-ttu-id="88f81-115">Jak są problemy z bezpieczeństwem, takie jak szyfrowanie na poziomie transportu i zarządzanie certyfikatami?</span><span class="sxs-lookup"><span data-stu-id="88f81-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="88f81-116">*Monitorowanie rozproszone.*</span><span class="sxs-lookup"><span data-stu-id="88f81-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="88f81-117">-Jak skorelować i przechwytywać śledzenie i monitorowanie jednego żądania w wielu zużywanych mikrousługach?</span><span class="sxs-lookup"><span data-stu-id="88f81-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="88f81-118">Można rozwiązać te problemy z różnymi bibliotekami i strukturami, ale implementacja może być kosztowna, złożona i czasochłonna.</span><span class="sxs-lookup"><span data-stu-id="88f81-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="88f81-119">Istnieją również problemy z infrastrukturą połączone z logiką biznesową.</span><span class="sxs-lookup"><span data-stu-id="88f81-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="88f81-120">Siatka usług</span><span class="sxs-lookup"><span data-stu-id="88f81-120">Service mesh</span></span>

<span data-ttu-id="88f81-121">Lepszym rozwiązaniem jest rozwój technologii uprawniony do działania *sieci*.</span><span class="sxs-lookup"><span data-stu-id="88f81-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="88f81-122">[Siatka usług](https://www.nginx.com/blog/what-is-a-service-mesh/) to konfigurowalna warstwa infrastruktury z wbudowanymi funkcjami do obsługi komunikacji z usługą i innych wyzwań wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="88f81-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="88f81-123">Oddziely te problemy, przenosząc je do serwera proxy usługi.</span><span class="sxs-lookup"><span data-stu-id="88f81-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="88f81-124">Serwer proxy jest wdrażany w osobnym procesie (nazywanym [przyczepą](https://docs.microsoft.com/azure/architecture/patterns/sidecar)), aby zapewnić izolację z kodu biznesowego.</span><span class="sxs-lookup"><span data-stu-id="88f81-124">The proxy is deployed into a separate process (called a [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="88f81-125">Jednak Przyczepka jest połączona z usługą — została utworzona wraz z nią i udostępnia jej cykl życia.</span><span class="sxs-lookup"><span data-stu-id="88f81-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="88f81-126">Na rysunku 6-7 przedstawiono ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="88f81-126">Figure 6-7 shows this scenario.</span></span>

![Siatka usług z samochodem bocznym](./media/service-mesh-with-side-car.png)

<span data-ttu-id="88f81-128">**Rysunek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="88f81-128">**Figure 6-7**.</span></span> <span data-ttu-id="88f81-129">Siatka usług z samochodem bocznym</span><span class="sxs-lookup"><span data-stu-id="88f81-129">Service mesh with a side car</span></span>

<span data-ttu-id="88f81-130">Na poprzedniej ilustracji należy zwrócić uwagę na to, jak serwer proxy przechwytuje i zarządza komunikacją między mikrousługami i klastrem.</span><span class="sxs-lookup"><span data-stu-id="88f81-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="88f81-131">Siatka usługi jest logicznie dzielona na dwa różne składniki: [płaszczyzna danych](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) i [płaszczyzna kontroli](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span><span class="sxs-lookup"><span data-stu-id="88f81-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="88f81-132">Na rysunku 6-8 przedstawiono te składniki i ich obowiązki.</span><span class="sxs-lookup"><span data-stu-id="88f81-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![Sterowanie siatką usług i płaszczyzna danych](./media/istio-control-and-data-plane.png)

<span data-ttu-id="88f81-134">**Rysunek 6-8.**</span><span class="sxs-lookup"><span data-stu-id="88f81-134">**Figure 6-8.**</span></span> <span data-ttu-id="88f81-135">Sterowanie siatką usług i płaszczyzna danych</span><span class="sxs-lookup"><span data-stu-id="88f81-135">Service mesh control and data plane</span></span>

<span data-ttu-id="88f81-136">Po skonfigurowaniu usługi siatka jest wysoce funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="88f81-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="88f81-137">Może pobrać odpowiadającą pulę wystąpień z punktu końcowego odnajdowania usług.</span><span class="sxs-lookup"><span data-stu-id="88f81-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="88f81-138">Siatka może wysyłać żądanie do określonego wystąpienia, rejestrując czas oczekiwania i typ odpowiedzi wyniku.</span><span class="sxs-lookup"><span data-stu-id="88f81-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="88f81-139">Siatka może wybrać wystąpienie najlepiej zwracające szybką odpowiedź w oparciu o wiele czynników, w tym ich zaobserwowany czas oczekiwania na ostatnie żądania.</span><span class="sxs-lookup"><span data-stu-id="88f81-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="88f81-140">Jeśli wystąpienie nie odpowiada lub kończy się niepowodzeniem, Siatka ponowi próbę wykonania żądania w innym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="88f81-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="88f81-141">Jeśli zwróci błędy, Siatka spowoduje wykluczenie wystąpienia z puli równoważenia obciążenia i przestanie go po wprowadzeniu go.</span><span class="sxs-lookup"><span data-stu-id="88f81-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="88f81-142">Jeśli upłynął limit czasu żądania, Siatka może zakończyć się niepowodzeniem, a następnie ponowić próbę żądania.</span><span class="sxs-lookup"><span data-stu-id="88f81-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="88f81-143">Siatka przechwytuje i emituje metryki i rozproszone śledzenie do scentralizowanego systemu metryk.</span><span class="sxs-lookup"><span data-stu-id="88f81-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="88f81-144">Istio i wysłannika</span><span class="sxs-lookup"><span data-stu-id="88f81-144">Istio and Envoy</span></span>

<span data-ttu-id="88f81-145">Chociaż obecnie istnieje kilka opcji sieci usługi, [Istio](https://istio.io/docs/concepts/what-is-istio/) to najpopularniejsze w czasie tego pisania.</span><span class="sxs-lookup"><span data-stu-id="88f81-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="88f81-146">Istio jest wspólnym przedsięwzięciem firmy IBM, Google i LYFT.</span><span class="sxs-lookup"><span data-stu-id="88f81-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="88f81-147">Jest to oferta typu "open source", którą można zintegrować z nową lub istniejącą aplikacją rozproszoną.</span><span class="sxs-lookup"><span data-stu-id="88f81-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="88f81-148">Technologia zapewnia spójne i kompletne rozwiązanie do zabezpieczania, łączenia i monitorowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="88f81-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="88f81-149">Dostępne są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="88f81-149">Its features include:</span></span>

- <span data-ttu-id="88f81-150">Zabezpieczanie komunikacji między usługami w klastrze z silnym uwierzytelnianiem i autoryzacją w oparciu o tożsamość.</span><span class="sxs-lookup"><span data-stu-id="88f81-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="88f81-151">Automatyczne równoważenie obciążenia dla ruchu HTTP, [gRPC](https://grpc.io/), WEBSOCKET i TCP.</span><span class="sxs-lookup"><span data-stu-id="88f81-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="88f81-152">Szczegółową kontrolę nad zachowaniem ruchu przy użyciu zaawansowanych reguł routingu, ponownych prób, przełączeń do trybu failover i iniekcji błędów.</span><span class="sxs-lookup"><span data-stu-id="88f81-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="88f81-153">Podłączana warstwa zasad i interfejs API konfiguracji obsługujący kontrolę dostępu, limity szybkości i przydziały.</span><span class="sxs-lookup"><span data-stu-id="88f81-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="88f81-154">Automatyczne metryki, dzienniki i ślady dla całego ruchu w klastrze, w tym dane przychodzące i wychodzące klastra.</span><span class="sxs-lookup"><span data-stu-id="88f81-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="88f81-155">Kluczowy składnik implementacji Istio to usługa serwera proxy uprawniona do [serwera proxy wysłannika](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span><span class="sxs-lookup"><span data-stu-id="88f81-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="88f81-156">Jest ona uruchamiana obok każdej usługi i udostępnia platformę niezależny od Foundation dla następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="88f81-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="88f81-157">Odnajdywanie usługi dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="88f81-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="88f81-158">Równoważenie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="88f81-158">Load balancing.</span></span>
- <span data-ttu-id="88f81-159">Zakończenie protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="88f81-159">TLS termination.</span></span>
- <span data-ttu-id="88f81-160">Serwery proxy HTTP i gRPC.</span><span class="sxs-lookup"><span data-stu-id="88f81-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="88f81-161">Odporność wyłącznika.</span><span class="sxs-lookup"><span data-stu-id="88f81-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="88f81-162">Kontrole kondycji.</span><span class="sxs-lookup"><span data-stu-id="88f81-162">Health checks.</span></span>
- <span data-ttu-id="88f81-163">Aktualizacje stopniowe przy użyciu wdrożeń [Kanaryjskich](https://martinfowler.com/bliki/CanaryRelease.html) .</span><span class="sxs-lookup"><span data-stu-id="88f81-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="88f81-164">Jak wspomniano wcześniej, wysłannika jest wdrażany jako Przyczepka dla każdej mikrousługi w klastrze.</span><span class="sxs-lookup"><span data-stu-id="88f81-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="88f81-165">Integracja z usługami Azure Kubernetes Services</span><span class="sxs-lookup"><span data-stu-id="88f81-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="88f81-166">Chmura Azure obejmuje usługę Istio i zapewnia bezpośrednią pomoc techniczną w ramach usług Azure Kubernetes Services.</span><span class="sxs-lookup"><span data-stu-id="88f81-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="88f81-167">Następujące linki mogą pomóc Ci rozpocząć pracę:</span><span class="sxs-lookup"><span data-stu-id="88f81-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="88f81-168">Instalowanie Istio w AKS</span><span class="sxs-lookup"><span data-stu-id="88f81-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="88f81-169">Korzystanie z AKS i Istio</span><span class="sxs-lookup"><span data-stu-id="88f81-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="88f81-170">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="88f81-170">References</span></span>

- [<span data-ttu-id="88f81-171">Usługa Polly</span><span class="sxs-lookup"><span data-stu-id="88f81-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="88f81-172">Wzorzec ponawiania</span><span class="sxs-lookup"><span data-stu-id="88f81-172">Retry pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [<span data-ttu-id="88f81-173">Wzorzec wyłącznika</span><span class="sxs-lookup"><span data-stu-id="88f81-173">Circuit Breaker pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="88f81-174">Dokumentacja odporności na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="88f81-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="88f81-175">opóźnienie sieci</span><span class="sxs-lookup"><span data-stu-id="88f81-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="88f81-176">Nadmiarowość</span><span class="sxs-lookup"><span data-stu-id="88f81-176">Redundancy</span></span>](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="88f81-177">replikacja geograficzna</span><span class="sxs-lookup"><span data-stu-id="88f81-177">geo-replication</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="88f81-178">Traffic Manager platformy Azure</span><span class="sxs-lookup"><span data-stu-id="88f81-178">Azure Traffic Manager</span></span>](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="88f81-179">Wskazówki dotyczące skalowania automatycznego</span><span class="sxs-lookup"><span data-stu-id="88f81-179">Autoscaling guidance</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="88f81-180">Istio</span><span class="sxs-lookup"><span data-stu-id="88f81-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="88f81-181">Wysłannika serwer proxy</span><span class="sxs-lookup"><span data-stu-id="88f81-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="88f81-182">[Poprzedni](infrastructure-resiliency-azure.md) 
> [Dalej](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="88f81-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
