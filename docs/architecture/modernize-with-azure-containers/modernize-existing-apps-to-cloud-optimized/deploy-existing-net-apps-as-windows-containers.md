---
title: Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
description: Modernizacja istniejących aplikacji platformy .NET za pomocą kontenerów usługi Azure Cloud i Windows | Wdrażanie istniejących aplikacji platformy .NET jako kontenerów systemu Windows
ms.date: 04/29/2018
ms.openlocfilehash: c99c2e756320fc886203efcbf98a81e571d907e5
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987975"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows

Wdrożenia oparte na kontenerach systemu Windows mają zastosowanie do aplikacji zoptymalizowanych pod kątem chmury i aplikacji natywnych dla chmury.

Jednak w tym przewodniku, a zwłaszcza w poniższych sekcjach, koncentruje się głównie na użyciu kontenerów systemu Windows dla aplikacji *zoptymalizowanych pod kątem chmury,* gdzie nie trzeba ponownie przeprojektować aplikację.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenery? (Linux lub Windows)

Kontenery są sposobem, aby zakończyć aplikację do własnego pakietu izolowane. W jego kontenerze aplikacja nie ma wpływu na aplikacje lub procesy, które istnieją poza kontenerem. Wszystko, od czego aplikacja zależy, aby pomyślnie uruchomić jako proces znajduje się wewnątrz kontenera. Wszędzie tam, gdzie kontener może przenieść, wymagania aplikacji zawsze będą spełnione, pod względem bezpośrednich zależności, ponieważ jest on dołączony do wszystkiego, co musi uruchomić (zależności biblioteki, środowiska wykonawcze i tak dalej).

Główną cechą kontenera jest to, że sprawia, że środowisko jest takie same w różnych wdrożeniach, ponieważ sam kontener jest wyposażony we wszystkie zależności, których potrzebuje. Można debugować aplikację na komputerze, a następnie wdrożyć ją na innym komputerze, z tego samego środowiska gwarantowane.

Kontener jest wystąpieniem obrazu kontenera. Obraz kontenera to sposób na spakowanie aplikacji lub usługi (na znak migawki), a następnie wdrożenie go w sposób niezawodny i powtarzalny. Można powiedzieć, że Docker to nie tylko technologia, ale także filozofia i proces.

Ponieważ kontenery codziennie stają się coraz bardziej powszechne, stają się one ogólnobranżową "jednostką wdrażania".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Zalety kontenerów (Docker Engine w systemie Linux lub Windows)

Tworzenie aplikacji przy użyciu kontenerów, które również mogą być zdefiniowane jako lekkie bloki konstrukcyjne oferuje znaczny wzrost elastyczności w budowaniu, wysyłania i uruchamiania dowolnej aplikacji w dowolnej infrastrukturze.

Dzięki kontenerom możesz przejść dowolną aplikację z dewelopera do produkcji bez zmiany kodu lub bez niej, dzięki integracji platformy Docker w narzędziach deweloperskich firmy Microsoft, systemach operacyjnych i chmurze.

Podczas wdrażania na zwykłych maszyn wirtualnych, prawdopodobnie masz już metodę wdrażania ASP.NET aplikacji do maszyn wirtualnych. Jest jednak prawdopodobne, że metoda obejmuje wiele kroków ręcznych lub złożonych zautomatyzowanych procesów przy użyciu narzędzia wdrażania, takiego jak Puppet lub podobnego narzędzia. Może być konieczne wykonanie zadań, takich jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami i uruchamianie interaktywnych programów instalacyjnych opartych na konfiguracjach msi, a następnie testowanie. Wszystkie te kroki we wdrożeniu dodać czas i ryzyko dla wdrożeń. Pojawią się błędy, gdy zależność nie jest obecny w środowisku docelowym.

W kontenerach systemu Windows proces pakowania aplikacji jest w pełni zautomatyzowany. Kontenery systemu Windows jest oparty na platformie Platformy Docker, która oferuje automatyczne aktualizacje i wycofywania dla wdrożeń kontenerów. Głównym ulepszeniem, które można uzyskać z korzystania z aparatu platformy Docker jest tworzenie obrazów, które są jak migawki aplikacji, ze wszystkimi jego zależności. Obrazy są obrazy platformy Docker (obraz kontenera systemu Windows, w tym przypadku). Obrazy są uruchamiane ASP.NET aplikacji w kontenerach, bez powrotu do kodu źródłowego. Migawka kontenera staje się jednostką wdrożenia.

Wiele organizacji konteneryzuje istniejące aplikacje monolityczne z następujących powodów:

