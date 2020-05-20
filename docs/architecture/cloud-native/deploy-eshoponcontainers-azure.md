---
title: Wdrażanie aplikacji eShopOnContainers na platformie Azure
description: Wdrażanie aplikacji eShopOnContainers przy użyciu usługi Azure Kubernetes Service, Helm i DevSpaces.
ms.date: 05/13/2020
ms.openlocfilehash: 93a2848f095d7593e1e169f4a6c6c1818a76217d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614100"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>Wdrażanie aplikacji eShopOnContainers na platformie Azure

Aplikację eShopOnContainers można wdrożyć na różnych platformach platformy Azure. Zalecanym rozwiązaniem jest wdrożenie aplikacji w usłudze Azure Kubernetes Services (AKS). Helm, narzędzie wdrażania Kubernetes, jest dostępne w celu ograniczenia złożoności wdrożenia. Opcjonalnie deweloperzy mogą wdrożyć Azure Dev Spaces dla Kubernetes, aby usprawnić proces tworzenia aplikacji.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Aby hostować eShop w AKS, pierwszym krokiem jest utworzenie klastra AKS. W tym celu można użyć Azure Portal, który przeprowadzi Cię przez wymagane kroki. Możesz również utworzyć klaster z poziomu interfejsu wiersza polecenia platformy Azure, pamiętając o włączeniu Access Control opartego na rolach (RBAC) i routingu aplikacji. Dokumentacja eShopOnContainers ' zawiera szczegółowe instrukcje dotyczące tworzenia własnego klastra AKS. Po utworzeniu można uzyskać dostęp do klastra i zarządzać nim z poziomu pulpitu nawigacyjnego Kubernetes.

Teraz można wdrożyć aplikację eShop w klastrze za pomocą Helm Ier.

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>Wdrażanie w usłudze Azure Kubernetes za pomocą usługi Helm

Helm to narzędzie Menedżera pakietów aplikacji, które działa bezpośrednio z Kubernetes. Ułatwia ona Definiowanie, Instalowanie i Uaktualnianie aplikacji Kubernetes. Chociaż proste aplikacje można wdrażać w usłudze AKS przy użyciu niestandardowych skryptów interfejsu wiersza polecenia lub prostych plików wdrożenia, złożone aplikacje mogą zawierać wiele obiektów Kubernetes i korzystać z Helm.

Przy użyciu Helm aplikacje obejmują pliki konfiguracyjne oparte na tekście, nazywane wykresymi Helm, które deklaratywnie opisują aplikację i konfigurację w pakietach Helm. Wykresy używają standardowych plików YAML-sformatowana do opisywania powiązanego zestawu zasobów Kubernetes. Są one w wersji wraz z opisywanym przez siebie kodem aplikacji. Helm wykresy z prostego do złożonego, w zależności od wymagań instalacji opisywanej przez nie.

Helm składa się z narzędzia wiersza polecenia klienta, które korzysta z wykresów Helm i uruchamia polecenia do składnika serwera o nazwie. Do programu komunikuje się za pomocą interfejsu API Kubernetes w celu zapewnienia prawidłowej obsługi obciążeń kontenerów. Helm jest obsługiwany przez natywną podstawę obliczeniową w chmurze.

Następujący plik YAML przedstawia szablon Helm:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

Należy zauważyć, jak szablon opisuje dynamiczny zestaw par klucz/wartość. Po wywołaniu szablonu wartości ujęte w nawiasy klamrowe są pobierane z innych plików konfiguracji opartych na YAML.

Wykresy eShopOnContainers Helm można znaleźć w folderze/k8s/Helm Rysunek 2-6 pokazuje, w jaki sposób różne składniki aplikacji są zorganizowane w strukturę folderów używaną przez Helm do definiowania wdrożeń i zarządzania nimi.

![Rysunek architektury eShopOnContainers ](./media/eshoponcontainers-helm-folder.png)
 **2-6**. Folder eShopOnContainers Helm.

Każdy indywidualny składnik jest instalowany przy użyciu `helm install` polecenia. eShop zawiera skrypt "Deploy All", który powoduje pętlę i instaluje składniki przy użyciu odpowiednich wykresów Helm. Wynikiem jest powtarzalny proces, wersja z aplikacją w kontroli źródła, którą każdy członek zespołu może wdrożyć w klastrze AKS z jednowierszowym poleceniem skryptu.

