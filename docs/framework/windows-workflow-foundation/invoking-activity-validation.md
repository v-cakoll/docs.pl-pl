---
title: Wywoływanie walidacji działania
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 61491e906bfc58bbd19cf43a5980b2781493411b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035139"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="4eb60-102">Wywoływanie walidacji działania</span><span class="sxs-lookup"><span data-stu-id="4eb60-102">Invoking Activity Validation</span></span>
<span data-ttu-id="4eb60-103">Działanie sprawdzania poprawności zapewnia metodę, aby zidentyfikować i raportowania błędów w konfiguracji dowolne działanie przed jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="4eb60-104">Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i żadnych ostrzeżeń ani błędów sprawdzania poprawności, które są wyświetlane w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="4eb60-105">Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez domyślną logikę weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="4eb60-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="4eb60-106">Windows Workflow Foundation (WF) zapewnia <xref:System.Activities.Validation.ActivityValidationServices> klasę, która może służyć przez aplikacji przepływu pracy i deweloperom narzędzia do jawnie sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="4eb60-107">W tym temacie opisano sposób użycia <xref:System.Activities.Validation.ActivityValidationServices> do wykonywania sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="4eb60-108">Za pomocą ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="4eb60-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="4eb60-109"><xref:System.Activities.Validation.ActivityValidationServices> ma dwa <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> przeciążenia, które są używane do wywołania logiki sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="4eb60-110">Pierwsze przeciążenie przyjmuje działania głównego, aby zostać uwierzytelnionym i zwraca kolekcję błędy i ostrzeżenia walidacji.</span><span class="sxs-lookup"><span data-stu-id="4eb60-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="4eb60-111">W poniższym przykładzie niestandardową `Add` działanie jest używane, że ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="4eb60-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="4eb60-112">`Add` Działania jest używana wewnątrz <xref:System.Activities.Statements.Sequence>, ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="4eb60-113">Ten przepływ pracy można zweryfikować przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="4eb60-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Zwraca kolekcję wszelkie błędy sprawdzania poprawności lub ostrzeżenia zawarte działanie i żadnych elementów podrzędnych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="4eb60-115">Gdy <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> jest wywoływana w tym przykładowym przepływie pracy dwóch sprawdzania poprawności są zwracane błędy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="4eb60-116">**Błąd: Nie podano wartości argumentu wymagane działania 'Operand2'.**</span><span class="sxs-lookup"><span data-stu-id="4eb60-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="4eb60-117">**Błąd: Nie podano wartości argumentu wymagane działania "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="4eb60-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="4eb60-118">Jeśli ten przepływ pracy został wywołany, <xref:System.Activities.InvalidWorkflowException> może zostać zgłoszone, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="4eb60-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="4eb60-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="4eb60-120">**Napotkano następujące błędy podczas przetwarzania drzewa przepływu pracy:** </span><span class="sxs-lookup"><span data-stu-id="4eb60-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="4eb60-121">**"Dodaj": wartość argumentu w postaci wymagane działania 'Operand2' nie został dostarczony.** </span><span class="sxs-lookup"><span data-stu-id="4eb60-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="4eb60-122">**"Dodaj": wartość argumentu w postaci wymagane działania "Operand1" nie został podany.**</span><span class="sxs-lookup"><span data-stu-id="4eb60-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="4eb60-123">Dla tego przykładowego przepływu pracy był prawidłowy, dwa wymagane argumenty `Add` działanie musi być powiązana.</span><span class="sxs-lookup"><span data-stu-id="4eb60-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="4eb60-124">W poniższym przykładzie dwa wymagane argumenty są powiązane z zmienne przepływu pracy oraz wartość wyniku.</span><span class="sxs-lookup"><span data-stu-id="4eb60-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="4eb60-125">W tym przykładzie <xref:System.Activities.Activity%601.Result%2A> argument jest powiązana wraz z dwóch wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="4eb60-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="4eb60-126"><xref:System.Activities.Activity%601.Result%2A> Argument nie jest wymagana z oświadczeniem i nie powoduje błąd sprawdzania poprawności, jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="4eb60-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="4eb60-127">Jest odpowiedzialny za tworzenie przepływu pracy można powiązać <xref:System.Activities.Activity%601.Result%2A> jeśli jego wartość jest używana w innym miejscu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="4eb60-128">Sprawdzanie poprawności wymagane argumenty dla działania głównego</span><span class="sxs-lookup"><span data-stu-id="4eb60-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="4eb60-129">Jeśli działanie główne przepływu pracy zawiera argumenty, te nie są powiązane aż do przepływu pracy jest wywoływany i parametry są przekazywane do przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="4eb60-130">Poniższy przepływ pracy pozytywnie zweryfikowane, ale wyjątek jest generowany, jeśli przepływ pracy jest wywoływane bez przekazywania w wymaganych argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="4eb60-131">**System.ArgumentException: Działania głównego ustawienia argumentów są nieprawidłowe.**</span><span class="sxs-lookup"><span data-stu-id="4eb60-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="4eb60-132">**Napraw definicji przepływu pracy lub podać wartości wejściowe, aby naprawić te błędy:** </span><span class="sxs-lookup"><span data-stu-id="4eb60-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="4eb60-133">**"Dodaj": wartość argumentu w postaci wymagane działania 'Operand2' nie został dostarczony.** </span><span class="sxs-lookup"><span data-stu-id="4eb60-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="4eb60-134">**"Dodaj": wartość argumentu w postaci wymagane działania "Operand1" nie został podany.**</span><span class="sxs-lookup"><span data-stu-id="4eb60-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="4eb60-135">Po poprawne argumenty są przekazywane, przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="4eb60-136">W tym przykładzie działania głównego został zadeklarowany jako `Add` zamiast `Activity` co w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="4eb60-137">Dzięki temu `WorkflowInvoker.Invoke` metody, aby przywrócić pojedyncze liczby całkowite, który reprezentuje wyniki `Add` zamiast słownik `out` argumentów.</span><span class="sxs-lookup"><span data-stu-id="4eb60-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="4eb60-138">Zmienna `wf` może być także zadeklarowana jako `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="4eb60-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="4eb60-139">Podczas sprawdzania poprawności argumentów głównego, spoczywa aplikacji hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazywane podczas wywoływania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="4eb60-140">Wywoływanie Imperatywne sprawdzanie poprawności, które są oparte na kodzie</span><span class="sxs-lookup"><span data-stu-id="4eb60-140">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="4eb60-141">Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i jest dostępny dla działań, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="4eb60-142">Kod sprawdzania poprawności, który określa żadnych ostrzeżeń ani błędów sprawdzania poprawności jest dodawany do działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="4eb60-143">Podczas sprawdzania poprawności na działanie, te ostrzeżenia i błędy są zawarte w zbiorze zwróconym przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="4eb60-144">W poniższym przykładzie `CreateProduct` działania jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4eb60-144">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="4eb60-145">Jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="4eb60-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="4eb60-146">W tym przykładzie przepływ pracy jest skonfigurowany przy użyciu `CreateProduct` działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="4eb60-147">W tym przepływie pracy `Cost` jest większa niż `Price`, a także wymagane `Description` argument nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="4eb60-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="4eb60-148">Podczas sprawdzania poprawności, zwracane są następujące błędy.</span><span class="sxs-lookup"><span data-stu-id="4eb60-148">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =   
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="4eb60-149">**Błąd: Koszt musi być większa niż cena.**</span><span class="sxs-lookup"><span data-stu-id="4eb60-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="4eb60-150">**Błąd: Nie podano wartości argumentu wymagane działania "Opis".**</span><span class="sxs-lookup"><span data-stu-id="4eb60-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="4eb60-151">Niestandardowe działanie autorzy mogą udostępniać logikę weryfikacji w działaniu <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="4eb60-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="4eb60-152">Wszelkie wyjątki, które są generowane przez <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4eb60-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="4eb60-153">Wyjątki te będą uciekały z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4eb60-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="4eb60-154">Za pomocą ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="4eb60-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="4eb60-155">Domyślnie wszystkie działania w drzewie działania są oceniane podczas sprawdzania poprawności jest wywoływana przez <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="4eb60-156"><xref:System.Activities.Validation.ValidationSettings> Umożliwia sprawdzanie poprawności można dostosować na kilka różnych sposobów, konfigurując jego trzy właściwości.</span><span class="sxs-lookup"><span data-stu-id="4eb60-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="4eb60-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Określa, czy moduł weryfikacji powinny przejść przez drzewo działanie całej dotyczą tylko logikę weryfikacji podanej działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="4eb60-158">Wartością domyślną dla tej wartości jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4eb60-158">The default for this value is `false`.</span></span> <span data-ttu-id="4eb60-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Określa dodatkowe ograniczenia mapowanie z typu do listy ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="4eb60-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="4eb60-160">Typ podstawowy elementu każde działanie w drzewie działanie sprawdzania poprawności jest wyszukiwanie w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="4eb60-161">Jeśli zostanie znalezione pasujące lista ograniczeń, wszystkie ograniczenia na liście są oceniane pod kątem działania.</span><span class="sxs-lookup"><span data-stu-id="4eb60-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="4eb60-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Określa, czy moduł weryfikacji należy ocenić wszystkie ograniczenia lub tylko te określone w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="4eb60-163">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4eb60-163">The default value is `false`.</span></span> <span data-ttu-id="4eb60-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hosta przepływu pracy dodać dodatkowe sprawdzanie poprawności dla przepływów pracy, takich jak zasady ograniczeń dla narzędzi, takich jak programu FxCop.</span><span class="sxs-lookup"><span data-stu-id="4eb60-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="4eb60-165">Aby uzyskać więcej informacji na temat ograniczeń, zobacz [ograniczenia deklaratywne](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="4eb60-165">For more information about constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="4eb60-166">Aby użyć <xref:System.Activities.Validation.ValidationSettings>skonfiguruj żądane właściwości, a następnie przekazać go w wywołaniu <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4eb60-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="4eb60-167">W tym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> za pomocą niestandardowego `Add` działania jest weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="4eb60-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="4eb60-168">`Add` Działanie ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="4eb60-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="4eb60-169">Następujące `Add` działania jest używana w <xref:System.Activities.Statements.Sequence>, ale jego dwóch wymagane argumenty nie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="4eb60-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="4eb60-170">W poniższym przykładzie, sprawdzanie poprawności jest wykonywane przy użyciu <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> równa `true`, więc tylko główny <xref:System.Activities.Statements.Sequence> działania jest weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="4eb60-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="4eb60-171">Ten kod wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4eb60-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="4eb60-172">**Żadne ostrzeżenia ani błędy** mimo że `Add` działania wymaga argumentów, które nie są powiązane, weryfikacja zakończy się pomyślnie, ponieważ jest oceniane tylko działania głównego.</span><span class="sxs-lookup"><span data-stu-id="4eb60-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="4eb60-173">Tego rodzaju Walidacja przydaje się do sprawdzania poprawności tylko określone elementy w drzewie działania, takie jak weryfikacja zmianę właściwości jedno działanie w projektancie.</span><span class="sxs-lookup"><span data-stu-id="4eb60-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="4eb60-174">Należy pamiętać, jeśli ten przepływ pracy zostanie wywołana, pełna Walidacja skonfigurowany w przepływie pracy jest obliczane i <xref:System.Activities.InvalidWorkflowException> może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="4eb60-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="4eb60-175"><xref:System.Activities.Validation.ActivityValidationServices> i <xref:System.Activities.Validation.ValidationSettings> skonfigurować tylko sprawdzanie poprawności jawnie wywoływane przez hosta i nie występuje, gdy jest wywoływana przez przepływ pracy weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="4eb60-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
