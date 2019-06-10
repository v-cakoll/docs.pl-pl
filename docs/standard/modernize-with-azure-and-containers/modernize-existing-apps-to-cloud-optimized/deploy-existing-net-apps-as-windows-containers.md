---
title: Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Wdrażanie istniejących aplikacji .NET jako kontenerów Windows
ms.date: 04/29/2018
ms.openlocfilehash: ba9af3fc3a5bf285830bb873fa6a5da8390dc6b4
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758836"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows

Wdrożenia, które są oparte na Windows kontenery są stosowane do aplikacji zoptymalizowane pod kątem chmury i aplikacji natywnych dla chmury.

Jednak w tym przewodniku, a zwłaszcza w poniższych sekcjach, przede wszystkim koncentruje się ona na przy użyciu kontenerów Windows *zoptymalizowane pod kątem chmury* aplikacje, których nie ma potrzeby Przekształcanie aplikacji.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenery? (Linux lub Windows)

Kontenery są sposobem zawinąć aplikacji na swój własny pakiet izolowany. W jego kontenerze nie dotyczy aplikacji przez aplikacje lub procesy, które istnieją poza kontenerem. Wszystko, co aplikacja zależy od do wykonywania pomyślnie procesu znajduje się wewnątrz kontenera. Wszędzie tam, gdzie może przenieść kontener, wymagań aplikacji zawsze spełnione zostaną, pod kątem bezpośrednich zależności, ponieważ jest powiązany ze wszystkim, co potrzebne do uruchomienia (zależności biblioteki, środowisk wykonawczych i tak dalej).

Główną cechą kontenera jest fakt, że środowisko takie same we wszystkich wdrożeniach różnych ponieważ samego kontenera, który jest dostarczany ze wszystkimi zależnościami, których potrzebuje. Debugowanie aplikacji na komputerze i wdrożyć ją do innej maszyny, z tym samym środowisku, gwarantowana.

Kontener jest wystąpienia obrazu kontenera. Obraz kontenera jest sposobem pakietu aplikacji lub usługi (takie jak migawki), a następnie wdrożyć go w sposób niezawodny i odtworzenia. Można powiedzieć, że platformy Docker nie jest tylko technologii it roku filozofii i procesu.

Kontenery codziennie stały się bardziej powszechne, stają się się całej branży "jednostka wdrożenia".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Korzyści z kontenerów (aparat platformy Docker w systemie Linux lub Windows)

Tworzenie aplikacji za pomocą kontenerów, które mogą być również zdefiniowane jako lekka oferuje bloki konstrukcyjne znaczny wzrost w elastyczność tworzenia i wysyłania, oraz uruchamiania dowolnej aplikacji w dowolnym infrastrukturze.

Za pomocą kontenerów możesz korzystać z dowolnej aplikacji od projektowania do produkcji za pomocą niewielkiego lub żadnego zmiany w kodzie, dzięki integracji platformy Docker w narzędziach deweloperskich firmy Microsoft, w systemach operacyjnych i w chmurze.

Podczas wdrażania do zwykłych maszyn wirtualnych, prawdopodobnie masz już metody w miejscu na potrzeby wdrażania aplikacji platformy ASP.NET na maszynach wirtualnych. Prawdopodobne jest, jednak, że metoda obejmuje wiele kroków lub złożone procesy zautomatyzowane przy użyciu narzędzia wdrażania, takich jak Puppet lub podobnego narzędzia. Konieczne może wykonywać zadania takie jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami i uruchamianie programów instalacji interakcyjnej opartych na msi konfiguracje, następuje testowanie. Te kroki w ramach wdrożenia Dodaj czasu i ryzyka do wdrożeń. Otrzymasz błędów w każdym przypadku, gdy zależność nie znajduje się w środowisku docelowym.

W kontenerach Windows jest w pełni zautomatyzowane proces pakowania aplikacji. Kontenery Windows opiera się na platformie Docker oferuje automatyczne aktualizacje i wycofywanie zmian, w przypadku wdrożeń kontenera. Główne poprawy jakości obsługi, który jest pobierany z przy użyciu aparatu platformy Docker jest tworzenie obrazów, które są podobne migawek aplikacji, ze wszystkimi jej zależnościami. Obrazy są obrazy platformy Docker (Windows obraz kontenera, w tym przypadku). Obrazy, uruchamianie aplikacji platformy ASP.NET w kontenerach, bez konieczności powrotu do kodu źródłowego. Migawka kontenerów staje się jednostką wdrożenia.

W wielu organizacjach są konteneryzowania istniejącej aplikacji monolitycznych z następujących powodów:

