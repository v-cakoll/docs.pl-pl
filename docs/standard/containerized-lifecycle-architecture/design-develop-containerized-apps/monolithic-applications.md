---
title: Wbudowanymi aplikacji
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: fe25fa8772c60625c5564d5e7194957366a6010a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="monolithic-applications"></a>Wbudowanymi aplikacji

W tym scenariuszu są Tworzenie pojedynczych i wbudowanymi sieci web aplikacji lub usługi i wdrażanie go jako kontener. W aplikacji struktura nie może być wbudowanymi; może on zawierać kilka bibliotek, składniki lub nawet warstwy (warstwy aplikacji, warstwy domeny, Warstwa dostępu do danych itp.). Zewnętrznie jest jeden kontener, takimi jak jednego procesu, aplikacji sieci web jednej lub pojedynczą usługę.

Aby zarządzać tego modelu, możesz wdrożyć jeden kontener do reprezentowania aplikacji. Można go skalować, wystarczy dodać kilka większej liczby kopii usługi równoważenia obciążenia z przodu. Łatwość pochodzi z zarządzania pojedynczego wdrożenia w jeden kontener lub maszyny wirtualnej (VM).

Następujące podmiot zabezpieczeń kontener jest tylko jeden element czy jest ona w jednym procesie wbudowanymi wzorzec jest w konflikcie. Zgodnie z opisami w rysunek 4-1 może zawierać wiele składników/biblioteki lub wewnętrzny warstw w ramach każdego kontenera.

![](./media/image1.png)

Rysunek 4-1: przykład wbudowanymi aplikacja — architektura

Wadą tego podejścia interfejsu pochodzi, lub w przypadku rozwoju aplikacji wymaganiem go do skalowania. W przypadku zmiany skali całej aplikacji nie jest naprawdę problem. Jednak w większości przypadków kilka części aplikacji są punkty urządzenie rozruchowe, które wymagają skalowania, inne składniki są używane mniej.

W przykładzie typowe handlu elektronicznego, co prawdopodobnie należy jest skalowania składnika informacji produktu. Wielu klientów więcej Przeglądanie produktów, niż ich zakupu. Więcej klientów użyj koszyka niż używanie potoku płatności. Mniejszą liczbę klientów Dodawanie komentarzy i wyświetlanie ich historii zakupów. I może mieć tylko grupy pracowników w pojedynczym regionie, które są potrzebne do zarządzania zawartością i kampanii marketingowych. Skalując wbudowanymi projektowania cały kod jest wdrażany wiele razy.

Dodatkowo "skali — wszystko" problemu, zmiany pojedynczego składnika wymagają pełne ponowne całej aplikacji, a także ukończenie ponownego rozmieszczenia wszystkich wystąpień.

W wielu organizacjach opracowujesz przy użyciu tej metody architektury i wbudowanymi podejście jest. Wiele dobre kredyty za mało wyników, napotykają inne ograniczenia. Wiele zaprojektowane swoich aplikacji, w tym modelu, ponieważ infrastruktura i narzędzia było zbyt trudne do tworzenia SOAs i nie widzą na potrzeby — do momentu zwiększył aplikacji.

Z perspektywy infrastruktury każdego serwera można uruchomić wiele aplikacji w obrębie tego samego hosta i mieć zaakceptowania wskaźnik wydajności w użycie zasobów, jak pokazano na rysunku 4-2.

![](./media/image2.png)

Rysunek 4-2: hosta z systemem wiele aplikacji/kontenerów

