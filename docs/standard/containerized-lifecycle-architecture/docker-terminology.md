---
title: Terminologia docker
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a622b2949c1d2277bb3e82617a5bc2d8cb432263
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="docker-terminology"></a>Terminologia docker

W tej sekcji wymieniono terminy i definicje, z którymi należy zapoznać się z przed zagłębieniem głębiej do Docker (dla dalszego definicje, zobacz szeroką gamę [słownik](https://docs.docker.com/glossary/) dostarczonych przez Docker na <https:// docs.docker.com/glossary/>:

-   **Kontener obrazu** pakiet ze wszystkich zależności i informacje potrzebne do utworzenia kontenera. Obraz zawiera wszystkie zależności (na przykład struktury) oraz wdrażania i konfiguracji, które mają być używane przez moduł wykonawczy kontenera. Zazwyczaj obraz pochodzi z wielu obrazów podstawowej czy warstwy stos jedną korzystającego z drugiej strony do utworzenia kontenera systemu plików. Obraz nie można modyfikować po jego utworzeniu.

-   **Kontener** wystąpienia obrazu Docker. Kontener reprezentuje obsługi dla pojedynczej aplikacji, procesu lub usługi. Składa się z zawartości obrazu Docker, środowisko uruchomieniowe i standardowy zestaw instrukcji. Podczas skalowania usługi, tworzy się wiele wystąpień kontenera w ten sam obraz. Lub zadania wsadowego można utworzyć wiele kontenerów na podstawie takiego samego obrazu, przekazywanie różnych parametrów do każdego wystąpienia.

-   **Tag** znaku lub etykietę, którą można stosować do obrazów, dzięki czemu można zidentyfikować różnych obrazy lub wersji tego samego obrazu (w zależności od numeru wersji lub środowisko docelowe).

-   **Plik Dockerfile** plik tekstowy, który zawiera instrukcje dotyczące sposobu tworzenia obrazu Docker.

-   **Tworzenie** akcji tworzenia obrazu kontenera na podstawie informacji i kontekstu dostarczonych przez jego plik Dockerfile, a także dodatkowe pliki w folderze, w którym obraz jest tworzony. Obrazy można tworzyć za pomocą polecenia Docker docker kompilacji.

-   **Repozytorium (znanej także jako repozytorium)** Kolekcja powiązanych obrazy usługi Docker i wskazujący wersję obrazu znacznika. Niektóre repozytoria zawierają wiele odmian określonego obrazu, takich jak obraz zawierającego obraz zawierającego tylko środowisk uruchomieniowych (jaśniejszy), zestawy SDK (większych), i tak dalej. Warianty te mogą być oznaczane przy użyciu tagów. Jednym repozytorium może zawierać wariantów platform, takich jak obraz systemu Linux i obrazu systemu Windows.

-   **Rejestru** usługa, która zapewnia dostęp do repozytoriów. Rejestr domyślne najbardziej publicznego obrazów jest [Centrum Docker](https://hub.docker.com/) (właściciel Docker jako organizacja). Rejestr zawiera zwykle repozytoria kilka zespołów. Firmy muszą często prywatnej rejestrów do przechowywania i zarządzania obrazami, które zostały one utworzone. *Azure rejestru kontenera* inny przykład.

-   **Centrum docker** publicznego rejestru w celu przekazania obrazów i pracować z nimi. Centrum docker zapewnia Docker hosting obrazu, rejestrów publicznych lub prywatnych kompilacji wyzwalaczy i punkty zaczepienia sieci web i integracja z usługą GitHub i Bitbucket.

-   **Azure rejestru kontenera** publicznego zasobów do pracy z obrazy usługi Docker i jego składniki na platformie Azure. Zapewnia to rejestru jest bliski wdrażanie na platformie Azure i zapewniającą kontrolę dostępu, umożliwiając przy użyciu grup usługi Azure Active Directory i uprawnienia.

-   **Docker zaufane rejestru (DTR)** usługi rejestru A Docker (z Docker), które można zainstalować lokalnie, aby znajduje się on w centrum danych i sieci organizacji. Jest wygodną metodą prywatnej obrazów, które mają być zarządzane w przedsiębiorstwie. Docker zaufane rejestru wchodzi w skład produktu Docker centrum danych. Aby uzyskać więcej informacji, przejdź do [https://docs.docker.com/docker-trusted-registry/overview/](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** narzędzia deweloperskie dla systemu Windows i macOS służący do tworzenia, uruchamiania i testowania kontenery lokalnie. CE docker dla systemu Windows zapewnia środowisk deweloperskich dla systemu Linux i kontenery systemu Windows. Host Docker systemu Linux w systemie Windows jest oparta na [funkcji Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) maszyny Wirtualnej. Host dla kontenerów systemu Windows opiera się bezpośrednio w systemie Windows. Docker CE dla komputerów Mac jest oparta na funkcji Hypervisor Apple framework i [funkcji hypervisor xhyve](https://github.com/mist64/xhyve), zapewniające hosta maszyny Wirtualnej systemu Linux Docker na Mac OS X. Docker CE dla systemu Windows i Mac zastępuje Docker przybornika, które było oparte na Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** wersji skali przedsiębiorstwa Docker narzędzi do tworzenia aplikacji systemu Linux i Windows.

-   **Redagowanie** narzędzia wiersza polecenia i yaml programu pliku w formacie z metadanymi do definiowania i uruchamiania multicontainer aplikacji. Należy zdefiniować pojedynczej aplikacji oparte na wiele obrazów z jednego lub więcej plików .yml, które można zastąpić wartości w zależności od środowiska. Po utworzeniu definicje multicontainer całej aplikacji można wdrożyć za pomocą jednego polecenia (docker-tworzą w górę) tworzącą kontener na obraz na hoście Docker.

-   **Klaster** kolekcji hostów Docker widoczne, tak jakby były jednego wirtualnego hosta Docker tak, aby aplikację można skalować do wielu wystąpień usług rozprzestrzeniające się na wielu hostach w klastrze. Można utworzyć klastry z Docker przy użyciu rozwiązania Docker Swarm, Mesosphere DC/OS Kubernetes i sieci szkieletowej usług Azure. (Jeśli używasz Docker Swarm do zarządzania klastrem, zwykle odwołujesz się do klastra jako *swarm* zamiast klastra.)

-   **Orchestrator** narzędzie, które upraszcza zarządzanie klastrów i hostów Docker. Przy użyciu orchestrators, można zarządzać ich obrazów, kontenery i hostami za pomocą interfejsu wiersza polecenia lub graficznego interfejsu użytkownika. Można zarządzać kontenera sieci, konfiguracji równoważenia obciążenia, odnajdywania usługi, wysoką dostępność, Konfiguracja hosta Docker i więcej. Orchestrator jest odpowiedzialny za uruchomione, dystrybucja skalowanie i naprawianie obciążeń przez zbiór węzłów. Zazwyczaj produkty programu orchestrator są te same produkty, które udostępniają infrastrukturę klastra, takie jak Mesosphere DC/OS, Kubernetes Docker Swarm i sieci szkieletowej usług Azure.


>[!div class="step-by-step"]
[Previous] (what-is-docker.md) [Next] (docker-containers-images-and-registries.md)
