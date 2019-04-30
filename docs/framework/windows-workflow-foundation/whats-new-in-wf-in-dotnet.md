---
title: Co nowego w programie Windows Workflow Foundation na platformie .NET 4.5
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: a76ec56cf6ac5260f00031bc815b32b1e10804a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61671421"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Co nowego w programie Windows Workflow Foundation na platformie .NET 4.5

Windows Workflow Foundation (WF) w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono wiele nowych funkcji, takich jak nowe działania, funkcje projektanta i modele programowania przepływu pracy. Wiele, ale nie dla wszystkich nowych funkcji przepływu pracy, wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] są obsługiwane w Projektancie ponownie hostowanej przepływu pracy. Aby uzyskać więcej informacji na temat nowych funkcji, które są obsługiwane, zobacz [obsługę nowych funkcji Workflow Foundation 4.5 w Rehostowanym projektancie przepływu pracy](wf-features-in-the-rehosted-workflow-designer.md). Aby uzyskać więcej informacji na temat migrowania aplikacji .NET 3.0 i .NET 3.5 przepływu pracy można korzystać z najnowszej wersji, zobacz [wskazówek dotyczących migracji](migration-guidance.md). Ten temat zawiera omówienie nowych funkcji przepływu pracy, wprowadzonych w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].

> [!WARNING]
> Nowe funkcje programu Windows Workflow Foundation, wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są dostępne w projektach przeznaczonych dla poprzednich wersji Framework. Jeśli projekt, który jest przeznaczony dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ponownie jest przeznaczona do poprzedniej wersji framework, może wystąpić kilka problemów.
>
> - Wyrażeń języka C# zostanie zastąpiony w Projektancie komunikat **wartość została ustawiona w XAML**.
> - Wiele kompilacji wystąpią błędy, łącznie z powodu następującego błędu.
>
> **Format pliku nie jest zgodny z bieżącej struktury określania wartości docelowej. Aby dokonać konwersji na format pliku, należy jawnie Zapisz plik. Ten komunikat o błędzie znikną po zapisaniu go i ponownie otwórz projektanta.**

## <a name="BKMK_Versioning"></a> Przechowywanie wersji przepływu pracy

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] wprowadzono kilka nowych funkcji przechowywania wersji, na podstawie nowej <xref:System.Activities.WorkflowIdentity> klasy. <xref:System.Activities.WorkflowIdentity> udostępnia autorzy aplikacji przepływu pracy mechanizmu mapowania utrwalonego wystąpienia przepływu pracy przy użyciu jego definicji.

