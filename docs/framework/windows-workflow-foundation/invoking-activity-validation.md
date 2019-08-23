---
title: Wywoływanie walidacji działania
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: b45840081f5fc142cf3ec88853dea984b204c9d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934976"
---
# <a name="invoking-activity-validation"></a>Wywoływanie walidacji działania
Walidacja działań zapewnia metodę w celu identyfikowania i zgłaszania błędów w konfiguracji dowolnego działania przed jego wykonaniem. Walidacja występuje, gdy przepływ pracy jest modyfikowany w Projektancie przepływu pracy, a wszystkie błędy lub ostrzeżenia dotyczące walidacji są wyświetlane w Projektancie przepływu pracy. Sprawdzanie poprawności występuje również w czasie wykonywania, gdy przepływ pracy jest wywoływany, a jeśli wystąpią <xref:System.Activities.InvalidWorkflowException> błędy walidacji, jest generowany przez domyślną logikę walidacji. Windows Workflow Foundation (WF) zawiera <xref:System.Activities.Validation.ActivityValidationServices> klasę, która może być używana przez deweloperów aplikacji i narzędzi do pracy w celu jawnego sprawdzania poprawności działania. W tym temacie opisano sposób użycia <xref:System.Activities.Validation.ActivityValidationServices> programu w celu przeprowadzenia walidacji działania.  
  
## <a name="using-activityvalidationservices"></a>Korzystanie z ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices>ma dwa <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> przeciążenia, które są używane do wywołania logiki walidacji działania. Pierwsze Przeciążenie powoduje sprawdzenie poprawności działania głównego i zwrócenie kolekcji błędów i ostrzeżeń walidacji. W poniższym przykładzie użyto niestandardowego `Add` działania, które ma dwa wymagane argumenty.  
  
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
  
 To działanie jest używane wewnątrz, ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie. <xref:System.Activities.Statements.Sequence> `Add`  
  
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
  
 Ten przepływ pracy można zweryfikować, wywołując <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>metodę. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Zwraca kolekcję błędów walidacji lub ostrzeżeń zawartych w działaniu i wszelkich elementów podrzędnych, jak pokazano w poniższym przykładzie.  
  
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
  
 Gdy <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> jest wywoływana dla tego przykładowego przepływu pracy, zwracane są dwa błędy walidacji.  
  
 **Błąd: Nie podano wartości dla wymaganego argumentu działania "Operand2".**  
**Błąd: Nie podano wartości dla wymaganego argumentu działania "Operand1".**  Jeśli ten przepływ pracy został wywołany <xref:System.Activities.InvalidWorkflowException> , zostałby zgłoszony, jak pokazano w poniższym przykładzie.  
  
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
  
 **System. Activities. InvalidWorkflowException:**  
**Napotkano następujące błędy podczas przetwarzania drzewa przepływu pracy:**    
**"Dodaj": Nie podano wartości dla wymaganego argumentu działania "Operand2".**    
**"Dodaj": Nie podano wartości dla wymaganego argumentu działania "Operand1".**  Aby ten przykładowy przepływ pracy był prawidłowy, muszą być powiązane dwa wymagane argumenty `Add` działania. W poniższym przykładzie dwa wymagane argumenty są powiązane ze zmiennymi przepływu pracy wraz z wartością wyniku. W tym przykładzie <xref:System.Activities.Activity%601.Result%2A> argument jest powiązany wraz z dwoma wymaganymi argumentami. <xref:System.Activities.Activity%601.Result%2A> Argument nie musi być powiązany i nie powoduje błędu walidacji, jeśli nie jest. Jest odpowiedzialny za utworzenie powiązania <xref:System.Activities.Activity%601.Result%2A> przez autora przepływu pracy, jeśli jego wartość jest używana w innym miejscu w przepływie pracy.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Weryfikowanie wymaganych argumentów dla działania głównego  
 Jeśli działanie główne przepływu pracy ma argumenty, nie są one powiązane, dopóki przepływ pracy nie zostanie wywołany, a parametry są przekazane do przepływu pracy. Następujący przepływ pracy przeszedł sprawdzanie poprawności, ale jest generowany wyjątek, jeśli przepływ pracy jest wywoływany bez przekazywania w wymaganych argumentach, jak pokazano w poniższym przykładzie.  
  
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
  
 **System.ArgumentException: Ustawienia argumentu działania głównego są nieprawidłowe.**  
**Popraw definicję przepływu pracy lub podaj wartości wejściowe, aby naprawić te błędy:**    
**"Dodaj": Nie podano wartości dla wymaganego argumentu działania "Operand2".**    
**"Dodaj": Nie podano wartości dla wymaganego argumentu działania "Operand1".**  Po przekazaniu prawidłowych argumentów przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.  
  
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
> W tym przykładzie działanie główne zostało zadeklarowane jako `Add` `Activity` zamiast tak jak w poprzednim przykładzie. Dzięki temu `WorkflowInvoker.Invoke` Metoda zwraca pojedynczą liczbę całkowitą, która reprezentuje wyniki `Add` działania `out` zamiast słownika argumentów. Zmienna `wf` mogła być również zadeklarowana jako `Activity<int>`.  
  
 Podczas sprawdzania poprawności argumentów głównych jest odpowiedzialna aplikacja hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazane po wywołaniu przepływu pracy.  
  
