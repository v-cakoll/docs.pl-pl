---
title: Terminologia platformy docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 1efb2fa567bd452f0a0a5ee5afb6f759511e4145
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151317"
---
# <a name="docker-terminology"></a>Terminologia platformy docker

W tej sekcji przedstawiono terminów i definicje, z którymi należy zapoznać się z przed zagłębieniem bardziej platformy docker (uzyskać dalsze definicje, zobacz rozbudowane [słownik](https://docs.docker.com/glossary/) dostarczane przez platformę Docker na <https://docs.docker.com/glossary/>:

-   **Obraz kontenera** pakietu ze wszystkimi zależnościami i informacje potrzebne do tworzenia kontenera. Obraz obejmuje wszystkie zależności (np. Platform) oraz wdrażania i konfiguracji, który będzie używany przez kontener środowiska uruchomieniowego. Zwykle obraz pochodzi z wielu obrazy podstawowe, są warstwy ułożone jeden na jego podstawie innych w celu utworzenia kontenera systemu plików. Obraz jest niezmienny, po jego utworzeniu.

-   **Kontener** wystąpienia obrazu platformy Docker. Kontener reprezentuje środowiska uruchomieniowego dla pojedynczej aplikacji, proces lub usługi. Składa się z zawartości obrazu platformy Docker, środowisko uruchomieniowe i standardowy zestaw instrukcji. Podczas skalowania usługi, tworzysz wiele wystąpień kontenera za pomocą tego samego obrazu. Lub zadania usługi batch można tworzyć wiele kontenerów za pomocą tego samego obrazu, przekazując różnych parametrów do każdego wystąpienia.

-   **Tag** znaku lub etykiety, które można zastosować do obrazów, dzięki czemu można zidentyfikować różne obrazy lub wersji tego samego obrazu (w zależności od numeru wersji lub środowisko docelowe).

-   **Plik Dockerfile** plik tekstowy, który zawiera instrukcje dotyczące sposobu tworzenia obrazu platformy Docker.

-   **Tworzenie** Akcja kompilowania obrazu kontenera na podstawie informacji i kontekst dostarczonych przez jego pliku Dockerfile, a także dodatkowe pliki w folderze, w którym obraz jest kompilowany. Możesz tworzyć obrazy za pomocą polecenia kompilacji platformy docker platformy Docker.

-   **Repozytorium (znany także jako repozytorium)** zbiór powiązanych obrazów platformy Docker z etykietą znacznik, który wskazuje wersję obrazu. Niektóre repozytoria zawierają wiele wariantów określonego obrazu, takich jak obrazy, które zawierają zestawy SDK (większe), obrazy, które zawierają tylko środowisk uruchomieniowych (jaśniejszy), i tak dalej. Warianty te mogą być oznaczone tagami. Pojedyncze repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz.

-   **Rejestr** to usługa, która zapewnia dostęp do repozytoriów. Rejestr domyślne obrazy najbardziej publiczny jest [usługi Docker Hub](https://hub.docker.com/) (właściciel platformy Docker jako organizacja). Rejestr zawiera zazwyczaj repozytoriów z wielu zespołów. Firmy często mają prywatnych rejestrów do przechowywania obrazów i zarządzanie nimi, które zostały przez nich utworzone. *Usługa Azure Container Registry* jest inny przykład.

-   **Usługi docker Hub** publicznego rejestru przekazywania obrazów i pracować z nimi. Usługi docker Hub udostępnia platformy Docker hostingu obrazu, publicznych lub prywatnych rejestrów, wyzwalaczy kompilacji oraz elementów web hook i integracja z usługą GitHub i Bitbucket.

-   **Usługa Azure Container Registry** zasób publicznego do pracy z obrazów platformy Docker i jego składniki na platformie Azure. Dzięki temu rejestru, który znajduje się w pobliżu wdrożeń na platformie Azure i zapewnia kontrolę dostępu, dzięki czemu można użyć usługi Azure Active Directory, grup i uprawnień.

-   **Docker Trusted Registry (DTR)** usługi rejestru aparatu Docker (z platformy Docker), który można zainstalować w środowisku lokalnym, aby znajduje się w obrębie centrum danych i sieci w organizacji. Jest to wygodne dla prywatnych obrazów, które powinny być zarządzane w ramach organizacji. Docker Trusted Registry wchodzi w skład produktów Docker Datacenter. Aby uzyskać więcej informacji, przejdź do [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** narzędzia programistyczne dla Windows i macOS, tworzenia, uruchamiania i testowania kontenery lokalnie. Docker CE dla Windows zapewnia środowisk deweloperskich dla systemu Linux i Windows kontenery. Hosta platformy Docker w systemie Linux na Windows opiera się na [funkcji Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) maszyny Wirtualnej. Host dla kontenerów Windows jest bezpośrednio oparty na Windows. Docker CE dla komputerów Mac opiera się w ramach funkcji Hypervisor firmy Apple i [funkcji hypervisor xhyve](https://github.com/mist64/xhyve), zapewniającą hosta platformy Docker w systemie Linux maszyny Wirtualnej na systemu operacyjnego Mac Docker X. CE for Windows i dla komputerów Mac zastępuje przybornika platformy Docker został oparty na Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** skali korporacyjnej wersję narzędzia platformy Docker do tworzenia aplikacji systemu Linux i Windows.

-   **Redagowanie** narzędzie wiersza polecenia i YAML pliku w formacie za pomocą metadanych do definiowania i uruchamiania aplikacji z wieloma kontenerami w celu. Należy zdefiniować pojedynczej aplikacji opartych na obrazach wielu z co najmniej jeden plik yml, które mogą zastępować wartości w zależności od środowiska. Po utworzeniu definicjami wieloma kontenerami w celu całej aplikacji można wdrożyć za pomocą jednego polecenia (docker-compose się), tworzy kontener na obraz na hoście platformy Docker.

-   **Klaster** zbiór hostów platformy Docker, udostępniane tak, jakby były one jednego wirtualnego hosta platformy Docker tak, aby aplikację można skalować do wielu wystąpień usługi rozkładają się na wielu hostach w klastrze. Można utworzyć klastry platformy Docker przy użyciu rozwiązania Docker Swarm, Mesosphere DC/OS, Kubernetes i usługi Azure Service Fabric. (Jeśli używasz rozwiązania Docker Swarm dla zarządzania klastrem, zwykle odwołasz się do klastra jako *swarm* zamiast klastra.)

-   **Program orchestrator** narzędzia, która upraszcza zarządzanie klastrów i hostów platformy Docker. Przy użyciu koordynatorów, można zarządzać ich obrazów kontenerów i hostami za pomocą interfejsu wiersza polecenia lub graficznego interfejsu użytkownika. Można zarządzać kontenerowa, konfiguracje, równoważenia obciążenia, odnajdowania usług, wysoką dostępność, Konfiguracja hosta platformy Docker i więcej. Program orchestrator jest odpowiedzialny za systemem, dystrybucja, skalowanie i naprawiania obciążeń między kolekcję węzłów. Zazwyczaj produkty programu orchestrator są tego samego produktów, które udostępniają infrastrukturę klastra, takie jak Mesosphere DC/OS, Kubernetes, Docker Swarm i usługi Azure Service Fabric.

>[!div class="step-by-step"]
>[Poprzednie](what-is-docker.md)
>[dalej](docker-containers-images-and-registries.md)