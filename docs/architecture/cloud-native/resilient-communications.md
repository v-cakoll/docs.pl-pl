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
# <a name="resilient-communications"></a>Komunikacja odporna

W tej książce zamieszczono podejście architektoniczne oparte na mikrousługach. Chociaż taka architektura zapewnia ważne korzyści, wiąże się to z wieloma wyzwaniami:

- *Komunikacja sieciowa poza procesem.* Każda mikrousługa komunikuje się za pośrednictwem protokołu sieciowego, który wprowadza Przeciążenie sieci, opóźnienia i błędy przejściowe.

- *Odnajdowanie usług.* Jak mikrousługi odnajdują i komunikują się ze sobą podczas uruchamiania w klastrze maszyn z własnymi adresami IP i portami?

- *Odporności.* Jak zarządzać awariami krótko-i zachować stabilność systemu?

- *Równoważenie obciążenia.* Jak ruch przychodzący jest dystrybuowany między wieloma wystąpieniami mikrousług?

- *Bezpieczeństw.* Jak są problemy z bezpieczeństwem, takie jak szyfrowanie na poziomie transportu i zarządzanie certyfikatami?

- *Monitorowanie rozproszone.* -Jak skorelować i przechwytywać śledzenie i monitorowanie jednego żądania w wielu zużywanych mikrousługach?

Można rozwiązać te problemy z różnymi bibliotekami i strukturami, ale implementacja może być kosztowna, złożona i czasochłonna. Istnieją również problemy z infrastrukturą połączone z logiką biznesową.

## <a name="service-mesh"></a>Siatka usług

Lepszym rozwiązaniem jest rozwój technologii uprawniony do działania *sieci*. [Siatka usług](https://www.nginx.com/blog/what-is-a-service-mesh/) to konfigurowalna warstwa infrastruktury z wbudowanymi funkcjami do obsługi komunikacji z usługą i innych wyzwań wymienionych powyżej. Oddziely te problemy, przenosząc je do serwera proxy usługi. Serwer proxy jest wdrażany w osobnym procesie (nazywanym [przyczepą](https://docs.microsoft.com/azure/architecture/patterns/sidecar)), aby zapewnić izolację z kodu biznesowego. Jednak Przyczepka jest połączona z usługą — została utworzona wraz z nią i udostępnia jej cykl życia. Na rysunku 6-7 przedstawiono ten scenariusz.

![Siatka usług z samochodem bocznym](./media/service-mesh-with-side-car.png)

**Rysunek 6-7**. Siatka usług z samochodem bocznym

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak serwer proxy przechwytuje i zarządza komunikacją między mikrousługami i klastrem.

Siatka usługi jest logicznie dzielona na dwa różne składniki: [płaszczyzna danych](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) i [płaszczyzna kontroli](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Na rysunku 6-8 przedstawiono te składniki i ich obowiązki.

![Sterowanie siatką usług i płaszczyzna danych](./media/istio-control-and-data-plane.png)

**Rysunek 6-8.** Sterowanie siatką usług i płaszczyzna danych

Po skonfigurowaniu usługi siatka jest wysoce funkcjonalna. Może pobrać odpowiadającą pulę wystąpień z punktu końcowego odnajdowania usług. Siatka może wysyłać żądanie do określonego wystąpienia, rejestrując czas oczekiwania i typ odpowiedzi wyniku. Siatka może wybrać wystąpienie najlepiej zwracające szybką odpowiedź w oparciu o wiele czynników, w tym ich zaobserwowany czas oczekiwania na ostatnie żądania.

Jeśli wystąpienie nie odpowiada lub kończy się niepowodzeniem, Siatka ponowi próbę wykonania żądania w innym wystąpieniu. Jeśli zwróci błędy, Siatka spowoduje wykluczenie wystąpienia z puli równoważenia obciążenia i przestanie go po wprowadzeniu go. Jeśli upłynął limit czasu żądania, Siatka może zakończyć się niepowodzeniem, a następnie ponowić próbę żądania. Siatka przechwytuje i emituje metryki i rozproszone śledzenie do scentralizowanego systemu metryk.

## <a name="istio-and-envoy"></a>Istio i wysłannika

Chociaż obecnie istnieje kilka opcji sieci usługi, [Istio](https://istio.io/docs/concepts/what-is-istio/) to najpopularniejsze w czasie tego pisania. Istio jest wspólnym przedsięwzięciem firmy IBM, Google i LYFT. Jest to oferta typu "open source", którą można zintegrować z nową lub istniejącą aplikacją rozproszoną. Technologia zapewnia spójne i kompletne rozwiązanie do zabezpieczania, łączenia i monitorowania mikrousług. Dostępne są następujące funkcje:

- Zabezpieczanie komunikacji między usługami w klastrze z silnym uwierzytelnianiem i autoryzacją w oparciu o tożsamość.
- Automatyczne równoważenie obciążenia dla ruchu HTTP, [gRPC](https://grpc.io/), WEBSOCKET i TCP.
- Szczegółową kontrolę nad zachowaniem ruchu przy użyciu zaawansowanych reguł routingu, ponownych prób, przełączeń do trybu failover i iniekcji błędów.
- Podłączana warstwa zasad i interfejs API konfiguracji obsługujący kontrolę dostępu, limity szybkości i przydziały.
- Automatyczne metryki, dzienniki i ślady dla całego ruchu w klastrze, w tym dane przychodzące i wychodzące klastra.

Kluczowy składnik implementacji Istio to usługa serwera proxy uprawniona do [serwera proxy wysłannika](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Jest ona uruchamiana obok każdej usługi i udostępnia platformę niezależny od Foundation dla następujących funkcji:

- Odnajdywanie usługi dynamicznej.
- Równoważenie obciążenia.
- Zakończenie protokołu TLS.
- Serwery proxy HTTP i gRPC.
- Odporność wyłącznika.
- Kontrole kondycji.
- Aktualizacje stopniowe przy użyciu wdrożeń [Kanaryjskich](https://martinfowler.com/bliki/CanaryRelease.html) .

Jak wspomniano wcześniej, wysłannika jest wdrażany jako Przyczepka dla każdej mikrousługi w klastrze.

## <a name="integration-with-azure-kubernetes-services"></a>Integracja z usługami Azure Kubernetes Services

Chmura Azure obejmuje usługę Istio i zapewnia bezpośrednią pomoc techniczną w ramach usług Azure Kubernetes Services. Następujące linki mogą pomóc Ci rozpocząć pracę:

- [Instalowanie Istio w AKS](https://docs.microsoft.com/azure/aks/istio-install)
- [Korzystanie z AKS i Istio](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a>Dokumentacja

- [Usługa Polly](http://www.thepollyproject.org/)

- [Wzorzec ponawiania](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [Wzorzec wyłącznika](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [Dokumentacja odporności na platformie Azure](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [opóźnienie sieci](https://www.techopedia.com/definition/8553/network-latency)

- [Nadmiarowość](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [replikacja geograficzna](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [Traffic Manager platformy Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [Wskazówki dotyczące skalowania automatycznego](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [Istio](https://istio.io/docs/concepts/what-is-istio/)

- [Wysłannika serwer proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-resiliency-azure.md) 
> [Dalej](monitoring-health.md)
