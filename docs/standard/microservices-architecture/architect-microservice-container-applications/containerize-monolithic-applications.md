---
title: Konteneryzowania aplikacji monolitycznych
description: Umieszczania aplikacji monolitycznych w kontenerze, ale nie od razu korzystać z architektury mikrousług, ma wdrożenia ważne korzyści, które mogą być natychmiast dostarczane.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: d1de4c4beb8c60aa543e5c71243d93b83fe52072
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130910"
---
# <a name="containerizing-monolithic-applications"></a>Konteneryzowania aplikacji monolitycznych

Możesz chcieć utworzyć pojedynczą, monolithically wdrożonej w sieci web aplikacji lub usługi i wdrożyć go jako kontener. Sama aplikacja nie może być wewnętrznie monolityczne, ale mają strukturę jako kilka bibliotek, składników lub nawet warstwy (warstwa aplikacji, warstwa domeny, Warstwa dostępu do danych itp.). Zewnętrznie, jest jednak jeden kontener — jeden proces, aplikacji sieci web jednej lub jednej usługi.

Aby zarządzać tym modelu, możesz wdrożyć jeden kontener, do reprezentowania aplikacji. Aby zwiększyć pojemność, możesz skalować w poziomie, oznacza to, wystarczy dodać większej liczby kopii z modułem równoważenia obciążenia z przodu. Prostotę pochodzi z zarządzania pojedyncze wdrożenie w ramach jednego kontenera lub maszyny Wirtualnej.

![Konteneryzowanych aplikacji monolitycznej ma większości jej funkcji w obrębie jednego kontenera, za pomocą wewnętrznego warstwy lub bibliotek, i można skalować w poziomie przez Sklonowanie kontener na wielu serwerach lub maszynach wirtualnych](./media/image1.png)

**Rysunek 4-1**. Przykład architektura konteneryzowanych aplikacji monolitycznej

Wiele składników, bibliotek lub wewnętrzny warstwy może zawierać w każdego kontenera zgodnie z opisami w rysunek 4-1. Jednak ten wzorzec monolityczne może powodować konflikt z zasadą kontenera "kontener jest jedną z rzeczy i zrobi to w jednym procesie", ale może być ok w niektórych przypadkach.

Wadą tego podejścia staje się oczywiste, gdy aplikacja powiększa się w wymaganiem go do skalowania. Jeśli można skalować w całej aplikacji, tak naprawdę nie problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe, że wymagających skalowania, podczas gdy inne składniki są używane mniejsze.

Na przykład w aplikacji typowe handlu elektronicznego, prawdopodobnie musisz skalować podsystemu informacji produktu, ponieważ wiele większej liczby klientów, przeglądanie produktów niż je zakupić. Większej liczby klientów użyj koszyka, niż korzystanie z potoku płatności. Dodaj komentarze lub mniejszej liczby klientów, w którym zostanie wyświetlanie ich historii zakupów. I może mieć tylko niewielki podzbiór pracowników, którzy muszą zarządzać zawartość i kampanii marketingowych. Skala monolityczny projekt cały kod dla tych różnych zadań jest wdrożona wiele razy i skalowane w tej samej klasy korporacyjnej.

Istnieje wiele sposobów skalowania duplikatów aplikacji w poziomie, dzielenie różnych obszarów aplikacji i partycjonowania podobne koncepcji biznesowych lub danych. Jednak oprócz problem skalowania wszystkie składniki zmiany pojedynczego składnika wymagają pełne ponowne przetestowanie całej aplikacji i pełne ponowne wdrożenie wszystkich wystąpień.

Podejścia monolitycznego jest jednak typowy, ponieważ rozwoju aplikacji jest początkowo łatwiejsze niż w przypadku metod mikrousług. W związku z tym w wielu organizacjach programować przy użyciu tego podejścia architektury. Chociaż w niektórych organizacjach mieli dobra wystarczająco dużo wyników innych osiągnięcia limitów. W wielu organizacjach zaprojektowane swoich aplikacji przy użyciu tego modelu, ponieważ infrastruktura i narzędzia wprowadzone zbyt trudne do tworzenia architektury zorientowanej na usługi (SOA) lat temu, a nie została uwzględniona potrzeby — do momentu zwiększył aplikacji.

Z perspektywy infrastruktury każdy serwer można uruchomić wiele aplikacji, w tym samym hoście i mieć zaakceptowania wskaźnik wydajności użycia zasobów, jak pokazano w rysunek 4-2.

![Kilka aplikacji monolitycznej, każdy z nich w kontenerze oddzielnym, można uruchomić hosta.](./media/image2.png)

**Rysunek 4-2**. Podejścia monolitycznego: Na hoście uruchomiono wiele aplikacji, każda aplikacja uruchomionego jako kontener

