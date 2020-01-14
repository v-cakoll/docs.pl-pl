---
title: Co nowego w programie Windows Workflow Foundation na platformie .NET 4.5
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: b14f18dce64bc5738f3d3c6af11d6d6224764486
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937889"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Co nowego w programie Windows Workflow Foundation na platformie .NET 4.5

Windows Workflow Foundation (WF) w .NET Framework 4,5 wprowadza wiele nowych funkcji, takich jak nowe działania, możliwości projektanta i modele tworzenia przepływu pracy. Wiele, ale nie wszystkie, nowych funkcji przepływu pracy wprowadzonych w .NET Framework 4,5 są obsługiwane w ponownie hostowanym Projektancie przepływu pracy. Aby uzyskać więcej informacji o nowych funkcjach, które są obsługiwane, zobacz [Obsługa nowych funkcji programu Workflow Foundation 4,5 w Projektant przepływu pracy](wf-features-in-the-rehosted-workflow-designer.md)przewidzianych do przeszukania. Aby uzyskać więcej informacji na temat migrowania aplikacji przepływu pracy .NET 3,0 i .NET 3,5 do korzystania z najnowszej wersji, zobacz [wskazówki dotyczące migracji](migration-guidance.md). Ten temat zawiera omówienie nowych funkcji przepływu pracy wprowadzonych w .NET Framework 4,5.

> [!WARNING]
> Nowe funkcje Windows Workflow Foundation wprowadzone w .NET Framework 4,5 nie są dostępne dla projektów przeznaczonych dla wcześniejszych wersji platformy. Jeśli projekt przeznaczony dla .NET Framework 4,5 zostanie odtworzony w poprzedniej wersji środowiska, mogą wystąpić pewne problemy.
>
> - C#wyrażenia zostaną zastąpione w Projektancie z **wartością komunikatu ustawioną w kodzie XAML**.
> - Wystąpi wiele błędów kompilacji, w tym następujący błąd.
>
> **Format pliku nie jest zgodny z bieżącą platformą docelową. Aby przekonwertować format pliku, należy jawnie zapisać plik. Ten komunikat o błędzie zostanie odsunięty po zapisaniu pliku i ponownym otwarciu projektanta.**

## <a name="BKMK_Versioning"></a>Wersja przepływu pracy

W .NET Framework 4,5 wprowadzono kilka nowych funkcji obsługi wersji na podstawie nowej klasy <xref:System.Activities.WorkflowIdentity>. <xref:System.Activities.WorkflowIdentity> zapewnia autorom aplikacji przepływu pracy mechanizm mapowania utrwalonego wystąpienia przepływu pracy z jego definicją.

- Deweloperzy korzystający z usługi <xref:System.Activities.WorkflowApplication> hosting mogą używać <xref:System.Activities.WorkflowIdentity>, aby umożliwić hostowanie wielu wersji przepływu pracy obok siebie. Wystąpienia utrwalonych przepływów pracy mogą być ładowane przy użyciu nowej klasy <xref:System.Activities.WorkflowApplicationInstance>, a następnie <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> mogą być używane przez hosta w celu zapewnienia prawidłowej wersji definicji przepływu pracy podczas tworzenia wystąpienia <xref:System.Activities.WorkflowApplication>. Aby uzyskać więcej informacji, zobacz [Korzystanie z właściwości WorkflowIdentity i przechowywanie wersji](using-workflowidentity-and-versioning.md) oraz [instrukcje: hostowanie wielu wersji przepływu pracy obok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)siebie.

