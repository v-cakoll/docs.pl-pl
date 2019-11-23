---
title: Co to jest Docker?
description: Zapoznaj się z bardziej szczegółowymi informacjami na temat platformy Docker, ale proste analogowe rozwiązanie może Ci pomóc.
ms.date: 02/15/2019
ms.openlocfilehash: 8636ae3b1ad32158e10ce2aa58423f9c9824d8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738157"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) to [projekt typu "open source"](https://github.com/docker/docker) służący do automatyzowania wdrażania aplikacji jako przenośne, samoobsługowe kontenery, które można uruchamiać w chmurze lub lokalnie. Platforma Docker to również [firma](https://www.docker.com/) , która wspiera i zmienia tę technologię, pracując w współpracy z dostawcami chmury, Linux i Windows, w tym z firmą Microsoft.

![Diagram przedstawiający miejsca, w których można uruchamiać kontenery platformy Docker.](./media/what-is-docker/docker-containers-run-anywhere.png)

**Rysunek 1-2**. Platforma Docker wdraża kontenery we wszystkich warstwach chmury hybrydowej

Jak pokazano na powyższym diagramie, kontenery platformy Docker mogą działać w dowolnym miejscu, lokalnie w centrum danych klienta, w zewnętrznym dostawcy usług lub w chmurze na platformie Azure. Kontenery obrazów platformy Docker można również uruchamiać natywnie w systemach Linux i Windows. Jednak obrazy systemu Windows można uruchamiać tylko na hostach z systemem Windows, a obrazy systemu Linux można uruchamiać na hostach z systemem Linux i hostach Windows (do tej pory przy użyciu maszyny wirtualnej funkcji Hyper-V z systemem Linux), gdzie host oznacza serwer lub maszynę wirtualną.

Deweloperzy mogą używać środowisk programistycznych w systemie Windows, Linux lub macOS. Na komputerze deweloperskim deweloper uruchamia Host platformy Docker, na którym są wdrażane obrazy platformy Docker, w tym aplikację i jej zależności. Deweloperzy, którzy pracują w systemie Linux lub na komputerach Mac, używają hosta platformy Docker, który jest oparty na systemie Linux i mogą tworzyć obrazy tylko dla kontenerów systemu Linux. (Deweloperzy pracujący na komputerze Mac mogą edytować kod lub uruchamiać interfejs wiersza polecenia platformy Docker z macOS, ale w przypadku tego zapisu kontenery nie są uruchamiane bezpośrednio na macOS). Deweloperzy, którzy pracują w systemie Windows, mogą tworzyć obrazy dla kontenerów systemu Linux lub Windows.

