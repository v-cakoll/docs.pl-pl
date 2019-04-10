---
title: Zmienne i argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 29ce5222435b68ed13cbc967e58e72a937625e8e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320746"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="03a02-102">Zmienne i argumenty</span><span class="sxs-lookup"><span data-stu-id="03a02-102">Variables and Arguments</span></span>
<span data-ttu-id="03a02-103">W Windows Workflow Foundation (WF), zmienne reprezentują przechowywania danych i argumenty reprezentują przepływ danych do i z działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="03a02-104">Działanie ma zestawu argumentów i stanowią one podpis działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="03a02-105">Ponadto działanie może zachować listę zmiennych, do których Deweloper można dodawać i usuwać zmiennych podczas projektowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="03a02-106">Argument jest powiązany za pomocą wyrażenia, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="03a02-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="03a02-107">Zmienne</span><span class="sxs-lookup"><span data-stu-id="03a02-107">Variables</span></span>  
 <span data-ttu-id="03a02-108">Zmienne są lokalizacje magazynu dla danych.</span><span class="sxs-lookup"><span data-stu-id="03a02-108">Variables are storage locations for data.</span></span> <span data-ttu-id="03a02-109">Zmienne są deklarowane jako część definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="03a02-110">Zmienne przyjmą wartości w czasie wykonywania, a te wartości są przechowywane jako część stanu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="03a02-111">Definicja zmiennej określa typ zmiennej, i opcjonalnie nazwy.</span><span class="sxs-lookup"><span data-stu-id="03a02-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="03a02-112">Poniższy kod pokazuje sposób deklarowania zmiennych, przypisz wartości do niego przy użyciu <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetl jego wartość za pomocą konsoli <xref:System.Activities.Statements.WriteLine> działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="03a02-113">Opcjonalnie można określić wyrażenie wartości domyślnej jako część deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="03a02-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="03a02-114">Zmienne również może mieć modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="03a02-114">Variables also can have modifiers.</span></span> <span data-ttu-id="03a02-115">Aby uzyskać przykład, jeśli zmienna jest tylko do odczytu, a następnie tylko do odczytu <xref:System.Activities.VariableModifiers> modyfikator mogą być stosowane.</span><span class="sxs-lookup"><span data-stu-id="03a02-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="03a02-116">W poniższym przykładzie utworzono zmiennej tylko do odczytu, która ma przypisaną wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="03a02-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="03a02-117">Zmienna zakresu</span><span class="sxs-lookup"><span data-stu-id="03a02-117">Variable Scoping</span></span>  
 <span data-ttu-id="03a02-118">Okres istnienia zmiennej w czasie wykonywania jest równy okres istnienia działania, który deklaruje ją.</span><span class="sxs-lookup"><span data-stu-id="03a02-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="03a02-119">Po ukończeniu działania swoje zmienne są wyczyszczone, a nie będzie można się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="03a02-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="03a02-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="03a02-120">Arguments</span></span>  
 <span data-ttu-id="03a02-121">Autorzy działania używać argumentów do definiowania danych sposób przepływy do i z działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="03a02-122">Każdy argument ma określony kierunek: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, lub <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="03a02-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="03a02-123">Środowisko wykonawcze przepływów pracy zapewnia następujące gwarancje, dotyczące czas przenoszenia danych do i z działań:</span><span class="sxs-lookup"><span data-stu-id="03a02-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="03a02-124">Po uruchomieniu działania wykonywania jest obliczany wartości wszystkich argumentów wejściowych i wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="03a02-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="03a02-125">Na przykład, niezależnie od tego, kiedy <xref:System.Activities.Argument.Get%2A> jest wywoływana, wartość zwracana jest ten, który jest obliczana przez środowisko wykonawcze przed jej wywołanie `Execute`.</span><span class="sxs-lookup"><span data-stu-id="03a02-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="03a02-126">Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe ustawia wartość natychmiast.</span><span class="sxs-lookup"><span data-stu-id="03a02-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="03a02-127">Argumenty mogą opcjonalnie mieć ich <xref:System.Activities.Argument.EvaluationOrder%2A> określony.</span><span class="sxs-lookup"><span data-stu-id="03a02-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <xref:System.Activities.Argument.EvaluationOrder%2A> <span data-ttu-id="03a02-128">jest liczony od zera wartość, która określa kolejność szacowania argumentu.</span><span class="sxs-lookup"><span data-stu-id="03a02-128">is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="03a02-129">Domyślnie kolejność oceny argument jest nieokreślony i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartość.</span><span class="sxs-lookup"><span data-stu-id="03a02-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="03a02-130">Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> na wartość większą lub równą zero, aby określić kolejność obliczania dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="03a02-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="03a02-131">Windows Workflow Foundation ocenia argumenty w kolejności określonej wersji ewaluacyjnej, w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="03a02-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="03a02-132">Należy pamiętać, że argumenty z kolejnością nieokreślony oceny są obliczane przed elementami o kolejność oceny określonej.</span><span class="sxs-lookup"><span data-stu-id="03a02-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="03a02-133">Autor aktywności można użyć silnie typizowane mechanizm do udostępniania jej argumentów.</span><span class="sxs-lookup"><span data-stu-id="03a02-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="03a02-134">Jest to realizowane przez zadeklarowanie właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="03a02-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="03a02-135">Dzięki temu Autor działania ustalenie określonej umowy o dane przesyłane do i z działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="03a02-136">Definiowanie argumenty w działaniu</span><span class="sxs-lookup"><span data-stu-id="03a02-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="03a02-137">Argumenty można zdefiniować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="03a02-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="03a02-138">Poniższy kod przedstawia sposób definiowania argumenty `Prompt` działanie, które przyjmuje w ciągu do wyświetlania użytkownikowi i zwraca ciąg, który zawiera odpowiedź użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03a02-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="03a02-139">Działania, które zwraca pojedynczą wartość może pochodzić z <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, lub <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="03a02-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="03a02-140">Te działania muszą być dobrze zdefiniowane <xref:System.Activities.OutArgument%601> o nazwie <xref:System.Activities.Activity%601.Result%2A> zawierający wartość zwracaną przez działanie.</span><span class="sxs-lookup"><span data-stu-id="03a02-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="03a02-141">Używanie zmienne i argumenty w przepływach pracy</span><span class="sxs-lookup"><span data-stu-id="03a02-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="03a02-142">Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="03a02-143">Przepływ pracy jest sekwencji, która deklaruje trzy zmienne: `var1`, `var2`, i `var3`.</span><span class="sxs-lookup"><span data-stu-id="03a02-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="03a02-144">Pierwsze działanie w przepływie pracy jest `Assign` działanie, które przypisuje wartość zmiennej `var1` do zmiennej `var2`.</span><span class="sxs-lookup"><span data-stu-id="03a02-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="03a02-145">Następuje to `WriteLine` działań, która drukuje wartość `var2` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="03a02-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="03a02-146">Następnie jest kolejnym `Assign` działanie, które przypisuje wartość zmiennej `var2` do zmiennej `var3`.</span><span class="sxs-lookup"><span data-stu-id="03a02-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="03a02-147">Na koniec istnieje inny `WriteLine` działań, która drukuje wartość `var3` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="03a02-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="03a02-148">Pierwszy `Assign` używa działania `InArgument<string>` i `OutArgument<string>` obiekty reprezentujące jawnie powiązania dla argumentów tego działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> `InArgument<string>` <span data-ttu-id="03a02-149">Służy do <xref:System.Activities.Statements.Assign.Value%2A> ponieważ wartość będą przepływać do <xref:System.Activities.Statements.Assign%601> działania za pośrednictwem jego <xref:System.Activities.Statements.Assign.Value%2A> argument i `OutArgument<string>` służy do <xref:System.Activities.Statements.Assign.To%2A> ponieważ wartość będą przepływać z <xref:System.Activities.Statements.Assign.To%2A> argument do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="03a02-149">is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="03a02-150">Drugi `Assign` działanie wykonuje ten sam efekt więcej compact ale równoważne składnia, która używa niejawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="03a02-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="03a02-151">`WriteLine` Działania również użyć zwięzłą składnią.</span><span class="sxs-lookup"><span data-stu-id="03a02-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="03a02-152">Za pomocą zmienne i argumenty w działaniach oparte na kodzie</span><span class="sxs-lookup"><span data-stu-id="03a02-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="03a02-153">Sposób używania argumentów i zmiennych w przepływach pracy i deklaratywne działania można znaleźć w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="03a02-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="03a02-154">Zmienne i argumenty są również używane w działaniach oparte na kodzie.</span><span class="sxs-lookup"><span data-stu-id="03a02-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="03a02-155">Koncepcyjnie użycie jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="03a02-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="03a02-156">Zmienne reprezentowania magazynu danych w ramach działania, a argumenty reprezentują przepływ danych do lub z działalności i są powiązane reprezentujące, gdzie dane są wczytywane do lub z innych zmienne i argumenty w przepływie pracy Autor przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="03a02-157">Do pobierania lub zestaw, który należy użyć wartości zmiennej lub argumentu w działaniu, kontekst działania reprezentujący bieżące środowisko wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="03a02-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="03a02-158">Te informacje są przekazywane do <xref:System.Activities.CodeActivity%601.Execute%2A> sposób działania w czasie wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="03a02-159">W tym przykładzie niestandardową `Add` działania jest zdefiniowany, który ma dwa <xref:System.Activities.ArgumentDirection.In> argumentów.</span><span class="sxs-lookup"><span data-stu-id="03a02-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="03a02-160">Aby uzyskać dostęp do wartości argumentów, <xref:System.Activities.Argument.Get%2A> metoda jest używana i jest używany w kontekście, która została przekazana przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="03a02-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="03a02-161">Aby uzyskać więcej informacji na temat pracy z argumentami, zmienne i wyrażenia w kodzie, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md) i [wymagane argumenty i grupy przeciążenia](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="03a02-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
