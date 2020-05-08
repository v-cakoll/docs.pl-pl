---
title: Korzystanie z kontenerów i orkiestratorów
description: Korzystanie z kontenerów platformy Docker i koordynatorów Kubernetes na platformie Azure
ms.date: 04/13/2020
ms.openlocfilehash: 64c6c0666398d9ccbc87efad18017bf278568fc4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895548"
---
# <a name="leveraging-containers-and-orchestrators"></a>Korzystanie z kontenerów i orkiestratorów

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontenery i Koordynatory zostały zaprojektowane w celu rozwiązywania problemów typowych dla podejścia do wdrożenia.

## <a name="challenges-with-monolithic-deployments"></a>Wyzwania z niemonolitycznymi wdrożeniami

Tradycyjnie większość aplikacji wdrożono jako pojedynczą jednostkę. Takie aplikacje są określane jako monolitu. To ogólne podejście do wdrażania aplikacji jako pojedyncze jednostki nawet wtedy, gdy składają się z wielu modułów lub zestawów, jest znana jako architektura monolityczna, jak pokazano na rysunku 3-1.

![Architektura monolityczna.](./media/monolithic-architecture.png)

**Rysunek 3-1**. Architektura monolityczna.

Chociaż mają zalety prostoty, monolityczne architektury mają kilka wyzwań:

### <a name="deployment"></a>Wdrożenie

Aplikacje monolityczne wymagają pełnego wdrożenia całej aplikacji, nawet jeśli została wprowadzona tylko niewielka zmiana. Pełne wdrożenia mogą być kosztowne i podatne na błędy. Ponadto wymagają ponownego uruchomienia aplikacji, która tymczasowo ma wpływ na niedostępność.

### <a name="scaling"></a>Skalowanie

Aplikacja monolityczna jest hostowana całkowicie w jednym wystąpieniu maszyny, co często wymaga sprzętu wysokiej klasy. Jeśli jakakolwiek część monolitu wymaga skalowania, należy wdrożyć inną kopię całej aplikacji na innej maszynie. Za pomocą monolitu nie można skalować składników aplikacji pojedynczo — wszystko to wszystko lub nic nie rób. Skalowanie składników, które nie wymagają skalowania, skutkuje niewydajnem i kosztownym użyciem zasobów.

### <a name="environment"></a>Środowisko

Aplikacje monolityczne są zwykle wdrażane w środowisku hostingu ze wstępnie zainstalowanymi zależnościami systemu operacyjnego, środowiska uruchomieniowego i biblioteki. To środowisko może nie pasować do tego, na którym aplikacja została opracowana lub przetestowana. Niespójności między środowiskami aplikacji są typowym źródłem problemów związanych z wdrożeniami monolitycznymi.

### <a name="coupling"></a>-

Aplikacja monolityczna prawdopodobnie będzie mieć wysokie sprzężenia w ramach jego składników funkcjonalnych. Bez stałych granic, zmiany systemu często powodują niezamierzone i kosztowne skutki uboczne. Nowe funkcje/poprawki stają się trudne, czasochłonne i kosztowne do wdrożenia. Aktualizacje wymagają obszernego testowania. Sprzęganie sprawia również trudne do refaktoryzacji składniki lub zamianę na alternatywne implementacje. Nawet w przypadku skonstruowania z ścisłym oddzieleniem problemów architektura erozji jest ustawiana w postaci, w jakiej baza kodu monolitycznego pogorszy się bez zakończenia "specjalnych przypadków".

### <a name="platform-lock-in"></a>Blokada platformy

Aplikacja monolityczna jest zbudowana przy użyciu jednego stosu technologii. Zapewniając jednolitość, to zobowiązanie może stać się barierą dla innowacji. Nowe funkcje i składniki zostaną skompilowane przy użyciu bieżącego stosu aplikacji — nawet wtedy, gdy bardziej nowoczesne technologie mogą być lepszym wyborem. Dłuższe ryzyko polega na tym, że stos technologii staje się nieaktualny i przestarzały. Ponowne tworzenie architektury całej aplikacji do nowej, bardziej nowoczesnej platformy jest najtańsze i ryzykowne.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Jakie są korzyści z kontenerów i koordynatorów?

