---
title: Inne opcje wdrażania kontenera
description: Inne opcje wdrażania kontenerów korzystających z platformy Azure
ms.date: 06/30/2019
ms.openlocfilehash: 892514417cb8650c28b7491315f767758278ad6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184884"
---
# <a name="other-container-deployment-options"></a>Inne opcje wdrażania kontenera

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Oprócz wdrażania w programie AKS można także wdrożyć kontenery do Azure App Service na potrzeby kontenerów i Azure Container Instances.

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>Kiedy warto wdrożyć do App Service dla kontenerów?

Proste aplikacje produkcyjne, które nie wymagają aranżacji, są dobrze dostosowane do Azure App Service kontenerów.

## <a name="how-to-deploy-to-app-service-for-containers"></a>Jak wdrożyć do App Service dla kontenerów

Aby wdrożyć program do [Azure App Service dla kontenerów](https://azure.microsoft.com/services/app-service/containers/), musisz skonfigurować Azure Container Registry (ACR) i poświadczenia do uzyskiwania do nich dostępu. Wypchnij kontener, który ma być hostowany do rejestru, aby można było go pobrać do Azure App Service. Po utworzeniu można skonfigurować aplikację do ciągłego wdrażania, która będzie automatycznie wdrażać aktualizacje aplikacji przy każdej aktualizacji odpowiedniego obrazu w ACR.

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>Kiedy warto wdrożyć do Azure Container Instances?

Azure Container Instances najlepiej używać na potrzeby scenariuszy testowania. Zapewniają one szybki i prosty sposób wdrożenia aplikacji w wystąpieniu kontenera hostowanego w chmurze. Korzystaj z nich do testowania i demonstracji aplikacji, jeśli nie potrzebujesz funkcji skalowania i aranżacji oferowanych przez usługę Azure Kubernetes.

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>Jak wdrożyć aplikację w Azure Container Instances

Aby wdrożyć program do [Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/), musisz skonfigurować Azure Container Registry (ACR) i poświadczenia do uzyskiwania do nich dostępu. Należy również wcześniej wypchnąć obraz kontenera do rejestru, aby można było go pobrać do ACI. Możesz korzystać z ACI za pomocą interfejsu wiersza polecenia platformy Azure lub portalu. Rejestry kontenerów platformy Azure ułatwiają wdrażanie pojedynczych wystąpień kontenera do ACI bezpośrednio z rejestru, jak pokazano na rysunku 3-14.

![Wystąpienie uruchomienia Azure Container Registry](./media/acr-runinstance-contextmenu.png)

**Rysunek 3-14**. Wystąpienie uruchomienia Azure Container Registry

Tworzenie wystąpienia kontenera z rejestru tylko wymaga określenia zwykłych ustawień platformy Azure (nazwa, subskrypcja, Grupa zasobów i lokalizacja), ilości pamięci do przydzielenia do kontenera oraz portu, na którym należy nasłuchiwać. W tym [przewodniku szybki start pokazano, jak wdrożyć wystąpienie kontenera do ACI przy użyciu Azure Portal](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal).

Po zakończeniu wdrożenia Znajdź nowo wdrożony adres IP kontenera i skontaktuj się z nim za pośrednictwem określonego portu.

Azure Container Instances oferuje najszybszy, najprostszy sposób uruchamiania kontenera na platformie Azure. Nie ma potrzeby konfigurowania usługi App Service ani programu Orchestrator ani do obsługi maszyn wirtualnych. Jednak ze względu na prostotę ACI należy wykorzystać głównie do celów testowych. Jeśli aplikacja wymaga automatycznej skalowalności, wiele kontenerów skonfigurowanych do współdziałania lub wszelkich dodatkowych funkcji złożonych, dostępne są inne usługi platformy Azure, które umożliwiają hostowanie Twojej aplikacji.

## <a name="references"></a>Odwołania

- [Dokumentacja Azure Container Instances](https://docs.microsoft.com/azure/container-instances/)
- [Wdróż wystąpienie kontenera z ACR](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[Poprzedni](scale-containers-serverless.md)
>[Następny](communication-patterns.md) <!-- Next Chapter -->
