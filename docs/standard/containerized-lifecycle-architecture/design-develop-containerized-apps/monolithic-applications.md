---
title: Aplikacje monolityczne
description: Zrozumienie podstawowych pojęć do umieszczania aplikacji monolitycznych w kontenerze.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 056f4bd8abf5c482855f38e45435b67b487769fb
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221358"
---
# <a name="monolithic-applications"></a>Aplikacje monolityczne

W tym scenariuszu są tworzenia pojedynczej i monolitycznych aplikacji sieci web lub usługi i wdrożyć go jako kontener. W aplikacji struktura może nie być monolityczne; może on zawierać kilka bibliotek, składników lub nawet warstwy (warstwa aplikacji, warstwa domeny, warstwy dostępu do danych itp.). Zewnętrznie jest jeden kontener, takich jak pojedynczego procesu, aplikacji sieci web jednej lub jednej usługi.

Aby zarządzać tym modelu, możesz wdrożyć jeden kontener, do reprezentowania aplikacji. W celu skalowania, wystarczy dodać kilka większej liczby kopii z modułem równoważenia obciążenia z przodu. Prostotę pochodzi z zarządzania pojedyncze wdrożenie w ramach jednego kontenera lub maszyny wirtualnej (VM).

Następujące jednostki kontenera jest tylko jedno i zrobi to w jednym procesie monolityczne wzorzec jest w konflikcie. Może zawierać wielu składniki i biblioteki lub wewnętrzny warstwy w ramach każdego kontenera, jak pokazano w rysunek 4-1.

![](./media/image1.png)

Rysunek 4-1. Przykładem architektury aplikacji monolitycznych

Wadą tego podejścia jest dostarczany, lub gdy aplikacja powiększa się w wymaganiem go do skalowania. W przypadku zmiany skali całej aplikacji nie jest tak naprawdę problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe, które wymagają skalowania, inne składniki są używane w mniej.

Korzystając z przykładu typowe handlu elektronicznego, prawdopodobnie potrzebne jest skalowanie składnik informacji produktu. Wielu klientów więcej Przeglądaj produktów, niż je zakupić. Większej liczby klientów użyj koszyka, niż korzystanie z potoku płatności. Dodaj komentarze lub mniejszej liczby klientów, w którym zostanie wyświetlanie ich historii zakupów. I prawdopodobnie masz tylko grupy pracowników w jednym regionie, musisz zarządzać zawartości i kampanii marketingowych. Przy użyciu skalowania monolityczny projekt, cały kod jest wdrażany wiele razy.

Oprócz "skali — wszystko, czego" problemu, zmiany pojedynczego składnika wymagają pełne ponowne przetestowanie całej aplikacji, a także pełne ponowne wdrożenie wszystkich wystąpień.

Podejścia monolitycznego jest wspólny, i tworzysz wiele organizacji przy użyciu tej metody architektury. Wiele Ciesz się dobra wystarczająco dużo wyników napotykają inne ograniczenia. Wiele zaprojektowane swoich aplikacji, w tym modelu, ponieważ infrastruktura i narzędzia było zbyt trudne do tworzenia SOAs i nie widzą potrzeby — do momentu zwiększył aplikacji.

Z perspektywy infrastruktury każdy serwer można uruchomić wiele aplikacji, w tym samym hoście i mieć zaakceptowania wskaźnik wydajności w wykorzystanie zasobów, jak pokazano w rysunek 4-2.

![](./media/image2.png)

Rysunek 4-2: Host uruchomionych wiele aplikacji/kontenerów