- Deweloperzy korzystający z <xref:System.Activities.WorkflowApplication> hostingu może użyć <xref:System.Activities.WorkflowIdentity> hostowania wielu wersji przepływu pracy side-by-side. Wystąpienia przepływu pracy utrwalonych może zostać załadowany za pomocą nowego <xref:System.Activities.WorkflowApplicationInstance> klasy, a następnie <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> może służyć przez hosta w celu zapewnienia odpowiedniej wersji definicji przepływu pracy podczas tworzenia wystąpienia <xref:System.Activities.WorkflowApplication>. Aby uzyskać więcej informacji, zobacz [przy użyciu obiektu WorkflowIdentity i wersjonowanie](using-workflowidentity-and-versioning.md) i [jak: Hostowanie wielu wersji przepływu pracy Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

- <xref:System.ServiceModel.WorkflowServiceHost> jest teraz hostem wielu wersji. Po wdrożeniu nowej wersji usługi przepływu pracy nowe wystąpienia są tworzone przy użyciu nowej usługi, ale istniejące wystąpienia wykonać przy użyciu poprzedniej wersji. Aby uzyskać więcej informacji, zobacz [równoległe przechowywanie wersji w klasie WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Aktualizacja dynamiczna jest wprowadzenie udostępnia mechanizm do aktualizowania definicji utrwalonego wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [aktualizacja dynamiczna](dynamic-update.md) i [jak: Aktualizowanie definicji działającego wystąpienia przepływu pracy](how-to-update-the-definition-of-a-running-workflow-instance.md).

- Skrypt bazy danych SqlWorkflowInstanceStoreSchemaUpgrade.sql znajduje się do uaktualnienia bazy danych trwałości utworzone za pomocą [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bazy danych skryptów. Ten skrypt aktualizacji [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] trwałości baz danych w celu obsługują nowe możliwości przechowywania wersji, wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Wystąpienia utrwalonych przepływów pracy w bazie danych są podane wartości wersji domyślnych i mogą uczestniczyć w aktualizacji dynamicznych i wykonywanie side-by-side. Aby uzyskać więcej informacji, zobacz [uaktualnianie .NET Framework 4 trwałości baz danych do przechowywania wersji przepływu pracy obsługi](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="BKMK_NewActivities"></a> Działania

Wbudowana biblioteka działań zawiera nowe działania i nowe funkcje dla istniejących działań.

### <a name="BKMK_NoPersistScope"></a> Zakres NoPersist

<xref:System.Activities.Statements.NoPersistScope> to nowe działanie kontenera, który uniemożliwia są zachowywane w przypadku działania podrzędne NoPersistScope są wykonywane przez przepływ pracy. Jest to przydatne w scenariuszach, w którym nie jest odpowiedni dla przepływu pracy w celu jego utrwalenia, takie jak podczas przepływu pracy używane są zasoby specyficzny dla komputera, takich jak dojścia do plików lub w trakcie transakcji bazy danych. Wcześniej aby zapobiec trwałości z występujące podczas wykonywania działania, niestandardowe <xref:System.Activities.NativeActivity> używanym <xref:System.Activities.NoPersistHandle> była wymagana.

### <a name="BKMK_NewFlowchartCapabilities"></a> Nowe możliwości schematu blokowego

Blokowe zostały zaktualizowane do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i ma następujące nowe funkcje:

- `DisplayName` Właściwość <xref:System.Activities.Statements.FlowSwitch%601> lub <xref:System.Activities.Statements.FlowDecision> działania jest edytowalny. Umożliwi to Projektant działań, Pokaż więcej informacji na temat cel działania.

- Blokowe ma nową właściwość o nazwie <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; wartość domyślna tej właściwości to `False`. Jeśli ta właściwość jest ustawiona `True`, następnie węzły niepołączonych schemat blokowy generuje błędy sprawdzania poprawności.

## <a name="support-for-partial-trust"></a>Obsługa częściowego zaufania

Przepływy pracy w [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] wymagane pełni zaufanej domeny aplikacji. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], przepływy pracy mogą działać w środowisku częściowej relacji zaufania. W środowisku częściowej relacji zaufania składników innych firm może służyć bez nadawania im pełny dostęp do zasobów hosta. Niektóre problemy dotyczące uruchamiania przepływów pracy w trybie częściowego zaufania są następujące:

1. Za pomocą starszej wersji składników (w tym reguły) zawartych w <xref:System.Activities.Statements.Interop> działania nie jest obsługiwana w częściowej relacji zaufania.

2. Uruchamianie przepływów pracy w częściowej relacji zaufania w <xref:System.ServiceModel.WorkflowServiceHost> nie jest obsługiwane.

3. Utrwalanie wyjątków w częściowym zaufaniu scenariusz polega na potencjalne zagrożenia bezpieczeństwa. Aby wyłączyć utrwalanie wyjątków, rozszerzenie typu <xref:System.Activities.ExceptionPersistenceExtension> musi zostać dodany do projektu, aby zrezygnować z utrwalanie wyjątków. Poniższy przykład kodu demonstruje sposób implementacji tego typu.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     Jeśli wyjątki nie powinny być serializowane, upewnij się, że wyjątki są używane w ramach <xref:System.Activities.Statements.NoPersistScope>.

4. Autorzy działania powinny przesłaniać <xref:System.Activities.Activity.CacheMetadata%2A> pozwala uniknąć środowiska uruchomieniowego przepływu pracy, automatyczne wykonywanie odbicie wobec typu. Argumenty i działania podrzędne muszą być różna od null, i <xref:System.Activities.ActivityMetadata.Bind%2A> musi być wywoływana jawnie. Aby uzyskać więcej informacji na temat zastępowania <xref:System.Activities.Activity.CacheMetadata%2A>, zobacz [Uwidacznianie danych przy użyciu metody CacheMetadata](exposing-data-with-cachemetadata.md). Ponadto wystąpienia argumenty, które są typu, który jest `internal` lub **prywatnej** muszą być jawnie tworzone w <xref:System.Activities.Activity.CacheMetadata%2A> w celu uniknięcia tworzonego przez odbicie.

5. Typy nie będzie używać <xref:System.Runtime.Serialization.ISerializable> lub <xref:System.SerializableAttribute> do serializacji; typy, które mają być serializowane musi obsługiwać <xref:System.Runtime.Serialization.DataContractSerializer>.

6. Wyrażenia, które używają <xref:System.Activities.Expressions.LambdaValue%601> wymagają <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>i dlatego nie będzie działać w częściowej relacji zaufania. Przepływy pracy korzystające z <xref:System.Activities.Expressions.LambdaValue%601> należy zastąpić te wyrażenia z działaniami, które wynikają z <xref:System.Activities.CodeActivity%601>. .

7. Wyrażenia nie może być skompilowana przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler> lub Visual Basic hostowane kompilatora w częściowej relacji zaufania, ale wcześniej skompilowanych wyrażeń, które mogą być uruchamiane.

8. Pojedynczy zestaw, który używa [poziomu 2 przejrzystości](https://aka.ms/Level2Transparency) nie można używać w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w trybie pełnego zaufania, a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w częściowej relacji zaufania.

## <a name="BKMK_NewDesignerCapabilites"></a> Nowe funkcje projektanta

### <a name="BKMK_DesignerSearch"></a> Wyszukiwanie projektanta

Aby większych przepływy pracy łatwiejsze w obsłudze, przepływy pracy mogą być wyszukiwane teraz według słów kluczowych. Ta funkcja jest dostępna tylko w programie Visual Studio; Ta funkcja nie jest dostępna w rehostowanym projektancie. Dostępne są dwa rodzaje wyszukiwania:

- Szybkie szukanie, inicjowane z oboma **Ctrl + F** lub **Edytuj**, **Znajdź i Zamień**, **szybkie znajdowanie**.

- Znajdź w plikach, inicjowane z oboma **Ctrl + Shift + F** lub **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**.

Należy pamiętać, że Zamień nie jest obsługiwany.

#### <a name="BKMK_QuickFind"></a> Szybkie wyszukiwanie

Słowa kluczowe przeszukiwane w przepływach pracy będzie odpowiadał projektanta następujące elementy:

- Właściwości <xref:System.Activities.Activity> obiektów <xref:System.Activities.Statements.FlowNode> obiektów <xref:System.Activities.Statements.State> obiektów <xref:System.Activities.Statements.Transition> obiektów i innych elementów niestandardowych sterowanie przepływem.

- Zmienne

- Argumenty

- Wyrażenia

Szybkie wyszukiwanie jest wykonywane na projektanta <xref:System.Activities.Presentation.Model.ModelItem> drzewa. Szybkiego wyszukiwania nie będzie wyszukiwać przestrzenie nazw, zaimportowana definicja przepływu pracy.

#### <a name="BKMK_FindInFiles"></a> Znajdź w plikach

Słowa kluczowe przeszukiwane w przepływach pracy będzie odpowiadał rzeczywistej zawartości pliki przepływu pracy. Wyniki wyszukiwania będą wyświetlane w okienku widoku programu Visual Studio Znajdź wyniki. Dwukrotne kliknięcie wyniku elementu, spowoduje przejście do działania, które zawiera dopasowanie w Projektancie przepływu pracy.

### <a name="BKMK_VariableDeleteContextMenu"></a> Usuń element menu kontekstowego w Projektancie zmienną i argument

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], zmienne i argumenty można usunąć tylko w projektancie, za pomocą klawiatury. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zmienne i argumenty można usunąć za pomocą menu kontekstowego.

Poniższy zrzut ekranu przedstawia zmienną i argument menu kontekstowe projektanta.

![Zmienna i Menu kontekstowego projektanta argumentów](./media/designercontextmenu.png "DesignerContextMenu")

### <a name="BKMK_AutoSurround"></a> Auto umieszczanie w sekwencji

Od przepływu pracy lub niektóre działania kontenera (takie jak <xref:System.Activities.Statements.NoPersistScope>) może zawierać tylko jednej jednostki działania, dodawanie drugiego działania wymagane dla deweloperów usunąć pierwsze działanie, Dodaj <xref:System.Activities.Statements.Sequence> działania, a następnie dodaj oba działań działanie w sekwencji. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], podczas dodawania drugiego działania do powierzchni projektanta `Sequence` działanie zostanie automatycznie utworzone do opakowania obu działań.

Poniższy zrzut ekranu przedstawia `WriteLine` działania w `Body` z `NoPersistScope`.

![Automatyczne&#45;otaczające lokalizację wrzucania](./media/autosurround1.png "AutoSurround1")

Poniższy zrzut ekranu przedstawia utworzone automatycznie `Sequence` działania w `Body` po drugiej `WriteLine` jest spadła poniżej pierwszej.

![Automatycznie utworzone działaniu sequence](./media/autosurround2.png "AutoSurround2")

### <a name="BKMK_PanMode"></a> Tryb Pan

Aby łatwiej przejść z dużych przepływów pracy w projektancie, można włączyć tryb Przesuń, umożliwiając deweloperom kliknij i przeciągnij, aby przenieść widocznej części przepływu pracy, zamiast konieczności używania pasków przewijania. Przycisk, aby uaktywnić tryb panoramowanie jest w prawym dolnym rogu projektanta.

Poniższy zrzut ekranu przedstawia przycisk przesunięcie, który znajduje się w prawym dolnym rogu projektanta przepływów pracy.

![Przycisk przesunięcie w Projektancie przepływu pracy](./media/panbutton.png "PanButton")

Środkowy przycisk myszy lub spacji może również służyć do Przesuń w Projektancie przepływu pracy.

### <a name="BKMK_MultiSelect"></a> Możliwość wielokrotnego wyboru

Wiele działań można wybrać w tym samym czasie, przeciągając prostokąt wokół nich (gdy nie jest włączony tryb pan) i, przytrzymując klawisz Ctrl i kliknij żądany działania po kolei.

Wielokrotny działania można też przeciąganie i upuszczanie w Projektancie i może również przetwarzanie za pomocą menu kontekstowego.

### <a name="BKMK_DocumentOutline"></a> Wyświetlanie konspektu elementów przepływu pracy

Aby ułatwić hierarchiczne przepływów pracy można przejść, składniki przepływu pracy są wyświetlane w widoku konspektu stylu drzewa. Wyświetlanie konspektu jest wyświetlany w **konspekt dokumentu** widoku. Aby otworzyć ten widok z górnego menu, wybierz **widoku**, **Windows inne**, **konspekt dokumentu**, lub naciśnij klawisze Ctrl W U. Klikając węzeł w widoku konspektu spowoduje przejście do odpowiadającego im działania w Projektancie przepływów pracy i widoku konspektu zostaną zaktualizowane w celu wyświetlenia działań, które są wybrane w projektancie.

Poniższy zrzut ekranu przedstawiający ukończony przepływ pracy z [Samouczek wprowadzający](getting-started-tutorial.md) Pokazuje widok konspektu sekwencyjnego przepływu pracy.

![Widoku w Projektancie przepływu pracy konspektu](./media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")

### <a name="BKMK_CSharpExpressions"></a> Wyrażeń języka C#

Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie wyrażenia w przepływach pracy można zapisać tylko w języku Visual Basic. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka Visual Basic są używane tylko w przypadku projektów utworzonych za pomocą języka Visual Basic. Projekty języka Visual C# teraz używać języka C# dla wyrażenia. W pełni funkcjonalny edytor wyrażeń języka C# znajduje się które możliwości, takie jak intellisense i wyróżnianie gramatyki. Przepływ pracy projektów języka C# utworzone w poprzednich wersjach, które używają wyrażeń języka Visual Basic będą nadal działać.

Wyrażeń języka C# są weryfikowane w czasie projektowania. Błędy w wyrażeniach języka C# będzie oznaczone czerwoną, falistą linią.

Aby uzyskać więcej informacji na temat wyrażeń języka C#, zobacz [wyrażeń języka C#](csharp-expressions.md).

### <a name="BKMK_Visibility"></a> Większa kontrola nad widoczność pasek powłoki i nagłówek elementów

W rehostowanym projektancie niektóre standardowych kontrolek interfejsu użytkownika nie może mieć znaczenie dla danego przepływu pracy i może być wyłączona. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], to dostosowanie jest obsługiwana tylko przez pasek powłoki w dolnej części projektanta. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], widoczność powłoki elementy nagłówka w górnej części projektanta może być regulowany poprzez ustawienie <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> z odpowiednią <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> wartość.

### <a name="BKMK_AutoConnect"></a> Automatyczne łączenie i automatyczne wstawianie w przepływach pracy schematu blokowego i automatu stanów

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], musiały ręcznie dodawać połączeń między węzłami w przepływie pracy schematu blokowego. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], jest blokowy i automatu stanów węzłów automatycznie połączyć z punkty, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika na powierzchni projektowej. Upuszczanie działania na jednym z tych punktów automatycznie dodaje działanie oraz niezbędne połączenie.

Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne, gdy działanie zostanie przeciągnięty z przybornika.

