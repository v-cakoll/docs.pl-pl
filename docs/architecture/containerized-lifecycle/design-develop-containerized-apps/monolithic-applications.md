---
title: Aplikacje monolityczne
description: Zapoznaj się z podstawowymi pojęciami dotyczącymi aplikacji konteneryzowania monolitycznych.
ms.date: 02/15/2019
ms.openlocfilehash: a67015452fb1245ef4b24a8dc50a4b33d3f9f32e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295711"
---
# <a name="monolithic-applications"></a>Aplikacje monolityczne

W tym scenariuszu tworzysz jedną i monolityczną aplikację sieci Web lub usługę i wdrażasz ją jako kontener. W aplikacji struktura może nie być lity; może składać się z kilku bibliotek, składników, a nawet warstw (warstwy aplikacji, warstwy domeny, warstwy dostępu do danych itp.). Zewnętrznie jest to jeden kontener, taki jak pojedynczy proces, pojedyncza aplikacja internetowa lub jedna usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby ją skalować, wystarczy dodać kilka więcej kopii z modułem równoważenia obciążenia. Prostota pochodzi z zarządzania pojedynczym wdrożeniem w jednym kontenerze lub maszynie wirtualnej.

Zgodnie z podmiotem zabezpieczeń, który kontener wykonuje tylko jeden element i robi w jednym procesie, wzorzec monolityczny jest w konflikcie. W każdym kontenerze można uwzględnić wiele składników/bibliotek lub warstwy wewnętrzne, jak pokazano na rysunku 4-1.

![Aplikacja monolityczna ma wszystkie lub większość funkcji w ramach jednego procesu lub kontenera i jest częścią wewnętrznych warstw lub bibliotek.](./media/image1.png)

**Rysunek 4-1.** Przykładowa architektura aplikacji monolitycznych

Minusem do tego podejścia ma miejsce, gdy aplikacja zostanie powiększona, co wymaga jego skalowania. Jeśli cała aplikacja jest skalowana, problem nie występuje. Jednak w większości przypadków kilka części aplikacji to punkty podlewki, które wymagają skalowania, a inne składniki są używane mniej.

Korzystając z typowego przykładu handlu elektronicznego, prawdopodobnie trzeba będzie skalować składnik informacji o produkcie. Wielu więcej klientów przegląda produkty od ich zakupu. Więcej klientów korzysta z koszyka niż w przypadku korzystania z potoku płatności. Mniejsza liczba klientów umożliwia dodanie komentarzy lub wyświetlenie ich historii zakupów. W jednym regionie może być kilku tylko pracownicy, którzy muszą zarządzać zawartością i kampaniami marketingowymi. Poprzez skalowanie projektu monolitycznego cały kod jest wdrażany wiele razy.

Oprócz problemu "Skaluj do wszystkiego" zmiany w pojedynczym składniku wymagają pełnego przetestowania całej aplikacji oraz całkowitego ponownego wdrożenia wszystkich wystąpień.

Podejście monolityczne jest wspólne i wiele organizacji opracowuje przy użyciu tej metody architektonicznej. Wiele osób ma wystarczającą ilość wyników, a inne napotykają limity. Wiele zaprojektowanych aplikacji w tym modelu, ponieważ narzędzia i infrastruktura były zbyt trudne do kompilowania SOAs i nie widzą potrzeb — do momentu, aż aplikacja zwiększyła się.

Z punktu widzenia infrastruktury każdy serwer może uruchamiać wiele aplikacji na tym samym hoście i mieć akceptowalny współczynnik wydajności w użyciu zasobów, jak pokazano na rysunku 4-2.

![Pojedynczy host może uruchamiać wiele aplikacji w oddzielnych kontenerach.](./media/image2.png)

**Rysunek 4-2.** Host z wieloma aplikacjami/kontenerami

Na koniec z perspektywy dostępności aplikacje monolityczne muszą być wdrażane jako całość; oznacza to, że w przypadku konieczności *zatrzymania i uruchomienia*programu wszystkie funkcje i wszyscy użytkownicy będą mieć na to zastosowanie w oknie wdrożenia. W niektórych sytuacjach korzystanie z platformy Azure i kontenerów może zminimalizować te sytuacje i zmniejszyć prawdopodobieństwo przestoju aplikacji, jak widać na rysunku 4-3.

Aplikacje monolityczne można wdrażać na platformie Azure przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Za pomocą [usługi Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)można łatwo skalować maszyny wirtualne.

