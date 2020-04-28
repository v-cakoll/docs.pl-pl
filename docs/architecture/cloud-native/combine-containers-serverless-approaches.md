---
title: Łączenie kontenerów oraz metod bezserwerowych dla usług natywnych w chmurze
description: Łączenie kontenerów i Kubernetes za pomocą podejścia bezserwerowego
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199667"
---
# <a name="combining-containers-and-serverless-approaches"></a>Łączenie kontenerów i rozwiązań bezserwerowych

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikacje natywne w chmurze zwykle implementują usługi korzystające z kontenerów i aranżacji. Często istnieje możliwość uwidocznienia niektórych usług aplikacji jako Azure Functions. Jednak w przypadku aplikacji natywnej w chmurze wdrożonej w usłudze Kubernetes warto wykorzystać Azure Functions w tym samym zestawie narzędzi. Na szczęście można zawijać Azure Functions wewnątrz kontenerów platformy Docker i wdrażać je przy użyciu tych samych procesów i narzędzi, co w przypadku pozostałej części aplikacji opartej na Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Kiedy warto używać kontenerów z bezserwerowym użyciem?

Funkcja platformy Azure nie ma informacji o platformie, w której została wdrożona. W przypadku niektórych scenariuszy mogą istnieć określone wymagania i trzeba dostosować środowisko, w którym zostanie uruchomiony kod funkcji. Potrzebny jest obraz niestandardowy obsługujący zależności lub Konfiguracja nieobsługiwana przez domyślny obraz. W takich przypadkach warto wdrożyć funkcję w niestandardowym kontenerze platformy Docker.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Kiedy należy unikać używania kontenerów z Azure Functionsami?

Jeśli chcesz korzystać z rozliczeń zużycia, nie będzie można uruchamiać funkcji w kontenerze. Co więcej, jeśli funkcja zostanie wdrożona w klastrze Kubernetes, nie będzie już można korzystać z wbudowanego skalowania dostarczonego przez Azure Functions. Musisz użyć funkcji skalowania Kubernetes, opisanej wcześniej w tym rozdziale.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Jak połączyć kontenery bezserwerowe i platformy Docker

Aby otoczyć funkcję platformy Azure w kontenerze platformy Docker, zainstaluj [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) a następnie uruchom następujące polecenie:

```console
func init ProjectName --worker-runtime dotnet --docker
```

Po utworzeniu projektu będzie on zawierał pliku dockerfile i środowisko uruchomieniowe procesu roboczego skonfigurowane do `dotnet`. Teraz można tworzyć i testować funkcję lokalnie. Kompiluj i uruchamiaj przy użyciu `docker build` poleceń `docker run` i. Aby uzyskać szczegółowe instrukcje dotyczące rozpoczynania tworzenia Azure Functions z obsługą platformy Docker, zobacz samouczek [Tworzenie funkcji w systemie Linux przy użyciu niestandardowego obrazu](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Łączenie bezserwerowe i Kubernetes z KEDA

Usługa Azure Functions jest skalowana automatycznie, aby zaspokoić zapotrzebowanie na podstawie liczby zdarzeń docelowych. Zawsze możesz korzystać z AKS, aby hostować funkcje i korzystać z funkcji automatycznego skalowania opartego na zdarzeniach Kubernetes lub KEDA. Gdy nie są wykonywane żadne zdarzenia, KEDA może skalować w dół do zero wystąpień. [Dowiedz się więcej na temat skalowania usługi Azure Functions za pomocą KEDA](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

>[!div class="step-by-step"]
>[Poprzedni](leverage-serverless-functions.md)
>[Następny](deploy-containers-azure.md)
