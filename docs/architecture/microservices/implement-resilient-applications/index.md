---
title: Implementuj aplikacje odporne
description: Dowiedz się więcej o odporności, podstawowej koncepcji w architekturze mikrousług. Należy wiedzieć, jak bezpiecznie obsługiwać błędy przejściowe.
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502656"
---
# <a name="implement-resilient-applications"></a>Implementuj aplikacje odporne

*Aplikacje mikrousługowe i oparte na chmurze muszą obejmować częściowe awarie, które wystąpiły w przyszłości. Musisz zaprojektować aplikację, aby była odporna na błędy częściowe.*

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Nie ma ona wpływu na błędy, ale akceptuje fakt, że awarie i odpowiadanie na nie są w taki sposób, aby uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.

Jest to trudne do zaprojektowania i wdrożenia aplikacji opartej na mikrousługach. Jednak należy również zachować swoją aplikację w środowisku, w którym niektóre różne błędy są pewne. W związku z tym aplikacja powinna być odporna na błędy. Powinna być zaprojektowana tak, aby sprostać częściowym błędom, takim jak awaria sieci lub węzły lub maszyny wirtualne, które uległy awarii w chmurze. Nawet mikrousługi (kontenery) przenoszone do innego węzła w klastrze mogą spowodować sporadyczne krótkie błędy w aplikacji.

Wiele pojedynczych składników aplikacji powinna również zawierać funkcje monitorowania kondycji. Postępując zgodnie z wytycznymi w tym rozdziale, można utworzyć aplikację, która może działać bezproblemowo pomimo przejściowego przestoju lub normalnego hiccupsu w przypadku wdrożeń złożonych i opartych na chmurze.

>[!IMPORTANT]
> eShopOnContainer użyto [biblioteki Polly](http://www.thepollyproject.org/) w celu zaimplementowania odporności przy użyciu [wpisanych klientów](./use-httpclientfactory-to-implement-resilient-http-requests.md) do momentu wydania 3.0.0.
>
> Począwszy od wersji 3.0.0, odporność wywołań HTTP jest implementowana za pomocą [konsolidatora siatki](https://linkerd.io/), która obsługuje ponowne próby w sposób przezroczysty i konfigurowalny w klastrze Kubernetes, bez konieczności obsługi tych problemów w kodzie.
>
> Biblioteka Polly jest nadal używana do dodawania odporności do połączeń z bazą danych, szczególnie podczas uruchamiania usług.

>[!WARNING]
> Wszystkie przykłady kodu w tej sekcji były prawidłowe przed użyciem konsolidatora i nie są aktualizowane w celu odzwierciedlenia bieżącego rzeczywistego kodu. Dlatego mają sens w kontekście tej sekcji.

>[!div class="step-by-step"]
>[Poprzednie](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[dalej](handle-partial-failure.md)
