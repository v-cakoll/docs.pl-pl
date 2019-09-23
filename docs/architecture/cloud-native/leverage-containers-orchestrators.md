---
title: Korzystanie z kontenerów i Orchestrator
description: Korzystanie z kontenerów platformy Docker i koordynatorów Kubernetes na platformie Azure
ms.date: 06/30/2019
ms.openlocfilehash: 4008a14e4db28e07d5fda0a1f175aada9ffe6734
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182882"
---
# <a name="leveraging-containers-and-orchestrators"></a>Korzystanie z kontenerów i Orchestrator

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontenery i Koordynatory zostały zaprojektowane w celu rozwiązywania problemów typowych dla podejścia do wdrożenia.

## <a name="challenges-with-monolithic-deployments"></a>Wyzwania z niemonolitycznymi wdrożeniami

Tradycyjnie większość aplikacji wdrożono jako pojedynczą jednostkę. Takie aplikacje są określane jako monolitu. To ogólne podejście do wdrażania aplikacji jako pojedyncze jednostki nawet wtedy, gdy składają się z wielu modułów lub zestawów, jest znana jako architektura monolityczna, jak pokazano na rysunku 3-1.

![Architektura monolityczna.](./media/monolithic-architecture.png)

**Rysunek 3-1**. Architektura monolityczna.

Chociaż mają zalety prostoty, monolityczne architektury mają kilka wyzwań:

### <a name="deployments"></a>Wdrożenia

Wdrożenie w aplikacjach monolitycznych zazwyczaj wymaga ponownego uruchomienia całej aplikacji, nawet jeśli jest zastępowany tylko jeden mały moduł. W zależności od liczby maszyn obsługujących aplikację może to spowodować przestoje podczas wdrożeń.

### <a name="hosting"></a>Hosting

Aplikacje monolityczne są hostowane całkowicie w wystąpieniu jednego komputera. Może to wymagać sprzętu wyższej funkcjonalności niż każdy moduł w aplikacji rozproszonej. Ponadto, jeśli jakakolwiek część aplikacji staną się wąskim gardłem, cała aplikacja musi zostać wdrożona w dodatkowych węzłach maszyn w celu skalowania w poziomie.

### <a name="environment"></a>Środowisko

Aplikacje monolityczne są zwykle wdrażane w istniejącym środowisku hostingu (system operacyjny, zainstalowane struktury itp.). To środowisko może nie być zgodne ze środowiskiem, w którym aplikacja została opracowana lub przetestowana. Niespójności w środowisku aplikacji są typowym źródłem problemów związanych z wdrożeniami monolitycznymi.

### <a name="coupling"></a>-

Aplikacje monolityczne mogą mieć bardzo duże okazje do sprzęgania różnych części aplikacji oraz między aplikacją i jej środowiskiem. Może to utrudnić wypróbowanie konkretnej usługi lub obawę w przyszłości, aby zwiększyć jej skalowalność lub wymianę w alternatywną implementację. Ten sprzężenie prowadzi również do znacznie większego potencjalnego wpływu na zmiany w systemie, wymagając obszernego testowania w większych aplikacjach.

### <a name="technology-choice"></a>Wybór technologii

Aplikacje monolityczne są kompilowane i wdrażane jako jednostka. Zapewnia prostotę i jednorodność, ale może być barierą dla innowacji. Mimo że nowa funkcja lub moduł w systemie może być lepiej dostosowany do bardziej nowoczesnej platformy lub struktury, prawdopodobnie zostanie skompilowany przy użyciu obecnego podejścia aplikacji w celu zapewnienia spójności, a także łatwość programowania i wdrażania.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jakie są korzyści z kontenerów i koordynatorów?

