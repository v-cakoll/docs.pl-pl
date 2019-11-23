---
title: Wdrażanie aplikacji eShopOnContainers na platformie Azure
description: Wdrażanie aplikacji eShopOnContainers przy użyciu usługi Azure Kubernetes Service, Helm i DevSpaces.
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183274"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Wdrażanie aplikacji eShopOnContainers na platformie Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Logika obsługująca aplikację eShopOnContainers może być obsługiwana przez platformę Azure przy użyciu różnych usług. Zalecanym podejściem jest skorzystanie z Kubernetes za pomocą usługi Azure Kubernetes Service (AKS). Można to zrobić za pomocą wdrażania Helm, aby zapewnić łatwą konfigurację infrastruktury. Opcjonalnie deweloperzy mogą korzystać z Azure Dev Spaces dla Kubernetes w ramach procesu tworzenia aplikacji. Inną opcją jest hostowanie funkcjonalności aplikacji przy użyciu funkcji bezserwerowych platformy Azure, takich jak Azure Functions i Azure Logic Apps.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Jeśli chcesz hostować aplikację eShopOnContainers w swoim klastrze AKS, pierwszym krokiem jest utworzenie klastra. Można to zrobić za pomocą Azure Portal, który przeprowadzi Cię przez wymagane kroki lub można użyć interfejsu wiersza polecenia platformy Azure, pamiętając, aby zapewnić włączenie Access Control (RBAC) opartego na rolach i routingu aplikacji. W dokumentacji eShopOnContainers opisano czynności związane z tworzeniem własnego klastra AKS. Po utworzeniu klastra należy włączyć dostęp do pulpitu nawigacyjnego Kubernetes, w którym można przejść do pulpitu nawigacyjnego Kubernetes w celu zarządzania klastrem.

Po utworzeniu i skonfigurowaniu klastra można wdrożyć w nim aplikację przy użyciu Helm i do niej.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Wdrażanie w usłudze Azure Kubernetes za pomocą usługi Helm

Podstawowe wdrożenia do AKS mogą używać niestandardowych skryptów interfejsu wiersza polecenia lub prostych plików wdrożenia, ale bardziej złożone aplikacje powinny używać narzędzia do zarządzania zależnościami, takiego jak Helm. Usługa Helm jest obsługiwana przez natywną Fundację obliczeniową w chmurze i ułatwia definiowanie, Instalowanie i Uaktualnianie aplikacji Kubernetes. Helm składa się z wiersza polecenia klienta, Helm, który używa wykresów Helm oraz składnika w klastrze, do którego odnosi się. Wykresy Helm używają standardowych plików YAML do opisywania powiązanego zestawu zasobów Kubernetes i są zwykle używane wraz z opisywaną przez siebie aplikacją. Helm wykresy z prostego do złożonego, w zależności od wymagań instalacji opisywanej przez nie.

Wykresy eShopOnContainers Helm można znaleźć w folderze/k8s/Helm Rysunek 2-6 pokazuje, w jaki sposób różne składniki aplikacji są zorganizowane w strukturę folderów używaną przez Helm do definiowania wdrożeń i zarządzania nimi.

![architekturę eShopOnContainers](./media/eshoponcontainers-helm-folder.png)
**rysunek 2-6**. Folder eShopOnContainers Helm.

