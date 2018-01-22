---
title: Co to jest Docker?
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c75b2fa87e5aad93693c76c3bbd135044b36525f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projekt open source](https://github.com/docker/docker) automatyzację wdrażania aplikacji jako przenośny, samowystarczalne kontenerów, które można uruchomić w chmurze lub lokalnie (zobacz rysunek 1 - 2). Docker jest również [firmy](https://www.docker.com/) wspiera i rozwija tej technologii w współpracy z chmury, Linux i dostawców systemu Windows, takie jak Microsoft.

![](./media/image2.png)

Rysunek 1-2: Docker wdraża kontenerów na wszystkie warstwy chmury hybrydowej

Kontenery obrazu docker można uruchomić natywnie w systemie Linux i Windows. Jednak obrazów systemu Windows można uruchamiać tylko na hostach z systemem Windows i Linux obrazy można uruchomić tylko na hostach Linux, co oznacza serwera hosta lub maszyny Wirtualnej.

Deweloperzy mogą używać środowiska projektowania w systemie Windows, Linux lub macOS. Na komputerze dewelopera dewelopera uruchamia hostów Docker, do których Docker są wdrażane obrazy, w tym aplikacji i jego zależności. Deweloperzy, którzy pracują w systemie Linux lub Mac Użyj hosta Docker, który jest opartymi na systemie Linux i mogli tworzyć obrazy tylko dla systemu Linux kontenerów. (Deweloperów pracujących na Mac można edytować kodu lub uruchomić interfejsu wiersza polecenia Docker \[CLI\] z macOS, ale opracowywania tego tekstu, kontenery nie należy uruchamiać bezpośrednio na macOS.) Deweloperzy, którzy pracują w systemie Windows można tworzyć obrazy dla systemu Linux lub kontenery systemu Windows.

Host kontenery w środowiskach programistycznych i narzędzia deweloperskie dodatkowych, dostarczany Docker [Docker Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows lub macOS. Te produkty zainstalować niezbędne maszyny Wirtualnej (Docker hosta) do obsługi kontenerów. Docker powoduje udostępnienie [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), który jest przeznaczony dla rozwoju przedsiębiorstwa i jest używany przez zespoły IT, którzy tworzą wysyłki i uruchomić dużych aplikacji biznesowych o znaczeniu krytycznym w środowisku produkcyjnym.

Aby uruchomić [kontenery Windows](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), istnieją dwa typy środowisk uruchomieniowych:

-   **Windows Server kontenera** to środowisko uruchomieniowe zapewnia izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra z hosta kontenera i wszystkich kontenerów uruchomiona na hoście.

-   **Kontener funkcji Hyper-V** to rozszerzenie izolacji udostępniane przez kontenery systemu Windows Server, uruchamiając każdy kontener zoptymalizowanego maszynie wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest współużytkowany z kontenerów funkcji Hyper-V, zapewniając lepsze izolacji.

Obrazy te kontenerów są tworzone w taki sam sposób i działać takie same. Różnica polega na tym, w jaki sposób ten kontener jest tworzony z obrazu — uruchamianie kontener funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać więcej informacji, zobacz [kontenery funkcji Hyper-V](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Porównywanie kontenery Docker z maszynami wirtualnymi

Rysunek 1 – 3 przedstawiono porównanie maszyn wirtualnych i Docker kontenerów.

Ponieważ kontenery wymaga mniej zasobów (na przykład nie potrzebują oni pełnej wersji systemu operacyjnego), łatwych do wdrożenia i szybkiego uruchamiania. Dzięki temu można mieć zwiększeniu, co oznacza, że można uruchomić więcej usług w tej samej jednostce sprzętu, a tym samym obniżenie kosztów.

Jako efekt uboczny uruchomionych na tym samym jądra uzyskania izolacji mniejsze niż maszyn wirtualnych.

Głównym celem obrazu jest fakt, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, można debugować go na komputerze i wdrożyć go na inny komputer o tym samym środowisku gwarancji.

Obraz kontenera to sposób pakietu aplikacji lub usługi, a następnie wdrożyć go w sposób niezawodny i odtworzenia. W związku z tym Docker nie tylko technologii, jest również zasady klas i procesu.

Używając Docker, nie usłyszysz deweloperzy powiedzieć, "Działa na komputerze, dlaczego nie w środowisku produkcyjnym?" Można po prostu mówią, "Jest uruchamiany na Docker," ponieważ spakowanych aplikacji Docker można uruchomić na dowolnym obsługiwanym środowisku Docker i będzie działał jak ma na wszystkich miejsc docelowych wdrożenia (deweloperów, pytań i odpowiedzi, przemieszczania, produkcji, itd.).

![](./media/image3.png)

Rysunek 1-3: porównanie tradycyjnych maszyn wirtualnych do kontenerów Docker


>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (docker terminology.md)
