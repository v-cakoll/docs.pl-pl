---
title: Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089558"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Wdrażanie istniejących aplikacji .NET jako kontenerów systemu Windows

Wdrożenia oparte na kontenerach systemu Windows mają zastosowanie do aplikacji zoptymalizowanych pod kątem chmury i aplikacji natywnych dla chmury.

Jednak w tym przewodniku, a zwłaszcza w poniższych sekcjach, skupia się głównie na użyciu kontenerów systemu Windows dla aplikacji *zoptymalizowanych pod kątem chmury,* gdzie nie trzeba ponownie architekta aplikacji.

## <a name="what-are-containers-linux-or-windows"></a>Co to są kontenery? (Linux lub Windows)

Kontenery są sposobem, aby zawinąć aplikację do własnego izolowanego pakietu. W jego kontenerze aplikacji nie ma wpływu aplikacji lub procesów, które istnieją poza kontenerem. Wszystko, od czego zależy aplikacja, aby pomyślnie uruchomić, ponieważ proces znajduje się wewnątrz kontenera. Wszędzie tam, gdzie kontener może zostać przeniesione, wymagania aplikacji będą zawsze spełnione, pod względem zależności bezpośrednich, ponieważ jest on apakowany ze wszystkim, co musi uruchomić (zależności biblioteki, uruchamianie i tak dalej).

Główną cechą kontenera jest to, że sprawia, że środowisko takie samo w różnych wdrożeniach, ponieważ sam kontener pochodzi ze wszystkimi zależnościami, których potrzebuje. Można debugować aplikację na komputerze, a następnie wdrożyć go na innym komputerze, z tego samego środowiska gwarantowane.

Kontener jest wystąpieniem obrazu kontenera. Obraz kontenera jest sposobem na spakowanie aplikacji lub usługi (np. migawka), a następnie wdrożenie go w sposób niezawodny i powtarzalny. Można powiedzieć, że Docker to nie tylko technologia, ale także filozofia i proces.

Ponieważ kontenery codziennie stają się coraz bardziej powszechne, stają się one "jednostką wdrażania".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Zalety kontenerów (Aparat platformy Docker w systemie Linux lub Windows)

Tworzenie aplikacji przy użyciu kontenerów, które również mogą być zdefiniowane jako lekkie bloki konstrukcyjne, oferuje znaczny wzrost elastyczności do tworzenia, wysyłki i uruchamiania dowolnej aplikacji w dowolnej infrastrukturze.

Za pomocą kontenerów można wykonywać dowolną aplikację z programowania do produkcji z niewielką lub żadną zmianą kodu dzięki integracji platformy Docker w narzędziach deweloperskich firmy Microsoft, systemach operacyjnych i chmurze.

Podczas wdrażania na zwykłych maszynach wirtualnych prawdopodobnie masz już metodę wdrażania ASP.NET aplikacji na maszynach wirtualnych. Jest jednak prawdopodobne, że metoda obejmuje wiele ręcznych kroków lub złożonych zautomatyzowanych procesów przy użyciu narzędzia wdrażania, takiego jak Puppet lub podobnego narzędzia. Może być konieczne wykonanie zadań, takich jak modyfikowanie elementów konfiguracji, kopiowanie zawartości aplikacji między serwerami i uruchamianie interaktywnych programów instalacyjnych na podstawie konfiguracji msi, a następnie testowanie. Wszystkie te kroki we wdrożeniu dodać czas i ryzyko do wdrożeń. Otrzymasz błędy, gdy zależność nie jest obecny w środowisku docelowym.

W kontenerach systemu Windows proces pakowania aplikacji jest w pełni zautomatyzowany. Kontenery systemu Windows jest oparta na platformie Platforma Platforma Docker, która oferuje automatyczne aktualizacje i wycofywania dla wdrożeń kontenerów. Głównym ulepszeniem, które można uzyskać przy użyciu aparatu platformy Docker jest tworzenie obrazów, które są jak migawki aplikacji, ze wszystkimi jej zależności. Obrazy są obrazy platformy Docker (obraz kontenera systemu Windows, w tym przypadku). Obrazy są uruchamiane ASP.NET aplikacji w kontenerach, bez powrotu do kodu źródłowego. Migawka kontenera staje się jednostką wdrożenia.

Wiele organizacji konteneryzuje istniejące aplikacje monolityczne z następujących powodów:

