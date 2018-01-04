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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a11c62c7011d7ffb13ed0d0ebf060a3cbeb7d7f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="declarative-constraints"></a><span data-ttu-id="68e94-102">Ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="68e94-102">Declarative Constraints</span></span>
<span data-ttu-id="68e94-103">Deklaratywne ograniczenia udostępnia zaawansowane metody sprawdzania poprawności działania i ich relacji z innymi działaniami.</span><span class="sxs-lookup"><span data-stu-id="68e94-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="68e94-104">Ograniczenia są skonfigurowane dla działania podczas procesu tworzenia, ale można również określić dodatkowe ograniczenia przez hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="68e94-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="68e94-105">Ten temat zawiera omówienie sposobu użycia deklaratywne ograniczenia do udostępnienia weryfikacji działania.</span><span class="sxs-lookup"><span data-stu-id="68e94-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="68e94-106">Używanie ograniczeń deklaratywne</span><span class="sxs-lookup"><span data-stu-id="68e94-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="68e94-107">Ograniczenie to działanie, które zawiera logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="68e94-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="68e94-108">To działanie ograniczenie można tworzyć w kodzie, lub w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="68e94-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="68e94-109">Po utworzeniu działania ograniczenia autorów działania dodać ten warunek ograniczający do <xref:System.Activities.Activity.Constraints%2A> właściwości działania do sprawdzania poprawności, ograniczenie też używać w celu udostępnienia dodatkowych weryfikacji przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> wystąpienia .</span><span class="sxs-lookup"><span data-stu-id="68e94-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="68e94-110">Logikę weryfikacji może składać się z prostych operacji sprawdzania poprawności, takich jak sprawdzanie poprawności działania metadanych, ale mogą też wykonywać sprawdzania poprawności, która uwzględnia relacji bieżące działanie do jego działania nadrzędnego, elementy podrzędne i tego samego poziomu.</span><span class="sxs-lookup"><span data-stu-id="68e94-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="68e94-111">Ograniczenia są tworzone przy użyciu <xref:System.Activities.Validation.Constraint%601> działania i kilka dodatkowych sprawdzania poprawności działania są dostarczane z tworzenia błędy sprawdzania poprawności i ostrzeżenia i aby podać informacje o powiązanych działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="68e94-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="68e94-112">AssertValidation i metodę AddValidationError</span><span class="sxs-lookup"><span data-stu-id="68e94-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="68e94-113"><xref:System.Activities.Validation.AssertValidation> Działania oblicza wyrażenie odwołuje się jego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> właściwości, a jeśli wyrażenie ma `false`, błąd sprawdzania poprawności lub ostrzeżenie zostanie dodany do <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="68e94-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="68e94-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Właściwość opisuje błąd sprawdzania poprawności i <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> właściwość wskazuje, czy niepowodzenia weryfikacji jest błąd lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="68e94-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="68e94-115">Wartość domyślna dla <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68e94-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="68e94-116">W poniższym przykładzie zadeklarowano ograniczenie zwraca ostrzeżenie walidacji, jeśli <xref:System.Activities.Activity.DisplayName%2A> działania sprawdzana jest dwóch znaków lub mniej długości.</span><span class="sxs-lookup"><span data-stu-id="68e94-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="68e94-117">Parametr typu ogólnego używane dla <xref:System.Activities.Validation.Constraint%601> Określa typ działania, którego poprawność jest sprawdzana przez ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="68e94-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="68e94-118">To ograniczenie używa <xref:System.Activities.Activity> jako ogólnego typu i może służyć do sprawdzania poprawności wszystkie typy działań.</span><span class="sxs-lookup"><span data-stu-id="68e94-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="68e94-119">Aby określić to ograniczenie dla działania, jest ona dodawana do <xref:System.Activities.Activity.Constraints%2A> działania, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="68e94-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="68e94-120">Hosta można również określić to ograniczenie działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, którego dotyczy w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="68e94-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="68e94-121"><xref:System.Activities.Validation.AddValidationError> Działania jest używany do generowania błąd sprawdzania poprawności lub ostrzeżenie bez konieczności obliczenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="68e94-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="68e94-122">Jego właściwości są podobne do <xref:System.Activities.Validation.AssertValidation> i może służyć w połączeniu z działania przepływu sterowania ograniczenia takich jak <xref:System.Activities.Statements.If> działania.</span><span class="sxs-lookup"><span data-stu-id="68e94-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>  
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="68e94-123">Działania przepływu pracy relacji</span><span class="sxs-lookup"><span data-stu-id="68e94-123">Workflow Relationship Activities</span></span>  
 <span data-ttu-id="68e94-124">Dostępnych jest kilka działań weryfikacji zawierających informacje o innych działań w przepływie pracy w odniesieniu do działania sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="68e94-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="68e94-125"><xref:System.Activities.Validation.GetParentChain>Zwraca kolekcję działań, która zawiera wszystkie działania między bieżące działanie i działanie główne.</span><span class="sxs-lookup"><span data-stu-id="68e94-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="68e94-126"><xref:System.Activities.Validation.GetChildSubtree>udostępnia kolekcję zawierającą działania podrzędne w układzie cykliczne, działań i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="68e94-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
 <span data-ttu-id="68e94-127">W poniższym przykładzie z [weryfikacji relacje działania](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) próbki, `CreateState` zdefiniowano działania.</span><span class="sxs-lookup"><span data-stu-id="68e94-127">In the following example from the [Activity Relationships Validation](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) sample, a `CreateState` activity is defined.</span></span> <span data-ttu-id="68e94-128">`CreateState` Działanie musi być zawarty w `CreateCountry` działania, a `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie.</span><span class="sxs-lookup"><span data-stu-id="68e94-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="68e94-129">`GetParent`używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu z <xref:System.Activities.Statements.ForEach%601> działanie, aby sprawdzić działania nadrzędnego `CreateState` działanie, aby określić, czy to wymaganie jest spełnione.</span><span class="sxs-lookup"><span data-stu-id="68e94-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="68e94-130">Windows Workflow Foundation [weryfikacji](../../../docs/framework/windows-workflow-foundation/samples/validation.md) próbek.</span><span class="sxs-lookup"><span data-stu-id="68e94-130"> the Windows Workflow Foundation [Validation](../../../docs/framework/windows-workflow-foundation/samples/validation.md) samples.</span></span>  
  
## <a name="additional-constraints"></a><span data-ttu-id="68e94-131">Dodatkowe ograniczenia</span><span class="sxs-lookup"><span data-stu-id="68e94-131">Additional Constraints</span></span>  
 <span data-ttu-id="68e94-132">Autorzy hosta przepływu pracy można określić dodatkowe sprawdzenie poprawności ograniczenia dla działań w przepływie pracy przy tworzeniu ograniczeń i dodawanie ich do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> słownik <xref:System.Activities.Validation.ValidationSettings> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68e94-132">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="68e94-133">Każdy element <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> zawiera typ działania dla ograniczenia stosowane oraz listę dodatkowe ograniczenia dla tego typu działania.</span><span class="sxs-lookup"><span data-stu-id="68e94-133">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="68e94-134">Podczas sprawdzania poprawności jest wywoływany dla przepływu pracy, każde działanie określonego typu, łącznie z klasy pochodnej, ocenia ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="68e94-134">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="68e94-135">W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji, jest stosowane do wszystkich działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="68e94-135">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="68e94-136">Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> jest `true`, następnie określonego dodatkowe ograniczenia są oceniane podczas sprawdzania poprawności jest wywoływany przez wywołanie metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="68e94-136">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="68e94-137">Może to być przydatne do inspekcji przepływy pracy dla określonych sprawdzania poprawności konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="68e94-137">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="68e94-138">Zauważ jednak, że po wywołaniu przepływu pracy logikę weryfikacji skonfigurowany w przepływie pracy jest obliczane i musi przejść pomyślnie rozpocząć przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="68e94-138">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="68e94-139">wywoływanie weryfikacji, zobacz [wywoływania sprawdzania poprawności działania](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="68e94-139"> invoking validation, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>
