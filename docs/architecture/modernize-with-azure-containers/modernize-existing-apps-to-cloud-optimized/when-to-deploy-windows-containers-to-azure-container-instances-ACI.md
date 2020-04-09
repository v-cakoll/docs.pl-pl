---
title: Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989158"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kiedy wdrożyć kontenery systemu Windows w wystąpieniach kontenerów platformy Azure (ACI)

Głównym propozycja wartości wystąpienia kontenerów platformy Azure jest, że można od razu wdrożyć kontenery do niego i nie trzeba utrzymywać tego środowiska, nie trzeba uaktualnić/załatać podstawowy system operacyjny lub maszyn wirtualnych, wszystko, co jest przezroczyste i po prostu wdrożyć kontenery w środowisku gotowym do użycia.

Przyczyny i scenariusze, gdy chcesz użyć usługi ACI są podobne do głównych scenariuszy podczas korzystania z maszyn wirtualnych platformy Azure z kontenerami, więc zasadniczo główne scenariusze dotyczące korzystania z wystąpień kontenera platformy Azure są:

- **Scenariusze deweloperów/testów**
- **Automatyzacja zadań**
- **Agenci ciągłej integracji/ciągłego wdrażania**
- **Przetwarzanie wsadowe na małą skalę**
- **Proste aplikacje internetowe**

Scenariusz prostych aplikacji sieci web jest sprawiedliwy scenariusz dla ACI, ale wziąć pod uwagę, że ponieważ w ACI można mieć tylko jedno wystąpienie kontenera na obraz kontenera, nie będzie mieć wysoką dostępność i tylko ograniczoną skalowalność.

Jednak nawet wtedy, gdy usługa ACI jest uważana za infrastrukturę, ponieważ udostępnia tylko wystąpienia pojedynczego kontenera, istnieje ogromna korzyść w porównaniu do zwykłych maszyn wirtualnych platformy Azure z systemem Windows Server. Z ACI, po prostu wdrożyć kontenery w środowisku samodzielnej konserwacji i po prostu zapłacić za te kontenery. Nie trzeba obsługiwać/update/patch maszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których może być przy użyciu maszyn wirtualnych z kontenerami. Za pomocą usługi ACI jest prosta, wystarczy wdrożyć kontener, nie ma potrzeby tworzenia środowiska maszyny Wirtualnej, które po prostu wdrożyć kontenery.

Główne zalety wystąpień kontenerów platformy Azure (ACI) to:

- Uruchamianie kontenerów bez zarządzania serwerami
- Zwiększ elastyczność dzięki kontenerom na żądanie
- Wdrażaj kontenery w chmurze z niespotykaną dotąd prostotą i szybkością — za pomocą jednego polecenia.
- Zabezpieczanie aplikacji z izolacją hipernadzorcy

Krótko mówiąc, dzięki ACI możesz szybko tworzyć aplikacje bez zarządzania maszynami wirtualnymi lub konieczności uczenia się nowych narzędzi. To tylko aplikacja w kontenerze, działająca w chmurze.

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [następny](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
