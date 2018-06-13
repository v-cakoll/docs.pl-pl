---
title: Implementowanie odporność aplikacji
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odporność aplikacji
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 211814eff0f2aaf0cf71a19cfcaaeb44924fb6f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573747"
---
# <a name="implementing-resilient-applications"></a>Implementowanie odporność aplikacji

*Twoje mikrousługi i w chmurze aplikacji musi obejmować częściowe błędów, które na pewno nastąpi po pewnym czasie. Należy więc był odporny na błędy te częściowe, Utwórz projekt swojej aplikacji.*

Odporność jest możliwość skutków błędów i kontynuować działanie. Nie jest o unikanie błędów, ale akceptuje fakt, że nastąpi błędów i odpowiada na je w taki sposób, który pozwala uniknąć przestoju lub utraty danych. Celem odporności jest do zwrócenia aplikacji w pełni funkcjonalnej stan po awarii.

Jest trudne do projektowania i wdrażania aplikacji na podstawie mikrousług. Jednak należy zachować uruchomiony w środowisku jakiegoś awarii w przypadku niektórych aplikacji. W związku z tym należy odporność aplikacji. Powinny być zaprojektowane do radzenia sobie z częściowa błędami, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych. Nawet mikrousług (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótkich w aplikacji.

Wiele pojedynczych składników aplikacji powinien uwzględniać kondycji funkcji monitorowania. Wykonując wskazówki zawarte w tym rozdziale można utworzyć aplikacji działającej sprawnie mimo przejściowego przestój lub hiccups normalne, które występują w przypadku wdrożeń złożona i w chmurze.


>[!div class="step-by-step"]
[Poprzednie] (.. / microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [dalej] (dojście partial-failure.md)