> Należy zauważyć, że wersja 3 Helm oficjalnie eliminuje konieczność użycia składnika serwera programu do obsługi. Więcej informacji na temat tego rozszerzenia można znaleźć [tutaj](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Aplikacje natywne w chmurze mogą szybko rozwijać duże i złożone, co wymaga znaczących zasobów obliczeniowych. W tych scenariuszach cała aplikacja nie może być hostowana na maszynie deweloperskiej (szczególnie w przypadku laptopu). Azure Dev Spaces zaprojektowano w celu rozwiązania tego problemu przy użyciu AKS. Pozwala to deweloperom na współdziałanie z lokalną wersją swoich usług przy jednoczesnym obsługiwaniu reszty aplikacji w klastrze projektowym AKS.

Deweloperzy mogą korzystać z działającego wystąpienia (Programowanie) w klastrze AKS zawierającym całą zaprojektowaną aplikację. Ale korzystają z miejsc osobistych skonfigurowanych na ich maszynach do lokalnego tworzenia usług. Gdy wszystko będzie gotowe, testuje od końca do końca w klastrze AKS — bez replikowania zależności. Azure Dev Spaces Scala kod z komputera lokalnego z usługami w AKS. Członkowie zespołu mogą zobaczyć, jak ich zmiany będą zachowywać się w rzeczywistym środowisku AKS. Deweloperzy mogą szybko iterować i debugować kod bezpośrednio w Kubernetes za pomocą programu Visual Studio 2017 lub Visual Studio Code.

Na rysunku 2-7 można zobaczyć, że Susie dewelopera wdrożono zaktualizowaną wersję mikrousługi programu Bikes do jej obszaru dev. Następnie można testować zmiany przy użyciu niestandardowego adresu URL rozpoczynającego się od nazwy miejsca (susie.s.dev.myapp.eus.azds.io).

![Rysunek architektury eShopOnContainers ](./media/azure-devspaces-one.png)
 **2-7**. Susie dewelopera wdraża własną wersję mikrousługi programu Bikes i testuje ją.

W tym samym czasie Developer Jan dostosowuje mikrousługę rezerwacji i wymaga przetestowania zmian. Wdraża zmiany w swoim własnym obszarze deweloperskim bez konfliktu ze zmianami Susie, jak pokazano na rysunku 2-8. Jan następnie testuje swoje zmiany przy użyciu własnego adresu URL, który jest poprzedzony nazwą swojego miejsca (john.s.dev.myapp.eus.azds.io).

![Rysunek architektury eShopOnContainers ](./media/azure-devspaces-two.png)
 **2-8**. Deweloperzy nie wdrażają własnej wersji mikrousługi rezerwacji i testują ją bez konfliktu z innymi deweloperami.

Za pomocą Azure Dev Spaces zespoły mogą współpracować bezpośrednio z usługą AKS, niezależnie od zmieniania, wdrażania i testowania zmian. Takie podejście zmniejsza potrzebę korzystania z oddzielnych dedykowanych środowisk hostowanych, ponieważ każdy deweloper efektywnie ma własne środowisko AKS. Deweloperzy mogą korzystać z Azure Dev Spaces przy użyciu interfejsu wiersza polecenia lub uruchamiać aplikacje do Azure Dev Spaces bezpośrednio z programu Visual Studio. [Dowiedz się więcej o tym, jak działa Azure Dev Spaces i czy jest skonfigurowane.](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions i Logic Apps (bezserwerowo)

Przykład eShopOnContainers obejmuje obsługę śledzenia kampanii marketingowych online. Funkcja platformy Azure służy do śledzenia szczegółów kampanii marketingowej dla danego identyfikatora kampanii. Zamiast tworzyć pełną mikrousługi, pojedyncza funkcja platformy Azure jest prostsza i wystarczająca. Azure Functions mieć prosty model kompilacji i wdrażania, szczególnie gdy jest skonfigurowany do uruchamiania w Kubernetes. Wdrażanie funkcji jest skryptem przy użyciu szablonów Azure Resource Manager (ARM) i interfejsu wiersza polecenia platformy Azure. Ta usługa kampanii nie jest połączona z klientem i wywołuje pojedynczą operację, co sprawia, że jest to doskonały kandydat do Azure Functions. Funkcja wymaga minimalnej konfiguracji, w tym danych parametrów połączenia bazy danych i podstawowych ustawień identyfikatora URI obrazu. Azure Functions można skonfigurować w Azure Portal.

>[!div class="step-by-step"]
>[Poprzedni](map-eshoponcontainers-azure-services.md) 
> [Dalej](centralized-configuration.md)
