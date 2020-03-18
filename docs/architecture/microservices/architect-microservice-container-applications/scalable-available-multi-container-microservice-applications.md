---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Poznaj opcje organizowania mikrousług i aplikacji wielokontenerowych w celu zapewnienia wysokiej skalowalności i dostępności oraz możliwości usługi Azure Dev Spaces podczas opracowywania cyklu życia aplikacji Kubernetes.
ms.date: 01/30/2020
ms.openlocfilehash: ea204941a461794fbeeb2482aa11973b79437027
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628504"
---
# <a name="orchestrate-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Za pomocą koordynatorów dla aplikacji gotowych do produkcji jest niezbędna, jeśli aplikacja jest oparta na mikrousługach lub po prostu podzielić na wiele kontenerów. Jak wprowadzono wcześniej w podejściu opartym na mikrousługach, każda mikrousługa jest właścicielem swojego modelu i danych, dzięki czemu będzie autonomiczna z punktu widzenia rozwoju i wdrażania. Ale nawet jeśli masz bardziej tradycyjną aplikację, która składa się z wielu usług (takich jak SOA), będziesz mieć również wiele kontenerów lub usług obejmujących jedną aplikację biznesową, które muszą zostać wdrożone jako system rozproszony. Tego rodzaju systemy są złożone do skalowania w sposób skalowany i zarządzania; w związku z tym absolutnie potrzebujesz koordynatora, jeśli chcesz mieć gotowe do produkcji i skalowalne aplikacji wielokontenerowej.

Rysunek 4-23 ilustruje wdrożenie w klastrze aplikacji składającej się z wielu mikrousług (kontenerów).

![Diagram przedstawiający złożone aplikacje platformy Docker w klastrze.](./media/scalable-available-multi-container-microservice-applications/composed-docker-applications-cluster.png)

**Rysunek 4-23**. Skupisko kontenerów

Użyj jednego kontenera dla każdego wystąpienia usługi. Kontenery platformy Docker są "jednostki wdrożenia", a kontener jest wystąpieniem platformy Docker. Host obsługuje wiele kontenerów. Wygląda na to logiczne podejście. Ale jak obsługiwać równoważenie obciążenia, routingu i organizowanie tych złożonych aplikacji?

Zwykły aparat platformy Docker w pojedynczych hostach platformy Docker spełnia potrzeby zarządzania wystąpieniami pojedynczego obrazu na jednym hoście, ale nie jest krótki, jeśli chodzi o zarządzanie wieloma kontenerami wdrożonymi na wielu hostach dla bardziej złożonych aplikacji rozproszonych. W większości przypadków potrzebna jest platforma zarządzania, która automatycznie uruchamia kontenery, skalowanie kontenerów z wieloma wystąpieniami na obraz, zawiesza je lub zamyka w razie potrzeby, a najlepiej także kontroluje sposób uzyskiwania dostępu do zasobów, takich jak sieć i dane Magazynu.

Aby wyjść poza zarządzanie poszczególnych kontenerów lub bardzo prostych złożonych aplikacji i przejść w kierunku większych aplikacji przedsiębiorstwa z mikrousług, należy zwrócić się do platform aranżacji i klastrowania.

Z punktu widzenia architektury i rozwoju, jeśli budujesz duże przedsiębiorstwo składające się z aplikacji opartych na mikrousługach, ważne jest, aby zrozumieć następujące platformy i produkty obsługujące zaawansowane scenariusze:

**Klastry i koordynatorów.** Gdy trzeba skalować w sposób skalowalny aplikacji na wielu hostach platformy Docker, jak wtedy, gdy aplikacja oparta na dużych mikrousług, ważne jest, aby móc zarządzać wszystkimi tymi hostami jako pojedynczy klaster przez abstrakcję złożoności platformy źródłowej. To, co klastry kontenerów i koordynatorów zapewniają. Kubernetes jest przykładem koordynatora i jest dostępny na platformie Azure za pośrednictwem usługi Azure Kubernetes Service.

**Pracownikom.** *Planowanie* oznacza możliwość uruchamiania kontenerów w klastrze przez administratora, dzięki czemu zapewniają one również interfejsu administracyjnego. Harmonogram klastra ma kilka obowiązków: efektywne korzystanie z zasobów klastra, ustawianie ograniczeń oferowanych przez użytkownika, efektywne równoważenie obciążenia kontenerów między węzłami lub hostami oraz niezawodne korzystanie z błędów przy jednoczesnym zapewnieniu wysokiej jakości Dostępność.

Pojęcia klastra i harmonogramu są ściśle powiązane, więc produkty dostarczane przez różnych dostawców często zapewniają oba zestawy możliwości. Na poniższej liście przedstawiono najważniejsze opcje platformy i oprogramowania dla klastrów i harmonogramów. Te koordynatory są zazwyczaj oferowane w chmurach publicznych, takich jak Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania do klastrowania kontenerów, aranżacji i planowania

