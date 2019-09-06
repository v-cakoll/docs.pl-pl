---
title: Implementowanie aplikacji odpornych na błędy
description: Dowiedz się więcej o odporności, podstawowej koncepcji w architekturze mikrousług. Musisz wiedzieć, jak bezpiecznie obsługiwać błędy przejściowe, ponieważ wystąpią.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296061"
---
# <a name="implement-resilient-applications"></a>Implementuj aplikacje odporne

*Aplikacje mikrousługowe i oparte na chmurze muszą obejmować częściowe awarie, które wystąpiły w przyszłości. Musisz zaprojektować aplikację, aby była odporna na błędy częściowe.*

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Nie ma ona wpływu na błędy, ale akceptuje fakt, że awarie i odpowiadanie na nie są w taki sposób, aby uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu w pełni funkcjonalnym po awarii.

Jest to trudne do zaprojektowania i wdrożenia aplikacji opartej na mikrousługach. Jednak należy również zachować swoją aplikację w środowisku, w którym niektóre różne błędy są pewne. W związku z tym aplikacja powinna być odporna na błędy. Powinna być zaprojektowana tak, aby sprostać częściowym błędom, takim jak awaria sieci lub węzły lub maszyny wirtualne, które uległy awarii w chmurze. Nawet mikrousługi (kontenery) przenoszone do innego węzła w klastrze mogą spowodować sporadyczne krótkie błędy w aplikacji.

Wiele pojedynczych składników aplikacji powinna również zawierać funkcje monitorowania kondycji. Postępując zgodnie z wytycznymi w tym rozdziale, można utworzyć aplikację, która może działać bezproblemowo pomimo przejściowego przestoju lub normalnego hiccupsu w przypadku wdrożeń złożonych i opartych na chmurze.

>[!div class="step-by-step"]
>[Poprzedni](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)Następny
>[](handle-partial-failure.md)
