---
title: Komunikacja odporna
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Komunikacja odporna
ms.date: 06/30/2019
ms.openlocfilehash: 75a2ffe611ad0cf4bfa20efb49a6993bdbe6b073
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184849"
---
# <a name="resilient-communications"></a>Komunikacja odporna

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tej książce evangelized się korzyści związane z przechodzeniem poza tradycyjne, monolityczne projektowanie aplikacji i wdrażanie architektury opartej na mikrousługach, w której zestaw rozproszonych, samodzielnych usług działa niezależnie i komunikuje się z każdym inne przy użyciu standardowych protokołów komunikacyjnych, takich jak HTTP i HTTPS. Chociaż taka architektura kupuje wiele ważnych korzyści, oferuje również wiele wyzwań. Rozważmy na przykład następujące kwestie:

- *Komunikacja sieciowa poza procesem.* Każda usługa komunikuje się za pośrednictwem protokołu sieciowego, który wprowadza Przeciążenie sieci, opóźnienia i błędy przejściowe.
- *Odnajdowanie usług.* W jaki sposób usługi są wykrywane i komunikują się ze sobą za pomocą każdej usługi uruchomionej w klastrze maszyn z własnym adresem IP i portem?
- *Odporności.* Jak zarządzać awariami krótko-i zachować stabilność systemu?
- *Równoważenie obciążenia.* Jak ruch przychodzący jest dystrybuowany między wieloma wystąpieniami usługi?
- *Bezpieczeństw.* Jak są problemy z bezpieczeństwem, takie jak szyfrowanie na poziomie transportu i zarządzanie certyfikatami?
- \* Monitorowanie rozproszone. -Jak skorelować i przechwytywać możliwości śledzenia i monitorowania pojedynczego żądania w wielu usługach korzystających z usług?

Chociaż te problemy mogą być rozwiązywane z różnymi bibliotekami i strukturami, implementacja ich wewnątrz bazy kodu może być kosztowna, złożona i czasochłonna. Ponadto można dokończyć rozwiązanie, w którym zagadnienia dotyczące infrastruktury są połączone z logiką biznesową.

## <a name="service-mesh"></a>Siatka usług

Lepszym rozwiązaniem jest uwzględnienie nowej i szybko rozwijanej technologii zatytułowanej *sieci*. [Siatka usług](https://www.nginx.com/blog/what-is-a-service-mesh/) to konfigurowalna warstwa infrastruktury z wbudowanymi funkcjami do obsługi komunikacji z usługą i wielu wyzwań wymienionych powyżej. Oddziely te problemy od kodu biznesowego i przenosi je do serwera proxy usługi, którego wystąpienie towarzyszy każdej z Twoich usług. Często określany jako [wzorzec przyczepki](https://docs.microsoft.com/azure/architecture/patterns/sidecar), serwer proxy siatki usługi jest wdrażany w osobnym procesie, aby zapewnić izolację i hermetyzację z kodu biznesowego. Jednak serwer proxy jest ściśle połączony z utworzoną usługą wraz z nią i udostępnia cykl życia. Na rysunku 6-9 przedstawiono ten scenariusz.

![Siatka usług z samochodem bocznym](./media/service-mesh-with-side-car.png)

**Rysunek 6-9**. Siatka usług z samochodem bocznym

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak serwer proxy przechwytuje i zarządza komunikacją między mikrousługami i klastrem.

Siatka usługi jest logicznie dzielona na dwa różne składniki: Płaszczyzna [danych](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) i [płaszczyzna kontroli](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Na rysunku 6-10 przedstawiono te składniki i ich obowiązki.

![Sterowanie siatką usług i płaszczyzna danych](./media/istio-control-and-data-plane.png)

**Rysunek 6-10.** Sterowanie siatką usług i płaszczyzna danych

Po skonfigurowaniu usługi siatka jest wysoce funkcjonalna. Może pobrać odpowiadającą pulę wystąpień z punktu końcowego odnajdowania usług. Następnie może wysłać żądanie do określonego wystąpienia, rejestrując czas oczekiwania i typ odpowiedzi wyniku. Siatka może wybrać wystąpienie najlepiej zwracające szybką odpowiedź w oparciu o wiele czynników, w tym ich zaobserwowany czas oczekiwania na ostatnie żądania.

Jeśli wystąpienie nie odpowiada lub kończy się niepowodzeniem, Siatka może ponowić żądanie w innym wystąpieniu. Jeśli pula zwraca błędy, Siatka może wykluczyć ją z puli równoważenia obciążenia, aby ponowić próbę w późniejszym czasie po wprowadzeniu błędów. Jeśli upłynął limit czasu żądania, Siatka może zakończyć się niepowodzeniem, a następnie ponowić próbę żądania. Siatka przechwytuje zachowanie w formie metryk i rozproszonego śledzenia, które następnie można emitować do scentralizowanego systemu metryk.

## <a name="istio-and-envoy"></a>Istio i wysłannika

Mimo że niektóre opcje sieci usługi są obecnie dostępne, [Istio](https://istio.io/docs/concepts/what-is-istio/) jest najpopularniejsze w czasie tego pisania. Wspólnym przedsiębiorstwem firmy IBM, Google i LYFT jest oferta typu "open source", którą można zintegrować z nową lub istniejącą aplikacją rozproszoną. Zapewnia spójne i kompletne rozwiązanie do zabezpieczania, łączenia i monitorowania mikrousług. Dostępne są następujące funkcje:

- Zabezpieczanie komunikacji między usługami w klastrze z silnym uwierzytelnianiem i autoryzacją w oparciu o tożsamość.
- Automatyczne równoważenie obciążenia dla ruchu HTTP, [gRPC](https://grpc.io/), WEBSOCKET i TCP.
- Szczegółową kontrolę nad zachowaniem ruchu przy użyciu zaawansowanych reguł routingu, ponownych prób, przełączeń do trybu failover i iniekcji błędów.
- Podłączana warstwa zasad i interfejs API konfiguracji obsługujący kontrolę dostępu, limity szybkości i przydziały.
- Automatyczne metryki, dzienniki i ślady dla całego ruchu w klastrze, w tym dane przychodzące i wychodzące klastra.

Kluczowy składnik implementacji Istio to usługa serwera proxy uprawniona do [serwera proxy wysłannika](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Pochodzące z LYFT, a następnie do [natywnej podstawy obliczeniowej w chmurze](https://www.cncf.io/) (omówione w rozdziale 1), serwer proxy wysłannika działa obok każdej usługi i udostępnia platformę niezależny od Foundation dla następujących funkcji:

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

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-resiliency-azure.md)
>[Następny](monitoring-health.md) <!-- Next Chapter -->