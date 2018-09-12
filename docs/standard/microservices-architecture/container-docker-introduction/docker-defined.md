---
title: Co to jest Docker?
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Co to jest Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 36a153ca636adbfe7a335d71cc1baef4e213f4c9
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709720"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projektu open-source](https://github.com/docker/docker) automatyzację wdrażania aplikacji jako przenośny, samowystarczalne kontenery, które można uruchomić w chmurze lub lokalnie. Docker to również [firmy](https://www.docker.com/) który promuje i rozwojem tej technologii. Docker działa we współpracy z chmury, Linux i Windows producentów, takie jak Microsoft.

![](./media/image2.png)

**Rysunek 2-2**. Docker służy do wdrażania kontenerów we wszystkich warstwach chmury hybrydowej

Kontenery obrazu platformy docker działa natywnie w systemie Linux i Windows. Obrazy Windows uruchomienia tylko na hostach Windows i obrazów systemu Linux, Uruchom tylko na hostach z systemem Linux. Host jest serwerem lub maszyny Wirtualnej.

Można tworzyć w Windows, Linux lub macOS. Na komputerze deweloperskim uruchamia hosta platformy Docker, w których są wdrażane obrazy platformy Docker, łącznie z aplikacji i jego zależności. W systemie Linux lub macOS możesz użyć hosta platformy Docker, który jest systemem Linux i można tworzyć obrazy tylko dla kontenerów systemu Linux. (W systemie macOS można edytować kod lub uruchomić interfejs wiersza polecenia platformy Docker, ale począwszy od chwili pisania tego dokumentu, kontenery są uruchamiane bezpośrednio w systemie macOS). Na Windows można tworzyć obrazy systemu Linux lub Windows kontenery.

W Windows lub macOS [Docker Community Edition (CE)](https://www.docker.com/community-edition) obsługuje kontenery w środowisku deweloperskim oraz udostępnia narzędzia, dodatkowe dla deweloperów. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) jest używana przez zespoły IT, którzy kompilują, dostarczanie i uruchamiają duże aplikacje krytyczne dla prowadzonej działalności. Obydwa te produkty zainstalować niezbędnych maszyny Wirtualnej (hosta platformy Docker) do hostowania kontenerów.

[Kontenery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) działają z dwóch typów środowisk uruchomieniowych:

-   Kontenery systemu Windows Server zapewniają izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra hosta kontenera i wszystkie kontenery uruchomione na hoście.

-   Kontenery funkcji Hyper-V rozwiń na izolacja świadczona przez kontenery systemu Windows Server, uruchamiając każdego kontenera na wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest udostępniony za pomocą kontenerów funkcji Hyper-V, zapewniając lepsze izolację. Kontenery funkcji Hyper-V, Zezwalaj na niezaufane i *szkodliwy wielodostępnych* uruchamiania aplikacji na tym samym hoście. Kontenery funkcji Hyper-V mają nieco mniej wydajność w czasu uruchamiania i z dużą gęstością niż kontenery systemu Windows Server.

Obrazy dla tych kontenerów są tworzone i działają tak samo. Różnią się one w sposób tworzenia kontenera. Aby uzyskać więcej informacji, zobacz [kontenery funkcji Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenerów platformy Docker przy użyciu maszyn wirtualnych

Rysunek 2 – 3 przedstawiono porównanie między maszynami wirtualnymi i Docker kontenerów.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Maszyny wirtualne****kontenerów platformy Docker**
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Maszyny wirtualne obejmują aplikację, wymaganych bibliotek lub pliki binarne i systemu operacyjnego gościa pełne. Pełne wirtualizacji wymaga większej ilości zasobów niż konteneryzacji. Kontenery obejmują aplikacji i wszystkich jego zależności. Jednak kontenery współdzielą jądro systemu operacyjnego za pomocą innych kontenerów. Kontenery są uruchamiane jako procesach izolowanych, w obszarze użytkownika w systemie operacyjnym hosta. Z wyjątkiem kontenery funkcji Hyper-V, w którym każdy kontener jest uruchomiona wewnątrz specjalną maszyną wirtualną na kontener.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Rysunek 2 – 3**. Porównanie tradycyjnych maszyn wirtualnych do kontenerów platformy Docker

Ponieważ kontenery wymaga znacznie mniej zasobów (na przykład, nie ma potrzeby pełnej wersji systemu operacyjnego), błyskawicznie zaczynaj pracę i są łatwe do wdrożenia. Niskie użycie zasobów umożliwia zwiększenie gęstości. Można uruchomić więcej usług w tej samej jednostce sprzętu i obniżyć koszty.

Uruchomione na te same wyniki jądra w izolacji jest mniejszy niż maszyny wirtualne zapewniają.

Głównym celem obrazu jest fakt, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, można to debugować na maszynie i następnie wdrożyć go na inny komputer, z tym samym środowisku, gwarantowana.

Obraz kontenera jest sposobem pakietu aplikacji lub usługi oraz wdrożyć ją w sposób niezawodny i odtworzenia. Można powiedzieć, że platformy Docker jest nie tylko technologii, ale również filozofia i procesu.

Deweloperzy platformy docker nie powiedzieć "Działa na komputerze, dlaczego w środowisku produkcyjnym?" Mówią, "Korzystają one z platformy Docker". Platformy docker w pakiecie aplikacji mogą być wykonywane na wszystkie obsługiwane środowiska Docker. Aplikacje platformy docker w pakiecie Uruchom spójne dla wszystkich elementów docelowych wdrożenia (deweloperskie, QA, przejściowego i produkcji).

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](docker-terminology.md)