- **Zwolnij elastyczność dzięki ulepszonemu wdrożeniu.** Kontenery oferują spójną umowę wdrożenia między programowaniem a operacjami. Kiedy używasz kontenerów, nie usłyszysz, jak deweloperzy mówią: "To działa na moim komputerze, dlaczego nie w środowisku produkcyjnym?" Mogą powiedzieć: "Działa jako kontener, więc będzie działać w środowisku produkcyjnym." Spakowana aplikacja ze wszystkimi jej zależnościami może być wykonywana w dowolnym obsługiwanym środowisku opartym na kontenerach. Będzie działać tak, jak zamierzali działać we wszystkich obiektach docelowych wdrażania (dev, QA, staging, production). Kontenery eliminują większość tarć, gdy przechodzą z jednego etapu do drugiego, co znacznie poprawia wdrażanie i można wysyłać szybciej.

- **Redukcje kosztów**. Kontenery prowadzą do obniżenia kosztów poprzez konsolidację i usunięcie istniejącego sprzętu lub uruchamianie aplikacji o większej gęstości na jednostkę sprzętu.

- **Przenośność**. Kontenery są modułowe i przenośne. Kontenery platformy Docker są obsługiwane w dowolnym systemie operacyjnym serwera (Linux i Windows), w dowolnej głównej chmurze publicznej (Microsoft Azure, Amazon AWS, Google, IBM) oraz w środowiskach chmury lokalnej i prywatnej i hybrydowej.

- **Sterowanie**. Kontenery oferują elastyczne i bezpieczne środowisko, które jest kontrolowane na poziomie kontenera. Kontener może być zabezpieczony, izolowany, a nawet ograniczony przez ustawienie zasad ograniczeń wykonywania w kontenerze. Jak opisano w sekcji Kontenery systemu Windows, kontenery systemu Windows Server 2016 i Hyper-V oferują dodatkowe opcje pomocy technicznej dla przedsiębiorstw.

Znaczna poprawa elastyczności, przenośności i kontroli ostatecznie prowadzi do znacznego obniżenia kosztów podczas używania kontenerów do tworzenia i utrzymywania aplikacji.

## <a name="what-is-docker"></a>Co to jest Docker?

