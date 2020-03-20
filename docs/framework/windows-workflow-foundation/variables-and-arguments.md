---
title: Zmienne i argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: f975f46a1858d204d12588f7570b7ea5a365e650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182682"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="ea11a-102">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="ea11a-102">Variables and Arguments</span></span>
<span data-ttu-id="ea11a-103">W programie Windows Workflow Foundation (WF) zmienne reprezentują przechowywanie danych, a argumenty reprezentują przepływ danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="ea11a-104">Działanie ma zestaw argumentów i tworzą podpis działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="ea11a-105">Ponadto działanie może obsługiwać listę zmiennych, do których deweloper może dodawać lub usuwać zmienne podczas projektowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="ea11a-106">Argument jest powiązany przy użyciu wyrażenia, które zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="ea11a-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="ea11a-107">Zmienne</span><span class="sxs-lookup"><span data-stu-id="ea11a-107">Variables</span></span>  
 <span data-ttu-id="ea11a-108">Zmienne są lokalizacjami przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="ea11a-108">Variables are storage locations for data.</span></span> <span data-ttu-id="ea11a-109">Zmienne są deklarowane jako część definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="ea11a-110">Zmienne przyjmują wartości w czasie wykonywania i te wartości są przechowywane jako część stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="ea11a-111">Definicja zmiennej określa typ zmiennej i opcjonalnie nazwę.</span><span class="sxs-lookup"><span data-stu-id="ea11a-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="ea11a-112">Poniższy kod pokazuje, jak zadeklarować zmienną, <xref:System.Activities.Statements.Assign%601> przypisać do niej wartość za pomocą <xref:System.Activities.Statements.WriteLine> działania, a następnie wyświetlić jej wartość w konsoli przy użyciu działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="ea11a-113">Domyślne wyrażenie wartości można opcjonalnie określić jako część deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ea11a-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="ea11a-114">Zmienne mogą również mieć modyfikatory.</span><span class="sxs-lookup"><span data-stu-id="ea11a-114">Variables also can have modifiers.</span></span> <span data-ttu-id="ea11a-115">Na przykład jeśli zmienna jest tylko do <xref:System.Activities.VariableModifiers> odczytu, można zastosować modyfikator tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ea11a-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="ea11a-116">W poniższym przykładzie jest tworzona zmienna tylko do odczytu, która ma przypisaną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="ea11a-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="ea11a-117">Zakres zmiennej</span><span class="sxs-lookup"><span data-stu-id="ea11a-117">Variable Scoping</span></span>  
 <span data-ttu-id="ea11a-118">Okres istnienia zmiennej w czasie wykonywania jest równy okresowi istnienia działania, które ją deklaruje.</span><span class="sxs-lookup"><span data-stu-id="ea11a-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="ea11a-119">Po zakończeniu działania jego zmienne są czyszczone i nie można już odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="ea11a-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="ea11a-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ea11a-120">Arguments</span></span>  
 <span data-ttu-id="ea11a-121">Autorzy działań używają argumentów do definiowania sposobu przepływu danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="ea11a-122">Każdy argument ma określony <xref:System.Activities.ArgumentDirection.In> <xref:System.Activities.ArgumentDirection.Out>kierunek: <xref:System.Activities.ArgumentDirection.InOut>, , lub .</span><span class="sxs-lookup"><span data-stu-id="ea11a-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="ea11a-123">Środowisko wykonawcze przepływu pracy daje następujące gwarancje dotyczące czasu przenoszenia danych do i z działań:</span><span class="sxs-lookup"><span data-stu-id="ea11a-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="ea11a-124">Po rozpoczęciu wykonywania działania obliczane są wartości wszystkich jego argumentów wejściowych i wejściowych/wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ea11a-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="ea11a-125">Na przykład, niezależnie <xref:System.Activities.Argument.Get%2A> od tego, kiedy jest wywoływana, zwracana wartość jest wartością obliczoną przez środowisko wykonawcze przed wywołaniem . `Execute`</span><span class="sxs-lookup"><span data-stu-id="ea11a-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="ea11a-126">Po <xref:System.Activities.InOutArgument%601.Set%2A> wywołaniu środowisko wykonawcze natychmiast ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="ea11a-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="ea11a-127">Argumenty mogą opcjonalnie <xref:System.Activities.Argument.EvaluationOrder%2A> mieć ich określony.</span><span class="sxs-lookup"><span data-stu-id="ea11a-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="ea11a-128"><xref:System.Activities.Argument.EvaluationOrder%2A>jest wartością od zera, która określa kolejność, w jakiej argument jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="ea11a-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="ea11a-129">Domyślnie kolejność oceny argumentu jest nieokreślony i jest <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> równa wartości.</span><span class="sxs-lookup"><span data-stu-id="ea11a-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="ea11a-130">Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> wartość większą lub równą zero, aby określić kolejność oceny dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="ea11a-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="ea11a-131">Fundacja przepływu pracy systemu Windows ocenia argumenty o określonej kolejności oceny w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="ea11a-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="ea11a-132">Należy zauważyć, że argumenty z nieokreśloną kolejnością oceny są oceniane przed argumentami z określoną kolejnością oceny.</span><span class="sxs-lookup"><span data-stu-id="ea11a-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="ea11a-133">Autor działania można użyć mechanizmu silnie typizowane do uwidaczniania jego argumenty.</span><span class="sxs-lookup"><span data-stu-id="ea11a-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="ea11a-134">Odbywa się to poprzez deklarowanie <xref:System.Activities.InArgument%601>właściwości <xref:System.Activities.OutArgument%601>typu <xref:System.Activities.InOutArgument%601>, i .</span><span class="sxs-lookup"><span data-stu-id="ea11a-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="ea11a-135">Dzięki temu autor działania do ustanowienia określonej umowy o danych wchodząc i wychodząc z działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="ea11a-136">Definiowanie argumentów w działaniu</span><span class="sxs-lookup"><span data-stu-id="ea11a-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="ea11a-137">Argumenty można zdefiniować w działaniu, określając <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>właściwości <xref:System.Activities.InOutArgument%601>typu , i .</span><span class="sxs-lookup"><span data-stu-id="ea11a-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="ea11a-138">Poniższy kod pokazuje, jak zdefiniować argumenty dla `Prompt` działania, które ma w ciągu do wyświetlenia do użytkownika i zwraca ciąg, który zawiera odpowiedź użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ea11a-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="ea11a-139">Działania zwracające pojedynczą wartość mogą <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>pochodzić <xref:System.Activities.CodeActivity%601>z , lub .</span><span class="sxs-lookup"><span data-stu-id="ea11a-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="ea11a-140">Te działania mają dobrze <xref:System.Activities.OutArgument%601> zdefiniowaną nazwę, <xref:System.Activities.Activity%601.Result%2A> która zawiera zwracaną wartość działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="ea11a-141">Używanie zmiennych i argumentów w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="ea11a-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="ea11a-142">Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="ea11a-143">Przepływ pracy jest sekwencją, która deklaruje `var1` `var2`trzy `var3`zmienne: , , i .</span><span class="sxs-lookup"><span data-stu-id="ea11a-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="ea11a-144">Pierwsze działanie w przepływie `Assign` pracy to działanie, które `var1` przypisuje `var2`wartość zmiennej do zmiennej .</span><span class="sxs-lookup"><span data-stu-id="ea11a-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="ea11a-145">Po tym następuje `WriteLine` działanie, które drukuje wartość zmiennej. `var2`</span><span class="sxs-lookup"><span data-stu-id="ea11a-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="ea11a-146">Dalej jest `Assign` inne działanie, które `var2` przypisuje wartość `var3`zmiennej do zmiennej .</span><span class="sxs-lookup"><span data-stu-id="ea11a-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="ea11a-147">Na koniec istnieje `WriteLine` inne działanie, które `var3` drukuje wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ea11a-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="ea11a-148">Pierwsze `Assign` działanie używa `InArgument<string>` `OutArgument<string>` i obiektów, które jawnie reprezentują powiązania dla argumentów działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="ea11a-149">`InArgument<string>`jest <xref:System.Activities.Statements.Assign.Value%2A> używany, ponieważ wartość jest <xref:System.Activities.Statements.Assign%601> przepływa <xref:System.Activities.Statements.Assign.Value%2A> do działania `OutArgument<string>` za <xref:System.Activities.Statements.Assign.To%2A> pośrednictwem jego argumentu i <xref:System.Activities.Statements.Assign.To%2A> jest używany, ponieważ wartość jest wypływa z argumentu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ea11a-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="ea11a-150">Drugie `Assign` działanie wykonuje to samo z bardziej kompaktowe, ale równoważne składni, która używa rzutowań niejawnych.</span><span class="sxs-lookup"><span data-stu-id="ea11a-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="ea11a-151">Działania `WriteLine` również użyć składni kompaktowej.</span><span class="sxs-lookup"><span data-stu-id="ea11a-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="ea11a-152">Używanie zmiennych i argumentów w działaniach opartych na kodzie</span><span class="sxs-lookup"><span data-stu-id="ea11a-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="ea11a-153">Poprzednie przykłady pokazują, jak używać argumentów i zmiennych w przepływach pracy i działaniach deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="ea11a-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="ea11a-154">Argumenty i zmienne są również używane w działaniach opartych na kodzie.</span><span class="sxs-lookup"><span data-stu-id="ea11a-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="ea11a-155">Koncepcyjnie użycie jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="ea11a-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="ea11a-156">Zmienne reprezentują magazyn danych w ramach działania, a argumenty reprezentują przepływ danych do lub z działania i są powiązane przez autora przepływu pracy z innymi zmiennymi lub argumentami w przepływie pracy, które reprezentują, gdzie dane są przepływa do lub z.</span><span class="sxs-lookup"><span data-stu-id="ea11a-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="ea11a-157">Aby uzyskać lub ustawić wartość zmiennej lub argumentu w działaniu, kontekst działania musi być używany, który reprezentuje bieżące środowisko wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="ea11a-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="ea11a-158">Jest to przekazywane <xref:System.Activities.CodeActivity%601.Execute%2A> do metody działania przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="ea11a-159">W tym przykładzie `Add` zdefiniowano działanie <xref:System.Activities.ArgumentDirection.In> niestandardowe, które ma dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="ea11a-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="ea11a-160">Aby uzyskać dostęp do wartości <xref:System.Activities.Argument.Get%2A> argumentów, używana jest metoda i używany jest kontekst, który został przekazany przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea11a-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="ea11a-161">Aby uzyskać więcej informacji na temat pracy z argumentami, zmiennymi i wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywu](authoring-workflows-activities-and-expressions-using-imperative-code.md) oraz [wymaganych argumentów i grup przeciążenia](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="ea11a-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
