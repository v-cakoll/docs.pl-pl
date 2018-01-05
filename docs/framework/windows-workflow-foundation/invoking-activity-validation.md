---
title: "Wywoływanie sprawdzania poprawności działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22fc7dc53f52b47be2da3313f678825d4362750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invoking-activity-validation"></a>Wywoływanie sprawdzania poprawności działania
Działanie sprawdzania poprawności udostępnia metodę do identyfikowania i raportów o błędach w konfiguracji żadnego działania przed jego wykonywania. Sprawdzanie poprawności występuje, gdy przepływ pracy zostanie zmodyfikowany w Projektancie przepływów pracy i wszelkie błędy sprawdzania poprawności zostaną wyświetlone w Projektancie przepływów pracy. Sprawdzanie poprawności występuje także w czasie wykonywania po wywołaniu przepływu pracy i, jeśli wystąpią jakieś błędy sprawdzania poprawności, <xref:System.Activities.InvalidWorkflowException> jest generowany przez logikę sprawdzania poprawności domyślnej. [!INCLUDE[wf](../../../includes/wf-md.md)]udostępnia <xref:System.Activities.Validation.ActivityValidationServices> klasy, która umożliwia aplikacji przepływu pracy i deweloperów narzędzi jawnie sprawdzić poprawność działania. W tym temacie opisano sposób użycia <xref:System.Activities.Validation.ActivityValidationServices> do sprawdzania poprawności działania.  
  
## <a name="using-activityvalidationservices"></a>Przy użyciu obiektu ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices>zawiera dwa <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> przeciążeń, które są używane do wywołania logiki sprawdzania poprawności działania. Pierwszy przeciążenia przyjmuje działanie główne do sprawdzenia poprawności i zwraca zbiór błędy sprawdzania poprawności i ostrzeżenia. W poniższym przykładzie niestandardowego `Add` działania jest używana, że dwa wymaga argumentów.  
  
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
  
 `Add` Działania jest używany wewnątrz <xref:System.Activities.Statements.Sequence>, ale jego dwa wymagane argumenty nie są powiązane, jak pokazano w poniższym przykładzie.  
  
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
  
 Ten przepływ pracy można zweryfikować przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Zwraca kolekcję wszelkie błędy lub ostrzeżenia walidacji zawarte działanie i podrzędnych, jak pokazano w poniższym przykładzie.  
  
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
  
 Gdy <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> jest wywoływana na ten przepływ pracy próbki dwóch weryfikacji błędy są zwracane.  
  
 **Błąd: Nie podano wartości dla wymaganego argumentu działania 'Operand2'.**  
**Błąd: Nie podano wartości dla wymaganego argumentu działania "Operand1".**  Jeśli ten przepływ pracy został wywołany, <xref:System.Activities.InvalidWorkflowException> może zostać zgłoszony, jak pokazano w poniższym przykładzie.  
  
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
**"Dodaj": wartość dla wymaganego argumentu działania 'Operand2' nie został dostarczony.**   
**"Dodaj": wartość dla wymaganego argumentu działania "Operand1" nie został dostarczony.**  Dla tego przykładowego przepływu pracy jest nieprawidłowy, dwa wymagane argumenty `Add` działanie musi być powiązany. W poniższym przykładzie dwa wymagane argumenty są powiązane z zmienne przepływu pracy oraz wartość wyniku. W tym przykładzie <xref:System.Activities.Activity%601.Result%2A> argument jest powiązany wraz z dwóch wymaganych argumentów. <xref:System.Activities.Activity%601.Result%2A> Argument nie jest wymagane może być powiązane i nie powoduje błąd sprawdzania poprawności, jeśli nie jest. Jest odpowiedzialny za tworzenie przepływu pracy można powiązać <xref:System.Activities.Activity%601.Result%2A> jeśli jego wartość jest używana w innym miejscu w przepływie pracy.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Sprawdzanie poprawności wymaganych argumentów działania głównego  
 Jeśli działanie główne w przepływie pracy zawiera argumenty, te nie są powiązane dopiero po wywołaniu przepływu pracy i parametry są przekazywane do przepływu pracy. Poniższy przepływ pracy pozytywnej weryfikacji, ale jest zwracany wyjątek, jeśli przepływ pracy zostanie wywołany bez przekazywanie wymaganych argumentów, jak pokazano w poniższym przykładzie.  
  
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
  
 **System.ArgumentException: Ustawienia argumentów działania głównego są niepoprawne.**  
**Napraw definicji przepływu pracy lub podaj wartości wejściowe w celu usunięcia następujących błędów:**   
**"Dodaj": wartość dla wymaganego argumentu działania 'Operand2' nie został dostarczony.**   
**"Dodaj": wartość dla wymaganego argumentu działania "Operand1" nie został dostarczony.**  Po poprawne argumenty są przekazywane, przepływ pracy zakończy się pomyślnie, jak pokazano w poniższym przykładzie.  
  
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
>  W tym przykładzie działanie główne został zadeklarowany jako `Add` zamiast `Activity` co w poprzednim przykładzie. Dzięki temu `WorkflowInvoker.Invoke` metodę, aby zwrócić pojedynczego liczba całkowita, która reprezentuje wyniki `Add` działania zamiast słownik `out` argumentów. Zmienna `wf` może być również zadeklarowany jako `Activity<int>`.  
  
 Podczas sprawdzania poprawności argumentów głównego, jest odpowiedzialny za aplikacji hosta, aby upewnić się, że wszystkie wymagane argumenty są przekazywane po wywołaniu przepływu pracy.  
  
