---
title: Argumenty i zmienne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d01c31cce9aa6ae6d87773fc8e616e0e08bbd8c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="variables-and-arguments"></a><span data-ttu-id="c8fa7-102">Argumenty i zmienne</span><span class="sxs-lookup"><span data-stu-id="c8fa7-102">Variables and Arguments</span></span>
<span data-ttu-id="c8fa7-103">W [!INCLUDE[wf](../../../includes/wf-md.md)], zmienne reprezentują magazynu danych i argumenty reprezentują przepływ danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-103">In [!INCLUDE[wf](../../../includes/wf-md.md)], variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="c8fa7-104">Działanie ma zestaw argumentów i tworzą one podpisu działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="c8fa7-105">Ponadto działania można zachować listę zmiennych, których projektant można dodawać i usuwać zmienne podczas projektowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="c8fa7-106">Argument jest powiązany za pomocą wyrażenia, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="c8fa7-107">Zmienne</span><span class="sxs-lookup"><span data-stu-id="c8fa7-107">Variables</span></span>  
 <span data-ttu-id="c8fa7-108">Zmienne są lokalizacje magazynu dla danych.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-108">Variables are storage locations for data.</span></span> <span data-ttu-id="c8fa7-109">Zmienne są deklarowane jako część definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="c8fa7-110">Zmienne Przełącz wartości w czasie wykonywania, a te wartości są przechowywane w ramach stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="c8fa7-111">Definicja zmiennej określa typu zmienną, i opcjonalnie nazwy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="c8fa7-112">Poniższy kod przedstawia sposób zadeklarować zmiennej, przypisywanie wartości do niej przy użyciu <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetl jego wartość przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="c8fa7-113">Opcjonalnie można określić wyrażenie wartości domyślnej w ramach deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="c8fa7-114">Zmienne można również mieć modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-114">Variables also can have modifiers.</span></span> <span data-ttu-id="c8fa7-115">Na przykład jeśli zmienna jest tylko do odczytu, a następnie tylko do odczytu <xref:System.Activities.VariableModifiers> modyfikator mogą być stosowane.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="c8fa7-116">W poniższym przykładzie utworzono zmiennej tylko do odczytu, która ma przypisaną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="c8fa7-117">Zakres zmiennej</span><span class="sxs-lookup"><span data-stu-id="c8fa7-117">Variable Scoping</span></span>  
 <span data-ttu-id="c8fa7-118">Okres istnienia zmienną w czasie wykonywania jest równa okres istnienia działania, który deklaruje go.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="c8fa7-119">Po zakończeniu działania, zmienne są wyczyszczone, a nie może być przywoływany.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="c8fa7-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c8fa7-120">Arguments</span></span>  
 <span data-ttu-id="c8fa7-121">Autorzy działania używać argumentów do definiowania danych sposób przepływy do i z działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="c8fa7-122">Każdy argument ma kierunek określony: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, lub <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="c8fa7-123">Środowiska uruchomieniowego przepływu pracy wykonuje następujące gwarancje o czas przenoszenia danych do i z działania:</span><span class="sxs-lookup"><span data-stu-id="c8fa7-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1.  <span data-ttu-id="c8fa7-124">Po uruchomieniu działania wykonywane są obliczane wartości wszystkich argumentów wejściowych i operacjami wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="c8fa7-125">Na przykład, niezależnie od tego, kiedy <xref:System.Activities.Argument.Get%2A> jest wywoływana, zwracana wartość jest obliczana co w czasie wykonywania przed jej wywołanie `Execute`.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2.  <span data-ttu-id="c8fa7-126">Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe ustawia wartość natychmiast.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3.  <span data-ttu-id="c8fa7-127">Opcjonalnie może mieć argumentów ich <xref:System.Activities.Argument.EvaluationOrder%2A> określony.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="c8fa7-128"><xref:System.Activities.Argument.EvaluationOrder%2A>jest liczony od zera wartość, która określa kolejność, w jakiej są oceniane argument.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="c8fa7-129">Domyślnie kolejność obliczania argumentu nie jest określona i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartość.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="c8fa7-130">Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> na wartość większą lub równą zero, aby określić kolejność obliczania dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> [!INCLUDE[wf2](../../../includes/wf2-md.md)]<span data-ttu-id="c8fa7-131">oblicza argumentów, których kolejność obliczania określony w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-131"> evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="c8fa7-132">Należy pamiętać, że argumenty z kolejnością obliczania nieokreślony są oceniane przed elementami z kolejnością obliczania określony.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="c8fa7-133">Przez autora działania można używać mechanizmu jednoznacznie udostępnianie argumenty.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="c8fa7-134">Jest to osiągane przez deklarowanie właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="c8fa7-135">Dzięki temu przez autora działania nawiązać z określonym kontraktem o danych, przechodząc do i z działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="c8fa7-136">Definiowanie argumenty w działaniu</span><span class="sxs-lookup"><span data-stu-id="c8fa7-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="c8fa7-137">Argumenty można zdefiniować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="c8fa7-138">Poniższy kod przedstawia sposób definiowania argumenty `Prompt` działania, która przyjmuje w ciągu do wyświetlenia dla użytkownika i zwraca ciąg zawierający odpowiedzi użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="c8fa7-139">Działania, które zwraca pojedynczą wartość może pochodzić od <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, lub <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="c8fa7-140">Te działania mają dobrze zdefiniowanego <xref:System.Activities.OutArgument%601> o nazwie <xref:System.Activities.Activity%601.Result%2A> zawiera wartość zwracaną przez działanie.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="c8fa7-141">Używanie zmiennych i argumenty w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="c8fa7-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="c8fa7-142">W poniższym przykładzie pokazano, jak argumenty i zmienne są używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="c8fa7-143">Przepływ pracy jest sekwencji, który deklaruje trzy zmienne: `var1`, `var2`, i `var3`.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="c8fa7-144">Pierwsze działanie w przepływie pracy jest `Assign` działania, która przypisuje wartość zmiennej `var1` do zmiennej `var2`.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="c8fa7-145">Następuje to `WriteLine` działanie, które wartości `var2` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="c8fa7-146">Następnie jest inny `Assign` działania, która przypisuje wartość zmiennej `var2` do zmiennej `var3`.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="c8fa7-147">Na koniec istnieje inny `WriteLine` działanie, które wartości `var3` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="c8fa7-148">Pierwszy `Assign` używa działania `InArgument<string>` i `OutArgument<string>` obiekty reprezentujące jawnie powiązań dla argumentów działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="c8fa7-149">`InArgument<string>`Służy do <xref:System.Activities.Statements.Assign.Value%2A> , ponieważ wartość wejściowa jest do <xref:System.Activities.Statements.Assign%601> działania za pomocą jego <xref:System.Activities.Statements.Assign.Value%2A> argumentu, i `OutArgument<string>` służy do <xref:System.Activities.Statements.Assign.To%2A> , ponieważ wartość jest wynikających z <xref:System.Activities.Statements.Assign.To%2A> argument do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="c8fa7-150">Drugi `Assign` działania wykonuje ten sam efekt z więcej compact ale równoważne składnię, która używa niejawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="c8fa7-151">`WriteLine` Działań również użyć zwięzłą składnią.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="c8fa7-152">Użycie zmiennych i argumentów działania oparte na kodzie</span><span class="sxs-lookup"><span data-stu-id="c8fa7-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="c8fa7-153">W powyższym przykładzie pokazano sposób użycia argumentów i zmiennych w przepływach pracy i deklaratywne działań.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="c8fa7-154">Argumenty i zmienne są również używane w działaniach opartej na kodzie.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="c8fa7-155">Koncepcyjnie jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="c8fa7-156">Zmienne reprezentują magazynu danych w ramach działania i argumenty reprezentują przepływ danych do lub z działania i są powiązane przez autora przepływu pracy do innych zmiennych lub argumentów w przepływie pracy reprezentujące, w którym dane przepływają do lub z.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="c8fa7-157">Get lub zestaw, który należy użyć wartości zmiennej lub argumentu w działaniu, kontekst działania reprezentujący aktualnego środowiska wykonawczego działania.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="c8fa7-158">To jest przekazywany do <xref:System.Activities.CodeActivity%601.Execute%2A> metody działania przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="c8fa7-159">W tym przykładzie niestandardowego `Add` zdefiniowano zawiera dwa działania <xref:System.Activities.ArgumentDirection.In> argumentów.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="c8fa7-160">Aby uzyskać dostęp do wartości argumentów <xref:System.Activities.Argument.Get%2A> metoda jest używana i jest używany w kontekście, który został przekazany w czasie wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8fa7-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="c8fa7-161">Praca z argumentami, zmienne i wyrażenia w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne przy użyciu wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) i [wymaganych argumentów i grup przeciążenia](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="c8fa7-161"> working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>
