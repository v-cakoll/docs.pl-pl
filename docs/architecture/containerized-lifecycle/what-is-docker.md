---
title: Co to jest Docker?
description: Trochę głębiej w swoim rozumieniu Docker, prosta analogia tutaj może ci pomóc.
ms.date: 02/15/2019
ms.openlocfilehash: e3b3685f2fc6d5a9d33bb176d04ca910f0289344
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76919878"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Platforma Docker](https://www.docker.com/) jest [projektem typu open source](https://github.com/docker/docker) do automatyzacji wdrażania aplikacji jako przenośnych, samowystarczalnych kontenerów, które można uruchamiać w chmurze lub lokalnie. Docker jest również [firmą,](https://www.docker.com/) która promuje i rozwija tę technologię, współpracując z dostawcami chmury, systemu Linux i Windows, w tym microsoft.

![Diagram przedstawiający miejsca, w których można uruchomić kontenery platformy Docker.](./media/what-is-docker/docker-containers-run-anywhere.png)

**Rysunek 1-2**. Platforma Docker wdraża kontenery na wszystkich warstwach chmury hybrydowej

Jak pokazano na powyższym diagramie kontenery platformy Docker można uruchamiać w dowolnym miejscu, lokalnie w centrum danych klienta, w zewnętrznym dostawcy usług lub w chmurze, na platformie Azure. Kontenery obrazów platformy Docker można również uruchamiać natywnie w systemach Linux i Windows. Jednak obrazy systemu Windows można uruchamiać tylko na hostach systemu Windows, a obrazy systemu Linux mogą być uruchamiane na hostach systemu Linux i hostach systemu Windows (do tej pory przy użyciu maszyny Wirtualnej systemu Linux hyper-V), gdzie host oznacza serwer lub maszynę wirtualną.

Deweloperzy mogą korzystać ze środowisk programistycznych w systemach Windows, Linux lub macOS. Na komputerze deweloperskim deweloper uruchamia hosta platformy Docker, w którym są wdrażane obrazy platformy Docker, w tym aplikacji i jej zależności. Deweloperzy, którzy pracują na linuksie lub komputerze Mac, używają hosta platformy Docker, który jest oparty na systemie Linux i mogą tworzyć obrazy tylko dla kontenerów systemu Linux. (Deweloperzy pracujący na komputerze Mac mogą edytować kod lub uruchamiać kod CLI platformy Docker z systemu macOS, ale od tego zapisu kontenery nie są uruchamiane bezpośrednio w systemie macOS). Deweloperzy, którzy pracują w systemie Windows, mogą tworzyć obrazy dla kontenerów systemu Linux lub Windows.

