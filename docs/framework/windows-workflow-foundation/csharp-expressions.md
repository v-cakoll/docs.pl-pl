---
title: Wyrażenia języka C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: d1728758a4f1af76c2d08695a83c0f9acc3dde3e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140093"
---
# <a name="c-expressions"></a>Wyrażenia języka C#
Począwszy od .NET Framework 4,5, C# wyrażenia są obsługiwane w Windows Workflow Foundation (WF). Nowe C# projekty przepływu pracy utworzone w programie Visual Studio 2012, które są C# przeznaczone dla wyrażeń use .NET Framework 4,5 i Visual Basic projects używają wyrażeń Visual Basic. Istniejące projekty przepływu pracy w .NET Framework 4, które używają wyrażeń Visual Basic, można migrować do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] niezależnie od języka projektu i są obsługiwane. Ten temat zawiera omówienie C# wyrażeń w [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Używanie C# wyrażeń w przepływach pracy

- [Używanie C# wyrażeń w Projektant przepływu pracy](csharp-expressions.md#WFDesigner)

  - [Zgodność z poprzednimi wersjami](csharp-expressions.md#BackwardCompat)

- [Używanie C# wyrażeń w przepływach pracy w kodzie](csharp-expressions.md#CodeWorkflows)

- [Używanie C# wyrażeń w przepływach pracy XAML](csharp-expressions.md#XamlWorkflows)

  - [Skompilowany kod XAML](csharp-expressions.md#CompiledXaml)

  - [Luźny kod XAML](csharp-expressions.md#LooseXaml)

- [Używanie C# wyrażeń w usługach xamlx Workflow Services](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a>Używanie C# wyrażeń w Projektant przepływu pracy

Począwszy od .NET Framework 4,5, C# wyrażenia są obsługiwane w Windows Workflow Foundation (WF). C#projekty przepływu pracy utworzone w programie Visual Studio 2012, które są C# przeznaczone dla .NET Framework 4,5 używać wyrażeń, podczas Visual Basic projekty przepływu pracy używają wyrażeń Visual Basic. Aby określić żądane C# wyrażenie, wpisz je w polu oznaczonym etykietą **wprowadź C# wyrażenie**. Etykieta jest wyświetlana w oknie właściwości, gdy działanie jest wybrane w projektancie, lub na działaniu w Projektancie przepływu pracy. W poniższym przykładzie dwa `WriteLine` działania są zawarte w `Sequence` wewnątrz `NoPersistScope`.

![Zrzut ekranu pokazujący automatycznie utworzone działanie sekwencji.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> C#wyrażenia są obsługiwane tylko w programie Visual Studio i nie są obsługiwane w rehostowanym Projektancie przepływu pracy. Aby uzyskać więcej informacji na temat nowych funkcji WF45 obsługiwanych w projektancie w dalszym zakresie, zobacz temat [Obsługa nowych funkcji programu Workflow Foundation 4,5 w Projektant przepływu pracy](wf-features-in-the-rehosted-workflow-designer.md)przeprowadzonej przez Ciebie.

#### <a name="BackwardCompat"></a>Zgodność z poprzednimi wersjami

Obsługiwane są wyrażenia Visual Basic w istniejących C# projektach .NET Framework 4 przepływach pracy, które zostały poddane migracji do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Gdy wyrażenia Visual Basic są wyświetlane w Projektancie przepływu pracy, tekst istniejącego wyrażenia Visual Basic zostanie zastąpiony **wartością wartość została ustawiona w języku XAML**, chyba że wyrażenie Visual Basic jest prawidłową C# składnią. Jeśli wyrażenie Visual Basic jest prawidłową C# składnią, wyświetlane jest wyrażenie. Aby zaktualizować wyrażenia Visual Basic do C#, można je edytować w Projektancie przepływu pracy i określić równoważne C# wyrażenie. Nie jest wymagane aktualizowanie wyrażeń Visual Basic do C#, ale po zaktualizowaniu wyrażeń w Projektancie przepływu pracy są one konwertowane na C# i nie można ich przywrócić do Visual Basic.

### <a name="CodeWorkflows"></a>Używanie C# wyrażeń w przepływach pracy w kodzie

C#wyrażenia są obsługiwane w przepływach pracy opartych na kodzie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], ale zanim przepływ pracy C# może być wywoływany, wyrażenia muszą być kompilowane przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Autorzy przepływu pracy mogą używać `CSharpValue` do reprezentowania wartości r wyrażenia i `CSharpReference` do reprezentowania l-wartości wyrażenia. W poniższym przykładzie przepływ pracy jest tworzony przy użyciu działania `Assign` i działania `WriteLine` zawartego w działaniu `Sequence`. `CSharpReference` jest określony dla argumentu `To` `Assign`i reprezentuje wartość l wyrażenia. `CSharpValue` jest określony dla argumentu `Value` `Assign`oraz dla argumentu `Text` `WriteLine`i reprezentuje wartość r dla tych dwóch wyrażeń.

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

Po skonstruowaniu przepływu pracy C# wyrażenia są kompilowane przez wywołanie metody pomocnika `CompileExpressions`, a następnie wywołania przepływu pracy. Poniższy przykład jest metodą `CompileExpressions`.

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
> Jeśli C# wyrażenia nie są kompilowane, zostanie zgłoszony <xref:System.NotSupportedException>, gdy przepływ pracy zostanie wywołany z komunikatem podobnym do następującego: `Expression Activity type 'CSharpValue`1 "wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany.

Jeśli przepływ pracy oparty na kodzie niestandardowym używa `DynamicActivity`, wówczas wymagane są pewne zmiany metody `CompileExpressions`, jak pokazano w poniższym przykładzie kodu.

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

Istnieje kilka różnic w Przeciążenie `CompileExpressions`, które kompiluje C# wyrażenia w działaniu dynamicznym.

- Parametr do `CompileExpressions` jest `DynamicActivity`.

- Nazwa typu i przestrzeń nazw są pobierane przy użyciu właściwości `DynamicActivity.Name`.

- `TextExpressionCompilerSettings.ForImplementation` jest ustawiony na `true`.

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` jest wywoływana zamiast `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

Aby uzyskać więcej informacji na temat pracy z wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu własnego kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a>Używanie C# wyrażeń w przepływach pracy XAML

C#wyrażenia są obsługiwane w przepływach pracy XAML. Skompilowane przepływy pracy XAML są kompilowane w typie i luźne przepływy pracy XAML są ładowane przez środowisko uruchomieniowe i kompilowane w drzewie aktywności podczas wykonywania przepływu pracy.

- [Skompilowany kod XAML](csharp-expressions.md#CompiledXaml)

- [Luźny kod XAML](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a>Skompilowany kod XAML

C#wyrażenia są obsługiwane w skompilowanych przepływach pracy XAML, które są kompilowane do typu w C# ramach projektu przepływu pracy, który jest przeznaczony dla [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Skompilowany kod XAML to domyślny typ tworzenia przepływu pracy w programie Visual Studio i C# projekty przepływu pracy utworzone w programie Visual Studio, które C# są przeznaczone dla [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] używać wyrażeń.

#### <a name="LooseXaml"></a>Luźny kod XAML

C#wyrażenia są obsługiwane w luźnych przepływach pracy XAML. Program hosta przepływu pracy, który ładuje i wywołuje luźny przepływ pracy XAML, musi mieć wartość docelową [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musi być ustawiona na `true` (wartość domyślna to `false`). Aby ustawić <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> na `true`, należy utworzyć wystąpienie <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> z właściwością <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną na `true`i przekazać go jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Jeśli `CompileExpressions` nie jest ustawiona na `true`, zostanie zgłoszony <xref:System.NotSupportedException> z komunikatem podobnym do następującego: `Expression Activity type 'CSharpValue`1 ' wymaga kompilacji w celu uruchomienia.  Upewnij się, że przepływ pracy został skompilowany.

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Aby uzyskać więcej informacji na temat pracy z przepływami pracy XAML, zobacz [Serializowanie przepływów pracy i działań do i z języka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a>Używanie C# wyrażeń w usługach xamlx Workflow Services

C#wyrażenia są obsługiwane w usługach XAMLX Workflow Services. Gdy usługa przepływu pracy jest hostowana w usługach IIS lub nie jest wymagana żadna dodatkowa procedura, ale jeśli usługa przepływu pracy XAML jest samodzielna, C# wyrażenia muszą być kompilowane. Aby skompilować C# wyrażenia w ramach samodzielnej usługi przepływu pracy xamlx, najpierw Załaduj plik XAMLX do `WorkflowService`, a następnie przekaż `Body` `WorkflowService` do metody `CompileExpressions` opisanej w poprzednich [wyrażeniach using C# w sekcji przepływy kodu](csharp-expressions.md#CodeWorkflows) . W poniższym przykładzie jest załadowana usługa przepływu pracy XAMLX, C# wyrażenia są kompilowane, a następnie usługa przepływu pracy jest otwarta i oczekuje na żądania.

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

Jeśli C# wyrażenia nie są kompilowane, operacja `Open` powiedzie się, ale przepływ pracy zakończy się niepowodzeniem, gdy zostanie wywołany. Następująca `CompileExpressions` Metoda jest taka sama jak metoda z poprzednich [wyrażeń using C# w sekcji przepływy pracy kodu](csharp-expressions.md#CodeWorkflows) .

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