- <xref:System.ServiceModel.WorkflowServiceHost> jest teraz hostem z obsługą wiele wersji. Po wdrożeniu nowej wersji usługi przepływu pracy nowe wystąpienia są tworzone przy użyciu nowej usługi, ale istniejące wystąpienia są gotowe do użycia w poprzedniej wersji. Aby uzyskać więcej informacji, zobacz [znajdujące się obok siebie wersje w obszarze WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Wprowadzono aktualizację dynamiczną, która udostępnia mechanizm aktualizowania definicji utrwalonego wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [Aktualizacja dynamiczna](dynamic-update.md) i [instrukcje: aktualizowanie definicji uruchomionego wystąpienia przepływu pracy](how-to-update-the-definition-of-a-running-workflow-instance.md).

- Skrypt bazy danych SqlWorkflowInstanceStoreSchemaUpgrade. SQL jest dostarczany w celu uaktualnienia baz danych trwałości utworzonych przy użyciu skryptów bazy danych .NET Framework 4. Ten skrypt aktualizuje .NET Framework 4 trwałości baz danych w celu obsługi nowych możliwości przechowywania wersji wprowadzonych w .NET Framework 4,5. Wystąpienia utrwalonych przepływów pracy w bazie danych mają domyślne wartości wersji i mogą uczestniczyć w wykonywaniu równoczesnym i aktualizacji dynamicznej. Aby uzyskać więcej informacji, zobacz [uaktualnianie baz danych trwałości .NET Framework 4 w celu zapewnienia obsługi wersji przepływu pracy](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="BKMK_NewActivities"></a>Demonstracj

Wbudowana Biblioteka działań zawiera nowe działania i nowe funkcje dla istniejących działań.

### <a name="BKMK_NoPersistScope"></a>Zakres noutrwalania

<xref:System.Activities.Statements.NoPersistScope> to nowe działanie kontenera, które uniemożliwia utrwalanie przepływu pracy podczas wykonywania działań podrzędnych NoPersistScope. Jest to przydatne w scenariuszach, w których przepływ pracy ma być trwały, na przykład wtedy, gdy przepływ pracy używa zasobów specyficznych dla maszyn, takich jak dojścia do plików lub podczas transakcji bazy danych. Wcześniej, aby zapobiec sytuacji, w której wystąpił błąd podczas wykonywania działania, wymagana jest niestandardowa <xref:System.Activities.NativeActivity>, która użyła <xref:System.Activities.NoPersistHandle>.

### <a name="BKMK_NewFlowchartCapabilities"></a>Nowe możliwości schematu blokowego

Schematy blokowe są aktualizowane dla .NET Framework 4,5 i mają następujące nowe możliwości:

- Właściwość `DisplayName` działania <xref:System.Activities.Statements.FlowSwitch%601> lub <xref:System.Activities.Statements.FlowDecision> można edytować. Dzięki temu Projektant działań będzie wyświetlał więcej informacji o przeznaczeniu działania.

- Schematy blokowe mają nową właściwość o nazwie <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; wartość domyślna tej właściwości to `False`. Jeśli ta właściwość ma wartość `True`, niepołączone węzły schematu blokowego spowodują błędy walidacji.

## <a name="support-for-partial-trust"></a>Obsługa częściowego zaufania

Przepływy pracy w .NET Framework 4 wymagały w pełni zaufanej domeny aplikacji. W .NET Framework 4,5 przepływy pracy mogą działać w środowisku częściowej relacji zaufania. W środowisku częściowej relacji zaufania można używać składników innych firm bez udzielania im pełnego dostępu do zasobów hosta. Niektóre zagadnienia dotyczące uruchamiania przepływów pracy w częściowej relacji zaufania są następujące:

1. Używanie starszych składników (w tym reguł) zawartych w działaniu <xref:System.Activities.Statements.Interop> nie jest obsługiwane w ramach częściowej relacji zaufania.

2. Uruchomione przepływy pracy w częściowej relacji zaufania w <xref:System.ServiceModel.WorkflowServiceHost> nie są obsługiwane.

3. Utrzymywanie wyjątków w scenariuszu częściowego zaufania jest potencjalnym zagrożeniem bezpieczeństwa. Aby wyłączyć utrwalanie wyjątków, do projektu należy dodać rozszerzenie typu <xref:System.Activities.ExceptionPersistenceExtension>, aby zrezygnować z utrwalania wyjątków. Poniższy przykład kodu demonstruje, jak zaimplementować ten typ.

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

     Jeśli wyjątki nie mają być serializowane, należy się upewnić, że wyjątki są używane w <xref:System.Activities.Statements.NoPersistScope>.

4. Autorzy działań powinni przesłonić <xref:System.Activities.Activity.CacheMetadata%2A>, aby uniknąć, że środowisko uruchomieniowe przepływu pracy automatycznie wykonuje odbicie względem typu. Argumenty i działania podrzędne muszą mieć wartość różną od null, a <xref:System.Activities.ActivityMetadata.Bind%2A> muszą być wywoływane jawnie. Aby uzyskać więcej informacji na temat zastępowania <xref:System.Activities.Activity.CacheMetadata%2A>, zobacz [udostępnianie danych za pomocą wywołaniem metody CacheMetadata](exposing-data-with-cachemetadata.md). Ponadto wystąpienia argumentów typu `internal` lub **Private** muszą być jawnie utworzone w <xref:System.Activities.Activity.CacheMetadata%2A>, aby uniknąć ich tworzenia przez odbicie.

5. Typy nie będą używać <xref:System.Runtime.Serialization.ISerializable> ani <xref:System.SerializableAttribute> do serializacji; typy, które mają być serializowane, muszą obsługiwać <xref:System.Runtime.Serialization.DataContractSerializer>.

6. Wyrażenia, które używają <xref:System.Activities.Expressions.LambdaValue%601> wymagają <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>i w ten sposób nie będą działały w ramach częściowej relacji zaufania. Przepływy pracy używające <xref:System.Activities.Expressions.LambdaValue%601> powinny zastąpić te wyrażenia działaniami, które pochodzą z <xref:System.Activities.CodeActivity%601>. .

7. Wyrażenia nie mogą być kompilowane przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler> lub kompilatora hostowanego Visual Basic w częściowej relacji zaufania, ale można uruchomić wcześniej skompilowane wyrażenia.

8. Jednego zestawu, który używa [przezroczystości poziomu 2](https://aka.ms/Level2Transparency) , nie można używać w .NET Framework 4, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w trybie pełnego zaufania i [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w częściowej relacji zaufania.

## <a name="BKMK_NewDesignerCapabilites"></a>Nowe możliwości projektanta

### <a name="BKMK_DesignerSearch"></a>Wyszukiwanie projektanta

Aby zapewnić większą łatwość zarządzania przepływami pracy, przepływy pracy mogą teraz być przeszukiwane według słowa kluczowego. Ta funkcja jest dostępna tylko w programie Visual Studio; Ta funkcja jest niedostępna w projektancie przehostowanym. Dostępne są dwa rodzaje wyszukiwania:

- Szybkie wyszukiwanie, zainicjowane przy użyciu **kombinacji klawiszy Ctrl + F** lub **Edytuj**, **Znajdź i Zamień**, **szybkie znajdowanie**.

- Znajdź w plikach, zainicjowane za pomocą **klawiszy Ctrl + Shift + F** lub **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**.

Pamiętaj, że zastąpienie nie jest obsługiwane.

#### <a name="BKMK_QuickFind"></a>Szybkie wyszukiwanie

Słowa kluczowe przeszukiwane w przepływach pracy będą zgodne z następującymi elementami projektanta:

- Właściwości obiektów <xref:System.Activities.Activity>, obiektów <xref:System.Activities.Statements.FlowNode>, obiektów <xref:System.Activities.Statements.State>, obiektów <xref:System.Activities.Statements.Transition> i innych niestandardowych elementów sterowania przepływem.

- Zmienne

- Argumenty

- {1&gt;Wyrażenia&lt;1}

Szybkie wyszukiwanie jest wykonywane w drzewie <xref:System.Activities.Presentation.Model.ModelItem> projektanta. Szybkie wyszukiwanie nie będzie lokalizować przestrzeni nazw zaimportowanych w definicji przepływu pracy.

#### <a name="BKMK_FindInFiles"></a>Znajdź w plikach

Słowa kluczowe przeszukiwane w przepływach pracy będą zgodne z rzeczywistą zawartością plików przepływu pracy. Wyniki wyszukiwania zostaną wyświetlone w okienku znajdź widok wyników w programie Visual Studio. Dwukrotne kliknięcie elementu wyników spowoduje przejście do działania, które zawiera dopasowanie w Projektancie przepływu pracy.

### <a name="BKMK_VariableDeleteContextMenu"></a>Usuń element menu kontekstowego w programie Variable i Konstruktor argumentów

W .NET Framework 4 zmienne i argumenty można usunąć tylko w projektancie przy użyciu klawiatury. Począwszy od .NET Framework 4,5, zmienne i argumenty można usuwać za pomocą menu kontekstowego.

Poniższy zrzut ekranu przedstawia menu kontekstowe dla zmiennej i argumentu projektanta.

![Menu kontekstowe projektanta zmiennych i argumentów](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="BKMK_AutoSurround"></a>Funkcja autoprzestrzenny z sekwencją

Ponieważ przepływ pracy lub niektóre działania kontenera (takie jak <xref:System.Activities.Statements.NoPersistScope>) mogą zawierać tylko jedno działanie dotyczące treści, dodanie drugiego działania wymagało od dewelopera usunięcia pierwszego działania, dodania działania <xref:System.Activities.Statements.Sequence>, a następnie dodania obu działań do działania sekwencji. Począwszy od .NET Framework 4,5, podczas dodawania drugiego działania do powierzchni projektanta, działanie `Sequence` zostanie automatycznie utworzone w celu zawinięcia obu działań.

Poniższy zrzut ekranu przedstawia działanie `WriteLine` w `Body` `NoPersistScope`.

![Działanie WriteLine w treści działania NoPersistScope.](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

Poniższy zrzut ekranu przedstawia działanie automatycznie utworzone `Sequence` w `Body`, gdy drugi `WriteLine` zostanie porzucony poniżej pierwszego.

![Automatycznie utworzona sekwencja w treści NoPersistScope.](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="BKMK_PanMode"></a>Tryb kadrowania

Aby łatwiej nawigować do dużego przepływu pracy w projektancie, można włączyć tryb kadrowania, co umożliwia deweloperom kliknięcie i przeciągnięcie go w celu przeniesienia widocznej części przepływu pracy zamiast używania pasków przewijania. Przycisk służący do uaktywniania trybu kadrowania znajduje się w prawym dolnym rogu projektanta.

Poniższy zrzut ekranu przedstawia przycisk przesuń znajdujący się w prawym dolnym rogu projektanta przepływu pracy.

![Przycisk kadrowania wyróżniony w Projektancie przepływu pracy.](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

Do kadrowania projektanta przepływu pracy można również użyć środkowego przycisku myszy lub paska spacji.

### <a name="BKMK_MultiSelect"></a>Wybór wieloznaczny

Jednocześnie można wybrać wiele działań, przeciągając wokół nich prostokąt (gdy tryb panoramowania nie jest włączony) lub przytrzymując klawisz Ctrl i klikając żądane działania po jednym.

W projektancie można również przeciągać i upuszczać wiele opcji, a także korzystać z menu kontekstowego.

### <a name="BKMK_DocumentOutline"></a>widok konspektu elementów przepływu pracy

W celu ułatwienia nawigacji hierarchicznych przepływów pracy składniki przepływu pracy są wyświetlane w widoku konspektu w stylu drzewa. Widok konspektu jest wyświetlany w widoku **konspektu dokumentu** . Aby otworzyć ten widok, w górnym menu wybierz pozycję **Widok**, **inne okna**, **Konspekt dokumentu**lub naciśnij klawisze Ctrl W, U. Kliknięcie węzła w widoku konspektu spowoduje przejście do odpowiedniego działania w Projektancie przepływu pracy, a widok konspektu zostanie zaktualizowany w celu wyświetlenia działań wybranych w projektancie.

Poniższy zrzut ekranu ukończonego przepływu pracy w [samouczku wprowadzenie](getting-started-tutorial.md) przedstawia widok konspektu z sekwencyjnym przepływem pracy.

![Zrzut ekranu przedstawiający widok konspektu z sekwencyjnym przepływem pracy w programie Visual Studio.](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="BKMK_CSharpExpressions"></a>C# Wyrażenia

Przed .NET Framework 4,5 wszystkie wyrażenia w przepływach pracy mogą być zapisywane tylko w Visual Basic. W .NET Framework 4,5 wyrażenia Visual Basic są używane tylko dla projektów utworzonych przy użyciu Visual Basic. Projekty C# wizualizacji teraz C# używają wyrażeń. W pełni funkcjonalny C# Edytor wyrażeń udostępnia funkcje, takie jak wyróżnianie gramatyki i technologia IntelliSense. C#projekty przepływu pracy utworzone w poprzednich wersjach, które używają wyrażeń Visual Basic, nadal będą działały.

C#wyrażenia są weryfikowane w czasie projektowania. Błędy w C# wyrażeniach będą oznaczone czerwoną linią falistą.

Aby uzyskać więcej informacji C# na temat wyrażeń, zobacz [ C# Expressions](csharp-expressions.md).

### <a name="BKMK_Visibility"></a>Większa kontrola widoczności paska powłoki i elementów nagłówka

W nieobsługiwanym projektancie niektóre standardowe kontrolki interfejsu użytkownika mogą nie mieć znaczenia dla danego przepływu pracy i mogą być wyłączone. W .NET Framework 4 to dostosowanie jest obsługiwane tylko przez pasek powłoki w dolnej części projektanta. W .NET Framework 4,5 widoczność elementów nagłówka powłoki w górnej części projektanta może być dostosowywana przez ustawienie <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> z odpowiednią wartością <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility>.

### <a name="BKMK_AutoConnect"></a>AutoConnect i autoinsert w schemacie blokowym i przepływie pracy automatu Stanów

W .NET Framework 4 połączenia między węzłami w przepływie pracy Flowchart musiały zostać dodane ręcznie. W .NET Framework 4,5, schemat blokowy i węzły automatu Stanów mają punkty AutoConnect, które stają się widoczne po przeciągnięciu działania z przybornika na powierzchnię projektanta. Porzucenie działania jednego z tych punktów powoduje automatyczne dodanie działania wraz z wymaganym połączeniem.

Poniższy zrzut ekranu przedstawia punkty załącznika, które stają się widoczne po przeciągnięciu działania z przybornika.

![Węzeł początkowy Flowchart przedstawiający punkty AutoConnect](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

Działania można również przeciągać do połączeń między węzłami i Stanami schematu blokowego, aby wstawić węzeł między dwoma innymi węzłami. Poniższy zrzut ekranu pokazuje wyróżnioną linię łączącą, w której działania mogą być przeciągane z przybornika i upuszczane.

![Wstawianie dojścia do usuwania działań](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="BKMK_Annotations"></a>Adnotacje projektanta

Aby ułatwić tworzenie większych przepływów pracy, Projektant obsługuje teraz Dodawanie adnotacji, aby ułatwić śledzenie procesu projektowania. Adnotację można dodać do działań, Stanów, węzłów schematu blokowego, zmiennych i argumentów. Poniższy zrzut ekranu przedstawia menu kontekstowe używane do dodawania adnotacji do projektanta.

![Zrzut ekranu przedstawiający menu umożliwiające dodawanie adnotacji.](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>Stany debugowania

W .NET Framework 4 elementy niedziałające nie mogą obsługiwać punktów przerwania debugowania, ponieważ nie były one jednostkami wykonywania. Ta wersja udostępnia mechanizm dodawania punktów przerwania do <xref:System.Activities.Statements.State> obiektów. Gdy punkt przerwania jest ustawiony na <xref:System.Activities.Statements.State>, wykonanie będzie przerywane, gdy stan zostanie przeniesiony do, przed zaplanowaniem działania wejścia lub wyzwalaczy.

### <a name="BKMK_ActivityDelegates"></a>Definiowanie i używanie obiektów ActivityDelegate w projektancie

Działania w .NET Framework 4 używane <xref:System.Activities.ActivityDelegate> obiektów do udostępniania punktów wykonywania, w których inne części przepływu pracy mogą współdziałać z wykonywaniem przepływu pracy, ale używanie tych punktów wykonania zwykle wymagało uczciwej ilości kodu. W tej wersji deweloperzy mogą definiować i korzystać z delegatów działań za pomocą projektanta przepływu pracy. Aby uzyskać więcej informacji, zobacz [jak: definiować i korzystać z delegatów działań w Projektant przepływu pracy](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="BKMK_BuildTimeValidation"></a>Weryfikacja czasu kompilacji

W .NET Framework 4 błędy walidacji przepływu pracy nie były zliczane jako błędy kompilacji podczas kompilacji projektu przepływu pracy. W ten sposób Kompilowanie projektu przepływu pracy może się powieść, nawet jeśli wystąpiły błędy sprawdzania poprawności przepływu pracy. W .NET Framework 4,5 błędy walidacji przepływu pracy powodują niepowodzenie kompilacji.

### <a name="BKMK_DesignTimeValidation"></a>Walidacja w tle w czasie projektowania

W .NET Framework 4 przepływy pracy zostały zweryfikowane jako proces pierwszego planu, który może potencjalnie blokować interfejs użytkownika w trakcie skomplikowanych lub czasochłonnych procesów weryfikacji. Sprawdzanie poprawności przepływu pracy odbywa się teraz w wątku w tle, dzięki czemu interfejs użytkownika nie jest blokowany.

### <a name="BKMK_ViewState"></a>Stan widoku znajdujący się w oddzielnej lokalizacji w plikach XAML

W .NET Framework 4 Informacje o stanie widoku dla przepływu pracy są przechowywane w pliku XAML w wielu różnych lokalizacjach. Jest to niewygodne dla deweloperów, którzy chcą bezpośrednio czytać dane XAML, lub napisać kod, aby usunąć informacje o stanie widoku. W .NET Framework 4,5 informacje o stanie widoku w pliku XAML są serializowane jako osobny element w pliku XAML. Deweloperzy mogą łatwo lokalizować i edytować informacje o stanie widoku działania lub całkowicie usunąć stan widoku.

### <a name="BKMK_ExpressionExtensibility"></a>Rozszerzalność wyrażeń

W .NET Framework 4,5 zapewniamy deweloperom możliwość tworzenia własnych wyrażeń i tworzenia wyrażeń, które mogą być podłączone do projektanta przepływu pracy.

### <a name="BKMK_BackwardCompatRehostedDesigner"></a>Możliwość uczestnictwa w funkcjach przepływu pracy w programie Workflow 4,5 w projektancie przeszukanym

Aby zachować zgodność z poprzednimi wersjami, niektóre nowe funkcje zawarte w .NET Framework 4,5 nie są domyślnie włączone w projektancie przeszukanym. Jest to konieczne, aby upewnić się, że istniejące aplikacje korzystające z przeszukanego projektanta nie są uszkodzone przez aktualizację do najnowszej wersji. Aby włączyć nowe funkcje w projektancie ponownie hostowanym, należy ustawić <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> na ".NET Framework 4,5" lub ustawić poszczególnych członków <xref:System.Activities.Presentation.DesignerConfigurationService>, aby włączyć poszczególne funkcje.

## <a name="BKMK_NewWFModels"></a>Nowe modele projektowania przepływu pracy

Poza schematem blokowym i modelami programowania sekwencyjnego przepływu pracy ta wersja obejmuje przepływy pracy automatu stanów i usługi przepływu pracy pierwszego kontraktu.

### <a name="BKMK_StateMachine"></a>Przepływy pracy automatu Stanów

Przepływy pracy automatu Stanów zostały wprowadzone w ramach .NET Framework 4 w wersji 4.0.1 na [platformie Microsoft .NET Framework 4 Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1). Ta aktualizacja zawiera kilka nowych klas i działań, które pozwalają deweloperom tworzyć przepływy pracy automatu Stanów. Te klasy i działania zostały zaktualizowane dla .NET Framework 4,5. Aktualizacje obejmują:

1. Możliwość ustawiania punktów przerwania na Stanach

2. Możliwość kopiowania i wklejania przejść w Projektancie przepływu pracy

3. Obsługa tworzenia przejść wyzwalaczy udostępnionych przez projektanta

4. Działania używane do tworzenia przepływów pracy automatu Stanów, w tym: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>i <xref:System.Activities.Statements.Transition>

Poniższy zrzut ekranu przedstawia ukończony przepływ pracy automatu Stanów z [samouczka Wprowadzenie](getting-started-tutorial.md) krok [: tworzenie przepływu pracy automatu Stanów](how-to-create-a-state-machine-workflow.md).

![Ilustracja przedstawiająca ukończony przepływ pracy automatu Stanów.](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

Aby uzyskać więcej informacji o tworzeniu przepływów pracy automatu Stanów, zobacz [przepływy pracy automatu Stanów](state-machine-workflows.md).

### <a name="BKMK_ContractFirst"></a>Programowanie — pierwszy przepływ pracy

Narzędzie do tworzenia przepływów pracy pierwszego kontraktu pozwala deweloperowi na zaprojektowanie kontraktu w kodzie, a następnie za pomocą kilku kliknięć w programie Visual Studio, automatyczne wygenerowanie szablonu działania w przyborniku reprezentującym każdą operację. Te działania są następnie używane do tworzenia przepływu pracy, który implementuje operacje zdefiniowane przez umowę. Projektant przepływu pracy sprawdza poprawność usługi przepływu pracy, aby upewnić się, że te operacje są zaimplementowane, a sygnatura przepływu pracy jest zgodna z podpisem kontraktu. Deweloper może również skojarzyć usługę przepływu pracy z kolekcją wdrożonych kontraktów. Aby uzyskać więcej informacji na temat tworzenia usługi przepływu pracy w pierwszej kolejności, zobacz [jak: Tworzenie usługi przepływu pracy korzystającej z istniejącego kontraktu usługi](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