Wbudowanymi aplikacji na platformie Azure można wdrożyć przy użyciu dedykowanych maszyn wirtualnych dla poszczególnych wystąpień. Przy użyciu [zestawy skalowania maszyny Wirtualnej Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), można łatwo skalować maszyn wirtualnych. [Usługa Azure App Service](https://azure.microsoft.com/en-us/services/app-service/) można uruchamiać aplikacje wbudowanymi i łatwego skalowania wystąpienia bez konieczności zarządzania maszynami wirtualnymi. Od 2016 usługi aplikacji Azure można uruchomić pojedynczego wystąpienia Docker kontenerów, jak również uprościć wdrażanie. I przy użyciu rozwiązania Docker, można wdrożyć jeden maszynę Wirtualną jako hosta Docker i uruchomić wiele wystąpień. Przy użyciu równoważenia Azure, jak pokazano na rysunku 4-3, można zarządzać skalowania.

![](./media/image3.png)

Rysunek 4-3: wiele hostów skalowania w poziomie pojedynczego Docker aplikacji/kontenerów aplikacji

Można zarządzać wdrażaniem na różnych hostach za pomocą techniki tradycyjnego wdrażania. Hostach Docker można zarządzać za pomocą poleceń, takich jak `docker run` ręcznie, za pomocą automatyzacji, takie jak potoki ciągłego dostarczania (CD), które firma Microsoft wyjaśniono dalej w tej sekcji e.

## <a name="monolithic-application-deployed-as-a-container"></a>Wbudowanymi aplikacji wdrożonych jako kontener

Istnieją korzyści wynikające z używania kontenery Zarządzanie wbudowanymi wdrożeniami. Skalowanie wystąpienia kontenery jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych. Mimo że zestawy skalowania maszyny Wirtualnej to doskonały funkcji skalowania maszyn wirtualnych, które są wymagane do obsługi kontenerów Docker, ich trwać do skonfigurowania. Po wdrożeniu jako wystąpienia aplikacji Konfiguracja aplikacji jest zarządzana w ramach maszyny wirtualnej.

Wdrażanie aktualizacji, jak obrazy usługi Docker jest znacznie szybsze i wydajność sieci. Wystąpienia Vn można skonfigurować na tej samej hostach jako swoich wystąpień Vn-1 eliminowanie dodany kosztów wynikających z dodatkowych maszyn wirtualnych. Obrazy usługi docker zazwyczaj rozpoczyna się w sekundach, przyspieszania wdrożeniach. Przerwanie w dół wystąpienia Docker jest równie proste jak wywoływanie `docker stop` polecenia zwykle kończonych w mniej niż 1 sekunda.

Ponieważ kontenery są z założenia niezmienne, zgodnie z projektem, nigdy nie trzeba martwić uszkodzony maszyn wirtualnych, ponieważ skrypt aktualizacji nie pamiętasz dla niektórych określonej konfiguracji lub pliku pozostałego miejsca na dysku.

Mimo że wbudowanymi aplikacje mogą korzystać z Docker, firma Microsoft jest dotknięcie na tylko porady korzyści. Większe korzyści wynikające z zarządzania kontenery pochodzi z wdrażania z orchestrators kontenera, zarządzających różnych wystąpień i cyklu życia każde wystąpienie kontenera. Podzielenie wbudowanymi aplikacji na podsystemy, które można skalować, opracowany i wdrażane pojedynczo jest punkt wejścia do obszaru mikrousług.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publikowanie tylko jednej aplikacji kontenera Docker w usłudze Azure App Service

Ponieważ w celu uzyskania szybkiego sprawdzania poprawności kontenera wdrożeniu na platformie Azure lub aplikacja jest po prostu kontenera pojedynczej aplikacji, usługi aplikacji Azure albo zawiera doskonałym sposobem zapewnienia skalowalnych usług jeden kontener.

Przy użyciu usługi Azure App Service jest intuicyjne i można uzyskać w i szybko uruchomić, ponieważ zapewnia dużą Git integracji do wykonania kodu, skompiluj go w programie Microsoft Visual Studio i bezpośrednie wdrażanie na platformie Azure. Ale, tradycyjnie (nie z rozwiązaniem Docker z), w razie potrzeby innych możliwości, struktury lub zależności, które nie są obsługiwane w usługach aplikacji, konieczne jest poczekaj na jej przez zespół Azure aktualizacji tych zależności w usłudze App Service lub przełączone do innych usług, takich jak Sieć szkieletowa usług, usługi w chmurze lub nawet zwykły maszyn wirtualnych, dla których mają dodatkowe kontrolę i można zainstalować wymaganego składnika lub struktury aplikacji.

Teraz, jednak (ogłaszane w Microsoft Connect 2016 w listopada 2016) oraz jak pokazano na 4‑4 rysunku, korzystając z programu Visual Studio 2017, obsługa kontenerów w usłudze Azure App Service udostępnia możliwość zawierać dowolne w danym środowisku aplikacji. Jeśli dodano zależności do aplikacji, ponieważ jest on używany w kontenerze, możesz uzyskać możliwość włączenia tych zależności w obrazie plik Dockerfile lub Docker.

![](./media/image4.png)

Rysunek 4 — 4: publikowanie kontener usłudze Azure App Service z programu Visual Studio aplikacje/kontenerów.

Rysunek 4-4 przedstawiono również, że przepływ publikowania wypchnięcia obrazu za pomocą rejestru kontenera, który może być rejestru kontenera platformy Azure (rejestru w pobliżu do wdrożeń na platformie Azure i zabezpieczane przez usługi Azure Active Directory grup i kont) lub innych rejestru Docker Podobnie jak Centrum Docker lub lokalnie rejestry organizacji.


>[!div class="step-by-step"]
[Poprzednie] (typowe kontenera projekt principles.md) [dalej] (state-and-data-in-docker-applications.md)
