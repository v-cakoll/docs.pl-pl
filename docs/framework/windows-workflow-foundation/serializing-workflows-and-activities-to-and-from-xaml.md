---
title: Serializowanie przepływów pracy i działań do i z plików XAML
description: Ten artykuł zawiera omówienie serializowania definicji przepływu pracy i pracy z definicjami przepływu pracy XAML w programie Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421348"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="2258a-103">Serializowanie przepływów pracy i działań do i z języka XAML</span><span class="sxs-lookup"><span data-stu-id="2258a-103">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="2258a-104">Oprócz kompilowania do typów, które są zawarte w zestawach, definicje przepływu pracy mogą być również serializowane do języka XAML.</span><span class="sxs-lookup"><span data-stu-id="2258a-104">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="2258a-105">Te serializowane definicje można ponownie załadować do edycji lub inspekcji, przekazywać do systemu kompilacji dla kompilacji lub ładowane i wywoływane.</span><span class="sxs-lookup"><span data-stu-id="2258a-105">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="2258a-106">Ten temat zawiera omówienie serializowania definicji przepływu pracy i pracy z definicjami przepływu pracy XAML.</span><span class="sxs-lookup"><span data-stu-id="2258a-106">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="2258a-107">Korzystanie z definicji przepływu pracy XAML</span><span class="sxs-lookup"><span data-stu-id="2258a-107">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="2258a-108">Aby utworzyć definicję przepływu pracy dla serializacji, <xref:System.Activities.ActivityBuilder> używana jest Klasa.</span><span class="sxs-lookup"><span data-stu-id="2258a-108">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="2258a-109">Tworzenie programu <xref:System.Activities.ActivityBuilder> jest bardzo podobne do tworzenia <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="2258a-109">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="2258a-110">Wszystkie żądane argumenty są określone i są konfigurowane działania, które stanowią zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2258a-110">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="2258a-111">W poniższym przykładzie `Add` jest tworzone działanie, które przyjmuje dwa argumenty wejściowe, dodaje je razem i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="2258a-111">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="2258a-112">Ponieważ to działanie zwraca wynik, <xref:System.Activities.ActivityBuilder%601> używana jest Klasa generyczna.</span><span class="sxs-lookup"><span data-stu-id="2258a-112">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="2258a-113">Każde <xref:System.Activities.DynamicActivityProperty> wystąpienie reprezentuje jeden z argumentów wejściowych dla przepływu pracy, a <xref:System.Activities.ActivityBuilder.Implementation%2A> zawiera działania, które tworzą logikę przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2258a-113">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="2258a-114">Należy zauważyć, że wyrażenia r-Value w tym przykładzie są Visual Basic Expressions.</span><span class="sxs-lookup"><span data-stu-id="2258a-114">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="2258a-115">Wyrażenia lambda nie można serializować do języka XAML, chyba że <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> jest używany.</span><span class="sxs-lookup"><span data-stu-id="2258a-115">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="2258a-116">Jeśli serializowane przepływy pracy mają być otwierane lub edytowane w Projektancie przepływu pracy, należy użyć wyrażeń Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2258a-116">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="2258a-117">Aby uzyskać więcej informacji, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md)bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="2258a-117">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="2258a-118">Aby serializować definicję przepływu pracy reprezentowanego przez <xref:System.Activities.ActivityBuilder> wystąpienie do języka XAML, użyj polecenia <xref:System.Activities.XamlIntegration.ActivityXamlServices> do utworzenia <xref:System.Xaml.XamlWriter> , a następnie użyj polecenia, <xref:System.Xaml.XamlServices> Aby serializować definicję przepływu pracy przy użyciu <xref:System.Xaml.XamlWriter> .</span><span class="sxs-lookup"><span data-stu-id="2258a-118">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="2258a-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices>ma metody mapowania <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML oraz ładowania przepływów pracy XAML i zwracania <xref:System.Activities.DynamicActivity> , które mogą być wywoływane.</span><span class="sxs-lookup"><span data-stu-id="2258a-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="2258a-120">W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienie z poprzedniego przykładu jest serializowane do ciągu i zapisywane w pliku.</span><span class="sxs-lookup"><span data-stu-id="2258a-120">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="2258a-121">Poniższy przykład reprezentuje serializowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="2258a-121">The following example represents the serialized workflow.</span></span>

```xaml
<Activity
  x:TypeArguments="x:Int32"
  x:Class="Add"
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />
  </x:Members>
  <Sequence>
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">
      <Assign.To>
        <OutArgument x:TypeArguments="x:Int32">
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />
          </OutArgument>
      </Assign.To>
    </Assign>
  </Sequence>
</Activity>
```

<span data-ttu-id="2258a-122">Aby załadować serializowany przepływ pracy, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2258a-122">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="2258a-123">Spowoduje to przedefiniowanie serializowanej definicji przepływu pracy i zwrócenie <xref:System.Activities.DynamicActivity> , która reprezentuje definicję przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2258a-123">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="2258a-124">Należy pamiętać, że kod XAML nie jest deserializowany do momentu <xref:System.Activities.Activity.CacheMetadata%2A> wywołania w treści <xref:System.Activities.DynamicActivity> procesu walidacji.</span><span class="sxs-lookup"><span data-stu-id="2258a-124">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="2258a-125">Jeśli walidacja nie jest jawnie wywoływana, jest wykonywana po wywołaniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2258a-125">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="2258a-126">Jeśli definicja przepływu pracy XAML jest nieprawidłowa, <xref:System.ArgumentException> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2258a-126">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="2258a-127">Wszystkie wyjątki zgłoszone przez funkcję <xref:System.Activities.Activity.CacheMetadata%2A> ucieczki z wywołania do <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2258a-127">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="2258a-128">W poniższym przykładzie serializowany przepływ pracy z poprzedniego przykładu jest ładowany i wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="2258a-128">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="2258a-129">Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="2258a-129">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="2258a-130">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="2258a-130">**25 + 15**</span></span>\
<span data-ttu-id="2258a-131">**40**</span><span class="sxs-lookup"><span data-stu-id="2258a-131">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="2258a-132">Aby uzyskać więcej informacji na temat wywoływania przepływów pracy za pomocą argumentów wejściowych i wyjściowych, zobacz [using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) i <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="2258a-132">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="2258a-133">Jeśli serializowany przepływ pracy zawiera wyrażenia języka C#, <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienie z <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną jego właściwością `true` musi być przesyłane jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , w przeciwnym razie <xref:System.NotSupportedException> zostanie wygenerowany komunikat podobny do następującego: **Typ działania wyrażenia "CSharpValue" 1 "wymaga kompilacji, aby można było ją uruchomić.  Upewnij się, że przepływ pracy został skompilowany.**</span><span class="sxs-lookup"><span data-stu-id="2258a-133">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="2258a-134">Aby uzyskać więcej informacji, zobacz [wyrażenia języka C#](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2258a-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="2258a-135">Można także załadować seryjną definicję przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2258a-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="2258a-136">Po załadowaniu serializowanego przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można go sprawdzić i zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="2258a-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="2258a-137">Jest to przydatne w przypadku autorów projektanta niestandardowego przepływu pracy i oferuje mechanizm zapisywania i ponownego ładowania definicji przepływu pracy podczas procesu projektowania.</span><span class="sxs-lookup"><span data-stu-id="2258a-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="2258a-138">W poniższym przykładzie załadowano seryjną definicję przepływu pracy z poprzedniego przykładu, a jej właściwości są kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="2258a-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
