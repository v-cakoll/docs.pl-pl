---
title: Co&#39;s nowe w programie Windows Workflow Foundation programu .NET 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b57cf990f9fdf987f4cc414cb42db6cf9fe0da21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="what39s-new-in-windows-workflow-foundation-in-net-45"></a>Co&#39;s nowe w programie Windows Workflow Foundation programu .NET 4.5
[!INCLUDE[wf](../../../includes/wf-md.md)] w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono wiele nowych funkcji, takich jak nowe działania, funkcje projektanta i modele programowania przepływu pracy. Wiele, ale nie wszystkich nowych funkcji przepływu pracy, wprowadzone w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] są obsługiwane w Projektancie ponownie hostowanej przepływu pracy. [!INCLUDE[crabout](../../../includes/crabout-md.md)] nowe funkcje, które są obsługiwane, zobacz [obsługę nowych funkcji Workflow Foundation 4.5 w Projektancie przepływów pracy Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] Migrowanie .NET 3.0 i .NET 3.5 przepływu pracy aplikacji do korzystania z najnowszej wersji, zobacz [wskazówki dotyczące migracji](../../../docs/framework/windows-workflow-foundation/migration-guidance.md). Ten temat zawiera omówienie nowych funkcji przepływu pracy, wprowadzone w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
> [!WARNING]
>  Nowy [!INCLUDE[wf2](../../../includes/wf2-md.md)] funkcje dodane w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są dostępne dla projektów, które odnoszą się do poprzednich wersji platformy. Jeśli projekt, którego celem jest [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ponownie jest skierowany do poprzednich wersji platformy, może wystąpić pewne problemy.  
>   
>  -   C# wyrażenia zostaną zastąpione w Projektancie komunikat **wartość została ustawiona w języku XAML**.  
> -   Wiele błędów kompilacji nastąpi, łącznie z powodu następującego błędu.  
>   
>  **Format pliku nie jest zgodny z bieżącym docelowego framework. Aby przekonwertować format pliku, jawnie Zapisz plik. Ten komunikat o błędzie zniknie po zapisaniu pliku i ponownie otworzyć projektanta.**  
  
##  <a name="BKMK_Versioning"></a> Przechowywanie wersji przepływu pracy  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono kilka nowych funkcji przechowywania wersji na podstawie tych nowe <xref:System.Activities.WorkflowIdentity> klasy. <xref:System.Activities.WorkflowIdentity> udostępnia mechanizm mapowania wystąpienia przepływu pracy utrwalonych z jego definicji przepływu pracy aplikacji autorów.  
  
-   Deweloperzy przy użyciu <xref:System.Activities.WorkflowApplication> hostingu mogą za pomocą <xref:System.Activities.WorkflowIdentity> do włączenia obsługi wielu wersji przepływu pracy side-by-side. Wystąpienia utrwalonego przepływu pracy mogą być ładowane przy użyciu nowego <xref:System.Activities.WorkflowApplicationInstance> klasy, a następnie <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> może służyć przez hosta do poprawnej wersji definicji przepływu pracy podczas tworzenia wystąpienia <xref:System.Activities.WorkflowApplication>. Aby uzyskać więcej informacji, zobacz [za pomocą właściwości WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md) i [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> jest teraz hostem wielu wersji. Gdy wdrażana jest nowa wersja usługi przepływu pracy, nowe wystąpienia są tworzone przy użyciu nowej usługi, ale istniejące wystąpienia wykonać przy użyciu poprzedniej wersji. Aby uzyskać więcej informacji, zobacz [równoległe przechowywanie wersji w klasie WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).  
  
-   Aktualizacja dynamiczna jest wprowadzenie zapewnia mechanizm aktualizacji definicji wystąpienia utrwalonego przepływu pracy. Aby uzyskać więcej informacji, zobacz [aktualizacja dynamiczna](../../../docs/framework/windows-workflow-foundation/dynamic-update.md) i [porady: aktualizacji definicji wystąpienia przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
-   Podano SqlWorkflowInstanceStoreSchemaUpgrade.sql skryptu bazy danych do uaktualnienia trwałości baz danych utworzonych przy użyciu [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bazy danych skryptów. Ten skrypt aktualizacji [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] trwałości baz danych obsługują nowe możliwości przechowywania wersji wprowadzone w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Wystąpienia utrwalonego przepływu pracy w bazie danych są podane wartości domyślne przechowywanie wersji i mogą uczestniczyć w side-by-side wykonywania i aktualizacji dynamicznej. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [.NET Framework 4 trwałości baz danych obsługi przechowywania wersji przepływu pracy uaktualniania](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
##  <a name="BKMK_NewActivities"></a> działania  
 Biblioteka działań wbudowanych zawiera nowe działania i nowe funkcje istniejących działań.  
  
###  <a name="BKMK_NoPersistScope"></a> Zakres NoPersist  
 <xref:System.Activities.Statements.NoPersistScope> to nowe działanie kontenera, który uniemożliwia są zachowywane w przypadku wykonywania działań podrzędnych NoPersistScope przepływu pracy. Jest to przydatne w sytuacjach, gdy nie jest odpowiedni dla przepływu pracy utrwalenia, np. gdy przepływ pracy używa zasobów komputera, takich jak dojścia do plików lub podczas transakcji bazy danych. Wcześniej aby zapobiec trwałości z występujących podczas wykonywania działania, niestandardowego <xref:System.Activities.NativeActivity> używany <xref:System.Activities.NoPersistHandle> była wymagana.  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> Nowe funkcje schematu blokowego  
 Blokowe są aktualizowane dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i ma następujące nowe funkcje:  
  
-   `DisplayName` Właściwość <xref:System.Activities.Statements.FlowSwitch%601> lub <xref:System.Activities.Statements.FlowDecision> działanie to można edytować. Umożliwi to Projektant działań Pokaż więcej informacji na temat działania cel.  
  
-   Blokowe ma nową właściwość o nazwie <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; wartość domyślna tej właściwości to `False`. Jeśli ta właściwość jest ustawiona na `True`, następnie odłączony schemat blokowy węzłów powodują błędy sprawdzania poprawności.  
  
## <a name="support-for-partial-trust"></a>Obsługa częściowej relacji zaufania  
 Przepływy pracy w [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] wymagane domeny aplikacji w pełni zaufany. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], przepływy pracy mogą działać w środowisku częściowej relacji zaufania. W środowisku częściowej relacji zaufania składników innych firm może służyć bez przyznawania im pełny dostęp do zasobów hosta. Niektóre problemy dotyczące uruchamiania przepływów pracy w częściowej relacji zaufania są następujące:  
  
1.  Przy użyciu starszej wersji składników (w tym reguły) zawartych w <xref:System.Activities.Statements.Interop> działania nie jest obsługiwane w częściowej relacji zaufania.  
  
2.  Uruchomione przepływy pracy w częściowej relacji zaufania w <xref:System.ServiceModel.WorkflowServiceHost> nie jest obsługiwane.  
  
3.  Utrwalanie wyjątków w częściowo zaufanym scenariusz jest potencjalnym zagrożeniem dla bezpieczeństwa. Aby wyłączyć utrwalanie wyjątków, rozszerzenie typu <xref:System.Activities.ExceptionPersistenceExtension> musi zostać dodany do projektu, aby zrezygnować z wyjątków trwałych. Poniższy przykład kodu pokazuje sposób wykonania tego typu.  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
    ```  
  
     Jeśli nie, aby można było serializować wyjątki, upewnij się, że wyjątki są używane w ramach <xref:System.Activities.Statements.NoPersistScope>.  
  
4.  Autorzy działania powinny zastępować <xref:System.Activities.Activity.CacheMetadata%2A> środowiska uruchomieniowego przepływu pracy, automatycznie wykonywane odbicia względem typu unikając. Argumenty i działania podrzędne musi być różna od null, a <xref:System.Activities.ActivityMetadata.Bind%2A> musi być jawnie wywołana. Aby uzyskać więcej informacji na temat zastępowania <xref:System.Activities.Activity.CacheMetadata%2A>, zobacz [udostępnianie danych z CacheMetadata](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md). Ponadto wystąpień argumentów typu, który jest `internal` lub **prywatnej** muszą być jawnie tworzone w <xref:System.Activities.Activity.CacheMetadata%2A> w celu uniknięcia tworzonego przez odbicie.  
  
5.  Typy nie będzie używać <xref:System.Runtime.Serialization.ISerializable> lub <xref:System.SerializableAttribute> serializacji; musi obsługiwać typy, które mają być serializowane <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
6.  Wyrażeń, które używają <xref:System.Activities.Expressions.LambdaValue%601> wymagają <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>i w związku z tym nie będzie działać w częściowej relacji zaufania. Przepływy pracy używające <xref:System.Activities.Expressions.LambdaValue%601> należy zastąpić te wyrażenia z działaniami, które pochodzą z <xref:System.Activities.CodeActivity%601>. .  
  
7.  Wyrażenia nie może być kompilowana przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler> lub Visual Basic obsługiwana kompilatora w częściowej relacji zaufania, ale można uruchomić wcześniej skompilowane wyrażenia.  
  
8.  Jednego zestawu, który używa [poziom 2 przezroczystość](http://aka.ms/Level2Transparency) nie można używać w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w trybie pełnego zaufania, i [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w częściowej relacji zaufania.  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> Nowe funkcje projektanta  
  
###  <a name="BKMK_DesignerSearch"></a> Wyszukiwanie projektanta  
 Aby większych przepływy pracy łatwiejsze w obsłudze, przepływy pracy teraz można przeszukiwać według słów kluczowych. Ta funkcja jest dostępna tylko w programie Visual Studio; Ta funkcja nie jest dostępna w Projektancie rehosted. Dostępne są dwa rodzaje wyszukiwania:  
  
-   Szybkie szukanie inicjowane z albo **Ctrl + F** lub **Edytuj**, **Znajdź i Zamień**, **szybkiego wyszukiwania**.  
  
-   Znajdź w plikach, inicjowane z albo **Ctrl + Shift + F** lub **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**.  
  
 Należy pamiętać, że zamiany nie jest obsługiwany.  
  
####  <a name="BKMK_QuickFind"></a> Szybkie wyszukiwanie  
 Słowa kluczowe przeszukiwane w przepływach pracy będzie odpowiadała projektanta następujące elementy:  
  
-   Właściwości <xref:System.Activities.Activity> obiektów, <xref:System.Activities.Statements.FlowNode> obiektów, <xref:System.Activities.Statements.State> obiektów, <xref:System.Activities.Statements.Transition> obiektów i inne elementy niestandardowe sterowanie przepływem.  
  
-   Zmienne  
  
-   Argumenty  
  
-   Wyrażenia  
  
 Szybkie szukanie odbywa się na projektanta <xref:System.Activities.Presentation.Model.ModelItem> drzewa. Szybkie szukanie nie będzie wyszukiwać przestrzenie nazw zaimportowany w definicji przepływu pracy.  
  
####  <a name="BKMK_FindInFiles"></a> Znajdź w plikach  
 Słowa kluczowe przeszukiwane w przepływach pracy będzie odpowiadała rzeczywistej zawartości pliki przepływu pracy. Wyniki wyszukiwania będą wyświetlane w okienku widoku programu Visual Studio znaleźć wyników. Dwukrotne kliknięcie wyniku elementu umożliwi nawigację do działania, która zawiera dopasowania w Projektancie przepływów pracy.  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> Usunięcie elementu menu kontekstowego w zmiennej i argument projektanta  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], zmienne i argumenty można usunąć tylko w Projektancie za pomocą klawiatury. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zmienne i argumenty można usunąć za pomocą menu kontekstowego.  
  
 Poniższy zrzut ekranu przedstawia menu kontekstowe projektanta zmienną i argument.  
  
 ![Zmienna i Menu kontekstowego projektanta argumentów](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> Auto przestrzennego sekwencji  
 Od przepływu pracy lub działania niektórych kontenera (takich jak <xref:System.Activities.Statements.NoPersistScope>) może zawierać tylko działania jednej jednostki, dodawanie drugiego działania wymagane developer usunąć pierwsze działanie, należy dodać <xref:System.Activities.Statements.Sequence> działania, a następnie dodać zarówno działania działanie sekwencji. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], podczas dodawania drugiego działania na powierzchnię projektanta `Sequence` działanie zostanie automatycznie utworzone opakowywać zarówno działań.  
  
 Poniższy zrzut ekranu przedstawia `WriteLine` działania w `Body` z `NoPersistScope`.  
  
 ![Automatycznie&#45;przestrzenny lokalizacji docelowej](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Poniższy zrzut ekranu przedstawia tworzonych automatycznie `Sequence` działania w `Body` po drugiej `WriteLine` jest spadła poniżej pierwszy.  
  
 ![Automatycznie utworzone działania sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> Tryb kadrowania  
 Aby łatwiej dużych przepływu pracy w projektancie, można włączyć tryb kadrowania, co pozwala deweloperowi kliknij i przeciągnij, aby przenieść widoczną część przepływu pracy zamiast konieczności korzystania z pasków przewijania. Przycisk, aby aktywować tryb kadrowania jest w prawym dolnym rogu projektanta.  
  
 Poniższy zrzut ekranu przedstawia przycisk przesunięcie, który znajduje się w prawym dolnym rogu projektanta przepływów pracy.  
  
 ![Przycisk przesunięcie w Projektancie przepływów pracy](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Środkowy przycisk myszy lub spacji może również służyć do kadrować projektanta przepływów pracy.  
  
###  <a name="BKMK_MultiSelect"></a> Wielokrotnego wyboru  
 Wiele działań można wybrać w tym samym czasie, przeciągając prostokąt wokół nich (Jeśli nie jest włączony tryb kadrowania) lub trzymając wciśnięty klawisz Ctrl i kliknij odpowiednie działania po kolei.  
  
 Wielokrotny działania może także przeciąganie i upuszczanie w Projektancie i może również przetwarzanie za pomocą menu kontekstowego.  
  
###  <a name="BKMK_DocumentOutline"></a> Wyświetlanie konspektu elementów przepływu pracy  
 Aby ułatwić Przejdź hierarchiczny przepływów pracy, składniki przepływu pracy są wyświetlane w widoku konspektu style drzewa. Wyświetlanie konspektu jest wyświetlany w **konspekt dokumentu** widoku. Aby otworzyć ten widok z górnego menu, wybierz **widoku**, **inne okna**, **konspekt dokumentu**, lub naciśnij klawisz Ctrl W U. Klikając węzeł w widoku konspektu przejdzie do odpowiadającego im działania w Projektancie przepływów pracy i widoku konspektu zostaną zaktualizowane w celu wyświetlenia działań, które są wybrane w projektancie.  
  
 Poniższy zrzut ekranu ukończone przepływu pracy z [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) przedstawia widok konspektu z sekwencyjnego przepływu pracy.  
  
 ![Widoku w Projektancie przepływów pracy konspektu](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> Wyrażenia języka C#  
 Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie wyrażenia w przepływach pracy można zapisywać tylko w języku Visual Basic. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka Visual Basic są używane tylko w przypadku projektów utworzonych za pomocą języka Visual Basic. Projekty Visual C# teraz używać C# dla wyrażeń. Jakie funkcje, takie jak intellisense i wyróżnianie gramatyki dostępny jest funkcjonalnej Edytor wyrażenia języka C#. C# projektów przepływu pracy utworzone w poprzednich wersjach, które używają wyrażeń języka Visual Basic, będą nadal działać.  
  
 C# wyrażenia są weryfikowane w czasie projektowania. Błędy w wyrażeniach języka C# będą oznaczone znakiem gramatyczne.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] C# wyrażeń, zobacz [wyrażeń C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
###  <a name="BKMK_Visibility"></a> Większa kontrola nad widoczność paska powłoki i nagłówek elementów  
 W Projektancie rehosted niektóre ze standardowych formantów interfejsu użytkownika nie może mieć znaczenie dla danego przepływu pracy i może być wyłączona. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], to dostosowanie jest obsługiwana tylko na pasku powłoki w dolnej części projektanta. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], widoczność powłoki elementy nagłówka w górnej części projektanta można dostosować przez ustawienie <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> z odpowiednią <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> wartość.  
  
###  <a name="BKMK_AutoConnect"></a> Automatycznie połączyć i auto-insert w przepływach pracy schemat blokowy i automatu stanów  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], połączeń między węzłami w przepływie pracy schemat blokowy musiały ręcznie dodawać. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], schemat blokowy i automatu stanów węzły mają automatycznie połączyć punktów, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika na powierzchnię projektanta. Porzucenie działania w jednej z tych punktów automatycznie dodaje działanie oraz konieczne połączenia.  
  
 Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika.  
  
 ![Węzeł początkowy schemat blokowy przedstawiający punktów połączenie automatyczne](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Działania można również być przeciągnięto połączeń między węzłami schemat blokowy a Państwa auto wstawienie węzła między dwóch pozostałych węzłach. Poniższy zrzut ekranu pokazuje linie łączące wyróżnione gdzie działania mogą być przeciągnięte z przybornika i porzucony.  
  
 ![Automatycznie&#45;Wstaw obsługę upuszczanie działań](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "automatycznego wstawiania")  
  
###  <a name="BKMK_Annotations"></a> Adnotacje projektanta  
 W celu ułatwienia tworzenia przepływów pracy większy, projektanta obsługuje dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotacja można dodać do działania, stanów, schemat blokowy węzłów, zmienne i argumentów. Poniższy zrzut ekranu przedstawia menu kontekstowego pozwala dodawać adnotacje do projektanta.  
  
 ![Menu kontekstowe adnotacji](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>Stany debugowania  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], elementy z systemem innym niż działania nie obsługuje punktów przerwania debugowania, ponieważ nie były jednostki wykonywania. Ta wersja udostępnia mechanizm do dodawania punktów przerwania, aby <xref:System.Activities.Statements.State> obiektów. Gdy punkt przerwania jest ustawiony na <xref:System.Activities.Statements.State>, spowoduje przerwanie wykonywania, jeśli stan jest optymalizowane pod, przed jego wpis zaplanowane działania lub wyzwalaczy.  
  
###  <a name="BKMK_ActivityDelegates"></a> Definiowanie oraz stosowanie ActivityDelegate obiektów w Projektancie  
 Działania w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] używane <xref:System.Activities.ActivityDelegate> obiektu wykonywania punkty inne części przepływu pracy może interakcyjnie wykonywania przepływu pracy, ale dla których zwykle przy użyciu tych punktów wykonywania wymagane odpowiedniej ilości kodu. W tej wersji deweloperzy mogą Definiowanie oraz stosowanie delegatów działania za pomocą projektanta przepływów pracy. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie oraz stosowanie delegatów działania w Projektancie przepływów pracy](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
###  <a name="BKMK_BuildTimeValidation"></a> Weryfikacja w czasie kompilacji  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], błędy sprawdzania poprawności przepływu pracy są traktowane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. Oznacza to, tworzenie przepływu pracy projektu może się powieść, nawet jeśli wystąpiły błędy sprawdzania poprawności przepływu pracy. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], błędy sprawdzania poprawności przepływu pracy spowodować niepowodzenie kompilacji.  
  
###  <a name="BKMK_DesignTimeValidation"></a> Sprawdzanie poprawności czasu projektowania tła  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], przepływy pracy została sprawdzona jako proces pierwszoplanowy potencjalnie mogą powodować zawieszanie interfejsu użytkownika podczas weryfikacji złożony i czasochłonny procesów. Teraz sprawdzania poprawności przepływu pracy odbywa się na wątku w tle, dzięki czemu interfejsu użytkownika nie jest blokowane.  
  
###  <a name="BKMK_ViewState"></a> Wyświetlanie stanu znajduje się w innej lokalizacji w plikach XAML  
 W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to niewygodne dla deweloperów, którzy chcą bezpośrednio odczytywać XAML lub napisać kod, aby usunąć informacje o stanie widoku. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], informacje o stanie widoku w pliku XAML jest szeregowana jako oddzielny element w pliku XAML.  Deweloperzy mogą łatwo zlokalizować i Edytuj informacje widok stanu działania lub całkowicie usunąć stan widoku.  
  
###  <a name="BKMK_ExpressionExtensibility"></a> Wyrażenie rozszerzalności  
 W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], możemy umożliwiają deweloperom tworzenie własnych wyrażeń i środowisko, które można podłączyć do projektanta przepływów pracy autorstwa wyrażenia.  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> Zgody na funkcje 4.5 przepływu pracy w Projektancie rehosted  
 Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje uwzględnione w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są włączone domyślnie projektancie rehosted. To, aby upewnić się, że aplikacje korzystające z funkcji rehosted projektanta nie są dzielone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w Projektancie rehosted, albo ustaw <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> ".NET Framework 4.5" lub zestaw poszczególnych członków <xref:System.Activities.Presentation.DesignerConfigurationService> umożliwiające poszczególnych funkcji.  
  
##  <a name="BKMK_NewWFModels"></a> Nowe modele programowania przepływu pracy  
 Oprócz schemat blokowy i modele programowania sekwencyjnego przepływu pracy ta wersja zawiera przepływy pracy automatu stanów i usług przepływu pracy pierwszy kontraktu.  
  
###  <a name="BKMK_StateMachine"></a> Przepływy pracy automatu stanów  
 Przepływy pracy automatu stanów zostały wprowadzone w ramach programu .NET Framework 4, wersja 4.0.1 w [Aktualizacja platformy Microsoft .NET Framework 4 1](http://go.microsoft.com/fwlink/?LinkID=215092). Ta aktualizacja jest uwzględniona kilka nowych klas i działań, które mogą deweloperom tworzenie przepływów pracy komputera stanu. Zaktualizowane dla tych klas i działań [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizacje obejmują:  
  
1.  Możliwość określenia punktów przerwania stanów  
  
2.  Możliwość kopiowania i wklejania przejścia w Projektancie przepływów pracy  
  
3.  Projektanta obsługę tworzenia przejścia wyzwalaczem udostępnionym  
  
4.  Używany do tworzenia przepływów pracy automatu stanów, łącznie z czynności: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>  
  
 Poniższy zrzut ekranu przedstawia przepływ pracy automatu stanu ukończenia od [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [jak: utworzyć przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Ukończono przepływ pracy automatu stanów](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Aby uzyskać więcej informacji o tworzeniu przepływów pracy maszyny stanu, zobacz [przepływy pracy maszyny stanu](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
###  <a name="BKMK_ContractFirst"></a> Programowanie pierwszy kontraktu przepływu pracy  
 Narzędzie do projektowania przepływu pracy pierwszy kontraktu umożliwia deweloperowi najpierw Projektuj kontraktu w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio automatycznie wygenerować szablon czynności w przyborniku reprezentujący każdej operacji. Te działania są następnie używane do tworzenia przepływu pracy, który implementuje operacji zdefiniowanych przez umowy. Projektant przepływu pracy zostanie przeprowadzona Weryfikacja usługi przepływu pracy, aby upewnić się, czy te operacje są wykonywane i podpis przepływ pracy odpowiada podpisu kontraktu. Deweloper można również skojarzyć usługi przepływu pracy z kolekcją zaimplementowanych kontraktów. Aby uzyskać więcej informacji na projektowanie usługi kontraktu pierwszy przepływu pracy, zobacz [porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
