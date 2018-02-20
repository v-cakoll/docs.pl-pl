---
title: "Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9a30605313c06542fabf9689f700ed726445f57
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenery systemu Windows

Wdrożenia, które są oparte na kontenery systemu Windows mają zastosowanie do aplikacji zoptymalizowanych pod kątem chmury, chmury native oraz aplikacje gotowe do chmury DevOps.

W tym przewodniku, a w poniższych sekcjach, możemy skupić się na używanie kontenerów systemu Windows dla *gotowe DevOps chmury* aplikacji, gdy Podnieś i przesunięcia istniejących aplikacji .NET.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenerami? (Linux lub Windows)

Kontenery służą do opakowywania aplikacji w izolowanej pakietu. W jego kontenera aplikacji nie ma wpływu na aplikacje lub procesy, które znajdują się poza kontener. Wszystkie elementy aplikacji zależy od do uruchomienia pomyślnie procesu znajduje się wewnątrz kontenera. Wszędzie tam, gdzie może przenieść kontenera, aplikacji będzie zawsze być spełnione wymagania, pod względem bezpośrednich zależności, ponieważ jest on powiązany z wszystko, co jest wymagane do uruchomienia (zależności biblioteki, środowisk uruchomieniowych itd.).

Główną cechą kontenera jest fakt, że środowisko taka sama we wszystkich wdrożeniach różnych ponieważ sam pojemnik pochodzi z zależnościami, które są niezbędne. Oznacza to debugowanie aplikacji na komputerze, a następnie wdrożyć go na innym komputerze, z tym samym środowisku gwarancji.

Kontener jest wystąpieniem obrazu kontenera. Obraz kontenera to sposób pakietu aplikacji lub usługi (takie jak migawki), a następnie wdrożyć je w sposób niezawodny i odtworzenia. Można powiedzieć, że Docker jest nie tylko technologii it również przez zasady i procesu.

Jak kontenery codziennie stają się częściej, stają się one branżowym "jednostka wdrożenia".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Korzyści wynikające z kontenerów (aparatem platformy Docker w systemie Linux lub Windows)

Kompilowanie aplikacji przy użyciu kontenerów, które również mogą być zdefiniowane jako lekkie oferty bloków konstrukcyjnych znaczne zwiększenie w elastyczność tworzenia i wysyłania, oraz uruchamianie dowolnej aplikacji we dowolnej infrastruktury.

Bez kontenerów należy wykonać dowolną aplikację od projektowania do produkcji w przypadku niewielkiego lub żadnego zmiany kodu, dzięki użyciu Docker Integracja narzędzi dla deweloperów, systemów operacyjnych i chmury.

Podczas wdrażania maszyn wirtualnych zwykły prawdopodobnie już ma metody w przypadku wdrażania aplikacji ASP.NET do maszyn wirtualnych. Prawdopodobne jest, jednak, że metodę obejmuje wiele czynności ręcznej lub złożonych zautomatyzowanych procesów przy użyciu narzędzia wdrażania, takiego jak Puppet lub podobnego narzędzia. Może być konieczne wykonywanie zadań takich jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami i uruchamianie programów instalacji interakcyjnej opartych na konfiguracje msi, a następnie testowania. Te czynności w ramach wdrożenia Dodaj czasu i ryzyka do wdrożenia. Zostanie wyświetlone błędy przy każdym zależność nie znajduje się w środowisku docelowym.

W kontenerach Windows pełni jest zautomatyzowany proces tworzenia pakietów aplikacji. Kontenery systemu Windows jest oparta na platformy Docker oferuje aktualizacje automatyczne i wycofań wdrożeń kontenera. Główne poprawy jakości, uzyskasz od przy użyciu aparatu Docker jest tworzenie obrazów, które są takie jak migawki aplikacji, ze wszystkimi zależnościami. Obrazy są obrazy usługi Docker (obrazu systemu Windows kontenera, w tym przypadku). Obrazy uruchamiania aplikacji ASP.NET w kontenerach, bez po powrocie do kodu źródłowego. Migawki kontenera staje się jednostką wdrożenia.

Wiele organizacji są containerizing istniejące aplikacje wbudowanymi z następujących powodów:

-   **Zwolnij elastyczność za pośrednictwem ulepszone wdrażanie**. Kontenery oferują kontrakt między i spójne wdrażanie. Korzystając z kontenerów, nie będzie słyszysz deweloperzy powiedzieć, "Działa na komputerze, dlaczego nie w środowisku produkcyjnym?" Można po prostu mówią, "Jest uruchamiana jako kontener, więc będą uruchamiane w środowisku produkcyjnym." Opakowanej aplikacji ze wszystkimi zależnościami, można wykonać w dowolnym środowisku obsługiwanych na podstawie kontenera. Zostanie on uruchomiony sposób zamierzano uruchamiane w wszystkich celów wdrożenia (deweloperów, pytań i odpowiedzi, przemieszczania i produkcji). Kontenery wyeliminować większość frictions łączącymi się z jednego etapu do drugiego, co znacznie zwiększa wdrożenia, i można wysłać szybciej.

