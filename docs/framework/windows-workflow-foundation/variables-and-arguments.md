---
title: Zmienne i argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 251641c924bbf33c176f519f8fc4f9dec59e2eb8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962195"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="3b07c-102">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="3b07c-102">Variables and Arguments</span></span>
<span data-ttu-id="3b07c-103">W Windows Workflow Foundation (WF) zmienne reprezentują magazyn danych i argumenty reprezentują przepływ danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="3b07c-104">Działanie ma zestaw argumentów i składają się na podpis działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="3b07c-105">Ponadto działanie może obsługiwać listę zmiennych, do których deweloper może dodawać lub usuwać zmienne podczas projektowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="3b07c-106">Argument jest powiązany przy użyciu wyrażenia, które zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="3b07c-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="3b07c-107">Zmienne</span><span class="sxs-lookup"><span data-stu-id="3b07c-107">Variables</span></span>  
 <span data-ttu-id="3b07c-108">Zmienne są lokalizacjami przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="3b07c-108">Variables are storage locations for data.</span></span> <span data-ttu-id="3b07c-109">Zmienne są zadeklarowane jako część definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="3b07c-110">Zmienne przyjmują wartości w czasie wykonywania, a te wartości są przechowywane jako część stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="3b07c-111">Definicja zmiennej określa typ zmiennej i opcjonalnie nazwę.</span><span class="sxs-lookup"><span data-stu-id="3b07c-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="3b07c-112">Poniższy kod pokazuje, jak zadeklarować zmienną, przypisać do niej wartość za pomocą <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetlić jej wartość w konsoli <xref:System.Activities.Statements.WriteLine> programu za pomocą działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="3b07c-113">Opcjonalnie można określić wyrażenie wartości domyślnej jako część deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="3b07c-114">Zmienne mogą również mieć modyfikatory.</span><span class="sxs-lookup"><span data-stu-id="3b07c-114">Variables also can have modifiers.</span></span> <span data-ttu-id="3b07c-115">Na przykład jeśli zmienna jest tylko do odczytu, można zastosować modyfikator tylko <xref:System.Activities.VariableModifiers> do odczytu.</span><span class="sxs-lookup"><span data-stu-id="3b07c-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="3b07c-116">W poniższym przykładzie jest tworzona zmienna tylko do odczytu z przypisaną wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="3b07c-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="3b07c-117">Określanie zakresu zmiennych</span><span class="sxs-lookup"><span data-stu-id="3b07c-117">Variable Scoping</span></span>  
 <span data-ttu-id="3b07c-118">Okres istnienia zmiennej w czasie wykonywania jest równy okresowi istnienia działania, które deklaruje je.</span><span class="sxs-lookup"><span data-stu-id="3b07c-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="3b07c-119">Po zakończeniu działania jego zmienne są czyszczone i nie można już do nich odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="3b07c-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="3b07c-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3b07c-120">Arguments</span></span>  
 <span data-ttu-id="3b07c-121">Autorzy działań używają argumentów do definiowania sposobu, w jaki dane są przesyłane do i z działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="3b07c-122">Każdy argument ma określony kierunek: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, lub <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="3b07c-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="3b07c-123">Środowisko uruchomieniowe przepływu pracy zapewnia następujące gwarancje dotyczące chronometrażu przenoszenia danych do i z działań:</span><span class="sxs-lookup"><span data-stu-id="3b07c-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="3b07c-124">Po rozpoczęciu działania wykonywane są wartości wszystkich argumentów wejściowych i wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3b07c-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="3b07c-125">Na przykład bez względu <xref:System.Activities.Argument.Get%2A> na to, że zwracana wartość jest wartością obliczoną przez środowisko uruchomieniowe przed `Execute`wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="3b07c-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="3b07c-126">Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe natychmiast ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="3b07c-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="3b07c-127">Argumenty mogą opcjonalnie mieć <xref:System.Activities.Argument.EvaluationOrder%2A> określone.</span><span class="sxs-lookup"><span data-stu-id="3b07c-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="3b07c-128"><xref:System.Activities.Argument.EvaluationOrder%2A>jest wartością zerową, która określa kolejność, w której argument jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="3b07c-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="3b07c-129">Domyślnie kolejność oceny argumentu nie jest określona i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartości.</span><span class="sxs-lookup"><span data-stu-id="3b07c-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="3b07c-130">Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> wartość większą lub równą zero, aby określić kolejność szacowania dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="3b07c-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="3b07c-131">Windows Workflow Foundation ocenia argumenty z określoną kolejnością szacowania w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="3b07c-132">Należy zauważyć, że argumenty z nieokreśloną kolejnością szacowania są oceniane przed tymi z określoną kolejnością szacowania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="3b07c-133">Autor działania może użyć mechanizmu o jednoznacznie określonym typie do ujawnienia swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="3b07c-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="3b07c-134">Jest to realizowane przez deklarując właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="3b07c-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="3b07c-135">Dzięki temu autor działania może ustanowić konkretną umowę dotyczącą danych przechodzących do działania i z niego.</span><span class="sxs-lookup"><span data-stu-id="3b07c-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="3b07c-136">Definiowanie argumentów dla działania</span><span class="sxs-lookup"><span data-stu-id="3b07c-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="3b07c-137">Argumenty można definiować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="3b07c-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="3b07c-138">Poniższy kod ilustruje sposób definiowania argumentów dla `Prompt` działania pobierającego ciąg, który ma być wyświetlany użytkownikowi i zwraca ciąg zawierający odpowiedź użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3b07c-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="3b07c-139">Działania zwracające pojedynczą wartość mogą pochodzić od <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, lub <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="3b07c-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="3b07c-140">Te działania mają dobrze zdefiniowaną <xref:System.Activities.OutArgument%601> nazwę <xref:System.Activities.Activity%601.Result%2A> , która zawiera wartość zwracaną działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="3b07c-141">Używanie zmiennych i argumentów w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="3b07c-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="3b07c-142">Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="3b07c-143">Przepływ pracy to sekwencja, która deklaruje trzy zmienne `var1`: `var2`,, `var3`i.</span><span class="sxs-lookup"><span data-stu-id="3b07c-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="3b07c-144">Pierwsze działanie w przepływie pracy to `Assign` działanie, które przypisuje wartość zmiennej `var1` do zmiennej `var2`.</span><span class="sxs-lookup"><span data-stu-id="3b07c-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="3b07c-145">Następuje `WriteLine` to działanie, które drukuje wartość `var2` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="3b07c-146">Dalej jest innym `Assign` działaniem, które przypisuje wartość `var2` zmiennej do zmiennej `var3`.</span><span class="sxs-lookup"><span data-stu-id="3b07c-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="3b07c-147">Na koniec istnieje inne `WriteLine` działanie, które drukuje wartość `var3` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="3b07c-148">Pierwsze `Assign` `InArgument<string>` działanie`OutArgument<string>` korzysta z obiektów, które jawnie reprezentują powiązania dla argumentów działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="3b07c-149">`InArgument<string>`jest używany w <xref:System.Activities.Statements.Assign.Value%2A> przypadku, gdy wartość jest przepływa <xref:System.Activities.Statements.Assign%601> do działania za pomocą <xref:System.Activities.Statements.Assign.Value%2A> jego argumentu i `OutArgument<string>` jest <xref:System.Activities.Statements.Assign.To%2A> używana dla <xref:System.Activities.Statements.Assign.To%2A> , ponieważ wartość przepływa z argumentu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="3b07c-150">Drugie `Assign` działanie wykonuje tę samą czynność z bardziej zwartą, ale równoważną składnią, która używa niejawnych rzutowania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="3b07c-151">`WriteLine` Działania również używają składni kompaktowej.</span><span class="sxs-lookup"><span data-stu-id="3b07c-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="3b07c-152">Używanie zmiennych i argumentów w działaniach opartych na kodzie</span><span class="sxs-lookup"><span data-stu-id="3b07c-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="3b07c-153">Poprzednie przykłady pokazują, jak używać argumentów i zmiennych w przepływach pracy i działaniach deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="3b07c-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="3b07c-154">Argumenty i zmienne są również używane w działaniach opartych na kodzie.</span><span class="sxs-lookup"><span data-stu-id="3b07c-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="3b07c-155">Koncepcje użycia są bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="3b07c-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="3b07c-156">Zmienne reprezentują magazyn danych w ramach działania, a argumenty reprezentują przepływ danych do działania lub z niego, i są powiązane przez autora przepływu pracy z innymi zmiennymi lub argumentami w przepływie pracy, które reprezentują miejsce, do którego dane są przesyłane do lub z.</span><span class="sxs-lookup"><span data-stu-id="3b07c-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="3b07c-157">Aby uzyskać lub ustawić wartość zmiennej lub argumentu w działaniu, należy użyć kontekstu działania, który reprezentuje bieżące środowisko wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="3b07c-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="3b07c-158">Jest to przesyłane do <xref:System.Activities.CodeActivity%601.Execute%2A> metody działania przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="3b07c-159">W tym przykładzie zdefiniowano działanie `Add` niestandardowe, które ma dwa <xref:System.Activities.ArgumentDirection.In> argumenty.</span><span class="sxs-lookup"><span data-stu-id="3b07c-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="3b07c-160">Aby uzyskać dostęp do wartości argumentów, <xref:System.Activities.Argument.Get%2A> używana jest metoda oraz kontekst, który został przekazane przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3b07c-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="3b07c-161">Aby uzyskać więcej informacji na temat pracy z argumentami, zmiennymi i wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md) obowiązkowego oraz [wymaganych argumentów i grup](required-arguments-and-overload-groups.md)przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="3b07c-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
