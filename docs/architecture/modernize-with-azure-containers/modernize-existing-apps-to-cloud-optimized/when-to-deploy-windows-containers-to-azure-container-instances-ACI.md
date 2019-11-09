---
title: Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676908"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kiedy należy wdrażać kontenery systemu Windows do Azure Container Instances (ACI)

Azure Container Instances propozycja wartości głównej polega na tym, że możesz od razu wdrożyć kontenery i nie musisz obsługiwać tego środowiska, nie musisz uaktualniać ani poprawiać bazowego systemu operacyjnego lub maszyn wirtualnych, a wszystko to jest widoczne, a dopiero po prostu wdrażasz kontenery w gotowym do użycia środowisku.

Przyczyny i scenariusze, które należy stosować ACI, są podobne do głównych scenariuszy w przypadku używania maszyn wirtualnych platformy Azure z kontenerami, dlatego główne scenariusze używania Azure Container Instances są następujące:

- **Scenariusze tworzenia i testowania**
- **Automatyzacja zadań**
- **Agenci CI/CD**
- **Małe/skalowane przetwarzanie wsadowe**
- **Proste aplikacje sieci Web**

Scenariusz prostego programu Web Apps jest uczciwym scenariuszem dla ACI, ale należy wziąć pod uwagę, że ponieważ w ACI może istnieć tylko jedno wystąpienie kontenera dla każdego obrazu kontenera, nie ma wysokiej dostępności i ma ograniczoną skalowalność.

Jednak nawet jeśli ACI jest uznawany za infrastrukturę, ponieważ tylko zawiera ona pojedyncze wystąpienia kontenera, w porównaniu z regularnymi maszynami wirtualnymi platformy Azure w systemie Windows Server istnieje ogromna korzyść. Dzięki usłudze ACI możesz wdrażać kontenery w środowisku z własnym obsługą i płacisz tylko za te kontenery. Nie musisz obsługiwać ani aktualizować/poprawiać maszyn wirtualnych, więc jest to znacznie lepsza platforma dla większości scenariuszy, w których można używać maszyn wirtualnych z kontenerami. Korzystanie z usługi ACI jest proste — wystarczy wdrożyć kontener, ale nie ma potrzeby tworzenia środowiska maszyny wirtualnej, które wdrażają kontenery.

Główne zalety Azure Container Instances (ACI) to:

- Uruchamianie kontenerów bez zarządzania serwerami
- Zwiększ elastyczność dzięki kontenerom na żądanie
- Wdrażaj kontenery w chmurze z niepoprzednią prostotą i szybkością — za pomocą jednego polecenia.
- Zabezpieczanie aplikacji z izolacją funkcji hypervisor

Krótko mówiąc, dzięki funkcji ACI można szybko opracowywać aplikacje bez konieczności zarządzania maszynami wirtualnymi ani uczenia się nowych narzędzi. Jest to tylko Twoja aplikacja w kontenerze działającym w chmurze.

> [!div class="step-by-step"]
> [Poprzedni](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [dalej](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
