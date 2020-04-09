---
title: Korzystanie z kontenerów i orkiestratorów
description: Korzystanie z kontenerów platformy Docker i koordynatorów platformy Kubernetes na platformie Azure
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989041"
---
# <a name="leveraging-containers-and-orchestrators"></a>Korzystanie z kontenerów i orkiestratorów

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontenery i koordynatorzy są przeznaczone do rozwiązywania problemów wspólnych dla monolitycznych metod wdrażania.

## <a name="challenges-with-monolithic-deployments"></a>Wyzwania związane z wdrożeniami monolitycznymi

Tradycyjnie większość aplikacji zostały wdrożone jako pojedyncza jednostka. Takie zastosowania są określane jako monolit. To ogólne podejście do wdrażania aplikacji jako pojedynczych jednostek, nawet jeśli składają się one z wielu modułów lub zestawów jest znany jako architektury monolityczne, jak pokazano na rysunku 3-1.

![Architektura monolityczna.](./media/monolithic-architecture.png)

**Rysunek 3-1**. Architektura monolityczna.

Chociaż mają one zaletę prostoty, monolityczne architektury stoją przed szeregiem wyzwań:

### <a name="deployments"></a>Wdrożenia

Wdrażanie w aplikacjach monolitycznych zazwyczaj wymaga ponownego uruchomienia całej aplikacji, nawet jeśli tylko jeden mały moduł jest zastępowany. W zależności od liczby komputerów obsługujących aplikację może to spowodować przestoje podczas wdrożeń.

### <a name="hosting"></a>Hosting

Aplikacje monolityczne są hostowane w całości na jednym wystąpieniu komputera. Może to wymagać sprzętu o większej wydajności niż jakikolwiek moduł w aplikacji rozproszonej będzie potrzebował. Ponadto jeśli dowolna część aplikacji staje się wąskim gardłem, cała aplikacja musi zostać wdrożona w dodatkowych węzłach komputera w celu skalowania w poziomie.

### <a name="environment"></a>Środowisko

Aplikacje monolityczne są zazwyczaj wdrażane w istniejącym środowisku hostingowym (system operacyjny, zainstalowane struktury itp.). To środowisko może nie odpowiadać środowisku, w którym aplikacja została opracowana lub przetestowana. Niespójności w środowisku aplikacji są częstym źródłem problemów dla wdrożeń monolitycznych.

### <a name="coupling"></a>Sprzęgła

Aplikacje monolityczne mogą mieć wiele sprzężenia między różnymi częściami aplikacji i między aplikacją a jej środowiskiem. Może to utrudnić uwzględnienie określonej usługi lub obawy później, w celu zwiększenia jej skalowalności lub wymiany w alternatywnej implementacji. Sprzężenie to prowadzi również do znacznie większego potencjalnego wpływu na zmiany w systemie, co wymaga szeroko zakrojonych testów w większych zastosowaniach.

### <a name="technology-choice"></a>Wybór technologii

Aplikacje monolityczne są budowane i wdrażane jako jednostka. Zapewnia to prostotę i jednolitość, ale może być barierą dla innowacji. Chociaż nowa funkcja lub moduł w systemie może być lepiej nadaje się do bardziej nowoczesnej platformy lub struktury, prawdopodobnie zostanie zbudowany przy użyciu bieżącego podejścia aplikacji ze względu na spójność, a także łatwość programowania i wdrażania.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jakie są korzyści z kontenerów i koordynatorów?

Docker jest najpopularniejszą platformą do zarządzania kontenerami i przetwarzania obrazu i umożliwia szybką pracę z kontenerami w systemach Linux i Windows. Kontenery zapewniają oddzielne, ale powtarzalne środowiska aplikacji, które działają w ten sam sposób w dowolnym systemie. Dzięki temu idealnie nadają się do tworzenia i hostowania aplikacji i składników aplikacji w aplikacjach natywnych dla chmury. Kontenery są odizolowane od siebie, więc dwa kontenery na tym samym sprzęcie hosta mogą mieć zainstalowane różne wersje oprogramowania, a nawet system operacyjny, bez zależności powodujących konflikty.

Co więcej, kontenery są definiowane przez proste pliki, które można zaewidencjonować w formancie źródła. W przeciwieństwie do pełnych serwerów, nawet maszyn wirtualnych, które często wymagają ręcznej pracy w celu zastosowania aktualizacji lub zainstalowania dodatkowych usług, infrastruktura kontenera może być łatwo kontrolowana przez wersję. W związku z tym aplikacje utworzone do uruchamiania w kontenerach mogą być opracowywane, testowane i wdrażane przy użyciu zautomatyzowanych narzędzi w ramach potoku kompilacji.

