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
# <a name="invoking-activity-validation"></a>Wywoływanie walidacji działania
Sprawdzanie poprawności działania zawiera metodę identyfikowania i raportowania błędów w konfiguracji dowolnego działania przed jego wykonaniem. Sprawdzanie poprawności występuje, gdy przepływ pracy jest modyfikowany w projektancie przepływu pracy i wszelkie błędy sprawdzania poprawności lub ostrzeżenia są wyświetlane w projektancie przepływu pracy. Sprawdzanie poprawności występuje również w czasie wykonywania, gdy jest wywoływany <xref:System.Activities.InvalidWorkflowException> przepływ pracy i jeśli wystąpią błędy sprawdzania poprawności, jest generowany przez domyślną logikę sprawdzania poprawności. Windows Workflow Foundation (WF) zapewnia <xref:System.Activities.Validation.ActivityValidationServices> klasę, która może być używana przez aplikacje przepływu pracy i narzędzi deweloperów jawnie sprawdzania poprawności działania. W tym temacie <xref:System.Activities.Validation.ActivityValidationServices> opisano sposób wykonywania sprawdzania poprawności działania.  
  
## <a name="using-activityvalidationservices"></a>Korzystanie z usługi ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices>ma <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> dwa przeciążenia, które są używane do wywoływania logiki sprawdzania poprawności działania. Pierwsze przeciążenie ma działanie główne do sprawdzenia poprawności i zwraca kolekcję błędów sprawdzania poprawności i ostrzeżenia. W poniższym przykładzie `Add` używane jest działanie niestandardowe, które ma dwa wymagane argumenty.  
  
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
  
 Działanie `Add` jest używane <xref:System.Activities.Statements.Sequence>wewnątrz , ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie.  
  
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
  
 Ten przepływ pracy można sprawdzić, dzwoniąc <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>zwraca kolekcję błędów sprawdzania poprawności lub ostrzeżeń zawartych przez działanie i wszystkie elementy podrzędne, jak pokazano w poniższym przykładzie.  
  
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
  
 Po <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> wywołaniu tego przykładowego przepływu pracy zwracane są dwa błędy sprawdzania poprawności.  
  
 **Błąd: wartość wymaganego argumentu działania "Operand2" nie została dostarczona.**  
**Błąd: wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**  Jeśli ten przepływ pracy został <xref:System.Activities.InvalidWorkflowException> wywołany, zostanie zgłoszony, jak pokazano w poniższym przykładzie.  
  
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
  
 **System.Activities.InvalidWorkflowException:**  
**Podczas przetwarzania drzewa przepływu pracy napotkano następujące błędy:**
 **"Dodaj": wartość wymaganego argumentu działania "Operand2" nie została dostarczona.** 
 **"Dodaj": Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**  W tym przykładzie przepływu pracy, aby były `Add` prawidłowe, dwa wymagane argumenty działania muszą być powiązane. W poniższym przykładzie dwa wymagane argumenty są powiązane ze zmiennymi przepływu pracy wraz z wartością wyniku. W tym <xref:System.Activities.Activity%601.Result%2A> przykładzie argument jest powiązany wraz z dwoma wymaganymi argumentami. Argument <xref:System.Activities.Activity%601.Result%2A> nie jest wymagane do wiązanego i nie powoduje błąd sprawdzania poprawności, jeśli nie jest. Jest odpowiedzialny za autora przepływu <xref:System.Activities.Activity%601.Result%2A> pracy do powiązania, jeśli jego wartość jest używana w innym miejscu w przepływie pracy.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Sprawdzanie poprawności wymaganych argumentów w działaniu głównym  
 Jeśli działanie główne przepływu pracy ma argumenty, nie są one powiązane, dopóki nie zostanie wywołany przepływ pracy i parametry są przekazywane do przepływu pracy. Następujący przepływ pracy przekazuje sprawdzanie poprawności, ale wyjątek jest zgłaszany, jeśli przepływ pracy jest wywoływany bez przekazywania w wymaganych argumentów, jak pokazano w poniższym przykładzie.  
  
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
  
 **System.ArgumentException: Ustawienia argumentu działania głównego są niepoprawne.**  
**Poprawkę definicji przepływu pracy lub wartości wejściowych dostawy, aby naprawić te błędy:**
 **"Dodaj": Wartość dla wymaganego argumentu działania "Operand2" nie została dostarczona.** 
 **"Dodaj": Wartość wymaganego argumentu działania "Operand1" nie została dostarczona.**  Po przekazaniu prawidłowych argumentów przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.  
  
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
> W tym przykładzie działanie główne `Add` zostało `Activity` zadeklarowane jako zamiast jak w poprzednim przykładzie. Dzięki temu `WorkflowInvoker.Invoke` metoda do zwrócenia pojedynczej liczby całkowitej, która reprezentuje wyniki `Add` `out` działania zamiast słownika argumentów. Zmienna `wf` mogła również zostać `Activity<int>`zadeklarowana jako .  
  
 Podczas sprawdzania poprawności argumentów głównych, jest odpowiedzialny za aplikację hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazywane podczas wywoływania przepływu pracy.  
  
### <a name="invoking-imperative-code-based-validation"></a>Wywoływanie sprawdzania poprawności opartej na kodzie imperatywnym

