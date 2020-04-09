---
title: Aplikacje monolityczne
description: Zapoznaj się z podstawowymi pojęciami konteneryzacji aplikacji monolitycznych.
ms.date: 02/15/2019
ms.openlocfilehash: 3c186f6a300588816916886927f93e0c06ebd6bc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988989"
---
# <a name="monolithic-applications"></a>Aplikacje monolityczne

W tym scenariuszu budujesz pojedynczą i monolityczną aplikację sieci web lub usługę sieci web i wdrażasz ją jako kontener. W aplikacji struktura może nie być monolityczne; może składać się z kilku bibliotek, składników, a nawet warstw (warstwa aplikacji, warstwa domeny, warstwa dostępu do danych itp.). Zewnętrznie jest to pojedynczy kontener, taki jak pojedynczy proces, pojedyncza aplikacja sieci web lub pojedyncza usługa.

Aby zarządzać tym modelem, należy wdrożyć pojedynczy kontener do reprezentowania aplikacji. Aby go skalować, wystarczy dodać kilka dodatkowych kopii z modułem równoważenia obciążenia z przodu. Prostota pochodzi z zarządzania pojedynczym wdrożeniem w jednym kontenerze lub maszynie wirtualnej (VM).

Po zleceniodawcy, że kontener robi tylko jedną rzecz i robi to w jednym procesie, wzorzec monolityczny jest w konflikcie. W każdym kontenerze można dołączyć wiele składników/bibliotek lub warstw wewnętrznych, jak pokazano na rysunku 4-1.

