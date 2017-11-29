---
title: Ograniczenia deklaratywne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a51f77864478dcefbe5b2742288f9cc91648f7bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="declarative-constraints"></a>Ograniczenia deklaratywne
Deklaratywne ograniczenia udostępnia zaawansowane metody sprawdzania poprawności działania i ich relacji z innymi działaniami. Ograniczenia są skonfigurowane dla działania podczas procesu tworzenia, ale można również określić dodatkowe ograniczenia przez hosta przepływu pracy. Ten temat zawiera omówienie sposobu użycia deklaratywne ograniczenia do udostępnienia weryfikacji działania.  
  
## <a name="using-declarative-constraints"></a>Używanie ograniczeń deklaratywne  
 Ograniczenie to działanie, które zawiera logikę sprawdzania poprawności. To działanie ograniczenie można tworzyć w kodzie, lub w języku XAML. Po utworzeniu działania ograniczenia autorów działania dodać ten warunek ograniczający do <xref:System.Activities.Activity.Constraints%2A> właściwości działania do sprawdzania poprawności, ograniczenie też używać w celu udostępnienia dodatkowych weryfikacji przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> wystąpienia . Logikę weryfikacji może składać się z prostych operacji sprawdzania poprawności, takich jak sprawdzanie poprawności działania metadanych, ale mogą też wykonywać sprawdzania poprawności, która uwzględnia relacji bieżące działanie do jego działania nadrzędnego, elementy podrzędne i tego samego poziomu. Ograniczenia są tworzone przy użyciu <xref:System.Activities.Validation.Constraint%601> działania i kilka dodatkowych sprawdzania poprawności działania są dostarczane z tworzenia błędy sprawdzania poprawności i ostrzeżenia i aby podać informacje o powiązanych działań w przepływie pracy.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation i metodę AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Działania oblicza wyrażenie odwołuje się jego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> właściwości, a jeśli wyrażenie ma `false`, błąd sprawdzania poprawności lub ostrzeżenie zostanie dodany do <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Właściwość opisuje błąd sprawdzania poprawności i <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> właściwość wskazuje, czy niepowodzenia weryfikacji jest błąd lub ostrzeżenie. Wartość domyślna dla <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> jest `false`.  
  
 W poniższym przykładzie zadeklarowano ograniczenie zwraca ostrzeżenie walidacji, jeśli <xref:System.Activities.Activity.DisplayName%2A> działania sprawdzana jest dwóch znaków lub mniej długości. Parametr typu ogólnego używane dla <xref:System.Activities.Validation.Constraint%601> Określa typ działania, którego poprawność jest sprawdzana przez ograniczenie. To ograniczenie używa <xref:System.Activities.Activity> jako ogólnego typu i może służyć do sprawdzania poprawności wszystkie typy działań.  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 Aby określić to ograniczenie dla działania, jest ona dodawana do <xref:System.Activities.Activity.Constraints%2A> działania, jak pokazano w poniższym przykładzie kodzie.  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 Hosta można również określić to ograniczenie działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, którego dotyczy w następnej sekcji.  
  
 <xref:System.Activities.Validation.AddValidationError> Działania jest używany do generowania błąd sprawdzania poprawności lub ostrzeżenie bez konieczności obliczenia wyrażenia. Jego właściwości są podobne do <xref:System.Activities.Validation.AssertValidation> i może służyć w połączeniu z działania przepływu sterowania ograniczenia takich jak <xref:System.Activities.Statements.If> działania.  
  
### <a name="workflow-relationship-activities"></a>Działania przepływu pracy relacji  
 Dostępnych jest kilka działań weryfikacji zawierających informacje o innych działań w przepływie pracy w odniesieniu do działania sprawdzania poprawności. <xref:System.Activities.Validation.GetParentChain>Zwraca kolekcję działań, która zawiera wszystkie działania między bieżące działanie i działanie główne. <xref:System.Activities.Validation.GetChildSubtree>udostępnia kolekcję zawierającą działania podrzędne w układzie cykliczne, działań i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.  
  
 W poniższym przykładzie z [weryfikacji relacje działania](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) próbki, `CreateState` zdefiniowano działania. `CreateState` Działanie musi być zawarty w `CreateCountry` działania, a `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie. `GetParent`używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu z <xref:System.Activities.Statements.ForEach%601> działanie, aby sprawdzić działania nadrzędnego `CreateState` działanie, aby określić, czy to wymaganie jest spełnione.  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();              
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }    
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();                          
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {                                     
            Body = new ActivityAction<CreateState,ValidationContext>  
            {                      
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result   
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {                                  
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context                                      
                            },  
                            Body = new ActivityAction<Activity>  
                            {     
                                Argument = parent,   
                                Handler = new If()  
                                {                                            
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),                                          
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }                                  
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),                                                                  
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]Windows Workflow Foundation [weryfikacji](../../../docs/framework/windows-workflow-foundation/samples/validation.md) próbek.  
  
## <a name="additional-constraints"></a>Dodatkowe ograniczenia  
 Autorzy hosta przepływu pracy można określić dodatkowe sprawdzenie poprawności ograniczenia dla działań w przepływie pracy przy tworzeniu ograniczeń i dodawanie ich do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> słownik <xref:System.Activities.Validation.ValidationSettings> wystąpienia. Każdy element <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> zawiera typ działania dla ograniczenia stosowane oraz listę dodatkowe ograniczenia dla tego typu działania. Podczas sprawdzania poprawności jest wywoływany dla przepływu pracy, każde działanie określonego typu, łącznie z klasy pochodnej, ocenia ograniczenia. W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji, jest stosowane do wszystkich działań w przepływie pracy.  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},       
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> jest `true`, następnie określonego dodatkowe ograniczenia są oceniane podczas sprawdzania poprawności jest wywoływany przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Może to być przydatne do inspekcji przepływy pracy dla określonych sprawdzania poprawności konfiguracji. Zauważ jednak, że po wywołaniu przepływu pracy logikę weryfikacji skonfigurowany w przepływie pracy jest obliczane i musi przejść pomyślnie rozpocząć przepływu pracy. [!INCLUDE[crabout](../../../includes/crabout-md.md)]wywoływanie weryfikacji, zobacz [wywoływania sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).