Trwać w testapikonietce opartej na kodzie imperatywnym zapewnia <xref:System.Activities.CodeActivity>prosty <xref:System.Activities.AsyncCodeActivity>sposób <xref:System.Activities.NativeActivity>działania w celu zapewnienia sprawdzania poprawności o sobie i jest dostępna dla działań, które wynikają z , i . Kod sprawdzania poprawności, który określa wszelkie błędy sprawdzania poprawności lub ostrzeżenia jest dodawany do działania. Gdy sprawdzanie poprawności jest wywoływane na działanie, te ostrzeżenia lub błędy są <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>zawarte w kolekcji zwrócone przez wywołanie do . W poniższym przykładzie zdefiniowano `CreateProduct` działanie. Jeśli `Cost` jest większa `Price`niż , błąd sprawdzania poprawności jest <xref:System.Activities.CodeActivity.CacheMetadata%2A> dodawany do metadanych w zastąpienia.  
  
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
  
 W tym przykładzie przepływ pracy jest `CreateProduct` skonfigurowany przy użyciu działania. W tym przepływie `Cost` pracy jest `Price`większa niż `Description` , a wymagany argument nie jest ustawiony. Po wywołaniu sprawdzania poprawności zwracane są następujące błędy.  
  
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
  
 **Błąd: Koszt musi być mniejszy lub równy cenie.**  
**Błąd: nie podano wartości wymaganego argumentu działania "Opis".**
> [!NOTE]
> Autorzy działań niestandardowych można podać <xref:System.Activities.CodeActivity.CacheMetadata%2A> logikę sprawdzania poprawności w zastąpienia działania. Wszelkie wyjątki, które <xref:System.Activities.CodeActivity.CacheMetadata%2A> są generowane z nie są traktowane jako błędy sprawdzania poprawności. Te wyjątki uciekną <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> od wywołania i muszą być obsługiwane przez wywołującego.  
  
## <a name="using-validationsettings"></a>Korzystanie z validationsettings  
 Domyślnie wszystkie działania w drzewie działań są oceniane, gdy sprawdzanie poprawności jest wywoływane przez <xref:System.Activities.Validation.ActivityValidationServices>program . <xref:System.Activities.Validation.ValidationSettings>umożliwia dostosowanie sprawdzania poprawności na kilka różnych sposobów, konfigurując jej trzy właściwości. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>określa, czy walidator powinien przejść całe drzewo działania lub zastosować tylko logikę sprawdzania poprawności do dostarczonego działania. Wartość domyślna dla `false`tej wartości to . <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>określa dodatkowe mapowanie ograniczeń z typu do listy ograniczeń. Dla typu podstawowego każdego działania w sprawdzanym drzewie działań istnieje wyszukiwanie <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>w pliku . Jeśli zostanie znaleziona lista ograniczeń dopasowania, wszystkie ograniczenia na liście są oceniane dla działania. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>określa, czy walidator powinien oceniać wszystkie <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>ograniczenia, czy tylko te określone w pliku . Wartością domyślną jest `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hostów przepływu pracy, aby dodać dodatkowe sprawdzanie poprawności dla przepływów pracy, takich jak ograniczenia zasad dla narzędzi, takich jak FxCop. Aby uzyskać więcej informacji na temat ograniczeń, zobacz [Ograniczenia deklaratywne](declarative-constraints.md).  
  
 Aby <xref:System.Activities.Validation.ValidationSettings>użyć , skonfiguruj żądane właściwości, <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>a następnie przekaż je w wywołaniu do . W tym przykładzie przepływ pracy, <xref:System.Activities.Statements.Sequence> który `Add` składa się z działania niestandardowego jest sprawdzany. Działanie `Add` ma dwa wymagane argumenty.  
  
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
  
 Następujące `Add` działanie jest używane <xref:System.Activities.Statements.Sequence>w , ale jego dwa wymagane argumenty nie są powiązane.  
  
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
  
 W poniższym przykładzie sprawdzanie <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> poprawności `true`jest wykonywane <xref:System.Activities.Statements.Sequence> z set to , więc tylko działanie główne jest sprawdzane.  
  
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
  
 Ten kod wyświetla następujące dane wyjściowe:  
  
 **Brak ostrzeżeń i błędów** Mimo że `Add` działanie ma wymagane argumenty, które nie są powiązane, sprawdzanie poprawności zakończy się pomyślnie, ponieważ oceniane jest tylko działanie główne. Ten typ sprawdzania poprawności jest przydatne do sprawdzania poprawności tylko określonych elementów w drzewie działań, takich jak sprawdzanie poprawności zmiany właściwości pojedynczego działania w projektancie. Należy zauważyć, że jeśli ten przepływ pracy jest wywoływany, pełna <xref:System.Activities.InvalidWorkflowException> sprawdzanie poprawności skonfigurowane w przepływie pracy jest oceniane i zostanie zgłoszony. <xref:System.Activities.Validation.ActivityValidationServices>i <xref:System.Activities.Validation.ValidationSettings> skonfigurować tylko sprawdzanie poprawności jawnie wywoływane przez hosta, a nie sprawdzanie poprawności, które występuje, gdy wywoływany jest przepływ pracy.