![Diagram przedstawiający monolityczną aplikację, która jest skalowana w poziomie przez klonowanie aplikacji.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Rysunek 4-1.** Przykład monolitycznej architektury aplikacji

Aplikacja monolityczne ma wszystkie lub większość jego funkcji w ramach jednego procesu lub kontenera i jest s componentized w warstwach wewnętrznych lub bibliotek. Wadą tego podejścia jest, jeśli lub gdy aplikacja rośnie, wymagając go do skalowania. Jeśli cała aplikacja skalowana, to naprawdę nie jest problem. Jednak w większości przypadków kilka części aplikacji są punkty dławika, które wymagają skalowania, podczas gdy inne składniki są używane mniej.

Korzystając z typowego przykładu handlu elektronicznego, prawdopodobnie potrzebujesz skalowania składnika informacji o produkcie. O wiele więcej klientów przegląda produkty niż je kupuje. Więcej klientów korzysta z koszyka niż z potoku płatności. Mniej klientów dodawać komentarze lub wyświetlić ich historii zakupów. I prawdopodobnie masz tylko garstkę pracowników, w jednym regionie, którzy muszą zarządzać treściami i kampaniami marketingowymi. Skalując projekt monolityczny, cały kod jest wdrażany wiele razy.

Oprócz problemu "scale-everything", zmiany w jednym składniku wymagają pełnego ponownego przetestowania całej aplikacji, a także pełnego ponownego rozmieszczenia wszystkich wystąpień.

Podejście monolityczne jest powszechne, a wiele organizacji opracowuje za pomocą tej metody architektonicznej. Wielu z nich cieszy się wystarczająco dobrymi wynikami, podczas gdy inni napotykają ograniczenia. Wiele z nich zaprojektowało swoje aplikacje w tym modelu, ponieważ narzędzia i infrastruktura były zbyt trudne do zbudowania soa i nie widzą potrzeby — dopóki aplikacja nie wzrosła.

Z punktu widzenia infrastruktury każdy serwer może uruchamiać wiele aplikacji w ramach tego samego hosta i mieć akceptowalny stosunek wydajności w użyciu zasobów, jak pokazano na rysunku 4-2.

![Diagram przedstawiający jeden host z wieloma aplikacjami w oddzielnych kontenerach.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Rysunek 4-2.** Host z wieloma aplikacjami/kontenerami

Wreszcie, z punktu widzenia dostępności, aplikacje monolityczne muszą być wdrażane jako całość; oznacza to, że w przypadku, gdy należy *zatrzymać i uruchomić,* wszystkie funkcje i wszyscy użytkownicy zostaną naruszone podczas okna wdrażania. W niektórych sytuacjach użycie platformy Azure i kontenerów można zminimalizować te sytuacje i zmniejszyć prawdopodobieństwo przestoju aplikacji, jak widać na rysunku 4-3.

Aplikacje monolityczne można wdrożyć na platformie Azure przy użyciu dedykowanych maszyn wirtualnych dla każdego wystąpienia. Za pomocą [zestawów skalowania maszyn wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)można łatwo skalować maszyny wirtualne.

Usługi Azure [App Services](https://azure.microsoft.com/services/app-service/) można również używać do uruchamiania aplikacji monolitycznych i łatwego skalowania wystąpień bez konieczności zarządzania maszynami wirtualnymi. Usługi Azure App Services można uruchomić pojedyncze wystąpienia kontenerów platformy Docker, jak również, upraszczając wdrożenie.

Można wdrożyć wiele maszyn wirtualnych jako hosty platformy Docker i uruchomić dowolną liczbę kontenerów na maszynę wirtualną. Następnie za pomocą modułu Równoważenia obciążenia platformy Azure, jak pokazano na rysunku 4-3, można zarządzać skalowania.

![Diagram przedstawiający monolityczną aplikację skalowany w poziomie do różnych hostów.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Rysunek 4-3**. Wiele hostów skalowania w poziomie pojedynczej aplikacji platformy Docker

Można zarządzać wdrażaniem samych hostów za pomocą tradycyjnych technik wdrażania.

Kontenery platformy Docker można zarządzać z wiersza polecenia za pomocą poleceń, takich jak `docker run` i `docker-compose up`, a także można zautomatyzować go w potokach ciągłego dostarczania (CD) i wdrożyć do hostów platformy Docker z usług Azure DevOps, na przykład.

## <a name="monolithic-application-deployed-as-a-container"></a>Aplikacja monolityczna wdrożona jako kontener

Istnieją korzyści przy użyciu kontenerów do zarządzania wdrożeniami monolitycznymi. Skalowanie wystąpień kontenerów jest znacznie szybsze i łatwiejsze niż wdrażanie dodatkowych maszyn wirtualnych.

Wdrażanie aktualizacji jako obrazów platformy Docker jest znacznie szybsze i wydajne w sieci. Kontenery platformy Docker zazwyczaj rozpoczynają się w ciągu kilku sekund, przyspieszając wdrażanie. Burzenie kontenera platformy Docker jest tak `docker stop` proste, jak wywoływanie polecenia, zazwyczaj ukończenie w mniej niż sekundę.

Ponieważ kontenery są z natury niezmienne, zgodnie z projektem, nigdy nie musisz się martwić o uszkodzone maszyny wirtualne, ponieważ skrypt aktualizacji zapomniał uwzględnić określoną konfigurację lub plik pozostawiony na dysku.

Chociaż aplikacje monolityczne mogą korzystać z platformy Docker, dotykamy tylko wskazówek dotyczących korzyści. Większe korzyści z zarządzania kontenerami pochodzą z wdrażania za pomocą koordynatorów kontenerów, które zarządzają różnymi wystąpieniami i cyklem życia każdego wystąpienia kontenera. Podział aplikacji monolitycznych na podsystemy, które mogą być skalowane, opracowane i wdrażane indywidualnie jest punkt wejścia do obszaru mikrousług.

Aby dowiedzieć się, jak "podnieść i przesunąć" aplikacje monolityczne za pomocą kontenerów i jak zmodernizować aplikacje, możesz przeczytać ten dodatkowy przewodnik <https://aka.ms/LiftAndShiftWithContainersEbook>firmy Microsoft, [Modernizuj istniejące aplikacje .NET za pomocą chmury Azure i kontenerów systemu Windows,](../../modernize-with-azure-containers/index.md)które można również pobrać w formacie PDF z .

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikowanie pojedynczej aplikacji kontenera platformy Docker w usłudze Azure App Service

Ponieważ chcesz uzyskać szybką weryfikację kontenera wdrożonego na platformie Azure lub ponieważ aplikacja jest po prostu aplikacją z jednym kontenerem, usługi Azure App Services zapewniają doskonały sposób na zapewnienie skalowalnych usług pojedynczego kontenera.

Korzystanie z usługi Azure App Service jest intuicyjne i można szybko rozpocząć i uruchomić, ponieważ zapewnia doskonałą integrację Git do podjęcia kodu, skompilować go w programie Microsoft Visual Studio i bezpośrednio wdrożyć go na platformie Azure. Ale tradycyjnie (bez platformy Docker), jeśli potrzebujesz innych funkcji, struktur lub zależności, które nie są obsługiwane w usługach app services, trzeba czekać na to, aż zespół platformy Azure aktualizuje te zależności w usłudze App Service lub przełączyć się na inne usługi, takie jak sieć szkieletowa usług, usługi w chmurze lub nawet zwykłych maszyn wirtualnych, dla których masz dalszą kontrolę i można zainstalować wymagany składnik lub strukturę dla aplikacji.

Teraz, jak pokazano na rysunku 4-4, podczas korzystania z programu Visual Studio 2017 obsługa kontenerów w usłudze Azure App Service umożliwia uwzględnienie tego, co chcesz w środowisku aplikacji. Jeśli dodano zależność do aplikacji, ponieważ jest on uruchomiony w kontenerze, można uzyskać możliwość włączenia tych zależności w obrazie dockerfile lub docker.

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie usługi app service przedstawiające rejestr kontenerów.](./media/monolithic-applications/publish-azure-app-service-container.png)

**Rysunek 4-4**. Publikowanie kontenera w usłudze Azure App Service z aplikacji/kontenerów programu Visual Studio

Rysunek 4-4 pokazuje również, że przepływ publikowania wypycha obraz za pośrednictwem rejestru kontenerów, który może być rejestrem kontenerów platformy Azure (rejestrem zbliżonym do wdrożeń na platformie Azure i zabezpieczonym przez grupy i konta usługi Azure Active Directory) lub dowolnym innym rejestrem platformy Docker, takim jak Docker Hub lub rejestrami lokalnymi.

>[!div class="step-by-step"]
>[Poprzedni](common-container-design-principles.md)
>[następny](state-and-data-in-docker-applications.md)