![Węzeł początkowy schemat blokowy przedstawiający punktów połączenie automatyczne](./media/autoconnect1.png "Autoconnect1")

Działania również można przeciągać połączeń między węzłami schemat blokowy i Stanami automatyczne wstawianie węzła między dwóch pozostałych węzłach. Poniższy zrzut ekranu przedstawia wyróżnione linii łączącej, gdzie można przeciągnąć z przybornika i porzucić działania.

![Automatyczne&#45;Wstaw uchwytu upuszczanie działania](./media/autoinsert.png "automatycznego wstawiania")

### <a name="BKMK_Annotations"></a> Adnotacje projektanta

W celu ułatwienia tworzenia większych przepływów pracy, Projektant obsługuje dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotację można dodać do działań, Stany, węzłów schematu blokowego, zmienne i argumenty. Poniższy zrzut ekranu przedstawia menu kontekstowe służy do dodawania adnotacji do projektanta.

![Menu kontekstowe adnotacji](./media/annotationdialog.png "annotationdialog")

### <a name="debugging-states"></a>Stany debugowania

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], elementy-activity nie obsługuje punktów przerwania debugowania, ponieważ nie były one jednostki wykonywania. Ta wersja oferuje mechanizm służący do dodawania punktów przerwania, aby <xref:System.Activities.Statements.State> obiektów. Gdy punkt przerwania jest ustawiony na <xref:System.Activities.Statements.State>przerywał wykonywanie, gdy stan jest przenoszone do, przed jej wprowadzeniem zaplanowane działania lub wyzwalaczy.

