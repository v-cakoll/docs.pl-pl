---
title: Wyrażenia języka C#
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32fb7be6f8c465994b40814a94efd95d42a481da
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="c-expressions"></a><span data-ttu-id="bac2f-102">Wyrażenia języka C#</span><span class="sxs-lookup"><span data-stu-id="bac2f-102">C# Expressions</span></span>
<span data-ttu-id="bac2f-103">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# wyrażenia są obsługiwane w systemie Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="bac2f-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="bac2f-104">Nowych projektów C# przepływu pracy utworzone w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] kierowanych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Użyj C# wyrażeń i projekty Visual Basic przepływu pracy, użyj wyrażenia języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bac2f-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="bac2f-105">Istniejące [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projektów przepływu pracy, które używają wyrażeń języka Visual Basic można poddać migracji do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] niezależnie od tego projektu języka i są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bac2f-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="bac2f-106">Ten temat zawiera omówienie wyrażeń C# w [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bac2f-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="bac2f-107">Za pomocą wyrażeń C# w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="bac2f-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="bac2f-108">Za pomocą wyrażeń C# w Projektancie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="bac2f-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="bac2f-109">Zapewnienia zgodności</span><span class="sxs-lookup"><span data-stu-id="bac2f-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="bac2f-110">Za pomocą wyrażeń C# w przepływach pracy kodu</span><span class="sxs-lookup"><span data-stu-id="bac2f-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="bac2f-111">Za pomocą wyrażeń C# w przepływach pracy XAML</span><span class="sxs-lookup"><span data-stu-id="bac2f-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="bac2f-112">Skompilowany Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="bac2f-113">Luźne Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="bac2f-114">Za pomocą wyrażeń C# w XAMLX usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bac2f-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a> <span data-ttu-id="bac2f-115">Za pomocą wyrażeń C# w Projektancie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="bac2f-115">Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="bac2f-116">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# wyrażenia są obsługiwane w systemie Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="bac2f-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="bac2f-117">C# przepływu pracy projektów utworzonych w [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] kierowanych [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] używanie języka C# wyrażeń, gdy projekty Visual Basic przepływu pracy za pomocą wyrażeń języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bac2f-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="bac2f-118">Aby określić żądaną wyrażenia języka C#, wpisz go w polu **wprowadź wyrażenie C#**.</span><span class="sxs-lookup"><span data-stu-id="bac2f-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="bac2f-119">Etykieta jest wyświetlana w oknie właściwości, gdy działanie jest wybrane w projektancie, lub na działanie w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="bac2f-120">W poniższym przykładzie dwa `WriteLine` działania są zawarte w `Sequence` wewnątrz `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="bac2f-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="bac2f-121">![Automatycznie utworzone działania sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="bac2f-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bac2f-122">C# wyrażenia są obsługiwane tylko w programie Visual Studio i nie są obsługiwane w Projektancie ponownie hostowanej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="bac2f-123">Aby uzyskać więcej informacji o nowych funkcjach WF45 obsługiwane w Projektancie ponownie hostowanej, zobacz [obsługę nowych funkcji Workflow Foundation 4.5 w Projektancie przepływów pracy Rehosted](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="bac2f-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <a name="BackwardCompat"></a> <span data-ttu-id="bac2f-124">Zapewnienia zgodności</span><span class="sxs-lookup"><span data-stu-id="bac2f-124">Backwards compatibility</span></span>  
 <span data-ttu-id="bac2f-125">Wyrażenia języka Visual Basic w istniejących [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# przepływu pracy projektów, które zostały poddane migracji do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bac2f-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="bac2f-126">Patrząc wyrażeń języka Visual Basic w Projektancie przepływów pracy tekst istniejących wyrażenia języka Visual Basic jest zastępowany **wartość została ustawiona w języku XAML**, chyba że wyrażenie języka Visual Basic jest prawidłowej składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="bac2f-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="bac2f-127">Jeśli wyrażenie języka Visual Basic jest prawidłowej składni języka C#, wyrażenie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="bac2f-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="bac2f-128">Aby zaktualizować wyrażeń języka Visual Basic na język C#, można je edytować w Projektancie przepływów pracy i określ równoważne wyrażenie języka C#.</span><span class="sxs-lookup"><span data-stu-id="bac2f-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="bac2f-129">Zaktualizuj wyrażenia języka Visual Basic, C#, ale po wyrażenia są aktualizowane w Projektancie przepływów pracy są konwertowane na język C# i nie można przywrócić w języku Visual Basic nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="bac2f-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <a name="CodeWorkflows"></a> <span data-ttu-id="bac2f-130">Za pomocą wyrażeń C# w przepływach pracy kodu</span><span class="sxs-lookup"><span data-stu-id="bac2f-130">Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="bac2f-131">C# wyrażenia są obsługiwane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływów pracy opartych na kodzie, ale przed przepływu pracy można wywołać wyrażenia języka C# musi być kompilowana przy użyciu <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bac2f-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bac2f-132">Przepływ pracy autorzy mogą używać `CSharpValue` do reprezentowania r wyrażenia i `CSharpReference` do reprezentowania l wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bac2f-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="bac2f-133">W poniższym przykładzie przepływ pracy zostanie utworzona z `Assign` działania i `WriteLine` działań zawartych w `Sequence` działania.</span><span class="sxs-lookup"><span data-stu-id="bac2f-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="bac2f-134">A `CSharpReference` określono `To` argument `Assign`i reprezentuje l wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bac2f-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="bac2f-135">A `CSharpValue` określono `Value` argument `Assign`oraz `Text` argument `WriteLine`i reprezentuje r dla tych dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="bac2f-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
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
  
 <span data-ttu-id="bac2f-136">Po przepływu pracy jest tworzony, wyrażeń języka C# są kompilowane przez wywołanie metody `CompileExpressions` wywoływana jest metoda pomocnika, a następnie przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="bac2f-137">Poniżej przedstawiono przykład `CompileExpressions` metody.</span><span class="sxs-lookup"><span data-stu-id="bac2f-137">The following example is the `CompileExpressions` method.</span></span>  
  
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
>  <span data-ttu-id="bac2f-138">Jeśli nie są kompilowane wyrażeń C#, <xref:System.NotSupportedException> jest generowany, gdy przepływ pracy jest wywoływana z komunikatu podobnego do następującego: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="bac2f-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="bac2f-139">Upewnij się, że przepływ pracy został skompilowany. "</span><span class="sxs-lookup"><span data-stu-id="bac2f-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="bac2f-140">Jeśli przepływ pracy używa na podstawie niestandardowy kod `DynamicActivity`, następnie pewne zmiany do `CompileExpressions` metody są wymagane, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="bac2f-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="bac2f-141">Istnieje kilka różnic w `CompileExpressions` przeciążenia kompilowany wyrażeń C# w działaniu dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="bac2f-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="bac2f-142">Parametr `CompileExpressions` jest `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="bac2f-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="bac2f-143">Wpisz nazwę i przestrzeń nazw są pobierane przy użyciu `DynamicActivity.Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="bac2f-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="bac2f-144">`TextExpressionCompilerSettings.ForImplementation` ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="bac2f-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="bac2f-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` jest wywoływana zamiast `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="bac2f-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 <span data-ttu-id="bac2f-146">Aby uzyskać więcej informacji na temat pracy z wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="bac2f-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <a name="XamlWorkflows"></a> <span data-ttu-id="bac2f-147">Za pomocą wyrażeń C# w przepływach pracy XAML</span><span class="sxs-lookup"><span data-stu-id="bac2f-147">Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="bac2f-148">C# wyrażenia są obsługiwane w przepływach pracy XAML.</span><span class="sxs-lookup"><span data-stu-id="bac2f-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="bac2f-149">Skompilowany przepływów pracy XAML są kompilowane na typ i utracić przepływów pracy XAML są załadowane w czasie wykonywania i skompilowany w drzewie działań podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="bac2f-150">Skompilowany Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="bac2f-151">Luźne Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a> <span data-ttu-id="bac2f-152">Skompilowany Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-152">Compiled Xaml</span></span>  
 <span data-ttu-id="bac2f-153">C# wyrażenia są obsługiwane w skompilowanych przepływów pracy XAML, które są kompilowane do typu w ramach projektu przepływu pracy C# przeznaczonego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bac2f-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="bac2f-154">Domyślny typ przepływu pracy tworzenia w programie Visual Studio jest skompilowany XAML i projektów C# przepływu pracy utworzone w Visual Studio kierowanych [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] za pomocą wyrażeń C#.</span><span class="sxs-lookup"><span data-stu-id="bac2f-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <a name="LooseXaml"></a> <span data-ttu-id="bac2f-155">Luźne Xaml</span><span class="sxs-lookup"><span data-stu-id="bac2f-155">Loose Xaml</span></span>  
 <span data-ttu-id="bac2f-156">C# wyrażenia są obsługiwane w utracić przepływów pracy XAML.</span><span class="sxs-lookup"><span data-stu-id="bac2f-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="bac2f-157">Program hosta przepływu pracy, który ładuje i wywołuje utracić XAML przepływu pracy muszą wskazywać [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], i <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musi mieć ustawioną `true` (wartość domyślna to `false`).</span><span class="sxs-lookup"><span data-stu-id="bac2f-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="bac2f-158">Aby ustawić <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> do `true`, Utwórz <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną właściwość `true`i przekaż go jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bac2f-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bac2f-159">Jeśli `CompileExpressions` nie jest ustawiony na `true`, <xref:System.NotSupportedException> zostanie wygenerowany komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.</span><span class="sxs-lookup"><span data-stu-id="bac2f-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="bac2f-160">Upewnij się, że przepływ pracy został skompilowany. "</span><span class="sxs-lookup"><span data-stu-id="bac2f-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 <span data-ttu-id="bac2f-161">Aby uzyskać więcej informacji na temat pracy z przepływów pracy XAML, zobacz [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="bac2f-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <a name="WFServices"></a> <span data-ttu-id="bac2f-162">Za pomocą wyrażeń C# w XAMLX usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bac2f-162">Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="bac2f-163">C# wyrażenia są obsługiwane w XAMLX usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="bac2f-164">Gdy nie są wymagane żadne dodatkowe czynności, a następnie usługi przepływu pracy znajduje się w usługach IIS lub WAS, ale własnym znajduje się usługa XAML przepływu pracy, muszą być skompilowane wyrażenia języka C#.</span><span class="sxs-lookup"><span data-stu-id="bac2f-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="bac2f-165">Aby skompilować wyrażeń C# własnym hostowanej usługi przepływu pracy XAMLX, najpierw załadować pliku XAMLX do `WorkflowService`, a następnie przekazać `Body` z `WorkflowService` do `CompileExpressions` metody opisane w poprzedniej [przy użyciu języka C# wyrażenia w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji.</span><span class="sxs-lookup"><span data-stu-id="bac2f-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="bac2f-166">W poniższym przykładzie jest ładowany XAMLX usługi przepływu pracy, są kompilowane wyrażeń C#, a następnie usługi przepływu pracy jest otwarty i czeka na żądania.</span><span class="sxs-lookup"><span data-stu-id="bac2f-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
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
  
 <span data-ttu-id="bac2f-167">Jeśli nie są kompilowane wyrażeń C#, `Open` operacja zakończy się pomyślnie, ale przepływ pracy zakończy się niepowodzeniem, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="bac2f-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="bac2f-168">Następujące `CompileExpressions` metody jest taka sama jak metoda z poprzedniej [wyrażenia przy użyciu języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji.</span><span class="sxs-lookup"><span data-stu-id="bac2f-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
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
