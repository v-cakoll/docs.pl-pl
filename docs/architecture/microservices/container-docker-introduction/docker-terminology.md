---
title: Terminologia platformy Docker
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Terminologia platformy Docker
ms.date: 01/30/2020
ms.openlocfilehash: fdcc5ec3603579c36d7339bd3ff651713b8eba88
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523334"
---
# <a name="docker-terminology"></a>Terminologia platformy Docker

W tej sekcji wymieniono terminy i definicje, które należy znać przed wejściem głębiej do platformy Docker. Aby uzyskać więcej definicji, zobacz obszerny [glosariusz](https://docs.docker.com/glossary/) dostarczony przez platformę Docker.

**Obraz kontenera:** pakiet ze wszystkimi zależnościami i informacjami potrzebnymi do utworzenia kontenera. Obraz zawiera wszystkie zależności (takie jak struktury) oraz konfiguracji wdrażania i wykonywania do użycia przez środowisko uruchomieniowe kontenera. Zazwyczaj obraz pochodzi z wielu obrazów podstawowych, które są warstwami ułożonymi jeden na drugim w celu utworzenia systemu plików kontenera. Obraz jest niezmienny po jego utworzeniu.

**Dockerfile**: Plik tekstowy zawierający instrukcje dotyczące tworzenia obrazu platformy Docker. Jest jak skrypt wsadowy, pierwszy wiersz stwierdza obraz podstawowy na początek, a następnie postępuj zgodnie z instrukcjami, aby zainstalować wymagane programy, skopiować pliki i tak dalej, aż pojawi się środowisko pracy, którego potrzebujesz.

**Kompilacja:** Akcja tworzenia obrazu kontenera na podstawie informacji i kontekstu dostarczonych przez jego Dockerfile, plus dodatkowe pliki w folderze, w którym jest zbudowany obraz. Obrazy można tworzyć za pomocą polecenia Docker:

> `docker build`

**Kontener:** Wystąpienie obrazu platformy Docker. Kontener reprezentuje wykonanie pojedynczej aplikacji, procesu lub usługi. Składa się z zawartości obrazu platformy Docker, środowiska wykonywania i standardowego zestawu instrukcji. Podczas skalowania usługi, można utworzyć wiele wystąpień kontenera z tego samego obrazu. Lub zadanie wsadowe można utworzyć wiele kontenerów z tego samego obrazu, przekazując różne parametry do każdego wystąpienia.

**Woluminy:** Zaoferuj zapisywalny system plików, którego kontener może używać. Ponieważ obrazy są tylko do odczytu, ale większość programów musi zapisywać do systemu plików, woluminy dodać zapisywalną warstwę, na górze obrazu kontenera, więc programy mają dostęp do zapisywalny system plików. Program nie wie, że uzyskuje dostęp do warstwowego systemu plików, to tylko system plików jak zwykle. Woluminy są aktywne w systemie hosta i są zarządzane przez docker.

**Tag:** Znacznik lub etykieta, które można zastosować do obrazów, tak aby można było zidentyfikować różne obrazy lub wersje tego samego obrazu (w zależności od numeru wersji lub środowiska docelowego).

**Kompilacja wieloetapowa:** Jest to funkcja, ponieważ docker 17.05 lub nowsze, który pomaga zmniejszyć rozmiar obrazów końcowych. W kilku zdaniach, z kompilacji wieloetapowej można użyć, na przykład, duży obraz podstawowy, zawierający zestaw SDK, do kompilowania i publikowania aplikacji, a następnie za pomocą folderu publikowania z małym obrazem podstawowym tylko do wykonywania, do uzyskania znacznie mniejszy obraz końcowy.

**Repozytorium (repozytorium)**: Zbiór powiązanych obrazów platformy Docker, oznaczony tagiem wskazującym wersję obrazu. Niektóre repozytoria zawierają wiele wariantów określonego obrazu, takich jak obraz zawierający zestaw SDK (cięższy), obraz zawierający tylko środowiska wykonawcze (lżejsze) itp. Te warianty mogą być oznaczone tagami. Pojedyncze repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows.

**Rejestr**: Usługa, która zapewnia dostęp do repozytoriów. Domyślnym rejestrem większości obrazów publicznych jest [Centrum platformy Docker](https://hub.docker.com/) (należące do platformy Docker jako organizacji). Rejestr zwykle zawiera repozytoria z wielu zespołów. Firmy często mają prywatne rejestry do przechowywania i zarządzania obrazami, które stworzyli. Innym przykładem jest usługa Azure Container Registry.

**Obraz wielocherzekowy:** W przypadku wielu architektur jest to funkcja, która upraszcza wybór odpowiedniego obrazu, zgodnie z platformą, na której działa docker. Na przykład, gdy Dockerfile żąda obrazu podstawowego **z mcr.microsoft.com/dotnet/core/sdk:3.1** z rejestru, to rzeczywiście pobiera **3.1-sdk-nanoserver-1909**, **3.1-sdk-nanoserver-1809** lub **3.1-sdk-buster-slim**, w zależności od systemu operacyjnego i wersji, w której jest uruchomiony docker.

**Docker Hub:** rejestr publiczny do przekazywania obrazów i pracy z nimi. Docker Hub zapewnia hosting obrazów platformy Docker, rejestry publiczne lub prywatne, wyzwalacze kompilacji i haki sieci web oraz integrację z GitHub i Bitbucket.

**Usługa Azure Container Registry:** zasób publiczny do pracy z obrazami platformy Docker i jego składnikami na platformie Azure. Zapewnia to rejestr, który jest blisko wdrożeń na platformie Azure i który daje kontrolę nad dostępem, dzięki czemu można używać grup i uprawnień usługi Azure Active Directory.

**Docker Trusted Registry (DTR)**: Usługa rejestru platformy Docker (z platformy Docker), która może być zainstalowana lokalnie, dzięki czemu działa w centrum danych i sieci organizacji. Jest to wygodne dla obrazów prywatnych, które powinny być zarządzane w przedsiębiorstwie. Zaufany rejestr platformy Docker jest dołączony jako część produktu centrum danych platformy Docker. Aby uzyskać więcej informacji, zobacz [Zaufany rejestr platformy Docker (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: Narzędzia programistyczne dla systemów Windows i macOS do tworzenia, uruchamiania i testowania kontenerów lokalnie. Docker CE dla systemu Windows udostępnia środowiska programistyczne dla kontenerów systemu Linux i Windows. Host platformy Docker systemu Linux w systemie Windows jest oparty na maszynie wirtualnej [funkcji Hyper-V.](https://www.microsoft.com/cloud-platform/server-virtualization) Host kontenerów systemu Windows jest oparty bezpośrednio na systemie Windows. Docker CE dla komputerów Mac opiera się na platformie Apple Hypervisor i [hypervisor xhyve](https://github.com/mist64/xhyve), który zapewnia linux docker hosta maszyny wirtualnej na Mac OS X. Docker CE dla Windows i dla Komputerów Mac zastępuje Docker Toolbox, który został oparty na Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: wersja docker w skali przedsiębiorstwa dla tworzenia systemów Linux i Windows.

**Redagowanie:** Narzędzie wiersza polecenia i format pliku YAML z metadanymi do definiowania i uruchamiania aplikacji z wieloma kontenerami. Definiujesz pojedynczą aplikację na podstawie wielu obrazów z jednym lub kilkoma plikami .yml, które mogą zastępować wartości w zależności od środowiska. Po utworzeniu definicji można wdrożyć całą aplikację wielu kontenerów za pomocą jednego polecenia (docker-compose up), który tworzy kontener na obraz na hoście platformy Docker.

**Klaster:** Kolekcja hostów platformy Docker jest widoczna tak, jakby była pojedynczym wirtualnym hostem platformy Docker, dzięki czemu aplikacja może skalować do wielu wystąpień usług rozłożonych na wiele hostów w klastrze. Klastry platformy Docker można tworzyć za pomocą platformy Kubernetes, usługi Azure Service Fabric, Docker Swarm i Mesosphere DC/OS.

**Orchestrator**: Narzędzie, które upraszcza zarządzanie klastrami i hostami platformy Docker. Koordynatorzy umożliwiają zarządzanie ich obrazów, kontenerów i hostów za pośrednictwem interfejsu wiersza polecenia lub interfejsu użytkownika graficznego. Można zarządzać siecią kontenerów, konfiguracjami, równoważeniem obciążenia, odnajdywaniem usług, wysoką dostępnością, konfiguracją hosta platformy Docker i nie tylko. Koordynator jest odpowiedzialny za uruchamianie, dystrybucję, skalowanie i korygowanie obciążeń w kolekcji węzłów. Zazwyczaj produkty orchestrator są te same produkty, które zapewniają infrastruktury klastra, takich jak Kubernetes i azure service fabric, wśród innych ofert na rynku.

>[!div class="step-by-step"]
>[Poprzedni](docker-defined.md)
>[następny](docker-containers-images-registries.md)
