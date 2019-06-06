---
title: Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności
description: Odkryj opcje do organizowania mikrousług i wielokontenerowych aplikacji pod kątem wysokiej skalowalności i dostępności oraz możliwości usługi Azure Dev miejsca do magazynowania podczas tworzenia cyklem życia aplikacji platformy Kubernetes.
ms.date: 09/20/2018
ms.openlocfilehash: a0f7efa4b21aedfb574659df283adc65741cefdb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690499"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności

Przy użyciu koordynatorów aplikacji gotowych do produkcji jest istotne, jeśli aplikacja jest oparta na mikrousługach lub po prostu podzielone między wiele kontenerów. Jak wprowadzona wcześniej w podejściu opartych na mikrousługach, każda mikrousługa jest właścicielem jej modelu i danych tak, aby go autonomicznego od środowisk programowania i wdrażania punktu widzenia. Ale nawet w przypadku bardziej tradycyjny aplikację która składa się z wielu usług (np. SOA), będziesz również mieć wiele kontenerów i usług wchodzących w skład aplikacji biznesowej, które muszą zostać wdrożone jako rozproszony system. Tego rodzaju systemy są złożone i skalowanie w poziomie i zarządzać; w związku z tym bezwzględnie konieczne koordynatora, jeśli chcesz mieć aplikację obsługującą wiele kontenerów gotowe do produkcji i skalowalny.

Rysunek 4-23 przedstawiono wdrożenie w klastrze aplikacji składających się z wielu mikrousług (kontenery).

![Złożone aplikacje platformy Docker w klastrze: Możesz użyć jednego kontenera dla każdego wystąpienia usługi. Kontenery platformy docker są "jednostki wdrożenia" i kontener jest wystąpienie hosta Docker.A obsługuje wiele kontenerów](./media/image23.png)

**Rysunek 4-23**. Klaster kontenerów

Wygląda jak algorytmu. Ale jak możesz obsługi równoważeniem obciążenia, routingu i organizowanie te składają się aplikacje?

Zwykły aparat platformy Docker w jednym hostów platformy Docker spełnia potrzeby zarządzania wystąpieniami pojedynczy obraz na jednym hoście, ale znajduje się krótki w przypadku zarządzania wieloma kontenerami wdrażane na wielu hostach w przypadku bardziej złożonych aplikacji rozproszonych. W większości przypadków należy to platforma zarządzania, która będzie automatycznie uruchom kontenery, kontenery skalowalnego w poziomie za pomocą wielu wystąpień na obrazie, zawieszać je lub wyłączać je w razie i najlepiej także kontrolować sposób uzyskiwania dostępu do zasobów, takich jak sieci i danych Magazyn.

Czegoś Zarządzanie poszczególne kontenery lub bardzo proste aplikacje złożone i Przenieś kierunku większych aplikacje dla przedsiębiorstw przy użyciu mikrousług, należy go włączyć do aranżacji i klastrowanie platform.

Z architektury i projektowania punktu widzenia Jeśli tworzysz duże przedsiębiorstwo składa się z aplikacji opartych na mikrousługach, warto zapoznać się z następujących platform i produktów, które obsługuje zaawansowane scenariusze:

**Klastry i koordynatorów.** Kiedy należy skalować aplikacje na wielu hostach Docker, jak w przypadku dużych aplikacji opartych na mikrousługach, koniecznie będzie można zarządzać tymi hostami jako pojedynczy klaster, zapewniając abstrakcyjność złożoność podstawowej platformy. To, co zapewnia klastry kontenerów i koordynatorów. Kubernetes jest przykładem koordynatora, a jest dostępna w systemie Azure za pomocą usługi Azure Kubernetes Service.

**Transfery danych.** *Planowanie* oznacza, że mają możliwość, aby administrator mógł Uruchom kontenery w klastrze, dzięki czemu zapewniają także interfejs użytkownika. Harmonogram klastra ma kilka obowiązki: wydajnie korzystać z zasobów klastra, aby ustawić ograniczenia podana przez użytkownika, do wydajne Równoważenie obciążenia kontenerów w węzłach lub hosty i być odporne na błędy przy jednoczesnym zapewnieniu wysokiego dostępność.

