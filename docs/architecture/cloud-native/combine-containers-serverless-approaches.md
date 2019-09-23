---
title: Łączenie kontenerów i metod bezserwerowych
description: Łączenie kontenerów i Kubernetes za pomocą podejścia bezserwerowego
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183435"
---
# <a name="combining-containers-and-serverless-approaches"></a>Łączenie kontenerów i metod bezserwerowych

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Często aplikacje oparte na mikrousługach opierają się na kontenerach, aranżacji i przekazywaniu komunikatów do komunikacji między węzłami. Ten komunikat jest idealnym zadaniem dla Azure Functions, ale wraz z pozostałą częścią aplikacji skonfigurowanej i wdrożonej przy użyciu Kubernetes i narzędzi związanych z nimi, najprawdopodobniej będzie można wykorzystać Azure Functions w tym samym przyborniku. Na szczęście można zawijać Azure Functions w kontenerach platformy Docker i wdrażać je przy użyciu tych samych procesów i narzędzi, co w przypadku pozostałej części aplikacji opartej na Kubernetes.

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a>Kiedy warto używać kontenerów z bezserwerowym użyciem?

Domyślnie funkcje bezserwerowe nie mają informacji o platformie, w której będą uruchamiane. Jednak w niektórych przypadkach mogą istnieć konkretne wymagania, które są ważne, aby można było dostosować obraz kontenera, w którym będzie wykonywany kod. Możesz chcieć użyć niestandardowego obrazu, ponieważ funkcja korzysta z określonej wersji językowej lub ma zależności lub wymagania dotyczące konfiguracji, które nie są obsługiwane przez domyślny obraz. W takich przypadkach warto dostosować własny kontener i wdrożyć funkcję w niestandardowym kontenerze platformy Docker.

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a>Kiedy należy unikać używania kontenerów z Azure Functionsami?

Jeśli zamierzasz korzystać z rozliczeń planu zużycia dla funkcji, nie będzie można tego robić, jeśli używasz własnego kontenera. Co więcej, jeśli przejdziesz poza prostu przy użyciu kontenera Docker i wdrażasz funkcje w własnym klastrze Kubernetes, nie będziesz już korzystać z wbudowanego skalowania zapewnianego przez Azure Functions. Musisz użyć funkcji skalowania Kubernetes "opisanych poniżej.

## <a name="how-to-combine-serverless-and-docker-containers"></a>Jak połączyć kontenery bezserwerowe i platformy Docker

Aby otoczyć funkcję platformy Azure w kontenerze platformy Docker, Zainstaluj Azure Functions Core Tools a następnie uruchom następujące polecenie:

```console
func init ProjectName --docker
```

Wybierz z następujących opcji środowisko uruchomieniowe procesu roboczego:

- `dotnet` (C#)
- `node` (JavaScript)
- `python`

Po utworzeniu projektu będzie on zawierał pliku dockerfile. Teraz można tworzyć i testować funkcję lokalnie. Kompiluj i uruchamiaj przy użyciu `docker build` poleceń `docker run` i. Aby uzyskać szczegółowe instrukcje dotyczące rozpoczynania tworzenia Azure Functions z obsługą platformy Docker, zobacz samouczek [Tworzenie funkcji w systemie Linux przy użyciu niestandardowego obrazu](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a>Łączenie bezserwerowe i Kubernetes z KEDA

Usługa Azure Functions jest skalowana automatycznie, aby zaspokoić zapotrzebowanie na podstawie liczby zdarzeń przeznaczonych dla danej funkcji. Ponadto można korzystać z Kubernetes, aby hostować funkcje i korzystać z funkcji automatycznego skalowania opartego na zdarzeniach Kubernetes lub KEDA. Gdy nie są wykonywane żadne zdarzenia, KEDA może skalować w dół do 0 wystąpień, a następnie w odpowiedzi na zdarzenia może skalować liczbę kontenerów, aby zaspokoić zapotrzebowanie przy użyciu jego skalowania w poziomie. [Dowiedz się więcej na temat skalowania usługi Azure Functions za pomocą KEDA](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).

## <a name="references"></a>Odwołania

- [Uruchamianie Azure Functions w kontenerze platformy Docker](https://markheath.net/post/azure-functions-docker)
- [Tworzenie funkcji w systemie Linux przy użyciu obrazu niestandardowego](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [Azure Functions z funkcją automatycznego skalowania opartego na zdarzeniach Kubernetes](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
>[Poprzedni](leverage-serverless-functions.md)
>[Następny](deploy-containers-azure.md)