Kontenery są niezmienne. Po definicji kontenera, można odtworzyć tego kontenera i będzie działać dokładnie w ten sam sposób. Ta niezmienność nadaje się do projektowania opartego na składnikach. Jeśli niektóre części aplikacji nie zmieniają się tak często, jak inne, po co ponownie wdrażać całą aplikację, gdy można po prostu wdrożyć części, które zmieniają się najczęściej? Różne funkcje i przekrojowe problemy aplikacji można podzielić na oddzielne jednostki. Rysunek 3-2 pokazuje, jak aplikacja monolityczne mogą korzystać z kontenerów i mikrousług, delegując niektóre funkcje lub funkcje. Pozostałe funkcje w samej aplikacji również został konteneryzowany.

![Rozbicie aplikacji monolityczne do korzystania z mikrousług w zapleczu. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Rysunek 3-2**. Rozbicie aplikacji monolityczne do korzystania z mikrousług w zapleczu.

Aplikacje natywne w chmurze utworzone przy użyciu oddzielnych kontenerów korzystają z możliwości wdrażania jak najwięcej lub tak mało aplikacji, jak to konieczne. Poszczególne usługi mogą być hostowane w węzłach z zasobami odpowiednimi dla każdej usługi. Środowisko, w którym działa każda usługa, jest niezmienne, może być współużytkowane przez deweloperów, test i produkcję i można je łatwo wersjonować. Sprzężenie między różnymi obszarami aplikacji występuje jawnie jako wywołania lub wiadomości między usługami, a nie zależności w czasie kompilacji w monolit. A każda część ogólnej aplikacji może wybrać technologię, która ma największy sens dla tej funkcji lub możliwości bez konieczności zmiany w pozostałej części aplikacji.

## <a name="what-are-the-scaling-benefits"></a>Jakie są korzyści skalowania?

Usługi oparte na kontenerach mogą korzystać z korzyści skalowania zapewnianych przez narzędzia aranżacji, takie jak Kubernetes. Według projektu kontenery wiedzą tylko o sobie. Po uruchomieniu wielu kontenerów, które muszą współpracować, może być warto zorganizować je na wyższym poziomie. Organizowanie dużej liczby kontenerów i ich współdzielonych zależności, takich jak konfiguracja sieci, jest, gdzie narzędzia aranżacji przyjść, aby zapisać dzień! Kubernetes to platforma aranżacji kontenerów przeznaczona do automatyzacji wdrażania, skalowania i zarządzania aplikacjami konteneryzowanymi. Tworzy warstwę abstrakcji na wierzchu grup kontenerów i organizuje je w *zasobniki*. Zasobniki działają na maszynach roboczych, określanych jako *węzły*. Cała zorganizowana grupa jest określana jako *klaster*. Rysunek 3-3 przedstawia różne składniki klastra Kubernetes.

![Składniki klastra kubernetes. ](./media/kubernetes-cluster-components.png)
 **Rysunek 3-3**. Składniki klastra kubernetes.

Kubernetes ma wbudowaną obsługę skalowania klastrów w celu zaspokojenia popytu. W połączeniu z konteneryzowanymi mikrousługami zapewnia to aplikacjom natywnym dla chmury możliwość szybkiego i wydajnego reagowania na skoki popytu z dodatkowymi zasobami, kiedy i gdzie są potrzebne.

### <a name="declarative-versus-imperative"></a>Deklaratywne a imperatyw

Kubernetes obsługuje zarówno deklaratywny i imperatywny konfiguracji obiektu. Podejście imperatywne polega na uruchamianiu różnych poleceń, które informują kubernetes, co zrobić na każdym kroku. *Uruchom* ten obraz. *Usuń* tę kapsułę. *Udostępnij* ten port. W przypadku podejścia deklaratywnego należy użyć pliku konfiguracji, który *opisuje, co chcesz,* a nie *co zrobić,* a kubernetes określa, co należy zrobić, aby osiągnąć żądany stan końcowy. Jeśli klaster został już skonfigurowany przy użyciu poleceń imperatywów, można wyeksportować manifest deklaratywny za pomocą programu `kubectl get svc SERVICENAME -o yaml > service.yaml`. Spowoduje to powstanie pliku manifestu, takiego jak ten:

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

Korzystając z konfiguracji deklaratywnej, można wyświetlić podgląd `kubectl diff -f FOLDERNAME` zmian, które zostaną wprowadzone przed zatwierdzeniem ich przy użyciu względem folderu, w którym znajdują się pliki konfiguracyjne. Gdy na pewno chcesz zastosować zmiany, `kubectl apply -f FOLDERNAME`uruchom program . Dodaj `-R` do cyklicznego przetwarzania hierarchii folderów.

Oprócz usług można użyć konfiguracji deklaratywnej dla innych funkcji kubernetes, takich jak *wdrożenia*. Wdrożenia deklaratywne są używane przez kontrolery wdrażania do aktualizowania zasobów klastra. Wdrożenia są używane do wprowadzania nowych zmian, skalowania w górę w celu obsługi większego obciążenia lub wycofywania do poprzedniej wersji. Jeśli klaster jest niestabilny, deklaratywnych wdrożeń zapewniają mechanizm automatycznego przywracania klastra do żądanego stanu.

Za pomocą konfiguracji deklaratywnej umożliwia infrastruktury, które mają być reprezentowane jako kod, który może być zaewidencjonowany i wersjona obok kodu aplikacji. Zapewnia to lepszą kontrolę zmian i lepszą obsługę ciągłego wdrażania przy użyciu kompilacji i wdrażania potoku powiązanego ze zmianami kontroli źródła.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jakie scenariusze są idealne dla kontenerów i koordynatorów?

Poniższe scenariusze są idealne do korzystania z kontenerów i koordynatorów.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikacje wymagające dużej dyspozycyjności i skalowalności

Poszczególne aplikacje, które mają wysoki czas pracy bez przestojów i wymagania dotyczące skalowalności są idealnymi kandydatami do architektury natywnej w chmurze przy użyciu mikrousług, kontenerów i koordynatorów. Te aplikacje mogą być tworzone w kontenerach przy użyciu środowisk wersjonatowanych, mogą być szczegółowo testowane przed przejściem do produkcji i mogą być wdrażane w środowisku produkcyjnym bez przestojów. Użycie klastrów Kubernetes zapewnia, że takie aplikacje mogą również skalować się na żądanie i automatycznie odzyskać z błędów węzłów.

### <a name="large-numbers-of-applications"></a>Duża liczba aplikacji

Organizacje, które wdrażają i muszą następnie obsługiwać dużą liczbę aplikacji, korzystają z kontenerów i koordynatorów. Z góry wysiłek konfigurowania konteneryzowanych środowisk i klastrów Kubernetes jest przede wszystkim kosztem stałym. Wdrażanie, obsługa i aktualizowanie poszczególnych aplikacji ma koszt, który różni się w zależności od liczby aplikacji, które muszą być obsługiwane. Poza pewną dość małą liczbę aplikacji, złożoność obsługi aplikacji niestandardowych ręcznie przekracza koszty implementacji rozwiązania przy użyciu kontenerów i koordynatorów.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kiedy należy unikać używania kontenerów i koordynatorów?

Jeśli nie chcesz lub nie możesz utworzyć aplikacji zgodnie z zasadami aplikacji Dwunastu czynników, prawdopodobnie lepiej będzie uniknąć kontenerów i koordynatorów. W takich przypadkach może być najlepiej, aby przejść do przodu z platformą hostingową opartą na maszynie Wirtualnej lub ewentualnie jakiś system hybrydowy, w którym można odkręcić niektóre elementy funkcjonalności do oddzielnych kontenerów lub nawet funkcji bezserwerowych.

## <a name="development-resources"></a>Zasoby rozwojowe

W tej sekcji przedstawiono krótką listę zasobów programistów, które mogą pomóc w rozpoczęciu korzystania z kontenerów i koordynatorów dla następnej aplikacji. Jeśli szukasz wskazówek dotyczących projektowania aplikacji architektury mikrousług natywnych dla chmury, przeczytaj towarzysza tej książki, [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Rozwój lokalnych Kubernetes

Wdrożenia kubernetes zapewniają dużą wartość w środowiskach produkcyjnych, ale można również uruchomić je lokalnie. Mimo że przez większość czasu dobrze jest mieć możliwość pracy z poszczególnych aplikacji lub mikrousług niezależnie, czasami dobrze jest być w stanie uruchomić cały system lokalnie, tak jak będzie działać po wdrożeniu do produkcji. Istnieje kilka sposobów, aby to osiągnąć, z których dwa to Minikube i Docker Desktop. Visual Studio udostępnia również narzędzia do tworzenia platformy Docker.

### <a name="minikube"></a>Minikube ( minikube )

Co to jest Minikube? Projekt Minikube mówi: "Minikube implementuje lokalny klaster Kubernetes w systemach macOS, Linux i Windows". Jego głównymi celami są "być najlepszym narzędziem do tworzenia lokalnych aplikacji Kubernetes i obsługiwać wszystkie funkcje Kubernetes, które pasują." Instalacja Minikube jest oddzielona od platformy Docker, ale Minikube obsługuje inne hipernadzorce niż docker desktop obsługuje. Minikube obsługuje obecnie następujące funkcje kubernetes:

- DNS
- Porty węzłów
- ConfigMaps i tajemnice
- Pulpity nawigacyjne
- Środowiska wykonawcze kontenera: Docker, rkt, CRI-O i containerd
- Włączanie interfejsu sieci kontenerów (CNI)
- Ruch przychodzący

Po zainstalowaniu Minikube można szybko rozpocząć `minikube start` korzystanie z niego, uruchamiając polecenie, które pobiera obraz i uruchamia lokalny klaster Kubernetes. Po uruchomieniu klastra można z nim wchodzić w `kubectl` interakcje przy użyciu standardowych poleceń Kubernetes.

### <a name="docker-desktop"></a>Pulpit platformy Docker

Można również pracować z kubernetes bezpośrednio z pulpitu platformy Docker w systemie Windows. Jest to jedyna opcja, jeśli używasz kontenerów systemu Windows i jest doskonałym wyborem dla kontenerów innych niż Windows, jak również. Standardowa aplikacja konfiguracja pulpitu platformy Docker służy do konfigurowania aplikacji Kubernetes z komputera Docker Desktop.

![Konfigurowanie aplikacji Kubernetes w aplikacji Pulpit platformy Docker](./media/docker-desktop-kubernetes.png)

**Rysunek 3-4**. Konfigurowanie aplikacji Kubernetes w aplikacji Docker Desktop.

Docker Desktop jest już najpopularniejszym narzędziem do konfigurowania i uruchamiania aplikacji konteneryzowanych lokalnie. Podczas pracy z pulpitem platformy Docker można tworzyć lokalnie względem dokładnie tego samego zestawu obrazów kontenerów platformy Docker, które będą wdrażane w środowiskach produkcyjnych. Docker Desktop jest przeznaczony do "tworzenia, testowania i wysyłki" konteneryzowanych aplikacji lokalnie. Po wysłaniu obrazów do rejestru obrazów, takich jak Usługa Azure Container Registry lub Docker Hub, usługi takie jak usługa Azure Kubernetes Service (AKS) zarządzają aplikacją w środowiskach produkcyjnych.

### <a name="visual-studio-docker-tooling"></a>Narzędzia platformy Docker programu Visual Studio

Program Visual Studio obsługuje program docker dla aplikacji sieci web. Podczas tworzenia nowej aplikacji ASP.NET Core, masz możliwość skonfigurowania go z obsługą platformy Docker w ramach procesu tworzenia projektu, jak pokazano na rysunku 3-5.

![Obsługa platformy Docker włączania programu Visual Studio](./media/visual-studio-enable-docker-support.png)

**Rysunek 3-5**. Obsługa platformy Docker włączania programu Visual Studio

Gdy ta opcja jest zaznaczona, `Dockerfile` projekt jest tworzony z w katalogu głównym, który może służyć do tworzenia i hostowania aplikacji w kontenerze platformy Docker. Przykład dockerfile jest pokazany na rysunku 3-6.

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

**Rysunek 3-6**. Program Visual Studio wygenerował plik dockerfile

Domyślne zachowanie podczas pracy aplikacji jest skonfigurowany do korzystania z platformy Docker, jak również. Rysunek 3-7 przedstawia różne opcje uruchamiania dostępne w nowym projekcie ASP.NET Core utworzonym z dodanym wsparciem platformy Docker.

![Opcje uruchamiania platformy Docker programu Visual Studio](./media/visual-studio-docker-run-options.png)

**Rysunek 3-7**. Opcje uruchamiania platformy Docker programu Visual Studio

Oprócz lokalnego rozwoju [usługa Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) zapewnia wygodny sposób pracy wielu deweloperów z ich własnymi konfiguracjami kubernetes na platformie Azure. Jak widać na rysunku 3-7, można również uruchomić aplikację w usłudze Azure Dev Spaces.

Jeśli nie dodasz do aplikacji platformy Docker do aplikacji ASP.NET Core podczas jej tworzenia, zawsze możesz dodać ją później. W Eksploratorze rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Dodaj** > **obsługę platformy Docker,** jak pokazano na rysunku 3-8.

![Obsługa doklin dodatku docker w programie Visual Studio](./media/visual-studio-add-docker-support.png)

**Rysunek 3-8**. Obsługa doklin dodatku docker w programie Visual Studio

Oprócz obsługi platformy Docker można również dodać obsługę aranżacji kontenera, również pokazano na rysunku 3-8. Domyślnie orchestrator używa Kubernetes i Helm. Po wybraniu koordynatora `azds.yaml` plik jest dodawany do katalogu głównego `charts` projektu i dodawany jest folder zawierający wykresy Helm używane do konfigurowania i wdrażania aplikacji w usłudze Kubernetes. Rysunek 3-9 przedstawia wynikowe pliki w nowym projekcie.

![Obsługa dodatku programu Visual Studio Add Orchestrator](./media/visual-studio-add-orchestrator-support.png)

**Rysunek 3-9**. Obsługa dodatku programu Visual Studio Add Orchestrator

## <a name="references"></a>Dokumentacja

- [Co to jest Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalacja Kubernetes z Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Poprzedni](scale-applications.md)
>[następny](leverage-serverless-functions.md)