Wprowadziliśmy kontenery w rozdziale 1. Wyróżniono sposób, w jaki usługa Cloud Native Computing Foundation (CNCF) ma rangę kontenerach jako pierwszy krok w swojej [natywnej mapie w chmurze](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) — wskazówki dla przedsiębiorstw, które rozpoczynają podróż w chmurze. W tej sekcji omówiono zalety kontenerów.

Docker to najpopularniejsza Platforma zarządzania kontenerami. Współpracuje z kontenerami w systemie Linux lub Windows. Kontenery zapewniają oddzielne, ale odwielone środowiska aplikacji, które działają w taki sam sposób w dowolnym systemie. Ten aspekt sprawia, że są one idealne do tworzenia i hostowania usług natywnych w chmurze. Kontenery są od siebie odizolowane. Dwa kontenery na tym samym sprzęcie hosta mogą mieć różne wersje oprogramowania bez powodowania konfliktów.

Kontenery są definiowane przez proste pliki tekstowe, które stają się artefaktami projektu i są sprawdzane w kontroli źródła. Gdy pełne serwery i maszyny wirtualne wymagają ręcznej pracy w celu aktualizacji, kontenery są łatwo kontrolowane pod kątem wersji. Aplikacje skompilowane do uruchamiania w kontenerach można opracowywać, testować i wdrażać za pomocą zautomatyzowanych narzędzi w ramach potoku kompilacji.

Kontenery są niezmienne. Po zdefiniowaniu kontenera można go ponownie utworzyć i uruchomić w ten sam sposób. Ta niezmienności nadają się do projektowania opartego na składnikach. Jeśli niektóre części aplikacji są rozmieszczone inaczej niż inne, dlaczego należy ponownie wdrożyć całą aplikację, gdy wystarczy wdrożyć części, które ulegają zmianie najczęściej? Różne funkcje i zagadnienia dotyczące krzyżowego nacięcia aplikacji można podzielić na oddzielne jednostki. Rysunek 3-2 pokazuje, jak aplikacja monolityczna może korzystać z kontenerów i mikrousług przez delegowanie niektórych funkcji lub funkcji. Pozostałe funkcje w samej aplikacji również zostały zakontenerne.

Kontenery są niezmienne. Po zdefiniowaniu kontenera można go ponownie utworzyć i uruchomić w ten sam sposób. Ta niezmienności nadają się do projektowania opartego na składnikach. Jeśli niektóre części aplikacji są rozmieszczone inaczej niż inne, dlaczego należy ponownie wdrożyć całą aplikację, gdy wystarczy wdrożyć części, które ulegają zmianie najczęściej? Różne funkcje i zagadnienia dotyczące krzyżowego nacięcia aplikacji można podzielić na oddzielne jednostki. Rysunek 3-2 pokazuje, jak aplikacja monolityczna może korzystać z kontenerów i mikrousług przez delegowanie niektórych funkcji lub funkcji. Pozostałe funkcje w samej aplikacji również zostały zakontenerne.

