---
title: Implementowanie aplikacji odpornych na błędy
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie aplikacji odpornych na błędy
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: dc0db8f0cdfa77bcca467c3c632b3d93de8851d8
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875127"
---
# <a name="implementing-resilient-applications"></a>Implementowanie aplikacji odpornych na błędy

*Na mikrousługach i aplikacji działających w chmurze musi obejmować częściowe błędy, które na pewno zostanie przeprowadzona po pewnym czasie. Należy tak zaprojektować aplikację, więc będą odporne na awarie, którym te częściowe.*

Odporność to zdolność do odzyskiwania po awarii i kontynuowania działania. Nie jest o unikanie błędów, ale przyjmuje fakt, że będą zdarzać się błędy i reagowanie na ich w taki sposób, aby uniknąć przestoju lub utraty danych. Celem odporności jest przywrócenie aplikacji do stanu pełnej funkcjonalności po wystąpieniu awarii.

Jest trudne do projektowania i wdrażania aplikacji opartych na mikrousługach. Jednak trzeba będzie również nadal uruchomiony w środowisku jakieś awarii w przypadku niektórych aplikacji. W związku z tym aplikacja powinna być odporne na błędy. Powinny zostać tak zaprojektowane do radzenia sobie z błędami częściowych, takich jak awarii sieci lub węzłów lub awarii w chmurze maszyn wirtualnych. Nawet mikrousługi (kontenery) jest przenoszony do innego węzła w klastrze może powodować sporadyczne błędy krótki w ramach aplikacji.

Wielu pojedynczych składników aplikacji powinien również zawierać funkcje monitorowania kondycji. Postępując zgodnie z wytycznymi podanymi w tym rozdziale, można utworzyć aplikację, która można sprawnie współpracować z autora przejściowy przestój lub skalujący normalne, które występują we wdrożeniach złożone i oparte na chmurze.


>[!div class="step-by-step"]
[Poprzednie](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[dalej](handle-partial-failure.md)
