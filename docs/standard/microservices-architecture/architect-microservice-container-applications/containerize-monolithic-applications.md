---
title: Containerizing wbudowanymi aplikacji
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Containerizing wbudowanymi aplikacji"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 11e2c24403b9b61584e424696c844e00e5d34b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="containerizing-monolithic-applications"></a>Containerizing wbudowanymi aplikacji

Można utworzyć pojedynczą, monolithically wdrożonego w sieci web aplikacji lub usługi i wdróż je jako kontener. Sama aplikacja może nie być wewnętrznie wbudowanymi, ale strukturę jako kilka bibliotek, składniki lub nawet warstwy (warstwy aplikacji, warstwy domeny, Warstwa dostępu do danych itp.). Zewnętrznie, jest jednak jeden kontener — jeden proces, aplikacji sieci web jednej lub pojedynczą usługę.

Aby zarządzać tego modelu, możesz wdrożyć jeden kontener do reprezentowania aplikacji. Aby skalować, po prostu Dodaj więcej kopii usługi równoważenia obciążenia z przodu. Łatwość pochodzi z zarządzania pojedynczego wdrożenia w jeden kontener lub maszyny Wirtualnej.

![](./media/image1.png)

**Rysunek 4-1**. Przykład architektury konteneryzowanych aplikacji wbudowanymi

Wiele składników, bibliotek lub wewnętrzny warstwy można uwzględnić w poszczególnych kontenerach zgodnie z opisami w rysunek 4-1. Jednak ten wzorzec wbudowanymi może powodować konflikt z zasadą kontenera "kontener nie rzecz i jest w jednym procesie", ale może być ok w niektórych przypadkach.

Wadą interfejsu tego podejścia staje się oczywiste, gdy rozwoju aplikacji wymaganiem go do skalowania. Jeśli całej aplikacji można skalować, nie jest naprawdę problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe, że wymagające skalowania, podczas gdy inne składniki są używane mniejsze.

Na przykład w aplikacji typowe handlu elektronicznego, prawdopodobnie musisz skalować podsystemu informacji produktu, ponieważ dużo więcej klientów Przeglądanie produktów, niż ich zakupu. Więcej klientów użyj koszyka niż używanie potoku płatności. Mniejszą liczbę klientów Dodawanie komentarzy i wyświetlanie ich historii zakupów. I może mieć tylko grupy pracowników, które muszą zarządzać zawartość i kampanii marketingowych. Skala wbudowanymi projektu cały kod dla tych różnych zadań jest wdrożonych wiele razy i skalowania w tej samej kategorii.

Istnieje wiele sposobów, aby skalować aplikację — poziome duplikatów, dzielenie różne obszary aplikacji i partycjonowania podobne koncepcje biznesowe lub danych. Jednak oprócz problem skalowania wszystkie składniki zmiany pojedynczego składnika wymagają pełne ponowne całej aplikacji i pełne ponowne wdrożenie wszystkich wystąpień.

Wbudowanymi podejście jest jednak wspólne, ponieważ programowanie aplikacji jest początkowo łatwiejsze niż podejścia mikrousług. W związku z tym organizacje za pomocą tej metody architektury. Gdy niektóre organizacje dobre miały wystarczająco dużo wyników, inne czy osiągnięto limity. W wielu organizacjach zaprojektowane ich aplikacji przy użyciu tego modelu, ponieważ infrastruktura i narzędzia możliwe zbyt trudne do usługi kompilacji na architektury (SOA) lat temu, a nie została uwzględniona potrzeby — do momentu zwiększył aplikacji.

Z perspektywy infrastruktury każdego serwera można uruchomić wiele aplikacji w obrębie tego samego hosta i mieć zaakceptowania wskaźnik wydajności użycia zasobów, jak pokazano na rysunku 4-2.

![](./media/image2.png)

**Rysunek 4-2**. Podejście wbudowanymi: Host uruchamianie wielu aplikacji każdej aplikacji uruchomionej jako kontener

