---
title: Ograniczenia deklaratywne
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 5599513405c77aa213b329b085075660baed5c47
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580494"
---
# <a name="declarative-constraints"></a><span data-ttu-id="1be6e-102">Ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="1be6e-102">Declarative Constraints</span></span>
<span data-ttu-id="1be6e-103">Ograniczenia deklaratywne udostępnia zaawansowane metody sprawdzania poprawności działania i jej relacji z innymi działaniami.</span><span class="sxs-lookup"><span data-stu-id="1be6e-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="1be6e-104">Ograniczenia są skonfigurowane do działania podczas procesu tworzenia, ale można również określić dodatkowe ograniczenia przez hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1be6e-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="1be6e-105">Ten temat zawiera omówienie sposobu użycia ograniczenia deklaratywne, aby zapewnić działanie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1be6e-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="1be6e-106">Za pomocą ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="1be6e-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="1be6e-107">Ograniczenie to działanie, które zawiera logikę weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="1be6e-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="1be6e-108">To działanie ograniczenia można tworzyć w kodzie lub w XAML.</span><span class="sxs-lookup"><span data-stu-id="1be6e-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="1be6e-109">Po utworzeniu działania ograniczenie autorzy działanie, dodaj to ograniczenie było <xref:System.Activities.Activity.Constraints%2A> właściwość działania, aby zweryfikować, lub używają ograniczenie do udostępnienia dodatkowej weryfikacji za pomocą <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> wystąpienia .</span><span class="sxs-lookup"><span data-stu-id="1be6e-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="1be6e-110">Logikę weryfikacji może składać się z prostych operacji sprawdzania poprawności, takich jak sprawdzanie poprawności metadanych działania, ale może również przeprowadzać weryfikacji, który uwzględnia relacji bieżące działanie do jego działania nadrzędnego, elementy podrzędne i tego samego poziomu.</span><span class="sxs-lookup"><span data-stu-id="1be6e-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="1be6e-111">Ograniczenia są tworzone za pomocą <xref:System.Activities.Validation.Constraint%601> działanie i kilku działań dodatkowe sprawdzenie poprawności są udostępniane na potrzeby tworzenia błędy i ostrzeżenia walidacji i podaj informacje o powiązanych działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="1be6e-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="1be6e-112">AssertValidation i AddValidationError</span><span class="sxs-lookup"><span data-stu-id="1be6e-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="1be6e-113"><xref:System.Activities.Validation.AssertValidation> Działanie ocenia wyrażenie odwołuje się jego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> właściwości, a jeśli wyrażenie ma `false`, błąd sprawdzania poprawności lub ostrzeżenie zostanie dodany do <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="1be6e-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="1be6e-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Właściwość opisuje błąd sprawdzania poprawności i <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> właściwość wskazuje, czy błąd sprawdzania poprawności jest błąd lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1be6e-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="1be6e-115">Wartością domyślną dla <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="1be6e-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="1be6e-116">W poniższym przykładzie zadeklarowano ograniczenie zwraca ostrzeżeń dotyczących weryfikacji, jeśli <xref:System.Activities.Activity.DisplayName%2A> działania sprawdzania poprawności jest dwóch znaków lub mniej znaków.</span><span class="sxs-lookup"><span data-stu-id="1be6e-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="1be6e-117">Parametr typu ogólnego, umożliwiający <xref:System.Activities.Validation.Constraint%601> Określa typ działania, którego poprawność jest sprawdzana przez ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="1be6e-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="1be6e-118">To ograniczenie używa <xref:System.Activities.Activity> jako ogólnego typu i może służyć do sprawdzania poprawności wszystkich typów działań.</span><span class="sxs-lookup"><span data-stu-id="1be6e-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="1be6e-119">Aby określić, to ograniczenie dla działania, jest ona dodawana do <xref:System.Activities.Activity.Constraints%2A> działań, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1be6e-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="1be6e-120">Hosta można również określić tego ograniczenia dotyczące działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, które zostało omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1be6e-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="1be6e-121"><xref:System.Activities.Validation.AddValidationError> Działania jest używany do generowania błąd sprawdzania poprawności lub ostrzeżenie bez wyniku obliczenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1be6e-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="1be6e-122">Jego właściwości są podobne do <xref:System.Activities.Validation.AssertValidation> i może służyć w połączeniu z działań sterowania przepływem ograniczenia takich jak <xref:System.Activities.Statements.If> działania.</span><span class="sxs-lookup"><span data-stu-id="1be6e-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="1be6e-123">Działania relacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1be6e-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="1be6e-124">Dostępnych jest kilka działań sprawdzania poprawności, podaj informacje o innych działań w przepływie pracy w odniesieniu do działania sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1be6e-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="1be6e-125"><xref:System.Activities.Validation.GetParentChain> Zwraca kolekcję działań, która zawiera wszystkie działania od bieżącej aktywności i działania głównego.</span><span class="sxs-lookup"><span data-stu-id="1be6e-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="1be6e-126"><xref:System.Activities.Validation.GetChildSubtree> zawiera kolekcję działań, która zawiera działania podrzędne we wzorcu cyklicznego i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="1be6e-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="1be6e-127">W poniższym przykładzie `CreateState` działania jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="1be6e-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="1be6e-128">`CreateState` Działania muszą być zawarte w obrębie `CreateCountry` działania i `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie.</span><span class="sxs-lookup"><span data-stu-id="1be6e-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="1be6e-129">`GetParent` używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu z <xref:System.Activities.Statements.ForEach%601> działanie, aby sprawdzić działania nadrzędnego `CreateState` działanie, aby określić, jeśli to wymaganie można spełnić.</span><span class="sxs-lookup"><span data-stu-id="1be6e-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="1be6e-130">Dodatkowe ograniczenia</span><span class="sxs-lookup"><span data-stu-id="1be6e-130">Additional Constraints</span></span>  
 <span data-ttu-id="1be6e-131">Autorzy hosta przepływu pracy można określić dodatkowe sprawdzenie poprawności ograniczenia dotyczące działań w przepływie pracy, tworząc ograniczeń i dodanie ich do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> słownik <xref:System.Activities.Validation.ValidationSettings> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1be6e-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="1be6e-132">Każdy element na <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> zawiera typ aktywności dla ograniczenia stosowane oraz listę dodatkowych ograniczeń dla tego typu działania.</span><span class="sxs-lookup"><span data-stu-id="1be6e-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="1be6e-133">Podczas sprawdzania poprawności dla przepływu pracy, każde działanie określonego typu, w tym klasy pochodne, daje w wyniku ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="1be6e-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="1be6e-134">W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji jest stosowane do wszystkich działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="1be6e-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="1be6e-135">Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> jest `true`, a następnie określone dodatkowe ograniczenia są oceniane podczas sprawdzania poprawności, wywołując <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="1be6e-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="1be6e-136">Może to być przydatne w przypadku sprawdzanie przepływów pracy na potrzeby sprawdzania poprawności określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1be6e-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="1be6e-137">Należy jednak pamiętać, że podczas wywoływania przepływu pracy logikę weryfikacji skonfigurowany w przepływie pracy jest obliczane i musi pomyślnie przejść dla przepływu pracy rozpocząć pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1be6e-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="1be6e-138">Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności, zobacz [wywoływanie walidacji działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="1be6e-138">For more information about invoking validation, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>
