---
title: Co to jest Docker?
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Co to jest docker?
ms.date: 08/31/2018
ms.openlocfilehash: a53845d3bbcf24f3eaeb98b9e08b6f35a023c30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337704"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Platforma Docker](https://www.docker.com/) jest [projektem typu open source](https://github.com/docker/docker) do automatyzacji wdrażania aplikacji jako przenośnych, samowystarczalnych kontenerów, które można uruchamiać w chmurze lub lokalnie. Docker jest również [firmą,](https://www.docker.com/) która promuje i rozwija tę technologię, współpracując z dostawcami chmury, systemu Linux i Windows, w tym microsoft.

![Diagram przedstawiający miejsca, w których można uruchomić kontenery platformy Docker.](./media/docker-defined/docker-containers-run-anywhere.png)

**Rysunek 2-2**. Platforma Docker wdraża kontenery na wszystkich warstwach chmury hybrydowej.

Kontenery platformy Docker można uruchamiać w dowolnym miejscu, lokalnie w centrum danych klienta, w zewnętrznym dostawcy usług lub w chmurze, na platformie Azure. Kontenery obrazów platformy Docker można uruchamiać natywnie w systemach Linux i Windows. Jednak obrazy systemu Windows można uruchamiać tylko na hostach systemu Windows, a obrazy systemu Linux mogą być uruchamiane na hostach systemu Linux i hostach systemu Windows (do tej pory przy użyciu maszyny Wirtualnej systemu Linux hyper-V), gdzie host oznacza serwer lub maszynę wirtualną.

Deweloperzy mogą korzystać ze środowisk programistycznych w systemach Windows, Linux lub macOS. Na komputerze deweloperskim deweloper uruchamia hosta platformy Docker, w którym są wdrażane obrazy platformy Docker, w tym aplikacji i jej zależności. Deweloperzy, którzy pracują w systemie Linux lub na macOS używać hosta Platformy Docker, który jest oparty na systemie Linux i mogą tworzyć obrazy tylko dla kontenerów systemu Linux. (Deweloperzy pracujący nad systemem macOS mogą edytować kod lub uruchamiać kod CLI platformy Docker z systemu macOS, ale od czasu pisania kontenery nie są uruchamiane bezpośrednio w systemie macOS). Deweloperzy, którzy pracują w systemie Windows, mogą tworzyć obrazy dla kontenerów systemu Linux lub Windows.

Aby hostować kontenery w środowiskach programistycznych i udostępniać dodatkowe narzędzia deweloperskie, platforma Docker wysyła [platformę Docker Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows lub systemu macOS. Te produkty instalują niezbędną maszynę wirtualną (host docker) do obsługi kontenerów. Platforma Docker udostępnia również [platformę Docker Enterprise Edition (EE),](https://www.docker.com/enterprise-edition)która jest przeznaczona do rozwoju przedsiębiorstw i jest używana przez zespoły IT, które tworzą, akcesorią i uruchamianiem dużych aplikacji o znaczeniu krytycznym dla firmy w środowisku produkcyjnym.

Aby uruchomić [kontenery systemu Windows,](/virtualization/windowscontainers/about/)istnieją dwa typy środowiska uruchomieniowego:

- Kontenery systemu Windows Server zapewniają izolację aplikacji za pomocą technologii izolacji procesów i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądro z hostem kontenera i ze wszystkimi kontenerami uruchomionymi na hoście.

- Kontenery funkcji Hyper-V rozwiń izolacji dostarczonych przez kontenery systemu Windows Server, uruchamiając każdy kontener w wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądro hosta kontenera nie jest współużytkowane z kontenerami funkcji Hyper-V, zapewniając lepszą izolację.

Obrazy dla tych kontenerów są tworzone w ten sam sposób i działają tak samo. Różnica polega na tym, jak kontener jest tworzony z obrazu z uruchomionym kontenerem funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać szczegółowe informacje, zobacz [Kontenery funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenerów platformy Docker z maszynami wirtualnymi

Rysunek 2-3 przedstawia porównanie maszyn wirtualnych i kontenerów platformy Docker.

| Maszyny wirtualne | Kontenery platformy Docker |
| -----------------| ------------------|
|![Diagram przedstawiający stos sprzętu/oprogramowania tradycyjnej maszyny Wirtualnej.](./media/docker-defined/virtual-machine-hardware-software.png)|![Diagram przedstawiający stos sprzętu/oprogramowania dla kontenerów platformy Docker.](./media/docker-defined/docker-container-hardware-software.png)|
|Maszyny wirtualne obejmują aplikację, wymagane biblioteki lub pliki binarne oraz pełny system operacyjny gościa. Pełna wirtualizacja wymaga więcej zasobów niż konteneryzacji. | Kontenery obejmują aplikację i wszystkie jej zależności. Jednak współużytkują jądro systemu operacyjnego z innymi kontenerami, działa jako pojedyncze procesy w przestrzeni użytkownika w systemie operacyjnym hosta. (Z wyjątkiem kontenerów funkcji Hyper-V, gdzie każdy kontener jest uruchamiany wewnątrz specjalnej maszyny wirtualnej na kontener). |

**Rysunek 2-3**. Porównanie tradycyjnych maszyn wirtualnych z kontenerami platformy Docker

W przypadku maszyn wirtualnych istnieją trzy warstwy podstawowe na serwerze hosta, od dołu do góry: infrastruktura, system operacyjny hosta i hypervisor, a na dodatek każda maszyna wirtualna ma własny system operacyjny i wszystkie niezbędne biblioteki. Dla platformy Docker serwer hosta ma tylko infrastrukturę i system operacyjny, a na dodatek aparat kontenera, który utrzymuje kontenera izolowane, ale udostępnianie podstawowych usług systemu operacyjnego.

Ponieważ kontenery wymagają znacznie mniej zasobów (na przykład nie potrzebują pełnego systemu operacyjnego), są łatwe do wdrożenia i uruchamiają się szybko. Pozwala to na większą gęstość, co oznacza, że pozwala na uruchamianie większej liczby usług na tej samej jednostce sprzętowej, zmniejszając w ten sposób koszty.

Jako efekt uboczny uruchamiania na tym samym jądrze, otrzymujesz mniejszą izolację niż maszyny wirtualne.

Głównym celem obrazu jest, że sprawia, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, że można go debugować na komputerze, a następnie wdrożyć go na innym komputerze z tego samego środowiska gwarantowane.

Obraz kontenera to sposób na spakowanie aplikacji lub usługi i wdrożenie jej w niezawodny i powtarzalny sposób. Można powiedzieć, że Docker to nie tylko technologia, ale także filozofia i proces.

Podczas korzystania z platformy Docker, nie usłyszysz deweloperzy mówią: "To działa na moim komputerze, dlaczego nie w środowisku produkcyjnym?" Mogą po prostu powiedzieć" Działa na platformie Docker", ponieważ spakowana aplikacja platformy Docker może być wykonywana w dowolnym obsługiwanym środowisku platformy Docker i działa tak, jak była przeznaczona dla wszystkich celów wdrażania (takich jak Dev, QA, staging i production).

## <a name="a-simple-analogy"></a>Prosta analogia

Być może prosta analogia może pomóc zrozumieć podstawową koncepcję Docker.

Cofniemy się na chwilę do lat 50. Nie było edytorów tekstu, a kserokopiarki były używane wszędzie (rodzaj).

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