Docker to najpopularniejsza Platforma zarządzania kontenerami i tworzenia obrazów, dzięki której można szybko korzystać z kontenerów w systemach Linux i Windows. Kontenery zapewniają oddzielne, ale odwielone środowiska aplikacji, które działają w taki sam sposób w dowolnym systemie. Dzięki temu są one idealne do tworzenia i hostowania aplikacji i składników aplikacji w aplikacjach natywnych dla chmury. Kontenery są od siebie odizolowane, więc dwa kontenery na tym samym sprzęcie hosta mogą mieć zainstalowane różne wersje oprogramowania, a nawet system operacyjny, bez zależności powodujących konflikty.

Co więcej, kontenery są definiowane przez proste pliki, które można zaewidencjonować do kontroli źródła. W przeciwieństwie do pełnych serwerów, nawet maszyn wirtualnych, które często wymagają ręcznej pracy w celu zastosowania aktualizacji lub zainstalowania dodatkowych usług, infrastruktura kontenera może łatwo być kontrolowana w wersji. W ten sposób aplikacje skompilowane do uruchamiania w kontenerach można opracowywać, testować i wdrażać za pomocą zautomatyzowanych narzędzi w ramach potoku kompilacji.

Kontenery są niezmienne. Po zdefiniowaniu kontenera można ponownie utworzyć ten kontener i uruchomić go dokładnie tak samo. Ta niezmienności nadają się do projektowania opartego na składnikach. Jeśli niektóre części aplikacji nie zmieniają się tak często jak inne osoby, dlatego po prostu wdrożyć całą aplikację, gdy można tylko wdrożyć części, które ulegają zmianie najczęściej? Różne funkcje i zagadnienia dotyczące krzyżowego nacięcia aplikacji można podzielić na oddzielne jednostki. Rysunek 3-2 pokazuje, jak aplikacja monolityczna może korzystać z kontenerów i mikrousług przez delegowanie niektórych funkcji lub funkcji. Pozostałe funkcje w samej aplikacji również zostały zakontenerne.

![Rozdzielenie aplikacji monolitycznej na korzystanie z mikrousług w zapleczu. **Rysunek 3-2**. ](./media/breaking-up-monolith-with-backend-microservices.png)
 Rozdzielenie aplikacji monolitycznej na korzystanie z mikrousług w zapleczu.

Aplikacje natywne w chmurze skompilowane przy użyciu osobnych kontenerów mogą w razie potrzeby wdrażać dowolną lub niewielką część aplikacji. Poszczególne usługi mogą być hostowane na węzłach mających zasoby odpowiednie dla każdej usługi. Środowisko, w którym są uruchamiane poszczególne usługi, jest niezmienne, może być współużytkowane przez programowanie, testowanie i produkcję oraz może być łatwo w wersji. Sprzęganie różnych obszarów aplikacji występuje jawnie jako wywołania lub komunikaty między usługami, a nie zależności czasu kompilacji w ramach monolitu. Każda z tych części ogólnej aplikacji może wybrać technologię, która najbardziej wykrywa tę funkcję lub możliwość, bez konieczności wprowadzania zmian w pozostałej części aplikacji.

## <a name="what-are-the-scaling-benefits"></a>Jakie są korzyści z skalowania?

Usługi oparte na kontenerach mogą korzystać z zalet skalowania zapewnianych przez narzędzia Orchestration, takie jak Kubernetes. Za pomocą kontenerów projektowych są znane tylko informacje o sobie. Po rozpoczęciu pracy z wieloma kontenerami, które muszą współdziałać, można wartościowa je na wyższym poziomie. Organizowanie dużej liczby kontenerów i ich współużytkowanych zależności, takich jak konfiguracja sieci, polega na tym, że narzędzia aranżacji są dostępne w celu zapisania tego dnia. Kubernetes to platforma aranżacji kontenerów zaprojektowana w celu zautomatyzowania wdrażania, skalowania i zarządzania aplikacjami z kontenerami. Tworzy warstwę abstrakcji na podstawie grup kontenerów i organizuje je do *zasobników*. W przypadku maszyn roboczych, które są nazywane *węzłami*, są uruchamiane. Cała zorganizowana grupa jest określana jako *klaster*. Rysunek 3-3 przedstawia różne składniki klastra Kubernetes.

