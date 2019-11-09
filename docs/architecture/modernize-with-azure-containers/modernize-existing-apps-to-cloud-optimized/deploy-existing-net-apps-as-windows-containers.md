---
title: Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "73089558"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows

Wdrożenia, które są oparte na kontenerach systemu Windows, mają zastosowanie do aplikacji zoptymalizowanych pod kątem chmury i aplikacji natywnych w chmurze.

Jednak w tym przewodniku i szczególnie w poniższych sekcjach, w szczególności, koncentruje się na korzystaniu z kontenerów systemu Windows dla aplikacji *zoptymalizowanych pod kątem chmury* , w których nie trzeba ponownie tworzyć architektury aplikacji.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenery? (Linux lub Windows)

Kontenery umożliwiają Zawijanie aplikacji do własnego pakietu izolowanego. W kontenerze aplikacja nie ma wpływ na aplikacje lub procesy, które istnieją poza kontenerem. Wszystkie elementy, od których zależy aplikacja, mogą działać prawidłowo, ponieważ proces znajduje się w kontenerze. W każdym przypadku, gdy kontener może zostać przeniesiony, wymagania aplikacji zawsze będą spełnione, w odniesieniu do bezpośrednich zależności, ponieważ są powiązane z wszystko, czego potrzebuje do uruchomienia (zależności biblioteki, środowiska uruchomieniowe itd.).

Główną cechą kontenera jest to, że środowisko jest takie samo w różnych wdrożeniach, ponieważ sam kontener zawiera wszystkie wymagane zależności. Można debugować aplikację na maszynie, a następnie wdrożyć ją na innym komputerze z gwarancją tego samego środowiska.

Kontener jest wystąpieniem obrazu kontenera. Obraz kontenera to sposób na spakowanie aplikacji lub usługi (na przykład migawki), a następnie wdrożenie jej w sposób niezawodny i powtarzalny. Można powiedzieć, że platforma Docker nie jest tylko technologią — jest to również bioplika i proces.

Jako że kontenery codziennie stają się bardziej popularne, stają się one jednostką wdrożenia ".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Zalety kontenerów (aparat platformy Docker w systemie Linux lub Windows)

Tworzenie aplikacji przy użyciu kontenerów, które również mogą być zdefiniowane jako uproszczone bloki konstrukcyjne — oferuje znaczący wzrost elastyczności podczas tworzenia, wysyłania i uruchamiania dowolnych aplikacji w każdej infrastrukturze.

Za pomocą kontenerów można utworzyć dowolną aplikację od projektowania do produkcji z niewielką lub bez zmiany kodu, dzięki integracji platformy Docker między narzędziami deweloperskimi firmy Microsoft, systemami operacyjnymi i chmurą.

W przypadku wdrażania na zwykłych maszynach wirtualnych prawdopodobnie masz już metodę wdrażania aplikacji ASP.NET na maszynach wirtualnych. Istnieje najprawdopodobniej, że metoda obejmuje wiele ręcznych kroków lub złożonych zautomatyzowanych procesów przy użyciu narzędzia do wdrażania, takiego jak Puppet, lub podobnego narzędzia. Może być konieczne wykonanie zadań, takich jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami oraz uruchamianie programów instalacji interaktywnej na podstawie instalacji MSI, a następnie testowanie. Wszystkie te kroki w rozmieszczeniu umożliwiają dodanie czasu i ryzyka wdrożenia. Wystąpią błędy, gdy zależność nie jest obecna w środowisku docelowym.

W kontenerach systemu Windows proces tworzenia pakietów aplikacji jest w pełni zautomatyzowany. Kontenery systemu Windows bazują na platformie Docker, która oferuje automatyczne aktualizacje i wycofywanie w ramach wdrożeń kontenerów. Głównym ulepszeniem uzyskanym z używania aparatu platformy Docker jest tworzenie obrazów, takich jak migawki aplikacji, wraz ze wszystkimi jej zależnościami. Obrazy to obrazy platformy Docker (w tym przypadku obraz kontenera systemu Windows). Obrazy uruchamiają aplikacje ASP.NET w kontenerach bez powrotu do kodu źródłowego. Migawka kontenera jest jednostką wdrożenia.

Wiele organizacji konteneryzowania istniejące aplikacje monolityczne z następujących powodów:

