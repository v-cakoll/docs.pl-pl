---
title: Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 829f33aba14d79d7d9003d1ac7472a19060d401a
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows

Wdrożenia, które są oparte na kontenery systemu Windows są stosowane do zoptymalizowanych pod kątem chmury aplikacje i aplikacje natywne chmury.

Jednak w tym przewodniku, a szczególnie w poniższych sekcjach, przede wszystkim koncentruje się on na używanie kontenerów systemu Windows dla *zoptymalizowanych pod kątem chmury* aplikacji, których nie ma potrzeby rearchitect aplikacji.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenerami? (Linux lub Windows)

Kontenery służą do opakowywania aplikacji w izolowanej pakietu. W jego kontenera aplikacji nie ma wpływu na aplikacje lub procesy, które znajdują się poza kontener. Wszystkie elementy aplikacji zależy od do uruchomienia pomyślnie procesu znajduje się wewnątrz kontenera. Wszędzie tam, gdzie może przenieść kontenera, aplikacji będzie zawsze być spełnione wymagania, pod względem bezpośrednich zależności, ponieważ jest on powiązany z wszystko, co jest wymagane do uruchomienia (zależności biblioteki, środowisk uruchomieniowych itd.).

Główną cechą kontenera jest fakt, że środowisko taka sama we wszystkich wdrożeniach różnych ponieważ sam pojemnik pochodzi z zależnościami, które są niezbędne. Debugowanie aplikacji na tym komputerze i wdrożyć go na inny komputer, z tym samym środowisku gwarancji.

Kontener jest wystąpieniem obrazu kontenera. Obraz kontenera to sposób pakietu aplikacji lub usługi (takie jak migawki), a następnie wdrożyć je w sposób niezawodny i odtworzenia. Można powiedzieć, że Docker jest nie tylko technologii it również przez zasady i procesu.

Jak kontenery codziennie stają się częściej, stają się one branżowym "jednostka wdrożenia".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Korzyści wynikające z kontenerów (aparatem platformy Docker w systemie Linux lub Windows)

Kompilowanie aplikacji przy użyciu kontenerów, które również mogą być zdefiniowane jako lekkie oferty bloków konstrukcyjnych znaczne zwiększenie w elastyczność tworzenia i wysyłania, oraz uruchamianie dowolnej aplikacji we dowolnej infrastruktury.

Bez kontenerów należy wykonać dowolną aplikację od projektowania do produkcji w przypadku niewielkiego lub żadnego zmiany kodu, dzięki użyciu Docker Integracja narzędzi dla deweloperów, systemów operacyjnych i chmury.

Podczas wdrażania maszyn wirtualnych zwykły prawdopodobnie już ma metody w przypadku wdrażania aplikacji ASP.NET do maszyn wirtualnych. Prawdopodobne jest, jednak, że metodę obejmuje wiele czynności ręcznej lub złożonych zautomatyzowanych procesów przy użyciu narzędzia wdrażania, takiego jak Puppet lub podobnego narzędzia. Może być konieczne wykonywanie zadań takich jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami i uruchamianie programów instalacji interakcyjnej opartych na konfiguracje msi, a następnie testowania. Te czynności w ramach wdrożenia Dodaj czasu i ryzyka do wdrożenia. Zostanie wyświetlone błędy przy każdym zależność nie znajduje się w środowisku docelowym.

W kontenerach Windows pełni jest zautomatyzowany proces tworzenia pakietów aplikacji. Kontenery systemu Windows jest oparta na platformy Docker oferuje aktualizacje automatyczne i wycofań wdrożeń kontenera. Główne poprawy jakości, uzyskasz od przy użyciu aparatu Docker jest tworzenie obrazów, które są takie jak migawki aplikacji, ze wszystkimi zależnościami. Obrazy są obrazy usługi Docker (obrazu systemu Windows kontenera, w tym przypadku). Obrazy uruchamiania aplikacji ASP.NET w kontenerach, bez po powrocie do kodu źródłowego. Migawki kontenera staje się jednostką wdrożenia.

W wielu organizacjach są containerizing istniejące aplikacje wbudowanymi z następujących powodów:

