---
title: Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958225"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Podczas wdrażania systemu Windows kontenerów do wystąpień kontenera platformy Azure (ACI)

Azure wystąpień kontenera głównego wartości oferty jest od razu wdrożeniem kontenerów do niego, a nie trzeba Obsługa tego środowiska, nie ma potrzeby uaktualniania/poprawka systemu operacyjnego underlaying lub maszyn wirtualnych, jest niewidoczny i wdrażać tylko kontenery w środowisku gotowe do użycia.

Przyczyny i scenariusze, w których chcesz użyć ACI są podobne do głównych scenariuszy, korzystając z maszyn wirtualnych platformy Azure z kontenerami, więc zasadniczo, są główne scenariusze za pomocą wystąpień kontenera platformy Azure:

-   **Scenariusze tworzenia/testowania**
-   **Automatyzacja zadań**
-   **Agenci CI/CD**
-   **Przetwarzanie wsadowe małych/skali**
-   **Aplikacje sieci web proste**

Prostego scenariusza aplikacji jest to odpowiedni scenariusz dla ACI, ale wziąć pod uwagę, że od czasu w ACI może zawierać tylko wystąpienia jeden kontener na obraz kontenera, nie będziesz mieć wysokiej dostępności i mają ograniczoną skalowalności.

Jednak nawet wtedy, gdy ACI jest uważany za infrastruktury, ponieważ zapewnia tylko jeden kontener wystąpień, brak ogromne korzyści w porównaniu do regularnych maszynach wirtualnych platformy Azure z systemem Windows Server. ACI po prostu wdrażanie kontenerów do zapewnienia własnym środowiska i płacisz tylko dla tych kontenerach. Obsługa/aktualizacji/poprawki maszyn wirtualnych, nie trzeba więc jest znacznie lepszą platformę dla większości scenariuszy, w których możesz używać maszyn wirtualnych z kontenerami. Używanie ACI jest wprost do przodu, po prostu wdrożenia kontenera, nie istnieje potrzeba aby utworzyć środowisko maszyny Wirtualnej, po prostu wdrażanie kontenerów.

Główne zalety z wystąpień kontenera platformy Azure (ACI) to:

-   Uruchom kontenery bez zarządzanie serwerami
-   Zwiększyć elastyczność z kontenerami na żądanie
-   Wdrażanie kontenerów do chmury przy Niespotykana prostoty i szybkość — za pomocą jednego polecenia. 
-   Zabezpieczenia aplikacji przy użyciu funkcji hypervisor izolacji

Krótko mówiąc z ACI można programować aplikacje fast bez zarządzania maszynami wirtualnymi lub do nowego narzędzia. Jest po prostu aplikacji, w kontenerze działającą w chmurze.

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[dalej](when-to-deploy-windows-containers-to-service-fabric.md)
