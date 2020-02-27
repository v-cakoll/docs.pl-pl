---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Odkryj opcje organizowania mikrousług i wielokontenerowych aplikacji w celu zapewnienia wysokiej skalowalności i dostępności oraz możliwości Azure Dev Spaces podczas opracowywania cyklu życia aplikacji Kubernetes.
ms.date: 01/30/2020
ms.openlocfilehash: ea204941a461794fbeeb2482aa11973b79437027
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628504"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Korzystanie z koordynatorów dla aplikacji gotowych do użycia w środowisku produkcyjnym jest niezbędne, jeśli aplikacja jest oparta na mikrousługach lub po prostu jest dzielona na wiele kontenerów. Jak zostało to zrobione wcześniej, w podejściu opartym na mikrousługach każda mikrousługa jest właścicielem modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia projektowania i wdrożenia. Jednak nawet jeśli masz bardziej tradycyjną aplikację składającą się z wielu usług (na przykład SOA), będziesz mieć również wiele kontenerów lub usług składających się z jednej aplikacji biznesowej, która musi zostać wdrożona jako system rozproszony. Te rodzaje systemów są skomplikowane do skalowania w poziomie i zarządzania nimi. w związku z tym, jeśli chcesz korzystać z gotowej do produkcji i skalowalnej aplikacji z obsługą kontenerów, musisz mieć absolutną wartość Orchestrator.

Rysunek 4-23 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Diagram przedstawiający złożone aplikacje platformy Docker w klastrze.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Rysunek 4-23**. Klaster kontenerów

Dla każdego wystąpienia usługi należy użyć jednego kontenera. Kontenery platformy Docker to "jednostki wdrożenia", a kontener to wystąpienie platformy Docker. Host obsługuje wiele kontenerów. Wygląda podobnie do podejścia logicznego. Ale w jaki sposób są obsługiwane Równoważenie obciążenia, Routing i organizowanie tych aplikacji złożonych?

Aparat aparatu Docker w ramach jednego hosta platformy Docker spełnia potrzeby zarządzania wystąpieniami jednego obrazu na jednym hoście, ale jest on krótki, gdy przyjdzie do zarządzania wieloma kontenerami wdrożonymi na wielu hostach w celu uzyskania bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która będzie automatycznie uruchamiać kontenery, skalować w poziomie kontenery z wieloma wystąpieniami na obraz, wstrzymywać je lub zamykać je w razie potrzeby, a także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieć i dane Chowan.

Aby przekroczyć możliwości zarządzania indywidualnymi kontenerami lub bardzo prostymi aplikacjami złożonymi i przenieść się do większej liczby aplikacji przedsiębiorstwa przy użyciu mikrousług, musisz włączyć aranżację i platformę klastrowania.

Jeśli tworzysz duże przedsiębiorstwa składające się z aplikacji opartych na mikrousługach, pamiętaj, aby zrozumieć następujące platformy i produkty, które obsługują zaawansowane scenariusze:

**Klastry i usługi Orchestrator.** Gdy konieczne jest skalowanie aplikacji w poziomie na wielu hostach platformy Docker, tak jak w przypadku dużych aplikacji opartych na mikrousługach, ma ona kluczowe znaczenie dla zarządzania wszystkimi hostami jako pojedynczym klastrem przez abstrakcję złożoności podstawowej platformy. To właśnie zapewnia klaster kontenerów i koordynatorów. Kubernetes jest przykładem programu Orchestrator i jest dostępny na platformie Azure za pomocą usługi Azure Kubernetes Service.

**Planiści.** *Planowanie* oznacza możliwość, aby administrator mógł uruchamiać kontenery w klastrze, a także udostępnia interfejs użytkownika. Harmonogram klastrów ma kilka obowiązków: aby wydajnie korzystać z zasobów klastra, ustaw ograniczenia udostępniane przez użytkownika w celu wydajnego równoważenia obciążenia kontenerów w węzłach lub hostach, a także zazawodności przed błędami, zapewniając wysoką opóźnienie.

