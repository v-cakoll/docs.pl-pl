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
# <a name="invoking-activity-validation"></a>Wywoływanie walidacji działania
Działanie sprawdzania poprawności zapewnia metodę, aby zidentyfikować i raportowania błędów w konfiguracji dowolne działanie przed jej wykonanie. Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i żadnych ostrzeżeń ani błędów sprawdzania poprawności, które są wyświetlane w Projektancie przepływu pracy. Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez domyślną logikę weryfikacji. Windows Workflow Foundation (WF) zapewnia <xref:System.Activities.Validation.ActivityValidationServices> klasę, która może służyć przez aplikacji przepływu pracy i deweloperom narzędzia do jawnie sprawdzania poprawności działania. W tym temacie opisano sposób użycia <xref:System.Activities.Validation.ActivityValidationServices> do wykonywania sprawdzania poprawności działania.  
  
## <a name="using-activityvalidationservices"></a>Za pomocą ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices> ma dwa <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> przeciążenia, które są używane do wywołania logiki sprawdzania poprawności działania. Pierwsze przeciążenie przyjmuje działania głównego, aby zostać uwierzytelnionym i zwraca kolekcję błędy i ostrzeżenia walidacji. W poniższym przykładzie niestandardową `Add` działanie jest używane, że ma dwa wymagane argumenty.  
  
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
  
 `Add` Działania jest używana wewnątrz <xref:System.Activities.Statements.Sequence>, ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie.  
  
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
  
 Ten przepływ pracy można zweryfikować przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Zwraca kolekcję wszelkie błędy sprawdzania poprawności lub ostrzeżenia zawarte działanie i żadnych elementów podrzędnych, jak pokazano w poniższym przykładzie.  
  
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
  
 Gdy <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> jest wywoływana w tym przykładowym przepływie pracy dwóch sprawdzania poprawności są zwracane błędy.  
  
 **Błąd: Nie podano wartości argumentu wymagane działania 'Operand2'.**  
**Błąd: Nie podano wartości argumentu wymagane działania "Operand1".**  Jeśli ten przepływ pracy został wywołany, <xref:System.Activities.InvalidWorkflowException> może zostać zgłoszone, jak pokazano w poniższym przykładzie.  
  
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
**Napotkano następujące błędy podczas przetwarzania drzewa przepływu pracy:**   
**"Dodaj": wartość argumentu w postaci wymagane działania 'Operand2' nie został dostarczony.**   
**"Dodaj": wartość argumentu w postaci wymagane działania "Operand1" nie został podany.**  Dla tego przykładowego przepływu pracy był prawidłowy, dwa wymagane argumenty `Add` działanie musi być powiązana. W poniższym przykładzie dwa wymagane argumenty są powiązane z zmienne przepływu pracy oraz wartość wyniku. W tym przykładzie <xref:System.Activities.Activity%601.Result%2A> argument jest powiązana wraz z dwóch wymaganych argumentów. <xref:System.Activities.Activity%601.Result%2A> Argument nie jest wymagana z oświadczeniem i nie powoduje błąd sprawdzania poprawności, jeśli nie jest. Jest odpowiedzialny za tworzenie przepływu pracy można powiązać <xref:System.Activities.Activity%601.Result%2A> jeśli jego wartość jest używana w innym miejscu w przepływie pracy.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Sprawdzanie poprawności wymagane argumenty dla działania głównego  
 Jeśli działanie główne przepływu pracy zawiera argumenty, te nie są powiązane aż do przepływu pracy jest wywoływany i parametry są przekazywane do przepływu pracy. Poniższy przepływ pracy pozytywnie zweryfikowane, ale wyjątek jest generowany, jeśli przepływ pracy jest wywoływane bez przekazywania w wymaganych argumentów, jak pokazano w poniższym przykładzie.  
  
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
  
 **System.ArgumentException: Działania głównego ustawienia argumentów są nieprawidłowe.**  
**Napraw definicji przepływu pracy lub podać wartości wejściowe, aby naprawić te błędy:**   
**"Dodaj": wartość argumentu w postaci wymagane działania 'Operand2' nie został dostarczony.**   
**"Dodaj": wartość argumentu w postaci wymagane działania "Operand1" nie został podany.**  Po poprawne argumenty są przekazywane, przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.  
  
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
> W tym przykładzie działania głównego został zadeklarowany jako `Add` zamiast `Activity` co w poprzednim przykładzie. Dzięki temu `WorkflowInvoker.Invoke` metody, aby przywrócić pojedyncze liczby całkowite, który reprezentuje wyniki `Add` zamiast słownik `out` argumentów. Zmienna `wf` może być także zadeklarowana jako `Activity<int>`.  
  
 Podczas sprawdzania poprawności argumentów głównego, spoczywa aplikacji hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazywane podczas wywoływania przepływu pracy.  
  