![Składniki klastra Kubernetes. **Rysunek 3-3**. ](./media/kubernetes-cluster-components.png)
 Składniki klastra Kubernetes.

Kubernetes ma wbudowaną obsługę skalowania klastrów w celu spełnienia wymagań. Dzięki połączeniu z mikrousługą kontenerów zapewnia aplikacje natywne dla chmury z możliwością szybkiego i efektywnego reagowania na popyt na żądanie z dodatkowymi zasobami, gdy są one konieczne.

### <a name="declarative-versus-imperative"></a>Deklaratywne i bezwzględne

Kubernetes obsługuje zarówno deklaratywną, jak i bezwzględną konfigurację obiektu. Bezwzględne podejście polega na uruchamianiu różnych poleceń, które informują Kubernetes o tym, co należy zrobić w każdym kroku. *Uruchom* ten obraz. *Usuń* ten temat. *Uwidocznić* ten port. Korzystając z podejścia deklaracyjnego, należy użyć pliku konfiguracji, który opisuje *to, czego* potrzebujesz *, a następnie Kubernetes, co* należy zrobić, aby osiągnąć żądany stan końcowy. Jeśli klaster został już skonfigurowany za pomocą bezwzględnych poleceń, można wyeksportować deklaratywny manifest za pomocą `kubectl get svc SERVICENAME -o yaml > service.yaml`. Spowoduje to utworzenie pliku manifestu, takiego jak ten:

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

W przypadku korzystania z konfiguracji deklaracyjnej można wyświetlić podgląd zmian, które zostaną wprowadzone przed ich zatwierdzeniem za `kubectl diff -f FOLDERNAME` pomocą folderu, w którym znajdują się pliki konfiguracji. Po upewnieniu się, że chcesz zastosować zmiany, uruchom `kubectl apply -f FOLDERNAME`polecenie. Dodaj `-R` , aby rekursywnie przetworzyć hierarchię folderów.

Oprócz usług można użyć konfiguracji deklaracyjnej dla innych funkcji Kubernetes, takich jak *wdrożenia*. Wdrożenia deklaracyjne są używane przez kontrolery wdrażania do aktualizowania zasobów klastra. Wdrożenia są używane do tworzenia nowych zmian, skalowania w górę w celu obsługi większej liczby obciążeń lub wycofywania do poprzedniej poprawki. Jeśli klaster jest niestabilny, wdrożenia deklaracyjne zapewniają mechanizm automatycznego przełączenia klastra do żądanego stanu.

Użycie konfiguracji deklaracyjnej pozwala na prezentowanie infrastruktury jako kodu, który można zaewidencjonować i wersji obok kodu aplikacji. Zapewnia to ulepszoną kontrolę zmian i lepszą obsługę ciągłego wdrażania przy użyciu potoków kompilowania i wdrażania powiązanych ze zmianami kontroli źródła.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jakie scenariusze doskonale sprawdzają się w przypadku kontenerów i koordynatorów?

Poniższe scenariusze doskonale nadają się do korzystania z kontenerów i Orchestrator.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikacje wymagające dużego czasu przestoju i skalowalności

Pojedyncze aplikacje, które mają duże przestoje i wymagania dotyczące skalowalności, są idealnymi kandydatami do obsługi architektur natywnych w chmurze przy użyciu mikrousług, kontenerów i Orchestrator. Te aplikacje można opracowywać w kontenerach korzystających ze środowisk z wersjami, które mogą być w szerokim zakresie testowane przed przejściem do środowiska produkcyjnego i można je wdrożyć w środowisku produkcyjnym bez przestojów. Użycie klastrów Kubernetes gwarantuje, że aplikacje mogą również skalować na żądanie i automatycznie odzyskiwać z awarii węzłów.

### <a name="large-numbers-of-applications"></a>Duża liczba aplikacji