Aplikacje monolityczne na platformie Microsoft Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Ponadto za pomocą [zestawów skalowania maszyn wirtualnych platformy Azure](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/), można łatwo skalować maszyny wirtualne. [Usługa Azure App Service](https://azure.microsoft.com/services/app-service/) można również uruchamiać aplikacje monolityczne i łatwe skalowanie wystąpień bez konieczności zarządzania maszynami wirtualnymi. Od 2016 r. usługi Azure App Services można uruchomić jednego wystąpienia kontenerów platformy Docker, jak również uproszczenia procesu wdrażania.

Jako środowisko pytań i odpowiedzi lub ograniczonym środowisku produkcyjnym możesz wdrożyć hosta platformy Docker wielu maszyn wirtualnych i zrównoważenia je przy użyciu równoważenia platformy Azure, jak pokazano w rysunek 4-3. Pozwoli to zarządzać skalowania dzięki podejściu zgrubnym ziarna, ponieważ cała aplikacja znajduje się w jednym kontenerze.

![Kilka hostów, każdy z nich uruchamiania kontenera za pomocą aplikacji monolitycznej.](./media/image3.png)

**Rysunek 4-3**. Przykład wielu hostach, skalowanie w górę aplikacji jeden kontener

Wdrożenia na różnych hostach można zarządzać za pomocą techniki wdrażania tradycyjnych. Hostów platformy docker można zarządzać za pomocą poleceń, takich jak `docker run` lub `docker-compose` wykonać ręcznie lub za pomocą automatyzacji, takie jak potoki ciągłe dostarczanie (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Wdrażanie aplikacji monolitycznej jako kontener

Istnieją korzyści, aby zarządzać wdrożeniami aplikacji monolitycznej przy użyciu kontenerów. Skalowanie wystąpienia kontenera jest znacznie szybsze i prostsze wdrażania dodatkowych maszyn wirtualnych. Nawet w przypadku używania zestawów skalowania maszyn wirtualnych, maszyny wirtualnej może potrwać godzinę, aby rozpocząć. Po wdrożeniu jako wystąpienia tradycyjnych aplikacji zamiast kontenerów, konfigurację aplikacji odbywa się w ramach maszyny wirtualnej nie jest najlepszym rozwiązaniem.

Wdrażanie aktualizacji zgodnie z obrazów platformy Docker jest znacznie szybszy i wydajność sieci. Obrazy platformy docker zazwyczaj rozpoczyna się w ciągu kilku sekund, co przyspiesza wprowadzanie. Zniszczenia wystąpienia obrazu platformy Docker jest równie proste jak wystawianie `docker stop` poleceń i zazwyczaj kończy się w ciągu niecałej sekundy.

Ponieważ kontenery są niezmienne zgodnie z projektem, nigdy nie musisz się martwić o maszynach wirtualnych w uszkodzona. Z kolei skryptów aktualizacji dla maszyny Wirtualnej może być zapomnij konto niektóre konkretnej konfiguracji lub plik pozostanie na dysku.

Gdy monolitycznych aplikacji mogą korzystać z platformy Docker, firma Microsoft jest dotknięcie tylko na korzyści. Dodatkowe zalety zarządzania kontenerami pochodzą z wdrażania przy użyciu koordynatorów kontenerów, które zarządzają różnych wystąpień i cyklu życia każdego wystąpienia kontenera. Podzielenie aplikacji monolitycznej na podsystemy, które można skalować, opracowane i wdrażane indywidualnie jest punktem wejścia do obszaru mikrousług.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikowanie aplikacji opartych na kontenerach pojedynczej usłudze Azure App Service

Czy chcesz pobrać weryfikacji kontenera wdrażane na platformie Azure lub gdy aplikacja jest po prostu aplikacji jednego kontenera usługi Azure App Service zapewnia dobry sposób na dostarczenie skalowalnych usług opartych na kontenerach pojedynczej. Za pomocą usługi Azure App Service jest proste. Zapewnia ona doskonałą integrację za pomocą narzędzia Git, aby ułatwić zająć kodu, skompiluj go w programie Visual Studio i wdróż je bezpośrednio na platformie Azure.

![Kreator publikowania aplikacji jeden kontener w usłudze Azure App Service w programie Visual Studio](./media/image4.png)

**Rysunek 4-4**. Publikowanie aplikacji pojedynczego kontenera w usłudze Azure App Service z programu Visual Studio

Bez platformy Docker Jeśli to konieczne, inne możliwości, struktury lub zależności, które nie są obsługiwane w usłudze Azure App Service, trzeba było poczekaj, aż zespół platformy Azure, zaktualizować tych zależności w usłudze App Service. Czy przełączyć się do innych usług, takich jak Azure Service Fabric, Azure Cloud Services lub nawet maszyn wirtualnych, gdzie trzeba było dalsze kontroli i może zainstalować wymaganego składnika lub framework dla aplikacji.

Obsługa kontenerów w programie Visual Studio 2017 zapewnia możliwość zawierać dowolne w danym środowisku aplikacji, jak pokazano na rysunku 4-4. Ponieważ używasz go w kontenerze, jeśli Dodawanie zależności do aplikacji, może zawierać zależności w pliku Dockerfile lub rozwiązania Docker obrazie.

Również przedstawione w rysunek 4-4 przepływ publikowania wypycha obraz do rejestru kontenerów. Może to być usługa Azure Container Registry (rejestr najbliżej Twoich wdrożeń na platformie Azure i chronione przez usługę Azure Active Directory, grupy i konta) oraz wszelkich innych rejestru platformy Docker, takich jak usługi Docker Hub lub rejestru w środowisku lokalnym.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](docker-application-state-data.md)