Aplikacje monolityczne na platformie Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Za pomocą [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), łatwe skalowanie maszyn wirtualnych. [Usługi Azure App Services](https://azure.microsoft.com/services/app-service/) uruchamiać aplikacje monolityczne i łatwo skalować wystąpień bez konieczności zarządzania maszynami wirtualnymi. Od 2016 r. usługi Azure App Services można uruchomić jednego wystąpienia kontenerów platformy Docker, jak również uproszczenia procesu wdrażania. Ponadto za pomocą platformy Docker, możesz wdrożyć jedną maszynę Wirtualną jako hosta Docker i uruchomić wiele wystąpień. Za pomocą równoważenie Azure, jak pokazano w rysunek 4-3, możesz zarządzać, skalowanie.

![](./media/image3.png)

Rysunek 4-3: Wiele hostów skalowanie w poziomie w jednej aplikacji aplikacji/kontenerów Docker

Możesz zarządzać wdrożenia na różnych hostach przy użyciu techniki wdrażania tradycyjnych. Hostów platformy Docker można zarządzać za pomocą poleceń, takich jak `docker run` ręcznie, za pomocą usługi automation, takie jak potoki ciągłe dostarczanie (CD), które firma Microsoft opisano w dalszej części tej książce elektronicznej.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolitycznych wdrożone jako kontener

Istnieją korzyści wynikające z używania kontenerów, zarządzanie wdrożeniami monolitycznego. Skalowanie wystąpienia kontenerów jest znacznie szybsze i prostsze wdrażania dodatkowych maszyn wirtualnych. Mimo że zestawy skalowania maszyn wirtualnych są doskonałe funkcji skalowania maszyn wirtualnych, które są wymagane do obsługi kontenerów Docker, ich trwać do skonfigurowania. Po wdrożeniu jako wystąpień aplikacji, konfiguracji aplikacji odbywa się w ramach maszyny wirtualnej.

Wdrażanie aktualizacji zgodnie z obrazów platformy Docker jest znacznie szybszy i wydajność sieci. Wystąpienia Vn można skonfigurować tak, na tym samym hosty jako wystąpień Vn-1, eliminując koszty dodano dodatkowe maszyny wirtualne. Obrazy platformy docker zazwyczaj rozpoczyna się w ciągu kilku sekund, skracając wdrożeniach. Zniszczenia wystąpienia platformy Docker jest równie proste jak wywoływanie `docker stop` polecenia, zwykle Kończenie pracy w ciągu niecałej sekundy.

Ponieważ kontenery są założenia niezmienne, zgodnie z projektem, nigdy nie trzeba martwić się o uszkodzony maszyn wirtualnych, ponieważ skrypt aktualizacji to, że nie można uwzględnić niektóre konkretnej konfiguracji lub plik pozostanie na dysku.

Mimo że monolitycznych aplikacji mogą korzystać z platformy Docker, firma Microsoft jest dotknięcie na tylko porady dotyczące korzyści. Większe korzyści wynikające z zarządzania kontenerów pochodzi z wdrażania przy użyciu koordynatorów kontenerów, które zarządzają różnych wystąpień i cyklu życia każdego wystąpienia kontenera. Podzielenie aplikacji monolitycznej na podsystemy, które można skalować, opracowane i wdrażane indywidualnie jest punktem wejścia do obszaru mikrousług.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publikowanie jednym aplikacji kontenera aparatu Docker w usłudze Azure App Service

Albo ponieważ w celu uzyskania szybkiego sprawdzania poprawności kontenera wdrażane na platformie Azure lub aplikacja jest po prostu kontener pojedynczej aplikacji usługi Azure App Services zapewnia doskonały sposób zapewnienia skalowalnych usług po jednym kontenerze.

Za pomocą usługi Azure App Service jest intuicyjna i można rozpocząć pracę i szybkie uruchomione, ponieważ udostępnia doskonałe narzędzia Git integracji do wykonania kodu, skompiluj go w programie Microsoft Visual Studio i bezpośrednie wdrażanie na platformie Azure. Ale, tradycyjnie (przy użyciu nie platformy Docker), jeśli to konieczne, inne możliwości, struktury lub zależności, które nie są obsługiwane w usługach App potrzebnych do poczekaj na jego zespół Azure aktualizuje te zależności w usłudze App Service lub przełączone do innych usług, takich jak Usługa Service Fabric, Cloud Services lub nawet zwykły maszyn wirtualnych, dla których masz dodatkowe kontroli i może zainstalować wymaganego składnika lub framework dla aplikacji.

Teraz, jednak (o którym poinformowano na konferencji Microsoft Connect 2016 w listopadzie 2016) i pokazany na rysunku 4‑4, korzystając z programu Visual Studio 2017, obsługa kontenerów w usłudze Azure App Service daje możliwość zawierać dowolne w danym środowisku aplikacji. Jeśli dodano zależności aplikacji, ponieważ jest on używany w kontenerze, zostanie wyświetlony możliwości tych zależności, w tym obrazie pliku Dockerfile lub rozwiązania Docker.

![](./media/image4.png)

Rysunek 4-4: Publikowanie kontenera w usłudze Azure App Service z programu Visual Studio aplikacje/kontenerów

Rysunek 4-4 pokazuje również, że przepływ publikowania wypycha obraz do rejestru kontenerów, która może być usługa Azure Container Registry (rejestru blisko wdrożenia na platformie Azure i chronione przez usługę Azure Active Directory, grupy i konta) lub dowolnego rejestru platformy Docker Podobnie jak rejestry usługi Docker Hub lub w środowisku lokalnym.

>[!div class="step-by-step"]
>[Poprzednie](common-container-design-principles.md)
>[dalej](state-and-data-in-docker-applications.md)