Organizacje, które wdrażają i muszą w dalszym ciągu obsługiwać dużą liczbę aplikacji, z kontenerów i Orchestrator. Przede wszystkim nakłady pracy związane z konfigurowaniem środowisk kontenerów i klastrów Kubernetes jest kosztem stałym. Wdrażanie, konserwowanie i aktualizowanie poszczególnych aplikacji ma koszt, który jest zależny od liczby aplikacji, które muszą być utrzymywane. Poza pewną dość małą liczbą aplikacji, złożoność konserwacji aplikacji niestandardowych ręcznie przekracza koszt wdrożenia rozwiązania przy użyciu kontenerów i Orchestrator.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kiedy należy unikać używania kontenerów i koordynatorów?

Jeśli nie będziesz mieć możliwości kompilowania aplikacji lub nie możesz jej skompilować po wykorzystaniu zasad aplikacji 12-składnikowych, prawdopodobnie lepiej będzie uniknąć unikania kontenerów i Orchestrator. W takich przypadkach najlepszym rozwiązaniem może być przechodzenie do przodu przy użyciu platformy hostingu opartej na maszynach wirtualnych lub w niektórych systemach hybrydowych, w których można wyłączyć niektóre elementy funkcji w oddzielnych kontenerach, a nawet funkcji bezserwerowych. 

## <a name="development-resources"></a>Zasoby programistyczne