-   **Zwolnij elastyczność za pośrednictwem ulepszone wdrażanie**. Kontenery oferują kontrakt między i spójne wdrażanie. Korzystając z kontenerów, nie będzie słyszysz deweloperzy powiedzieć, "Działa na komputerze, dlaczego nie w środowisku produkcyjnym?" Mogą one powiedzieć, "Jest uruchamiana jako kontener, więc zostanie uruchomiony w środowisku produkcyjnym." Opakowanej aplikacji ze wszystkimi zależnościami, można wykonać w dowolnym środowisku obsługiwanych na podstawie kontenera. Zostanie on uruchomiony sposób zamierzano uruchamiane w wszystkich celów wdrożenia (deweloperów, pytań i odpowiedzi, przemieszczania i produkcji). Kontenery wyeliminować większość frictions łączącymi się z jednego etapu do drugiego, co znacznie zwiększa wdrożenia, i można wysłać szybciej.

-   **Obniżenie kosztów**. Kontenery prowadzić do obniżenia kosztów, albo poprzez konsolidacji i usunięcia istniejącego sprzętu lub uruchomienie aplikacji w zwiększeniu na jednostkę sprzętu.

-   **Przenośność**. Kontenery są moduły i przenośnych. Kontenery docker są obsługiwane przez dowolnego systemu operacyjnego serwera (Linux i Windows), w dowolnym głównych chmury publicznej (Microsoft Azure, Amazon AWS, Google, IBM) i w lokalnej i prywatnej lub środowisk chmury hybrydowej.

-   **Formant**. Kontenery oferują elastyczną i bezpieczną środowiska, które są kontrolowane na poziomie kontenera. Kontener można zabezpieczony, izolowany i nawet ograniczony przez ustawienia ograniczenia zasad wykonywania w kontenerze. Zgodnie z opisem w sekcji o kontenery systemu Windows kontenery systemu Windows Server 2016 i funkcji Hyper-V oferuje enterprise dodatkowe opcje pomocy technicznej.

Wprowadzono znaczne ulepszenia w elastyczności, przenośność i kontroli ostatecznie prowadzić do zmniejszenia kosztów, gdy używanie kontenerów do opracowywania i zachowanie aplikacji.

## <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projekt open source](https://github.com/docker/docker) który automatyzuje wdrażania aplikacji jako przenośny, samowystarczalne kontenerów, które można uruchomić w chmurze lub lokalnie. Docker jest również [firmy](https://www.docker.com/) wspiera i rozwoju tej technologii. Firma działa we współpracy z chmury, Linux i dostawców systemu Windows, takie jak Microsoft.

![](./media/image6.png)

> **Rysunek 4 – 6.** Docker wdraża kontenerów na wszystkie warstwy chmury hybrydowej

Osobie zapoznać się z maszynami wirtualnymi kontenerów może się wydawać niezwykle podobne. Kontener ma zainstalowany system operacyjny, ma system plików i jest dostępna za pośrednictwem sieci, podobnie jak komputer fizyczny lub wirtualny system. Jednak technologii i pojęć kontenery różnią się znacząco od maszyny wirtualnej. Z punktu widzenia developer kontener muszą być traktowane więcej takich jak jednego procesu. W rzeczywistości kontener ma jeden punkt wejścia dla jednego procesu.

Kontenery docker (dla uproszczenia *kontenery*) można uruchomić natywnie w systemie Linux i Windows. Podczas uruchamiania regularne kontenery, kontenery systemu Windows można uruchomić tylko na hostach z systemem Windows (serwera hosta lub maszyny Wirtualnej), a kontenery systemu Linux można uruchomić tylko na hostach z systemem Linux. Jednak w nowszych wersjach systemu Windows Server i Hyper-V kontenerów kontenera Linux również uruchomić natywnie w systemie Windows Server przy użyciu technologii Hyper-V izolacji, który obecnie jest dostępne tylko w kontenery systemu Windows Server.

W niedalekiej przyszłości środowiskach mieszanych, w których kontenerów zarówno systemu Linux i Windows będzie możliwe, a nawet typowe.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Korzyści wynikające z kontenerów Windows istniejących aplikacji .NET

Korzyści wynikające ze stosowania kontenery systemu Windows są zasadniczo takich samych korzyści, uzyskasz z kontenerów ogólnie. Używanie kontenerów systemu Windows jest o znacznie poprawia elastyczności, przenośność i kontroli.

Istniejące aplikacje .NET odnosi się do tych aplikacji, które zostały utworzone przy użyciu programu .NET Framework. Na przykład może być tradycyjne aplikacje sieci web ASP.NET-nie korzystają z platformy .NET Core, który jest nowszy i uruchamia i platform w systemie Linux, Windows i MacOS.

Systemu Windows jest głównym zależność w programie .NET Framework. Ma również dodatkowej zależności, takich jak usługi IIS i System.Web w tradycyjnych ASP.NET.