|     |   |
|:---:|---|
| **Kubernetes** <br> ![Obraz logo Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) to produkt typu open source, który udostępnia funkcje, które wahają się od infrastruktury klastra i planowania kontenerów do aranżowania możliwości. Umożliwia automatyzację wdrażania, skalowania i operacji kontenerów aplikacji w klastrach hostów. <br><br> *Kubernetes* zapewnia infrastrukturę zorientowaną na kontenery, która grupuje kontenery aplikacji w jednostki logiczne w celu łatwego zarządzania i odnajdywania. <br><br> *Kubernetes* jest dojrzały w Linuksie, mniej dojrzały w systemie Windows. |
| **Azure Kubernetes Service (AKS)** <br> ![Obraz logo usługi Azure Kubernetes.](./media/scalable-available-multi-container-microservice-applications/azure-kubernetes-service-logo.png) | [AKS](https://azure.microsoft.com/services/kubernetes-service/) to zarządzana usługa aranżacji kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie, wdrażanie i operacje klastra Kubernetes. |

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Korzystanie z koordynatorów opartych na kontenerach na platformie Microsoft Azure

Kilku dostawców chmury oferuje obsługę kontenerów platformy Docker oraz klastry platformy Docker i obsługę aranżacji, w tym microsoft azure, amazon EC2 Container Service i Google Container Engine. Platforma Microsoft Azure zapewnia obsługę klastra platformy Docker i koordynatora za pośrednictwem usługi Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Korzystanie z usługi Azure Kubernetes

Klastra Kubernetes puluje wiele hostów platformy Docker i udostępnia je jako jeden wirtualny host platformy Docker, dzięki czemu można wdrożyć wiele kontenerów w klastrze i skalowania w sposób skalowania w sposób z dowolną liczbą wystąpień kontenera. Klaster będzie obsługiwać wszystkie złożone instalacji wodociągowej zarządzania, takich jak skalowalność, kondycja i tak dalej.

Usługa AKS umożliwia uproszczenie tworzenia, konfigurowania i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania aplikacji konteneryzowanych. Korzystając ze zoptymalizowanej konfiguracji popularnych narzędzi do planowania i aranżacji typu open source, usługa AKS umożliwia korzystanie z istniejących umiejętności lub korzystanie z dużej i rosnącej wiedzy społeczności w celu wdrażania aplikacji opartych na kontenerach na platformie Microsoft Azure i zarządzania nimi .

Usługa Azure Kubernetes optymalizuje konfigurację popularnych narzędzi i technologii typu docker klastrowania typu open source specjalnie dla platformy Azure. Otrzymujesz otwarte rozwiązanie, które oferuje przenośność zarówno dla kontenerów, jak i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a AKS obsługuje wszystko inne.

![Diagram przedstawiający strukturę klastra Kubernetes.](./media/scalable-available-multi-container-microservice-applications/kubernetes-cluster-simplified-structure.png)

**Rysunek 4-24**. Uproszczona struktura i topologia klastra Kubernetes

Na rysunku 4-24 można zobaczyć strukturę klastra Kubernetes, gdzie węzeł główny (VM) kontroluje większość koordynacji klastra i można wdrożyć kontenery do reszty węzłów, które są zarządzane jako pojedyncza pula z punktu widzenia aplikacji i umożliwia skalować do tysięcy, a nawet dziesiątek tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla Kubernetes

W środowisku programistycznym [Firma Docker ogłosiła w lipcu 2018 r.,](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) że kubernetes może również działać na jednym komputerze deweloperskim (Windows 10 lub macOS), po prostu instalując [program Docker Desktop](https://docs.docker.com/install/). Później można wdrożyć w chmurze (AKS) do dalszych testów integracji, jak pokazano na rysunku 4-25.

![Diagram przedstawiający Kubernetes a następnie wdrożony w aksie](./media/scalable-available-multi-container-microservice-applications/kubernetes-development-environment.png)

**Rysunek 4-25**. Uruchamianie Kubernetes w maszynie deweloperskiej i chmurze

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do usługi Azure Kubernetes Service (AKS)

Aby rozpocząć korzystanie z usługi AKS, można wdrożyć klaster AKS z witryny Azure portal lub przy użyciu interfejsu ósemki. Aby uzyskać więcej informacji na temat wdrażania klastra Kubernetes na platformie Azure, zobacz [Wdrażanie klastra usługi Azure Kubernetes Service (AKS).](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

Nie ma żadnych opłat za oprogramowanie zainstalowane domyślnie jako część Usługi AKS. Wszystkie opcje domyślne są implementowane za pomocą oprogramowania open source. Usługa AKS jest dostępna dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wybrane wystąpienia obliczeniowe, a także inne zużywane zasoby infrastruktury, takie jak magazyn i sieć. Nie ma żadnych opłat przyrostowych dla samego Usługi AKS.

Domyślną opcją wdrażania produkcyjnego dla kubernetes jest użycie wykresów Helm, który jest wprowadzony w następnej sekcji.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie z wykresami Helma w klastrach Kubernetes

Podczas wdrażania aplikacji w klastrze Kubernetes można użyć oryginalnego narzędzia interfejsów CLI kubectl.exe przy użyciu plików wdrażania opartych na formacie macierzystym (plików yaml), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji Kubernetes, takich jak podczas wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się użycie [Helm](https://helm.sh/).

Helm Charts pomaga zdefiniować, wersja, zainstalować, udostępnić, uaktualnić lub wycofać nawet najbardziej złożonych aplikacji Kubernetes.

Idąc dalej, użycie helm jest również zalecane, ponieważ dodatkowe środowiska Kubernetes na platformie Azure, takie jak [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) są również oparte na wykresach Helm.

Helm jest utrzymywany przez [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) - we współpracy z Firmami Microsoft, Google, Bitnami i społecznością współautorów Helm.

Aby uzyskać więcej informacji o implementacji wykresów Helm i Kubernetes, zobacz [za pomocą wykresów helm do wdrażania eShopOnContainers do AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)) post.

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Korzystanie z platformy Azure Dev Spaces w cyklu życia aplikacji Kubernetes

[Usługa Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne kubernetes dla zespołów. W przypadku minimalnej konfiguracji maszyny deweloperskiej możesz iteracyjnie uruchamiać i debugować kontenery bezpośrednio w usłudze Azure Kubernetes Service (AKS). Programuj na komputerach z systemem Windows, Mac lub Linux, używając znanych narzędzi, takich jak Visual Studio, Visual Studio Code czy wiersz polecenia.

Jak wspomniano, usługi Azure Dev Spaces używa wykresów Helm podczas wdrażania aplikacji opartych na kontenerach.

Usługa Azure Dev Spaces pomaga zespołom programistycznym zwiększyć produktywność w programie Kubernetes, ponieważ umożliwia szybkie iterowanie i debugowanie kodu bezpośrednio w globalnym klastrze Kubernetes na platformie Azure, po prostu przy użyciu programu Visual Studio 2019 lub kodu programu Visual Studio. Ten klaster Kubernetes na platformie Azure jest udostępnionym zarządzanym klastrem Kubernetes, dzięki czemu twój zespół może współpracować. Można opracować kod w izolacji, a następnie wdrożyć do klastra globalnego i zrobić testowanie end-to-end z innymi składnikami bez replikowania lub makiety zależności.

Jak pokazano na rysunku 4-26, najbardziej zróżnicowaną funkcją w usłudze Azure Dev Spaces jest możliwość tworzenia "spacji", które można uruchomić zintegrowane z resztą globalnego wdrożenia w klastrze.

![Diagram przedstawiający użycie wielu spacji w przestrzeniach deweloperskich platformy Azure.](./media/scalable-available-multi-container-microservice-applications/use-multiple-spaces-azure-dev.png)

**Rysunek 4-26**. Korzystanie z wielu spacji w przestrzeniach deweloperskich platformy Azure

Zasadniczo można skonfigurować współużytkowane miejsce dewelopera na platformie Azure. Każdy deweloper może skupić się wyłącznie na swojej części aplikacji oraz iteracyjnie tworzyć wstępnie zatwierdzony kod w przestrzeni deweloperskiej zawierającej już wszystkie pozostałe usługi i zasoby w chmurze, od których zależą jego scenariusze. Zależności są zawsze aktualne, a deweloperzy pracują w sposób odzwierciedlający środowisko produkcyjne.

Usługa Azure Dev Spaces udostępnia koncepcję przestrzeni, która umożliwia pracę w względnej izolacji i bez obawy o zerwanie pracy zespołu. Każda przestrzeń dewelopera jest częścią struktury hierarchicznej, która umożliwia zastąpienie jednej mikrousługi (lub wielu) z "górnej" przestrzeni dewelopera głównego, z własną mikrousługą pracy w toku.

Ta funkcja jest oparta na prefiksach adresu URL, więc w przypadku korzystania z dowolnego prefiksu miejsca dewelopera w adresie URL, żądanie jest obsługiwane z mikrousługi docelowej, jeśli istnieje w przestrzeni dewelopera, w przeciwnym razie jest przekazywane do pierwszego wystąpienia mikrousługi docelowej znalezionej w hierarchii , w końcu dotarcie do przestrzeni dewelopera mistrza na górze.

Aby uzyskać praktyczny widok na konkretny przykład, zobacz [stronę wiki eShopOnContainers na platformie Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces).

Aby uzyskać więcej informacji, zapoznaj się z artykułem na [temat tworzenia zespołu za pomocą platformy Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do usługi Azure Kubernetes Service (AKS)** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Przestrzenie deweloperów platformy Azure** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes (Kubernetes)** Oficjalna strona. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Poprzedni](resilient-high-availability-microservices.md)
>[następny](../docker-application-development-process/index.md)