### <a name="BKMK_ActivityDelegates"></a> Definiowanie oraz stosowanie ActivityDelegate obiektów w Projektancie

Działania w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] używane <xref:System.Activities.ActivityDelegate> obiekty do udostępnienia punktami wykonania, gdy inne części przepływu pracy można wchodzić w interakcje z wykonywania przepływu pracy, ale zazwyczaj przy użyciu tych punktów wykonywania wymagana ilość kodu. W tej wersji deweloperzy mogą zdefiniować i stosowanie delegowania działania, za pomocą projektanta przepływów pracy. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="BKMK_BuildTimeValidation"></a> Sprawdzanie poprawności w czasie kompilacji

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], błędy sprawdzania poprawności przepływu pracy nie traktowane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. Oznacza to, tworzenia przepływu pracy projektu może zakończyć się pomyślnie, nawet wtedy, gdy wystąpiły błędy sprawdzania poprawności przepływu pracy. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kompilacja nie powiedzie się, że błędy walidacji przepływu pracy.

### <a name="BKMK_DesignTimeValidation"></a> Sprawdzanie poprawności tła w czasie projektowania

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], przepływy pracy zostały zweryfikowane jako proces pierwszoplanowy, które potencjalnie mogą powodować zawieszanie interfejsu użytkownika podczas procesu weryfikacji złożone i czasochłonne. Teraz walidacji przepływu pracy odbywa się na wątku w tle, dzięki czemu interfejs użytkownika nie jest zablokowany.