Aplikacja .NET Framework, należy uruchomić w systemie Windows, okres. Jeśli chcesz containerize istniejących aplikacji .NET Framework i nie może lub nie chce inwestycji w przypadku migracji do platformy .NET Core ("Jeśli działa on prawidłowo, nie jest wykonywana migracja go"), jedyną dostępną dla kontenerów jest użycie kontenery systemu Windows.

Dlatego jest jedną z głównych zalet kontenery systemu Windows, że ich umożliwiają sposobem modernizacji istniejących aplikacji .NET Framework uruchomionych na Windows przez przechowywanie w kontenerach. Ostatecznie kontenery systemu Windows pobiera korzyści, które chcesz uzyskać przy użyciu kontenerów elastyczności, przenośność i lepszą kontrolę.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Wybierz system operacyjny do miejsca docelowego z. Na podstawie NET kontenerów

Biorąc pod uwagę różnorodność systemów operacyjnych, które są obsługiwane przez Docker, a także różnice między .NET Framework i .NET Core, docelowych określonego systemu operacyjnego oraz wersje określone w ramach, którego używasz.

W systemie Windows można użyć systemu Windows Server Core lub serwerze Nano systemu Windows. Te wersje systemu Windows zawierają różnej charakterystyce (np. usługi IIS i serwer sieci web siebie, takie jak Kestrel), które mogą być wymagane przez aplikacje .NET Framework lub .NET Core.

Dla systemu Linux wiele dystrybucjach są dostępne i obsługiwane w oficjalnego obrazy usługi .NET Docker (na przykład Debian).

Rysunek 4-7 przedstawiono wersji systemu operacyjnego, które można wskazać, w zależności od wersji aplikacji programu .NET Framework.

![](./media/image7.png)

> **Rysunek 4-7.** Systemy operacyjne do docelowej wersji .NET Framework

W scenariuszach migracji istniejące lub starsze aplikacje, które są oparte na aplikacji .NET Framework głównego zależności są w systemach Windows i usług IIS. Jedyną opcją jest do użycia obrazy usługi Docker oparte na systemie Windows Server Core i .NET Framework.

Po dodaniu nazwy obrazu do pliku plik Dockerfile wersja systemu operacyjnego i można wybrać przy użyciu tagu, na przykład w przypadku obrazów kontenera systemu Windows opartych na programie .NET Framework:

> | **Tag** | **Wersja systemu i** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x w systemie Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x z dodatkowe dostosowanie ASP.NET, w systemie Windows Server Core |

Dla platformy .NET Core (i platform dla systemu Linux i Windows) znaczniki będzie wyglądać następująco:

> | **Tag** | **Wersja systemu i**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 runtime-only on Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 tylko do środowiska uruchomieniowego w systemie Windows Nano Server |

### <a name="multi-arch-images"></a>Wiele architektury obrazów

Począwszy od połowy 2017, można też użyć nowej funkcji w nazwie Docker [wielu arch](https://github.com/moby/moby/issues/15866) obrazów. .NET core Docker obrazów za pomocą wielu architektury znaczników. Twoje plik Dockerfile już plików trzeba zdefiniować systemu operacyjnego, który ma być przeznaczona dla. Funkcja wielu architektury umożliwia jeden tag do użycia przez wiele konfiguracji komputera. Na przykład w wielu arch, możesz użyć jeden tag wspólnej: **microsoft/dotnet:2.0.0-runtime**. Jeśli ściągnięcia tagu ze środowiska kontenera systemu Linux, możesz uzyskać Debian na podstawie obrazu. Jeśli ściągnięcia tagu z środowiska kontenera systemu Windows, możesz uzyskać obrazu na serwerze Nano.

Obrazy .NET Framework ponieważ tradycyjnych .NET Framework obsługuje tylko systemu Windows, nie można używać wielu architektury funkcji.

## <a name="windows-container-types"></a>Typy kontenera systemu Windows

Jak kontenery Linux kontenery systemu Windows Server są zarządzane przy użyciu aparatu Docker. W przeciwieństwie do kontenerów Linux kontenery systemu Windows zawierają dwa różne typy kontenera lub uruchom kontenery razy-systemu Windows Server i izolacja funkcji Hyper-V.

**Kontenery systemu Windows Server**: zapewnia izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra hosta kontenera i wszystkich kontenerów, które są uruchomione na hoście. Kontenery nie udostępniają granicy zabezpieczeń szkodliwy i nie powinny być używane do izolowania kodzie niezaufanym. Ze względu na miejsce udostępnione jądra kontenery wymagają konfiguracji i tej samej wersji jądra.

**Funkcja Hyper-V izolacji**: rozszerzenie izolacji udostępniane przez kontenery systemu Windows Server, uruchamiając każdy kontener zoptymalizowanego maszyny wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest współużytkowany z innymi kontenerów na tym samym hoście. Kontenery zostały zaprojektowane dla szkodliwy hosting wielodostępnym, z taką samą pewność zabezpieczeń maszyny wirtualnej. Ponieważ kontenery nie udostępniać jądra hosta lub innych kontenerów na hoście, mogą uruchamiać jądra różne wersje i konfiguracji (z obsługiwanych wersji). Na przykład wszystkie kontenery systemu Windows w systemie Windows 10 użyć izolacji funkcji Hyper-V mogą korzystać z wersji jądra systemu Windows Server i konfiguracji.

Uruchamianie kontener w systemie Windows z lub bez izolacji funkcji Hyper-V jest decyzji czasu wykonywania. Możesz wybrać opcję utworzenia kontenera początkowo izolacji funkcji Hyper-V i w czasie wykonywania, wybierz polecenie do uruchomienia go jako kontenera systemu Windows Server.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Dokumentacja kontenery systemu Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Podstawowe informacje na temat kontenery systemu Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **Infographic: Firma Microsoft i kontenery**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)


