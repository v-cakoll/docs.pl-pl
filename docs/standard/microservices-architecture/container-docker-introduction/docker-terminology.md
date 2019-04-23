---
title: Terminologia platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Terminologia platformy docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9cfb8ceb4fa1b95603ccc9aa006dd6ee3e8e8b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767724"
---
# <a name="docker-terminology"></a>Terminologia platformy Docker

W tej sekcji przedstawiono terminów i definicje, które należy zapoznać się z przed pobraniem bardziej platformy docker. Dodatkowo definicji, zobacz rozbudowane [słownik](https://docs.docker.com/glossary/) dostarczane przez platformę Docker.

**Obraz kontenera**: Pakiet ze wszystkimi zależnościami i informacje potrzebne do utworzenia kontenera. Obraz obejmuje wszystkie zależności (np. Platform) oraz wdrażaniem i uruchamianiem konfiguracji ma być używany przez kontener środowiska uruchomieniowego. Zwykle obraz pochodzi z wielu obrazy podstawowe, znajdujących się na siebie w celu utworzenia kontenera systemu plików, stos warstwy. Obraz jest niezmienny, po jego utworzeniu.

**Dockerfile**: Plik tekstowy, który zawiera instrukcje dotyczące sposobu tworzenia obrazu platformy Docker. Jest on podobny do skryptu wsadowego, pierwszy wiersz stany obrazu podstawowego z, a następnie postępuj zgodnie z instrukcjami, aby zainstalować wymagane programy, skopiuj pliki i tak dalej, dopóki nie zostanie wyświetlony środowiska pracy należy.

**Tworzenie**: Akcja kompilowania obrazu kontenera, na podstawie informacji i kontekst dostarczonych przez jego pliku Dockerfile, a także dodatkowe pliki w folderze, w którym obraz jest kompilowany. Możesz tworzyć obrazy platformy Docker **kompilacji platformy docker** polecenia. 

**kontener**: Wystąpienie obrazu platformy Docker. Kontener reprezentuje wykonanie jednej aplikacji, proces lub usługi. Składa się z zawartości obrazu platformy Docker, środowisko wykonawcze i standardowy zestaw instrukcji. Podczas skalowania usługi, tworzysz wiele wystąpień kontenera za pomocą tego samego obrazu. Zadania usługi batch można też tworzyć wiele kontenerów za pomocą tego samego obrazu, przekazując różnych parametrów do każdego wystąpienia.

**Woluminy**: Oferują zapisywalny system plików, można użyć kontenera. Ponieważ obrazy są przeznaczone tylko do odczytu, ale w większości programów trzeba było pisać w systemie plików, woluminy Dodaj warstwę zapisywalny, dodaną do obrazu kontenera, dzięki czemu programy mają dostęp do zapisu plików. Program nie może ustalić uzyskuje dostęp do plików warstwowych, jest po prostu systemu plików w zwykły sposób. Woluminy live w systemie hosta, a także są zarządzane przez platformę Docker.

**Tag**: Znak lub etykiety, które można stosować do obrazów, dzięki czemu można zidentyfikować różne obrazy lub wersji tego samego obrazu (w zależności od numeru wersji lub środowiska docelowego).

**Kompilacja wieloetapowych**: Jest funkcją, od 17.05 platformy Docker lub wyższym, która pomaga zredukować rozmiar końcowy obrazów. W kilku zdaniach wieloetapowych kompilacji można użyć, na przykład duży obraz podstawowy, zawierające zestaw SDK do kompilowania i publikowania aplikacji i następnie przy użyciu folderu publikowania za pomocą małych tylko do środowiska wykonawczego obrazu podstawowego, dają znacznie mniejszy obraz końcowe

**Repozytorium (repozytorium)**: Zbiór powiązanych obrazów platformy Docker, oznaczone znacznikiem, który wskazuje wersję obrazu. Niektóre repozytoria zawierają wiele wariantów określonego obrazu, takich jak obrazy, które zawierają zestawy SDK (większe), obrazy, które zawierają tylko środowisk uruchomieniowych (jaśniejszy) itp. Warianty te mogą być oznaczone tagami. Jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz.

**Rejestr**: To usługa, która zapewnia dostęp do repozytoriów. Rejestr domyślne obrazy najbardziej publiczny jest [usługi Docker Hub](https://hub.docker.com/) (właściciel platformy Docker jako organizacja). Rejestr zawiera zazwyczaj repozytoriów z wielu zespołów. Firmy często mają prywatnych rejestrów do przechowywania i zarządzania obrazami, którym zostały utworzone. Usługa Azure Container Registry jest inny przykład.

**Obraz architektury wielu**: W przypadku wielu architektury jest funkcja, która ułatwia wybór odpowiedniej obrazu, zależnie od platformy, na którym działa platformy Docker, np. gdy plik Dockerfile żąda obrazu podstawowego **z mcr.microsoft.com/dotnet/core/sdk:2.2**z rejestru faktycznie pobiera **2.2-sdk-nanoserver-1709**, **2.2-sdk-nanoserver-1803**, **2.2-sdk-nanoserver-1809** lub **2.2 - zestaw SDK stretch**, w zależności od systemu operacyjnego i wersji, w którym platformy Docker jest uruchomiona.

**Docker Hub**: Publicznego rejestru przekazywania obrazów i pracować z nimi. Usługi docker Hub udostępnia platformy Docker hostingu obrazu, publicznych lub prywatnych rejestrów, wyzwalaczy kompilacji oraz elementów web hook i integracja z usługą GitHub i Bitbucket.

**Usługa Azure Container Registry**: Zasób publicznego do pracy z obrazów platformy Docker i jego składniki na platformie Azure. Dzięki temu rejestru, który znajduje się w pobliżu wdrożeń na platformie Azure i zapewnia kontrolę dostępu, dzięki czemu można użyć usługi Azure Active Directory, grup i uprawnień.

**Docker Trusted Registry (DTR)**: Rejestru usługi Docker (z platformy Docker), może być zainstalowany w środowisku lokalnym, więc znajduje się w obrębie centrum danych organizacji i sieć. Jest to wygodne dla prywatnych obrazów, które powinny być zarządzane w ramach organizacji. Docker Trusted Registry wchodzi w skład produktów Docker Datacenter. Aby uzyskać więcej informacji, zobacz [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Platformę docker Community Edition (CE)**: Narzędzia programistyczne dla Windows i macOS, tworzenia, uruchamiania i testowania kontenery lokalnie. Docker CE dla Windows zapewnia środowisk deweloperskich dla systemu Linux i Windows kontenery. Hosta platformy Docker w systemie Linux na Windows opiera się na [funkcji Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) maszyny wirtualnej. Host dla kontenerów Windows jest bezpośrednio oparty na Windows. Docker CE dla komputerów Mac opiera się w ramach funkcji Hypervisor firmy Apple i [funkcji hypervisor xhyve](https://github.com/mist64/xhyve), zapewniającą maszyny wirtualnej hosta platformy Docker w systemie Linux na systemu operacyjnego Mac Docker X. CE for Windows i dla komputerów Mac zastępuje przybornika Docker zależała od bazy danych Oracle VirtualBox.

**Rozwiązania docker Enterprise Edition (EE)**: Wersja skali korporacyjnej narzędzia platformy Docker do tworzenia aplikacji systemu Linux i Windows.

**Redagowanie**: Narzędzie wiersza polecenia i YAML pliku formatu metadanych do definiowania i uruchamiania aplikacji obsługującej wiele kontenerów. Należy zdefiniować pojedynczej aplikacji opartych na obrazach wielu z co najmniej jeden plik yml, które mogą zastępować wartości w zależności od środowiska. Po utworzeniu definicjami można wdrożyć aplikacji wielokontenerowych zupełnie za pomocą jednego polecenia (docker-compose się), tworzy kontener na obraz na hoście platformy Docker.

**Klaster**: Kolekcja hostów platformy Docker, udostępniane tak, jakby była pojedynczego wirtualnego hosta platformy Docker, tak aby aplikację można skalować do wielu wystąpień usługi rozkładają się na wielu hostach w klastrze. Klastry platformy docker można tworzyć przy użyciu rozwiązania Kubernetes, Azure Service Fabric, Docker Swarm i Mesosphere DC/OS.

**Orchestrator**: Narzędzie, które upraszcza zarządzanie klastrów i hostów platformy Docker. Orkiestratory umożliwiają zarządzanie ich obrazów kontenerów i hostami za pomocą interfejsu wiersza polecenia (CLI) lub graficznego interfejsu użytkownika. Można zarządzać kontenerowa, konfiguracje, równoważenia obciążenia, odnajdowania usług, wysoką dostępność, Konfiguracja hosta platformy Docker i więcej. Program orchestrator jest odpowiedzialny za systemem, dystrybucja, skalowanie i naprawiania obciążeń między kolekcję węzłów. Zazwyczaj produkty programu orchestrator są tego samego produktów, które udostępniają infrastrukturę klastra, takich jak Kubernetes i usługi Azure Service Fabric, wśród innych ofert na rynku. 

>[!div class="step-by-step"]
>[Poprzednie](docker-defined.md)
>[dalej](docker-containers-images-registries.md)