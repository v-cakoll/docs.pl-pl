---
title: Terminologia platformy Docker
description: Podczas pracy z platformą Docker naucz się podstawowej terminologii używanej codziennie.
ms.date: 02/15/2019
ms.openlocfilehash: c352bf7235e8a3dc2d52bbbfe4390863fff9991f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295679"
---
# <a name="docker-terminology"></a>Terminologia platformy Docker

W tej sekcji wymieniono terminy i definicje, które należy zapoznać się z przed zagłębieniem się w platformę Docker. Aby uzyskać dalsze definicje, zobacz obszerny [słownik](https://docs.docker.com/glossary/) dostarczony przez platformę Docker.

**Obraz kontenera:** Pakiet ze wszystkimi zależnościami i informacjami potrzebnymi do utworzenia kontenera. Obraz zawiera wszystkie zależności (takie jak struktury) oraz konfiguracji wdrażania i wykonywania, które mają być używane przez program wykonawczy kontenera. Zazwyczaj obraz pochodzi z wielu obrazów bazowych, które są warstwami ułożonymi jeden na drugim, tworząc system plików kontenera. Obraz jest niezmienny po jego utworzeniu.

**Plik dokacji:** plik tekstowy zawierający instrukcje dotyczące tworzenia obrazu platformy Docker. To jak skrypt wsadowy, pierwszy wiersz określa obraz podstawowy na początek, a następnie postępuj zgodnie z instrukcjami, aby zainstalować wymagane programy, skopiować pliki i tak dalej, aż pojawi się środowisko pracy, którego potrzebujesz.

**Kompilacja:** Akcja tworzenia obrazu kontenera na podstawie informacji i kontekstu dostarczonych przez jego Plik Dockerfile, a także dodatkowe pliki w folderze, w którym jest zbudowany obraz. Obrazy można tworzyć za **`docker build`** pomocą polecenia Docker.

**Kontener:** Wystąpienie obrazu platformy Docker. Kontener reprezentuje wykonanie pojedynczej aplikacji, procesu lub usługi. Składa się z zawartości obrazu platformy Docker, środowiska wykonywania i standardowy zestaw instrukcji. Podczas skalowania usługi, można utworzyć wiele wystąpień kontenera z tego samego obrazu. Lub zadanie wsadowe można utworzyć wiele kontenerów z tego samego obrazu, przekazując różne parametry do każdego wystąpienia.

**Woluminy:** Zaoferuj zapisywalny system plików, z którego może korzystać kontener. Ponieważ obrazy są tylko do odczytu, ale większość programów musi zapisywać do systemu plików, woluminy dodać zapisywalną warstwę, na górze obrazu kontenera, więc programy mają dostęp do zapisywalny system plików. Program nie wie, że uzyskuje dostęp do warstwowego systemu plików, to tylko system plików jak zwykle. Woluminy są aktywne w systemie hosta i są zarządzane przez platformę Docker.

**Znacznik:** Znak lub etykietę, którą można zastosować do obrazów, tak aby można było zidentyfikować różne obrazy lub wersje tego samego obrazu (w zależności od numeru wersji lub środowiska docelowego).

**Kompilacja wieloetapowa:** Jest funkcją, ponieważ docker 17.05 lub nowszej, który pomaga zmniejszyć rozmiar obrazów końcowych. W kilku zdaniach, za pomocą kompilacji wieloetapowej, można użyć na przykład dużego obrazu podstawowego zawierającego zestaw SDK do kompilowania i publikowania aplikacji, a następnie do korzystania z folderu publikowania z małym obrazem podstawowym tylko w czasie wykonywania, aby uzyskać znacznie mniejszy obraz końcowy

**Repozytorium (repozytorium):** Kolekcja powiązanych obrazów platformy Docker, oznaczonych tagiem wskazującym wersję obrazu. Niektóre reppo zawierają wiele wariantów określonego obrazu, takich jak obraz zawierający zestawy SDK (cięższe), obraz zawierający tylko czas wykonywania (lżejszy) itp. Te warianty mogą być oznaczone tagami. Pojedyncze reppo może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows.

**Rejestr:** Usługa zapewniająca dostęp do repozytoriów. Domyślnym rejestrem większości obrazów publicznych jest [centrum docker hub](https://hub.docker.com/) (należące do platformy Docker jako organizacji). Rejestr zwykle zawiera repozytoria z wielu zespołów. Firmy często mają prywatne rejestry do przechowywania i zarządzania utworzonymi przez nie obrazami. Rejestr kontenerów platformy Azure jest kolejnym przykładem.

**Obraz wielołukowy:** Dla wielu architektury, jest funkcją, która upraszcza wybór odpowiedniego obrazu, w zależności od platformy, na **`FROM mcr.microsoft.com/dotnet/core/sdk:2.2`** której działa docker, na przykład, gdy Plik Dockerfile żąda obrazu podstawowego z rejestru, **`2.2-nanoserver-1709`** który faktycznie dostaje **`2.2-nanoserver-1803`**, **`2.2-nanoserver-1809`** lub **`2.2-stretch`**, w zależności od systemu operacyjnego i wersji, w której działa platforma Docker.

**Docker Hub**: Rejestr publiczny do przekazywania obrazów i pracy z nimi. Docker Hub zapewnia hosting obrazów platformy Docker, rejestry publiczne lub prywatne, wyzwalacze kompilacji i haki internetowe oraz integrację z usługami GitHub i Bitbucket.

**Rejestr kontenerów platformy Azure:** zasób publiczny do pracy z obrazami platformy Docker i jego składnikami na platformie Azure. Zapewnia to rejestr, który jest blisko wdrożeń na platformie Azure i który zapewnia kontrolę nad dostępem, umożliwiając korzystanie z grup i uprawnień usługi Azure Active Directory.

**Docker Trusted Registry (DTR):** Usługa rejestru platformy Docker (z platformy Docker), która może być instalowana lokalnie, dzięki czemu znajduje się w centrum danych i sieci organizacji. Jest to wygodne dla prywatnych obrazów, które powinny być zarządzane w przedsiębiorstwie. Rejestr zaufany docker jest uwzględniony jako część produktu docker Datacenter. Aby uzyskać więcej informacji, zobacz [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: Narzędzia programistyczne dla systemu Windows i macOS do lokalnego tworzenia, uruchamiania i testowania kontenerów. Platforma Docker CE dla systemu Windows udostępnia środowiska programistyczne dla kontenerów systemu Linux i Windows. Host platformy Docker systemu Linux w systemie Windows jest oparty na maszynie wirtualnej [funkcji Hyper-V.](https://www.microsoft.com/cloud-platform/server-virtualization) Host kontenerów systemu Windows jest bezpośrednio oparty na systemie Windows. Docker CE dla komputerów Mac jest oparty na platformie Hypervisor firmy Apple i [hipernadzorcy xhyve,](https://github.com/mist64/xhyve)która zapewnia maszynę wirtualną hosta Linux Docker w systemie Mac OS X. Docker CE dla Windows i dla komputerów Mac zastępuje Docker Toolbox, który został oparty na Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: wersja narzędzi docker w skali przedsiębiorstwa dla tworzenia systemów Linux i Windows.

**Redagowanie:** narzędzie wiersza polecenia i format pliku YAML z metadanymi do definiowania i uruchamiania aplikacji wielokontenerowych. Pojedynczą aplikację można zdefiniować na podstawie wielu obrazów z co najmniej jednym plikiem .yml, które mogą zastąpić wartości w zależności od środowiska. Po utworzeniu definicji można wdrożyć całą aplikację wielokontenerową za pomocą jednego polecenia (docker-compose up), które tworzy kontener na obraz na hoście platformy Docker.

**Klaster:** Kolekcja hostów platformy Docker uwidacznianych tak, jakby była pojedynczym wirtualnym hostem platformy Docker, dzięki czemu aplikacja może być skalowana do wielu wystąpień usług rozmieszczonych na wielu hostach w klastrze. Klastry platformy Docker można tworzyć za pomocą platformy Kubernetes, sieci szkieletowej usług Azure, roju platformy Docker i mezosfery DC/OS.

**Orchestrator**: Narzędzie, które upraszcza zarządzanie klastrami i hostami platformy Docker. Koordynatorzy umożliwiają zarządzanie ich obrazów, kontenerów i hostów za pośrednictwem interfejsu wiersza polecenia (CLI) lub graficznego interfejsu użytkownika. Można zarządzać siecią kontenerów, konfiguracjami, równoważeniem obciążenia, odnajdowaniem usług, wysoką dostępnością, konfiguracją hosta platformy Docker i nie tylko. Koordynator jest odpowiedzialny za uruchamianie, dystrybucji, skalowanie i uzdrawiania obciążeń w kolekcji węzłów. Zazwyczaj produkty koordynatora są te same produkty, które zapewniają infrastrukturę klastra, takich jak Kubernetes i sieci szkieletowej usług Azure, wśród innych ofert na rynku.

>[!div class="step-by-step"]
>[Poprzedni](what-is-docker.md)
>[następny](docker-containers-images-and-registries.md)
