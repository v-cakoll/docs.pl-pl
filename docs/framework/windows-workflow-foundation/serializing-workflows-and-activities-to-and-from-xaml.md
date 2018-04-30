---
title: Serializacja przepływów pracy i działań do i z XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a36b8a6bdf1a024f4ddee91bd937afac516e391f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="0501f-102">Serializacja przepływów pracy i działań do i z XAML</span><span class="sxs-lookup"><span data-stu-id="0501f-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="0501f-103">Oprócz kompilowany do typów, które znajdują się w zestawach definicji przepływu pracy może być Zserializowany w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="0501f-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="0501f-104">Te definicje serializacji można wykorzystać do edycji lub inspekcję, przekazany do system kompilacji dla kompilacji, i załadować wywołany.</span><span class="sxs-lookup"><span data-stu-id="0501f-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="0501f-105">Ten temat zawiera omówienie serializacji definicji przepływu pracy oraz pracy z definicji przepływu pracy XAML.</span><span class="sxs-lookup"><span data-stu-id="0501f-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="0501f-106">Praca z definicji przepływu pracy XAML</span><span class="sxs-lookup"><span data-stu-id="0501f-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="0501f-107">Do tworzenia definicji przepływu pracy do serializacji, <xref:System.Activities.ActivityBuilder> klasa jest używana.</span><span class="sxs-lookup"><span data-stu-id="0501f-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="0501f-108">Tworzenie <xref:System.Activities.ActivityBuilder> jest bardzo podobny do tworzenia <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="0501f-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="0501f-109">Podano argumenty żądanej i działania, które stanowią zachowanie są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="0501f-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="0501f-110">W poniższym przykładzie `Add` utworzeniu działania, który przyjmuje dwa argumenty wejściowe, dodaje je ze sobą i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="0501f-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="0501f-111">Ponieważ to działanie zwraca wynik, ogólnego <xref:System.Activities.ActivityBuilder%601> klasa jest używana.</span><span class="sxs-lookup"><span data-stu-id="0501f-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="0501f-112">Każdy z <xref:System.Activities.DynamicActivityProperty> wystąpień reprezentuje jeden z argumentów wejściowych w przepływie pracy oraz <xref:System.Activities.ActivityBuilder.Implementation%2A> zawiera działania, które tworzą logika przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0501f-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="0501f-113">Należy pamiętać, że wyrażenia r-wartości w tym przykładzie są wyrażeń języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0501f-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="0501f-114">Wyrażenia lambda nie są do serializacji w języku XAML chyba że <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> jest używany.</span><span class="sxs-lookup"><span data-stu-id="0501f-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="0501f-115">Jeśli serializacji przepływy pracy mają można otworzyć lub edytować w Projektancie przepływów pracy, a następnie wyrażeń języka Visual Basic powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="0501f-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> <span data-ttu-id="0501f-116">Aby uzyskać więcej informacji, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="0501f-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="0501f-117">Do serializacji definicji przepływu pracy reprezentowany przez <xref:System.Activities.ActivityBuilder> wystąpienia w języku XAML, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> utworzyć <xref:System.Xaml.XamlWriter>, a następnie użyj <xref:System.Xaml.XamlServices> do serializacji definicji przepływu pracy przy użyciu <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0501f-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="0501f-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> metody mapowania <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML i załadować przepływów pracy XAML i zwracać <xref:System.Activities.DynamicActivity> może być wywołany.</span><span class="sxs-lookup"><span data-stu-id="0501f-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="0501f-119">W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienia z poprzedniego przykładu uszeregować w ciągu, a także zapisane w pliku.</span><span class="sxs-lookup"><span data-stu-id="0501f-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="0501f-120">Poniższy przykład przedstawia serializacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0501f-120">The following example represents the serialized workflow.</span></span>  
  
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
  
 <span data-ttu-id="0501f-121">Do załadowania serializacji przepływu pracy, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="0501f-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="0501f-122">To przyjmuje definicja Zserializowany przepływu pracy i zwraca <xref:System.Activities.DynamicActivity> reprezentujący definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0501f-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="0501f-123">Należy pamiętać, że XAML nie jest zdeserializować do <xref:System.Activities.Activity.CacheMetadata%2A> jest wywoływana w treści <xref:System.Activities.DynamicActivity> w procesie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="0501f-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="0501f-124">Jeśli weryfikacja nie została jawnie wywołana. jest on również wykonywane po wywołaniu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="0501f-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="0501f-125">Jeśli XAML definicji przepływu pracy jest nieprawidłowy, a następnie <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0501f-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="0501f-126">Wszelkie wyjątki zgłaszane z <xref:System.Activities.Activity.CacheMetadata%2A> ucieczki z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0501f-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="0501f-127">W poniższym przykładzie serializacji przepływu pracy z poprzedniego przykładu jest załadowany i wywoływane przy użyciu <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="0501f-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="0501f-128">Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="0501f-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="0501f-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="0501f-129">**25 + 15**</span></span>  
<span data-ttu-id="0501f-130">**40**</span><span class="sxs-lookup"><span data-stu-id="0501f-130">**40**</span></span>    
> [!NOTE]
>  <span data-ttu-id="0501f-131">Aby uzyskać więcej informacji na temat wywoływania przepływy pracy argumentów wejściowych i wyjściowych, zobacz [przy użyciu WorkflowInvoker i działanie obiektu WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) i <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="0501f-131">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="0501f-132">Jeśli serializacji przepływ pracy zawiera wyrażenia języka C#, a następnie <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną właściwość `true` muszą być przekazywane jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, w przeciwnym razie <xref:System.NotSupportedException> zostanie zgłoszony z komunikatu podobnego do następujące: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="0501f-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="0501f-133">Upewnij się, że przepływ pracy został skompilowany. "</span><span class="sxs-lookup"><span data-stu-id="0501f-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 <span data-ttu-id="0501f-134">Aby uzyskać więcej informacji, zobacz [wyrażeń C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0501f-134">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="0501f-135">Definicja Zserializowany przepływu pracy mogą także zostać załadowane do <xref:System.Activities.ActivityBuilder> wystąpienia przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0501f-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="0501f-136">Po załadowaniu serializacji przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można sprawdzić i modyfikować.</span><span class="sxs-lookup"><span data-stu-id="0501f-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="0501f-137">Jest to użyteczne dla autorów projektanta niestandardowego przepływu pracy i udostępnia mechanizm dla zapisywanie i ponowne załadowanie definicji przepływu pracy podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="0501f-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="0501f-138">W poniższym przykładzie jest ładowany definicja Zserializowany przepływu pracy z poprzedniego przykładu, a jego właściwości są kontrolowane.</span><span class="sxs-lookup"><span data-stu-id="0501f-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
