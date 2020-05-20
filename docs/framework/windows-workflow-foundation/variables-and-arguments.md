---
title: Zmienne i argumenty
description: W tym artykule opisano zmienne, które reprezentują magazyn danych i argumenty reprezentujące przepływ danych do/z działania w programie Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 47b8a7bddc8c3a9a8427bcb3e93760a63e5fa976
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421309"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="8d419-103">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="8d419-103">Variables and Arguments</span></span>
<span data-ttu-id="8d419-104">W Windows Workflow Foundation (WF) zmienne reprezentują magazyn danych i argumenty reprezentują przepływ danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="8d419-105">Działanie ma zestaw argumentów i składają się na podpis działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="8d419-106">Ponadto działanie może obsługiwać listę zmiennych, do których deweloper może dodawać lub usuwać zmienne podczas projektowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="8d419-107">Argument jest powiązany przy użyciu wyrażenia, które zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="8d419-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="8d419-108">Zmienne</span><span class="sxs-lookup"><span data-stu-id="8d419-108">Variables</span></span>  
 <span data-ttu-id="8d419-109">Zmienne są lokalizacjami przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="8d419-109">Variables are storage locations for data.</span></span> <span data-ttu-id="8d419-110">Zmienne są zadeklarowane jako część definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="8d419-111">Zmienne przyjmują wartości w czasie wykonywania, a te wartości są przechowywane jako część stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="8d419-112">Definicja zmiennej określa typ zmiennej i opcjonalnie nazwę.</span><span class="sxs-lookup"><span data-stu-id="8d419-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="8d419-113">Poniższy kod pokazuje, jak zadeklarować zmienną, przypisać do niej wartość za pomocą <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetlić jej wartość w konsoli programu za pomocą <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="8d419-114">Opcjonalnie można określić wyrażenie wartości domyślnej jako część deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8d419-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="8d419-115">Zmienne mogą również mieć modyfikatory.</span><span class="sxs-lookup"><span data-stu-id="8d419-115">Variables also can have modifiers.</span></span> <span data-ttu-id="8d419-116">Na przykład jeśli zmienna jest tylko do odczytu, można zastosować modyfikator tylko do odczytu <xref:System.Activities.VariableModifiers> .</span><span class="sxs-lookup"><span data-stu-id="8d419-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="8d419-117">W poniższym przykładzie jest tworzona zmienna tylko do odczytu z przypisaną wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="8d419-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="8d419-118">Określanie zakresu zmiennych</span><span class="sxs-lookup"><span data-stu-id="8d419-118">Variable Scoping</span></span>  
 <span data-ttu-id="8d419-119">Okres istnienia zmiennej w czasie wykonywania jest równy okresowi istnienia działania, które deklaruje je.</span><span class="sxs-lookup"><span data-stu-id="8d419-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="8d419-120">Po zakończeniu działania jego zmienne są czyszczone i nie można już do nich odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="8d419-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="8d419-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8d419-121">Arguments</span></span>  
 <span data-ttu-id="8d419-122">Autorzy działań używają argumentów do definiowania sposobu, w jaki dane są przesyłane do i z działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="8d419-123">Każdy argument ma określony kierunek: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> , lub <xref:System.Activities.ArgumentDirection.InOut> .</span><span class="sxs-lookup"><span data-stu-id="8d419-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="8d419-124">Środowisko uruchomieniowe przepływu pracy zapewnia następujące gwarancje dotyczące chronometrażu przenoszenia danych do i z działań:</span><span class="sxs-lookup"><span data-stu-id="8d419-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="8d419-125">Po rozpoczęciu działania wykonywane są wartości wszystkich argumentów wejściowych i wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8d419-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="8d419-126">Na przykład bez względu <xref:System.Activities.Argument.Get%2A> na to, że zwracana wartość jest wartością obliczoną przez środowisko uruchomieniowe przed wywołaniem metody `Execute` .</span><span class="sxs-lookup"><span data-stu-id="8d419-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="8d419-127">Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe natychmiast ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="8d419-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="8d419-128">Argumenty mogą opcjonalnie mieć <xref:System.Activities.Argument.EvaluationOrder%2A> określone.</span><span class="sxs-lookup"><span data-stu-id="8d419-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="8d419-129"><xref:System.Activities.Argument.EvaluationOrder%2A>jest wartością zerową, która określa kolejność, w której argument jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="8d419-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="8d419-130">Domyślnie kolejność oceny argumentu nie jest określona i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartości.</span><span class="sxs-lookup"><span data-stu-id="8d419-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="8d419-131">Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> wartość większą lub równą zero, aby określić kolejność szacowania dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d419-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="8d419-132">Windows Workflow Foundation ocenia argumenty z określoną kolejnością szacowania w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="8d419-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="8d419-133">Należy zauważyć, że argumenty z nieokreśloną kolejnością szacowania są oceniane przed tymi z określoną kolejnością szacowania.</span><span class="sxs-lookup"><span data-stu-id="8d419-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="8d419-134">Autor działania może użyć mechanizmu o jednoznacznie określonym typie do ujawnienia swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="8d419-134">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="8d419-135">Jest to realizowane przez deklarując właściwości typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> , i <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="8d419-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="8d419-136">Dzięki temu autor działania może ustanowić konkretną umowę dotyczącą danych przechodzących do działania i z niego.</span><span class="sxs-lookup"><span data-stu-id="8d419-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="8d419-137">Definiowanie argumentów dla działania</span><span class="sxs-lookup"><span data-stu-id="8d419-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="8d419-138">Argumenty można definiować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> , i <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="8d419-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="8d419-139">Poniższy kod ilustruje sposób definiowania argumentów dla `Prompt` działania pobierającego ciąg, który ma być wyświetlany użytkownikowi i zwraca ciąg zawierający odpowiedź użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d419-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="8d419-140">Działania zwracające pojedynczą wartość mogą pochodzić od <xref:System.Activities.Activity%601> , <xref:System.Activities.NativeActivity%601> , lub <xref:System.Activities.CodeActivity%601> .</span><span class="sxs-lookup"><span data-stu-id="8d419-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="8d419-141">Te działania mają dobrze zdefiniowaną <xref:System.Activities.OutArgument%601> nazwę <xref:System.Activities.Activity%601.Result%2A> , która zawiera wartość zwracaną działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="8d419-142">Używanie zmiennych i argumentów w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="8d419-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="8d419-143">Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="8d419-144">Przepływ pracy to sekwencja, która deklaruje trzy zmienne: `var1` , `var2` , i `var3` .</span><span class="sxs-lookup"><span data-stu-id="8d419-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="8d419-145">Pierwsze działanie w przepływie pracy to `Assign` działanie, które przypisuje wartość zmiennej `var1` do zmiennej `var2` .</span><span class="sxs-lookup"><span data-stu-id="8d419-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="8d419-146">Następuje to `WriteLine` działanie, które drukuje wartość `var2` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8d419-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="8d419-147">Dalej jest innym `Assign` działaniem, które przypisuje wartość zmiennej `var2` do zmiennej `var3` .</span><span class="sxs-lookup"><span data-stu-id="8d419-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="8d419-148">Na koniec istnieje inne `WriteLine` działanie, które drukuje wartość `var3` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8d419-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="8d419-149">Pierwsze `Assign` działanie korzysta z `InArgument<string>` `OutArgument<string>` obiektów, które jawnie reprezentują powiązania dla argumentów działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="8d419-150">`InArgument<string>`jest używany w przypadku <xref:System.Activities.Statements.Assign.Value%2A> , gdy wartość jest przepływa do <xref:System.Activities.Statements.Assign%601> działania za pomocą jego <xref:System.Activities.Statements.Assign.Value%2A> argumentu i `OutArgument<string>` jest używana dla, <xref:System.Activities.Statements.Assign.To%2A> ponieważ wartość przepływa z <xref:System.Activities.Statements.Assign.To%2A> argumentu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8d419-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="8d419-151">Drugie działanie wykonuje tę `Assign` samą czynność z bardziej zwartą, ale równoważną składnią, która używa niejawnych rzutowania.</span><span class="sxs-lookup"><span data-stu-id="8d419-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="8d419-152">`WriteLine`Działania również używają składni kompaktowej.</span><span class="sxs-lookup"><span data-stu-id="8d419-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="8d419-153">Używanie zmiennych i argumentów w działaniach opartych na kodzie</span><span class="sxs-lookup"><span data-stu-id="8d419-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="8d419-154">Poprzednie przykłady pokazują, jak używać argumentów i zmiennych w przepływach pracy i działaniach deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="8d419-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="8d419-155">Argumenty i zmienne są również używane w działaniach opartych na kodzie.</span><span class="sxs-lookup"><span data-stu-id="8d419-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="8d419-156">Koncepcje użycia są bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="8d419-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="8d419-157">Zmienne reprezentują magazyn danych w ramach działania, a argumenty reprezentują przepływ danych do działania lub z niego, i są powiązane przez autora przepływu pracy z innymi zmiennymi lub argumentami w przepływie pracy, które reprezentują miejsce, do którego dane są przesyłane do lub z.</span><span class="sxs-lookup"><span data-stu-id="8d419-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="8d419-158">Aby uzyskać lub ustawić wartość zmiennej lub argumentu w działaniu, należy użyć kontekstu działania, który reprezentuje bieżące środowisko wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="8d419-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="8d419-159">Jest to przesyłane do <xref:System.Activities.CodeActivity%601.Execute%2A> metody działania przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="8d419-160">W tym przykładzie `Add` zdefiniowano działanie niestandardowe, które ma dwa <xref:System.Activities.ArgumentDirection.In> argumenty.</span><span class="sxs-lookup"><span data-stu-id="8d419-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="8d419-161">Aby uzyskać dostęp do wartości argumentów, używana jest <xref:System.Activities.Argument.Get%2A> Metoda oraz kontekst, który został przekazane przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8d419-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="8d419-162">Aby uzyskać więcej informacji na temat pracy z argumentami, zmiennymi i wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md) [obowiązkowego oraz wymaganych argumentów i grup przeciążeń](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="8d419-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