- **Elastyczność dzięki ulepszone wdrażanie wersji**. Kontenery oferują umowy spójne wdrażanie, między środowiskami deweloperskim i operacji. Podczas używania kontenerów nie słyszysz deweloperów powiedzieć, "działa na komputerze, dlaczego w środowisku produkcyjnym?" One można powiedzieć "Działa jako kontener, dzięki czemu będzie ona uruchamiana w środowisku produkcyjnym." Spakowanej aplikacji ze wszystkimi jej zależnościami, można wykonać w dowolnym środowisku obsługiwanych opartych na kontenerach. Sposób, w jaki jest przeznaczona do uruchamiania w wszystkich celów wdrożenia (deweloperskie, QA, przejściowego i produkcji), będzie działać. Kontenery wyeliminować większość frictions łączącymi się z jednego etapu do następnego, co znacznie zwiększa wdrożenia, i może to być szybsze dostarczanie.

- **Obniżenie kosztów**. Kontenery prowadzić do obniżenia kosztów, albo poprzez konsolidacji i usunięcie istniejącego sprzętu lub uruchamianie aplikacji na zwiększenie gęstości jednostkę sprzętu.

- **Przenośność**. Kontenery są moduły i przenośnych. Kontenery platformy docker są obsługiwane na dowolnej systemu operacyjnego Linux i Windows, w dowolnej głównych chmurze publicznej (Microsoft Azure, Amazon AWS, Google, IBM) oraz w lokalnych i prywatnych środowiskach chmury hybrydowej.

- **Kontrolka**. Kontenery oferują elastyczne i bezpieczne środowisko, które są kontrolowane na poziomie kontenera. Kontener można zabezpieczony, izolowane i nawet ograniczony przez ustawienia ograniczenia zasad wykonywania w kontenerze. Zgodnie z opisem w sekcji o kontenerach Windows Windows Server 2016 i funkcji Hyper-V kontenery oferują enterprise dodatkowe opcje pomocy technicznej.

Znaczne ulepszenia dotyczące elastyczności, przenoszenia i kontroli ostatecznie prowadzić do obniżenia kosztów, gdy używać kontenerów do tworzenia i konserwowania aplikacji.

## <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projektu open-source](https://github.com/docker/docker) który umożliwia automatyzowanie wdrażania aplikacji jako przenośne, samowystarczalne kontenery, działających w chmurze lub lokalnie. Docker to również [firmy](https://www.docker.com/) który promuje i rozwojem tej technologii. Firma działa we współpracy z chmury, Linux i Windows producentów, takie jak Microsoft.

![](./media/image6.png)

> **Rysunek 4 – 6.** Docker służy do wdrażania kontenerów we wszystkich warstwach chmury hybrydowej

Do kogoś zapoznać się z maszyn wirtualnych, kontenerów może się wydawać niezwykle podobne. Kontener jest uruchamiany system operacyjny, system plików jest i jest dostępna za pośrednictwem sieci, podobnie jak komputer fizyczny lub wirtualny system. Jednakże, technologii i pojęcia dotyczące kontenerów znacząco różnią się od maszyn wirtualnych. Z punktu widzenia projektanta kontener muszą być traktowane więcej takich jak pojedynczego procesu. W rzeczywistości kontener ma jeden punkt wejścia dla jednego procesu.

Kontenery platformy docker (dla uproszczenia *kontenery*) można działa natywnie w systemie Linux i Windows. Podczas uruchamiania kontenerów regularnych, kontenery Windows można uruchomić tylko na hostach Windows (serwer hosta lub maszyny Wirtualnej) i kontenerów systemu Linux można uruchomić tylko na hostach z systemem Linux. Natomiast w nowszych wersjach systemu Windows Server i funkcji Hyper-V kontenerów kontenera systemu Linux można również uruchomić natywnie w systemie Windows Server przy użyciu technologii izolacji funkcji Hyper-V, która obecnie jest dostępna tylko w przypadku kontenery systemu Windows Server.

W najbliższej przyszłości środowiskach mieszanych, które mają kontenerów systemów Linux i Windows będzie możliwe nawet typowe.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Korzyści z kontenerów Windows istniejących aplikacji .NET

Korzyści z używania kontenerów Windows całkowicie są te same korzyści, który jest pobierany z kontenerów ogólnie rzecz biorąc. Używanie kontenerów Windows dotyczy znacznie poprawia elastyczność, przenoszenia i kontroli.

Istniejące aplikacje .NET odnoszą się do tych aplikacji, które zostały utworzone przy użyciu programu .NET Framework. Na przykład może być tradycyjnych aplikacji sieci web ASP.NET-nie korzystają z platformy .NET Core jest nowszy, która jest uruchamiana dla wielu platform w systemie Linux, Windows i MacOS.

