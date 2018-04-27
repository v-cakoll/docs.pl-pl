---
title: Obsługa nowej funkcji Foundation 4.5 przepływu pracy w Projektancie Rehosted przepływów pracy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 999c18f20264a71cf73bbd5afd352ad3104a03e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Obsługa nowej funkcji Foundation 4.5 przepływu pracy w Projektancie Rehosted przepływów pracy
[!INCLUDE[wf](../../../includes/wf-md.md)] w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono wiele nowych funkcji, w tym kilka ulepszeń obsługi projektanta przepływów pracy. W tym temacie szczegółowe informacje, które te funkcje są obsługiwane w Projektancie rehosted i te, które nie są obecnie obsługiwane.  
  
> [!NOTE]
>  Aby uzyskać listę wszystkich nowej [!INCLUDE[wf](../../../includes/wf-md.md)] funkcje dodane w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], w tym te, które są związane z projektanta rehosting, zobacz [What's New in Windows Workflow Foundation w programie .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="activities"></a>Kategoria Activities  
 Biblioteka działań wbudowanych zawiera nowe działania i nowe funkcje istniejących działań. Wszystkie te nowe działania są obsługiwane w Projektancie rehosted. Aby uzyskać więcej informacji o tych nowych działań, zobacz [działania](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) sekcji [What's New in Windows Workflow Foundation w programie .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="c-expressions"></a>Wyrażenia języka C#  
 Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie wyrażenia w przepływach pracy można zapisywać tylko w języku Visual Basic. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka Visual Basic są używane tylko w przypadku projektów utworzonych za pomocą języka Visual Basic. Projekty Visual C# teraz używać C# dla wyrażeń. Podczas tworzenia przepływów pracy w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], jakie funkcje, takie jak intellisense i wyróżnianie gramatyki dostępny jest funkcjonalnej Edytor wyrażenia języka C#. C# projektów przepływu pracy utworzone w poprzednich wersjach, które używają wyrażeń języka Visual Basic, będą nadal działać.  
  
> [!WARNING]
>  C# wyrażenia nie są obsługiwane w Projektancie rehosted.  
  
## <a name="new-designer-capabilities"></a>Nowe funkcje projektanta  
  
### <a name="designer-search"></a>Wyszukiwanie projektanta  
 [Szybkiego wyszukiwania](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [Znajdź w plikach](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) funkcje wprowadzone w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są obsługiwane w Projektancie rehosted. `Toolbox` Wyszukiwanie jest obsługiwane w Projektancie rehosted. Aby uzyskać więcej informacji o tych funkcjach, zobacz [wyszukiwania projektanta](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).  
  
> [!WARNING]
>  [Szybkie wyszukiwanie](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) i [Znajdź w plikach](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nie są obsługiwane w Projektancie rehosted.  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Usunięcie elementu menu kontekstowego w zmiennej i argument projektanta  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], zmienne i argumenty można usunąć tylko w Projektancie za pomocą klawiatury. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zmienne i argumenty można usunąć za pomocą menu kontekstowego. Ta funkcja jest obsługiwana w Projektancie rehosted.  
  
 Poniższy zrzut ekranu przedstawia menu kontekstowe projektanta zmienną i argument.  
  
 ![Zmienna i Menu kontekstowego projektanta argumentów](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>Auto przestrzennego sekwencji  
 Od przepływu pracy lub działania niektórych kontenera (takich jak <xref:System.Activities.Statements.NoPersistScope>) może zawierać tylko działania jednej jednostki, dodawanie drugiego działania wymagane developer usunąć pierwsze działanie, należy dodać <xref:System.Activities.Statements.Sequence> działania, a następnie dodać zarówno działania działanie sekwencji. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], podczas dodawania drugiego działania na powierzchnię projektanta `Sequence` działanie zostanie automatycznie utworzone opakowywać zarówno działań. Ta funkcja jest obsługiwana w Projektancie rehosted.  
  
 Poniższy zrzut ekranu przedstawia `WriteLine` działania w `Body` z `NoPersistScope`.  
  
 ![Automatycznie&#45;przestrzenny lokalizacji docelowej](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Poniższy zrzut ekranu przedstawia tworzonych automatycznie `Sequence` działania w `Body` po drugiej `WriteLine` jest spadła poniżej pierwszy.  
  
 ![Automatycznie utworzone działania sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>Tryb kadrowania  
 Aby łatwiej dużych przepływu pracy w projektancie, można włączyć tryb kadrowania, co pozwala deweloperowi kliknij i przeciągnij, aby przenieść widoczną część przepływu pracy zamiast konieczności korzystania z pasków przewijania. Przycisk, aby aktywować tryb kadrowania jest w prawym dolnym rogu projektanta. Ta funkcja jest obsługiwana w Projektancie rehosted.  
  
 Poniższy zrzut ekranu przedstawia przycisk przesunięcie, który znajduje się w prawym dolnym rogu projektanta przepływów pracy.  
  
 ![Przycisk przesunięcie w Projektancie przepływów pracy](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Środkowy przycisk myszy lub spacji może również służyć do kadrować projektanta przepływów pracy.  
  
### <a name="multi-select"></a>Wielokrotnego wyboru  
 Wiele działań można wybrać w tym samym czasie, przeciągając prostokąt wokół nich (Jeśli nie jest włączony tryb kadrowania) lub trzymając wciśnięty klawisz Ctrl i kliknij odpowiednie działania po kolei. Ta funkcja jest obsługiwana w Projektancie rehosted.  
  
 Wielokrotny działania może także przeciąganie i upuszczanie w Projektancie i może również przetwarzanie za pomocą menu kontekstowego.  
  
### <a name="outline-view-of-workflow-items"></a>Wyświetlanie konspektu elementów przepływu pracy  
 Aby ułatwić Przejdź hierarchiczny przepływów pracy, składniki przepływu pracy są wyświetlane w widoku konspektu style drzewa. Wyświetlanie konspektu jest wyświetlany w **konspekt dokumentu** widoku. Aby otworzyć ten widok w programie Visual Studio z górnego menu, wybierz **widoku**, **inne okna**, **konspekt dokumentu**, lub naciśnij klawisz Ctrl W U. Klikając węzeł w widoku konspektu przejdzie do odpowiadającego im działania w Projektancie przepływów pracy i widoku konspektu zostaną zaktualizowane w celu wyświetlenia działań, które są wybrane w projektancie. Ta funkcja jest obsługiwana w Projektancie rehosted.  
  
 Poniższy zrzut ekranu ukończone przepływu pracy z [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) przedstawia widok konspektu z sekwencyjnego przepływu pracy.  
  
 ![Widoku w Projektancie przepływów pracy konspektu](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Większa kontrola nad widoczność paska powłoki i nagłówek elementów  
 W Projektancie rehosted niektóre ze standardowych formantów interfejsu użytkownika nie może mieć znaczenie dla danego przepływu pracy i może być wyłączona. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], to dostosowanie jest obsługiwana tylko na pasku powłoki w dolnej części projektanta. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], widoczność powłoki elementy nagłówka w górnej części projektanta można dostosować przez ustawienie <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> z odpowiednią <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> wartość.  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Automatycznie połączyć i auto-insert w przepływach pracy schemat blokowy i automatu stanów  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], połączeń między węzłami w przepływie pracy schemat blokowy musiały ręcznie dodawać. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], schemat blokowy i automatu stanów węzły mają automatycznie połączyć punktów, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika na powierzchnię projektanta. Porzucenie działania w jednej z tych punktów automatycznie dodaje działanie oraz konieczne połączenia.  
  
 Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika.  
  
 ![Węzeł początkowy schemat blokowy przedstawiający punktów połączenie automatyczne](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Działania można również być przeciągnięto połączeń między węzłami schemat blokowy a Państwa auto wstawienie węzła między dwóch pozostałych węzłach. Poniższy zrzut ekranu pokazuje linie łączące wyróżnione gdzie działania mogą być przeciągnięte z przybornika i porzucony.  
  
 ![Automatycznie&#45;Wstaw obsługę upuszczanie działań](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "automatycznego wstawiania")  
  
 Automatycznie połączyć i automatyczne wstawianie są obsługiwane w Projektancie rehosted.  
  
### <a name="designer-annotations"></a>Adnotacje projektanta  
 W celu ułatwienia tworzenia przepływów pracy większy, projektanta obsługuje dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotacja można dodać do działania, stanów, schemat blokowy węzłów, zmienne i argumentów. Poniższy zrzut ekranu przedstawia menu kontekstowego pozwala dodawać adnotacje do projektanta.  
  
 ![Menu kontekstowe adnotacji](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 Adnotacje projektanta są obsługiwane w Projektancie rehosted.  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definiowanie oraz stosowanie ActivityDelegate obiektów w Projektancie  
 Działania w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] używane <xref:System.Activities.ActivityDelegate> obiektu wykonywania punkty inne części przepływu pracy może interakcyjnie wykonywania przepływu pracy, ale dla których zwykle przy użyciu tych punktów wykonywania wymagane odpowiedniej ilości kodu. W tej wersji deweloperzy mogą Definiowanie oraz stosowanie delegatów działania za pomocą projektanta przepływów pracy. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie oraz stosowanie delegatów działania w Projektancie przepływów pracy](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
 Obiekty delegowane działania są obsługiwane w Projektancie rehosted.  
  
### <a name="build-time-validation"></a>Weryfikacja w czasie kompilacji  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], błędy sprawdzania poprawności przepływu pracy są traktowane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. Oznacza to, tworzenie przepływu pracy projektu może się powieść, nawet jeśli wystąpiły błędy sprawdzania poprawności przepływu pracy. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], błędy sprawdzania poprawności przepływu pracy spowodować niepowodzenie kompilacji.  
  
> [!WARNING]
>  Sprawdzania poprawności czasu kompilacji nie jest obsługiwana w Projektancie rehosted.  
  
### <a name="design-time-background-validation"></a>Sprawdzanie poprawności czasu projektowania tła  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], przepływy pracy została sprawdzona jako proces pierwszoplanowy potencjalnie mogą powodować zawieszanie interfejsu użytkownika podczas weryfikacji złożony i czasochłonny procesów. Teraz sprawdzania poprawności przepływu pracy odbywa się na wątku w tle, dzięki czemu interfejsu użytkownika nie jest blokowane.  
  
 Sprawdzanie poprawności czasu projektowania tła jest obsługiwana w Projektancie rehosted.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Wyświetlanie stanu znajduje się w innej lokalizacji w plikach XAML  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to niewygodne dla deweloperów, którzy chcą bezpośrednio odczytywać XAML lub napisać kod, aby usunąć informacje o stanie widoku. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], informacje o stanie widoku w pliku XAML jest szeregowana jako oddzielny element w pliku XAML.  Deweloperzy mogą łatwo zlokalizować i Edytuj informacje widok stanu działania lub całkowicie usunąć stan widoku.  
  
 Ta funkcja jest obsługiwana w Projektancie rehosted przepływu pracy.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Zgody na funkcje 4.5 przepływu pracy w Projektancie rehosted  
 Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje uwzględnione w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są włączone domyślnie projektancie rehosted. To, aby upewnić się, że aplikacje korzystające z funkcji rehosted projektanta nie są dzielone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w Projektancie rehosted, albo ustaw <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> do ".Net Framework 4.5", lub ustaw poszczególnych członków <xref:System.Activities.Presentation.DesignerConfigurationService> umożliwiające poszczególnych funkcji.  
  
## <a name="new-workflow-development-models"></a>Nowe modele programowania przepływu pracy  
 Oprócz schemat blokowy i modele programowania sekwencyjnego przepływu pracy ta wersja zawiera przepływy pracy automatu stanów i usług przepływu pracy pierwszy kontraktu.  
  
### <a name="state-machine-workflows"></a>Przepływy pracy automatu stanów  
 Przepływy pracy automatu stanów zostały wprowadzone w ramach programu .NET Framework 4.0.1 w [Aktualizacja platformy Microsoft .NET Framework 4 1](http://go.microsoft.com/fwlink/?LinkID=215092). Ta aktualizacja jest uwzględniona kilka nowych klas i działań, które mogą deweloperom tworzenie przepływów pracy komputera stanu. Zaktualizowane dla tych klas i działań [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizacje obejmują:  
  
1.  Możliwość określenia punktów przerwania stanów  
  
2.  Możliwość kopiowania i wklejania przejścia w Projektancie przepływów pracy  
  
3.  Projektanta obsługę tworzenia przejścia wyzwalaczem udostępnionym  
  
4.  Używany do tworzenia przepływów pracy automatu stanów, łącznie z czynności: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>  
  
 Poniższy zrzut ekranu przedstawia przepływ pracy automatu stanu ukończenia od [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [jak: utworzyć przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Aby uzyskać więcej informacji o tworzeniu przepływów pracy maszyny stanu, zobacz [przepływy pracy maszyny stanu](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md). Przepływy pracy automatu stanów są obsługiwane w Projektancie rehosted.  
  
### <a name="contract-first-workflow-development"></a>Programowanie pierwszy kontraktu przepływu pracy  
 Narzędzie do projektowania przepływu pracy pierwszy kontraktu umożliwia deweloperowi najpierw Projektuj kontraktu w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio automatycznie wygenerować szablon czynności w przyborniku reprezentujący każdej operacji. Te działania są następnie używane do tworzenia przepływu pracy, który implementuje operacji zdefiniowanych przez umowy. Projektant przepływu pracy zostanie przeprowadzona Weryfikacja usługi przepływu pracy, aby upewnić się, czy te operacje są wykonywane i podpis przepływ pracy odpowiada podpisu kontraktu. Deweloper można również skojarzyć usługi przepływu pracy z kolekcją zaimplementowanych kontraktów. Aby uzyskać więcej informacji na projektowanie usługi kontraktu pierwszy przepływu pracy, zobacz [porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Programowanie pierwszy kontraktu przepływu pracy nie jest obsługiwana w Projektancie przepływów pracy.
