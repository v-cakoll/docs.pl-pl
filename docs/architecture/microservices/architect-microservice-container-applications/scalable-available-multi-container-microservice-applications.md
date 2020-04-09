---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Odnajduj opcje organizowania mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności oraz możliwości usługi Azure Dev Spaces podczas opracowywania cyklu życia aplikacji kubernetes.
ms.date: 01/30/2020
ms.openlocfilehash: 8a67235109bed806caa7d9caa2bc26fd4fe9daca
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988911"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Za pomocą orchestrators dla aplikacji gotowych do produkcji jest niezbędne, jeśli aplikacja jest oparta na mikrousług lub po prostu podzielić na wiele kontenerów. Zgodnie z wcześniejszym wprowadzeniem w podejściu opartym na mikrousługach każda mikrousługa jest właścicielem swojego modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia rozwoju i wdrażania. Ale nawet jeśli masz bardziej tradycyjną aplikację, która składa się z wielu usług (takich jak SOA), będziesz mieć również wiele kontenerów lub usług składających się z jednej aplikacji biznesowej, które muszą zostać wdrożone jako system rozproszony. Tego rodzaju systemy są złożone do skalowania w poziomie i zarządzania; w związku z tym absolutnie potrzebujesz koordynatora, jeśli chcesz mieć gotową do produkcji i skalowalną aplikację wielokontensjalną.

Rysunek 4-23 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Diagram przedstawiający skomponowane aplikacje platformy Docker w klastrze.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Rysunek 4-23**. Klaster kontenerów

Użyj jednego kontenera dla każdego wystąpienia usługi. Kontenery platformy Docker są "jednostkami wdrożenia", a kontener jest wystąpieniem platformy Docker. Host obsługuje wiele kontenerów. Wygląda to na logiczne podejście. Ale jak obsługiwać równoważenia obciążenia, routingu i organizowania tych złożonych aplikacji?

Zwykły aparat platformy Docker w pojedynczych hostach platformy Docker spełnia potrzeby zarządzania wystąpieniami pojedynczego obrazu na jednym hoście, ale nie jest w stanie zarządzać wieloma kontenerami wdrożonymi na wielu hostach dla bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która automatycznie uruchomi kontenery, skalowaj w poziomie kontenerów z wieloma wystąpieniami na obraz, zawiesi je lub zamknie w razie potrzeby, a najlepiej również kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieć i magazyn danych.

Aby wyjść poza zarządzanie poszczególnych kontenerów lub bardzo proste aplikacje składa i przejść do większych aplikacji korporacyjnych z mikrousług, należy zwrócić się do platform aranżacji i klastrowania.

Z punktu widzenia architektury i rozwoju, jeśli budujesz duże przedsiębiorstwo składające się z aplikacji opartych na mikrousługach, ważne jest, aby zrozumieć następujące platformy i produkty, które obsługują zaawansowane scenariusze:

**Klastry i koordynatorzy.** Gdy trzeba skalować w poziomie aplikacji w wielu hostach platformy Docker, jak wtedy, gdy aplikacja oparta na dużych mikrousługach, jest bardzo ważne, aby móc zarządzać wszystkimi tymi hostami jako pojedynczy klaster, abstrakcjonowanie złożoności podstawowej platformy. To, co zapewniają klastry kontenerów i orchestrators. Kubernetes jest przykładem koordynatora i jest dostępny na platformie Azure za pośrednictwem usługi Azure Kubernetes.

**Pracownikom.** *Planowanie* oznacza, że administrator może uruchamiać kontenery w klastrze, aby również zapewnić interfejs użytkownika. Harmonogram klastra ma kilka obowiązków: aby efektywnie korzystać z zasobów klastra, ustawić ograniczenia dostarczone przez użytkownika, skutecznie równoważyć obciążenia kontenerów między węzłami lub hostami i być niezawodne przed błędami, zapewniając jednocześnie wysoką dostępność.

