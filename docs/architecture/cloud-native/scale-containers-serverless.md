---
title: Skalowanie kontenerów i aplikacji bezserwerowych
description: Skalowanie aplikacji natywnych w chmurze za pomocą usługi Azure Kubernetes Service, aby zaspokoić zapotrzebowanie użytkowników przez zwiększenie indywidualnych zasobów maszynowych lub zwiększenie liczby maszyn w klastrze aplikacji.
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184800"
---
# <a name="scaling-containers-and-serverless-applications"></a>Skalowanie kontenerów i aplikacji bezserwerowych

Istnieją dwa typowe sposoby skalowania aplikacji: skalowanie w górę i skalowanie w poziomie. Dawna odnosi się do dodawania funkcji do jednego hosta, podczas gdy drugie odwołuje się do dodawania do całkowitej liczby hostów. Typowym analogem, który można wykorzystać w celu zapoznania się z tym, jak poznać siebie i kilku znajomych w miejscowości. Jeśli jest to tylko jeden znajomy, możesz przełączać się do samochodu wyścigowego z dwoma stanowiskami. Ale jeśli jest to trzy lub cztery, może być konieczne wykonanie jednej z SUVs lub minivan, skalowanie w górę w celu zwiększenia pojemności. Gdy łączna liczba przeskoczy do dziesiątek lub więcej, to prawdopodobnie trzeba będzie korzystać z wielu pojazdów (o ile ktoś nie korzysta z magistrali), który pokazuje koncepcję skalowania przez dodanie większej liczby wystąpień (w tym przypadku więcej pojazdów). Zobaczmy, jak to dotyczy nasze aplikacje.

## <a name="the-simple-solution-scaling-up"></a>Proste rozwiązanie: skalowanie w górę

Proces uaktualniania istniejących serwerów w celu udostępnienia im więcej zasobów (procesor CPU, pamięć, szybkość we/wy dysku, szybkość operacji we/wy sieci) jest określana jako *skalowanie w górę*. W przypadku aplikacji natywnych w chmurze skalowanie w górę nie odnosi się zazwyczaj do kupowania i instalowania rzeczywistego sprzętu na komputerach fizycznych, tak jak w przypadku wybrania planu z możliwością obsługi z listy dostępnych opcji. Aplikacje natywne w chmurze zwykle są skalowane przez modyfikację rozmiaru maszyny wirtualnej używanej do hostowania poszczególnych węzłów w puli węzłów Kubernetes. Koncepcje Kubernetes, takie jak węzły, klastry i zasobniki, są opisane w [następnej sekcji](leverage-containers-orchestrators.md). Platforma Azure obsługuje różne rozmiary maszyn wirtualnych z systemami [Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) i [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes). Aby skalować aplikację w pionie, Utwórz nową pulę węzłów o większym rozmiarze maszyny wirtualnej, a następnie Migruj obciążenia do nowej puli. Wymaga to [wielu pul węzłów dla klastra AKS](https://docs.microsoft.com/azure/aks/use-multiple-node-pools), która jest obecnie dostępna w wersji zapoznawczej. Aplikacje bezserwerowe skalowanie w górę, wybierając [Plan Premium](https://docs.microsoft.com/azure/azure-functions/functions-scale) i rozmiary wystąpienia Premium lub wybierając inny dedykowany plan usługi App Service.

## <a name="scaling-out-cloud-native-apps"></a>Skalowanie aplikacji natywnych w chmurze

Aplikacje natywne w chmurze obsługują skalowanie w poziomie przez dodanie do żądania obsługi dodatkowych węzłów lub zasobników. Można to zrobić ręcznie przez dostosowanie ustawień konfiguracji aplikacji (na przykład [skalowanie puli węzłów](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) lub *skalowanie*automatyczne. Skalowanie automatyczne dostosowuje zasoby używane przez aplikację w celu reagowania na zapotrzebowanie, podobnie jak termostat reaguje na temperaturę, wywołując w celu dodatkowego ogrzewania lub chłodzenia. W przypadku korzystania z skalowania automatycznego skalowanie ręczne jest wyłączone.

Klastry AKS można skalować na jeden z dwóch sposobów:

- [Automatyczne skalowanie klastra](https://docs.microsoft.com/azure/aks/cluster-autoscaler) jest obserwujące dla zasobników, których nie można zaplanować w węzłach ze względu na ograniczenia zasobów. Dodaje dodatkowe węzły zgodnie z potrzebami.
- **Skalowanie w poziomie** poniżej używa serwera metryk w klastrze Kubernetes do monitorowania zapotrzebowania na zasoby. Jeśli usługa wymaga więcej zasobów, Skalowanie automatyczne zwiększa liczbę zasobników.

Rysunek 3-13 przedstawia relację między tymi dwoma usługami skalowania.

![Skalowanie planu App Service.](./media/aks-cluster-autoscaler.png)

**Rysunek 3-13**. Skalowanie planu App Service.

Te usługi mogą również zmniejszyć liczbę potrzebnych lub węzłów. Te dwie usługi mogą współdziałać ze sobą i są często wdrażane w klastrze. Po połączeniu, skalowanie w poziomie na pionie jest ukierunkowane na uruchamianie liczby numerów wymaganych do spełnienia wymagań aplikacji. Automatyczne skalowanie klastra koncentruje się na uruchamianiu liczby węzłów wymaganych do obsługi zaplanowanych zasobników.

### <a name="scaling-azure-functions"></a>Skalowanie Azure Functions

Azure Functions automatycznie obsługuje skalowanie w górę. Domyślny plan zużycia umożliwia dynamiczne dodawanie (i usuwanie) zasobów na podstawie liczby zdarzeń wyzwalających. Opłata jest naliczana tylko za zasoby obliczeniowe używane, gdy funkcje są uruchomione na podstawie liczby wykonań, czasu wykonania i używanej pamięci. Korzystając z planu Premium, uzyskasz te same funkcje, ale można również kontrolować używane rozmiary wystąpień, mieć już wykonane wystąpienia (aby uniknąć opóźnień uruchamiania) i skonfigurować dedykowane maszyny wirtualne, na których mają być uruchamiane funkcje. Mimo że domyślna konfiguracja powinna zapewniać ekonomiczne i skalowalne rozwiązanie dla większości aplikacji, opcja Premium umożliwia deweloperom elastyczność niestandardowych wymagań Azure Functions.

## <a name="references"></a>Odwołania

- [AKS pul wielu węzłów](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Automatyczne skalowanie klastra AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Samouczek: Skalowanie aplikacji w AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure Functions skalowanie i hosting](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[Poprzedni](deploy-containers-azure.md)
>[Następny](other-deployment-options.md)