### <a name="invoking-imperative-code-based-validation"></a>Wywoływanie Imperatywnych weryfikacji opartych na kodzie  
 Konieczne weryfikacji opartych na kodzie zapewnia prosty sposób działania w celu udostępnienia weryfikacji o sobie samym i jest dostępny dla działań, które pochodzą z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, i <xref:System.Activities.NativeActivity>. Sprawdzanie poprawności kodu, który określa wszelkie błędy lub ostrzeżenia walidacji jest dodawany do działania. Podczas sprawdzania poprawności jest wywoływana w działaniu, tych ostrzeżeń lub błędów znajdują się w kolekcji zwróconej przez wywołanie <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. W poniższym przykładzie pobierana z [podstawowe sprawdzanie poprawności](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) próbki, `CreateProduct` zdefiniowano działania. Jeśli `Cost` jest większa niż `Price`, błąd sprawdzania poprawności jest dodawany do metadanych w <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia.  
  
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
  
 W tym przykładzie przepływ pracy jest konfigurowana przy użyciu `CreateProduct` działania. W tym przepływie pracy `Cost` jest większa niż `Price`oraz wymagane `Description` argument nie jest ustawiona. Po wywołaniu weryfikacji następujące błędy są zwracane.  
  
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
  
 **Błąd: Koszt musi być mniejsza lub równa cenie.**  
**Błąd: Nie podano wartości dla wymaganego argumentu działania "Opis".**    
> [!NOTE]
>  Autorzy działania niestandardowego można podać logiki sprawdzania poprawności w działaniu <xref:System.Activities.CodeActivity.CacheMetadata%2A> zastąpienia. Wszelkie wyjątki, które są generowane z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nie są traktowane jako błędy sprawdzania poprawności. Te wyjątki zostaną wyjścia z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący.  
  
## <a name="using-validationsettings"></a>Przy użyciu ValidationSettings  
 Domyślnie wszystkie działania w drzewie działań są oceniane podczas sprawdzania poprawności jest wywoływany przez <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings>Umożliwia sprawdzanie poprawności można dostosować na różne sposoby, konfigurując trzy właściwości. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Określa, czy moduł weryfikacji powinien objaśniono działanie całego drzewa lub dotyczą tylko logikę weryfikacji dostarczonego działania. Wartość domyślna dla tej wartości to `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>Określa dodatkowe ograniczenie mapowanie typu do listy ograniczeń. Dla typu podstawowego każde działanie w drzewie działań, sprawdzana jest wyszukiwanie w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Jeśli zostanie znaleziony dopasowania listy ograniczeń, wszystkie ograniczenia na liście są oceniane pod kątem działania. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Określa, czy moduł weryfikacji należy ocenić wszystkie ograniczenia lub tylko te określone w <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Wartość domyślna to `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>i <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> są przydatne dla autorów hosta przepływu pracy dodać dodatkowe sprawdzanie poprawności dla przepływów pracy, takich jak warunki ograniczające zasady dla narzędzi, takich jak programu FxCop. [!INCLUDE[crabout](../../../includes/crabout-md.md)]ograniczenia, zobacz [deklaratywne ograniczenia](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).  
  
 Aby użyć <xref:System.Activities.Validation.ValidationSettings>skonfiguruj odpowiednie właściwości, a następnie przekazać w wywołaniu <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. W tym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.Sequence> z niestandardowego `Add` sprawdzania poprawności działania. `Add` Działanie ma dwa wymaganych argumentów.  
  
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
  
 Następujące `Add` działania jest używana w <xref:System.Activities.Statements.Sequence>, ale jego dwa wymagane argumenty nie są powiązane.  
  
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
  
 Na przykład następujące, weryfikacja jest przeprowadzana z <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ustawioną `true`, więc tylko głównego <xref:System.Activities.Statements.Sequence> sprawdzania poprawności działania.  
  
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
  
 **Brak ostrzeżeń i błędów** mimo że `Add` działania wymaga argumentów, które nie są powiązane, Weryfikacja powiodła się, ponieważ działanie główne jest obliczane. Ten typ sprawdzania poprawności jest przydatna do sprawdzania poprawności tylko określonych elementów w drzewie działań, takich jak sprawdzanie poprawności zmiany właściwości pojedynczego działania w projektancie. Jeśli ten przepływ pracy zostanie wywołany, całkowicie zweryfikować skonfigurowany w przepływie pracy jest oceniane i <xref:System.Activities.InvalidWorkflowException> może zostać zgłoszony. <xref:System.Activities.Validation.ActivityValidationServices>i <xref:System.Activities.Validation.ValidationSettings> skonfigurować tylko weryfikacji jawnie wywoływane przez hosta i nie występuje, gdy przepływ pracy jest wywoływany weryfikacji.