Każdy indywidualny składnik jest instalowany przy użyciu polecenia `helm install`. Te polecenia można łatwo zaskryptować, a eShopOnContainers zawiera skrypt "Deploy All", który przechodzi przez różne składniki i instaluje je przy użyciu odpowiednich wykresów Helm. Wynikiem jest powtarzalny proces, wersja z aplikacją w kontroli źródła, którą każdy członek zespołu może wdrożyć w klastrze AKS z jednowierszowym poleceniem skryptu. Szczególnie w połączeniu z Azure Dev Spaces, ułatwiają deweloperom diagnozowanie i testowanie indywidualnych zmian w aplikacjach natywnych w chmurze opartych na mikrousługach.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces pomaga indywidualnym deweloperom hostować własne, unikatowe wersje klastrów AKS na platformie Azure podczas opracowywania. Minimalizuje to wymagania komputera lokalnego i umożliwia członkom zespołu szybkie sprawdzenie, jak ich zmiany będą zachowywać się w rzeczywistym środowisku AKS. Azure Dev Spaces oferuje interfejs wiersza polecenia dla deweloperów, który umożliwia deweloperom zarządzanie miejscami deweloperskimi oraz wdrażanie ich w określonym podrzędnym miejscu deweloperskim zgodnie z potrzebami. Każde podrzędne miejsce dev jest przywoływana przy użyciu unikatowej poddomeny adresu URL, co umożliwia równoczesne wdrażanie zmodyfikowanych klastrów, dzięki czemu Indywidualni deweloperzy mogą uniknąć konfliktu ze sobą w toku. Na rysunku 2-7 można zobaczyć, w jaki sposób deweloper Susie wdrożył własną wersję mikrousługi programu Bikes do swojej przestrzeni dev. Następnie można testować zmiany przy użyciu niestandardowego adresu URL rozpoczynającego się od nazwy miejsca (susie.s.dev.myapp.eus.azds.io).

![architekturę eShopOnContainers](./media/azure-devspaces-one.png)
**rysunek 2-7**. Susie dewelopera wdraża własną wersję mikrousługi programu Bikes i testuje ją.

W tym samym czasie Developer Jan dostosowuje mikrousługę rezerwacji i wymaga przetestowania zmian. Jest w stanie wdrożyć zmiany w swoim własnym obszarze deweloperskim bez konfliktu ze zmianami Susie, jak pokazano na rysunku 2-8. Może testować swoje zmiany przy użyciu własnego adresu URL, który jest poprzedzony nazwą jego miejsca (john.s.dev.myapp.eus.azds.io).

![architekturę eShopOnContainers](./media/azure-devspaces-two.png)
**rysunek 2-8**. Deweloperzy nie wdrażają własnej wersji mikrousługi rezerwacji i testują ją bez konfliktu z innymi deweloperami.

Za pomocą Azure Dev Spaces zespoły mogą współpracować bezpośrednio z usługą AKS, niezależnie od zmieniania, wdrażania i testowania zmian. Takie podejście zmniejsza potrzebę korzystania z oddzielnych dedykowanych środowisk hostowanych, ponieważ każdy deweloper efektywnie ma własne środowisko AKS. Deweloperzy mogą korzystać z Azure Dev Spaces przy użyciu interfejsu wiersza polecenia lub uruchamiać aplikacje do Azure Dev Spaces bezpośrednio z programu Visual Studio. [Dowiedz się więcej o tym, jak działa Azure Dev Spaces i czy jest skonfigurowane.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions i Logic Apps (bezserwerowo)

Przykład eShopOnContainers obejmuje obsługę śledzenia kampanii marketingowych online. Funkcja platformy Azure służy do ściągania szczegółów kampanii marketingowej dla danego identyfikatora kampanii. Zamiast tworzenia w tym celu kompletnej aplikacji ASP.NET Core, jeden punkt końcowy funkcji platformy Azure jest łatwiejszy i wystarczający. Azure Functions mieć znacznie prostszy model kompilowania i wdrażania niż pełne aplikacje ASP.NET Core, szczególnie w przypadku, gdy jest skonfigurowany do uruchamiania w Kubernetes. Wdrażanie funkcji jest skryptem przy użyciu szablonów Azure Resource Manager (ARM) i interfejsu wiersza polecenia platformy Azure. Ta szczegóły kampanii mikrousługa nie jest dostępna dla klientów i nie ma takich samych wymagań, jak w przypadku sklepu online, dzięki czemu jest to dobry kandydat do Azure Functions. Funkcja wymaga, aby pewna konfiguracja działała prawidłowo, na przykład w przypadku danych parametrów połączenia bazy danych i podstawowych ustawień URI obrazu. Azure Functions można skonfigurować w witrynie Azure Portal.

## <a name="references"></a>Odwołania

- [eShopOnContainers: Utwórz klaster Kubernetes w AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Poprzedni](map-eshoponcontainers-azure-services.md)
>[Następny](centralized-configuration.md)
