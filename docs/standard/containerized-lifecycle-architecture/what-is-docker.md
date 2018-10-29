---
title: Co to jest Docker?
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 056fb613c078cc407380060dc11890406ac8cffd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197681"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projektu open-source](https://github.com/docker/docker) automatyzację wdrażania aplikacji jako przenośne, samowystarczalne kontenery, działających w chmurze lub lokalnie (zobacz rysunek 1 - 2). Docker to również [firmy](https://www.docker.com/) który promuje i rozwija tej technologii w współpracy z chmury, Linux i Windows producentów, takie jak Microsoft.

![](./media/image2.png)

Rysunek 1 – 2: platformy Docker służy do wdrażania kontenerów we wszystkich warstwach chmury hybrydowej

Kontenery obrazu platformy docker można uruchomić natywnie w systemie Linux i Windows. Jednak obrazów Windows można uruchamiać tylko na hostach Windows i obrazów systemu Linux można uruchamiać tylko na hostach systemu Linux, co oznacza serwera hosta lub maszyny Wirtualnej.

Deweloperzy mogą używać środowisk deweloperskich w Windows, Linux lub macOS. Na komputerze deweloperskim Deweloper uruchamia hosta platformy Docker, które Docker obrazy są wdrożone, łącznie z aplikacji i jego zależności. Deweloperzy pracujący w systemie Linux lub na komputerze Mac, użyj hosta platformy Docker, który jest opartych na systemie Linux, a mogą utworzyć obrazy tylko dla kontenerów systemu Linux. (Deweloperzy pracujący na komputerze Mac można edytować kod lub uruchomić interfejs wiersza polecenia platformy Docker \[interfejsu wiersza polecenia\] z systemem macOS, ale na chwilę obecną, nie uruchamiaj kontenery bezpośrednio w systemie macOS.) Deweloperzy, którzy pracują nad Windows można tworzyć obrazy systemu Linux lub Windows kontenery.

Do hostowania kontenerów w środowiskach programistycznych i zapewniają narzędzia programistyczne dodatkowe, Docker jest dostarczany [Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows lub macOS. Te produkty zainstalować niezbędnych maszyny Wirtualnej (hosta platformy Docker) do hostowania kontenerów. Docker powoduje udostępnienie [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), który jest przeznaczony dla rozwoju przedsiębiorstwa i jest używana przez zespoły IT, którzy tworzą, dostarczanie i uruchamiać duże aplikacje krytyczne dla działania firmy w środowisku produkcyjnym.

Aby uruchomić [kontenery Windows](/virtualization/windowscontainers/about/), istnieją dwa rodzaje środowisk uruchomieniowych:

-   **Kontenera z systemem Windows Server** to środowisko wykonawcze zapewnia izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra hosta kontenera i wszystkie kontenery uruchomione na hoście.

-   **Kontener funkcji Hyper-V** rozszerza to izolacja świadczona przez kontenery systemu Windows Server, uruchamiając każdego kontenera na wysoce zoptymalizowanej maszynie Wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest udostępniony za pomocą kontenerów funkcji Hyper-V, zapewniając lepsze izolację.

Obrazy dla tych kontenerów są tworzone w taki sam sposób, a funkcja takie same. Różnica polega na tym, w jaki sposób ten kontener jest tworzony z obrazu — uruchamianie kontenera funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać więcej informacji, zobacz [kontenery funkcji Hyper-V](/virtualization/windowscontainers/about/).

## <a name="comparing-docker-containers-with-vms"></a>Porównywanie kontenerów platformy Docker przy użyciu maszyn wirtualnych

Rysunek 1 – 3 przedstawiono porównanie między maszynami wirtualnymi i Docker kontenerów.

Ponieważ kontenery wymaga znacznie mniej zasobów (na przykład, nie ma potrzeby pełnej wersji systemu operacyjnego), są one łatwe do wdrożenia i szybkiego uruchamiania. Dzięki temu umożliwiają zwiększenie gęstości, co oznacza, czy można uruchomić więcej usług w tej samej jednostce sprzętu, zmniejszając w ten sposób kosztów.

Jako efekt uboczny uruchomionych na tym samym jądra osiągasz izolacji jest mniejszy niż maszyny wirtualne.

Głównym celem obrazu jest fakt, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, można to debugować na maszynie i następnie wdrożyć go na inny komputer, z tym samym środowisku, gwarantowana.

Obraz kontenera jest sposobem pakietu aplikacji lub usługi oraz wdrożyć ją w sposób niezawodny i odtworzenia. W związku z tym Docker nie jest tylko technologii, również jest filozofii i procesu.

Korzystając z platformy Docker, nie otrzymasz od deweloperów powiedzieć, "działa na komputerze, dlaczego w środowisku produkcyjnym?" Można po prostu mówią, "Korzystają one z platformy Docker," ponieważ spakowanej aplikacji platformy Docker, można uruchomić na dowolnym obsługiwanych środowisku platformy Docker i sposób, który ma to na wszystkich docelowych wdrożenia (deweloperskie, QA, przemieszczania, produkcyjne itp.), będzie działać.

![](./media/image3.png)

Rysunek 1-3: porównanie tradycyjne maszyny wirtualne dostępne w kontenerach platformy Docker


>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](docker-terminology.md)
