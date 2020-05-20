---
title: Skalowanie kontenerów i aplikacji bezserwerowych
description: Skalowanie aplikacji natywnych w chmurze za pomocą usługi Azure Kubernetes Service w celu spełnienia wymagań użytkownika.
ms.date: 05/13/2020
ms.openlocfilehash: a5e1e8df785fd08901d9be41c0a06db35e09296b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613723"
---
# <a name="scaling-containers-and-serverless-applications"></a>Skalowanie kontenerów i aplikacji bezserwerowych

Istnieją dwa sposoby skalowania aplikacji: w górę lub w dół. Dawniej dotyczy Dodawanie pojemności do pojedynczego zasobu, podczas gdy drugie odnosi się do dodawania większej liczby zasobów w celu zwiększenia pojemności.

## <a name="the-simple-solution-scaling-up"></a>Proste rozwiązanie: skalowanie w górę

Uaktualnienie istniejącego serwera hosta z zwiększonym procesorem CPU, pamięci, szybkością we/wy dysku i szybkością operacji we/wy sieci jest określana jako *skalowanie w górę*. Skalowanie aplikacji natywnej w chmurze polega na wyborze większej ilości zasobów od dostawcy chmury. Na przykład można uzyskać nową pulę węzłów z większymi maszynami wirtualnymi w klastrze Kubernetes. Następnie Przeprowadź migrację usług kontenerowych do nowej puli.

Aplikacje bezserwerowe skalowanie w górę przez wybranie rozmiaru [planu funkcji Premium](https://docs.microsoft.com/azure/azure-functions/functions-scale) lub wystąpienia Premium z dedykowanego planu usługi App Service.

## <a name="scaling-out-cloud-native-apps"></a>Skalowanie aplikacji natywnych w chmurze

Aplikacje natywne w chmurze często napotykają duże wahania popytu i wymagają skalowania na chwilę. Preferują skalowanie w górę. Skalowanie w poziomie jest realizowane przez dodanie do istniejącego klastra dodatkowych maszyn (nazywanych węzłami) lub wystąpień aplikacji. W Kubernetes można skalować ręcznie przez dostosowanie ustawień konfiguracji dla aplikacji (na przykład [skalowanie puli węzłów](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) lub Skalowanie automatyczne.

Klastry AKS można skalować automatycznie na jeden z dwóch sposobów:

Najpierw monitoruje zapotrzebowanie na zasoby i automatycznie skaluje repliki na [poziomie](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods) , aby je spełnić. Po zwiększeniu natężenia ruchu dodatkowe repliki są automatycznie inicjowane w celu skalowania usług. Podobnie po zmniejszeniu zapotrzebowania są one usuwane do usługi skalowanie w poziomie. Należy zdefiniować metrykę, dla której ma być skalowane, na przykład użycie procesora CPU. Możesz również określić minimalną i maksymalną liczbę replik do uruchomienia. AKS monitoruje tę metrykę i skaluje się odpowiednio.

Następnie funkcja automatycznego [skalowania klastra AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler) umożliwia automatyczne skalowanie węzłów obliczeniowych w klastrze Kubernetes w celu spełnienia wymagań. Dzięki niej można automatycznie dodawać nowe maszyny wirtualne do podstawowego zestawu skalowania maszyn wirtualnych platformy Azure, gdy jest wymagana większa pojemność obliczeniowa. Powoduje również usunięcie węzłów, gdy nie są już wymagane.

Rysunek 3-13 przedstawia relację między tymi dwoma usługami skalowania.

![Skalowanie planu App Service.](./media/aks-cluster-autoscaler.png)

**Rysunek 3-13**. Skalowanie planu App Service.

Jednocześnie należy zapewnić optymalną liczbę wystąpień kontenerów i węzłów obliczeniowych do obsługi wahań popytu. Skalowanie w poziomie poniżej optymalizuje wymaganą liczbę zasobników. Automatyczne skalowanie klastra optymalizuje wymaganą liczbę węzłów.

### <a name="scaling-azure-functions"></a>Skalowanie Azure Functions

Azure Functions automatycznie skalować na żądanie. Zasoby serwera są przydzielane dynamicznie i usuwane na podstawie liczby wyzwalanych zdarzeń. Opłata jest naliczana tylko za zasoby obliczeniowe używane podczas uruchamiania funkcji. Opłaty są naliczane na podstawie liczby wykonań, czasu wykonania i używanej pamięci.

Chociaż domyślny plan zużycia zapewnia ekonomiczne i skalowalne rozwiązanie dla większości aplikacji, opcja Premium umożliwia deweloperom elastyczność niestandardowych wymagań Azure Functions. Uaktualnienie do planu Premium zapewnia kontrolę nad rozmiarem wystąpienia, przed wystąpieniem awaryjnym (w celu uniknięcia opóźnień uruchamiania) i dedykowanych maszyn wirtualnych.

>[!div class="step-by-step"]
>[Poprzedni](deploy-containers-azure.md) 
> [Dalej](other-deployment-options.md)