Za pomocą [usługi Azure App Services](https://azure.microsoft.com/services/app-service/) można także uruchamiać aplikacje monolityczne i łatwo skalować wystąpienia bez potrzeby zarządzania maszynami wirtualnymi. Na platformie Azure App Services można uruchamiać pojedyncze wystąpienia kontenerów platformy Docker, a także uprościć wdrażanie.

Możesz wdrożyć wiele maszyn wirtualnych jako hosty platformy Docker i uruchomić dowolną liczbę kontenerów na maszynę wirtualną. Następnie przy użyciu Azure Load Balancer, jak pokazano na rysunku 4-3, można zarządzać skalowaniem.

![Aplikacja monolityczna może być skalowana w poziomie na różnych hostach, na których każda z nich uruchamia aplikację w kontenerach.](./media/image3.png)

**Rysunek 4-3**. Skalowanie wielu hostów — pojedyncze aplikacje/kontenery aplikacji platformy Docker

Wdrożeniem hostów można zarządzać za pomocą tradycyjnych technik wdrażania.

Kontenerów platformy Docker można zarządzać z poziomu wiersza polecenia, korzystając z `docker run` poleceń `docker-compose up`takich jak i, a także zautomatyzować je w potokach ciągłego dostarczania (CD) i wdrażać na hostach platformy Docker z Azure DevOps Services, na przykład.

## <a name="monolithic-application-deployed-as-a-container"></a>Aplikacja monolityczna wdrożona jako kontener

Istnieją zalety korzystania z kontenerów do zarządzania wdrożeniami monolitycznymi. Skalowanie wystąpień kontenerów jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych.

Wdrażanie aktualizacji jako obrazów platformy Docker odbywa się znacznie szybciej i wydajniej. Kontenery platformy Docker zwykle zaczynają się w ciągu sekund, co przyspiesza wprowadzanie. Przerywanie kontenera Docker jest tak proste jak wywoływanie `docker stop` polecenia, zwykle kończącego się w mniej niż drugim.

Ze względu na to, że kontenery są z natury niezmienne, przez zaprojektowanie, nigdy nie trzeba martwić się o uszkodzone maszyny wirtualne, ponieważ skrypt aktualizacji nie uwzględnia konkretnej konfiguracji lub pliku pozostawionego na dysku.

Chociaż aplikacje monolityczne mogą korzystać z platformy Docker, firma Microsoft wprowadza tylko porady dotyczące korzyści. Większe korzyści wynikające z zarządzania kontenerami nie są wdrażane za pomocą koordynatorów kontenerów, które zarządzają różnymi wystąpieniami i cyklem życia każdego wystąpienia kontenera. Rozdzielenie aplikacji monolitycznej na podsystemy, które mogą być skalowane, opracowywane i wdrażane, jest punktem wejścia do obszaru mikrousług.

Aby dowiedzieć się, jak "podnieść i przesunąć" aplikacje monolityczne z kontenerami i jak można przeprowadzić modernizację aplikacji, możesz przeczytać ten dodatkowy przewodnik firmy Microsoft, modernizowanie [istniejących aplikacji platformy .NET za pomocą chmury platformy Azure i kontenerów systemu Windows](../../modernize-with-azure-containers/index.md), które Możesz również pobrać plik PDF z programu <https://aka.ms/LiftAndShiftWithContainersEbook>.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikowanie pojedynczej aplikacji kontenera Docker do Azure App Service

Ponieważ chcesz szybko sprawdzić poprawność kontenera wdrożonego na platformie Azure lub ponieważ aplikacja jest po prostu aplikacją z jednym kontenerem, platforma Azure App Services zapewnia doskonały sposób zapewnienia skalowalnych usług jednego kontenera.

Korzystanie z Azure App Service jest intuicyjne i można szybko rozpocząć pracę, ponieważ zapewnia to doskonałą integrację z usługą git umożliwiającą korzystanie z kodu, kompilowanie go w Microsoft Visual Studio i bezpośrednio wdrażanie go na platformie Azure. Jednak tradycyjnie (bez platformy Docker), jeśli potrzebujesz innych możliwości, struktur lub zależności, które nie są obsługiwane w App Services, musisz oczekiwać na to, dopóki zespół platformy Azure zaktualizuje te zależności w App Service lub przełączył się do innych usług, takich jak Service Fabric, Cloud Services lub nawet zwykłe maszyny wirtualne, dla których masz jeszcze lepszą kontrolę i można zainstalować wymagany składnik lub platformę dla aplikacji.

Teraz, jak pokazano na rysunku 4-4, w przypadku korzystania z programu Visual Studio 2017 obsługa kontenerów w Azure App Service umożliwia dołączenie dowolnych danych w środowisku aplikacji. Jeśli dodaliśmy zależność do aplikacji, ponieważ jest ona uruchamiana w kontenerze, uzyskasz możliwość dołączenia tych zależności do obrazu pliku dockerfile lub Docker.

![Widok kreatora programu Visual Studio do publikowania w usłudze Azure App Service, wyróżnienie selektora dla rejestru kontenerów.](./media/image4.png)

**Rysunek 4-4**. Publikowanie kontenera do Azure App Service z aplikacji lub kontenerów programu Visual Studio

Rysunek 4-4 pokazuje również, że przepływ publikowania wypycha obraz za pomocą Container Registry, który może być Azure Container Registry (rejestr w sąsiedztwie wdrożenia na platformie Azure i zabezpieczony przez Azure Active Directory grup i kont) lub dowolny inny rejestr platformy Docker Podobnie jak w przypadku centrów platformy Docker lub lokalnych rejestrów.

>[!div class="step-by-step"]
>[Poprzedni](common-container-design-principles.md)Następny
>[](state-and-data-in-docker-applications.md)
