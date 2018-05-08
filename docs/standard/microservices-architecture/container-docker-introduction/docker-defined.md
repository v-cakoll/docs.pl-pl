---
title: Co to jest Docker?
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Co to jest Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fadd2611283f0a7dadbf1734fe48f7d1a13096ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projekt open source](https://github.com/docker/docker) automatyzację wdrażania aplikacji jako przenośny, samowystarczalne kontenerów, które można uruchomić w chmurze lub lokalnie. Docker jest również [firmy](https://www.docker.com/) wspiera i rozwoju tej technologii. Docker działa we współpracy z chmury, Linux i dostawców systemu Windows, takie jak Microsoft.

![](./media/image2.png)

**Rysunek 2-2**. Docker wdraża kontenerów na wszystkie warstwy chmury hybrydowej

Kontenery obrazu docker działania w systemie Linux i Windows. Obrazy systemu Windows Uruchom tylko na hostach z systemem Windows i Linux obrazy uruchomić tylko na hostach z systemem Linux. Host jest nazwą serwera lub maszyny Wirtualnej.

Można tworzyć w systemie Windows, Linux lub macOS. Na komputerze deweloperskim uruchamia hostów Docker, gdzie są wdrażane obrazy usługi Docker, łącznie z aplikacji i jego zależności. W systemie Linux lub macOS używasz Docker hosta, który jest systemem Linux i nie można tworzyć obrazy tylko dla systemu Linux kontenerów. (Na macOS można edytować kodu lub uruchomić interfejsu wiersza polecenia Docker, ale począwszy od chwili pisania tego dokumentu, kontenery są uruchamiane bezpośrednio na macOS). W systemie Windows można tworzyć obrazy dla systemu Linux lub kontenery systemu Windows.

W systemie Windows lub macOS [Docker Community Edition (CE)](https://www.docker.com/community-edition) przechowuje kontenery w środowisku deweloperskim i udostępnia dodatkowe developer tools. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) jest używany przez zespoły IT, którzy kompilacji, wysyłki i uruchom dużych aplikacji biznesowych o znaczeniu krytycznym. ~ Obydwa te produkty zainstalować niezbędne maszyny Wirtualnej (Docker hosta) do obsługi kontenerów. ~ 

[Kontenery systemu Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) pracować z dwóch typów środowisk uruchomieniowych:

-   Kontenery systemu Windows Server zapewniają izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra z hosta kontenera i wszystkich kontenerów uruchomiona na hoście.

-   Kontenery funkcji Hyper-V rozwiń węzeł na izolację udostępniane przez kontenery systemu Windows Server, uruchamiając każdy kontener zoptymalizowanego maszynie wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest współużytkowany z kontenerów funkcji Hyper-V, zapewniając lepsze izolacji. Kontenery funkcji Hyper-V Zezwalaj na niezaufane i *szkodliwy wielodostępne* uruchamiania aplikacji na tym samym hoście. Kontenery funkcji Hyper-V ma nieco mniejszą wydajność w czasu uruchamiania i z dużą gęstością niż kontenery systemu Windows Server.

Obrazy te kontenerów są tworzone i działają tak samo. Różnią się one w sposób tworzenia kontenera. Aby uzyskać więcej informacji, zobacz [kontenery funkcji Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenery Docker z maszynami wirtualnymi

Rysunek 2 – 3 przedstawiono porównanie maszyn wirtualnych i Docker kontenerów.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Maszyny wirtualne****Docker kontenerów** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Maszyny wirtualne obejmują aplikacji, wymaganych bibliotek lub pliki binarne i systemu operacyjnego gościa pełna. Wirtualizacja pełne wymaga większej ilości zasobów niż przechowywanie w kontenerach. Kontenery obejmują aplikacji i wszystkich jego zależności. Jednak kontenery udostępnić inne kontenery jądra systemu operacyjnego. Kontenery Uruchom jako procesach izolowanych przestrzeni użytkownika w systemie operacyjnym hosta. Z wyjątkiem w kontenerach funkcji Hyper-V, w którym jest uruchamiany każdego kontenera wewnątrz specjalną maszyną wirtualną na kontenera.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Rysunek 2 – 3**. Porównanie tradycyjnych maszyn wirtualnych do kontenerów Docker

Ponieważ kontenery wymaga mniej zasobów (na przykład nie potrzebują oni pełnej wersji systemu operacyjnego), uruchom szybkie i łatwe do wdrożenia. Niskie użycie zasobów umożliwia zwiększeniu. Można uruchomić więcej usług w tej samej jednostce sprzętu i zmniejszenie kosztów.

Uruchomiona na takie same wyniki jądra w izolacji, mniej niż maszyn wirtualnych.

Głównym celem obrazu jest fakt, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, można debugować go na komputerze i wdrożyć go na inny komputer o tym samym środowisku gwarancji.

Obraz kontenera to sposób pakietu aplikacji lub usługi, a następnie wdrożyć go w sposób niezawodny i odtworzenia. Można powiedzieć, że Docker jest nie tylko technologii, ale również zasady klas i procesu.

Deweloperzy docker nie powiedzieć "Działa na komputerze, dlaczego nie w środowisku produkcyjnym?" Mówią, "Jest uruchamiany na Docker". Docker spakowane aplikacje mogą być wykonywane na dowolnym obsługiwanym środowisku Docker. Docker spakowane aplikacje stale Uruchom na wszystkich docelowych wdrożenia (deweloperów, pytań i odpowiedzi, przemieszczania i produkcji).

>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (docker terminology.md)