Ta sekcja zawiera krótką listę zasobów programistycznych, które mogą pomóc rozpocząć korzystanie z kontenerów i Orchestrator dla następnej aplikacji. Jeśli szukasz wskazówek dotyczących sposobu projektowania aplikacji architektury mikrousług natywnych dla chmury, przeczytaj pomocnika tej książki, [mikrousługi platformy .NET: Architektura dla kontenerów aplikacji](https://aka.ms/microservicesebook).NET.

### <a name="local-kubernetes-development"></a>Lokalne programowanie Kubernetes

Wdrożenia Kubernetes zapewniają znakomitą wartość w środowiskach produkcyjnych, ale można je również uruchamiać lokalnie. Mimo że warto bardzo często pracować nad indywidualnymi aplikacjami lub mikrousługami, czasami warto mieć możliwość lokalnego uruchamiania całego systemu w taki sposób, w jaki zostanie on uruchomiony po wdrożeniu w środowisku produkcyjnym. Istnieje kilka sposobów osiągnięcia tego, dwa z nich to Minikube i Docker Desktop. Program Visual Studio udostępnia także narzędzia do programowania platformy Docker.

### <a name="minikube"></a>Minikube

Co to jest Minikube? W projekcie Minikube jest wyświetlany komunikat "Minikube implementuje lokalny klaster Kubernetes w systemach macOS, Linux i Windows". Głównym celem jest "to najlepsze narzędzie do tworzenia lokalnych aplikacji Kubernetes oraz do obsługi wszystkich funkcji Kubernetes." Instalowanie Minikube jest oddzielone od platformy Docker, ale Minikube obsługuje inne funkcje hypervisor niż obsługuje program Docker Desktop. Następujące funkcje Kubernetes są obecnie obsługiwane przez Minikube:

- DNS
- NodePorts
- ConfigMaps i wpisy tajne
- Pulpity nawigacyjne
- Środowiska uruchomieniowe kontenera: Docker, RKT, CRI-O i kontenery
- Włączanie interfejsu sieciowego kontenera (CNI)
- Ruch przychodzący

Po zainstalowaniu Minikube można szybko rozpocząć korzystanie z niego, uruchamiając `minikube start` polecenie, które pobiera obraz i uruchamia lokalny klaster Kubernetes. Po uruchomieniu klastra możesz korzystać z niego przy użyciu standardowych poleceń Kubernetes `kubectl` .

### <a name="docker-desktop"></a>Pulpit Docker

Możesz również korzystać z usługi Kubernetes bezpośrednio z poziomu pulpitu Docker w systemie Windows. Jest to jedyna opcja, jeśli używasz kontenerów systemu Windows i jest to doskonały wybór dla kontenerów innych niż Windows. Standardowa aplikacja konfiguracji pulpitu platformy Docker służy do konfigurowania Kubernetes uruchomionych z poziomu programu Docker Desktop.

![Konfigurowanie Kubernetes w programie Docker Desktop](./media/docker-desktop-kubernetes.png)

**Rysunek 3-4**. Konfigurowanie Kubernetes w programie Docker Desktop.

Program Docker Desktop jest już najpopularniejszym narzędziem do konfigurowania i uruchamiania lokalnych aplikacji w kontenerze. Podczas pracy z programem Docker Desktop można opracowywać lokalnie na dokładnie tym samym zestawie obrazów kontenerów platformy Docker, które będą wdrażane w środowisku produkcyjnym. Program Docker Desktop został zaprojektowany na potrzeby lokalnego kompilowania, testowania i dostarczania aplikacji w kontenerze. Po wysłaniu obrazów do rejestru obrazów, takich jak Azure Container Registry lub Hub Docker, usługi, takie jak Azure Kubernetes Service (AKS), zarządzają aplikacją w środowisku produkcyjnym.

### <a name="visual-studio-docker-tooling"></a>Narzędzia platformy Docker programu Visual Studio

Program Visual Studio obsługuje programowanie platformy Docker dla aplikacji sieci Web. Podczas tworzenia nowej aplikacji ASP.NET Core można skonfigurować ją z obsługą platformy Docker w ramach procesu tworzenia projektu, jak pokazano na rysunku 3-5.

![Program Visual Studio umożliwia obsługę platformy Docker](./media/visual-studio-enable-docker-support.png)

**Rysunek 3-5**. Program Visual Studio umożliwia obsługę platformy Docker

Gdy ta opcja jest zaznaczona, projekt jest tworzony przy użyciu elementu `Dockerfile` w jego katalogu głównym, który może służyć do kompilowania i hostowania aplikacji w kontenerze platformy Docker. Przykład pliku dockerfile przedstawiono na rysunku 3-6.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**Rysunek 3-6**. Program Visual Studio wygenerował pliku dockerfile

Domyślne zachowanie podczas uruchamiania aplikacji jest skonfigurowane do korzystania z platformy Docker. Na rysunku 3-7 przedstawiono różne opcje uruchamiania dostępne w nowym projekcie ASP.NET Core utworzonym za pomocą dodanej obsługi platformy Docker.

![Opcje uruchamiania programu Visual Studio Docker](./media/visual-studio-docker-run-options.png)

**Rysunek 3-7**. Opcje uruchamiania programu Visual Studio Docker

Poza programowaniem lokalnym [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) zapewnia wygodny sposób pracy wielu programistów z własnymi konfiguracjami Kubernetes na platformie Azure. Jak widać na rysunku 3-10, można również uruchomić aplikację w Azure Dev Spaces.

Jeśli nie dodasz obsługi platformy Docker do aplikacji ASP.NET Core podczas jej tworzenia, zawsze możesz dodać ją później. W Eksplorator rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **obsługę platformy Docker**, jak pokazano na rysunku 3-8.

![Dodawanie obsługi platformy Docker w programie Visual Studio](./media/visual-studio-add-docker-support.png)

**Rysunek 3-8**. Dodawanie obsługi platformy Docker w programie Visual Studio

Oprócz obsługi platformy Docker można również dodać obsługę aranżacji kontenerów, również pokazane na rysunku 3-11. Domyślnie w programie Orchestrator są stosowane Kubernetes i Helm. Po wybraniu programu Orchestrator `azds.yaml` plik zostanie dodany do katalogu głównego projektu `charts` i zostanie dodany folder zawierający wykresy Helm używane do konfigurowania i wdrażania aplikacji w Kubernetes. Rysunek 3-9 pokazuje pliki wyników w nowym projekcie.

![Obsługa programu Visual Studio Add Orchestrator](./media/visual-studio-add-orchestrator-support.png)

**Rysunek 3-9**. Obsługa programu Visual Studio Add Orchestrator

## <a name="references"></a>Odwołania

- [Co to jest Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalowanie Kubernetes z Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Poprzedni](scale-applications.md)
>[Następny](leverage-serverless-functions.md)