- **Elastyczność wydawania dzięki ulepszonym wdrażaniu**. Kontenery oferują spójną umowę wdrażania między programowania i operacji. Kiedy używasz kontenerów, nie usłyszysz, jak deweloperzy mówią: "To działa na moim komputerze, dlaczego nie w produkcji?" Mogą powiedzieć: "Działa jako kontener, więc będzie działać w produkcji." Spakowana aplikacja, ze wszystkimi jej zależnościami, może być wykonywana w dowolnym obsługiwanym środowisku opartym na kontenerze. Będzie działać tak, jak miał działać we wszystkich celach wdrażania (dev, QA, staging, production). Kontenery eliminują większość tarć, gdy przechodzą z jednego etapu do następnego, co znacznie poprawia wdrażanie i można wysyłać szybciej.

- **Redukcja kosztów**. Kontenery prowadzą do niższych kosztów, albo przez konsolidację i usunięcie istniejącego sprzętu, albo z uruchamiania aplikacji o większej gęstości na jednostkę sprzętu.

- **Przenośność**. Pojemniki są modułowe i przenośne. Kontenery platformy Docker są obsługiwane w dowolnym systemie operacyjnym serwera (Linux i Windows), w dowolnej głównej chmurze publicznej (Microsoft Azure, Amazon AWS, Google, IBM) oraz w środowiskach lokalnych i prywatnych lub hybrydowych w chmurze.

- **Sterowanie**. Kontenery oferują elastyczne i bezpieczne środowisko, które jest kontrolowane na poziomie kontenera. Kontener może być zabezpieczony, izolowany, a nawet ograniczony przez ustawienie zasad ograniczeń wykonywania w kontenerze. Jak opisano w sekcji dotyczącej kontenerów systemu Windows, kontenery systemu Windows Server 2016 i Hyper-V oferują dodatkowe opcje pomocy technicznej dla przedsiębiorstw.

Znacząca poprawa elastyczności, przenośności i kontroli ostatecznie prowadzi do znacznych redukcji kosztów podczas korzystania z kontenerów do tworzenia i obsługi aplikacji.

## <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) to [projekt typu open source,](https://github.com/docker/docker) który automatyzuje wdrażanie aplikacji jako przenośnych, samowystarczalnych kontenerów, które można uruchamiać w chmurze lub lokalnie. Docker jest również [firmą,](https://www.docker.com/) która promuje i rozwija tę technologię. Firma współpracuje z dostawcami chmury, linuksa i systemu Windows, w tym firmy Microsoft.