Główne zależności w programie .NET Framework jest Windows. Zawiera również dodatkowej zależności, takich jak usługi IIS i System.Web w tradycyjnych ASP.NET.

Aplikacja .NET Framework, należy uruchomić na Windows, okres. Jeśli chcesz konteneryzowanie istniejącej aplikacji .NET Framework i nie może lub nie chcesz inwestować w przypadku migracji do programu .NET Core ("Jeśli działa on prawidłowo, nie dokonuj migracji go"), jest tylko opcja dla kontenerów Windows kontenery.

Dlatego jest jedną z głównych zalet kontenerów Windows, czy ich umożliwiają sposób modernizacji istniejących aplikacji .NET Framework, które są uruchomione na Windows do obsługi kontenerów. Ostatecznie kontenery Windows pobiera korzyści, których szukasz, korzystając z elastyczności kontenerów, przenoszenia i lepszej kontroli.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Wybierz system operacyjny do docelowych. Na podstawie NET kontenerów

Biorąc pod uwagę różnorodność systemów operacyjnych, które są obsługiwane przez platformy Docker, a także różnice między .NET Framework i .NET Core, powinien dotyczyć określonego systemu operacyjnego i określonych wersji, w oparciu o platformę, którego używasz.

Dla Windows można użyć systemu Windows Server Core lub Windows Nano Server. Te wersje Windows podaj inne cechy (np. usługi IIS i serwer samodzielnie hostowanej sieci web, takich jak Kestrel), które mogą być wymagane przez aplikacje platformy .NET Framework lub .NET Core.

W przypadku systemu Linux dystrybucje wielu są dostępne i jest obsługiwany w oficjalne obrazy Docker w programie .NET (na przykład Debian).

Rysunek 4 – 7 przedstawiono wersje systemów operacyjnych, które można wskazać, w zależności od wersji aplikacji programu .NET Framework.

![](./media/image7.png)

> **Rysunek 4 – 7.** Systemy operacyjne do obiektu docelowego, na podstawie wersji systemu .NET Framework

W scenariuszach migracji dla istniejące lub starsze aplikacje, które opierają się na aplikacjach .NET Framework zależności głównej znajdują się na Windows oraz usług IIS. Jedynym rozwiązaniem jest używać obrazów Docker opartych na systemie Windows Server Core i .NET Framework.

Po dodaniu nazwy obrazu do pliku Dockerfile, można wybrać system operacyjny i wersję za pomocą znacznika, tak jak w poniższych przykładach dotyczących obrazów kontenerów Windows oparte na programie .NET Framework:

> | **Tag** | **Wersja i system** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x, w systemie Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x, za pomocą dodatkowych dostosowań programu ASP.NET, w systemie Windows Server Core |

Dla platformy .NET Core (dla wielu platform dla systemów Linux i Windows) tagi powinien wyglądać następująco:

> | **Tag** | **Wersja i system**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 runtime-only on Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 na serwerze Windows Nano Server jest tylko do środowiska uruchomieniowego |

### <a name="multi-arch-images"></a>Wielu architektury obrazów

