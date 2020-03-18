---
title: Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676908"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kiedy wdrażać kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)

Propozycja głównej wartości wystąpień kontenera azure polega na tym, że można od razu wdrożyć kontenery i nie trzeba utrzymywać tego środowiska, nie trzeba uaktualniać/łatać podstawowego systemu operacyjnego lub maszyn wirtualnych, wszystko, co jest przezroczyste i po prostu wdrożyć kontenery w środowisku gotowy do użycia.

Przyczyny i scenariusze, gdy chcesz użyć usługi ACI są podobne do głównych scenariuszy podczas korzystania z maszyn wirtualnych platformy Azure z kontenerami, więc w zasadzie główne scenariusze korzystania z wystąpień usługi Azure Container są:

- **Scenariusze tworzenia/testowania**
- **Automatyzacja zadań**
- **Agenci CI/CD**
- **Przetwarzanie wsadowe na małą skalę**
- **Proste aplikacje internetowe**

Prosty scenariusz aplikacji sieci web jest uczciwy scenariusz dla usługi ACI, ale należy wziąć pod uwagę, że ponieważ w aci można mieć tylko jedno wystąpienie kontenera na obraz kontenera, nie będzie miał wysoką dostępność i mają tylko ograniczoną skalowalność.

Jednak nawet wtedy, gdy usługa ACI jest uważana za infrastrukturę, ponieważ zapewnia tylko pojedyncze wystąpienia kontenera, istnieje ogromna korzyść w porównaniu do zwykłych maszyn wirtualnych platformy Azure z systemem Windows Server. Dzięki aci wystarczy wdrożyć kontenery w środowisku samoobsługowym i po prostu zapłacić za te kontenery. Nie trzeba obsługiwać/aktualizować/łatamaszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których może być przy użyciu maszyn wirtualnych z kontenerami. Za pomocą ACI jest prosto do przodu, po prostu wdrożyć kontenera, nie ma potrzeby tworzenia środowiska maszyn wirtualnych po prostu wdrożyć kontenery.

Główne zalety wystąpienia kontenera platformy Azure (ACI) to:

- Uruchamianie kontenerów bez zarządzania serwerami
- Zwiększ elastyczność dzięki kontenerom na żądanie
- Wdrażaj kontenery w chmurze z niespotykaną dotąd prostotą i szybkością — za pomocą jednego polecenia.
- Bezpieczne aplikacje dzięki izolacji hiperwizorowej

Krótko mówiąc, dzięki ACI możesz szybko tworzyć aplikacje bez zarządzania maszynami wirtualnymi lub konieczności uczenia się nowych narzędzi. To tylko aplikacja, w kontenerze, uruchomiony w chmurze.

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [następny](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
