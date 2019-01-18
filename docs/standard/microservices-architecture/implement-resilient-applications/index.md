---
title: Implementowanie aplikacji odpornych na błędy
description: Więcej informacji na temat odporności, ideą w architekturze mikrousług. Należy znać sposób poprawnego działania obsługi błędów przejściowych, ponieważ będą one występować.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362746"
---
# <a name="implement-resilient-applications"></a>Implementowanie aplikacji odpornych na błędy

*Na mikrousługach i aplikacji działających w chmurze musi obejmować częściowe błędy, które na pewno zostanie przeprowadzona po pewnym czasie. Należy zaprojektować aplikację, aby była odporna na awarie, którym te częściowe.*

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Nie o unikanie błędów, ale przyjmuje fakt, że będą zdarzać się błędy i reagowanie na ich w taki sposób, aby uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu pełnej funkcjonalności po wystąpieniu awarii.

Jest trudne do projektowania i wdrażania aplikacji opartych na mikrousługach. Jednak trzeba będzie również nadal uruchomiony w środowisku jakieś awarii w przypadku niektórych aplikacji. W związku z tym aplikacja powinna być odporne na błędy. Powinny zostać tak zaprojektowane do radzenia sobie z błędami częściowych, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych. Nawet mikrousługi (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótki w ramach aplikacji.

Wielu pojedynczych składników aplikacji powinien również zawierać funkcje monitorowania kondycji. Postępując zgodnie z wytycznymi podanymi w tym rozdziale, można utworzyć aplikację, która można sprawnie współpracować z autora przejściowy przestój lub skalujący normalne, które występują we wdrożeniach złożone i oparte na chmurze.

>[!div class="step-by-step"]
>[Poprzednie](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[dalej](handle-partial-failure.md)