Począwszy od połowy 2017, pozwala też nowej funkcji na platformie Docker o nazwie [wielu arch](https://github.com/moby/moby/issues/15866) obrazów. Obrazy Docker w programie .NET core za pomocą architektury wielu tagów. Z pliku Dockerfile nie jest już pliki trzeba zdefiniować systemu operacyjnego, który przeznaczonych do pracy. Funkcja wielu architektury umożliwia pojedynczy tag ma być używany w wielu konfiguracjach maszyny. Na przykład za pomocą wielu arch, można użyć jeden tag wspólnej: **microsoft/dotnet:2.0.0-runtime**. W przypadku ściągania tego tagu środowiska kontenera systemu Linux, uzyskasz oparta na rozwiązaniu Debian obrazu. W przypadku ściągania tego tagu środowiska kontenera Windows, otrzymasz obrazów serwera Nano Server.

.NET Framework obrazów ponieważ tradycyjnych .NET Framework obsługuje tylko Windows nie można użyć funkcji wielu architektury.

## <a name="windows-container-types"></a>Typy kontenera Windows

Takich jak kontenery systemu Linux kontenerów systemu Windows Server są zarządzane przy użyciu aparatu platformy Docker. Inaczej niż w przypadku kontenerów systemu Linux Windows kontenery obejmują dwa typy innego kontenera lub uruchomić razy od systemu Windows Server i izolacji funkcji Hyper-V.

**Kontenery systemu Windows Server**: Zapewnia izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra hosta kontenera i wszystkie kontenery, które są uruchomione na hoście. Te kontenery nie są oferowane w granicach zabezpieczeń szkodliwy i nie powinny być używane do izolowania niezaufanego kodu. Ze względu na miejsce udostępnionego jądra te kontenery wymagają tę samą wersję jądra i konfiguracji.

**Izolacji funkcji Hyper-V**: Rozszerza izolacja świadczona przez kontenery systemu Windows Server, uruchamiając każdego kontenera na wysoce zoptymalizowanej maszynie Wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest udostępniony za pomocą innych kontenerów w tym samym hoście. Te kontenery są przeznaczone do szkodliwy hostingu wielodostępnego, za pomocą tego samego gwarancji bezpieczeństwa maszyny wirtualnej. Ponieważ te kontenery nie udostępnia jądra hosta lub innych kontenerów na hoście, można uruchomić jądra, przy użyciu różnych wersji i konfiguracji (z obsługiwanych wersji). Na przykład wszystkie kontenery Windows w systemie Windows 10 umożliwia korzystanie z wersji jądra systemu Windows Server i konfiguracja izolacji funkcji Hyper-V.

Uruchamianie kontenera na Windows z użyciem lub bez izolacji funkcji Hyper-V jest decyzja czasu wykonywania. Możesz wybrać opcję utworzenia kontenera za pomocą izolacji funkcji Hyper-V początkowo i w czasie wykonywania, chcesz uruchomić go jako kontener systemu Windows Server.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Dokumentacja usługi kontenerów Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Podstawowe informacje dotyczące kontenerów Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Grafika informacyjna: Firma Microsoft i kontenery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystem kontenera na platformie Azure

W poprzednich sekcjach zostały wyjaśnione, co to są korzyści z kontenerów platformy Docker oraz szczegółowe informacje na temat obrazów kontenera dla aplikacji .NET. Wszystko to ogólne informacje jest niezbędne, aby tworzyć lub konteneryzowanie aplikacji.
Jednak Jeśli zastanawiasz się nad środowisko wdrażania w środowisku produkcyjnym lub nawet w środowiskach pytań i odpowiedzi oraz tworzenia i testowania, Microsoft Azure oferuje otwarte i szerokiej rozmaite opcje, z ekosystemem pełną kontenera w chmurze (pokazane na poniższym diagramie). W zależności od potrzeb konkretnej aplikacji należy wybrać co najmniej innego produktu Azure.

![](./media/image7.5.png)

> **Rysunek 4 — 7.5.** Ekosystem kontenera na platformie Azure

W ekosystemie kontenera na platformie Azure, następujące produkty obsługę kontenerów, które są uważane za infrastrukturę:
- **Usługa Azure Container Instances (ACI)**
- **Usługa Azure Virtual Machines** (z obsługą kontenera)
- **Usługa Azure Virtual Machine Scale Sets** (z obsługą kontenera)

Z tych trzech usługa ACI zapewnia ogromne korzyści jest fakt, że nie trzeba utrzymywać podstawowego systemu operacyjnego nie konieczności uaktualnianie/poprawianie, itp., ale ACI nadal znajduje się na poziomie infrastruktury, jak lepiej wyjaśniono w kolejnych sekcjach tego podręcznika.

Dostępne są następujące produkty z obsługi kontenerów platformy Azure, które są w tym samym czasie więcej umieszczony w modelu PaaS (platforma jako usługa), poziom:

- **Usługa Azure App Service**
- **Azure Kubernetes Service (AKS i usługi ACS)**
- **Azure Batch** 

Następnie usługi Azure Container Registry to rejestr kontenera skalowalne wysokiej hostowanych na platformie Azure, korzystających z wszystkie poprzednie produkty podczas rejestrowania i wdrażania obrazów kontenerów niestandardowych.

Ponadto z kontenerów, będzie można korzystać innych usług zarządzanych na platformie Azure, takich jak Azure SQL Database, Azure Redis cache, Azure Cosmos DB itd. Ponadto w portalu Azure Marketplace, takich jak usługi Cloud Foundry i OpenShift, gdzie można również użyć kontenerów w ramach platformy Azure są dostępne rozwiązania innych firm/platform. 

W kolejnych sekcjach możesz eksplorować zalecenia firmy Microsoft na tym, kiedy należy używać każdego z tych produktów platformy Azure i rozwiązania, szczególnie w przypadku, gdy obsługiwane kontenerów Windows.

>[!div class="step-by-step"]
>[Poprzednie](what-about-cloud-native-applications.md)
>[dalej](when-not-to-deploy-to-windows-containers.md)