### <a name="BKMK_ViewState"></a> Wyświetlanie stanu znajduje się w innej lokalizacji w plikach XAML

W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to wygodne, dla deweloperów, którzy chcą bezpośrednio odczytywać XAML lub napisać kod, aby usunąć informacje o stanie widoku. W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyświetlanie informacji o stanie w pliku XAML jest serializowana jako osobny element w pliku XAML. Deweloperzy można łatwo zlokalizować i edytować informacje o stanie widoku działania lub całkowicie usunąć stan widoku.

### <a name="BKMK_ExpressionExtensibility"></a> Wyrażenie rozszerzalności

W [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], firma Microsoft zapewnia sposób deweloperzy mogą tworzyć własne wyrażenie i środowisko, które można podłączyć do projektanta przepływów pracy tworzenia wyrażenia.

### <a name="BKMK_BackwardCompatRehostedDesigner"></a> Zoptymalizowany pod kątem w funkcji Workflow 4.5 w rehostowanym projektancie

Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje uwzględnione w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nie są włączone domyślnie w rehostowanym projektancie. To, aby upewnić się, że istniejące aplikacje korzystające z rehostowanym projektancie nie są uszkodzone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w rehostowanym projektancie, ustaw wartość <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> ".NET Framework 4.5" lub Ustaw poszczególne elementy członkowskie <xref:System.Activities.Presentation.DesignerConfigurationService> można włączać poszczególne funkcje.

