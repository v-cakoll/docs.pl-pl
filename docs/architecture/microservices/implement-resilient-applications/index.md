---
title: Wdrażanie odpornych aplikacji
description: Dowiedz się więcej o odporności, podstawowej koncepcji w architekturze mikrousług. Musisz wiedzieć, jak bezpiecznie obsługiwać błędy przejściowe, gdy wystąpią.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847235"
---
# <a name="implement-resilient-applications"></a>Wdrażanie odpornych aplikacji

*Mikrousługi i aplikacji opartych na chmurze musi obejmować częściowe błędy, które z pewnością wystąpi po pewnym czasie. Należy zaprojektować aplikację, aby być odporne na te częściowe błędy.*

Odporność jest możliwość odzyskania z awarii i nadal działać. Nie chodzi o unikanie awarii, ale o zaakceptowanie faktu, że awarie się pojawią i reagowanie na nie w sposób, który pozwala uniknąć przestojów lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonującego po awarii.

Jest wystarczająco trudne do projektowania i wdrażania aplikacji opartej na mikrousługach. But you also need to keep your application running in an environment where some sort of failure is certain. W związku z tym aplikacja powinna być odporna. Powinien być zaprojektowany do radzenia sobie z częściowymi awariami, takimi jak awarie sieci lub węzły lub maszyny wirtualne ulegające awarii w chmurze. Nawet mikrousługi (kontenery) przenoszone do innego węzła w klastrze może spowodować sporadyczne krótkie błędy w aplikacji.

Wiele poszczególnych składników aplikacji powinny również zawierać funkcje monitorowania kondycji. Postępując zgodnie z wytycznymi w tym rozdziale, można utworzyć aplikację, która może działać płynnie pomimo przejściowych przestojów lub normalnej czkawki, które występują w złożonych i opartych na chmurze wdrożeń.

>[!IMPORTANT]
> EShopOnContainer był przy użyciu [polly biblioteki](http://www.thepollyproject.org/) do implementowania odporności przy użyciu [klientów wpisanych](./use-httpclientfactory-to-implement-resilient-http-requests.md) aż do wydania 3.0.0.
>
> Począwszy od wersji 3.0.0, odporność wywołań HTTP jest implementowana przy użyciu [siatki Linkerd](https://linkerd.io/), która obsługuje ponownych prób w sposób przezroczysty i konfigurowalny, w klastrze Kubernetes, bez konieczności obsługi tych problemów w kodzie.
>
> Biblioteka Polly jest nadal używana do zwiększania odporności połączeń z bazami danych, szczególnie podczas uruchamiania usług.

>[!WARNING]
> Wszystkie przykłady kodu w tej sekcji były prawidłowe przed użyciem Linkerd i nie są aktualizowane w celu odzwierciedlenia bieżącego rzeczywistego kodu. Mają więc sens w kontekście tej sekcji.

>[!div class="step-by-step"]
>[Poprzedni](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[następny](handle-partial-failure.md)
