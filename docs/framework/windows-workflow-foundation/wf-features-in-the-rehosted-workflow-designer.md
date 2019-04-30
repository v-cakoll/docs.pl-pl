---
title: Obsługa nowych funkcji w programie Workflow Foundation 4.5 w rehostowanym projektancie przepływu pracy
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: a7b7ed6987320314ee3fdccf0e58a8c7314fe50d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669842"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Obsługa nowych funkcji w programie Workflow Foundation 4.5 w rehostowanym projektancie przepływu pracy
Windows Workflow Foundation (WF) w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono wiele nowych funkcji, w tym kilka ulepszeń środowiska projektanta przepływu pracy. W tym temacie przedstawiono, które z tych funkcji są obsługiwane w rehostowanym projektancie i te, które nie są obecnie obsługiwane.

> [!NOTE]
>  Aby uzyskać listę wszystkich nowych funkcji Windows Workflow Foundation (WF), wprowadzone w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], w tym te, które są powiązane z rehostowanie projektanta, zobacz [What's New in Windows Workflow Foundation w .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Kategoria Activities
 Wbudowana biblioteka działań zawiera nowe działania i nowe funkcje dla istniejących działań. Wszystkie te nowe działania są obsługiwane w rehostowanym projektancie. Aby uzyskać więcej informacji na temat tych nowych działań, zobacz [działania](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) części [What's New in Windows Workflow Foundation w .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Wyrażenia języka C#
 Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie wyrażenia w przepływach pracy można zapisać tylko w języku Visual Basic. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka Visual Basic są używane tylko w przypadku projektów utworzonych za pomocą języka Visual Basic. Projekty języka Visual C# teraz używać języka C# dla wyrażenia. Podczas tworzenia przepływów pracy w programie Visual Studio 2012, w pełni funkcjonalny edytor wyrażeń języka C# znajduje się które możliwości, takie jak intellisense i wyróżnianie gramatyki. Przepływ pracy projektów języka C# utworzone w poprzednich wersjach, które używają wyrażeń języka Visual Basic będą nadal działać.

> [!WARNING]
>  Wyrażeń języka C# nie są obsługiwane w rehostowanym projektancie.

## <a name="new-designer-capabilities"></a>Nowe funkcje projektanta

### <a name="designer-search"></a>Wyszukiwanie projektanta
 [Szybkie znajdowanie](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [Znajdź w plikach](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) funkcje wprowadzone w programie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są obsługiwane w rehostowanym projektancie. `Toolbox` Wyszukiwanie jest obsługiwane w rehostowanym projektancie. Aby uzyskać więcej informacji o tych funkcjach, zobacz [wyszukiwania projektanta](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
>  [Szybkie wyszukiwanie](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [Znajdź w plikach](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nie są obsługiwane w rehostowanym projektancie.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Usuń element menu kontekstowego w Projektancie zmienną i argument
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], zmienne i argumenty można usunąć tylko w projektancie, za pomocą klawiatury. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zmienne i argumenty można usunąć za pomocą menu kontekstowego. Ta funkcja jest obsługiwana w rehostowanym projektancie.

 Poniższy zrzut ekranu przedstawia zmienną i argument menu kontekstowe projektanta.

 ![Zmienna i Menu kontekstowego projektanta argumentów](./media/designercontextmenu.png "DesignerContextMenu")

### <a name="auto-surround-with-sequence"></a>Auto umieszczanie w sekwencji
 Od przepływu pracy lub niektóre działania kontenera (takie jak <xref:System.Activities.Statements.NoPersistScope>) może zawierać tylko jednej jednostki działania, dodawanie drugiego działania wymagane dla deweloperów usunąć pierwsze działanie, Dodaj <xref:System.Activities.Statements.Sequence> działania, a następnie dodaj oba działań działanie w sekwencji. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], podczas dodawania drugiego działania do powierzchni projektanta `Sequence` działanie zostanie automatycznie utworzone do opakowania obu działań. Ta funkcja jest obsługiwana w rehostowanym projektancie.

 Poniższy zrzut ekranu przedstawia `WriteLine` działania w `Body` z `NoPersistScope`.

 ![Automatyczne&#45;otaczające lokalizację wrzucania](./media/autosurround1.png "AutoSurround1")

 Poniższy zrzut ekranu przedstawia utworzone automatycznie `Sequence` działania w `Body` po drugiej `WriteLine` jest spadła poniżej pierwszej.

 ![Automatycznie utworzone działaniu sequence](./media/autosurround2.png "AutoSurround2")

### <a name="pan-mode"></a>Tryb Pan
 Aby łatwiej przejść z dużych przepływów pracy w projektancie, można włączyć tryb Przesuń, umożliwiając deweloperom kliknij i przeciągnij, aby przenieść widocznej części przepływu pracy, zamiast konieczności używania pasków przewijania. Przycisk, aby uaktywnić tryb panoramowanie jest w prawym dolnym rogu projektanta. Ta funkcja jest obsługiwana w rehostowanym projektancie.

 Poniższy zrzut ekranu przedstawia przycisk przesunięcie, który znajduje się w prawym dolnym rogu projektanta przepływów pracy.

 ![Przycisk przesunięcie w Projektancie przepływu pracy](./media/panbutton.png "PanButton")

 Środkowy przycisk myszy lub spacji może również służyć do Przesuń w Projektancie przepływu pracy.

### <a name="multi-select"></a>Możliwość wielokrotnego wyboru
 Wiele działań można wybrać w tym samym czasie, przeciągając prostokąt wokół nich (gdy nie jest włączony tryb pan) i, przytrzymując klawisz Ctrl i kliknij żądany działania po kolei. Ta funkcja jest obsługiwana w rehostowanym projektancie.

 Wielokrotny działania można też przeciąganie i upuszczanie w Projektancie i może również przetwarzanie za pomocą menu kontekstowego.

### <a name="outline-view-of-workflow-items"></a>Wyświetlanie konspektu elementów przepływu pracy
 Aby ułatwić hierarchiczne przepływów pracy można przejść, składniki przepływu pracy są wyświetlane w widoku konspektu stylu drzewa. Wyświetlanie konspektu jest wyświetlany w **konspekt dokumentu** widoku. Aby otworzyć ten widok w programie Visual Studio z górnego menu, wybierz **widoku**, **Windows inne**, **konspekt dokumentu**, lub naciśnij klawisze Ctrl W U. Klikając węzeł w widoku konspektu spowoduje przejście do odpowiadającego im działania w Projektancie przepływów pracy i widoku konspektu zostaną zaktualizowane w celu wyświetlenia działań, które są wybrane w projektancie. Ta funkcja jest obsługiwana w rehostowanym projektancie.

 Poniższy zrzut ekranu przedstawiający ukończony przepływ pracy z [Samouczek wprowadzający](getting-started-tutorial.md) Pokazuje widok konspektu sekwencyjnego przepływu pracy.

 ![Widoku w Projektancie przepływu pracy konspektu](./media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Większa kontrola nad widoczność pasek powłoki i nagłówek elementów
 W rehostowanym projektancie niektóre standardowych kontrolek interfejsu użytkownika nie może mieć znaczenie dla danego przepływu pracy i może być wyłączona. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], to dostosowanie jest obsługiwana tylko przez pasek powłoki w dolnej części projektanta. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], widoczność powłoki elementy nagłówka w górnej części projektanta może być regulowany poprzez ustawienie <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> z odpowiednią <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> wartość.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Automatyczne łączenie i automatyczne wstawianie w przepływach pracy schematu blokowego i automatu stanów
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], musiały ręcznie dodawać połączeń między węzłami w przepływie pracy schematu blokowego. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], jest blokowy i automatu stanów węzłów automatycznie połączyć z punkty, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika na powierzchni projektowej. Upuszczanie działania na jednym z tych punktów automatycznie dodaje działanie oraz niezbędne połączenie.

 Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika.

 ![Węzeł początkowy schemat blokowy przedstawiający punktów połączenie automatyczne](./media/autoconnect1.png "Autoconnect1")

 Działania również można przeciągać połączeń między węzłami schemat blokowy i Stanami automatyczne wstawianie węzła między dwóch pozostałych węzłach. Poniższy zrzut ekranu przedstawia wyróżnione linii łączącej, gdzie można przeciągnąć z przybornika i porzucić działania.

 ![Automatyczne&#45;Wstaw uchwytu upuszczanie działania](./media/autoinsert.png "automatycznego wstawiania")

 Automatyczne łączenie i automatyczne wstawianie są obsługiwane w rehostowanym projektancie.

### <a name="designer-annotations"></a>Adnotacje projektanta
 W celu ułatwienia tworzenia większych przepływów pracy, Projektant obsługuje dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotację można dodać do działań, Stany, węzłów schematu blokowego, zmienne i argumenty. Poniższy zrzut ekranu przedstawia menu kontekstowe służy do dodawania adnotacji do projektanta.

 ![Menu kontekstowe adnotacji](./media/annotationdialog.png "annotationdialog")

 Adnotacje projektanta są obsługiwane w rehostowanym projektancie.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definiowanie oraz stosowanie ActivityDelegate obiektów w Projektancie
 Działania w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] używane <xref:System.Activities.ActivityDelegate> obiekty do udostępnienia punktami wykonania, gdy inne części przepływu pracy można wchodzić w interakcje z wykonywania przepływu pracy, ale zazwyczaj przy użyciu tych punktów wykonywania wymagana ilość kodu. W tej wersji deweloperzy mogą zdefiniować i stosowanie delegowania działania, za pomocą projektanta przepływów pracy. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Działania delegatach są obsługiwane w rehostowanym projektancie.

### <a name="build-time-validation"></a>Sprawdzanie poprawności w czasie kompilacji
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], błędy sprawdzania poprawności przepływu pracy nie traktowane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. Oznacza to, tworzenia przepływu pracy projektu może zakończyć się pomyślnie, nawet wtedy, gdy wystąpiły błędy sprawdzania poprawności przepływu pracy. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kompilacja nie powiedzie się, że błędy walidacji przepływu pracy.

> [!WARNING]
>  Czas kompilacji sprawdzania poprawności nie jest obsługiwana w rehostowanym projektancie.  
  
### <a name="design-time-background-validation"></a>Sprawdzanie poprawności tła w czasie projektowania  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], przepływy pracy zostały zweryfikowane jako proces pierwszoplanowy, które potencjalnie mogą powodować zawieszanie interfejsu użytkownika podczas procesu weryfikacji złożone i czasochłonne. Teraz walidacji przepływu pracy odbywa się na wątku w tle, dzięki czemu interfejs użytkownika nie jest zablokowany.  
  
 Sprawdzanie poprawności tła w czasie projektowania jest obsługiwana w rehostowanym projektancie.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Wyświetlanie stanu znajduje się w innej lokalizacji w plikach XAML  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to wygodne, dla deweloperów, którzy chcą bezpośrednio odczytywać XAML lub napisać kod, aby usunąć informacje o stanie widoku. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyświetlanie informacji o stanie w pliku XAML jest serializowana jako osobny element w pliku XAML.  Deweloperzy można łatwo zlokalizować i edytować informacje o stanie widoku działania lub całkowicie usunąć stan widoku.  
  
 Ta funkcja jest obsługiwana w rehostowanym projektancie przepływu pracy.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Zoptymalizowany pod kątem w funkcji Workflow 4.5 w rehostowanym projektancie  
 Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje uwzględnione w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są włączone domyślnie w rehostowanym projektancie. To, aby upewnić się, że istniejące aplikacje korzystające z rehostowanym projektancie nie są uszkodzone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w rehostowanym projektancie, ustaw wartość <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> do ".Net Framework 4.5", lub ustawić poszczególnych członków <xref:System.Activities.Presentation.DesignerConfigurationService> można włączać poszczególne funkcje.  
  
## <a name="new-workflow-development-models"></a>Nowe modele projektowania przepływu pracy  
 Oprócz schemat blokowy i modele programowania sekwencyjnego przepływu pracy ta wersja zawiera przepływy pracy automatu stanów i usług przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu.  
  
### <a name="state-machine-workflows"></a>Przepływy pracy automatu stanów  
 Przepływy pracy automatu stanów zostały wprowadzone w ramach programu .NET Framework 4.0.1 w [programu Microsoft .NET Framework 4 platformy Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Ta aktualizacja zawierała kilka nowych klas i działań, które mogą deweloperom tworzenie przepływów pracy automatu stanów. Te klasy i działania zostały zaktualizowane w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizacje obejmują:  
  
1. Możliwość ustawienia punktów przerwania na Stanach  
  
2. Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy  
  
3. Wsparcie tworzenia udostępnionych przejść wyzwalaczy  
  
4. Działania używany do tworzenia przepływów pracy automatu stanów, w tym: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>  
  
 Poniższy zrzut ekranu przedstawia przepływ pracy automatu stanu ukończenia od [Samouczek wprowadzający](getting-started-tutorial.md) kroku [jak: Tworzenie przepływu pracy automatu stanów](how-to-create-a-state-machine-workflow.md).  
  
 ![Ukończono przepływ pracy automatu stanów](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Aby uzyskać więcej informacji na temat tworzenia przepływów pracy automatu stanów, zobacz [przepływów pracy automatu stanów](state-machine-workflows.md). Przepływy pracy automatu stanów są obsługiwane w rehostowanym projektancie.  
  
### <a name="contract-first-workflow-development"></a>Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu  
 Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia deweloperom projektowanie najpierw kontrakt w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio automatycznie wygenerować szablon działania w przyborniku, reprezentujący każdej operacji. Działania te są następnie używane do tworzenia przepływu pracy, który implementuje operacje zdefiniowane przez umowę. Projektant przepływu pracy zostanie przeprowadzona Weryfikacja usługi przepływu pracy, aby upewnić się, czy te operacje są wykonywane, i podpis przepływu pracy odpowiada sygnatury Umowa. Deweloper można również skojarzyć usługi przepływu pracy z kolekcją zaimplementowane kontrakty. Aby uzyskać więcej informacji na temat opracowywania rozwiązań usługi przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu, zobacz [jak: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu nie jest obsługiwana w Projektancie przepływu pracy.
