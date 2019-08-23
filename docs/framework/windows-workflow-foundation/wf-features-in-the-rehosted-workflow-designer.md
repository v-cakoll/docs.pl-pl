---
title: Obsługa nowych funkcji w programie Workflow Foundation 4.5 w rehostowanym projektancie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 69c3577c82c7a0899fb94461255721f4b2ab3ecd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913702"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Obsługa nowych funkcji w programie Workflow Foundation 4.5 w rehostowanym projektancie przepływu pracy
Windows Workflow Foundation (WF) w .NET Framework 4,5 wprowadzono wiele nowych funkcji, w tym kilka ulepszeń środowiska projektanta przepływu pracy. Ten temat zawiera szczegółowe informacje o tych funkcjach, które są obsługiwane w projektancie przeszukanym i które nie są obecnie obsługiwane.

> [!NOTE]
> Aby uzyskać listę wszystkich nowych funkcji Windows Workflow Foundation (WF) wprowadzonych w .NET Framework 4,5, w tym tych, które nie są związane z rehostem projektanta, zobacz artykuł [co nowego w Windows Workflow Foundation w programie .net 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Kategoria Activities
 Wbudowana Biblioteka działań zawiera nowe działania i nowe funkcje dla istniejących działań. Wszystkie te nowe działania są obsługiwane w projektancie przeprowadzonym przez hosta. Aby uzyskać więcej informacji na temat tych nowych działań, zobacz sekcję [działania](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) w artykule [co nowego w Windows Workflow Foundation w programie .NET 4,5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Wyrażenia języka C#
 Przed .NET Framework 4,5 wszystkie wyrażenia w przepływach pracy mogą być zapisywane tylko w Visual Basic. W .NET Framework 4,5 wyrażenia Visual Basic są używane tylko dla projektów utworzonych przy użyciu Visual Basic. Projekty C# wizualizacji teraz C# używają wyrażeń. Podczas tworzenia przepływów pracy w programie Visual Studio 2012 jest C# dostępny w pełni funkcjonalny Edytor wyrażeń, który zawiera funkcje, takie jak wyróżnianie gramatyki i technologia IntelliSense. C#projekty przepływu pracy utworzone w poprzednich wersjach, które używają wyrażeń Visual Basic, nadal będą działały.

> [!WARNING]
>  C#wyrażenia nie są obsługiwane w projektancie przeszukanym.

## <a name="new-designer-capabilities"></a>Nowe możliwości projektanta

### <a name="designer-search"></a>Wyszukiwanie projektanta
 Funkcje [szybkiego znajdowania](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [znajdowania plików](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) wprowadzone w .NET Framework 4,5 nie są obsługiwane w projektancie przewidzianym przez hosta. `Toolbox` Wyszukiwanie jest obsługiwane w projektancie przeszukiwanym. Aby uzyskać więcej informacji na temat tych funkcji, zobacz [Wyszukiwanie projektanta](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
>  [Szybkie znajdowanie](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [Znajdowanie plików](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nie są obsługiwane w projektancie przeszukiwanym.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Usuń element menu kontekstowego w programie Variable i Konstruktor argumentów
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie zmienne i argumenty można usunąć tylko w projektancie przy użyciu klawiatury. Począwszy od .NET Framework 4,5, zmienne i argumenty można usuwać za pomocą menu kontekstowego. Ta funkcja jest obsługiwana w projektancie przehostowanym.

 Poniższy zrzut ekranu przedstawia menu kontekstowe dla zmiennej i argumentu projektanta.

 ![Menu kontekstowe projektanta zmiennych i argumentów](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Funkcja autoprzestrzenny z sekwencją
 Ponieważ przepływ pracy lub pewne działania kontenera (takie jak <xref:System.Activities.Statements.NoPersistScope>) mogą zawierać tylko jedno działanie dotyczące treści, dodanie drugiego działania wymagało od dewelopera usunięcia pierwszego działania, <xref:System.Activities.Statements.Sequence> dodania działania, a następnie dodania obu działań do działanie sekwencji. Począwszy od .NET Framework 4,5, podczas dodawania drugiego działania do powierzchni `Sequence` projektanta zostanie automatycznie utworzone działanie umożliwiające zawinięcie obu działań. Ta funkcja jest obsługiwana w projektancie przehostowanym.

 Poniższy zrzut ekranu przedstawia `WriteLine` działanie `Body` w `NoPersistScope`.

 ![Działanie WriteLine w treści działania NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 Poniższy zrzut ekranu przedstawia działanie utworzone `Sequence` automatycznie w czasie, `Body` gdy drugi `WriteLine` zostanie porzucony poniżej pierwszego.

 ![Automatycznie utworzona sekwencja w treści NoPersistScope.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>Tryb kadrowania
 Aby łatwiej nawigować do dużego przepływu pracy w projektancie, można włączyć tryb kadrowania, co umożliwia deweloperom kliknięcie i przeciągnięcie go w celu przeniesienia widocznej części przepływu pracy zamiast używania pasków przewijania. Przycisk służący do uaktywniania trybu kadrowania znajduje się w prawym dolnym rogu projektanta. Ta funkcja jest obsługiwana w projektancie przehostowanym.

 Poniższy zrzut ekranu przedstawia przycisk przesuń znajdujący się w prawym dolnym rogu projektanta przepływu pracy.

 ![Przycisk kadrowania wyróżniony w Projektancie przepływu pracy.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 Do kadrowania projektanta przepływu pracy można również użyć środkowego przycisku myszy lub paska spacji.

### <a name="multi-select"></a>Wybór wieloznaczny
 Jednocześnie można wybrać wiele działań, przeciągając wokół nich prostokąt (gdy tryb panoramowania nie jest włączony) lub przytrzymując klawisz Ctrl i klikając żądane działania po jednym z nich. Ta funkcja jest obsługiwana w projektancie przehostowanym.

 W projektancie można również przeciągać i upuszczać wiele opcji, a także korzystać z menu kontekstowego.

### <a name="outline-view-of-workflow-items"></a>widok konspektu elementów przepływu pracy
 W celu ułatwienia nawigacji hierarchicznych przepływów pracy składniki przepływu pracy są wyświetlane w widoku konspektu w stylu drzewa. Widok konspektu jest wyświetlany w widoku **konspektu dokumentu** . Aby otworzyć ten widok w programie Visual Studio, w menu u góry wybierz pozycję **Widok**, **inne okna**, **Konspekt dokumentu**lub naciśnij klawisze Ctrl W, U. Kliknięcie węzła w widoku konspektu spowoduje przejście do odpowiedniego działania w Projektancie przepływu pracy, a widok konspektu zostanie zaktualizowany w celu wyświetlenia działań wybranych w projektancie. Ta funkcja jest obsługiwana w projektancie przehostowanym.

 Poniższy zrzut ekranu ukończonego przepływu pracy w [samouczku wprowadzenie](getting-started-tutorial.md) przedstawia widok konspektu z sekwencyjnym przepływem pracy.

 ![Zrzut ekranu przedstawiający widok konspektu z sekwencyjnym przepływem pracy w programie Visual Studio](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Większa kontrola widoczności paska powłoki i elementów nagłówka
 W nieobsługiwanym projektancie niektóre standardowe kontrolki interfejsu użytkownika mogą nie mieć znaczenia dla danego przepływu pracy i mogą być wyłączone. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie to dostosowanie jest obsługiwane tylko przez pasek powłoki w dolnej części projektanta. W .NET Framework 4,5 widoczność elementów nagłówka powłoki w górnej części projektanta można dostosować, ustawiając <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> odpowiednią <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> wartość.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>AutoConnect i autoinsert w schemacie blokowym i przepływie pracy automatu Stanów
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie połączenia między węzłami w przepływie pracy Flowchart musiały zostać dodane ręcznie. W .NET Framework 4,5, schemat blokowy i węzły automatu Stanów mają punkty AutoConnect, które stają się widoczne po przeciągnięciu działania z przybornika na powierzchnię projektanta. Porzucenie działania jednego z tych punktów powoduje automatyczne dodanie działania wraz z wymaganym połączeniem.

 Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne po przeciągnięciu działania z przybornika.

 ![Węzeł początkowy Flowchart przedstawiający punkty AutoConnect](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Działania można również przeciągać do połączeń między węzłami i Stanami schematu blokowego, aby wstawić węzeł między dwoma innymi węzłami. Poniższy zrzut ekranu pokazuje wyróżnioną linię łączącą, w której działania mogą być przeciągane z przybornika i upuszczane.

 ![Wstawianie dojścia do usuwania działań](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Funkcja AutoConnect i funkcja autoinsert są obsługiwane w projektancie przeszukanym.

### <a name="designer-annotations"></a>Adnotacje projektanta
 Aby ułatwić tworzenie większych przepływów pracy, Projektant obsługuje teraz Dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotację można dodać do działań, Stanów, węzłów schematu blokowego, zmiennych i argumentów. Poniższy zrzut ekranu przedstawia menu kontekstowe używane do dodawania adnotacji do projektanta.

 ![Zrzut ekranu pokazujący menu dodawania notacji.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Adnotacje projektanta są obsługiwane w projektancie przeszukanym.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definiowanie i używanie obiektów ActivityDelegate w projektancie
 Działania w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] używanych <xref:System.Activities.ActivityDelegate> obiektach umożliwiają uwidocznienie punktów wykonywania, w których inne części przepływu pracy mogą współdziałać z wykonywaniem przepływu pracy, ale używanie tych punktów wykonania zwykle wymagało odpowiedniej ilości kodu. W tej wersji deweloperzy mogą definiować i korzystać z delegatów działań za pomocą projektanta przepływu pracy. Aby uzyskać więcej informacji, zobacz [jak: Zdefiniuj i korzystaj z delegatów działań w](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)Projektant przepływu pracy.

 Delegaty działań są obsługiwane w projektancie przeszukanym.

### <a name="build-time-validation"></a>Weryfikacja czasu kompilacji
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie błędy walidacji przepływu pracy nie były zliczane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. W ten sposób Kompilowanie projektu przepływu pracy może się powieść, nawet jeśli wystąpiły błędy sprawdzania poprawności przepływu pracy. W .NET Framework 4,5 błędy walidacji przepływu pracy powodują niepowodzenie kompilacji.

> [!WARNING]
>  Walidacja czasu kompilacji nie jest obsługiwana w projektancie przehostowanym.  
  
### <a name="design-time-background-validation"></a>Walidacja w tle w czasie projektowania  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie przepływy pracy zostały zweryfikowane jako proces pierwszego planu, który może potencjalnie blokować interfejs użytkownika w trakcie skomplikowanych lub czasochłonnych procesów weryfikacji. Sprawdzanie poprawności przepływu pracy odbywa się teraz w wątku w tle, dzięki czemu interfejs użytkownika nie jest blokowany.  
  
 Walidacja w czasie projektowania w tle jest obsługiwana w projektancie przehostowanym.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Stan widoku znajdujący się w oddzielnej lokalizacji w plikach XAML  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]programie Informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to niewygodne dla deweloperów, którzy chcą bezpośrednio czytać dane XAML, lub napisać kod, aby usunąć informacje o stanie widoku. W .NET Framework 4,5 informacje o stanie widoku w pliku XAML są serializowane jako osobny element w pliku XAML.  Deweloperzy mogą łatwo lokalizować i edytować informacje o stanie widoku działania lub całkowicie usunąć stan widoku.  
  
 Ta funkcja jest obsługiwana w Projektancie przepływów pracy przehostowanej.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Możliwość uczestnictwa w funkcjach przepływu pracy w programie Workflow 4,5 w projektancie przeszukanym  
 Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje zawarte w .NET Framework 4,5 nie są domyślnie włączone w projektancie przeszukanym. Jest to konieczne, aby upewnić się, że istniejące aplikacje korzystające z przeszukanego projektanta nie są uszkodzone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w projektancie ponownie hostowanym, ustaw <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> wartość ".NET Framework 4,5" lub ustaw poszczególnych <xref:System.Activities.Presentation.DesignerConfigurationService> członków, aby włączyć poszczególne funkcje.  
  
## <a name="new-workflow-development-models"></a>Nowe modele projektowania przepływu pracy  
 Poza schematem blokowym i modelami programowania sekwencyjnego przepływu pracy ta wersja obejmuje przepływy pracy automatu stanów i usługi przepływu pracy pierwszego kontraktu.  
  
### <a name="state-machine-workflows"></a>Przepływy pracy automatu Stanów  
 Przepływy pracy automatu Stanów zostały wprowadzone w ramach .NET Framework 4.0.1 w [ramach aktualizacji platformy Microsoft .NET Framework 4](https://go.microsoft.com/fwlink/?LinkID=215092). Ta aktualizacja zawiera kilka nowych klas i działań, które pozwalają deweloperom tworzyć przepływy pracy automatu Stanów. Te klasy i działania zostały zaktualizowane dla .NET Framework 4,5. Aktualizacje obejmują:  
  
1. Możliwość ustawiania punktów przerwania na Stanach  
  
2. Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy  
  
3. Obsługa tworzenia przejść wyzwalaczy udostępnionych przez projektanta  
  
4. Działania służące do tworzenia przepływów pracy automatu <xref:System.Activities.Statements.StateMachine>Stanów, w tym:, <xref:System.Activities.Statements.State>, i<xref:System.Activities.Statements.Transition>  
  
 Poniższy zrzut ekranu przedstawia ukończony przepływ pracy automatu Stanów z samouczka [ [wprowadzenie](getting-started-tutorial.md) krok: Utwórz przepływ pracy](how-to-create-a-state-machine-workflow.md)automatu Stanów.  
  
 ![Ilustracja przedstawiająca ukończony przepływ pracy automatu Stanów.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 Aby uzyskać więcej informacji o tworzeniu przepływów pracy automatu Stanów, zobacz [przepływy pracy automatu Stanów](state-machine-workflows.md). Przepływy pracy automatu Stanów są obsługiwane w projektancie przeszukanym.  
  
### <a name="contract-first-workflow-development"></a>Programowanie — pierwszy przepływ pracy  
 Narzędzie do tworzenia przepływów pracy pierwszego kontraktu pozwala deweloperowi na zaprojektowanie kontraktu w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio, automatyczne wygenerowanie szablonu działania w przyborniku reprezentującym każdą operację. Te działania są następnie używane do tworzenia przepływu pracy, który implementuje operacje zdefiniowane przez umowę. Projektant przepływu pracy sprawdza poprawność usługi przepływu pracy, aby upewnić się, że te operacje są zaimplementowane, a sygnatura przepływu pracy jest zgodna z podpisem kontraktu. Deweloper może również skojarzyć usługę przepływu pracy z kolekcją wdrożonych kontraktów. Aby uzyskać więcej informacji na temat tworzenia usługi przepływu pracy w pierwszej [kolejności, zobacz How to: Utwórz usługę przepływu pracy, która korzysta z istniejącego kontraktu](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)usługi.  
  
> [!WARNING]
>  Opracowywanie kontraktu — pierwszy przepływ pracy nie jest obsługiwany w Projektancie przepływu pracy.
