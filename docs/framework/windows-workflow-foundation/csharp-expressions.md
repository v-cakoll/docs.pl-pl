---
title: Wyrażeń języka C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: 819f52c345983ca81794b8b1f33b6e2ba96b3922
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584171"
---
# <a name="c-expressions"></a>Wyrażeń języka C#
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka C# są obsługiwane w Windows Workflow Foundation (WF). Nowe projekty przepływu pracy C# utworzone w programie Visual Studio 2012 przeznaczonych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] korzystanie z wyrażeń języka C# i używać wyrażeń języka Visual Basic projektów przepływu pracy programu Visual Basic. Istniejące [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projektów przepływu pracy, które używają wyrażeń języka Visual Basic można przeprowadzić migrację do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] niezależnie od tego, w projekcie języka i są obsługiwane. Ten temat zawiera omówienie wyrażeń języka C# w [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Używanie wyrażeń języka C# w przepływach pracy

-   [W Projektancie przepływu pracy przy użyciu wyrażeń języka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)

    -   [Wstecznej zgodności](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)

-   [Używanie wyrażeń języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)

-   [Używanie wyrażeń języka C# w przepływach pracy XAML](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)

    -   [Skompilowany kod Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

    -   [Użył luźnego kodu Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

-   [Przy użyciu wyrażeń języka C# w XAMLX usług przepływu pracy](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)

###  <a name="WFDesigner"></a> W Projektancie przepływu pracy przy użyciu wyrażeń języka C#
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wyrażeń języka C# są obsługiwane w Windows Workflow Foundation (WF). Projekty przepływu pracy w języku C# utworzone w programie Visual Studio 2012 przeznaczonych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] używać wyrażeń języka C#, podczas gdy projekty przepływu pracy w języku Visual Basic używają wyrażeń języka Visual Basic. Aby określić żądaną wyrażenie języka C#, wpisz go w pole o nazwie **wprowadź wyrażenie języka C#**. Ta etykieta jest wyświetlana w oknie dialogowym właściwości po wybraniu działania w Projektancie lub działania w Projektancie przepływu pracy. W poniższym przykładzie dwa `WriteLine` działań są zawarte w `Sequence` wewnątrz `NoPersistScope`.

 ![Automatycznie utworzone działaniu sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")

> [!NOTE]
>  Wyrażeń języka C# są obsługiwane tylko w programie Visual Studio i nie są obsługiwane w Projektancie ponownie hostowanej przepływu pracy. Aby uzyskać więcej informacji o nowych funkcjach WF45 obsługiwane w Projektancie ponownie hostowanej, zobacz [obsługę nowych funkcji Workflow Foundation 4.5 w Rehostowanym projektancie przepływu pracy](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).

####  <a name="BackwardCompat"></a> Wstecznej zgodności
 Wyrażenia języka Visual Basic w istniejących [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projektów języka C# przepływu pracy, które zostały zmigrowane do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są obsługiwane. Patrząc wyrażeń języka Visual Basic w Projektancie przepływu pracy tekst istniejący wyrażenie języka Visual Basic jest zastępowany **wartość została ustawiona w XAML**, chyba że wyrażenie języka Visual Basic jest nieprawidłowa składnia języka C#. Jeśli wyrażenie języka Visual Basic jest nieprawidłowa składnia języka C#, wyrażenie jest wyświetlany. Aby zaktualizować wyrażeń języka Visual Basic do języka C#, można je edytować w Projektancie przepływów pracy i określić równoważne wyrażenie języka C#. Aktualizuj wyrażeń języka Visual Basic, C#, ale po wyrażenia są aktualizowane w Projektancie przepływu pracy są konwertowane do języka C# i nie można przywrócić w języku Visual Basic nie jest wymagany.

###  <a name="CodeWorkflows"></a> Używanie wyrażeń języka C# w przepływach pracy kodu
 Wyrażeń języka C# są obsługiwane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływy pracy oparte na kodzie, ale przed przepływ pracy może być wywoływany wyrażeń języka C# musi być skompilowana przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Przepływ pracy autorzy mogą używać `CSharpValue` do reprezentowania wartości wyrażenia i `CSharpReference` do reprezentowania l wartość wyrażenia. W poniższym przykładzie przepływ pracy jest tworzony z `Assign` działania i `WriteLine` działania zawarte w `Sequence` działania. A `CSharpReference` jest określona dla `To` argument `Assign`i reprezentuje l wartość wyrażenia. A `CSharpValue` jest określona dla `Value` argument `Assign`oraz `Text` argument `WriteLine`i reprezentuje r-wartości dla tych dwóch wyrażeń.

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

 Po przepływ pracy jest tworzony, wyrażeń języka C# są kompilowane przez wywołanie metody `CompileExpressions` zostanie wywołana metoda pomocnika, a następnie przepływ pracy. Poniższy przykład jest `CompileExpressions` metody.

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
>  Jeśli nie są kompilowane wyrażeń języka C#, <xref:System.NotSupportedException> jest zgłaszany, gdy przepływ pracy jest wywoływana z komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1' wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "

 Jeśli kod niestandardowy na podstawie przepływu pracy używa `DynamicActivity`, następnie niektóre zmiany `CompileExpressions` metody są wymagane, jak pokazano w poniższym przykładzie kodu.

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

 Istnieje kilka różnic w `CompileExpressions` przeciążenia, który kompiluje wyrażeń języka C# w działaniu dynamicznych.

-   Parametr `CompileExpressions` jest `DynamicActivity`.

-   Wpisz nazwę i przestrzeń nazw są pobierane przy użyciu `DynamicActivity.Name` właściwości.

-   `TextExpressionCompilerSettings.ForImplementation` ustawiono `true`.

-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` jest wywoływana zamiast `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

 Aby uzyskać więcej informacji na temat pracy z wyrażeniami w kodzie, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).

###  <a name="XamlWorkflows"></a> Używanie wyrażeń języka C# w przepływach pracy XAML
 Wyrażeń języka C# są obsługiwane w przepływach pracy XAML. Skompilowany XAML przepływach pracy są kompilowane do typu, a luźne XAML przepływach pracy są ładowane w czasie wykonywania i kompilowane do drzewa działań, podczas wykonywania przepływu pracy.

-   [Skompilowany kod Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

-   [Użył luźnego kodu Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

####  <a name="CompiledXaml"></a> Skompilowany kod Xaml
 Wyrażeń języka C# są obsługiwane w skompilowanych przepływów pracy XAML, które są kompilowane do typu w ramach projektu przepływu pracy C#, który jest przeznaczony dla [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Skompilowany XAML jest domyślny typ przepływu pracy tworzenia w programie Visual Studio, a projekty przepływu pracy w języku C# utworzony w Visual Studio, których platformą docelową [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] używać wyrażeń języka C#.

####  <a name="LooseXaml"></a> Użył luźnego kodu Xaml
 Wyrażeń języka C# są obsługiwane w luźne XAML przepływach pracy. Program hosta przepływu pracy, który ładuje, a następnie wywołuje luźne XAML przepływu pracy musi być przeznaczony [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], i <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musi być równa `true` (wartość domyślna to `false`). Można ustawić <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> do `true`, Utwórz <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> właściwością `true`i przekazać go jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Jeśli `CompileExpressions` nie jest ustawiony na `true`, <xref:System.NotSupportedException> zostanie zwrócony komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1' wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 Aby uzyskać więcej informacji na temat pracy z przepływami pracy XAML, zobacz [serializowanie przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).

###  <a name="WFServices"></a> Przy użyciu wyrażeń języka C# w XAMLX usług przepływu pracy
 Wyrażeń języka C# są obsługiwane w XAMLX usług przepływu pracy. Gdy usługi przepływu pracy znajduje się w usługach IIS i WAS, a następnie żadne dodatkowe kroki są wymagane, ale Self-Hosted usługi przepływu pracy XAML, muszą być skompilowane wyrażeń języka C#. Aby skompilować wyrażenia języka C# samodzielnie hostowanej usługi przepływu pracy XAMLX, najpierw załadować pliku XAMLX do `WorkflowService`, a następnie przekaż `Body` z `WorkflowService` do `CompileExpressions` metody opisanej w poprzednim [przy użyciu języka C# wyrażenia w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji. W poniższym przykładzie XAMLX usługi przepływu pracy jest ładowany, wyrażeń języka C# są kompilowane, a następnie usługi przepływu pracy jest otwarty i czeka na żądania.

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

 Jeśli nie są kompilowane wyrażeń języka C#, `Open` operacja kończy się powodzeniem, ale przepływ pracy zakończy się niepowodzeniem, gdy jest wywoływana. Następujące `CompileExpressions` metody jest taka sama jak metoda z poprzedniego [wyrażeń przy użyciu języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji.

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