### <a name="invoking-imperative-code-based-validation"></a>Wywoływanie bezwzględnej walidacji opartej na kodzie

Bezwzględna Walidacja oparta na kodzie zapewnia prosty sposób, aby działanie zapewniało jego weryfikację i jest dostępne dla działań, które <xref:System.Activities.CodeActivity>pochodzą <xref:System.Activities.AsyncCodeActivity>z, <xref:System.Activities.NativeActivity>i. Kod sprawdzania poprawności, który określa wszelkie błędy walidacji lub ostrzeżenia są dodawane do działania. Po wywołaniu walidacji dla działania te ostrzeżenia lub błędy są zawarte w kolekcji zwróconej przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. W poniższym przykładzie `CreateProduct` zdefiniowano działanie. Jeśli wartość `Price` <xref:System.Activities.CodeActivity.CacheMetadata%2A> jest większa niż, do metadanych w przesłonięciu zostanie dodany błąd walidacji. `Cost`  
  
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
  
 W tym przykładzie przepływ pracy jest konfigurowany za pomocą `CreateProduct` działania. W tym przepływie pracy `Cost` jest większy `Price`niż, a wymagany `Description` argument nie jest ustawiony. Po wywołaniu walidacji zwracane są następujące błędy.  
  
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
  
 **Błąd: Koszt nie może być większy niż cena.**  
**Błąd: Nie podano wartości dla wymaganego argumentu działania "Description".**    
> [!NOTE]
> Autorzy działań niestandardowych mogą zapewnić logikę walidacji w <xref:System.Activities.CodeActivity.CacheMetadata%2A> przesłonięciu działania. Wszystkie wyjątki zgłoszone przez <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy walidacji. Te wyjątki spowodują wyjście z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez wywołującego.  
  
## <a name="using-validationsettings"></a>Korzystanie z Właściwość  
 Domyślnie wszystkie działania w drzewie aktywności są oceniane, gdy Walidacja jest wywoływana przez <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings>umożliwia dostosowanie walidacji na kilka różnych sposobów przez skonfigurowanie jej trzech właściwości. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Określa, czy moduł walidacji ma przewidzieć całe drzewo aktywności, czy ma zastosowanie tylko logiki walidacji do podanego działania. Wartością domyślną tego ustawienia jest `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>określa dodatkowe mapowanie ograniczeń z typu do listy ograniczeń. W przypadku typu podstawowego każdego działania w drzewie aktywności jest wyszukiwany <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Jeśli zostanie znaleziona zgodna lista ograniczeń, wszystkie ograniczenia na liście są oceniane dla działania. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Określa, czy moduł walidacji ma oszacować wszystkie ograniczenia, czy tylko <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>te określone w. Wartość domyślna to `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hostów przepływu pracy do dodawania dodatkowej weryfikacji dla przepływów pracy, takich jak ograniczenia zasad dla narzędzi, takich jak FxCop. Aby uzyskać więcej informacji o ograniczeniach, zobacz [ograniczenia deklaratywne](declarative-constraints.md).  
  
 Aby użyć <xref:System.Activities.Validation.ValidationSettings>, skonfiguruj żądane właściwości, a następnie Przekaż je w <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>wywołaniu. W tym przykładzie zostanie zweryfikowany przepływ pracy, który <xref:System.Activities.Statements.Sequence> składa się `Add` z niestandardowym działaniem. `Add` Działanie ma dwa wymagane argumenty.  
  
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
  
 Poniższe `Add` działanie jest używane <xref:System.Activities.Statements.Sequence>w, ale jego dwa wymagane argumenty nie są powiązane.  
  
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
  
 W poniższym przykładzie Walidacja jest wykonywana z <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ustawioną na `true`, więc sprawdzane jest tylko działanie główne. <xref:System.Activities.Statements.Sequence>  
  
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
  
 **Brak ostrzeżeń lub błędów** Mimo że działanie ma wymagane argumenty, które nie są powiązane, walidacja zakończyła się pomyślnie, ponieważ oceniane jest tylko działanie główne. `Add` Ten typ weryfikacji jest przydatny do sprawdzania poprawności tylko określonych elementów w drzewie aktywności, takich jak walidacja zmiany właściwości pojedynczego działania w projektancie. Należy pamiętać, że w przypadku wywołania tego przepływu pracy jest oceniana pełna Walidacja skonfigurowana w przepływie pracy i <xref:System.Activities.InvalidWorkflowException> zostałaby zgłoszona. <xref:System.Activities.Validation.ActivityValidationServices>i <xref:System.Activities.Validation.ValidationSettings> skonfigurować wyłącznie sprawdzanie poprawności wywoływane przez hosta, a nie sprawdzanie poprawności, które występuje po wywołaniu przepływu pracy.
