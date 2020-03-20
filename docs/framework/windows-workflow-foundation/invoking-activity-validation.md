---
title: Wywoływanie walidacji działania
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 1241e6445cde20a192581e8132e563e0f7ca8d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182883"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="b51f0-102">Wywoływanie walidacji działania</span><span class="sxs-lookup"><span data-stu-id="b51f0-102">Invoking Activity Validation</span></span>
<span data-ttu-id="b51f0-103">Sprawdzanie poprawności działania zawiera metodę identyfikowania i raportowania błędów w konfiguracji dowolnego działania przed jego wykonaniem.</span><span class="sxs-lookup"><span data-stu-id="b51f0-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="b51f0-104">Sprawdzanie poprawności występuje, gdy przepływ pracy jest modyfikowany w projektancie przepływu pracy i wszelkie błędy sprawdzania poprawności lub ostrzeżenia są wyświetlane w projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="b51f0-105">Sprawdzanie poprawności występuje również w czasie wykonywania, gdy jest wywoływany <xref:System.Activities.InvalidWorkflowException> przepływ pracy i jeśli wystąpią błędy sprawdzania poprawności, jest generowany przez domyślną logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="b51f0-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="b51f0-106">Windows Workflow Foundation (WF) zapewnia <xref:System.Activities.Validation.ActivityValidationServices> klasę, która może być używana przez aplikacje przepływu pracy i narzędzi deweloperów jawnie sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="b51f0-107">W tym temacie <xref:System.Activities.Validation.ActivityValidationServices> opisano sposób wykonywania sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="b51f0-108">Korzystanie z usługi ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="b51f0-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="b51f0-109"><xref:System.Activities.Validation.ActivityValidationServices>ma <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> dwa przeciążenia, które są używane do wywoływania logiki sprawdzania poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="b51f0-110">Pierwsze przeciążenie ma działanie główne do sprawdzenia poprawności i zwraca kolekcję błędów sprawdzania poprawności i ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="b51f0-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="b51f0-111">W poniższym przykładzie `Add` używane jest działanie niestandardowe, które ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="b51f0-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-112">Działanie `Add` jest używane <xref:System.Activities.Statements.Sequence>wewnątrz , ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-113">Ten przepływ pracy można sprawdzić, dzwoniąc <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="b51f0-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="b51f0-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>zwraca kolekcję błędów sprawdzania poprawności lub ostrzeżeń zawartych przez działanie i wszystkie elementy podrzędne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-115">Po <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> wywołaniu tego przykładowego przepływu pracy zwracane są dwa błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="b51f0-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="b51f0-116">**Błąd: wartość wymaganego argumentu działania "Operand2" nie została dostarczona.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="b51f0-117">**Błąd: wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="b51f0-118">Jeśli ten przepływ pracy został <xref:System.Activities.InvalidWorkflowException> wywołany, zostanie zgłoszony, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="b51f0-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="b51f0-120">**Podczas przetwarzania drzewa przepływu pracy napotkano następujące błędy:**
 **"Dodaj": wartość wymaganego argumentu działania "Operand2" nie została dostarczona.** 
 **"Dodaj": Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-120">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="b51f0-121">W tym przykładzie przepływu pracy, aby były `Add` prawidłowe, dwa wymagane argumenty działania muszą być powiązane.</span><span class="sxs-lookup"><span data-stu-id="b51f0-121">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="b51f0-122">W poniższym przykładzie dwa wymagane argumenty są powiązane ze zmiennymi przepływu pracy wraz z wartością wyniku.</span><span class="sxs-lookup"><span data-stu-id="b51f0-122">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="b51f0-123">W tym <xref:System.Activities.Activity%601.Result%2A> przykładzie argument jest powiązany wraz z dwoma wymaganymi argumentami.</span><span class="sxs-lookup"><span data-stu-id="b51f0-123">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="b51f0-124">Argument <xref:System.Activities.Activity%601.Result%2A> nie jest wymagane do wiązanego i nie powoduje błąd sprawdzania poprawności, jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="b51f0-124">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="b51f0-125">Jest odpowiedzialny za autora przepływu <xref:System.Activities.Activity%601.Result%2A> pracy do powiązania, jeśli jego wartość jest używana w innym miejscu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-125">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="b51f0-126">Sprawdzanie poprawności wymaganych argumentów w działaniu głównym</span><span class="sxs-lookup"><span data-stu-id="b51f0-126">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="b51f0-127">Jeśli działanie główne przepływu pracy ma argumenty, nie są one powiązane, dopóki nie zostanie wywołany przepływ pracy i parametry są przekazywane do przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-127">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="b51f0-128">Następujący przepływ pracy przekazuje sprawdzanie poprawności, ale wyjątek jest zgłaszany, jeśli przepływ pracy jest wywoływany bez przekazywania w wymaganych argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-128">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-129">**System.ArgumentException: Ustawienia argumentu działania głównego są niepoprawne.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-129">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="b51f0-130">**Poprawkę definicji przepływu pracy lub wartości wejściowych dostawy, aby naprawić te błędy:**
 **"Dodaj": Wartość dla wymaganego argumentu działania "Operand2" nie została dostarczona.** 
 **"Dodaj": Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-130">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="b51f0-131">Po przekazaniu prawidłowych argumentów przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-131">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="b51f0-132">W tym przykładzie działanie główne `Add` zostało `Activity` zadeklarowane jako zamiast jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-132">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="b51f0-133">Dzięki temu `WorkflowInvoker.Invoke` metoda do zwrócenia pojedynczej liczby całkowitej, która reprezentuje wyniki `Add` `out` działania zamiast słownika argumentów.</span><span class="sxs-lookup"><span data-stu-id="b51f0-133">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="b51f0-134">Zmienna `wf` mogła również zostać `Activity<int>`zadeklarowana jako .</span><span class="sxs-lookup"><span data-stu-id="b51f0-134">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="b51f0-135">Podczas sprawdzania poprawności argumentów głównych, jest odpowiedzialny za aplikację hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazywane podczas wywoływania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-135">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="b51f0-136">Wywoływanie sprawdzania poprawności opartej na kodzie imperatywnym</span><span class="sxs-lookup"><span data-stu-id="b51f0-136">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="b51f0-137">Trwać w testapikonietce opartej na kodzie imperatywnym zapewnia <xref:System.Activities.CodeActivity>prosty <xref:System.Activities.AsyncCodeActivity>sposób <xref:System.Activities.NativeActivity>działania w celu zapewnienia sprawdzania poprawności o sobie i jest dostępna dla działań, które wynikają z , i .</span><span class="sxs-lookup"><span data-stu-id="b51f0-137">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="b51f0-138">Kod sprawdzania poprawności, który określa wszelkie błędy sprawdzania poprawności lub ostrzeżenia jest dodawany do działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-138">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="b51f0-139">Gdy sprawdzanie poprawności jest wywoływane na działanie, te ostrzeżenia lub błędy są <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>zawarte w kolekcji zwrócone przez wywołanie do .</span><span class="sxs-lookup"><span data-stu-id="b51f0-139">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="b51f0-140">W poniższym przykładzie zdefiniowano `CreateProduct` działanie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-140">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="b51f0-141">Jeśli `Cost` jest większa `Price`niż , błąd sprawdzania poprawności jest <xref:System.Activities.CodeActivity.CacheMetadata%2A> dodawany do metadanych w zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="b51f0-141">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-142">W tym przykładzie przepływ pracy jest `CreateProduct` skonfigurowany przy użyciu działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-142">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="b51f0-143">W tym przepływie `Cost` pracy jest `Price`większa niż `Description` , a wymagany argument nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="b51f0-143">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="b51f0-144">Po wywołaniu sprawdzania poprawności zwracane są następujące błędy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-144">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-145">**Błąd: Koszt musi być mniejszy lub równy cenie.**</span><span class="sxs-lookup"><span data-stu-id="b51f0-145">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="b51f0-146">**Błąd: nie podano wartości wymaganego argumentu działania "Opis".**</span><span class="sxs-lookup"><span data-stu-id="b51f0-146">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="b51f0-147">Autorzy działań niestandardowych można podać <xref:System.Activities.CodeActivity.CacheMetadata%2A> logikę sprawdzania poprawności w zastąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-147">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="b51f0-148">Wszelkie wyjątki, które <xref:System.Activities.CodeActivity.CacheMetadata%2A> są generowane z nie są traktowane jako błędy sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="b51f0-148">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="b51f0-149">Te wyjątki uciekną <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> od wywołania i muszą być obsługiwane przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b51f0-149">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="b51f0-150">Korzystanie z validationsettings</span><span class="sxs-lookup"><span data-stu-id="b51f0-150">Using ValidationSettings</span></span>  
 <span data-ttu-id="b51f0-151">Domyślnie wszystkie działania w drzewie działań są oceniane, gdy sprawdzanie poprawności jest wywoływane przez <xref:System.Activities.Validation.ActivityValidationServices>program .</span><span class="sxs-lookup"><span data-stu-id="b51f0-151">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="b51f0-152"><xref:System.Activities.Validation.ValidationSettings>umożliwia dostosowanie sprawdzania poprawności na kilka różnych sposobów, konfigurując jej trzy właściwości.</span><span class="sxs-lookup"><span data-stu-id="b51f0-152"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="b51f0-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>określa, czy walidator powinien przejść całe drzewo działania lub zastosować tylko logikę sprawdzania poprawności do dostarczonego działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="b51f0-154">Wartość domyślna dla `false`tej wartości to .</span><span class="sxs-lookup"><span data-stu-id="b51f0-154">The default for this value is `false`.</span></span> <span data-ttu-id="b51f0-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>określa dodatkowe mapowanie ograniczeń z typu do listy ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="b51f0-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="b51f0-156">Dla typu podstawowego każdego działania w sprawdzanym drzewie działań istnieje wyszukiwanie <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>w pliku .</span><span class="sxs-lookup"><span data-stu-id="b51f0-156">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="b51f0-157">Jeśli zostanie znaleziona lista ograniczeń dopasowania, wszystkie ograniczenia na liście są oceniane dla działania.</span><span class="sxs-lookup"><span data-stu-id="b51f0-157">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="b51f0-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>określa, czy walidator powinien oceniać wszystkie <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ograniczenia, czy tylko te określone w pliku .</span><span class="sxs-lookup"><span data-stu-id="b51f0-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="b51f0-159">Wartością domyślną jest `false`.</span><span class="sxs-lookup"><span data-stu-id="b51f0-159">The default value is `false`.</span></span> <span data-ttu-id="b51f0-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hostów przepływu pracy, aby dodać dodatkowe sprawdzanie poprawności dla przepływów pracy, takich jak ograniczenia zasad dla narzędzi, takich jak FxCop.</span><span class="sxs-lookup"><span data-stu-id="b51f0-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="b51f0-161">Aby uzyskać więcej informacji na temat ograniczeń, zobacz [Ograniczenia deklaratywne](declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="b51f0-161">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="b51f0-162">Aby <xref:System.Activities.Validation.ValidationSettings>użyć , skonfiguruj żądane właściwości, <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>a następnie przekaż je w wywołaniu do .</span><span class="sxs-lookup"><span data-stu-id="b51f0-162">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="b51f0-163">W tym przykładzie przepływ pracy, <xref:System.Activities.Statements.Sequence> który `Add` składa się z działania niestandardowego jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="b51f0-163">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="b51f0-164">Działanie `Add` ma dwa wymagane argumenty.</span><span class="sxs-lookup"><span data-stu-id="b51f0-164">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-165">Następujące `Add` działanie jest używane <xref:System.Activities.Statements.Sequence>w , ale jego dwa wymagane argumenty nie są powiązane.</span><span class="sxs-lookup"><span data-stu-id="b51f0-165">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-166">W poniższym przykładzie sprawdzanie <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> poprawności `true`jest wykonywane <xref:System.Activities.Statements.Sequence> z set to , więc tylko działanie główne jest sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="b51f0-166">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="b51f0-167">Ten kod wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b51f0-167">This code displays the following output:</span></span>  
  
 <span data-ttu-id="b51f0-168">**Brak ostrzeżeń i błędów** Mimo że `Add` działanie ma wymagane argumenty, które nie są powiązane, sprawdzanie poprawności zakończy się pomyślnie, ponieważ oceniane jest tylko działanie główne.</span><span class="sxs-lookup"><span data-stu-id="b51f0-168">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="b51f0-169">Ten typ sprawdzania poprawności jest przydatne do sprawdzania poprawności tylko określonych elementów w drzewie działań, takich jak sprawdzanie poprawności zmiany właściwości pojedynczego działania w projektancie.</span><span class="sxs-lookup"><span data-stu-id="b51f0-169">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="b51f0-170">Należy zauważyć, że jeśli ten przepływ pracy jest wywoływany, pełna <xref:System.Activities.InvalidWorkflowException> sprawdzanie poprawności skonfigurowane w przepływie pracy jest oceniane i zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="b51f0-170">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="b51f0-171"><xref:System.Activities.Validation.ActivityValidationServices>i <xref:System.Activities.Validation.ValidationSettings> skonfigurować tylko sprawdzanie poprawności jawnie wywoływane przez hosta, a nie sprawdzanie poprawności, które występuje, gdy wywoływany jest przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="b51f0-171"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