## <a name="BKMK_NewWFModels"></a> Nowe modele projektowania przepływu pracy

Oprócz schemat blokowy i modele programowania sekwencyjnego przepływu pracy ta wersja zawiera przepływy pracy automatu stanów i usług przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu.

### <a name="BKMK_StateMachine"></a> Przepływy pracy automatu stanów

Przepływy pracy automatu stanów zostały wprowadzone w ramach programu .NET Framework 4, wersja 4.0.1 [programu Microsoft .NET Framework 4 platformy Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Ta aktualizacja zawierała kilka nowych klas i działań, które mogą deweloperom tworzenie przepływów pracy automatu stanów. Te klasy i działania zostały zaktualizowane w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizacje obejmują:

1. Możliwość ustawienia punktów przerwania na Stanach

2. Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy

3. Wsparcie tworzenia udostępnionych przejść wyzwalaczy

4. Działania używany do tworzenia przepływów pracy automatu stanów, w tym: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, i <xref:System.Activities.Statements.Transition>

Poniższy zrzut ekranu przedstawia przepływ pracy automatu stanu ukończenia od [Samouczek wprowadzający](getting-started-tutorial.md) kroku [jak: Tworzenie przepływu pracy automatu stanów](how-to-create-a-state-machine-workflow.md).

![Ukończono przepływ pracy automatu stanów](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")

Aby uzyskać więcej informacji na temat tworzenia przepływów pracy automatu stanów, zobacz [przepływów pracy automatu stanów](state-machine-workflows.md).

### <a name="BKMK_ContractFirst"></a> Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu

Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia deweloperom projektowanie najpierw kontrakt w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio automatycznie wygenerować szablon działania w przyborniku, reprezentujący każdej operacji. Działania te są następnie używane do tworzenia przepływu pracy, który implementuje operacje zdefiniowane przez umowę. Projektant przepływu pracy zostanie przeprowadzona Weryfikacja usługi przepływu pracy, aby upewnić się, czy te operacje są wykonywane, i podpis przepływu pracy odpowiada sygnatury Umowa. Deweloper można również skojarzyć usługi przepływu pracy z kolekcją zaimplementowane kontrakty. Aby uzyskać więcej informacji na temat opracowywania rozwiązań usługi przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu, zobacz [jak: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