Koncepcje klastra i harmonogramu są ściśle powiązane, dlatego produkty udostępniane przez różnych dostawców często udostępniają oba zestawy funkcji. Na poniższej liście przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te koordynatorzy są zwykle oferowane w chmurach publicznych, takich jak platforma Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

|     |   |
|:---:|---|
| **Kubernetes** <br> ![obraz logo Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt "open source", który oferuje funkcje, które są przeznaczone dla zakresu od infrastruktury klastra i planowania kontenera do organizowania możliwości. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji między klastrami hostów. <br><br> *Kubernetes* zapewnia infrastrukturę skoncentrowaną na kontenerach, która grupuje kontenery aplikacji w jednostki logiczne do łatwego zarządzania i odnajdywania. <br><br> *Kubernetes* jest w systemie Linux, mniej dojrzały w systemach Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![obraz logo usługi Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Korzystanie z koordynatorów opartych na kontenerach w Microsoft Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry Docker i wsparcie w zakresie aranżacji, w tym Microsoft Azure, Amazon EC2 Container Service i Google Container Engine. Microsoft Azure zapewnia obsługę klastrów platformy Docker i programu Orchestrator za pomocą usługi Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes Service

Klastry Kubernetes pule wielu hostów platformy Docker i uwidaczniają je jako pojedyncze wirtualne hosty platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalować je z dowolną liczbą wystąpień kontenerów. Klaster będzie obsługiwał wszystkie złożone instalacje administracyjne, takie jak skalowalność, kondycja i tak dalej.

AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji kontenerowych. Dzięki zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu "open source" AKS umożliwia korzystanie z istniejących umiejętności lub narysowanie dużej i rosnącej treści wiedzy społecznościowej w celu wdrażania aplikacji opartych na kontenerach i zarządzania nimi na Microsoft Azure .

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi typu "open source" i technologii platformy Docker przeznaczonych dla platformy Azure. Uzyskasz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierasz rozmiar, liczbę hostów i narzędzia programu Orchestrator, a AKS obsługuje wszystkie inne.

![Diagram przedstawiający strukturę klastra Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Rysunek 4-24**. Uproszczona struktura i topologia klastra Kubernetes

Na rysunku 4-24 można zobaczyć strukturę klastra Kubernetes, w którym węzeł główny (VM) kontroluje większość koordynacji klastra i można wdrożyć kontenery w pozostałej części węzłów, które są zarządzane jako jedna pula z punktu aplikacji, i zezwala na t jednostka organizacyjna do skalowania do tysięcy lub nawet dziesiątki tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla Kubernetes

W środowisku programistycznym program [Docker ogłoszony w lipcu 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) , który Kubernetes może również działać na jednym komputerze deweloperskim (Windows 10 lub macOS), po prostu instalując program [Docker Desktop](https://docs.docker.com/install/). Później można wykonać wdrożenie w chmurze (AKS) w celu przeprowadzenia dalszych testów integracji, jak pokazano na rysunku 4-25.

![Diagram przedstawiający Kubernetes na komputerze deweloperskim wdrożony w AKS](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Rysunek 4-25**. Uruchamianie Kubernetes na komputerze deweloperskim i w chmurze

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z AKS, należy wdrożyć klaster AKS z poziomu Azure Portal lub przy użyciu interfejsu wiersza polecenia. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [wdrażanie klastra usługi Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nie są naliczane opłaty za żadne oprogramowanie instalowane domyślnie w ramach usługi AKS. Wszystkie opcje domyślne są implementowane za pomocą oprogramowania open source. AKS jest dostępny dla wielu maszyn wirtualnych na platformie Azure. Opłata jest naliczana tylko za wybrane wystąpienia obliczeniowe, a także dla innych użytych zasobów infrastruktury, takich jak magazyn i sieć. Nie są naliczane opłaty przyrostowe za AKS.

Domyślną opcją wdrożenia produkcyjnego dla Kubernetes jest użycie wykresów Helm, które zostały wprowadzone w następnej sekcji.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z użyciem wykresów Helm do klastrów Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można użyć oryginalnego narzędzia interfejsu wiersza polecenia polecenia kubectl. exe przy użyciu plików wdrożenia na podstawie formatu natywnego (pliki YAML), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji Kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się korzystanie z [Helm](https://helm.sh/).

Wykresy Helm ułatwiają Definiowanie, wersję, instalowanie, udostępnianie, Uaktualnianie lub wycofywanie nawet najbardziej złożonej aplikacji Kubernetes.

Ponadto zaleca się użycie Helm, ponieważ dodatkowe środowiska Kubernetes na platformie Azure, takie jak [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach Helm.

Helm jest obsługiwany przez firmę [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) — we współpracy z firmą Microsoft, Google, Bitnami i społecznością współautora Helm.

Aby uzyskać więcej informacji o implementacji na wykresach Helm i Kubernetes, zapoznaj się z [wykresem using Helm, aby wdrożyć eShopOnContainers do AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) post.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Użyj Azure Dev Spaces dla cyklu życia aplikacji Kubernetes

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie i iteracyjne środowisko programistyczne Kubernetes dla zespołów. W przypadku minimalnej konfiguracji maszyny deweloperskiej możesz iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Programuj na komputerach z systemem Windows, Mac lub Linux, używając znanych narzędzi, takich jak Visual Studio, Visual Studio Code czy wiersz polecenia.

Jak wspomniano, Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Azure Dev Spaces ułatwia zespołom programistycznym wydajniejszą pracę w Kubernetes, ponieważ umożliwia szybkie iteracyjne i debugowanie kodu bezpośrednio w globalnym klastrze Kubernetes na platformie Azure za pomocą programu Visual Studio 2019 lub Visual Studio Code. Ten klaster Kubernetes na platformie Azure jest udostępnionym zarządzanym klastrem Kubernetes, dzięki czemu zespół może wspólnie współpracować. Możesz opracować swój kod w izolacji, a następnie wdrożyć go w klastrze globalnym i przeprowadzić kompleksowe testowanie z innymi składnikami bez replikowania lub makietowania zależności.

Jak pokazano na rysunku 4-26, najbardziej różnicowa funkcja w Azure Dev Spaces jest możliwością tworzenia "spacji", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze.

![Diagram przedstawiający użycie wielu spacji w Azure Dev Spaces.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Rysunek 4-26**. Używanie wielu spacji w Azure Dev Spaces

W zasadzie można skonfigurować udostępnione miejsce na platformie Azure. Każdy deweloper może skupić się na części aplikacji i może iteracyjnie opracować kod poprzedzający zatwierdzenie w obszarze deweloperskim, który zawiera już wszystkie inne usługi i zasoby w chmurze, od których zależą te scenariusze. Zależności są zawsze aktualne, a deweloperzy pracują w sposób odzwierciedlający środowisko produkcyjne.

Azure Dev Spaces zawiera koncepcję obszaru, która pozwala na współdziałanie z izolacją względną i bez obaw o rozdzielenie pracy zespołu. Każdy obszar dev jest częścią struktury hierarchicznej, która umożliwia przesłonięcie jednej mikrousługi (lub wielu) z "górnego" głównego obszaru deweloperskiego z własną mikrousługą pracy w toku.

Ta funkcja jest oparta na prefiksach adresów URL, więc w przypadku używania dowolnego prefiksu obszaru dev w adresie URL żądanie jest obsługiwane z mikrousługi docelowej, jeśli istnieje w przestrzeni dev, w przeciwnym razie jest przekazywane do pierwszego wystąpienia mikrousługi docelowej, która znajduje się w hierarchii , ostatecznie przechodzenie do głównego miejsca deweloperskiego w górnej części.

Aby uzyskać praktyczny widok w konkretnym przykładzie, zobacz [stronę typu wiki eShopOnContainers na Azure dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces).

Aby uzyskać więcej informacji, zapoznaj się z artykułem [opracowywanie zespołu w programie Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** Oficjalna lokacja. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Poprzednie](resilient-high-availability-microservices.md)
>[dalej](../docker-application-development-process/index.md)
