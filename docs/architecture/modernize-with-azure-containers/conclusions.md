---
title: Wnioski
description: Modernizacja istniejących aplikacji .NET za pomocą usługi Azure Cloud i kontenerów systemu Windows | Wnioski
ms.date: 10/26/2017
ms.openlocfilehash: c7c4042b224577238ae74bd786d4803e487998e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68677106"
---
# <a name="conclusions"></a>Wnioski

- Rozwiązania oparte na kontenerach zapewniają ostatecznie korzyści z oszczędności kosztów. Kontenery są rozwiązaniem problemów z wdrażaniem, ponieważ usuwają tarcie spowodowane brakiem zależności w środowiskach produkcyjnych. Usuwając te problemy, znacznie poprawia deweloperów/testów, devops i operacji produkcyjnych.

- Kontener platformy Docker staje się standardową jednostką wdrożenia dla dowolnej aplikacji lub usługi opartej na serwerze.

- W środowiskach produkcyjnych należy użyć koordynatora (jak Kubernetes) do hosta skalowalnych aplikacji opartych na kontenerach.

- Maszyny wirtualne platformy Azure hostujących kontenery to szybki i prosty sposób tworzenia małych środowisk deweloperskich/testowych w chmurze.

- Wystąpienie zarządzane bazy danych SQL platformy Azure jest domyślnie zalecane podczas migracji relacyjnych baz danych z istniejących aplikacji na platformę Azure.

- Visual Studio 2017 i Image2Docker to podstawowe narzędzia umożliwiające rozpoczęcie modernizacji istniejących aplikacji .NET za pomocą kontenerów systemu Windows, przyspieszając wprowadzenie krzywej uczenia się.

- Podczas umieszczania aplikacji konteneryzowanych w środowisku produkcyjnym zawsze należy utworzyć lub przyjąć devops kultury i devops narzędzi dla potoków ciągłej integracji/ciągłego dysku CD, takich jak usługi Azure DevOps Services lub Jenkins.

- Platforma Microsoft Azure zapewnia najbardziej kompleksowe i kompletne środowisko do modernizacji istniejących aplikacji .NET Framework za pomocą kontenerów systemu Windows, infrastruktury chmury i usług PaaS.

>[!div class="step-by-step"]
>[Wstecz](walkthroughs-technical-get-started-overview.md)