- Zwiększ **elastyczność dzięki ulepszonemu wdrożeniu**. Kontenery oferują spójną umowę dotyczącą wdrożenia między programowaniem i operacjami. Gdy korzystasz z kontenerów, nie słyszą Cię deweloperzy, "działa na mojej maszynie, dlaczego nie w środowisku produkcyjnym?". Mogą oni powiedzieć, że jest uruchamiana jako kontener, więc będzie działać w środowisku produkcyjnym. Spakowana aplikacja wraz ze wszystkimi jej zależnościami może być wykonywana w dowolnym obsługiwanym środowisku opartym na kontenerach. Zostanie ona uruchomiona w taki sposób, aby działała we wszystkich celach wdrożenia (dev, pytań i odpowiedzi, przemieszczanie, produkcja). Kontenery eliminują największe tarcie, gdy przechodzą z jednego etapu do następnego, co znacznie ulepsza wdrożenie i można je wysłać szybciej.

- **Obniżki kosztów**. Kontenery prowadzą do obniżenia kosztów, konsolidacji i usuwania istniejącego sprzętu lub uruchamiania aplikacji o wyższej gęstości na jednostkę sprzętu.

- **Przenośność**. Kontenery są modularne i przenośne. Kontenery platformy Docker są obsługiwane w dowolnym systemie operacyjnym serwera (Linux i Windows) w dowolnej głównej chmurze publicznej (Microsoft Azure, Amazon AWS, Google, IBM) oraz w środowiskach lokalnych i prywatnych lub hybrydowych.

- **Kontrolka**. Kontenery oferują elastyczne i bezpieczne środowisko, które jest kontrolowane na poziomie kontenera. Kontener może być zabezpieczony, izolowany, a nawet ograniczony przez ustawienie zasad ograniczeń wykonywania w kontenerze. Zgodnie z opisem w sekcji dotyczącej kontenerów systemu Windows, Windows Server 2016 i kontenerów funkcji Hyper-V oferują dodatkowe opcje pomocy technicznej dla przedsiębiorstw.

Znaczące ulepszenia elastyczności, przenośności i kontroli mogą ostatecznie prowadzić do znacznego obniżenia kosztów podczas tworzenia i konserwowania aplikacji przy użyciu kontenerów.

## <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) to [projekt typu "open source"](https://github.com/docker/docker) , który automatyzuje wdrażanie aplikacji jako przenośnych, samowystarczalnych kontenerów, które mogą działać w chmurze lub lokalnie. Platforma Docker to również [firma](https://www.docker.com/) , która wspiera i rozwija tę technologię. Firma współpracuje z dostawcami chmury, Linux i Windows, w tym z firmą Microsoft.