## <a name="the-container-ecosystem-in-azure"></a>Ekosystem kontenera na platformie Azure

W poprzednich sekcjach zostały wyjaśniono, zalet Docker kontenery są oraz szczegóły dotyczące obrazów określony kontener dla aplikacji .NET. Wszystkie te ogólne informacje jest niezbędne, aby można było utworzyć lub containerize aplikacji.
Rozważania na temat środowiska wdrożenia produkcyjnego lub nawet w środowiskach odpowiedzi na pytania i tworzenie/testowanie, Microsoft Azure zapewnia jednak otwarte i szeroki wybór możliwości, ekosystemu pełne kontenera, w chmurze (przedstawiono na poniższym diagramie). W zależności od potrzeb określonej aplikacji należy wybrać co najmniej innego produktu Azure.

![](./media/image7.5.png)

> **Rysunek 4-7.5.** Ekosystem kontenera na platformie Azure

Z ekosystemem kontenera na platformie Azure, następujące produkty Obsługa kontenerów, które są traktowane jako infrastruktury:
-   **Wystąpień kontenera platformy Azure (ACI)**
-   **Maszyny wirtualne platformy Azure** (z obsługą kontenera)
-   **Zestawy skalowania maszyny wirtualnej Azure** (z obsługą kontenera)

Z tych trzech ACI zapewnia ogromne korzyści jest fakt, że nie trzeba zachować podstawowego systemu operacyjnego, nie trzeba do uaktualnienia/poprawki, itp., ale ACI nadal znajduje się na poziomie infrastruktury, jak lepiej wyjaśniono w kolejnych sekcjach tego podręcznika.

Produkty Azure kontenerów pomocnicze, które są w tym samym czasie więcej znajduje się w PaaS (platforma jako usługa) poziomu są:

-   **Usługa aplikacji Azure**
-   **Usługa Azure Kubernetes (AKS i ACS)**
-   **Sieć szkieletowa usług Azure** 
-   **Azure Batch** 

Następnie rejestru kontenera Azure jest hostowana na platformie Azure korzystające ze wszystkich produktów poprzedniej podczas rejestracji i wdrażanie obrazów niestandardowych kontenera rejestru wysokiej skalowalności kontenera.

Ponadto z kontenerów, będzie można korzystać z innych usług zarządzanych na platformie Azure, takich jak bazy danych SQL Azure, pamięć podręczna Azure Redis, Azure DB rozwiązania Cosmos, itp. Dodatkowo w portalu Azure Marketplace, takich jak chmury Foundry i OpenShift, gdzie można również użyć kontenery w obrębie platformy Azure są dostępne rozwiązania innych firm/platform. 

W kolejnych sekcjach można sprawdzić zalecenia firmy Microsoft na tym, kiedy należy używać każdego z tych produktów platformy Azure i rozwiązań, szczególnie gdy kontenery systemu Windows.


>[!div class="step-by-step"]
[Poprzednie](what-about-cloud-native-applications.md)
[dalej](when-not-to-deploy-to-windows-containers.md)