Do hostowania kontenerów w środowiskach deweloperskich i dostarczania dodatkowych narzędzi programistycznych, Docker [Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows lub dla macOS. Te produkty instalują niezbędną maszynę wirtualną (host platformy Docker) do hostowania kontenerów. Platforma Docker udostępnia również dostęp do [platformy Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), która jest przeznaczona do programowania w przedsiębiorstwie i jest używana przez zespoły IT, którzy tworzą, dostarczają i uruchamiają duże aplikacje o krytycznym znaczeniu dla firmy w środowisku produkcyjnym.

Aby uruchamiać [kontenery systemu Windows](/virtualization/windowscontainers/about/), istnieją dwa typy środowiska uruchomieniowego:

- **Kontenery systemu Windows Server** zapewniają izolację aplikacji za poorednictwem technologii izolacji procesów i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i ze wszystkimi kontenerami uruchomionymi na hoście.

- **Kontenery funkcji Hyper-V** rozszerzają się na izolację zapewnioną przez kontenery systemu Windows Server, uruchamiając każdy kontener w wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest udostępniane kontenerom funkcji Hyper-V, co zapewnia lepszą izolację.

Obrazy dla tych kontenerów są tworzone i działają w taki sam sposób. Różnica polega na tym, jak kontener jest tworzony na podstawie obrazu — uruchomienie kontenera funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać szczegółowe informacje, zobacz [kontenery funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenerów platformy Docker z maszynami wirtualnymi

Rysunek 1-3 przedstawia porównanie między maszynami wirtualnymi i kontenerami platformy Docker.

![Diagram przedstawiający Porównanie środowisk maszyn wirtualnych i kontenerów.](./media/what-is-docker/comparison-vms-docker-conatiners.png)

**Rysunek 1-3**. Porównanie tradycyjnych maszyn wirtualnych z kontenerami platformy Docker

Jak pokazano na powyższym diagramie, w przypadku maszyn wirtualnych istnieją trzy warstwy podstawowe na serwerze hosta. W dolnej części: infrastruktura, system operacyjny hosta i funkcja hypervisor. Na każdej maszynie wirtualnej każda maszyna wirtualna ma własny system operacyjny i wszystkie niezbędne biblioteki. Z drugiej strony, dla platformy Docker, serwer hosta ma tylko infrastrukturę i system operacyjny. W tym celu aparat kontenera utrzymuje izolowane kontenery, ale umożliwia im udostępnianie usług pojedynczej podstawowej systemu operacyjnego.

Ponieważ kontenery wymagają znacznie mniejszej ilości zasobów (na przykład nie potrzebują pełnego systemu operacyjnego), można je łatwo wdrażać i uruchamiać szybko. Dzięki temu można uzyskać większą gęstość, co oznacza, że umożliwia uruchamianie więcej usług w tej samej jednostce sprzętowej, co zmniejsza koszty.

Efektem ubocznym uruchamiania na tym samym jądrze jest mniejsza izolacja niż maszyny wirtualne.

Głównym celem obrazu jest zapewnienie tego samego środowiska (zależności) w różnych wdrożeniach. Oznacza to, że można debugować go na maszynie, a następnie wdrożyć na innym komputerze, co gwarantuje odpowiednie środowisko.

Obraz kontenera to sposób na spakowanie aplikacji lub usługi oraz wdrożenie jej w sposób niezawodny i powtarzalny. Można powiedzieć, że platforma Docker nie jest tylko technologią, ale również z wytwarzeniem i procesem.

W przypadku korzystania z platformy Docker nie są nasłuchiwani deweloperzy, "działa na mojej maszynie, dlaczego nie w środowisku produkcyjnym?". Mogą one powiedzieć, "działa na platformie Docker", ponieważ spakowana aplikacja platformy Docker może być wykonywana na dowolnym obsługiwanym środowisku Docker i działa tak, jak w przypadku wszystkich celów wdrożenia (takich jak dev, pytań i odpowiedzi, przemieszczanie i produkcja).

## <a name="a-simple-analogy"></a>Prosta analogowa

Być może prosta analogowa może pomóc Ci w opanujesz podstawowej koncepcji platformy Docker.

Wróćmy w czasie do 1950s przez chwilę. Nie wykryto żadnych procesorów programu Word, a kopiarki były używane wszędzie (również w rodzaju).

Wyobraź sobie, że użytkownik jest odpowiedzialny za szybkie wydawanie partii liter zgodnie z potrzebami, aby wysłać je do klientów za pomocą rzeczywistych dokumentów i kopert, aby dostarczyć fizycznie do adresu każdego klienta (nie wysłano jeszcze wiadomości e-mail).

W pewnym momencie należy pamiętać, że litery są tylko kompozycją dużego zestawu akapitów, które są wybierane i rozmieszczane w razie potrzeby zgodnie z przeznaczeniem. w tym celu należy opracować system do szybkiego wydawania listów, co oczekuje na pobranie Hefty.

System jest prosty:

1. Zaczynasz od talii arkuszy przezroczystych zawierających jeden akapit każdy.

2. Aby wystawić zestaw liter, należy wybrać arkusze z akapitami, które są potrzebne, a następnie przetworzyć je i wyrównać.

3. Na koniec należy umieścić zestaw w kopiarkach i nacisnąć przycisk Rozpocznij, aby utworzyć dowolną liczbę liter zgodnie z potrzebami.

Upraszcza to, że jest to podstawowy pomysł dotyczący platformy Docker.

W programie Docker każda warstwa to powstały zestaw zmian, które przechodzą do systemu plików po wykonaniu polecenia, na przykład instalując program.

W związku z tym, gdy po skopiowaniu warstwy zostanie "odszukasz", zobaczysz wszystkie pliki z uwzględnieniem warstwy podczas instalacji programu.

Obraz można traktować jako pomocniczy dysk twardy tylko do odczytu gotowy do zainstalowania na komputerze, na którym jest już zainstalowany system operacyjny.

Podobnie można traktować kontener jako "komputer" z zainstalowanym dyskiem twardym obrazu. Kontener, podobnie jak komputer, może być włączony lub wyłączony.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](docker-terminology.md)