![Diagram przedstawiający sposób wdrażania kontenerów w chmurze hybrydowej.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Rysunek 4-6.** Platforma Docker wdraża kontenery we wszystkich warstwach chmury hybrydowej

Dla kogoś zaznajomionego z maszyn wirtualnych kontenery mogą wydawać się niezwykle podobne. Kontener uruchamia system operacyjny, ma system plików i jest dostępny za pośrednictwem sieci, podobnie jak fizyczny lub wirtualny system komputerowy. Jednak technologia i koncepcje za kontenery znacznie różnią się od maszyn wirtualnych. Z punktu widzenia dewelopera kontener musi być traktowany bardziej jak pojedynczy proces. W rzeczywistości kontener ma jeden punkt wejścia dla jednego procesu.

Kontenery platformy Docker (dla uproszczenia, *kontenery)* mogą działać natywnie w systemach Linux i Windows. Podczas uruchamiania zwykłych kontenerów kontenery systemu Windows mogą być uruchamiane tylko na hostach systemu Windows (serwer hosta lub maszyna wirtualna), a kontenery systemu Linux mogą być uruchamiane tylko na hostach systemu Linux. Jednak w najnowszych wersjach kontenerów systemu Windows Server i Hyper-V kontener systemu Linux może również działać natywnie w systemie Windows Server przy użyciu technologii izolacji funkcji Hyper-V, która jest obecnie dostępna tylko w kontenerach systemu Windows Server.

W najbliższej przyszłości mieszane środowiska, które mają kontenery Linux i Windows będą możliwe, a nawet powszechne.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Korzyści z kontenerów systemu Windows dla istniejących aplikacji .NET

Korzyści wynikające z używania kontenerów systemu Windows są zasadniczo takie same korzyści, jakie można uzyskać z kontenerów w ogóle. Korzystanie z kontenerów systemu Windows jest znacznie poprawy elastyczności, przenośności i kontroli.

Istniejące aplikacje platformy .NET odnoszą się do tych aplikacji, które zostały utworzone przy użyciu programu .NET Framework. Na przykład mogą być tradycyjne ASP.NET aplikacji sieci web, nie używają .NET Core, który jest nowszy i działa na wielu platformach w systemach Linux, Windows i MacOS.

Główną zależnością w programie .NET Framework jest system Windows. Ma również zależności pomocnicze, takie jak usługi IIS i System.Web w tradycyjnych ASP.NET.

Aplikacja .NET Framework musi działać w systemie Windows, okres. Jeśli chcesz konteneryzować istniejące aplikacje .NET Framework i nie możesz lub nie chcesz inwestować w migrację do platformy .NET Core ("Jeśli działa poprawnie, nie migruj go"), jedynym wyborem dla kontenerów jest użycie kontenerów systemu Windows.

Tak więc jedną z głównych zalet kontenerów systemu Windows jest to, że oferują one sposób modernizacji istniejących aplikacji .NET Framework, które są uruchomione w konteneryzacji systemu Windows. Ostatecznie kontenery systemu Windows zapewnia korzyści, których szukasz przy użyciu kontenerów elastyczność, przenośność i lepszą kontrolę.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Wybierz system operacyjny, który ma być skierowany za pomocą pliku . Kontenery oparte na sieci

Biorąc pod uwagę różnorodność systemów operacyjnych, które są obsługiwane przez platformę Docker, a także różnice między programem .NET Framework i .NET Core, należy kierować określony system operacyjny i konkretne wersje oparte na używanej platformie.

W systemie Windows można używać systemu Windows Server Core lub Windows Nano Server. Te wersje systemu Windows zapewniają różne cechy (takie jak usługi IIS w porównaniu z serwerem sieci web hostowanym samodzielnie, takim jak Kestrel), które mogą być potrzebne przez aplikacje .NET Framework lub .NET Core.

W przypadku systemu Linux wiele dystrybucji jest dostępnych i obsługiwanych w oficjalnych obrazach platformy Docker .NET (takich jak Debian).

Rysunek 4-7 przedstawia wersje systemu operacyjnego, które można kierować, w zależności od wersji programu .NET Framework aplikacji.

![Diagram przedstawiający, co system operacyjny do docelowego na podstawie wersji .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Rysunek 4-7.** Systemy operacyjne przeznaczone na podstawie wersji .NET Framework

W scenariuszach migracji dla istniejących lub starszych aplikacji, które są oparte na aplikacjach .NET Framework, główne zależności są w systemach Windows i IIS. Jedyną opcją jest użycie obrazów platformy Docker opartych na systemie Windows Server Core i programie .NET Framework.

Po dodaniu nazwy obrazu do pliku Dockerfile można wybrać system operacyjny i wersję za pomocą znacznika, jak w poniższych przykładach dla obrazów kontenerów systemu Windows opartych na platformie .NET Framework:

> | **Tag** | **System i wersja** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | Program .NET Framework 4.x w systemie Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | Program .NET Framework 4.x z dodatkowym dostosowaniem ASP.NET w systemie Windows Server Core |

W przypadku platformy .NET Core (międzyplatformowych dla systemów Linux i Windows) tagi będą wyglądać następująco:

> | **Tag** | **System i wersja**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 tylko w systemie Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Program .NET Core 2.0 tylko w systemie Windows Nano Server |

### <a name="multi-arch-images"></a>Obrazy wielo łukowe

Począwszy od połowy 2017 r., można również użyć nowej funkcji w docker nazwie [multi-arch](https://github.com/moby/moby/issues/15866) obrazów. Obrazy platformy Docker .NET Core mogą używać znaczników wielochuchłowych. Pliki dockerfile nie muszą już definiować systemu operacyjnego, do którego kierowano. Funkcja multi-arch umożliwia użycie pojedynczego znacznika w wielu konfiguracjach maszyn. Na przykład, z multi-arch, można użyć jednego wspólnego tagu: **microsoft / dotnet: 2.0.0-runtime**. Jeśli wyciągniesz ten tag ze środowiska kontenera Linuksa, otrzymasz obraz oparty na Debianie. Jeśli pobierzesz ten znacznik ze środowiska kontenera systemu Windows, zostanie nali będzie obraz oparty na serwerze Nano Server.

W przypadku obrazów programu .NET Framework, ponieważ tradycyjna .NET Framework obsługuje tylko system Windows, nie można użyć funkcji multi-arch.

## <a name="windows-container-types"></a>Typy kontenerów systemu Windows

Podobnie jak kontenery systemu Linux, kontenery systemu Windows Server są zarządzane przy użyciu aparatu platformy Docker. W przeciwieństwie do kontenerów systemu Linux kontenery systemu Windows zawierają dwa różne typy kontenerów lub uruchamianie kontenerów systemu Windows Server i izolacji funkcji Hyper-V.

**Kontenery systemu Windows Server:** Zapewnia izolację aplikacji za pomocą technologii izolacji obszaru nazw i procesu. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i wszystkimi kontenerami, które są uruchomione na hoście. Te kontenery nie zapewniają wrogie granice zabezpieczeń i nie powinny być używane do izolowania niezaufanego kodu. Ze względu na udostępnione miejsce jądra te kontenery wymagają tej samej wersji jądra i konfiguracji.

**Izolacja funkcji Hyper-V:** rozszerza izolację zapewnianą przez kontenery systemu Windows Server, uruchamiając każdy kontener na wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest współużytkowane z innymi kontenerami na tym samym hoście. Kontenery te są przeznaczone do wrogiego hostingu wielodostępnego, z tymi samymi gwarancjami zabezpieczeń maszyny Wirtualnej. Ponieważ te kontenery nie współużytkują jądra hostowi lub innym kontenerom na hoście, mogą uruchamiać jądra w różnych wersjach i konfiguracjach (z obsługiwanymi wersjami). Na przykład wszystkie kontenery systemu Windows w systemie Windows 10 używają izolacji funkcji Hyper-V do korzystania z wersji i konfiguracji jądra systemu Windows Server.

Uruchamianie kontenera w systemie Windows z izolacją funkcji Hyper-V lub bez niej jest decyzją w czasie wykonywania. Można utworzyć kontener z izolacją funkcji Hyper-V początkowo i w czasie wykonywania, zamiast tego wybierz opcję uruchomienia go jako kontenera systemu Windows Server.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Dokumentacja kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Podstawy kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infografika: Microsoft i kontenery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystem kontenerów na platformie Azure

W poprzednich sekcjach wyjaśniono, jakie są zalety kontenerów platformy Docker, a także szczegółowe informacje na temat obrazów określonych kontenerów dla aplikacji platformy .NET. Wszystkie te ogólne informacje mają podstawowe znaczenie w celu opracowania lub konteneryzacji aplikacji.
Jednak myśląc o środowisku wdrażania produkcyjnego lub nawet środowiskach QA i Dev/Test, Platforma Microsoft Azure zapewnia otwartą i szeroką gamę opcji, pełny ekosystem kontenerów w chmurze (pokazany na poniższym diagramie). W zależności od potrzeb konkretnej aplikacji należy wybrać jeden lub inny produkt platformy Azure.

![Diagram ekosystemu kontenerów na platformie Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Rysunek 4-7.5.** Ekosystem kontenerów na platformie Azure

Z ekosystemu kontenerów na platformie Azure następujące produkty obsługujące kontenery, które są uważane za infrastrukturę:

- **Azure Container Instances (ACI)**
- **Maszyny wirtualne platformy Azure** (z obsługą kontenera)
- **Zestawy skalowania maszyny wirtualnej platformy Azure** (z obsługą kontenera)

Z tych trzech, ACI zapewnia wielką korzyść, która jest fakt, że nie trzeba utrzymywać podstawowy system operacyjny, nie ma potrzeby, aby uaktualnić / patch, itp., ale ACI nadal jest umieszczony w poziomie infrastruktury, jak lepiej wyjaśnione w nadchodzących sekcjach tej książki.

Produkty na platformie Azure obsługujące kontenery, które są jednocześnie umieszczone bardziej na poziomie PaaS (Platforma jako usługa) są:

- **Azure App Service**
- **Usługa Azure Kubernetes (AKS i ACS)**
- **Azure Batch**

Następnie usługa Azure Container Registry to rejestr kontenerów o wysokiej skalowalności hostowany na platformie Azure, którego można używać ze wszystkich poprzednich produktów podczas rejestrowania i wdrażania obrazów kontenerów niestandardowych.

Ponadto z kontenerów można korzystać z innych usług zarządzanych na platformie Azure, takich jak usługa Azure SQL Database, pamięć podręczna Usługi Azure Redis, usługa Azure Cosmos DB itp. plus istnieją rozwiązania/platformy innych firm dostępne w usłudze Azure Marketplace, takie jak Cloud Foundry i OpenShift, gdzie można również używać kontenerów na platformie Azure.

W następnych sekcjach można zapoznać się z zaleceniami firmy Microsoft dotyczącymi tego, kiedy należy używać każdego z tych produktów i rozwiązań platformy Azure, w szczególności podczas kierowania na kontenery systemu Windows.

>[!div class="step-by-step"]
>[Poprzedni](what-about-cloud-native-applications.md)
>[następny](when-not-to-deploy-to-windows-containers.md)