Pojęcia związane z klastra i harmonogramu są ściśle powiązane, dlatego produktów dostarczane przez różnych dostawców często podać oba zestawy funkcji. Na poniższej liście przedstawiono najważniejsze platformy i opcje oprogramowania, które mają dla klastrów i transfery danych. Te koordynatorów zazwyczaj są oferowane w chmurach publicznych, takich jak platforma Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Platformy oprogramowania dla kontenera, klastrowanie, aranżację i planowanie

### <a name="kubernetes"></a>Kubernetes

![Logo rozwiązania Kubernetes](./media/image24.png)

> [*Kubernetes* ](https://kubernetes.io/) to produkt typu open source, który zapewnia funkcje z zakresu od infrastruktury klastra i kontenerów harmonogramów, organizowanie możliwości. Dzięki temu można zautomatyzować wdrażanie, skalowanie i działanie kontenerów aplikacji w klastrach hostów.
>
> *Kubernetes* udostępnia infrastrukturę skoncentrowane na kontenera, która grupuje kontenery aplikacji w jednostki logiczne, aby ułatwić zarządzanie i odnajdywania.
>
> *Kubernetes* to dojrzała w systemie Linux, mniej dojrzałe w Windows.

### <a name="azure-kubernetes-service-aks"></a>Usługa Azure Kubernetes Service (AKS)

![Logo usługi Azure Kubernetes Service](./media/image41.png)

> [Usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) jest zarządzanej usługi organizowania kontenerów Kubernetes na platformie Azure, która upraszcza zarządzanie klastrem Kubernetes, wdrażania i operacji.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Przy użyciu koordynatorów opartych na kontenerach, w systemie Microsoft Azure

Kilku dostawców chmury oferują obsługę kontenerów platformy Docker oraz klastrów platformy Docker oraz obsługę aranżacji, w tym Microsoft Azure, Amazon EC2 Container Service i Google kontenera aparatu. Microsoft Azure oferuje platformy Docker, obsługę klastra i programu orchestrator za pomocą usługi Azure Kubernetes Service (AKS).

## <a name="using-azure-kubernetes-service"></a>Za pomocą usługi Azure Kubernetes Service

Klaster usługi Kubernetes pul wielu hostów platformy Docker i przedstawia je w postaci jednego wirtualnego hosta platformy Docker, aby umożliwić wdrażanie wielu kontenerów do klastra i skalowalnego w poziomie przy użyciu dowolnej liczby wystąpień kontenera. Klaster będzie obsługiwać wszystkie złożonego zarządzania żmudne procesy, takie jak skalowalność, kondycji i tak dalej.

AKS umożliwia uproszczenie tworzenia, konfiguracji i zarządzania klastrem maszyn wirtualnych na platformie Azure, które są wstępnie skonfigurowane do uruchamiania konteneryzowanych aplikacji. Użycie zoptymalizowanej konfiguracji popularnych narzędzi planowania i organizowania typu open source, AKS umożliwia używanie posiadanych umiejętności lub sięganie na treść duży i rosnący zasób wiedzy społeczności, wdrażanie i zarządzanie nimi opartych na kontenerach aplikacje w systemie Microsoft Azure .

Usługa Azure Kubernetes Service optymalizuje konfigurację popularnych narzędzi typu open-source klastrowania platformy Docker i technologii pod kątem platformy Azure. Uzyskujesz otwarte rozwiązanie, która oferuje przenośność kontenerów i konfiguracji aplikacji. Wybierz rozmiar, liczbę hostów i narzędzia koordynatora, a AKS zajmuje się całą resztą.

![Struktura klastra Kubernetes: Brak jednego węzła głównego, który obsługuje DNS, harmonogram, serwer proxy, itp. oraz kilka węzłów procesów roboczych, które hostują kontenery.](media/image36.png)

**Rysunek 4-24**. Uproszczoną strukturę i topologii klastra Kubernetes

Na rysunku 4 – 24 widać strukturę klastra Kubernetes, w którym węzła głównego (VM) określa większość koordynację klastra i kontenerów można wdrożyć na pozostałe węzły, które są zarządzane jako pojedynczy puli z punktu widzenia aplikacji i umożliwia y jednostki organizacyjnej, aby możliwe było skalowanie tysięcy lub nawet dziesiątków tysięcy kontenerów.

## <a name="development-environment-for-kubernetes"></a>Środowisko programistyczne dla platformy Kubernetes

W środowisku programistycznym [platformy Docker z ogłoszeniem z lipca 2018 r.](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) , Kubernetes można również uruchomić w maszynie deweloperskiej pojedynczego (system Windows 10 lub macOS), po prostu instalując [pulpitu platformy Docker](https://docs.docker.com/install/). Możesz później wdrożyć do chmury (AKS) na potrzeby dalszych badań integracji, jak pokazano na rysunku 4-25.

![Docker ogłosiła pomoc techniczna dla deweloperów maszyny dla klastrów Kubernetes na lipca "2018 r. za pomocą programu Desktop platformy Docker.](media/image37.png) 

**Rysunek 4-25**. Uruchamianie rozwiązania Kubernetes w komputerze deweloperskim i w chmurze

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Wprowadzenie do korzystania z usługi Azure Kubernetes Service (AKS) 

Aby rozpocząć, za pomocą usługi AKS, musisz wdrożyć klaster AKS z witryny Azure portal lub za pomocą interfejsu wiersza polecenia. Aby uzyskać więcej informacji o wdrażaniu klastra Kubernetes na platformie Azure, zobacz [wdrażanie klastra usługi Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nie ma żadnych opłat za oprogramowanie instalowane domyślnie w jako część usługi AKS. Wszystkie opcje domyślne są implementowane przy użyciu oprogramowania typu open source. AKS jest dostępny dla wielu maszyn wirtualnych na platformie Azure. Opłaty są naliczane tylko za wystąpienia obliczeniowe, które możesz wybrać, jak również inne użyte zasoby infrastruktury bazowej, takie jak storage i sieci. Są naliczane opłaty przyrostowe AKS sam.

Dalsze informacje o implementacji na wdrażanie w usłudze Kubernetes opartego na kubectl i oryginalnych plików .yaml, sprawdź wpis na [Konfigurowanie ramach aplikacji eShopOnContainers w usłudze AKS (usługi Azure Kubernetes Service)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Wdrażanie przy użyciu narzędzia Helm do klastrów Kubernetes

W przypadku wdrażania aplikacji w klastrze Kubernetes, służy narzędzie interfejsu wiersza polecenia oryginalnej kubectl.exe przy użyciu plików wdrożenia na podstawie formatu macierzystego (pliki .yaml), jak już wspomniano w poprzedniej sekcji. Jednak w przypadku bardziej złożonych aplikacji platformy Kubernetes, takie jak w przypadku wdrażania złożonych aplikacji opartych na mikrousługach, zaleca się używać [Helm](https://helm.sh/).

Narzędzia Helm pomaga zdefiniować wersji Zainstaluj udziału, uaktualnianie lub wycofywania nawet najbardziej złożoną aplikację platformy Kubernetes.

Idąc dalej, użycie narzędzia Helm jest również zalecana, ponieważ dodatkowych środowisk Kubernetes na platformie Azure, takich jak [miejsca do magazynowania Azure Dev](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) również są oparte na wykresów rozwiązania Helm.

Helm jest obsługiwana przez [Foundation natywnych obliczeń w chmurze (CNCF)](https://www.cncf.io/) — we współpracy z firmą Microsoft, Google, Bitnami i Helm Współautor społeczności.

Do wykonania dalszych informacji na temat planów narzędzia Helm i Kubernetes sprawdzić wpis [przy użyciu wykresów rozwiązania Helm, aby wdrażanie w ramach aplikacji eShopOnContainers usłudze AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Użyj usługi Azure Dev miejsca do magazynowania dla cyklu użytkowania Twojej aplikacji platformy Kubernetes

[Usługa Azure Dev spacje](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) zapewnia szybkie, iteracyjne środowisko programistyczne Kubernetes dla zespołów. W przypadku konfiguracji maszyny dev minimalny iteracyjne było uruchomić i debugować kontenerów bezpośrednio w usłudze Azure Kubernetes Service (AKS). Programowanie na Windows, Mac lub Linux przy użyciu znanych narzędzi, takich jak Visual Studio, Visual Studio Code lub wiersza polecenia.

Jak wspomniano wcześniej, podczas wdrażania aplikacji opartych na kontenerach Azure Dev miejsca do magazynowania korzysta z narzędzia Helm.

Usługa Azure Dev spacje pomaga zespołom programistycznym mu bardziej wydajnej pracy, na platformie Kubernetes, ponieważ pozwala na szybkie Iterowanie i debugowania kodu bezpośrednio w globalnych klastra Kubernetes na platformie Azure przy użyciu programu Visual Studio 2017 lub Visual Studio Code. Czy klastra Kubernetes na platformie Azure udostępnionej odbywa się klastra Kubernetes, dzięki czemu Twój zespół może wspólnie współpracują ze sobą. Można tworzyć kod w izolacji, a następnie wdrożenie w klastrze globalnych i end-to-end testowanie z innymi składnikami bez replikacji lub pozorowanie się zależności.

Jak pokazano na rysunku 4-26 najbardziej różnicowych funkcji w Azure Dev miejsca do magazynowania jest możliwość tworzenia miejsca do magazynowania, które można uruchomić zintegrowanego w pozostałej części globalnego wdrażania w klastrze.

![Usługa Azure Dev spacje przezroczyste mieszać i dopasowywać mikrousług w środowisku produkcyjnym z tworzenia wystąpienia kontenera, aby ułatwić testowanie nowych wersji.](media/image38.png)

**Rysunek 4-26**. Korzystanie z wielu miejsc do magazynowania w Azure Dev miejsca do magazynowania

W zasadzie można skonfigurować miejsce na udostępnionym deweloperów na platformie Azure. Każdy deweloper może skupić się na ich części aplikacji, można iteracyjne tworzenie kodu wstępnego zatwierdzenia w miejsce deweloperów, która już zawiera wszystkich innych usług i zasobów, które zależą od ich scenariuszy w chmurze. Zależności są zawsze aktualne, a deweloperzy pracują nad w sposób, który odzwierciedla produkcji.

Usługa Azure Dev spacje wprowadza pojęcie obszarem, co pozwala na pracę w izolacji względne i bez obawiać się, że przerwanie pracy zespołu. Każdą spację dev jest częścią hierarchiczna struktura, która pozwala zastąpić jedną mikrousługi (lub wielu) z obszaru głównego dev "top", przy użyciu własnych mikrousług prac w toku.

Ta funkcja jest oparta na prefiksy URL, używając dowolnego prefiksu przestrzeni dev w adresie url, żądanie jest udostępniany z mikrousług docelowy, jeśli istnieje w przestrzeni adresowej deweloperów, w przeciwnym razie jest ona przesyłana dalej do pierwszego wystąpienia mikrousług docelowej znaleziony w hierarchii , po pewnym czasie wprowadzenie do obszaru głównego dev u góry.

Możesz zobaczyć [strony typu wiki w ramach aplikacji eShopOnContainers na miejsca do magazynowania Azure Dev](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS), aby uzyskać praktyczne widok na konkretny przykład.

Aby uzyskać więcej informacji Sprawdź artykuł [programowanie zespołowe za pomocą usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do korzystania z usługi Azure Kubernetes Service (AKS)**  \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes** oficjalna witryna. \
  <https://kubernetes.io/>

>[!div class="step-by-step"]
>[Poprzednie](resilient-high-availability-microservices.md)
>[dalej](docker-application-development-process.md)