Wbudowanymi aplikacji na platformie Microsoft Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Ponadto przy użyciu [zestawy skalowania maszyny Wirtualnej Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyn wirtualnych. [Usługa aplikacji Azure](https://azure.microsoft.com/services/app-service/) można również uruchomić wbudowanymi aplikacjami i łatwego skalowania wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Ponieważ 2016 usługi aplikacji Azure można uruchomić pojedynczych wystąpień również kontenery Docker celu uproszczenia wdrażania.

Jako środowisko pytań i odpowiedzi lub ograniczonym środowisku produkcyjnym można wdrożyć wiele Docker hosta maszyn wirtualnych i zrównoważenia je za pomocą równoważenia Azure, jak pokazano na rysunku 4-3. Dzięki temu możesz zarządzać skalowanie przy użyciu podejścia grubą ziarna ponieważ całej aplikacji znajduje się w jeden kontener.

![](./media/image3.png)

**Rysunek 4-3**. Przykład wielu hostach skalowaniu aplikacji jeden kontener

Wdrożenia na różnych hostach można zarządzać za pomocą techniki tradycyjnego wdrażania. Hostach docker można zarządzać za pomocą poleceń, takich jak `docker run` lub `docker-compose` wykonać ręcznie lub za pomocą automatyzacji, takie jak potoki ciągłego dostarczania (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Wdrażanie aplikacji wbudowanymi jako kontener

Istnieją korzyści wynikające z używania kontenery Zarządzanie wdrożeniami wbudowanymi aplikacji. Skalowanie wystąpień kontenera jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Nawet wtedy, gdy używasz zestawy skalowania maszyny Wirtualnej, maszyn wirtualnych trwać, aby rozpocząć. Po wdrożeniu jako wystąpień tradycyjnych aplikacji zamiast kontenery konfiguracji aplikacji jest zarządzana w ramach maszyny wirtualnej, która nie jest idealnym rozwiązaniem.

Wdrażanie aktualizacji, jak obrazy usługi Docker jest znacznie szybsze i wydajność sieci. Obrazy usługi docker zazwyczaj rozpoczyna się w sekundach, co przyspiesza wdrożeniach. Przerwanie w dół wystąpienia obrazu Docker jest tak proste, jak wystawianie `docker stop` poleceń i zwykle jest przeprowadzany w mniej niż 1 sekunda.

Ponieważ kontenery są niezmienne zgodnie z projektem, nigdy nie trzeba martwić uszkodzony maszyn wirtualnych. Z kolei skryptów aktualizacji dla maszyny Wirtualnej może zapomnij konta dla niektórych określonej konfiguracji lub pliku pozostałego miejsca na dysku.

Gdy wbudowanymi aplikacje mogą korzystać z Docker, możemy są dotknięcie tylko na korzyści. Dodatkowe korzyści związanych z zarządzaniem kontenery pochodzą z wdrażania z orchestrators kontenera, które zarządzają różnych wystąpień i cyklem życia każde wystąpienie kontenera. Podzielenie wbudowanymi aplikacji na podsystemy, które można skalować, opracowany i wdrażane pojedynczo jest punkt wejścia do obszaru mikrousług.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikowanie aplikacji jeden kontener opartych na usłudze Azure App Service

Czy chcesz pobrać weryfikacji kontenera wdrożeniu na platformie Azure lub gdy aplikacja jest po prostu aplikacji kontenera pojedynczej usługi Azure App Service zapewnia to dobry sposób na Podaj skalowalnych usług na podstawie kontenera jednym. Za pomocą usługi Azure App Service jest proste. Zapewnia dużą integracji z usługą Git, aby ułatwić otrzymuje kodu, skompiluj go w programie Visual Studio i wdrażanie go bezpośrednio na platformie Azure.

![](./media/image4.png)

**Rysunek 4-4**. Publikowanie aplikacji jeden kontener w usłudze Azure App Service w programie Visual Studio

Bez Docker w razie potrzeby innych możliwości, struktury lub zależności, które nie są obsługiwane w usłudze Azure App Service, trzeba było poczekaj, aż zespół Azure zaktualizować te zależności w usłudze App Service. Czy przełączyć się do innych usług, takich jak sieć szkieletowa usług Azure, usługi w chmurze Azure lub nawet maszyn wirtualnych, których dalsze były kontroli i może zainstalować wymaganego składnika lub struktury aplikacji.

Obsługa kontenerów w Visual Studio 2017 daje możliwość zawierać dowolne w danym środowisku aplikacji, jak pokazano na rysunku 4-4. Ponieważ jest on używany w kontenerze, jeśli Dodaj zależności do aplikacji, można dołączyć zależności obrazu plik Dockerfile lub Docker.

Jak również pokazano rysunek 4 — 4 przepływ publikowania wypycha obrazu za pomocą rejestru kontenera. Może to być Azure kontenera rejestru (rejestr Zamknij, aby wdrażanie na platformie Azure i zabezpieczonej przez usługi Azure Active Directory grupy i konta) lub wszelkie inne rejestru Docker, takich jak Centrum Docker lub rejestru lokalnych.


>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (docker aplikacji — stan data.md)