-   **Obniżenie kosztów**. Kontenery prowadzić do obniżenia kosztów, albo poprzez konsolidacji i usunięcia istniejącego sprzętu lub uruchomienie aplikacji w zwiększeniu na jednostkę sprzętu.

-   **Przenośność**. Kontenery są moduły i przenośnych. Kontenery docker są obsługiwane przez dowolnego systemu operacyjnego serwera (Linux i Windows), w dowolnym głównych chmury publicznej (Microsoft Azure, Amazon AWS, Google, IBM) i w lokalnej i prywatnej lub środowisk chmury hybrydowej.

-   **Formant**. Kontenery oferują elastyczną i bezpieczną środowiska, które są kontrolowane na poziomie kontenera. Kontener można zabezpieczony, izolowany i nawet ograniczony przez ustawienia ograniczenia zasad wykonywania w kontenerze. Zgodnie z opisem w sekcji o kontenery systemu Windows kontenery systemu Windows Server 2016 i funkcji Hyper-V oferuje enterprise dodatkowe opcje pomocy technicznej.

Wprowadzono znaczne ulepszenia w elastyczności, przenośność i kontroli ostatecznie prowadzić do zmniejszenia kosztów, gdy używanie kontenerów do opracowywania i zachowanie aplikacji.

## <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projekt open source](https://github.com/docker/docker) który automatyzuje wdrażania aplikacji jako przenośny, samowystarczalne kontenerów, które można uruchomić w chmurze lub lokalnie. Jest także docker [firmy](https://www.docker.com/) wspiera i rozwoju tej technologii. Firma działa we współpracy z chmury, Linux i dostawców systemu Windows, takie jak Microsoft.

![](./media/image6.png)

> **Rysunek 4 – 6.** Docker wdraża kontenerów na wszystkie warstwy chmury hybrydowej

Osobie zapoznać się z maszynami wirtualnymi kontenerów może się wydawać niezwykle podobne. Kontener ma zainstalowany system operacyjny, ma system plików i jest dostępna za pośrednictwem sieci, podobnie jak komputer fizyczny lub wirtualny system. Jednak technologii i pojęć kontenery różnią się znacząco od maszyny wirtualnej. Z punktu widzenia developer kontener muszą być traktowane więcej takich jak jednego procesu. W rzeczywistości kontener ma jeden punkt wejścia dla jednego procesu.

Kontenery docker (dla uproszczenia *kontenery*) można uruchomić natywnie w systemie Linux i Windows. Podczas uruchamiania regularne kontenery, kontenery systemu Windows można uruchomić tylko na hostach z systemem Windows (serwera hosta lub maszyny Wirtualnej), a kontenery systemu Linux można uruchomić tylko na hostach z systemem Linux. Jednak w nowszych wersjach systemu Windows Server i Hyper-V kontenerów kontenera Linux również uruchomić natywnie w systemie Windows Server przy użyciu technologii Hyper-V izolacji, który obecnie jest dostępne tylko w kontenery systemu Windows Server.

W niedalekiej przyszłości środowiskach mieszanych, w których kontenerów zarówno systemu Linux i Windows będzie możliwe, a nawet typowe.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Korzyści wynikające z kontenerów Windows istniejących aplikacji .NET

Korzyści wynikające ze stosowania kontenery systemu Windows są zasadniczo takich samych korzyści, uzyskasz z kontenerów ogólnie. Używanie kontenerów systemu Windows jest o znacznie poprawia elastyczności, przenośność i kontroli.

Przy omawianiu istniejących aplikacji .NET możemy przede wszystkim oznacza tradycyjne aplikacje, które zostały utworzone przy użyciu programu .NET Framework. Na przykład może być tradycyjne aplikacje sieci web ASP.NET-nie korzystają z platformy .NET Core, który jest nowszy i uruchamia i platform w systemie Linux, Windows i MacOS.

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

> | Tag | **Wersja systemu i** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x w systemie Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x z dodatkowe dostosowanie ASP.NET, w systemie Windows Server Core |

Dla platformy .NET Core (i platform dla systemu Linux i Windows) znaczniki będzie wyglądać następująco:

> | Tag | **Wersja systemu i**
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

>[!div class="step-by-step"]
[Poprzednie](how-to-deploy-existing-net-apps-to-azure-app-service.md)
[dalej](when-not-to-deploy-to-windows-containers.md)
