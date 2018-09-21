---
title: Co to jest Docker?
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Co to jest Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 1b0cae037371666f2f1cd2ccb8c509a5618e7397
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493389"
---
# <a name="what-is-docker"></a>Co to jest Docker?

[Docker](https://www.docker.com/) jest [projektu open-source](https://github.com/docker/docker) automatyzację wdrażania aplikacji jako przenośny, samowystarczalne kontenery, które można uruchomić w chmurze lub lokalnie. Docker to również [firmy](https://www.docker.com/) który promuje i rozwojem tej technologii w współpracy z chmury, Linux i Windows producentów, takie jak Microsoft.

![Kontenery platformy docker można uruchamiać wszędzie, lokalnie w centrum danych klienta, dostawca usług zewnętrznych lub w chmurze na platformie Azure.](./media/image2.png)

**Rysunek 2-2**. Docker służy do wdrażania kontenerów we wszystkich warstwach chmury hybrydowej

Kontenery obrazu platformy docker można uruchomić natywnie w systemie Linux i Windows. Jednak obrazów Windows można uruchamiać tylko na hostach Windows i obrazów systemu Linux można uruchamiać na hosty z systemem Linux i Windows hostów (do tej pory przy użyciu systemu Linux maszyny Wirtualnej funkcji Hyper-V), gdzie hosta oznacza, że serwer lub maszyny Wirtualnej.

Deweloperzy mogą używać środowisk deweloperskich w Windows, Linux lub macOS. Na komputerze deweloperskim Deweloper uruchamia hosta platformy Docker, w których są wdrażane obrazy platformy Docker, łącznie z aplikacji i jego zależności. Deweloperzy pracujący w systemie Linux lub na komputerze Mac, użyj hosta platformy Docker, który jest opartych na systemie Linux, a mogą utworzyć obrazy tylko dla kontenerów systemu Linux. (Deweloperzy pracujący na komputerze Mac można edytować kod lub uruchomić interfejs wiersza polecenia platformy Docker z systemu macOS, ale począwszy od chwili pisania tego dokumentu, kontenery są uruchamiane bezpośrednio w systemie macOS). Deweloperzy, którzy pracują nad Windows można tworzyć obrazy systemu Linux lub Windows kontenery.

Do hostowania kontenerów w środowiskach programistycznych i zapewniają narzędzia programistyczne dodatkowe, Docker jest dostarczany [Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows lub macOS. Te produkty zainstalować niezbędnych maszyny Wirtualnej (hosta platformy Docker) do hostowania kontenerów. Docker powoduje udostępnienie [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), który jest przeznaczony dla rozwoju przedsiębiorstwa i jest używana przez zespoły IT, którzy tworzą, dostarczanie i uruchamiać duże aplikacje krytyczne dla działania firmy w środowisku produkcyjnym.

Aby uruchomić [kontenery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), istnieją dwa rodzaje środowisk uruchomieniowych:

-   Kontenery systemu Windows Server zapewniają izolację aplikacji za pomocą technologii izolacji procesu i przestrzeni nazw. Kontener systemu Windows Server udostępnia jądra hosta kontenera i wszystkie kontenery uruchomione na hoście.

-   Kontenery funkcji Hyper-V rozwiń na izolacja świadczona przez kontenery systemu Windows Server, uruchamiając każdego kontenera na wysoce zoptymalizowanej maszynie wirtualnej. W tej konfiguracji jądra hosta kontenera nie jest udostępniony za pomocą kontenerów funkcji Hyper-V, zapewniając lepsze izolację.

Obrazy dla tych kontenerów są tworzone w taki sam sposób i funkcja takie same. Różnica polega na tym, w jaki sposób ten kontener jest tworzony z obrazu uruchamiania kontenera funkcji Hyper-V wymaga dodatkowego parametru. Aby uzyskać więcej informacji, zobacz [kontenery funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porównywanie kontenerów platformy Docker przy użyciu maszyn wirtualnych

Rysunek 2 – 3 przedstawiono porównanie między maszynami wirtualnymi i Docker kontenerów.

<table>
<tbody>
<tr>
<td style="width:50%"><p><strong>Maszyny wirtualne</strong></p>
<p><img src="media/image3.png" style="width:100%; vertical-align:top;" alt="For VMs, there are three base layers in the host server, from the bottom-up: infrastructure, Host Operating System and a Hypervisor and on top of all that each VM has its own OS and all necessary libraries"/></p>
<p>Maszyny wirtualne obejmują aplikację, wymaganych bibliotek lub pliki binarne i systemu operacyjnego gościa pełne. Pełne wirtualizacji wymaga większej ilości zasobów niż konteneryzacji.</p></td>
<td style="width:50%"><p><strong>Kontenery platformy docker</strong></p>
<p><img src="media/image4.png" style="width:100%; vertical-align:top;" alt="For Docker, the host server only has the infrastructure and the OS and on top of that, the container engine, that keeps container isolated but sharing the base OS services."/></p>
<p>Kontenery obejmują aplikacji i wszystkich jego zależności. Jednak ich współdzielą jądro systemu operacyjnego za pomocą innych kontenerów, uruchomione jako procesy w izolowanej przestrzeni użytkownika w systemie operacyjnym hosta. (Z wyjątkiem kontenery funkcji Hyper-V, w którym każdy kontener jest uruchomiona wewnątrz specjalną maszyną wirtualną na kontener.)</p></td>
</tr>
</tbody>
</table>

**Rysunek 2 – 3**. Porównanie tradycyjnych maszyn wirtualnych do kontenerów platformy Docker

Ponieważ kontenery wymaga znacznie mniej zasobów (na przykład, nie ma potrzeby pełnej wersji systemu operacyjnego), są one łatwe do wdrożenia i szybkiego uruchamiania. Dzięki temu można mieć zwiększenie gęstości, co oznacza, umożliwia uruchamianie większej liczby usług w tej samej jednostce sprzętu, zmniejszając w ten sposób kosztów.

Jako efekt uboczny uruchomionych na tym samym jądra uzyskasz izolacji jest mniejszy niż maszyny wirtualne.

Głównym celem obrazu jest fakt, że środowisko (zależności) takie same w różnych wdrożeniach. Oznacza to, można to debugować na maszynie i następnie wdrożyć go na inny komputer, z tym samym środowisku, gwarantowana.

Obraz kontenera jest sposobem pakietu aplikacji lub usługi oraz wdrożyć ją w sposób niezawodny i odtworzenia. Można powiedzieć, że platformy Docker jest nie tylko technologii, ale również filozofia i procesu.

Korzystając z platformy Docker, nie otrzymasz od deweloperów powiedzieć, "działa na komputerze, dlaczego w środowisku produkcyjnym?" Można po prostu mówią, "Korzystają one z platformy Docker", ponieważ spakowanej aplikacji platformy Docker można wykonywać w dowolnej obsługiwanej środowisku platformy Docker i będzie działać sposób zamierzano dla wszystkich elementów docelowych wdrożenia (deweloperskie, QA, przemieszczania, produkcyjne itp.).

## <a name="a-simple-analogy"></a>Prosty sposób analogiczny

Może być prosty sposób analogiczny może pomóc wprowadzenie opanujesz ideą usługi Docker.

Przejdź wstecz w czasie, aby 50's na chwilę. Nie było żadnych edytorów tekstów i kopiarkach były używane wszędzie, gdzie (rodzaj).

Załóżmy, że użytkownik jest odpowiedzialny szybkie wydawanie partie liter zgodnie z wymaganiami, aby wysłać do klientów przy użyciu rzeczywistego dokument i koperty, został fizycznie dostarczony do adresu każdego klienta (nie było żadnych wiadomości e-mail w tamtym).

W pewnym momencie możesz należy pamiętać, że litery są po prostu skład szerokiej gamy akapitów, które są pobierane i rozmieszczane zgodnie z potrzebami, zgodnie z celem literę, aby opracować system do wystawiania bardzo szybko litery oczekiwano można pobrać hefty Zgłoś.

System jest naprawdę proste:

1.  Rozpoczynać talii przezroczyste arkusze zawierające jeden akapitu

2.  Do wystawiania zbiór litery, Pobierz arkusze przy użyciu akapitów, należy, a następnie stosu i ustawić je, dlatego ich wygląd i Przeczytaj dokładnie i

3.  Na koniec należy zaznaczyć zestaw start fotokopiarkę, a następnie naciśnij klawisz, aby wygenerować dowolną liczbę liter zgodnie z potrzebami.

Tak upraszczając, to pomysł core, platformy docker,

Na platformie Docker każda warstwa jest Wynikowy zestaw zmian, które występują w systemie plików po wykonaniu polecenia, np. zainstalowanie programu.

Więc jeśli "przyjrzymy się" systemu plików po warstwa została skopiowana, zobaczysz wszystkie pliki uwzględnione warstwy, gdy program został zainstalowany.

Można traktować obrazu jako pomocniczego tylko do odczytu dysku twardego gotowe do zainstalowania w "computer" gdzie jest już zainstalowany system operacyjny.

Podobnie, można traktować kontenera jako "komputer" z obrazu dysk twardy zainstalowany. Kontener, podobnie jak komputer, można wyłączyć lub wyłączyć.

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](docker-terminology.md)