![Rozdzielenie aplikacji monolitycznej na korzystanie z mikrousług w zapleczu. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Rysunek 3-2**. Rozdzielenie aplikacji monolitycznej na korzystanie z mikrousług w zapleczu.

Każda usługa w chmurze została skompilowana i wdrożona w osobnym kontenerze. Każda z nich może być aktualizowana w razie konieczności. Poszczególne usługi mogą być hostowane na węzłach mających zasoby odpowiednie dla każdej usługi. Środowisko, w którym działa każda usługa, jest niezmienne, współużytkowane przez środowisko deweloperskie, testowe i produkcyjne oraz w łatwy sposób. Sprzęganie różnych obszarów aplikacji występuje jawnie jako wywołania lub komunikaty między usługami, a nie zależności czasu kompilacji w ramach monolitu. Możesz również wybrać technologię, która najlepiej spełnia daną możliwość, bez konieczności wprowadzania zmian w pozostałej części aplikacji.

Usługi kontenerowe wymagają zautomatyzowanego zarządzania. Nie byłoby możliwe ręczne administrowanie dużym zestawem niezależnie wdrożonych kontenerów. Rozważmy na przykład następujące zadania:

- Jak będą obsługiwane wystąpienia kontenerów w klastrze wielu maszyn?
- Po wdrożeniu, w jaki sposób kontenery będą odnajdywane i komunikować się ze sobą?
- Jak można skalować kontenery w poziomie lub na żądanie?
- Jak monitorować kondycję każdego kontenera?
- Jak chronić kontener przed awariami sprzętu i oprogramowania?
- Jak należy uaktualnić kontenery dla działającej aplikacji bez przestoju?

Koordynatory kontenerów i automatyzują te i inne zagadnienia.

W natywnym systemie ekonomicznym w chmurze Kubernetes stał się de facto koordynatorem kontenerów. Jest to platforma "open source" zarządzana przez natywną platformę obliczeniową w chmurze (CNCF). Kubernetes automatyzuje wdrażanie, skalowanie i problemy operacyjne obciążeń kontenerów w ramach klastra maszynowego. Jednak Instalowanie Kubernetes i zarządzanie nim jest wielowątkowy bardzo złożone.

Znacznie lepszym rozwiązaniem jest wykorzystanie Kubernetes jako usługi zarządzanej od dostawcy chmury. Usługa Azure Cloud oferuje w pełni zarządzaną platformę Kubernetes uprawnioną do [usługi Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). AKS abstrakcje złożoności i obciążenia operacyjnego związane z zarządzaniem Kubernetes. Korzystasz z Kubernetes jako usługi w chmurze; Firma Microsoft ponosi odpowiedzialność za zarządzanie i obsługę. AKS także ścisłą integrację z innymi usługami platformy Azure i narzędziami deweloperskimi.

AKS jest technologią opartą na klastrze. Pula federacyjnych maszyn wirtualnych lub węzłów jest wdrażana w chmurze platformy Azure. Razem tworzą one środowisko o wysokiej dostępności lub klaster. Klaster jest wyświetlany jako bezproblemową, pojedynczą jednostkę w aplikacji natywnej w chmurze. W obszarze okapu AKS wdraża usługi kontenerów w tych węzłach zgodnie ze wstępnie zdefiniowaną strategią, która równomiernie dystrybuuje obciążenie.

Usługi kontenerowe wymagają zautomatyzowanego zarządzania. Nie byłoby możliwe ręczne administrowanie dużym zestawem niezależnie wdrożonych kontenerów. Rozważmy na przykład następujące zadania:

- Jak będą obsługiwane wystąpienia kontenerów w klastrze wielu maszyn?
- Po wdrożeniu, w jaki sposób kontenery będą odnajdywane i komunikować się ze sobą?
- Jak można skalować kontenery w poziomie lub na żądanie?
- Jak monitorować kondycję każdego kontenera?
- Jak chronić kontener przed awariami sprzętu i oprogramowania?
- Jak należy uaktualnić kontenery dla działającej aplikacji bez przestoju?

Koordynatory kontenerów i automatyzują te i inne zagadnienia.

W natywnym systemie ekonomicznym w chmurze Kubernetes stał się de facto koordynatorem kontenerów. Jest to platforma "open source" zarządzana przez natywną platformę obliczeniową w chmurze (CNCF). Kubernetes automatyzuje wdrażanie, skalowanie i problemy operacyjne obciążeń kontenerów w ramach klastra maszynowego. Jednak Instalowanie Kubernetes i zarządzanie nim jest wielowątkowy bardzo złożone.

Znacznie lepszym rozwiązaniem jest wykorzystanie Kubernetes jako usługi zarządzanej od dostawcy chmury. Usługa Azure Cloud oferuje w pełni zarządzaną platformę Kubernetes uprawnioną do [usługi Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). AKS abstrakcje złożoności i obciążenia operacyjnego związane z zarządzaniem Kubernetes. Korzystasz z Kubernetes jako usługi w chmurze; Firma Microsoft ponosi odpowiedzialność za zarządzanie i obsługę. AKS także ścisłą integrację z innymi usługami platformy Azure i narzędziami deweloperskimi.

AKS jest technologią opartą na klastrze. Pula federacyjnych maszyn wirtualnych lub węzłów jest wdrażana w chmurze platformy Azure. Razem tworzą one środowisko o wysokiej dostępności lub klaster. Klaster jest wyświetlany jako bezproblemową, pojedynczą jednostkę w aplikacji natywnej w chmurze. W obszarze okapu AKS wdraża usługi kontenerów w tych węzłach zgodnie ze wstępnie zdefiniowaną strategią, która równomiernie dystrybuuje obciążenie.

## <a name="what-are-the-scaling-benefits"></a>Jakie są korzyści z skalowania?

Usługi oparte na kontenerach mogą korzystać z zalet skalowania zapewnianych przez narzędzia Orchestration, takie jak Kubernetes. Za pomocą kontenerów projektowych są znane tylko informacje o sobie. Jeśli masz wiele kontenerów, które muszą współdziałać, należy je zorganizować na wyższym poziomie. Organizowanie dużej liczby kontenerów i ich współużytkowanych zależności, takich jak konfiguracja sieci, polega na tym, że narzędzia aranżacji są dostępne w celu zapisania tego dnia. Kubernetes tworzy warstwę abstrakcji za pośrednictwem grup kontenerów i organizuje je do *zasobników*. W przypadku maszyn roboczych, które są nazywane *węzłami*, są uruchamiane. Ta zorganizowana struktura jest określana jako *klaster*. Rysunek 3-3 przedstawia różne składniki klastra Kubernetes.

![Składniki klastra Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Rysunek 3-3**. Składniki klastra Kubernetes.

Skalowanie obciążeń kontenerów jest kluczową funkcją koordynatorów kontenerów. AKS obsługuje automatyczne skalowanie w dwóch wymiarach: wystąpienia kontenerów i węzły obliczeniowe. Wspólnie zapewniają AKS możliwość szybkiego i efektywnego reagowania na popyt na żądanie i dodawania dodatkowych zasobów. Omawiamy skalowanie w AKS w dalszej części tego rozdziału.

### <a name="declarative-versus-imperative"></a>Deklaratywne i bezwzględne

Kubernetes obsługuje zarówno deklaratywną, jak i bezwzględną konfigurację. Bezwzględne podejście polega na uruchamianiu różnych poleceń, które informują Kubernetes o tym, co należy zrobić w każdym kroku. Uruchom ten obraz. Usuń ten temat. Uwidocznić ten port. Z podejściem deklaratywnym tworzysz plik konfiguracji o nazwie Manifest, aby opisać, co chcesz zrobić, zamiast tego, co należy zrobić. Kubernetes odczytuje manifest i przekształca żądany stan końcowy do rzeczywistego stanu końcowego.

Bezwzględne polecenia są doskonałe do uczenia się i interaktywnego eksperymentowania. Należy jednak pamiętać o deklaratywnym utworzeniu plików manifestu Kubernetes, aby wdrożyć infrastrukturę jako podejście kodu, zapewniając niezawodne i powtarzalne wdrożenia. Plik manifestu jest artefaktem projektu i jest używany w potoku CI/CD do automatyzowania wdrożeń Kubernetes.

Jeśli klaster został już skonfigurowany za pomocą bezwzględnych poleceń, można wyeksportować deklaratywny manifest za pomocą `kubectl get svc SERVICENAME -o yaml > service.yaml`. To polecenie generuje manifest podobny do przedstawionego poniżej:

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

Można również użyć konfiguracji deklaratywnej z innymi funkcjami Kubernetes, jednym z nich, które są wdrażane. Wdrożenia deklaratywne ułatwiają Zarządzanie wersjami, aktualizacjami i skalowaniem. Poinstruują Kubernetes Deployment Controller o sposobie wdrażania nowych zmian, skalowania w poziomie lub wycofywania do poprzedniej poprawki. Jeśli klaster jest niestabilny, wdrożenie deklaracyjne automatycznie zwróci klaster z powrotem do żądanego stanu. Jeśli na przykład węzeł ma awaria, mechanizm wdrażania ponownie wdroży zastąpienie w celu osiągnięcia żądanego stanu

Użycie konfiguracji deklaracyjnej pozwala na prezentowanie infrastruktury jako kodu, który można zaewidencjonować i wersji obok kodu aplikacji. Zapewnia ulepszoną kontrolę zmian i lepszą obsługę ciągłego wdrażania przy użyciu potoku kompilowania i wdrażania.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Jakie scenariusze doskonale sprawdzają się w przypadku kontenerów i koordynatorów?

Poniższe scenariusze doskonale nadają się do korzystania z kontenerów i Orchestrator.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplikacje wymagające dużego czasu przestoju i skalowalności

Pojedyncze aplikacje, które mają duże przestoje i wymagania dotyczące skalowalności, są idealnymi kandydatami do obsługi architektur natywnych w chmurze przy użyciu mikrousług, kontenerów i Orchestrator. Mogą one być opracowywane w kontenerach, testowane w środowiskach z wersjami i wdrażane w środowisku produkcyjnym bez przestojów. Użycie klastrów Kubernetes gwarantuje, że aplikacje mogą również skalować na żądanie i automatycznie odzyskiwać z awarii węzłów.

### <a name="large-numbers-of-applications"></a>Duża liczba aplikacji

Organizacje, które wdrażają i utrzymują dużą liczbę aplikacji, korzystają z kontenerów i koordynatorów. Przede wszystkim nakłady pracy związane z konfigurowaniem środowisk kontenerów i klastrów Kubernetes jest kosztem stałym. Wdrażanie, konserwowanie i aktualizowanie poszczególnych aplikacji ma koszt, który różni się w zależności od liczby aplikacji. W przypadku niewielkiej liczby aplikacji złożoność utrzymywania aplikacji niestandardowych ręcznie przekracza koszt wdrożenia rozwiązania przy użyciu kontenerów i Orchestrator.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kiedy należy unikać używania kontenerów i koordynatorów?

Jeśli nie możesz skompilować aplikacji przy użyciu zasad aplikacji 12-składnikowych, rozważ uniknięcie kontenerów i Orchestrator. W takich przypadkach należy wziąć pod uwagę platformę hostingu opartą na maszynach wirtualnych lub kilka systemów hybrydowych. Dzięki niej można zawsze wyłączać niektóre elementy funkcjonalności do oddzielnych kontenerów lub nawet funkcji bezserwerowych.

## <a name="development-resources"></a>Zasoby programistyczne

Ta sekcja zawiera krótką listę zasobów programistycznych, które mogą pomóc rozpocząć korzystanie z kontenerów i Orchestrator dla następnej aplikacji. Jeśli szukasz wskazówek dotyczących projektowania aplikacji architektury mikrousług natywnych dla chmury, przeczytaj pomocnika tej książki, [mikrousługi platformy .NET: architektura dla kontenerów aplikacji .NET](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

### <a name="local-kubernetes-development"></a>Lokalne programowanie Kubernetes

Wdrożenia Kubernetes zapewniają znakomitą wartość w środowiskach produkcyjnych, ale mogą być również uruchamiane lokalnie na komputerze deweloperskim. Mimo że użytkownik może pracować na pojedynczych mikrousługach niezależnie, może się okazać, że będzie konieczne lokalne uruchomienie całego systemu — podobnie jak zostanie ono uruchomione po wdrożeniu w środowisku produkcyjnym. Istnieje kilka narzędzi, które mogą pomóc: Minikube i Docker Desktop. Program Visual Studio udostępnia także narzędzia do programowania platformy Docker.

### <a name="minikube"></a>Minikube

Co to jest Minikube? W projekcie Minikube jest wyświetlany komunikat "Minikube implementuje lokalny klaster Kubernetes w systemach macOS, Linux i Windows". Głównym celem jest "to najlepsze narzędzie do tworzenia lokalnych aplikacji Kubernetes oraz do obsługi wszystkich funkcji Kubernetes." Instalowanie Minikube jest oddzielone od platformy Docker, ale Minikube obsługuje inne funkcje hypervisor niż obsługuje program Docker Desktop. Następujące funkcje Kubernetes są obecnie obsługiwane przez Minikube:

- DNS
- NodePorts
- ConfigMaps i wpisy tajne
- Pulpity nawigacyjne
- Środowiska uruchomieniowe kontenera: Docker, RKT, CRI-O, i kontener
- Włączanie interfejsu sieciowego kontenera (CNI)
- Ruch przychodzący

Po zainstalowaniu Minikube można szybko rozpocząć korzystanie z niego, uruchamiając `minikube start` polecenie, które pobiera obraz i uruchamia lokalny klaster Kubernetes. Po uruchomieniu klastra możesz korzystać z niego przy użyciu standardowych poleceń Kubernetes `kubectl` .

### <a name="docker-desktop"></a>Pulpit Docker

Możesz również korzystać z usługi Kubernetes bezpośrednio z poziomu pulpitu Docker w systemie Windows. Jest to jedyna opcja, jeśli używasz kontenerów systemu Windows i jest to doskonały wybór dla kontenerów innych niż Windows. Rysunek 3-4 pokazuje, jak włączyć obsługę lokalnego Kubernetes podczas uruchamiania programu Docker Desktop.

![Konfigurowanie Kubernetes w programie Docker Desktop](./media/docker-desktop-kubernetes.png)

**Rysunek 3-4**. Konfigurowanie Kubernetes w programie Docker Desktop.

Docker Desktop to najpopularniejsze narzędzie do konfigurowania i uruchamiania lokalnych aplikacji w kontenerze. Podczas pracy z programem Docker Desktop można opracowywać lokalnie na dokładnie tym samym zestawie obrazów kontenerów platformy Docker, które będą wdrażane w środowisku produkcyjnym. Program Docker Desktop został zaprojektowany na potrzeby lokalnego kompilowania, testowania i dostarczania aplikacji w kontenerze. Obsługuje zarówno kontenery systemu Linux, jak i Windows. Po wypchnięciu obrazów do rejestru obrazów, takich jak Azure Container Registry lub Hub Docker, AKS może ściągnąć i wdrożyć je w środowisku produkcyjnym.

### <a name="visual-studio-docker-tooling"></a>Narzędzia platformy Docker programu Visual Studio

Program Visual Studio obsługuje programowanie platformy Docker dla aplikacji sieci Web. Podczas tworzenia nowej aplikacji ASP.NET Core można skonfigurować ją z obsługą platformy Docker, jak pokazano na rysunku 3-5.

![Program Visual Studio umożliwia obsługę platformy Docker](./media/visual-studio-enable-docker-support.png)

**Rysunek 3-5**. Program Visual Studio umożliwia obsługę platformy Docker

Gdy ta opcja jest zaznaczona, projekt jest tworzony przy użyciu elementu `Dockerfile` w jego katalogu głównym, który może służyć do kompilowania i hostowania aplikacji w kontenerze platformy Docker. Przykład pliku dockerfile przedstawiono na rysunku 3 -6. git

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

Poza programowaniem lokalnym [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) zapewnia wygodny sposób pracy wielu programistów z własnymi konfiguracjami Kubernetes na platformie Azure. Jak widać na rysunku 3-7, można również uruchomić aplikację w Azure Dev Spaces.

Ponadto w dowolnym momencie można dodać obsługę platformy Docker do istniejącej aplikacji ASP.NET Core. W programie Visual Studio Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i **Dodaj** > **obsługę platformy Docker**, jak pokazano na rysunku 3-8.

**Rysunek 3-8**. Dodawanie obsługi platformy Docker do programu Visual Studio

Możesz również dodać obsługę aranżacji kontenera, jak pokazano na rysunku 3-8. Domyślnie w programie Orchestrator są stosowane Kubernetes i Helm. Po wybraniu programu Orchestrator `azds.yaml` plik zostanie dodany do katalogu głównego projektu i zostanie dodany `charts` folder zawierający wykresy Helm używane do konfigurowania i wdrażania aplikacji w Kubernetes. Rysunek 3-9 pokazuje pliki wyników w nowym projekcie.

Możesz również dodać obsługę aranżacji kontenera, jak pokazano na rysunku 3-8. Domyślnie w programie Orchestrator są stosowane Kubernetes i Helm. Po wybraniu programu Orchestrator `azds.yaml` plik zostanie dodany do katalogu głównego projektu i zostanie dodany `charts` folder zawierający wykresy Helm używane do konfigurowania i wdrażania aplikacji w Kubernetes. Rysunek 3-9 pokazuje pliki wyników w nowym projekcie.

**Rysunek 3-9**. Dodawanie obsługi aranżacji do programu Visual Studio

### <a name="visual-studio-code-docker-tooling"></a>Visual Studio Code narzędzia platformy Docker

Istnieje wiele rozszerzeń dostępnych dla Visual Studio Code obsługujących programowanie platformy Docker.

Firma Microsoft udostępnia [platformę Docker dla Visual Studio Code rozszerzenia](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker). To rozszerzenie upraszcza proces dodawania obsługi kontenera do aplikacji. Szkieletuje wymagane pliki, tworzy obrazy platformy Docker i umożliwia debugowanie aplikacji w kontenerze. Rozszerzenie zawiera program Visual Explorer, który ułatwia podejmowanie działań na kontenerach i obrazach, takich jak uruchamianie, zatrzymywanie, inspekcja, usuwanie i nie tylko. Rozszerzenie obsługuje również Docker Compose umożliwiające zarządzanie wieloma uruchomionymi kontenerami jako pojedynczą jednostką.

>[!div class="step-by-step"]
>[Poprzedni](scale-applications.md)
>[Następny](leverage-serverless-functions.md)
