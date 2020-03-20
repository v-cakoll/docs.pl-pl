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
# <a name="declarative-constraints"></a><span data-ttu-id="15640-102">Ograniczenia deklaratywne</span><span class="sxs-lookup"><span data-stu-id="15640-102">Declarative Constraints</span></span>
<span data-ttu-id="15640-103">Ograniczenia deklaratywne zapewniają zaawansowana metoda sprawdzania poprawności dla działania i jego relacji z innymi działaniami.</span><span class="sxs-lookup"><span data-stu-id="15640-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="15640-104">Ograniczenia są konfigurowane dla działania podczas procesu tworzenia, ale dodatkowe ograniczenia mogą być również określone przez hosta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15640-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="15640-105">Ten temat zawiera omówienie przy użyciu ograniczeń deklaratywnych, aby zapewnić sprawdzanie poprawności działania.</span><span class="sxs-lookup"><span data-stu-id="15640-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="15640-106">Korzystanie z ograniczeń deklaratywnych</span><span class="sxs-lookup"><span data-stu-id="15640-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="15640-107">Ograniczenie jest działaniem zawierającym logikę sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="15640-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="15640-108">To działanie ograniczenia można tworzyć w kodzie lub w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="15640-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="15640-109">Po utworzeniu działania ograniczenia autorzy działań <xref:System.Activities.Activity.Constraints%2A> dodają to ograniczenie do właściwości działania w celu sprawdzenia <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> poprawności lub <xref:System.Activities.Validation.ValidationSettings> używają ograniczenia, aby zapewnić dodatkową weryfikację przy użyciu właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15640-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="15640-110">Logika sprawdzania poprawności może składać się z prostych sprawdzania poprawności, takich jak sprawdzanie poprawności metadanych działania, ale może również wykonywać sprawdzanie poprawności, która uwzględnia relację bieżącego działania z jego działaniami nadrzędnymi, podrzędnymi i równorzędnymi.</span><span class="sxs-lookup"><span data-stu-id="15640-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="15640-111">Ograniczenia są tworzene <xref:System.Activities.Validation.Constraint%601> przy użyciu działania, a kilka dodatkowych działań sprawdzania poprawności są dostarczane w celu pomocy w tworzeniu błędów sprawdzania poprawności i ostrzeżenia i dostarczyć informacji o powiązanych działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="15640-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="15640-112">AssertValidation i AddValidationError</span><span class="sxs-lookup"><span data-stu-id="15640-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="15640-113">Działanie <xref:System.Activities.Validation.AssertValidation> ocenia wyrażenie, do którego <xref:System.Activities.Validation.AssertValidation.Assertion%2A> odwołuje się jego właściwość, a jeśli wyrażenie ocenia `false` <xref:System.Activities.Validation.ValidationResults>, błąd sprawdzania poprawności lub ostrzeżenie jest dodawany do .</span><span class="sxs-lookup"><span data-stu-id="15640-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="15640-114">Właściwość <xref:System.Activities.Validation.AssertValidation.Message%2A> opisuje błąd sprawdzania <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> poprawności i właściwość wskazuje, czy błąd sprawdzania poprawności jest błąd lub ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="15640-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="15640-115">Wartością domyślną `false`jest <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> .</span><span class="sxs-lookup"><span data-stu-id="15640-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="15640-116">W poniższym przykładzie jest zadeklarowane ograniczenie, <xref:System.Activities.Activity.DisplayName%2A> które zwraca ostrzeżenie sprawdzania poprawności, jeśli działanie jest sprawdzane jest dwa znaki lub mniej długości.</span><span class="sxs-lookup"><span data-stu-id="15640-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="15640-117">Parametr typu ogólnego <xref:System.Activities.Validation.Constraint%601> używany dla określa typ działania, który jest sprawdzany przez ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="15640-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="15640-118">To ograniczenie <xref:System.Activities.Activity> używa jako typ ogólny i może służyć do sprawdzania poprawności wszystkich typów działań.</span><span class="sxs-lookup"><span data-stu-id="15640-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="15640-119">Aby określić to ograniczenie dla działania, <xref:System.Activities.Activity.Constraints%2A> jest dodawany do działania, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="15640-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="15640-120">Host może również określić to ograniczenie dla działań w przepływie pracy przy użyciu <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>programu , który jest omówiony w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="15640-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="15640-121">Działanie <xref:System.Activities.Validation.AddValidationError> jest używane do generowania błędu sprawdzania poprawności lub ostrzeżenia bez konieczności oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="15640-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="15640-122">Jego właściwości są <xref:System.Activities.Validation.AssertValidation> podobne do i może być używany w połączeniu z <xref:System.Activities.Statements.If> działaniami kontroli przepływu ograniczenia, takich jak działanie.</span><span class="sxs-lookup"><span data-stu-id="15640-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="15640-123">Działania relacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="15640-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="15640-124">Dostępnych jest kilka działań sprawdzania poprawności, które zawierają informacje o innych działaniach w przepływie pracy w odniesieniu do sprawdzane działanie.</span><span class="sxs-lookup"><span data-stu-id="15640-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="15640-125"><xref:System.Activities.Validation.GetParentChain>zwraca kolekcję działań, która zawiera wszystkie działania między bieżącym działaniem a działaniem głównym.</span><span class="sxs-lookup"><span data-stu-id="15640-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="15640-126"><xref:System.Activities.Validation.GetChildSubtree>zawiera zbiór działań, który zawiera działania podrzędne w wzorzec cykliczny i <xref:System.Activities.Validation.GetWorkflowTree> pobiera wszystkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="15640-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="15640-127">W poniższym przykładzie zdefiniowano `CreateState` działanie.</span><span class="sxs-lookup"><span data-stu-id="15640-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="15640-128">Działanie `CreateState` musi być zawarte `CreateCountry` w działaniu, a `GetParent` metoda zwraca ograniczenie, które wymusza to wymaganie.</span><span class="sxs-lookup"><span data-stu-id="15640-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="15640-129">`GetParent`używa <xref:System.Activities.Validation.GetParentChain> działania w połączeniu <xref:System.Activities.Statements.ForEach%601> z działaniem do sprawdzania `CreateState` działań nadrzędnych działania działania w celu ustalenia, czy wymóg jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="15640-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="15640-130">Dodatkowe ograniczenia</span><span class="sxs-lookup"><span data-stu-id="15640-130">Additional Constraints</span></span>  
 <span data-ttu-id="15640-131">Autorzy hosta przepływu pracy mogą określić dodatkowe ograniczenia sprawdzania poprawności dla działań <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> w przepływie pracy, tworząc ograniczenia i dodając je do słownika <xref:System.Activities.Validation.ValidationSettings> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15640-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="15640-132">Każdy element <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> w zawiera typ działania, dla którego ograniczenia mają zastosowanie i listę dodatkowych ograniczeń dla tego typu działania.</span><span class="sxs-lookup"><span data-stu-id="15640-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="15640-133">Gdy sprawdzanie poprawności jest wywoływane dla przepływu pracy, każde działanie określonego typu, w tym klasy pochodne, ocenia ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="15640-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="15640-134">W tym przykładzie `ActivityDisplayNameIsNotSetWarning` ograniczenie z poprzedniej sekcji jest stosowane do wszystkich działań w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="15640-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="15640-135">Jeśli <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> właściwość <xref:System.Activities.Validation.ValidationSettings> `true`jest , to tylko określone dodatkowe ograniczenia są oceniane <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>podczas sprawdzania poprawności jest wywoływana przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="15640-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="15640-136">Może to być przydatne do sprawdzania przepływów pracy dla określonych konfiguracji sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="15640-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="15640-137">Należy jednak zauważyć, że po wywołaniu przepływu pracy logika sprawdzania poprawności skonfigurowana w przepływie pracy jest oceniana i musi przebiegać, aby przepływ pracy został pomyślnie rozpocznieny.</span><span class="sxs-lookup"><span data-stu-id="15640-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="15640-138">Aby uzyskać więcej informacji na temat wywoływania sprawdzania poprawności, zobacz [Wywoływanie sprawdzania poprawności działania](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="15640-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