[Platforma Docker](https://www.docker.com/) to [projekt typu open source,](https://github.com/docker/docker) który automatyzuje wdrażanie aplikacji jako przenośnych, samowystarczalnych kontenerów, które można uruchamiać w chmurze lub lokalnie. Docker jest również [firmą,](https://www.docker.com/) która promuje i rozwija tę technologię. Firma współpracuje z dostawcami chmury, systemu Linux i Windows, w tym z firmą Microsoft.

![Diagram przedstawiający sposób wdrażania kontenerów w chmurze hybrydowej.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Rysunek 4-6.** Platforma Docker wdraża kontenery na wszystkich warstwach chmury hybrydowej

Dla osoby zaznajomionej z maszynami wirtualnymi kontenery mogą wydawać się niezwykle podobne. Kontener uruchamia system operacyjny, ma system plików i jest dostępny za pomocą sieci, podobnie jak system komputerów fizycznych lub wirtualnych. Jednak technologia i pojęcia za kontenerami znacznie różnią się od maszyn wirtualnych. Z punktu widzenia dewelopera kontener musi być traktowany bardziej jak pojedynczy proces. W rzeczywistości kontener ma pojedynczy punkt wejścia dla jednego procesu.

Kontenery platformy Docker (dla uproszczenia, *kontenery)* można uruchomić natywnie w systemach Linux i Windows. Podczas uruchamiania zwykłych kontenerów kontenery systemu Windows mogą być uruchamiane tylko na hostach systemu Windows (serwer hosta lub maszyna wirtualna), a kontenery systemu Linux mogą być uruchamiane tylko na hostach systemu Linux. Jednak w najnowszych wersjach kontenerów systemu Windows Server i Hyper-V kontener systemu Linux może również działać natywnie na serwerze Windows Server przy użyciu technologii izolacji funkcji Hyper-V, która jest obecnie dostępna tylko w kontenerach systemu Windows Server.

W niedalekiej przyszłości środowiska mieszane, które mają zarówno kontenery Linux, jak i Windows, będą możliwe, a nawet powszechne.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Zalety kontenerów systemu Windows dla istniejących aplikacji .NET

Korzyści z używania kontenerów systemu Windows są zasadniczo takie same korzyści, które można uzyskać z kontenerów w ogóle. Korzystanie z kontenerów systemu Windows polega na znacznej poprawie elastyczności, przenośności i kontroli.

Istniejące aplikacje .NET odnoszą się do tych aplikacji, które zostały utworzone przy użyciu .NET Framework. Na przykład mogą być tradycyjne ASP.NET aplikacji sieci web, nie używają .NET Core, który jest nowszy i działa między platformami w systemie Linux, Windows i MacOS.

Główną zależnością w programie .NET Framework jest system Windows. Ma również drugorzędne zależności, takie jak usługi IIS i System.Web w tradycyjnych ASP.NET.

Aplikacja .NET Framework musi działać w systemie Windows, kropka. Jeśli chcesz konteneryzować istniejące aplikacje .NET Framework i nie możesz lub nie chcesz inwestować w migrację do .NET Core ("Jeśli działa poprawnie, nie migruj go"), jedynym wyborem dla kontenerów jest użycie kontenerów systemu Windows.

Dlatego jedną z głównych zalet kontenerów systemu Windows jest to, że oferują one sposób na modernizację istniejących aplikacji .NET Framework, które są uruchomione w konteneryzacji systemu Windows. Ostatecznie kontenery systemu Windows zapewnia korzyści, których szukasz przy użyciu kontenerów elastyczność, przenośność i lepszą kontrolę.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Wybierz os do kierowania za pomocą . Kontenery oparte na sieci

Biorąc pod uwagę różnorodność systemów operacyjnych, które są obsługiwane przez platformę Docker, a także różnice między .NET Framework i .NET Core, należy kierować określone systemy operacyjne i konkretne wersje na podstawie struktury, której używasz.

W przypadku systemu Windows można używać systemu Windows Server Core lub Systemu Windows Nano Server. Te wersje systemu Windows zapewniają różne cechy (takie jak usługi IIS w porównaniu z samoobsługowym serwerem sieci Web, takim jak Kestrel), które mogą być potrzebne przez .NET Framework lub aplikacje .NET Core.

W przypadku Linuksa wiele dystrybucji jest dostępnych i obsługiwanych w oficjalnych obrazach dockera .NET (takich jak Debian).

Rysunek 4-7 przedstawia wersje systemu operacyjnego, na które można kierować reklamy, w zależności od wersji programu .NET Framework w aplikacji.

![Diagram przedstawiający, co os do docelowego na podstawie .NET Framework wersji.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Rysunek 4-7.** Systemy operacyjne do kierowania na podstawie wersji .NET Framework

W scenariuszach migracji dla istniejących lub starszych aplikacji, które są oparte na aplikacjach .NET Framework, główne zależności są w systemach Windows i IIS. Jedyną opcją jest użycie obrazów platformy Docker opartych na programie Windows Server Core i platformie .NET Framework.

Po dodaniu nazwy obrazu do pliku Dockerfile można wybrać system operacyjny i wersję przy użyciu znacznika, jak w poniższych przykładach dla obrazów kontenerów systemu Windows opartych na platformie .NET Framework:

> | **Tag** | **System i wersja** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET Framework 4.x w systemie Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET Framework 4.x z dodatkowym dostosowaniem ASP.NET w systemie Windows Server Core |

W przypadku programu .NET Core (między platformami dla systemów Linux i Windows) tagi będą wyglądać następująco:

> | **Tag** | **System i wersja**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | Tylko w czasie wykonywania programu .NET Core 2.0 w systemie Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Tylko środowisko uruchomieniowe programu .NET Core 2.0 w systemie Windows Nano Server |

### <a name="multi-arch-images"></a>Obrazy wielołukowe

Począwszy od połowy 2017 r., można również użyć nowej funkcji w platformie Docker o nazwie obrazów [wielołukowych.](https://github.com/moby/moby/issues/15866) Obrazy platformy Docker .NET Core mogą używać znaczników wielołukowych. Pliki dockerfile nie muszą już definiować systemu operacyjnego, na który jest kierowany. Funkcja wielołukowa umożliwia uzywanie pojedynczego znacznika w wielu konfiguracjach maszyn. Na przykład w przypadku wielu łuków można użyć jednego wspólnego tagu: **microsoft/dotnet:2.0.0-runtime**. Jeśli wyciągniesz ten tag ze środowiska kontenerów Linuksa, otrzymasz obraz oparty na Debianie. Jeśli ten tag zostanie ściągnięty ze środowiska kontenerów systemu Windows, zostanie uzyskany obraz oparty na serwerze Nano Server.

W przypadku obrazów .NET Framework, ponieważ tradycyjna platforma .NET Framework obsługuje tylko system Windows, nie można użyć funkcji wielołukowej.

## <a name="windows-container-types"></a>Typy kontenerów systemu Windows

Podobnie jak kontenery systemu Linux kontenery systemu Windows Server są zarządzane przy użyciu aparatu platformy Docker. W przeciwieństwie do kontenerów systemu Linux kontenery systemu Windows zawierają dwa różne typy kontenerów lub kontenery systemu Windows Server i izolację funkcji Hyper-V.

**Kontenery systemu Windows Server:** Zapewnia izolację aplikacji za pomocą technologii izolacji procesów i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i wszystkimi kontenerami, które są uruchomione na hoście. Kontenery te nie zapewniają wrogie granice zabezpieczeń i nie powinny być używane do izolowania niezaufanego kodu. Ze względu na współużytkowane miejsce jądra te kontenery wymagają tej samej wersji jądra i konfiguracji.

**Izolacja funkcji Hyper-V:** Rozszerza izolację zapewnianą przez kontenery systemu Windows Server, uruchamiając każdy kontener na wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest współużytkowane z innymi kontenerami na tym samym hoście. Kontenery te są przeznaczone do wrogiego hostingu wielodostępnego, z tymi samymi gwarancjami zabezpieczeń maszyny Wirtualnej. Ponieważ te kontenery nie współużytkują jądra z hostem lub innymi kontenerami na hoście, mogą uruchamiać jądra z różnymi wersjami i konfiguracjami (z obsługiwanymi wersjami). Na przykład wszystkie kontenery systemu Windows w systemie Windows 10 używają izolacji funkcji Hyper-V do korzystania z wersji jądra systemu Windows Server i konfiguracji.

Uruchamianie kontenera w systemie Windows z izolacją funkcji Hyper-V lub bez niej jest decyzją w czasie wykonywania. Można utworzyć kontener z izolacją funkcji Hyper-V początkowo i w czasie wykonywania, zamiast tego należy uruchomić go jako kontener systemu Windows Server.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Dokumentacja kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Podstawy kontenerów systemu Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infografika: Microsoft i kontenery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystem kontenerów na platformie Azure

W poprzednich sekcjach wyjaśniono, jakie są zalety kontenerów platformy Docker, a także szczegóły dotyczące obrazów określonego kontenera dla aplikacji .NET. Wszystkie te informacje ogólne ma podstawowe znaczenie dla opracowania lub konteneryzacji aplikacji.
Jednak podczas myślenia o środowisku wdrażania w środowisku produkcyjnym lub nawet środowiskach qa i dev/test, Microsoft Azure zapewnia otwarty i szeroki wybór opcji, pełny ekosystem kontenerów w chmurze (pokazane na poniższym diagramie). W zależności od potrzeb określonej aplikacji należy wybrać jeden lub inny produkt platformy Azure.

![Diagram ekosystemu kontenerów na platformie Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Rysunek 4-7.5.** Ekosystem kontenerów na platformie Azure

Z ekosystemu kontenerów na platformie Azure następujące produkty obsługujące kontenery, które są uważane za infrastrukturę:

- **Azure Container Instances (ACI)**
- **Maszyny wirtualne platformy Azure** (z obsługą kontenera)
- **Zestawy skalowania maszyn wirtualnych platformy Azure** (z obsługą kontenera)

Z tych trzech, ACI zapewnia wielką korzyść, która jest fakt, że nie trzeba utrzymać podstawowego systemu operacyjnego, nie ma potrzeby, aby uaktualnić / patch, itp., ale ACI nadal jest umieszczony na poziomie infrastruktury, jak lepiej wyjaśnione w nadchodzących sekcjach tej książki.

Produkty na platformie Azure obsługujących kontenery, które są w tym samym czasie umieszczone bardziej na poziomie PaaS (Platforma jako usługa) są:

- **Usługa aplikacji platformy Azure**
- **Usługa Azure Kubernetes (AKS i ACS)**
- **Azure Batch**

Następnie azure container registry to wysoki skalowalny rejestr kontenerów hostowany na platformie Azure, którego można używać ze wszystkich poprzednich produktów podczas rejestrowania i wdrażania obrazów kontenerów niestandardowych.

Ponadto z kontenerów można korzystać z innych usług zarządzanych na platformie Azure, takich jak azure SQL Database, Azure Redis cache, Usługi Azure Cosmos DB, itp. ponadto istnieją rozwiązania/platformy innych firm dostępne w portalu Azure Marketplace, takie jak Odlewnia chmur i OpenShift, gdzie można również używać kontenerów na platformie Azure.

W następnych sekcjach można zapoznać się z zaleceniami firmy Microsoft dotyczącymi używania każdego z tych produktów i rozwiązań platformy Azure, w szczególności podczas określania reklamowania kontenerów systemu Windows.

>[!div class="step-by-step"]
>[Poprzedni](what-about-cloud-native-applications.md)
>[następny](when-not-to-deploy-to-windows-containers.md)
