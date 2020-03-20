---
title: Ograniczenia deklaratywne
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 321021e3d73daecae07268f33807c992414a7b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182961"
---
# <a name="declarative-constraints"></a>Ograniczenia deklaratywne
Ograniczenia deklaratywne zapewniają zaawansowana metoda sprawdzania poprawności dla działania i jego relacji z innymi działaniami. Ograniczenia są konfigurowane dla działania podczas procesu tworzenia, ale dodatkowe ograniczenia mogą być również określone przez hosta przepływu pracy. Ten temat zawiera omówienie przy użyciu ograniczeń deklaratywnych, aby zapewnić sprawdzanie poprawności działania.  
  
## <a name="using-declarative-constraints"></a>Korzystanie z ograniczeń deklaratywnych  
 Ograniczenie jest działaniem zawierającym logikę sprawdzania poprawności. To działanie ograniczenia można tworzyć w kodzie lub w języku XAML. Po utworzeniu działania ograniczenia autorzy działań <xref:System.Activities.Activity.Constraints%2A> dodają to ograniczenie do właściwości działania w celu sprawdzenia <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> poprawności lub <xref:System.Activities.Validation.ValidationSettings> używają ograniczenia, aby zapewnić dodatkową weryfikację przy użyciu właściwości wystąpienia. Logika sprawdzania poprawności może składać się z prostych sprawdzania poprawności, takich jak sprawdzanie poprawności metadanych działania, ale może również wykonywać sprawdzanie poprawności, która uwzględnia relację bieżącego działania z jego działaniami nadrzędnymi, podrzędnymi i równorzędnymi. Ograniczenia są tworzene <xref:System.Activities.Validation.Constraint%601> przy użyciu działania, a kilka dodatkowych działań sprawdzania poprawności są dostarczane w celu pomocy w tworzeniu błędów sprawdzania poprawności i ostrzeżenia i dostarczyć informacji o powiązanych działań w przepływie pracy.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation i AddValidationError  
 Działanie <xref:System.Activities.Validation.AssertValidation> ocenia wyrażenie, do którego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> odwołuje się jego właściwość, a jeśli wyrażenie ocenia `false` <xref:System.Activities.Validation.ValidationResults>, błąd sprawdzania poprawności lub ostrzeżenie jest dodawany do . Właściwość <xref:System.Activities.Validation.AssertValidation.Message%2A> opisuje błąd sprawdzania <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> poprawności i właściwość wskazuje, czy błąd sprawdzania poprawności jest błąd lub ostrzeżenie. Wartością domyślną `false`jest <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> .  
  
 W poniższym przykładzie jest zadeklarowane ograniczenie, <xref:System.Activities.Activity.DisplayName%2A> które zwraca ostrzeżenie sprawdzania poprawności, jeśli działanie jest sprawdzane jest dwa znaki lub mniej długości. Parametr typu ogólnego <xref:System.Activities.Validation.Constraint%601> używany dla określa typ działania, który jest sprawdzany przez ograniczenie. To ograniczenie <xref:System.Activities.Activity> używa jako typ ogólny i może służyć do sprawdzania poprawności wszystkich typów działań.  
  
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
  
 Aby określić to ograniczenie dla działania, <xref:System.Activities.Activity.Constraints%2A> jest dodawany do działania, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Host może również określić to ograniczenie dla działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>programu , który jest omówiony w następnej sekcji.  
  
 Działanie <xref:System.Activities.Validation.AddValidationError> jest używane do generowania błędu sprawdzania poprawności lub ostrzeżenia bez konieczności oceny wyrażenia. Jego właściwości są <xref:System.Activities.Validation.AssertValidation> podobne do i może być używany w połączeniu z <xref:System.Activities.Statements.If> działaniami kontroli przepływu ograniczenia, takich jak działanie.
  
### <a name="workflow-relationship-activities"></a>Działania relacji przepływu pracy

Dostępnych jest kilka działań sprawdzania poprawności, które zawierają informacje o innych działaniach w przepływie pracy w odniesieniu do sprawdzane działanie. <xref:System.Activities.Validation.GetParentChain>zwraca kolekcję działań, która zawiera wszystkie działania między bieżącym działaniem a działaniem głównym. <xref:System.Activities.Validation.GetChildSubtree>zawiera zbiór działań, który zawiera działania podrzędne w wzorzec cykliczny i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.  
  
W poniższym przykładzie zdefiniowano `CreateState` działanie. Działanie `CreateState` musi być zawarte `CreateCountry` w działaniu, a `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie. `GetParent`używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu <xref:System.Activities.Statements.ForEach%601> z działaniem do sprawdzania `CreateState` działań nadrzędnych działania działania w celu ustalenia, czy wymóg jest spełniony.  
  
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
 Autorzy hosta przepływu pracy mogą określić dodatkowe ograniczenia sprawdzania poprawności dla działań <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> w przepływie pracy, tworząc ograniczenia i dodając je do słownika <xref:System.Activities.Validation.ValidationSettings> wystąpienia. Każdy element <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> w zawiera typ działania, dla którego ograniczenia mają zastosowanie i listę dodatkowych ograniczeń dla tego typu działania. Gdy sprawdzanie poprawności jest wywoływane dla przepływu pracy, każde działanie określonego typu, w tym klasy pochodne, ocenia ograniczenia. W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji jest stosowane do wszystkich działań w przepływie pracy.  
  
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
  
 Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> `true`jest , to tylko określone dodatkowe ograniczenia są oceniane <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>podczas sprawdzania poprawności jest wywoływana przez wywołanie . Może to być przydatne do sprawdzania przepływów pracy dla określonych konfiguracji sprawdzania poprawności. Należy jednak zauważyć, że po wywołaniu przepływu pracy logika sprawdzania poprawności skonfigurowana w przepływie pracy jest oceniana i musi przebiegać, aby przepływ pracy został pomyślnie rozpocznieny. Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).
