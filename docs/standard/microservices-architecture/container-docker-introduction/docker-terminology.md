---
title: Terminologia docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Terminologia docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bbeff8c467e762e682fdaf99c8a11851b291db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576649"
---
# <a name="docker-terminology"></a>Terminologia docker

W tej sekcji wymieniono terminy i definicje, należy zapoznać się z przed pobraniem głębiej do rozwiązania Docker. Dla dalszego definicje, zobacz szeroką gamę [słownik](https://docs.docker.com/glossary/) dostarczonych przez Docker.

**Kontener obrazu**: pakiet ze wszystkich zależności i informacje potrzebne do utworzenia kontenera. Obraz zawiera wszystkie zależności (na przykład struktury) oraz konfiguracji wdrożenia i wykonywania mają być używane przez moduł wykonawczy kontenera. Zazwyczaj obraz pochodzi z wielu obrazów podstawowej są warstwy skumulowany na siebie w celu utworzenia kontenera systemu plików. Obraz nie można modyfikować po jego utworzeniu.

**Kontener**: wystąpienie obrazu Docker. Kontener reprezentuje wykonanie jednej aplikacji, procesu lub usługi. Składa się z zawartości obrazu Docker środowiska wykonawczego i standardowy zestaw instrukcji. Podczas skalowania usługi, tworzy się wiele wystąpień kontenera w ten sam obraz. Lub zadania wsadowego można utworzyć wiele kontenerów na podstawie takiego samego obrazu, przekazywanie różnych parametrów do każdego wystąpienia.

**Tag**: znak lub etykiety można stosować do obrazów, dzięki czemu można zidentyfikować różnych obrazy lub wersji tego samego obrazu (w zależności od numeru wersji lub środowisko docelowe).

**Plik Dockerfile**: plik tekstowy, który zawiera instrukcje dotyczące sposobu tworzenia obrazu Docker.

**Tworzenie**: Akcja tworzenia obrazu kontenera na podstawie informacji i kontekstu dostarczonych przez jego plik Dockerfile, a także dodatkowe pliki w folderze, w którym obraz jest tworzony. Można tworzyć obrazy przy użyciu polecenia Docker docker kompilacji.

**Repozytorium (repozytorium)**: kolekcja powiązanych obrazy usługi Docker, etykietą tag, który wskazuje wersję obrazu. Niektóre repozytoriów zawiera wiele odmian określonego obrazu, takich jak obraz zawierający zestawy SDK (większych) obraz zawierającego tylko środowisk uruchomieniowych (jaśniejszy) itp. Warianty te mogą być oznaczane przy użyciu tagów. Pojedynczy repozytorium może zawierać wariantów platform, takich jak obraz systemu Linux i obrazu systemu Windows.

**Rejestru**: usługa, która zapewnia dostęp do repozytoriów. Rejestr domyślne najbardziej publicznego obrazów jest [Centrum Docker](https://hub.docker.com/) (właściciel Docker jako organizacja). Rejestr zawiera zwykle repozytoria kilka zespołów. Firmy muszą często prywatnej rejestrów do przechowywania obrazów i zarządzanie nimi one utworzone. Rejestru kontenera platformy Azure jest inny przykład.

**Centrum docker**: publiczny rejestru w celu przekazania obrazów i pracować z nimi. Centrum docker zapewnia Docker hosting obrazu, rejestrów publicznych lub prywatnych kompilacji wyzwalaczy i punkty zaczepienia sieci web i integracja z usługą GitHub i Bitbucket.

**Azure rejestru kontenera**: publiczny zasobów do pracy z obrazy usługi Docker i jego składniki na platformie Azure. Zapewnia to rejestru jest bliski wdrażanie na platformie Azure i zapewniającą kontrolę dostępu, umożliwiając przy użyciu grup usługi Azure Active Directory i uprawnienia.

**Docker zaufane rejestru (DTR)**: usługi rejestru A Docker (z Docker), które mogą być zainstalowane lokalnie, znajduje się w obrębie centrum danych i sieci organizacji. Jest wygodną metodą prywatnej obrazów, które mają być zarządzane w przedsiębiorstwie. Docker zaufane rejestru wchodzi w skład produktu Docker centrum danych. Aby uzyskać więcej informacji, zobacz [Docker zaufane rejestru (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: narzędzia deweloperskie dla systemu Windows i macOS służący do tworzenia, uruchamiania i testowania kontenery lokalnie. CE docker dla systemu Windows zapewnia środowisk deweloperskich dla systemu Linux i kontenery systemu Windows. Host Docker systemu Linux w systemie Windows jest oparta na [funkcji Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) maszyny wirtualnej. Host dla kontenerów systemu Windows opiera się bezpośrednio w systemie Windows. Docker CE dla komputerów Mac jest oparta na funkcji Hypervisor Apple framework i [funkcji hypervisor xhyve](https://github.com/mist64/xhyve), zapewniające hosta maszyny wirtualnej systemu Linux Docker na Mac OS X. Docker CE dla systemu Windows i Mac zastępuje Docker przybornika, które było oparte na Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: wersja skali przedsiębiorstwa Docker narzędzi do tworzenia aplikacji systemu Linux i Windows.

**Redagowanie**: narzędzie wiersza polecenia i yaml programu pliku w formacie z metadanymi do definiowania i uruchamiania usługi kontenera aplikacji. Należy zdefiniować pojedynczej aplikacji oparte na wiele obrazów z jednego lub więcej plików .yml, które można zastąpić wartości w zależności od środowiska. Po utworzeniu definicje, możesz wdrożyć aplikację całego kontenera usługi za pomocą jednego polecenia (docker-tworzą w górę) tworzącą kontener na obraz na hoście Docker.

**Klaster**: zbiór hostów Docker widoczne tak, jakby była pojedynczego wirtualnego hosta Docker, dzięki czemu aplikacja można skalować do wielu wystąpień usług rozprzestrzeniające się na wielu hostach w klastrze. Docker klastrów mogą być tworzone z Docker Swarm, Mesosphere DC/OS Kubernetes i sieci szkieletowej usług Azure. (Jeśli używasz Docker Swarm do zarządzania klastrem, zwykle odwołujesz się do klastra jako *swarm* zamiast klastra.)

**Orchestrator**: narzędzie, które upraszcza zarządzanie klastrów i hostów Docker. Orchestrators umożliwiają zarządzanie obrazów, kontenery i hostami za pomocą interfejsu wiersza polecenia (CLI) lub graficznego interfejsu użytkownika. Można zarządzać kontenera sieci, konfiguracji równoważenia obciążenia, odnajdywania usługi, wysoką dostępność, Konfiguracja hosta Docker i więcej. Orchestrator jest odpowiedzialny za uruchomione, dystrybucja skalowanie i naprawianie obciążeń przez zbiór węzłów. Zazwyczaj produkty programu orchestrator są te same produkty, które udostępniają infrastrukturę klastra, takie jak Mesosphere DC/OS, Kubernetes Docker Swarm i sieci szkieletowej usług Azure.


>[!div class="step-by-step"]
[Previous] (docker-defined.md) [Next] (docker-containers-images-registries.md)