Pojęcia klastra i harmonogramu są ściśle powiązane, więc produkty dostarczane przez różnych dostawców często zapewniają oba zestawy możliwości. Na poniższej liście przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te orchestrators są zazwyczaj oferowane w chmurach publicznych, takich jak Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Obraz logo Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt typu open source, który zapewnia funkcje, które waha się od infrastruktury klastra i planowania kontenerów do możliwości aranżacji. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji w klastrach hostów. <br><br> *Kubernetes* zapewnia kontenerozajęzykową, która grupuje kontenery aplikacji w jednostki logiczne w celu łatwego zarządzania i odnajdywania. <br><br> *Kubernetes* jest dojrzały w Linuksie, mniej dojrzały w systemie Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![Obraz logo usługi Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [Usługa AKS](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Korzystanie z koordynatorów opartych na kontenerach na platformie Microsoft Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry platformy Docker i obsługę aranżacji, w tym microsoft azure, usługę kontenerów Amazon EC2 i aparat kontenerów Google. Platforma Microsoft Azure zapewnia obsługę klastra i koordynatora platformy Docker za pośrednictwem usługi Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes

Klaster usługi Kubernetes buforuje wiele hostów platformy Docker i udostępnia je jako pojedynczy wirtualny host platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalować w poziomie z dowolną liczbą wystąpień kontenerów. Klaster będzie obsługiwać wszystkie złożone instalacji wodno-kanalizacyjne zarządzania, takich jak skalowalność, kondycja i tak dalej.

Usługa AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Korzystając ze zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu open source, usługa AKS umożliwia korzystanie z istniejących umiejętności lub korzystanie z dużej i rosnącej wiedzy specjalistycznej społeczności w celu wdrażania aplikacji opartych na kontenerach i zarządzania nimi na platformie Microsoft Azure.

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi i technologii typu open source klastrowania platformy Docker specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia aranżatora, a AKS obsługuje wszystko inne.

![Diagram przedstawiający strukturę klastra Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Rysunek 4-24**. Uproszczona struktura i topologia klastra Kubernetes

Na rysunku 4-24 można zobaczyć strukturę klastra Kubernetes, gdzie węzeł główny (VM) kontroluje większość koordynacji klastra i można wdrożyć kontenery do pozostałych węzłów, które są zarządzane jako pojedyncza pula z punktu widzenia aplikacji i umożliwia skalowanie do tysięcy lub nawet dziesiątki tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla kubernetes

W środowisku deweloperskim [docker ogłosił w lipcu 2018,](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) że kubernetes może również działać na jednym komputerze deweloperskim (Windows 10 lub macOS), po prostu instalując [program Docker Desktop](https://docs.docker.com/install/). Później można wdrożyć w chmurze (AKS) do dalszych testów integracji, jak pokazano na rysunku 4-25.

![Diagram przedstawiający kubernetes na komputerze deweloperskim, a następnie wdrożony w u usługi AKS](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Rysunek 4-25**. Uruchamianie kubernetes na komputerze deweloperskim i chmurze

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z usługi AKS, należy wdrożyć klaster AKS z witryny Azure portal lub przy użyciu interfejsu wiersza polecenia. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [Wdrażanie klastra usługi Azure Kubernetes (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Nie ma żadnych opłat za oprogramowanie zainstalowane domyślnie w ramach usługi AKS. Wszystkie opcje domyślne są implementowane z oprogramowaniem open source. Usługa AKS jest dostępna dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wybraną instancję obliczeniową, a także za inne używane zasoby infrastruktury, takie jak magazynowanie i sieć. Nie ma żadnych opłat przyrostowych dla samego AKS.

Domyślną opcją wdrożenia produkcyjnego dla usługi Kubernetes jest użycie wykresów helm, które zostały wprowadzone w następnej sekcji.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z wykresami helm w klastrach Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można użyć oryginalnego narzędzia interfejsu wiersza polecenia kubectl.exe przy użyciu plików wdrażania opartych na formacie macierzystym (pliki yaml), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się użycie [helm.](https://helm.sh/)

Helm Charts pomaga zdefiniować, wersję, zainstalować, udostępnić, uaktualnić lub wycofać nawet najbardziej złożoną aplikację Kubernetes.

Idąc dalej, użycie helmu jest również zalecane, ponieważ dodatkowe środowiska kubernetes na platformie Azure, takie jak [usługi Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach helm.

Helm jest utrzymywany przez [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) - we współpracy z Microsoft, Google, Bitnami i społecznością współpracowników Helm.

Aby uzyskać więcej informacji na temat implementacji wykresów helm i Kubernetes, zobacz [Za pomocą wykresów helm do wdrażania eShopOnContainers do AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) post.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Używanie usługi Azure Dev Spaces dla cyklu życia aplikacji Kubernetes

[Usługa Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne Kubernetes dla zespołów. W przypadku minimalnej konfiguracji maszyny deweloperskiej możesz iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Programuj na komputerach z systemem Windows, Mac lub Linux, używając znanych narzędzi, takich jak Visual Studio, Visual Studio Code czy wiersz polecenia.

Jak wspomniano, usługa Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Usługa Azure Dev Spaces pomaga zespołom deweloperskim zwiększyć produktywność w witrynie Kubernetes, ponieważ umożliwia szybkie iterację i debugowanie kodu bezpośrednio w globalnym klastrze kubernetes na platformie Azure, po prostu używając programu Visual Studio 2019 lub kodu programu Visual Studio. Ten klaster Kubernetes na platformie Azure jest udostępnionym klastrem kubernetes zarządzanym, dzięki czemu zespół może współpracować ze sobą. Można opracować kod w izolacji, a następnie wdrożyć w klastrze globalnym i zrobić end-to-end testowania z innymi składnikami bez replikowania lub mocking się zależności.

Jak pokazano na rysunku 4-26, najbardziej zróżnicowaną funkcją w usłudze Azure Dev Spaces jest możliwość tworzenia "przestrzeni", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze.

![Diagram przedstawiający użycie wielu spacji w przestrzeniach deweloperów platformy Azure.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Rysunek 4-26**. Korzystanie z wielu spacji w przestrzeniach deweloperskich platformy Azure

Zasadniczo można skonfigurować udostępnionego obszaru deweloperów na platformie Azure. Każdy deweloper może skupić się wyłącznie na swojej części aplikacji oraz iteracyjnie tworzyć wstępnie zatwierdzony kod w przestrzeni deweloperskiej zawierającej już wszystkie pozostałe usługi i zasoby w chmurze, od których zależą jego scenariusze. Zależności są zawsze aktualne, a deweloperzy pracują w sposób odzwierciedlający środowisko produkcyjne.

Usługa Azure Dev Spaces udostępnia koncepcję miejsca, która umożliwia pracę w względnej izolacji i bez obawy przed przerwaniem pracy zespołu. Każda przestrzeń dewelopera jest częścią struktury hierarchicznej, która pozwala zastąpić jedną mikrousługę (lub wiele), z "górnej" przestrzeni dewelopera głównego, z własnej mikrousługi pracy w toku.

Ta funkcja jest oparta na prefiksach adresu URL, więc podczas korzystania z dowolnego prefiksu przestrzeni dev w adresie URL żądanie jest obsługiwane z mikrousługi docelowej, jeśli istnieje w przestrzeni deweloperskiej, w przeciwnym razie jest przekazywane do pierwszego wystąpienia mikrousługi docelowej znalezionej w hierarchii, ostatecznie uzyskując do głównego miejsca dewelopera u góry.

Aby uzyskać praktyczny widok na konkretny przykład, zobacz [stronę wiki eShopOnContainers w usłudze Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces).

Aby uzyskać więcej informacji, zapoznaj się z artykułem [dotyczącymi rozwoju zespołu za pomocą usługi Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Miejsca deweloperów platformy Azure** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Okręg wyborczy Kubernetes** Oficjalna strona. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Poprzedni](resilient-high-availability-microservices.md)
>[następny](../docker-application-development-process/index.md)