### <a name="invoking-imperative-code-based-validation"></a>Wywoływanie Imperatywne sprawdzanie poprawności, które są oparte na kodzie

Imperatywne sprawdzanie poprawności, które są oparte na kodzie zapewnia prostą metodę dla działania w celu udostępnienia weryfikacji o sobie i jest dostępny dla działań, które wynikają z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Kod sprawdzania poprawności, który określa żadnych ostrzeżeń ani błędów sprawdzania poprawności jest dodawany do działania. Podczas sprawdzania poprawności na działanie, te ostrzeżenia i błędy są zawarte w zbiorze zwróconym przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. W poniższym przykładzie `CreateProduct` działania jest zdefiniowana. Jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.  
  
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
  
 W tym przykładzie przepływ pracy jest skonfigurowany przy użyciu `CreateProduct` działania. W tym przepływie pracy `Cost` jest większa niż `Price`, a także wymagane `Description` argument nie jest ustawiona. Podczas sprawdzania poprawności, zwracane są następujące błędy.  
  
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
  
 **Błąd: Koszt musi być większa niż cena.**  
**Błąd: Nie podano wartości argumentu wymagane działania "Opis".**    
> [!NOTE]
>  Niestandardowe działanie autorzy mogą udostępniać logikę weryfikacji w działaniu <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia. Wszelkie wyjątki, które są generowane przez <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności. Wyjątki te będą uciekały z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.  
  
## <a name="using-validationsettings"></a>Za pomocą ValidationSettings  
 Domyślnie wszystkie działania w drzewie działania są oceniane podczas sprawdzania poprawności jest wywoływana przez <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings> Umożliwia sprawdzanie poprawności można dostosować na kilka różnych sposobów, konfigurując jego trzy właściwości. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Określa, czy moduł weryfikacji powinny przejść przez drzewo działanie całej dotyczą tylko logikę weryfikacji podanej działania. Wartością domyślną dla tej wartości jest `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Określa dodatkowe ograniczenia mapowanie z typu do listy ograniczeń. Typ podstawowy elementu każde działanie w drzewie działanie sprawdzania poprawności jest wyszukiwanie w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Jeśli zostanie znalezione pasujące lista ograniczeń, wszystkie ograniczenia na liście są oceniane pod kątem działania. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Określa, czy moduł weryfikacji należy ocenić wszystkie ograniczenia lub tylko te określone w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Wartość domyślna to `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hosta przepływu pracy dodać dodatkowe sprawdzanie poprawności dla przepływów pracy, takich jak zasady ograniczeń dla narzędzi, takich jak programu FxCop. Aby uzyskać więcej informacji na temat ograniczeń, zobacz [ograniczenia deklaratywne](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).  
  
 Aby użyć <xref:System.Activities.Validation.ValidationSettings>skonfiguruj żądane właściwości, a następnie przekazać go w wywołaniu <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. W tym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> za pomocą niestandardowego `Add` działania jest weryfikowane. `Add` Działanie ma dwa wymagane argumenty.  
  
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
  
 Następujące `Add` działania jest używana w <xref:System.Activities.Statements.Sequence>, ale jego dwóch wymagane argumenty nie są powiązane.  
  
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
  
 W poniższym przykładzie, sprawdzanie poprawności jest wykonywane przy użyciu <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> równa `true`, więc tylko główny <xref:System.Activities.Statements.Sequence> działania jest weryfikowane.  
  
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
  
 **Żadne ostrzeżenia ani błędy** mimo że `Add` działania wymaga argumentów, które nie są powiązane, weryfikacja zakończy się pomyślnie, ponieważ jest oceniane tylko działania głównego. Tego rodzaju Walidacja przydaje się do sprawdzania poprawności tylko określone elementy w drzewie działania, takie jak weryfikacja zmianę właściwości jedno działanie w projektancie. Należy pamiętać, jeśli ten przepływ pracy zostanie wywołana, pełna Walidacja skonfigurowany w przepływie pracy jest obliczane i <xref:System.Activities.InvalidWorkflowException> może zostać wygenerowany. <xref:System.Activities.Validation.ActivityValidationServices> i <xref:System.Activities.Validation.ValidationSettings> skonfigurować tylko sprawdzanie poprawności jawnie wywoływane przez hosta i nie występuje, gdy jest wywoływana przez przepływ pracy weryfikacji.
