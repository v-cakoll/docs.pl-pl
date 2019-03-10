---
title: Ograniczenia deklaratywne
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: e3ced8f6f88d698273ace5c8b74fe90b94fa9720
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708157"
---
# <a name="declarative-constraints"></a>Ograniczenia deklaratywne
Ograniczenia deklaratywne udostępnia zaawansowane metody sprawdzania poprawności działania i jej relacji z innymi działaniami. Ograniczenia są skonfigurowane do działania podczas procesu tworzenia, ale można również określić dodatkowe ograniczenia przez hosta przepływu pracy. Ten temat zawiera omówienie sposobu użycia ograniczenia deklaratywne, aby zapewnić działanie sprawdzania poprawności.  
  
## <a name="using-declarative-constraints"></a>Za pomocą ograniczenia deklaratywne  
 Ograniczenie to działanie, które zawiera logikę weryfikacji. To działanie ograniczenia można tworzyć w kodzie lub w XAML. Po utworzeniu działania ograniczenie autorzy działanie, dodaj to ograniczenie było <xref:System.Activities.Activity.Constraints%2A> właściwość działania, aby zweryfikować, lub używają ograniczenie do udostępnienia dodatkowej weryfikacji za pomocą <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> wystąpienia . Logikę weryfikacji może składać się z prostych operacji sprawdzania poprawności, takich jak sprawdzanie poprawności metadanych działania, ale może również przeprowadzać weryfikacji, który uwzględnia relacji bieżące działanie do jego działania nadrzędnego, elementy podrzędne i tego samego poziomu. Ograniczenia są tworzone za pomocą <xref:System.Activities.Validation.Constraint%601> działanie i kilku działań dodatkowe sprawdzenie poprawności są udostępniane na potrzeby tworzenia błędy i ostrzeżenia walidacji i podaj informacje o powiązanych działań w przepływie pracy.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation i AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Działanie ocenia wyrażenie odwołuje się jego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> właściwości, a jeśli wyrażenie ma `false`, błąd sprawdzania poprawności lub ostrzeżenie zostanie dodany do <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Właściwość opisuje błąd sprawdzania poprawności i <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> właściwość wskazuje, czy błąd sprawdzania poprawności jest błąd lub ostrzeżenie. Wartością domyślną dla <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> jest `false`.  
  
 W poniższym przykładzie zadeklarowano ograniczenie zwraca ostrzeżeń dotyczących weryfikacji, jeśli <xref:System.Activities.Activity.DisplayName%2A> działania sprawdzania poprawności jest dwóch znaków lub mniej znaków. Parametr typu ogólnego, umożliwiający <xref:System.Activities.Validation.Constraint%601> Określa typ działania, którego poprawność jest sprawdzana przez ograniczenie. To ograniczenie używa <xref:System.Activities.Activity> jako ogólnego typu i może służyć do sprawdzania poprawności wszystkich typów działań.  
  
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
  
 Aby określić, to ograniczenie dla działania, jest ona dodawana do <xref:System.Activities.Activity.Constraints%2A> działań, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Hosta można również określić tego ograniczenia dotyczące działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, które zostało omówione w następnej sekcji.  
  
 <xref:System.Activities.Validation.AddValidationError> Działania jest używany do generowania błąd sprawdzania poprawności lub ostrzeżenie bez wyniku obliczenia wyrażenia. Jego właściwości są podobne do <xref:System.Activities.Validation.AssertValidation> i może służyć w połączeniu z działań sterowania przepływem ograniczenia takich jak <xref:System.Activities.Statements.If> działania.
  
### <a name="workflow-relationship-activities"></a>Działania relacji przepływu pracy

Dostępnych jest kilka działań sprawdzania poprawności, podaj informacje o innych działań w przepływie pracy w odniesieniu do działania sprawdzania poprawności. <xref:System.Activities.Validation.GetParentChain> Zwraca kolekcję działań, która zawiera wszystkie działania od bieżącej aktywności i działania głównego. <xref:System.Activities.Validation.GetChildSubtree> zawiera kolekcję działań, która zawiera działania podrzędne we wzorcu cyklicznego i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.  
  
W poniższym przykładzie `CreateState` działania jest zdefiniowana. `CreateState` Działania muszą być zawarte w obrębie `CreateCountry` działania i `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie. `GetParent` używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu z <xref:System.Activities.Statements.ForEach%601> działanie, aby sprawdzić działania nadrzędnego `CreateState` działanie, aby określić, jeśli to wymaganie można spełnić.  
  
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
  
## <a name="additional-constraints"></a>Dodatkowe ograniczenia  
 Autorzy hosta przepływu pracy można określić dodatkowe sprawdzenie poprawności ograniczenia dotyczące działań w przepływie pracy, tworząc ograniczeń i dodanie ich do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> słownik <xref:System.Activities.Validation.ValidationSettings> wystąpienia. Każdy element na <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> zawiera typ aktywności dla ograniczenia stosowane oraz listę dodatkowych ograniczeń dla tego typu działania. Podczas sprawdzania poprawności dla przepływu pracy, każde działanie określonego typu, w tym klasy pochodne, daje w wyniku ograniczenia. W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji jest stosowane do wszystkich działań w przepływie pracy.  
  
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
  
 Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> jest `true`, a następnie określone dodatkowe ograniczenia są oceniane podczas sprawdzania poprawności, wywołując <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Może to być przydatne w przypadku sprawdzanie przepływów pracy na potrzeby sprawdzania poprawności określonej konfiguracji. Należy jednak pamiętać, że podczas wywoływania przepływu pracy logikę weryfikacji skonfigurowany w przepływie pracy jest obliczane i musi pomyślnie przejść dla przepływu pracy rozpocząć pomyślnie. Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności, zobacz [wywoływanie walidacji działania](invoking-activity-validation.md).