![Diagram przedstawiający sposób wdrażania kontenerów w chmurze hybrydowej przez platformę Docker.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Rysunek 4-6.** Platforma Docker wdraża kontenery we wszystkich warstwach chmury hybrydowej

W przypadku osób zaznajomionych z maszynami wirtualnymi kontenery mogą wydawać się niezwykle podobne. W kontenerze jest uruchomiony system operacyjny, ma system plików i można uzyskać do niego dostęp za pośrednictwem sieci, podobnie jak w przypadku fizycznego lub wirtualnego systemu komputerowego. Jednak technologia i pojęcia związane z kontenerami są znacznie różne od maszyn wirtualnych. Z punktu widzenia dewelopera kontener musi być traktowany jak pojedynczy proces. W rzeczywistości kontener ma jeden punkt wejścia dla jednego procesu.

Kontenery platformy Docker (dla prostoty, *kontenerów*) mogą działać natywnie w systemach Linux i Windows. W przypadku uruchamiania zwykłych kontenerów kontenery systemu Windows mogą być uruchamiane tylko na hostach z systemem Windows (na serwerze hosta lub maszynie wirtualnej), a kontenery systemu Linux można uruchamiać tylko na hostach z systemem Linux. Jednak w ostatnich wersjach systemu Windows Server i kontenerów funkcji Hyper-V w systemie Windows Server można natywnie uruchamiać kontener z systemem Linux przy użyciu technologii izolacji funkcji Hyper-V, która jest obecnie dostępna tylko w kontenerach systemu Windows Server.

W najbliższej przyszłości środowiska mieszane, które mają zarówno kontenery systemu Linux, jak i Windows, będą dostępne, a nawet wspólne.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Zalety kontenerów systemu Windows dla istniejących aplikacji .NET

Korzyści wynikające z korzystania z kontenerów systemu Windows są zasadniczo takie same, jak w przypadku ogólnie oferowanych kontenerów. Korzystanie z kontenerów systemu Windows znacznie poprawia elastyczność, przenośność i kontrolę.

Istniejące aplikacje .NET odwołują się do tych aplikacji, które zostały utworzone przy użyciu .NET Framework. Na przykład mogą to być tradycyjne ASP.NET aplikacje sieci Web — nie korzystają z platformy .NET Core, która jest nowsza i działa na wielu platformach w systemach Linux, Windows i MacOS.

Główną zależnością w .NET Framework jest system Windows. Ma także pomocnicze zależności, takie jak IIS i system. Web w tradycyjnych ASP.NET.

Aplikacja .NET Framework musi działać w systemie Windows, kropki. Jeśli chcesz konteneryzowanie istniejące aplikacje .NET Framework i nie możesz lub nie chcesz inwestować w migrację do platformy .NET Core ("Jeśli działa prawidłowo, nie należy jej migrować"), jedyną opcją dla kontenerów jest użycie kontenerów systemu Windows.

Z tego względu jedną z głównych korzyści związanych z kontenerami systemu Windows jest możliwość modernizacji istniejących aplikacji .NET Framework działających w systemie Windows — do kontenerach. Ostatecznie kontenery systemu Windows uzyskują korzyści, których szukasz, przy użyciu kontenerów, elastyczności, przenośności i lepszej kontroli.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Wybierz system operacyjny, z którym chcesz się połączyć. Kontenery oparte na sieci

Ze względu na różnorodność systemów operacyjnych obsługiwanych przez platformę Docker, a także różnice między .NET Framework i .NET Core, należy wskazać określony system operacyjny i konkretne wersje na podstawie używanej platformy.

W przypadku systemu Windows można użyć systemu Windows Server Core lub Windows nano Server. Te wersje systemu Windows zapewniają różne cechy (takie jak usługi IIS i samodzielny serwer sieci Web, taki jak Kestrel), które mogą być konieczne przez aplikacje .NET Framework lub .NET Core.

W przypadku systemu Linux dostępne są wiele dystrybucje i są obsługiwane w oficjalnych obrazach platformy Docker .NET (na przykład Debian).

Rysunek 4-7 zawiera wersje systemu operacyjnego, które można wybrać, w zależności od wersji .NET Framework aplikacji.

![Diagram przedstawiający system operacyjny, który ma być przeznaczony na podstawie wersji .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Rysunek 4-7.** Systemy operacyjne przeznaczone do celów opartych na wersji .NET Framework

W scenariuszach migracji dla istniejących lub starszych aplikacji, które są oparte na .NET Framework aplikacjach, główne zależności znajdują się w systemach Windows i IIS. Jedyną opcją jest użycie obrazów platformy Docker opartych na systemie Windows Server Core i .NET Framework.

Po dodaniu nazwy obrazu do pliku pliku dockerfile można wybrać system operacyjny i wersję przy użyciu znacznika, jak w poniższych przykładach dla obrazów kontenerów systemu Windows opartych na .NET Framework:

> | **Seryjn** | **System i wersja** |
> |---|---|
> | **Microsoft/dotnet-Framework: 4. x-windowsservercore** | .NET Framework 4. x w systemie Windows Server Core |
> | **Microsoft/ASPNET: 4. x-windowsservercore** | .NET Framework 4. x z dodatkowym ASP.NET dostosowania w systemie Windows Server Core |

W przypadku platformy .NET Core (międzyplatformowego dla systemów Linux i Windows) Tagi będą wyglądać następująco:

> | **Seryjn** | **System i wersja**
> |---|---|
> | **Microsoft/dotnet: 2.0.0 — środowisko uruchomieniowe** | Środowisko uruchomieniowe programu .NET Core 2,0 — tylko w systemie Linux |
> | **Microsoft/dotnet: 2.0.0-Runtime-nanoserver** | Środowisko uruchomieniowe programu .NET Core 2,0 — tylko w systemie Windows nano Server |

### <a name="multi-arch-images"></a>Obrazy z obsługą wielodostępności

Począwszy od średniej 2017, można także użyć nowej funkcji platformy Docker o nazwie obrazy z [obsługą wielodostępności](https://github.com/moby/moby/issues/15866) . Obrazy .NET Core Docker mogą używać tagów wieloskładnikowych. Pliki pliku dockerfile nie muszą już definiować systemu operacyjnego, którego dotyczy. Funkcja wielodostępna umożliwia użycie jednego tagu w wielu konfiguracjach maszyn. Na przykład przy użyciu wielu archów można użyć jednego wspólnego tagu: **Microsoft/dotnet: 2.0.0-Runtime**. Jeśli ściągasz ten tag ze środowiska kontenera systemu Linux, uzyskasz obraz oparty na debian. Jeśli ten tag zostanie pobrany ze środowiska kontenera systemu Windows, zostanie wyświetlony obraz oparty na serwerze nano.

W przypadku obrazów .NET Framework, ponieważ tradycyjny .NET Framework obsługuje tylko system Windows, nie można użyć funkcji wieloskładnikowej.

## <a name="windows-container-types"></a>Typy kontenerów systemu Windows

Podobnie jak kontenery systemu Linux, kontenery Windows Server są zarządzane przy użyciu aparatu Docker. W przeciwieństwie do kontenerów systemu Linux, kontenery Windows obejmują dwa różne typy kontenerów lub czasy uruchamiania — kontenery systemu Windows Server i izolacja funkcji Hyper-V.

**Kontenery systemu Windows Server**: zapewnia izolację aplikacji za poorednictwem technologii izolacji procesów i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i wszystkimi kontenerami uruchomionymi na hoście. Te kontenery nie zapewniają niezaufanej granicy zabezpieczeń i nie powinny być używane do izolowania niezaufanych kodów. Ze względu na współużytkowaną przestrzeń jądra te kontenery wymagają takiej samej wersji jądra i konfiguracji.

**Izolacja funkcji Hyper-V**: rozszerza na izolację zapewnianą przez kontenery systemu Windows Server przez uruchomienie każdego kontenera na wysoce ZOPTYMALIZOWANEJ maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest współużytkowane z innymi kontenerami na tym samym hoście. Te kontenery zostały zaprojektowane w celu zagwarantowania niedostępności hostingu wielodostępnego z zachowaniem zabezpieczeń maszyny wirtualnej. Ponieważ te kontenery nie współdzielą jądra z hostem lub innymi kontenerami na hoście, mogą uruchamiać jądra z różnymi wersjami i konfiguracjami (z obsługiwanymi wersjami). Na przykład wszystkie kontenery systemu Windows w systemie Windows 10 używają izolacji funkcji Hyper-V, aby korzystać z wersji i konfiguracji jądra systemu Windows Server.

Uruchamianie kontenera w systemie Windows z izolacją funkcji Hyper-V lub bez niej jest podjęciem decyzji w czasie wykonywania. Można najpierw utworzyć kontener z izolacją funkcji Hyper-V, a w czasie wykonywania wybrać opcję uruchomienia zamiast niego kontenera systemu Windows Server.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Dokumentacja kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Podstawy kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Grafika informacyjna: Microsoft i kontenery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystem kontenera na platformie Azure

W poprzednich sekcjach wyjaśniono, jakie korzyści z kontenerów platformy Docker są również szczegółowe w przypadku określonych obrazów kontenerów dla aplikacji .NET. Wszystkie informacje ogólne są podstawowe w celu opracowania lub konteneryzowanie aplikacji.
Jednak w przypadku środowiska wdrażania produkcyjnego, a nawet środowisk do tworzenia i testowania, Microsoft Azure zapewnia otwarte i szeroki wybór różnych opcji, a pełny ekosystem kontenera w chmurze (pokazano na poniższym diagramie). W zależności od potrzeb aplikacji należy wybrać jeden lub inny produkt platformy Azure.

![Diagram ekosystemu kontenerów na platformie Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Rysunek 4.7.5.** Ekosystem kontenera na platformie Azure

Z ekosystemu kontenerów na platformie Azure następujące produkty obsługujące kontenery, które są uważane za infrastrukturę:

- **Azure Container Instances (ACI)**
- **Virtual Machines platformy Azure** (z obsługą kontenera)
- **Virtual Machine Scale Sets platformy Azure** (z obsługą kontenera)

Z tych trzech ACI zapewnia znakomitą korzyść, która jest faktem, że nie musisz obsługiwać bazowego systemu operacyjnego, bez konieczności uaktualniania/poprawek itd., ale ACI nadal znajduje się na poziomie infrastruktury, jak lepiej wyjaśniono w kolejnych sekcjach tej książki.

Produkty na platformie Azure obsługujące kontenery, które w tym samym czasie są rozmieszczone więcej na poziomie PaaS (platforma jako usługa):

- **Azure App Service**
- **Usługa Azure Kubernetes Service (AKS i ACS)**
- **Azure Batch**

Następnie Azure Container Registry to wysoce skalowalny rejestr kontenerów hostowany na platformie Azure, z którego można korzystać ze wszystkich poprzednich produktów podczas rejestrowania i wdrażania niestandardowych obrazów kontenerów.

Ponadto z kontenerów można korzystać z innych usług zarządzanych na platformie Azure, takich jak Azure SQL Database, pamięć podręczna Redis Azure, Azure Cosmos DB itd. Dodatkowo dostępne są rozwiązania/platformy innych firm w witrynie Azure Marketplace, takie jak Cloud Foundry i OpenShift, gdzie można również używać kontenerów na platformie Azure.

W następnych sekcjach można zapoznać się z zaleceniami firmy Microsoft dotyczącymi używania poszczególnych produktów i rozwiązań platformy Azure, które są przeznaczone dla kontenerów systemu Windows.

>[!div class="step-by-step"]
>[Poprzedni](what-about-cloud-native-applications.md)
>[dalej](when-not-to-deploy-to-windows-containers.md)