Aby hostować kontenery w środowiskach programistycznych i udostępniać dodatkowe narzędzia deweloperskie, platforma Docker wysyła [platformę Docker Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows lub systemu macOS. Te produkty instalują niezbędną maszynę wirtualną (host docker) do obsługi kontenerów. Platforma Docker udostępnia również [platformę Docker Enterprise Edition (EE),](https://www.docker.com/enterprise-edition)która jest przeznaczona do rozwoju przedsiębiorstw i jest używana przez zespoły IT, które tworzą, akcesorią i uruchamianiem dużych aplikacji o znaczeniu krytycznym dla firmy w środowisku produkcyjnym.

Aby uruchomić [kontenery systemu Windows,](/virtualization/windowscontainers/about/)istnieją dwa typy środowiska uruchomieniowego:

- **Kontenery systemu Windows Server** zapewniają izolację aplikacji za pomocą technologii izolacji procesów i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i ze wszystkimi kontenerami uruchomionymi na hoście.

- **Kontenery funkcji Hyper-V** rozwiń izolacji dostarczonych przez kontenery systemu Windows Server, uruchamiając każdy kontener w wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest współużytkowane z kontenerami funkcji Hyper-V, zapewniając lepszą izolację.

Obrazy dla tych kontenerów są tworzone i działają w ten sam sposób. Różnica polega na tym, jak kontener jest tworzony z obrazu — uruchomienie kontenera funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać szczegółowe informacje, zobacz [Kontenery funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenerów platformy Docker z maszynami wirtualnymi

Rysunek 1-3 przedstawia porównanie maszyn wirtualnych i kontenerów platformy Docker.

![Diagram przedstawiający porównanie środowisk maszyn wirtualnych i kontenerów.](./media/what-is-docker/comparison-vms-docker-conatiners.png)

**Rysunek 1-3**. Porównanie tradycyjnych maszyn wirtualnych z kontenerami platformy Docker

Jak pokazano na powyższym diagramie, dla maszyn wirtualnych istnieją trzy warstwy podstawowe na serwerze hosta. Od dołu do góry: infrastruktura, system operacyjny hosta i hypervisor. Oprócz tego każda maszyna wirtualna ma swój własny os i wszystkie niezbędne biblioteki. Z drugiej strony dla platformy Docker serwer hosta ma tylko infrastrukturę i system operacyjny. Oprócz tego aparat kontenera utrzymuje kontenery w izolacji, ale pozwala im współużytkować usługi pojedynczego podstawowego systemu operacyjnego.

Ponieważ kontenery wymagają znacznie mniej zasobów (na przykład nie potrzebują pełnego systemu operacyjnego), są łatwe do wdrożenia i uruchamiają się szybko. Pozwala to na większą gęstość, co oznacza, że pozwala na uruchamianie większej liczby usług na tej samej jednostce sprzętowej, zmniejszając w ten sposób koszty.

Jako efekt uboczny uruchamiania na tym samym jądrze, otrzymujesz mniejszą izolację niż maszyny wirtualne.

Głównym celem obrazu jest zapewnienie tego samego środowiska (zależności) w różnych wdrożeniach. Oznacza to, że można go debugować na komputerze, a następnie wdrożyć go na innym komputerze, w tym samym środowisku gwarantowane.

Obraz kontenera to sposób na spakowanie aplikacji lub usługi i wdrożenie jej w niezawodny i powtarzalny sposób. Można powiedzieć, że Docker to nie tylko technologia, ale także filozofia i proces.

Podczas korzystania z platformy Docker, nie usłyszysz deweloperzy mówią: "To działa na moim komputerze, dlaczego nie w środowisku produkcyjnym?" Mogą po prostu powiedzieć" Działa na platformie Docker", ponieważ spakowana aplikacja docker może być wykonywana w dowolnym obsługiwanym środowisku platformy Docker i działa tak, jak była przeznaczona dla wszystkich celów wdrażania (takich jak Dev, QA, staging i production).

## <a name="a-simple-analogy"></a>Prosta analogia

Być może prosta analogia może pomóc zrozumieć podstawową koncepcję Docker.

Cofniemy się na chwilę do lat 50. Nie było edytorów tekstu, a kserokopiarki były używane wszędzie (no cóż, rodzaj).

Wyobraź sobie, że jesteś odpowiedzialny za szybkie wydawanie partii listów zgodnie z wymaganiami, aby wysłać je do klientów, przy użyciu prawdziwego papieru i kopert, które mają być dostarczone fizycznie na adres każdego klienta (nie było wtedy wiadomości e-mail).

W pewnym momencie zdajesz sobie sprawę, że litery są tylko kompozycją dużego zestawu akapitów, które są zbierane i ułożone zgodnie z potrzebami, zgodnie z celem listu, więc opracujesz system szybkiego wydawania listów, spodziewając się potężnego podniesienia.

System jest prosty:

1. Zaczynasz od talii przezroczystych arkuszy zawierających po jednym akapicie.

2. Aby wydać zestaw liter, należy wybrać arkusze z akapitami, których potrzebujesz, a następnie ułożyć i wyrównać je tak, aby wyglądały i dobrze czytały.

3. Na koniec umieszczasz zestaw w kserokopiarkai i naciśnij przycisk start, aby wyprodukować tyle liter, ile jest wymagane.

Tak więc, upraszczając, to jest podstawowa idea Docker.

W platformie Docker każda warstwa jest wynikowym zestawem zmian, które zachodzą w systemie plików po wykonaniu polecenia, na przykład o zainstalowaniu programu.

Tak więc, gdy "patrzysz" na system plików po skopiowaniu warstwy, zobaczysz wszystkie pliki, w tym warstwę, gdy program został zainstalowany.

Obraz można pomyśleć jako pomocniczy dysk twardy tylko do odczytu gotowy do zainstalowania na "komputerze", na którym system operacyjny jest już zainstalowany.

Podobnie można myśleć o kontenerze jako "komputerze" z zainstalowanym dyskiem twardym obrazu. Kontener, podobnie jak komputer, może być włączony lub wyłączony.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](docker-terminology.md)
