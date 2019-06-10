---
title: Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758596"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kiedy należy wdrażać kontenery Windows do usługi Azure Container Instances (ACI)

Usługa Azure Container Instances, jest główne korzyści, że można następnie od razu wdrażać kontenery do niego, i nie trzeba utrzymywać w tym środowisku, nie trzeba uaktualnianie/poprawianie w systemie operacyjnym lub maszyn wirtualnych, wszystkie, które jest przejrzysta i po prostu wdrażasz kontenery w środowisku z gotowych do użycia.

Przyczyny i scenariusze, jeśli chcesz użyć usługi ACI są podobne do główne scenariusze, w przypadku użycia maszyn wirtualnych platformy Azure z kontenerów, więc po prostu, główne scenariusze dotyczące korzystania z usługi Azure Container Instances są:

- **Scenariusze tworzenia i testowania**
- **Automatyzacja zadań**
- **Ciągła Integracja/ciągłe wdrażanie agentów**
- **Przetwarzanie wsadowe małych/skalowanie**
- **Prostych aplikacji sieci web**

Scenariusz aplikacji prostą jest uczciwe scenariusz dotyczący usługi ACI, ale weź pod uwagę, że od czasu w usłudze ACI może mieć tylko wystąpienie jednego kontenera dla obrazu kontenera, nie będziesz mieć wysokiej dostępności i ma ograniczoną skalowalność.

Jednak nawet wtedy, gdy ACI zostanie uznany za infrastrukturę, ponieważ zawiera ono tylko jeden kontener wystąpień, ma ogromne korzyści w porównaniu do regularnego maszyn wirtualnych platformy Azure z systemem Windows Server. Za pomocą usługi ACI po prostu wdrażanie kontenerów w środowisku z własnym utrzymywane w dobrym stanie, i płacisz tylko za tych kontenerów. Nie trzeba utrzymywać/aktualizacji/poprawek maszyn wirtualnych, więc jest znacznie lepszą platformę dla większości scenariuszy, w którym może być używany maszyn wirtualnych za pomocą kontenerów. Za pomocą usługi ACI jest bardzo proste, po prostu wdrażanie kontenera, trzeba utworzyć środowisko maszyny Wirtualnej, po prostu wdrażanie kontenerów.

Dostępne są następujące główne korzyści z usługi Azure Container Instances (ACI):

- Uruchamiaj kontenery bez potrzeby zarządzania serwerami
- Zwiększ elastyczność dzięki użyciu kontenerów na żądanie
- Wdrażanie kontenerów do chmury dzięki niezrównaną prostotą i szybkością — za pomocą jednego polecenia.
- Zabezpieczaj aplikacje za pomocą izolacji funkcji hypervisor

Krótko mówiąc za pomocą usługi ACI możesz opracowywać aplikacje szybko bez zarządzania maszynami wirtualnymi oraz konieczności korzystania z nowych narzędzi. To właśnie aplikacja w kontenerze uruchomiona w chmurze.

> [!div class="step-by-step"]
> [Poprzednie](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [dalej](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
