---
title: Łączenie kontenerów oraz metod bezserwerowych dla usług natywnych w chmurze
description: Łączenie kontenerów i Kubernetes za pomocą podejścia bezserwerowego
ms.date: 04/23/2020
ms.openlocfilehash: a6ae17543c9075ca84126a4c19f9f51887f7fe9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895640"
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

W tym rozdziale zaobserwowano, że platforma Azure Functions "automatycznie skaluje się w celu spełnienia wymagań. W przypadku wdrażania funkcji kontenera w programie AKS jednak tracisz wbudowaną funkcję skalowania. Do ratowania jest [oparta Kubernetes zdarzeń (KEDA)](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda). Umożliwia precyzyjne Skalowanie automatyczne w celu `event-driven Kubernetes workloads,` uwzględnienia funkcji kontenerów.

KEDA zapewnia funkcję skalowania sterowaną zdarzeniami do środowiska uruchomieniowego Functions w kontenerze platformy Docker. KEDA można skalować od zero wystąpień (gdy nie są wykonywane `n instances`żadne zdarzenia) na podstawie obciążenia. Umożliwia automatyczne skalowanie przez udostępnienie metryk niestandardowych do skalowania automatycznego (Kubernetes). Używanie kontenerów funkcji z KEDA umożliwia replikowanie funkcji bezserwerowych w dowolnym klastrze Kubernetes.

Warto zauważyć, że projekt KEDA jest teraz zarządzany przez natywną fundament w chmurze (CNCF).

>[!div class="step-by-step"]
>[Poprzedni](leverage-serverless-functions.md)
>[Następny](deploy-containers-azure.md)
